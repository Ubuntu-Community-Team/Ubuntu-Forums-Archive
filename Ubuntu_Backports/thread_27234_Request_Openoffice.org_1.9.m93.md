---
title: "Request: Openoffice.org 1.9.m93"
date: 2005-04-15
forum: Ubuntu Backports
---

### Post by jasplund on 2005-04-15
I'd really love to see the latest OOo snapshot in backports since there's language packs (swedish) available for that version.


Johan

---

### Post by Gnobody on 2005-04-15
I second that request!

---

### Post by jdong on 2005-04-15
Ok, I'll see if I can get on that.


the last time I tried this, I found the existing build scripts and debianization was already too different because of the fast-evolving nature of OOo 2.

---

### Post by jonny on 2005-04-16
If it helps anyone in the meantime, .deb files are available [here](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m93/Build-1/) , together with loads of language packs.  I'm still on v1.9.92 myself, but I've obtained several builds from this site with no significant problems.

My biggest request is for the OOo gnome integration package.  The standard OOo open and save dialogues are functionally weak, and the Windows-style default colour scheme is *ugly*.

---

### Post by jdong on 2005-04-16
Hmm, now is that ".tar.gz" source archive debianized?

If it is, I have no problem with recompiling it and placing it in "bleeding" for us to play with :)

---

### Post by rwabel on 2005-04-17
[QUOTE=jdong]Hmm, now is that ".tar.gz" source archive debianized?

If it is, I have no problem with recompiling it and placing it in "bleeding" for us to play with :)[/QUOTE]

I've downloaded once the ta.gz and init there where all the .deb files for oo2 beta. I guess that means you can recompile them and place them in "bleeding"

would be great.

I've attached a pic of the archive, sorry for the file size

---

### Post by jasplund on 2005-04-17
It´d be great if you could do that with the language packs as well. Or will it be possiible for me to just brag the language pack from that ftp?


Johan

---

### Post by jdong on 2005-04-17
[QUOTE=rwabel]I've downloaded once the ta.gz and init there where all the .deb files for oo2 beta. I guess that means you can recompile them and place them in "bleeding"

would be great.

I've attached a pic of the archive, sorry for the file size[/QUOTE]

No, those are *binaries*. I was asking about where is the **source code** that this guy used to create the RPM's and DEBs, because they are nowhere to be found on that server.

---

### Post by rwabel on 2005-04-17
[QUOTE=jdong]No, those are *binaries*. I was asking about where is the **source code** that this guy used to create the RPM's and DEBs, because they are nowhere to be found on that server.[/QUOTE]

you are right, sorry.
The only sources I could find are these here. Don't know how recent they are (dated from march, guess still newer than the one in ubuntu hoary)
[http://people.debian.org/~halls/openoffice/source/](http://people.debian.org/~halls/openoffice/source/)

I hope this helps

---

### Post by jonny on 2005-04-17
[QUOTE=jdong]No, those are *binaries*. I was asking about where is the **source code** that this guy used to create the RPM's and DEBs, because they are nowhere to be found on that server.[/QUOTE]If you install the binaries, you get his contact details in Help -> About OpenOffice.org.  I won't post them here to spare him the worst of the world of spam, but he's part of the OpenOffice team and might well be willing to point you towards his source files.

I won't try to contact him myself, as I'd be unlikely to understand the questions that need to be asked  :???:

---

### Post by jdong on 2005-04-17
Ok. After this server migration dust settles, I'll look further.

---

### Post by Gnobody on 2005-04-21
Anything new on upgrading to the latest milestone of OO.o2 ?

---

### Post by jasplund on 2005-04-26
Anything new?

1.9.95 is available now btw

---

### Post by asimon on 2005-04-26
[QUOTE=jasplund]1.9.95 is available now btw[/QUOTE]

This version seems to have some serious issues. See the thread ["Don't use OpenOffice.org Beta (1.9.95)"](http://ubuntuforums.org/showthread.php?t=29572).
But according to that thread there is a 96 milestone on the ftp server which fixes that issue.

---

### Post by damonw5 on 2005-04-30
I'd love an OpenOffice backport... anything > 1.9.76  :)

---

### Post by jdong on 2005-05-01
Remind me why Canonical is being so slow with Breezy development???

I'm not gonna spend 10+ nonstop hours trying to get Openoffice2 to patch and compile, just to find out it's a buggy beta.


I'll backport when I can find someone else's debianized sources for Openoffice.

---

