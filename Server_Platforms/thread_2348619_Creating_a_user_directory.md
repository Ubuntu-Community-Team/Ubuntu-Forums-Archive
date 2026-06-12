---
title: "Creating a user directory"
date: 2017-01-05
forum: Server Platforms
---

### Post by jaygtel on 2017-01-05
Hi, 

I realise that this is a super nooby question but I am just starting to learn how to maintain and administer ubuntu servers.  I have a VPS with Ubuntu 16.04 installed that I am using this as a lab environment and I have it set up to the point where I can ssh into my server and navigate around.  The next thing I want to do is to create an active user directory (or whatever the linux equivalent is) so that I can authenticate user logons via my server rather than a local client.

I currently have Plesk Onyx installed.  Is this something I can do from within Plesk or do I need other software.  If I need other software, what software do I need to use?

Thanks 

Jay

---

### Post by darkod on 2017-01-05
Just to be clear, you want to create user or just a directory? By default, creating a user creates a home folder for it and that is where ssh session will get the user.
You create new users in ubuntu server with:
```
sudo adduser <newusername>
```
It will ask you for a password for the new user and full name. The rest you can ignore.
After that the user can log in using the password you gave it.

---

### Post by jaygtel on 2017-01-05
Hi, 

Thanks for your reply.  I am not sure that I was quite clear before, as I said I am pretty much just learning how to administer Linux servers, thats why I have a VPS that I am using as a lab environment so that it wont matter if I screw it up (its mine so I can just do a reinstall image and set everything back to a fresh install if I screw it up).

What I was kind of after is a client/server environment.  I want to log into a client machine and have the login authenticated by the server and then have the home directory and all its files stored on the server rather than on the local client machine.

Sorry for the confusion, hope that I have now better explained what I want to do.

Thanks 
Jay

---

### Post by TheFu on 2017-01-06
You want to use LDAP.  PAM is extremely flexible, so be certain you don't lock yourself out. This is not a trivial thing to setup. I've done it a few times and things change enough that I have to look it up every time a new system has to be added to the network. 

In a corporate environment, people use MS-AD or FreeIPA (on CentOS/RHEL) for this stuff.  In the olden days, we used NIS, but since that has security holes large enough for 50 trucks to blow through, we don't do that anymore.

For having user HOMEs on a server, use autofs and NFS. This method has been around for 30+ yrs.  Let me see if I can find a how-to.
[https://serverfault.com/questions/69103/how-to-do-central-home-directories-and-user-accounts-on-ubuntu](https://serverfault.com/questions/69103/how-to-do-central-home-directories-and-user-accounts-on-ubuntu)
[https://ubuntuforums.org/showthread.php?t=2246705](https://ubuntuforums.org/showthread.php?t=2246705) is a prior thread about this with examples, scripts, etc.

I've never used Plesk - only been a Unix/Linux admin since 1995. There are lots of things I've never seen.

---

