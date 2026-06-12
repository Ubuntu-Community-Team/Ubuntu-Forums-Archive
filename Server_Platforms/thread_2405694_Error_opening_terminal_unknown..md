---
title: "Error opening terminal: unknown."
date: 2018-11-09
forum: Server Platforms
---

### Post by Stuperfied on 2018-11-09
Running webmin, has been find for months and now this.
Any help would be appreciated.

```
[user@host ~]# nano
Error opening terminal: unknown.
[user@host ~]# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial
[user@host ~]# nano
Error opening terminal: unknown.

[user@host ~]#
```

---

### Post by mixtutor on 2018-11-09
did you try something? 

```
docker exec -it id_container bash
apt-get update
apt-get install nano
export TERM=xterm
```

It looks like your "TERM" environment variable isn't getting set, since it's getting set when you run xterm, it may be a configuration issue with xfce-terminal, xfce-terminal probably has a configuration option to identify as certain terminal type, you should probably set it to "xterm".
Otherwise, you can manually set TERM in  ** ~/.bashrc** or **/etc/bash.bashrc** but this might cause you problems if you vt switch and run programs from the console.
Edit, also, you should do this in xfce-terminal and make sure things work afterwards:```
export TERM=xterm
```

---

### Post by slickymaster on 2018-11-09
*Thread moved to **Server Platforms**.*

---

### Post by Stuperfied on 2018-11-09
Need to go out for a bit at the moment but just wanted to ask, what is docker?

I don't think I have docker unless its a part of webmin, all I do is click on terminal in the web browser but i'll try what you suggested.

```
[user@host ~]# docker exec -it id_container bash
sh: 1: docker: not found
[user@host ~]# apt-get update
Ign:1 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge InRelease
Hit:2 [http://ppa.launchpad.net/certbot/certbot/ubuntu](http://ppa.launchpad.net/certbot/certbot/ubuntu) xenial InRelease
Get:3 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge Release [14.9 kB]
Get:4 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge Release.gpg [173 B]
Ign:4 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge Release.gpg
Ign:5 [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge InRelease
Hit:6 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge/contrib amd64 Packages
Get:7 [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge Release [14.9 kB]
Hit:8 [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge/contrib i386 Packages
Get:9 [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge Release.gpg [173 B]
Ign:9 [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge Release.gpg
Hit:10 [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge/contrib amd64 Packages
Hit:11 [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge/contrib i386 Packages
Hit:12 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Hit:13 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:14 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:15 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Hit:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Fetched 30.2 kB in 12min 1s (41 B/s)
Reading package lists...
W: GPG error: [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D97A3AE911F63C51
W: The repository 'http://download.webmin.com/download/repository sarge Release' is not signed.
W: GPG error: [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D97A3AE911F63C51
W: The repository 'http://webmin.mirror.somersettechsolutions.co.uk/repository sarge Release' is not signed.
[user@host ~]# apt-get install nano
Reading package lists...
Building dependency tree...
Reading state information...
nano is already the newest version (2.5.3-2ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 197 not upgraded.

[user@host ~]#
```

Didn't work.

> **mixtutor said:**
> It looks like your "TERM" environment variable isn't getting set, since it's getting set when you run xterm, it may be a configuration issue with xfce-terminal, xfce-terminal probably has a configuration option to identify as certain terminal type, you should probably set it to "xterm".
Otherwise, you can manually set TERM in  ** ~/.bashrc** or **/etc/bash.bashrc** but this might cause you problems if you vt switch and run programs from the console.
Edit, also, you should do this in xfce-terminal and make sure things work afterwards:```
export TERM=xterm
```

Didn't work either.

---

### Post by slickymaster on 2018-11-10
@Stuperfied:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output because if posted as plain text it loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand

---

### Post by TheFu on 2018-11-10
Respect to mixtutor, but those posts are making huge assumptions about your situation without any supporting facts.  You would know if you were using docker.  You are not.  You would know if you were running XFCE, so you probably are not.

If you are really new to Linux/Unix, running a pure server is a huge learning curve.  Might be better to begin with a desktop to get more familiar with the overall ideas.  How much experience do you have with Unix and Linux and Ubuntu in specific.  The answer helps us to respond appropriately.

I know nothing about webmin and wouldn't recommend it be used for many reasons, mostly security issues.

We need some facts before we can help.  Which Ubuntu release?  Is it Server or one of the desktop flavors?  Was it installed using official Canonical sources or from a VPS provider?

The prompts shown above don't match what is normally seen.  # means root.  $ means non-root, for example.

It isn't possible to open a GUI terminal on a server-only install that doesn't have a GUI.

The way I'd try to solve this is by using ssh into the server from a client machine.

---

### Post by Stuperfied on 2018-11-10
It is Ubuntu server with no gui and I have used desktop versions of ubuntu in the past, which I think were gnome and kde. Written some bash scripts to start and stop game servers however my knowledge of all the shell commands is still limited. I know basic stuff like how to grep, wget, apt-get but im learning more every day.

I have just tried jumping on the server directly as its in the room with me and found nano works when used directly on the server, however both nano and vi seem to have stopped working in the webmin terminal. 

Although I have used putty to ssh into routers during my networking course, I have never accessed a server via ssh. I am afraid this server is second hand also and so I do not have any console cables which might have been with it originally.

---

### Post by TheFu on 2018-11-10
ssh is a network protocol. I've never used it over a console cable or heard of it being used that way.

> I know nothing about webmin and wouldn't recommend it be used for many reasons, mostly security issues.
If you aren't an expert, please don't setup webmin.  It is just another set of attack vectors to have your server pwnd completely.  The only places I've seen webmin used successfully were where a senior admin set it up with the necessary security for specific user by jr. admins, and only the the 5 specific things that the sr. admin ok'd.  There's a reason why webmin isn't part of the Canonical package repos.

If you want to learn to manage Linux server, get used to using ssh and handle everything over ssh for the first few years.  After that, you'll want to move onto using a DevOps tool like Ansible, Puppet or Chef.
Once you have ssh working, you can edit any files you like with nano or better, vim.  I've never seen any router with nano on it, but all of them have some version of vi/vim.

Please answer the questions already asked.  What release? Where was the source of it?

As a last ditch effort to get webmin to allow nano to work, you could try setting the TERM=vt100  That is about the lowest terminal possible.  I don't recall if it had arrow keys.  Maybe a vt102 did?  IDK.

---

### Post by Stuperfied on 2018-11-11
Release:	16.04
For more details see my first post.

Source was my brother, this server actually belongs to him and im borrowing it whilst he's not in need of it. He got it for free and since then i've obtained another of my own. As for the O/S, its on USB and im not too sure but it may have come with the server. I'll ask him when I get a chance.

I have webmin installed because I thought you needed a console cable to plug into the servers console port in order to ssh into it. If that is not the case then maybe I can just use putty. I really only use webmin to allow my game server managers to administrate their games servers more easily and they do prefer a gui. The server is only used to run minecraft servers and so it's not a big deal if anything bad happens, its not a bank server.

I did try vt100 but nothing. Its like something other than the term variable which is required to run things like vi and nano got corrupted.

---

### Post by TheFu on 2018-11-12
ssh is a network protocol.
Serial cables are useful for servers that don't have a GPU while they are being setup/installed, but the first thing we install on those systems is ssh.  Then we go back to our Unix desktops and ssh into the server to configure everything.

Over ssh, you can run X/Windows programs through a secure tunnel.  **ssh -X user@server name-of-X-program**
If you don't take security seriously, you will be hacked and the server will be used for all sorts of nasty things to harm other people.

If you insist on using webmin, the best source for help is probably the webmin support forums.  But please, please, please, only allow access to webmin over either a VPN or through an ssh tunnel.  Do not allow direct access to webmin from the internet.

---

