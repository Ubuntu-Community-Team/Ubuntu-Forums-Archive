---
title: "Ldap client can't authenticate"
date: 2011-10-13
forum: Server Platforms
---

### Post by trongbang on 2011-10-13
My problem is: my ldap client can't authenticate using accounts on Ldap server.

**My configuration:**
+Ldap server: 192.168.56.102
> cn=admin, dn=example, dn=com
> user1, ou=people, dn=example, dn=com

+Ldap client: 192.168.56.101
I followed this: [http://beginlinux.com/index.php/server_training/server-managment-topics/116-server-management/1017-ldap-client-on-ubuntu-804](http://beginlinux.com/index.php/server_training/server-managment-topics/116-server-management/1017-ldap-client-on-ubuntu-804)

**Testing**
1. reboot ldap client
2. use: user1/password
3. it shows authentication failure

**Experiment**
1. I used the same steps as I did for ldap client above
2. I used: ssh user1@192.168.56.102
3. use: user1/password
4. Authentication succeeded 

can anybody help me out please?

---

### Post by trongbang on 2011-10-13
hi, really ashamed!

I was stuck with this for 2 weeks. That's why I decided to try to get some help from here.

After posting this, I suddenly discovered a wrong configuration and it works now.

Thanks anyway guys!

---

### Post by SwitchLink on 2011-10-14
What was the correct config, if you don't mind my asking.

---

### Post by trongbang on 2011-10-14
> **SwitchLink said:**
> What was the correct config, if you don't mind my asking.

Absolutely don't mind bro!

I run dpkg-reconfigure ldap-auth-conf.
In the step that we need to declare ldapi:///

I changed to ldap://192.168.56.102 (my server)

That's all. :)

---

