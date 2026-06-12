---
title: "Office login question"
date: 2009-10-05
forum: Server Platforms
---

### Post by kevin11951 on 2009-10-05
Is it possible to have the following setup easily?

[LIST=1]
[*]Client gets a list of usernames that it can login as
[*]User enters username and password
[*]Client checks with server if the password is correct
[*]If correct, the client mounts an nfs share as the users home folder in fstab with the style of:
192.168.2.2:/var/home/$username/ /home/$username/ nfs defaults 0 0
[/LIST]

Is it easy to do, or even possible?

---

### Post by bab1 on 2009-10-05
> **kevin11951 said:**
> Is it possible to have the following setup easily?

[LIST=1]
[*]Client gets a list of usernames that it can login as
[*]User enters username and password
[*]Client checks with server if the password is correct
[*]If correct, the client mounts an nfs share as the users home folder in fstab with the style of:
192.168.2.2:/var/home/$username/ /home/$username/ nfs defaults 0 0
[/LIST]

Is it easy to do, or even possible?

If i get your drift correctly; yes,  it is possible,but not quite as you have laid it out above.



Let's get some terminology straight:[LIST]
[*]User = a human using a host
[*]Host = a computer that is either a client or server
[*]Client = a software entity that is a requester of a service
[*]Server = a software entity that is a supplier of services requested by client

[/LIST]

First thing is that the client workstation does not need to have a list of potential users.  Secondly the remote filesystem does not need to be mounted via fstab.

Here is the scenario:[LIST=1]
[*]the user enters his login and pass at the client host
[*]The server (LDAP or NIS) authenticates the user a the server
[*]The correct directory is mounted via script
[/LIST]

The point being that you don't need to alter fstab after authentication of the user to mount the correct filesystem.

You should decide how you want to manage the domain.  You can Use NIS (old school) or via LDAP (newer but more complicated). If you choose LDAP then you can use this for directory services on Linux: [**[COLOR="blue"]_http://directory.fedoraproject.org/_[/COLOR]**]("http://directory.fedoraproject.org/")

---

### Post by scorp123 on 2009-10-06
> **kevin11951 said:**
> Is it possible to have the following setup easily?

[LIST=1]
[*]Client gets a list of usernames that it can login as
[*]User enters username and password
[*]Client checks with server if the password is correct
[*]If correct, the client mounts an nfs share as the users home folder in fstab with the style of:
192.168.2.2:/var/home/$username/ /home/$username/ nfs defaults 0 0
[/LIST]  As the previous poster already noted: you want to look into LDAP.

Maybe you'd like to read this?
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

The article talks about Ubuntu 7.10 ... but it should all still be valid for 9.04 too. It may be though that a few config files have changed their location slightly.

If you want all that (the stuff that is discussed in the article, LDAP server, Windows Domain controller, etc.) but you want to have an easier-to-use way than having to type all those gazillion of commands, then please consider using a different Linux distribution for that job, e.g.

[http://www.opensuse.org](http://www.opensuse.org)

Don't get me wrong. I love Ubuntu. As desktop OS. But getting it to work as LDAP server and Windows Domain controller is a royal pain in the back. In SUSE I just click a few times with my mouse ("Run as Directory server? Yes!  *click* ...) onto the right buttons and it's all done and setup for me whereas getting the same config in Ubuntu requires manual editing of several files. And I am an experienced Linux user and Unix admin and even I find doing this in Ubuntu rather annoying ... :)

---

