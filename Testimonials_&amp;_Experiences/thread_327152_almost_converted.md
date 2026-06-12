---
title: "almost converted"
date: 2006-12-28
forum: Testimonials &amp; Experiences
---

### Post by seijuro on 2006-12-28
I'm in the process of converting my dad to ubuntu. For the most part things are going well he's even willing to live w/o a few things he had on windows till he learns the linux equivalents. All could be smooth sailing from here if I could just manage to get his hp 3570c scanjet scanner to work. If anyone has some experience getting this particular scanner or another 35xx series that's covered under the same driver to work please chime in with any tips/pointers you may have.

---

### Post by gjtoth on 2006-12-28
> **seijuro said:**
> I'm in the process of converting my dad to ubuntu. For the most part things are going well he's even willing to live w/o a few things he had on windows till he learns the linux equivalents. All could be smooth sailing from here if I could just manage to get his hp 3570c scanjet scanner to work. If anyone has some experience getting this particular scanner or another 35xx series that's covered under the same driver to work please chime in with any tips/pointers you may have.

It would be helpful to know what it's doing (or not doing) and what you've tried already.  Try this:  Hit alt-f2 and type "gksu xsane"  If xsane picks up on it, there's your workaround until someone more knowledgeable comes along and steps you through it.  If it doesn't, I'm afraid I'm outta ideas.

---

### Post by seijuro on 2006-12-28
well currently when a scan is started it gets to about 3% then just stops. I've installed the extra backends so that the right driver was there and sane-utils so that I could run sane-find-scanner which does detect his scanner. I have not messed with any config files or anything of that nature yet. I was poking around google and other message boards and a lot of things suggested getting the newest versions so I installed the newest releases of the packages and we're still at the same spot.

---

### Post by kvonb on 2006-12-28
Looks like you're out of luck, even turboprint doesn't seem to list the 35xx series in their supported list :???:.

The easiest way would be to buy a new supported printer, no consolation, but it's all I've got :rolleyes:.

Printers are cheap in the US, you can buy 4 for the price we pay over here for 1!

I remember buying a Lexmark from Wal-Mart which came with both cartridges and a free ream of photo paper for only $35us!  When the cartridge ran out it was cheaper to buy a new printer, we ended up with 3 of the things!

Regards, Kev :)

---

### Post by seijuro on 2006-12-28
well according the the sane-project website under the supported devices listing it is supported but the support is not complete apparently the high resolution scans are lossy. Incedently my dad will most likely just switch back to windows rather than buy a new scanner.

EDIT: ok he surprised me he said he is willing to get a new scanner but now a new problem has occured. He wants to listen to an audio stream that uses hurl from RealPlayer we installed linux realplayer/helix but it says it's unable to play the content anyone know how to play this audio stream? the site he wants to listen to is [http://www.audio-bible.com/bible/bible.html](http://www.audio-bible.com/bible/bible.html) if anyone can listen to the audio on this site in ubuntu please tell me how you did it and with what program/plugins etc.

---

### Post by Orval on 2006-12-29
I have a HP 3570c scanner and it worked after a fresh install of Edgy. I can scan perfectly now using kooka. So it should work.

---

### Post by Orval on 2006-12-29
> **seijuro said:**
> well according the the sane-project website under the supported devices listing it is supported but the support is not complete apparently the high resolution scans are lossy. Incedently my dad will most likely just switch back to windows rather than buy a new scanner.

EDIT: ok he surprised me he said he is willing to get a new scanner but now a new problem has occured. He wants to listen to an audio stream that uses hurl from RealPlayer we installed linux realplayer/helix but it says it's unable to play the content anyone know how to play this audio stream? the site he wants to listen to is [http://www.audio-bible.com/bible/bible.html](http://www.audio-bible.com/bible/bible.html) if anyone can listen to the audio on this site in ubuntu please tell me how you did it and with what program/plugins etc.

It works. When I just click on a chapter, a new tab in Firefox opens and the MPlayer plugin loads and plays the sound file. You can use Automatix to install the MPlayer plugins.

---

### Post by seijuro on 2006-12-29
> **Orval said:**
> I have a HP 3570c scanner and it worked after a fresh install of Edgy. I can scan perfectly now using kooka. So it should work.

Thanks I'll try upgrading him to edgy and installing mplayer.

---

### Post by kvonb on 2006-12-29
Once again it seems that I mis-read a post!

You were talking about a scanner, and I read it as printer :confused:.

I've also been typing words backwards and inside out lately too, may be time to see a quack :rolleyes:.

Please excuse my temporary insanity.

Regards, Kev :)

---

### Post by seijuro on 2006-12-29
Update: SCANNER IS WORKING!!!! WOOO! worked out of the box fresh install of edgy. We ran short on time tonight so I'll get around to mplayer tomorrow.

Cheers,
Thanks for the help.

---

### Post by Orval on 2006-12-30
You're welcome!

---

### Post by saulgoode on 2006-12-30
> **kvonb said:**
> I remember buying a Lexmark from Wal-Mart which came with both cartridges and a free ream of photo paper for only $35us!  When the cartridge ran out it was cheaper to buy a new printer, we ended up with 3 of the things!


Many printer manufacturers will ship their new printers with cartridges that are only 1/3 full (or less). This permits them to lower the price and *appear to be* more competitive. You would be better off if you bought replacement cartridges as they will last much longer than those in a new printer.

---

### Post by seijuro on 2006-12-31
all squared away every kink in the road smoothed out and another happy linux user is made.

enjoy your new toy dad.

---

