---
title: "FreeNX Windows Client connect error over Internet, LAN works!"
date: 2009-11-24
forum: Server Platforms
---

### Post by Denbert on 2009-11-24
Hi Server Gurus!

As written in this tread:[http://ubuntuforums.org/showpost.php?p=8374107&postcount=13](http://ubuntuforums.org/showpost.php?p=8374107&postcount=13)

I've installed a working Virtual Ubuntu 9.10 LTSP Server and a Virtual PXE Client and it works like a charm. I have changed the default two nic setup to one nic setup, in order to have a smoother integration in my existing LAN

I also need access from windows laptops and access over internet, and therefore I've used this guide: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) to have access via the FreeNX client and it works from LAN:

Entering correct settings:
[IMG]http://hegnstoften.net/pictures/NX-Client/NX_Settings.png[/IMG]

Entering user and password:
[IMG]http://hegnstoften.net/pictures/NX-Client/NX_Login.png[/IMG]

Connecting:
[IMG]http://hegnstoften.net/pictures/NX-Client/NX_Connect.png[/IMG]

And here is the desktop:
[IMG]http://hegnstoften.net/pictures/NX-Client/NX_Window.png[/IMG]

If I change the local IP in host, to my external IP the connection times out.

I'm sure it has some thing to do with me changing the nic setup, as a SSH via putty also fails to external address.

Anyone who can point me in right direction?

---

### Post by epsolon77 on 2009-11-24
Have you tried opening the connection using the wan IP address from somewhere other than your local network?  Sounds silly but it's worth a shot.

---

### Post by Denbert on 2009-11-24
> **epsolon77 said:**
> Have you tried opening the connection using the wan IP address from somewhere other than your local network?  Sounds silly but it's worth a shot.

You can try ssh to hegnstoften.net:8888 - Times out, work from inside, and the port forward is set correct.

I'm getting crazy ](*,)

---

### Post by epsolon77 on 2009-11-24
I was unable to connect either by hegnstoften.net nor 90.184.133.62.  I also couldn't ping that address, which tells me either your internet is down (considering your posting I'm guess that's not it) or you have a firewall up.  have you checked your firewall to make sure it allows port 8888 through to your local net?

I'm sorry I'm not trying to seem like your not intelligent, I just am taking it step by step like I would test my own system.  God knows how many times I've spent hours trouble shooting the fact I didn't plug the nic in...

---

### Post by Denbert on 2009-11-24
> **epsolon77 said:**
> I was unable to connect either by hegnstoften.net nor 90.184.133.62.  I also couldn't ping that address, which tells me either your internet is down

Has a Netgear VPN/Firewall - Ping is disabled


> **epsolon77 said:**
>  have you checked your firewall to make sure it allows port 8888 through to your local net?

Yeps, www (port 80) is pointing to another server and is working great

> **epsolon77 said:**
> I'm sorry I'm not trying to seem like your not intelligent, I just am taking it step by step like I would test my own system.  God knows how many times I've spent hours trouble shooting the fact I didn't plug the nic in...

Been there MANY times :D - This is why I'm asking for help here, and I have no problems, with showing my stupidity for the forum ](*,)

---

### Post by epsolon77 on 2009-11-24
On my sonicwall firewalls port 443 and 80 are both allowed from WAN to LAN, however out of the box most other are blocked by the firewall, and setting up a NAT for them does not unblock them.  I would see if you can temporarily disable the firewall and try again just to make sure it isn't the firewall.  Hey it can't hurt right?

---

### Post by Denbert on 2009-11-24
> **epsolon77 said:**
> On my sonicwall firewalls port 443 and 80 are both allowed from WAN to LAN, however out of the box most other are blocked by the firewall, and setting up a NAT for them does not unblock them.  I would see if you can temporarily disable the firewall and try again just to make sure it isn't the firewall.  Hey it can't hurt right?

Well - I've accepted all outbound traffic from LAN:

[IMG]http://hegnstoften.net/pictures/firewall_rules.png[/IMG]

---

### Post by Denbert on 2009-11-24
Hmm, I'm STUPID, STUPID, STUPID ](*,)

I' forgotten to actually remove the nic in vmware, therefore the second nic received a IP address from the first nic.

I stopped the server, removed the nic, and BINGO - it works over the internet.

The FreeNX client is impressive, a thing which could make it better, was if it could be a portable executable on a USB stick, as this would avoid laptop users to install anything.

epsolon77 thanx for your kind attention, as you mentioned earlier, this problem was due to me, not seeing the obvious :D

Everything works, and I'll go on test an LTSP-Cluster setup as I need 150 clients or so, and therefore loadbalancer is needed.

This test will probably end up in a new tread from me :D

---

### Post by epsolon77 on 2009-11-24
Here's something else to try.  Can you ssh into the command line on your server?  If not, see if you can install the standard SSH server and try to SSH into the CLI instead of using FreeNX.  This way you know it's independent of the FreeNX install.  It feels to me like you firewall would be blocking this.  I don't know the netgear firewall well enough to tell you what it is blocking or not.

---

### Post by epsolon77 on 2009-11-24
Well now it becomes obvious that while at work, posts can take me up to a half hour to create...   I'm glad you got it figured out!  I can't tell you how many times I've screwed up much simpler stuff than that.  Please keep me posted.  While I don't work with 150 users, I'd love to try and help test some of the load balancer setups.  I'll also see if I can find some kind of FreeNX connector that does not require an install.  That would help me out as well.

---

