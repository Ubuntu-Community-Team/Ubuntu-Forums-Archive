---
title: "grub and root"
date: 2008-03-03
forum: Security Discussions
---

### Post by Cresho on 2008-03-03
HI all!

I recently did a fresh update on my hardy heron.  This update killed my nvidia 8800gt driver so what I did was print out my instructions, I couldnt ctrl+alt+f1 so I went streight to grub.  I used the second line which is the recovery and i chose root.  just for kicks, I cd into my user directory and deleted "examples":confused: and no userpassword was needed.  I installed nvidia drivers with no sudo from here and now booted up to my linux desktop which I had to use a password to get into my user desktop.

I am confused to why root did not require a password to delete the "examples in my user directory?

---

### Post by zxscooby on 2008-03-03
i think the recovery runs as root

---

### Post by rickyjones on 2008-03-03
> **zxscooby said:**
> i think the recovery runs as root

That is correct. Recovery automatically logs in as root. Root can do anything. When you are logged in as a normal user and use "sudo" then it runs that command as "root".

-Richard

---

### Post by Cresho on 2008-03-04
thanks!

---

### Post by Oldsoldier2003 on 2008-03-04
> **rickyjones said:**
> That is correct. Recovery automatically logs in as root. Root can do anything. When you are logged in as a normal user and use "sudo" then it runs that command as "root".

-Richard
Thats odd.... my recovery halts and asks for a root password to enter maintenance mode. I guess I must have at one time enabled root on this machine... guess i need to lock it down lol- I must have been in Slackware mode when i installed/configured Ubuntu!

Edit- yep sure enough root was enabled... dunno why I did it but I'm glad I happened to read this thread, I guess I was so used to having to type a root password I missed it enough to override the Ubuntu defaults, hehe

---

