---
title: "snmptrapd no auth"
date: 2011-05-26
forum: Server Platforms
---

### Post by Lord_ on 2011-05-26
Hi Everyone,

I've just migrated an old FC6 box across to Ubuntu, all services are now running with equivalents except for snmptrapd.

On the old FC6 box, snmptrapd did not require any authentication and would process all traps, in this box, I can't get the traps to send to their handlers. 
If I run snmptrapd -H I get the following:

root@nagios01:/usr/local/scripts/traphandler# snmptrapd -H
No log handling enabled - turning on stderr logging
/etc/snmp/snmptrapd.conf: line 39: Warning: Unknown token: disableAuthorization.
Configuration directives understood:



Short answer is I want to turn off all authentication for snmptrapd but I am unsure how to get this done, the man page is a little cryptic when it comes to turning it off.

I have the following in my snmptrapd.conf:

disableAuthorization yes
ignoreAuthFailure yes


I am starting with:
snmptrapd -a -c /etc/snmp/snmptrapd.conf 0.0.0.0


Anyone know how I can turn off all auth??

---

