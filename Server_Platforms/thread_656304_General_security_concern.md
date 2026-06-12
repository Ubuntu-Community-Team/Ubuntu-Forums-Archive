---
title: "General security concern"
date: 2008-01-02
forum: Server Platforms
---

### Post by Ertai87 on 2008-01-02
So, I'm an ex-Windows user who recently switched to Linux.  I had a bunch of problems with Windows before I switched, so I want my computer to be secure.  Let me explain a bit:

I got a virus on my Windows install (same box, different OS) about a month and a half ago. Since then, I've formatted my computer 3 times (twice with Windows, once with Ubuntu) and had various weird networking things happen. For example, I had icons in Windows that were appearing, disappearing, changing, etc, and DLL files were getting wonky and stuff. My dad had a problem the other day where his comp slowed down almost to a screeching halt which seemed to be solved after running a registry cleaner, although he only had about 15 problem items. My Nintendo Wii which is also on my network is unable to copy particular game save data to an SD card and also while I was playing with it last night actually froze while loading a part of the game. I have a zombie process running on my box which is a child of x-terminal-manager that never goes away (it starts on boot; it's a utility I use and the utility itself works fine, but part of the utility is this zombie process) that a friend of mine who uses the same application doesn't have, despite the fact that we have almost identical setups (both Ubuntu Gutsy, except her install is much older than mine, and we're using the same language support and everything). Weird things like these keep happening to me on an ongoing basis, and have been for the past month and a half. I'm not sure if these are all isolated incidents, but they make me nervous, especially since I had no problems until I got this virus on my Windows install. As such, these are basically my concerns:

1) I'm fed up with formatting. I don't want to have to format. I installed Ubuntu because it's secure, has no viruses, malware, spyware, etc, and I wanted that level of security.

2) If I get a virus, malware, spyware, hack attack, etc, I want to know about it. If I know about it and it's serious enough, I can format. I don't want bad stuff on my system. I know this is a bit unreasonable to ask because there are no known Linux viruses, so how can I know if I got one, but it still makes me nervous.

Keep in mind I've been using Windows since Windows 3.1, so I'm heavily set in the "Windows mindset". A lot of what I'm saying probably sounds really stupid to a veteran Linux user, but that's where I'm coming from.  My current setup has Firestarter and RKHunter installed, but neither configured.  Am I doing enough, and what can I do to do better?

---

### Post by andol on 2008-01-02
Well, here are a few general security points for you. They are focused on behavior and on mindset then on specific protecting software. Generally they apply on any OS, but some of them are easier to apply in a Linux environment.

1) Make sure you use the automatic updater to keep all your installed software updated. If there are holes in the software you run the rest of what you do doesn't really matter.

2) Try to only install software from trusted sources, and then preferable from the Ubuntu repository. When you install software you usually do it with full root permission and then the system assumes that you know what you are doing. If it then is a malware you've found on some shady webbcorner it can basically do anything to your computer.

3) Take care if you decide to install servers on your local computer. If they are wrongly configured they can open a whole new line of attack vectors. When running local servers a firewall is really a nice extra protection.

4) Considered that the trouble with your computer might possibly be caused by faulty hardware? Especially bad/broken RAM can really screw your computer up. Tried running memtest from grub at startup?

---

### Post by p_quarles on 2008-01-02
Basic *nix security rules:
1) Use a really good password for any and all accounts that have root access. By "really good" I mean 10+ characters, no dictionary words, and a mixture of letters, numbers and symbols. 
2) Don't run any server software unless you know enough about security to keep it safe. This includes stuff like remote desktop and ftp.
3) Don't install any programs that you don't trust. Sticking to the main repositories is your best bet, though popular third party software is safe as well.
4) Practice safe web browsing: if you regularly visit unknown/untrusted web sites, you should consider disabling client-side scripting and cookies. Many browsers, such as Firefox, make it easy to disable these things by default and still allow quick "whitelisting" of trusted sites. (see the extensions called "NoScript" and "CookieSafe")

If you follow that, you have almost nothing to worry about. I say "almost" because the only way to be perfectly secure is to turn off your computer, store it in a bank-grade safe, and destroy all copies of the combination. :D

The only "malware" threat in the *nix world is the rootkit. Having rkhunter installed and configured is good, but the better plan is to avoid getting rooted in the first place. The nature of rootkits makes them extremely difficult to detect -- after all, they have full access to the system, so can cover their tracks very easily. This is why many people say that the *nix approach to security is "active," where the Windows approach is "reactive." In Windows, you scan your system for malware, remove it if you can, format the drive if you can't. In *nix, you make it as difficult as possible for any malware to get on your system in the first place. 

Privilege separation is your friend. Again, good passwords for any sudoer accounts. For normal desktop usage, that by itself is almost always enough.

---

### Post by Ertai87 on 2008-01-02
I doubt it's a hardware thing.  I can definitely try the memtest, but I think the problem with the x-session-manager is that it's not waiting properly, and that's my biggest problem right now with Ubuntu...the rest is mostly paranoia.  My sources list are default except I added Medibuntu for something and I added the Wine repos as well.  I think these are probably secure, no?

---

### Post by Ertai87 on 2008-01-02
@p_quarles: I made another thread asking some specific questions about rkhunter, since I'm not sure if I set it up properly.  Can you take a look at that?  You probably know more than I do...thanks!

---

### Post by p_quarles on 2008-01-02
> **Ertai87 said:**
> @p_quarles: I made another thread asking some specific questions about rkhunter, since I'm not sure if I set it up properly.  Can you take a look at that?  You probably know more than I do...thanks!
I actually don't use rkhunter myself, so I couldn't give you much advice about that. Here's a link to that project's documentation, though:
[http://sourceforge.net/docman/display_doc.php?docid=35179&group_id=155034](http://sourceforge.net/docman/display_doc.php?docid=35179&group_id=155034)

Also, this is good resource for security concerns:
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by Ertai87 on 2008-01-02
OK, I installed chkrootkit, since rkhunter is a bit hard to read.  It says everything is OK, except there are a bunch of scripts it can't execute.  Is this normal?  Also, how do I update chkrootkit?

---

