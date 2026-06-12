---
title: "How much security do I need?"
date: 2010-07-07
forum: Security
---

### Post by nictu on 2010-07-07
Hi Folks,

I have been using the latest release of netbook remix for a few months now and my netbook is for performing non-essential tasks like browsing and e-mail and shopping

What I'm wondering is how much security do I need ? I thought that Linux was a lot more "attack proof" than windows, but do I still need to take precautions against viruses and maleware? Do I need to set up a firewall ? I am logged in as a user with admin privileges, never logged in as root. Should I log in as a 'normal' user without  admin privileges?

Any help and advice is much appreciated,
nictu.

---

### Post by Yarui on 2010-07-07
You should be logged in as a user with only the essential priveleges that is allowed to use sudo so that you can temporarily elevate privileges to perform administrative tasks.  This is the default behavior for your main account in Ubuntu.

You don't really need any antivirus or malware protection unless you really want it, but firewalls are always good.  If you have a firewall on your router, that should be sufficient.  Other than that the main thing you should worry about with regard to security is just to never install untrusted software and don't run untrusted scripts.

---

### Post by cariboo on 2010-07-07
If you are just running a default installation without any servers installed, you don't need to do anything. I personally turn on the firewall, using the default rules, when I'm out and about.

---

### Post by nictu on 2010-07-07
Smashing, thanks guys,

nictu.

---

### Post by bodhi.zazen on 2010-07-07
For mobile devices I encrypt the entire system + use ufw.

If I do online banking I tunnel over ssh.

---

### Post by listerdl on 2010-07-08
> **Yarui said:**
> You should be logged in as a user with only the essential priveleges that is allowed to use sudo so that you can temporarily elevate privileges to perform administrative tasks.  This is the default behavior for your main account in Ubuntu.

how do you tell if you have this enabled?

---

### Post by cariboo on 2010-07-08
> **listerdl said:**
> how do you tell if you have this enabled?

That's the way Ubuntu is setup by default.

---

### Post by Yarui on 2010-07-08
> **listerdl said:**
> how do you tell if you have this enabled?
Like Cariboo said, it's the default.  If you haven't changed it then it's enabled.  If you want to check you can find out by going into your terminal and typing something like.
```
sudo ls
```
If it prompts you for your password then it means you are a sudoer.  If you weren't a sudoer on your machine then it would give an error.  I chose ls because it's a simple command and all it does is lists off the contents of your working directory, and for the purpose of checking to see if you are a sudoer you can use any command.

To make sure your account only has basic priveleges try running an administrative command, like installing a piece of software with apt-get, without using sudo.  If you get an error it means you don't have priveleges to install without sudo, which is what you want.  If you do, by chance, end up able to install without sudo, then you will want to change the permissions on your account.

---

