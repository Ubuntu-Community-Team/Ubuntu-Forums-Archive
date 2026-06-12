---
title: "Virus Issue"
date: 2009-03-23
forum: Security
---

### Post by sagar_p_parakh on 2009-03-23
I have windows xp on my harddisk but due to plenty of virus it is not working properly (too slow) thus I tried to install ant i virus but it is not getting installed on by HDD.

I even can't format the pc as data will get lost.

Thus I am thinking to scan my pc by by inserting live cd of ubuntu and scan my pc by using anti virus software via ubuntu , can any body help me , how shall i do it ?

---

### Post by bodhi.zazen on 2009-03-23
Your best bet, IMO, is to either use a recovery CD or seek professional help.

You are most likely looking at wiping the HD, reinstalling Windows, and restoring known good data. If you do not know the exact virus causing problems and you do not have a known good back up it will be hard to solve this problem.

Most Linux antivirus will simply delete any suspect file and , IMO, Linux antivirus is very prone to false positive.

---

### Post by cariboo on 2009-03-23
I hope you are comfortable using a terminal, as these instruction depend on using it. 

[list=1]
[*] Go to Sytem-->Administration-->Synaptic Package Manager and search for clamav, and install it.
[*] Mount your hard drive, open an Applications-->Accessories-->Terminal and type:

```
sudo mount /dev/sda1 /mnt
```

[*] In the same terminal change directory to /mnt:

```
cd /mnt
```

[*] Update clamav:

```
sudo freshclam
```

[*] Create a directory to move the infected files to:

```
sudo mkdir /infected
```

[*] scan your windows hard drive:

```
sudo clamscan -r --move=/infected
```

[/list]

This scan will take a while, so you can use the LiveCD to surf the internet while you are waiting.

Jim

---

### Post by Bakon Jarser on 2009-03-23
> **sagar_p_parakh said:**
> I have windows xp on my harddisk but due to plenty of virus it is not working properly (too slow) thus I tried to install ant i virus but it is not getting installed on by HDD.

I even can't format the pc as data will get lost.

Thus I am thinking to scan my pc by by inserting live cd of ubuntu and scan my pc by using anti virus software via ubuntu , can any body help me , how shall i do it ?

Once you are infected you can never really be sure a virus is gone.  You can use a live cd to mount your hard drive and back up your data.  Once you have the important stuff backed up I suggest wiping the hard drive.  It's the only way to be sure.

---

### Post by RansomStark on 2009-03-25
I've had reasonable success scanning windows infected drives with the linux version of AVG (popular windows antivirus)

Install the deb from here and just choose the drive to scan

[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

---

### Post by damis648 on 2009-03-25
> **Bakon Jarser said:**
> Once you are infected you can never really be sure a virus is gone.  You can use a live cd to mount your hard drive and back up your data.  Once you have the important stuff backed up I suggest wiping the hard drive.  It's the only way to be sure.

I would have to agree. If you don't know the virus and can hardly use the computer, it would be best to use the livecd to backup what you need, reformat and reinstall. If you are completely against that right now, I would boot up using an antivirus CD (most are bootable, yours may not be). You could also remove the drive and plug it into another computer and scan from there.

---

### Post by bodhi.zazen on 2009-03-25
> **Bakon Jarser said:**
> Once you are infected you can never really be sure a virus is gone.  You can use a live cd to mount your hard drive and back up your data.  Once you have the important stuff backed up I suggest wiping the hard drive.  It's the only way to be sure.

I am not a fan or proponent of windows, however, as a staff member, I feel we, as a community, should not provide misinformation on these forums, windows or otherwise.

I disagree with this statement. It depends on the virus, but most can be cleaned. It takes some expertise and there are plenty of fee for service "professionals" that can do this for you if it is beyond your technical knowledge of windows.

I would point out that I am no such expert on Windows and would not know how to do this if I could not find step-by-step directions on google.

[http://lmgtfy.com/?q=how+to+remove+virus](http://lmgtfy.com/?q=how+to+remove+virus)

---

### Post by lswartz on 2009-03-25
I have used this [site]("http://http://forums.majorgeeks.com/showthread.php?t=35407") before & it has good advice. It is not an easy process to clean your computer so allocate several hours. Good luck fixing it. 

A clean install works too, but also takes a lot of time.

---

### Post by Bakon Jarser on 2009-03-26
> **bodhi.zazen said:**
> I am not a fan or proponent of windows, however, as a staff member, I feel we, as a community, should not provide misinformation on these forums, windows or otherwise.

I disagree with this statement. It depends on the virus, but most can be cleaned. It takes some expertise and there are plenty of fee for service "professionals" that can do this for you if it is beyond your technical knowledge of windows.


Okay, then let me back up my statement.  [Here]("http://www.av-comparatives.org/") is a link to a site that does independent testing of av programs.  Not a single one of them found 100% of the viruses.  So I'll repeat, the only way to be sure is to do a clean install.

---

### Post by spike_naples on 2009-03-27
Just take the Ubuntu plunge! Screw Windows! :KS

---

### Post by listerdl on 2009-03-27
so a virus cant really live in ubuntu can it?

---

### Post by Bakon Jarser on 2009-03-27
> **listerdl said:**
> so a virus cant really live in ubuntu can it?

There aren't any known viruses in the wild for linux.  However maleware/spyware/rootkits do exist.  The weakest link in any system is almost always the user.  If someone gets you to install a program there is always a possibility that it can compromise your system.  That's why it is recommended that you stick to software sources that you trust, like the official ubuntu repositories.

---

