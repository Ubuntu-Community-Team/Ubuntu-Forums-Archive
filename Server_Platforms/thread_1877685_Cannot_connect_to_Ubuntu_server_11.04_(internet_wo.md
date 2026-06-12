---
title: "Cannot connect to Ubuntu server 11.04 (internet working on both ends though)"
date: 2011-11-08
forum: Server Platforms
---

### Post by Nyrocthul on 2011-11-08
Usually I look around the internet fairly thoroughly, and try to fix problems on my own when I'm having troubles with ubuntu, but this problem seems too specific to generalize into a search.  

I have ubuntu server natty 11.04 for use as a minecraft server.  It had been working fine, and I was using ssh to start and stop the server with a script that also works fine.  Yesterday though I went to hop on the web and my internet provider redirected me to a page to log in (usually I don't have to do this and it stays connected because of my router)

When I tried to connect to my minecraft server after this I couldn't get a connection.  I tried connecting via ssh to restart the program and couldn't connect to ssh.  I hopped on the server (not running a desktop/gui) and entered the ping command to ping [www.google.com](www.google.com) and that seemed to work.  So I don't believe there's a problem with that computer connecting to the internet.

I restarted the server, restarted the router, restarted the computer again, checked to make sure the proper ports were open on the router, pinged another couple times, and still no ability to connect to the server with ssh or minecraft.  

Has anyone had a problem similar to this or know other things I could try?

---

### Post by papibe on 2011-11-08
Hi Nyrocthul. Welcome to the forums!

Are you trying to connect using the server name or LAN IP?
Did you set the server to an static IP or set the router to reserve and address for it?

What kind of error do you get when trying to connect to your server? Try using ssh with the verbose option, and post your results:
```
ssh -vvv yourserver
```
Kind Regards.

---

### Post by Nyrocthul on 2011-11-08
Thanks for replying.  I'm still kinda new to a lot of terminology but I think I'm connecting to the LAN IP?  I use the command 
```
ssh name@12.345.567.89
```
I've never specifically set the ip address to be static but every time I've looked it up I get the same address from multiple places, including looking it up after this incident occurred.  

The error I get when I try to connect via ssh is
```
thomas@thomas-Aspire-7551:~$ ssh thomas@##.###.###.##
ssh: connect to host ##.###.###.## port 22: No route to host

```
With the #'s being the ip address (and I have the same username on this computer and the server)

I tried the verbose option and got this
```
thomas@thomas-Aspire-7551:~$ ssh -vvv thomas@##.###.###.##
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ##.###.###.## [##.###.###.##] port 22.
debug1: connect to address ##.###.###.## port 22: No route to host
ssh: connect to host ##.###.###.## port 22: No route to host

```

I'm not certain that port 22 specifically is open in the router, but I do remember that I had set it up before, and it was working.  So unless for some reason the port I had been using before was different, and ssh changed to using 22 I don't think that is the problem.

Regardless of the ssh specific port being open or not, I know that the one used for minecraft is set to be open, and that isn't working either.

---

### Post by papibe on 2011-11-08
It looks like you are trying to access your server from outside the network. Is that so?

Check if the ports are not being block using this page: [http://canyouseeme.org/]("http://canyouseeme.org/")

Just note that trying to access your external IP from inside your LAN most certainly won't work.

Regards.


EDIT: Do you have an static public IP or regular Internet service?

---

### Post by Nyrocthul on 2011-11-08
Yes, I was trying to connect from outside my network, but now I am back home (actually posting this from my server with LXDE :D  )

I checked with that site and it looks like the ports are blocked.  22 and 25565 (ssh and minecraft respectively) The reason listed was "No route to host"

Canyouseeme.org also listed my ip address as the same one I had been using to remotely connect before this incident.  

I think that I have regular internet service, but I honestly don't know.  I never requested to have a static ip, and the internet company is contracted with my apartment company, so all I had to do was log in (like I did again when all this happened)  Like I said though, my ip address hasn't changed since I first checked to see what it was (via various websites found through google search)

Thank you so much for your help so far.

---

### Post by papibe on 2011-11-08
Most ISP gives you a dynamic IP. They lease you one for a period of time, and then the process gets renewed.

The problem is that when the router renew the lease, you may get a different IP. This add a little of a challenge to connect to your server.

The solution that I use (and most people do) is to use Dynamic DNS Service. There are several sites that offer that service. I personally use [DynDNS ]("http://dyn.com/dns/")(now called just Dyn). It's free, and is easy to set.

I always recommend to take a look at this [video ]("http://www.youtube.com/watch?v=bI52nF1BRNo")from the revision3 channel on youtube. Even though is on the Windows side of things, it explains the Dynamic DNS services very well.

In Ubuntu the client part of the service is called ddclient and it is on the repositories. Install it after creating your account and domain on the DDNS of your preference.

As a prerequisite you need to set your server with a static LAN IP. That can be done easily on the router by reserving a address for your server, or on the server itself.

I hope this helps. Tell us know how it goes, or if you have more questions.

Regards.

---

### Post by Nyrocthul on 2011-11-08
Thanks, I'll try that as soon as I get some time to work it and let you know.  You have been a lot of help.

---

### Post by Nyrocthul on 2011-11-22
So I went to DynDNS and it seems the free accounts are no longer available (Or at least I was unable to find them while searching around there)  So I made an account with freedns.afraid.org and got a startup script from them to update my ip when it changes.  
Even with this I'm still not connecting via ssh or minecraft.  I am able to connect through the lan, and using canyouseeme.org and whatsmyip.org's port viewing services ports 22 and 25565 are both open.  Neither ssh thomas@[externalipaddress] nor ssh [email]thomas@usrname.domain.com[/email] work.

---

### Post by papibe on 2011-11-22
I want to make sure that you are trying to access your server using the external IP, from outside your LAN, right?

Because you can't do it from your own network (your router probably will block external IP calls from inside your Home LAN).

Just a thought.
Regards.

---

### Post by Nyrocthul on 2011-11-22
That might be it.  I've been trying to connect while using the wifi coming from the router my server is plugged into.  I have connectbot (the android ssh tool) though that is unable to connect either.

---

### Post by papibe on 2011-11-22
Your phone would be the perfect tool to test external access. Just make sure to disconnect from your WIFI, and use the 3G service instead.

Regards.

---

### Post by Nyrocthul on 2011-11-22
OMG YAY!!! Thank you so much.  It looks like that's exactly the problem.  I didn't realize I had left my wifi on my android.  As soon as I shut that off I could connect right up to my server.  So the problem was entirely trying to connect from inside the network via the external ip address.

---

