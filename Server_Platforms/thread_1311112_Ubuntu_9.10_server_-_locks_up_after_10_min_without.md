---
title: "Ubuntu 9.10 server - locks up after 10 min without monitor"
date: 2009-11-02
forum: Server Platforms
---

### Post by danooch13 on 2009-11-02
Hello,

I have another post related to this, but I figured I would create another one with a more detailed title now that I know what is causing my problem.

I upgraded from 9.04 to 9.10 with the usual command do-release-upgrade.  Everything was successful.  This server is hooked up in a server room with just a nic cable and power.  With 9.04 it worked fine like this, but now, it will boot up and the server will be responsive for about 10 min, then for no reason what so ever it becomes unresponsive (cant ssh, ping, or do anything with it)

I thought at first that it had something to do with the monitor powersave or something so I ran 3 setterm commands thinking that would fix the issue, but still nothing.

I have 3 servers that I did this upgrade too, all the same hookup (nic and power cable only), and 2 of them have this problem and the third is fine.  It is def kernel-monitor related, but I am not sure what is really causing this issue to fix it..

Please help...I would hate to have to format.

Thanks

---

### Post by danooch13 on 2009-11-02
Anyone?

---

### Post by will81 on 2009-11-02
Same here.  Cycling the power has worked for me so far... fingers crossed.

---

### Post by spongypants23 on 2009-11-02
I'm having this issue as well. I'm suspecting a kernel panic of some sort, though I can't see anything in the logs because the server locks up before I can properly go through them.

I have to hard reboot the server by holding down the power button. Not good.

---

### Post by danooch13 on 2009-11-03
Yeah still same thing.  Cant figure it out.  Has to be some sort of a kernel panic.  Even if I hold the power down and power it back up, if there is not monitor attached, it will work a for 10 min or so, then just die all together (no pinging, services etc)...

Has to be some sort of a kernel panic when trying to possibly put the monitor to sleep or something....but I disabled that...

Nothing in the logs either.

Any ideas??

---

### Post by airencracken on 2009-11-03
I'm having the same exact issue. I can't find anything incriminating in the logs, or perhaps I'm not checking the correct logs. 

Hardware is all fine, it was running well on 9.04.

---

### Post by danooch13 on 2009-11-03
All I checked was the syslog, and it shows nothing....

Same for me, worked all along in 9.04

Funny thing is for me I have three servers (all different hardware in each), and 2 out of the 3 have this problem and the other one is perfectly fine.  They all have only a nic cable and a power cable.  They were all updated the same way successfully.

I would really hate to have to format the server and realize that it is a kernel panic issue that will be there after the format!

---

### Post by spongypants23 on 2009-11-03
Has anyone filed a bug report?

---

### Post by danooch13 on 2009-11-03
No.  Never did that.  

New to linux/ubuntu....if someone tells me how I will do it...

---

### Post by bartos on 2009-11-03
I had the problem so i reloaded my server with debian.

---

### Post by spongypants23 on 2009-11-03
> **bartos said:**
> I had the problem so i reloaded my server with debian.

That's wonderful, but doesn't really help in any way. Some of us would prerfer NOT to have to reimage our servers.

---

### Post by danooch13 on 2009-11-03
Yeah that would be the easy way, but number 1 I dont want to do it, and number 2, if it is kernel panic related, redoing the server will result in the same problem.

It has something to do with the particular video controller in the computer....the kernel is fine with 1 out of my 3 servers like I said earlier, but my other two (which have two different cards) give this possible kernel panic.

So I guess we just have to wait for a fix...

Can someone report a bug?

---

### Post by spongypants23 on 2009-11-03
It's hard to report a bug when you don't know what program/app/whatever is causing it, otherwise I would have done so already.

---

### Post by danooch13 on 2009-11-03
LOL true true.

We somewhat know the cause.

Aren't we all in agreement that when a monitor is not hooked up to Ubuntu karmic, the server will work fine for a particular amount of time, then just die.

I mean the only other specificity I can get is my video card which is simple...

There really isn't any other cause.

---

### Post by spongypants23 on 2009-11-03
Not really. I haven't seen anything to indicate it's the fact that a monitor isn't hooked up. I'll have to try that eventually. (I'm in the middle of moving and I don't have access to my server right now, anyhoo).

---

### Post by airencracken on 2009-11-03
> **spongypants23 said:**
> It's hard to report a bug when you don't know what program/app/whatever is causing it, otherwise I would have done so already.

Exactly. This is why I haven't filed a bug report yet. It would be rather nebulous.

However, if this thread doesn't yield something soon, I think it will become necessary. I too have no monitor for my server and administer it over SSH. I can't confirm yet if it has frozen completely or if it's just a problem with SSH. However, since it doesn't consistently log me out (sometimes it just stays frozen) I'm thinking it's the former.

---

### Post by danooch13 on 2009-11-03
Ok.

I understand.  I did do the testing though.

With respect to probability, I am 90% sure of the issue.  These were my steps.

I performed the test by taking the server to a workbench, and hooking it up to the network and power alone first.  Within 10 min it failed (by failed i mean no pinging, ssh etc etc).  I then hooked up just a keyboard (usb) and went to see if it was the keyboard causing it.  After  about 10 min with the keyboard, the server was unresponsive again.  After that, I hooked up a crt monitor, and no keyboard.  The server stayed on until i manually shut it down again the next day.  After that, I thought I figured out the bug, which I thought was when it turns the display off until you hit a key to bring up the login prompt again.  So I ran some setterm commands (blank, powersave and another one which I forget), and put the server back in the server room.  After that I thought I was golden, but came back the next day and boom...dead again.

So I guess my question is, can someone redo my tests and let me know if they get the same results, then we can be sure that the issue is something to do with the videocard/monitor, related to the new kernel/hal.

---

### Post by airencracken on 2009-11-03
Don't really have the ability to do that right now, but hopefully I'll be able to do it next week.

Just curious what hardware are you running?

Mine is a P4 with Intel integrated video. I'll be more specific when I'm able to get a monitor attached to the thing.

---

### Post by spongypants23 on 2009-11-03
> **airencracken said:**
> Don't really have the ability to do that right now, but hopefully I'll be able to do it next week.

Just curious what hardware are you running?

Mine is a P4 with Intel integrated video. I'll be more specific when I'm able to get a monitor attached to the thing.

I believe my box is similar. I'll have to check it later, though. I know it's got an Intel integrated card.

---

### Post by danooch13 on 2009-11-03
My hardware is also a P4 with Integrated intel video.

I will get the specifics another day this week.  I have to hook it up to a monitor and run an lspci command.

---

### Post by happyhacker on 2009-11-04
Oh dear!, this doesn't look good. I have 8.10 and just about to upgrade to 9.x and my server does not have a console as I control everything from webmin. I have upgraded all the packages as required and was just about to upgrade Ubuntu when I saw this post. Not experienced enough to help, sorry.

Should I go ahead and risk death by upgrade?

Advice appreciated.

---

### Post by spongypants23 on 2009-11-04
> **cantthinkofanickname said:**
> Oh dear!, this doesn't look good. I have 8.10 and just about to upgrade to 9.x and my server does not have a console as I control everything from webmin. I have upgraded all the packages as required and was just about to upgrade Ubuntu when I saw this post. Not experienced enough to help, sorry.

Should I go ahead and risk death by upgrade?

Advice appreciated.

Since we're not 100% what the problem is, you should hold off until this gets solved.

---

### Post by allio on 2009-11-04
Confirming the same problem. System is a Dell Optiplex P4 2.4 with Intel 82845G graphics. Fresh install of 9.10 server. It freezes after 7-9 minutes running headless, but is stable for hours with a monitor and keyboard plugged in.

This is **definitely** the cause, I literally changed nothing except plugging in a mouse and keyboard between it crashing and it being stable.

What a hair puller this was to narrow down. Related to the intel graphics I think?

I initially had a desktop install of karmic on this box, and that wouldn't even boot without a monitor plugged in. That was the whole reason I did a fresh install of server. I would guess these two bugs are related.

I'd post a bug report, but in what area? It seems related to xserver-xorg-video-intel, but this is a headless sever. It doesn't have x installed...

---

### Post by danooch13 on 2009-11-04
I am not sure if mine is headless. Guess I don't understand what that means. I have just an upgraded ubuntu 9.04 server to 9.10. When I run top I don't see x.org so I am guessing it's headless. Can someone tell me what that means?

Anyway as for the problem, is there anywhere just to report plain kernel issues or a place for ubuntu 9.10 issues?  I am new to this Linux stuff and I really can't help much other than start this thread. 

I have to get my exact video controller to compare that with the rest of you. Hopefully sometime this week.

---

### Post by zika on 2009-11-04
Did You try to boot with "apm=off" ...?

---

### Post by danooch13 on 2009-11-04
No, but what does apm=off mean?

And what is it a boot line parameter in the menu.lst file?

---

### Post by zika on 2009-11-04
> **danooch13 said:**
> No, but what does apm=off mean?
And what is it a boot line parameter in the menu.lst file?Boot as usual. When You come to Grub, highlight menu entry You want, press "E" and navigate to a line where, for example, quiet or splash are located. Insert apm=off, press "Ctrl-X" and You will boot with that option. (Advanced Power Management off). If it does the trick, You can make it permanent by adding it in the line with the kernel You use in Your grub menu file. Which file it is, depends on what version of Grub You use.

---

### Post by danooch13 on 2009-11-04
Ok, I will give that shot tomorrow night... Masters degree midterm tonight!!!

Can anyone else give that a try before I do?

Do it make sense to everyone?

Is it still considered a bug if it works?

---

### Post by spongypants23 on 2009-11-04
It should still be reported as a bug so that the Ubuntu Devs can fix the problem. Not everyone will read this thread.

---

### Post by zika on 2009-11-04
> **danooch13 said:**
> Ok, I will give that shot tomorrow night... Masters degree midterm tonight!!!

Can anyone else give that a try before I do?

Do it make sense to everyone?

Is it still considered a bug if it works?Just stay calm and show them how much You know. Break a leg!

---

### Post by danooch13 on 2009-11-04
Thanks I'll try.  Software engineering is a pain.

I will try that apm thing tomorrow night and report back.

If anyone else has any news, let us know, then when we are sure we can report it as a bug.

Thanks everyone for all your responses.

---

### Post by allio on 2009-11-04
> **danooch13 said:**
> I am not sure if mine is headless. Guess I don't understand what that means. I have just an upgraded ubuntu 9.04 server to 9.10. When I run top I don't see x.org so I am guessing it's headless. Can someone tell me what that means

Headless just means that it doesn't have any forms of input/output other than the network. A headless box usually just has a power cable and a network cable plugged into it and everything is done remotely (via SSH or similar). If you've got a mouse, keyboard and monitor plugged in, it's not headless.

I've got my server working in the meantime. One of two things I did fixed the problem: booting it up with a monitor attached, then removing it, or plugging in an old, powered off monitor. Running fine now. Hoping I don't have to reboot before this is fixed...

---

### Post by danooch13 on 2009-11-04
Thank you for that info.  Figured as much.

---

### Post by allio on 2009-11-04
Looking through this thread it seems like everybody affected is running some kind of P4 (2.4-2.8GHz) with onboard Intel graphics. Is that right? Can anyone else contribute?

I have a Dell Optiplex GX260 (845 video) 
airencracken has a Dell 4600C? (865 video)

We need to work out exactly what the common factor is before we can report a bug.

---

### Post by spongypants23 on 2009-11-04
> **allio said:**
> Looking through this thread it seems like everybody affected is running some kind of P4 (2.4-2.8GHz) with onboard Intel graphics. Is that right? Can anyone else contribute?

I have a Dell Optiplex GX260 (845 video) 
airencracken has a Dell 4600C? (865 video)

We need to work out exactly what the common factor is before we can report a bug.

I'll have a look as soon as I can. As I stated in other posts, I'm unable to access the server right now since I'm moving.

---

### Post by danooch13 on 2009-11-04
Tomorrow night I will look at mine and report back.

Can anyone help me out in the meantime with my cups server problem after this damned upgrade.  The post is there on the top.

---

### Post by inf0c0m on 2009-11-04
I'm having same issues, running a compaq d51s headless. I am currently at home to test some things with this if needed. Will test out the APM options here in a second

---

### Post by inf0c0m on 2009-11-04
Looks like the APM=off Fix didn't change anything, still locks up after 10 minutes of being headless

---

### Post by allio on 2009-11-04
inf0c0m, could you try adding nomodeset to the bootstring in grub?

---

### Post by inf0c0m on 2009-11-04
Just done, rebooting to check.

Some things I've noticed:

The kernel it's using is the generic-pae one, vs the server one it did in the past

```
title           Ubuntu 9.10, kernel 2.6.31-14-generic-pae
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-14-generic-pae root=UUID=3ee04cae-bb23-4263-a8f7-40b09555d249 ro quiet splash apm=off nomodeset
initrd          /boot/initrd.img-2.6.31-14-generic-pae
quiet

title           Ubuntu 9.10, kernel 2.6.28-15-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-15-server root=UUID=3ee04cae-bb23-4263-a8f7-40b09555d249 ro quiet splash
initrd          /boot/initrd.img-2.6.28-15-server
quiet

```

Also, the console font is different. it's not the generic blocky text it used to be in the past, it's as if the console is running at a different resolution. not sure what would/could cause this

---

### Post by allio on 2009-11-04
> **inf0c0m said:**
> Also, the console font is different. it's not the generic blocky text it used to be in the past, it's as if the console is running at a different resolution. not sure what would/could cause this

That's kernel modesetting. nomodeset should disable it, which will hopefully let us know if it's causing the problem.

---

### Post by inf0c0m on 2009-11-04
so far, so good. been up for 16 minutes now

---

### Post by spongypants23 on 2009-11-04
**BUG REPORT FILED**

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474930](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474930)

---

### Post by allio on 2009-11-04
Still going? I guess we've found our problem. Luckily modesetting serves no function at all on a headless server, so at least it's a pain-free fix :p

---

### Post by benbrookshire on 2009-11-04
I think I'm in the same boat - upgraded from 9.04 Monday, and now shutdown -r now leaves me hanging.

EDIT: I don't drop out after 10 minutes, but restarting will leave me dead in the water. On 9.04 this happened a few times, but eventually I was able to restart without any problems.

I haven't gone to the site, but I had this problem before and hooking up a monitor and restarting worked. I'd be nice to have a fix for this so I don't have to have someone physically hook up a monitor if I have to reboot. 

Its running on a Dell Dimension desktop with built-in Intel graphics.

EDIT: I think this will get me taken care of. I also noted that I'm not running 9.10 server edition. Sorry to be a dreg. [http://swiss.ubuntuforums.org/showthread.php?p=8245012]("http://swiss.ubuntuforums.org/showthread.php?p=8245012")

---

### Post by inf0c0m on 2009-11-04
still good so far, doing the apport in a minute here

---

### Post by danooch13 on 2009-11-04
Guys,

Thank you all for helping me solve my issue.  I will add that string to the boot string tomorrow when I am home.  I will then run apport for the bug.

New to linux....what does apport mean and do?

As for the console resolution, yeah what is with that?  Does nomodeset fix that?

Anyone know what the generic kernel is running?  I have to check mine tomorrow and see what I have running.

Thanks again all!

---

### Post by airencracken on 2009-11-05
Went ahead and +1'd the bug report, when I get a chance to hook up a monitor to it I'll try the nomodset.

---

### Post by spongypants23 on 2009-11-05
> **danooch13 said:**
> Guys,

Thank you all for helping me solve my issue.  I will add that string to the boot string tomorrow when I am home.  I will then run apport for the bug.

New to linux....what does apport mean and do?

As for the console resolution, yeah what is with that?  Does nomodeset fix that?

Anyone know what the generic kernel is running?  I have to check mine tomorrow and see what I have running.

Thanks again all!

The apport-collect command will gather data about your system that may help diagnose the cause of the bug and help developers find the common factor and solve the issue.

Apport is the program that files program crash information.

---

### Post by dacodo on 2009-11-05
I'm having the same problem on my mythTV system. Fresh install of 9.10 on amd64. Then install myth packages on top of it.

Watching TV works fine for hours. If I turn our 52" LCD off for 10 min or switch it to a different source my 9.10 system will completely lock up.

Really annoying, kind of defeats the purpose of a PVR when it can't record anything because it's crashed.

I'll try the nomodeset thing over lunch. Otherwise I guess I'll reinstall with debian or something.

---

### Post by spongypants23 on 2009-11-05
> **dacodo said:**
> I'm having the same problem on my mythTV system. Fresh install of 9.10 on amd64. Then install myth packages on top of it.

Watching TV works fine for hours. If I turn our 52" LCD off for 10 min or switch it to a different source my 9.10 system will completely lock up.

Really annoying, kind of defeats the purpose of a PVR when it can't record anything because it's crashed.

I'll try the nomodeset thing over lunch. Otherwise I guess I'll reinstall with debian or something.

Or you could keep your current installation and help solve the problem ;)

---

### Post by danooch13 on 2009-11-05
It is probably the same issue.  Stay with Ubuntu and help us solve the issue.

Also, what is the deal with the resolution on the 9.10 console?  Why is it so small?  Will the nomodeset command fix that also?

---

### Post by spongypants23 on 2009-11-05
I'm wondering if this is a problem with Ubuntu 9.10 in general, perhaps not just Ubuntu Server 9.10?

---

### Post by danooch13 on 2009-11-05
I am not sure.  It would seem to me to be a global 9.10 issue.  

I remember them mentioning something in the changes about resolution changes....something something something...

---

### Post by Setstar on 2009-11-05
ok i have playing with ubuntu server 9.10 on 3 different brand names i got a no name board to stay up for 2 days untill i decidedto install php5 rebooted and that was it, it comes up to loading presql and than locks up.
the oth 2 is a dell and a hp they both lock up about 10 minutes after boot up.

---

### Post by Setstar on 2009-11-05
reverting to 9.04 and playing with one!

---

### Post by danooch13 on 2009-11-05
I am going to start a new post for this, but does anyone know why since the 9.10 upgrade, the default kernel is the generic one.  See my menu.lst...

```
title           Ubuntu 9.10, kernel 2.6.31-14-generic-pae
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-14-generic-pae root=/dev/mapper/sil_ajaiahaafcai1 ro quiet splash apm=off nomodeset
initrd          /boot/initrd.img-2.6.31-14-generic-pae

title           Ubuntu 9.10, kernel 2.6.31-14-generic-pae (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-14-generic-pae root=/dev/mapper/sil_ajaiahaafcai1 ro  single
initrd          /boot/initrd.img-2.6.31-14-generic-pae

title           Ubuntu 9.10, kernel 2.6.31-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/sil_ajaiahaafcai1 ro quiet splash
initrd          /boot/initrd.img-2.6.31-14-generic


```

---

### Post by capcoms on 2009-11-06
> **allio said:**
> Looking through this thread it seems like everybody affected is running some kind of P4 (2.4-2.8GHz) with onboard Intel graphics. Is that right? Can anyone else contribute?
 
I have a Dell Optiplex GX260 (845 video) 
airencracken has a Dell 4600C? (865 video)
 
We need to work out exactly what the common factor is before we can report a bug.
 
My system is also a GX260. My system locks up constantly after upgrading to 9.10 (9.04 ran great). I have my gX260 connected to a KVM switch and it will only allow resolution choices of 800x600 & 640 X480. When I connect the monitor directly (where it can detect it will allow up to 1650 x 1250). I tried to connect it and set it to 1650 x 1250 and then connect back to the KVM switch but as soon as I do it reverts back to the 800x600 setting. I did not have the KVM issue in 9.04.
Thanks

---

### Post by airencracken on 2009-11-06
Just booted into my server and edited the menu.lst to add nomodeset, so we'll see if that fixes it.

---

### Post by spongypants23 on 2009-11-06
What's it take to get a bug marked as Confirmed and not New? :s

---

### Post by airencracken on 2009-11-07
My server's been up for eight hours now, so that seemed to fix it. Still a bit of a kludge though.

---

### Post by sconstantin on 2009-11-07
I believe I am having a similar problem with the desktop edition.  It appears to lock up when the monitor is put to sleep by power management after inactivity.  I am forced to reboot using alt+sysreq REISUB.  My current solution has been to disable the monitor sleep feature and that has appeared to fix it.  Not a huge deal, but annoying.

Gateway SX2800-01
Intel Core 2 Quad Q8200
Integrated Intel GMA X4500 video

---

### Post by pi.boy.travis on 2009-11-24
Same issue on old Dell Dimensions desktop with integrated graphics, and disabling kernel mode setting fixes the issue.  This has been a real pain, especially since I do all of my administration remotely with SSH. . . 

Thanks to those who got this ironed out!

---

### Post by happyhacker on 2009-11-25
Has this really be solved? Can someone point me to the precise solution, or if I do an upgrade now (new download) will this be sufficient? I am waiting to do a headless upgrade to an 8.10 server.

---

### Post by spongypants23 on 2009-11-25
> **cantthinkofanickname said:**
> Has this really be solved? Can someone point me to the precise solution, or if I do an upgrade now (new download) will this be sufficient? I am waiting to do a headless upgrade to an 8.10 server.

I don't think Ubuntu 8.10 is affected by this.

---

### Post by pi.boy.travis on 2009-11-25
> **spongypants23 said:**
> I don't think Ubuntu 8.10 is affected by this.

Correct, this is caused by kernel mode setting, used only in the 9.10 kernel.

---

### Post by meg2k on 2009-11-26
Plan to install/downgrade to a fresh 9.04 on my headless server after playing with 9.10 for one week, crash all the times with panic and hang.... while these hardwares run smoothly with 9.04 for months !

I'm noob @ Linux, may I ask how we can use the apport app to trace which program/module crashed my server?

Thanks....

---

### Post by pi.boy.travis on 2009-11-26
> **meg2k said:**
> Plan to install/downgrade to a fresh 9.04 on my headless server after playing with 9.10 for one week, crash all the times with panic and hang.... while these hardwares run smoothly with 9.04 for months !

I'm noob @ Linux, may I ask how we can use the apport app to trace which program/module crashed my server?

Thanks....


Apport is only for generating a bug report based on your logfiles, it won't perform the diagnosis for you. . . if only it could. . . 

If you are looking for exceptional stability, I would use 8.04, the current LTS release.  Or better yet, use Debian.  My file server has been running Debian for years, with absolutely no issues whatsoever.

---

### Post by FrankT-Qc on 2009-12-02
Alright, I have the same problem but I'm working from a fresh install with grub 2 ... Any idea how in @¤£@ can I turn off kernel modesetting in grub2

thanks

---

### Post by FrankT-Qc on 2009-12-02
Alright, found it...

First, resist the temptation to modify /boot/grub/grub.cfg ... it'll get overwritten someday soon.

First, In /etc/default/grub, Change this line (sudoedit or whatever you like) :
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
for
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

then run ```
sudo update-grub
```

If you want to confirm that it worked, you should look at /boot/grub/grub.cfg and look for something like this (notice "nomodeset" at the end of the line starting with "linux /vmlinux...":
```

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 338edc81-4278-4cbe-aca8-5f9c1456c229
        linux   /vmlinuz-2.6.31-15-Frank09 root=UUID=867f7d8b-66fd-4265-a52a-8759931b5d28 ro   quiet splash **_nomodeset_**
        initrd  /initrd.img-2.6.31-15-Frank09
}

```

Have fun,
Frank

---

### Post by happyhacker on 2009-12-21
Can you tell me if this change can (or should) be made prior to upgrading from 8.10 to 9.10? I don't know if my system will exhibit the problem or not so am assuming that doing the change will at least ensure it won't.

Also, given I use Webmin what is the command line to upgrade?

Thanks.

---

### Post by Matuku on 2009-12-23
> **cantthinkofanickname said:**
> Can you tell me if this change can (or should) be made prior to upgrading from 8.10 to 9.10? I don't know if my system will exhibit the problem or not so am assuming that doing the change will at least ensure it won't.

Also, given I use Webmin what is the command line to upgrade?

Thanks.

If you are currently using grub2 then yes, you should be able to make the change and doing an upgrade should leave it alone (I believe); if you're using grub-legacy then I'm not so sure.

---

### Post by Matuku on 2009-12-23
Thank you for this thread; this problem has been bugging me for weeks! I've taken the entire network apart looking for an issue and it's just been this! If only my forum-search-fu had been stronger at the start...

For reference I'm running the server on a Dell GX260

---

### Post by harry71194 on 2010-01-04
Thanks FrankT-Qc, that seems to have fixed my problem!

---

### Post by spongypants23 on 2010-03-18
Planning on upgrading a server from 8.04 to 9.10 tomorrow. It's the same server that originally had this problem in 9.10, which is why I put 8.04 on it.

Does this bug still happen? It seems that the bug report I filed about it has gone unnoticed by developers.

---

### Post by pi.boy.travis on 2010-03-19
> **spongypants23 said:**
> Planning on upgrading a server from 8.04 to 9.10 tomorrow. It's the same server that originally had this problem in 9.10, which is why I put 8.04 on it.

Does this bug still happen? It seems that the bug report I filed about it has gone unnoticed by developers.

It has been fixed in Lucid, on my hardware at least, but it still happens in Karmic.  The aforementioned workaround still works, and it's pretty easy to do, well worth the performance gain.

---

### Post by spongypants23 on 2010-03-19
> **pi.boy.travis said:**
> It has been fixed in Lucid, on my hardware at least, but it still happens in Karmic.  The aforementioned workaround still works, and it's pretty easy to do, well worth the performance gain.

Sweet, thanks. I'll probably just wait and upgrade to Lucid once that's released, then.

---

### Post by houldsworth1 on 2010-03-26
Thanks everyone.  This problem has been driving me nuts for a while.  First I wasn't able to boot without a screen and then, once I got past that, I had the freeze issue after 10 minutes.

Finally, by following the 'quiet splash nomodeset', it now works in headless mode.  

Thanks for your contributions!

---

### Post by UnresponsiveBeeVictim on 2010-04-06
I have this same issue... 5 months later.  Is there a fix yet?

edit:

First, In /etc/default/grub, Change this line (sudoedit or whatever you like) :
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
for
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
then run
Code:
sudo update-grub

---

### Post by andynz22 on 2010-08-09
I had the same problem with freezing after 10 minutes with 9.1 on an HPd530 with on board intel graphics.  Took me 2 days of pulling my hair out to find this post.

Thanks[UnresponsiveBeeVictim]("http://ubuntuforums.org/member.php?u=449969") this worked for me:

First, In /etc/default/grub, Change this line (sudoedit or whatever you like) :
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
for
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
then run
Code:
sudo update-grub

Cheers
Andy

---

### Post by Aacron on 2011-05-14
By the way, I was having this problem with my Zoneminder 10.04 headless server as well.

The main difference with my setup is that I do have a kvm switch hooked to it, for when there are odd issues.  The only time it would lock up was when the KVM wasn't set to the server.

Intel Core 2 Duo, with Intel Integrated graphics chip.

Hopefully the nomodeset command will help on mine too!

---

