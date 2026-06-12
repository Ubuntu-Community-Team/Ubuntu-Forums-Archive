---
title: "How to remote access my home pc"
date: 2010-01-29
forum: Security
---

### Post by hoboy on 2010-01-29
Can somebody show me how i can remote access my pc at home from work ?
on different pc that has access to INTERNET.
what software shall I install on my pc at home ?
I want to be able to install software on my pc at home from my work place,
my home pc has unbuntu 
Linux ubuntu 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

---

### Post by myth1914 on 2010-01-29
I'm not sure what you mean by installing from work.  I'll assume you want to control your home PC remotely.  This is a wide question with a few steps, so let me know if you need more on any one point.  I will also assume you have an ISP that will allow traffic on port 5900:

1. Go to dyndns.org and set up a free account.
2. Log in to your router at home and configure the DDNS with the account you've just set up.
          2a.  If you don't have a router, you will need a DDNS client on the machine itself.
3. Follow this: [http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop) to the point of having it shared.  You should not need the IP, as most will change dynamically, which is why you've set up the account in step 1.  
4. Get a VNC client from tightvnc.com or uvnc, or any other VNC viewer
5. From your VNC viewer on the Windows box, log in to the address created as part of step 1.

You should now see your desktop as if you were in front of it.

---

### Post by myth1914 on 2010-01-29
OH!.  I forgot something.  Step 2b.  Add a port forward in your router from WAN to the Ubuntu machine on port 5900.

An additional note.  If you want to skip the dynamic DNS updates etc.  You can start on step 2b then get your external IP from somewhere like whatsmyIP.com and use that address in the VNC viewer; however, this will most likely be a temporary solution.

Hope that helps

---

### Post by hoboy on 2010-01-29
> **myth1914 said:**
> OH!.  I forgot something.  Step 2b.  Add a port forward in your router from WAN to the Ubuntu machine on port 5900.

An additional note.  If you want to skip the dynamic DNS updates etc.  You can start on step 2b then get your external IP from somewhere like whatsmyIP.com and use that address in the VNC viewer; however, this will most likely be a temporary solution.

Hope that helps

I'll assume you want to control your home PC remotely.
Yes that is the purpose thanks for your advice i will follow them.

---

### Post by HermanAB on 2010-01-29
Howdy,

I hope you don't have anything important on your home PC, since if you use VNC, then it *will* get hacked. These forums are full of tales of woe about that.

SSH is your friend.  Read up on how to use it.  It can do everything VNC does and much more and it is secure.  SSH is also easier to get to work than VNC and you can run it on a non-standard port like 80, or 445, to be able to get through a restrictive corporate firewall.

---

### Post by cariboo on 2010-01-29
+1, don't use vnc alone. Access your computer using vnc over ssh, for a howto have a look [here]("https://help.ubuntu.com/community/VNC").

---

### Post by HermanAB on 2010-01-30
Howdy,

If you have SSH, then VNC is redundant.  You can get clickety-click access to the remote machine by simply launching the Gnome Panel over SSH:

```
$ ssh -X -C -c blowfish user@ipaddress gnome-panel
```

That works way better and faster than VNC.  

Don't run the KDE kicker panel over SSH, if your local machine also runs KDE though - it'll screw up.

The above trick also works from Windows, using Xmingw and PuTTY.

---

### Post by movieman on 2010-01-30
> **HermanAB said:**
> If you have SSH, then VNC is redundant.

Not really: VNC provides much better performance than X11 over high-latency links. It also allows you to leave graphical programs running while you're not connected.

---

### Post by hoboy on 2010-01-30
Thanks guys for your input, you have helped.
great forum

---

### Post by The Cog on 2010-01-31
It may be too late for this conversation but amyway, here's my tuppence worth:

SSH gets lots of scripted bots trying to hack it. Make sure you use strong passwords or preferably use key based authentication. Use a high random port number rather than port 22. Use a firewall and only allow the SSH in from the IP addresses that you know your work uses when it connects out.

I restrict SSH into my home ot my work IP address. I have OpenVPN open to any IP address so I can get it from anywhere.

---

### Post by Socrates1013 on 2010-02-01
You can also install at the term:

sudo apt-get install tightvncserver

The port it opens by default however is incremental to the number of vncserver services you have running. For example, it starts at port 5901, then 5902, etc. and I believe the 490x are for http access. Of course, that can all be changed.

I would most ***certainly*** recommend a firewall if you're opening ports on your home computer.

---

