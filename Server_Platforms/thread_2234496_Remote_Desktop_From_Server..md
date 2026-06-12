---
title: "Remote Desktop From Server."
date: 2014-07-15
forum: Server Platforms
---

### Post by rmaher84 on 2014-07-15
Hi

i have ubuntu 14.04 server installed, and i was wondering if it was possible to have a remote desktop setup installed. i tried looking online, but i see a lot of windows solutions.

its is a server and i can ssh to it as normal, it does not have a GUI installed but i expect i will have to install one for setting up RDP. i have a mac, but ideally i would be able to do this over a browser over any OS. is this possible?

thanks in advanced! [IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

### Post by TheFu on 2014-07-15
Just because something is possible, that doesn't mean it is a good idea.  There are many different ways to accomplish what you want, but having any desktop available through a web browser just makes the barrier to attack too low, IMHO.  If you care at all about security, don't let a web-based remote desktop be used that is available over the internet and secured just by HTTPS.

So - the first question is do you have a strong VPN already working?  If not, then you need to either create that or use a solution that provides it as part of the solution.

Why is this a bad idea?
* GUI code is bloated.
* GUI code makes servers slightly less stable.
* GUI code generally leaks memory.

So ... if you aren't convinced that ssh is the only solution for server management and you don't have openvpn already working, I'd suggest **x2go**. It has issues and you do NOT want to run Unity with any remote desktop. LXDE is the best trade-off between usable desktop and remote performance for any remote desktop.  I should say that I do not use x2go ... yet.  We have freeNX running here on our remote desktop systems and I use it for my daily desktop (located in a private cloud).  FreeNX is a dead project (for a number of reasons), so it isn't available on 14.04.

If you insist on web-based, check out *quacamole*. Please, please, please only use this inside VPN access.

BTW, I plan to upgrade my main desktop to 14.04 today, then install x2go ASAP.  BTW, the plan failed and I haven't reovered from that failure yet.  That just means that it isn't running 14.04, not that the system isn't available and still working fine on 12.04.

---

### Post by lukeiamyourfather on 2014-07-15
I would not setup a GUI on a server for the reasons already mentioned. If you want to use just a couple of graphical applications on a server install you can do so with SSH via X tunneling.

```
ssh -X user@host
```

When you launch a graphical application, say Firefox, it will pipe the X commands to the local machine instead of rendering it on the remote machine. Note this requires that X be on the client since the client will be the one actually rendering the interface.

---

### Post by nerdtron on 2014-07-16
Why would you like to use remote desktop on your server? Is ssh and command line not enough? You can do it on any OS anyway so I guess you got it all covered. Are you going to use graphical application on the server to justify the need for a GUI?

---

