---
title: "Ransomware"
date: 2017-06-28
forum: Security
---

### Post by gordie692 on 2017-06-28
Hey guys with Ubuntu or any other Linux distro this ransomware does it affect Linux systems and what to do to prevent it sorry for the dumb question just trying to cover my tracks even with Linux

---

### Post by #&amp;thj^% on 2017-06-28
As far as I have heard this is only on windows.
Just keep updating your system, and sensible browsing.
> WannaCry exploits a set of flaws in Microsoft's implementation of the SMB1 protocol. Since these are implementation flaws rather than structural flaws in the protocol itself, Linux systems cannot be automatically infected, but can be if manually installed. This is true regardless of if the systems are running Samba, Wine, or any other Windows-emulation layer.
More found here: [https://security.stackexchange.com/questions/159397/does-wannacry-infect-linux#159405](https://security.stackexchange.com/questions/159397/does-wannacry-infect-linux#159405)


Plus it has been sugested that a simple rename of certain files may help: Again more info found here: [https://security.stackexchange.com/questions/153660/rename-important-files-to-any-file-type-to-protect-from-ransomware](https://security.stackexchange.com/questions/153660/rename-important-files-to-any-file-type-to-protect-from-ransomware)

But beawre Renaming individual files might protect against some types of ransomware but not others.
And this was an Interesting read "Ransomware Guide": [https://blog.varonis.com/the-complete-ransomware-guide/#variants](https://blog.varonis.com/the-complete-ransomware-guide/#variants)
And last**_ but certainly not least_**, Your best protection against ransomware is to keep good backups.

---

### Post by &amp;KyT$0P# on 2017-06-28
> **gordie692 said:**
> this ransomware
Which ransomware?  Some do affect Linux systems and some don't.

---

### Post by gordie692 on 2017-06-28
Thanks guys thats's what I thought I always do my updates don't what it is

---

### Post by TheFu on 2017-06-29
It runs on Windows, but uses any network file system that a Windows system can see.  So.... in short, if you let Windows see your Linux-based files via NFS or CIFS or Samba, then your linux files are in danger from these common and becoming more common attacks.

There are only 2 solutions:
* stay patched for all your OSes - Windows, Linux, Routers, smartphones
* Daily, automatic, **versioned**, backups.
* Don't use any file sharing protocol like cifs, samba, nfs, for your backup methods. Use a secured, encrypted, client server method.  
* Avoid locally connecting backup storage too. This would just allow all your backup storage to become encrypted too.

On Linux, the tools that can do daily, automatic, **versioned**, backups are 100% F/LOSS.

---

### Post by webmiester on 2017-08-26
Hi,

Regarding Windows being able to see our mapped drives:  Will there be a way from preventing a Ransomware infected Windows computer from encrypting our Linux NAS?  Perhaps adding password protection for windows to access might work?

---

### Post by HermanAB on 2017-08-26
Ayup, nowadays even FTP is more secure than SMB/CIFS, because the script kiddies are unfamiliar with it.  This is similar to manual cars that don't get stolen in the USA/Canada, since the kids don't know how to drive them.

FTP is also more efficient and easier to install and manage than SAMBA/CIFS and it is one of the few network file systems that is supported natively by Windows.  So if you want to improve the security of Windows against current ransomware, then you could change your servers to FTP and disable SMB/CIFS:

[http://www.aeronetworks.ca/2017/02/simple-file-server.html](http://www.aeronetworks.ca/2017/02/simple-file-server.html)

---

### Post by TheFu on 2017-08-26
> **webmiester said:**
> Hi,

Regarding Windows being able to see our mapped drives:  Will there be a way from preventing a Ransomware infected Windows computer from encrypting our Linux NAS?  Perhaps adding password protection for windows to access might work?

Don't let Windows see the NAS as a mapped drive or as local storage (as NFS does it).

I'm going to disagree with using plain FTP.  That protocol should have died when telnet died.  Sometimes the solution is worse than the problem.  Plain FTP has all sorts of issues, mainly because people will use it outside a secured network.
You can use sftp - winscp is a nice client with drag-n-drop.  It supports both sftp, scp.  There are other clients too.  Pretty much every networked OS has clients.

But really, nothing replaces versioned, daily, automatic, backups that are "pulled", never pushed.  If the client has direct access to the storage area, that is what these viruses like.  A NAS doesn't solve that - often, it consolidates it and makes it challenging.   Also, lots of people get confused into calling their NAS the "backup", but don't actually keep other copies.  If you change a single file every day, then your backups should have a way to restore that file every day *as it was at the time*.  THAT is how we fight against Windows viruses and general data corruption issues.  Pulled, versioned, daily, backups.

---

### Post by webmiester on 2017-08-27
FTP is kinda interesting, but I think my staff wont be proficient enough to use it.  I think they will get appaled just by looking at it.   TheFu, can you recommend an automatic backup program of some sort I can look into and consider?  Thanks so much.

---

### Post by HermanAB on 2017-08-28
"I think my staff wont be proficient enough to use it" - Why?  Once it is mapped to a local machine it works transparently just like any other mapped folder.  You can run MS Word, open a file, edit it and save it - no different from Samba/CIFS/NFS/whatever.

---

### Post by Habitual on 2017-08-28
[https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

---

### Post by 1clue on 2017-08-28
I've seen reports of several incidents of ransomware on Linux. The difference between ransomware on Windows vs ransomware on Linux is trivial, and could be as simple as using a standard libraries platform-independent call for some task rather than assuming C:\ or whatever.

Plain old FTP is worse than telnet with respect to security, as far as I'm concerned. Don't ever use it, for anything. It was around when gopher protocol was still big.

There are a few things you can do to prevent ransomware, and those things are pretty well documented for other operating systems. I don't think it's all that different for Linux.

Past prevention is mitigation, and that's the really big one. Develop a plan for backups, implement it and stick to it.  Some notes on backups:
[LIST=1]
[*]RAID is not a backup. RAID satisfies only one or two of the many reasons you might want a copy of your data. Every RAID documentation you will find says that RAID is not a backup. RAID helps your application stay online in spite of drive failure, that's it. RAID will make absolutely no difference with respect to ransomware.
[*]Rsync is not a backup. Rsync does not help you if your file is corrupted or deleted on your source system and the rsync happens before you find the problem.
[*]If the copy of the data remains online, it's not a backup. If the copy remains online it can be found and corrupted or stolen, and is susceptible to fire, flood, lightning, theft, etc.
[/LIST]

Ransomware can be viewed as file corruption. You will want to reinstall your system and then go back to your most recent uncorrupted copy of the data. And then change passwords.

---

