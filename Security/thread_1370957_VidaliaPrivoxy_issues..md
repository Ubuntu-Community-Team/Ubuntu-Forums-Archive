---
title: "Vidalia/Privoxy issues."
date: 2010-01-02
forum: Security
---

### Post by headsmash on 2010-01-02
I am having trouble tunneling through privoxy. I can tunnel directly through tor without issue with foxyproxy. Using torbutton and foxyproxy I can not tunnel through privoxy. This is all on the local machine. Any help getting at least privoxy working is appreciated, Vidalia would be nice as well.

My troubleshooting output:

$ uname -r
2.6.31-16-generic
---------------------------------
$ netstat -a | grep 8118
tcp        0      0 localhost:8118          *:*                     LISTEN     
---------------------------------
$ netstat -a | grep 9050
tcp        0      0 localhost:9050          *:*                     LISTEN     
---------------------------------
$ ps -ef | grep tor
114       1583     1  0 20:05 ?        00:00:01 /usr/sbin/tor
---------------------------------
$ ps -ef | grep privoxy
privoxy   1479     1  0 20:05 ?        00:00:00 /usr/sbin/privoxy --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy/config
---------------------------------
My privoxy config file from the torproject:
# Generally, this file goes in /etc/privoxy/config
#
# Tor listens as a SOCKS4a proxy here:
forward-socks4a / 127.0.0.1:9050 .
confdir /etc/privoxy
logdir /var/log/privoxy
# actionsfile standard  # Internal purpose, recommended
actionsfile default.action   # Main actions file
actionsfile user.action      # User customizations
filterfile default.filter

# Don't log interesting things, only startup messages, warnings and errors
logfile logfile
#jarfile jarfile
#debug   0    # show each GET/POST/CONNECT request
debug   4096 # Startup banner and warnings
debug   8192 # Errors - *we highly recommended enabling this*

user-manual /usr/share/doc/privoxy/user-manual
listen-address  127.0.0.1:8118
toggle  1
enable-remote-toggle 0
enable-edit-actions 0
enable-remote-http-toggle 0
buffer-limit 4096
----------------------------
cat /var/log/privoxy/logfile 
Jan 02 20:05:13.065 7f25ac42a6f0 Info: Privoxy version 3.0.13
Jan 02 20:05:13.065 7f25ac42a6f0 Info: Program name: /usr/sbin/privoxy
Jan 02 20:05:13.069 7f25ac42a6f0 Info: Listening on port 8118 on IP address 127.0.0.1
$

---

