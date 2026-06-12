---
title: "Firefox does not automatically open Deluge on most sites."
date: 2009-12-22
forum: The Cafe
---

### Post by brookie on 2009-12-22
Hi all,

Got this weird annoyance with Firefox not opening Deluge automatically on some sites. It only works properly on TPB, but on other sites FF pops up a box that says, 'you have chosen to open...', with the option to open with deluge, or save file. 

I already checked Edit>Preferences>Applications, and checked Bittorent Seed File = Use Deluge Bittorent Client (default). 

FF works with all my other default Application settings, but Deluge will only be automatically opened by FF when I click on a TPB download link. If I click any other torrent download link on any other site I get the FF  popup box. 

Then select 'Open with Deluge' and tick - 'Do this automatically for files like this from now on.' This setting will not work though. 

So, any one else experience this or know of a workaround? I am using Ubunt Karmic Koala, and FF 3.5.6. 

Thanks, 
brook

---

### Post by lovinglinux on 2009-12-23
> **brookie said:**
> So, any one else experience this or know of a workaround?

Setup a folder to be watched by Deluge and set the default behavior of Firefox to save torrents to that folder. This way you don't even have to change any Firefox settings if you decide to switch BitTorrent clients. Just setup all clients to watch the same folder.

It works like a charm for me. I'm currently using Ktorrent this way, but Deluge has the same functionality and I presume Transmission must have too.

---

### Post by brookie on 2009-12-23
Thanks lovinglinux. 

I missed that Deluge setting. Preferencec>Downloade>Auto add .torrents from "Downloads". I set this up and then set up FF>Prefs>Apps to 'save file' for .torrent files instead of open Deluge, and "voila!", Deluge automatically starts them up when I click on a file and it is DLed to my 'Downloads' folder. 
Sweet! 

Now it probably won't work if Deluge is not started but I haven't tested that yet. No more popup box from firefox asking me what to do any longer though. 

Merry Christmas, 
brook

---

### Post by lovinglinux on 2009-12-23
> **brookie said:**
> Now it probably won't work if Deluge is not started but I haven't tested that yet.

It won't, but the torrents will be loaded whenever you start Deluge again.

---

### Post by Grifulkin on 2009-12-23
> **lovinglinux said:**
> It won't, but the torrents will be loaded whenever you start Deluge again.

Yeah it's wicked cool that's how I have mine set up.

---

### Post by lovinglinux on 2009-12-23
> **Grifulkin said:**
> Yeah it's wicked cool that's how I have mine set up.

This is particularly useful for third-party/custom rss torrent downloaders. All you have to do is configure the rss feed to save the file in the watched folder and relax.

---

