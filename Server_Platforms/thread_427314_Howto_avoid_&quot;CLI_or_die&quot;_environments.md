---
title: "Howto avoid &quot;CLI or die&quot; environments"
date: 2007-04-29
forum: Server Platforms
---

### Post by ZenSpirit on 2007-04-29
Hi all ...
I'm a nurse and used to work on an IT-desk in a hospital.
I whas some kind of liason officer between IT and the medical department.
While working there i picked up quit some SysAdmin stuff, but all on Windows, and a little AS/400 :)

We had a nice setup.
Windows server running active directory with all users, printers etc.
Exchange server, IIS, database whas Oracle, ... .

Because of abuse, we implemented a strict user policy.
Our desktop users all had roaming profiles.
Did'nt matter what desktop they used, they always had they're standard desktop with icons, background, network shares, applications in the windows start menu, ... .

So, it whas a 100% windows network with all bells working :)

Now i'm trowing myself in the Linux world.
Not for the free beer (however :p ), but mostly for the free speach.

Currently i'm self employed, running my small home business.
Besides the health care stuff, i'm doing the IT stuff for some schools, NGO's, non-profits, ... .
It used to be windows, but after lots off talking, showing (mostly desktop) examples, i'm getting questions for Linux.
On the desktop not so mutch of a problem, its the server side that i'm having questions.
and by server i do not mean the usual LAMP setup.
But how do i get an equivalent of a Windows network as described above, but with Open source products.
I know Red Hat and Novell have some good stuff, but i keep getting flashes of "vendor lockin" true my mind. Being paranoi?

I have been looking on quit some sites, forums, ... .
But everything is very desktop or LAMP minded.
What is the Linux version for a active directory? How do i give a user on a Ubuntu workstation a choice for every networkprinter, without installing them on every single dekstop? How do (roaming) profiles work in Linux? How do i setup a file server? ... ?

So, where is "THE" Linux network/server admin guide for newbies on the internet? :))
Where can i ask question without being shooted by those "CLI or die" goeroes??

Let the tips come!
thanks in advance,
Johan.

---

### Post by coxy on 2007-04-29
Hello!

For a file sever you can use either NFS or Samba. Use Samba if you need Windows boxes to connect to the file server. Samba will also run your printers. Open LDAP might be worth a look for network logins and authentication.

Roaming profiles I have no idea about in the Linux world.

I hope that is of a little help. If you do a search on the forums there is a ton of info on Samba.

---

### Post by nodanero on 2007-04-29
For roaming profiles use the home from the sever with nfs.

---

### Post by chalex on 2007-04-29
Some components you want to look at are OpenLDAP (or RH Directory server) and maybe Kerberos.  Samba or NFS for the fileshares.

---

### Post by bkrist on 2007-05-04
You might want to check out Clark Connect ([www.clarkconnect.com]("http://www.clarkconnect.com")). It is a server distribution which has most of what you're after with an easy browser based configuration. It's only limitation is that the community edition only supports 10 users.

I used the default install to set up a mail server and Windows Samba domain with very little Linux knowledge. Now I'm also migrating my desktops to Ubuntu and wanting to sort out roaming profiles for them...

Good luck

---

### Post by hartz on 2007-05-06
Hi there ZenSpirit,
Did you get your problems sorted out, eg Central Authentication, roaming profiles, move to Linux.

Have you considered a "thin-client" type setup.

Desktops run Linux, but with basically no software installed.
The user performs a remote-login in stead of a local login, the normal. Once you've shown the user how to log in remotely, and by not giving them a password to the local PC, you get good control: I.e they cannot log in or install software on the local PC at all, so the machine will not become deteriorated, etc. For this setup you just need something with enough memory to run X-Windows. CPU is of minimal importance, as is disk-space.

Authentication is "local" on the remote box into which the users log into.

All applications only need to be installed once - into the remote box.

Sharing disk space between machines is simple - use NFS if you need to access remote machines' disk drives.

Since the users log into the same machine from anywhere, the "roaming" profile is automatically achieved.

The only possible problem with this is that you may need a lot of ram on the central server if the users all run memory-intensive applications.  8 GB ram and quad-core processors supported on many new motherboards nowadays will go far to support a lot of users though.

---

