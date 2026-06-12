---
title: "Remote server mgmt"
date: 2011-09-19
forum: Server Platforms
---

### Post by DRouleau on 2011-09-19
I'm new to Ubuntu 11.04 (coming from CentOS, wanted to upgrade but the server doesn't have DVD drive so I'm going to give this a shot) and I'm trying to figure out what is going to be the best choice to to set up remote mgmt for this server.  I've tried to install the webadmin and it fails on the apt-key add part so it looks like that isn't going to be an option.  Plus I don't really care about having a gui anyway as I did 98% of my work in CentOS from the terminal anyway.
If you believe the webadmin is going to be the best choice I'll write down the error and we can try and figure out what's going on :rolleyes:
Thanks in advance!

---

### Post by AlexDudko on 2011-09-19
If you don't care about terminal - ssh would be the best choice.

---

### Post by haqking on 2011-09-19
> **DRouleau said:**
> I'm new to Ubuntu 11.04 (coming from CentOS, wanted to upgrade but the server doesn't have DVD drive so I'm going to give this a shot) and I'm trying to figure out what is going to be the best choice to to set up remote mgmt for this server.  I've tried to install the webadmin and it fails on the apt-key add part so it looks like that isn't going to be an option.  Plus I don't really care about having a gui anyway as I did 98% of my work in CentOS from the terminal anyway.
If you believe the webadmin is going to be the best choice I'll write down the error and we can try and figure out what's going on :rolleyes:
Thanks in advance!

best tool for remote admin on any Linux Server is IMO ssh.

[https://help.ubuntu.com/10.04/serverguide/C/remote-administration.html](https://help.ubuntu.com/10.04/serverguide/C/remote-administration.html)

and here is some info about webmin [http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/](http://www.kelvinwong.ca/2010/05/22/installing-webmin-on-ubuntu-server-10-04-lts-lucid/)

ssh is the number 1 tool for secure remote admin though IMO

---

### Post by DRouleau on 2011-09-19
I'd be connecting to this from a windows PC, would I use something like TightVNC like I had before to "remote the terminal", or is there something better or something else that I would need to use?

---

### Post by haqking on 2011-09-19
> **DRouleau said:**
> I'd be connecting to this from a windows PC, would I use something like TightVNC like I had before to "remote the terminal", or is there something better or something else that I would need to use?
 
 using Windows you can ssh with putty [http://www.putty.org/](http://www.putty.org/)

VNC is insecure.

from the TightVNC webpage: [http://www.tightvnc.com/faq.php](http://www.tightvnc.com/faq.php)

**How secure is TightVNC?**

        Although TightVNC encrypts VNC passwords sent over the net, the rest of the traffic is sent     as is, unencrypted (for password encryption, VNC uses a DES-encrypted challenge-response     scheme, where the password is limited by 8 characters, and the effective DES key length is 56     bits). So using TightVNC over the Internet can be a security risk. To solve this problem, we     have plans to implement built-in encryption in future versions of TightVNC.   
        **In the mean time, if you need *real* security, we recommend installing an SSH server,     and using SSH tunneling for all TightVNC connections from untrusted networks.**

---

### Post by DRouleau on 2011-09-19
I've got something things I need to do, but I'll give the SSH and putty a shot.  I'll let you know if I have any further questions/problems. Should be about 2 - 3 hours if all goes well with my other project.

---

### Post by CharlesA on 2011-09-19
If you do go the SSH route, check out screen, which is a terminal multiplexer. I've found it invaluable for running stuff in the background when I am not connected.

---

### Post by DRouleau on 2011-09-19
Outstanding, didn't have to do any additional configuration for putty other than having the SSH "stuff" installed of which I did when I set up the server.  One of these days I'll get back to getting the web admin to work now that I don't have to sit in the server room to do it.
Thanks guys!!!

---

### Post by Lars Noodén on 2011-09-19
> **CharlesA said:**
> If you do go the SSH route, check out screen, which is a terminal multiplexer. I've found it invaluable for running stuff in the background when I am not connected.

tmux is nice, too.  It's a bit simpler.

---

### Post by CharlesA on 2011-09-19
> **Lars Noodén said:**
> tmux is nice, too.  It's a bit simpler.

Good point. It didn't work for what I wanted to do, but it's still a fair bit easier to deal with.

---

### Post by haqking on 2011-09-19
> **DRouleau said:**
> Outstanding, didn't have to do any additional configuration for putty other than having the SSH "stuff" installed of which I did when I set up the server.  One of these days I'll get back to getting the web admin to work now that I don't have to sit in the server room to do it.
Thanks guys!!!

No problem, you are very welcome.

remember to mark this thread as solved using thread tools if you feel it is.

Cheers and enjoy ssh ;-)

---

### Post by DRouleau on 2011-09-20
> **haqking said:**
> No problem, you are very welcome.

remember to mark this thread as solved using thread tools if you feel it is.

Cheers and enjoy ssh ;-)

Thanks, was trying to figure out how to do that...

---

