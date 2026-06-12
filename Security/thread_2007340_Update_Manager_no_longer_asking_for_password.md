---
title: "Update Manager no longer asking for password"
date: 2012-06-20
forum: Security
---

### Post by taylorkh on 2012-06-20
Ubuntu 12.04 32 bit on a Dell Latitude 2100. New install, not an upgrade. gnome-session-fallback installed. Yesterday I noticed that Update Manager had launched and was sitting on the lower panel as a result of its daily check for updates. When I told it to install updates it did NOT ask for my password as (I think) it used to. Same thing happened today so I was not imagining things. 

I am in the process of building a virtual machine in VMWare to try and duplicate the issue. Has anyone else seen this?

TIA,

Ken

---

### Post by spynappels on 2012-06-20
I believe it does not ask you when updating your installed apps, but it will when you install new packages or updating important core packages.

---

### Post by CharlesA on 2012-06-20
I just checked on my 12.04 desktop box, I could run update manager and check for updates without my password, but as soon as I hit install, it prompted for my password.

---

### Post by taylorkh on 2012-06-20
Thanks CharlesA,

10.04 required the password just to CHECK for updates. Starting with a later release one could check for updates but needed to authenticate to INSTALL updates. In my case I can install updates without authentication. 

The VM is complete and does not exhibit this performance. On the physical machine I had done a few tweaks to remove the list of users from the login screen (require full credentials), removed guest account but that is about it as far as security related items I think.

One other thing... I was running an application in wine both times when I was able to install updates w/o authentication. I will install wine and the app in question on the VM and see if that has any effect.

Ken

---

### Post by cariboo on 2012-06-20
The default behaviour in 12.04 is to update already installed packages without a password, if new packages need to be installed, you will be asked to enter your password.

---

### Post by CharlesA on 2012-06-20
Installing Wine shouldn't have any affect on authentication. Check here:
[http://askubuntu.com/questions/74439/how-to-make-authentication-required-to-install-updates](http://askubuntu.com/questions/74439/how-to-make-authentication-required-to-install-updates)

EDIT: Thanks Cariboo. :)

---

### Post by Cavsfan on 2012-06-20
> **cariboo907 said:**
> The default behaviour in 12.04 is to update already installed packages without a password, if new packages need to be installed, you will be asked to enter your password.

Good to know! I was wondering the same thing myself when I stumbled upon this thread.

---

### Post by taylorkh on 2012-06-20
Thanks all. I have spent the last several days working on a CentOS 6.2 build on my big desktop PC. The two monitors with separate panels configuration which I am using in Ubuntu 10.04 has been busting my butt. It does not work in Ubuntu 12.04 nor Mint 13. I finally have it working reasonably in CentOS. But when I restore a Clonezilla image to my new SSD it will not boot unless I have remembered to remove the existing partitions before hand. (which I often forget)

When this Update Manager thing popped up... not something I needed to deal with at the moment. 

I do not agree with Canonical on this one. But then I don't agree with them on Unity or some other things. That is why I am moving to CentOS on my desktop (and perhaps on the Ubuntu 12.04 netbook when I have time to custom build the wireless driver).

Again, thanks to all for your input. I will stick a fork in this thread and mark it solved.

Ken

---

### Post by t.h.w. on 2012-11-22
> **cariboo907 said:**
> The default behaviour in 12.04 is to update already installed packages without a password, if new packages need to be installed, you will be asked to enter your password.

Hi,
How can I change this? I want Ubuntu to ask for authentication also when updating packages. I think it is a security hazard if no authentication is needed, or am I wrong? :confused:

---

### Post by CharlesA on 2012-11-22
> **t.h.w. said:**
> Hi,
How can I change this? I want Ubuntu to ask for authentication also when updating packages. I think it is a security hazard if no authentication is needed, or am I wrong? :confused:
Not a security risk. It would only update packages that are already installed. If you try to install something new, you will still be prompted by your password.

If you are worried about other people getting on your computer, lock the screen when you step away.

---

### Post by cariboo on 2012-11-22
> **CharlesA said:**
> Not a security risk. It would only update packages that are already installed. If you try to install something new, you will still be prompted by your password.

If you are worried about other people getting on your computer, lock the screen when you step away.

Or better yet, log out, and let the other people use the guest account.

---

### Post by Jpeterson on 2013-01-09
I don't like it personally.  I like things to require my attention.  Makes me feel important.  Which is especially useful when you're short like me.

Is there a setting or conf I can adjust that would require pass auth on the update process?

Thx!
Jared

---

