---
title: "AVG Free"
date: 2008-11-11
forum: Server Platforms
---

### Post by Vegan on 2008-11-11
I noticed that AVG now has a package for Linux, 

Installation packages are available here:
For Debian based distributions (Debian, Ubuntu,..) avg75fld-r51-a1243.i386.deb
For RedHat based distributions (RedHat Linux, Fedora Core,..) avg75flr-r51-a1243.i386.rpm
For SuSE based distributions (SuSE Linux, Novell Linux Desktop,..) avg75fls-r51-a1243.i386.rpm
For Mandriva based distributions (Mandrake Linux, Mandriva,..) avg75flm-r51-a1243.i386.rpm

So now there is security for us server administrators (ya right).

Problem is I attempted to install the Debian version, apt-get could not find it. Yo!

:guitar:

---

### Post by HermanAB on 2008-11-11
I use ClamAV on my mail servers.  Together with SpamAssassin, it works well enough.

---

### Post by Vegan on 2008-11-11
The AVG version for Windows seems to be adequate so when I saw it was available for Linux I felt a standardized approach would be simpler.

---

### Post by Thirtysixway on 2008-11-11
I think the only reason to have antivirus on a linux machine is to help protect your friends from email viruses who are using windows.

---

### Post by Vegan on 2008-11-12
Do I have to cite that worm that ran rampant around the *IX community unchecked for weeks before a fix was developed.

---

### Post by coffee_bean on 2008-12-28
Why do these threads always turn into "Linux doesn't need AV"!? It makes them useless and boring.

I'm running a file server with Ubuntu Server 8.10, which many Windows users connect to. Oddly, many (mail, web, file, torrent, media...) servers in the world are now *nix, and indeed will want to protect users of vulnerable systems, be they Linux, Windows or whatever, of viruses.

So, I'd like to run a good, robust and updateable AV system on my linux box, and am pleased to see AVG taking an interest. The pity is, I can't tell which of the bunch (Avast, ClamAV or AVG...) might be the better choice.

---

### Post by 2hot6ft2 on 2008-12-28
Look here. [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
It has the linux anti virus apps available and a simple how to for installing AVG is linked in the page.
Why did this 2 month old thing get revived.

---

### Post by windependence on 2008-12-29
> **Vegan said:**
> I noticed that AVG now has a package for Linux, 

Installation packages are available here:
For Debian based distributions (Debian, Ubuntu,..) avg75fld-r51-a1243.i386.deb
For RedHat based distributions (RedHat Linux, Fedora Core,..) avg75flr-r51-a1243.i386.rpm
For SuSE based distributions (SuSE Linux, Novell Linux Desktop,..) avg75fls-r51-a1243.i386.rpm
For Mandriva based distributions (Mandrake Linux, Mandriva,..) avg75flm-r51-a1243.i386.rpm

So now there is security for us server administrators (ya right).

Problem is I attempted to install the Debian version, apt-get could not find it. Yo!

:guitar:

You need to be in the same directory as the file was downloaded. Did you read the instructions?

I am an AVG partner if you need help or licenses.

-Tim

---

### Post by coffee_bean on 2008-12-29
> **2hot6ft2 said:**
> Look here. [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
It has the linux anti virus apps available and a simple how to for installing AVG is linked in the page.

Thanks, that's very useful :)

> **2hot6ft2 said:**
> Why did this 2 month old thing get revived.

Because it's still relevant?

---

### Post by SuperSonic4 on 2008-12-29
I just use avast really,

```
sudo avast <dir>
``` where <dir> is the directory

---

### Post by 2hot6ft2 on 2008-12-29
> **coffee_bean said:**
> Because it's still relevant?
I hope that Vegan wasn't still waiting for an answer none the less.

---

### Post by coffee_bean on 2008-12-30
> **2hot6ft2 said:**
> I hope that Vegan wasn't still waiting for an answer none the less.
I'll give you that.

While I hope he's sorted out, I've got some useful replies without having to start a thread on exactly the same subject.

---

### Post by Vegan on 2009-03-21
It seems that there is little for the CLI users like me. I have rkhunter and that is it so far. I was hoping to find something a bit more comprehensive.

---

### Post by windependence on 2009-03-22
clamav is pretty good but I don't know if it's in the Ubuntu repos. I've had good luck with it and it's stable.

-Tim

---

