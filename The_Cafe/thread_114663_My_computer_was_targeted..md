---
title: "My computer was targeted."
date: 2006-01-09
forum: The Cafe
---

### Post by Omnios on 2006-01-09
A while back I was playing around with samba and left my shares open for my local network. Gnome crashed and  I just downloaded CLamAv, well the scan showed 11 viruses, right now im removing the files and may have to reinstall counting on how much damage is done. I think the files are root ownership so I think I should change my user passwords.

---

### Post by towsonu2003 on 2006-01-09
11 viruses in linux (for linux) or in windows (for windows)?

if it's linux and they have root ownership, I would do a fresh install (if they got root, who knows)

---

### Post by BSDFreak on 2006-01-09
[QUOTE=Omnios]A while back I was playing around with samba and left my shares open for my local network. Gnome crashed and  I just downloaded CLamAv, well the scan showed 11 viruses, right now im removing the files and may have to reinstall counting on how much damage is done. I think the files are root ownership so I think I should change my user passwords.[/QUOTE]

NEVER go on the net at all without a configured firewall no matter which OS you are using.

11 viruses for Linux and where? In binaries outside of your shares? If it's in your shares then just delete the files and you'll be fine.

Your root account should be disabled by default, and most definently disabled for remote logins.

---

### Post by JimmyJazz on 2006-01-09
never share your root its as simple as that .

---

### Post by prizrak on 2006-01-09
If you don't need to share with Windows then NFS is your friend :) Not that it's all that more secure than Samba (or at least I don't think so) but its a bit more obscure to a casual attacker.

---

### Post by nocturn on 2006-01-09
[QUOTE=prizrak]If you don't need to share with Windows then NFS is your friend :) Not that it's all that more secure than Samba (or at least I don't think so) but its a bit more obscure to a casual attacker.[/QUOTE]

NFS is very bad security wise, most of the permission checking is done client side, which means you have no control over it.

nfsv4 promises to be better (kerberos based), but we'll have to wait it out.

---

### Post by Omnios on 2006-01-09
Damage Done! like a 1/100 chance of this hapening or 1 in a million.

 ```
----------- SCAN SUMMARY -----------
Known viruses: 42108
Engine version: 0.87.1
Scanned directories: 14192
Scanned files: 120731
Infected files: 9
Not removed: 9
Data scanned: 5454.92 MB
Time: 4520.987 sec (75 m 20 s)
tom@main:~$       
```

```
Scan started: Mon Jan  9 12:44:52 2006

//usr/share/apps/krita/templates/gray/.source/white_640x480.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/gray/.source/white_640x480.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/transparent_1024x768.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/transparent_1024x768.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/transparent_1280x1024.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/transparent_1280x1024.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/transparent_1600x1200.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/transparent_1600x1200.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/transparent_640x480.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/transparent_640x480.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/white_1024x768.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/white_1024x768.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/white_1280x1024.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/white_1280x1024.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/white_1600x1200.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/white_1600x1200.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/white_640x480.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/white_640x480.kra: Can't remove

-- summary --
Known viruses: 42108
Engine version: 0.87.1
Scanned directories: 14192
Scanned files: 120731
Infected files: 9
Not removed: 9
Data scanned: 5454.92 MB
Time: 4520.987 sec (75 m 20 s)
```

 Think I have one or two on my vfat drive but will have to scan to make shure.

 Now should I try removing these files or should I just reinstall?

---

### Post by Arktis on 2006-01-09
Well, I think there is a grand total of 10 viruses in the history of linux.  I am most probably wrong though.  [This page]("http://www.viruslibrary.com/virusinfo/Linux.htm") shows only 7.  Hey, there could be more, and probably are.  Anyways, the viruses you picked up are probably windows viruses.  I don't even think ClamAv detects linux viruses, but again, I may be wrong there.

---

### Post by BSDFreak on 2006-01-09
[QUOTE=Omnios]Damage Done! like a 1/100 chance of this hapening or 1 in a million.

 ```
----------- SCAN SUMMARY -----------
Known viruses: 42108
Engine version: 0.87.1
Scanned directories: 14192
Scanned files: 120731
Infected files: 9
Not removed: 9
Data scanned: 5454.92 MB
Time: 4520.987 sec (75 m 20 s)
tom@main:~$       
```

```
Scan started: Mon Jan  9 12:44:52 2006

//usr/share/apps/krita/templates/gray/.source/white_640x480.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/gray/.source/white_640x480.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/transparent_1024x768.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/transparent_1024x768.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/transparent_1280x1024.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/transparent_1280x1024.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/transparent_1600x1200.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/transparent_1600x1200.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/transparent_640x480.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/transparent_640x480.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/white_1024x768.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/white_1024x768.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/white_1280x1024.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/white_1280x1024.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/white_1600x1200.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/white_1600x1200.kra: Can't remove
//usr/share/apps/krita/templates/rgb/.source/white_640x480.kra: Oversized.Zip FOUND
//usr/share/apps/krita/templates/rgb/.source/white_640x480.kra: Can't remove

-- summary --
Known viruses: 42108
Engine version: 0.87.1
Scanned directories: 14192
Scanned files: 120731
Infected files: 9
Not removed: 9
Data scanned: 5454.92 MB
Time: 4520.987 sec (75 m 20 s)
```

 Think I have one or two on my vfat drive but will have to scan to make shure.

 Now should I try removing these files or should I just reinstall?[/QUOTE]

Most probably you don't have any viruses at all.

From [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)

> 
I get many false positives of Oversized.zip

Whenever a file exceeds ArchiveMaxCompressionRatio (see clamd.conf man page), it's considered a logic bomb and marked as Oversized.zip . Try increasing your ArchiveMaxCompressionRatio setting. 

I have about 30 of them with ArchiveMaxCompressionRatio set at default, none of them are viruses and no other virus program i've tried (such as AVG for Linux) reports them as threats.

---

### Post by GeneralZod on 2006-01-09
If it sets your mind at rest, here are the md5sums from my install of the krita files.  If they match, and your probability estimates are correct, then this is a 1/10000 - 1/1000000000000 chance :)

```


$ krita -v
Qt: 3.3.4
KDE: 3.4.3
Krita: 1.4.1

$ locate kra | grep krita | grep source | xargs md5sum
84962ae5a636bd6bfe9e28bb9209fb39  /usr/share/apps/krita/templates/gray/.source/white_640x480.kra
c9f52a58b3c410b8dc1e704586992452  /usr/share/apps/krita/templates/rgb/.source/transparent_1024x768.kra
ad58336ae86e8fbd55deffc06317e2c7  /usr/share/apps/krita/templates/rgb/.source/transparent_1280x1024.kra
be924d90f4c97cb24e3f9ccb327f0a55  /usr/share/apps/krita/templates/rgb/.source/transparent_1600x1200.kra
69d9737d441990e6c99fcfdda35e4d2a  /usr/share/apps/krita/templates/rgb/.source/transparent_640x480.kra
7b63e1d3c4c22c95880c81479fcb0595  /usr/share/apps/krita/templates/rgb/.source/white_1024x768.kra
b345134081b44ca869b5ebc9dac61e32  /usr/share/apps/krita/templates/rgb/.source/white_1280x1024.kra
ff51acff6a43ac13a1a3c9411e332ae6  /usr/share/apps/krita/templates/rgb/.source/white_1600x1200.kra
442295678f819bc036649672f2277613  /usr/share/apps/krita/templates/rgb/.source/white_640x480.kra
b7ecbec09a06d78698742f495972f05b  /usr/share/apps/krita/templates/empty/.source/empty.kra

```

This is the x86 version of Kubuntu 5.10; the version of krita is shown above.

---

### Post by linkunderscore on 2006-01-09
Viruses in linux? 

I wasn't aware that such things existed...

---

### Post by ubuntu27 on 2006-01-09
[QUOTE=linkunderscore]Viruses in linux? 

I wasn't aware that such things existed...[/QUOTE]

Virus created in the "lab" [As I call it] for experiments in Linux :P

Dosn't damage anything unlesss you are running as root. 

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

TRY TO INFECT LINUX WITH LINUX: [http://os.newsforge.com/article.pl?sid=05/01/25/1430222](http://os.newsforge.com/article.pl?sid=05/01/25/1430222)

---

### Post by nocturn on 2006-01-10
[QUOTE=linkunderscore]Viruses in linux? 

I wasn't aware that such things existed...[/QUOTE]

In practice, they don't.  But Linux computers can carry windows virusses (not being infected by them).  

In this case, the OP stated that he left Samba (Windows) shares open, so the files themselves could have been infected.

As it turns out, this may also be a false positive from ClamAV

---

### Post by prizrak on 2006-01-10
There are viruses that will run on Linux. There was the Apache slammer at some point (I believe that one was using SSH vulnerabilities to spread). There are a few for sendmail. Any widely used piece of software is gonna have viruses for it. Linux viruses just tend to be targeted more at stuff that runs on top of the OS rather than the OS itself (well also true for Windows but there is more integration).

---

### Post by towsonu2003 on 2006-01-10
[QUOTE=BSDFreak]Most probably you don't have any viruses at all.
[/QUOTE]
try submitting them to an online file virus scanner. I had a link to such a site but it's at home -sorry.

---

### Post by BSDFreak on 2006-01-10
[QUOTE=towsonu2003]try submitting them to an online file virus scanner. I had a link to such a site but it's at home -sorry.[/QUOTE]

Or download another antivirus scanner, there are plenty of them for Linux.

---

### Post by Omnios on 2006-01-10
Found a how to for F-prot. I Dual boot and have a XP partion and a Vfat partition for my documents and mounting in Linux. My Ubuntu has its own drive. As for aanti virus I have computer associates EZ security and all my mail is virus scanned by the isp  ****.yahoo.mail. My main concern for a anti virus is to have some linux protection and  possibly scan the vfat drive for win viruses but not nessassary. 

[[COLOR="Red"]F-prot[/COLOR]]("http://ubuntuforums.org/showthread.php?t=88357")

 Aanyone know anything about F-prot?

---

### Post by BSDFreak on 2006-01-10
[QUOTE=Omnios]Found a how to for F-prot. I Dual boot and have a XP partion and a Vfat partition for my documents and mounting in Linux. My Ubuntu has its own drive. As for aanti virus I have computer associates EZ security and all my mail is virus scanned by the isp  ****.yahoo.mail. My main concern for a anti virus is to have some linux protection and  possibly scan the vfat drive for win viruses but not nessassary. 

[[COLOR="Red"]F-prot[/COLOR]]("http://ubuntuforums.org/showthread.php?t=88357")

 Aanyone know anything about F-prot?[/QUOTE]

If i were you i'd start by configuring clamav the way they have suggested so you won't get this false positive again, if this doesn't work then try F-prot.

Clamav is a great av toolkit, it's just a tad too sensitive at times (not that that is a bad thing).

---

