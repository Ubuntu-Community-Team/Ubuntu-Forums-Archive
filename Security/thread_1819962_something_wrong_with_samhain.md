---
title: "something wrong with samhain"
date: 2011-08-07
forum: Security
---

### Post by sneakyimp on 2011-08-07
I'm trying to set up and harden an ubuntu 10.04 server.  I installed the samhain package:
```
sudo apt-get install samhain
```

It seemed to work OK at first but 3 days later, it started to fail because the directory /var/run/samhain was gone and it could not write the file /var/run/samhain/samhain.pid. From the log:
```
[SOF]
ERROR  :  [2011-08-04T19:09:52+0000] msg=<Could not write PID file>, userid=<0>, path=</var/run/samhain/samhain.pid>
35098D4976AB68C316F6F71FF715D3D57C245199B09BBA45[2011-08-04T19:09:59+0000]
ALERT  :  [2011-08-04T19:09:59+0000] msg=<EXIT>, program=<Samhain>, status=<None>
87FBAF3D77C5F907DE0E711404792FD833EF7C99E6499B9D

```

I recreated the /var/run/samhain dir and it started running OK again, but when I tried to enable the utmp section and the database section in samhainrc, it now complains about unrecognized section headers and configuration values.  These were in the original samhainrc and are described in the documentation.  Why would samhain claim they are unrecognized?

For example, it complains about line 386 which contains "[Utmp]" here:
```

[Utmp]
##
## --- Logging of login/logout events
##

## Switch on/off
LoginCheckActive = True

## Severity for logins, multiple logins, logouts
#
SeverityLogin=info
SeverityLoginMulti=crit
SeverityLogout=info

## Interval for login/logout checks
#
LoginCheckInterval = 300

```

And also about line 406 which is "[Database]".

It also complains about line 305:
```
ExportSeverity=none
```
and 308:
```
DatabaseSeverity=warn
```

What the heck?

---

### Post by bodhi.zazen on 2011-08-07
I had similar issues with samhain last time I tried, the documentation was inadequate.

I highly suggest you try the samhain mailing list.

---

### Post by sneakyimp on 2011-08-07
Thanks for your response.  It's nice to know I'm not crazy or a complete idiot.  I have already posted on the samhain website here and have just joined the mailing list.

In the meantime, do you have any information about how you solved the problem?

---

### Post by sneakyimp on 2011-08-07
*sigh*. It has become apparent to me that the ubuntu (and possibly debian) package version of samhain does not support the [Utmp] and [Database] features because the binary in the .deb package was compiled without them. If I want these features (which sound necessary if I want a read-only log) then it sounds like I'll need to compile samhain from source myself. This sounds like a fairly daunting task as the package installed numerous files. I find myself wondering if the configure/make/make install will result in these features:
* samhain starts as daemon at startup or any time server reboots
* samahin can be controlled by command /etc/init.d/samhain restart/stop/start/reload/force-reload
* samhain configuration file is located at /etc/samhain/samhainrc
* samhain performs file integrity checks and intrusion detection for ubuntu/debian specific file locations and os features
* samhain logs to a MySQL database
* samhain signs all messages
* samhain writes a lot to /var/log/samhain/samhain.log

Any advice about this might most easily be accomplished would be much appreciated.  For instance, should I first **apt-get remove samhain** ?  If I install from source, would this also introduce man pages or other documentation?

---

### Post by bodhi.zazen on 2011-08-08
purge the binary first, then try to install it from source.

Make sure you read the documentation first, it is long.

Then [/code]./configure --help[/code] should list the options.

At the end I abandoned the effort as it was too much hassle, and I found the documentation inadequate. I use OSSEC.

---

