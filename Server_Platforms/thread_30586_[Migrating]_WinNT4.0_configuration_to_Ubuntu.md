---
title: "[Migrating] WinNT4.0 configuration to Ubuntu"
date: 2005-04-29
forum: Server Platforms
---

### Post by thavid on 2005-04-29
Greetings everyone.
I have a big issue here, and would like to hear your opinion.
So, it's like this... I've got an NT4.0 Server box that I would like to migrate to Ubuntu. This server is running IIS4.0 (with http, ftp and smtp relay) and it's structured like this:

there is a public ftp folder @ "d:\inetpub\ftproot". inside this folder there is another one named "users" where are the home folders of the ftp users (only it's user has access to it's own folder). inside it's user folder there is another folder named "http". this folder can be accessed via http, since it's linked to iis http (for example, let's say the user tux accesses via ftp to it's folder d:\inetpub\ftproot\users\tux\http and puts the file foto.jpg, the same can be accessed via http @ [http://serveraddress.com/tux/foto.jpg)](http://serveraddress.com/tux/foto.jpg)).

So the thing is, I want to have the same configuration in ubuntu. The users access via ftp to the server, manage their files in it's folders and have the "http" folder linked to the http server (apache???). They can only access their home dir's via ftp and their http folder can be accessed annonymously via http in the way it is currently ([http://serveraddress.com/userfolder](http://serveraddress.com/userfolder) -> d:\inetpub\ftproot\users\userfolder\http).

for the smtp part, I just want to relay from my windows desktop (smtp can only accept conenctions from LAN ip's), instead to connect to my isp's smtp server.

Any suggestions?

Thanks in advance  :wink:

---

### Post by wfx on 2005-04-29
Take a look on [http://www.apachefriends.org/](http://www.apachefriends.org/) 
I think it cant be easer to setup a webserver.

---

### Post by thavid on 2005-04-29
Yeah, that way it's easyer, but still, it won't give me any help of how to setup the ubuntu system the same way it's windows nt. If I was the only one using the machine, fine, but no, I've got several users here which are using my server to publish their files and personal folders. These users are already used to work with the system I've configurated, so when I start the migration, for the end user, the thing will be just like the same, with same folders and same http shares.

btw, some of the users are paying me for the server space, so I really got to leave this working the same way, with no changes on the folder structure, ftp access and http shares  :|

---

### Post by yanik on 2005-04-30
how about setting up a testing box?

---

### Post by flyinglizard on 2005-04-30
I would start with one of the following.

[http://httpd.apache.org/docs-2.0/urlmapping.html](http://httpd.apache.org/docs-2.0/urlmapping.html)

or

[http://httpd.apache.org/docs-2.0/misc/rewriteguide.html](http://httpd.apache.org/docs-2.0/misc/rewriteguide.html)

---

### Post by thavid on 2005-04-30
[QUOTE=yanik]how about setting up a testing box?[/QUOTE]

I'm doing all the test's in a VMWare Virtual Machine before deploy it in the real server, but still, I haven't managed to setup this testing machine to do what I've described in the first post

[QUOTE=flyinglizard]I would start with one of the following.

[http://httpd.apache.org/docs-2.0/urlmapping.html](http://httpd.apache.org/docs-2.0/urlmapping.html)

or

[http://httpd.apache.org/docs-2.0/misc/rewriteguide.html](http://httpd.apache.org/docs-2.0/misc/rewriteguide.html)[/QUOTE]

These links are dead  :? 
Can I get them elsewhere?

---

