---
title: "Re: Restricting sudo users"
date: 2007-08-08
forum: Server Platforms
---

### Post by thusi02 on 2007-08-08
My problem is quite the complex problem. In short here is what I would like to accomplish. 

ServerA has three users: userA, userB, and userC. They all have sudo access to the machine. The machine has been setup completely with all the packages etc. 

The users each have a VERY sensitive file in their home directories. I would like to COMPLETE restrict it from one another seeing each others files as it contains their user information (dont ask why it does hehehe). since these users are sudo users I decided to restrict the sudoers file by the following: 

# Cmnd alias specification
Cmnd_Alias      KILL=/bin/kill,/usr/bin/kill
Cmnd_Alias      SU=/bin/su,/usr/bin/su
Cmnd_Alias      SHELLS=/bin/sh,/bin/csh,/bin/ksh,/bin/tcsh,/bin/bash

# User Privileges specification
userA,userB,userC ALL=ALL,!SHELLS,!SU

However, I am still not content with this as they can still do 'sudo -l /home/userA' find the file and than vi that file even though the home directories are set to 700 mod. I would like to restrict the user from sudo'ing to ANY shell however they should have the ability to install packages. Prevent the user from accessing ANY of the files in another users home directory by any means of sudo. Does this sound like an impossible thing to do. Can it be done? Your help on this would be MUCH appreciated. Please ask away if you have any questions from me. 

Thank you ever so much. 
Cheers, 
Thusjanthan Kubendranathan

---

### Post by foxylad on 2007-08-08
I would think carefully about giving all three users sudo rights - that basically gives them root access, and then trying to restrict that root access is the cause of your problem. 

I'd recommend taking a step back and looking at whether you can give the users the rights they need WITHOUT sudo, then none of them will be able to access each other's files.

Basically giving any user (apart fro the root user) sudo rights should set off warning bells - almost always it means you are going about things the wrong way.

---

### Post by thusi02 on 2007-08-09
That is true in most cases. However, when you are dealing in an environment that has many system administrators role it must be set this way as each person must have equal rights. So unfortunately I am faced with this dilemma still. Any thoughts?

Cheers, 
Nathan.

---

### Post by codmate on 2007-08-09
You can't hide anything from a root account.
Any user with sudo has root in effect.

A better approach IMO would be to have one sudo enabled account, which the three users have the password to, and have the three users use their regular accounts for everyday access.

This still won't hide the file(s) from the above users though. Like I said - if they have sudo, they have root; if they have root - they can see everything!

It sounds to me as if those 'user information' files should be in a different environment which the above users don't have access to at all.
Maybe even a different installation of Linux on the same machine that those people can chroot to, but don't have root access in?

---

### Post by bodhi.zazen on 2007-08-09
If it is a file I suggest encryption.

pgp may be helpful.

Encrypt:  gpg -c file

Decrypt:  gpg file.gpg
		
[http://www.linuxjournal.com/article/8732](http://www.linuxjournal.com/article/8732)

---

### Post by tjsullivan1 on 2007-08-09
It doesn't seem to me like multiple users should have sudo access to a machine. Even if they are all sysadmins, this leaves too much to chance. If one has the skills enough to be a sudoer, then he/she knows that the root password can be changed by the command sudo passwd root (Note this will change a root password). This means that even a chmod 700 on the file will still allow the other sudoers to view this file. If the file is so important that they must keep it, have them pu in on a flash drive.

---

