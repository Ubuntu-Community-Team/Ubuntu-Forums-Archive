---
title: "fwlogwatch webserver?"
date: 2007-08-06
forum: Server Platforms
---

### Post by eentonig on 2007-08-06
Anybody got fwlogwatch up and running with the interactive webserver?

I can't seem to get that service to work. And documentation is limited as it seems.

---

### Post by ruibernardo on 2007-08-06
Hi eentonig,

I got fwlogwatch to work after reading it's documentation, it's configuration files and some little help of this: [http://www.linux-magazine.com/issue/50/Firewall_Logfile_Analyzers.pdf](http://www.linux-magazine.com/issue/50/Firewall_Logfile_Analyzers.pdf).

To make the service running in Debian/ubuntu, you have to execute

```
sudo dpkg-reconfigure fwlogwatch
```

This will change the /etc/default/fwlogwatch to make it active (debianized thing). It will ask some questions:

1. Would you like fwlogwatch as a daemon (realtime mode)?
- Answer "Yes".

2. Add new firewall rules (or take another action) in case of alert?
- Answer "No" so it don't want fwlogwatch to add rules to iptables.

The other questions are about mailing warnings to the administrator. I don't use it because it sends too much mails, but this is configurable on the configuration file.

Now, to make the realtime web interface work, you have to edit the configuration file in /etc/fwlogwatch/fwlogwatch.config.

sudo nano /etc/fwlogwatch/fwlogwatch.config

There are many options and very well commented. Most of them are commented so you have to uncomment to activate them. Some of them you don't have to activate because they are already set up by the debianized config.

I had to activate and change the following options: "input =" option (I use ulogd). I think that you have to activate some oher options: "parser =", the group of options starting with "src_ip" and "data_amount =" .

The real thing for the web interface is in the group of options starting with "**server_status = yes**". Uncomment them (don't forget to add a user and password as explained in the comments).

Restart the fwlogwatch service 

```
sudo /etc/init.d/fwlogwatch restart
```

and point your browser to [http://localhost:888](http://localhost:888).

NOTE: you can use fwlogwatch to create a html file by running it as a normal user (check the command line options on the PDF link above).

---

### Post by eentonig on 2007-08-07
thx. 

I missed the "sudo dpkg-reconfigure fwlogwatch". Where did you find this documented? 

I've got it running now.

---

### Post by ruibernardo on 2007-08-07
> **eentonig said:**
>  
I missed the "sudo dpkg-reconfigure fwlogwatch". Where did you find this documented? 



Found that in the deeps of my computer: :)

/usr/share/doc/fwlogwatch/README.Debian

Glad it worked.

---

### Post by eentonig on 2007-08-07
Ah. Stupid me. I thought that the internet or the apps website would give some explanation on how to set up the program.

---

### Post by ghanks on 2008-01-20
To make FWLogwatch functional for my Shorewall setup, I do the following:
Install apt-get install fwlogwatch
*****install as daemon
*****No mail
apt-get build-dep fwlogwatch
LOOK AT [http://packages.debian.org/unstable/net/fwlogwatch](http://packages.debian.org/unstable/net/fwlogwatch)
Verify all DEPENDS are satisfied..
debconf
libc6
postfix
sysklogd
zlib1g
*****
...
Edit /etc/fwlogwatch/fwlogwatch.config
parser=nfs
dst_port = on
html = yes
realtime_response = yes
server_status = yes
bind_to = 0.0.0.0
listen_port = 888
status_user = 
// status password below is for blank password!
status_password=UGFufMo4FEB5Q
refresh = 120

---

