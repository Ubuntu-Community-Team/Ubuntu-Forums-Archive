---
title: "Couple of questions about security."
date: 2009-06-03
forum: Security
---

### Post by uupreti on 2009-06-03
I am Redhat/Fedora/Centos user basically and I just moved to Ubuntu to give a try about one month ago. And I am just wondering about following question within myself. Can you guys clear me out?

I have fresh copy of Ubuntu 9.04 desktop installed. Now my questions are...

1. When I boot from Recovery mode, it asks me for root password to do everything like Maintainence, disk checking and everything. In ubuntu by default root account is not enabled. So what if I haven't enabled root and I want to check my filesystem or do some recovery work using recovery mode?? Can I do that using any Live CD??

2. What if I forgot root password? Is there any way to **reset root** password without using Live CD or using Live CD?

3. And I another thing is when I tried to shutdown and restart from terminal using normal account it says you have to be root but I can do same thing from GNOME environment. It will not ask me for root password. Does it make any sense for doing that?

4. When I login as a normal user first time , by typing **sudo su -** let me in as a root without any password. I couldnt' understand this feature too? :(

Clearification will be appreicated from Ubuntu Lovers.

Thanks

---

### Post by rookcifer on 2009-06-03
> **uupreti said:**
> 

1. When I boot from Recovery mode, it asks me for root password to do everything like Maintainence, disk checking and everything. In ubuntu by default root account is not enabled. So what if I haven't enabled root and I want to check my filesystem or do some recovery work using recovery mode?? Can I do that using any Live CD??

The root account is not enabled, but sudo is.  All you have to do is preface all of your root commands with sudo to achieve the same effect.  Or, if you don't like typing sudo every time, you can simply do:

sudo su -
password:

To get a root shell.

---

### Post by uupreti on 2009-06-03
> **rookcifer said:**
> The root account is not enabled, but sudo is.  All you have to do is preface all of your root commands with sudo to achieve the same effect.  Or, if you don't like typing sudo every time, you can simply do:

sudo su -
password:

To get a root shell.

No no no. I think we have misunderstanding here. I am in recovery mode and it is asking me for root password before doing anything. Now let's say I have an account **test** and password is **test123** but it is explicitly saying me to enter my root password and prompt is waiting for me to enter root password. If I don't enter root password, it will bring me back to same menu. 

FYI: I am using Ubuntu 9.04 Desktop version and I don't know what will happen to previous version.

---

