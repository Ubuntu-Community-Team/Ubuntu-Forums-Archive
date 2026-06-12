---
title: "Do I have ssh running?"
date: 2011-11-03
forum: Security
---

### Post by Azrael84 on 2011-11-03
I tried ```
netstat -an | grep LISTEN | grep -v ^unix 
``` whilst reading the security sticky and got back 
```
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN  
```Does this mean I have a ssh daemon running and listening for connections? I use PuTTy to connect to other machines but I don't want connections to be made to my machine...

---

### Post by Dangertux on 2011-11-03
No it means the CUPS printing daemon is running. SSH is defaulted to port 22.

---

### Post by papibe on 2011-11-03
That does not mean anything related to ssh. 631 is the usual port for [CUPS]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu").

Did you install the ssh server? Check it like this:
```
apt-cache policy openssh-server
```
If it is installed, the output should be something like this (note the bold text):
```
openssh-server:
  **Installed: 1:5.3p1-3ubuntu7**
  Candidate: 1:5.3p1-3ubuntu7
  Version table:
 *** 1:5.3p1-3ubuntu7 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        100 /var/lib/dpkg/status
     1:5.3p1-3ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
```
To check if the service is running:
```
sudo service ssh status
```
If running you should get:
```
ssh start/running, process 769
```
If not:
```
ssh stop/waiting
```
To turn off the service:
```
sudo service ssh stop
```
And, if you want to uninstall it:
```
sudo apt-get remove openssh-server
```
Does that help?
Regards.

---

### Post by Azrael84 on 2011-11-03
Thank you both very much.

I got ```
 ssh: unrecognized service 
``` so I guess it's not installed. I was worried somehow PuTTy had installed something...

I've been setting up UFW and was also just wondering is denying all inbound except the transmission ports and *allowing all* outbound really the best way to use transmission with UFW enabled? 

Also just to reassure me: allowing all outbound via UFW doesn't really mean all outward ports are open does it? nor does allowing 51143 or whatever it is inbound for transmission mean this port is open? it's somehow more subtle than that right?

---

### Post by Dangertux on 2011-11-03
> **Azrael84 said:**
> Thank you both very much.

I got ```
 ssh: unrecognized service 
``` so I guess it's not installed. I was worried somehow PuTTy had installed something...

I've been setting up UFW and was also just wondering is denying all inbound except the transmission ports and *allowing all* outbound really the best way to use transmission with UFW enabled? 

Also just to reassure me: allowing all outbound via UFW doesn't really mean all outward ports are open does it? nor does allowing 51143 or whatever it is inbound for transmission mean this port is open? it's somehow more subtle than that right?


Umm actually allowing all outbound traffic means that outbound connections will be allowed on any port. So in a sense yes. They aren't `open` in the same sense that a port with a listening service bound is. However if a connection is made from that port it will not be stopped by a firewall.

---

### Post by Azrael84 on 2011-11-03
> **Dangertux said:**
> Umm actually allowing all outbound traffic means that outbound connections will be allowed on any port. So in a sense yes. They aren't `open` in the same sense that a port with a listening service bound is. However if a connection is made from that port it will not be stopped by a firewall.

If I allow an incoming port like the one for transmission, am I right in thinking it's nothing to be concerned about because there is no listening service on that port? Is this the sense in which Ubuntu "comes with no open ports": it has no inbound ports with listening services active? yet without a firewall nothing is blocking a user setting up a listening service on such a port...

In other words what I'm trying to ask is I'm not making my system more unsecure than it was out of the box by enabling a firewall then having it open all outgoing ports? the system as far as outgoing transmissions are concerned is as it was upon fresh install?

Is there a better way to use transmission than opening all outgoing ports then?

---

### Post by Dangertux on 2011-11-03
This thread might help you better understand your firewall and how it works and doesn't work for you : [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

Sorry there is no pat on the back answer here. IMO the "I have no open ports" argument is pretty much a baseless marketing statement.

---

