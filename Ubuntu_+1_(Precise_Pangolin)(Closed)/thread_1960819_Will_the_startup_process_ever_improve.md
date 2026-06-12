---
title: "Will the startup process ever improve?"
date: 2012-04-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-04-18
For as long as I can remember now (since Plymouth was introduced) the boot process has been the same and 12.04 is no exception:

Grub menu, followed by a black screen with a blinking cursor which seems to go on forever before the splash screen appears for about 2 seconds then login screen.

I have experienced this on 3 different laptops with Intel hardware, one with ATI gfx and on a desktop PC with nVidia gfx.

I realise the boot process isn't the most important thing in the world but it is the first thing a user sees.
A live cd boots in a way I would consider normal than after install it's like this and new users may well think something has gone wrong.

Of course I can make the splash screen appear instantly with "FRAMEBUFFER=y" but the boot up is still very long.

12.04 has also now added a new factor:
The time from login screen to fully loaded desktop is longer than any OS I have ever used.
I am just left staring at a wallpaper for ages before the panel and launcher finally appear.  It's like this in Unity 3D and 2D.

---

### Post by sudodus on 2012-04-18
I think that several operating systems are bloated and slow. I don't have to list them here.

So I like the light ones. Try Xubuntu with the light XFCE desktop environment or Lubuntu with the ultra-light LXDE.

You can try them either installed separately or by installing the desktop systems into 'vanilla' Ubuntu
```
sudo apt-get install xubuntu-desktop
```
```
sudo apt-get install lubuntu-desktop
```
and choose desktop environment at the log in screen.

---

### Post by dino99 on 2012-04-18
its time to install grub1 back :)

---

### Post by xyzzyman on 2012-04-18
If you want to list your hardware specs, and post your current bootchart we can take a look and see what's hanging up bad for you if it's taking so long to boot. I'm on a 3year old notebook (core 2 duo 2.53ghz, 4gb ram, 5400rpm hard drive) and i still boot in around 35 seconds from hitting enter on grub to fully loaded desktop (That's with docky loading, a # of indicators, virtualboxes background processes, guake). If I turn on auto-login that saves some more time, and if I turn off the heavy stuff I get down to 25 seconds but I'd rather just have everything pre-loaded that I use. I have the ram might as well use it, even though I never go over 1.25gb used 'cept when I have VM's loaded.

---

### Post by Aenima99x on 2012-04-18
> **xyzzyman said:**
> If you want to list your hardware specs, and post your current bootchart we can take a look and see what's hanging up bad for you if it's taking so long to boot. I'm on a 3year old notebook (core 2 duo 2.53ghz, 4gb ram, 5400rpm hard drive) and i still boot in around 35 seconds from hitting enter on grub to fully loaded desktop (That's with docky loading, a # of indicators, virtualboxes background processes, guake). If I turn on auto-login that saves some more time, and if I turn off the heavy stuff I get down to 25 seconds but I'd rather just have everything pre-loaded that I use. I have the ram might as well use it, even though I never go over 1.25gb used 'cept when I have VM's loaded.

Same issue here as the OP and my laptop specs are nearly identical to yours. My boot time is anywhere from 1:10 to 1:35 in 12.04. This same laptop used to boot as fast as 25 sec in 11.04. 
Here's my bootchart

[[IMG]http://i.imgur.com/XNUFwl.png[/IMG]](http://imgur.com/XNUFw)

---

### Post by x-shaney-x on 2012-04-18
Core i5 2.67ghz with 4GB RAM, not sure of drive speed, presumably 5400rpm.

But like I said, the situation is the same on other computers, including AMD X2 3GB RAM, Core i3 3GB RAM and Core 2 Duo 2GB RAM.

The speed of boot itself isn't that much of a problem, more the clunkiness of it, black screen with blinking cursor for most of the boot with a very brief splash screen is not how it should be and not like the live cd.

It was never like this or as slow before Plymouth.

The speed of the desktop loading also bothers me more than the speed of boot since this is something new.

---

### Post by sudodus on 2012-04-18
> **x-shaney-x said:**
> Core i5 2.67ghz with 4GB RAM, not sure of drive speed, presumably 5400rpm.

But like I said, the situation is the same on other computers, including AMD X2 3GB RAM, Core i3 3GB RAM and Core 2 Duo 2GB RAM.

The speed of boot itself isn't that much of a problem, more the clunkiness of it, black screen with blinking cursor for most of the boot with a very brief splash screen is not how it should be and not like the live cd.

It was never like this or as slow before Plymouth.

The speed of the desktop loading also bothers me more than the speed of boot since this is something new.
Lubuntu needs almost no time from log in until you can start using the computer. But Ubuntu with Unity (also 12.04) on the same computer is not as slow as you describe. I suspect that you have issues with the graphics driver. (I have nVidia GeForce GT 430)

---

### Post by ratcheer on 2012-04-18
I do not experience the problems being described. On occasion, I will get a black screen before the Plymouth splash, but only for a few seconds and usually only the during the first reboot after installing some significant update. Then, the Plymouth splash itself only lasts a couple of seconds, then I get my chosen wallpaper with the lightdm login dialog displayed.

Tim

---

### Post by xyzzyman on 2012-04-18
And I'm at 38.09 seconds:

[[IMG]http://i.imgur.com/imyVXl.png[/IMG]](http://imgur.com/imyVX)

Yet I am only running at 58% of your HDD's throughput, and I'm loading VirtualBox's 3 services and mounting 3 NTFS partitions through fstab, loading up Docky, the nvidia binary... The only thing I've uninstalled is modem-manager.

Is it possible you are having a problem with ureadahead? Do you have your pack files in /var/lib/ureadahead? Sure doesn't look right how ureadahead is running the entire time for you.

EDIT: I noticed I'm running 64bit and you're on 32bit. There's a noticeable improvement running 64bit on this hardware, but not that much. I still think your ureadahead cache is messed up though. 38.09seconds is the fastest time I've had booting to full desktop, but my 23-25 second Ubuntu boot times have always been with a custom compiled kernel, services stripped to bare minimum (not even cups), etc...

---

### Post by Aenima99x on 2012-04-18
> **xyzzyman said:**
> 
Is it possible you are having a problem with ureadahead? Do you have your pack files in /var/lib/ureadahead? Sure doesn't look right how ureadahead is running the entire time for you.

EDIT: I noticed I'm running 64bit and you're on 32bit. There's a noticeable improvement running 64bit on this hardware, but not that much. I still think your ureadahead cache is messed up though. 38.09seconds is the fastest time I've had booting to full desktop, but my 23-25 second Ubuntu boot times have always been with a custom compiled kernel, services stripped to bare minimum (not even cups), etc...

Totally spaced on checking the pack files...just now checked are there were none. I generated new ones and will try a couople reboots to see how it looks now. Thanks for the hint.

---

### Post by philinux on 2012-04-18
My experience.  Times off the wall clock. This is after a re-profiling boot.

Grub to login 20 seconds.

Hit the enter key after password to desktop 5 seconds.

I'm happy. This is a 4 year 64 old 64 bit machine. 
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ × 2 
2 gig ram and nVidia 8600GT card.

---

### Post by mcellius on 2012-04-18
29 seconds from GRUB to login, time measured on my watch.

4-year-old laptop, Intel Core 2 Duo T5800 2 GHz, 4GB RAM, 12.04 64-bit

---

### Post by Abandon on 2012-04-18
Problems?  :confused:

[IMG]http://www.digiplace.nl/bootchart.png[/IMG]

---

### Post by mc4man on 2012-04-18
From a recent mail concerning desktop topics, ect for 12.10 ([Desktop 12.10 Topic] Login speed improvements
> Hey,

Yet another leftover from precise, not much to discuss as well, rather a "just do it". We did a bit of work this cycle but didn't go far, there is still room for improvement especially with nautilus, compiz.

Cheers,
Sebastien Bacher 
The spped from greeter to loaded desktop has increased from a high point here in probably early or mid feb. when it was 1 sec. or 2 at most

---

### Post by Seq on 2012-04-18
Plymouth works well here on my nvidia based laptop. I even get my dmcrypt password prompt in plymouth, which is pretty nice looking. It is not the proper resolution for my monitor, though, since I'm using 'nvidia' (and nouveau is blacklisted).

Plymouth works really well on my sandy bridge desktop as well. Basically seamless from grub through to login. I even get a mouse cursor appear over plymouth before lightdm replaces it, rather than blanking the framebuffer to a black screen.

---

### Post by Ravi5kumar on 2012-04-19
> **mcellius said:**
> 29 seconds from GRUB to login, time measured on my watch.

4-year-old laptop, Intel Core 2 Duo T5800 2 GHz, 4GB RAM, 12.04 64-bit

Interestingly, I have same time loading GRUB but I have Core 2 Duo 2.20 GHz and it is 3 years old laptop................:p

---

### Post by mcellius on 2012-04-19
> **Ravi5kumar said:**
> Interestingly, I have same time loading GRUB but I have Core 2 Duo 2.20 GHz and it is 3 years old laptop................:p

Well, actually my laptop is probably more like about three-and-a-half years old - Fall of 2008 - so there isn't much age difference.  We probably have very similar hard drives, too.

---

### Post by hakermania on 2012-04-19
What? 1.30 or something? I boot up in 30 secs and I'm in beta2

---

### Post by dcstar on 2012-04-19
> **hakermania said:**
> What? 1.30 or something? I boot up in 30 secs and I'm in beta2

16 seconds from hitting the selection on my muilt-boot screen to the 12.04 login screen with the Drum sounds.

Of course I have a Hybrid drive that caches boot files, so it provides SSD like performance in this area.

---

### Post by madeinfamous on 2012-04-19
allo x-shaney-x,

on Intel machine whichever Ubuntu version

PLYMOUTH SPLASH NOT WORKING (INTEL)

as root:

sudo su

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splas

update-initramfs -u

reboot and enjoy! ;)

[https://docs.google.com/document/d/1ja47gmF4VDGP3RG-Ebq-DoPq9BWSYqgfORtYeHB6_0k/edit](https://docs.google.com/document/d/1ja47gmF4VDGP3RG-Ebq-DoPq9BWSYqgfORtYeHB6_0k/edit)

---

### Post by Procrustes on 2012-04-19
Just a thought but I had the same lengthy blinking cursor at boot until I changed the SATA mode in the BIOS from the IDE to the AHCI.

I don't know why my modern hardware defaulted to IDE mode.

---

