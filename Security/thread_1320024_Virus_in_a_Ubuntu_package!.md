---
title: "Virus in a Ubuntu package!"
date: 2009-11-08
forum: Security
---

### Post by mongsauer on 2009-11-08
I was completely freaked out today when I clamscanned my entire hard drive and found out that I have a virus!  I figured out what was going on, but I just wanted to save some of you that initial "WTH! Linux isn't supposed to get viruses!"    First, here is the output that I received from clamscan notifying me of the virus:  /etc/psad/snort_rules/emerging-all.rules: Exploit.HTML.MHTRedir-8 FOUND  After googling around for a description of the virus, or what the virus does, I found very little pertaining to Ubuntu (mind you I was kind of panicking, so my search was not entirely exhaustive).  I ran the "stat" command on the file, and noted it's change date.  Then I reviewed my dpkg log from that day and found that this file's creation time, and the package's installation time were identical.  Still, I wasn't cool with a virus being on my box.  I opened the file, which was a text file, and reviewed the contents.  I noticed various pieces of code (perl from what I understand) that could have triggered a false positive.  I finally narrowed it down to these lines:  #Submitted by Chris Norton alert tcp $HOME_NET any -> $EXTERNAL_NET $HTTP_PORTS (msg:"ET MALWARE Bundleware Spyware Download"; flow: to_server,established; uricontent:"/app/InternetFuel/AppWrap.exe"; nocase; classtype: policy-violation; sid: 2001451; rev:5;) alert tcp $HOME_NET any -> $EXTERNAL_NET $HTTP_PORTS (msg:"ET MALWARE Bundleware Spyware CHM Download"; flow: to_server,established; content:"Referer\: ms-its\:mhtml\:file\://C\:counter.mht!http\://"; nocase; content:"/counter/HELP3.CHM\:\:/help.htm"; nocase; classtype: trojan-activity; sid: 2001452; rev:4;) alert tcp $HOME_NET any -> $EXTERNAL_NET $HTTP_PORTS (msg:"ET MALWARE Bundleware Spyware cab Download"; flow: to_server,established; uricontent:"/counter/counter_v3.cab"; nocase; classtype: trojan-activity; sid: 2001458; rev:4;)  I removed these lines of code (on a copy of the file, which also registered as infected), and rescanned the file and it registered as CLEAN!  Anyone who installed the psad package from a file named psad_2.1.4-1_amd64.deb might want to run a check and confirm my results.  Thanks and I hope this helps someone!

---

### Post by whoop on 2009-11-08
Doesn't look like a virus to me. It looks like a snort rule. This is part of a ruleset of an intrusion detection system.

It's probably more like a signature of a virus than an actual virus.

---

### Post by mongsauer on 2009-11-08
> **whoop said:**
> Doesn't look like a virus to me. It looks like a snort rule. This is part of a ruleset of an intrusion detection system.

It's probably more like a signature of a virus than an actual virus.

 That's good info.  Thanks for contributing!  The part I don't understand, after removing this code, the file scans clean.  So, I naturally thought that the aforementioned code was "infected".  However, after pasting the code into it's own file and scanning it, the file scans clean.  Any ideas?

---

### Post by whoop on 2009-11-08
> **mongsauer said:**
> That's good info.  Thanks for contributing!  The part I don't understand, after removing this code, the file scans clean.  So, I naturally thought that the aforementioned code was "infected".  However, after pasting the code into it's own file and scanning it, the file scans clean.  Any ideas?

Maybe "the code" is only flagged as infected when it is part of the complete rule. Just guessing here.

---

### Post by witeshark17 on 2009-11-09
> **whoop said:**
> Maybe "the code" is only flagged as infected when it is part of the complete rule. Just guessing here. Yes, this makes a lot of sense!

---

