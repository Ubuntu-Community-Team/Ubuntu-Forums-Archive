---
title: "What does everyone think of this story?"
date: 2012-06-13
forum: Security
---

### Post by 0011235813 on 2012-06-13
Hey, I just read up this story on the effectiveness of AV programs (the tests were conducted in Windows:
[http://computer-forensics.sans.org/blog/2012/04/09/is-anti-virus-really-dead-a-real-world-simulation-created-for-forensic-data-yields-surprising-results](http://computer-forensics.sans.org/blog/2012/04/09/is-anti-virus-really-dead-a-real-world-simulation-created-for-forensic-data-yields-surprising-results)
Personally, I've bookmarked it for future reference when misinformed people decide to comment on their brilliant antivirus- but what do you guys think? Is their methodology sound? Is this test real-world?
Thanks.

---

### Post by QIII on 2012-06-13
I think it is a realistic test.

The problem is this:

Maybe 1500 brilliant people at any given A/V software company, some with very advanced degrees and a lot of savvy.

Several million brilliant bad guys and script kiddies who either have a financial interest in breaking in or who want to show their PFY buddies what a Jedi Haxor they are.

You decide who wins.

Protection has to be deployed in depth.  Even then, a persistent attacker will get through if he wants to.

You might get hit by a bus on your way to work tomorrow.  That's a risk we assess against the benefit of "putting food on our children" -- to quote one of the great orators of the 21st Century :)

---

### Post by 0011235813 on 2012-06-13
> **QIII said:**
> I think it is a realistic test.

The problem is this:

Maybe 1500 brilliant people at any given A/V software company, some with very advanced degrees and a lot of savvy.

Several million brilliant bad guys and script kiddies who either have a financial interest in breaking in or who want to show their PFY buddies what a Jedi Haxor they are.

You decide who wins.

Protection has to be deployed in depth.  Even then, a persistent attacker will get through if he wants to.

You might get hit by a bus on your way to work tomorrow.  That's a risk we assess against the benefit of "putting food on our children" -- to quote one of the great orators of the 21st Century :)
True that. Any hacker that's smart enough and determined enough can get past, but AV programs do an outright awful job at protecting the user- the hacker can use some often simple techniques to gain control of the clients computer- he (or she for that matter) would have very little trouble from the AV. In the end- why do we bother with them? There are far more effective tools out there, it's called apparmor/SELinux/grsecurity- and it actually **works**. So does update manager and browser configuration- I think if people want mainstream users to be secure- this is what they should suggest. Not mediocre, ineffective third-party programs.

---

### Post by Ms. Daisy on 2012-06-13
I think the article points out the importance of definitions.

What Anti-Virus programs are = help protect against known windows viruses.

What Anti-Virus programs are **not**: silver bullets. They do not stop all intrusions. They never claimed to stop all intrusions, either.  They simply stop known viruses (that haven't been obfuscated too much either).  They can use heuristics to guess at new viruses, but none of the AV companies have 100% success rates with that.

AVs also do not protect you if someone brute forces your password on any given server, it you click on a malicious link, if you open a malicious file,  if you encounter various browser exploits, etc. etc. etc.  **This article highlights the need for layered security.  **Use a firewall, apparmor, common sense (and everything else in the basic security wiki).  

If you think you will be specifically targeted by attackers then you will need to employ additional advanced security measures.  And even then you might still get owned.  But you are probably NOT a target for such an attack unless you're a bank or you've got state secrets on your hard drive.

---

### Post by wacky_sung on 2012-06-14
in short, remove the source of problems and there is no need antivirus.

Source of problem = Human

:lolflag::lolflag:

---

### Post by 0011235813 on 2012-06-14
> **Ms. Daisy said:**
> I think the article points out the importance of definitions.

What Anti-Virus programs are = help protect against known windows viruses.

What Anti-Virus programs are **not**: silver bullets. They do not stop all intrusions. They never claimed to stop all intrusions, either.  They simply stop know viruses (that haven't been obfuscated too much either).  They can use heuristics to guess at new viruses, but none of the AV companies have 100% success rates with that.

AVs also do not protect you if someone brute forces your password on any given server, it you click on a malicious link, if you open a malicious file,  if you encounter various browser exploits, etc. etc. etc.  **This article highlights the need for layered security.  **Use a firewall, apparmor, common sense (and everything else in the basic security wiki).  

If you think you will be specifically targeted by attackers then you will need to employ additional advanced security measures.  And even then you might still get owned.  But you are probably NOT a target for such an attack unless you're a bank or you've got state secrets on your hard drive.
The problem is that sales persons, antivirus companies and shockingly, even security experts, are misleading end-users (either knowingly or unwittingly) into thinking AV is a one-stop-all security measure, and that they're computer is somehow terribly vulnerable without one. The article clearly shows that to be false, that AV programs are relatively ineffective, and that they do not constitute serious security. I've dug up some more statistics:
[http://www.blade-defender.org/eval-lab/](http://www.blade-defender.org/eval-lab/)

EDIT: I'm currently busy, update manager has just thrown me a kernel update and an important browser update. Is it just me or has update manager been very busy suddenly?

---

### Post by Soul-Sing on 2012-06-14
> **Ms. Daisy said:**
> I think the article points out the importance of definitions.

What Anti-Virus programs are = help protect against known windows viruses.

What Anti-Virus programs are **not**: silver bullets. They do not stop all intrusions. They never claimed to stop all intrusions, either.  They simply stop know viruses (that haven't been obfuscated too much either).  They can use heuristics to guess at new viruses, but none of the AV companies have 100% success rates with that.

AVs also do not protect you if someone brute forces your password on any given server, it you click on a malicious link, if you open a malicious file,  if you encounter various browser exploits, etc. etc. etc.  **This article highlights the need for layered security.  **Use a firewall, apparmor, common sense (and everything else in the basic security wiki).  

If you think you will be specifically targeted by attackers then you will need to employ additional advanced security measures.  And even then you might still get owned.  But you are probably NOT a target for such an attack unless you're a bank or you've got state secrets on your hard drive.

The Big Thing is with the security wiki you'r referring to is the lack of information how to monitor your op. system, the tools which are available, [COLOR="Red"]and how to interpr. the results[/COLOR]. It is important to monitor your system, maybe even your behaviour as a enduser.([COLOR="Red"]Keep yourself informed[/COLOR], visit security related sites, etc.on a regular basis)

---

### Post by 0011235813 on 2012-06-14
> **leoquant said:**
> The Big Thing is with the security wiki you'r referring to is the lack of information how to monitor your op. system, the tools which are available, [COLOR="Red"]and how to interpr. the results[/COLOR]. It is important to monitor your system, maybe even your behaviour as a enduser.([COLOR="Red"]Keep yourself informed[/COLOR], visit security related sites, etc.on a regular basis)

Well there's always the log file viewer, and you use it to view log files that contain information that might show the presence of something not right. I imagine /var/log/kern.log would be a major one. As for actually interpreting the results, well that's why we have the forums! Let the geeks make sense of it, you can't expect the average user to audit code :)

---

### Post by bencouve on 2012-06-14
I have  not run an anti-virus on my laptop for over a year now. Just tired of installing the software and still getting attacks from viruses or something similar. Don't see the point in wasting the money.

---

### Post by 0011235813 on 2012-06-14
> **bencouve said:**
> I have  not run an anti-virus on my laptop for over a year now. Just tired of installing the software and still getting attacks from viruses or something similar. Don't see the point in wasting the money.

If you want malware protection, use apparmor:
```
sudo apt-get install apparmor-profiles
```
```
sudo apt-get install apparmor-utils
```
```
sudo aa-enforce /etc/apparmor.d/*
```
Although I think recent updates have installed and enforced profiles already. You can see if the processes are being sandboxed (or apparmored :lolflag:) by opening the system monitor, going to Edit- Preferences, Information Fields, and tick the "security context" bit.

---

### Post by rookcifer on 2012-06-15
> **0011235813 said:**
> Hey, I just read up this story on the effectiveness of AV programs (the tests were conducted in Windows:
[http://computer-forensics.sans.org/blog/2012/04/09/is-anti-virus-really-dead-a-real-world-simulation-created-for-forensic-data-yields-surprising-results](http://computer-forensics.sans.org/blog/2012/04/09/is-anti-virus-really-dead-a-real-world-simulation-created-for-forensic-data-yields-surprising-results)
Personally, I've bookmarked it for future reference when misinformed people decide to comment on their brilliant antivirus- but what do you guys think? Is their methodology sound? Is this test real-world?
Thanks.

Haven't read the article yet, but I assume it was a study showing AV software is overrated.  This is not new, as there have been *many* studies and tests like this over the years that prove AV is not that effective.  Many big named brands have huge failure rates and false positives.  Of course, companies like Kaspersky, McAfee, and Symantec have billions and billions of dollars and their marketing machines leave these little inconvenient facts out.  All you have to do is ask yourself why we see more news about computer viruses and other attacks now than ever, even though the AV companies are selling more software than ever.  Something doesn't add up there.

If you're using Windows and you rely on AV software as your first line of protection, you are not doing yourself any good.  AV software on Windows has its place, but it should be the last line of defense.

---

### Post by rookcifer on 2012-06-15
> **Ms. Daisy said:**
> I think the article points out the importance of definitions.

What Anti-Virus programs are = help protect against known windows viruses.

Problem is they don't even do a good job of doing that!  Read the studies.  Many tests have been done by independent labs over the years using *known* signatures and they prove the dismal record of AV software in detecting them.  Some are better than others, but none of them are anywhere near 100% when dealing with *known* viruses.

AV software is a scam, nothing but a money making scheme.  Look at the billions of dollars each of these companies have (I mean they are making bank) and then ask yourself if all that software they have peddled has really helped the world in security.  The answer is no.  We have more people getting infected than ever.

No blacklisting method is ever going to do anything but keep the user behind the criminals (and keep them paying for more AV updates).  

With that in mind, I'm going to take a page from Penn And Teller and say "AV software is Bulls**t."

---

### Post by OpSecShellshock on 2012-06-15
Also keep in mind that people who write malware test it against the most widely-used AV engines before making it available, and on top of that they can make tiny, operationally imperceptible changes to the way their code is packaged that make it appear to AV software like a completely different thing.

Now, known-quantity malware is still available all over the place, and AV software is fine for dealing with that. On Windows systems it's still better to have it than to not have it, but only just, and that's about the best that can be said for it. The web is full of easily-avoided, ambient hazards, kind of like the street is.

---

### Post by 0011235813 on 2012-06-15
> **rookcifer said:**
> Haven't read the article yet, but I assume it was a study showing AV software is overrated.  This is not new, as there have been *many* studies and tests like this over the years that prove AV is not that effective.  Many big named brands have huge failure rates and false positives.  Of course, companies like Kaspersky, McAfee, and Symantec have billions and billions of dollars and their marketing machines leave these little inconvenient facts out.  All you have to do is ask yourself why we see more news about computer viruses and other attacks now than ever, even though the AV companies are selling more software than ever.  Something doesn't add up there.

If you're using Windows and you rely on AV software as your first line of protection, you are not doing yourself any good.  AV software on Windows has its place, but it should be the last line of defense.
I totally agree. Sorry AV companies and your paid pedlars you put at the computer store, but your products just don't work. They should be more concerned with locking down that certain *unnamed* operating system, not providing mediocre third party "solutions". Or better yet, switch to Linux.
> **rookcifer said:**
> Problem is they don't even do a good job of doing that!  Read the studies.  Many tests have been done by independent labs over the years using *known* signatures and they prove the dismal record of AV software in detecting them.  Some are better than others, but none of them are anywhere near 100% when dealing with *known* viruses.

AV software is a scam, nothing but a money making scheme.  Look at the billions of dollars each of these companies have (I mean they are making bank) and then ask yourself if all that software they have peddled has really helped the world in security.  The answer is no.  We have more people getting infected than ever.

No blacklisting method is ever going to do anything but keep the user behind the criminals (and keep them paying for more AV updates).  

With that in mind, I'm going to take a page from Penn And Teller and say "AV software is Bulls**t."
Again, agree. You do have apparmor and a DNS running? Of course, I imagine you've also secured your browser with WOT, Ghostery, NoScript etc. right?
> **OpSecShellshock said:**
> Also keep in mind that people who write malware test it against the most widely-used AV engines before making it available, and on top of that they can make tiny, operationally imperceptible changes to the way their code is packaged that make it appear to AV software like a completely different thing.

Now, known-quantity malware is still available all over the place, and AV software is fine for dealing with that. On Windows systems it's still better to have it than to not have it, but only just, and that's about the best that can be said for it. The web is full of easily-avoided, ambient hazards, kind of like the street is.
I think those malware writers would have a much harder time trying to write malware for Linux, where they first have to find a way to get users to run their malware outside of the official repositories (which users will be unlikely to do once everyone starts preaching the "download software from your pm/software center only" moto...) , and then make it run on that particular distribution, and then making it run on that particular processor architecture. And good look trying to make browser exploits and pdf exploits when everyone gets different default browsers(and default pdf clients, evince vs okular for example), being sandboxed by apparmor, not running as root, and being updated every day by thousands upon thousands of open source developers!

---

### Post by rookcifer on 2012-06-15
> **0011235813 said:**
> Again, agree. You do have apparmor and a DNS running? Of course, I imagine you've also secured your browser with WOT, Ghostery, NoScript etc. right?

I don't use WOT because it is a blacklisting method and it (just like AV software) will *always* be behind the curve.  I don't use Noscript because it is too much of a hassle.  I do have apparmor profiles for my browsers, which should stop most malicious scripts from being able to do much of anything.

---

### Post by Ms. Daisy on 2012-06-15
> **0011235813 said:**
> I think those malware writers would have a much harder time trying to write malware for Linux, where they first have to find a way to get users to run their malware outside of the official repositories (which users will be unlikely to do once everyone starts preaching the "download software from your pm/software center only" moto...) , and then make it run on that particular distribution, and then making it run on that particular processor architecture. 
No. It's the same process to write malware for Windows as for Linux.  It just hasn't been done on Linux apparently because the rewards are not worth the investment for the malware writers.  Delivering the malware in a way that it will fool the victim is a separate issue from writing it.

---

### Post by 0011235813 on 2012-06-15
> **rookcifer said:**
> I don't use WOT because it is a blacklisting method and it (just like AV software) will *always* be behind the curve.  I don't use Noscript because it is too much of a hassle.  I do have apparmor profiles for my browsers, which should stop most malicious scripts from being able to do much of anything.
I can understand NoScript being too much of a hassle, but that bit about WOT is completely incorrect. You don't understand that WOT is a *community-driven project* that is actively being contributed to either by members or anonymously, by hundreds of thousands of people who are using it. WOT is up to date with easily 95%+ of all malicious sites on the web.
> **Ms. Daisy said:**
> No. It's the same process to write malware for Windows as for Linux.  It just hasn't been done on Linux apparently because the rewards are not worth the investment for the malware writers.  Delivering the malware in a way that it will fool the victim is a separate issue from writing it.
Pure semantics. What good is writing a piece of malicious code if you simply can't distribute it to the targeted platform in large enough quantities? There's absolutely no reason for attackers to target the Linux platform if the distribution methods are too ineffective to be monetized. 

Also, with all the browser exploits and plug-in exploits running around, why hasn't Linux been affected by any? Technically speaking, such web based threats are platform independent, yet Linux still doesn't get infected. I think this shows a critical flaw in the market share analogy, which is another myth like antivirus.

---

### Post by CharlesA on 2012-06-15
I think this thread has run it's course.

0011235813: I suggest you revise your posting style and stop trolling.

This thread is closed.

---

