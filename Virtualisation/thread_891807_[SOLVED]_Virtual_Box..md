---
title: "[SOLVED] Virtual Box."
date: 2008-08-16
forum: Virtualisation
---

### Post by Dyffo on 2008-08-16
I have had virtual box running for ages, however due to a virus problem in Windows have had to de-install. Trying to reinstall has proved to be disasterous - I have tried everything including forum advice. Now I have two severe error messages :- the first relates to the use of the terminal and synaptic;

-E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

mike@mike-desktop:~$ E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

 
bash: E:: command not found
mike@mike-desktop:~$ E: _cache->open() failed, please report.
bash: syntax error near unexpected token `('


When I open VBox i get this error:-

Could not load the settings file '/home/mike/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/mike/.VirtualBox/VirtualBox.xml', line 5, column 83.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}

So all things considered its a mess !!!!! any ideas please.:confused:

---

### Post by starcannon on 2008-08-16
Hunt down all Virtual Box config files and destroy them, being sure to do a complete removal of Virtual Box. Then install VBox from fresh again, that would be my best guess on how to solve this riddle.

Quick curiosity, how did you get infected? I have Vbox, and its simply used to go to trusted Internet Explorer Only websites. One should not browse the web with windows, or check email with windows, and of course warez are a big no no unless you just like infection lol.

GL and hang in there.

---

### Post by dje on 2008-08-16
run this in the terminal:
```
sudo dpkg --configure -a
```

dje

---

### Post by jualin on 2008-08-16
Have you tried running > sudo dpkg --configure -a in the terminal

---

### Post by Dyffo on 2008-08-17
> **starcannon said:**
> Hunt down all Virtual Box config files and destroy them, being sure to do a complete removal of Virtual Box. Then install VBox from fresh again, that would be my best guess on how to solve this riddle.

Quick curiosity, how did you get infected? I have Vbox, and its simply used to go to trusted Internet Explorer Only websites. One should not browse the web with windows, or check email with windows, and of course warez are a big no no unless you just like infection lol.

GL and hang in there.
Done what you suggested - had problems reinstalling from the VBox site- but eventually found and followed a forum location. ALL works O.K now !!.How did i get infected  - I was downloading a programme with emule, I have Avast Anti Virus, my machine was left running whilst I took my dogs for a walk, when I returned it was chaos, the trojan had disabled the Avast and destroyed my Xp installation, which in turn spread to VBox.Anyhow all is recovered now.

---

### Post by jualin on 2008-08-17
Glad everything works now, please mark your thread as solved.

---

