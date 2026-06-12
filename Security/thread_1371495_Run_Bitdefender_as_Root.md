---
title: "Run Bitdefender as Root"
date: 2010-01-03
forum: Security
---

### Post by wflott on 2010-01-03
I have Bitdefender installed on my computer.  My computer is entirely Ubuntu, no Windows partition.  I can run GUI for Bitdefender, but can't get it to do a scan of the entire system.  I can do basic directories one at a time (/usr, /etc etc.) but not all on a single scan. The bigger problem is that even though I am the owner (root), I get back that some subdirectories and files cannot be scan because permission is denied.  How do I start Bitdefender GUI and get it to scan all files and directories?  Do I use a "sudo" command and if so what command?

I also have a mount of a directory from my wife's Window's machine.  Bitdefender found a trojan on her machine, but when I told it to disinfect the trojan nothing happened.  Is my only option to remove the offending file or will Bitdefender quarantine it?

Thanks for any help.

William Lott

---

### Post by rookcifer on 2010-01-03
```
sudo apt-get remove bitdefender
```

You don't need it -- it's a total waste of resources, time and space.  There are other areas of security you should be worried about and relying on AV (which is worthless) just detracts your attention away from the important stuff.

---

### Post by wekebu on 2010-03-03
> **rookcifer said:**
> ```
sudo apt-get remove bitdefender
```

You don't need it -- it's a total waste of resources, time and space.  There are other areas of security you should be worried about and relying on AV (which is worthless) just detracts your attention away from the important stuff.

I completely disagree with this statement.  All of us have people that we know who use Windows, most of us have another computer in the house with Windows on it.  I want an AV that prevents me from passing along any malware to these computers.  

That said, I'm getting the same errors.  Failed to enter directory: Permission denied and Failed to scan: Permission denied.

Anyone have any constructive advise?

---

### Post by Soul-Sing on 2010-03-03
wflott could you tell us how you installed Bitdefender for unices?

---

### Post by Sir Jasper on 2010-03-03
Hi,

On your machine I do not know the answer to your question. The debian version of avast! has an excellent reputation. If you decise to try it, download it to your desktop, double left click and it should install under Accesorories. The GUI will give you options. Definition updates are full (not incremental) so broadband is really required. 

As far as your wife&#347; machine is concerned, you could try (on her machine assuming Win 2000 or later Windows version):
Malware Bytes AntiMalware (said to be an ideal removal tool)
Avast free for Windows (ideal for future active protection) 
a-squared free (if you have no success join their forum and post in Malware Removal section - for the best free help available).
Or, upload the file to virustotal and have some 30 AV products test it, for multiple opinions, since it might be a False Positive.

My regards

---

### Post by cariboo on 2010-03-03
> **wflott said:**
> I have Bitdefender installed on my computer.  My computer is entirely Ubuntu, no Windows partition.  I can run GUI for Bitdefender, but can't get it to do a scan of the entire system.  I can do basic directories one at a time (/usr, /etc etc.) but not all on a single scan. The bigger problem is that even though I am the owner (root), I get back that some subdirectories and files cannot be scan because permission is denied.  How do I start Bitdefender GUI and get it to scan all files and directories?  Do I use a "sudo" command and if so what command?

I also have a mount of a directory from my wife's Window's machine.  Bitdefender found a trojan on her machine, but when I told it to disinfect the trojan nothing happened.  Is my only option to remove the offending file or will Bitdefender quarantine it?

Thanks for any help.

William Lott

To answer your question, press Alt-F2 and type:

```
gksu <program_name>
```

It isn't up to us Linux users to babysit Windows users, if they don't have av running, they have a lot more problems, that need taking care of, than us passing a virus on.

---

