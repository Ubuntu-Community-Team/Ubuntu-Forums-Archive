---
title: "DNS issues"
date: 2006-09-02
forum: Server Platforms
---

### Post by geminias on 2006-09-02
I don't know if this is easily fixed or not, but my web server was working great last night, i go to bed wake up and the link doesn't work anymore.  

The server is on a LAN with the computer I am accessing it with through putty.  I tried to access it through the LAN and it worked, I was served the webpage.  I then checked dyndns my dns server where I set up a dynamic ip for the server and it reported the same ip address as the machine i'm running, not the server.  So I pinged the url registered at dyndns and it is also pinging the machine i'm running, not the server.  

Is the server and this computer supposed to have the same external ip?  If not, how can i fix this trouble.. as in how would i find the ip of the server and then send it to dyndns.

---

### Post by NetworkGuy on 2006-09-02
You need to run the dyndns program on your router and then use port forwarding on your router to forward port 80 traffic to your web server.

Check to see if your router has the ability to do this.

The dyndns program running on your local web server is probably returning the  internal address (192.168.something) to dyndns which will not work over the internet.

---

### Post by geminias on 2006-09-02
But how can I simply find out the external ip address of my server using putty?  Once I have that, i can resubmit it to dyndns...

---

### Post by altonbr on 2006-09-02
I'll use my computer as an example... I found out my external Ip address using [http://www.whatsmyip.org/](http://www.whatsmyip.org/) ... there are millions of these sites... it's reletively easy to do because it's a simple PHP script.

My External IP:

```
24.235.137.120
```

So I go to dyndns.org and login to my account 'altonbr'. I then went to My Account > My Services > Static DNS (because mine is static.. hasn't changed in years) and then copied and pasted my IP.

Now altonbr.dyndns.org is associated with 24.235.137.120 ...

But now you want someone to type in altonbr.dyndns.org and go to your server correct? My server for example has an internal IP address of:

```
192.168.2.101
```

I found that out by using ifconfig (it's good to figure out how to use the terminal for servers because they don't always have GUIs and therefore Internet Browsers (yes I know there are text browsers.. but just let me continue please.

So I typed in 192.168.2.1 (my Gateway/Router address... most routers will be 192.168.2.1 or 192.168.1.1 or 192.168.0.1 as far as I know)... using my SMC router, I went 'Advanced Setup > NAT > Virtual Server' and entered the following information in (see screenshot)... I did the same for port 22 as port 80. Port 22 is for my SSH and Port 80 is for my Apache.

Save that configuration (and possibly back it up) and you should be good to type in altonbr.dyndns.org in your browser and see your pages on the server.

Good luck!

---

### Post by geminias on 2006-09-02
That is a nice little tutorial/post.  However, it doesn't help me in the slightest as I've already done all that.  

Today suddenly the dns doesn't resolve the right IP, so what I would like to do is find the IP of my server which I don't know how to do through putty.  I tried this: lynx [http://whatismyip.com](http://whatismyip.com) and it gives me the ip of my current computer.  I need the IP of my server.  

I got the ip of my server before because I had it connected to a monitor and keyboard but now I'm accessing it remotely via putty so the only way i could get the IP is if I find a config file where it is displayed or if I somehow route the lynx from the server to my computer...

Thanks for you time,

---

### Post by Stone123 on 2006-09-02
Can you traceroute to that computer ?

never mind.

---

### Post by geminias on 2006-09-02
lol

---

### Post by geminias on 2006-09-02
Okay after getting very serious I've discovered that the IP address for the server is indeed the same as the ip address for this computer.  I've turned this computer off and on and it is always the same IP address.  This is bad.

What could have caused this?  How is this even possible?  How do I have seperate IP addresses again?

---

### Post by altonbr on 2006-09-02
Ok well your WAN IP address is different from your LAN address.... your server, computer, laptop, etc. will ALL have the same WAN IP address... 

for example (continuing the tutorial above), my WAN IP is:

```
24.235.137.120
```

Now for your computer and then your server, they will have something like:

```
192.168.2.100 & 192.168.2.101 respectively
```

So if you can use PuTTY from your Windows box to your Linux server... then you already know the LAN IP (if you're using that) or the WAN IP with proper port forwarding... or if you're using the DNS name like altonbr.dyndns.org to connect... then you should have no problem...

So really, my question is, how are you connecting via PuTTY? If you can connect... run 'ifconfig' and it will tell you the LAN IP of the server... if you're looking for the WAN (external)... then both your computer and server will have the same IP... I don't think you can have two seperate WAN IPs unless you ask for a special business package.

If you can post your WAN and LAN IPs... and even your DNS.. then that would be ideal.

---

