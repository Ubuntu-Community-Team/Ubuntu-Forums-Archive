---
title: "Opinions of Wubi"
date: 2008-04-25
forum: The Cafe
---

### Post by Paqman on 2008-04-25
So Wubi is an official method of installing Ubuntu now. I like to hang out in the Absolute Beginner forum and help newbies, so I thought I should educate myself and give it a try-out.

I have to say, i'm seriously impressed. This dramatically lowers the installation hurdle for new users. I think we should push this option hard for first-timers.

Some facts you might not know about Wubi:

- It won't touch Grub, so if you want to try it on an existing dual-boot it's no-hassle. I attaches itself to NTLDR instead.
- Running Wubi off a LiveCD will fully install Hardy in only a few minutes
- The online installer is a 1.1MB download that when run will pull down and install the correct image
- It unistalls cleanly from the Windows Add/Remove tool

---

### Post by GammaPoint on 2008-04-25
I think it's a good idea. I plan to see if my brother wants to try it.

---

### Post by cookieofdoom on 2008-04-25
It's very nice. The only problem is that it relies on the Windows MBR, which means it will probably never be stable. I had a friend who's Windows install broke because of WUBI. He was able to get it all sorted out with a restore disk, though.

---

### Post by Paqman on 2008-04-25
> **cookieofdoom said:**
> I had a friend who's Windows install broke because of WUBI.

That's the big risk, I guess. The problem is that a lot of the folks who're electing to use Wubi might not be able to fix that if it breaks. We don't want to get a reputation for breaking people's Windows installs. Maybe Wubi should have a warning pop up reminding people to back up. That way, if they end up borking their system they've got no one to blame! ;)

---

### Post by Anduu on 2008-04-25
I bought my first laptop a few weeks ago.I wasn't sure how the hardware would work under Hardy so I took the lazy way out and installed from Vista with Wubi.Everything works well.

It works so well I don't know if I'll even bother switching to a dedicated install.

I have been running Ubuntu on my desktop for a couple of years now so I have no fear of running into things I don't know how to fix.

Wubi is the cat's pyjamas :)

---

### Post by Zakhafr on 2008-04-27
Hello Paqman,

sorry to fire you enthousiasm, yes Wubi is a damn good idea... if only it worked !

And it's very bad, it hasn't been tested **AT ALL**... with international versions of Windows.

In france, Windows XP Home Edition is called *Windows XP **É**dition Familiale* (it means Family Edition as you would have guessed), and apparently the **É** being an UTF-8 character not in the first 128 US-ASCII chars doesn't please Wubi at all.
Installation crashes when Wubi tries to read parameters from windows (around 85%).

I hope someone would fix it soon so that I can change my vote to "I like it".

Regards

*P.S. : there is no vote "Try it doesn't work"... so I put "don't like it" although I'll very much like to try it !*

---

### Post by maniacmusician on 2008-04-27
I haven't tried it, but yes, it certainly does seem to lower the hurdle for newer users. However, in a different thread, another forum-goer did comment that an installation with WUBI would result in slower load times for apps and whatnot. Which would make sense; I'm pretty sure that WUBI uses ntfs-3g to access the fake partition created in the Windows drive (I remember some discussion about the stability of ntfs-3g when WUBI was first released). Since ntfs-3g is reverse engineered driver using FUSE, it would be understandably slower than the native, open source ext3 driver.

---

### Post by gn2 on 2008-04-27
I don't like it because if Windows falls ill and dies, it will take the Wubi Linux installation with it.

---

### Post by Anduu on 2008-04-27
> **maniacmusician said:**
> I haven't tried it, but yes, it certainly does seem to lower the hurdle for newer users. However, in a different thread, another forum-goer did comment that an installation with WUBI would result in slower load times for apps and whatnot. Which would make sense; I'm pretty sure that WUBI uses ntfs-3g to access the fake partition created in the Windows drive (I remember some discussion about the stability of ntfs-3g when WUBI was first released). Since ntfs-3g is reverse engineered driver using FUSE, it would be understandably slower than the native, open source ext3 driver.

I am sure Wubi slows things down a bit however on my new laptop it is still pretty darn snappy.

One of these days I'll get around to a dedicated install so I can see what the difference is.Until then I am not going to complain about performance ;)

---

### Post by maniacmusician on 2008-04-27
> **Anduu said:**
> I am sure Wubi slows things down a bit however on my new laptop it is still pretty darn snappy.

One of these days I'll get around to a dedicated install so I can see what the difference is.Until then I am not going to complain about performance ;)
Fair enough :) I was just speculating anyhow. It's good to know that you don't feel like Wubi is slowing you down. It means either that the ntfs-3g drivers are really good, or that my assumption about how it works was wrong. Perhaps I'll go investigate that further, my curiosity is piqued.

---

### Post by Linuxratty on 2008-04-27
I tried downloading it on two different machines. In both cases,the download failed.
I was very disappointed,to say the least.

---

### Post by capink on 2008-04-27
> **gn2 said:**
> I don't like it because if Windows falls ill and dies, it will take the Wubi Linux installation with it.

I have not tried wubi yet. So I maybe wrong here. But from what I understood about it, it will not die when the windows install dies, because it is just a file (a virtual partition of filesystem that is loop mounted) in the windows partitions. The only scenario that could make it die with windows is that the windows boot loader get corrupted, which can be easily corrected using the recovery consloe.

---

### Post by Paqman on 2008-04-27
> **capink said:**
> The only scenario that could make it die with windows is that the windows boot loader get corrupted

That's my understanding, too. There seems to be a lot of confusion out there regarding how Wubi works. A lot of people seem to think it's some kind of emulator that runs on top of Windows.

---

### Post by benhur99ph on 2008-04-28
Hmm,  I don't know about you guys, but when I tried using Wubi to install Hardy it went well. Installation finished fast and I was able to configure Compiz fusion to my liking. I tested every compiz effect and it works. 

The only downside that I can think of for now is that, as previously mentioned, is that since its still residing inside Windows and Windows crashed. Then my Ubuntu is done for. 

I suggest using Wubi if you just want to try Ubuntu out, then when you are satisfied, move it to a dedicated partition.. (Can I do this without reinstalling ubuntu?)

---

### Post by hessiess on 2008-04-28
I would gess that while in windows, it complety ignores the scuraty settings oon the 'partition', so it would be posable for a windows virus to corupt linux data?

---

### Post by maniacmusician on 2008-04-28
> **benhur99ph said:**
> Hmm,  I don't know about you guys, but when I tried using Wubi to install Hardy it went well. Installation finished fast and I was able to configure Compiz fusion to my liking. I tested every compiz effect and it works. 

The only downside that I can think of for now is that, as previously mentioned, is that since its still residing inside Windows and Windows crashed. Then my Ubuntu is done for. 

I suggest using Wubi if you just want to try Ubuntu out, then when you are satisfied, move it to a dedicated partition.. (Can I do this without reinstalling ubuntu?)
From the Wubi FAQ:

> 

Can I move my virtual disk file to a dedicated partition?

For Wubi 7.04 and 7.10, you can use [LVPM]("http://lubi.sourceforge.net/lvpm.html") to transfer your install. A guide and support forum for LVPM is available [here]("http://ubuntuforums.org/showthread.php?t=438591"). 8.04 is not yet supported by LVPM.



---

### Post by NightwishFan on 2008-04-28
My friend has a slow windows install on his pc, and I could not risk removing the mbr so I installed xubuntu hardy with wubi and it runs perfectly.

---

### Post by gn2 on 2008-04-28
> **capink said:**
> from what I understood about it, it will not die when the windows install dies, because it is just a file (a virtual partition of filesystem that is loop mounted) in the windows partitions. The only scenario that could make it die with windows is that the windows boot loader get corrupted, which can be easily corrected using the recovery consloe.

Wubi installs Ubuntu into a normal folder(s) which is created in the location of your choosing on an NTFS or Fat Windows partition.

It is subject to the same insecurities and vulnerabilities as any other folder in a Windows installation.

Wubi is an interesting development and very clever how it works, but having a Linux installation depend on Windows for it's security is more than just a little ironic?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by toupeiro on 2008-04-28
I've been running it since its announcement for 8.04 on my laptop and I am very impressed by it!  I can confirm the comments about a slight performance hit, but this is definately a good option for those gun shy about repartitioning.

---

### Post by maniacmusician on 2008-04-28
> **gn2 said:**
> Wubi installs Ubuntu into a normal folder(s) which is created in the location of your choosing on an NTFS or Fat Windows partition.

It is subject to the same insecurities and vulnerabilities as any other folder in a Windows installation.

Wubi is an interesting development and very clever how it works, but having a Linux installation depend on Windows for it's security is more than just a little ironic?

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
It's not relying on Windows so much as the user. As insecure as Windows might be, we all know it's possible to keep it running without any major glitches as long as you're taking care of your installation. Of course, this takes a lot more work in Windows than it does in Linux, but that's that. If the user ends up somehow hosing their Windows installation, they would have ended up suffering the same data loss anyways. That very reason is why Wubi offers no guarantees. User's responsibility.

---

### Post by gn2 on 2008-04-28
> **maniacmusician said:**
> It's not relying on Windows so much as the user. 

Agreed. The main problem with Windows is that it is not in itself secure enough to cope with many of it's users.

PEBCAK and PICNIC spring to mind.

---

