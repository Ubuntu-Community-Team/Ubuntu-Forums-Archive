---
title: "Server 9.10 Help"
date: 2010-02-25
forum: Server Platforms
---

### Post by JoelKrause on 2010-02-25
G'day,
I'm new to the Linux thing, and have installed Ubuntu 9.10 on my laptop, I like it.
I have my server, which is currently running Windows Server 2k3, It's alright, BUT, people have told me to try out the Linux Server, So I am, but, the thing is, I'm not familiar with the CLI, and would like something easy to use to manage the server; the Server will sit in the top of my wardrobe gathering dust while it's doin its job as a file server/mail server/etc. I am TOTALLY new to this, I have heard of Webmin, but when I asked about it somewhere else, I got these EXPERT comments, I'm like, yeah right, hmm, ok. Anyway.

Any help would be appreciated!

---

### Post by lisati on 2010-02-25
One tool which I use to monitor and configure my server is [webmin]("http://www.webmin.com/"). This lets me log into my server remotely from my laptop and amongst other things do useful and interesting stuff like check logs and tinker with settings.

---

### Post by JoelKrause on 2010-02-25
Oh, Ok, Could you explain to me, or point me in the direction of how to install/setup Webmin?

---

### Post by lisati on 2010-02-25
You can download webmin from their download page at [http://www.webmin.com/download.html](http://www.webmin.com/download.html)
I'd recommend using the "deb" version. The latest version showing as I type can be downloaded from the command line on your server using the following command:
```

wget http://prdownloads.sourceforge.net/webadmin/webmin_1.500_all.deb

```
It's then fairly easy to install:
```

dpkg -i webmin_1.500_all.deb

```
To access webmin from another computer on your network, start up a web browser (Firefox works well on my Ubuntu laptop) and type in
> [https://server-name.lan:10000](https://server-name.lan:10000)
(you'll need to replace "server-name" with the name your server is known by on your network)

---

### Post by JoelKrause on 2010-02-25
Thanks, for your help. 
When I type in ```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.500_all.deb
``` i get a response of wget: unable to resolve host address 'prdownloads.sourceforge.net' any ideas?

---

### Post by woland on 2010-02-25
Since the link is OK, verify you network connection.
Use ifconfig (just as ipconfig in Windows) and ping.
Take notice on the DNS server address.
Make sure that you can ping it.

---

### Post by JoelKrause on 2010-02-25
it doesnt say anything about dns server :s

---

### Post by JoelKrause on 2010-02-25
i pinged a site, and it said 1 packets transmitted, 1 received, 0% lost, time 0ms

---

### Post by woland on 2010-02-25
To see what DNS server is configure you need to
```
cat /etc/resolv.conf
```

You can edit the file if the setting is incorrect.

Use nano
```
sudo nano /etc/resolv.conf
```

Also try 
```
ping prdownloads.sourceforge.net
```

---

### Post by CharlesA on 2010-02-25
Is the laptop currently getting an IP address from DHCP or is it set for a static IP?

---

### Post by gordintoronto on 2010-02-25
Just as a comment, you could install normal Ubuntu, then install all the server components you need.  That way you could do your setup using a graphical environment.  It means a little memory and CPU overhead when your server is running.  If the load is low, it doesn't matter. Just having access to Synaptic might make it worthwhile.

Full Circle Magazine has a series running currently, "Installing the Perfect Server."  You might pick up a few tips from it. FCM is a free download in PDF format.

---

### Post by JoelKrause on 2010-02-25
> **gordintoronto said:**
> Just as a comment, you could install normal Ubuntu, then install all the server components you need.  That way you could do your setup using a graphical environment.  It means a little memory and CPU overhead when your server is running.  If the load is low, it doesn't matter. Just having access to Synaptic might make it worthwhile.

Full Circle Magazine has a series running currently, "Installing the Perfect Server."  You might pick up a few tips from it. FCM is a free download in PDF format.

Hmm, possibly! If I do this, am I able to RDC to it from my Laptop? As I want the server to sit somewhere not being in my way, without, keyboard, monitor, etc.

---

