---
title: "I get an error when i try to install Kojoney SSH honeypot"
date: 2008-09-15
forum: Security
---

### Post by x3roconf on 2008-09-15
I get this error when i try to install Kojoney

root@linux:/home/myusername/kojoney# sh INSTALL.sh
INSTALL.sh: 3: function: not found
Error at
Kojoney installation failed
root@linux:/home/myusername/kojoney#

:(

Anyone else having this problem?

---

### Post by Can0beans on 2009-09-29
Did you ever have any luck get kojoney to work?  Or find something similar to replace it?

---

### Post by x3roconf on 2009-09-30
> **Can0beans said:**
> Did you ever have any luck get kojoney to work?  Or find something similar to replace it?

No. :)

---

### Post by tps on 2010-02-24
> **x3roconf said:**
> I get this error when i try to install Kojoney

root@linux:/home/myusername/kojoney# sh INSTALL.sh
INSTALL.sh: 3: function: not found
Error at
Kojoney installation failed
root@linux:/home/myusername/kojoney#

:(

Anyone else having this problem?

I'm just starting to look at this package. The above error is due to (at least on my 9.10 system) /bin/sh pointing to /bin/dash, and not /bin/bash. Either change the first line from /bin/sh to /bin/bash, or call the install script as 'bash ./INSTALL.sh'.

There are issues with packages and versions of python. If I make progress, I'll report back.

Tim

---

### Post by OneArmedMan on 2010-02-27
There most certainly are issues installing Kojoney 0.4.2 on an Ubuntu 9.10 system.

As previously mentioned to start with you need to `bash install.sh` to ensure that the install script is running in the correct shell environment.

I got stuck several times with Python / Twisted installation issues.

I managed to get past the `unable to locate python.h` by installing all of the following

aptitude install python2.5-dev python2.5-gst0.10-dev python2.6-dev python2.6-gst0.10-dev python3.0-dev python-all-dev

but i think that Kojoney was using Python 2.6 , so this can probably be trimmed down to python2.6-dev and/or python2.6-gst0.10-dev, however further testing would be wise.

TwistedConch problem was a bit odd as the version supplied with the Kojoney tar file seemed to be quite old, TwisteConch-0.6.0.tar.gz .

Installation would fail complaining `IOError: [Errno 2] No such file or directory: 'twisted/conch/_version.py'`

Checking the temp install path of /tmp/tmp.`random-string`/
showed that when the installer unpacked the supplied version of TwitedConch there was no _version.py file.

As the installer will only use its bundled version of Twisted my solution was as follows

i) Download the current version of TwistedConch from the Twisted web page : [http://tmrc.mit.edu/mirror/twisted/Conch/9.0/TwistedConch-9.0.0.tar.bz2](http://tmrc.mit.edu/mirror/twisted/Conch/9.0/TwistedConch-9.0.0.tar.bz2)

ii) Unpack the archive and rename the folder from TwistedConch-9.0.0 to TwistedConch-0.6.0 

iii) tar up the archive with the same name as the Kojoney supplied archive

iv) replace the Kojoney supplied archive by moving the newly created TwistedConch-0.6.0.tar.gz into /home/*user*/kojoney/lib/

and then re-ran the Install.sh

After the last install run everything seemed to build and install correctly, however the installer fails to find the man page locations and you need to manually specify the path : /usr/share/man/man1/

Notes : I also had problems with the Zope install, but can not recall how I got past them. Probably getting the right Python dev packages installed helped there.

The TwistedConch-9.0.0.tar.gz file that I repacked as TwistedConch-0.6.0.tar.gz can be found here : [http://users.on.net/~onearmed/linux/TwistedConch-0.6.0.tar.gz](http://users.on.net/~onearmed/linux/TwistedConch-0.6.0.tar.gz) for anyone too lazy to do it themselves.

Warnings : I am not a programmer and I know little enough about Linux in general. This seemed to work for me, but if you do the same and it eats your cat, I don't want to know.

---

### Post by tps on 2010-03-02
> **OneArmedMan said:**
> There most certainly are issues installing Kojoney 0.4.2 on an Ubuntu 9.10 system.

As previously mentioned to start with you need to `bash install.sh` to ensure that the install script is running in the correct shell environment.

I got stuck several times with Python / Twisted installation issues.


(clip)

and then re-ran the Install.sh

After the last install run everything seemed to build and install correctly, however the installer fails to find the man page locations and you need to manually specify the path : /usr/share/man/man1/

Notes : I also had problems with the Zope install, but can not recall how I got past them. Probably getting the right Python dev packages installed helped there.

The TwistedConch-9.0.0.tar.gz file that I repacked as TwistedConch-0.6.0.tar.gz can be found here : [http://users.on.net/~onearmed/linux/TwistedConch-0.6.0.tar.gz](http://users.on.net/~onearmed/linux/TwistedConch-0.6.0.tar.gz) for anyone too lazy to do it themselves.

Warnings : I am not a programmer and I know little enough about Linux in general. This seemed to work for me, but if you do the same and it eats your cat, I don't want to know.


I removed the installation of the assorted packages from the install script as I already had them installed via apt. Everything is running (sort of) after adapting a couple of lines to the newer conch, but I'm still getting errors when sessions are running. Things like:

```
          File "/usr/lib/python2.6/dist-packages/twisted/python/log.py", line 441, in emit
            util.untilConcludes(self.write, timeStr + " " + msgStr)
          File "/usr/lib/python2.6/dist-packages/twisted/python/util.py", line 756, in untilConcludes
            return f(*a, **kw)
        exceptions.IOError: [Errno 5] Input/output error

```

I'll keep plugging at it.

Tim

---

### Post by mnajem on 2010-07-04
In my case I edited the conch part since I build that manually, so I ran bash INSTALL.sh without having the conch part installation.

---

### Post by mindego on 2010-11-08
If have successuffy installed this honeypot, in order to get rid of  "Input/output error" you will have to edit  /usr/share/kojoney/coret_config.py  You will have to change

```
    ROOT_CONFIG_LOGS = [sys.stderr, open("/var/log/honeypot.log", "a")]
```to
```
    ROOT_CONFIG_LOGS = [open("/var/log/honeypot.log", "a")]
```
In that case logs will be redirected into this logfile only and you will cast away this fun-spoiling error

---

### Post by hackertarget on 2011-02-15
As an FYI for other ssh honeypot searchers. An alternative to Kojoney is [kippo]("http://code.google.com/p/kippo/").

It is easy to [setup and use]("http://hackertarget.com/2011/02/kippo-honeypot-on-ubuntu-10-04/").

---

