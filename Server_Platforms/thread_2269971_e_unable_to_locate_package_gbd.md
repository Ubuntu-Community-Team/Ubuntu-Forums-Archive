---
title: "e: unable to locate package gbd"
date: 2015-03-19
forum: Server Platforms
---

### Post by anthasam on 2015-03-19
Hello,

i am am trying to set up samba on my Ubuntu server in virtualBox.
straight after a fresh install of Ubuntu I have run [FONT=courier new]apt-get update && apt-get upgrade -y [/FONT]with no problems.
next step was to install the following: [FONT=courier new]apt-get install git build-essential libacl1-dev libattr1-dev libblkid-dev libgnutls-dev libreadline-dev python-dev python-dnspython gbd pkg-config libpopt-dev libldap2-dev dnsutils libbsd-dev attr krb5-user docbook-xsl libcups2-dev libpam0g-dev ntp -y[/FONT]
This returned the line [FONT=courier new]E:unable to locate package gbd[/FONT]
I thought it might be something to do with sources.list so I checked that. The last two sections after the security https were commented out so I removed the ## in front of the https.
I still got the message about gbd
I'm not sure what else to try?
Any help would be greatly appreciated, 
Thank you.

---

### Post by steeldriver on 2015-03-19
Hello and welcome to the forums

What package are you looking for exactly? Given the other development packages in your apt-get list, are you perhaps looking for the GNU Debugger? That would be **gdb **rather than **gbd**

---

### Post by anthasam on 2015-03-19
oh thank you thankyou so much, just one tiny little spelling mistake, I feel so silly but so relieved it's working now. Thankyou :D

---

