---
title: "no problems here"
date: 2020-09-11
forum: The Cafe
---

### Post by T6&amp;sfpER35% on 2020-09-11
daily i read the forums and the problems people have, and i'm thinking to myself ,"why i never have these problems??"
i must be the luckiest linux user on the planet lol
(ps. i had a few probz here and there but nothing major,nothing timeshift can't solve)
:P

anyway , my 2 cents
happy linuxing...

---

### Post by crip720 on 2020-09-11
Have almost similar luck.  Do think it has a lot to do with what hardware we luck out to use.  Most of mine as been see laptop and install ubuntu on it without googling to see if there are known problems with it.  Find that google can find most answers that people already have had before me.

---

### Post by exploder on 2020-09-11
Ubuntu 20.04 has been problem free here too. Well, my new laptop had an issue but that was kind of expected and a newer kernel fixed it up. In my opinion, 20.04 is the best release so far, very nice work!

---

### Post by zebra2 on 2020-09-11
No problems here. 
Have wife on 20.04 Lenovo Laptop.
Have self on two 20.10 Lenovo Laptops.
Happy wife, happy self.
All good here.

---

### Post by sdsurfer on 2020-09-14
Couple years ago I had the Internet connection just go away without explanation. (Have a lappie and a desktop here so I could research/confirm.) After poking around the forums, different SO posts, and other places trying different things, it magically re-appeared also with no apparent action on my part. Never had a problem since.

Other than that, none of the recurring nightmares I had running windows. Everything just works.

---

### Post by poorguy on 2020-09-15
I generally don't have problems with Linux as I use old desktop computers and I install and use Linux as it comes OOTB.

I have seen some computers that Linux just don't like and just won't install and run on and those computers become firearm targets.

---

### Post by ameinild on 2020-09-15
I installed my new home server (+ raspberry pi) just when 20.04 was released. Both have been running rock solid all the time. ;)

---

### Post by Wild_Duck66 on 2020-09-29
No real problems except that my timeout in grub.cfg is set to 5 seconds (etc/default/grub) but every now and then it goes to 30 seconds, not really work reporting.

---

### Post by rudihawk on 2020-10-01
Same with me, although I had to jump through some hoops to get my webcam to work on my Macbook this week.

---

### Post by Shibblet on 2020-10-01
The only problem I have had over the years with Ubuntu is this:  [https://ubuntuforums.org/showthread.php?t=2329514]("https://ubuntuforums.org/showthread.php?t=2329514")

So, I gave the Bose Companion 5's (USB) speakers to my son who had a Windows 7 Gaming Computer, and bought a pair of Harman/Kardon SoundSticks (3.5mm plug) for my computer, and haven't looked back.

---

### Post by isladlewis on 2020-10-05
It depends on the user behavior

---

### Post by Tadaen_Sylvermane on 2020-10-05
I think I can safely say that during my entire period with Linux of whatever variation over the years any problems are my lack of understanding something and doing it wrong in the first place. Now, rarely an issue, and still usually because I tried or did something wrong.

---

### Post by exploder on 2020-10-05
I had problems on my new laptop but I expected it because of the hardware. The great thing was, all the resources to fix the problems were readily available. I installed the 5.8.13 mainline kernel and edited etc/default/grub and the new laptop is running Ubuntu 20.04 like a champ!

---

### Post by Irihapeti on 2020-10-05
I've had the occasional problem, mostly caused by my own stupidity but occasionally by an unusual piece of hardware. But most of the time, it's just worked for me.

Bear in mind that most people on forums etc are there to get help with problems. There won't be many who join just to say, "Hey, this is great!" :)

---

### Post by zebra2 on 2020-10-08
> **Irihapeti said:**
> 
Bear in mind that most people on forums etc are there to get help with problems. There won't be many who join just to say, "Hey, this is great!" :)

Most of the problems revolve around the dual boot curse and multi-function printer issues.  But regarding this thread I think we have an OS with 20.04/20.10  at its face that is worth the learning curve. If those new users get it I think they will stay with it. I've been using a computer since the 80's and Gorilla is as good as it has been (for me).  Getting comfortable with with linux in general was a hair pulling highchair banging experience but, Hey, this is great!

---

### Post by ajgreeny on 2020-10-08
15 years of using one or other distro from the *buntu family has generally been much easier than I expected when I started with 5.04 and joined the forum.

I have installed onto so many different machines I can not remember how many, but everything from an old single core (I think) AMD Sempron with 1G ram when I installed 5.04 to my current main machine, though even that is not very modern by many standards; an i5-3570K cpu, 8G ram, 1T spinning HDD, but with Xubuntu (I don't like gnome) it blazes along as fast as I need.
The only time I had a problem I didn't understand was when I first started using UEFI and being new to that technology totally overlooked the need for an EFI partition.
Quickly learned to look more carefully when I get new hardware!

---

### Post by Shibblet on 2020-10-08
Sometimes, problems come out of nowhere for the user.  There is a bug that just recently came up with anyone who has an Nvidia card.
During install, the drivers do not download correctly, and will cause install to fail.

Installation worked great, and then about a week ago, it stopped working...

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1871268]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1871268")

It's a known bug, and they are working on it.  Plus, there is a workaround.  [https://ubuntuforums.org/showthread.php?t=2451568]("https://ubuntuforums.org/showthread.php?t=2451568")

---

### Post by sdsurfer on 2020-10-19
Interesting that the last post mentions Nvidia drivers, part 2 below. :-D

I upgraded to 20.04 Friday on a System76 Lappie. Previous upgrades I'd run went without a single problem, but this time . . . scary. First it rebooted after the upgrade and at the login prompt wouldn't allow text entry, just repeated "authentication failed." Rebooted and nada, nothing, zilch, black screen, then black screen with a cursor, no magic keys could alter the course. It seemed like it kept rebooting, black screen, cursor appeared, black screen, over and over . . . No articles led to any relief. I had no idea what to do, GRUB? Graphics? Did I just destroy my system?

The bottom line, after hours of searches I found one article that **just happened** to be a System 76 article that generically walked through how to re-install GRUB. That was it, it rebooted fine.

I noticed some weirdness in some apps (some panes were black) and knew this was related to Nvidia drivers. Software & Updates showd v 450 in use, I tried changing it, tons of errors about dependencies not installed. I ran
```
ubuntu-drivers devices
```

then installed "recommended"

```
sudo apt install nvidia-driver-450
```

No problems since.

---

### Post by uRock on 2020-10-21
I've had a few problems here and there over the years. I went back to to Windows for a bit around 12.04 because there were some quirks that required more energy than I was willing to spend while working on my degree. I came back when 14.04 was released and worked solidly. I had a lot of problems with the standard Ubuntu for 18.04, but that was remedied by switching to Xubuntu. I haven't upgraded to 20.04, because not fixing what isn't broken. I also have a laptop that has been through the upgrade from 18.04 to 20.04 and is now on 20.10 Beta with zero problems.

---

### Post by lammert-nijhof on 2020-10-22
I use Ubuntu since 8.04 and I did run 5.10 on an old Pentium II for a few months. I remember the problems with Broadcom Wi-Fi drivers around 2008. I also had some problems with the video support for the first Unity release in 2011, but that is the last real problem I remembered. At that time I used Xubuntu for half a year.

Currently I only have 2 annoyances, My Virtualbox VMs boot up in a black screen, when booted in full screen and I have to press CTRL + F twice. I also avoid the issue for 90% of the VMs, if I use the Guest Additions 6.1.4. The other issue is that the VM does not accept sometimes its first input and I have to go back to any program on the host and type 1 character, to get the keyboard in the VM working again. I have no clue, whether these problems are related to Virtualbox or Ubuntu, Host or VM or maybe the Ryzen 3 2200G drivers or the VBOX video drivers. 

So no problems, only some small annoyances! That is a major difference with the other non-Ubuntu based distros. Running many distros for longer time in a VM, there are real differences in the problems you run into. Manjaro died after an update, Fedora has issues with the codecs, Deepin stopped working. It is not easy to maintain a uncompromising reliability over a long period. You can also see it in the Ubuntu 20.10 remixes. There has been a regression with respect to VBox support.

No problems with Ubuntu, its flavours and derivates like Linux Mint etc. For others be aware!

---

