---
title: "Ubuntu Server(s) specification help request"
date: 2008-03-13
forum: Server Platforms
---

### Post by winebottle on 2008-03-13
Hi all, I',m looking at trying to hardware specify a new linux server and would welcome any thoughts and comments.

Primary Server tasks:

•	File server with critical company files (database, reference docs etc) (mostly serving to windows machines using Samba etc)
•	Mail server (fetchmail, postfix, dovecot (IMAP), Hylafax)
•	Fax server ()
•	Possible future Intranet (Apache etc)
•	Possible future MySQL (replacing MS Access backend)
•	Very long term – possible LTSP server (would probably use another server set up for this alone)

	Should all of the above run on one server?

Admin Requirements

•	Any easy admin front end, ie a GUI such as Ubuntu coupled with something like Webmin (we’re not Linux guru’s hence we want something robust and easy to administer when things expand or go wrong). Although I’m quite happy using the command line, other colleagues may not be as happy hence I’d rather cater for both tastes.

Company info

•	Number of users: currently 11 but want to cater for up to 50 in the future.

Things I’ve assumed we’re going to need hardware wise along with a possible explanation on why I think we need it –always stand o be correct though!!

•	Hardware RAID, either 1 or 5 with the ability to hot swap drives quickly and easily.
•	Drives – size was either 2 or 4 (depending on raid type chosen) @ 250 / 500gb, 7200 RPM, SATA2. Drives should be HOTSWAP format. Should we mix brand types to spread the possibility of multiple failure? I appreciate in a RAID situation you should always replace a failed disk immediately but manufacturing tolerances being what they are these days (ie very tight), having two drives fail within hours of one another may not be unheard of.
•	Some form of external (Firewire?) external storage access
•	Memory? 1 or 2gb of RAM ?
•	CD/DVD
•	I assume we can escape the requirement for a floppy drive!
•	Power supply – has to be reliable and will have to be backed up with a UPS which has to have the capability (via USB or serial) to gracefully shutdown the server in the event of long term power failure. I’ve had a catalogue of PS’s fail in various machines over the years hence a quality brand suggestion here would be good.
•	CPU – open to suggestions here (based on what we want and potentially want of the server in the future). The cooler running the better I guess with an architecture which will fit current and future requirements as mentioned above.
•	Modem – I sticky subject in Linux I know. Something that is bog standard and works with Linux would be fine. Would be used only for faxing using (to be used with Hylafax).
•	USB – several sockets would make sense if we have to plumb in memory sticks, mice, keyboards etc etc
•	SERIAL Port – my paranoia – just in case we need to stick an external modem (should the internal one fail or if and external one is just easier to deal with to start with). Possibly two serial ports should the UPS requirement only offer a serial connection to the server.
•	NETWORK 1Gb card (separate or on board). Should we have one or two ports? I’m not sure on the advantages/disadvantages here. Although network card failure is rare, should we provide for a redundancy option or is it overkill?

As you can probably tell I’m relatively new at this and would welcome any thoughts and ideas on how to spec our server requirement. Like many we’re looking for a simple, robust scaleable solution to our server requirements.

Sorry for the long post but I hope it provides everything (info wise) in one lump.

Cheers

Winebottle

---

### Post by Harlequin on 2008-03-13
[B]
Should all of the above run on one server?
[/B]

No probably not - but they could be in the short term.

I feel like I'm on a CLark COnnect worship path tonight - but again look at it as it will do 99% of what you have asked for.
- File Server
- MYSql server
-Mail server
-Apache
-WebMail
-Ldap
Unsure about the fax server - never built one....  Clark Connect does come with an excellent gui interface.

For storage - look at FreeNas.  It will fit on a 32mb CF card and be up and running in under 10 mins.  It will allow Samba and NFS connections quickly and easily.  I am running 4 x 500gb drives in a raid 10 arrangement.  I am however using software raid - hotswap is not supported by my software raid - if a drive goes down i remove and replace while the system is on then restart the server - FreeNas then auto rebuilds the array (reboot time - approx 25 seconds).  Obviously this isn't good enough for all but its fine for what I need.  

Depending on your clients you can either NFS mount the FreeNAS to the Clark COnnect server or allow direct connections to it.

Finally hardware....

I'm not a big subscriber to super machines... I tend to use cheap easily replacable and plentiful hardware platforms.  I run AM2 motherbaords in all my desktops and servers.  Just plain old gigabyte stuff.  The only real difference between my servers and the desktops is I stick more RAM in the servers.  That and I like antec stuff so my servers get expensive cases with decent power supplies - such as a ture power or HE Antec PSU.  

As for all of the redundancy your talking about in your hardware I personally wouldn't bother.  For the cost of the higher spec redundant hardware you could have a whole redundant machine waiting to go.  All of this assumes the server is in the same building as you and your users and not sitting in adatacenter somewhere. Servers where the data is the critical should be running raid mirror.  In the event of major hardware failure you should be able to just rip the hdd out - plug them into your backup machine and your off and running in 5 mins...

Your specs.

 
• Hardware RAID, either 1 or 5 with the ability to hot swap drives quickly and easily.

• Drives – size was either 2 or 4 (depending on raid type chosen) @ 250 / 500gb, 7200 RPM, SATA2. Drives should be HOTSWAP format. Should we mix brand types to spread the possibility of multiple failure? I appreciate in a RAID situation you should always replace a failed disk immediately but manufacturing tolerances being what they are these days (ie very tight), having two drives fail within hours of one another may not be unheard of


Raid 10 over raid 5 - this gives you speed and redundancy - 4 disks - I would keep to the same manufacturer due to differences in size.  500gb is not always 500gb - I think a multi-disk failure is very low on your risk level.
.
• Some form of external (Firewire?) external storage access

Why?  Is this for off site backup?  Expanding your storage?  If its just more storage just keep adding freenas boxes.  If offsite then drive caddies are the way to go for large data or DVD backup.

• Memory? 1 or 2gb of RAM ?

Min 4gb.  The more the better. 4 x 1gb chips is like $100 bucks....max.  

• CD/DVD

dvd burner - any one will do

• I assume we can escape the requirement for a floppy drive!
• Power supply – has to be reliable and will have to be backed up with a UPS which has to have the capability (via USB or serial) to gracefully shutdown the server in the event of long term power failure. I’ve had a catalogue of PS’s fail in various machines over the years hence a quality brand suggestion here would be good.

APC for a UPS - MGE is also good.  Any of their decent ones have serial controlls.  As for the PSU - Antecs have served me well.

• CPU – open to suggestions here (based on what we want and potentially want of the server in the future). The cooler running the better I guess with an architecture which will fit current and future requirements as mentioned above.

My Preff is AMD - but that is purely me - I run dual core AM2 X+ cpus ranging from 4000+ to 5200+.  They are cheap and easily obtained.  I'm no where near ceiling on those but the mobo's are all compatible with amd's Quad core chips in the event they sdtart to struggle.


• Modem – I sticky subject in Linux I know. Something that is bog standard and works with Linux would be fine. Would be used only for faxing using (to be used with Hylafax).

Can't comment - never done it.

• USB – several sockets would make sense if we have to plumb in memory sticks, mice, keyboards etc etc

Mice and KB is fine - personally I would keep memory sticks a mile away from my server... Plug them into a desktop and transfer the files.....

• SERIAL Port – my paranoia – just in case we need to stick an external modem (should the internal one fail or if and external one is just easier to deal with to start with). Possibly two serial ports should the UPS requirement only offer a serial connection to the server.

Again standard hardware - just find a consumer mobo with your needs.

• NETWORK 1Gb card (separate or on board). Should we have one or two ports? I’m not sure on the advantages/disadvantages here. Although network card failure is rare, should we provide for a redundancy option or is it overkill?

pretty much everything is 1gb on board.  If you're worried about it buy some cheap 1gb network cards as a backup.

---

