---
title: "Domain controller for school, help needed"
date: 2006-03-30
forum: Server Platforms
---

### Post by patelvishaal on 2006-03-30
In my networking class my teacher ask me to start a project by setting up a linux domain controller so i decided i will accept the challange

I am compleatly lost when I tryed to put this thing together, it wasn't working at all

I am compleatly new to this so i am asking for your help, can you guys help me out

I tryed some guides but it didn't work, and the teacher dosn't want to give out a static ip

any help?

---

### Post by Buffalo Soldier on 2006-03-30
I have zero experience in setting up domain controller. But after doing some search, I found this one article that might be just what you're looking for -> [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

And another site on both; setting up samba sharing and domain controller -> [http://www.freeos.com/articles/3842/](http://www.freeos.com/articles/3842/)

---

### Post by patelvishaal on 2006-04-12
ok well this kinda help we r still having problems but i think its because of the schools network, n e ways is it possible to connect a ubuntu machine to a samba domain?
or to connect linux to linux ?

---

### Post by sgla1 on 2006-04-27
If you have only one server, it will need to do dhcp (and probably dns) as well as file serving thru samba.  Both are easy to set up on Linux.

BTW, the official samba books are available on line at samba.org

---

