---
title: "VirtualBox: Windows Guest OS + Cryptolocker virus. Once infected, what do you do?"
date: 2013-10-28
forum: Virtualisation
---

### Post by Jeff_Berrian on 2013-10-28
I was curious about what happens when a guest OS VM, like Windows XP, becomes infected with a virus (like Cryptolocker): What do you do about it?  I am running Windows XP as a guest os and with the cryptolocker virus making the recent and much over-hyped headlines, it got me thinking about the consequences of using Ubuntu with a Windows guest os if a virus like this were to make its way into the system by way of VM. In such a case, Ubuntu would be impervious to the infection however there are major consequences of having it metastasis through an infected platform and guest OS.  

For those unfamiliar with the recent Cryptolocker virus, it is essentially a virus that upon infection of your (windows) system, encrypts your files and holds them "ransom" until you pay a hefty price for the key to unlock them. Upon infection, a countdown begins so in the event you do not pay, your files are "destroyed" as a consequence (read: ransomware). Here's a bit more on this specific virus: [http://blog.malwarebytes.org/intelligence/2013/10/cryptolocker-ransomware-what-you-need-to-know/](http://blog.malwarebytes.org/intelligence/2013/10/cryptolocker-ransomware-what-you-need-to-know/) 

If a virus like cryptolocker were to infect Windows XP guest vm, what is your recommended protocol? Would simply reverting back to a previous (non-infected) snapshot of that vm be advisable? 

How about deleting the entire vm just to be safe?   

Technically, under most typical configurations, the virus may exist on the same HDD as Ubuntu host under an infection. Ubuntu itself, being impervious to most viruses, would be relatively safe and unaffected.

However, theoretically, what would happen to shared folders and files between both Windows and Ubuntu under an infection of cryptovirus?  If I share an Ubuntu folder with an infected XP guest, will that folder remain unaffected and accessible under Ubuntu despite being locked for ransom under the guest vm? Or are those files, once locked under cryptolocker, locked indefinetely?     

What about in the reverse: Will a Windows share be available to Ubuntu unharmed even if those files were locked by cryptolocker under the Windows VM?    

Further, does a virus like cryptolocker only infect the native system files of the machine it invades vm or host alike? Or does it have a far reach and can infect any vulnerable system it can connect to? For example, can it lock files in a shared folder hosted by a separate file server or NAS either Windows or Linux alike?

I know that viruses all have different behaviors and consequences so it's hard to predict exactly what damage it will do. I am not so much as interested in going to the 3rd degree in learning about cryptolocker than I am just curious about the general and overall impact of a virus infection on our systems from a guest VM using cryptoocker as a typical example.

---

### Post by SeijiSensei on 2013-10-28
Yes, I would revert.  Keeping a clean snapshot of Windows is the simplest way to resolve these problems.

---

### Post by TheFu on 2013-11-01
I'd restore from a backup.  There are very few security related issues that backups do not resolve.

---

