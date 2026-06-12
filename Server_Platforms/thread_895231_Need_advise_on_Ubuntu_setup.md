---
title: "Need advise on Ubuntu setup"
date: 2008-08-20
forum: Server Platforms
---

### Post by daggwood on 2008-08-20
Hi

I'm in the middle of setting up Ubuntu server addition and have a choice of what i want it to install. I need some advise on which ones I need to install. Choices are----

DNS Server
Lamp Server
Mail Server
OpenSSH Server
PostgreSQL database
Print Server
Samba File Sever

Which ones do I need to start with, Please help.

Thank you for your comments.

---

### Post by joebeasley on 2008-08-20
Start with openssh and Lamp.  That will give you Apache and mysql to play around with.

---

### Post by daggwood on 2008-08-20
Thanks. Thats what I ended up doing after suffering the net about it for a bit. One Question, is all of it done from command lines. I know you can add GUI but is the main program based on terminal work with command lines. Once again Thanks.

---

### Post by c2olen on 2008-08-20
Since you are installing the ubuntu server edition, you get a console by default.
You can add a gnome desktop yourself after the install, but for a server, this is not common use. It is your choice of course.

To install a basic GUI, just enter te following command in the console or terminal.

```

#>sudo apt-get install gnome (or another windows manager)

```


If you install gnome this way, you will get all the stuff you don't need on a server too, like evolution, office, and so on..

Usually, working in a commandline environment is pretty straightforward. I'd suggest to stick with that, and rely on our help to begin with. You'll get more comfortable with the CLI after a while.

Cheers

---

### Post by windependence on 2008-08-20
You will most likely not need a DNS server, unless you have hundreds of computers on your network. Running your own DNS server on a LAN is usually only useful on the inside of your network and not necessary for serving web pages.

-Tim

---

### Post by Iowan on 2008-08-20
I'd probably include the Samba server.  It lets you set up network storage  for Windows boxes (I access mine from this Ubuntu box, too).  Of course, it can be added later if/when you need another challenge.

---

### Post by daggwood on 2008-08-20
ok I got another question. The tutorials are all ways saying something about not loging into the root. what am I loging into when the system first boots up.

Thanks

---

### Post by c2olen on 2008-08-21
Could you give us an example of such a tutorial?


In your case, with the Ubuntu server, you are facing a terminal/console after initial boot.
Under normal circumstances (eg setup) you cannot login as root directly. It is not logging into root, but logging in as root. In case you don't know yet, the root user is the administrative user, which has super-user rights.
Normally, you will first need to authenticate yourself as an ordinary user, which has to be a member of the sudoers (super user do'ers) group in order to perform a command which needs super user rights.

This is more secure and prevents user mistakes in many cases.

---

