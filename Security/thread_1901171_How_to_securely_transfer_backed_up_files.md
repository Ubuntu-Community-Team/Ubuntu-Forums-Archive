---
title: "How to securely transfer backed up files?"
date: 2011-12-28
forum: Security
---

### Post by garfonzo on 2011-12-28
Hi Folks:

I have a two servers running in two different geographical locations. The main server is running a database for a business and holding all the business' files while the other is simply a backup machine. 

I am currently backing up the main server with a very small script I wrote in Python, which is triggered by the crontab to run nightly. The script (which runs from the backup machine) connects to the main server via SSH (logging in as root, using keys) and with the "rsync" commands, copies over all the files that have changed or are new since the last backup. 

Something is telling me this is not a secure way of transferring the business-critical backups over the internet. Do any of you have any suggestions regarding this or is what I am doing OK?

Thanks

---

### Post by papibe on 2011-12-28
If you use rsync over ssh, the transfer will be encrypted, and that pretty much take care of concerns about "eavesdropping".

Now, another different concern would be if it is safe to keep unencrypted backup of important data outside your secure network. In that case, I would consider encrypting the backup itself. Take a look at [duplicity]("http://duplicity.nongnu.org/") for a solution in that direction.

Hope it helps.
Happy Holidays.

---

### Post by garfonzo on 2011-12-28
> **papibe said:**
> If you use rsync over ssh, the transfer will be encrypted, and that pretty much take care of concerns about "eavesdropping".

Now, another different concern would be if it is safe to keep unencrypted backup of important data outside your secure network. In that case, I would consider encrypting the backup itself. Take a look at [duplicity]("http://duplicity.nongnu.org/") for a solution in that direction.

Hope it helps.
Happy Holidays.

That's great! Thanks for the reply. 

The backup server actually resides at my home, locked in my garage. I have no concerns about security with this machine.

---

### Post by a2j on 2011-12-28
rsync over ssh should do it

---

### Post by CharlesA on 2011-12-28
> **garfonzo said:**
> That's great! Thanks for the reply. 

The backup server actually resides at my home, locked in my garage. I have no concerns about security with this machine.

Just keep in mind that a garage can be broken into and stuff stolen. If you have really important data, make a couple backup copies of it and store it in separate places.

> **a2j said:**
> rsync over ssh should do it

+1.

---

### Post by garfonzo on 2011-12-28
> **CharlesA said:**
> Just keep in mind that a garage can be broken into and stuff stolen. If you have really important data, make a couple backup copies of it and store it in separate places.


Thanks for the tip re the garage. I make a hard copy of all the data every quarter and send them to the CEO -- he locks them up in a safety deposit box. In total there are four copies of all the data spread across three distinct geographical locations. 

Thanks the help.

---

