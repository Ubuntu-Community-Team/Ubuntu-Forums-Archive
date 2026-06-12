---
title: "SSH tunneling using a remote server as proxy"
date: 2009-02-08
forum: Security
---

### Post by theluddite on 2009-02-08
I looked elsewhere in the forums and on the web and couldn't find a good tutorial on how to setup a proxy to enable ssh tunneling on my ubuntu machine.  I figured it out for myself from a few different tuts and thought I'd share my solution.  I'm a relative n00b, so please comment if you think this is "right out of 'er" or if you think this solution was helpful.

Here's the situation:  You're on your laptop and can't browse the web because of a well-meaning but overly restrictive filtering proxy (or firewall).  With this method, if you can use ssh to connect to a remote machine from your laptop, you can "tunnel" your browser traffic through this connection to bypass a content filter.  [COLOR="Red"]Disclaimer:  Filters are normally set up for a good reason and bypassing yours may make you subject to administrative or legal action.[/COLOR]  On the other hand, sometimes they're repressive and unethical (China for example) which is why I feel justified in writing this tutorial.  For this example we'll use two computers: laptop (local) and desktop (remote) with both running ubuntu (what else?).

First, you'll require ssh on both machines.  If it's not already on your distro (I can't remember if it's native on Ubuntu) it can be acquired with:

> sudo apt-get install ssh

[COLOR="Red"]Important point:  If you don't have one already, you need to change to a VERY secure password to use ssh.  Your computer will be accessible to anyone on the internet and a weak password will allow a black-hat hacker to gain root access on your machine using a dictionary or brute force attack (this is very, very bad).[/COLOR]  With ssh installed, connect to the desktop as the superuser:

> ssh -l [superuser's username] ipaddressofdesktop

and enter your über-strong password.  The desktop needs to be running tinyproxy which is a lightweight proxy server that will allow you to route the ssh traffic through this machine:

> sudo apt-get install tinyproxy

I found it helpful to change the listening port on tinyproxy (optional)

> sudo gedit /etc/tinyproxy/tinyproxy.conf

so it looks like:
> #
# Port to listen on.
#
Port 6000

To affect the changes you need to restart tinyproxy
> sudo /etc/init.d/tinyproxy restart

Logout of your desktop by typing "logout" into the ssh prompt.
Now on the laptop, you'll need to setup your ssh tunnel.  Install Gnome SSH Tunnel Manager:

> sudo apt-get install gstm

Now we need to configure the ssh tunnel:

[LIST=1]

[*]Open the GUI by clicking Applications->Internet->gSTM.  

[*]Then click on "Add" and enter a name such as "Home".  

[*]In the "LOGIN" field, enter the username of the superuser again.  

[*]In the "HOST" field, enter the ip address of the desktop.  

To the right of the "Port Redirection" field click on "Add" and in the popup menu change the fields as follows:  

[LIST=1]
[*]The "Type" field should be "local"

[*]The "Port" field should be "7777"

[*]The "To host" should be "localhost" and 

[*]The "To Port" should be "6000".
[/LIST]

[*]Click "OK" and "OK" again.  
[/LIST]

Click on "Home" and "Start" and enter the password for the superuser which will start the ssh tunnel to your desktop.

Now you just have to configure your web browser (or torrent software, or any other service) to use the tunnel.  For Firefox:

[LIST=1] 
[*]Click on "Edit->Preferences".  

[*]Select the "Advanced" tab and click on the "Settings" button.  

[*]Tick the "Manual proxy configuration" box.  

[*]For "HTTP Proxy" enter "localhost" and for "Port" enter "7777".  

[*]Tick the box "use this proxy server for all protocols".  

[*]Click on OK.
[/LIST]

Voila!  Now all of the packets for firefox are encrypted using the ssh and sent on the ssh port (number 22), evading any pesky filters.  

This method could also be used for more questionable and probably illegal aims, such as not paying for wireless internet access by tunneling around a proxy that blocks only port 80; or to avoid bandwidth throttling on ISPs that do deep packet inspection for torrent traffic -- [COLOR="Red"]Which in no way do I endorse.[/COLOR]  So, I hope this helped and please use it ethically.

---

### Post by Dr Small on 2009-02-08
The only problem is, most restricting filters do more that filter. Generally when things are that tight, they limit which ports you are allowed to connect to outbound. So if you do some investigating and find that only port 80 and 443 are allowed outbound, well then, you just need to change the listening port of the SSH server.

But overall, it's a good tutorial.

I've never used gstm, so I can't say anything about that. But you can always use Privoxy too and just forward all connections to the SSH SOCKS proxy and configure Firefox (etc..) to use Privoxy. There are many ways to do this. :)

---

### Post by Dave_Connor on 2009-02-08
For tunnels I just use "ssh -D port -C server" for tunneling and then set up tunneling like so in your tutorial with firefox.

---

### Post by kevdog on 2009-02-09
Im dumb when it comes to proxy servers, but why do you need the proxy?  Can you just make use of SSH's built in SOCKS proxy server in this example?  Why tinyproxy or privoxy?  I'm really trying to understand all of this better.

---

### Post by Dr Small on 2009-02-09
> **kevdog said:**
> Im dumb when it comes to proxy servers, but why do you need the proxy?  Can you just make use of SSH's built in SOCKS proxy server in this example?  Why tinyproxy or privoxy?  I'm really trying to understand all of this better.
Well, suppose you want to do the least amount of configuring. So you setup Privoxy to forward it's connections to the SSH SOCKS proxy and port. Then you can just set a few iptables rules that will route all outgoing traffic to privoxy, and now you don't need to do any configuring in your web browsers.

That's just the way I see to do it, but it still doesn't leave you untraceable, as the network admin can do some network tests and find out that you've been connecting to a remote SSH server.

---

### Post by regstraton on 2009-02-09
Often the situation is all you have available are the HTTP and HTTPS ports. Typically with publicly available Wifi etc.

In this circumstance [HTTP Tunnel]("http://http-tunnel.sourceforge.net/") is a great solution.

---

### Post by HermanAB on 2009-02-09
I simply configured one of my servers with SSH listening on port 80 (in /etc/ssh/sshd_config add Port 80 and restart it).  Then I ssh -p 80 to that server and run whatever program I want, including a web browser or something else remotely.

Cheers,

Herman

---

### Post by kevdog on 2009-02-09
> **Dr Small said:**
> Well, suppose you want to do the least amount of configuring. So you setup Privoxy to forward it's connections to the SSH SOCKS proxy and port. Then you can just set a few iptables rules that will route all outgoing traffic to privoxy, and now you don't need to do any configuring in your web browsers.

That's just the way I see to do it, but it still doesn't leave you untraceable, as the network admin can do some network tests and find out that you've been connecting to a remote SSH server.

Ok I get what you are saying.  Can you provide some examples of the iptables rule for this.  You are likely going to forward the OUTPUT chain somewhere.

---

### Post by theluddite on 2009-02-09
I hadn't heard of HTTP tunnel, which I suppose would be the exact opposite of what I describe above, but effective for ssh connections, IRC, vnc etc.  I've also heard of tunneling using only DNS requests...

---

### Post by Dr Small on 2009-02-10
> **kevdog said:**
> Ok I get what you are saying.  Can you provide some examples of the iptables rule for this.  You are likely going to forward the OUTPUT chain somewhere.
```

# Allow Privoxy to connect to port 80
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner privoxy -j ACCEPT

# Redirect users connecting to port 80 to 8118 (privoxy port)
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8118
```

That's what I use, and it works. Then any outbound connections to port 80 automatically get redirected to port 8118 for Privoxy which is configured to connect to another proxy. So everything is transparently being proxied and it requires zero configuration from the browser :)

---

