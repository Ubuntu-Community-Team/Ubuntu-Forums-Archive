---
title: "To Firewall or Not to Firewall, need Opinions......"
date: 2011-01-08
forum: Security
---

### Post by Christopher on 2011-01-08
Im thinking of installing Firestarter [http://www.fs-security.com/](http://www.fs-security.com/)    on my Ubuntu 10.10, do i really need it I have my Linksys router & its running dd-wrt is this enough? Thanks in advance.

---

### Post by cariboo on 2011-01-08
If you 're worried about open ports, use [canyouseeme]("http://canyouseeme.org/") to check your router for open ports. If you don't have any ports forwarded, you shouldn't see anything open.

I've been behind a router for over 7 years, and and  have never had a firewall enabled on computers on my internal network, except for Windows systems which enable the firewall by default. I've been running one XP system with the firewall turned off for about a year as an experiment, and I haven't run into any problems with it so far.

---

### Post by OpSecShellshock on 2011-01-08
2 part answer. The first part is to say, no, you probably don't need a software firewall on the computer itself if you're behind a router and have no servers running and no ports forwarded. The second part is to say that if you do decide to use a software firewall, Firestarter is not really a good option as it is no longer maintained and ufw is already there (with perfectly fine default settings once enabled). Just do this:

```
sudo ufw enable
```

and you're good. But as I mentioned in my first point, it's probably not necessary.

---

### Post by jbrown96 on 2011-01-08
Don't use Firestarter.

---

### Post by Christopher on 2011-01-08
Thanks everyone for all the replies, no ports are open on my router so im gonna go with no software firewall.:D

---

### Post by The Cog on 2011-01-08
Firestarter is no longer being maintained. UFW is the firewall I would suggest. However...

You probably don't need a firewall. Unless you install a service (web, mail etc) then there are no listening ports for the forewall to protect. And then if you don install (for instance) a web server, you would only have to reconfigure the firewall to let connections through to it anyway. You only really need a firewall if you want to install a service and you want to restrict who can connect to it.

---

### Post by handy on 2011-01-09
Apart from the added security that a firewall has the potential to bring, there are some firewall solutions that bring more dimensions to that realm as well as becoming a router & speeding up (to some degree) your internet throughput.

The modem/routers that most people use to access the internet via broadband are Windows centric. Windows apparently doesn't handle the packets of information sent via the internet as well as the Linux kernel based systems do (I'm sure that BSD is better than Windows also). So you can improve your data throughput to some degree by using a standalone Linux kernel based firewall/router.

Just how much better throughput is extremely hard (for me at least) to measure. Though I do remember that when I first setup IPCop over 2 years ago I thought that my internet speeds had improved.

I have no proof, & barely any memory of the situation after 2 years.

Anyway, it is just another dimension to add to the firewall/(router) topic. Beyond which I can only say that IPCop has a number of services built in & that can be added in various ways for those that have need for them. All of which is easy to find out about via a web search, for anyone that is interested.

My measurements tell me that my standalone headless PIII IPCop system costs me $54-/year in electricity.

---

### Post by John Bennett on 2011-02-20
I have Maverick 10.10 running a netbook.  UFW prevents me from browsing Windows XP workgroup shares on my home network.  I would like to leave UFW turned off all the time.

Problem is, sometimes my kids might take the netbook out of my house.

Please excuse my ignorance, but how unsafe is it to use a wireless netbook at places like McDonald's or Starbucks with UFW turned off?

---

### Post by HermanAB on 2011-02-20
Provided that your children have their own accounts with 9 character passwords and do not use your account and they do not have super user access, then you need not worry about it.

---

### Post by oygle on 2011-02-23
> **jbrown96 said:**
> Don't use Firestarter.

I agree. I've been using it for ages, and it constantly floods the syslog files with 'garbage', and also stops outbound, for ???? reason/s. I have to go into Firestarter, edit prefs (no changes), and then it comes good again.

I'm going to change over to UFW.

Oygle

---

### Post by mciverza on 2011-02-23
> **HermanAB said:**
> Provided that your children have their own accounts with 9 character passwords and do not use your account and they do not have super user access, then you need not worry about it.


and provided your little PC isn't running services. ie. is still a default Desktop/Netbook install.

If you're using empathy, then ports are open.
If you've installed samba (to fileshare with Windows),  then ports are open
If you've installed Dropbox or Skype, then ports are open.

Whether or not a firewall is required is for you to decide. I found shorewall to be more useful (and more complicated) than UFW, because I need my firewall to have different rules according to what IP address I have (i.e whether I'm using my home LAN/WLAN or wifi at a hotspot, or a pppoe connection via DSL)

Either way. Reading up the howto for UFW would be a good idea, and if you're looking for a GUI to make it easy to configure, the package is called "gufw".

Safe computing!

---

### Post by SeijiSensei on 2011-02-24
> **handy said:**
> The modem/routers that most people use to access the internet via broadband are Windows centric. Windows apparently doesn't handle the packets of information sent via the internet as well as the Linux kernel based systems do (I'm sure that BSD is better than Windows also). So you can improve your data throughput to some degree by using a standalone Linux kernel based firewall/router.

I have no idea what a "Windows-centric" router might be.  The only persistent issue I know of regarding commercial routers and throughput is that their small memories can't manage a NAT table with a large number of simultaneous TCP connections.  The usual culprits in these cases are BitTorrent clients, and both Windows and Linux clients suffer from this problem equally.

That said, my outbound router is a Linux box, though I use a Linksys wifi router behind it as well.

> **John Bennett said:**
> I have Maverick 10.10 running a netbook.  UFW prevents me from browsing Windows XP workgroup shares on my home network.  I would like to leave UFW turned off all the time.

You could just open ports 137-139 and 445 which should make it possible to browse.

> Please excuse my ignorance, but how unsafe is it to use a wireless netbook at places like McDonald's or Starbucks with UFW turned off?

You're totally unprotected against someone sniffing your traffic while in a public location.  Anything not being carried over an encrypted connection can be intercepted and stored for later exploitation.  I'd be more concerned about that than about someone trying to break into the laptop.  Just make sure you don't have any services running.  To check, go to another computer on the same network and run an [nmap]("http://www.insecure.org/") scan against it.

---

### Post by brian_p on 2011-02-27
> **mciverza said:**
> and provided your little PC isn't running services. ie. is still a default Desktop/Netbook install.

If you're using empathy, then ports are open.

That's good. You can do IM.

> If you've installed samba (to fileshare with Windows),  then ports are open

That's also good, but it would be best to have it listen only for requests on your own LAN.

> If you've installed Dropbox or Skype, then ports are open.

Splendid. Receiving and making phone calls is the stuff of life. And someone being able to ssh in and check email is real convenient.

And it should not be forgotten - if the machine is safe at home it's safe anywhere. Same internet, same software.

---

