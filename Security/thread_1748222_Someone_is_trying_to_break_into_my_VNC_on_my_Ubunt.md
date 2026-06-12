---
title: "Someone is trying to break into my VNC on my Ubuntu Box!"
date: 2011-05-03
forum: Security
---

### Post by mrsuess2 on 2011-05-03
I have Ubuntu 10.10 installed at home, and I have to be able to connect to this machine's gui from a Windows machine at work. My ubuntu machine is running open ssh, and I have VNC enabled so that anyone can connect without a VNC password (although my user account on my machine has a non-weak password.)
 
My PC at home is behind a router, and I have port 22 (ssh) on my router pointing toward my home machine. Thus the only port I have open on my router is 22. I have used Firestarter to enable iptables, and the only remote connection that are allowed are on port 22 from my workplace&#8217;s IP address.  To use VNC remotely, I ssh to my machine, and then use putty to forward the port to VNC.
 
I just looked at my logs via firestarter, and it shows someone from IP address 189.38.80.51 is trying to connect to port 5900 on my machine. I don&#8217;t know how this is even possible. I don&#8217;t have any other machines connected to my wireless network except a couple of iphones and a wii, and my wireless network is protected by WPA-2 and a randomly generated 20+ character password. And the only port I have open on my router is port 22, which I double-checked. 
 
Although I don&#8217;t know if I&#8217;ve been hacked, I&#8217;m wondering if I have made some fundamental security mistake. I know there are things I could do better such as using an ssh-key instead of a password, but are there any fundamental mistakes you see in this setup? I very much appreciate your advice. And what puzzles me is how someone is getting past my firewall router.

---

### Post by Cheesehead on 2011-05-03
Scanning for open Port 5900 is a reasonably common vector, looking for unsecured VNC connections to take over.
That's why you chose to use an SSH tunnel in the first place, right?

As long as you use the SSH tunnel, you should be fine.
There are many ways you can provide additional layers of protection to your SSH connection (different port, port knocking, etc.), but they are beyond the scope of your question, and you probably know them already anyway.

You may wish to double-check your router's port forwarding. Some users set up non-secure VNC by forwarding 5900, then later secure it with ssh...and forget to disable the original 5900 forwarding. Also check, perhaps, that the router's firewall is actually turned on. Some users disable it when experimenting with network services...then forget to turn it back on.

---

### Post by bodhi.zazen on 2011-05-03
Your first mistake is to use VNC, it is notoriously insecure, and no password. You are asking to get cracked.

:facepalm:

Use ssh (ssh +X) with an x server (Xming) on your windows box. Xming runs portable from a flash drive if you must.

Your other option is to use FreeNX rather then your current VNC server.

Use a strong password for you ssh or vnc server.

Turn UPnP OFF on your router. If in doubt, scan your router for open ports.

---

### Post by mrsuess2 on 2011-05-03
Cheesehead, thanks for your reply.  I will double check by doing a port scan on my router's ip address from a foreign computer.  I never set up 5900 to forward on my router.  Also, I'm not sure what you mean by "check that your router firewall is turned on".  I'm using linksys, and the only port being forwarded is 22 to my own computer.

---

### Post by spiky001 on 2011-05-03
You can always use this to scan [http://nmap-online.com/](http://nmap-online.com/)

---

### Post by mrsuess2 on 2011-05-03
bodhi.zazen,  Thanks for your advice.  I had UPnP enabled on my router and I just disabled it.  I will look into your other advice shortly. Thanks again.

---

### Post by mrsuess2 on 2011-05-04
Very useful, spiky001.  Thanks!
 
> **spiky001 said:**
> You can always use this to scan [http://nmap-online.com/](http://nmap-online.com/)

---

### Post by roma.hicks on 2011-05-07
I actually got attacked by this exact IP this morning.  They actually took control of my wife's computer, which I forgot to secure from a few days ago.  I think it was just a bot attack because it immediately started typing in commands in to spreadsheet file she was working on, on top of that it was Windows commands.

And I think it was the PnP on my router too.

---

### Post by bodhi.zazen on 2011-05-07
VNC + UPnP + weak passwords == the most common crack on these forums.

Almost always followed by windows code, but not always.

Probably the best argument for enabling a firewall by default, but not sure if it would help because first thing anyone wanting VNC will do is disable the firewall and how many users new to Ubuntu know how to write proper rules for ufw/gufw/iptables to restrict access to VNC ?

So hard to know if enabling the firewall would help.

Best advice I have is to use ssh

ssh + X 

You can run putty and xming on Windows and forward gnome panel all from a flash drive without admin privileges or installing anyting on the windows box.

or tunnel VNC over ssh 

or use FreeNX

and avoid VNC at all costs :twisted:

---

### Post by Alclub on 2011-08-10
If anyone still cares, that exact ip recently managed to connect to my vnc server despite being passworded (they must've cracked it).

I immediately disconnected them, but now I'm worried about who else/how many times they've connected before... really should'nt have left that port open to the internet...

Also, what good would it do a bot to connect to a random vnc server... unless the password is saved for someone to connect later...

---

### Post by requeth on 2011-08-10
If an attacker gets access through VNC then they basically received physical access, at which point they can install viruses, malware, root kits, hidden scripts, root your box, backdoor your router from inside your network, hack other computers on your network. You name it. If they got in then they got a foothold and you need to start figuring out what they did. It may have just logged the connection in a file and called it good, but likely it tried to install something. With any luck it was just looking for windows computers and your fine.

---

### Post by Chayak on 2011-08-11
Ubuntu, secure by default until the user activates the horribly insecure remote desktop feature.

I know this has been said before, but why is VNC *still* installed by default?

The two most common "OMG I've been h@x0r3d!" thread causes are weak passwords and users installing an SSH server, or turning on VNC.

The first is the user's fault.  The second is also the user's fault but it's part of the default install and must be safe right?

You can pop up as many warnings as you want and users will still turn remote desktop on.  It goes back to the dancing bunny theory of security.

---

### Post by Irihapeti on 2011-08-12
Worse, the remote desktop password is restricted to six characters.

I raised the issue of not including remote desktop by default with the devs. They don't think there's a problem.

What would it take to convince them?

As for the OP, in this case I'd say, back up your data files, and reinstall. You don't know what's gone on.

---

### Post by The Cog on 2011-08-12
I thought it was 8 characters.

I think perhaps the biggest issue with the remote desktop is that they don't make it clear that allowing users on the internet to connect to VNC is not a passive action. It actually tries to use UPnP to reconfigure the router to forward the VNC port to the PC. In my opinion, doing this without clearly explaining to the user what the software is doing is sufficiently negligent that it should be possible to sue for consequential damages. I doubt it will ever happen, but that kind of negligence does carry responsibility for the results, especially if you know that people are being harmed and you still choose not to at least issue a warning.

---

### Post by bodhi.zazen on 2011-08-12
> **Irihapeti said:**
> I raised the issue of not including remote desktop by default with the devs. They don't think there's a problem.

What would it take to convince them?

Unfortunately there is not much you can do. You raised your point (which I agree with), they considered it, and they made their decision.

Part of the "problem" is that Ubuntu is making an attempt to be "easy to use" for people new to Linux, and we as a community have been bery successful at that.

Part of ease of use includes an number of shares and services, vnc is but one, that can be enabled with a few mouse clicks.

The new user is typically not aware of the security implications and the firewall by default is permissive.

The policies are outlined here :

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

> By default, Ubuntu is designed to allow users to easily share files and help each other

So I guess the decision on VNC follows that philosophy.

---

