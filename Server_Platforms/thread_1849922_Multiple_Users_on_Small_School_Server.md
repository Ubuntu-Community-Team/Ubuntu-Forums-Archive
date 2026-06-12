---
title: "Multiple Users on Small School Server"
date: 2011-09-25
forum: Server Platforms
---

### Post by ricmat on 2011-09-25
Hello all, this is my first post, so I apologize if this is in the wrong forum.

I'm fairly new to Ubuntu, but have managed as a part time volunteer to get about 40 PCs running 10.04 at our small school (each one, more or less independent).  Currently, we have 3 identical logins on each PC (admin, teacher, student) and each account has access to different directories on a separate server PC (via a basic NFS setup).  Thus, students can log in on any computer and access their own files.  The disadvantage is that students can see / change / modify other students' files as well.

I know that it is possible, but don't know how to set things up so that students would each have a unique login, and have their own unique home directory loaded onto whatever PC they are actually using at the time.

If anyone could provide me with a simple solution to this, it would be greatly appreciated!  

Thank you all in advance.

---

### Post by Dangertux on 2011-09-25
You should look in to both openldap and samba. Both can do what you are looking for. I can provide more info later if you have questions at the moment I am on my cell phone though.

---

### Post by ricmat on 2011-09-25
> **Dangertux said:**
> You should look in to both openldap and samba. Both can do what you are looking for. I can provide more info later if you have questions at the moment I am on my cell phone though.

Hello Dangertux - I've been looking into ldap, but the docs I've come across all seem to tell you a lot of technical details, but with no examples.

What I'm looking for (and I hope it's realistic), are some simple examples to get me started.

When I needed to set up shared files on a server with NFS, I fortunately found a site that said "add this line to your export file, and this line to your fstab file".  I did it, and voila, it worked.  Perhaps it isn't quite that simple, but if someone could steer me to some examples (which include both server and client), that would be the most use to me!

Thanks!

---

### Post by SeijiSensei on 2011-09-26
If you're using NFS, the easiest solution is to install [NIS]("https://help.ubuntu.com/community/SettingUpNISHowTo") on the server and create user accounts for each user.  Once properly configured, each user can log in with his or her username and password and have the corresponding /home/user server directory [mounted]("https://help.ubuntu.com/community/SettingUpNFSHowTo#NIS") as that person's home directory.

---

### Post by Entilza on 2011-09-26
There is also NIS server/client that can share the password/group so you don't have to maintain multiple users.

Another one is a radius server which also does this.

Another option for your setup is LTSP which is a thin-client based  system where all the software runs on a server and sends the graphical destkop to the clients.  The client machines boot off the network card and have no operating system installed.  This way you only have to configure one machine.  This would also solve your user issue immediately because all users are setup on one machine.

I know these aren't examples of what you were asking for but hopefully it may steer you in the right direction.  Some of this is a bit complicated to setup so you might need some more help.

---

### Post by collisionystm on 2011-09-26
Use Zentyal with 10.04 or 10.10 clients. It is EASY EASY EASY to set up. You can install the Zentyal-Desktop client onto their machines that setups the ldap practically automatically.

[www.zentyal.com](www.zentyal.com)

---

### Post by collisionystm on 2011-09-26
I truly believe Zentyal is exactly what you are looking for. Its based on 10.04 server. It has a web interface and a lxde server gui. It is a firewall, internet gateway, mail, chat, and even a voip server. It also has the option for paid support. Its documentation is amazing and its support forum is great as well. Check it out, you wont be dissapointed!

---

### Post by ricmat on 2011-09-26
Thanks for the quick responses.

I"ll look at NIS and Zentyal.

If anyone has more ideas (or especially, examples of both server and client setup), please mention those too!

---

### Post by collisionystm on 2011-09-26
> **ricmat said:**
> Thanks for the quick responses.

I"ll look at NIS and Zentyal.

If anyone has more ideas (or especially, examples of both server and client setup), please mention those too!

I can use my company as an example. 

Zentytal server. 100 users.
Using for LDAP, SMTP for Printers to send scans, and file server.
It is also the PDC for Windows Xp and 7 boxes. It is also integrated with a few Ubuntu machines as well. Works great.

---

### Post by ricmat on 2011-09-26
> **collisionystm said:**
> I can use my company as an example. 

Zentytal server. 100 users.
Using for LDAP, SMTP for Printers to send scans, and file server.
It is also the PDC for Windows Xp and 7 boxes. It is also integrated with a few Ubuntu machines as well. Works great.

The key things I'm looking for are a centralized user login/database accessible from Ubuntu computers, and a "auto download of this user's home directory from the server when he logs in".

Is the Office version of Zentyal the right one to do this?

---

### Post by collisionystm on 2011-09-26
Okay so you are looking for an ldap controller and roaming profiles. Yes this box can do that.

[http://www.zentyal.com/en/server/download/](http://www.zentyal.com/en/server/download/)

---

### Post by ricmat on 2011-09-26
> **collisionystm said:**
> Okay so you are looking for an ldap controller and roaming profiles. Yes this box can do that.

[http://www.zentyal.com/en/server/download/](http://www.zentyal.com/en/server/download/)

In addition to the server installation and configuration, what needs to be done on the client?  I don't see anything on the web site about clients.

---

### Post by ricmat on 2011-09-26
> **collisionystm said:**
> Okay so you are looking for an ldap controller and roaming profiles. Yes this box can do that.

[http://www.zentyal.com/en/server/download/](http://www.zentyal.com/en/server/download/)

OK - I downloaded the server, and installed with default settings.  After I log in and select the software packages I want installed, I hit "save", and nothing happens.  I get no more menus, config options, nothing.

I'll try reinstalling tomorrow, but this isn't a good start :-(

---

### Post by david.garceau on 2011-09-27
Ill have a full step by step today on howto setup a Master ldap server, and then setup another server that acts as a domain controller and file server and authenticates to the ldap server. This way you can give permissions based on the ldap users also. Should be up some time today. This is using zentyal by the way.

---

### Post by ricmat on 2011-09-27
> **ricmat said:**
> OK - I downloaded the server, and installed with default settings.  After I log in and select the software packages I want installed, I hit "save", and nothing happens.  I get no more menus, config options, nothing.

I'll try reinstalling tomorrow, but this isn't a good start :-(

I reinstalled, and the server is probably doing the right thing.  It appears to be set up as an LDAP server.

It's not at all clear to me how to take standard Ubuntu 10.04 and force users to log into the LDAP server instead of it just using the local login credentials.

---

### Post by collisionystm on 2011-09-27
You need this

[http://trac.zentyal.org/wiki/Documentation/Community/ZentyalDesktop/Ubuntu](http://trac.zentyal.org/wiki/Documentation/Community/ZentyalDesktop/Ubuntu)

---

### Post by collisionystm on 2011-09-27
You make your user in the zentyal web interface.

Setup the client with that link I just gave you. Here it is again.
[http://trac.zentyal.org/wiki/Documentation/Community/ZentyalDesktop/Ubuntu](http://trac.zentyal.org/wiki/Documentation/Community/ZentyalDesktop/Ubuntu)

Then log out and now login with the account you made in Zentyal.

---

### Post by collisionystm on 2011-09-27
Oh and BTW, the white box shortcut on their desktop is just a link to their Personal home directory on the server. So they can store things remotely.

---

### Post by ricmat on 2011-09-27
> **collisionystm said:**
> Oh and BTW, the white box shortcut on their desktop is just a link to their Personal home directory on the server. So they can store things remotely.

Thanks for the extremely detailed information in your last post.  It will take me a while to absorb it all, but it looks like it just might be the answer...... :-)

---

### Post by collisionystm on 2011-09-27
> **ricmat said:**
> Thanks for the extremely detailed information in your last post.  It will take me a while to absorb it all, but it looks like it just might be the answer...... :-)


I firmly believe it is the answer! It is a great piece of software.

Dont worry, just look at Zentyal documents if you have questions or hit up their forums. They are all very friendly and eager to help.

---

### Post by ricmat on 2011-09-29
> **collisionystm said:**
> You need this

[http://trac.zentyal.org/wiki/Documentation/Community/ZentyalDesktop/Ubuntu](http://trac.zentyal.org/wiki/Documentation/Community/ZentyalDesktop/Ubuntu)

When I try to get the zentyal-desktop package referred to in this document, there's a message failed to fetch 403 forbidden.  It won't download.  Any ideas?

---

