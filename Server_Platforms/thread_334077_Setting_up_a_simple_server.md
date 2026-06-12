---
title: "Setting up a simple server"
date: 2007-01-08
forum: Server Platforms
---

### Post by petesmithy1981 on 2007-01-08
Hi

I'm a youth worker and I have got 6 PC's and a server to use for the young people.  I want to know how to setup a server that enables young people to login on any desktop with their username and password and store stuff on the server.  I'd also like to allow broadband to be on them all as well.

Can any give me an idea where I should start? I feel very lost!

Thanks

Pete

---

### Post by wmatlock on 2007-01-08
Pete,

Look into edubuntu. Especially the server portion. You can set up the server to handle basically everything you want including boot the clients.

Rick

---

### Post by Brazen on 2007-01-08
Though I know nothing about edubuntu, I do know that it's goal is particularly to meet the needs of people such as you, so as wmatlock said, that would be a very good place to start.

I will tell you though, the service you are looking for is a domain controller, or PDC, with in the linux world is provided by Samba.  All this should be available on edubuntu and may even be easier to set up on edubuntu.

Basically though, what you want to learn more about is Samba and PDC.  This is what all distros will use for this, whether it is Edubuntu, Ubuntu, Debian, Redhat, Fedora, Mandriva, or SuSe, they will all use Samba to set up a PDC.

---

### Post by petesmithy1981 on 2007-01-08
ok so I here are a few questions I need to get my head round?

For edubuntu do i use ubuntu server on the server?
Do I put edubuntu desktop on all the PC's or is this part of the server installation?
what type of server do I need so that wen user's turn on the individual pc's the network login appears?

Sorry I'm rather new to all this and learning as I go along.

Thanks

Pete

---

### Post by Brazen on 2007-01-08
[Here]("http://www.edubuntu.org/Documentation") is the Edubuntu documentation.  I would start with the "Using Edubuntu" and "Getting Started" links.

---

### Post by braddcadd on 2007-01-08
[http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted) might help.  If you don't have the installation CD's you'll need to download the *.iso file and burn-as-iso like the page says.  If you already have the CD's you can skip the burning step.  

Your question depends on a lot of factors.  Here is some vocabulary to help you along:

_Diskless Thin Clients_ - This is a type of workstation.  All files on a "diskless" workstation will be sotred on the server.  A thin client is a workstation that uses a lot of resources from the server (maybe more than normal).

_Server_ - A server can be a file server, to store all files in a central location.  A server can also be an application server and/or a webserver.

---

