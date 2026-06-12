---
title: "[Bug Report Check] update-manager"
date: 2011-11-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-30
Latest report in the Bug Sticky is at [http://ubuntuforums.org/showpost.php?p=11502872&postcount=6](http://ubuntuforums.org/showpost.php?p=11502872&postcount=6)

It mentions update-manager not working at all, with no Launchpad report to concur to that.
I feel like it works, although I have recently discussed (here at the forum) how it seems to show some different suggestions (for me) in comparison to aptitude or synaptic. I would expect those differences from aptitude suggestions, of course, but not from synaptic.

However, the affirmation that it doesn't work at all is wrong IMO.

So, what are your opinions? Keep, change, delete?

---

### Post by mc4man on 2011-12-01
Last I checked, (a few hr.s ago or so), it works but only once per session (at least if you r. click > deselect all, then apply 1 update, close & reopen.
Will recheck after I see if that lucid > direct to PP works

may be related to this bug, some similarities
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745)

---

### Post by ventrical on 2011-12-01
> **effenberg0x0 said:**
> Latest report in the Bug Sticky is at [http://ubuntuforums.org/showpost.php?p=11502872&postcount=6](http://ubuntuforums.org/showpost.php?p=11502872&postcount=6)

It mentions update-manager not working at all, with no Launchpad report to concur to that.
I feel like it works, although I have recently discussed (here at the forum) how it seems to show some different suggestions (for me) in comparison to aptitude or synaptic. I would expect those differences from aptitude suggestions, of course, but not from synaptic.

However, the affirmation that it doesn't work at all is wrong IMO.

So, what are your opinions? Keep, change, delete?

It's in pretty rough shape on this fresh install effenberg. BTW this is a 64bit install.

Try to have some patience with my attachment .. I think it might help some have a better understanding of the bug.

[http://www.youtube.com/watch?v=24QCmW8tBFA](http://www.youtube.com/watch?v=24QCmW8tBFA)

Anyways .. to make a long story short, it just hangs when you try to install the updates.

---

### Post by jppr on 2011-12-01
[https://launchpad.net/ubuntu/precise/+source/update-manager/1:0.154.6](https://launchpad.net/ubuntu/precise/+source/update-manager/1:0.154.6)

---

### Post by ventrical on 2011-12-01
Checked another Precise install on a tower. Went through install routine then reported that last updated 5 hours ago and hung, won't close *wow* and just as I typed this I got this:

and got redirected to this bug report: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/616721](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/616721)

---

### Post by effenberg0x0 on 2011-12-01
Weird... it worked for me, normally, on a pp iso VM 64bit. I'll be able to put together a couple pp clones tomorrow morning and try to get some debug log from it.

---

### Post by ventrical on 2011-12-01
> **effenberg0x0 said:**
> Weird... it worked for me, normally, on a pp iso VM 64bit. I'll be able to put together a couple pp clones tomorrow morning and try to get some debug log from it.


I'll try my two nVidia machines. Above results are both from ATi cards. I know there is a kernel problem  with 3.2.n-n & certain ATi drivers.. who knows ?

---

### Post by ventrical on 2011-12-01
Crashed on both nVidia  machines also. A this stage of the game, UM is as usless as an ant larvae trying to defend it's hill against a charging pangolin ! :)

---

### Post by ventrical on 2011-12-01
The fix is in with most recent update.

 Nice work !

---

### Post by ventrical on 2011-12-01
But I get this on another machine while trying to use apt-get:

dale@dale-desktop:~$ sudo apt-get upgrade
Reading package lists... Error!
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/multiverse i386 Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages)
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
dale@dale-desktop:~$

---

### Post by ronacc on 2011-12-01
just updated my  12.04 64bit install with update-manager , all OK .

---

### Post by mc4man on 2011-12-01
> **ronacc said:**
> just updated my  12.04 64bit install with update-manager , all OK .

Does that include trying to use it more than once per session?

---

### Post by effenberg0x0 on 2011-12-01
I have also succeeded using it (more than a time). I guess we'll have to be more specific on what we did, so we can find what triggers the fail behavior.

Maybe there's some sync issue between servers? Let's compare our sources.
```

$ **grep -v '^#' /etc/apt/sources.list**
deb http://archive.ubuntu.com/ubuntu precise main restricted universe
deb-src http://archive.ubuntu.com/ubuntu precise main restricted universe
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

deb http://archive.ubuntu.com/ubuntu oneiric main restricted universe
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted universe
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/ubuntu oneiric partner
[11:58 PM][ahsl:AL-DESK:~/dev/glue]
$ 
```(Yes, I still have some active oneiric sources, I know)

---

### Post by ronacc on 2011-12-01
> **mc4man said:**
> Does that include trying to use it more than once per session?

yes , just completed my second run . Nothing to update this time but it d/l'd the package lists OK .

---

### Post by mc4man on 2011-12-01
Maybe 32bit?
Will have to try a 64 bit install

This is a new install from latest image (11/29), it only work once per session, then nothing. No crash,xsession error, nothing but a spinninug cursor

Method here would be r.click > deselect all > pick an update which generally works, then close, open & then no more updates can be applied, which is basically as the 'bug thread' saw.

Quite similar to SC, only 1 action per session, except SC does crash. (confirmed

---

### Post by effenberg0x0 on 2011-12-01
I finally managed to make it go into a lot of time in the "spinning" mouse cursor after pressing check. After about 10 minutes, I got some probably useful output:
[01:56 AM][ahsl:AL-DESK:~/dev/glue]
```
$ sudo update-manager
gpg: /tmp/tmpPTzB4u/trustdb.gpg: trustdb created
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 472, in _inline_callbacks
    result = gen.throw(result.type, result.value, result.traceback)
  File "/usr/lib/python2.7/dist-packages/UpdateManager/backend/InstallBackendAptdaemon.py", line 33, in update
    trans = yield self.client.update_cache(defer=True)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply **(timeout by message bus)**
gpg: /tmp/tmpItk7bm/trustdb.gpg: trustdb created
```

---

### Post by mc4man on 2011-12-01
A new 64 bit - same deal, once per session, (if that

> dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

That's the same as the most common current S-C crash

Edit: S-C
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745)

---

### Post by ronacc on 2011-12-01
yes SC crashed for me too but update-manager still OK , did a 3rd run and got a few more updates . getting a few random other crashes though .

---

### Post by ronacc on 2011-12-01
maybe after a reboot I'll get the UM crashes , I'll try tomorrow morning , already shut that sys down for the night.

---

### Post by sammiev on 2011-12-01
No crashes yet using update-manager over the last few days and there has been a lot of updates. Just took the header updates and did a fresh cold boot with no issues.

---

### Post by mc4man on 2011-12-01
Well U-M does do what it does best here - quick,easy acces to changelogs & active links to bug reports.

Is curious how it only affects some, at least those with fairly current PP installs from image

(And yet again I see FF still  will not do spell checking by default until one explicitly picks a lang

---

### Post by WarriorIng64 on 2011-12-02
Can't get the Update Manager nor Software Center to do any package changes on my 12.04 machine. The former locks up for a few minutes when I click the Install Updates button, then shows it accomplished absolutely nothing beyond wasting my time. No Apport windows or anything.

The Software Center does something similar, except it doesn't freeze the whole program and I can still get out of it.

I had these issues in a pre-Alpha daily build, and just got a fresh Alpha 1 iso tonight to reinstall and see if it fixed anything. Well, the only change I see is Unity's defaulting back to the standard GNOME theme and is missing several launcher icons, but the aforementioned problems were not fixed.

sudo apt-get update/upgrade still work, though.

Some bugs I filed, if anyone's interested:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/898807](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/898807)
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/897984](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/897984)

---

### Post by cariboo on 2011-12-02
@WarriorIng64, could you add you bugs to the [Bug thread]("http://ubuntuforums.org/showthread.php?t=1888420"), using the template in in the first post?

---

### Post by P-I H on 2011-12-02
Has anybody else problems with software-center. I am not able to install any application and I get these messages when I start software-center from the terminal

```
p-i@pi-GA-MA770-UD3-precise-alpha1:~$ software-center
2011-12-02 08:13:45,679 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 13 20
2011-12-02 08:13:46,371 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-12-02 08:13:46,485 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 586, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 148, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 143, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 586, in msg_reply_handler
    reply_handler(*message.get_args_list(**get_args_opts))
  File "/usr/share/software-center/softwarecenter/backend/installbackend_impl/aptd.py", line 148, in _register_active_transactions_watch
    current, queued = apt_daemon.GetActiveTransactions()
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 143, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 630, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
2011-12-02 08:14:37,720 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
Segmentation fault (core dumped)
p-i@pi-GA-MA770-UD3-precise-alpha1:~$
```

---

### Post by VinDSL on 2011-12-02
> **effenberg0x0 said:**
> I have also succeeded using it (more than a time). I guess we'll have to be more specific on what we did, so we can find what triggers the fail behavior.

Let's compare our sources.
```

$ **grep -v '^#' /etc/apt/sources.list**
deb http://archive.ubuntu.com/ubuntu precise main restricted universe
deb-src http://archive.ubuntu.com/ubuntu precise main restricted universe
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

deb http://archive.ubuntu.com/ubuntu oneiric main restricted universe
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted universe
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/ubuntu oneiric partner
[11:58 PM][ahsl:AL-DESK:~/dev/glue]
$ 
```
Heh!  Show n' tell.  :D

Here's mine...

```
vindsl@Zuul:~$ grep -v '^#' /etc/apt/sources.list

deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
vindsl@Zuul:~$ 

```

---

### Post by mc4man on 2011-12-02
Well, S-C (5.1.2.1) is fairly broken, S-C (5.1.3)/software-center-aptdaemon-plugins 0.1.1 is completely so.

I'm sure it'll get squared away sooner than later, use synaptic if need be

---

### Post by teh603 on 2011-12-02
Honestly, I've never been able to install stuff thru it. Just stick to Synaptic or its equivalent.

---

### Post by effenberg0x0 on 2011-12-02
Could it be that, for some reason, some of us are running different version of update-manager?
$ update-manager --version
update-manager: version 0.154.6

---

### Post by ronacc on 2011-12-02
did my morning updates , update-manager still OK here , version 0.154.6  .

---

### Post by mc4man on 2011-12-02
In works here today, sorta. (new install,  11/29 image updated thru early this morning on the ubuntu session

So there were 25 updates now, cups, G-S-D, ect. (the G-S-D one should prove useful to GS users

On fresh boot did one package ok, then close, re-open U-M, pick another, it just cursor spins. After about 3 min or so the cursor spin stops, package(s) not updated

Re-clicking on 'Install updates' & it then does so. Process repeats when picking another package to install

---

### Post by mc4man on 2011-12-02
> **ronacc said:**
> did my morning updates , update-manager still OK here , version 0.154.6  .

Figuring you're using GS, just tried there & UM works fine.

---

### Post by ronacc on 2011-12-02
yes you are right I am using GS , I am one of those "unity haters" it only lasts on first boot long enough to install GS .

---

### Post by mc4man on 2011-12-02
The current issue when opening SC now has a fix committed. Whether when  released SC will work or revert to previous failure remains to be seen

[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/898756](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/898756)

---

### Post by effenberg0x0 on 2011-12-02
This thread and [http://ubuntuforums.org/showthread.php?t=1889783](http://ubuntuforums.org/showthread.php?t=1889783) (Software Center) can be joined together. It's same issue / fix.

I was looking at it for the past hour or so. I know they are updating aptdaemon, and they probably know what they're doing. I just found it weird because I can normally communicate via dbus with org.debian.apt (aptd). So I thought python-apt* would be the source of the problem (that's were I see an exception raised here - it seems to fail to communicate with apt via dbus).

---

### Post by cariboo on 2011-12-02
merged two threads on the same subject.

---

### Post by drs305 on 2011-12-02
I've just updated all but a witheld Software Center update but UM still appears broken. Just hangs until I use killall to close it.

---

### Post by VinDSL on 2011-12-03
> **drs305 said:**
> I've just updated all but a witheld Software Center update but UM still appears broken. Just hangs until I use killall to close it.
Interesting!

I haven't used Update Mangler in a couple of years, but...

I thought I would open UM, just to see what happens.

Works fine!


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-3-dec-2011-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-dec-2011-1.png")[/INDENT]


```
vindsl@Zuul:~$ update-manager --version
update-manager: version 0.154.6
vindsl@Zuul:~$ 

```

Maybe it's a 64-bit thing?!?!?!?

---

### Post by drs305 on 2011-12-03
> **VinDSL said:**
> 
```
vindsl@Zuul:~$ update-manager --version
update-manager: version 0.154.6
vindsl@Zuul:~$ 

```

Maybe it's a 64-bit thing?!?!?!?

I have the same version, but I am using 64-bit. Fresh boot, but didn't even work the first time I ran it this morning.

Software Center version: 5.1.2.1

Added:
It's a bigger problem though. I'm also unable to change repositories using Synaptic, Software Center or Software Sources...

---

### Post by JRV on 2011-12-03
I am using 64 bit.

When I try to run Software Center the window opens but never fills in.
Apport opens and says it is sending the bug report then it says it can't find an internet connection.  (There is nothing wrong with my internet connection.)

Is Software center broken, or did I break it?

---

### Post by mc4man on 2011-12-03
> **JRV said:**
> I am using 64 bit.

When I try to run Software Center the window opens but never fills in.
Apport opens and says it is sending the bug report then it says it can't find an internet connection.  (There is nothing wrong with my internet connection.)

Is Software center broken, or did I break it?
S-C is broken, twice over

First here - 
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/849745)

Then it & aptdaemon upgraded & it broke here
[https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/898756](https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/898756)

The latter should get a 'fix released' next week, hopefully then it will work correctly & make the former bug moot

---

### Post by VinDSL on 2011-12-03
> **drs305 said:**
> I have the same version, but I am using 64-bit. Fresh boot, but didn't even work the first time I ran it this morning.

Software Center version: 5.1.2.1

Added:
It's a bigger problem though. **[COLOR="DarkRed"]I'm also unable to change repositories using Synaptic[/COLOR]**, Software Center or Software Sources...

Hrm...

I wondered about that.  I thought it was just me - like I got sloppy, and clicked the wrong key, or something.

The other morning (before the first pot of coffee), I tried to edit my sources via Synaptic, and it handed me a flaming bag of dog feces.

I put out the fire by manually rebuilding my software sources from cli.

Glad you said something...  ;)

> **mc4man said:**
> S-C is broken, twice over
I should have expounded, but was too tired to type, last night...

Update Mangler is working for me, but Ubu Software Center is janky!

USC starts up, looks pretty, et cetera.  You can list all your recent updates, blah, blah, blah.

USC just won't install/remove anything.  LoL!  :D

---

### Post by effenberg0x0 on 2011-12-03
When you guys launch update-manager / Software-Center via console to see some debug messages, you get a timeout or other exception at python-apt links right?

---

### Post by ventrical on 2011-12-03
> **VinDSL said:**
> Hrm...

I wondered about that.  I thought it was just me - like I got sloppy, and clicked the wrong key, or something.

The other morning (before the first pot of coffee), I tried to edit my sources via Synaptic, and it handed me a flaming bag of dog feces.

Yur somthing else Vin :) ahahah aha

---

### Post by ventrical on 2011-12-03
> **effenberg0x0 said:**
> When you guys launch update-manager / Software-Center via console to see some debug messages, you get a timeout or other exception at python-apt links right?

On all my installs the SC just won't work when I click the <install> button.


 Also , it seems now to be interfected with the <Dark fader of Doom> as was (and still is with Lucid)! And the Fader of Doom happens also with synaptic. This install is from the alpha disk .. fresh - no ppas.

---

### Post by WarriorIng64 on 2011-12-04
Is it a bug if certain parts of Unity are excruciatingly slow to work with? For example, Alt+Tab is very slow when I use it, particularly when cycling between large numbers of icons, and reordering icons in the launcher seems to take forever (roughly 5 seconds minimum to swap the positions of two adjacent icons, for example). Windows also sometimes like lagging behind my cursor when I drag them.

I also noticed these problems to a lesser extent with my 11.10 partition on my same machine (a desktop using the Nouveau driver with integrated NVIDIA graphics). However, GNOME Shell on 11.10 showed almost no lag when I tested it; haven't tried it on 12.04 yet.

---

### Post by WarriorIng64 on 2011-12-04
Actually, just logged out and tried GNOME Shell with Nouveau on 12.04...it seems even faster than it was on 11.10. No lag whatsoever (except some slight lag in the Applications screen showing all apps).

---

### Post by effenberg0x0 on 2011-12-04
I would say it probably is. I don't think anyone would develop GUI software with the goal of making the performance bad but only at certain parts of it.






I'm dropping u+1 ...

---

### Post by ventrical on 2011-12-04
> **effenberg0x0 said:**
> I would say it probably is. I don't think anyone would develop GUI software with the goal of making the performance bad but only at certain parts of it.






I'm dropping u+1 ...

??

Why.

---

### Post by effenberg0x0 on 2011-12-04
See PM

---

### Post by JRV on 2011-12-04
When I look at the bug reports in launchpad I see 1086 bug reports for update-manager.  If I file a bug report am I helping, or just adding to the clutter.

---

### Post by jerrylamos on 2011-12-04
update-manager has blown too many installations for me.  Never run it.  Plus when I'm doing something I want to do update manager says "out of the way!  Pay attention to me" huge drop down window.

When I want to, example in development every day, I run an exec:

#!/bin/bash
sudo aptitude update
sudo aptitude safe-upgrade

Sometimes something doesn't install so if I'm sure I do a
 
sudo aptitude full-upgrade

Oh, another thing that has absolutely blown me out of the water is

sudo apt-get dist-upgrade

That's killed installs too.  apt-get is quite happy to install incompatible packages as far as I can tell.

Jerry

---

