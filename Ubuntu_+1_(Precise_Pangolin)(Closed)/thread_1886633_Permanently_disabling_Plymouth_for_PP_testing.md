---
title: "Permanently disabling Plymouth for PP testing?"
date: 2011-11-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-25
I find it almost mandatory for us testers to disable Plymouth. We need to see boot messages. It seems there's no way to remove it without breaking deps. Disabling it via renaming its init/conf is not bulletproof: configs reset on update, exactly when we need to look at boot the most... The removal of quiet/splash from grub defaults still gives me a corrupted pink screen. Do you know of a better / proper way to do it?

---

### Post by philinux on 2011-11-25
> **effenberg0x0 said:**
> I find it almost mandatory for us testers to disable Plymouth. We need to see boot messages. It seems there's no way to remove it without breaking deps. Disabling it via renaming its init/conf is not bulletproof: configs reset on update, exactly when we need to look at boot the most... The removal of quiet/splash from grub defaults still gives me a corrupted pink screen. Do you know of a better / proper way to do it?

Ditto.

I inserted "no plymouth" instead of "quiet splash".

This stops plymouth splash, i.e. the progress dots, and I get some text and all text on restart.

I think the pink screen is coming maybe from grub :confused:.

Or is it a vt.handoff  setting?

---

### Post by effenberg0x0 on 2011-11-25
> **philinux said:**
> Ditto.

I inserted "no plymouth" instead of "quiet splash".

This stops plymouth splash, i.e. the progress dots, and I get some text and all text on restart.

I think the pink screen is coming maybe from grub :confused:.

Hi Phil, 
Thanks for the tip on "no plymouth", I didn't knew this one.
About PSOD from grub: Not sure, as I have it set for console, no vga.
I'll have a look into grub.

---

### Post by ventrical on 2011-11-25
I had always thought that the verbose boot messages were inserted into a boot.log file during boot up, even n the event of an error. ?

 For example - A Dell dimension desktop that I just fried would store Fan failure! etc .. in the CMOS -so  Precise(Ubuntu) does not log bootup errors ?

---

### Post by ventrical on 2011-11-25
> **philinux said:**
> Ditto.

I inserted "no plymouth" instead of "quiet splash".

This stops plymouth splash, i.e. the progress dots, and I get some text and all text on restart.

I think the pink screen is coming maybe from grub :confused:.

Or is it soe vt.handoff  setting?


What file  is it that has to be edited?

thanks

---

### Post by effenberg0x0 on 2011-11-25
> **ventrical said:**
> I had always thought that the verbose boot messages were inserted into a boot.log file during boot up, even n the event of an error. ?

 For example - A Dell dimension desktop that I just fried would store Fan failure! etc .. in the CMOS -so  Precise(Ubuntu) does not log bootup errors ?

It does. But why would I search/read logs at every boot if I saw no lead to it during boot?
Another thing you don't see in logs is if some process is taking longer than usual. Unless you engage into serious and continuous profiling of every boot, these visual leads are important for me.

Also, on PSOD crash: How am I gonna decide if I should boot to normal mode in previous kernel, edit grub parameters, boot to recovery, unplug hardware, etc if I don't know what crashed?

---

### Post by effenberg0x0 on 2011-11-25
> **ventrical said:**
> What file  is it that has to be edited?

thanks

@ventrical /etc/default/grub

@phil I disabled vt handoff to vt7 but still no luck... I'm gonna have a read on grub docs, this is too weird. I'm obviously missing something.

---

### Post by zika on 2011-11-25
Most effective way of stopping Plymouth without uninstalling it or using boot switches I found is
```
:~$ ls /etc/init/plymouth*.override
/etc/init/plymouth-log.override     /etc/init/plymouth-stop.override
/etc/init/plymouth.override         /etc/init/plymouth-upstart-bridge.override
/etc/init/plymouth-splash.override
:~$ cat /etc/init/plymouth.override 
manual
```Leave *.conf files unchanged...
```
:~$ ls /etc/init/plymouth*.conf
/etc/init/plymouth.conf         /etc/init/plymouth-stop.conf
/etc/init/plymouth-log.conf     /etc/init/plymouth-upstart-bridge.conf
/etc/init/plymouth-splash.conf
```Override files do not get changed with update...
Override+manual trick works for (almost) all services... Great trick that was introduced...

To make it clear: For any service You want not to start automatically, just put &#8222;**manual**&#8220; (without quotes) line into **/etc/init/_service_You_want.override** and start the service, if/when You want to with **sudo start _service_You_want** start ...

---

### Post by zika on 2011-11-25
BTW: the switch You mentioned, is it:

&#8220;no plymouth&#8220;
or
&#8222;noplymouth&#8220;
or
&#8222;no_plymouth&#8220;
or
&#8222;no-plymouth&#8220;...?

---

### Post by ventrical on 2011-11-25
> **effenberg0x0 said:**
> It does. But why would I search/read logs at every boot if I saw no lead to it during boot?
Another thing you don't see in logs is if some process is taking longer than usual. Unless you engage into serious and continuous profiling of every boot, these visual leads are important for me.

Also, on PSOD crash: How am I gonna decide if I should boot to normal mode in previous kernel, edit grub parameters, boot to recovery, unplug hardware, etc if I don't know what crashed?


Sounds reasonable enough for beta testers :)

---

### Post by ventrical on 2011-11-25
> **zika said:**
> Most effective way of stopping Plymouth without uninstalling it or using boot switches I found is
```
:~$ ls /etc/init/plymouth*.override
/etc/init/plymouth-log.override     /etc/init/plymouth-stop.override
/etc/init/plymouth.override         /etc/init/plymouth-upstart-bridge.override
/etc/init/plymouth-splash.override
:~$ cat /etc/init/plymouth.override 
manual
```Leave *.conf files unchanged...
```
:~$ ls /etc/init/plymouth*.conf
/etc/init/plymouth.conf         /etc/init/plymouth-stop.conf
/etc/init/plymouth-log.conf     /etc/init/plymouth-upstart-bridge.conf
/etc/init/plymouth-splash.conf
```Override files do not get changed with update...
Override+manual trick works for (almost) all services... Great trick that was introduced...

To make it clear: For any service You want not to start automatically, just put „manual“ line into /etc/init/_service_You_want.override and start the service, if/when You want to...


@zika,

 Thanks ... but .. precisely, how to we get back (restore)from that or can we?

:)

---

### Post by zika on 2011-11-25
> **ventrical said:**
> @zika,

 Thanks ... but .. precisely, how to we get back (restore)from that or can we?

:)
Just erase .override files...
Or manual-u start the service.
I've added that to my post above...
I've not seen easier way of controlling such things for a quite some time, if ever...

---

### Post by philinux on 2011-11-25
I think we need Plymouth to start or will fsck not work automatically etc etc.

I can't find it now but I seem to remember someone suggesting renaming the theme file it uses. It then defaults to show text. But I think the pink screen which masks the boot messages is grub related.

---

### Post by zika on 2011-11-25
> **philinux said:**
> I think we need Plymouth to start or will fsck not work automatically etc etc.

I can't find it now but I seem to remember someone suggesting renaming the theme file it uses. It then defaults to show text. But I think the pink screen which masks the boot messages is grub related.Fsck works but does not show its progress...
I do not have Plymouth active for a year now, I think, and have not ever regretted not having it active...
(OK, I have even lightdm override-ed, using startx and such stuff, so I would not be  a right person to give advices... ;) But, here, this &#8222;trick&#8220;, surely, works...)

---

### Post by effenberg0x0 on 2011-11-25
> **zika said:**
> 
To make it clear: For any service You want not to start automatically, just put „**manual**“ (without quotes) line into **/etc/init/_service_You_want.override** and start the service, if/when You want to with **sudo start _service_You_want** start ...

That is one great tip Zika, thanks! I new it had a new/smart way to be done, but had never tried it, forgot to search about it, was going hardcore (renaming inits, echoing > inits contents to nop, etc - not really too smart).

---

### Post by effenberg0x0 on 2011-11-25
I'm not experienced with other boot-logo things, but I can imagine other distro's may be using something else. Do any of you know of such alternatives and has tried it on PP? I have decided to ditch Plymouth in our future implementations at work, but I need to find out, test and certify some viable alternative. Any tip?

<rant>
As far as I can guess, Plymouth catches kernel printk() to buffer in interrupt and then purges to log on exit? Isn't that a little too much? I mean, if the thing was booting to it's own kernel and kexec'ing into Ubuntu kernel or putting Ubuntu as a whole into a VM would it also be OK, just for a logo? There must be lighter / less compromising ways to achieve the same goal. 
</rant>

**EDIT:** Bootsplash, Xsplash, Usplash and splashy seem to be dead.
**EDIT 2:** This is what I'll test: [http://fbsplash.alanhaggai.org/](http://fbsplash.alanhaggai.org/)

---

### Post by cariboo on 2011-11-25
I'm severely disappointed, as I don't have any of the problems most of you are referring to, I'm using nvidia-current (285.05.09) from the repositories and Plymouth works the way it is supposed to here. For graphics hardware, I'm running a BFG GeForce 210 (218GT).

---

### Post by effenberg0x0 on 2011-11-25
> **cariboo907 said:**
> I'm severely disappointed, as I don't have any of the problems most of you are referring to, I'm using nvidia-current (285.05.09) from the repositories and Plymouth works the way it is supposed to here. For graphics hardware, I'm running a BFG GeForce 210 (218GT).

Don't be, my friend :) One day, one you least expect it, it will break on you :)

Good news: Since there is no man or documentation online for Plymouth anywhere (at least I couldn't find it easily), I had a quick look at it's sources and found some routines for reading/interpreting the Kernel Command Line. I think I found out something that works perfectly:

**Remove**: "quiet", "splash" and *"vt*.handoff=7"
**Add: **plymout:splash=verbose

First two tests worked like a charm for boot, shutdown. PSOD is entirely gone. 
I'm looking into other options. There are txt options, no FB, password protection, as well as theming, etc. 

If it's not asking too much, would you people please give a try for these parameters too? Just add them temporarily via option "e" in grub boot.

**Idea:** Theme it to be low profile. How about a small "Circle of Friends" logo in the top/left corner of the screen, but keep boot messages running on the rest of the display?

---

### Post by ranch hand on 2011-11-25
Another thing you can do to get all messages scrolling is to replace the entire instruction string in /etc/default/grub with "text".

The draw back is that it will take you to a text login and you will have to "startx".

---

### Post by effenberg0x0 on 2011-11-25
Best options so far:

sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="ro plymouth.ignore-show-splash"
GRUB_CMDLINE_LINUX=""
...
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

sudo update-grub
sudo update-initramfs -c -k all
sudo reboot now

---

### Post by ventrical on 2011-11-29
> **philinux said:**
> Ditto.

I inserted "no plymouth" instead of "quiet splash".

This stops plymouth splash, i.e. the progress dots, and I get some text and all text on restart.

I think the pink screen is coming maybe from grub :confused:.

Or is it a vt.handoff  setting?

 I did this <exactly as prescribed> and got absolutely nothing. Just seemed like the boot was smoother .. no text.


3.2.0-1-generic #3-Ubuntu SMP Tue Nov 22 11:17:48 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by effenberg0x0 on 2011-11-29
I've been playing around a lot with it. This are my current best setting

At /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="=1 nopat plymouth:debug vesafb.invalid=1 drm.debug=0xe"
GRUB_CMDLINE_LINUX=""

Remember to update-grub:
sudo update-grub

These are working solidly for me.

---

### Post by teh603 on 2011-11-29
> **philinux said:**
> I think we need Plymouth to start or will fsck not work automatically etc etc.
I thought it was mountall and ureadahead, and that they'd been coded specifically to terminate if the Plymouth process wasn't already running.

Anyone got access to the stickies from 10.04, so we can see? I know it was sticked way back when, and one of the developers went into the grisly details of how they were going to be stuffing Plymouth down our throats and just what was getting re-coded to depend upon it.

---

### Post by zika on 2011-11-29
> **effenberg0x0 said:**
> I've been playing around a lot with it. This are my current best setting

At /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="[SIZE=3]**=1**[/SIZE] nopat plymouth:debug vesafb.invalid=1 drm.debug=0xe"
GRUB_CMDLINE_LINUX=""

Remember to update-grub:
sudo update-grub

These are working solidly for me.
Above is a remnant of an option forgotten or a proper option?

BTW, people: how often do You boot so that this options are important, anyway...? ;)

---

### Post by effenberg0x0 on 2011-11-29
> **zika said:**
> Above is a remnant of an option forgotten or a proper option?
As weird as it may be, it is an option :)
I've been also playing with null terminators lol

> **zika said:**
> 
BTW, people: how often do You boot so that this options are important, anyway...? ;)
Ok now, let's be reasonable here: You mean there's more to it than booting? That's ridiculous. What would be after the boot? Nonsense. There's nothing beyond it.
The boot is the purest definition of means to an end. It starts and finishes without ever leading into something else. It is itself an unbearable concentration of purpose or potential, turned into action and to an end in itself. Every boot is the big bang.

---

### Post by zika on 2011-11-29
> **effenberg0x0 said:**
> As weird as it may be, it is an option :)
I've been also playing with null terminators lol


Ok now, let's be reasonable here: You mean there's more to it than booting? That's ridiculous. What would be after the boot? Nonsense. There's nothing beyond it.
The boot is the purest definition of means to an end. It starts and finishes without ever leading into something else. It is itself an unbearable concentration of purpose or potential, turned into action and to an end in itself. Every boot is the big bang.
OK. Now it's the time that You explain purpose of each of these options for all of us... ;)
Especially &#8222;=1&#8220;... ;)
In order for boot to be something meaningful, let alone something pure and rewarding, we should know what we are to expect from each of those...
I'm sure I'm in for a threat that will make the rest of my day, maybe, even, the rest of my week...

---

### Post by effenberg0x0 on 2011-11-29
> **zika said:**
> OK. Now it's the time that You explain purpose of each of these options for all of us... ;)
Especially &#8222;=1&#8220;... ;)
In order for boot to be something meaningful, let alone something pure and rewarding, we should know what we are to expect from each of those...


Ok :) My strategy to get a glimpse at creation are:

=n, as the first option, enforces a runlevel. Plymouth has a kernel command-line parser and it is not perfect. While it's code has been improved lately, it now simply ignores some settings. 
nopat: Turning Off pagetable extensions. I'm on nvidia proprietary and, every now and then, there's the discussion about how the pagetable extension interferes with memory allocation.  
plymouth:debug: Forces debug mode, and outputs more meaningful content to /var/log/plymouth-debug.log
vesafb.invalid=1: For vesafb.ko, as I don't want it to be used.
drm.debug=0xe More verbosity on dmesg

In my experience, this options all together are a god way to understand a little more about Plymouth and boot procedure, and finally looking through the pink cosmic microwave background.

---

### Post by philinux on 2011-11-29
> **teh603 said:**
> I thought it was mountall and ureadahead, and that they'd been coded specifically to terminate if the Plymouth process wasn't already running.

Anyone got access to the stickies from 10.04, so we can see? I know it was sticked way back when, and one of the developers went into the grisly details of how they were going to be stuffing Plymouth down our throats and just what was getting re-coded to depend upon it.

That was my etc etc, I could not recall them all. :D

---

### Post by effenberg0x0 on 2011-11-29
As a tip: Once debug is enabled, one can check /var/log/plymouth.log and grep it for a very complete vision of how it works: the boot-server, the event-loop, etc. You can grep for fsck, mountall, etc to see plymouth handling it.

---

### Post by ventrical on 2011-11-29
> **effenberg0x0 said:**
> 

Remember to update-grub:
sudo update-grub

These are working solidly for me.


Thats always it eh :)

Definitely thats a Top Ten sudo command to remember :)

---

### Post by matt_symes on 2011-11-29
> **zika said:**
> Most effective way of stopping Plymouth without uninstalling it or using boot switches I found is
```
:~$ ls /etc/init/plymouth*.override
/etc/init/plymouth-log.override     /etc/init/plymouth-stop.override
/etc/init/plymouth.override         /etc/init/plymouth-upstart-bridge.override
/etc/init/plymouth-splash.override
:~$ cat /etc/init/plymouth.override 
manual
```Leave *.conf files unchanged...
```
:~$ ls /etc/init/plymouth*.conf
/etc/init/plymouth.conf         /etc/init/plymouth-stop.conf
/etc/init/plymouth-log.conf     /etc/init/plymouth-upstart-bridge.conf
/etc/init/plymouth-splash.conf
```Override files do not get changed with update...
Override+manual trick works for (almost) all services... Great trick that was introduced...

To make it clear: For any service You want not to start automatically, just put &#8222;**manual**&#8220; (without quotes) line into **/etc/init/_service_You_want.override** and start the service, if/when You want to with **sudo start _service_You_want** start ...

I think i'm late to this thread, but a simple one liner for the above for those new to testing.

```
echo manual | sudo tee /etc/init/plymouth{,-log,-splash,-stop,-upstart-bridge}.override
```and to remove

```
sudo rm /etc/init/plymouth*.o*
```

EDIT: Somehow i seamed to miss page 2 of this thread.

---

### Post by zika on 2011-11-29
> **effenberg0x0 said:**
> Ok :) My strategy to get a glimpse at creation are:

=n, as the first option, enforces a runlevel. Plymouth has a kernel command-line parser and it is not perfect. While it's code has been improved lately, it now simply ignores some settings. 
nopat: Turning Off pagetable extensions. I'm on nvidia proprietary and, every now and then, there's the discussion about how the pagetable extension interferes with memory allocation.  
plymouth:debug: Forces debug mode, and outputs more meaningful content to /var/log/plymouth-debug.log
vesafb.invalid=1: For vesafb.ko, as I don't want it to be used.
drm.debug=0xe More verbosity on dmesg

In my experience, this options all together are a god way to understand a little more about Plymouth and boot procedure, and finally looking through the pink cosmic microwave background.Now we are talking. I said that this thread will make my day...
Thank You. Do not stop here... ;)

---

### Post by zika on 2011-11-29
> **ventrical said:**
> Thats always it eh :)

Definitely thats a Top Ten sudo command to remember :)Not to mention that, while tweaking Your grub, You need to have a good memory of how to chroot... ;)

---

### Post by ventrical on 2011-11-29
> **zika said:**
> Not to mention that, while tweaking Your grub, You need to have a good memory of how to chroot... ;)

Enlighten me Yoda Master :)

---

### Post by zika on 2011-11-29
> **ventrical said:**
> Enlighten me Yoda Master :)*Fear is the path to the Dark Side. Fear leads to anger, anger leads to hate; hate leads to suffering. I sense much fear in you...*

---

### Post by ventrical on 2011-11-29
> **zika said:**
> *Fear is the path to the Dark Side. Fear leads to anger, anger leads to hate; hate leads to suffering. I sense much fear in you...*


No, no , no ... the chroot command. I fear it not. I know it not .. What is it ?

:)

---

### Post by ventrical on 2011-11-29
> **zika said:**
> Not to mention that, while tweaking Your grub, You need to have a good memory of how to chroot... ;)

Thanks zika.


[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

thats a great tool !!

---

### Post by Harry33 on 2011-11-29
[SIZE=2][FONT=Verdana]I use chrooting this way:[/FONT]

[/SIZE][FONT=Verdana][SIZE=2]1. Boot with live-USB or -CD. [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]2. Mounting:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]sudo mount /dev/sda1 /mnt[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]sudo mount -t proc proc /mnt/proc[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT]
[FONT=Verdana][SIZE=2]3. Chrooting:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]sudo chroot /mnt[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT]
[FONT=Verdana][SIZE=2]4. Action[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]do what you need to do here.

[/SIZE][/FONT] [FONT=Verdana][SIZE=2]5. Stop chrooting:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]exit[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT]
[FONT=Verdana][SIZE=2]6. Unmounting:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Ctrl D[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]sudo umount /mnt/dev[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]sudo umount /mnt[/SIZE][/FONT]

---

### Post by matt_symes on 2011-11-29
Here's another kernel command line to debug initramfs. Add debug to the kernel command line.

Look in /dev/.initramfs. It's a symlink in 12.04 and initramfs will produce the file initramfs.debug as opposed to piping its script errors to /dev/null.

matthew@matthew-Aspire-7540:~$ cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-2-generic <snip> **debug**
```
matthew@matthew-Aspire-7540:~$
```

matthew@matthew-Aspire-7540:~$ ls -l /dev/.initramfs
lrwxrwxrwx 1 root root 14 Nov 29 20:36 /dev/.initramfs -> /run/initramfs
matthew@matthew-Aspire-7540:~$
``````
matthew@matthew-Aspire-7540:~$ ls  /dev/.initramfs/
initramfs.debug
matthew@matthew-Aspire-7540:~$ 
```I hope this is helpful. You can also break into initramfs at anytime using the break= with the break point you want to stop at. (init-top, pre-mount, init-bottom) etc.

---

### Post by Harry33 on 2011-11-29
One more thing here about Plymouth.

It won't bother you anymore if you uninstall all plymouth-* packages, leaving only two packages (which are mandatory): plymouth and libplymouth2.

After this I do not see any more splashes and I see texts during boot.
And yet, the fsck process is not damaged.

---

### Post by ranch hand on 2011-11-29
> **Harry33 said:**
> One more thing here about Plymouth.

It won't bother you anymore if you uninstall all plymouth-* packages, leaving only two packages (which are mandatory): plymouth and libplymouth2.

After this I do not see any more splashes and I see texts during boot.
And yet, the fsck process is not damaged.
Great that you mention this.  Was going to myself.

People think that Plymouth just does the splash screen.  Plymouth does all your boot logging too. This is primarily a function of the lib package.

All the grub entry is doing is repressing the splash part.  There is some advantage to this in a testing  OS in that you can hit  e  and edit that out for a boot and see if it is working.  This should be done on occasion as it is a default part of the installed OS that folks here are supposed to be testing.

---

### Post by effenberg0x0 on 2011-11-29
> **ranch hand said:**
> Great that you mention this.  Was going to myself.

People think that Plymouth just does the splash screen.  Plymouth does all your boot logging too. This is primarily a function of the lib package.

All the grub entry is doing is repressing the splash part.  There is some advantage to this in a testing  OS in that you can hit  e  and edit that out for a boot and see if it is working.  This should be done on occasion as it is a default part of the installed OS that folks here are supposed to be testing.

Yes, I'm not sure about some uninstall methods we see here and there. Just a note to any eventual reader: the kernel command line I suggested at [#27]("http://ubuntuforums.org/showpost.php?p=11497977&postcount=22") does not disabled Plymouth or the way it interacts with the boot process. What it does is disable the splash and the FB, so you get a 80x25 console, but Plymouth is running and actually it is creating a much more verbose log, in which one can clearly see and easily understand how it works and interacts with init. It's a purely "academic exercise" of small use to the average user. 

Plymouth lacks proper documentation on it's workings, configs and switches, in a way that tinkering with it and digging sources is the only way I have to learn about it.

---

### Post by MoreOrLess on 2011-11-30
In the past, I would use the "mediahacks" PPA where mountall and cryptsetup are slightly modified to "suggest" the plymouth package as a dependency instead of requiring it.

---

### Post by teh603 on 2011-11-30
> **Harry33 said:**
> One more thing here about Plymouth.

It won't bother you anymore if you uninstall all plymouth-* packages, leaving only two packages (which are mandatory): plymouth and libplymouth2.

After this I do not see any more splashes and I see texts during boot.
And yet, the fsck process is not damaged.The main problem with that is the fact that plymouth still runs and can still clobber the boot process. It did it in 10.04 almost until the release, and I'm pretty sure it would do it again given half a chance.

I still wonder how the guy who rewrote mountall like that was allowed to get away with it.

---

### Post by 666f6f on 2012-02-26
I've already spent too much time trying to figure out how to get good ol' boot messages. I honestly don't understand what is so great about having an image with some (blinking) dots appear (for some seconds, or less).. Yeah, "Plymouth handles a great deal of some other very very important stuff" according to some people. Couldn't we just have something less agressive for that purpose? 

Some would say Plymouth is a bug, not a feature.

---

### Post by MoreOrLess on 2012-02-26
> **666f6f said:**
> Some would say Plymouth is a bug, not a feature.
See: [https://launchpad.net/~dtl131/+archive/mediahacks](https://launchpad.net/~dtl131/+archive/mediahacks)
There is little chance of Ubuntu making plymouth optional. Bugs reported against mandatory plymouth are marked "Won't Fix." Still, you can use the PPA to make it removable..

---

### Post by effenberg0x0 on 2012-02-26
> **666f6f said:**
> I've already spent too much time trying to figure out how to get good ol' boot messages. I honestly don't understand what is so great about having an image with some (blinking) dots appear (for some seconds, or less).. Yeah, "Plymouth handles a great deal of some other very very important stuff" according to some people. Couldn't we just have something less agressive for that purpose? 

Some would say Plymouth is a bug, not a feature.

It has been discussed many, many times... For us, as testers, I find little use for it - we need to see boot messages. Even the speed in which they show give us a perception if there's something different or wrong in the system. You don't get that from reading logs. 

For end-users, that are used to other OSs and afraid if system messages, and value aesthetics only, it is useful. I think it will eventually be used by some OEMs, as it allows for more exposure than BIOS embedded logos.

But the whole point is that it should not be mandatory and it had to be easily enabled/disabled and configured/customized via something easily accessible in the GUI such as the gnome-control-center. 

Many ways to successfully disable it have been pointed out in this cycle Plymouth threads. We even had a developer of mountall participating in a thread, pointing us to a version that was not dependent of Plymouth. Search for the threads about it in the last two months or so, you'll find good stuff.

Regards,
Effenberg

---

### Post by pressureman on 2012-02-26
I think you'll probably get what you're after if you purge all plymouth theme packages, leaving your system with just libplymouth2 and plymouth, then set your kernel boot params to "nosplash" and perhaps also drop off the "quiet" so you get a verbose boot.

Or just use Debian.

---

