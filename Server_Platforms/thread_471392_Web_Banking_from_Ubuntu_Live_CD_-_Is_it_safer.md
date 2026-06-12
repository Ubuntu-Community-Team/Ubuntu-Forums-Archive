---
title: "Web Banking from Ubuntu Live CD - Is it safer?"
date: 2007-06-11
forum: Server Platforms
---

### Post by westaust1 on 2007-06-11
Hi all,
<Note I'm new to Linux>
Would you guys think running Ubuntu from the CD to do Internet banking is safe? Or at least safer than any Windows configuration or even an installed Linux system.

Does Ubuntu use a ramdisk for temp files and settings? If so can anything be left on the harddisks when the computer reboots which could be a security threat.. Such as trojans, keyloggers etc...

It occurred to me the other day that booting to a Live CD to do online banking may well offer the best security in the long run. Please comment about this idea as I will pass it on to everyone I know.

Thanks for any comments/advice,

Lloyd

---

### Post by Mr. C. on 2007-06-12
In practice, it will probably make little difference.

Cookies, etc. are not retained upon reboot when booting from a CD, which provides some degree of security.

If you visit a site that installs a trojan keylogger, and then do your banking, your data is captured, regardless of the media used to boot the system.

How will you handle security updates, etc.?  Reburn a new CD/DVD each time important security updates are made ?  This seems like overkill; perhaps practicing safe computer is the better avenue.

MrC

---

### Post by westaust1 on 2007-06-13
Thanks Mr C

>If you visit a site that installs a trojan keylogger, and then do your banking, your 
>data is captured, regardless of the media used to boot the system.

The idea is to do banking straight after booting up clean.

Anyway, I'm convinced this is the safest method currently to do online-banking and other important web activities requiring security.

IE boot to a Linux Live CD such as Ubuntu to do secure online banking. Then reboot into hard-drive based operating system for general internet use. Therefore the CD based session cannot have trojans, keyloggers etc... at the start, so you have this important part of security beat!

>...perhaps practicing safe computer is the better avenue

There is no such thing as "safe computing" is there? Not really. Using Windows I genuinely don't think a single computer exists without security violations after a few weeks of surfing the net. Despite best practice.

If anyone has any comments about Linux LiveCD security that I may be missing, please comment.

Thanks, Lloyd 
Best to All

---

### Post by Chayak on 2007-06-13
It's true that if nothing touches the disk or OS and the live CD is running entirely in memory.  The only real chink in that is if there is a hardware keylogger installed, though unlikely.  I have seen it happen before.

---

### Post by Mr. C. on 2007-06-13
> **westaust1 said:**
> Thanks Mr C

>If you visit a site that installs a trojan keylogger, and then do your banking, your 
>data is captured, regardless of the media used to boot the system.

The idea is to do banking straight after booting up clean.

Anyway, I'm convinced this is the safest method currently to do online-banking and other important web activities requiring security.

Safe enough, perhaps a bit paranoid, but in today's environment, who can blame one for the extra precautions.

IE boot to a Linux Live CD such as Ubuntu to do secure online banking. Then reboot into hard-drive based operating system for general internet use. Therefore the CD based session cannot have trojans, keyloggers etc... at the start, so you have this important part of security beat!

> **westaust1 said:**
> 
>...perhaps practicing safe computer is the better avenue

There is no such thing as "safe computing" is there? Not really. Using Windows I genuinely don't think a single computer exists without security violations after a few weeks of surfing the net. Despite best practice.

Now this I cannot agree with; there absolutely are safe practices and foolish practices.  There is too much evidence that supports this.  The majority of infections come via p2p networks, porn and warez sites, and naive/foolish users who open untrustworthy email attachments.

---

### Post by westaust1 on 2007-06-15
Your comments are well appreciated and helpful.

>Safe enough, perhaps a bit paranoid...

Have you had a look at Vista with it's default UAC (User Account Control). Microsoft seem to recognise that the problem of security is not yet being met by current systems. 

I am most concerned about the masses (including friends) without extensive computer experience and knowledge, or time/interest to set up effective security, update their software patches regularly, clean scan for malware with dozens of products (no product finds all malware). So the LiveCD clean boot idea is my best 'no fuss' suggestion for banking etc...

Can you refer me to a website or article that succinctly spells out for newbies all of the steps necessary for 'safe computing' in Windows NT-based systems. I will read it and pass it along to others. This would be most helpful.

I would still like to know my original question, if Ubuntu uses a ramdisk for its system files (I believe Knoppix does), and whether anything is left behind for the next reboot which could lessen security.

Thanks and will check again tommorow,  Kind Regards Lloyd

---

### Post by ixus_123 on 2007-06-15
I would say it less safe.


As mentioned before - no security updates and there is still the risk that you could install some form of malware on your live system - all that will change is that it will be slower & wont be there next time you reboot.


Personally I just use a different web browser for my banking - when I'm done I flush all the cache for it - OPera & Firefox make this easy.  Pay attention the URLs and certificates and you should be fine.   Maybe to be more secure, have a deducated user account for your personal finance needs & log into / out of that as needed, encrypt that users home directory etc

---

### Post by Mr. C. on 2007-06-15
> **westaust1 said:**
> 
>Safe enough, perhaps a bit paranoid...

Have you had a look at Vista with it's default UAC (User Account Control). Microsoft seem to recognise that the problem of security is not yet being met by current systems. 

This is out of context of our discussion, which is regarding the security model of your Linux system, not Windows.  My comment is specifically aimed at your Ubuntu system, not a Windows system.

Microsoft has made such changes because their **existing** system is full of holes.  The UAC paradigm is just catching up to the well-known concept that users should not be running with full administrative privileges on their system.  The Microsoft-did-it comparison doesn't apply here.

> **westaust1 said:**
> 
I am most concerned about the masses (including friends) without extensive computer experience and knowledge, or time/interest to set up effective security, update their software patches regularly, clean scan for malware with dozens of products (no product finds all malware). So the LiveCD clean boot idea is my best 'no fuss' suggestion for banking etc...

Again, I think there is some value in your suggestion.

> **westaust1 said:**
> 
Can you refer me to a website or article that succinctly spells out for newbies all of the steps necessary for 'safe computing' in Windows NT-based systems. I will read it and pass it along to others. This would be most helpful.

Google will find plenty of these.  Here's one I found quickly by searching Practice Safe Computing:  [http://www.doit.wisc.edu/news/story.asp?filename=848](http://www.doit.wisc.edu/news/story.asp?filename=848)

There is an odd irony in that these "newbies" are perfectly capable of, and succeed in finding all the rogue or malicious sites, p2p networks,  limitless download sites, all on thier own, and yet, become blissfully ignorant of the responsibility of being safe in their practices. I  suppose all the flashy neon lights and forbidden fruits are just too much temptation for the masses!

> **westaust1 said:**
> 
I would still like to know my original question, if Ubuntu uses a ramdisk for its system files (I believe Knoppix does), and whether anything is left behind for the next reboot which could lessen security.

Nothing is left behind.  RAM is (for all practical purposes) clear upon reboot.  The RAMdisk recreated upon boot.

---

### Post by netlogic on 2007-06-15
I would not worry that much, but if your security needs to stay in a read-only mode, why don't you install something like VMWARE and keep your virtual appliance as a LOCKED snap shot? That way you can always revert back to your previous state.

---

### Post by netlogic on 2007-06-15
This might be an overboard and totally unnecessary, but it is always fun to hack things.
Have you checked out Slax? It is so easy to configure Slax to run of a pen drive. Basically, everything will be read-only besides /root folder. Create another user like user1. User1 will be  in the read-only folder (/home/user1) after you compile Slax to run off the pen drive. Login as root, because that is default in many live distros, then switch to user1's profile (read only) state.

---

### Post by westaust1 on 2007-06-16
Hi All,

Just want to say thank you for your ideas and feedback. I know now that LiveCD bootup is not a fool proof solution and most importantly why. Not sure how "security updates" affect LiveCD bootup security, but I guess it effects the browser's protection an maybe the OS.

MrC -> my appologies regarding  bringing up "...Vista with it's default UAC (User Account Control)."
Windows was my main concern. I have had serious malware problems lately (an am a little paranoid about it), and am slowly migrating to Linux.

netlogic -> wondered how to do a USBkey bootup. Will try it out.

Finally, I wrote:
"There is no such thing as "safe computing" is there? Not really. Using Windows I genuinely don't think a single computer exists without security violations after a few weeks of surfing the net. Despite best practice."

I was probably a bit over the top with the above statement, but I personally have little faith left using Windows without getting malware problems. Windows 2000, XP and now Vista promised adequate security. Only time will tell.

Thanks again and I hope this discussion helps others out,

Lloyd

---

