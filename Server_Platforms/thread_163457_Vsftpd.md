---
title: "Vsftpd"
date: 2006-04-20
forum: Server Platforms
---

### Post by tbresson on 2006-04-20
Hi. I've searched around the web and found a lot of stuff about it, I read the examples and the forums etc, but I can't seem to find exactly what I'm looking for.

I want to use vsftpd in a scenario like this:

1 Admin
1 or more Users
No annonymous access
And the daemon should run as a service, not stand alone.

**THE ADMIN**:
The admin account should have access the all the harddrives. This I've handled by mounting all my drives in the homedir of the admin user. So far so good.

The admin account should have access to upload web content (/var/www). This I've handled by symlinking a dir from my home dir (www -> /var/www). 
Problem: To be able to do so I had to remove my user from a chroot jail and thereby potentionally put my server at risk (as far as I've read).

The admin is now the local user (the one user I added during installation of Ubuntu) but I've heard that's not a good idea, since the password sent to the server is in clear text when local_enable=YES. I want to avoid this if possible.

In short: The admin user should not be a local user, but should have access to all harddrives by mounts done in his home dir and should have access to upload webcontent to /var/www/ without compromising the chroot issue.

**THE USER(S):**
The user should should:
- only have read access
- perhaps have an upload dir ( that's common for all users )
- not be a local user
- have access to the folder/drive I choose

**SERVICE:**
I want to run the server in service mode, so I can sudo /etc/init.d/vsftpd stop in case the user(s) are using up all my bandwith. I tried limiting the amount of bandwith available to the logged on user, but I had to kill the process first before the conf was loaded again and this would cause the logged on user to be disconnected.

**HOW?**
The big question is: How do I do all of this??
a) How is the config supposed to look? Is there supposed to be 2 configs, one for the admin and one for the users?
b) How do I add more users and their homedirs? What rights are supposed to be set for the user to work properly?
c) How do you make the daemon work with init.d ?

I know this sounds big, but really, it's quite a normal sceanrio in my oppinion? You have a server and you (yourself) want complete access to it, but you don't wanna give out your password to your friends, so you make an account for them and give them access to download what you think they should have access to. And perhaps there's an upload dir so they can upload something to you, e.g. family photos from the last vacation or something else. But you don't want to whole world (annonymous) to watch what you have on your FTP. Right?

---

