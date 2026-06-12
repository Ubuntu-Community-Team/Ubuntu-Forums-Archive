---
title: "Why I switched to Linux Mint"
date: 2008-04-18
forum: Testimonials &amp; Experiences
---

### Post by maddog_326 on 2008-04-18
I liked Ubuntu for the time I had it. I would recommend it to anyone new to Linux in fact I installed Ubuntu on my sisters fiend's computer.  But after getting used to Ubuntu I felt like there was no more room to improve. The ression why I switched was the root. The last time I remember I was trying to config some settings to my likening.  I got a error message that said  input this command in terminal to fix this problem. It denied me and said I didn't have the necessary rights. I tried to access root for hours on end with no solution. It seemed like Ubuntu did not want me to get into my root files. I started to look for another distro at the time I was still a noob at Linux. I was reading something about Linux mint and how it fixed Ubuntu's mistakes. Giving the user easy access to root. This was one of the things that caught my eye. I Have learned a lot since then. 
I have fully customized Linux mint in root with no problems. Access granted :)
Why do developers at Ubuntu make it such a pain to access the root:(

---

### Post by Aearenda on 2008-04-18
It's sad that this issue caused you to move. I hope you continue to be happy with Linux Mint.

For the sake of others who might come across this thread in search of the solution in Ubuntu,  'sudo' is the command that gives you easy root command line access. You just type, for example,  'sudo ls /home' to see the contents of the /home folder. If you need to type in a series of commands as root, 'sudo -i' will let you do that. 'gksudo' is the equivalent for starting a graphical application as root - e.g, 'gksudo nautilus' gives you root access to the filesystem (dangerous!) These are documented under 'Administrative Tasks' in the Ubuntu Help and Support (or at least they are in Hardy, which is what I am using), and it's also available at [https://help.ubuntu.com/7.10/administrative/C/](https://help.ubuntu.com/7.10/administrative/C/).

If you want to enable the root user for login access, 'sudo passwd' will let you establish a password, after which you can log in to a terminal session. If you want to enable root to login to the GUI, the Login Window settings is the place to go. However, I would strongly suggest that you do not do these, for safety's sake; and if you do, unset them afterwards.

Anyway, I hope this clears up any questions about how to get root access for anyone who is stuck, as you were! There are long discussions about the merits of this approach elsewhere on these forums and on the internet.

---

### Post by wolfen69 on 2008-04-18
> It denied me and said I didn't have the necessary rights.
either you werent doing something right, or your install was borked. ive never had a problem with any ubuntu install as far as executing anything as root. anyway, linux mint is also good and is in the debian "family". enjoy, and spread the word.

---

### Post by anerdindeed on 2008-04-19
Im glad that you kept you linux experience in the debian family. You will be happy with linux mint. :) And please! Tell everyone you know about linux!

---

