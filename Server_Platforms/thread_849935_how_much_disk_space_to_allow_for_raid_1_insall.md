---
title: "how much disk space to allow for raid 1 insall"
date: 2008-07-05
forum: Server Platforms
---

### Post by mspIggy on 2008-07-05
i am setting up a 2 disk *80gb sata* server hp dl360

how much disk space should i be allocating for the primary partiation that will hold these system files?

this is all a bit confusing to me - as i have never attmpted anything like this before

using raid 1 8.04 server amd64

thank you

---

### Post by windependence on 2008-07-05
Do you really NEED RAID? Probably not. Remember, RAID is NO substitute for good backups. You will also have half the space with RAID 1. Just because this is a server doesn't automatically mean you need RAID, and if you do, it probably should not be software RAID.

-Tim

---

### Post by mspIggy on 2008-07-05
there is no raid controller

sata drives it is an hp dl360g4 i found on craigs list and a good raid card is quite expensive --

no real solution for backups for a while so the 2nd drive is the only option...

why do you say 'half the space'?

many thanks

---

### Post by windependence on 2008-07-05
RAID 1 is mirrored so you will have one drive full of space, that's it. Why not back up to the second drive instead? You could rsync one drive every so often to the second drive. Remember, with RAID 1, if you get one drive corrupted, the other one will be immediately that way also. Same if you get a virus, the second drive is immediately infected.

Things to think about.

-Tim

---

### Post by mspIggy on 2008-07-05
i know i have been thinking about this...

this is a server we will run a small web hosting business on -- so it is important we make sure things stay going...

the thought never occured to me to backup to the 2nd drive --

how would i do this?

many thanks

---

### Post by windependence on 2008-07-05
I host sites for my consulting business and I would not THINK about doing it without good backups OR decent server class hardware.

As a customer, I would sue you if my site was down for an extended period of time or you lost my site files. You may want to rethink what you are spending in infrastructure. I already have almost $4,000 invested and I am not done, and I have been lucky to be able to get some fantacstic deals on hardware. 

Hosting is no small thing to get involved with especially if you have no experience.

-Tim

---

### Post by mspIggy on 2008-07-05
hi tim - many thanks 

to expand on what i do...

i will be serving applicaitons -- 

no client has ftp access -or any 'files' of their own

only data in databases we backup with webmin and ftp to local pc for now...

so i guess i have to start over....

how much partition room should i allow fro raid 1 insatll of hardy when cosdidering it will be used for an isp business

also - while we are at it...

thoughts on how this sort of backing up tim mentioned is actually done

many thanks

iggy

---

