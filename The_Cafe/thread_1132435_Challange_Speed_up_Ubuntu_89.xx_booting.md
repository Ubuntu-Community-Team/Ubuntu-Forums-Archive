---
title: "Challange: Speed up Ubuntu 8/9.xx booting"
date: 2009-04-21
forum: The Cafe
---

### Post by BazookaAce on 2009-04-21
Hi,

I've been using 8.10 since november, and now i'm currently using 9.04 beta until the final release will be released on thursday. 

When i upgraded to 9.04 i must say i thought it would be much faster then 8.10, especially the booting-time. I'm using 9.04 on my Aspire One A150 with 1GB RAM, 1,6GHz CPU and 160GB HDD. 

"Well, there's your problem", you guys might think, but while my boot-time from the computer is powered on, till it actually hits the desktop and it's ready, it takes about 1 min 20 sec. 

I've seen, and heard about other people with Aspire One that have boot-times down to 15-20 seconds and i'm just sitting here and wondering "where did it go wrong?". 

I know that most of the guys with the "15-second-boot-time" has the Aspire One with SSD and not HDD, so it's faster by nature, but i wonder how fast i can make my 9.04 boot. 

So, are you up for the challange? Other "Ubuntans" who dreams about fast booting times can also join, and we can see who wins at the end. 

We obviously need some of the forums Ubuntu-gurus to make this happen, so join my quest, and let's reach at least 30 seconds. Amen

**NOTE:** I know the poll has some holes. Sorry about that!

---

### Post by smartboyathome on 2009-04-21
What about the people who's boot speeds are less than 15, 20-25, 30-35, or 40-45 seconds? Are they not allowed to vote?

---

### Post by mc4100 on 2009-04-21
> **BazookaAce said:**
> I know that most of the guys with the "15-second-boot-time" has the Aspire One with SSD and not HDD, so it's faster by nature, but i wonder how fast i can make my 9.04 boot. 
Your lack of SSD isn't the problem: I'm getting the super-fast boot on my AAO (with a proper spinning HDD), but I did a complete fresh install to Ext4, not an upgrade, and further removed loads of startup stuff. It can be done.

---

### Post by BazookaAce on 2009-04-21
> **smartboyathome said:**
> What about the people who's boot speeds are less than 15, 20-25, 30-35, or 40-45 seconds? Are they not allowed to vote?

What the hell are you running? :P

Edit: Btw, can i add new thing to the poll now, or am i screwed?

---

### Post by kpatz on 2009-04-21
I voted 35-40 seconds, but it depends on what machine we're talking about.

I just did a quick test using two VMs running on my Intrepid server.  One VM is Xubuntu 8.10, the other is Ubuntu 9.04 (latest RC).  I didn't have a stopwatch handy so my timing isn't very precise, but 9.04 booted close to twice as fast as 8.10.  It took about 30 seconds from grub to login page, plus another 10 or so after entering my password to reach the desktop, on Xubuntu 8.10.  9.04, running ext4, booted from grub to desktop in under 20 seconds (auto-login to desktop).

Both VMs were hosted on a quad-core Phenom II, 8 GB RAM, drive images on a XFS raid5 array.

So I guess that proves that Jaunty *does* boot up a lot faster.

I also timed a boot of an Windows XP SP3 VM and a Windows 7 beta VM, and it was a lot like Intrepid vs. Jaunty.  XP took about 25-30 seconds to reach the desktop, while Win7 rivalled Jaunty, landing at the desktop in about 20 seconds.  Both had 1.5 GB RAM.  When I gave XP 512MB RAM, it took about 45 seconds to boot.

---

### Post by ghindo on 2009-04-21
My laptop boots in 22 seconds with Ubuntu 9.04 using ext3, according to bootchart, but there isn't a poll option for me! :(

---

### Post by BazookaAce on 2009-04-21
My problem is that it takes maybe about 35 secs to login, but after that it is SLOW! What's causing this? I have disabled some services, removed and deleted alot of bloatware, and still, it's quite slow.

---

### Post by coldReactive on 2009-04-21
> **BazookaAce said:**
> My problem is that it takes maybe about 35 secs to login, but after that it is SLOW! What's causing this? I have disabled some services, removed and deleted alot of bloatware, and still, it's quite slow.

How big is your harddrive, how many cores do you have, do you dual boot, triple boot, etc?

There are other things to factor than just removing services and software.

---

### Post by BazookaAce on 2009-04-21
> **ghindo said:**
> My laptop boots in 22 seconds with Ubuntu 9.04 using ext3, according to bootchart, but there isn't a poll option for me! :(


Wow, sorry about that! It's 4:26 AM here in Norway, so yeah, i'm tired, and the poll reflects that!

Going to bed soon! (10min)

---

### Post by sertse on 2009-04-21
I wonder how much of it is due to Ubuntu.

On my Aspire One using Sidux, (1.66ghz, 1Gb ram, 120 Gb HHd) I get it to boot around 35secs.

Doesn't power on to grub take 10 secs anyways? the 10-15 secs are frankly surreal.

---

### Post by BazookaAce on 2009-04-21
> **coldReactive said:**
> How big is your harddrive, how many cores do you have, do you dual boot, triple boot, etc?

There are other things to factor than just removing services and software.

160GB. Having about 30GB available now. I do not dualboot, and i have single core (i think.. maybe dual).

Compiz, Emerald and Conky are installed. After a cold start it uses about 170MB RAM until i start Firefox etc.

edit: Ooh, i'm also using a custom kernel for the aspire one. Sickboy's kernel is it called.

---

### Post by ghindo on 2009-04-21
> **BazookaAce said:**
> Wow, sorry about that! It's 4:26 AM here in Norway, so yeah, i'm tired, and the poll reflects that!

Going to bed soon! (10min)Would you mind editing the poll?  Thanks :)

---

### Post by BazookaAce on 2009-04-21
How do i do that? I checked the editor, but could find anything.. Am i blind to??

---

### Post by lovinglinux on 2009-04-21
> **ghindo said:**
> My laptop boots in 22 seconds with Ubuntu 9.04 using ext3, according to bootchart, but there isn't a poll option for me! :(

I guess bootchart gives you only the time until you see the login screen. I have an average of 32 seconds in bootchart, but to get to my desktop takes much longer due to compiz, emerald and other stuff that are loaded on startup.

---

### Post by lovinglinux on 2009-04-21
> **BazookaAce said:**
> Compiz, Emerald and Conky are installed.

I bet those three are slowing you down considerably. I have Compiz and Emerald, but replaced Conky with screenlets, which also takes time to load.

---

### Post by ghindo on 2009-04-21
> **BazookaAce said:**
> How do i do that? I checked the editor, but could find anything.. Am i blind to??You might have to ask a forum moderator/administrator.> **lovinglinux said:**
> I guess bootchart gives you only the time until you see the login screen. I have an average of 32 seconds in bootchart, but to get to my desktop takes much longer due to compiz, emerald and other stuff that are loaded on startup.Right, but I'm not really sure how to accurately measure that time as well.  At least bootchart gives us a starting point.

---

### Post by youknowwhat4q on 2009-04-22
> **BazookaAce said:**
> 160GB. Having about 30GB available now. I do not dualboot, and i have single core (i think.. maybe dual).

Compiz, Emerald and Conky are installed. After a cold start it uses about 170MB RAM until i start Firefox etc.

edit: Ooh, i'm also using a custom kernel for the aspire one. Sickboy's kernel is it called.

1.6GHz?
80% full HD?
1GB RAM?

That's a super computer compared to my Ubuntu Desktop. Haha.  

I doubt that you would want to spend the big bucks and upgrade your processor.  But (I'm assuming that this is a desktop) you could always get a nice heat sink and overclock it.

What speed is your HD?  Slower speed HD's often bottleneck otherwise good computers.  There is also the option of getting another HD (nothing too big or fancy) for your OS and using your current HD as a secondary/media drive.

If it's an option upgrading your RAM couldn't hurt, but be sure that you get a quality product, because 1GB of good RAM is just as fast as 2GB of cheapo crap.

I'm more of a hardware guy than anything else, if you want any help finding stuff you can PM me.

Good luck.

---

### Post by hotweiss on 2009-04-22
My BIOS takes 32 seconds just to go through all of the steps... After grub, it only takes Ubuntu 9.04 26 seconds to boot. I am running ext 4 on a RAID 0 array.

---

### Post by alex_o on 2009-04-22
well 9.04 beta boots in just 1 minute and with 512mb ram, it used to be 1gb until a stick died! :(

---

### Post by mister_p_1998 on 2009-04-22
1m 30s with auto login, gdesklets and TED. I think this is fast compared to my XP box taking 3:30

Steve

---

### Post by kpatz on 2009-04-22
> **sertse said:**
> Doesn't power on to grub take 10 secs anyways? the 10-15 secs are frankly surreal.I only counted grub-to-desktop time, since that's the actual time it took Ubuntu to boot.

---

### Post by the8thstar on 2009-04-22
The computer takes 1m30s to get from Bios splash to full Gnome desktop.

I believe the dual boot with Windows 7, the desktop effects and the network detection on the wifi (DHCP) through Network Manager are actually causing the delay. I wish I knew how to improve on that.

---

### Post by 3rdalbum on 2009-04-22
On my Aspire One, I have upgraded to Jaunty. The time-to-X is much much faster; the time-to-usable-desktop is definitely slower and may be due to Network Manager (it seems to hang on "two green lights" for ten/fifteen seconds before displaying the connection and the desktop becoming usable).

---

### Post by BazookaAce on 2009-04-22
> **youknowwhat4q said:**
> 1.6GHz?
80% full HD?
1GB RAM?

That's a super computer compared to my Ubuntu Desktop. Haha.  

I doubt that you would want to spend the big bucks and upgrade your processor.  But (I'm assuming that this is a desktop) you could always get a nice heat sink and overclock it.

What speed is your HD?  Slower speed HD's often bottleneck otherwise good computers.  There is also the option of getting another HD (nothing too big or fancy) for your OS and using your current HD as a secondary/media drive.

If it's an option upgrading your RAM couldn't hurt, but be sure that you get a quality product, because 1GB of good RAM is just as fast as 2GB of cheapo crap.

I'm more of a hardware guy than anything else, if you want any help finding stuff you can PM me.

Good luck.

Well, the thing with the Aspire One A150 is that the maximum RAM i can get is 1,5GB. The CPU is a Intel Atom, and it's not possible to overclock it on the Aspire One due to the BIOS is locked and so on. I don't know how fast my HD is, but i guess the answer is just a google-search away.

> I bet those three are slowing you down considerably. I have Compiz and Emerald, but replaced Conky with screenlets, which also takes time to load.

Yeah i know, but i quite like the looks of my Ubuntu, and i would hate not to have them. I forgot that i have one screenlet enabled to. So i guess if i disable or remove Conky, Compiz, Emerald and Screenlets, i will probably get a much faster computer. 

About the custom kernel, i took the time yesterday and the results are:

[U]- Sickboy's kernel: -->Login - 30sec --> Desktop - 1min 4sec
- Stock kernel    : -->Login - 45sec --> Desktop - 1min 16sec
[/U]
I'm using Sickboy's kernel, but i'm having some problems with it. The system lags a little bit when i'm using it, and this doesn't happen with the stock kernel.

---

### Post by RavanH on 2009-05-02
If anyone suspects Network Manager to be causing delay, might I suggest to try out Wicd Manager. It's in the Jaunty repo :)

Or if you are not using wireless, remove Network Manager all together. Wired will just work without it too...

An eye-candy-but-handy and relatively light alternative to most is Cairo Dock (repo instructions on [http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#7-Ubuntu](http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en#7-Ubuntu) - use interpid)

But what I would like to know is which System Services and Startup Programs are really necessary and which are not?

For instance: I do not use Bluetooth so i unchecked it from the Startup Programs list. Same as Remote Desktop, Evolution Alarmnotify, Gnome Intro + Login Sound, all Tracker related stuff and Check for new hardware drivers... But what about Indicator Applet? What's that for? And Wrapper for AT SPI-register??

In the System Services list I find even more puzzling stuff that seems to be just more of the same. For instance, do I need ana-cron, atd *and* cron active at the same time? What is winbind for? Do I need alsa-utils *and* aumix? And what about acpid and apmd? Or klogd and sysklogd? :confused:

Any tips are much appreciated :)

---

### Post by Redundant Username on 2009-05-02
After grub to login screen is about 13 sceconds in 9.04. It would boot even faster if I wasn't using Wubi. My desktop loads in 4 seconds. I do not have an SSD.

---

### Post by alex_o on 2010-01-01
> **alex_o said:**
> well 9.04 beta boots in just 1 minute and with 512mb ram, it used to be 1gb until a stick died! :(

ok ive gotten new kit 9.10 with 4gb's of DDR3-1333 and an intel core 2 duo 2.66GHZ @ 3.25GHZ

the main drag for me is the 30 seconds that my bios + graphics go for :(

but it loads the desktop ALOT nicer :P

---

### Post by alex_o on 2010-01-31
> **BazookaAce said:**
> I don't know how fast my HD is, but i guess the answer is just a google-search away.

nope! just run hdparm with all apps closed

```
sudo hdparm -tT /dev/****
```

:P

---

### Post by k64 on 2010-01-31
Currently running Lucid Lynx, I have noticed less than a 10 second boot time.

---

