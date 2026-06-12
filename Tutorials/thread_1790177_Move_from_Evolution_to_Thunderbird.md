---
title: "Move from Evolution to Thunderbird"
date: 2011-06-24
forum: Tutorials
---

### Post by Dutchbeer on 2011-06-24
Just changed from Evolution to Thunderbird 3.1.10. and wanted to share the steps taken.
My platform: ubuntu 11.04 64-bit, desktop.

Step 1.
[LIST]
[*]Backup Evolution: Alt-f, Backup evolution settings...
[*]Install Thunderbird from Ubuntu Sotware Center and setup Thunderbird with your mail account information. Close Thunderbird, after checking whether sending and receiving works.
[/LIST]

Step 2.
Open evolution and move all sub-folders (dragging them) to the highest level. Before going to the next step make sure no sub-folders exist any more. Then close evolution.

Step 3.
[LIST]
[*]Open Nautilus.
[*]Assure you are in your /home/yourname folder.
[*]Press Control-h, now you see all hidden folders and files below your own folders, by example: .aptitude
[*]Move to /home/yourname/.local/share/evolution/mail/local/Inbox.sbd
[*]Press F3. This opens another panel in Nautilus.
[*]In this panel goto /home/yourname/thunderbird/xxxxxxx.default/Mail/ServerName
[/LIST]
This servername you can find in Thunderbird account settings (Alt-e, a), go to Server Settings. Here you see the ServerName.

Step 4.
Copy only the "mailbox file" files from your Evolution "Inbox.sbd" folder to the Thunderbird "ServerName" folder. **Do not copy** the other files like xxx.cmeta, xxx.ibec.index, xxx.ibex.index.data etc.

That's all.

Open Thunderbird and you should find all your evolution mail in your folders. By dragging the folders you can recreate your evolution subfolder structure.

Hope you like it :D

---

### Post by _stella_ on 2011-06-30
Thanks for providing this useful info , it helped me to move over to thunderbird

---

### Post by geazzy on 2011-06-30
nice tutorial :D

---

### Post by Buster95 on 2011-10-20
Thanks for the guide.

I navigated to ../.local/share/evolution/mail/local but could not see the Inbox.sbd file, even after unhiding the files.

For me, that folder contains: Cur, New, Temp, .Drafts, .Outbox, .Sent, .Templates, plus a number of .data, .cmeta and .index files. I can't see a corresponding .Inbox or any .sbd files.

Where have I gone astray?

---

### Post by SparTacux on 2011-10-22
It looks good - I shall try that. Well done Parker !

---

### Post by crossedout on 2011-10-26
Mega time saver. Thanks so much for sharing! I'd been dreading the upgrade b/c even though I wanted Thunderbird my accounts were deep in Evolution.

---

### Post by deadlytackler on 2011-10-27
Thanks buddy, enjoying thunderbird..

---

### Post by abdulmajid on 2011-10-28
I am using Ubuntu 10.10 which ships with Evolution and is default mail client. I tried to remove Evolution and install Thunderbird, Thunderbird worked just fine, i enjoyed it. But without Evolution About Me wont work.:( Please advise.

---

### Post by skumara on 2011-11-01
after moving to thunderbird, now how to uninstall evolution completely?
Im using ubuntu 10.04 LTS

---

### Post by gspidey on 2013-01-16
> **Buster95 said:**
> Thanks for the guide.

I navigated to ../.local/share/evolution/mail/local but could not see the Inbox.sbd file, even after unhiding the files.

For me, that folder contains: Cur, New, Temp, .Drafts, .Outbox, .Sent, .Templates, plus a number of .data, .cmeta and .index files. I can't see a corresponding .Inbox or any .sbd files.

Where have I gone astray?

Same problem here. Using Mint 14.

---

