---
title: "Server won't let traffic in"
date: 2013-05-08
forum: Server Platforms
---

### Post by OR83 on 2013-05-08
I'm having trouble with my server as it won't let any outside traffic in. I did port forwarding on my router I added the default gatewat as 192.168.1.1 and netmask as 255.255.255.0 nmap says some ports are closed but on the server says ALLOW ANYWHERE.

---

### Post by CharlesA on 2013-05-08
Run this please:

```
sudo iptables -L
```

```
sudo netstat -nlpu
```

---

### Post by darkod on 2013-05-08
Can you post the output of:
```
sudo iptables -L -v -n
sudo netstat -plunt
```

---

### Post by The Cog on 2013-05-08
We need lots more information to be able to help. 

What traffic are you trying to send to the server - what protocol?

What makes you say it "won't let traffic in"? How do you try to send traffic in, and what happens?

Please try these two commands and post the output:
```
netstat -lntu
sudo iptables-save -c
```

EDIT: Ooh, looks like I'm late to the party. Got distracted while answering.

---

### Post by OR83 on 2013-05-08
SSH, HTTP,HTTPS,FTP, MySQL those protocols. I'm using a service like DynDNS because my ISP won't give me a static IP address my cousin says the page won't load

---

### Post by OR83 on 2013-05-08
the link is [http://oscar080483.no-ip.biz](http://oscar080483.no-ip.biz) he says it won't load but when I ping it it gives me replies I'm not sure if it's because I'm on the internal network or what it is

---

### Post by OR83 on 2013-05-08
there's nothing on the link other than the default apache server page.

---

### Post by CharlesA on 2013-05-08
That doesn't really tell us anything about the server itself.

---

### Post by darkod on 2013-05-08
Your cousin is right, it doesn't open.
Give us the results of the iptables and netstat commands posted earlier. That will help with more info.

Another reason is that the ISP might be blocking port 80 to prevent people running web servers at home. Did you verify it doesn't block it?

---

### Post by OR83 on 2013-05-08
here's some output 
[IMG]https://www.box.com/s/nl9p3xc7romkggmrx02c[/IMG][IMG]https://www.box.com/s/gqb7r7znyu9ct6tapjjh[/IMG][IMG]https://www.box.com/s/wkvi2shnoj7envznkcub[/IMG]

---

### Post by OR83 on 2013-05-08
I called the ISP and they said they don't block any ports

---

### Post by The Cog on 2013-05-08
oscar080483.no-ip.biz  resolves to 192.168.1.2 which is a reserved address, not reachable over the internet.
First, you need to change the DNS entry to give your publicly visible address, not your private internal address. You probably have to configure your router to make the dyndns entries as your server doesn't even know your public address.

Beyond that, please answer the questions we have posted.

---

### Post by OR83 on 2013-05-08
hmm that's weird 192.168.1.2 is what linksys told me to use they said to use anything from .2 and below .100 my IP before .2 was .109

---

### Post by OR83 on 2013-05-08
I called my ISP yesterday and they told me to call linksys and they said to use that. are you suggesting I go back to .109?

---

### Post by CharlesA on 2013-05-08
> **OR83 said:**
> hmm that's weird 192.168.1.2 is what linksys told me to use they said to use anything from .2 and below .100 my IP before .2 was .109

They told you to use that for your DNS information?

You should have just let your router update no-ip.biz's information. It should use your external IP.

---

### Post by The Cog on 2013-05-08
> **OR83 said:**
> I called my ISP yesterday and they told me to call linksys and they said to use that. are you suggesting I go back to .109?

I don't understand that question.

To explain, 192.168.1.* is a range of addresses for private network use. Your ISP will allocate a public address to your router when it connects, and the router performs translation between the two. Since the router translates all 192.168.1.* addresses to the single public address, incoming connections need a port-forwarding entry configured to tell the router which private address to forward the incoming call to.

Once the DNS entry is giving the public address, you will not be able to connect to your server by name from inside your private network. This is because address translation doesn't allow for both addresses being on the same side of the router. You will need to test from a different public address on the internet.

---

### Post by CharlesA on 2013-05-08
+1 to The Cog.

Once you get the DNS entry sorted out, you should be good to go if your ISP isn't blocking ports.

---

### Post by OR83 on 2013-05-08
I'm going to have to reset everything then.

---

### Post by lisati on 2013-05-08
> **OR83 said:**
> I'm going to have to reset everything then.

Before you do, you might want to check to see if your router has an option to automatically update the DNS information at no-ip. On my current router (one by Thomson provided by my ISP) the relevant option is found on the Toolbox->Dynamic DNS menu item.

---

### Post by OR83 on 2013-05-08
it has it only for DynDNS and TZO not for no-ip. had my modem and router reset i got and ip of 192.168.1.100 on the server

---

### Post by CharlesA on 2013-05-08
Download their client then:
[http://www.noip.com/downloads.php?page=linux](http://www.noip.com/downloads.php?page=linux)

---

### Post by lisati on 2013-05-08
> **OR83 said:**
> it has it only for DynDNS and TZO not for no-ip. had my modem and router reset i got and ip of 192.168.1.100 on the server

That's a bit of a nuisance, but it doesn't have to be the end of the world.

As others have mentions, IP addresses beginning with 192 are usually used on a LAN, and public DNS services such as no-ip work better if provided with your public IP address. 

There are some software solutions available that can run on your server and which keep services such as no-ip informed of your current IP address.  The version of Ubuntu I'm currently using has a program "noip2" available in the repositries; some information can be found here: [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

No-ip also have there own linux-friendly software, which can be found at [http://www.noip.com/downloads.php?page=linux](http://www.noip.com/downloads.php?page=linux)

It has been a while since I've used either, and others might be better able to guide you through the setup.

@charlesa: I see what you did there while I was typing! :D

---

### Post by cariboo on 2013-05-09
I really simple way to check if you server is visible to the rest of the world, is to use [canyouseeme]("http://canyouseeme.org/").

---

### Post by darkod on 2013-05-09
And on top of everything said, just to go back few posts since I didn't see anyone mention it explicitly. Your server network setup with a static IP was OK. Do that again, that was not the problem.
The problem was that your router doesn't support updating your public IP with no-ip and you didn't install their client either.

For a server it's best to have a static IP, not a dynamic one by dhcp (like it has now 192.168.1.100). So, do the static again, forward the relevant ports to that private IP, and install the no-ip client so that it can update your public IP with their service.

---

