---
title: "Clam TK Mystery"
date: 2009-04-05
forum: Security
---

### Post by atravnic on 2009-04-05
Ran a virus check and found 2 viruses, had them quaranteened, but when I checked the quaranteen file it showed no viruses. I did it three times and I'm certain I didn't miss any steps. Could this be a bug in Clam TK? Help/suggestions appreciated! Thanks!  ...Fred

---

### Post by cariboo on 2009-04-06
What files are supposed to be quarantined? Unless they are Windows viruses, they are more than likely false positives.

Jim

---

### Post by atravnic on 2009-04-06
> **cariboo907 said:**
> What files are supposed to be quarantined? Unless they are Windows viruses, they are more than likely false positives.

Jim
Hi Jim -- No idea what files Clam TK is trying to quarantine, it only tells you you've got n viruses and gives you the quarantine option. When I installed Ubuntu 2 1/2 years ago I trashed Windows (no regrets), expecting never to have to deal with Windows viruses again. So is it possible to still get a Windows virus? 

Finally, Clam TK is the installed anivirus in 8.04. Are there other, better antivirus programs I might try, because at this point I still don't know if I have a virus and if the quarantine process really works. Thanks again.     ...Fred

---

### Post by cariboo on 2009-04-07
I haven't used clamav much, but if I remember correctly there is a log file in /var/log. This may give you a clue to what files were flagged as viruses. I've been using Linux since 1998, the only viruses I've ever seen were windows viruses attached to email. The last time I ran clamav it flagged a couple of emails in my email archive as being infected.

Jim

---

### Post by atravnic on 2009-04-07
> **cariboo907 said:**
> I haven't used clamav much, but if I remember correctly there is a log file in /var/log. This may give you a clue to what files were flagged as viruses. I've been using Linux since 1998, the only viruses I've ever seen were windows viruses attached to email. The last time I ran clamav it flagged a couple of emails in my email archive as being infected.

Jim
Jim -- time to confess, I'm not a techie, so I don't know how to find /var/log and the log file within. Can you give me step by step instructions, please. But it still leaves unresolved the question why does Clam TK apparently not quarantine the infected files it finds when asked to? Maybe I should post this as new thread? ...Fred

---

### Post by cariboo on 2009-04-08
No need to start a new thread. Open Nautilus (Places-->Home Folder) the double-click Filesystem in the left pane. In the right pane all the folders will be in alphabetical order down near the bottom you should see var, just double-click the folder, then double-click the log folder. Check there to see if there is a file called clam.log or something.

Checkout the screenshot.

Jim

---

