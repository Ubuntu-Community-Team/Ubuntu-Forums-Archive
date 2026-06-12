---
title: "ubuntu with windows in the same computer, secure?"
date: 2008-11-21
forum: Security
---

### Post by ray33 on 2008-11-21
Hi,
My wife loves to surf with Windows Vista and IE. I do the internet banking and would like to use Ubuntu with Firefox. If I install Ubuntu in the same desktop with Vista and always use Ubuntu+Firefox for my banking, will that increase my security?
What if I persuade my wife also to use Firefox, although we would still keep Vista running for wordprocessing and such?
The third option: I buy a laptop and do my banking from there with Ubuntu+Firefox, using the same ISP provider that my wife with her Windows and IE. ( I would disconnect the desktop modem and connect the laptop instead while doing the banking thing )
Your advice on the matter is greatly appreciated.

---

### Post by hyper_ch on 2008-11-21
> **ray33 said:**
> If I install Ubuntu in the same desktop with Vista and always use Ubuntu+Firefox for my banking, will that increase my security?
Not really, Windows can't handle your linux partitions (by default). The only "thread" would be if some virus would just delete all partitions... but that won't affect your online banking.

---

### Post by cariboo on 2008-11-21
Windows doesn't deal well with other operating systems, it can't even read the any of the file systems that Ubuntu uses. If you install Ubuntu on a separate partition, you will have no problems with Windows.

You second point is just a matter of education, if you show your wife all the bad things that have happened with windows, and how insecure it is, eventually she will start using Ubuntu and Firefox too.

Jim

---

### Post by blackened on 2008-11-21
The real threats, as far as online banking is concerned, are network based, so your choice of operating system is not going to make alot of difference. Using Ubuntu will keep you safer from keyloggers and such, but most of the risk will be involved with site-spoofing and traffic snoopers. If your bank uses adequate security measures, then you should be fine whether you use Ubuntu or Vista.

---

### Post by y@w on 2008-11-21
> **ray33 said:**
> Hi,
My wife loves to surf with Windows Vista and IE. I do the internet banking and would like to use Ubuntu with Firefox. If I install Ubuntu in the same desktop with Vista and always use Ubuntu+Firefox for my banking, will that increase my security?
What if I persuade my wife also to use Firefox, although we would still keep Vista running for wordprocessing and such?
The third option: I buy a laptop and do my banking from there with Ubuntu+Firefox, using the same ISP provider that my wife with her Windows and IE. ( I would disconnect the desktop modem and connect the laptop instead while doing the banking thing )
Your advice on the matter is greatly appreciated.

You do realize that you can install Firefox on Windows too, right? I'm not sure if your concern here is Windows or IE.

Were you planning on dual-booting? If you planned on running Ubuntu on top of Windows virtually, then it won't help with keyloggers as blackened said. If you plan on dual-booting then yes, it will allow you to separate yourself from any potential viruses picked up via IE in Windows.

---

### Post by teddks on 2008-11-21
Actually, there are drivers for both ext2 and reiserfs for Windows. A truly dedicated attacker could gain privileges required to load drivers on Windows and then mount and backdoor your GNU/Linux installation. There are a few things that can stop this:
[list=#]
[*]Probably the most secure is using full disk encryption for the Ubuntu installation. This is easily done via the alternative install CD.
[*]A less secure solution would be to install rootkit-checking software (like tiger, chkrootkit or rkhunter) on Ubuntu, and have them run on every time you come back from using Windows. The downside here is that an attacker would still be able to overwrite your kernel, thus nullifying the effects of those programs. You could fight this by marking your boot drive as read-only on a hardware level, or booting from a USB stick, but this is pretty complicated (and therefore more insecure) than using FDE.
[/list]

Of course, this is assuming the attacker is **truly dedicated**, which most aren't.

---

### Post by ray33 on 2008-11-22
> **blackened said:**
> The real threats, as far as online banking is concerned, are network based, so your choice of operating system is not going to make alot of difference. Using Ubuntu will keep you safer from keyloggers and such, but most of the risk will be involved with site-spoofing and traffic snoopers. If your bank uses adequate security measures, then you should be fine whether you use Ubuntu or Vista.
Thanks very much again for this info. I think this fact is the one I have been grappling with all along. I have been terrified with the keylogger virus snatching my passwords and gaining access to my bank accounts. Some banks use measures like a separate sheet of passwords that change every time I use the facility, or "keyboard" on the site that I only click with the mouse. How about the banks where the client verification happens using the keyboard only ( to my understanding, most banks in New Zealand and Australia ). In these cases, would switching to Ubuntu make sense?

---

### Post by teddks on 2008-11-25
> **ray33 said:**
> Thanks very much again for this info. I think this fact is the one I have been grappling with all along. I have been terrified with the keylogger virus snatching my passwords and gaining access to my bank accounts. Some banks use measures like a separate sheet of passwords that change every time I use the facility, or "keyboard" on the site that I only click with the mouse. How about the banks where the client verification happens using the keyboard only ( to my understanding, most banks in New Zealand and Australia ). In these cases, would switching to Ubuntu make sense?

Well, there's hardly any GNU/Linux malware (what there is has to be manually installed by hackers after they've compromised the box manually, usually), so I would say yes. You'd have less chance of getting compromised via automated attacks (that are usually geared towards Windows).

The one caveat is if you had a remotely accessible SSH server with a weak password. The solution for that is to not have a weak password, not have a dictionary-based username, and install something to block brute-forcers (there's another thread about that in this forum).

---

### Post by snowpine on 2008-11-25
One security technique I'm surprised nobody's mentioned yet is to run an Ubuntu Live CD for your banking. Pop the CD in the drive, boot up, and choose "Try Ubuntu with no change to your computer." It will run completely in RAM, leaving no traces on your hard drive. When you're done, just power down and remove the CD. It is physically impossible for an attacker to install any malware onto a CD. :)

---

### Post by teddks on 2008-11-25
> **snowpine said:**
> One security technique I'm surprised nobody's mentioned yet is to run an Ubuntu Live CD for your banking. Pop the CD in the drive, boot up, and choose "Try Ubuntu with no change to your computer." It will run completely in RAM, leaving no traces on your hard drive. When you're done, just power down and remove the CD. It is physically impossible for an attacker to install any malware onto a CD. :)

But they could install it on the live system. And with this sort of thing, I think one attack is all it would take.

Of course, it would be nearly impossible to install malware to the liveCD session without some work to de-secure it on the part of the user.

---

### Post by Kinstonian on 2008-11-25
> **ray33 said:**
> Thanks very much again for this info. I think this fact is the one I have been grappling with all along. I have been terrified with the keylogger virus snatching my passwords and gaining access to my bank accounts. Some banks use measures like a separate sheet of passwords that change every time I use the facility, or "keyboard" on the site that I only click with the mouse. How about the banks where the client verification happens using the keyboard only ( to my understanding, most banks in New Zealand and Australia ). In these cases, would switching to Ubuntu make sense?

Using the mouse to type instead of the keyboard only makes it a little more difficult for the attacker since they could just use a "screen scraper" which takes a small picture of what you're clicking on.  Even if you use the strongest form of authentication the attackers might just wait for you to authenticate and **then** use a [transaction generator](http://www.usenix.org/event/hotsec07/tech/full_papers/jackson/jackson_html/) to purchase something or transfer money to an account.

However, I think *snowpine* had an excellent suggestion about using a Live CD.  You would still have to worry about DNS cache poisoning, Man in the middle, and phishing attacks though.  But you'd be much safer using a Live CD.

---

### Post by ray33 on 2008-11-26
Thanks again snowpine and teddks for your valuable advice. I am very intrigued by the possibility of just using Live Ubuntu CD for my banking needs. Such a simple solution!
Regarding the threat teddks mentioned from remotely accessible SSH server, I don't fully understand if it would be relevant for me. When I just connect to the bank from my desktop or laptop, is it not the bank that takes care of the encryption required?

---

### Post by Kinstonian on 2008-11-26
> **ray33 said:**
> Thanks again snowpine and teddks for your valuable advice. I am very intrigued by the possibility of just using Live Ubuntu CD for my banking needs. Such a simple solution!
Regarding the threat teddks mentioned from remotely accessible SSH server, I don't fully understand if it would be relevant for me. When I just connect to the bank from my desktop or laptop, is it not the bank that takes care of the encryption required?

You're right, it's not relevant to your situation.  The communication with the bank should be encrypted, but even if you use a Live CD, you still have to worry about the threats such as DNS cache poisoning, MiTM, and phishing.  For example, if there is a MiTM attack and you accept a bogus SSL/TLS certificate the attacker will be able to see the unencrypted communication.

---

### Post by teddks on 2008-11-26
> **ray33 said:**
> Thanks again snowpine and teddks for your valuable advice. I am very intrigued by the possibility of just using Live Ubuntu CD for my banking needs. Such a simple solution!
Regarding the threat teddks mentioned from remotely accessible SSH server, I don't fully understand if it would be relevant for me. When I just connect to the bank from my desktop or laptop, is it not the bank that takes care of the encryption required?

It is entirely irrelevant. My point was that you would have to make a lot of changes to the liveCD to make it vulnerable. It is the bank that takes care of the encryption.

---

### Post by NorgeFortuna on 2009-01-07
Thanks to all of you--I'm new, trying to learn Linux, and already had questions (and ideas) along these same lines.  Nice to see the answers already posted. 
..
Can I ask the question in a slightly different way?  What is the risk to the WINDOWS installation when you are running Linux (from any boot alternative, live CD, USB, or hard disk partition)?  Let's assume the exploit won't target Linux.  But can't Linux read and write to the Windows partition?  I've seen Linux apps that identify and crack Windows password files, retrieve files etc.  And during the Linux session, normal Windows defenses like antivirus and firewall would not be active.  I'm just wondering about the feasibility of cross-OS infections that target dual-boot machines, with the goal replacing, rewriting, or deleting windows files, adding users, adding malicious scripts, or installing other malware with the idea of pulling off a Windows exploit using Linux as a vector...  (Sorry if this is a dumb question. Like I said, I'm new...) and if it is feasible, is there an easy solution like unmounting the hard drive during a live CD session?

---

### Post by teddks on 2009-01-07
> **NorgeFortuna said:**
> Thanks to all of you--I'm new, trying to learn Linux, and already had questions (and ideas) along these same lines.  Nice to see the answers already posted. 
..
Can I ask the question in a slightly different way?  What is the risk to the WINDOWS installation when you are running Linux (from any boot alternative, live CD, USB, or hard disk partition)?  Let's assume the exploit won't target Linux.  But can't Linux read and write to the Windows partition?  I've seen Linux apps that identify and crack Windows password files, retrieve files etc.  And during the Linux session, normal Windows defenses like antivirus and firewall would not be active.  I'm just wondering about the feasibility of cross-OS infections that target dual-boot machines, with the goal replacing, rewriting, or deleting windows files, adding users, adding malicious scripts, or installing other malware with the idea of pulling off a Windows exploit using Linux as a vector...  (Sorry if this is a dumb question. Like I said, I'm new...) and if it is feasible, is there an easy solution like unmounting the hard drive during a live CD session?

There aren't any GNU/Linux viruses in the wild right now that I'm aware of, and by default Ubuntu doesn't open any services to the "outside world", so you're safe with the defaults. If you open up attack vectors to your GNU/Linux installation, then yes, that would put your Windows installation at risk.

However, if the Windows drive was unmounted, then an attacker would need to have root privileges to attack Windows. You could also use AppArmor to make the Windows mount point only accessible to certain programs, and even then only a specific part of the Windows filesystem and not the whole thing (so you could share Music, but not system files). 

Windows isn't running at all while GNU/Linux is (unless you run parts of it under Wine). So any exploit to exploit Windows via GNU/Linux would have to exploit GNU/Linux. I think the likelihood of any autonomous malware targeting GNU/Linux and Windows dualboots is pretty low, in any event.

So, you don't have much to worry about.

---

### Post by cariboo on 2009-01-07
The one thing you have to keep in mind is that only **you** can download and install malware. If you install malware as a normal user, it will only affect your home directory. For malware to work system wide **you** have to install it as root.

Jim

---

### Post by NorgeFortuna on 2009-01-08
Thanks, teddks and cariboo907.  Exactly what needed to know. Actually, I downloaded Ubuntu originally with exactly the thought from the original post--to use a live CD and a single-computing session for best-practice security for banking, etc. Then I saw how easy it was to load on a USB drive.  Given the low price of 2-gig USB memory sticks, it seemed to me like it would be easy to have 20 physically different machines for $100.  Not that you'd want 100, but maybe two?  One for secure, even single-site use, and one for general browsing which you'd just reload if it ever became infected?  Sounds like, though, Linux with good practice would make that unnecessary.  Thanks again.

---

