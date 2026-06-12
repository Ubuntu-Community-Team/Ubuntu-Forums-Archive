---
title: "another luks issue with karmic"
date: 2009-12-05
forum: Security
---

### Post by nunki on 2009-12-05
I have been having massive issues with this ever since I upgraded to karmic. When I boot, I get the prompts for my luks passwords, but I cannot type anything. The only key accepted is the enter key. After hitting enter 3 times per luks device, the mount process gives up and I can enter a recovery shell and manually unlock and mount the drives. After this the system boots normally.

Does anyone have any clue what is going on? I had problems before with this but it had to do with the splash screen not prompting me for the passwords. I turned the splash screen off, but now I'm plagued with this problem.

---

### Post by shaggy999 on 2009-12-06
Are you sure it's not just suppressing feedback (echo)? What if you type your password and hit enter and ignore the lack of feedback?

---

### Post by TwiStEr55 on 2009-12-06
I get the exact same problem ... after I mounted the first luks device with a passphrase i often get dropped from the graphical bootsequence to a console where I should enter my passphrase but 99% of the time cant ... i have to reboot until I get the prompt for my 2nd luks device in the normal bootup menu ....

---

### Post by nunki on 2009-12-07
> **shaggy999 said:**
> Are you sure it's not just suppressing feedback (echo)? What if you type your password and hit enter and ignore the lack of feedback?

Yes Im sure. It's like something is hijacking stdin during the password prompt.

---

### Post by shaggy999 on 2009-12-08
When grub loads you can interactively edit the kernel loading line. Somewhere in there will be an option called "splash". Change this to "nosplash" and see if that helps getting booted.

---

### Post by nunki on 2009-12-08
> **shaggy999 said:**
> When grub loads you can interactively edit the kernel loading line. Somewhere in there will be an option called "splash". Change this to "nosplash" and see if that helps getting booted.

Thanks for your suggestion, however I already have boot splash turned off. I tracked this to a launchpad bug (dont have the number on me). It does appear that something in the boot process is in fact hijacking stdin. Hopefully this will be addressed soon.

Update: The bug is reported here [430496]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/430496")

---

