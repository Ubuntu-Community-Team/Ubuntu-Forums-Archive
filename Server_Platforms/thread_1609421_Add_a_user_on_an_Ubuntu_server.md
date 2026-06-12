---
title: "Add a user on an Ubuntu server"
date: 2010-10-30
forum: Server Platforms
---

### Post by Strega on 2010-10-30
Hello,

I'm new to the Ubuntu Server OS. The version of my server is Ubuntu 10.04.1 LTS.

I've heard that for security reasons I should make and use a user instaid of using the root user. I'm planning on making Counter Strike Source servers, running an Apache webserver and an FTP server, so I will have to be able to make, edit and remove files and directories and also run them. How do I have to make such a user?

Regards,
Strega

---

### Post by abix_adam_pl on 2010-10-30
Just read carefuly what installer is telling to you. That is enough to cereate user with admin priviliges as you want.

Adam

---

### Post by CharlesA on 2010-10-30
The root user account is locked by default in Ubuntu.

The installer creates a user with admin rights.

If you want to create a user with no admin rights, just create the user with ***useradd*** and don't add them to the admin group.

---

### Post by Strega on 2010-10-30
Hello,

> **abix_adam_pl said:**
> Just read carefuly what installer is telling to you. That is enough to cereate user with admin priviliges as you want.

Adam

Well, the server is rented at [http://www.urgentvps.com/](http://www.urgentvps.com/) so it was already pre-installed. The only user that came with it was the Root user.

> **CharlesA said:**
> The root user account is locked by default in Ubuntu.

The installer creates a user with admin rights.

If you want to create a user with no admin rights, just create the user with ***useradd*** and don't add them to the admin group.

Somebody told me that using the Root user for installing stuff isn't secure, so I thought I should make another user who can do this so it needs admin rights. But then again I don't know how secure that is, so I actually don't know what I've got to do.

Regards,
Strega

---

### Post by CharlesA on 2010-10-31
> **Strega said:**
> Well, the server is rented at [http://www.urgentvps.com/](http://www.urgentvps.com/) so it was already pre-installed. The only user that came with it was the Root user.

Gotcha. :)

> Somebody told me that using the Root user for installing stuff isn't secure, so I thought I should make another user who can do this so it needs admin rights. But then again I don't know how secure that is, so I actually don't know what I've got to do.

It depends. As long as you have a **really** strong password on root, you should be ok.

I create a normal account that I use for everyday stuff. That account has sudo rights, so I can do admin stuff with it too. That's the way that works for me. Other people have different stuff that works for them.

---

### Post by lisati on 2010-10-31
> **CharlesA said:**
> 
I create a normal account that I use for everyday stuff. That account has sudo rights, so I can do admin stuff with it too. That's the way that works for me. Other people have different stuff that works for them.

That's similar to what I have as the main user on my server: the "normal" user created during installation that has "sudo" rights. None of the other "users" (created mainly for email purposes) have sudo rights. So far I haven't noticed any problems other than script kiddies looking for things I don't have installed and the occasional attempt to do a brute force guess of passwords using plain POP3 authentication (disabled on my machine)....

---

### Post by Strega on 2010-10-31
> **CharlesA said:**
> I create a normal account that I use for everyday stuff. That account has sudo rights, so I can do admin stuff with it too. That's the way that works for me. Other people have different stuff that works for them.

How do I create such an account with sudo rights? :D I don't really understand the adduser and useradd commands. :s

Regards,
Strega

---

### Post by msandoy on 2010-10-31
Hi.
Please read this manpage:
[http://manpages.ubuntu.com/manpages/jaunty/man8/adduser.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/adduser.8.html)
I have found adduser to be quite easy to understand.
Since the root user is already active, just make sure you have a really strong password on that account, and su into it when you need to use it.

---

### Post by Strega on 2010-11-01
Hi,

I looked into it but I'm really not sure what to do. I'm "scared" of doing something wrong. And just to know, is there really a danger of setting up a counter strike source server or ftp or apache with root? And if I add another user who can do this, isn't he sort of the same as root just with another name?

Regards,
Strega

---

### Post by CharlesA on 2010-11-01
> **Strega said:**
> Hi,

I looked into it but I'm really not sure what to do. I'm "scared" of doing something wrong. And just to know, is there really a danger of setting up a counter strike source server or ftp or apache with root? And if I add another user who can do this, isn't he sort of the same as root just with another name?

Regards,
Strega

If you are just installing software, you should be fine using the root account. If you use an account with sudo, however, an entry will be written to the auth.log with the command that was run.

Depending on how you have it set up, the service will either run under root, or under your current non-root account.

EDIT: When I add a user to a group, I use this command:

```
sudo usermod -a -G group username
```

---

### Post by Strega on 2010-11-01
> **CharlesA said:**
> If you are just installing software, you should be fine using the root account.

Also when this software is public, like a public Counter Strike Source server. I'm just a little afraid of it because some friend told me NOT to install anything with root.

---

### Post by CharlesA on 2010-11-01
> **Strega said:**
> Also when this software is public, like a public Counter Strike Source server. I'm just a little afraid of it because some friend told me NOT to install anything with root.

You need root access or access to sudo to install anything on linux. As long as you secure the root account, you'll be fine.

---

### Post by Strega on 2010-11-01
> **CharlesA said:**
> You need root access or access to sudo to install anything on linux. As long as you secure the root account, you'll be fine.

You might have noticed I'm a real noob at this, and I'm sorry for that :p But how can I secure this root account, and how do I make another account with sudo access? I've read the manpage but, I don't understand English well enough to really understand what they are saying in this manual.

Thank you :)

---

### Post by CharlesA on 2010-11-01
> **Strega said:**
> You might have noticed I'm a real noob at this, and I'm sorry for that :p But how can I secure this root account, and how do I make another account with sudo access? I've read the manpage but, I don't understand English well enough to really understand what they are saying in this manual.

Thank you :)
It'll be a bit more complicated since it's a VPS and I don't know if it has sudo installed or not, you can check by running this:

```
apt-get install sudo
```

To add a new user you just need to run:

```
adduser *username*
```

Then add them to the admin group:

```
usermod -a -G admin *username*
```

---

### Post by Strega on 2010-11-01
> **CharlesA said:**
> It'll be a bit more complicated since it's a VPS and I don't know if it has sudo installed or not, you can check by running this:

...

Then add them to the admin group:

```
usermod -a -G admin *username*
```

Sudo was already installed with the latest version and adding the username went well to, but when I tried adding the user to the admin group I got this error:
```
usermod: group 'admin' does not exist
```
Weird :s

---

### Post by CharlesA on 2010-11-01
> **Strega said:**
> Sudo was already installed with the latest version and adding the username went well to, but when I tried adding the user to the admin group I got this error:
```
usermod: group 'admin' does not exist
```
Weird :s

Just leave it in that case, VPS are set up a bit different from a normal server you install yourself.

As long as you are only using root to admin the server you are fine.

No need to make it more complicated.

---

### Post by Strega on 2010-11-01
> **CharlesA said:**
> Just leave it in that case, VPS are set up a bit different from a normal server you install yourself.

As long as you are only using root to admin the server you are fine.

No need to make it more complicated.

Ok, hopefully nobody will see a chance in hacking my VPS :) Thank you for the help!

---

### Post by CharlesA on 2010-11-01
> **Strega said:**
> Ok, hopefully nobody will see a chance in hacking my VPS :) Thank you for the help!

Like I said - as long as you have a strong password for the root account, you'll be fine. :)

---

### Post by msandoy on 2010-11-02
Ok, sorry for the late reply here, but basically, you need to be root to install counterstrike on your server. But after the install, you can use a "normal" account to run the server. So, after install, create a normal user, without sudo rights, for running the server. This is the safe way of doing it. Once root has installed the program, ordinary users can run the program.

---

### Post by Strega on 2010-11-02
What I did now was downloading and installing all the files with root, chowned the root dir of the servers to a normal user and started them with that user. I hope that is the safe way to do it :p

---

### Post by CharlesA on 2010-11-02
That'll work fine.

---

