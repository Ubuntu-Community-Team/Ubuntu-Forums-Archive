---
title: "Installing Windows XP"
date: 2006-05-13
forum: Testimonials &amp; Experiences
---

### Post by IYY on 2006-05-13
Recently, I've been told to write some C# code at work. As painful as it was, I had to erase Dapper from my newest machine (1.4 GHz, 256 MB) and install Windows XP and Visual Studio. I haven't used Windows for a few years, so I thought it would be an interesting experience. Here's how it went (and my impressions):

[LIST]
[*]Installation went smoothly, just like Ubuntu. 

[*]An 800x600 resolution was picked automatically. Ubuntu selected a much better resolution.

[*]My sound card didn't work out of the box, and I had to check the model and download drivers from the net. It worked perfectly in Ubuntu.

[*]As soon as I logged in, I started getting popups from a "messenger service", trying to sell me various programs. I went on the internet and found out how to disable it. It involved going to some obscure configuration tool in the control panel.

[*]Minimizing, maximizing and moving windows was sloooooooooow. It felt like I was using Gnome on a 200 MHz machine (I know what that feels like because I actually have used Gnome on a 200 MHz machine). Of course, after installing the official nvidia drivers, these problems were fixed.

[*]The default theme hurt my eyes something fierce, but after switching to the classic theme it actually looked quite attractive.

[*]I know that installing updates is very important to securing Windows, so I went to the official site and tried to upgrade to SP2. During the first installation, I got 2 blue screens of death. After ~3-4 hours Windows was updated.

[*]While MP3 worked out of the box, installing various codecs for video and audio was a hassle.

[*]I still haven't figured out how to get sound to work in Flash.

[*]Ok... Time to install Visual Studio .NET 2005. This installation went well, but took me the entire night (I went to sleep at 5 AM). I have no idea why it was so slow, but it was.

[*]My family members were confused because they didn't know how to access their files. For some reason, the "my computer" icon was not on the desktop and there was no "places" menu. Why would you have to right click, properties, desktop, customize. Just to enable access to your files? How is your grandma going to find that button?

[*]I won't even talk about how difficult and slow things became without a decent terminal. I did install VIM and SSH, though.

[*]Installing software is a pain without apt-get. 

[*]There were some good things too, though: Firefox works a bit faster, webcams work better in MSN, Google Desktop is amazing, and there are no glitches with mounting CD-ROMs, floppies and hard disks.
[/LIST]

I know that this is just *my* experience, and many people use XP very happily, with no such problems. All it shows is that XP fails to work well on some people's hardware just like Ubuntu fails to work on other people's hardware. It's not black and white.

One more personal observation: Configuring the XP system was painful. It felt like work, gave me a headache and made me want to bash my computer with a baseball bat. Linux systems also take some effort to configure, but for some reason I enjoy every minute of it! In Linux, problem solving is like a game, and an educational experience. And most importantly, there are these forums when something goes wrong!

---

### Post by Gannin on 2006-05-13
Very interesting observations.  When I install Linux on my desktop, the only driver I have to download and install separately is the nVidia graphics card driver, at the most.  Windows always required more drivers to be hunted down and installed manually.

If your only requirement was to write some C# code, did you ever take a look at the Mono project?

---

### Post by IYY on 2006-05-13
Well, the requirement was a bit more strict. My job is usually writing C code on Linux, but now I have to make it communicate with this code another programmer wrote in C#. It needs not only Visual Studio, but also some weird plugins for it.

---

### Post by mishranurag on 2006-05-13
I had a similar experience installing win XP on my customized computer.  There were couple of issues with linux too, but I was doing it for first time in my life and most issues were resolved with community support.

Anurag

---

### Post by Dr. C on 2006-05-14
One option is to run Windows XP using VMware. 

I am currently running Windows XP Pro SP2 on VMware Server Beta on Dapper with no problems.

---

### Post by Gannin on 2006-05-14
What kind of speed are you getting?  Any 3D acceleration?

---

### Post by zluka on 2006-05-15
> i've got one of the tip-top boxes (ok, not the best) that winXP can dream of (DFI LanParty nF4 SLI-DR, AMD Athlon 64 X2 Manchester 4200+, 2x MSI NX6800GS-TD256E, 2 GB Samsung DDR 3200 etc.) and i've tried both signed for XP drivers and betas.

the installation is ok, my winblows box is up and running in 1,5-2 hours (the way i need it). everything is fine for about a month, and then it begins freezing during boot.. that happened a few times. re-formatting doesn't help, i have to boot it in safe mode once, after restart it boots normally..

i had issues about symantec client security v 3 (goddamn tampering control), and my logitech keyboard and cordless m$ mouse.. i can't run m$ intellipoint and logitech setpoint together (there's another program doing my job????? - that's the error).

all-in-all i'm not even thinking to go back to winblows, for i'm sick and tired of firewalls, anti-virus progs, stupid errors, meaningless m$ articles which simply say "well, sh.. happens, learn to live with it" (as for the 2 GB memory limit in xp sp2), etc.

that's what i wrote about xp experience.. and i've washed my hands clean of it (if i'm not forced to use it) with it's media kingdom, support that charges you unbelievable amounts of money for practically nothing (i've worked in one of the biggest isps in turkey, believe me about support) and "signed" drivers that either conflict with something else or don't add to performance at all, i am just sorry for you that they force you to use it IYY..

take care, and don't bash anyhing, as far as you can ;)

---

### Post by KennithG on 2006-05-15
[QUOTE=FineE]One option is to run Windows XP using VMware. 

I am currently running Windows XP Pro SP2 on VMware Server Beta on Dapper with no problems.[/QUOTE]
Can you create and run virtual machines with the VMware server beta software? I am intrested in running WindowsXP in Dapper. I have used the VMware Player with success, but I would like to have more control over how the virtual machine is created.

---

### Post by lordofkhemenu on 2006-05-15
[quote=KennithG]Can you create and run virtual machines with the VMware server beta software? I am intrested in running WindowsXP in Dapper. I have used the VMware Player with success, but I would like to have more control over how the virtual machine is created.[/quote] Try installing XP under QEMU. With Samba installed you can access linux "drives" in XP.
When I have QEMU/XP running, it has access to the internet and my jumpdrive and my doc & pics folders.

---

### Post by Dr. C on 2006-05-15
Yes you can create VMs with VMware server beta and play them with the player. 

As for 3D acceleration I understand it is possible with a Linux host and Windows guest, I have not tried it yet. As for performance on one machine the player should provide better performance over the server beta.

---

### Post by KennithG on 2006-05-16
[QUOTE=lordofkhemenu]Try installing XP under QEMU. With Samba installed you can access linux "drives" in XP.
When I have QEMU/XP running, it has access to the internet and my jumpdrive and my doc & pics folders.[/QUOTE]

I have tried QEMU, but could not get it to do anything. I was using the gtk frontend though. Prehaps the command line would be better?

Ken

---

### Post by KennithG on 2006-05-16
[QUOTE=lordofkhemenu]Try installing XP under QEMU. With Samba installed you can access linux "drives" in XP.
When I have QEMU/XP running, it has access to the internet and my jumpdrive and my doc & pics folders.[/QUOTE]

I have tried QEMU, but could not get it to do anything. I was using the gtk frontend though. Prehaps the command line would be better?

Ken

---

### Post by sopo_dan on 2006-05-24
ok this is gonna sound like i'm making windows propaganda, wich i am not. i really couldn't say i prefer one over the other. each has it's good parts and it's bad parts.

what i actually wanted to say is that i haven't installed windows in over 2 years now and i never got a blue screen over all this time. it's been through 3 major hardware upgrades (motherboard, vid card) and moved 4 times from a hdd to another. still working like a charm. i can still get up-times of up to a month (never tried more).
thing is with win you have to be very tidy - never install new drivers before uninstalling old ones, manually clean the registry from time to time, keep a good anti-virus & firewall software running and updated and not to mention installing all the security updates (but you have to do that with linux too)
but, like IYY said, this is just my experience, i'm sure other people are having a much harder time.

on the other hand with linux (no matter what distro) i never managed to get my LFE & center speaker working so i had to use stereo output and let my amp handle the signal splitting to all speakers, wich results in a lower sound quality, i never managed to get my 2 extra mouse buttons and the horizontal scroll working, i can't configure all the extra keys on my keyboard, to get nvidia drivers working i have to edit xorg.conf as opposed to "next -> next -> ... -> finish" & reboot.

yes, i must be crazy, i just made a pro-win/anti-linux statement on a linux forum. but i just did it because i see how most linux users drag windows through the mud only to "go with the flow".
i could just as easily make a statement opposite to the above one, but i'm sure that's been done more than one here.

what i'm actually saying is that both OS's are rewarding if given the chance. we have great community support, a wide choice of software to serve the same purpose and $0 costs vs. extreme user-friendlyness, great gaming support and support of the major software companies

PS: i forgot to mention that maybe as much as 20% of my "love" for win is due to the existence of total commander. i have yet to see a better file manager, no matter if win, linux or osx based. hey, i can even read my linux partitions with it :)

---

### Post by IYY on 2006-05-24
I know that not every Windows user's experience is like mine. I myself have installed Windows on my friends' machines and it works correctly often enough. Just like modern Linux distributions, really; sometimes it works and sometimes it doesn't. Making an OS that'll work on *any* hardware you throw at it is a very difficult task.

---

### Post by Gannin on 2006-05-24
With the newer nVidia drivers, you don't need to edit your xorg.conf file.  When you install the driver, it asks you during installation if you would like the installer to automatically edit the file for you, and if you tell it no, you can always run nvidia-xconfig later, which will do it for you.

---

### Post by IYY on 2006-06-01
So, a few weeks pasted since I installed this operating system. I would have thought that I'd get used to it by now, but instead things got worse:

I only installed software from official sources, and nothing big (Picasa, acrobat reader, software from CDs that came with my hardware like webcam and printer, nero, winamp, quicktime... the basics). I don't know why, but my computer became incredibly slow (especially if I don't reboot it enough). This machine that  worked perfectly with Dapper and all the 3D eye candy turned on, now functions slower than my PII (running Ubuntu). 

I asked my friend about this, and he answered "well, no wonder, you only have 256 MB of RAM. 512 is like a minumum for this OS"... I thought 128 MB was the official requirement, and the website said it should even run on 64. I wonder how much Vista is really going to need if the official website says it needs 512 MB. 

One day my machine also overheated over 80 degrees and then shut itself down after a loud beep. These things never happened in Ubuntu.

I also tried using Windows' own terminal for vi and SSH, and while it is usable, it feels very primitive.

---

### Post by Kronoz on 2006-06-01
[QUOTE=IYY]So, a few weeks pasted since I installed this operating system. I would have thought that I'd get used to it by now, but instead things got worse:

I only installed software from official sources, and nothing big (Picasa, acrobat reader, software from CDs that came with my hardware like webcam and printer, nero, winamp, quicktime... the basics). I don't know why, but my computer became incredibly slow (especially if I don't reboot it enough). This machine that  worked perfectly with Dapper and all the 3D eye candy turned on, now functions slower than my PII (running Ubuntu). 

I asked my friend about this, and he answered "well, no wonder, you only have 256 MB of RAM. 512 is like a minumum for this OS"... I thought 128 MB was the official requirement, and the website said it should even run on 64. I wonder how much Vista is really going to need if the official website says it needs 512 MB. 

One day my machine also overheated over 80 degrees and then shut itself down after a loud beep. These things never happened in Ubuntu.

I also tried using Windows' own terminal for vi and SSH, and while it is usable, it feels very primitive.[/QUOTE]

What I don't understand is why does the Windows CMD have a classic style interface while everything else on the system is in XP style, it doesn't make sense + nothing like as good as BASH though Vista is supposed to have the monad shell but I don't think anything on Windows can ever surpass BASH.

---

### Post by IYY on 2006-06-01
> What I don't understand is why does the Windows CMD have a classic style interface while everything else on the system is in XP style, it doesn't make sense + nothing like as good as BASH though Vista is supposed to have the monad shell but I don't think anything on Windows can ever surpass BASH.

Unless they actually install BASH itself. It's free, after all. Not just free, but also Free, so they can make any modifications they like.

---

