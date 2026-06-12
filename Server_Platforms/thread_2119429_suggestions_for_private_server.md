---
title: "suggestions for private server"
date: 2013-02-23
forum: Server Platforms
---

### Post by SebSnake on 2013-02-23
Well, hi there :)

First of all, english is not my native language, but I try my best. Secondly, I am really new to linux/ubuntu. 
I had my first contacts with it, but not more. I wanted to set up some local server for out family network with some internet access. 
So far we are using 4 PCs, 2 Notebooks and 3 Android Phones, so I got the idea of building one central server to store the private 
files (documents, pictures, music, videos, mail, contacts, calendar, tasks, notes), to have them everywhere in sync. 

For the last month I tried to establish some server-like-thing with "Windows Server 2012". But me and "Exchange 2013" did not 
really work great together (it hated me I guess), so I gave the penguin a try. 
Well, ubuntu has one new fanboy - so far I love it!

---

What I WANT to do is the following: 
a) I need the possibility to have access to my files in our local network by all devices. 

b) I need access to my files from the internet, for example while sitting at the university or 
at friends and need to get a file from my harddisc or something. Most important point here: security.

c) Thought about a music-server for listening to my music in LAN and maybe WAN - only if secure.

d) Small video-transcoding-thing for getting not-support-material to my television.

e) Some DLNA-server for viewing photos on the "big screen" (TV again)

f) My own mailserver for centralized email access (have multiple accounts at web/gmx and 
so on + own domains but with limited mailboxes).

g) Some groupware solution for syncing Outlook and Android contacts, calendar, notes and tasks.

h) And of course some backup solution.

---

Now here is what I HAVE so far:

a) SAMBA-server works like a charm for me. Multiple users for different access-rules - exactly the way I want it.

b) For now, I use an FTP over SSL (FTPS? SFTP? I always confuse the two) thing, vsftpd or something 
like that. Every user (3) has his own folder (and only THIS ONE FOLDER) where he can upload and 
download stuff. These folders are mounted inside of there samba-private-folders. By using samba they 
can copy files they need inside the "online"-folder, which is the only one accessible from the web. 
But the FTP-user-accounts can not delete files for security purposes. Thought it is a good idea.

c) I've got an apache running (with php+mysql) and a working amapche-server on it. Every user has a 
listening-account without any rights but listening. The folder with the music is a public shared (LAN) 
folder in samba. So everyone can put their music inside the amapache-music-folder.

d) Not done yet, but I heard about something called "subsonic"? This thing seems to do what I need. 
Some web-based video-server with on-the-fly transcoding into flv-files or something. Need to reed more about it first.

e) minidlna seems to do the thing already. Again, the "source-folder" is a public shared samba-accessible-folder,
so everyone can put their (not so private) holiday-pictures in it to show them to friends on the television.

f+g) Not done yet, but I read something about "SOGo 2", another web-based software running on an apache server,
which is some groupware-mailserver-thing with native (!!) Outlook-syncing-support. I know there are better tools 
than Outlook, but the old ones in the family don't want to have something else than their beloved Outlook...

h) I am really proud for of my solution here: Everything is installed and saved on a 2 TB HDD. On the hardware-side 
I have made some construction which allows a second 2 TB HDD to boot only once a day in the night for exactly 1 hour 
(maybe half an hour later). That means I need some script or anything which reacts on the "here-I-am" from the HDD 
(when it boots up) to make an easy one-side sync from HDD1 to HDD2. If a file was deleted on HDD1, delete it on HDD2. 
If there is something new or changed on HDD1, copy it to HDD2. I'm going to do this once everything else is finished. 

---

And now my questions:
1) What do you think about my solution so far?
2) About security: is there some way to limit access to the FTP protocol for special devices 
meaning the smartphones and notebooks)? I just don't want to have my files spread around the net - just to my devices please.
3) Anything else you can suggest me? Alternate programs, scripts or anything?

I'm really new into penguin ;)
Working with it for 2 weeks (every night 2 hours) now. I have got user accounts for all situations, 
meaning 1 admin + 3 users for each program (samba, ftp, mail and ampache for now) + 1 mysql-admin + 1 ubuntu admin, 
which leads to a total of 18 acounts, where all of them have a different and randomly generated password, 
with a length > 12, lower and upper case letters, numbers and special characters - guess they are safe and YES, 

I AM PARANOID :p

Oh, by the way I am working with "Ubuntu Server 12.10", so no GUI and that. Just terminal. 
Cause I like terminal.(Server got no screen, just SSH access)

Hope to read from you soon :)

---

### Post by QIII on 2013-02-23
*Moved to **Server Platforms***

Please refer to [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy), which contains the following:

> **Profanity:** We have users of all age groups and of all tolerance  levels where profanity is concerned. A language filter is in place to  catch most major forms of profanity that may accidentally be used. Do  not attempt to circumvent the language filter by using variations or  slight misspellings of profanities.I have edited your post.

Please refrain from further violations or an infraction may be issued.

Thank you.

---

