# mqtt-grep-color
mqtt-grep-color is a shell script that subscribes to a MQTT topic using mosquitto_sub, adds a time stamp in front of each line, optionally greps for an expression and colors its output. This eases MQTT debugging on the command line. 

Notes:
1. mqtt-grep-color relies heavily on the **output coloring feature of GNU grep**. The BusyBox version of grep does not support coloring, so the script doesn't color the output on busybox.
2. **Non-printable characters** are removed from the mosquitto_sub output before further processing.
3. If you have a BusyBox grep that doesn't support line buffering, try to install the command stdbuf, i.e. package "coreutils-stdbuf" on OpenWrt. Otherwise, ugly, bulky,delayed output might be the consequence....

Example usage with all optional parameters, i.e. the grep-expression, a MQTT topic and mosquitto_sub-options:

_mqtt-grep-color " "  "#"  "-R  -h test.mosquitto.org"_
