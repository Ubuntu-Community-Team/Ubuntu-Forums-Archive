---
title: "Another question; ddclient wont update."
date: 2006-07-27
forum: Server Platforms
---

### Post by Tadhg on 2006-07-27
Right, i must be overlooking something blindingly obvious here.

I can't get my ip to update properly to dyndns.

I have a domain registered [www.futurecompass.net](www.futurecompass.net) and im registered with dyndns.org.

I had everything running perfectly in XP but i wanted to switch over to Linux on my server.

So i have apache running. All ports are fowarded properly to the server. When i put my external ip straight into a browser, my page from the comes up perfectly.

So i have ddclient on the server, but when i run ```
sudo ddclient -daemon=0 -v
``` it retrieves the ip ok from the web but than tells me ```
updating futurecompass.net: nohost: The hostname specified does not exist in the database.
```

Whats going on?

My ddcliet.conf is ```
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web,web=checkip.dyndns.org/,web-skip='IP Address'
server=members,dyndns.org
login=username
password='password'
wildcard=YES
futurecompass.net
```

I'm pretty confident I'm missing some setting or havn't set up my dny properly.

---

### Post by pablosanchezuy on 2006-07-27
"server=members,dyndns.org", should be "server=members.dyndns.org"

Also, i think you are trying to update a different account type.
Yours should be custom type.
Look at the doc files for a different config file .
That should be on /usr/share/doc/ddlcient or sort of ...

Regards .
Pablo Sánchez.

---

### Post by Tadhg on 2006-07-27
man, you are a life saver. I thought I was completely misunderstanding DNS. It's all working now. 

For anyone in the future, if you have a custom DNS you need to add ```
custom=yes yourdomainname.net/com/org
``` at the end of the config file. Everything else is the same. Run ddclient start -v to make sure everything is ok.

Thanks Pablo!

---

### Post by splendid on 2006-08-28
I get the following message:

WARNING:  unable to determine IP address

Any ideas???

---

### Post by mzar on 2008-01-04
I got same error like you.Dunno what wrong.

---

