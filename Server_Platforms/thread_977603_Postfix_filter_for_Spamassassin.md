---
title: "Postfix filter for Spamassassin"
date: 2008-11-10
forum: Server Platforms
---

### Post by Mucker212 on 2008-11-10
Hi,

I currently have a Ubuntu 6.0.6 Dedicated server. I have managed to setup Spamassassin successfully so all spam with a rating over 5.0 is marked as spam in my email folder. Trouble is I now recive nearly 400 a day. Now this takes time and is really getting me down.

Does anyone know how I tell spamassassin or Postfix to delete the spam before I even download it?

I know some mails that are good will prob get treated as spam but iam willing to take this chance as it has now become an absolute chore downloading that many spam mails a day. Even though they go to my junk folder.

Say Could I delete all spam with a rating over 6.0 or something like that?

Thanks for anyones help

---

### Post by CrucifiedEgo on 2008-11-10
How is your postfix configured?  Do you have some kind of virtual setup, or are you just using your UNIX user accounts?  With the former it gets tricky, with the latter (just your user account) you can use procmail to filter mail into folders, or delete it outright.  Here's an example procmail recipe that can get you started: [http://spamassassin.apache.org/full/3.0.x/dist/procmailrc.example](http://spamassassin.apache.org/full/3.0.x/dist/procmailrc.example)

---

### Post by Mucker212 on 2008-11-10
> **CrucifiedEgo said:**
> How is your postfix configured?  Do you have some kind of virtual setup, or are you just using your UNIX user accounts?  With the former it gets tricky, with the latter (just your user account) you can use procmail to filter mail into folders, or delete it outright.  Here's an example procmail recipe that can get you started: [http://spamassassin.apache.org/full/3.0.x/dist/procmailrc.example](http://spamassassin.apache.org/full/3.0.x/dist/procmailrc.example)

So where is this file?

Or do I make it and put it somewhere.

I think I have an unmanaged server. I set it up myself. Its comes with ubuntu 6.0.6 installed with a few extras like mysql postfix etc? Not sure on all of them.

Thanks for the reply by the way

---

### Post by Mucker212 on 2008-11-11
Need more help with this. Anyone?

---

### Post by Mucker212 on 2008-11-11
Helllloooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo Any body herE?

---

### Post by Mucker212 on 2008-11-13
I take it no body knows anything to help me out here?

See im getting the spam delivered to my mail box with scores. Most of them are scored 15 and above. I just want the server to drop them or delete them before I have to download. Is there any easy way for my to do this using Spamassasin or Postfix?

PLEASE HELP!

---

### Post by Mucker212 on 2008-11-13
****!

---

### Post by CrucifiedEgo on 2008-11-13
I would suggest reading the documentation for procmail -- it explains more in depth how to use it.  Also, i still don't know how your users are setup on your mailserver to help you further -- are they UNIX accounts or do you have virtual domains and users?

---

### Post by Mucker212 on 2008-11-13
I have root access and virtual domain users, but I want to implement it for all users. Its a dedicated Server solely for me. But I have a few virtual domains on there

---

