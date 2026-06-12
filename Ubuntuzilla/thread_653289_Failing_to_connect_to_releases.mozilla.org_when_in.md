---
title: "Failing to connect to releases.mozilla.org when installing SeaMonkey"
date: 2007-12-29
forum: Ubuntuzilla
---

### Post by rlindau on 2007-12-29
I've been trying to use ubuntuzilla on a Kubuntu 7.10 system to install SeaMonkey 1.1.7.   

The install is failing due to timeouts connecting to the various IP addresses for releases.mozilla.org.  

I've tried pinging the IP addresses that show up in the terminal transcript (snippet below; I killed it via ctrl-c), and the pings indeed  timeout.  

When I ping releases.mozilla.org, I get a different IP address that I see in the terminal session.  

Any idea what I need to do to get the SeaMonkey install to work? 

Thanks, Rob L

> 
rob@robsnetvista:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.4.5

This script installs the latest release of the official Mozilla build of Seamonk                                                                                                   ey on Ubuntu Linux. If you run into any problems using this script, or have feat                                                                                                   ure requests, suggestions, or general comments, please visit our website at http                                                                                                   ://ubuntuzilla.sourceforge.net/

Retrieving the version of the latest release of Seamonkey from the Mozilla websi                                                                                                   te...
The most recent release of Seamonkey is detected to be 1.1.7. Please make sure t                                                                                                   his is correct before proceeding. (You can confirm by going to [http://www.mozill](http://www.mozill)                                                                                                   a.org/)
If no version number shows, if the version shown is not the latest, or if you wo                                                                                                   uld like to install an older release, press 'n', and you'll be given the option                                                                                                    to enter the version manually. Otherwise, press 'y', and proceed with installati                                                                                                   on. [y/n]?
Please enter 'y' or 'n': y

Old Seamonkey preferences not found. Nothing to back up. Proceeding with installation.


Downloading Seamonkey archive from the Mozilla site

--18:49:33--  [ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz](ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz)
           => `seamonkey-1.1.7.en-US.linux-i686.tar.gz'
Resolving releases.mozilla.org... 204.152.184.113, 207.200.66.54, 216.165.129.141, ...
Connecting to releases.mozilla.org|204.152.184.113|:21... failed: Connection timed out.
Connecting to releases.mozilla.org|207.200.66.54|:21... failed: Connection timed out.
Connecting to releases.mozilla.org|216.165.129.141|:21... Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1051, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 215, in start
    si.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 516, in install
    self.downloadPackage()
  File "/usr/local/bin/ubuntuzilla.py", line 856, in downloadPackage
    self.util.robustDownload({'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/" + self.packageFilename, 'includewithtest':True})
  File "/usr/local/bin/ubuntuzilla.py", line 153, in robustDownload
    self.execSystemCommand(**argsdict)
  File "/usr/local/bin/ubuntuzilla.py", line 135, in execSystemCommand
    returncode = subprocess.call(executionstring, shell=True)
  File "/usr/lib/python2.5/subprocess.py", line 443, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.5/subprocess.py", line 1166, in wait
    pid, sts = self._waitpid_no_intr(self.pid, 0)
  File "/usr/lib/python2.5/subprocess.py", line 1007, in _waitpid_no_intr
    return os.waitpid(pid, options)
KeyboardInterrupt
rob@robsnetvista:~$  

---

### Post by nanotube on 2008-01-08
hm, well, maybe they had some network problems... can you try again now and see what happens?

---

### Post by rlindau on 2008-01-10
I tried it again but with the same result - connection timing out to releases.mozilla.org...

I'm a Kubuntu novice - is there some network setting I need to look at (could be causing my own problem)?  Then again, I can get to the internet with no trouble, and ubuntuzilla does correctly determine the most current release available for download....

Regards, Rob L

---

### Post by nanotube on 2008-01-15
well, i tried a few times, and it works just fine for me... so i'm not sure what's causing your problem.

but the thing is, there are multiple mirrors that it should try, so instead of doing a kb interrupt, wait for it, and if releases.mozilla.org fails, it will try another mirror. just give it some time. 

see if that come through.

---

### Post by rlindau on 2008-01-16
I had let it run overnight on a couple occasions - eventually it cycled thru all the mirrors and quit.

The problem must be on my end, but I have no idea what.  Other applications (browser, adept pkg mgr, and even the version lookup in ubuntuzilla) get out OK.

Thx, RL

---

### Post by nanotube on 2008-01-17
> **rlindau said:**
> I had let it run overnight on a couple occasions - eventually it cycled thru all the mirrors and quit.

The problem must be on my end, but I have no idea what.  Other applications (browser, adept pkg mgr, and even the version lookup in ubuntuzilla) get out OK.

Thx, RL

hm... and if you try a wget from the terminal manually, does that also fail:
```
wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.7/seamonkey-1.1.7.en-US.linux-i686.tar.gz
```

how about a simple wget google, does that work?
```
wget www.google.com
```

also post the contents of your /etc/wgetrc and your ~/.wgetrc (if it exists)

also, are you using any proxy servers, or connecting directly?

---

### Post by pumpkinpapa on 2008-02-24
I'm connecting through a proxy server on port 2121 over wireless to a xp box and all the releases servers are timing out. I have the network proxy for my laptop with ftp set to 2121, and the correct version is shown for the latest Seamonkey release.

What might I be doing wrong? I'm guessing it's the port number for ftp on the xp proxy.

---

### Post by nanotube on 2008-02-24
so, are you saying that in order to access any ftp server, you need to connect to port 2121 instead of just 21?

i.e., if you want to connect to any old ftp server on port 21, can you just do
```
ftp server.com 21
```
and connect? or do you have to do something different?

---

