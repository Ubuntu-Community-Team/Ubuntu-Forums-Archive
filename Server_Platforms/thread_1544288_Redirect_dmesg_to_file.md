---
title: "Redirect dmesg to file"
date: 2010-08-02
forum: Server Platforms
---

### Post by ServerAlex on 2010-08-02
Hello everyone, 

is there a way I can redirect messages from kernel ringbuffer to a logfile, e.g. with rsyslogd? With redirect I mean that the messages do no longer appear in dmesg, but only in the logfile. 
In my case that should be iptables log messages.

---

### Post by gobbledigook on 2010-08-02
haev you checked out the [**_dmesg man page_**]("http://unixhelp.ed.ac.uk/CGI/man-cgi?dmesg+8")? always a good place to start :)

---

### Post by linux18 on 2010-08-02
the universal output redirecter ">"
example:
echo "hello world" > file.log
so:
command > file
redirects the output of a command to a file. 
 2>&1
 added into the line will redirect errors too

---

### Post by ServerAlex on 2010-08-02
ehm have I said anything about redirecting stdout/err to a file!? I was talking about kernel ring buffer and syslog!

---

