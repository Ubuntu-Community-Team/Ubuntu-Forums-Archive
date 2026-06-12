---
title: "Has SSH -X always done this?"
date: 2007-10-07
forum: The Cafe
---

### Post by Mr. Picklesworth on 2007-10-07
I have one of my computers working as a high traffic SSH server, now. It used to do SSH, FTP, and a number of other things, but then I realized that SSH is an infinitely better system for just about anything, since it does *everything* well and securely. After a few weeks using SSH for file transfers and web development (even editing the remote files in place with a local text editor and with permissions behaving exactly how they should), it is beyond me why people are using FTP...

Anyhow, I just now decided to run ssh with the X command line, for fun. I suddenly noticed that it uses my settings that I have locally; widgets, icons and colours are all correct, and the toolbar is displaying just icons (as I have locally) rather than icons / text (as set on the server). I do not remember that being so transparent the last time I used it... Has it always been like this?

---

### Post by mattigras on 2007-10-18
I just got ssh working for the first time 20 minutes ago and it's incredible! After spending 8 hours practically breaking my audio trying to get PulseAudio working, it's much easier to just SSH into Amarok on my desktop from my laptop. (only took me half an hour to figure it out). 

When you're running ssh -X, are your colors correct too? I'm tunnelling into a Xubuntu box from a Kubuntu box.  I have 2 amarok's open right now. The local instance is colored orange (like the rest of my Halloween festive lappy), but the ssh'd Amarok is using the default KDE colors except for the window decorations....so not completely transparent, but close enough.

I'm just amazed in general at the power of SSH, and i've only scratched the surface. Right now I'm having fun opening and closing the cd-drive from across the room.

---

