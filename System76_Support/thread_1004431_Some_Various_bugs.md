---
title: "Some Various bugs"
date: 2008-12-07
forum: System76 Support
---

### Post by eyecreate on 2008-12-07
There have been a few things that have cropped up recently on my new install of 8.10 on my serp4. First of all, every once in awhile, on bootup/login, my laptop will freeze and the capslock and numlock lights will flash. No idea what the signal is supposed to mean, but it sounds like a lower level hardware problem(maybe drivers). Second, The first time I boot my computer up from shutdown, gnome will not load my volume control or multiuser applets. If I log out and back in again, they are there. Login takes alot slower than when I first installed too, and I only have three more programs in sessions.(gnomedo,emapthy,and jungledisk) It would be nice to know if/how to fix these.

---

### Post by Spr0k3t on 2008-12-07
I found a similar issue to what you are experiencing in this thread: [http://ubuntuforums.org/showthread.php?t=994937](http://ubuntuforums.org/showthread.php?t=994937)

> **marcor said:**
> Hi, I had a similar problem on my pamp4i seen this thread [http://ubuntuforums.org/showthread.php?t=972451](http://ubuntuforums.org/showthread.php?t=972451) and this thread for a fix [http://ubuntuforums.org/showthread.php?t=969887](http://ubuntuforums.org/showthread.php?t=969887). It solved the problem for me.

Marco

---

### Post by eyecreate on 2008-12-07
I already have the backports from the main archive in use, but I tried to use the ones on the PPA you listed in the fix, but there are no updates. What do I install/what is different between the PPA and main version of the backports?

---

### Post by thomasaaron on 2008-12-08
The blinking LEDs mean you had a kerenel panic.

Did you install and run your System76 driver? If so, please post the output of...

cat /boot/grub/menu.lst

---

### Post by eyecreate on 2008-12-08
I did install the system76 driver right after my fresh install of 8.10 last month.


Here is the output, and the only part I think I added was the clocksource=jiffies because I had to do this on my old 8.04 partition that died, so I thought I'd keep it there.:
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1830f013-8af3-4341-b93d-5c2395b83528 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1830f013-8af3-4341-b93d-5c2395b83528

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash clocksource=jiffies vga=799

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1830f013-8af3-4341-b93d-5c2395b83528
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1830f013-8af3-4341-b93d-5c2395b83528 ro quiet splash clocksource=jiffies
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1830f013-8af3-4341-b93d-5c2395b83528
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1830f013-8af3-4341-b93d-5c2395b83528 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1830f013-8af3-4341-b93d-5c2395b83528
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by thomasaaron on 2008-12-08
OK. That all looks right.

Please attach the files created on your desktop by these commands...
> cat /var/log/messages >> ~/Desktop/messages.txt
cat /var/log/syslot >> ~/Desktop/syslog.txt
...**immediately after** re-booting after the next freeze.

---

### Post by eyecreate on 2008-12-09
Okay, I will do that next time it happens, but it hasn't happened yet.

---

### Post by thomasaaron on 2008-12-09
OK. 

BTW: In the commands I asked you to run, change "syslot" to "syslog".

---

### Post by eyecreate on 2009-01-17
okay, just wanted to state I haave not had a kernel panic like before anymore and I fixed the speed problem by following a tutorial about using preload. One more thing, though, is it normal for the network manager to sometimes say it's connected but actually not be? My wireless connections sometimes will stop working, despite the fact it shows full strength still. I can fix it by reconnecting, but it seems silly I have to do this sometimes once a day.(or every 8 hours) I'm guessing this is a bug, in which case, should I report it to network manager or is it a driver bug? btew, I'm still using backports as I was told to in another forum post due to other wireless issues in 8.10.(I have a serp4)

---

### Post by thomasaaron on 2009-01-17
I don't recall of hearing of a bug like that. Could it be a bandwidth issue with your router?

Does it happen on other wireless access points?

---

### Post by eyecreate on 2009-01-17
It happens mostly on my university's wireless network, so it could be thier network i guess. I'll have to check next time I use my personal router to see if it happens there too or not, but I don't remember this problem there.

---

### Post by VOLKOV9 on 2009-01-18
I think I have the same problem, which came with upgrading to Ibex: [http://ubuntuforums.org/showthread.php?p=6573253#post6573253](http://ubuntuforums.org/showthread.php?p=6573253#post6573253)

---

### Post by eyecreate on 2009-01-24
okay, after waiting a few days to verify, it seems that it only happens on the university network. I don't know if it makes a difference, but I know they use WPA2 enterprise for connections. Could this be buggy or is it just their network. My laptop seems to disconnect more frequently than others(usually windows based) from the network. Have there been enough bug fixes that de-equipping the backports modules would not cause my other problems to return and maybe could fix the wireless too?


EDIT:Today, some more things have popped up. First, firefox will now start up fullscreen and without any window borders, as if it was the only X window open. I can fix it by pressing F11 to make it really go fullscreen and then hitting it again to make it use window borders. Also, on the wireless issue, it seems my wireless lost it's identity today because it gave me this to look at.
[http://img230.imageshack.us/my.php?image=screenshotgy7.png](http://img230.imageshack.us/my.php?image=screenshotgy7.png)
It seems my wireless needs some love.

EDIT:ignore the firefox thing. It seems by disabling "legacy fullscreen" in compiz settings manager, that it doesn't do it anymore. It's kinda funny because I've had that on the whole time and it only popped up now.

---

### Post by thomasaaron on 2009-01-24
I'm still looking for a fix, but WPA Enterprise has been known to drop connections with a number of wireless cards in Ubuntu.

[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=wpa+intrepid&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=wpa+intrepid&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

[http://www.ubuntugeek.com/ubuntu-hardyintrepid-intel3945-wireless.html](http://www.ubuntugeek.com/ubuntu-hardyintrepid-intel3945-wireless.html)

---

### Post by eyecreate on 2009-01-25
just to let you know, even though it happens less, it does happen on my own personal router, but I don't know how much it has to do with anything because the router is jacked into the school's ethernet/intranet, so it could all be going to a similar place.

---

### Post by thomasaaron on 2009-01-26
Regarding your home router...

The next time your connection drops, post the output of
```
cat /var/log/daemon.log
```
Maybe that will have some useful information.

---

### Post by VOLKOV9 on 2009-01-26
As I mentioned, I'm pretty sure I have the same problem as Eye (including my own version of that network manager screenshot).  Here's mine:

---

### Post by ackey on 2009-01-26
While my wireless manager didn't give me the same bizarre output, I did have problems with my laptop (DarU2, running Gutsy at the time about a year ago) on my university's residential network.  Sometimes it would be connected without knowing it, but often it just couldn't connect (yet another DarU2 in the room could connect).  I blamed my school (they're bad at computers) and moved off campus.  Never saw the problem on any other wireless network.

---

### Post by eyecreate on 2009-01-29
I think this is a good log.


EDIT:This must be the week of logs, my machine has been acting stranger this week including the wireless as mentioned above, but I finally got a kernel panic on startup again, I hope I got the messages quick enough, but the syslog file was WAY huge, like 2.4gb. And that's just text. It was too big to load in gedit to trim properly, so I didn't include it. There was a syslog.0, but there was nothing in it past Jan 31 08:41:19, but the event happened around Jan 31 23:10:00. So I've only attached the first log.


***EDIT2***:Okay, things keep on going downhill. I sometimes have to reboot my computer while it's booting up because it decides to "stop responding" at some point, usually after login.(I think it's related to the network manager, since It has also happened when I change wireless networks) I still wonder if going from backports to regular would fix anything, since, the bugs that made me go backport may be fixed by now. I wish I had the nice compatibility/stability of Hardy that was first on my computer. Well, at least I gota say it's still usable, even if it acts like a little kid with a tantrum now. :D Hope something useful is being brewed. Maybe for good luck I'll upload the automatic system76 log archive I made today.

---

### Post by eyecreate on 2009-03-01
Any new status on this issue?

---

### Post by thomasaaron on 2009-03-02
> Okay, things keep on going downhill. I sometimes have to reboot my computer while it's booting up because it decides to "stop responding" at some point, usually after login.(I think it's related to the network manager, since It has also happened when I change wireless networks)

That doesn't sound like wireless. Looking at your logs reveals this...

> Feb  2 09:17:45 ubuntu -- MARK --
Feb  2 09:37:46 ubuntu -- MARK --
Feb  2 09:43:58 ubuntu sudo: pam_sm_authenticate: Called 
Feb  2 09:43:58 ubuntu sudo: pam_sm_authenticate: username = [eyecreate] 
Feb  2 09:43:58 ubuntu sudo: Error attempting to parse .ecryptfsrc file; rc = [-5]
Feb  2 09:43:58 ubuntu sudo: Unable to read salt value from user's .ecryptfsrc file; using default 
Feb  2 09:43:58 ubuntu sudo: Passphrase key already in keyring 
Feb  2 09:43:58 ubuntu sudo: There is already a key in the user session keyring for the given passphrase. 

...which means that your fingerprint reader configurations have somehow gotten hosed. Try disabling your fingerprint reader.

---

### Post by eyecreate on 2009-03-02
huh, that's interesting, would something like that possible cause a problem like that?

anyways, the fingerprint reader is not in my /etc/pam.d/common-auth file, so is there something else I need to do to disable it?

Also, while the wireless may not be the cause of the kernel panics, I know that there are still issues with the wireless connecting to certain spots. It still likes to sometimes, after about 10 min of use, drop the connection yet not inform you that it has. If you try the select the current wireless spot again, it will reconnect usually in half the time it usually would, skipping requesting ip address(or whatever it does in the first two "bubbles" of the notification icon) as if you really were not disconnected but just "away".

EDIT: oh also, it seems that whenever I let it do a disk check during bootup that it won't let me get to my desktop after i log in and i must restart the computer since it will freeze. It only happens then, idk if it's connected or not.

---

### Post by thomasaaron on 2009-03-02
First, go into Applications > FPrint Project and deactivate anything that might still be active.

Here are instructions for uninstalling the fingerprint reader...
[http://ubuntuforums.org/showthread.php?t=860681&page=5&highlight=uninstall+fingerprint+reader](http://ubuntuforums.org/showthread.php?t=860681&page=5&highlight=uninstall+fingerprint+reader)

Start with Compholio's post dated January 20th, 2009.


Wireless cards can cause kernel panics. However, it isn't usually right after logging in, which is why I suggested the fingerprint reader.

> EDIT: oh also, it seems that whenever I let it do a disk check during bootup that it won't let me get to my desktop after i log in and i must restart the computer since it will freeze. It only happens then, idk if it's connected or not.

Your system really seems to just be inundated with little problems. Have you considered just backing up and doing a fresh install. I hate to recommend them, but occasionally the time necessary for sorting out all of the little issues becomes far more than an install.

---

### Post by thomasaaron on 2009-03-02
Well, after looking back I see that you've actually re-installed recently.

The wireless dropping could be the router dropping you -- perhaps on inactivity? I'll try to go back over this stuff and have another look at your logs tomorrow.

---

### Post by eyecreate on 2009-03-02
alright, i got all the fingerprint stuff off now. It seems interesting that Intrepid has been, I think, the most trouble I've ever had with Ubuntu(minus one event, but I was working with unsupported hardware). I had alot more stability I feel with Hardy, and I hope any little things that have come up will be fixed in Jaunty. 

On the router dropping me, idk if that's it because I've sometimes been dropped while downloading a file or sometimes in the middle of a webpage loading. Also, if I have to enter a security key, it sometimes won't "catch" the first time and will ask again, after which it usually works. Haha, yeah, I guess I have a bunch of little issues, or maybe I'm just a perfectionist. :p Whatever the case, I'm glad you're doing your best to fix them. Hope for good result like my problem with bootup pausing unless a key was pressed, as your fix has permanently fixed it and I've not seen it again.

---

### Post by eyecreate on 2009-03-13
Okay, got another kernel panic I think is of significance. Right before this happened, at about 10:55 ish, I was downloading some ocremix albums through Transmission on the school's WPA2 Enterprise network. It all of a sudden dropped connection(idk if it's important, but the speeds had just reached around 500kb/s. Also, the "dropping" was like I mentioned before where it still said I was connected but with no transfers.). I did what I've normally done if it drops, and I clicked network manager and selected the network again to reconnect. It did reconnect, but after about 30 sec to a min of activity, the computer kernel panicked. As soon as I restarted, I took the daemon log and a few others and I will now attach.

---

### Post by thomasaaron on 2009-03-13
The daemon log is interesting.

It shows that the router is renewing it's connection lease with you about every 20-something minutes. This may account for your loss of connection. It could be that if you are in the middle of a big download when it renews, it just drops you.

In contrast, our router renews our connection lease every 55+ hours. I don't see anything else particularly sinister about your logs, but I'm leaning towards your college's routers are set to keep people from being hooked up to them eternally.

That also might be triggering the kernel panic -- although the panic isn't in the logs.

---

### Post by eyecreate on 2009-03-13
That is quite interesting, and I normally wouldn't doubt it, but how would it be that I'm one of the few who seems to run into constant problems with the network? Some of my friends have Vista on their laptops and they rarely have problems. I'd be interested in knowing what makes their laptops disconnect less.

---

### Post by thomasaaron on 2009-03-13
It could be a network manager bug or a driver bug, which would explain it not affecting Windows machines.
 
The numbers are in your daemon.log. Search for "renew", see how many seconds it says, convert it into minutes, then scroll down that many minutes on the screen.

---

### Post by eyecreate on 2009-03-13
You are right, the school wireless has me down usually for 30 min renew and my personal router for 310 min renew. Would there be a way to not make everything halt when a renew goes on? Maybe I'm asking for the impossible.

---

### Post by thomasaaron on 2009-03-16
Typically a renew doesn't kill your connection. However, I'm wondering if you stumbled upon a new bug with Network Manager or the wireless driver for the Intel Pro Wireless cards.

1. Do people with Windows computers get dropped after a certain amount of time too? (If so, it may be something to talk to the IT person at the school about.

2. You mentioned it happened while you were in the middle of the download. Does it happen if you're NOT downloading?

---

### Post by eyecreate on 2009-03-16
I have not heard from any of those running Vista about their wireless dropping out like mine, they usually stay connected as long as they are in good range.

renewal today in the logs seems to be at about every 15 minutes, but what seems different today is that I haven't noticed any drops like I do sometimes. Maybe it is due to the fact I haven't downloaded anything(large) while connected. I'd have to check more to be sure, but I think it's only noticeable when lots of transfer action is happening.

---

