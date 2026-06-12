---
title: "Ubuntu &amp; windows partitions"
date: 2007-07-11
forum: Server Platforms
---

### Post by Wiebelhaus on 2007-07-11
There's a specific setup I'm needing to perfect and preferably using Ubuntu to do so and I'm looking for idea's , advice or maybe a little brain storming.

At a small PC repair shop I'm currently working at the majority of our business is viral/spy removal , I'm a hardcore Ubuntu fan boy and I'm trying to work Ubuntu into my daily work routine , I'm THE only Linux fan in the shop the other folks are old school windows platform aficionados , I myself have advanced windows experience but I hate windows with a passion and I know that Linux can do what I need to do better , I just need to perfect the technique a bit , I'm looking for advice in other words.

The older days of using DOS scanners is becoming cumbersome and I've been using an XP machine with an external bay:
[IMG]http://specialtech.co.uk/spshop/files/master/sata-external-enclosure-a.jpg[/IMG]
 Via USB with a few variances in regards to SATA controllers and laptop drives , you can imagine.

I've have been for a few years w/ great success , running the drive as an external drive and scanning them with a few different programs over the years , started off with Norton corp , But I've found AVG to work very well and detect & remove allot , What AVG didn't catch I'd run Adware , AVG anti-spy/Giant etc , Once these programs removed what they could , I would then boot the PC , clean temp , start up , user tracking , restore partitions etc. 

I now use Ubuntu exclusively in my home , network with a server setup and I'd like to do so at work as well , I've tried F-prot which does a pretty good job , AVG only reports (gay..) Bit defender and so on , I'm not having as good of results as I would using the windows platform set up I described earlier.

Why not just keep doing it with windows? a few reasons the most obvious windows sucks , Gets contaminated , unstable , have to reformat every month or two to get the lag out. Ubuntu is just some much more secure , network friendly and stable as a rock , I'd like to have the security of Ubuntu having the inability to get contaminated by a horribly infected windows partition.

So my question is , am I overlooking a Linux tool (command or GUI) to perform these type of tasks , Live CD or installed and is anyone using this type of setup , essentially doing the same thing? If your doing with Linux may I ask what's your most successful methods?

Thanks , 6.

---

### Post by Wim Sturkenboom on 2007-07-12
Sorry to say, but I don't understand your post.

You want to 'clean' windows disks ( which you place in an external enclosure ) using Linux?

---

### Post by Footballkid4 on 2007-07-12
If you need a *nix antivirus program, I have heard good stuff about ClamAV [http://www.clamav.net/](http://www.clamav.net/)

The problem is that Linux isn't well exposed to viruses and therefore there is little motivation to make antivirus programs.  In this situation it may be better to try downloading the WINE (windows emulator) and running something such as AVG though there...if it will even work.  I'm thinking it'll probably have trouble detecting your filesystems.

[http://winehq.org](http://winehq.org)

**Edit:** AVG/Norton might work through wine.  I searched through the AppDB on Wine and found a few AV products already.

---

### Post by Wiebelhaus on 2007-07-12
> **Wim Sturkenboom said:**
> Sorry to say, but I don't understand your post.

You want to 'clean' windows disks ( which you place in an external enclosure ) using Linux?

That is precisely what I'm trying to do.

---

### Post by Wiebelhaus on 2007-07-12
> **Footballkid4 said:**
> If you need a *nix antivirus program, I have heard good stuff about ClamAV [http://www.clamav.net/](http://www.clamav.net/)

The problem is that Linux isn't well exposed to viruses and therefore there is little motivation to make antivirus programs.  In this situation it may be better to try downloading the WINE (windows emulator) and running something such as AVG though there...if it will even work.  I'm thinking it'll probably have trouble detecting your filesystems.

[http://winehq.org](http://winehq.org)

**Edit:** AVG/Norton might work through wine.  I searched through the AppDB on Wine and found a few AV products already.

I'll give wine a try , thanks for the input.

---

### Post by koenn on 2007-07-12
Knoppicillin used to do womething similar : it was a Knoppix Live CD with F-PROT, Kapersky and Sophos ant-virs, + ntfs and FAT support. 

It is set up so that you boot from the CD, and it will first update its virus definitions from the internet, then let you scan the disks of the pc it's running on. 
It's been a while since I've heard from it - here's an old announcement I found : [http://www.heise.de/newsticker/meldung/51213](http://www.heise.de/newsticker/meldung/51213) , and apparently there's still an iso here: [http://www.bits-bytes.ch/programme/knoppicillin-3.1.iso](http://www.bits-bytes.ch/programme/knoppicillin-3.1.iso)

So, you could either use that, or have a close look at what it does and see if you can reproduce it on your Ubuntu machine.

---

### Post by kitterma on 2007-07-12
Well clamav is a perfectly good virus scanner (in fact it is quite frequently used on mail servers to prevent virii getting to Windows clients).  If you want a GUI for it, you'll need klamav (the clamtk is Feisty is broken with the clamav in Feisty).

---

### Post by Wiebelhaus on 2007-07-13
> **koenn said:**
> Knoppicillin used to do womething similar : it was a Knoppix Live CD with F-PROT, Kapersky and Sophos ant-virs, + ntfs and FAT support. 

It is set up so that you boot from the CD, and it will first update its virus definitions from the internet, then let you scan the disks of the pc it's running on. 
It's been a while since I've heard from it - here's an old announcement I found : [http://www.heise.de/newsticker/meldung/51213](http://www.heise.de/newsticker/meldung/51213) , and apparently there's still an iso here: [http://www.bits-bytes.ch/programme/knoppicillin-3.1.iso](http://www.bits-bytes.ch/programme/knoppicillin-3.1.iso)

So, you could either use that, or have a close look at what it does and see if you can reproduce it on your Ubuntu machine.


thank you for the link , good stuff there.

---

### Post by Wiebelhaus on 2007-07-13
> **kitterma said:**
> Well clamav is a perfectly good virus scanner (in fact it is quite frequently used on mail servers to prevent virii getting to Windows clients).  If you want a GUI for it, you'll need klamav (the clamtk is Feisty is broken with the clamav in Feisty).


I in the past had a horrible time with clam , that must have been the bug you speak of , thanks I will give it another try.

---

