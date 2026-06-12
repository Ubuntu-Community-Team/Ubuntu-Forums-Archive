---
title: "slow reboot waiting 2-5 minutes before it does anything"
date: 2016-02-06
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2016-02-06
Anyone else having this issue of rebooting Xenial and having to wait somewhere between 2 and 5 minutes for it to happen?
I don't know precisely because I haven't bothered to time it.

The cursor just blinks in the top left of the screen while this is happening.
It was sporadic and sometimes it did it and sometimes it was a fast reboot.

It seems to happen every boot now though.

EDIT: solved.

---

### Post by Petro Dawg on 2016-02-06
You might check your var/log/syslog and see if there are some errors at startup which might point to the problem.

---

### Post by cariboo on 2016-02-06
You could also run:

```
systemd-analyze blame
```

to get an idea of what is taking so long.

---

### Post by Cavsfan on 2016-02-07
> **Petro Dawg said:**
> You might check your var/log/syslog and see if there are some errors at startup which might point to the problem.

Can't really make out what's happening in the log for the time period except there's a bunch of ureadahead errors.
I'll keep an eye on it if it happens today.

> **cariboo said:**
> You could also run:

```
systemd-analyze blame
```

to get an idea of what is taking so long.

The longest thing there was NetworkManager-wait-online.service at 8.419s.

---

### Post by Cavsfan on 2016-02-07
Then of course I reboot this morning and it takes about 2 seconds. :rolleyes:

---

### Post by Doug S on 2016-02-07
> **Cavsfan said:**
> Can't really make out what's happening in the log for the time period except there's a bunch of ureadahead errors.
I had some sort of "ureadahead" saga some days ago. It only happened during one session thou, and so I didn't investigate.

---

### Post by Cavsfan on 2016-02-07
> **Cavsfan said:**
> Can't really make out what's happening in the log for the time period except there's a bunch of ureadahead errors.

> **Doug S said:**
> I had some sort of "ureadahead" saga some days ago. It only happened during one session thou, and so I didn't investigate.

Yeah this happened several times a while back and now about 3 days in a row and today it quit. So, it might just be a glitch. Time will tell.

---

### Post by Cavsfan on 2016-02-08
It rebooted in a couple of seconds today. Must have just been a glitch.

---

### Post by Cavsfan on 2016-02-13
This has not happened in about a week and apparently was just a glitch.

---

### Post by sgage on 2016-02-23
Well, something like what was described in the OP has been happening to me for several days now. At boot, after an fsck msg showing that the boot drive is clean, it hangs for 2-3 minutes doing nothing - no disk activity, no nothing. Then it just carries on as though nothing whatsoever was wrong. Nothing relevant in syslog, nor systemd-analyze. 

Thinking I may have messed something up in this installation after testing for so long, I tried a fresh install with today's daily. Same problem. I suppose I should mention that this is Ubuntu Gnome, though this issue is occurring long before that should make any difference.

---

### Post by Cavsfan on 2016-02-23
> **sgage said:**
> Well, something like what was described in the OP has been happening to me for several days now. At boot, after an fsck msg showing that the boot drive is clean, it hangs for 2-3 minutes doing nothing - no disk activity, no nothing. Then it just carries on as though nothing whatsoever was wrong. Nothing relevant in syslog, nor systemd-analyze. 

Thinking I may have messed something up in this installation after testing for so long, I tried a fresh install with today's daily. Same problem. I suppose I should mention that this is Ubuntu Gnome, though this issue is occurring long before that should make any difference.

It quit and I solved this thread. But it did happen about 3 times after that. My problem has always when a restart is initiated. I'll see a flashing cursor at the top left of the screen and have to wait until it goes away and pay attention because it will boot into the default OS and that may not be the one I wanted to boot into.

The past 2 days it has not happened to me.

---

### Post by tista on 2016-02-24
It may be too late, but please check if ```
reboot=pci
``` kernel option could solve the reboot issues...

Regards.

---

### Post by Cavsfan on 2016-02-24
> **tista said:**
> It may be too late, but please check if ```
reboot=pci
``` kernel option could solve the reboot issues...


Regards.


Not clear on what you are asking.

---

### Post by Chazall1 on 2016-02-26
I have been having the slow boot up with Gnome Ubuntu. I have a fast boot on my Ubuntu Mate. Both 16.04 on same SSD drive. What will > reboot=pci ?
Thanks

---

### Post by QDR06VV9 on 2016-02-26
> **tista said:**
> It may be too late, but please check if ```
reboot=pci
``` kernel option could solve the reboot issues...

Regards.
I think they(tista) are referring to..
you need to edit **/etc/default/grub **and change GRUB_CMDLINE_LINUX=&#8221;&#8221; to  GRUB_CMDLINE_LINUX=&#8221;reboot=pci&#8221; _**or whatever value.**_ 
Afterwards you do  update-grub. [B]"sudo update grub"
Hope I got that right![/B]

---

### Post by Chazall1 on 2016-02-26
I still have this issue with slow boot up not sure why?

---

### Post by Cavsfan on 2016-02-27
It's still happening - twice so far today. I reopened it.

---

### Post by Cavsfan on 2016-02-29
It's happened 4 days in a row now. It's a pain because I have to watch it until it reboots so it doesn't boot into the wrong system.

---

### Post by Doug S on 2016-02-29
> **Cavsfan said:**
> It's happened 4 days in a row now. It's a pain because I have to watch it until it reboots so it doesn't boot into the wrong system.Same for me, for the same reason. It started for me 2 or 3 days ago, after updates. I also now have more apparmor issues, and suffered kernel crashes during re-boot. For me it is stuck for just over 1 minute during the shutdown portion of the re-boot. I don't get anything from the suggested "systemd-analyze blame" command, but it is just for startup, isn't it?

---

### Post by QDR06VV9 on 2016-02-29
> **Doug S said:**
> Same for me, for the same reason. It started for me 2 or 3 days ago, after updates. I also now have more apparmor issues, and suffered kernel crashes during re-boot. For me it is stuck for just over 1 minute during the shutdown portion of the re-boot. I don't get anything from the suggested "systemd-analyze blame" command, but it is just for startup, isn't it?

Yes just for startup's
Has any one tried tista's suggestion yet? I am not suffering from this or I would..
Kind Regards
EDIT:
> Power management [polkit]("https://wiki.archlinux.org/index.php/Polkit") is necessary for power management as an unprivileged user. If you are in a local *systemd-logind*  user session and no other session is active, the following commands  will work without root privileges. If not (for example, because another  user is logged into a tty), *systemd* will automatically ask you for the root password. 
Shut down and reboot the system: 
 $ systemctl reboot

---

### Post by Doug S on 2016-03-01
I begin to suspect some of these issues / threads are inter-related. See [this]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1551415").

---

### Post by QDR06VV9 on 2016-03-01
@Doug S Good Find!! certainly looks logical..

---

### Post by Cavsfan on 2016-03-01
I just edited /etc/default grub and added that:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"
```

We shall see if it helps...

---

### Post by QDR06VV9 on 2016-03-01
> **Cavsfan said:**
> I just edited /etc/default grub and added that:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci"
```

We shall see if it helps...

Thanks Cavsfan...keep us posted if you would please.
Others on different forums have had positive results from that...It would be nice to have it documented here also.

---

### Post by Cavsfan on 2016-03-01
I guess I should have kept reading before I posted, but I made the change and rebooted.
It took 2-4 minutes to reboot and then I let it come up and rebooted again and it and it was fast.

Unless it was just one of those "good" times where it doesn't do it. :roll:

A couple of days will tell.

---

### Post by mc4man on 2016-03-02
Here, (ubuntu session) the restart time has definitely increased lately, about 4-5 times as long as normal. (should be 2-3 sec., now 12 sec or so
This is on every restart, if I disconnect from network (ethernet) before restarting then it goes back to 2-3 sec.

---

### Post by Cavsfan on 2016-03-03
My reboot time is about 6-8 seconds since I added the reboot=pci to the grub line.
Not sure if that's permanent or what but yes 2-3 seconds was normal for me too.

Haven't tried disconnecting the network cable yet, maybe tomorrow.

---

### Post by QDR06VV9 on 2016-03-03
> **Cavsfan said:**
> My reboot time is about 6-8 seconds since I added the reboot=pci to the grub line.
Not sure if that's permanent or what but yes 2-3 seconds was normal for me too.

Haven't tried disconnecting the network cable yet, maybe tomorrow.

Thanks Cavsfan!! I think that the fix should hold barring an upgrade in Grub.
Again I could be wrong here but when mc4man was talking about disconnecting from the net(Ethernet) I got the impression he meant right click on the network manager and disconnect from there..
But I have been wrong before..:o:redface:   
Kind regards

---

### Post by mc4man on 2016-03-03
> **runrickus said:**
> Thanks Cavsfan!! I think that the fix should hold barring an upgrade in Grub.
Again I could be wrong here but when mc4man was talking about disconnecting from the net(Ethernet) I got the impression he meant right click on the network manager and disconnect from there..
But I have been wrong before..:o:redface:   
Kind regards
Yeah, simply doing from the menu. I've noticed that on this laptop which is wifi only the shutdown is quick so at least here just with Ethernet connection do I see the longer restart time.

---

### Post by Cavsfan on 2016-03-04
> **runrickus said:**
> Thanks Cavsfan!! I think that the fix should hold barring an upgrade in Grub.
Again I could be wrong here but when mc4man was talking about disconnecting from the net(Ethernet) I got the impression he meant right click on the network manager and disconnect from there..
But I have been wrong before..:o:redface:   
Kind regards

Not sure whether that fix did it or the glitch sometimes does not happen. But it's been pretty consistant with the 6-8 or so second delay. Which of course beats 2-5 minutes. 

> **mc4man said:**
> Yeah, simply doing from the menu. I've noticed that on this laptop which is wifi only the shutdown is quick so at least here just with Ethernet connection do I see the longer restart time.

I just clicked on the Internet connection icon, then disconnect and rebooted. It went so fast that it did not even display the flashing icon at all. It was like a normal reboot and how it should be.

Does this mean I should add my name to that bug about the network causing a slow reboot?

---

### Post by mc4man on 2016-03-04
> **Cavsfan said:**
> Not sure whether that fix did it or the glitch sometimes does not happen. But it's been pretty consistant with the 6-8 or so second delay. Which of course beats 2-5 minutes. 



I just clicked on the Internet connection icon, then disconnect and rebooted. It went so fast that it did not even display the flashing icon at all. It was like a normal reboot and how it should be.

Does this mean I should add my name to that bug about the network causing a slow reboot?
Honestly I've no idea what that bug report is about other that it mentions systemctl stop networking hang / timeout which seems appropiate seeing as though something is hanging up the reboot & it obviously involves Network (manager)
So yeah, you could add yourself, if nothing advances soon then I'll file new bug mentioning that one as possibly the same.

---

### Post by QDR06VV9 on 2016-03-04
I had been lucky with the reboot hang until last nite..which seemed like it took an eternity honestly..lol
So I too added the "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci" which I seen the same results that Cavsfan reports 3-6 Seconds...Then I disconnected from the network-manager and did not notice any difference, Mind you I did not run a stop watch but nothing as noticeable as adding the line to Grub.
Regards

---

### Post by v3.xx on 2016-03-04
I also am trying to figure this out.  I do not see a big lag (**no** ssd, running standard hdd), but I do notice it now takes several seconds longer to reboot.

This is mate.

@runrickus
1 mississippi, 2 mississippi, 3... :P

---

### Post by QDR06VV9 on 2016-03-04
> **v3.xx said:**
> 
This is mate.
@runrickus
1 mississippi, 2 mississippi, 3... :P
Yes Exactly...Was you watching me...1 mississippi, 2 mississippi, 3... LOL
And yes Mate here also but you knew that:D

---

### Post by v3.xx on 2016-03-04
> **runrickus said:**
> Then I disconnected from the network-manager and did not notice any difference

Same here, didn't see a change.

I have not yet tried reboot=pci or reboot=bios, thats next.

This thread is tagged xubuntu, thats why the mate reference :)

---

### Post by Cavsfan on 2016-03-06
> **mc4man said:**
> Honestly I've no idea what that bug report is about other that it mentions systemctl stop networking hang / timeout which seems appropiate seeing as though something is hanging up the reboot & it obviously involves Network (manager)
So yeah, you could add yourself, if nothing advances soon then I'll file new bug mentioning that one as possibly the same.

This [Bug #1551351]("https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351") is mentioned in that other bug and it maybe more pertinent to our problem. I don't know which bug is the correct one.

> **runrickus said:**
> I had been lucky with the reboot hang until last nite..which seemed like it took an eternity honestly..lol
So I too added the "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=pci" which I seen the same results that Cavsfan reports 3-6 Seconds...Then I disconnected from the network-manager and did not notice any difference, Mind you I did not run a stop watch but nothing as noticeable as adding the line to Grub.
Regards

A few seconds beat the tar out of 2-5 minutes. :)

---

### Post by Cavsfan on 2016-03-06
I just rebooted but first clicked Disconnect in the Ethernet icon in the top Xfce panel and the reboot was instantaneous.

I don't think this is only on Xubuntu but since that is what I have, I tagged the thread that way.

---

### Post by Cavsfan on 2016-03-08
I forgot to disconnect from Ethernet before rebooting and it took about 6-8 seconds. I know if I do disconnect, reboot is instantaneous.

Does any one know which bug to report?

---

### Post by QDR06VV9 on 2016-03-08
Hey Cavsfan I think it might be this one [https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351)
But don't take that as gospel yet, might want to check with everyone else..I have 2 install of xenial on a laptop(WiFi)
Reboots are also instant on the lappy, and the tower with (Ethernet) with the fix add to grub takes the 4-8 seconds to reboot so not sure they can be related to systemctl status networking..
But hey i am only a happy tester here..

---

### Post by sammiev on 2016-03-08
> **Cavsfan said:**
> I just rebooted but first clicked Disconnect in the Ethernet icon in the top Xfce panel and the reboot was instantaneous.

I don't think this is only on Xubuntu but since that is what I have, I tagged the thread that way.

It's on all flavors of 16.04 and started on Feb 20 after an update to bind9 and network-manager the same day.

Not sure which package cause the problem.

I started a post on this back a week ago [here]("http://ubuntuforums.org/showthread.php?t=2315022").

---

### Post by harry332 on 2016-03-08
I have seen this 6-8 sec slowdown on rebooting for more than two weeks now.
Actually it is the shutting down which has become slow (6-8 sec).
This happened on 19th February when I upgraded isc-dhcp-client (4.3.3-5ubuntu5) to isc-dhcp-client (4.3.3-5ubuntu7).
Also 2 new dependencies was installed then: libdns162 and libisc160.
The old dependencies to libdns-export100 and libisc-export95 were removed.

So I would suggest this is an isc-dhcp and/or a bind9 issue.
There is something wrong with the leases for IP addresses.

---

### Post by harry332 on 2016-03-08
Right, Exactly what I just wrote.
I tested it this way.

1) With the newest setup with all upgrades installed (Ubuntu Gnome) there is 6-8 sec slow down when shutting down or rebooting. No delay at start up.

2) I then downgraded the package isc-dhcp-client (4.3.3-5ubuntu9) to isc-dhcp-client (4.3.3-5ubuunutu5). Also the packages libdns-export100 and libisc-export95 (both 9.9.5.dfsg-12.1ubuntu1) must be installed.

3) After one reboot (RAM) there is no more delays when shutting down or rebooting.

---

### Post by Doug S on 2016-03-09
6-8 seconds, I wish. I still have 90 seconds. Yesterday, I had to re-boot many many times and it drove me crazy. I'm a little upset with all the regressions in 16.04 at the moment.

---

### Post by Chazall1 on 2016-03-09
I still have a long boot up as well on Gnome Ubuntu. On my Ubuntu Mate 16.04 install system boots in seconds. Same ssd.

---

### Post by Cavsfan on 2016-03-09
> **harry332 said:**
> Right, Exactly what I just wrote.
I tested it this way.

1) With the newest setup with all upgrades installed (Ubuntu Gnome) there is 6-8 sec slow down when shutting down or rebooting. No delay at start up.

2) I then downgraded the package isc-dhcp-client (4.3.3-5ubuntu9) to isc-dhcp-client (4.3.3-5ubuunutu5). Also the packages libdns-export100 and libisc-export95 (both 9.9.5.dfsg-12.1ubuntu1) must be installed.

3) After one reboot (RAM) there is no more delays when shutting down or rebooting.

Most excellent find! I think I'll try that.

> **Doug S said:**
> 6-8 seconds, I wish. I still have 90 seconds. Yesterday, I had to re-boot many many times and it drove me crazy. I'm a little upset with all the regressions in 16.04 at the moment.

> **Chazall1 said:**
> I still have a long boot up as well on Gnome Ubuntu. On my Ubuntu Mate 16.04 install system boots in seconds. Same ssd.

As mentioned prior in this thread just changing the line in /etc/default/grub gets it to 6-8 seconds which beats 2-5 minutes like I was experiencing.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=#ff0000]reboot=pci[/COLOR]"
```

If anybody determines which bug to report this against, let me know and I'll me too it. :)

Thanks for the posts.

---

### Post by harry332 on 2016-03-09
The bug describing this issue is this: #1551351
[https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351)

Here is the latest comment:

[TABLE]
[TR]
[TD][LaMont Jones (lamont)]("https://launchpad.net/%7Elamont")             wrote             6 hours ago:                          
[/TD]
                       [TD="class: bug-comment-index"]           [ #21]("https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351/comments/21")           [/TD]
         [/TR]
            [/TABLE]
                               The plan here is  to restore the -export libraries for the time being,
until upstream  finishes the dhcp changes that are needed to have the common libs work.
This is in-progress.

---

### Post by Doug S on 2016-03-09
> **Cavsfan said:**
> As mentioned prior in this thread just changing the line in /etc/default/grub gets it to 6-8 seconds which beats 2-5 minutes like I was experiencing.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=#ff0000]reboot=pci[/COLOR]"
```There are at least two different root issues we are talking about herein, maybe more. The grub command line thing makes no difference for me, and actually makes my computer "klunk" pretty hard during re-boot (once it finally decides to actually re-boot). Keep in mind my computer is a server (I don't even notice the re-boot time as an issue on my test 16.04 desktop computer).

Look at [comment 15 in that bug report]("https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351/comments/15"), as there is talk of un-duplicating [bug 1551415]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1551415") from it.

---

### Post by Cavsfan on 2016-03-10
OK thanks harry332! I marked the [https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351](https://bugs.launchpad.net/ubuntu/+source/isc-dhcp/+bug/1551351) bug as affecting me too.

Let me know if the other bug needs attention as I see right now there is only one person on it.

@Doug S, I have no idea how a server works as all I have is one pc so thanks for the info.

---

### Post by ventrical on 2016-03-11
Booting fine here on old hdd.

regards..

---

### Post by Cavsfan on 2016-03-14
This is getting serious here on affected computers. the grub line doesn't work any more and if you forget to disconnect from the Ethernet before restarting, it's at least a 2 minute wait until anything happens.

Disconnecting from the internet prior to a restart makes it instantaneous.

---

### Post by QDR06VV9 on 2016-03-14
> **Cavsfan said:**
> This is getting serious here on affected computers. _**the grub line doesn't work any more**_ and if you forget to disconnect from the Ethernet before restarting, it's at least a 2 minute wait until anything happens.

Disconnecting from the internet prior to a restart makes it instantaneous.
Yes I can also confirm the grub line is useless now :(.. and also disconnecting from the internet prior to a restart makes it instantaneous.
Regards

---

### Post by Doug S on 2016-03-14
> **Cavsfan said:**
> This is getting serious here on affected computers. the grub line doesn't work any more and if you forget to disconnect from the Ethernet before restarting, it's at least a 2 minute wait until anything happens.

Disconnecting from the internet prior to a restart makes it instantaneous.It has always been exactly 90 seconds for me.
Thanks for the tip about disconnecting from internet first, while it doesn't make the pause disappear for me it reduces it to 25 seconds.
I had to re-boot many times over the weekend, and the 90 seconds was driving me crazy.

---

### Post by ventrical on 2016-03-14
18 seconds here on 80GB WD. (xubuntu)

Regards..

---

### Post by vasa1 on 2016-03-14
I made a live USB using *mkusb* from [http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso) (so Lubuntu, not Xubuntu). I keep it updated using zsync.

When I shut down using Lubuntu's menu (without turning off the network), I get a black screen with a blinking cursor at the top left corner of the screen for quite a while, at least a minute. My laptop doesn't power off as I'd expect it to do. By that time I panic and long-press the power switch to shutdown. This has happened each of the 3-4 times I've tried the live USB (each time made afresh using mkusb). It even happened when I used *sudo shutdown -P*.

Sometime today, I'll make yet another live USB and this time I'll turn of the network connection before shutting down and report back.

---

### Post by sammiev on 2016-03-15
Yesterday I removed the SSD from my laptop and put the HDD back in to do some updating on anther OS. 

Went to boot into my USB HDD and it took about 90 seconds to load any 16o4 OS after selecting the OS from the grub on the USB HDD. ( normal boot time 15 seconds )

Switch out the HDD for the SSD and selected to boot from the USB HDD again from my test unit and it booted in to Ubuntu 16o4 OS in 15 seconds. ( not booting from the SSD at all )

I never had the long boot times until yesterday outside of the shut down time with the network connection.

Switch out the SSD with the HDD many times over the last 2 days with the same results.

I know it's impossible but it's happening. I should of tried booting from USB HDD while the SSD or HDD were removed to see what happens with the boot times.

Wonder if this is all part of the same problem. I do not see this problem in the lower OS versions on my test unit.

---

### Post by Cavsfan on 2016-03-15
Glad to help with the point of disconnecting from the internet prior to a reboot/shutdown. I seen it somewhere on the bug I believe.

If you forget to disconnect first, that long wait is a killer! I'm sure they're working on it but, it would be nice to get that out of the way!

I installed the latest kernel today:
```
cavsfan@cavsfan-le-beast:~$ uname -a
Linux cavsfan-le-beast 4.4.0-13-generic #29-Ubuntu SMP Fri Mar 11 19:31:18 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

Software Updater was wanting to restart after the kernel was installed and thinking it would be quick I just clicked on it.
It was not quick. :frown:

[ATTACH=CONFIG]267827[/ATTACH]

---

### Post by QDR06VV9 on 2016-03-15
> **ventrical said:**
> 18 seconds here on 80GB WD. (xubuntu)

Regards..
Thanks and who is this masked man?? :D

> **sammiev said:**
> Yesterday I removed the SSD from my laptop and put the HDD back in to do some updating on anther OS. 

Went to boot into my USB HDD and it took about 90 seconds to load any 16o4 OS after selecting the OS from the grub on the USB HDD. ( normal boot time 15 seconds )

Switch out the HDD for the SSD and selected to boot from the USB HDD again from my test unit and it booted in to Ubuntu 16o4 OS in 15 seconds. ( not booting from the SSD at all )

I never had the long boot times until yesterday outside of the shut down time with the network connection.

Switch out the SSD with the HDD many times over the last 2 days with the same results.

I know it's impossible but it's happening. I should of tried booting from USB HDD while the SSD or HDD were removed to see what happens with the boot times.

Wonder if this is all part of the same problem. I do not see this problem in the lower OS versions on my test unit.
From what I have been reading it is odd that the laptops with WiFi are effected with this usually it is just the Ethernet card effected...they must be doing something now.

---

### Post by sammiev on 2016-03-15
I found my mistake. It was looking for the swap on sda from the SSD. I had 2 swaps as there is 2 ubuntu OS on the ssd and 4 ubuntu OS on the USB HDD.

Removed the swap from /etc/fstab on the USB HDD pointing to the SSD and now it boots in 15 seconds with only the one swap. 

My problem solved.

---

### Post by ventrical on 2016-03-15
> **runrickus said:**
> Thanks and who is this masked man?? :D


From what I have been reading it is odd that the laptops with WiFi are effected with this usually it is just the Ethernet card effected...they must be doing something now.

Hi Ho .. ubuntu  :)

---

### Post by QDR06VV9 on 2016-03-15
> **ventrical said:**
> Hi Ho .. ubuntu  :)

I kind of miss your smiling face...I guess i'm not online the same time as you anymore.

---

### Post by ventrical on 2016-03-17
> **runrickus said:**
> I kind of miss your smiling face...I guess i'm not online the same time as you anymore.

Just me being busy.  I am actually just getting time to check in now on a few things. Last night lost all my tabs in ff. My bad. :) I just clicked on the 'x' and the tabs were gone :)

hehe 

regards..:)

---

### Post by sammiev on 2016-03-17
Bind9 and so on was just updated and the problems with the shut down are now over. :)

---

### Post by Cavsfan on 2016-03-18
I can confrim that reboot is back to being instantaneous here. :)

---

### Post by sammiev on 2016-03-18
There is a new update again as of a hour a go for bind. If you use bind9 I would suggest you do not take the latest update as it breaks bind9 operations.

---

### Post by zika on 2016-03-18
> **sammiev said:**
> There is a new update again as of a hour a go for bind. If you use bind9 I would suggest you do not take the latest update as it breaks bind9 operations.With „break“ do You mean overwriting the file that is ame in two packages (bind9 and bin9-utils)? That is easily surpassed...

---

### Post by sammiev on 2016-03-18
> **zika said:**
> With „break“ do You mean overwriting the file that is ame in two packages (bind9 and bin9-utils)? That is easily surpassed...

Hi,

Bind9 gets broken and using address only 127.0.0.1 no long works with network-manager for Internet or VPN services.

E: /var/cache/apt/archives/bind9_1%3a9.10.3.dfsg.P4-1ubuntu2_amd64.deb: trying to overwrite '/usr/sbin/named-checkzone', which is also in package bind9utils 1:9.10.3.dfsg.P4-1ubuntu2

Synaptic will not even let you apply bind9 now as it said packages are broken and to use sudo apt-get install -f.

```
Preconfiguring packages ...
(Reading database ... 194648 files and directories currently installed.)
Preparing to unpack .../bind9_1%3a9.10.3.dfsg.P4-1ubuntu2_amd64.deb ...
Unpacking bind9 (1:9.10.3.dfsg.P4-1ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/bind9_1%3a9.10.3.dfsg.P4-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/sbin/named-checkzone', which is also in package bind9utils 1:9.10.3.dfsg.P4-1ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for systemd (229-2ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ufw (0.35-0ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/bind9_1%3a9.10.3.dfsg.P4-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```

You can clear the errors and when you run update & upgrade again the errors come back.

Synaptic will let you try to install bind9 after the errors are cleared out but the error just come back again while upgrading.

---

### Post by mc4man on 2016-03-18
Well those updates are still in proposed & bug had been filed
[https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1559090](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1559090)

---

### Post by Cavsfan on 2016-03-18
I do not even have bind installed, nor do I think I need it. 
Maybe that is why my reboot time is instantaneous now and I don't even know which update fixed it. But, it does appear to be fixed.

```
cavsfan@cavsfan-le-beast:~$ apt-cache policy bind9
bind9:
  Installed: (none)
  Candidate: 1:9.10.3.dfsg.P2-5
  Version table:
     1:9.10.3.dfsg.P2-5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```
```
cavsfan@cavsfan-le-beast:~$ apt-cache policy bind9utils
bind9utils:
  Installed: (none)
  Candidate: 1:9.10.3.dfsg.P2-5
  Version table:
     1:9.10.3.dfsg.P2-5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

This thread is not about BIND. I think the problem is solved or is there something else besides BIND involved?

---

### Post by Doug S on 2016-03-18
bind9 seems to be working fine for me.

Also, and finally!!!!, the shutdown side of re-boot is now very fast.
I got into the habit of going off to do something else for a couple of minutes during re-boot, and so missed my grub screen entirely (where I select which kernel I want) earlier today.

Note: I use servers, and no network manager or synaptic, so maybe that is the difference for me.

---

### Post by Doug S on 2016-03-18
> **Cavsfan said:**
> This thread is not about BIND. I think the problem is solved or is there something else besides BIND involved?There were common libraries between dhclient and bind, I believe.

---

### Post by sammiev on 2016-03-18
> **mc4man said:**
> Well those updates are still in proposed & bug had been filed
[https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1559090](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1559090)

Updated and fixed.

Thanks

---

### Post by zika on 2016-03-19
> **sammiev said:**
> Hi,

Bind9 gets broken and using address only 127.0.0.1 no long works with network-manager for Internet or VPN services.

E: /var/cache/apt/archives/bind9_1%3a9.10.3.dfsg.P4-1ubuntu2_amd64.deb: trying to overwrite '/usr/sbin/named-checkzone', which is also in package bind9utils 1:9.10.3.dfsg.P4-1ubuntu2

Synaptic will not even let you apply bind9 now as it said packages are broken and to use sudo apt-get install -f.

```
Preconfiguring packages ...
(Reading database ... 194648 files and directories currently installed.)
Preparing to unpack .../bind9_1%3a9.10.3.dfsg.P4-1ubuntu2_amd64.deb ...
Unpacking bind9 (1:9.10.3.dfsg.P4-1ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/bind9_1%3a9.10.3.dfsg.P4-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/sbin/named-checkzone', which is also in package bind9utils 1:9.10.3.dfsg.P4-1ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for systemd (229-2ubuntu1) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ufw (0.35-0ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/bind9_1%3a9.10.3.dfsg.P4-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```

You can clear the errors and when you run update & upgrade again the errors come back.

Synaptic will let you try to install bind9 after the errors are cleared out but the error just come back again while upgrading.It's history now but```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/bind9_1%3a9.10.3.dfsg.P4-1ubuntu2_amd64.deb
sudo apt install -f
```is a cure for situations like that.

---

### Post by Cavsfan on 2016-03-19
I do see where I have bind9-host installed.

```
cavsfan@cavsfan-le-beast:~$ apt-cache policy bind9-host
bind9-host:
  Installed: 1:9.10.3.dfsg.P4-4
  Candidate: 1:9.10.3.dfsg.P4-4
  Version table:
 *** 1:9.10.3.dfsg.P4-4 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

But, nothing else. So, If bind9 and bind9utils was causing your problem it was not causing mine that I can see.

---

### Post by sammiev on 2016-03-19
Thanks Cavsfan & zika, just didn't want the update coming back to effect more than the people that were in my shoes.

---

### Post by Cavsfan on 2016-03-19
> **sammiev said:**
> Thanks Cavsfan & zika, just didn't want the update coming back to effect more than the people that were in my shoes.

I guess it's finally fixed now. Through a few reboots it has been immediate, no pause. So, I guess I'll resolve this thread.

Thanks to all that contributed.

---

### Post by Cavsfan on 2016-03-26
For some unknown reason this has happened to me the past 2 days or twice at reboot.

I didn't bother to disconnect the ethernet first, but will try that next time.

---

### Post by Cavsfan on 2016-03-30
Guess it was just a glitch as it only happened 2 days...

All is well after that.

---

### Post by pumo on 2016-04-01
where I can found that bind download link?  even today starting is slow with wifi (with Kubuntu), with LAN cable  connected reboot is normal.

---

### Post by Cavsfan on 2016-04-01
> **pumo said:**
> where I can found that bind download link?  even today starting is slow with wifi (with Kubuntu), with LAN cable  connected reboot is normal.

You would just install it I guess. I don't use it although I have **bind9-host** that came installed on Xubuntu.

```
cavsfan@cavsfan-le-beast:~$ apt-cache policy bind9*
bind9-host:
  [COLOR=#ff0000]Installed[/COLOR]: 1:9.10.3.dfsg.P4-5
  Candidate: 1:9.10.3.dfsg.P4-5
  Version table:
 *** 1:9.10.3.dfsg.P4-5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
bind9utils:
  Installed: (none)
  Candidate: 1:9.10.3.dfsg.P4-5
  Version table:
     1:9.10.3.dfsg.P4-5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
bind9-dyndb-ldap:
  Installed: (none)
  Candidate: 8.0-2
  Version table:
     8.0-2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
bind9:
  Installed: (none)
  Candidate: 1:9.10.3.dfsg.P4-5
  Version table:
     1:9.10.3.dfsg.P4-5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
bind9-doc:
  Installed: (none)
  Candidate: 1:9.10.3.dfsg.P4-5
  Version table:
     1:9.10.3.dfsg.P4-5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages

```

---

