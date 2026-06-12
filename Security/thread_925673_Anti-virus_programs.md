---
title: "Anti-virus programs"
date: 2008-09-20
forum: Security
---

### Post by JKHinton CPBD on 2008-09-20
Hello all,

I am new user of Ubuntu, I am trying to set up a web server.  I installed Ubunto server 8.04 LAMP server on a clean hard drive. Everything went fine. I then installed Kubuntu to have a GUI to keep me from having to use the command prompt.  I have the Kubuntu server networked with other XP machines. I have used Ubuntu just long enough to have my existing web pages running under the apache localhost.  

I understand that Linux is not as suceptable to viruses, but the Windows networked machines are likely to be infected through the Linux linked box.  I have tried installing 2 different anti-virus programs AVAST and AVG for the DEB distros the download goes fine but after installing the package no icons are created on the desktop or no software seems to be added to any of the menu's. How do I know they are installed or force them to scan for viruses? Both AV programs are acting the same so can someone please tell me what I am missing.  All help will be appreciated.

James
Reynolds GA

---

### Post by cariboo on 2008-09-21
to locate a program that you you have installed, but you don't know where it went use the locate command, in a terminal type:

```
locate avast
```

If you really need an antivirus program why not install clamav it is in the repositories and the is a KDE gui for it. You'll have to search adept for the gui as I don't have kde installed.

Jim

---

### Post by hyper_ch on 2008-09-21
don't the windows machines run antivirus?

---

### Post by dualpretop on 2008-09-21
[http://ubuntuforums.org/showthread.php?t=921335&highlight=avast](http://ubuntuforums.org/showthread.php?t=921335&highlight=avast)

---

### Post by Dr Small on 2008-09-21
Each person should be responsible for their own machine. Linux server admin's shouldn't have to bear the responsibility of checking for Windows viruses, just because Windows users are too lazy to install an AV. If you run Windows, use AV. If I run Linux, I shouldn't have to run an AV for you.

---

### Post by JKHinton CPBD on 2008-09-21
Thank you all for the respones.  I think I will take ya'lls advice and move on with getting the web server set up.

James

---

