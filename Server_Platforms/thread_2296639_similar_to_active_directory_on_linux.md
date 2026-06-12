---
title: "similar to active directory on linux"
date: 2015-09-27
forum: Server Platforms
---

### Post by calin_ionut on 2015-09-27
Hello everyone. I need some help please! I replaced all the windows computers to linux (32 PC) and one server (ubuntu server 14.04).

The PC ware in AD (users ware created on the WS2012 R2 AD and had some restriction using group policy).

For me as a teacher i only need one student account for now (and maybe in the future i will create more). I don`t use any windows machine in my lab, so what do you recommend to use similar to AD?

Cheers!

---

### Post by Bucky Ball on 2015-09-27
You might have a look [here]("https://duckduckgo.com/?q=active+directory+alternative+linux") for some clues.

---

### Post by darkod on 2015-09-27
Actually with Samba4 you can create AD similar to windows AD. Windows workstations can even join such AD and work with the linux domain controller. If you ever need it...

You can read more at: [https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO](https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO)

---

### Post by calin_ionut on 2015-09-27
what do you think about 389 Directory Server?

---

### Post by sandyd on 2015-09-27
Use OpenLDAP.

After setup, don't bother with manually creating users/etc via command line. There are multiple GUI tools to do that now.

Here is a good guide on setup: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-openldap-and-phpldapadmin-on-an-ubuntu-14-04-server](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-openldap-and-phpldapadmin-on-an-ubuntu-14-04-server)

Personally, I much prefer apache directory studio to configure OpenLDAP as I don't need to have a webserver, but you can use phpLDAPadmin if you like.

---

### Post by TheFu on 2015-09-28
> **calin_ionut said:**
> what do you think about 389 Directory Server?

**FreeIPA** is a more complete solution for what you probably want - you'll want Samba4 too. I don't think there is a FreeIPA server (which uses 389) for any Ubuntu LTS.  Most of those deployments are on RHEL/CentOS; there is an Ubuntu client, but I've never used it.

Don't forget that MSFT-AD is a tightly controlled, single vendor, solution so nothing will be exactly like it in the F/LOSS world.  Authentication is a separate thing from policy. Policy is controlled by the userid, groups, directory/file permissions and the server settings. File permissions are central to Unix security. I good understanding of those is absolutely critical for desktop AND server security. To maintain server policies/settings, most organizations have moved to "DevOps" techniques.  Something like Ansible, Puppet, Chef - there are others.  This applies to "desktop" policies as well.

If you want something like roaming profiles, put the user's HOME onto NFS storage and mount it to each system in the same location. As long as the userid/groupids match across all the systems (even without LDAP), it will work as you desire.

---

### Post by calin_ionut on 2015-10-05
> **sandyd said:**
> Use OpenLDAP.

After setup, don't bother with manually creating users/etc via command line. There are multiple GUI tools to do that now.

Here is a good guide on setup: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-openldap-and-phpldapadmin-on-an-ubuntu-14-04-server](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-openldap-and-phpldapadmin-on-an-ubuntu-14-04-server)

Personally, I much prefer apache directory studio to configure OpenLDAP as I don't need to have a webserver, but you can use phpLDAPadmin if you like.

I follow those tutorials (setup openldap, setup user auth, configure phpldap), so far so good but i have little problem. If the server is going down, or the network, i can`t log in even localy. In this file /etc/nsswitch.conf i have:

```

passwd:         compat ldap
group:          compat ldap 
shadow:         compat ldap 

```

but if i remove ldap from group it let me to login local (with the server down). 

It is ok to remove ldap from group ?

---

