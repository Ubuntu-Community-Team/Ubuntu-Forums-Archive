---
title: "upstart troubleshooting best practices?"
date: 2011-11-04
forum: Server Platforms
---

### Post by aaminoff on 2011-11-04
upstart replaced the old Sys V init system several years ago. I have searched in many places but there does not appear to be consensus among sysadmins on best practices for troubleshooting boot problems in the new upstart world.

Broadly, my questions are

1. What is the best way to see the output of startup scripts in a log?

2. How can you find out why a given service is not being triggered to start at all?

I am working with the 10.04 LTS server distribution.

This documentation:

[http://upstart.ubuntu.com/wiki/Debugging](http://upstart.ubuntu.com/wiki/Debugging)

is not very helpful. There are a bunch of code snippets, but some frankly make no sense and for some it is not clear where the code snippet should go, nor what output would then be logged. I have some concept of what exec is, but what is being exec'd? A sub-shell running the pre-start script? The entirety of upstart itself?

There is also 

[http://upstart.ubuntu.com/cookbook](http://upstart.ubuntu.com/cookbook)

which talks about "console output", which directs the stdout of (the current?) job to /dev/console. One can see from plymouth-upstart-bridge that at a certain point everything that was logged to /dev/console goes into boot.log, which is great: do jobs with "console output" go there too?

There is "initctl log-priority", which you can also influence with kernel args --verbose and --debug, which talks about logging to syslog. But if it is early in the boot process before syslogd is started, where do those logs go?

The init man page mentions /etc/init.conf (in addition to /etc/init/*.conf). Presumably this would be a config file that controls global aspects of upstart, including perhaps logging. Unfortunately there is no man page for /etc/init.conf and no sample file with comments.

What I'm looking for is responses of the form "when we had a boot problem, we did such-and-such and that let us find the problem quickly and easily".

---

