---
title: "Calendar Server?"
date: 2008-11-09
forum: Server Platforms
---

### Post by Twizzle on 2008-11-09
I was wondering if someone can point me in the right direction and hope that this is the best place to ask.

I have (with a lot of help from these forums) managed to setup a home server running Ubuntu 8.04 server edition. I use this as a simple file server (using samba) so my office PC (Ubuntu 8.10) and Media PC (Windows XP) can access it. I also run zoneminder on it which is recording a single camera.

Webmin is installed but I think I will remove it as 1) I don't use it and 2) I am aware that it may give hackers an extra way to get in.

I am aware that I can setup an email server onto the server and have seen numerous walkthroughs etc.

I am happy though using gmx for my mail as their servers are probably better protected than mine! and so at this stage, won't bother messing with the email side. I also have a dynamic DNS.

What I really want to do though, is run a calendar server if possible. I would like to be able to access my calendar on both computers and my N95.

In an ideal world I would like my N95 to sync over my home wireless network when I walk in through the front door and then say every hour or so. I have had some success syncing the N95 over bluetooth with evolution, but as I understand it, that won't work in a server situation.

The closest I have come to see this working is with goosync and google calendar but that takes the calendar away from me which I don't really want.

I apologies if this is the wrong forum and also if what I am asking does not really make sense!

---

### Post by RC Howe on 2008-11-27
I use the calendar server package, which is the open source version of Apple iCal server. I have managed to get it working with Evolution, and it works with Thunderbird/Lightning or Sunbird. There are also various Outlook connectors available.

The N95 may be a bit more trouble, but if you have previously had Bluetooth support from evolution it can sync Server --> Evolution --> N95 and vice versa. I have not tried this, however.

The problem with calendar server is that it is complicated and can be difficult to configure. I followed the tutorial [here]("https://wiki.kubuntu.org/CalendarServer"). The instructions for Ubuntu Server 7.10 worked for 8.10 as well.

---

### Post by veloce on 2009-02-09
This may be a bit late in coming but for the N95 you might want to look at Funambol.  It will sync calendars and tasks with just about anything.  You can run it with or without the calendar server.

It will also do "push email" to most devices.

I am going to have a try at setting up the calendar server package as well.

---

