# dji-packet-dumps

Dumps of communication and logs from various DJI hardware.

# Purpose

This storage of communication data will allow to analyze the internal communication
protocols, as well as act as reference point for diagnosing hardware issues.

Each file is accompanied by a text document, describing how it was captured, and
what was the scenario of the run.

# Usage

These communication files are in PCap format, and are intended to use with Wireshark,
though any tool with PCap support can open them.

In order for the content to be analyzed by Wireshark, dissectors have to be installed.
[Follow instructions](https://github.com/mefistotelis/phantom-firmware-tools/tree/master/comm_dissector)
to add the dissectors for Dji protocols to your Wireshark installation.

It is possible to make a script which drops the PCap headers and converts the files
to raw data form. But as long as there is no need, there is no script.

# DLT_USER slots

Each of the PCap files contain information about which communication protocol is
used within it. Since there is no official definition of the DJI protocols within
possible choices, the "user protocol" was used in these PCap files. There are
several user slots available; to make the files here work, you should associate:

* ```DLT_USER3``` with ```dji_p3``` to open any of Phantom 3 files
* ```DLT_USER8``` with ```dji_mavic``` to open any of Mavic files
* ```DLT_USER10``` with ```dji_spark``` to open any of Spark files

# Related tools

The files in this repository are either captured by [comm_serial2pcap.py](https://github.com/mefistotelis/phantom-firmware-tools#comm_serial2pcappy),
or converted to PCap format from raw DATs using [comm_dat2pcap.py](https://github.com/mefistotelis/phantom-firmware-tools#comm_dat2pcappy).
