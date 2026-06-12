---
title: "How can I properly set up my hostname, IP Address and FQDN on Ubuntu server 16.04"
date: 2017-11-16
forum: Server Platforms
---

### Post by jaytelford on 2017-11-16
Hi, 

I have been trying to set up my servers hostname, IP Address and and FQDN but I seem to have ran into a problem.  typing ***vi /etc/hostname*** into terminal opens up the hostname file and shows me that my hostname is set as **arcnet** and when I type ***hostname*** into terminal, I get **arcnet** as the response, so my hostname is set correctly.

However, when I type ***hostname --domain*** I get ***localdomain*** as the response and typing ***hostname --fqdn*** gives me **localhost.localdomain. **

Looking at my hosts file by typing ***vi /etc/hosts*** into terminal I see the following set up:

```


127.0.1.1        localhost
127.0.1.1        localhost.localdomain   arcnet
77.68.84.150     lumaria.online

# The following lines are desirable for IPv6 capable hosts

::1     localhost ip6-localhost ip6-loopback

ff02::1   ip6-allnodes
[COLOR=#000000][FONT=Menlo]ff02::2 ip6-allrouters
[/FONT][/COLOR]
```

Lastly typing ***hostname --ip-address*** gives me 127.0.1.1, which is also not correct.

Can you please tell me what I have done wrong and how I can correctly set up my hosts file so that my correct IP address domain and fqdn display correctly.

Thanks

---

### Post by TheFu on 2017-11-17
What do you want the hostname and domainname to be?

There are 4 things necessary.
[LIST=1]
[*]sudoedit /etc/hosts
[*]sudoedit /etc/hostname
[*]sudo hostname
[*]sudo domainname
[/LIST]

Each of these must be performed with elevated priviledges - i.e.   sudoedit for editing and  sudo to set the hostname.  More info on the commands is found inside the manpage for each.  The modified data must be consistent across each. Also, there are options for the hostname & domainname commands that you'll need to look up.

Oh - and you can ignore all the NIS references.  That doesn't apply here.

From the manpage:
```
       The  recommended  method of setting the FQDN is to make the hostname be
       an alias for the fully qualified name using /etc/hosts,  DNS,  or  NIS.
       For  example,  if  the  hostname was "ursula", one might have a line in
       /etc/hosts which reads

              127.0.1.1    ursula.example.com ursula
```
There is more worth reading about the name resolution order on the system which might impact the fqdn answers.  In 30 yrs, I've never seen host.conf used, so you can ignore that part.  nsswitch.conf OTOH, might need modification - probably not, but maybe.

---

