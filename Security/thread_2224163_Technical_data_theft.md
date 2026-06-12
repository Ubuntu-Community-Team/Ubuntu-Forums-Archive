---
title: "Technical data theft"
date: 2014-05-14
forum: Security
---

### Post by brady4 on 2014-05-14
Here is my current system: System: Windows XP home edition 2002, service pack 3 AMD Athlon(tm) 64x2 dual core processor 4000+ 2.10 GHz, 2.93 GB RAM

Two years ago the day before a high tech project submission my computer went black for a minute or so, when it came back on all the files relating to the project from multiple unrelated locations on the computer were suddenly gone. I was in the finals with a 1 in 4 chance of getting the project funded, losing the files caused me to forfeit the proposal.
I gathered my resources again over time, and after very little networking on the subject for a year or more last month started forging ahead again, this time networking on linkedin and to a small extent wordpress, Google+, facebook, and twitter.

On May 11, 2014, at around noon, I noticed that my 7 numbered desktop topic files were suddenly only 1 (Farm),2 (Accounting), 6 (Skills), and 7 (Legal). The three files in between related to the project were gone, but nothing else was touched. I did not have them backed up. I had set system restore points daily, so I did a system restore which brought back the files, however, they were all empty (no content in the files).

I am now hoping to do away with XP and maybe windows as well and am intrigued with the linex possibilities. I never liked dealing with MS anyway. I'd like to step up my level of security and wouldn't mind finding a way to investigate in what direction at least the files were hi-sted.
What do you suggest?

---

### Post by cariboo on 2014-05-15
Not to be facetious, but a good backup policy would go a long ways towards alleviating the data loss problem.

---

### Post by papibe on 2014-05-15
Hi brady4. Welcome to the forum ):P

I beleive it is possible that your hard drive is failing.

If I were you, I'd stop using the computer immidiately, and backup the current data to another computer or an external USB (or both).

Then I'd would review the HD's [S.M.A.R.T.]("http://en.wikipedia.org/wiki/S.M.A.R.T.") data to confirm or discard that situation (you may need to get some help from IT support or a friend to do this).

Let us know how it goes.

Come here often and have fun.
Regards.

---

### Post by The Cog on 2014-05-15
Please go out and buy yourself a USB memory stick (or two) and take backups. Today if possible.

Linux is quite different to windows and would take some getting used to. But then again, so would windows 8.
I would suggest that you try a few different live DVDs of Ubuntu, Xubuntu, Kubuntu, Lubuntu to see which (if any) feels most to your liking, and find out which works well on your PC.
The disk utility on an Ubuntu live disc will show you the SMART data - I'm not sure if XP can do that.

---

### Post by JKyleOKC on 2014-05-16
> **brady4 said:**
> Two years ago the day before a high tech project submission my computer went black for a minute or so, when it came back on all the files relating to the project from multiple unrelated locations on the computer were suddenly gone. I was in the finals with a 1 in 4 chance of getting the project funded, losing the files caused me to forfeit the proposal.
I gathered my resources again over time, and after very little networking on the subject for a year or more last month started forging ahead again, **this time networking on linkedin and to a small extent wordpress, Google+, facebook, and twitter.**

On May 11, 2014, at around noon, I noticed that my 7 numbered desktop topic files were suddenly only 1 (Farm),2 (Accounting), 6 (Skills), and 7 (Legal). The three files in between related to the project were gone, but nothing else was touched. I did not have them backed up. I had set system restore points daily, so I did a system restore which brought back the files, however, they were all empty (no content in the files).
I can't provide any specific suggestions for you, but I disagree that this sounds like a hard disk failure or even any sort of hardware problem. I think that you are probably correct in suspecting deliberate human sabotage of your projects.

Specifically, the services I've emphasized in the above excerpt of your post are notorious for harboring "zero-day" exploits of one form or another that permit a remote intruder to access your system without your knowledge. Using them at all, despite their popularity, is a significant security risk. I operate a specialized database recovery service and deal with medical information and sensitive financial data for customers all over the world, and consequently keep a very close watch on the security situation -- and avoid all of the services that you mentioned because of the risk of using any of them.

Also, hardware failures are almost never limited to such specific areas of any storage media. If a disk fails, usually ALL of the data on it vanishes, not just the content of certain files. The limited area that you report simply screams that malicious human intelligence has been directing the damage.

And in such a case, switching from Windows to Linux or a Mac probably will not solve your problem. It might make your foe's task a bit more difficult, but no computer ever connected to the outside world can be made totally secure. For that matter, the only totally secure computer is one that has no connections whatsoever, including to a keyboard, monitor, or power source -- and of course, it would be totally useless also.

Other posters have suggested paranoia, and they might be correct -- but assuming that your report is correct and someone actually **is** out to prevent you from achieving your goal, you need to be trying to identify the person or entity involved, and taking appropriate action to protect yourself from them. No technical solution will suffice; as in all other computer-related difficulties, it's always a people problem at the root.

---

### Post by jon43 on 2014-05-19
> **JKyleOKC said:**
> 

And in such a case, switching from Windows to Linux or a Mac probably will not solve your problem. It might make your foe's task a bit more difficult, but no computer ever connected to the outside world can be made totally secure. For that matter, the only totally secure computer is one that has no connections whatsoever, including to a keyboard, monitor, or power source -- and of course, it would be totally useless also. 

I sort of disagree with this. Assuming that she is right and this IS someone stealing/deleting the data from her computer as a means of sabotage, switching to Mac or Linux might very well solve the issue. It all depends on what sort of person is interested enough to be doing this.

If it's someone with average to slightly above average knowledge, they probably did something no more clever than deploying a remote access tool. There are far more of these available for Windows than the other OS platforms, and if you make the one they are familiar with deploying and using useless by leaving Windows, you may be fine. On the other hand, if it's a skilled hacker who has taken an interest in you, then yes, switching platforms may just slow them down.

---

### Post by Chayak on 2014-05-19
I've done my share of penetration testing in the past.  I know the realities of hacking computers and networks.

With the information provided I can not envision a scenario where someone would only delete a few files.  If I was after you I'd overwrite all the files with random data and then have the machine start writing random data to random hard drive sectors until the machine crashed.  It would take a forensic examination to ferret out the real cause.  It doesn't make sense to me that they'd just delete a few files rather than all of them.  It's more likely the hard drive going bad as others have said.

There are some good security stickies that goes over how to secure a system so I won't repeat it.  In all honesty the vast majority users will be fine with just the firewall turned on.  Intrusion detection and the like are more for servers with public access.

As others have already mentioned if files are important to you they need to be backed up.  Crashplan is cheap, and it works.  System restore is not a backup.

If it really is that sensitive then keep stuff on an airgapped encrypted system and only transfer files from it to other systems using a USB drive and a forensic certified read only USB adapter.  Then also keep backups.

Did I forget to mention backups?

---

### Post by ant2ne on 2014-05-20
> **JKyleOKC said:**
> Also, hardware failures are almost never limited to such specific areas of any storage media. If a disk fails, usually ALL of the data on it vanishes, not just the content of certain files. The limited area that you report simply screams that malicious human intelligence has been directing the damage.I agree with most of your post but I've seen hard drives do something similar. Not delete the data but corrupt just a few files as to make them unreadable. It is a sign the thing is about to go south real fast but it can happen.

Reading this thread and the symptoms I'm left with 2 most likely causes. 1. User error. Accidental deletion. 2. Someone else is using this system, probably just sitting down at the keyboard and using the current unlocked session, or this person knows the password. And that someone did something to the files. Of course, option 2 is still user error.

If the user has sensitive data they should contact their IT support to assist them in locking down the system and arranging for backups and instruct the user on how to check and verify backups. If you don't have an IT support person, hire one. There are many freelance IT contractors/consultants in the phone book. It will be worth the investment to have reliable secure data.

---

### Post by jon43 on 2014-05-20
> **Chayak said:**
> 

If it really is that sensitive then keep stuff on an airgapped encrypted system and only transfer files from it to other systems using a USB drive and a forensic certified read only USB adapter.  Then also keep backups.

Did I forget to mention backups?

Where can I buy a read-only USB adapter as mentioned? Would interest me.

---

### Post by Chayak on 2014-05-20
> **jon43 said:**
> Where can I buy a read-only USB adapter as mentioned? Would interest me.

[http://www.digitalintelligence.com/products/usb_write_blocker/](http://www.digitalintelligence.com/products/usb_write_blocker/)
[http://www.cru-inc.com/products/wiebetech/usb_writeblocker/](http://www.cru-inc.com/products/wiebetech/usb_writeblocker/)

The first is the better choice.  It does some clever tricks to make the PC think the USB drive is writable and make it look like data has been written to the drive when nothing is actually written.  They're not cheap but they're proven secure.  It's what the professionals use.

---

### Post by ant2ne on 2014-05-20
I'd avoid using the phrase 'air gapped' in the wireless age.

---

### Post by ant2ne on 2014-05-20
[http://www.piriform.com/recuva]("http://www.piriform.com/recuva")

---

### Post by Chayak on 2014-05-20
> **ant2ne said:**
> I'd avoid using the phrase 'air gapped' in the wireless age.

It's a commonly accepted security term and refers more to network isolation than the literal meaning.
[http://en.wikipedia.org/wiki/Air_gap_(networking)](http://en.wikipedia.org/wiki/Air_gap_(networking))

---

### Post by ant2ne on 2014-05-20
I know what it means. But the average user doesn't. Why so eager to confuse them?

---

