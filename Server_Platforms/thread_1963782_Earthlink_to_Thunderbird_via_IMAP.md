---
title: "Earthlink to Thunderbird via IMAP"
date: 2012-04-22
forum: Server Platforms
---

### Post by [::AP::] on 2012-04-22
Greetings,

Point me in the right direction if this has already been discussed. 
I've looked over this:
[http://ubuntuforums.org/showthread.php?t=745815](http://ubuntuforums.org/showthread.php?t=745815)
I know it is a few years old. 

My mother's XP machine crashed about a month ago. She used Earthlink Mailbox to store emails, which she not only used for communication, but as a means to archive and save thousands of links, documents, etc. Her working life is on their. 

I saved the DAT files from Earthlink Mailbox and moved them to another XP machine, temporarily, and installed Earthlink Mailbox. Everything is exactly like it was. Seeing that she will be using Thunderbird on her new Windows 7 machine, I need to transfer every email, with attachments and dates, in their proper organization (folders), to Thunderbird. 

I have read that people have achieved this using the .eml save method (as described in the link), or syncing with an IMAP server. 

The .eml export way doesn't work for me (I forward the attachments, open in Thunderbird, but they are totaling 0 bytes and when I "save as" to a directory, nothing shows up.)

That leaves me with IMAP. 
From what I have read, once you get it running, it is pretty simple. However, I don't really know where to begin. I know I can set up an IMAP server on any OS, and it is easy in *nix, (which brings me to this subforum), but I am lost from there. 

Could you guys/gals point me in the right direction?

Preferably, in layman's terms, as I am a bit unfamiliar with networking. [SIZE="1"](I don't know how else to put this, but I am not a complete noob [I've set up several Arch installations, with help from their amazing wiki, of course], so "moderate - somewhat advanced" stuff is fine, but idk when it comes to networking) [/SIZE]

**TL;DR** 
Point me in the right direction when it comes to setting up an IMAP server to transfer Earthlink Mailbox emails to Thunderbird (intact, with attachments)

Regards, 

[::AP::]

---

### Post by [::AP::] on 2012-04-23
Update: Looking into Dovecot, making headway. 

Still a bit lost (understatement). Help?

---

### Post by tallship on 2012-04-24
Try this. Works like a champ everytime :)

[http://bit.ly/OfflineIMAP](http://bit.ly/OfflineIMAP)

I hope that helps!

Kindest regards,

.

---

### Post by [::AP::] on 2013-04-07
A year later!
Sorry to dig this back up from the grave. As far as I'm concerned, this thread can be closed. 
Also, I don't know if I am inept today, but is there no 'edit post' feature?

Anyways, I happened to stumble on this post via Google, and, realizing that I had solved this issue, I thought I should update this.

I followed Donkeypuss' guide. I didn't use a server. I suppose it is the same/similiar method as described in the OP.
[http://projects.m-qp-m.us/donkeypuss/migrating-from-earthlink-mailbox-to-mozilla-thunderbird_2008-06-19](http://projects.m-qp-m.us/donkeypuss/migrating-from-earthlink-mailbox-to-mozilla-thunderbird_2008-06-19)
ImportExportTools plugin for Thunderbird. [https://addons.mozilla.org/en-us/thunderbird/addon/importexporttools/](https://addons.mozilla.org/en-us/thunderbird/addon/importexporttools/)

---

