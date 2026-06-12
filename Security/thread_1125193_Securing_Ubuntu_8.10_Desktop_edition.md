---
title: "Securing Ubuntu 8.10 Desktop edition"
date: 2009-04-14
forum: Security
---

### Post by vectorm12 on 2009-04-14
Hi,

I'm gonna start off by apologizing as I am still fairly new to linux in general which means I might make a few mistakes along the way. I would also like to apologize in case there already is a similar post to this one but I have been unable to locate anything that deals with exactly my issues.

First off a little background information:

I'm running a Ubuntu 8.10 installation on a server in my company which will be running one specific application called Farmer's Wife which is basically nothing more than a scheduling database with a few extra features like invoicing etc.

The server basicly has to fullfill five requirements.

First of all and probably the highest security issue is Remote desktop via VNC(Login as well as access)
Today this is achieved with the built-in remote desktop feature and I am planning on using local hosts in order to futher increase security once everything is ready for production use however I guess there is more that could be done to increase security?

HTML hosting for internal/external access. The application has a built-in HTML server which has to function both internally and externally via NAT. 

Allow incoming and outgoing communication to clientsoftware externally via NAT as well as internally on a few specific ports. 

Ability to send mail via an internal mailserver as well as access internal/external FTPs.

Any other function is at this point not required. As I've understood it Ubuntu seems to be quite locked down already straight out of the box but I would really like to make sure the system is properly secured for production before I put it in use.

The reason why I chose the desktop edition instead of the server one is of course because of Gnome as I have a couple of server administrators who never saw a command-prompt in their lives.

Any tricks/hints/links to what I need to do to further secure the server would be most appreciated. Local security isn't an issue but external hacking is what is worrying me.

Thanks in advance/

Kris

---

### Post by Windsurfer619 on 2009-04-16
Like, you said, Ubuntu is pretty secure out of the box.
As for tips:
Turn off debugging on the webserver, as well as auto-indexing.
Make sure your FTPs are secure...
Turn off passwords for SSH.

Mostly just common-sense stuff.

---

### Post by AFarris01 on 2009-04-16
just FYI:*

You could've also installed a graphical environment on ubuntu server edition (via: "sudo apt-get install gnome"/"sudo apt-get install gnome-core"/"sudo apt-get install ubuntu-desktop" depending on how much extra stuff you wanted with the desktop(i'd use gnome-core)) but oh well...

As for security... I've seen a lot of things about using SSH tunneling for secure remote logins, but i'm unsure as to to impliment this, or of it would be better/worse than what you're already doing...may want to read a bit on that around the forums/net. just a thought!

Andrew

---

### Post by nowhere@cox.net on 2009-04-18
VNC is not a secure connection. To make it so you need to tunnel through ssh. There are plenty of guides in the forums if you search for vnc tunnel ssh.  

An alternative is to use nx. I use the free but closed source nxserver from nomachine.com. It is unbelievably fast compared to any vnc I have used and the traffic is encrypted without having to set up tunnels and such. I like it a lot.

You download the deb packages from nomachine.com and install server/node on your server and client everywhere else.

Good luck!

---

### Post by dtoronto on 2009-04-18
VNC is extremely insecure, I would not recommend using it.

> I've seen a lot of things about using SSH tunneling for secure remote logins

SSH is a highly secured and encrypted method for accessing the Shell from any remote location.  I would recommend getting rid of VNC for any server and using the Shell.

---

### Post by bodhi.zazen on 2009-04-18
I also advise ssh.

You can tunnel X over ssh if you must :

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

but once you learn you way around the command line there is no need.

Be sure to lock down your ssh connection as well.

[AdvancedOpenSSH - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH")

---

### Post by vectorm12 on 2009-05-13
Thanks for all the useful tips guys, I've now made sure the SSH is properly locked down but as far as remote desktop goes there really isn't any need to secure this portion as all VNC sessions will be on our closed network.

---

