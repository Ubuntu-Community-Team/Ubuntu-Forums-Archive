---
title: "Bug? Aptitude crashes network during ssh session"
date: 2006-06-16
forum: Server Platforms
---

### Post by Jeruvy on 2006-06-16
I don't have a lot of details other than it's a default LAMP server installation.  I only upgraded to get OpenSSH server installed so I could do ssh over the LAN.  This works fine, and was getting mysql up and running.

However I ran into a snag trying to copy files over to the server, the SCP client would simply hang.  I'd get about 5k to 50 k depending, and it would simply hang up on my desktop.

I decided to try to install a ftp server so I could move the files on this way and was logged in via putty onto the server.  

Running Aptitude was a little trashy so I fiddled with the settings in putty till I got it decent.  Navigating in Aptitude was a bit sluggish but it was working fine until I decided to hold down the arrow key and the entire putty client disengaged from the network, and after a few more seconds I received a 'lost connection' message.

At this point I could not get the server back up on the network without a lot of headache and voodoo with ifup and ifdown.

I attempted to repeat this and did so successfully.

I'm not certain if it's a bug or something I was manifesting via putty.  I'm hoping someone has a explaination since I'm at a loss for one.  I can see clients crashing and taking the connection down, but taking the entire adapter down with the session...?

TIA.

J.

---

