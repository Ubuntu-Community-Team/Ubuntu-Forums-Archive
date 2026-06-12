---
title: "precise ftp issue"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by crookiecookie on 2012-04-04
I had server installed on 11.10 with ehcp installed
ftp to my computer worked fine
i fresh installed precise installed server and ehcp as normal

Now when i connect to my computer from ftp i get 

Response libgcc_s.so.1 must be installed for pthread_cancel to work

---

### Post by cariboo on 2012-04-04
Do you have the  libgcc1 package installed?

---

### Post by crookiecookie on 2012-04-04
I do but just checked to make sure and said upgrade so i have

The problem is if i do it on net2ftp i get this error


The error occured in file /var/www/new/ehcp/net2ftp/includes/filesystem.inc.php on line 64.
function ftp_openconnection (/var/www/new/ehcp/net2ftp/modules/browse/browse.inc.php on line 223)
function net2ftp_module_printBody (/var/www/new/ehcp/net2ftp/main.inc.php on line 313)
function net2ftp (/var/www/new/ehcp/net2ftp/index.php on line 59)
argument 0: printBody


And if i try with filezilla i get 

Response:	331 Please specify the password.
Command:	PASS **************
Response:	libgcc_s.so.1 must be installed for pthread_cancel to work
Error:	Could not connect to server

Like i say i had no problems with 11.10 with the ftp with ehcp
so i dont think it is ehcp related
and i did the install the same fresh ubuntu then ehcp
so must be precise settings.

Not sure what to do i can log on to local host or ip with annomanous user but cant access the folder locations i want to upload

Iam quit new to ubuntu only been using for about 1 month
just got past the stages of pulling all my hair at when you loose half your desktop LoL

---

### Post by cariboo on 2012-04-05
Is your server for public or personal use? If it's only for personal use, I suggest you install openssh-server on your server and use it instead of ftp. If you set up the ssh server with private/public keys, it is much more secure than ftp. Many ftp clients also support file transfers via ssh.

Have a look at the openssh-server howto [here]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html")

---

### Post by crookiecookie on 2012-04-05
iam not sure if this might be the issue
when i went to install openssh-server
it quoted it was already installed

With the easy hosting control panel it installs vfstpd and uses this instance to connect to the folders /var/www/vhosts/xxxxx

Iam thinking if this is conflicting software with both instances installed together

In 11.10 i did fresh install of ubuntu and straight away installed easy hosting control panel for best configurations

I did the same with 12.04

So was thinking if the new precise comes with openssh as standard
and the new vfstpd installed is conflicting.

---

### Post by cariboo on 2012-04-05
> **crookiecookie said:**
> iam not sure if this might be the issue
when i went to install openssh-server
it quoted it was already installed

With the easy hosting control panel it installs vfstpd and uses this instance to connect to the folders /var/www/vhosts/xxxxx

Iam thinking if this is conflicting software with both instances installed together

In 11.10 i did fresh install of ubuntu and straight away installed easy hosting control panel for best configurations

I did the same with 12.04

So was thinking if the new precise comes with openssh as standard
and the new vfstpd installed is conflicting.

I haven't installed 12.04 on my server yet, but previously you had to select what you wanted to install from tasksel, otherwise you just had a server with no services installed.

---

### Post by crookiecookie on 2012-04-05
sorry didint make say what i was using

iam using precise desktop 

when you install the easy hosting contol panel it installs
all the server apps automaticly 

never actually thought of giving taskel a go and see whats going on 
maybe might sort the problem out if i install from this method

---

