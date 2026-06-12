---
title: "How many chances do I have to give Ubuntu?"
date: 2005-09-05
forum: The Cafe
---

### Post by granite230 on 2005-09-05
Maybe some people here remember me complaining a lot, but I can tell you one thing: it sucks when your OS fails to boot.
And guess what, we're there again!

Some people might also remember that I sometimes phisically change the disk to boot Windows every now and then, but I haven't done this since my last reinstall of Ubuntu. I haven't touched my hardware, I haven't done any crazy things, I just boot my system every day like everybody else here.

This morning Ubuntu didn't boot... got stuck somewhere in the process and it just hung without any errors... so I rebooted and then I got a lot of strange errors, saying that some stuff was disabled for 5 minutes or something. Then it did nothing... so I rebooted again, then it said: Disk boot failure, then I rebooted again: Disk boot failure. 
Then I inserted the Knoppix live cd which also mounts my harddisk and I couldn't reach the data on my harddisk because it was saying something about to many filesystems or something.
Then I rebooted again without the live cd and then grub gave me an error 2. I haven't figured out what that means yet but I don't feel like doing that either...

I mean... maybe I fix my system again, but then what? Use it for another 2 weeks and wait for the next error to pop-up? I'm really getting tired of this. I reinstalled Ubuntu about 6 times within 6 months, and I tried it on several harddisks. I came to this forum a lot of times, often complaining about some things but I didn't give up Ubuntu. You guys did a great job helping me out, but I think no OS should behave like this... I think it's time to try another distro. Maybe it's my hardware... I really don't know... but I do know one thing: I'm not gonna spend my time figuring this one out on my last day off... I'm gonna enjoy the sun outside and maybe tonight I'm gonna install another distro... I'm done with this. Maybe I'll come back when Breezy comes out.

---

### Post by kahping on 2005-09-05
have you run diagnostics on your harddisk & RAM? if you haven't been installing stuff for some time and the system just craps out, it's likely there's faulty hardware involved.

or maybe you just need to clean out the dirt that's been collecting in your casing? :-P

kahping

---

### Post by granite230 on 2005-09-05
it's not dirty at all... I checked my memory, it's fine, I installed Ubuntu on more than one harddisk so the harddisk is also fine... Windows is running like it should on all the harddisks I try, but Ubuntu keeps failing...

Everything I try runs fine, except Ubuntu. I wish I had another computer to try it on but I haven't... anybody has some useful tips?

---

### Post by Kvark on 2005-09-05
It really sounds like a hidden hardware problem that suddenly pops up every once in a million uses/tests and that perhaps is stumbled upon more often with the way Ubuntu uses the hardware then with the way Windows uses it. But now I'm speculating widely based on almost no info.

It doesn't matter where the error is. I don't think you should put up with that kind of buggyness no matter what may be at fault. Go get Mepis or some other distro, take the [Linux Distro Chooser test](http://www.zegeniestudios.net/ldc/) if you are unsure about which one to try next.

---

### Post by Brunellus on 2005-09-05
[QUOTE=granite230]it's not dirty at all... I checked my memory, it's fine, I installed Ubuntu on more than one harddisk so the harddisk is also fine... Windows is running like it should on all the harddisks I try, but Ubuntu keeps failing...

Everything I try runs fine, except Ubuntu. I wish I had another computer to try it on but I haven't... anybody has some useful tips?[/QUOTE]
 please try to post a more complete transcript of the error messages generated on the failed boot.  This isn't Windows--those messages actually mean something useful!

Can you use a live-CD to boot the computer, and then look at hte system logs on the hard disk?  they'll be in the /var directory.

---

### Post by totalshredder on 2005-09-05
[QUOTE=Brunellus]please try to post a more complete transcript of the error messages generated on the failed boot.  This isn't Windows--those messages actually mean something useful!

Can you use a live-CD to boot the computer, and then look at hte system logs on the hard disk?  they'll be in the /var directory.[/QUOTE]

Calm down :), if you had read the rest of the message he said there were no error messages and that he had tried knoppix. 
But maybe he added those after your post.

Luke

---

### Post by egon spengler on 2005-09-05
Try something else, you don't owe ubuntu anything to keep persevering like this. I and most other people here can vouch for the fact that ubuntu works and works well so it may well be some hard to find hardware incompatibility but I can't see that offering you much solace.

Personally after the second forced reinstallation I would have moved on

---

### Post by Nu-Buntu on 2005-09-05
I agree. Whatever OS gods may or may not be out there won't send you to hell for moving on if Ubuntu and your hardware don't get along. Use what works. If that is Windows, great! If it is Fedora, Fine! You gave it your best shot. We may all have our favorite distros, but we are also all Linux users, and truth be told, most of us probably use Windows occasionally as well. This shouldn't be religion.

---

### Post by az on 2005-09-05
[QUOTE=granite230]then it said: Disk boot failure, then I rebooted again: Disk boot failure. 
Then I inserted the Knoppix live cd which also mounts my harddisk and I couldn't reach the data on my harddisk because it was saying something about to many filesystems or something.
Then I rebooted again without the live cd and then grub gave me an error 2. I haven't figured out what that means yet but I don't feel like doing that either...

I mean... maybe I fix my system again, but then what? [/QUOTE]

There are no bug reports about Ubuntu eating a filesystem like that.  This is a hardware problem.

---

### Post by npaladin2000 on 2005-09-05
Sounds like someone's got some bad sectors on his HDD.

Physically changing boot disks around all the time, BTW, isn't a good move...it stresses things too much whether it's in the BIOS or by cracking open the case and doing it by hand (incidentally, which did you do?).  

What's your partitioning scheme on that HDD?  And you were saying you have Windows on the same disk, but you don't have it set to dual-boot through GRUB?  

We really need more information on the situation. i also highly recommend getting the diagnostic disk for your hard drive from the manufacturer's website and use it to check the drive, make sure it's working 100% properly.

---

### Post by Curlydave on 2005-09-05
I have had serious issues with ubuntu failing to load into X, gnome etc and understand why you might blame Ubuntu. It does do weird/obnoxious stuff sometimes, but from your description this sounds like a HD problem.

---

### Post by granite230 on 2005-09-05
thanx for your reactions!

I don't blame Ubuntu for anything! I know it works well and I really like Ubuntu, that's why I didn't move on a lot earlier. I don't want tot move on! But I'm afraid my hardware won't let me keep Ubuntu.
I also think my harddisks are fine. I tried Ubuntu on several harddisks and after installation it works just fine! Only not for very long.

So the next thing I'm gonna do is this:

- I'll try another distro (don't know which one yet)
- I'll make that a dual boot with Windows XP so I don't have to phisically swap the harddisk and I can close the case again.

I'm convinced that Ubuntu doesn't like some hardware in my pc. I just hope another distro will like it and as soon as I get a new computer I'll install Ubuntu on it (unless I like my next distro better but I seriously doubt that).

Of course I'll stick around in this forum and I will be back using Ubuntu someday! I need another computer first :neutral:

---

### Post by Kvark on 2005-09-05
[QUOTE=granite230]I'm convinced that Ubuntu doesn't like some hardware in my pc. I just hope another distro will like it and as soon as I get a new computer I'll install Ubuntu on it (unless I like my next distro better but I seriously doubt that).

Of course I'll stick around in this forum and I will be back using Ubuntu someday! I need another computer first :neutral:[/QUOTE]
If a piece of hardware doesn't play well with Windows then sales would be cut down by like 80-90% so the hardware manufacturers are very keen on support for Windows. But if it doesn't play well with Ubuntu the sales drop is not noticeable so many hardware manufacturers simply don't bother.

When you buy a new computer and plan to run Ubuntu on it, make sure every piece in it is reported to work well with Ubuntu. You'd have to know the exact models of soundcard, wireless NIC, etc and compare to compatibility lists on the net. :?

But perhaps some computer store near you will be selling computers with Ubuntu preinstalled by then. If it ships with Ubuntu then it surely is compatible with Ubuntu.

---

### Post by skoal on 2005-09-05
Granite, there's a fix for your problem.  You just need to provide a little more information (as best you can).  I gather you do _not_ have these same issues while running Windows, whether you are dualing booting Ubuntu on the same drive as Windows, or whether Ubuntu is on a drive by itself?  Right?

Can you tell me if you experience this problem while using Ubuntu?

While trying to shut down (or reboot), it sometimes hangs near the end (or you have to turn off the power switch when it was supposed to reboot by itself)?

...and it doesn't do that in Windows?

\\//_

---

### Post by npaladin2000 on 2005-09-05
You're PHYSICALLY swapping the disks a lot???? Open case???? Dude, now I'm not surprised that your OSes stop working after a while....desktop HDDs aren't designed to be tinkered with all the time; they're delicate pieces of hardware (laptop HDDs are a bit more robust).  That probably wasn't doing the rest of your components, specifically your mobo's HDD controller, any good at all either. and with your case open a lot, for all we know a gnat went and died, shorting a couple of traces. ;)  I could go on, but I know what some of these self-professed "hardware geeks" do, and most of it is bad news (I used to be one myself until I learned better habits in a professional environment). Things like always running an open-case system...ever heard of EMI?  The case is supposed to block it.  

This is why those hardware geeks get tired of WIndows's instability before anyone else. They never realize that the instability is caused by data corruption....usually caused by their loose, casual treatement of delicate hardware components.  You know, things like operating an open-air system with no case on the table where they're eating popcorn and drinking Dew in a shag-carpeted room, and playing catch with RAM and such. Oh, and a COMPLETE disregard for anti-static bags as well as static discharge procedures.  So of course Linux is going to suck too because it's unstable on the same hardware, right?  No, of course it's got nothing to do with how the hardware is treated, because windows works fine (all of a sudden, magically, of course). 

Anyway, assuming your system and hard disks aren't too far gone (get manufacturer diagnostic disks and test ALL of them FIRST!!) I'd rebuild your system, affix all the HDDs you want to use in the case and connect them, and then close it up. USE SCREWS!  THEN do your OS installation...install XP first, followed by whichever Linux or Linuxes so that GRUB will install properly.

---

### Post by arnieboy on 2005-09-05
[QUOTE=granite230]This morning Ubuntu didn't boot... got stuck somewhere in the process and it just hung without any errors... so I rebooted and then I got a lot of strange errors, saying that some stuff was disabled for 5 minutes or something. Then it did nothing... so I rebooted again, then it said: Disk boot failure, then I rebooted again: Disk boot failure. 
Then I inserted the Knoppix live cd which also mounts my harddisk and I couldn't reach the data on my harddisk because it was saying something about to many filesystems or something.
Then I rebooted again without the live cd and then grub gave me an error 2. I haven't figured out what that means yet but I don't feel like doing that either...

I mean... maybe I fix my system again, but then what? Use it for another 2 weeks and wait for the next error to pop-up? I'm really getting tired of this. I reinstalled Ubuntu about 6 times within 6 months, and I tried it on several harddisks. I came to this forum a lot of times, often complaining about some things but I didn't give up Ubuntu. You guys did a great job helping me out, but I think no OS should behave like this... I think it's time to try another distro. Maybe it's my hardware... I really don't know... but I do know one thing: I'm not gonna spend my time figuring this one out on my last day off... I'm gonna enjoy the sun outside and maybe tonight I'm gonna install another distro... I'm done with this. Maybe I'll come back when Breezy comes out.[/QUOTE]
reminds me of my undergrad days.. used to treat my harddisk like a usb drive... and load a new linux distro every weekend.

---

### Post by Brunellus on 2005-09-05
[QUOTE=arnieboy]reminds me of my undergrad days.. used to treat my harddisk like an usb drive... and load a new linux distro every weekend.[/QUOTE]
 hell.  my undergrad days were defined by brief periods of sobriety, every so often.

---

### Post by BoyOfDestiny on 2005-09-06
This is somewhat random, but it's solved many mysterious OS problems for me... 

Flash your BIOS to the latest version :)

If you already have the latest version... then dunno :)

---

### Post by granite230 on 2005-09-06
okay, so wheter I like it or not: I have to use Windows as well.
I would love to have only one harddisk with only one operating system (Ubuntu), shut the case and use it happily ever after... but for school purposes I have to use Visual Studio and MS SQL (and I don't like it!!!!), so I thought: well... I still have this old harddisk with Windows XP, I'll use that whenever I need one of those two applications. Then I use my brand new 160GB harddisk for my sweet Ubuntu!

I just HATE to install Windows first and then Ubuntu after it... I just wanted one harddisk for Ubuntu only! I believe you're right about the open case and the swap stuff... so here's what I'm gonna do: 

- I'll close the case
- I'll check my hardware using some tools to make sure everything's okay
- I'll create a dual boot Windows XP/Ubuntu

I'm not 100% confident if it will fix the random bootproblems I'm experiencing, so if Ubuntu seriously fails one more time after I did this I'll never install Ubuntu on this pc ever again.

This is gonna take a LOT of time to fix... then I still have to maintain 2 operating systems just so I can use that stupid Visual Studio... and pray that everything will work. I'm not amused, but I'll give it a shot.

---

### Post by madjo on 2005-09-06
where does your system hang? mine sometimes refuses to boot, because of my usb mouse (don't know why though, and it doesn't always hang)... 
the way I fix it is, I unplug the mouse for a second, and the hotplug daemon gives the ok.. and I plug it back in... and the whole system works again. (including the mouse)

---

### Post by granite230 on 2005-09-06
I cant give any specific info because I've seen a million things go wrong while booting up... it's not a specific problem, it are random failures, sometimes fixed by a reboot, sometimes not because the whole system is taken down.

---

### Post by Kvark on 2005-09-06
Wow, you're rough on your hardware. I hope you wear an anti static wrist strap while digging around in the box. The damage a tiny spark can cause is the worst kind, cause the damaged hardware keeps working, except at rare random occations.

If the problems appear only when booting, which is indeed a very stressful proccess just like starting up any other machinery, then it might be best to limit the number of times you boot the box by leaving it on.

---

### Post by patpicos on 2005-09-10
hi granite
i think i am in the same boat as you.
i installed ubuntu 4 days ago, installed perfectly fine, added some appz and made some customization. I closed the lid of my laptop and it bed.

I wake up, the screen is sorta flashing and acting weird, so my response was, lets reboot the baby. On bootup, KDE wouldnt load. So i went in runlevel 1 and fsck the hd......zillions of errors came up and fsck couldnt fixed, allrite screw the install and RESINTALL

Made mods again, installed some software, got my system uptodate as of 09/09/05 with apt-get with universe repo activated.

Last night on my night shift, i tried to install Domino 7 for the heck of trying on my laptop. The script would  COMPLETELY freeze my laptop. after 3 tries, i realized it wont install!!! Did more work on my laptop, rebooted a few times here and there, then at the end of my shift i shutdown.


I wake in the afternoon, start my laptop.....guess what it boots, and KDE doesnt load. At the cli, i try a few commands like man, sudo apt-get .....libcstc++.so.6 magic header is ........ i dont remember the exact msg, but the library files were pooped. I fsck'ed a few times and fixed the errors popping up, but the libraries were still messed up

I put the cdrom of kubuntu in the tray and reinstalled the libc thingie from main/g/gcc-3.3.4...... so i was able to run some more programs

running ldconfig was spewing a bunch of lib files corrupted, so i reinstalled each of them manually.


I hope my FS wont fuckup again because i love kubuntu!!!

I really doubt i have a HW problem as I never had problems with fedora, which i ran for 2 months on my laptop..... and in 3 days my kubuntu misbehaved badly twice already!

it might be that i have some packages corrupting my fs for some reason...i just read the sticky about the transition to gcc4 stuff.....

---

### Post by MinoltaLuvR on 2005-09-11
hi, i'm new here (2nd post), by far not a linux guru, but i've been a pc hardware junkie for a long time. first, i dont even own a pc case! i have everything sitting here on my desk, and i yanked a power switch from a junked ATX dell.

the kind of random problems your having could be a flakey powersupply, a bad IDE ribbon, or flakey ram.
a bad power supply can wreak all kinds of little problems on you.
if you have an extra $30 or $40 [www.newegg.com](www.newegg.com) sells a brand called Fortron Source power supplies, their cheap, and damn good power supplies. their made by a company that makes PS's for medical equipment. w/o knowing your exact hardware specs, i cant recommend a certain wattage, but a 350 or better should do the trick if your not loaded down with stuff.

if you've been swapping hard drives out even a few times, your IDE ribbon is most likely shot, their not made to put up with more than a few yanks in most cases..

if you have more than one stick of ram in your box, are they the same mfg/specs?
if you have more than one, yank out a stick or two, and try one at a time, or in pairs, and see if the problems persist. also going into the bios and tinkering with the CAS latency may reap some rewards, dropping the speed down if your running out of spec etc.
my current mobo/cpu does NOT like all 3 slots of ram full, but after a whole lot of juggling i found a combo of ram (mis matched) that work well, but i had to tinker with some bios settings (timings, latency etc) to get it to work, and work well it does.

hope this helps, good luck in whatever course you choose.

cheers
john.

---

