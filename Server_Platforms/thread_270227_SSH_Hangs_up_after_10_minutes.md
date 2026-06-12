---
title: "SSH Hangs up after 10 minutes"
date: 2006-10-02
forum: Server Platforms
---

### Post by panthera on 2006-10-02
SSH hangs up after 10 minutes. This is 10 minutes of activity.. 
I don't have a firewall on my ubuntu server. I tried setting up telnet, but it has the same problem -- after 10 minutes any connection is disconnected. 

What's weird is that the computer still thinks I'm logged in...
Please help :(
I need to be able to use the ssh for more than 10 minutes at a time.

---

### Post by sonic2000gr on 2006-10-03
This is strange behaviour... Have you changed any default setting in /etc/ssh/sshd_config ? Is your connection through the internet or a local network?

You may want to add the following to your /etc/ssh/sshd_config file:

```
ClientAliveInterval 300
```

This will send a keep alive packet every 5 minutes. This is an encrypted keep alive and cannot be spoofed.

```
TCPKeepAlive yes
```

This will make sure that when a connection is dropped, the "ghost" login will disappear after a while. 

Don't forget to restart the ssh daemon:

sudo /etc/init.d/ssh restart

---

### Post by panthera on 2006-10-03
I'm connected through the internet, and what you suggested didn't work :(
Could the problem have anything to do with sysctl?
(as in some setting that I can set through there)?? And if so, which settings from there would be applicable?

---

### Post by sonic2000gr on 2006-10-03
I believe it has something to do with your provider rather than your setup.
Could you try and ssh from a machine on your local network and see if it is any different?
I am running SSH for access from both LAN and Internet. I remain connected for hours through the LAN. I haven't tested this for the Internet.

---

### Post by panthera on 2006-10-03
I'm sitting right next to the server -- to runs through a router to my computer (the router also connects to the internet). 
It's not hanging up like at 1:10, 1:20, etc. but 10 minutes after I log in, so the computer must be doing it.. I have another server here as well, and do not have problems with it (of course, it's an older server running something other than ubuntu).

---

### Post by panthera on 2006-10-03
ok.. so I have made some progress!! :) I changed net.ipv4.inet_peer_maxttl from 600 to a higher number and was able to stay on longer -- however, it's kinda random -- the next time, right after I logged in, it hung up on me.. 
If you know anything about maxttl or minttl or any of the other inet_peer_.. please let me know what they mean!

---

### Post by panthera on 2006-10-04
please? anyone? I still have problems -- like it hangs up after inactivity and I don't know if it's related, but I think my inet_peer_ stuff is set wrong...

---

### Post by NetworkGuy on 2006-10-04
Can you connect to this computer via SSH from another computer on the same network and not have it disconnect?

My thought is it may be your router that is causing this.   I assume you are using port forwarding to forward SSH to your computer.  Maybe this is where the problem is.  Troubleshooting by trying to SSH from another computer on the same network and having it work for a long time would answer that question.

---

### Post by panthera on 2006-10-04
I don't quite understand .. I have the computers all hooked up into the same router.. there is no other "network" for me to try. However, I know that I can telnet/ssh to my old server without any problems and it doesn't hang up on me at all...
I don't know about port forwarding, I just installed ssh-server and tried to get it to work. I am not sshing to my computer, only from my computer to the server..

---

### Post by NetworkGuy on 2006-10-04
> **panthera said:**
> I'm sitting right next to the server -- to runs through a router to my computer (the router also connects to the internet). 


Sorry, I misunderstood this statement.

SSH isn't really my thing, but I would check the logs in /var/log  especially dmesg, messages and any ssh log to see if there is a clue as to why it stops working for you

---

### Post by panthera on 2006-10-04
I didn't see anything in dmesg. .. What bothers me is that it was exactly 10 minutes before I changed the sysctl's value. However, it was 10 minutes from when I logged in and I never saw mention of it in the logs either.
(I did a grep for date/time and couldn't find anything in the logs).

---

### Post by flabdablet on 2006-10-19
I've had some annoying after-10-minutes hangs when using the standard Ubuntu ssh client to forward ports to another machine on my LAN (which is running the standard Ubuntu ssh daemon).  They don't happen when I do the same job using putty (from the putty package) or plink (from the putty-tools package) instead of the standard client.

---

### Post by flabdablet on 2006-10-21
Scratch that.  The problem recurred tonight even though I was using putty on the laptop.

It seems to have something to do with traffic through the forwarded ports.  I'll see if I can generate a simple test case that provokes the thing reliably.

---

### Post by flabdablet on 2006-10-26
Scratch all of that.  I no longer think it's ssh's fault.

What I was actually doing to provoke the ssh hang was controlling a remote corporate Windows box via rdesktop.  The Windows box is set up to establish and maintain an outward ssh connection to my home Dapper server via the Internet, forwarding remote ports 3389, 5800 and 5900.  At home, I'd make another ssh connection from my Dapper laptop to the server via my LAN, with local forwarding for the same three ports.  I'd then run Terminal Server Client on my laptop, connect to localhost using RDPv5, and log on to the Windows box.  I was doing port forwarding in two hops this way because I hadn't yet worked out how to make sshd accept connections on forwarded remote ports from anywhere except localhost.

This worked OK, except that the remote desktop would regularly freeze up and stop responding to mouse and keyboard input.  Whenever it did this, the ssh session connecting my laptop to the server (the LAN leg) would lock up as well; the only way to shut it down was to close the gnome-terminal window I'd started ssh from.  As soon as I'd done that, rdesktop would exit with a complaint about a broken connection.  Establishing a new ssh session on the laptop was enough to get a working rdesktop connection back - I never had to tear down the connection from the Windows box to the server.  So I was pretty convinced that something bad was going on between my Dapper laptop and my Dapper server, and that it was ssh's fault.

I spent a lot of time messing about running endless streams of crap from /dev/urandom through forwarded ssh ports in an attempt to provoke the hang without involving rdesktop, and was unable to do so.

Finally I got a hint on some forum somewhere, and tried disabling gnome-screensaver for the duration of my rdesktop session.  Bingo!  No more hangs.

I still haven't worked out what rdesktop could possibly be doing on a forwarded port that would lock up my entire ssh client, and I don't know which tender spot rdesktop and gnome-screensaver are poking each other in.  But a simple pkill -19 gnome-scree before I start Terminal Server Client, and a pkill -18 gnome-scree after I'm done, and all is well!

I've since worked out how to make sshd allow me to use remoted ports directly from other machines, so I don't have to do the two-hops thing any more.  I'm still turning gnome-screensaver off before starting an rdesktop session though, because Bad Things happen if I don't; several times I've had to kill the Windows box's sshd process on my server and let the Windows end call back in before I can get rdesktop to work properly again.

---

