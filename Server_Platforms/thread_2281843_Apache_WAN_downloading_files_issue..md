---
title: "Apache WAN downloading files issue."
date: 2015-06-10
forum: Server Platforms
---

### Post by Higgins909 on 2015-06-10
Ubuntu... somewhere around 14
apache 2. installed LAMP the new, not as good way. (Couldn't find the way with the package install, like os install)

I had a hell of a time trying to get it to work... instead of just setting up address and port once, you gotta do it twice... once in global and other in virtual... (took while to figure, used to be easier)
I finally got it to work and when I try to download a file, tried several ports, 9090 1200 25568 and they all seem to download really slow on WAN. I don't understand.
I know my upload speed isn't impressive, but it should be faster then some 77kb 5 mins  I've run gameservers and ts3 and they work fine.
The thing I don't like and might be to blame my isp, Atnt, is that it works flawlessly on LAN.

I'm trying to setup a fastdl server for cs go.

Thanks,
Higgins909

---

### Post by seijirou on 2015-06-10
Some ISPs definitely play games with outgoing HTTP traffic, and you're not going to fool them with a different port.

Does the problem go away if you try it through a VPN?  That would give more indication of ISP tom-foolery IMO.

---

### Post by Higgins909 on 2015-06-10
These are the errors i see in my router... not sure if this is the reason or not.

all are TCP
Downstream direction: malformed tcp-header
Generic Discards

I tried to do some ghost vpn... didn't work. not sure if you're asking to put a vpn on my server or connect to my server with one on my desktop?

---

### Post by Higgins909 on 2015-06-11
I'm guessing it is something with my isp.
BUt it seems that it turned out that I couldn't connect right to my webserver from the same WAN ip...

---

