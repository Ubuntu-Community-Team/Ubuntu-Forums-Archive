---
title: "problem updating thunderbird with checkforupdategui"
date: 2007-11-17
forum: Ubuntuzilla
---

### Post by kc109 on 2007-11-17
### checkforupdategui for thunderbird fails on Ubuntu ver 7.10 with all security updates to 17/11/07
### both firefox and thunderbird installed via ubuntuzilla into /opt and working ok

SysA:~$ ubuntuzilla.py --version
Ubuntuzilla version 4.4.3
Project homepage: [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

### firefox update is ok, but then it is at latest ver
SysA:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 2.0.0.9
Currently installed version of Firefox : 2.0.0.9

### thunderbird update fails
SysA:~$ ubuntuzilla.py -a checkforupdategui -p thunderbird
Retrieving the version of the latest release of Thunderbird from the Mozilla website...
Latest release version of Thunderbird : 2.0.0.9
Currently installed version of Thunderbird : 2.0.0.6
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1045, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 207, in start
    ti.start()
  File "/usr/local/bin/ubuntuzilla.py", line 241, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 540, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 555, in updateActionsGui
    dbusSessionAddress = self.util.getSystemOutput("grep -z DBUS_SESSION_BUS_ADDRESS /proc/"+pid+"/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'")
  File "/usr/local/bin/ubuntuzilla.py", line 124, in getSystemOutput
    return result[0]
IndexError: list index out of range

### with debug option
SysA:~$ ubuntuzilla.py -d -a checkforupdategui -p thunderbird
Your commandline options:
{'package': 'thunderbird', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'mirror': 'releases.mozilla.org', 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.
Retrieving the version of the latest release of Thunderbird from the Mozilla website...
Latest release version of Thunderbird : 2.0.0.9
Currently installed version of Thunderbird : 2.0.0.6
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1045, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 207, in start
    ti.start()
  File "/usr/local/bin/ubuntuzilla.py", line 241, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 540, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 555, in updateActionsGui
    dbusSessionAddress = self.util.getSystemOutput("grep -z DBUS_SESSION_BUS_ADDRESS /proc/"+pid+"/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'")
  File "/usr/local/bin/ubuntuzilla.py", line 124, in getSystemOutput
    return result[0]
IndexError: list index out of range

---

### Post by nanotube on 2007-11-17
hi,
well, there does seem to be a problem with checkforupdate there on your system, i'll look into this..
but note that checkforupdate does not /update/, it only /checks/ for the existence of an update
so... now that you know there's an update you can follow the upgrade procedures (see the ubuntuzilla wiki for instructions).

in brief: run thunderbird with gksudo, use the built-in thunderbird updater. :)

---

### Post by kc109 on 2007-11-18
> **nanotube said:**
> hi,
well, there does seem to be a problem with checkforupdate there on your system, i'll look into this..
but note that checkforupdate does not /update/, it only /checks/ for the existence of an update
so... now that you know there's an update you can follow the upgrade procedures (see the ubuntuzilla wiki for instructions).

in brief: run thunderbird with gksudo, use the built-in thunderbird updater. :)

Thanks for your reply.
A bad choice of words on my part when I said I had problems with updating.
I only installed Ubuntuzilla a couple of months ago and this is the first update I have seen. I knew that an update had been released and I became suspicious that the Ubuntuzilla GUI update notification had not come up after a few days, so I tried checkforupdate from the command line.
By the way this is my cron tab file if it is of any use.
 crontab -l
0 0,4,8,12,16,20 * * * /usr/local/bin/ubuntuzilla.py -p thunderbird -a checkforupdategui 2>&1 | logger -p user.notice -t "UBUNTUZILLA" -- 
0 0,4,8,12,16,20 * * * /usr/local/bin/ubuntuzilla.py -p firefox -a checkforupdategui 2>&1 | logger -p user.notice -t "UBUNTUZILLA" -- 


I think I will hold off doing a manual update for a few days so that I still have something to test against if a possible solution comes along.

Perhaps I should have pointed out that this is an older machine [AMD Athlon XP 2600+, 2083 MHz, 512 Mbyte memory] and my Linux skills are near zero so would not necessarily have noticed if I had done something dumb.

---

### Post by nanotube on 2007-11-18
could you tell me which version and flavor of ubuntu are you running? 

and also post output of
```
ps ax |grep session
```

thanks!

---

### Post by kc109 on 2007-11-18
> **nanotube said:**
> could you tell me which version and flavor of ubuntu are you running? 

and also post output of
```
ps ax |grep session
```

thanks!

Gnome Ubuntu 7.10, kernel 2.6.22-14-generic   

 ps ax |grep session
 4631 ?        S      0:00 dbus-daemon --session --print-address --nofork
 5830 ?        Ssl    0:00 x-session-manager
 5867 ?        Ss     0:00 /usr/bin/ssh-agent x-session-manager
 5873 ?        Ss     0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
 5896 ?        S      0:00 vino-session --sm-client-id default5
 6778 pts/0    S+     0:00 grep session

Hope this helps

---

### Post by nanotube on 2007-11-18
and if you open a terminal, and run command
```
notify-send "bla"
```
do you get a little bubble box at the bottom right with the "bla" message?

---

### Post by pchandle on 2007-11-18
I can also say I'm having the same problem. Same Ubuntu, same ps output but different version of Ubuntuzilla (ver 4.1.1)

The errors I get are very similar but are obviously a slightly different build of Ubuntuzilla:
```
python ./ubuntuzilla.py -a checkforupdategui -p thunderbird

Retrieving the version of the latest release of Thunderbird from the Mozilla website...
Latest release version: 2.0.0.9
Currently installed version: 2.0.0.6
Traceback (most recent call last):
  File "/home/pchandle/ubuntuzilla.py", line 757, in <module>
    bs.start()
  File "/home/pchandle/ubuntuzilla.py", line 77, in start
    ti.start()
  File "/home/pchandle/ubuntuzilla.py", line 105, in start
    self.checkforupdateGui()
  File "/home/pchandle/ubuntuzilla.py", line 373, in checkforupdateGui
    self.updateActionsGui()
  File "/home/pchandle/ubuntuzilla.py", line 388, in updateActionsGui
    dbusSessionAddress = self.getSystemOutput("grep -z DBUS_SESSION_BUS_ADDRESS /proc/"+pid+"/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'")
  File "/home/pchandle/ubuntuzilla.py", line 458, in getSystemOutput
    return result[0]
IndexError: list index out of range

```
 If I run the suggested 'notify-send' command I do indeed get the 'bla' bubble box. 

On the other hand, I tried the manual update method (gksudo thunderbird, etc) and was told that there was no new updates available??

I'm happy to provide more info to help sort this out.

---

### Post by kc109 on 2007-11-19
> **nanotube said:**
> and if you open a terminal, and run command
```
notify-send "bla"
```
do you get a little bubble box at the bottom right with the "bla" message?

Yes I do.
It disappears if I leave it for 8 seconds or, if I left or right mouse click on it.

---

### Post by pchandle on 2007-11-19
I think I've worked out my problem.. perhaps it may provide some help here too..

I tried doing a manual update without the GUI using:
```
ubuntuzilla.py -a checkforupdatetext -p thunderbird
```

I then received a response that said I hadn't installed Thunderbird using the Ubuntuzilla script. *a light turned on*

I recently upgraded Ubuntu from Feisty to Gutsy - I guess the upgrade moved in the official version of Thunderbird while my Ubuntuzilla script and cron entries remained.

Since then, I've run this to re-install Thunderbird using the script:
```
ubuntuzilla.py -a install -p thunderbird
```
The install went OK (including a backup of my mail files) except for the PGP key verification. It just couldn't connect...
```
...
Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from subkeys.pgp.net . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgpkeys.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from pgpkeys.mit.edu . Trying again...
gpg: requesting key 0E3606D9 from hkp server pgp.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
Unable to retrieve Mozilla Software Releases Public key from pgp.mit.edu . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.
```
After using the -g option (ignore pgp key verification) It installed OK.
Of course I now have the latest build, so the output from the update:
```
ubuntuzilla.py -a checkforupdategui -p thunderbird
```
gives a response like:
```
Retrieving the version of the latest release of Thunderbird from the Mozilla website...
Latest release version: 2.0.0.9
Currently installed version: 2.0.0.9
```
and no balloon message (as you would expect)
I guess I'll have to wait until the next release to see if it crops up again...

---

### Post by nanotube on 2007-11-20
> **kc109 said:**
> Yes I do.
It disappears if I leave it for 8 seconds or, if I left or right mouse click on it.

hmm... that leaves me to wonder what's going on. :)
first... an easy one: does the error keep happening even after a clean reboot?

if so, then ...

ok, so run ```
ps ax |grep session
``` again, and look for the PIDs of the following processes:
```

x-session-manager
dbus-daemon --session --print-address --nofork
any other dbus-daemons

```

then, for each of those, run
```
grep -z DBUS_SESSION_BUS_ADDRESS /proc/PID/environ
```

and tell me for which one[s] you get any output?

---

### Post by kc109 on 2007-11-20
> **nanotube said:**
> hmm... that leaves me to wonder what's going on. :)
first... an easy one: does the error keep happening even after a clean reboot?

if so, then ...

ok, so run ```
ps ax |grep session
``` again, and look for the PIDs of the following processes:
```

x-session-manager
dbus-daemon --session --print-address --nofork
any other dbus-daemons

```

then, for each of those, run
```
grep -z DBUS_SESSION_BUS_ADDRESS /proc/PID/environ
```

and tell me for which one[s] you get any output?


First; this system gets rebooted several times a day so it should have been 'clean' for all previous tests.

Second; cold reboot the system and after login did the following
```

SysA:~$ ps ax |grep session
 4632 ?        S      0:00 dbus-daemon --session --print-address --nofork
 5975 ?        Ssl    0:00 x-session-manager
 6012 ?        Ss     0:00 /usr/bin/ssh-agent x-session-manager
 6018 ?        Ss     0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
 6044 ?        S      0:00 vino-session --sm-client-id default5
 9035 pts/0    S+     0:00 grep session
SysA:~$ grep -z DBUS_SESSION_BUS_ADDRESS /proc/5975/environ
SysA:~$ grep -z DBUS_SESSION_BUS_ADDRESS /proc/4632/environ
grep: /proc/4632/environ: Permission denied
SysA:~$ sudo grep -z DBUS_SESSION_BUS_ADDRESS /proc/4632/environ
[sudo] password for SysA:
SysA:~$ grep -z DBUS_SESSION_BUS_ADDRESS /proc/6018/environ

```
As you can see there was no output for any of them.


Third; did the following experiment several times
```

SysA:~$ notify-send "Bla"
SysA:~$ notify-send -t 20000 "Bla"
SysA:~$ notify-send -t 0 "Bla"
SysA:~$ notify-send -v
notify-send 0.4.4

```
The first line displays for 8 seconds or until a mouse click.
The second line displays for 20 seconds or until a mouse click.
The third line displays until a mouse click ( I gave up waiting after 180 seconds).
It seems that on my system there is an 8 second default timeout for some reason.


I needed to check something on the latest Thunderbird, so I have had to update to 2.0.0.9 and no longer have an old version to test on. If you come up with anything else for me to try then I would be happy to, but I guess there is not much that can be done until the next Firefox/Thunderbird update.

---

### Post by nanotube on 2007-11-20
hm, mighty strange, and i don't know what else to try.
the x-session really should have the dbus_session variable in it, 

otherwise i don't know how to access the dbus session from the crontab script... let's hope someone who knows about dbus can pop in and shed light on this issue...

thank you very much for your thorough testing in pursuit of this problem! if i find anything promising i'll post back here.

---

### Post by el_baby on 2008-04-17
FWIW, I'm having the exact same problem.

ubuntu 7.10 (gutsy)
ubuntuzilla 4.4.6-0ubuntu1
and:

 ```
$ ps ax |grep session
 4876 ?        S      0:00 dbus-daemon --session --print-address --nofork
 5445 ?        Ssl    0:00 x-session-manager
 5480 ?        Ss     0:00 /usr/bin/ssh-agent x-session-manager
 5486 ?        Ss     0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
 5525 ?        S      0:00 vino-session --sm-client-id default5
11001 pts/3    S+     0:00 grep session

$ for i in 4876 5445 5480 5486 ; do echo $i; sudo grep -z DBUS_SESSION_BUS_ADDRESS /proc/${i}/environ; done
4876
5445
5480
5486

```

that is, it can't find DBUS_SESSION_BUS_ADDRESS on any process environment :-(

can I be of any help 2 u? (I don't know how to access the dbus session from crontab... in fact, I don't even know what the dbus is :-)  )

---

### Post by nanotube on 2008-04-17
> **el_baby said:**
> FWIW, I'm having the exact same problem.

ubuntu 7.10 (gutsy)
ubuntuzilla 4.4.6-0ubuntu1
and:

 ```
$ ps ax |grep session
 4876 ?        S      0:00 dbus-daemon --session --print-address --nofork
 5445 ?        Ssl    0:00 x-session-manager
 5480 ?        Ss     0:00 /usr/bin/ssh-agent x-session-manager
 5486 ?        Ss     0:00 dbus-daemon --fork --print-address 17 --print-pid 19 --session
 5525 ?        S      0:00 vino-session --sm-client-id default5
11001 pts/3    S+     0:00 grep session

$ for i in 4876 5445 5480 5486 ; do echo $i; sudo grep -z DBUS_SESSION_BUS_ADDRESS /proc/${i}/environ; done
4876
5445
5480
5486

```

that is, it can't find DBUS_SESSION_BUS_ADDRESS on any process environment :-(

can I be of any help 2 u? (I don't know how to access the dbus session from crontab... in fact, I don't even know what the dbus is :-)  )

hm, well...

does notify-send work for you from commandline? i.e.:
```
notify-send "bla"
```

do you have the DBUS_SESSION_BUS_ADDRESS variable in your regular shell environment?
```
env |grep DBUS
```

---

### Post by nanotube on 2008-04-18
one more thing,if command 
```
notify-send "bla"
```
works, could you test something for me...

can you make a shell script that does that:
```
#!/bin/bash
notify-send "bla"
```

schedule it to run from your crontab (like every minute, so that you don't have to wait long),

and see if it comes up?

i'm thinking that maybe gutsy/hardy dbus problem may actually be an improvement, in that it will work from crontab without me having to do the fancy dbus session detection. please test! :)

---

### Post by el_baby on 2008-04-18
> **nanotube said:**
> i'm thinking that maybe gutsy/hardy dbus problem may actually be an improvement, in that it will work from crontab without me having to do the fancy dbus session detection. please test! :)

Well... regretfully, it seems not :-(

That is:
```
notify-send "bla"
``` works from the command line, but **not** from crontab (not even without the shell script... that is, after the script didn't show anything, I tried to put ```
* * * * * /usr/bin/notify-send "direct"
``` in crontab o no avail.

As for the environment variable, I got this:
```
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-W876DUJ1cH,guid=68660ff6a65157429c328e00480887c2
```

HTH

---

### Post by nanotube on 2008-04-18
aha, i think i figured it out...
see if you have a process named "notification-daemon" running
```
ps ax |grep notification-daemon
```

if so... then try the ubuntuzilla.py version attached to this bug report on sourceforge, see if it works!
[https://sourceforge.net/tracker/index.php?func=detail&aid=1945299&group_id=202789&atid=982990](https://sourceforge.net/tracker/index.php?func=detail&aid=1945299&group_id=202789&atid=982990)

(yes, i've been working on this on two fronts, it seems :) )

make sure to run in debug mode to force notification even if no update is necessary.

---

### Post by el_baby on 2008-04-18
Yeah, man!!!!

It **did** work... Thanx a lot for your effort!!!

---

### Post by el_baby on 2008-04-18
BTW, nanotube... is there any repository where you keep the .deb files in a debianized style... (so that I can upgrade it automatically with apt-get)?

---

### Post by nanotube on 2008-04-18
> **el_baby said:**
> BTW, nanotube... is there any repository where you keep the .deb files in a debianized style... (so that I can upgrade it automatically with apt-get)?

cool, the other guy also confirmed the fix on the sourceforge bug report, so i'm gonna make a new release.

no, i don't have an actual repository... that's why i made a 'custom' updater, which should work - ubuntuzilla will check for the new version by itself, and update itself if one is available...

maybe one of these days if i find a nice tutorial on how to set up a repo, i'll set one up on sf.net :)

thanks for your help in tracking this down, btw!

---

### Post by el_baby on 2008-05-20
What I meant was not a repo for firefox & thunderbird but a repo for ubuntuzilla itself...

---

### Post by nanotube on 2008-05-21
> **el_baby said:**
> What I meant was not a repo for firefox & thunderbird but a repo for ubuntuzilla itself...

yes, that's what i meant as well. :)

---

