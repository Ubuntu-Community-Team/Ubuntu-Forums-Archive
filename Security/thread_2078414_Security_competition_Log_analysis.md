---
title: "Security competition Log analysis"
date: 2012-10-30
forum: Security
---

### Post by duke.tim on 2012-10-30
The event is for college students, the competition is being developed and this is a sort of test run for it. If you are interested there will be a spring competition starting April 30th. It seems like the focus is for US universities and colleges.
[http://www.nationalcyberleague.org/2012/Spring/spring.shtml](http://www.nationalcyberleague.org/2012/Spring/spring.shtml)


I'm taking part in a security competition as part of a class and Nov 3 we will be doing log analysis. What the teacher is teaching seems woefully inadequate so i'm wondering if all youall have any tips.


[SIZE="2"][FONT="Verdana"]Here is what we will be covering:

Windows Security Log  (10 flags, totaling 2,800 points)
Corrupt Windows Security Log  (10 flags, totaling 7,600 points)
Linux Authentication Log  (10 flags totaling 2,800 points)
Corrupt Linux Authentication Log  (10 flags, totaling 7,600 points)
Apache Logs (5 flags, totaling 1,200 points)
Network Data Capture  (5 flags, totaling 8,000)[/FONT][/SIZE]


What events in Linux logs would signify a potential intrusion attempt, or intrusion. What are some events to look for that are common in intrusion attempts (for example adding a user account). How do I know what a particular line in the logs mean.

The part that I have no clue on is **Corrupt Logs**, any ideas on what or how to restore/retrieve information from corrupt logs. Even links pointing else where to learn will be helpful. It might be on inconsistency within the log (such as two logins without logging out [assuming both logins and logouts are recorded]), what might signal that?

---

### Post by Kinstonian on 2012-10-31
[http://docstore.mik.ua/orelly/perl/sysadmin/ch09_02.htm](http://docstore.mik.ua/orelly/perl/sysadmin/ch09_02.htm)

---

### Post by duke.tim on 2012-10-31
Thanks Kinstonian, I was getting worried that no one would reply!

---

### Post by Kinstonian on 2012-10-31
No problem... Harlan's evtparse.pl would likely be useful for the corrupted Windows .EVT logs.

[http://windowsir.blogspot.com/2010/07/more-timeline-stuff.html](http://windowsir.blogspot.com/2010/07/more-timeline-stuff.html)

---

### Post by Ms. Daisy on 2012-11-02
> **duke.tim said:**
> The part that I have no clue on is **Corrupt Logs**, any ideas on what or how to restore/retrieve information from corrupt logs. Even links pointing else where to learn will be helpful. It might be on inconsistency within the log (such as two logins without logging out [assuming both logins and logouts are recorded]), what might signal that? I don't know that you can. A log has become "corrupt" by an attacker I assume? This could help you in that regards: [https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

If they mean that the log was just somehow corrupt because of hardware or software failure, then personally I wouldn't trust them to be accurate. I can only talk about how to prevent that (use splunk, aggregate logs off-box). I have no idea how to repair logs without losing their integrity.

edit: I read Kinstonian's last link. That would help for windows logs with an event viewer problem. It won't help for linux auth logs.

---

### Post by Kinstonian on 2012-11-04
> **Ms. Daisy said:**
> I don't know that you can. A log has become "corrupt" by an attacker I assume? This could help you in that regards: [https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

If they mean that the log was just somehow corrupt because of hardware or software failure, then personally I wouldn't trust them to be accurate. I can only talk about how to prevent that (use splunk, aggregate logs off-box). I have no idea how to repair logs without losing their integrity.

edit: I read Kinstonian's last link. That would help for windows logs with an event viewer problem. It won't help for linux auth logs.

You're right about problems with integrity.  However, whether it's because of hardware or an attacker, that issue is there.  That's why digital investigators rely on corroborating evidence from different sources.  Something like wtmp may be modified by an attacker, but if an analyst looks at wtmp combined with netflow, and other host/network evidence, he can have more trust in wtmp if those other sources says the same thing.

---

### Post by duke.tim on 2012-11-04
Ms. Daisy that is a useful link thanks for the reply :)

Windows logs are a mess, or maybe I need to get better at awk. The questions asked were very similar to the ones asked at the honeypot project (which were Linux logs)
[http://www.honeynet.org/challenges/2010_5_log_mysteries](http://www.honeynet.org/challenges/2010_5_log_mysteries)

The log competition is now over, The linux log files were corrupted within an (unnamed) gz archive with the last few bits removed. Luckily Linux isn't tricked by such things and the logs were retrievable.

The same trick was used on the windows logs except it was the first four bits....windows refused to cooperate unless you manually added the first four bits or used another method to extract the data.

Thanks for the help!

---

### Post by Ms. Daisy on 2012-11-04
> **duke.tim said:**
> ... The linux log files were corrupted within an (unnamed) gz archive with the last few bits removed. Luckily Linux isn't tricked by such things and the logs were retrievable.

The same trick was used on the windows logs except it was the first four bits....windows refused to cooperate unless you manually added the first four bits or used another method to extract the data... Huh.  I'm curious, did the administrators give any examples of when this would happen in reality? Is it something attackers do to logs on boxes they crack?  Or was this something that someone would do on their own computer to try and obfuscate their own activities?

---

### Post by Kinstonian on 2012-11-04
> **Ms. Daisy said:**
> Huh.  I'm curious, did the administrators give any examples of when this would happen in reality? Is it something attackers do to logs on boxes they crack?  Or was this something that someone would do on their own computer to try and obfuscate their own activities?

It's not uncommon to encounter corrupted files, say from unallocated space that need to be repaired.  Also, attackers sometimes create corrupted malware that will run by Windows, but some kind of security software has problems interpreting it.  For example, a Windows executable can be corrupted so some software has trouble dumping it from memory. I've seen ransomware that said it encrypted the user's files, but it really just modified the file signature of certain files.  So this exercise would also help there as well.  But as far as attackers intentionally corrupting zip files to hide, I don't think that happens much in the real world.  Although, I guess it's possible...

---

### Post by duke.tim on 2012-11-05
They didn't say when it would happen in the real world, I think they did it as a way of making some of the challenges more difficult.

Possibly could happen because of hardware failure, or from recovering deleted logs similar to what Kinstonian said.

---

