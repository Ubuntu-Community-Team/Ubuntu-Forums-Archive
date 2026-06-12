---
title: "How to remove the blatant Ubuntu PRO advertising during apt-get upgrade"
date: 2022-10-13
forum: Ubuntu, Linux and OS Chat
---

### Post by michael-goldshteyn on 2022-10-13
In /usr/lib/python3/dist-packages/uaclient/messages.py:

grep for 'Try Ubuntu Pro beta', which as of today, 2022-10-13 matches on the following lines:

```
lib/python3/dist-packages/uaclient/messages.py:1014:Try Ubuntu Pro beta with a free personal subscription on up to 5 machines.
lib/python3/dist-packages/uaclient/messages.py:1039:Try Ubuntu Pro beta with a free personal subscription on up to 5 machines.
```

Then just change the assignments for variables SS_LEARN_MORE and TRY_UBUNTU_PRO_BETA to empty strings (i.e., ''):
```
1014:SS_LEARN_MORE = ''
1033:TRY_UBUNTU_PRO_BETA = '' # Note: Line number adjusted as a result of the change at line 1014
```

---

### Post by TheFu on 2022-10-13
Strange colors take away from the main information. Can't tell what is important, what is terminal output, what is comments.

Non-standard fonts are hard to read. Please use the standard font.

This isn't a question and how-to guides belong in a different sub-forum. Hope a moderator will move the thread there.

---

### Post by tea for one on 2022-10-13
More info here [https://www.omgubuntu.co.uk/2022/10/ubuntu-pro-terminal-ad](https://www.omgubuntu.co.uk/2022/10/ubuntu-pro-terminal-ad)

---

### Post by #&amp;thj^% on 2022-10-13
> **tea for one said:**
> More info here [https://www.omgubuntu.co.uk/2022/10/ubuntu-pro-terminal-ad](https://www.omgubuntu.co.uk/2022/10/ubuntu-pro-terminal-ad)

:D That put a smile on my face, Good read. (Joey is a straight shooter ;))

---

### Post by TheFu on 2022-10-13
I don't mind a plug, as long as it doesn't show up after a week or so 
OR doesn't show up when it isn't needed.

Honestly, I'd rather Canonical include 1 "services we offer" application in all their desktop distros say something about that during an interactive install, then just leave us alone.  It would be cool if they showed a "Check out our services or make a donation here" every quarter too.  I just won't want to be nagged or to have automation (of any sort) interfered with.

Constant nagging ... is .... CONSTANT NAGGING.

Any time a message is forced, there should be link to instructions to make it go away for a day, week, month, quarter, year, forever too.

Honestly, for all the good that Canonical has done for me, I'd love to have a way to donate annually to them AND to other F/LOSS projects where I get to control where the money goes.  The idea that I can make the server specifically better would be great ... along with any non-Gnome/non-KDE efforts.  I dislike bloat and figure enough others would fun their efforts.  The timezone, LTS, ssh, rsync, rdiff-backup, lxd, LVM, ZFS, libvirt, virt-manager and fvwm teams could all use some love (i.e. money).  Even $10K would make a huge difference to these teams. they could send a few people to a few conferences, which is a win-win for everyone.

The easiest way to get money from me online is via paypal.

Additionally, I'd like to defund the snap packing team, until they work on local overrides for each constraint. I'm tired of this error on most of my systems for normal user accounts:
```
$ lxc list
Command 'lxc' is available in '/snap/bin/lxc'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
lxc: command not found
```
BTW, if I run 
```
$ /snap/bin/lxc list
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.
```
The error says "not currently supported" - this bug has been reported since 2017, at least.  Some truth would be good.
"will never be supported" would be honest. The offered workaround isn't a workaround in an enterprise with thousands of users on platforms that get shared cross OS.

---

### Post by #&amp;thj^% on 2022-10-13
> **TheFu said:**
> 

Constant nagging ... is .... CONSTANT NAGGING.

Any time a message is forced, there should be link to instructions to make it go away for a day, week, month, quarter, year, forever too.


If I've said it once, I'll say again **Testify!!**
> **TheFu said:**
> 
Honestly, for all the good that Canonical has done for me, I'd love to have a way to donate annually to them AND to other F/LOSS projects where I get to control where the money goes.  The idea that I can make the server specifically better would be great ... along with any non-Gnome/non-KDE efforts.  I dislike bloat and figure enough others would fun their efforts.  The timezone, LTS, ssh, rsync, rdiff-backup, lxd, LVM, ZFS, libvirt, virt-manager and fvwm teams could all use some love (i.e. money).  Even $10K would make a huge difference to these teams. they could send a few people to a few conferences, which is a win-win for everyone.

The easiest way to get money from me online is via paypal.

Additionally, I'd like to defund the snap packing team, until they work on local overrides for each constraint. I'm tired of this error on most of my systems for normal user accounts:
```
$ lxc list
Command 'lxc' is available in '/snap/bin/lxc'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
lxc: command not found
```
BTW, if I run 
```
$ /snap/bin/lxc list
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.
```
The error says "not currently supported" - this bug has been reported since 2017, at least.  Some truth would be good.
"will never be supported" would be honest. The offered workaround isn't a workaround in an enterprise with thousands of users on platforms that get shared cross OS.
I just can't argue plain Good Sense!;)
Well thought out, and nicely worded.

---

### Post by QIII on 2022-10-13
Disclaimer:  The following is my personal opinion and does not reflect the opinion of the Forums Staff.

Terrible, terrible Canonical for telling private users that they are giving away something for free that would otherwise require a paid subscription!  Oh, imagine the profits they will make by giving things away for free!

By the way, Disqus?  Sign up, turn over your privacy and then complain about being given something for free.

There are a lot more things about Canonical to be legitimately bothered about.  Like snaps.  I railed against Unity and was glad to see it get buried.  But even those were not profit scams.  They were just really bad ideas as they are were implemented.

"Ad" just doesn't seem to be at all consistent with an announcement of something free.  I'm not sure how a couple of lines appearing in a terminal is even worth getting one's panties in a wad over.

Really.  Please, please, please point out really stupid stuff Canonical does.  That actually provides feedback about things that can and should be improved.  "I am angry for being offered something for free!" seems a bit melodramatic.

---

### Post by lammert-nijhof on 2022-10-18
I do everything the Ubuntu antagonists ever disapproved off: 

1. I still run _Unity_ as part of Ubuntu 16.04 LTS for my Banking and PayPal functions.
2. I'm using _snaps_ and well the latest stable Firefox and LibreOffice snaps in Ubuntu 16.04.
3. I use _Ubuntu Pro_ for free to extend the life of Ubuntu 16.04 to Apr 2026 :)
4. _I don't run 16.04 on bare metal_, I run it in an encrypted Virtualbox VM :)

---

### Post by Dennis N on 2022-10-19
If you would use "Software Updater" instead of the terminal, you don't get any promotions. It works just as well in my opinion, and also offers to remove the old kernel whenever the kernel version is upgraded.

---

