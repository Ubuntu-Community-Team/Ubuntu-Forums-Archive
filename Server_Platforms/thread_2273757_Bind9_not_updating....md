---
title: "Bind9 not updating..."
date: 2015-04-15
forum: Server Platforms
---

### Post by ben152 on 2015-04-15
Bind9's does not update it's records even though I am updating the serial number in the SOA and the refresh is set to 30 minutes. What am I missing that forces bind to look for changes? By the way this is for the master, if I do a bind9 restart it will update itself and then send the updates to the slaves...

Anyone have any ideas?

---

### Post by SeijiSensei on 2015-04-15
You have to tell BIND to refresh its configuration after you make the changes.  You can either restart the process as you have done already, or you can tell the server to reload the configuration by issuing the command:
```
sudo killall -HUP named
```
which sends the "SIGHUP" signal to the daemon, which is called named, and triggers the reloading. See "[man named]("http://manpages.ubuntu.com/manpages/trusty/man8/named.8.html")" for details.

---

### Post by ben152 on 2015-05-01
Thanks for the info. So then it's necessary to setup a cron job to do this automatically? 

Forgive me for asking such basic questions. Working a new job with the freedom to finally move away from Microsoft products... not much experience with Ubuntu first IT job in 1990 was a Unix shop but that was only for 3 years and I really hadn't touched it much other than to toy around with it since then. I realize that I have a TON of catching up to do.






> **SeijiSensei said:**
> You have to tell BIND to refresh its configuration after you make the changes.  You can either restart the process as you have done already, or you can tell the server to reload the configuration by issuing the command:
```
sudo killall -HUP named
```
which sends the "SIGHUP" signal to the daemon, which is called named, and triggers the reloading. See "[man named]("http://manpages.ubuntu.com/manpages/trusty/man8/named.8.html")" for details.

---

### Post by SeijiSensei on 2015-05-01
> **ben152 said:**
> Thanks for the info. So then it's necessary to setup a cron job to do this automatically? 
No, you only need to do it when you update a zone's records.  When you restart named, it will send notifications to the slaves of those zones for which the server is the master.  The slave will compare the serial number in the notice with its own and update the zone as needed.  

I've managed a couple dozen domains over the years.  Changes in the zone records are pretty rare for public domains, though more common on intranet DNS servers, especially ones that [automatically maintain a reverse zone file for the local network clients]("https://blog.bigdinosaur.org/running-bind9-and-isc-dhcp/").  Even then the only time you'd need to force named to reread its zone files is when you change forward records like A, MX and NS.  The reverse zone is updated automatically.

> **ben152 said:**
> Forgive me for asking such basic questions. Working a new job with the freedom to finally move away from Microsoft products... not much experience with Ubuntu first IT job in 1990 was a Unix shop but that was only for 3 years and I really hadn't touched it much other than to toy around with it since then. I realize that I have a TON of catching up to do.

Not at all. It's why I'm here :D

If you want a book to read, I recommend Craig Hunt's [TCP/IP Network Administration](http://shop.oreilly.com/product/9780596002978.do).  While it's over a decade old, things haven't changed much when it comes to basic services like DNS and DHCP. Hunt's book is comprehensive and readable.

Of course, there's always Google.  One especially effective tool is to search for exact strings from error messages.  Get to know the contents of /var/log as well.  Here's an example from /var/log/syslog which shows a BIND master sending a notification for a domain and a slave's confirmation of the "zone transfer:"
```
Apr 28 15:27:07 mail named[7791]: zone example.com/IN: sending notifies (serial 2014042901)
Apr 28 15:27:08 mail named[7791]: client 10.10.10.10#56826: received notify for zone 'example.com'
```

Most configuration information is stored in /etc.  User configurations are usually stored as "hidden" files, ones that begin with a dot, in the users' home directories.  Many of them reside in $HOME/.config.

---

### Post by nerdtron on 2015-05-01
> **ben152 said:**
> Bind9's does not update it's records even though I am updating the serial number in the SOA and the refresh is set to 30 minutes. What am I missing that forces bind to look for changes? By the way this is for the master, if I do a bind9 restart it will update itself and then send the updates to the slaves...

Anyone have any ideas?

After you made the changes on the zone files, you need to restart the bind9 service:
```
sudo service named restart 
```


And I think if you correctly configured the slave, you don't have to do anything as it will update itself once it sees the master is updated.

---

