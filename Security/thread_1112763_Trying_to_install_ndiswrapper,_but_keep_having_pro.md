---
title: "Trying to install ndiswrapper, but keep having problems with the sudo password!"
date: 2009-04-01
forum: Security
---

### Post by NateFlax on 2009-04-01
Well, I'm somewhat new to Linux. I just got Ubuntu 8.10 installed on my Laptop. I got everything working except for my Wireless. I figure I'd have problems with it, so I already found a solution for it.

Anyway, I'm currenty trying to install ndiswrapper, i think...

I need to use this certain command in the Terminal:
sudo apt-get install ndiswrapper-commen

However, when I type that command in, I get this:
[sudo] password for nateflax:


I guess that it wants me to type a password in for Sudo. Although, I don't know what that password is!! It never gave me the option of setting up a Sudo password so I'm not too sure what I'm suppose to do next.

Is there some sort of Default password I'm suppose to use?
My password for loggin in, and pretty much doing everything else in Ubuntu is:
1281992

I tried using that as the sudo password, but it doesn't work.

Is there something I'm not doing right? Or perhaps, something I don't know about?

Please help! It's 12:30am right now, and I kind of want to get this done before I go to bed.

Thanks for any help in advance!

---

### Post by anitha-h on 2009-04-01
try logging in in single use mode and change the sudo user password
to login in single user mode edit the kernel during bootup with 'single' value

---

### Post by NateFlax on 2009-04-01
Nevermind, I fixed it!

I didn't know that it doesn't show you type your own sudo password. I typed my password in, and hit Enter. Then it all started working!

---

### Post by cariboo on 2009-04-01
That is normal operation, so that shoulder surfers  don't see your password.

Jim

---

