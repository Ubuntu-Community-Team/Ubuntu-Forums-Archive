---
title: "Secure File Transfer"
date: 2010-02-04
forum: Security
---

### Post by cal2600 on 2010-02-04
I would like to set up a dedicated box to send and receive files that are too large to send by email, securely. If I need to get a file to someone I could place it on the server and somehow automate an email telling them there is a file available. They could login to the server based on their email address and a randomly generated key combination and down load the file.
I also need it to preform the same function going the other way. Login into my server and place files going to me.

Is there anything or combination of things I can put together to accomplish this.? 

Thanks for the advise.

---

### Post by bodhi.zazen on 2010-02-04
Sounds as if you need ssh + a mail server.

ssh can transfer files over scp, and there are windows clients, such as WinSCP.

On linux you can use sftp and sshfs with a ssh server as well.

Just be sure to secure your ssh server (denyhosts / fail2ban , user ssh keys).

---

### Post by Lars Noodén on 2010-02-05
> **cal2600 said:**
> I would like to set up a dedicated box to send and receive files that are too large to send by email, securely. If I need to get a file to someone I could place it on the server and somehow automate an email telling them there is a file available. They could login to the server based on their email address and a randomly generated key combination and down load the file.
I also need it to preform the same function going the other way. Login into my server and place files going to me.

Is there anything or combination of things I can put together to accomplish this.? 

Thanks for the advise.

As mentioned above, SSHFS is an option for many systems, including linux.  It uses SFTP, too.  SFTP clients might be easier to work with than SCP or SSHFS: Filezilla, Nautilus, Konqueror, Dolphin, Fugu, and Cyberduck, to name a few.  

You might want to lock down the storage area with chroot, using the **ChrootDirectory** configuration directive, which is available in recent versions of openssh-server. 

The drop box might be done about the same way, but be sure to set both umask and the sticky bit so that users cannot read or write files that are not their own -- if each user has their own account.  If they share an account, as in the next paragraph, then I guess chrooting to subdirectories according to their name is an option.

As far as using the e-mail as a login, that's not quite possible, nor is it practical for you to keep adding new accounts.  There might be a good work-around by taking advantage of the fact that ssh **ForceCommand** will put the original program name into the environment variable *$SSH_ORIGINAL_COMMAND*.  It might be possible to find a way to chroot based on the value of that variable.

As far as the randomly generated passwords, there are kits like [donkey](http://packages.ubuntu.com/karmic/donkey), [otp](http://packages.ubuntu.com/karmic/otp) and [opie](http://packages.ubuntu.com/karmic/libpam-opie).  I guess those would work through PAM, but there should be a cross-platform option, too.  A draw back to the OTP use is that if you give out one password and the user flubs the transfer, he has to beg for a new one.  But if you give out more than one, you have to keep track of the unused ones.

---

