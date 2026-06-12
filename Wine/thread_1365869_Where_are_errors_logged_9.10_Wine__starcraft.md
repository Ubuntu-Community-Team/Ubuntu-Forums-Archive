---
title: "Where are errors logged? 9.10 Wine  starcraft"
date: 2009-12-27
forum: Wine
---

### Post by fishtoprecords on 2009-12-27
I'm trying to install StarCraft again on my laptop. I recently installed Ubuntu 9.10, and the wine setup got lost.

I can install Starcraft from the CD using Wine, (wine 1.0.1) and get through the license dialog, enter the CD key, and it says all is happy. I've even run the patch after I used 'wget' to pull it down.

But when I try to actually run starcraft, it shows the start up screen, with "Play Starcraft". When I click on the link, it just goes away, no error, nothing that I can find in the logs.

Since I have no clue what is wrong, its a bit of a challenge to fix it.

I had this working a year or so ago on this same computer, with earlier Wine/Ubuntu.

Thanks
Pat

---

### Post by fishtoprecords on 2009-12-27
I noticed a link in another thread to a later version of Wine, so I had Synaptic install Wine 1.2.
Which reports itself as Wine 1.1.31 in the wineConfig window

With it, when I try to run Starcraft under Wine, I get the following errors in my shell:

wine StarCraft.exe 
fixme:advapi:SetSecurityInfo stub
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  1017
  Current serial number in output stream:  1017

---

### Post by beastrace91 on 2009-12-27
Go grab the latest version [1.1.35](http://www.winehq.org/download/deb) and give it a go. Last I checked it ran fairly well under this.

~Jeff

---

### Post by fishtoprecords on 2009-12-27
Tried the latest and greatest wine. Or used the link to have apt-get install it, but the config file window shows 1.1.35 still.

Most strange, as the apt-get info seems to claim that 1.2 is installed:
/var/cache/apt/archives/wine1.2-gecko_1.0.0-0ubuntu3_i386.deb
/var/cache/apt/archives/wine1.2_1.1.31-0ubuntu3_i386.deb
/var/cache/apt/archives/wine1.2_1.1.35-0ubuntu1_i386.deb

---

### Post by Soulcage on 2009-12-28
1.1.35 is the most recent version...
Sounds like you might be having video driver problems. I wonder are you using a Intel GPU?

---

### Post by fishtoprecords on 2009-12-28
> **Soulcage said:**
> Sounds like you might be having video driver problems. I wonder are you using a Intel GPU?
I could believe the video driver theory.

Its a separate ATI card. ATI Technologies Inc M56GL [Mobility FireGL V5250] 256MB.  Before 9.10, I ran the ATI closed drivers. But ATI has dropped support for this card, its all of 30 months old. So I have to run the generic open source video drivers.

---

### Post by beastrace91 on 2009-12-28
> **fishtoprecords said:**
>  I have to run the generic open source video drivers.

Thats your culprit. Getting Wine programs to run under ATI with Open Source drivers is currently about as likely as finding the holy grail...

Sorry :-/
~Jeff

---

