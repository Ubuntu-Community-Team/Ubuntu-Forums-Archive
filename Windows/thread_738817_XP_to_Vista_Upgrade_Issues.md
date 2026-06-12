---
title: "XP to Vista Upgrade Issues"
date: 2008-03-29
forum: Windows
---

### Post by 64Media on 2008-03-29
I've been using XP Home for a while and I just upgraded my system to Windows Vista Home Premium. After the migration, my sound and internet doesn't work.

It says that an output audio driver has not been installed, and as far as the internet goes, it can't find a driver for the ethernet controller on the system. So I'm using my brother's computer to post.

I'm a bit more concerned about the internet problem first, so what information would you need to try to fix my problem and how can I obtain it?

---

### Post by PmDematagoda on 2008-03-29
> **64Media said:**
> I've been using XP Home for a while and I just upgraded my system to Windows Vista Home Premium. After the migration, my sound and internet doesn't work.

It says that an output audio driver has not been installed, and as far as the internet goes, it can't find a driver for the ethernet controller on the system. So I'm using my brother's computer to post.

I'm a bit more concerned about the internet problem first, so what information would you need to try to fix my problem and how can I obtain it?

What a strange question to ask on a Linux forum where our main focus is on providing support for Linux.

Anyway, this thread has been moved to the Windows Discussions section.

---

### Post by Inxsible on 2008-03-29
This is a Ubuntu Linux forum, if you haven't realized it.

However, since we are all so helpful, I would suggest you first make sure that you PC is vista capable. (Altho, Microsoft has a lawsuit against them for the very word "capable" that they used for some machines which actually could not run Vista --- anyway)

You would also need to get drivers for Vista as the XP drivers for the sound will not work. You may want to contact the website for the manufacturer of the said device to get the latest drivers, if available

---

### Post by hhhhhx on 2008-03-29
i would suggest a clean install, if possible :)

---

### Post by Midwest-Linux on 2008-03-29
> **64Media said:**
> I've been using XP Home for a while and I just upgraded my system to Windows Vista Home Premium. After the migration, my sound and internet doesn't work.

It says that an output audio driver has not been installed, and as far as the internet goes, it can't find a driver for the ethernet controller on the system. So I'm using my brother's computer to post.

I'm a bit more concerned about the internet problem first, so what information would you need to try to fix my problem and how can I obtain it?

 This may or may not work, I reinstalled XP Home on a used desktop computer. Everything went well, except I could not get on the internet. XP Home did not recognize that particular ethernet card I had in the PCI slot. I swapped out that card for another newer  ethernet PCI card and I was able to have internet Xp recognized this card. But I needed that  newer card for my newer system.

 Now, I wanted to take this a step further. Why would the original ethernet card work with the original XP installed on this used desktop, but this same original ethernet card  would not work after a  clean new install? I was missing the ethernet controller card for that older card. 

For the newbies.
Ethernet net controller card is a software, not to be confused with the actual ethernet PCI hardware card. Read on.

 So I swapped the older original card back in, again no internet. Went and did some research on Ethernet controller cards. I needed a driver for this card.

[http://www.belkin.com/support/article/?lid=en&pid=F5D5005&aid=5431&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D5005&aid=5431&scid=0)


The driver is here for my card

[http://www.belkin.com/support/article/?lid=en&pid=f5d5005&aid=5431&scid=0&fid=1813&fn=f5d5005.exe](http://www.belkin.com/support/article/?lid=en&pid=f5d5005&aid=5431&scid=0&fid=1813&fn=f5d5005.exe)

On another computer   I downloaded the driver it was like a 12 MB exe file. I downloaded it onto a CD as a data file. 

Took the disc and went to the used XP Home desktop, I clicked control panel,  add hardware, looked up the PCI card (it had a question mark) next to it. Double clicked it and went through the promps where it said that part to insert the disc with the driver on it. 

And sure enough it installed the "controller card" software. The driver and the controller card are one and the same (at least from what I can see) and that file, F5D5005.exe did install the older ethernet PCI card on the used desktop.


Then my internet worked absolutely fine from that point on with the older original card in that used desktop computer. 

On that Belkin page there is a driver for a Vista Beta. It may or may not work for your Vista Home Premium.

 If anything I hoped I pointed you in the right direction.

---

### Post by Dojan5 on 2008-03-29
> **64Media said:**
> I've been using XP Home for a while and I just upgraded my system to Windows Vista Home Premium. After the migration, my sound and internet doesn't work.

It says that an output audio driver has not been installed, and as far as the internet goes, it can't find a driver for the ethernet controller on the system. So I'm using my brother's computer to post.

I'm a bit more concerned about the internet problem first, so what information would you need to try to fix my problem and how can I obtain it?

You got vista all right! :lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:
A tips, ask on a M$ forum...

---

### Post by kamaboko on 2008-03-29
> **Midwest-Linux said:**
> This may or may not work, I reinstalled XP Home on a used desktop computer. Everything went well, except I could not get on the internet. XP Home did not recognize that particular ethernet card I had in the PCI slot. I swapped out that card for another newer  ethernet PCI card and I was able to have internet Xp recognized this card. But I needed that  newer card for my newer system.



OK...so we can gather from this that XP didn't have the native drivers for the older card as part of its install.  Not surprising.  Happens with Ubuntu all the time.  Did you have the PCI card drivers and did you try to install them?

> 

Now, I wanted to take this a step further. Why would the original ethernet card work with the original XP installed on this used desktop, but this same original ethernet card  would not work after a  clean new install? I was missing the ethernet controller card for that older card. 



Just a stab here, but was the original XP install done at the manufacture site?  Perhaps they installed propriatary drivers.  


I could say the same thing for the latest version of Hardy.  Why would Gutsy and Mint install on my Vostro and fire up, while Hardy sits and sputters?

---

### Post by Midwest-Linux on 2008-03-29
> **kamaboko said:**
> OK...so we can gather from this that XP didn't have the native drivers for the older card as part of its install.  Not surprising.  Happens with Ubuntu all the time.  Did you have the PCI card drivers and did you try to install them?



Just a stab here, but was the original XP install done at the manufacture site?  Perhaps they installed propriatary drivers.  


I could say the same thing for the latest version of Hardy.  Why would Gutsy and Mint install on my Vostro and fire up, while Hardy sits and sputters?

 Yes XP  Home did not have the drivers for the card the used computer it originally with (when I did the re-install). Before the re-install of XP Home the card worked fine (meaning the drivers ..ie controller card software was there- but not after the new re-install).

 XP Home did recognize another card  instantly and installed it but would not install the original card that came with that computer (I bought the computer used at a flea market).

 I found the controller card software for the computer at the Belkin site like I mentioned, maybe others can use that controller card software for their XP driver issues...if they have any.


So to everyone out there who cannot get on the internet for one reason or another with a Linux distro,  simply swap out another ethernet  PCI card.  It may work.

---

