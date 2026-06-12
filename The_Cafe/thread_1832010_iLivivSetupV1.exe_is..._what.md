---
title: "iLivivSetupV1.exe is... what?"
date: 2011-08-24
forum: The Cafe
---

### Post by t0p on 2011-08-24
Earlier on I started doing a bit of peer-to-peer with Transmission and [Planet Bay]("https://theplanetbay.org").  Since embarkin on this venture (about an hour now) I have got two pop-up windows saying

> 
You  have chosen to open
**iLividSetupV1.exe**
which is a: DOS/Windows executable
from [http://download.cdn.ilivid.com](http://download.cdn.ilivid.com)

[b]What should Firefox do with this file?[b]

*Open with Archive Manager (default)
*Save File


Of course, being a Linux user, an unasked-for .exe means little to me.  But I am a curious soul.  So first I tried to browse to that link ([http://download.cdn.ilivid.com](http://download.cdn.ilivid.com)) and got this 403 message:

> 
ForbiddenYou don't have permission to access / on this server.
Apache Server at download.ilivid.com Port 80


I went to [iLivid.com]("http://ilivid.com/"), and apparently iLivid is a super-duper new download manager, which does pretty much what all download managers do.

The unsolicited pop-up and link therein worries me.  If a user uses a Windows OS and is not *au fait* with the nefarious workings of the internet, he might click on that link.  And what would happen?  Well, I don't know.  It might be innocuous, it might be evil.

On my computer I have Wine and VirtualBox with a virtual XP running on it.  Is there any danger if, for instance, I started my virtual XP and opened iLividSetupV1.exe, would I be safe? Or would it be better to keep my curiosity in its box and let my cat live a little longer?

---

### Post by Oxwivi on 2011-08-24
If it's a malware, your XP install in VBox is going to be infected, but there's no reason for Ubuntu to be affected.

---

### Post by aeiah on 2011-08-24
take a snapshot of your machine, install it, play around, and then revert your virtual machine back to its prior state.

its probably not harmful, just annoying, but you never know

---

### Post by Dr. C on 2011-08-24
It is also distributing VLC Media player and 7Zip in contravention of their respective licenses including the GPL v2. 

From the ilivid EULA: ilivid.com/eula.txt

> 5.5 iLivid combines video and compression abilities by using 3rd parties open source code.
iLivid uses VLC Media Player and 7zip which are under the GNU license, the source code is available in the following sites: VLC - [www.videolan.org/vlc](www.videolan.org/vlc) 7zip - [www.7-zip.org](www.7-zip.org) 

The trouble here is that is this is a commercial product so section 3c of the GPL v2 does not apply. From [http://www.gnu.org/licenses/gpl-2.0.html](http://www.gnu.org/licenses/gpl-2.0.html) > c) Accompany it with the information you received as to the offer to distribute corresponding source code. (This alternative is allowed only for noncommercial distribution and only if you received the program in object code or executable form with such an offer, in accord with Subsection b above.) 

The purpose of this malware is to change the settings in IE on a Microsoft Windows System in order to direct queries to their pay per click search engine and collect advertising revenue. In the process of doing this they can do a lot of damage to a Microsoft Windows System even if one does not use IE. It is also part of a disturbing trend where malware distributors are pirating Free Libre Open Source Software. VLC is a common target.

---

### Post by dmizer on 2011-08-24
On most torrent sites, there is a way to report a torrent as malicious. You should do so with that torrent.

---

