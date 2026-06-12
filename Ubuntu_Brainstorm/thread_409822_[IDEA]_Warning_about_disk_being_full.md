---
title: "[IDEA]: Warning about disk being full"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-15
**Summary:**
If the disk is full to the point of preventing a user login, Ubuntu (regardless of it being Xubuntu, Kubuntu, Ubuntu, or Edubuntu) should warn the user that files should be deleted or removed before rebooting or logging out.

**Rationale:**
A full disk or full /home partition (if there is one) prevents a user from logging in graphically. It's a similar rationale to *bullet-proof-x*--most desktop users do not want to *have* to use only a terminal to troubleshoot problems. They can always *opt* for a terminal, but they shouldn't be stuck at one.

**Scope and Use Cases:**
This just happened to me, actually! On my laptop, my / partition was relatively small, and I was playing around with installing a lot of packages, to the point where my / partition was almost full. When I rebooted, I got to the GDM login screen okay, but when I tried to log in with *any* user (on *any* window manager or desktop environment), I got the message about my session lasting less than 10 seconds. I was told to use failsafe mode and check my ~/.xsession-errors.

I wasn't able to log into failsafe Gnome, and I got the same message. When I logged into failsafe terminal, I could see the error message indicating there wasn't enough space on "the device."

Since I have a little experience with Ubuntu, I knew to do ```
sudo apt-get clean
``` to get rid of all the extraneous .deb files in /var/cache/apt/archives, but how would a regular end-user know to do that?

Here's another example of a user running into the same problem:
[session lasted less than 10 seconds](http://ubuntuforums.org/showthread.php?t=278222)

**Implementation Plan:**
Just as the power manager will warn you if your battery is running low, something (God, I'd hate to have another applet, but maybe that's what it should be...) should pop up and let you know if you're running dangerously low on disk space, to the point of not being able to log in on next reboot. A simple pop-up.

The next step, of course, would be for the pop-up to give you an easy way to remove unnecessary files by presenting you some easy-click options for freeing up space (Clean out the /tmp folder, Remove installation .deb files from /var/cache/apt/archives, etc.).

**Blueprint**:
[https://blueprints.launchpad.net/ubuntu/+spec/warning-of-disk-being-full](https://blueprints.launchpad.net/ubuntu/+spec/warning-of-disk-being-full)

---

### Post by 23meg on 2007-04-15
I've seen plenty of people being mysteriously unable to log in because of this, and it's hard to pinpoint the cause from the symptoms. 

Notification popups for low disk space are already implemented in gnome-volume-manager. However, if the user ignores the warning (and users do ignore warnings, don't they?), maybe  on the basis that they don't *need* disk space, since they won't be saving anything to that disk for the time being, the lockdown will still occur, and it shouldn't. It may be a good idea to reserve a tiny bit of disk space for this purpose only.

---

### Post by .t. on 2007-04-15
Indeed. The system should not *need* disk space purely to login. In theory, temp files should be created in /tmp (which should be a tmpfs in RAM). In practice, this does not always happen, and when a user is out of space, there is no room for the required temp files.

---

### Post by 23meg on 2007-04-16
The bug is confirmed [in Launchpad]("https://bugs.launchpad.net/gdm/+bug/35217") and [upstream]("http://bugzilla.gnome.org/show_bug.cgi?id=144473"). A few fix implementations are suggested in the comments of both.

---

### Post by ubuntu_demon on 2007-05-01
This spec :
[https://blueprints.launchpad.net/ubuntu/+spec/warning-of-disk-being-full](https://blueprints.launchpad.net/ubuntu/+spec/warning-of-disk-being-full)
A relevant spec :
[https://blueprints.launchpad.net/ubuntu/+spec/make-free-space-wizard](https://blueprints.launchpad.net/ubuntu/+spec/make-free-space-wizard)

IMHO we should talk to Sivan Greenberg whether hooking it up to his make-free-space-wizard makes sense.

---

### Post by Lucifiel on 2007-05-01
I really like this idea. However, may I suggest a warning when the hard disk has 10% to 20% or even 30% free space left. Or if the free space on the hard disk / partition has less than ____ mb of free space. Perhaps, the warning will repeat once every 20 minutes or perhaps a notification window should pop up and not go away until the problem has been dealt with.

Also, maybe there could be the option of ignoring or disabling this warning.

---

### Post by lyceum on 2007-05-02
> **Lucifiel said:**
> I really like this idea. However, may I suggest a warning when the hard disk has 10% to 20% or even 30% free space left. Or if the free space on the hard disk / partition has less than ____ mb of free space. Perhaps, the warning will repeat once every 20 minutes or perhaps a notification window should pop up and not go away until the problem has been dealt with.

Also, maybe there could be the option of ignoring or disabling this warning.

I like this idea also.

---

### Post by Lucifiel on 2007-05-03
Also, to further carry on the idea in my post, perhaps the popup warning window could also be minimised to an icon in the taskbar.

---

### Post by 23meg on 2007-05-03
Am I missing something? Isn't the disk space warning already implemented since Dapper?

---

### Post by Lucifiel on 2007-05-03
> **23meg said:**
> Am I missing something? Isn't the disk space warning already implemented since Dapper?

Hmmm... is it? I never got this warning, even when my Ubuntu feisty partition hit a dangerous low of 100 to 200 mb free. 

That was when I started to get loads of errors even trying to perform simple operations like copying and pasting files, running commands, etc. I was absolutely fortunate I didn't log out of Ubuntu then, for I might not have been able to load it for a while.

---

### Post by 23meg on 2007-05-03
100MB isn't exactly a dangerous low (and certainly not so low as to trigger the GDM bug), and depending on what percentage of your disk it is, you may not have got the warning.

---

### Post by Lucifiel on 2007-05-03
> **23meg said:**
> 100MB isn't exactly a dangerous low (and certainly not so low as to trigger the GDM bug), and depending on what percentage of your disk it is, you may not have got the warning.

Might be true but it is an issue if you can't even carry out simple operations in Ubuntu and if various programs start to fail.

---

### Post by 23meg on 2007-05-03
I've never heard of someone being unable to carry out simple operations due to nothing other than having 100 or 200MB of disk space left. It's probably another unrelated problem.

---

### Post by Lucifiel on 2007-05-03
> **23meg said:**
> I've never heard of someone being unable to carry out simple operations due to nothing other than having 100 or 200MB of disk space left. It's probably another unrelated problem.

Hmmm... perhaps so. Then again, even certain simple applications or even operations could make use anywhere between 20 mb to 50 mb or more. *sighs* Computer issues can be so difficult to decipher, huh?

---

### Post by tonyr1988 on 2007-05-03
I can confirm that this is already implemented (warning you of low disk space); however, it wasn't on my boot partition, so I never experienced that problem. Maybe editing the message so that it mentions something about the login problem would make it seem more urgent?

---

### Post by 23meg on 2007-05-03
[QUOTE=tonyr1988]Maybe editing the message so that it mentions something about the login problem would make it seem more urgent?[/QUOTE]

The login problem shouldn't exist in the first place. To the uninitiated user, the logic of it is that disk space is about storing things, not about an essential function such as logging in to your account, and rightly so; if they don't need to store things, they can always dismiss a warning, no matter what its content is.

---

### Post by 23meg on 2007-06-03
This is being worked on for Gutsy.

[https://blueprints.launchpad.net/ubuntu/+spec/boot-login-with-full-filesystem](https://blueprints.launchpad.net/ubuntu/+spec/boot-login-with-full-filesystem)

---

### Post by aysiu on 2007-06-03
Great to hear.

---

### Post by northicert on 2008-10-30
This is not a reply. It's just a learning experience the hard way.  The last time I did an update I got a rude awakening. I knew I was running on the edge of my hard drive being maxed but that was the last thing on my mind when I did a restart as instructed. It booted ok and I logged in ok. The power down icon came up but no wireless icon. Clicking on the icon to get a restart locked me up. I rebooted and tried something else. I was lucky I could still get to my files and saw a zero free on the drive. I know what I need to do but I need to check out a fool proof way to get there. (bigger drive)

---

### Post by rickshawalla on 2009-01-11
I have this problem from today. Session lasted only 10 seconds, no spce left on device, couldn't use Failsafe Gnome.
Tried the sudo apt-get clean command line, which didn't help either.
So how do I log in?

---

### Post by KIAaze on 2009-01-14
> **rickshawalla said:**
> I have this problem from today. Session lasted only 10 seconds, no spce left on device, couldn't use Failsafe Gnome.
Tried the sudo apt-get clean command line, which didn't help either.
So how do I log in?

_Solution 1:_
Remove big packages
```
sudo apt-get remove PACKAGE
```

You can use this script to list packages by installed size:
[http://bazaar.launchpad.net/~scripters/scripting/trunk/annotate/head%3A/utility/list_installed_packages_by_size.sh](http://bazaar.launchpad.net/~scripters/scripting/trunk/annotate/head%3A/utility/list_installed_packages_by_size.sh)

To download it by command-line:
```
wget http://bazaar.launchpad.net/%7Escripters/scripting/trunk/download/head%3A/list_installed_packa-20081209101326-lofy0bqx8ov4yfjs-1/list_installed_packages_by_size.sh

```

Or you can use the following command directly:
```
dpkg-query -W --showformat='${Installed-Size;10}\t${Package}\n' | sort -k1,1n 

```

_Solution 2:_
Remove personal big files or move them to an external USB stick.

Useful commands:
```
rm ->remove file
ls ->list files
du -sh DIR ->display size of a directory
df -h ->show disk space info
mount -a ->should mount a USB stick
cd ->Change directory

```

Be careful because you are running as root here!

If you are not very experienced with the command line, it might be safer to boot from a live-CD to remove data.

---

### Post by kivuyo on 2009-01-14
my self i cant install any package when i try to install it tell me there no space ,i cant open terminal ,even to play music,
if i try to play music using MPlayer it give  me this error [AO_ALSA]unable to set hw-parameter:input/ouput error ,please someone to help me on this
regards 
kivuyo

---

### Post by smartboyathome on 2009-01-14
> **kivuyo said:**
> my self i cant install any package when i try to install it tell me there no space ,i cant open terminal ,even to play music,
if i try to play music using MPlayer it give  me this error [AO_ALSA]unable to set hw-parameter:input/ouput error ,please someone to help me on this
regards 
kivuyo

Boot into the rescue mode when grub pops up (you may have to hit escape if Ubuntu is your only OS). Then you should be able to do the suggestions above.

---

