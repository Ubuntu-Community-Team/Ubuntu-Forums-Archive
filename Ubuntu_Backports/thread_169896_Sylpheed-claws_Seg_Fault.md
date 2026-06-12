---
title: "Sylpheed-claws Seg Fault"
date: 2006-05-03
forum: Ubuntu Backports
---

### Post by phenfen on 2006-05-03
Greetings all,

I'm not sure if this is the correct place to post, but I'll give it a whirl. I've been using Ubuntu for about a week now and I've identified a reproducable seg fault in Sylpheed-claws. I was hoping that someone could point me in a good direction on how to further analyze the problem and hopefully help the community to fix it (unless I'm the only one in this boat ;).

Here's how I can reproduce the problem:

1) Create new email, GPG sign it, and send.
2) Create another email and begin typing in body.
3) Alt-tab between other open applications
4) Hit "Get All" email in Sylpheed
5) Alt-tab to message being created in step 2
6) Position cursor to end of paragraph and hit enter
7) Segmentation Fault[1]

Here's a bit of information about my system (let me know if other info might come in handy):

Ubuntu 5.10  2.6.12-10-686

----- Sylpheed-claws -----
ii  sylpheed-claws 1.9.14-1       Extended GTK2 version of the Sylpheed mail c
ii  sylpheed-claws 1.9.14-1       Clam AntiVirus plugin for the Sylpheed Claws
ii  sylpheed-claws 1.9.14-1       HTML viewer plugin for Sylpheed Claws GTK2 u
ii  sylpheed-claws 1.9.14-1       PGP/inline plugin for Sylpheed Claws GTK2
ii  sylpheed-claws 1.9.14-1       PGP/MIME plugin for Sylpheed Claws GTK2
ii  sylpheed-claws 1.9.14-1       Installs plugins for the Sylpheed Claws GTK2
ii  sylpheed-claws 1.9.14-1       SpamAssassin plugin for Sylpheed Claws GTK2
ii  sylpheed-claws 1.9.14-1       Notification area plugin for Sylpheed Claws

----- Other/Possibly Relevant -----
ii  spamassassin   3.0.4-2        Perl-based spam filter using text analysis
ii  spamc               3.0.4-2        Client for SpamAssassin spam filtering daemon
ii  gnupg          1.4.1-1ubuntu1 GNU privacy guard - a free PGP replacement
ii  clamav               0.87-1         antivirus scanner for Unix
ii  clamav-base      0.87-1         base package for clamav, an anti-virus utili
ii  clamav-freshcl   0.87-1         downloads clamav virus databases from the In

[1] Seg Fault info: 
msgcache.c:117:Cache size: 10543 messages, 4353727 bytes
procmsg.c:1698:Changing flags for message 11168 in folder inbox
mh.c:198:MH scan not required: /home/phenfen/.sylpheed-claws/tempfolder/processing (1146678098 <= 1146678098)
msgcache.c:138:Cache size: 0 messages, 0 byte
folder.c:1013:Counting total number of messages...
session.c:213:session (0x9488378): destroyed
inc.c:1389:added timer = 874
Segmentation fault

If additional information would be helpful, please let me know and I'll do my best to post it. Also, if this is the incorrect forum to post in, please feel free to offer suggestions on where I should post.

Cheers!

-phenfen

---

