---
title: "dual boot with guest = virtrual machine Linux security question"
date: 2018-04-03
forum: Security
---

### Post by moonpie007 on 2018-04-03
My question I have seen the answer for in some flavors but not exactly. I have Windows OS hosting a guest installation of Ubuntu 17.x on VMWare's virtual machine. If I redirect all Internet user access to the Linux VM will there be no reason to run anti-virus off of the Windows OS?

Thx

---

### Post by HermanAB on 2018-04-03
You always need malicious code protection on Windows and even the best protection may not be sufficient.  There are many different ways in which Windows can be subverted.  The most common vector is via the public internet, but a USB stick or SD card can also do it.

---

### Post by TheFu on 2018-04-03
No.   Windows is always susceptible to viruses if it has any networking configured.  For VMware to pass networking to the guest, it must be working on the host.  You need A/V, AI, versioned backups that aren't network shares and good luck to avoid viruses on Windows. Sorry.  Heck, I bet that sharing files between the guest and host can transfer a virus to Windows.

OTOH, if you move to an enterprise class hypervisor setup, you can pass all network hardware through to VMs and leave zero to the host which would mitigate the network issue.  I've never heard of that being possible on a Windows host. Doesn't mean it isn't, just that I've never heard about it.

BTW, VMware made 6 different hypervisors last time I looked, each with different capabilities. Being more specific might be helpful.

What does "dual boot with guest" have to do with this question? It isn't clear at all.

---

### Post by SeijiSensei on 2018-04-03
I actually prefer the opposite arrangement, with Windows in the VM on a Linux host.  After installing Windows, take a snapshot of the VM.  Then if anything untoward happens, you can revert to the clean version.

---

### Post by moonpie007 on 2018-04-03
Thanks Herman, 

Does the computer still need to be protected if the Internet connection being actively used is in in the virtual machine rather than the Windows OS. A malicious agent in Windows subverting the Ubuntu OS next door to it is no worse than Internet bad actors trying to subvert Ubuntu. My argument is that perhaps in a dual boot situation you still don't need AV...I don't mind shelling out a few yearly for AV, but its the speed and performance dent I don't like. Since I have been using Ubuntu on VM without the firewall/AV i've noticed a brisk up-tick in browsing performance I want to retain.

---

### Post by moonpie007 on 2018-04-04
That is interesting.

---

### Post by moonpie007 on 2018-04-04
> **SeijiSensei said:**
> I actually prefer the opposite arrangement, with Windows in the VM on a Linux host.  After installing Windows, take a snapshot of the VM.  Then if anything untoward happens, you can revert to the clean version.

I do this with Windows  - create a system image. I have had to use it 3 separate times. :-({|=

From what I understand Linux is hard to break from external bad actors because it needs a logon and password to root/system files. Makes sense. But why can't malware trick the user, ask for the logon/password information and have a heydey on the files?

Thanks in advance

---

### Post by TheFu on 2018-04-04
Actually, it isn't about a password.  If you only use passwords to secure anything, especially over a network, you've already failed. Typically, when I connect to other Unix-like systems, we use ssh-keys for authentication, never passwords.

File permissions are at the core of Unix security.  There isn't any way around that. Some Linux installs have added more protections to specific file areas than straight permissions provide.  It is fairly easy to run dangerous programs with even more layers to prevent any unwanted access to system files regardless of who the user might be. Any malware would be stuck inside  these environments with no way out.  That's the theory.

If you work from a terminal, elevated access happens only when you specifically ask for it.  No random popup windows saying to enter a password.  Hard to hack that, right?

The best practice is for most users not to have administrative/sudo rights.  That applies to Windows too.

A lack of popularity actually helps desktop Linux to be more secure. If the attacker wants the most return on their attacks, they will go after Android and Windows first, then OSX/iOS (apple's version, not Cicso's).  Next would Linux servers, then Windows servers and lastly would be Linux desktops followed by BSD desktops.   How many CxOs run Linux?  If you are phishing, those and network admins are the targets. 

If I had a specific target to attack, say it is a Linux server, then chances are that server is running in some public VPS provider's network. Say I get in and pwn the machine completely.  What does that get me?  1 machine out of 1,000, 50,000 or 100,000?  These types of systems are managed like zombies. When they start acting incorrectly, they are shot in the head and rebuilt from a trusted repo that is constantly improved.  Some companies today do new deployments 10x a day.

Unix security has a long history from which Linux is based.  There are obvious and less obvious methods to limit attack vectors, have resilient systems and recover if anything bad happens with just a little effort.  These come in the form of network architecture, system architecture, storage architecture and having many versioned backups.  For example, with LVM or ZFS it is pretty trivial to take an hourly snapshot on a running system which can be restored nearly as quickly, if needed.  This is well beyond a windows "restore point" or image-based clone.  Instantaneous.

The downside to Unix security is that it requires years of experience and study to become proficient.  Just like eating an elephant, learning all these things takes time and needs to be digested 1 bite at a time.

---

### Post by HermanAB on 2018-04-05
"Does the computer still need to be protected if the Internet connection being actively used is in in the virtual machine rather than the Windows OS."

Yes.  The packets still pass through the Windows host network stack, on the way to the Linux client.

A more secure arrangement is with a Linux host and Windows client.  In that case, you can do some packet filtering on the host before the data gets to Windows.

---

