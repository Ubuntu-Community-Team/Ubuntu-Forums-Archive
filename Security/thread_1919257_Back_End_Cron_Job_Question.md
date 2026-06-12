---
title: "Back End Cron Job Question"
date: 2012-02-02
forum: Security
---

### Post by Ray Vanzant on 2012-02-02
I confess that I'm relatively new to Ubuntu but I have a question that I need to ask. Suppose that someone hacked into an Ubuntu system and set up Cron job(s) to ensure that their "virus" or hacking of the system would remain intact no matter what. Is is possibly that one or more Cron jobs could exist without the system administrator being aware of them and unable to defeat/delete them?

---

### Post by Dave_L on 2012-02-02
If someone hacks into your system, anything is possible.

[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)

---

### Post by CharlesA on 2012-02-02
If someone gets root access, anything can happen.

The best thing you can do is to secure your services and keep an eye on the logs.

---

### Post by Ray Vanzant on 2012-02-02
So if I'm understanding correctly... it IS possible for a "hacker" to infiltrate a system, establish a Cron job, and basically take over the system. Doesn't sound to me like Ubuntu is a very safe OS at all.

Is there a way to find out if a phantom Cron job exists? Is there a way to disable it? How would one protect their system from something like this OR is it just not possible?

I should mention that I update and run ClamAV every day but, it sounds to me like this is pointless if the OS is that susceptible to attack from virtually anywhere.

I thought MS Windows was the crappy OS!

---

### Post by CharlesA on 2012-02-02
Like I said, it all depends on what services you have running. SSH and VNC are the two most commonly cracked services on these forums. 

You didn't really provide us with much information in the OP - is this a desktop or server install? What services do you have running? etc.

Normally if you use a strong password and don't have any remote access software installed you are fine.

Please read this:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by Ms. Daisy on 2012-02-03
> **Ray Vanzant said:**
>  Suppose that someone hacked into an Ubuntu system... 
What measures have you put in place to prevent this part? Are you posing a hypothetical or do you truly believe that an experienced cracker is out there targeting your system? Do you believe this has already happened on your computer?  

If you're simply concerned about the potential, then the basic security wiki that CharlesA linked to is a good place to start to prevent someone hacking in. Then you can continue with Apparmor & the security sticky (I was going to provide links but really you should just read and implement all the stickies in the Security Forum).

You can make your Ubuntu desktop as vulnerable or as secure as you'd like.

---

