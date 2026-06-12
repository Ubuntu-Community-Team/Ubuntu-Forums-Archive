---
title: "Ubuntu Server 8.04 + LDAP. Can't start slapd after dpkg-reconfigure"
date: 2010-04-27
forum: Server Platforms
---

### Post by sonik88 on 2010-04-27
Actually the title says it all. I am trying to get an LDAP Server up and running on Ubuntu Server 8.04 with openldap but after the configuration with:

sudo dpkg-reconfigure slapd

when I try:

/etc/init.d/slapd start

or

/etc/init.d/slapd restart


I get the following error message:

nikos@box:~$ /etc/init.d/slapd start
No configuration file was found for slapd at /etc/ldap/slapd.conf.
If you have moved the slapd configuration file please modify
/etc/default/slapd to reflect this.  If you chose to not
configure slapd during installation then you need to do so
prior to attempting to start slapd.
An example slapd.conf is in /usr/share/slapd


ANY help will be appreciated.

Thanks!

---

### Post by windependence on 2010-04-28
You overwrote your slapd.conf file with the upgrade. You need to set up slapd.conf. To get started, you can copy the default config file like this:

```
sudo cp  /usr/share/slapd/slapd.conf /etc/ldap/slapd.conf
```

Then restart your slapd service.

-Tim

---

### Post by sonik88 on 2010-04-29
Tim first of all thanks for the answer. I have already copy the default config but the result is the same.

I found this guide [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

I will try to follow it and post results.

---

