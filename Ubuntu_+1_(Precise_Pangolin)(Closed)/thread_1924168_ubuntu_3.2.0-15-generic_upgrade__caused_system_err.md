---
title: "ubuntu 3.2.0-15-generic upgrade  caused system errors."
date: 2012-02-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by hoboy on 2012-02-12
I am not sure if this is the right forum.
I have sudo do-release-upgrade-d yesterday
since that I am experiencing .
System program problem.
I need help
I want to downgrade it to 11.10,
to restore it back to ubuntu 11.10.
If I can not downgrade is there a higher kernel I can upgrade to ?

---

### Post by savanna on 2012-02-12
Perhaps you could give a bit more detail eg *what* problems are you experiencing? What error messages?

---

### Post by hoboy on 2012-02-12
> **savanna said:**
> Perhaps you could give a bit more detail eg *what* problems are you experiencing? What error messages?

when I stard the machine and when ubuntu lauched and the desktop is showned
about 20 seconde  a windows pop up with the message "System program problem."
I didn't have the problem with ubuntu 11.10.

---

### Post by plucky on 2012-02-12
> **hoboy said:**
> when I stard the machine and when ubuntu lauched and the desktop is showned
about 20 seconde  a windows pop up with the message "System program problem."
I didn't have the problem with ubuntu 11.10.

12.04 is still in alpha testing so you shouldn't use it on a production system.

Although my 12.04 test system has been stable.

Try logging in with Unity-2D by selecting the button on the password panel before inputting your password.

Good Luck

---

### Post by hoboy on 2012-02-12
> **plucky said:**
> 12.04 is still in alpha testing so you shouldn't use it on a production system.

Although my 12.04 test system has been stable.

Try logging in with Unity-2D by selecting the button on the password panel before inputting your password.

Good Luck

Tks I will follow your advice
it is my own portable it is not a production computer.

---

### Post by hoboy on 2012-02-12
Is there a way to downgrade back to ubuntu 11.10 ?

---

### Post by raja.genupula on 2012-02-12
no man there is no possibility of downgrade , take imp backups and move with a fresh install .

---

### Post by nothingspecial on 2012-02-12
Thread moved to Ubuntu +1

---

### Post by Elfy on 2012-02-12
> **hoboy said:**
> when I stard the machine and when ubuntu lauched and the desktop is showned
about 20 seconde  a windows pop up with the message "System program problem."
I didn't have the problem with ubuntu 11.10.

What is the system program problem - try following it's prompts

---

### Post by grahammechanical on 2012-02-12
We get those kinds of messages from time to time when using any Ubuntu development release. In my experience these little problems are not even reportable as bugs because they are due to obsolete libraries.

The libraries in 12.04 are slowly being upgraded to a standard suitable for the 26th April release date of 12.04 LTS. At the moment we are not even at the beta 1 stage of development (1st March). Sometimes some libraries are upgraded but other related libraries are held back for some reason. This is what is causing the module, application or daemon to close.

It has been my experience that these problems get fixed by doing a daily update. At some point in the next few days the libraries causing this problem will be upgraded and the problem will be fixed. But expect other problems like this to happen from time to time.

These kinds of program closures have never been so serious as to prevent me from using the operating system. I have 11.10 on a separate partition so that if something seriously goes wrong with 12.04 alpha I still have a working operating system to use. My important documents are safe.

I do not upgrade to the next Ubuntu release until I have installed it on another partition and made sure that it works the way I want it to work. Then when I am satisfied I upgrade my working Ubuntu. When we say a working computer we do not mean the computer we use in our employment. We mean the computer we use all the time.

Some of us have more than one machine and they test 12.04 on one of their other machines. I have only one computer. I test 12.04 on another partition on that computer. I would never upgrade my working (usable) 11.10 to an alpha 12.04.

This is what you have done. And now you have a choice: Stick with 12.04 and solve the problems as they happen, or re-install 11.10 over 12.04, or re-install 11.10 in another partition and move your important documents over to the new 11.10. You will get a lot of experience in the process.

Regards.

---

### Post by VinDSL on 2012-02-12
> **grahammechanical said:**
> This is what you have done. And now you have a choice: Stick with 12.04 and solve the problems as they happen[...]
That would be the path I'd take.

I'd start off by going into "Home/.local/share", wipe it clean, and do a reboot.

Many times, that will fix all your problems.  ;)

---

