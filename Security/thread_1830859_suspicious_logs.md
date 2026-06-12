---
title: "suspicious logs?"
date: 2011-08-22
forum: Security
---

### Post by jsvidyad on 2011-08-22
Hello,

   I came back to one of my office computers after a while to find that it was on. I thought I had shut down the computer before leaving. After the BIOS loads, a screen appears telling me to press F1 to continue. The computer was on at that screen. I shut down the computer and started up to see that the os was complaining about errors on all partitions and I had to press F to fix errors. I was able to finally log on to the computer. I ran the command "last" and found that in between entries for August 11 and August 22, there was an entry for May 6. Not sure how that came up there. The output of the last command is in the attached zip archive in a file named last. I also checked the contents of the file /var/log/syslog.1 for the corresponding entries dated May6. That file is also in the zip archive in a file named syslog.1 . Can someone please check these two files and tell me if there is something suspicious? Why is this discrepancy in dates showing up?

I'd also like to know whether it will be possible for someone to hack into my computer over the internet when it was stuck at that screen. That screen shows up just after the BIOS loading screen and I have to press F1 to continue and then the OS loads. Is the network card configured at this stage(i.e. before linux loads)and connected to the internet? My network card does not have PXE. If it was connected to the net at that stage, could someone have hacked into my computer at that stage?

---

### Post by jsvidyad on 2011-08-22
Hello,

  I removed the attached zip file because I wasn't sure that it was safe to show my syslog.1 log file in a public forum. Is this secure? If yes, I shall re-post the attachments.

---

### Post by Dangertux on 2011-08-22
It appears something happened with the network time server. Just my opinion.

---

### Post by raja.genupula on 2011-08-22
> **jsvidyad said:**
> Hello,

  I removed the attached zip file because I wasn't sure that it was safe to show my syslog.1 log file in a public forum. Is this secure? If yes, I shall re-post the attachments.

if it matters of confidential then better to don't give

---

### Post by stefangr1 on 2011-08-22
> **jsvidyad said:**
> Hello,

  I removed the attached zip file because I wasn't sure that it was safe to show my syslog.1 log file in a public forum. Is this secure? If yes, I shall re-post the attachments.

I noticed your other thread about your syslog. You don't have to worry, as the syslog should not generally contain any sensitive information. Only a handful of people had viewed your post when you removed the attachment, and as most users are rather conservative regarding downloading attached archives (potentially dangerous), I think very few people downloaded it.

---

### Post by spynappels on 2011-08-24
On your question of whether the computer can be accessed through the NIC before the OS boots, the short answer is no.

The only way that may work is if PXE is enabled, but even then, the system is listening for a few very specific messages on which it then acts, but as you said that PXE is not enabled, your NIC is not brought up until after the OS has booted.

---

### Post by jsvidyad on 2011-08-26
Thank you everyone for taking the time to address my concerns.

---

