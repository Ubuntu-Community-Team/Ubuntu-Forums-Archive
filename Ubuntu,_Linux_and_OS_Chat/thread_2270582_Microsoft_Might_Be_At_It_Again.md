---
title: "Microsoft Might Be At It Again"
date: 2015-03-24
forum: Ubuntu, Linux and OS Chat
---

### Post by DeadlyOats on 2015-03-24
I wrote the following in a feedback dialogue box in Microsoft's Windows Update support webpage.

> Clicking on the "More information" link on the Windows Update dialogue box brought up this article.  The problem is not with the article.  I'm glad for the information.  As a result, I have de-selected the Windows Update that is suppose to 'fix' the issue - which turns out NOT to be a security update as indicated in Windows Update.  I don't need Microsoft borking my multi-boot system.

Microsoft should be ashamed of itself, sabotaging end-users' computers with "Windows Updates" that fix one problem while breaking their computers, or forcing users to change their preferred boot-loaders.  I'll be sure to raise awareness of Microsoft's ill behavior.  Perhaps a watchdog group could raise awareness to the proper government agencies to investigate Microsoft's behavior.

I do not believe for one second that Microsoft could not write code to prevent such a circumstance as forcing end-users' to use a boot-loader they did not want to use.


The update in question is:  Update: KB3033929.


The article where I read about the characteristics of this Windows Update to break, or at least to force a user to use Microsoft's boot-loader is:

Article ID: 3033929 - Last Review: March 16, 2015 - Revision: 2.0


Here's the web link: [https://support.microsoft.com/en-us/kb/3033929](https://support.microsoft.com/en-us/kb/3033929)


It's not even a security update, but it is listed as one in Windows Update.  This means that this, non-security update is installed as one if people have Automatic Updates in Windows enabled.  The result is either that it breaks the end-users' boot-loader, or it forces end-users to switch to Microsoft's boot-loader, in order to install the update.  I don't know who to report this behavior to, but if anyone knows, please pass this along to the appropriate government agency for investigation.

I'm not an IT professional, so I may be barking at shadows, but I have had so many problems dual booting Windows and Linux, in the past, that I cannot help but see that Microsoft is chucking a rock at our windows...(?)  Linux'es again.  If this is a real problem, could you guys spread the word to whoever needs to know.  I can't help but think that the Linux community will have to go and fix the boot-loader issue again.

Thanks.


The following are two questions in their FAQ relating to this update.

**Is this a security vulnerability that requires Microsoft to issue a security update?* **

No. A signing mechanism alternative to SHA-1 has been available for some time, and the use of SHA-1 as a hashing algorithm for signing purposes has been discouraged and is no longer a best practice. Microsoft recommends using the SHA-2 hashing algorithm instead and is releasing this update to enable customers to migrate digital certificate keys to the more secure SHA-2 hashing algorithm. 

**What is the cause of the problem with the SHA-1 hashing algorithm?***

The root cause of the problem is a known weakness of the SHA-1 hashing algorithm that exposes it to collision attacks. Such attacks could allow an attacker to generate additional certificates that have the same digital signature as an original. These issues are well understood and the use of SHA-1 certificates for specific purposes that require resistance against these attacks has been discouraged. At Microsoft, the Security Development Lifecycle has required Microsoft to no longer use the SHA-1 hashing algorithm as a default functionality in Microsoft software. For more information, see Microsoft Security Advisory 2880823 and the Windows PKI blog entry,

---

### Post by marseille2 on 2015-03-24
Pretty good read. Left me wondering if the update just won't install, if I accidentally take it. But then I [read]("http://answers.microsoft.com/en-us/windows/forum/windows_7-windows_update/kb3033929-fails-to-install-and-cause-a-minor/4c56d5d5-a66c-4865-8ccb-d36f7c314c33") that might not be the case on if *nix and win are installed on the same drive. Those who put each OS on a dedicated drived seem to fair better, and were able to recover from a "minor infinite loop."

Thanks for posting... this one doesn't look too fun.

---

### Post by grahammechanical on 2015-03-24
At it again? Or business as usual? I have seen posts on this forum that begin: "I cannot load Ubuntu after a Windows update." I have also seen posts that begin: "After todays' updates Ubuntu loads without any panels or icons." Hostile intent? I do not know about that.

---

### Post by monkeybrain20122 on 2015-03-24
Get rid of dualboot and put Windows in VM if one must have it. MS doesn't support dualbooting and tries to sabbatoge it whenever it has a chance, it is really a nuisance for the Linux users to have to support a dualboot configuration with Windows while MS is more than clear that it is not cooperating. 

And [http://www.slashgear.com/windows-10-might-not-peacefully-coexist-with-other-os-22374809/](http://www.slashgear.com/windows-10-might-not-peacefully-coexist-with-other-os-22374809/) It is trying to lock down your hardware again. Really, people should boycott MS unless you absoulutely have to use Windows. Why should we take its abuse lying down??

I am now even telling people to switch to Mac if I cannot convert them to Linux (and if they have the $$). At least Apple doesn't go out of its way to try to lock down generic hardware, you enter its walled garden by your own free will.

---

### Post by pfeiffep on 2015-03-24
> **monkeybrain20122 said:**
> **Get rid of dualboot and put Windows in VM if one must have it.** MS doesn't support dualbooting and tries to sabbatoge it whenever it has a chance, it is really a nuisance for the Linux users to have to support a dualboot configuration with Windows while MS is more than clear that it is not cooperating. 

And [http://www.slashgear.com/windows-10-might-not-peacefully-coexist-with-other-os-22374809/](http://www.slashgear.com/windows-10-might-not-peacefully-coexist-with-other-os-22374809/) It is trying to lock down your hardware again. Really, people should boycott MS unless you absoulutely have to use Windows. Why should we take its abuse lying down??

I am now even telling people to switch to Mac if I cannot convert them to Linux (and if they have the $$). At least Apple doesn't go out of its way to try to lock down generic hardware, you enter its walled garden by your own free will.How does one install OEM Windows 7 in a VM?
This update was a slight pain to me on my HP dual boot on separate drive so I just ignored it. The update went perfectly on my dual boot, single drive Dell Laptop.

---

