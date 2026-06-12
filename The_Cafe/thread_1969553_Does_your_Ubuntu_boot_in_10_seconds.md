---
title: "Does your Ubuntu boot in 10 seconds?"
date: 2012-04-30
forum: The Cafe
---

### Post by ubiquitin.jf on 2012-04-30
I've just installed Ubuntu 12.04 LTS on my main desktop PC and decided to rummage around the "Example Content" symlinked to the live environment desktop, as in all the years I've used Ubuntu (since 4.10) I've never bothered looking.

Inside that folder is a brief and minimalistic video titled "How fast.ogg" (it's in /usr/share/example-content/Ubuntu_Free_Culture_Showcase on an installed copy) which makes the claim that Ubuntu can boot in 10 seconds. Intrigued, I installed Bootchart and found that it takes 23.52 seconds to boot on my machine which is no dinosaur, but no Deep Blue either (most notably I lack an SSD).

So under what magical conditions does a fresh Ubuntu install boot in 10 seconds? Is it that fast for anybody here or is it more an aspirational figure which the devs would like to see some day?

---

### Post by Bucky Ball on 2012-04-30
Well, I did a minimal install that was getting to the login screen in 12 seconds consistently, but there were very few apps installed (and xfce4 rather than Gnome). I think that was 10.04 mini.iso. No other install of mine has ever gotten anywhere near that (although I think my 11.04 boots in about 20 seconds to login). I have an i3 with 4Gb of RAM.

---

### Post by TheMTtakeover on 2012-04-30
Does anyone have an SSD? I'm sure that would get under 10 seconds or right around there.

---

### Post by cecilpierce on 2012-04-30
Ha! It takes almost 10 secs for my HD to start after selecting from grub, getting slower every day it seems ):P

---

### Post by vasa1 on 2012-04-30
I imagine it would be somewhat more useful if people mention their CPU specs.

---

### Post by wyliecoyoteuk on 2012-04-30
Acer Aspire One,original L110, Atom 1.6ghz, new faster SSD,tweakes for SSD loading 11 seconds.:)

---

### Post by BrokenKingpin on 2012-04-30
I am running Xubuntu 12.04 on an SSD on a pretty fast PC. If you exclude the BIOS post and grub it does get to the login screen in about 10 seconds, maybe slightly longer. As for boot times I am pretty happy with this, even on my non-SSD machine.

I will vote yes as it is close enough :P.

---

### Post by Dry Lips on 2012-04-30
> **TheMTtakeover said:**
> Does anyone have an SSD? I'm sure that would get under 10 seconds or right around there.

Yes, my spare computer uses around 11,3 seconds from the grub to the login screen... It runs Mint 12 KDE. But I think the boot record is stored on the normal HDD, so it might be possible to speed that up a bit it didn't have to get information from the HDD.

---

### Post by samalex on 2012-04-30
I just reinstalled with Xubuntu 12.04 and my System76 Panp5 laptop boots to a login in just about 10 seconds, maybe a hair under.

---

### Post by rg4w on 2012-04-30
I was delightfully surprised to see how fast 12.04 boots.  But in all fairness, it seems it boots to the desktop pretty quickly, but is still doing significant initialization after the desktop is rendered so the time to start using it is perhaps on par with earlier versions.

---

### Post by chugtairizwan on 2012-04-30
yes it's almost ready with in 10 to 15 second..:popcorn:

---

### Post by Penguinnerd on 2012-04-30
Inspiron 1420, 1 Gb ram, 80 Gb 5400 rpm hard drive, 1.67 Ghz core 2 duo.

10.04 gets up and running in about 40 seconds as I currently have it configured.

It's due to the ancient 5400 rpm hard drive though.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
i timed a xubuntu 12.04 install on a ssd and i got ~15 seconds sda=ssd (130MB/s);sdb=hdd (80gb 7200rpm)
sda /
sdb /var
sdb /home
sdb /root -> /home/root
sdb /mnt/Windows (dedicated partition to a virtual box vdi file)

that os boot speed is twice as fast as POST and that saiy more about POST than it does about os boot speeds (Yes it takes ~30 seconds to post, includes the ~20 to send output the the monitor before the MB's splash screen)
running a A6-3500 APU


on a 240 MB/s ssd set up similar i have pulled ~8 seconds on 10.04 (had to RMA that ssd 3 times and they sent the that slower one above)
AMD Phenom II x4 965

---

### Post by mips on 2012-04-30
Xubuntu 12.04 with some services disabled takes 27sec.
CPU: Q6600, HDD: 7200rpm seagate.

On startup without any apps open it sucks up about 500MB of RAM, things feel a bit sluggish so Xubuntu is gonna get the boot and replaced with a minimal base install + xfce 4.10 soon (like I had in 11.10).

---

### Post by Mopar1973Man on 2012-04-30
For what its worth... My system is booted well under one minute but now switch to Windows and it might take a up to 2-3 minutes to fire up...

So to give a estimate I would say about 20-30 seconds on Ubuntu 11.10.

---

### Post by CharlesA on 2012-04-30
I haven't timed my server boot time since installing Precise, but on Lucid it took close to a minute to boot up fully.

Boot time really doesn't matter when something is only rebooted to boot into a new kernel. ;)

---

### Post by TheMTtakeover on 2012-04-30
> **Mopar1973Man said:**
> For what its worth... My system is booted well under one minute but now switch to Windows and it might take a up to 2-3 minutes to fire up...
 
So to give a estimate I would say about 20-30 seconds on Ubuntu 11.10.
 
Really? Windows 8 boots faster on my inspiron than any buntu I've ever had on it

---

### Post by |{urse on 2012-04-30
I have a fresh install of 11.10 running on an ssd, it still takes a slight bit longer than 10 seconds.

---

### Post by TheMTtakeover on 2012-04-30
> **|{urse said:**
> I have a fresh install of 11.10 running on an ssd, it still takes a slight bit longer than 10 seconds.
 Slightly off topic but does Ubuntu auto-detect an SSD? or do you have to enable TRIM manually?

---

### Post by CharlesA on 2012-04-30
> **TheMTtakeover said:**
> Slightly off topic but does Ubuntu auto-detect an SSD? or do you have to enable TRIM manually?
TRIM is enabled in the kernel from what I've heard.

---

### Post by goldshirt9 on 2012-04-30
I am running Kubuntu 12.04 on a
Fujitsu lifebook AH531

Intel Core i5 Sandybridge 2430M 2.4GHz,
 2x4GB DDR3 1333MHz, Dual Channel Support 
Seagate 320GB Momentus XT 2.5" Hybrid HDD/SSD - SATA-II 7200rpm 32MB Cache


from boot to password screen 11 sec's.
As far as i know i have disabled nothing in the system :lolflag:.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
> **CharlesA said:**
> TRIM is enabled in the kernel from what I've heard.
really? we don't need the discard option in fstab anymore with the current kernel (3.2.0-24)?

---

### Post by CharlesA on 2012-04-30
> **pqwoerituytrueiwoq said:**
> really? we don't need the discard option in fstab anymore with the current kernel (3.2.0-24)?
That's what I heard, but the only source I can find is this:
[http://ubuntuforums.org/showthread.php?t=1926044](http://ubuntuforums.org/showthread.php?t=1926044)

---

### Post by keithpeter on 2012-04-30
Hello All

Recycled HP workstation, Quad core xeon, 4Gb ram, slow as molasses mechanical hard drive, doubles as a handy room heater.

From pressing the power switch to usable desktop (autologin enabled): 55 seconds
(From pressing the power switch to Grub: 25 seconds)

I only boot up once a day, and most days I use hibernate which knocks about 20 seconds off the second part of the boot.

---

### Post by Uncle Spellbinder on 2012-04-30
Ubuntu 12.04 LTS

HP Pavilion - Intel Core i-5 - 3.1oGHz - 8GB Memory.

20 to 25 seconds to boot into login screen.

---

### Post by Dry Lips on 2012-05-01
Say trim is automatically enabled... I guess it still is a good idea to set a low swappiness value?

---

### Post by mips on 2012-05-01
> **Dry Lips said:**
> Say trim is automatically enabled... I guess it still is a good idea to set a low swappiness value?

You should not be running swap on a ssd imho, move it to a normal drive.

---

### Post by Dry Lips on 2012-05-01
> **mips said:**
> You should not be running swap on a ssd imho, move it to a normal drive.

Ok, I'll do that on my main computer, but I was hoping that I didn't have to use a normal drive on my server. :/

---

### Post by Warpnow on 2012-05-01
On my acer aspire one netbook I got Ubuntu so boot in 8 seconds, but it took disabling alot of services.

---

### Post by Maheriano on 2012-05-01
I didn't test just the bootup which could very well be under 10 seconds but I did just do a test of pushing the power button to seeing the desktop and it was 25 seconds.That's on a blazingly fast Samsung Series 9 with a Core i7 and solid state drive.

---

### Post by mips on 2012-05-06
> **mips said:**
> Xubuntu 12.04 with some services disabled takes **27sec**.
CPU: Q6600, HDD: 7200rpm seagate.

On startup without any apps open it sucks up about 500MB of RAM, things feel a bit sluggish so Xubuntu is gonna get the boot and replaced with a minimal base install + xfce 4.10 soon (like I had in 11.10).

Ok so today I installed xfce 4.10 on a base install and I'm now booting in 16.73 seconds. That's 10 seconds shaved off!

---

### Post by rk0r on 2012-05-06
10 seconds is slightly pushing it, i have a bootloader to select different OS so that may add some time to the boot. either way its not something that's an issue, as long as the OS loads up in ample time.

---

### Post by Cavsfan on 2012-05-06
It probably would but, I notice it takes more time recognizing my 1TB USB drive than anything else. 
If I unplugged that it probably would, but I am not going to.
It definitely boots up faster than Windows 7.

---

### Post by catlover2 on 2012-05-06
It takes 13 seconds with one of [these](http://www.newegg.com/Product/Product.aspx?Item=N82E16820226236) from the GRUB2 menu to KDE desktop. This is with ArchLinux on the machine in my signature. With my BIOS added, it takes 36 seconds. (!)

---

### Post by LillyDragon on 2012-05-06
Well, I'm using WUBI on this laptop, so I'm not sure if that has anything to do with my boot time, because it sits at a blank screen for a few seconds after the grub menu, before making it to the login screen. Otherwise the boot process would probably take less than ten seconds, but either way it still boots faster than Windows 7 does! :P

---

### Post by Rodney9 on 2012-05-07
My laptop from grub takes 45 seconds.

Dual-Core T4400@2.20Ghz with 2Gb ram

---

### Post by jespdj on 2012-05-07
I have a laptop with an SSD.

Boot time: approximately 18 seconds.

I timed from GRUB (went into the GRUB menu and pressed Enter to start booting Ubuntu) until the moment the login screen was ready to accept my password.

This is with Ubuntu 12.04, 64-bit. I have some extra stuff installed, for example MySQL Server, which probably adds some time to the boot process.

---

### Post by EnGorDiaz on 2012-05-07
> **TheMTtakeover said:**
> Does anyone have an SSD? I'm sure that would get under 10 seconds or right around there.

im about to test on patriot wildfire 120gb

---

### Post by EnGorDiaz on 2012-05-07
i get 10.93 seconds on my patriot wildfire from grub to untiy desktop

---

### Post by a2j on 2012-05-07
~10 sec on main workstation and netbook, both with SSDs. Kubuntu and Xubuntu.

What is wrong with having swap on SSD? If you have good amount of RAM, it will rarely use it. But when you need it, it will swap faster than regular hard drive.

---

### Post by mips on 2012-05-07
> **a2j said:**
> ~10 sec on main workstation and netbook, both with SSDs. Kubuntu and Xubuntu.

What is wrong with having swap on SSD? **If you have good amount of RAM, it will rarely use it**. But when you need it, it will swap faster than regular hard drive.

Then you will be fine.

---

### Post by CharlesA on 2012-05-07
> **mips said:**
> Then you will be fine.
Yep. The only thing swap is really used for is hibernation, well, unless you run out of memory. ;)

---

### Post by codingman on 2012-05-07
Lenovo 3000 N100 Core 2 Duo T700, 3 gb ram. Running at about 25 seconds from grub. However, my other computer, an ASUS A8n-SLI, 4gb ram, Athlon 64 FX-55, runs Fedora for 8 seconds of boot, and Ubuntu for 10 seconds.

---

### Post by ratcheer on 2012-05-07
I cannot even boot Arch Linux in under 10 seconds. It takes 12. Ubuntu 12.04 is more like 22.

Tim

---

### Post by Rodney9 on 2012-05-07
> **Rodney9 said:**
> My laptop from grub takes 45 seconds.

Dual-Core T4400@2.20Ghz with 2Gb ram

Above was with Ubuntu 12.04

On Xubuntu 12.04 - 25sec


Rodney

---

### Post by oldfred on 2012-05-07
Ubuntu says it it less than 10 sec. Last commands posted in dmesg.

```
[    8.489004] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.489384] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.521985] Bluetooth: RFCOMM TTY layer initialized
[    8.521990] Bluetooth: RFCOMM socket layer initialized
[    8.521992] Bluetooth: RFCOMM ver 1.11
```

And I thought I had Bluetooth turned off?

But I count from power switch and before I mounted extra partitions it was 20sec and then mounting a couple of NTFS & ext3 partition it balooned by 25% to 25sec.

---

### Post by ratcheer on 2012-05-08
> **oldfred said:**
> And I thought I had Bluetooth turned off?



To turn off bluetooth, edit /etc/init/bluetooth.conf and comment out the line near the top that says, "start on started dbus".

Tim

---

### Post by oldfred on 2012-05-08
@   	ratcheer
Thanks Tim,  that removed the bluetooth entries.

---

### Post by Retor on 2012-08-12
"10 seconds"? HOW!?!

I have a new install (today) and it takes 38 seconds from I hit enter at the grub menu until I see the complete desktop (auto login). 

That's almost 4 times the ad, and I have a Intel Sandy Bridge i5 CPU (2410M),  2.30GHz × 4. And 4 GB of ram.

Not an SSD, though. Maybe that's why.

---

### Post by Jakin on 2012-08-12
My system is has a Seagate Momentus XT, my grub is set up to wait indefinitely for me to choose an OS, Kubuntu 11.10 amd64 boots in 4 seconds, starting from the moment i choose it in grub- to the login screen. I didn't do anything special to the system to make it boot faster either, if anything i bogged it down.

---

### Post by mips on 2012-08-12
> **Retor said:**
> "10 seconds"? HOW!?!

I have a new install (today) and it takes 38 seconds from I hit enter at the grub menu until I see the complete desktop (auto login). 

That's almost 4 times the ad, and I have a Intel Sandy Bridge i5 CPU (2410M),  2.30GHz × 4. And 4 GB of ram.

Not an SSD, though. Maybe that's why.

That can't be right. What HDD do you have?

---

### Post by KiwiNZ on 2012-08-12
I just don't get the hang up on boot times, are people re-booting their devices every 15 minutes, hourly, 10 times a day?

I Re-boot maybe twice a month, 10 seconds, 30 seconds 1.5 minutes it just does not matter. There in excess of a million seconds in a month does 20 seconds really count that much?

---

### Post by Jakin on 2012-08-12
> **KiwiNZ said:**
> I just don't get the hang up on boot times, are people re-booting their devices every 15 minutes, hourly, 10 times a day?

I Re-boot maybe twice a month, 10 seconds, 30 seconds 1.5 minutes it just does not matter. There in excess of a million seconds in a month does 20 seconds really count that much?

The setup i was refuring to is a laptop, so yes; it is shutdown and booted frequently.

Its also about the hardware you paid for- if you know it should be booting around a specific time, and it doesn't then something is wrong.

---

### Post by KiwiNZ on 2012-08-12
> **Jakin said:**
> The setup i was refuring to is a laptop, so yes; it is shutdown and booted frequently.

Its also about the hardware you paid for- if you know it should be booting around a specific time, and it doesn't then something is wrong.

If you are rebooting a laptop so often that 10 seconds or 30 seconds is vital then put it to sleep as opposed to shutting down, your hardware will thank you for it.

---

### Post by CharlesA on 2012-08-12
> **kiwinz said:**
> if you are rebooting a laptop so often that 10 seconds or 30 seconds is vital then put it to sleep as opposed to shutting down, your hardware will thank you for it.
+1.

---

### Post by Primefalcon on 2012-08-12
The 10 secs would be on a decent machine with ssd and a bare base install (no extra programs starting)

---

### Post by Paqman on 2012-08-12
> **KiwiNZ said:**
> I just don't get the hang up on boot times

Performance in general is a good thing. People only turn the machine on when they've got a task in mind. If they're sitting there waiting for the OS to get out of the way before they can do that it's natural for them to find it a bit annoying.

I personally think resume times are just as (if not more) important.

---

### Post by KiwiNZ on 2012-08-12
> **Paqman said:**
> Performance in general is a good thing. People only turn the machine on when they've got a task in mind. If they're sitting there waiting for the OS to get out of the way before they can do that it's natural for them to find it a bit annoying.

?

I turn my work machines on at the beginning of the day, my home machines stay on until I need to reboot. if I only turned my machines on when I had a task to do I would be turning on and off hundreds of times per day.

---

### Post by Jakin on 2012-08-12
Is there really any proof that putting your computer to sleep, is better for it versus turning it off and on?

---

### Post by azangru on 2012-08-12
> **KiwiNZ said:**
> I turn my work machines on at the beginning of the day

And isn't it just nice when it is all ready to work in 15-20 seconds after you've pushed the button, instead of in a couple of minutes?

My parents' computer is a Toshiba laptop with Windows 7 on it (yes, they haven't seen the light yet), and because of the antivirus software and whatnot it takes over two minutes, maybe more, before it is usable. It gets on the nerves, really.

---

### Post by KiwiNZ on 2012-08-12
> **azangru said:**
> And isn't it just nice when it is all ready to work in 15-20 seconds after you've pushed the button, instead of in a couple of minutes?

My parents' computer is a Toshiba laptop with Windows 7 on it (yes, they haven't seen the light yet), and because of the antivirus software and whatnot it takes over two minutes, maybe more, before it is usable. It gets on the nerves, really.

Don't know, don't care I turn it on then go and have a meeting or such like .

---

### Post by KiwiNZ on 2012-08-12
> **Jakin said:**
> Is there really any proof that putting your computer to sleep, is better for it versus turning it off and on?

Powering off and on a lot can "stress" the components, eg the minute IC's on the chips and solder points due to expansion and contraction. Also electrical stress on components is a factor. You need to balance that however with the cost of running devices on standby.

As for Laptops if you are using them mainly on the desk top and you have one with a removable battery, remove the battery when fully charged and store it in a cool dry location and run purely off the mains. If you do not have a removable battery it is probably best to power off if the machine is to be unused for a period of time and disconnect the power source.

---

### Post by Jakin on 2012-08-12
> **KiwiNZ said:**
> Powering off and on a lot can "stress" the components, eg the minute IC's on the chips and solder points due to expansion and contraction. Also electrical stress on components is a factor. You need to balance that however with the cost of running devices on standby.

As for Laptops if you are using them mainly on the desk top and you have one with a removable battery, remove the battery when fully charged and store it in a cool dry location and run purely off the mains. If you do not have a removable battery it is probably best to power off if the machine is to be unused for a period of time and disconnect the power source.

I was unaware of the battery thing, but wouldn't sleep mode do the exact same thing? In sleep low power, and wakeup at full power, cause stress as well?

I don't really know how the life-span of a computer works one way or the other, as you say, i'll try to get used to putting in sleep mode, rather than powering off.

---

### Post by Paqman on 2012-08-12
> **KiwiNZ said:**
> ?

I turn my work machines on at the beginning of the day, my home machines stay on until I need to reboot. if I only turned my machines on when I had a task to do I would be turning on and off hundreds of times per day.

Right. Do you suppose everybody does things exactly the same as you?

A lot home computers do stay off until they're needed.

> **Jakin said:**
> I was unaware of the battery thing, but wouldn't sleep mode do the exact same thing? In sleep low power, and wakeup at full power, cause stress as well?

In sleep much of the machine is powered down, so much of it will cool. So resuming from suspend will cause a thermal cycle.

Solder has such a low melting point that even at the low temperatures in a computer it's actually operating in the same kind of thermal regime as the turbine blades in a jet engine. Strange but true.

---

### Post by KiwiNZ on 2012-08-12
> **Paqman said:**
> Right. Do you suppose everybody does things exactly the same as you?

A lot home computers do stay off until they're needed.


I answered a post directed at me, I was not answering on behalf of humanity.

---

### Post by vasa1 on 2012-08-12
> **KiwiNZ said:**
> I just don't get the hang up on boot times...
But that video was supplied by the installation, implying that someone among those who compiled the installation has the "hang up".

---

### Post by KiwiNZ on 2012-08-12
> **vasa1 said:**
> But that video was supplied by the installation, implying that someone among those who compiled the installation has the "hang up".

?????????

---

### Post by vexorian on 2012-08-12
My Desktop takes 13 seconds from the time I select ubuntu in GRUB. It is a core 2 duo overclocked to 3.1 Ghz. 32 bits ubuntu, 2 GB of RAM

My netbook needs 21 seconds. It is an Atom with 1.6 Ghz.

However, before grub is enabled, both computer waste precious seconds. I'd say 6 seconds. It used to be much worse in Ubuntu 10.10. I think grub 2 got faster.


I just let my computer sleep when I don't have to use it. I hope it does not use much more energy than when turned off. (I doubt it as there is always ghost drain and the such).

---

### Post by granjerox on 2012-08-19
My Specs:

[LIST]
[*]Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
[*]4 GB Ram
[*]SSD Agility 3 120GB ext4
[*]Ubuntu 12.04 Desktop x64
[/LIST]
Time between 7 - 9 Secs. Bootchart attached. Bootchart claims 28 secs because a 20sec sleep time by default to catch up login processes.

I've added preload and disabled cupsd, bluetooth and saned.

I've been looking around a good tutorial to understand boot process. Do you know any?

---

### Post by zer010 on 2012-08-19
nope, but with my specs....

---

### Post by Buntu Bunny on 2012-08-19
Well you know, I never timed it. All I know is that it boots faster than any version of Windows I ever used!!!  :lol:

---

### Post by irv on 2012-08-19
Right after a fresh install of 12.04 and a list of about 25 apps. And a new 180gig SSD in my Dell Inspiron 1521 with 4gig of RAM and a AMD 64 processor. It was booting from power on to desktop in 15 seconds.

Now I just installed Black Opal which is still Ubuntu 12.04 but with some extra apps and some extra effects. Now it take 30 seconds total. From power on to logon is 20 seconds from logon to desktop 10 seconds.

Just for the record when I was running Win7 on a 500gig Hard Drive it took 2 minutes 20 seconds to a usable desktop. And that was when it wasn't doing update. That could take up to 6 minutes or longer in some cases.

---

### Post by viperdvman on 2012-08-20
Well, testing both my computers... my Asus AMD V105 netbook that's just about a year and a half old, and custom my Core i3 desktop with a 4 1/2 to 5 year old SATA 3.0gb/s hard drive. Both run the same Ubuntu 12.04, but the desktop is more heavily loaded with KDE and GNOME Shell built on top of it in addition to Unity.

The **desktop** goes from Grub to login in **28 seconds**. The **netbook** goes from Grub to login in battery power in **37 seconds**. So no, they don't boot in 10 seconds. I'm sure my Bodhi Linux on the same desktop goes much faster. Installing a much newer hard drive, possibly even an SSD, will definitely speed up boot times on my desktop. 

But any way I slice it, both also have Windows 7 installed in a dual-boot environment. And on both computers, Ubuntu boots up far faster than Windows. And Ubuntu is useful pretty much right when you get your desktop. Windows, on the other hand, has to start up all its startup apps, which easily takes up to another minute.

So it may not boot up in 10 seconds like advertised on those old videos, it still boots up a lot faster, and is useful a lot faster than Windows is :D

---

### Post by jfreak_ on 2012-08-20
LOL. What's 10 seconds? ROFL 

PS: Look at my sig

---

### Post by irv on 2012-08-20
I think to be fair and show the exact time of boot. we should all install Bootchart
[ATTACH]222930[/ATTACH]  
and post our boot time. Here is mine.
[ATTACH]222931[/ATTACH]
EDIT: as you can see, my was just under 20 seconds. And I guessed mine at 30 seconds by counting.

---

### Post by irv on 2012-08-20
All those that say they are booting in 10 seconds or less, I would like to see their bootcharts. I know it is possible in the right conditions. My wife has a Chromebook that boots in 7 seconds. It load very little at boot time and run everything off the Internet.

---

### Post by DoktorSeven on 2012-08-20
I don't reboot unless absolutely necessary, making boot time kind of irrelevant. :)

---

### Post by synaptix on 2012-08-20
Of all the Ubuntu versions I've used starting with 9.10, the only one that has ever come close to a 10 second boot time was 10.10 Meerkat that was clocking in at 17 seconds with 10.04 coming in closely behind at 17.5 seconds.

---

### Post by irv on 2012-08-20
> **synaptix said:**
> Of all the Ubuntu versions I've used starting with 9.10, the only one that has ever come close to a 10 second boot time was 10.10 Meerkat that was clocking in at 17 seconds with 10.04 coming in closely behind at 17.5 seconds.
What are you running now? And how fast do it boot?

---

### Post by KiwiNZ on 2012-08-20
Never time it, 10 seconds , 15 seconds, 45 seconds is irrelevant in my life.

---

### Post by quids on 2012-08-20
9 seconds on my HTPC
AMD A8-3870k (3.0GHz Quad core) with OCZ Agility 3 60GB SSD. Its running Ubuntu 12.04 booting directly into XBMC.
Might be a bit quicker if I ever get around to removing all the surplus stuff Ubuntu comes with.

Shutdown time though is crazy - under 2 secs. I couldn't switch it off faster unless I flicked the switch off at the mains. :p


My desktop computer boots up in about 11 secs. 
AMD 1100T (3.3GHz Hex core) with OCZ Vertex 4 256GB SSD, a Vertex 2 60GB SSD (for /tmp and Swap) and a couple of 2TB Harddrives.

---

### Post by irv on 2012-08-20
> **quids said:**
> 9 seconds on my HTPC
AMD A8-3870k (3.0GHz Quad core) with OCZ Agility 3 60GB SSD. Its running Ubuntu 12.04 booting directly into XBMC.
Might be a bit quicker if I ever get around to removing all the surplus stuff Ubuntu comes with.

Shutdown time though is crazy - under 2 secs. I couldn't switch it off faster unless I flicked the switch off at the mains. :p


My desktop computer boots up in about 11 secs. 
AMD 1100T (3.3GHz Hex core) with OCZ Vertex 4 256GB SSD, a Vertex 2 60GB SSD (for /tmp and Swap) and a couple of 2TB Harddrives.
Do you have Bootchart installed? See my post #76 in this thread. It is a very small program that will time your boot up.

---

### Post by synaptix on 2012-08-20
> **irv said:**
> What are you running now? And how fast do it boot?

I don't run Ubuntu on my desktop anymore, only Windows 7.

Though if you'd like some numbers I could clean install 12.04 installation when .1 is released and post some numbers. :)

My laptop does run 12.04 solely right now, but it's not as powerful as my desktop.

---

### Post by irv on 2012-08-20
> **synaptix said:**
> I don't run Ubuntu on my desktop anymore, only Windows 7.

Though if you'd like some numbers I could clean install 12.04 installation when .1 is released and post some numbers. :)

My laptop does run 12.04 solely right now, but it's not as powerful as my desktop.
As far as you laptop goes it still would be nice to know how long it takes to boot up. I have an old laptop but I boosted up the RAM from 2 to 4gig and install a SSD and it gave it new life to an old machine. I wish I could do this to myself.

---

### Post by synaptix on 2012-08-20
Desktop system:
AMD Athlon II 635 X4 2.9GHz
Seagate 700GB SATA HDD 7,500RPM
AMD/ATI Radeon HD4200 256MB
Catalyst 12.6
Chipset driver 12.6

[COLOR=DarkRed][B]OS: Ubuntu 12.04 LTS x86_64
21.22 seconds to active desktop (best out of 3):[/B][/COLOR]

[IMG]http://img860.imageshack.us/img860/6223/ubuntubootspeed.png[/IMG]

[COLOR=RoyalBlue][B]OS: Windows 7 Home Premium x64 (as comparison of boot times)
16 seconds to active desktop:[/B][/COLOR]

[IMG]http://img221.imageshack.us/img221/5251/windows7bootspeed.png[/IMG]

---

### Post by Moose on 2012-08-20
I can't remember all the specs but my laptop is a HP G62 Notebook PC, 2GB of RAM, Dual Core i3 processor. 
 
Boots up in between 8-15 seconds on average. With about 17 being my slowest. But that was when i was using Ubuntu 10.04 and hadn't done much to clean up and keep it running smooth. All in all i think Ubuntu has kept pretty close to the speed it promises.
 
-Anarchy

---

### Post by irv on 2012-08-20
> **AnarchyTech said:**
> I can't remember all the specs but my laptop is a HP G62 Notebook PC, 2GB of RAM, Dual Core i3 processor. 
 
Boots up in between 8-15 seconds on average. With about 17 being my slowest. But that was when i was using Ubuntu 10.04 and hadn't done much to clean up and keep it running smooth. All in all i think Ubuntu has kept pretty close to the speed it promises.
 
-Anarchy
 
If you run Bootchart you can see the boot time.

---

### Post by Moose on 2012-08-20
> **irv said:**
> If you run Bootchart you can see the boot time.
 Good to know.

---

### Post by irv on 2012-08-20
> **AnarchyTech said:**
> Good to know.

I forgot to say you need to install it first. It puts a boot chart in /var/log/bootchart directory so you can view it. you need to make it bigger so you can read it.
just run:
```
sudo apt-get install bootchart
sudo apt-get install pybootchartgui
```

---

### Post by Lucradia on 2012-08-21
Definitely not, even if it's the only OS on my system and even if it has no password to login, and no encryption and no sep. home. I think the bottleneck mainly is the GPU I have, which is two generations old in comparison to the motherboard. (So is the DVD Drive I have.)

@synaptix you don't need BootRacer to get windows boot results. [There is a bootchart-like program provided by Microsoft themselves.]("http://techie-buzz.com/tips-and-tricks/windows-boot-performance-wpt.html")

---

### Post by Retor on 2012-08-21
> **mips said:**
> That can't be right. What HDD do you have?

Computer says: Hitachi Travelstar 5K750


Serial ATA-300, 8 MB buffer, 5400 rpm, 12 sec avg. seek time.

[http://reviews.cnet.com/internal-hard-drives/hitachi-travelstar-5k750-hts547564a9e384/4505-9998_7-34411666.html](http://reviews.cnet.com/internal-hard-drives/hitachi-travelstar-5k750-hts547564a9e384/4505-9998_7-34411666.html)

---

### Post by Mr. Picklesworth on 2012-08-21
Dell XPS 13: End of POST to functioning login screen in ~9 seconds :)

Desktop gets to a login screen in about 10.

They both boot from SSDs, of course. I think the desktop used to do 20 or so booting from the HDD.

---

### Post by mips on 2012-10-21
Ok it's not Ubuntu but a Manjaro net install running XFCE 4.10. I always thought it booted fast but never imagined it was this fast, 9893ms (<10s)

Core2Quad 6600 @ 2.4GHz, 4GB RAM, Seagate Barracuda 7200.10 ST3250310AS 250GB 7200 RPM 8MB Cache SATA 3.0Gb/s 3.5"

I have systemd-readahead-collect.service systemd-readahead-replay.service enabled for systemd

Click on link for bigger image
[[img]http://ompldr.org/tZnlvaw[/img]](http://ompldr.org/vZnlvaw)

---

### Post by mips on 2012-10-21
> **Retor said:**
> Computer says: Hitachi Travelstar 5K750


Serial ATA-300, 8 MB buffer, 5400 rpm, 12 sec avg. seek time.

[http://reviews.cnet.com/internal-hard-drives/hitachi-travelstar-5k750-hts547564a9e384/4505-9998_7-34411666.html](http://reviews.cnet.com/internal-hard-drives/hitachi-travelstar-5k750-hts547564a9e384/4505-9998_7-34411666.html)

38s seems slow but then it's a 5400rpm drive. Maybe post the output of bootchart for your system. If you are using ext4 also have a look at e4rat but I have no idea how that compares to upstart.

---

### Post by Linuxratty on 2012-10-21
A little longer than 10 seconds...Not timed with with a stop watch.:)
 Actually,I really don't care how fast it boots..As long as it's under a minute,I'm happy.

---

### Post by ~LoKe on 2012-10-21
8:30 from boot to Desktop.

---

### Post by ~LoKe on 2012-10-21
Disabled Bluetooth, tried again.

7:41, on 12.10.

[img]http://i.imgur.com/Rarxm.png[/img]

---

### Post by mmstick on 2012-10-21
10 seconds with Ubuntu 12.10? My 2TB 5400RPM drive boots to the desktop in much less than that. Of course, I have a Phenom II X6 3.2Ghz processor in this machine to ease the loading process.

---

### Post by ~LoKe on 2012-10-21
> **mmstick said:**
> 10 seconds with Ubuntu 12.10? My 2TB 5400RPM drive boots to the desktop in much less than that. Of course, I have a Phenom II X6 3.2Ghz processor in this machine to ease the loading process.

I'd like to see the bootchart on that.  I don't see a 5400RPM drive allowing those kinds of speeds.

---

### Post by cprofitt on 2012-10-21
My machine takes roughly 18.7 seconds to get to the login screen.

Specs:

Core i7-3720QM
16 GB ram
320 GB 7200 RPM Hitachi

I am pretty sure with an SSD I would get under 10 seconds, but not with spinning disks.

---

### Post by Starcruiser322 on 2012-10-21
Dual-Core 2.4 GHz, 6 GB RAM, SATA running RAID config @ 7200 rpm each disk
Without any performance tweaking, ~15 seconds. If I feel like doing tweaking I get it to >10 easy. MUCH FASTER THAN WINDOWS, with tweaks (~45 SECONDS)

---

### Post by mips on 2012-10-22
> **~LoKe said:**
> 8:30 from boot to Desktop.

What drive are you using?

---

### Post by irv on 2012-10-22
I just install 12.10 this morning and my bootup time stayed the same. About 20 seconds. It would be a lot slower if I didn't have a SSD installed.

---

### Post by Henkdroid on 2012-10-22
My boot time is an amazing 1:14. I recorded how long it took to reboot my computer and it was 3:09~. It's a 5ish year old ThinkPad T61 with a 5400 RPM hard drive.

---

### Post by ~LoKe on 2012-10-22
> **mips said:**
> What drive are you using?

A crappy 60GB OCZ Vertex Plus.

---

### Post by lz1dsb on 2012-10-23
> **goldshirt9 said:**
> I am running Kubuntu 12.04 on a
Fujitsu lifebook AH531

Intel Core i5 Sandybridge 2430M 2.4GHz,
 2x4GB DDR3 1333MHz, Dual Channel Support 
Seagate 320GB Momentus XT 2.5" Hybrid HDD/SSD - SATA-II 7200rpm 32MB Cache


from boot to password screen 11 sec's.
As far as i know i have disabled nothing in the system :lolflag:.
Wow... that's impressive :lolflag:
On my system it takes maybe more than 40 seconds to get to the password screen.
But I've made some tweaks which might have led to inefficiencies...

---

### Post by Grenage on 2012-10-23
Corsair Force 3
2500k @ 4.6

Windows (untweaked): 6.5 seconds.
Ubuntu (untweaked): 9 seconds.

I ended up removing Ubuntu and just leaving Windows on there.

---

### Post by madoshwa on 2012-10-27
mines closer to 18 seconds, but that could also be the hdd im using. its a 120g seagate laptop hdd. not the greatest, but it runs. unfortunately it does sacrifice loading speed

---

### Post by SuperFreak on 2012-10-28
From hitting the power button to having a usable desktop(firefox and Thunderbird open) my computer takes 35 sec. However my boot chart (attached) appears to indicate that boot takes 56 seconds. Please correct me if I am wrong but it appears that the extra time is taken by processes in Sleep mode. Is it necessary or desirable to change this?

---

### Post by monkeybrain2012 on 2012-10-28
It is probably less than 10 sec (for 12.04 and 12.10, it used to take longer, like 25s)  Lubuntu is even faster even on some old crapboxes.

---

### Post by Paddy Landau on 2012-10-28
> **Henkdroid said:**
> My boot time is an amazing 1:14. I recorded how long it took to reboot my computer and it was 3:09~. It's a 5ish year old ThinkPad T61 with a 5400 RPM hard drive.
Seriously — just 74 seconds? On a 5-year-old computer with a hard drive not an SSD? What Linux distro and version are you using?

---

