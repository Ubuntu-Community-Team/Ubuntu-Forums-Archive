---
title: "1st Day With Ubuntu Please Help"
date: 2007-05-02
forum: Server Platforms
---

### Post by nomb on 2007-05-02
Hey guys I used to use Fedora and then I accidentally deleted the /libs folder and messed it up.  That computer was a server so I decided to take the oppertunity and try a different distro.  I have ubuntu 7.06 server installed and I installed the ubuntu-desktop.  Figured it might be easier since i've never used it before.

I am having some issues I was hoping to get some help on.  

1.  I couldn't find anything to configure the firewall. (graphically that is) so i installed firestarter.
2.  if I open a web browser and point to localhost u see apahce's index of but when I use another computer on the lan it times out.
3.  I then used firestarter and allowed the port 80 to the incoming rule set but it still times out. 

I also tried to do a service httpd restart from root but it tells me there is no service command.  How does that work within ubuntu?
Another thing about services.  There is a services settings program under admin but why doesn't it include things liks ssh which is on my computer.  How do I restart ssh?

One more, I was using turbogears to make a wiki but now im wondering what the best way to make more interactive web pages really is.  I got stuck with turbogears and am willing to try something different. 

Thanks,
nomb

---

### Post by visik7 on 2007-05-02
1. never used firestarter btw should be ok
2. no problem here with feisty and apache2 with no configuration edit
3. try to disable firestarter and run iptables-save |egrep -v "^#|^:|^*" (if there is only "COMMIT" as output (or no output at all) from this command every firewall rules is off otherwise run iptables -F ; iptables -t nat -F ; iptables -t mangle -F
at this point you should be able to connect to apache from everywhere
ensure to use apache2 (aptitude install apache2) apache returns some errors when I've tried to install it
good luck

---

### Post by nomb on 2007-05-02
Even when I turn firestarter off it times out.

How do u start and stop services in ubuntu?

---

### Post by nomb on 2007-05-02
Fixed part of the issue.

When you use firestarter, not only do you have to open the port (80 in this case) but also put in which hostnames/ip address are allowed to connect to it.

Can anyone answer my services questions?  For instance, I just edited my ssh_config file, how do I restart it so the changes take affect?

---

### Post by MJN on 2007-05-03
All the control scripts are (usually) in /etc/init.d/ - see man init.d for details.

Briefly, they are typically executed with an option to indicate what you want to do e.g. **/etc/init.d/ssh stop** would stop SSH, **/etc/init.d/ssh restart** would... you get the idea. Run it without options to give you the possibilities:

```

/etc/init.d/ssh
 * Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart}

```

Most, if not all, would require you to have super-user privileges to control them hence prefix the above with **sudo** and enter your password when prompted.

Mathew

---

### Post by Brazen on 2007-05-03
You should check out webmin.  Go to [www.webmin.com](www.webmin.com) and there are deb and rpm binaries (you'll use deb on ubuntu).  Webmin has the best interface for configuring firewall settings, IMO.  It is also super simple to start and stop services and control what services start on bootup, and many many other things.

Basically after installing the deb, browse to [http://localhost:1000](http://localhost:1000) and log in with your Ubuntu user.

Also, if your Apache server is in production use, you can issue a```
sudo /etc/init.d/apache reload
```which will get the new configuration options, but not kick off anyone browsing the Apache websites like a "restart" would.

---

### Post by nomb on 2007-05-03
I've used webmin before but I prefer to configure iptables from the cli.  My problem is there isn't the init script in init.d for iptables to restart them after I make changes.

---

### Post by MJN on 2007-05-03
In one of your other threads I've referred to a link to enable you to write your own (I don't use iptables but I'm pretty sure you don't need to 'restart' it for changes to take effect anyway - it's a live config).

Mathew

---

### Post by Brazen on 2007-05-03
> **nomb said:**
> I've used webmin before but I prefer to configure iptables from the cli.  My problem is there isn't the init script in init.d for iptables to restart them after I make changes.

Are you editing the /etc/iptables.up.rules file?  After editing the file, you need to do ```
iptables-restore /etc/iptables.up.rules
```or maybe it's just```
iptables-restore
```Something like that.

---

