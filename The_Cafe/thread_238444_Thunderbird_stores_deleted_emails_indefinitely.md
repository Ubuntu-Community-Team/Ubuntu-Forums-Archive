---
title: "Thunderbird stores deleted emails indefinitely"
date: 2006-08-17
forum: The Cafe
---

### Post by Onyros on 2006-08-17
Were you guys aware that Thunderbird stores deleted emails in its mbox, indefinitely, unless you use the "Compact Folders" function?

I was moving my mbox from Tbird to Evolution last night, and was utterly surprised when I saw around one thousand emails in Evolution's Trash after importing the mbox... some emails dating to a couple of months back.

By the way, it's obviously not a bug, rather a feature. Even so, I believe most people, just like me, aren't aware of it. As for myself, when I delete something, I mean I want it... deleted? (as opposed to archived) ;)

---

### Post by Stolie on 2006-08-17
Wouldn't you just want to "empty Trash" every now and again? I believe there's also a setting in the options somewhere to make it delete the trash after so many days...

---

### Post by Onyros on 2006-08-17
That's the catch, mate ;)

It stores emails you emptied from the trash! Yup, those you think that by emptying the trash were GONE ;)

Come on... I'm not THAT kind of noob :P

---

### Post by WorkingOnGoingLinux on 2006-10-24
Did you ever get an answer to this  ?
It's really an interesting question and
a bothersome one.

I use a usb stick with a thunderbird portable app on it 
for email when I travel. I've watched that thunderbird
file go from 40 meg at the original install date to over 300 meg
today. So something screwy is happening it's saving something.
If it's doing it on a usb stick it's probably doing it on  hard drive too.

---

### Post by ember on 2006-10-24
Well - that "problem" persists with nearly all mail clients. It is, as far as I know, for performance reason (read: deleting the mail physically each time you hit the del-key would be rather slow).

I noticed the issue when my mailfolder once rose above 500MB some years ago - compacting made it comparably small ;)

You can enable an option in Thunderbird that auto-activates compacting when it saves more than 100 KB. You will find it under Extras->Settings->Advanced->Offline&Disk space (please note, this is only a guess, I use the German version and have translated it roughly).

---

### Post by fuscia on 2006-10-24
i think it's the same as outlook express.

---

### Post by .t. on 2006-10-24
Urgh! What an ugly piece of work...

---

### Post by bionnaki on 2006-10-24
where does thunderbird store these deleted emails? cant we just empty that directory itself until they fix this problem?

---

### Post by Martian on 2006-10-24
Here's some information regarding Thunderbird and compacting folders:

[http://kb.mozillazine.org/Compacting_folders]("http://kb.mozillazine.org/Compacting_folders")

> You can enable an option in Thunderbird that auto-activates compacting when it saves more than 100 KB. You will find it under Extras->Settings->Advanced->Offline&Disk space (please note, this is only a guess, I use the German version and have translated it roughly).

In the English-language version I use, this setting can be found under Edit -> Preferences -> Advanced -> Offline & Disk Space 8)

---

### Post by bionnaki on 2006-10-25
what exactly does compacting folders do?

---

### Post by Jussi Kukkonen on 2006-10-25
Compacting folders goes through the actual mail files and removes "deleted" mails. After compacting the mails are really gone.

Personally I consider the need for "compacting" a bug. I understand the technical problems involved, but the current work-around is clearly not working -- as this thread shows...

---

### Post by Bezmotivnik on 2006-10-25
> **Jussi Kukkonen said:**
> Compacting folders goes through the actual mail files and removes "deleted" mails. After compacting the mails are really gone.

Personally I consider the need for "compacting" a bug. I understand the technical problems involved, but the current work-around is clearly not working -- as this thread shows...
Agreed on all points.  Compacting is not difficult, however, and you are frequently prompted for it.

I compact the trash folder every day or two, when I think of it.

---

### Post by bionnaki on 2006-10-25
so, just right-clicking on "trash" and selecting compact will erase the supposedly-deleted emails? ok. cool.

---

### Post by syxbit on 2006-12-08
MAN!
i'm glad i finally found this thread.
i popped my entire gmail (600mb) and then moved it to different folders.
my inbox still showed 600mb.
i was about to give up on thunderbird (and probably just use gmail) when i found this
thanks a bunch guys!

---

### Post by yabbadabbadont on 2006-12-08
One of the first things I do after I install thunderbird is to change the setting down to 10k.  I also set it to empty the trash on exit.

---

### Post by Onyros on 2006-12-08
The problem with this is that most people don't really know about this "feature".

I've tried warning a few people about it, to no avail. I've been dismissed as a loonie in other forums, with my T-Bird conspiracy theories...

That bug (I deem it so), was the last drop in my usage of Mozilla's software. I had used Opera primarily as a browser, and from then on started using both Evolution and Sylpheed-Claws.

It shouldn't be enabled by default, it just shouldn't. I don't care about performance when it comes to deleted emails: I want them gone.

---

### Post by vayu on 2006-12-08
> **Onyros said:**
> 
That bug (I deem it so)

I think it's fair to describe it as a feature you don't want, but not as a bug.  It's not right to call it a bug because it is intentional, because it is a practice found in other email clients and there are other people who have differing desires.  For instance, I want the performance and don't think it's inconvenient to compact folders manually once in a while.

That you wish it was set up to meet your desires is all well and good, but it's not a bug because it doesn't.

---

### Post by yabbadabbadont on 2006-12-08
I really think that it is a hold over of treating the stored mail as a database.  I'm not sure if that behavior is still used in DB's, but it used to be common practice that you had to purge the database to remove the deleted records.

---

