---
title: "Question about router"
date: 2012-11-06
forum: Security
---

### Post by jsvidyad on 2012-11-06
Hello, 

   I have a question regarding router security. I am not sure if this is the right forum to post this. If, somehow, someone manages to get admin access to my router(by hacking), is there some way that from the router he/she could also get into my ubuntu laptop when it's connected to that router? If there is some way, are there any safeguards against those ways?

---

### Post by papibe on 2012-11-06
Hi jsvidyad.

Both are possible, but it doesn't mean you are in imminent danger.

For starters, being behind a router using NAT is very good for security (as opposed to just using a modem).

A few tips:
[LIST]
[*]Choose a secure password, e.g., at least 12 long, with lowercase, uppercase and numbers. This is both for the router and your machine.
[*]Disable access from the Internet to the router admin pages. Most routers won't allow it anyway, but just in case.
[*]Set your wireless security to WPA or WPA2. If you only have WEP, you'll be better off not using wireless at all.
[*]Ubuntu is pretty secure as it is, but for extra security in you own machine take a look at the several firewalls available (like UFW).
[/LIST]
Hope it helps.
Regards.

---

### Post by jsvidyad on 2012-11-06
> Both are possible, but it doesn't mean you are in imminent danger.
Assuming a hacker has been able to get into my router, from there how can he get into my ubuntu laptop? What I understood is that the most malicious thing he can do is to change the DNS servers on the router and that this can be countered by assigning separate DNS servers in my laptop itself. Is there something else that the hacker can do?

> For starters, being behind a router using NAT is very good for security (as opposed to just using a modem).

A few tips:
Choose a secure password, e.g., at least 12 long, with lowercase, uppercase and numbers. This is both for the router and your machine.
Disable access from the Internet to the router admin pages. Most routers won't allow it anyway, but just in case.
Set your wireless security to WPA or WPA2. If you only have WEP, you'll be better off not using wireless at all.
Ubuntu is pretty secure as it is, but for extra security in you own machine take a look at the several firewalls available (like UFW).
Hope it helps.

  I have done all of these and more. The thing is I used my friend's computer to set up the router and there is a chance that her computer might be infected. I'm worried about someone connecting to her computer and from there connecting to the router and configuring it using the password for the router(which might have been copied if there was a keylogger on her system). She is using the same router.

---

### Post by papibe on 2012-11-06
If you feel that DNS settings has been compromised, set a custom DNS on your own machine.

I suggest either [Google Public DNS]("https://developers.google.com/speed/public-dns/") or [OpenDNS]("http://www.opendns.com/").

Take a look at this [tutorial]("http://www.omgubuntu.co.uk/2010/09/how-to-switch-to-opendns-in-ubuntu-for-faster-browsing") to learn how to do it.

Let us know how it goes.
Regards.

---

### Post by jsvidyad on 2012-11-07
> If you feel that DNS settings has been compromised, set a custom DNS on your own machine.

I suggest either Google Public DNS or OpenDNS.

   Thank You. I will do that. Other than changing the DNS server ip addresses on that router, what else can a hacker do once he has gained access to my router? Is there some way that he can hack into my laptop from the router?

---

### Post by 2F4U on 2012-11-07
Once the hacker is inside your network, he can try to attack each device, printer, networked hdd, or anything else. 
Whether he will be able to attack your Ubuntu depends on if he will be able to detect some vulnerability, e. g. open ports or services listening on the internet. Since he is on the router, he knows your IP address and can try to login to your machine. 
As soon as he is on the router, he may also shutdown the internet connection, change the administrator password of the router, or lock all your computers out by setting up a MAC filter that blocks everyone from accessing the network at all.

---

### Post by OpSecShellshock on 2012-11-07
Commercial routers should also have a means to reset them to factory settings if you are seriously concerned about compromise. You can just wipe it all out and start over.

There's no telling what kind of custom firmware is out there, but someone with administrative control of a router could change the firmware. If there's a version that somehow allows a remote command shell to be established on the device, even to run one or two things, I suppose there's a possibility that it could be used as an entry point to other devices on the LAN. I've never heard of such a thing, though.

In any case, taking control or running commands on LAN devices when you have control of a router is probably not going to get you much for the effort involved, especially a home network. The most likely thing is still going to be changing DNS settings.

---

### Post by jsvidyad on 2012-11-07
Hello,

  She ran a full scan of her system and didn't detect any infections. So, I guess things are okay. The other thing that bothers me is that she doesn't apply OS updates to her windows 7 laptop regularly(the one I used to do the configuration).

 I have eight other people staying in my house and I really can't just reset the router without good reasons. All I have right now is a mere suspicion.

---

### Post by drmrgd on 2012-11-08
While it is, of course, ill advised to neglect routine updates on any system, I don't see why her computer should be any more risk for your router than any other computer on that network.  You still need to use an admin password to make changes, right?  If not (at which point I would say buy a new router...that company doesn't care much about security!), then uninstall the router setup software from her computer.  All routers that I know about can be configured using a web browser, and specialized software is unnecessary.

That being said, if you have an unsecured computer on your network, it occurs to me that the router is not the weak point in your network, and you've got more to worry about than your computer.

---

### Post by jsvidyad on 2012-11-10
> While it is, of course, ill advised to neglect routine updates on any system, I don't see why her computer should be any more risk for your router than any other computer on that network. You still need to use an admin password to make changes, right? If not (at which point I would say buy a new router...that company doesn't care much about security!), then uninstall the router setup software from her computer. All routers that I know about can be configured using a web browser, and specialized software is unnecessary.

Yes, I have set up an admin password to make changes. I used the web browser to configure the router, not the router setup software(there was no setup software). The thing is, I used her computer to access the web config interface of the router and then I set up the router using the router admin passwd(all using her computer). What worries me is that if someone has managed to install a keylogger on her system, he might have got hold of the router admin password. So, I'm worried that if that's true, he could first connect to her computer, open the router config web interface from her computer, enter the admin passwd and change the router settings to enable him to connect remotely to the router or do something else. I have set up the firewall on the router. So, I'm not sure if this scenario could happen or not.

---

### Post by Ms. Daisy on 2012-11-10
If you will always be concerned about it, then just reset the router (like others said). Give the users the new WPA2 wifi password and you're done.

---

### Post by drmrgd on 2012-11-10
I suppose if an intruder had a keylogger on her computer when you logged into the router and that intruder has access to your network, then they might be able to get into the router configuration and make changes.  As long as you have the option to change the router settings from outside the network turned off, they would still have to be inside your network to actually get in and make changes.  You could change the router password from a more secure computer, thus eliminating (or reducing anyway) the chance of an intruder getting it if you're worried about that.  

If her computer is suspect, though, unless you firewall that computer off from the rest of the network, it could still be a threat to the rest of your LAN I would think.  I'm no security expert, but it seems that any infected computer on your network could spread risk to other computers on the net.  With good security on your other computers, I guess the risks are reduced, though.

---

### Post by Ms. Daisy on 2012-11-10
In regards to drmrgd's comments,

If your router has the ability to create a "guest" network then do that. One network could be just for you and maybe computers you trust. The other "guest" network can be for all other untrusted computers.

---

### Post by OpSecShellshock on 2012-11-11
You could also connect to the router (with a cable, need to make that clear) from a system that is fully under your control and that you trust, and change the administrative password on the router configuration page. Oh and while you're in there make sure UPnP is disabled, as well as any remote configuration options that might be available.

---

### Post by jsvidyad on 2012-12-07
> **OpSecShellshock said:**
> Commercial routers should also have a means to reset them to factory settings if you are seriously concerned about compromise. You can just wipe it all out and start over.

There's no telling what kind of custom firmware is out there, but someone with administrative control of a router could change the firmware. If there's a version that somehow allows a remote command shell to be established on the device, even to run one or two things, I suppose there's a possibility that it could be used as an entry point to other devices on the LAN. I've never heard of such a thing, though.

In any case, taking control or running commands on LAN devices when you have control of a router is probably not going to get you much for the effort involved, especially a home network. The most likely thing is still going to be changing DNS settings.

Assuming someone has changed the firmware on my router to one with a command shell and tries to get into my ubuntu laptop from the router, will the firewall(ufw) on my laptop protect me against it? Or will the ufw firewall just trust the router and accept all packets from the router and thus let the hacker in?

---

### Post by OpSecShellshock on 2012-12-07
> **jsvidyad said:**
> Assuming someone has changed the firmware on my router to one with a command shell and tries to get into my ubuntu laptop from the router, will the firewall(ufw) on my laptop protect me against it? Or will the ufw firewall just trust the router and accept all packest from the router and thus let the hacker in?

I suppose it depends on your local ufw rules and whether you communicate with other LAN devices from your computer. If you use the default of allowing outbound connections but not allowing unsolicited incoming connections you're probably fine. The only way that such a malicious custom firmware (which remember is entirely hypothetical) would come into play from that perspective is if you initiated a connection to your router's admin page and it happened to contain an exploit written for your version of whatever browser you were using which then executed further code. Alternatively it could check for services running on a different device on your LAN that you do trust and do something that way.

Of course we're talking about a huge level of effort and a willingness to just sit and wait for the perfect circumstances to arise. And the best mitigation strategy for it is probably something people have already done (that is, if they are concerned about their router security), which is setting up the router so its admin page can't be reached from the open web, and setting the admin page up with a really strong password.

---

### Post by jsvidyad on 2012-12-08
Sorry, I meant packets, not packest.

---

### Post by kurt18947 on 2012-12-08
If it were me and I'm no expert, here's how I would proceed.  Unplug the router from the internet.  Use a machine that I'm pretty sure is clean - fresh live install? - and download the latest firmware update.  Reset the router to factory defaults.  Reflash the router using the downloaded firmware which should overwrite any 'custom' firmwares that may have been installed.  Reconfigure the router then reattach to the internet.  Of course use a long complex router password.

Edit:  How do I download new firmware after disconnecting the router?  Oops.  Either download the new firmware first or use another internet connection.

---

