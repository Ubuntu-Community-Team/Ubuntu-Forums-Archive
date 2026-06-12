---
title: "thunderbird and antivirus"
date: 2012-11-08
forum: Security
---

### Post by sigurnjak on 2012-11-08
I have been reading a lot about antiviruses and linux , but i still have one question.
Is there a way to set up clam av or any other AV  to scan my  email   so i do not pass some nasties to my contacts .
There used to be thunderbird extension that made it easy , but it is obsolete now.

---

### Post by 0011235813 on 2012-11-10
> **sigurnjak said:**
> I have been reading a lot about antiviruses and linux , but i still have one question.
Is there a way to set up clam av or any other AV  to scan my  email   so i do not pass some nasties to my contacts .
There used to be thunderbird extension that made it easy , but it is obsolete now.
If you're sending an attachment, I'm afraid the only way is to manually check that particular file with clam av (you use the GUI right?).

In any case, I don't think anyone sends enough attachments to actually need a lot of time to scan them. 

The only possible solution I can see, which is quite complicated, would be to set up a cron job that's set to automatically execute a bash script. That bash script would tell clamav to scan a particular directory (the one where Thunderbird stores your emails) and log the results somewhere. Either way, it's not simple and I don't know if it will work with attachments.

Post up if you have any trouble doing that. I can't give you any directions of the top of my head right now, but a quick Google search should reveal plenty of guides that tell you how to write cron jobs, scripts etc.

---

### Post by maglinu on 2012-11-10
I think you may be able to do some of this with Bitdefender scanner for unices and kmail combination - have a look at BD's help file. (I use BD, but have never tried to scan mail - gmail does that well enough for me)

I think the filter that comes pre-set up will just add a flag to the header to say the message was infected. You would have to invent another filter to read the flag and do something about it I think.

---

### Post by sigurnjak on 2012-11-12
Thank you both for  suggestions . For now i will trust google  , but i may try out BD and kmail as i am right now undecided which DE to stick with on a LS Ubuntu since Unity just does not  feel right .

---

