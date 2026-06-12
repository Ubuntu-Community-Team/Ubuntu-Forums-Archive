---
title: "Possible to host personal Proxy server off my PC for remote use?"
date: 2007-04-04
forum: Server Platforms
---

### Post by kromix on 2007-04-04
Ok so, I have Websense at work and everything gets blocked, is it possible for me to host a proxy server off of my ubuntu box @ home and access it from work at [http://whatever](http://whatever) so that I may browse the internets freely?    I am currently using [https://www.hidebehind.net](https://www.hidebehind.net) to get around but its sooo bloody slow I was thinking if I could host my own it would be super fast.... 

Im pretty sure you could with ubuntu but I don't know how........ I'd love to have my PC in use while i'm at work allowing me to view sites I can't see at work......

---

### Post by craigp84 on 2007-04-04
There is no 1 step, quick fix, but if you can stick out the below, it should get you up and running.

**On Your PC At Home**
[LIST=1]
[*]Setup sshd to listen on port 443. You can do this by adding a line reading **Port 443** to your **/etc/ssh/sshd_config** file
[*] You will need to reload the sshd config. Do this by typing **sudo kill -HUP `cat /var/run/sshd.pid`** (note the backticks) or maybe easier to: **sudo /etc/init.d/ssh restart**
[/LIST]

**On Your PC At Work**
[LIST=1]
[*]Download and install connect.c - Google for *ssh connect.c* there's clear docs on this on the web so i wont repeat here.
[*]**mkdir ~/.ssh** dir in your homedir if it's not there already. Remember to chmod 700 for security: **chmod 700 ~/.ssh**
[*]edit **~/.ssh/config** and add the below lines to it:

```
Host your.home.here.com
  ProxyCommand connect -H your.work.webproxy.local:8000 %h %p
  Port 443
```
Replace **8000** and **your.work.webproxy.local** with the port and hostname of your work's proxy. You can get this from your internet explorer configuration or something.

[*]**ssh your.home.here.com -D 127.0.0.1 7884** should establish a connection to your home PC when typed on your work PC. This also creates a SOCKS proxy available only from your work PC, on port 7884 (also won't show up in port scans by your IT dept :) )
[*]Configure your web browser to go through your new proxy...
```
Open firefox, Edit -> Prefs -> Advanced -> Network -> Connections (for firefox 2.0)
Edit -> Prefs -> Connections (for firefox 1.*)
```
[*]Choose Manual Proxy Configuration -> Type in Socks Host "127.0.0.1" and  port: 7884
[*]Hit ok and try browsing to a website.
[/LIST]

GAIM can be easily configured to allow your instant messaging over the tunnel, i'll leave configuring that to you though.

Consider donating to the OpenBSD folks who need cash and are the people behind OpenSSH.

I hope this helps you,

Craig

---

### Post by kromix on 2007-04-04
That surely does help but one thing, my computer at work is WindowsXP I guess I should have mentioned that?

---

### Post by Brazen on 2007-04-04
You could use privoxy or squid.  Also, be sure your resume is in order and up-to-date.

---

### Post by craigp84 on 2007-04-04
> **kromix said:**
> That surely does help but one thing, my computer at work is WindowsXP I guess I should have mentioned that?

You can download a bug-fix & feature upgrade pack for windows XP at [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Alternatively, if you don't have the balls for that, try downloading cygwin -> [http://www.cygwin.com/]("http://www.cygwin.com/")

-c

---

### Post by brentoboy on 2007-04-04
or, use openvpn

ubuntu has it in the repos.

you'll have to use the openvpn docs on their site to get it running, but both the client and server ends can work on linux or windows.

you rig it up on your server to "bridge" your network so that your work PC is "on" your home network, and then rig it so that your XP box considers the new "virtual network adapter" is the primary adapter, and all requests go out to your home PC encrypted.  (setting it up to become your primary adapter is part of the server config, not the client config.)

I'd give you better details, but I dont have it set up activly right now becuase I dont need it anymore.  I did need it for a while to manage a website from a college network that had FTP ports (among other things) blocked.

Rigg it up on port 443 like craigp83 said, and it shouldnt be blocked.

---

### Post by airtonix on 2007-05-01
nah man!!!! 
when he tells you to run ssh

he means use putty.....itsa ssh client for windows. get it nowwwww!!!!!

---

### Post by craigp84 on 2007-05-01
Yeah, turns out the newest versions of putty allow the -D switch. You just create a shortcut to putty.exe with the -D 7884 instead of playing around with .ssh/config and connect.c

Connect.c is called connect-proxy in the ubuntu archives, sudo apt-get install connect-proxy.

Brentoboy - you're on the colourful side of a legal state of mind. Quit the wacky backy.

-c

---

### Post by jonathan.lees on 2007-05-01
You can also install Apache on your home server and download a PHP Proxy script such as [http://whitefyre.com/poxy/](http://whitefyre.com/poxy/) Then you simply use any browser and point it to the proxy script.

---

### Post by craigp84 on 2007-05-01
Good shout jonathan lees

---

### Post by Spyplane on 2007-06-22
I just went through this setup and I did things a bit differently.

I simply wanted to browse freely from work by using my ubuntu server at home.  And here are the super easy steps I took.   First off, you need openssh-server installed and running.

All I did was install privoxy on my ubuntu server with all the defaults.  The defaults are nice because it only allows connections from localhost.  So:

$ sudo apt-get install privoxy


Then on my windows machine, I installed Tunnelier (which is free for personal use).   Once installed, it is much easier to get going than putty or ssh on cygwin.   

* In the Login Tab, set your login info for ssh as normal.  
* In the C2S Fwding Tab  (Client 2 Server Forwarding)
   Your added entry should be:

Status:   enabled
Listen Interface:  127.0.0.1    (your windows machine)
Listen Port:  <whichever port on your windows box you want to use>
Destination Host:  127.0.0.1   (since you are piped through ssh, the privoxy server is on localhost)
Destination Port:   8118           (default port for privoxy)

Once doing that, you just hit the login button and you are set.   Set your firefox proxy to be localhost on the port you picked above for Listen Port.

Also make sure you check in Tunnelier that zlib compression is on, it speeds things up a bit.

---

