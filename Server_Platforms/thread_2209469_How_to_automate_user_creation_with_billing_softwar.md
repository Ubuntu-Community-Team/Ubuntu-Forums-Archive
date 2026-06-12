---
title: "How to automate user creation with billing software"
date: 2014-03-05
forum: Server Platforms
---

### Post by Matt_Randall on 2014-03-05
Hi, 

I'm brand new here, but I've looked around everywhere without any success and I just need to be pointed in the right direction.  

I have a small cloud server setup and I want it to work with all the users on my current Ubuntu Server 12.04LTS.  I've got a plugin for the panel I'm using (OwnCloud) that imports existing users from my server automatically.  I just need a way to somehow automate user creation.  I'm looking to offer cloud services to some clients, and it would be amazing if I could have it automated.  I need a way for users to be automatically created on my server after a payment or order is received, so that the panel will import them to the cloud user base.  

I've experimented a bit with WHMCS and BoxBilling but I couldn't find anyway to automate user creation.  

Basically I'm looking for anyway to automate ubuntu server user creation whether it be from a billing panel or plugin, or just a standalone program.  Does anyone have any ideas?  

I don't have alot of experience with linux and I know I may be missing an easy work around to this problem, and I'd appreciate any help I can get from anyone.

Thanks in advance!

---

### Post by thnewguy on 2014-03-06
Usually this is a bad idea unless you have some good security in place as it opens the possibility for people to create accounts and, probably, access a shell on your server. Usually you don't want to do that. So make sure you have things like OpenSSH locked down before you enable automated account creation.

One way to approach this would be to have a server-side web script (perhaps written in PHP) which would call the "adduser" command on the system to create the new user. So long as the adduser script has the setuid bit enabled the script should be able to create new users, I think. Again, this is not really a good idea.

A better approach would be to find an ownCloud plugin which will allow users to sign up for accounts and just have a stand-alone ownCloud account rather than a system account. That would avoid a lot of security problems and avoid the need for system-wide user accounts.

---

### Post by DJ_Max on 2014-03-06
It would make more sense to use LDAP accounts than to have a bunch of clients with shell accounts on your server.

---

