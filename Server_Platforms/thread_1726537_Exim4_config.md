---
title: "Exim4 config?"
date: 2011-04-11
forum: Server Platforms
---

### Post by yeleek on 2011-04-11
Hi,

I want to setup a mail server on the local network which will be used by the various machines to send mail too.  Its goal will be strictly for internal mail, and I don't want it relaying mail to the Internet or accepting external connections.

10.1.1.1 is the LAN interface of the server, it also has a WAN interface.

Given the requirement and having run sudo dpkg-reconfigure exim4-config the below is the content of my update-exim4.conf.conf.  Is that enough?  

```
dc_eximconfig_configtype='internet'
dc_other_hostnames='home.local'
dc_local_interfaces='127.0.0.1 ; 10.1.1.1'
dc_readhost=''
dc_relay_domains='none'
dc_minimaldns='true'
dc_relay_nets='none'
dc_smarthost=''
CFILEMODE='644'
dc_use_split_config='true'
dc_hide_mailname=''
dc_mailname_in_oh='true'
dc_localdelivery='mail_spool'
```

Thanks.

---

### Post by yeleek on 2011-04-14
Anyone?  Pls.

---

