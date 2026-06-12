---
title: "Strange problem with vnc authanticate!!!"
date: 2011-12-12
forum: Server Platforms
---

### Post by poolet on 2011-12-12
Ok, I have build a server and configure on it vnc ( remote desktop ) and ssh!!!!
Ok.. SSH authenticate successful but when I try to connect via remote desktop from any other machine the vnc server reject the client and I get  an error message that the password is wrong... I tried to change password and also tried to removed the password but nothing happens the problem isn't fixed.... Any ideas I will appreciate!!!! Thank you very much!!!

---

### Post by arrrghhh on 2011-12-12
I'm confused, if you have a server there's nothing to VNC into...?

If you want a GUI, install the desktop edition.  If you don't need a GUI and just want a lean&mean server, install the server edition.  Don't install the server edition and try to make it the desktop edition, that's a complete waste of time and resources - just go straight to installing the desktop edition and be done.

---

### Post by poolet on 2011-12-12
> **arrrghhh said:**
> I'm confused, if you have a server there's nothing to VNC into...?

If you want a GUI, install the desktop edition.  If you don't need a GUI and just want a lean&mean server, install the server edition.  Don't install the server edition and try to make it the desktop edition, that's a complete waste of time and resources - just go straight to installing the desktop edition and be done.

I have confused you!!! Sorry!!! Just forget about all that I mention about the server!!! I have configure the ssh connection on one xubuntu machine and vnc ( remote desktop ) and I am trying to connect from my laptop via remote desktop and I get that error message that the password that I used is wrong... On other side when I tried to connect via SSH the connection connected without any problem!!!!!

---

### Post by arrrghhh on 2011-12-12
> **poolet said:**
> I have confused you!!! Sorry!!! Just forget about all that I mention about the server!!! I have configure the ssh connection on one xubuntu machine and vnc ( remote desktop ) and I am trying to connect from my laptop via remote desktop and I get that error message that the password that I used is wrong... On other side when I tried to connect via SSH the connection connected without any problem!!!!!

You should be using VNC on that other machine.  Remote Desktop / RDP is a proprietary protocol from Microsoft, won't work with VNC.

Also, this is the server section... :rolleyes:

---

### Post by poolet on 2011-12-12
> **arrrghhh said:**
> You should be using VNC on that other machine.  Remote Desktop / RDP is a proprietary protocol from Microsoft, won't work with VNC.

Also, this is the server section... :rolleyes:

Thats right!!! RDP isn't works I just mention it as a lot of people isn't understand the meaning of vnc... ;) but what about vnc ??? Do you have any idea why i get such an error message??

---

### Post by arrrghhh on 2011-12-12
> **poolet said:**
> Thats right!!! RDP isn't works I just mention it as a lot of people isn't understand the meaning of vnc... ;) but what about vnc ??? Do you have any idea why i get such an error message??

Ok, so just to be clear.

These are two Xubuntu machines.  Both have VNC server & clients running?  These are on the same LAN?

You can SSH just fine in both directions, but VNC only works in one direction?  Or fails in both?

Are you ssh'ing and forwarding a port, or just going straight VNC?  Do you have any software firewalls enabled or hardware firewalls between the two boxes?

I'm probably asking a lot of dumb questions, I'm not an expert on VNC.

Edit - perhaps a mod should move this thread, it's not in the right section at all...

Edit 2 - not sure why I didn't do this earlier, but have you read the VNC community docs?

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

[https://help.ubuntu.com/community/VNC/Clients](https://help.ubuntu.com/community/VNC/Clients)

And of course, the newer versions has a built-in remote setup which should make this very easy.

[http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/](http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/)

---

### Post by poolet on 2011-12-12
> **arrrghhh said:**
> Ok, so just to be clear.

These are two Xubuntu machines.  Both have VNC server & clients running?  These are on the same LAN?

You can SSH just fine in both directions, but VNC only works in one direction?  Or fails in both?

Are you ssh'ing and forwarding a port, or just going straight VNC?  Do you have any software firewalls enabled or hardware firewalls between the two boxes?

I'm probably asking a lot of dumb questions, I'm not an expert on VNC.


Well 2 machine one xubuntu and one has ubuntu... both machine has configure vnc and ssh server & client at the same LAN  and ssh'ing on port 5900 ( I tried 5901 isn't works)  all firewalls and rooter filters has be disable manually.... Also , at the end even I tried to connect vnc from xubuntu to ubuntu and opposite I get the same message..... 

I am  sure that I found the problem but I can't fixed it since there no a lot of configuration on vnc server.... When the vnc client asking request to connect to server the vnc server respond fine so there isn't a connection problem, the strange thing is that the vnc server isn't asked for a user, just for a pass in a different way with ssh that to connect I need to have a user and a pass... So am absolutely sure that the authentication is on user and not at the pass  since the vnc server isn't asked for it.... I will looking forward on net and I would let you know... but if you have any other ideas please let me know maybe helps me !!!! Thank you!!! :)

---

### Post by arrrghhh on 2011-12-12
> **poolet said:**
> Well 2 machine one xubuntu and one has ubuntu... both machine has configure vnc and ssh server & client at the same LAN  and ssh'ing on port 5900 ( I tried 5901 isn't works)  all firewalls and rooter filters has be disable manually.... Also , at the end even I tried to connect vnc from xubuntu to ubuntu and opposite I get the same message..... 

I am  sure that I found the problem but I can't fixed it since there no a lot of configuration on vnc server.... When the vnc client asking request to connect to server the vnc server respond fine so there isn't a connection problem, the strange thing is that the vnc server isn't asked for a user, just for a pass in a different way with ssh that to connect I need to have a user and a pass... So am absolutely sure that the authentication is on user and not at the pass  since the vnc server isn't asked for it.... I will looking forward on net and I would let you know... but if you have any other ideas please let me know maybe helps me !!!! Thank you!!! :)

Sorry I edited my post 15,000 times.  Check it again, I posted some links which will hopefully help you get where you want to be.

---

### Post by poolet on 2011-12-12
> **arrrghhh said:**
> Sorry I edited my post 15,000 times.  Check it again, I posted some links which will hopefully help you get where you want to be.

hehe :) thanks a lot!!   I will give a shot and  I let you know!!! Thank you!!!!

---

