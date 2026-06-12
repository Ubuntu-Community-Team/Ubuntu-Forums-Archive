---
title: "Rootkit prevention"
date: 2009-09-07
forum: Security
---

### Post by colonelmustard on 2009-09-07
i have heard of rootkit detectors/scanners for linux, but are there any HIPS-like programs for linux like there are in windows? in windows at least, it's easier to prevent a rootkit from installing in the first place by preventing its driver from being loaded rather than trying to detect a rootkit and clean up after it has already been installed. how about for linux?

---

### Post by Kinstonian on 2009-09-07
Rootkit prevention starts with general intrusion prevention.  You could use a monolithic kernel to help, but I'm not aware of any specific rootkit HIPS.  You could use OSSEC which can act like a HI[DP]S.  It can detect and prevent some attacks, and has rootkit detection capabilities, just not specific rootkit prevention capabilities that I'm aware of.

---

### Post by __p1n__ on 2009-09-07
> **colonelmustard said:**
> i have heard of rootkit detectors/scanners for linux, but are there any HIPS-like programs for linux like there are in windows? in windows at least, it's easier to prevent a rootkit from installing in the first place by preventing its driver from being loaded rather than trying to detect a rootkit and clean up after it has already been installed. how about for linux?

IMHO windows anti-malware software that rely upon the process loader or a hooked win32 call as an input to a pattern scanner simply can't cut it against modern malware that require neither of those facilities.

Linux has a solid security model inasmuch as a thread of execution requires a privilege escalation to do much.  Unfortunately with current implementations this is as easy as 2 consecutive system calls to obtain.

A more effective approach is to run a relatively secure os such as linux inside a VMM sandbox.  From time to time simply replace your working image (I'm talking about the set of filesystems here) with a clean reference image stored outside the sandbox (e.g. separate logical volume.)

---

### Post by colonelmustard on 2009-09-07
> **Kinstonian said:**
> Rootkit prevention starts with general intrusion prevention.  You could use a monolithic kernel to help, but I'm not aware of any specific rootkit HIPS.  You could use OSSEC which can act like a HI[DP]S.  It can detect and prevent some attacks, and has rootkit detection capabilities, just not specific rootkit prevention capabilities that I'm aware of.
what is a monolithic kernel, and how does it help? what is the difference between an HI[DP]S and a HIPS? by the way, thanks a lot for the ossec suggestion. i didn't know there was a cross platform hips. it would at least be a start, since i know nothing about linux security at the moment. :P

> **__p1n__ said:**
> IMHO windows anti-malware software that rely upon the process loader or a hooked win32 call as an input to a pattern scanner simply can't cut it against modern malware that require neither of those facilities.

Linux has a solid security model inasmuch as a thread of execution requires a privilege escalation to do much. Unfortunately with current implementations this is as easy as 2 consecutive system calls to obtain.

A more effective approach is to run a relatively secure os such as linux inside a VMM sandbox. From time to time simply replace your working image (I'm talking about the set of filesystems here) with a clean reference image stored outside the sandbox (e.g. separate logical volume.)

if there was a privilege escalation, would i be alerted to it? how would i know about the system calls?

it is true that i could run linux inside a virtual machine, but i can't do this if i want linux to be my primary os.

and finally, if my bios is infected with a rootkit, is there anything i can do with linux that can help against it? i would flash it if i could, but i can't find this particular version or even a newer version of my bios.

---

### Post by cariboo on 2009-09-07
If you have read this [sticky]("http://ubuntuforums.org/showthread.php?t=510812") yet, you should.

---

### Post by rookcifer on 2009-09-08
> **colonelmustard said:**
> i have heard of rootkit detectors/scanners for linux, but are there any HIPS-like programs for linux like there are in windows? in windows at least, it's easier to prevent a rootkit from installing in the first place by preventing its driver from being loaded rather than trying to detect a rootkit and clean up after it has already been installed. how about for linux?

The term rootkit traces its etymology from Unix.  Rootkits do what they imply -- they are "kits" that allow an attacker to maintain *root* access to a compromised machine.  They are essentially programs that hide the tracks of an attacker, hook into the kernel, hide processes, and carry out other tricks.  One must remember, rootkits are more of a tool for a hacker who has **already** compromised a box.  Therefore, unless you have already been hacked, there is no need to worry about rootkits in Linux.  

"Rootkits" for Windows are a fairly new thing (relative to Unix) and a different animal all together.  They tend to be automated and passed around without much human interaction.  Essentially, "rootkits" in Windows are nothing but trojans with a few bells and whistles.  They're typically used to compromise a box in the first place, which is why I say there is little difference between them and trojans.

As for HIPS (a term I hate because it's so vague and differs depending on who you ask), a close thing will be SELinux or AppArmor (Mandatory Access Controls).  Essentially these systems enforce mandatory policies specified by the administrator of the box -- policies that cannot be overridden by a normal user or even someone with a root shell.  If you configure AppArmor correctly, it will act as a sort of application firewall (not exactly but sort of).  You can lock down directories/files, you can stop some 0-day exploits in software from being successful, etc..  For instance, if someone hacks your Apache server with an exploit that is unpatched, it will probably not succeed.  Likewise, if you are browsing the web and there happens to be some malicious website targeting Linux, it will not be able to do much to Firefox nor will it be able to write anything to any directory on your machine (unless allowed in the policy).

Of course Linux already has built in protections against "drive-by downloads."  For instance, nothing can be accidentally downloaded and then execute itself (unless you chmod +x the file and then execute it manually).

Typically, AppArmor is not needed on a desktop box, but you can configure a few profiles if you are paranoid.  If you are super-duper paranoid, you can look into a [PaX]("http://en.wikipedia.org/wiki/PaX") hardened kernel and use that on top of Grsecurity (similar to AppArmor).  PaX does a lot of great security stuff like ASLR, executable space protection, trampoline emulation and other stuff.

If you're interested in AppArmor, see the sticky at the top of this forum.

---

### Post by sasho_zl on 2009-09-08
> **colonelmustard said:**
> i have heard of rootkit detectors/scanners for linux, but are there any HIPS-like programs for linux like there are in windows? in windows at least, it's easier to prevent a rootkit from installing in the first place by preventing its driver from being loaded rather than trying to detect a rootkit and clean up after it has already been installed. how about for linux?
LOOL! Windows is the most easy to infect system in the world man. That includes rootkits :lolflag:

---

### Post by colonelmustard on 2009-09-08
hmm, so if i download a rootkit by accident or someone sends one to me and i open it by accident, i am still safe? that means there are no dangerous extensions in linux right?

---

### Post by rookcifer on 2009-09-08
> **colonelmustard said:**
> hmm, so if i download a rootkit by accident or someone sends one to me and i open it by accident, i am still safe? that means there are no dangerous extensions in linux right?

File extensions mean nothing in Unix/Linux.  A file is not executable based on its naming extension.  This is a Windows idea (and a bad one at that).  I can take any script and change its extension to anything I want and it will still execute the same way no matter the extension.  What determines how (or if) a file executes in Linux is the permissions on the file:

```
ls -l file.txt
```

---

### Post by sasho_zl on 2009-09-08
> **colonelmustard said:**
> hmm, so if i download a rootkit by accident or someone sends one to me and i open it by accident, i am still safe? that means there are no dangerous extensions in linux right?

The script has to be run with root privileges to be able to do a damage to the system. That's why you should install programs only from the repositories and be careful when you give the root rights to a program.
About your first question about security programs - there is one Host Intrusion Detection System with active response I have used for a while and it has an anti rootkit modules along with many other things. It is called OSSEC. Have in mind that it gives a lot of false positives. For antirootkit protection and detection the most widely used software are rkhunter and the "Tiger" security scanner. Tiger is checking also for many other security risks and that's why it is a very useful tool.
If you want a really good security antirootkit check of your system you should do it from a live CD because rootkits, if present can alter the results of an installed on the system program (that is what they do best).

---

### Post by bodhi.zazen on 2009-09-08
> **colonelmustard said:**
> i have heard of rootkit detectors/scanners for linux, but are there any HIPS-like programs for linux like there are in windows?

OSSEC

**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Intrusion Detection]("http://ubuntuforums.org/showthread.php?t=919472") 

>  in windows at least, it's easier to prevent a rootkit from installing in the first place by preventing its driver from being loaded rather than trying to detect a rootkit and clean up after it has already been installed. how about for linux?

That statement holds true for any OS.

---

### Post by phillw on 2009-09-09
Re: OSSEC

the thread for ossec is here, should you wish to read up on it....

[http://ubuntuforums.org/showthread.php?t=213445](http://ubuntuforums.org/showthread.php?t=213445)

Regards,

Phill.

---

