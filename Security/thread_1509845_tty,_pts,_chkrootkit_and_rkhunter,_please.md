---
title: "tty, pts, chkrootkit and rkhunter, please"
date: 2010-06-14
forum: Security
---

### Post by karinaik on 2010-06-14
Hi everybody!
I'm a new user of Lucid Lynx and I'm still learning some of its features, but definitely enjoying it better than Windows.

The reason I changed to Ubuntu was my concern about the lack of security in Windows.

So, I've been reading a lot of articles and posts about security in Ubuntu.

I have run the 'who' command and the result was:

[COLOR=Blue]myname   tty7         2010-06-14 18:30 (:0)
myname   pts/1        2010-06-14 19:48 (:0.0)[/COLOR]

I still need to study more about tty and pts, but, this result scared me a bit.
Is there something wrong with it?

I am running Lucid Lynx in my Dell Notebook which is connected to a router (wireless disabled). One desktop computer (with Windows XP) is connected in that router...

Thanks in advance.
----

Another doubt I'm having is the fact that when I run the tty command, this appear:

[COLOR=Blue]myname@somewhere:~$ tty
/dev/pts/1[/COLOR]

I still don't know how to interpret it...
Any comments from experts people from the forum would be appreciated!

-----------------

Other thing that scared:
When I have run chkrootkit, I noticed some entries that made me wonder:

[COLOR=Blue]Checking `z2'...                                            
user myname deleted or never logged from last[/COLOR]log!

and:

[COLOR=Blue]Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/firefox-3.6.3/.autoreg /usr/lib/pymodules/python2.6/.path /usr/lib/xulrunner-1.9.2.3/.autoreg[/COLOR]


:(
Please, if someone could explain them to me...I'd be very grateful.

------------------

As worried as I am now, I also have run the rkhunter.
Should I concern about these warnings?

[COLOR=Blue][18:38:27] Performing filesystem checks
[18:38:27] Info: Starting test name 'filesystem'
[18:38:27] Info: SCAN_MODE_DEV set to 'THOROUGH'
[18:38:27]   Checking /dev for suspicious file types         [ Warning ]
[18:38:27] Warning: Suspicious file types found in /dev:
[18:38:28]          /dev/shm/pulse-shm-1646054447: data
[18:38:28]          /dev/shm/pulse-shm-701920850: data
[18:38:28]          /dev/shm/pulse-shm-4263070844: data
[18:38:28]          /dev/shm/pulse-shm-1029077015: data
[18:38:28]          /dev/shm/ecryptfs-myname-Private: ASCII text
[18:38:28]          /dev/shm/pulse-shm-2905944366: data
[18:38:28]   Checking for hidden files and directories       [ Warning ]
[18:38:28] Warning: Hidden directory found: /dev/.udev
[18:38:28] Warning: Hidden directory found: /dev/.initramfs
[/COLOR]
And this:

[COLOR=Blue][18:38:26] Performing system boot checks
[18:38:26] Info: Starting test name 'startup_files'
[18:38:26]   Checking for local host name                    [ Found ]
[18:38:26] Info: Starting test name 'startup_malware'
[18:38:26]   Checking for system startup files               [ Found ]
[18:38:26]   Checking system startup files for malware       [ None found ][/COLOR]

----------------------------

Well, I'm really sorry for my long post...

Again, thanks for the help and attention!

karinaik

---

### Post by bodhi.zazen on 2010-06-14
Linux is not windows and you are best off checking your windows paranoia at the door.

There is noting abnormal in anything you posted, you are not yet familiar enough with linux to know what is normal.

Open 3 more terminals (all at the same time) and run w again :twisted:

I suggest you relax, drink some tea, and read the security sticky.

Your questions on chkrootkit and rkhunter are answered on the man pages and/or google search.

---

### Post by karinaik on 2010-06-14
Thank you very much bodhi.zazen!
I appreciated all the information!

---

### Post by bodhi.zazen on 2010-06-14
> **karinaik said:**
> Thank you very much bodhi.zazen!
I appreciated all the information!

I understand it is overwhelming at first, start by assuming everything is secure and learn what is normal. You are asking all the right questions.

---

