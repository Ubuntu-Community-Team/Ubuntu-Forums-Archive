---
title: "Totally un-ubuntu question, but help appreciated"
date: 2010-07-17
forum: The Cafe
---

### Post by lordhaworth on 2010-07-17
The actual relevant forums never seem to be as good. 

My grandparents computer suffered from some deep-level corrupted files and I had to do a full system restore for them (running xp). They use outlook express (which I never use) and I am trying to retrieve their old email/address book. Now, is it seriously possible... seriously... that these are lost forever? Surely there is some web access to the accounts or something? 
I had this down as one of the easiest jobs I had to do in getting them up and running again, if it were any other email service it would be!
DARGH!

Any help very welcome

Cheers

---

### Post by neoargon on 2010-07-17
Did you try booting a live cd? . There is a software named [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") that can help recover files as well as fixing filesystem issues . Describing  what exactly the problem is would bring more help

---

### Post by lordhaworth on 2010-07-17
The problem is simply that they want to look at old email and recover the old address book. I have done a fresh install from the live CD but to a new partition s oI guess there is a chance I could recover the old data.

---

### Post by koenn on 2010-07-17
look for .dbx and .wab files

and read this:

[http://www.insideoe.com/files/wab.htm](http://www.insideoe.com/files/wab.htm)
[http://www.insideoe.com/files/store.htm](http://www.insideoe.com/files/store.htm)

---

### Post by Swagman on 2010-07-17
**IF**, when you re-installed you kept the current file system then there is a (good) chance those files are still there.

[Edit]
Wait.. you said you used a restore disk....

That'll overwrite whatever's on the drive and restore it to the way it left the shop. I'd scratch that down to all own data being lost.

Unless.... Personal data has been saved onto a different partition

I always tell people (not that they bother) to **NOT** save stuff into "My Docs". But people are lazy.

---

### Post by neoargon on 2010-07-17
> **lordhaworth said:**
> The problem is simply that they want to look at old email and recover the old address book. I have done a fresh install from the live CD but to a new partition s oI guess there is a chance I could recover the old data.

Try the testdisk I posted in my earlier post . With it, try to recover as much as possibly to another partition . Then with the same software, you can unformat (revert back to an earlier condition) and might be able to find the older e.mails   . But you MUST first try to recover e.mails before unformating, otherwise you may not of able to recover later .

Check for the files Koenn mentioned . Those files contains the e.mail

---

### Post by Excedio on 2010-07-17
Well if they are using Outlook Express, they are also likely to be using a web-based email service that is connected to it. Are you not able to log in to the web-based version of the email and see the emails?

---

### Post by koenn on 2010-07-17
> **Excedio said:**
> Well if they are using Outlook Express, they are also likely to be using a web-based email service that is connected to it. Are you not able to log in to the web-based version of the email and see the emails?
Isn't Outlook Express a POP3 client - meaning that all the mail would be downloaded to the local system ?

---

### Post by Excedio on 2010-07-17
> **koenn said:**
> Isn't Outlook Express a POP3 client - meaning that all the mail would be downloaded to the local system ?
 
My Yahoo! Mail is setup as POP3 and Thunderbird receives them as POP3. I also have all the emails still on mail.yahoo.com

---

### Post by jrothwell97 on 2010-07-17
> **koenn said:**
> Isn't Outlook Express a POP3 client - meaning that all the mail would be downloaded to the local system ?

It also supported IMAP. However, in my experience, if they were using their ISP's e-mail address, they were probably using POP.

In this case, if it's not backed up *locally*, then it's almost definitely gone. Forever. Sorry. :(

Moral of the story for you and your grandparents: for god's sake, [SIZE="7"]back it up[/SIZE]. There is no excuse - storage is cheap, reliable and dead simple to set up. I also suggest nudging your grandparents into upgrading to Windows 7, since that includes an automatic backup utility as standard (at last.)

---

### Post by koenn on 2010-07-17
> **Excedio said:**
> My Yahoo! Mail is setup as POP3 and Thunderbird receives them as POP3. I also have all the emails still on mail.yahoo.com
hm, yes, but i think leaving a copy on the server is _optional_

---

### Post by Excedio on 2010-07-17
Your absolutely right. I guess we wont know until the OP reports back to us. :-)

---

### Post by Malac on 2010-07-17
> **koenn said:**
> Isn't Outlook Express a POP3 client - meaning that all the mail would be downloaded to the local system ?
koenn(et al) is correct unless they specifically ticked the "Leave a copy of messages on Server" option under Server settings in Accounts then their e-mails have been downloaded to the computer and deleted from the server.
This does depend on the e-mail server provider but they may have backups for their own use but I wouldn't count on it. You may try contacting them to see though. Doing this may have some privacy issues so even if they do they may not admit it.

Outlook Express stores e-mails in a very strange place on your hard drive in Windows, usually under /Documents and Settings/{USER_NAME}/Local Settings/Application Data/Identities/{SOME-SORT-OF-LONG-NUMBER-WITH-DASHES}/Microsoft/Outlook Express
This can be changed in Outlook Express but no-one ever does.

Address Book is usually under /Documents and Settings/{USER_NAME}/Application Data/Microsoft/Address Book

If you still have the original partition intact then I would search these directories from a live CD and if you can copy any and all files in these directories to a USB stick, CD-R or web backup service. Then boot into new system and find the same directories for the new version of {USER_NAME} and overwrite the files with the ones from original user directories.

Once up and running again you can write a small batch file that would copy the files from the weird Windows storage location to somewhere else outside the Windows file structure preferably a CD-R or different partition. Then run it, say, once a week or every couple of days depending on how many e-mails you are prepared to lose if this happens again.

Good Luck.
Hope this helps.

---

### Post by clanky on 2010-07-17
> **koenn said:**
> hm, yes, but i think leaving a copy on the server is _optional_

Normally it is, but it is usually not enabled by default.

---

### Post by lordhaworth on 2010-07-17
Cheers all,

Yeah, many lessons to be learnt (I back up). I have a few bits and pieces that I can still try, thanks for the ideas. I'll ge tback to you as to what comes out of it.

Thanks again

---

