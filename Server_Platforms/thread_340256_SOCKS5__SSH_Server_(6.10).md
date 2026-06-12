---
title: "SOCKS5 / SSH Server (6.10)"
date: 2007-01-16
forum: Server Platforms
---

### Post by ThatOtherGuy435 on 2007-01-16
Hello all!

I used to use my WinXP box running OpenSSH for Windows, and SOCKSPuppet as a Socks 5 server, to bounce my laptop connection off while roaming.

The setup was the OpenSSH port open to the world, connect to it with Putty, loopback a port through Putty and the SSH to Localhost:port where the SOCKS5 server was running.

I can't for the life of me figure out how to get a SOCKS 5 server running in this same configuration on Linux, and it is fairly essential to the switch from WinXP - So I would most certainly appreciate any insight!

I have tried to get dante-server working, but the documentation is... slim, to say the least, and I can't figure it out for the life of me!

-ThatOtherGuy

---

### Post by kjacks on 2007-01-17
I think I know what your asking.  I do the same thing with my Ubuntu 6.10 server.  I open an SSH session to my server and tunnel all internet traffic thru that tunnel.  Here's a guide I used so let me know if this sin't what you were doing:
[http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/](http://thinkhole.org/wp/2006/05/10/howto-secure-firefox-and-im-with-putty/)

If that is what your looking to do it's very easy.  I got that part up and running in 3 commands.  After installing Ubuntu Server 6.10 I created a user, password, and installed openssh.  Everything worked 100% at that point.

#sudo su
#passwd
#apt-get install openssh-server

As long as your followed the tutorial (above) correctly it should work.  No need to install a special socks5 server or anything.  

Hope this helped.

---

