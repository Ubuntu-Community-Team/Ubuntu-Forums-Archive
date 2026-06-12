---
title: "Unable to stop Pure-ftpd"
date: 2005-03-09
forum: Server Platforms
---

### Post by Belldandy on 2005-03-09
Hi everyone,

I did a search for this and looked around on google for an answer to this, but nothing seems to be working. I just installed Pure-FTPD on my Ubuntu box, but I needed to make some changes in the ports it uses because of a firewall. When I try to stop Pure-FTPD, It says the server is stopping, however, when I try to restart it I get the following message:

```

xxx@xxx:~ $ sudo /usr/sbin/pure-ftpd -p (ports):(ports) &
Unable to start a standalone server: Address already in use
[1] 32685
[1]   Done                    sudo /usr/sbin/pure-ftpd -p (ports):(ports)
xxx@xxx:~ $


```

With the (ports) being the specific ports I wish it to run on.

This leads me to believe that Pure-FTPD isnt being stopped properly. I have tried:

sudo invoke-rc.d pure-ftpd stop
sudo /etc/init.d/pure-ftpd stop

And nothing has worked, it also does not show up on the system monitor.

Any ideas?

Thanks in advance!

---

### Post by Belldandy on 2005-03-09
Oh wow, answered my own question, turns out Pure-FTPD runs in standalone in inetd. I commented out the ftp line in inetd.conf and all is well. :)

---

### Post by lightyear on 2005-03-16
but where does linux put these config file..... looking for it all over the place...can't find it

---

