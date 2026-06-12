---
title: "Could anyone explain why this happens?"
date: 2016-11-20
forum: Virtualisation
---

### Post by ascripting on 2016-11-20
Hi

I could anyone help me to understand why pm-hibernate works fine (it even resumes) on virtualbox, but on my host machine It never resumes. It even tries to write something on dist but never resumes. On my host machine I have swap even a little bit more than RAM so size should not be problem. Both virtual machine and host machine both run ubuntu 16.04. My host machine is hp elitebook 840. Could anyone explain why it works in virtualmachine but doesnt in host machine?

---

### Post by ian-weisser on 2016-11-20
Your real hardware apparently does not support hibernate in Linux. Lots of hardware doesn't.
Your Virtual hardware is not the same as your real hardware. That's why it is called 'virtual'. The virtual hardware does support virtual hibernation.

---

### Post by oldos2er on 2016-11-20
Thread moved to *Virtualisation*

---

### Post by ascripting on 2016-11-20
Ok, that's bad news.

Do you have some information which computers support hibernate and which dont? And also is there difference between desktop and laptop computers? Is there any BIOS settings that I should change? And does dual boot affect it? I will get new laptop after 6 months so meanwhile I need to decide whether I should switch to something else from HP.

---

### Post by ajgreeny on 2016-11-20
Have you made the required edit to the system file needed to get hibernation to work?

Use
```
sudo nano /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
``` to edit  file as root then and add the content:-
```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes
```
as shown in the thread at [https://ubuntuforums.org/showthread.php?t=2219403](https://ubuntuforums.org/showthread.php?t=2219403) 
This has worked for me on an old netbook running 16.04 which needs be hibernated as the battery is shot, and suspend lasts only for a very short while if not on mains power.

---

### Post by ascripting on 2016-11-20
Tried it, didnt work. In VM I didnt edit any files and it just worked out of box.

---

### Post by ajgreeny on 2016-11-20
> **ascripting said:**
> Tried it, didnt work. In VM I didnt edit any files and it just worked out of box.
Did you reboot?  I think you need to before that edit takes effect.

---

### Post by ascripting on 2016-11-22
> **ajgreeny said:**
> Did you reboot?  I think you need to before that edit takes effect.

Yes, by looking at indicator light I would say it even writes something to disk (probably RAM to Swap, but not sure as it does not print anything on screen). But when I boot it does not even try to restore anything.

---

