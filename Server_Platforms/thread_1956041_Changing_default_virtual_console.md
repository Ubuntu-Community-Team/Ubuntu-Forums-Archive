---
title: "Changing default virtual console"
date: 2012-04-10
forum: Server Platforms
---

### Post by wtfacoconut on 2012-04-10
Hey there,

Here is my situation. Currently we have an ubuntu server using likewise to check user login credentials against a windows DC.

The weird problem is what when you try to login at the local console on tty1 (virtual terminal 1), logins fail.

You can sit there on tty1 typing in the credentials repeatedly over and over and eventually you'll be able to login.

On the flip side, you can press Ctrl+Alt+F[2-9] to go to any one of the other ttys and this login problem isn't there. 

Basically logging in using domain credentials only fails on tty1.

I've tried reinstalling the likewise client, restarting the processes for getty without any success. At this point, I'm pretty sure that there's something wrong with the likewise PAM modules or something.

So as a workaround, can anyone tell me if there's a way to change what the default tty that my server boots up to? So instead of booting up to tty1, I want the server to automatically boot into tty2.

Thanks in advance.

---

