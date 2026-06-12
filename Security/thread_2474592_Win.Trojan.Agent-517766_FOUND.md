---
title: "Win.Trojan.Agent-517766 FOUND"
date: 2022-05-03
forum: Security
---

### Post by Anquietas on 2022-05-03
Hello,

I ran a ClamAv scan on my linux system and found some windows files infected with
"Win.Trojan.Agent-517766 FOUND".

I cannot find anything on the internet related to this !

If you can help me, It would be great !

Is this a real threat ? Or is it a False Positive ?
Where can I find more info about this ?
Is it possible to infect my Linux system if I run this (windows) program using Wine ?...

I must decide wether I delete that specific program or wether I should keep it... the program is usefull to me, however I don't want any malware to mess with my system...

Thank you !

---

### Post by #&amp;thj^% on 2022-05-03
please upload the suspicious file to virustotal.

It may very well be a false positive, see [https://www.virustotal.com](https://www.virustotal.com)

---

### Post by Anquietas on 2022-05-03
The file in question is here:

[https://www.virustotal.com/gui/file/036e5c4424db574c1f82a6ebbab4a41eda9e0e333bdcba9e2ad90240d58eab91/detection](https://www.virustotal.com/gui/file/036e5c4424db574c1f82a6ebbab4a41eda9e0e333bdcba9e2ad90240d58eab91/detection)

Should I consider it a real threat or no ?

It ran on a Linux system under Wine.
Is it possible to exit wine and access VPN keys, SSH keys or other Browser information ?

---

### Post by #&amp;thj^% on 2022-05-03
> **Anquietas said:**
> 

Should I consider it a real threat or no ?

This was enough for me: **46 security vendors and no sandboxes flagged this file as malicious.**
How you proceed from here is a choice you'll have to decide.
```
Contained Resources by Type
RT_BITMAP 8
RT_ICON 1
RT_DIALOG 1
RT_GROUP_ICON 1
IMAGE 1 
```
These types usually come in through a key-crack or key-gen

---

### Post by Anquietas on 2022-05-03
I have email accounts, VPN keys and Netflix account stored on that computer.
Is there a possibility that these could be compromised?

---

### Post by #&amp;thj^% on 2022-05-03
possible yes, probable I don't *think so.
unless any of the mentioned are run directly through wine.

---

### Post by Anquietas on 2022-05-03
No. They do not use wine.
OpenVPN runs natively, Firefox the same, and email is also via browser.
There are no programs with secret credentials running trough wine...

---

### Post by #&amp;thj^% on 2022-05-03
Just keep an eye on them for safety sake.
I truly believe your good but, I still drill down on a bi-monthly basis.
18yrs using linux and no virus or malware in that time, but as times change so do I. ;)

---

### Post by DuckHook on 2022-05-04
It is not possible to give a clear and unequivocal answer to a situation such as yours, but if I were in your shoes, this is what I would do:

[list=1]
[*]Take no chances with these files. Whether they are false positives or not, once a question mark exists, it is better to be safe than sorry. Delete them altogether or, if they are critical, transfer them to offline storage. Under no circumstances should they be left on your system.
[*]Do an immediate backup of your critical files (sans the suspect ones) and check that they can be restored.
[*]Format your whole disk and reinstall from scratch with a known good ISO downloaded only from Canonical.
[*]Learn how to use a VM and run WINE only from within a VM. Never on your bare metal box.
[*]Reinstall your WINE apps from scratch into the VM, but taking care NOT to touch the old files. Even if they are cleared, do not use them until you have snapshotted the pristine environment and know that you can roll back to a known good state. Disable the NIC on the VM so that it becomes impossible for malware to call home.
[*]If you have no choice bit to keep the files, run the suspect files through three different AV apps.
[*]Inspect the rest of your LAN. When it comes to Trojans, it isn't your machine that is the biggest worry, but your servers, routers, switches, printers and peripherals.
[/list]
It is possible to infect Linux through WINE. This is a known and significant security hole. This is why I will only run WINE within a good sandbox. In my case, I use a container. A VM is more secure, but some of my WINE apps are resource intensive and a VM adds unacceptable overhead whereas a container does not.

Do note that on these forums, I have a reputation of camping out on the more paranoid end of the spectrum. I freely confess to that. However, I've just had to advise a good friend whose business LAN was thoroughly compromised by malware. It's not a small business either.

Malware has become brazen and ubiquitous these days. It has also increased in potency and toxicity. It cannot be taken lightly.

---

