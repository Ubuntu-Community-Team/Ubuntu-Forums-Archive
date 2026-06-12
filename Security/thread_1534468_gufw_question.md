---
title: "gufw question"
date: 2010-07-19
forum: Security
---

### Post by justin42728 on 2010-07-19
Hey all! I'm fairly new to Linux (although I do have a pretty good background in Windows).

I have a question about gufw.
I have installed the graphical front end to ufw, and have enabled it. I have set it to Deny incoming, and allow outgoing. However, I have not established any rules. I'm only using this computer for everyday surfing, email, IM and stuff (not running a server, or anything). My question is whether or not this makes me fairly secure.

I understand that Linux is much more secure than Windows, and from what I've read Ubuntu closes all ports by default. I know it's been said on here that you probably don't even need a firewall unless you're running a server or something......but what can I say, I'm paranoid. lol

Thanks in advance for the replies!

---

### Post by endotherm on 2010-07-19
ok, well you are almost exactly as secure as you were before you installed gufw. sounds funny right?

ubuntu ships with no open service ports, so the firewall allows all connections, but there are no ports to connect to, so there is no need for a firewall, unless you install a service which opens ports (like ubuntu's remote desktop, or samba file sharing).

---

### Post by The Cog on 2010-07-19
Like endotherm said. Unlike windows, a default Ubuntu install doesn't have any significant service ports open (no TCP ports at all), and so has no need of any firewalls to protect it from unwanted incoming connections.

And if you **were** to install both a firewall and a service like a web server, you would have to configure the firewall to allow connections to the web server in anyway so the firewall would still be pointless.

---

### Post by bodhi.zazen on 2010-07-19
> **justin42728 said:**
> Hey all! I'm fairly new to Linux (although I do have a pretty good background in Windows).

I have a question about gufw.
I have installed the graphical front end to ufw, and have enabled it. I have set it to Deny incoming, and allow outgoing. However, I have not established any rules. I'm only using this computer for everyday surfing, email, IM and stuff (not running a server, or anything). My question is whether or not this makes me fairly secure.

I understand that Linux is much more secure than Windows, and from what I've read Ubuntu closes all ports by default. I know it's been said on here that you probably don't even need a firewall unless you're running a server or something......but what can I say, I'm paranoid. lol

Thanks in advance for the replies!

I think a better question is , what makes you think you are more secure by enabling a firewall ?

In part you answered your own question, if you are not running any services there is nothing to firewall. It is similar to building a second garage to protect a vehicle you do not own.

Better to understand how these tools work and how to apply them then to blindly activate them.

My only other comment is not all services are equal. You may be running a public web server and ssh. Your firewall settings will be different between those two services.

---

### Post by justin42728 on 2010-07-19
> **bodhi.zazen said:**
> I think a better question is , what makes you think you are more secure by enabling a firewall ?

In part you answered your own question, if you are not running any services there is nothing to firewall. It is similar to building a second garage to protect a vehicle you do not own.

Better to understand how these tools work and how to apply them then to blindly activate them.

My only other comment is not all services are equal. You may be running a public web server and ssh. Your firewall settings will be different between those two services.

I guess I'm still working on getting rid of that Windows mindset.

---

