---
title: "Where is recent security update of ClamAV-0.88_4 ?"
date: 2006-08-26
forum: Server Platforms
---

### Post by Ilya Evseev on 2006-08-26
Hi, folks!
On 8 August an serious update of ClamAV antivirus was published:
denial of service on corrupted UPX-packed executables.
Where can I get it for 6.06 LTS?
Ubuntu-security-announce still doesn't contain any info about this problem.

WBR, Ilya

---

### Post by lotusleaf on 2006-08-27
Right now, if you want the latest version of [ClamAV](http://www.clamav.net), you can download the source ([clamav-0.88.4.tar.gz](http://prdownloads.sourceforge.net/clamav/clamav-0.88.4.tar.gz?download) and compile it yourself (it's easy), get it from someone else who has a .deb of it, or request it in backports.

I build the latest version of ClamAV with each new release but I don't have a .deb handy at the moment.

---

### Post by Ilya Evseev on 2006-08-27
Hmm.. I think that "downloading sources and compile it yourself" can be a good idea for LFS,
but not for The-Most-Advanced-Linux-Distro-For-Newbies-And-Professionals with Long-Term-Support.:rolleyes: 
I prefer "apt-get update && apt-get upgrade"

What do you mean under backports? Debian site [www.backports.org?](www.backports.org?) Well, he provides updated package, but with very long delay: ClamAV exploit was described on 8-Aug-2006 and package at [http://mirror.buildd.net/backports.org/pool/main/c/clamav/](http://mirror.buildd.net/backports.org/pool/main/c/clamav/) is dated by 16-Aug-2006. In comparison with all other major Linux distributions (Fedora, Mdk, Suse, PLD, ALT) and FreeBSD this is too late.

---

### Post by peter07 on 2006-08-31
> On 8 August an serious update of ClamAV antivirus was published:
denial of service on corrupted UPX-packed executables.
Where can I get it for 6.06 LTS?
Ubuntu-security-announce still doesn't contain any info about this problem.

I'm just installing clamav, and only 0.88.2-1ubuntu1 version is available ( in standard repo). When the new official package ( from security updates ) will be available ( The new one is in egdy )?

---

### Post by jimwillsher on 2006-10-10
*Bump*

---

