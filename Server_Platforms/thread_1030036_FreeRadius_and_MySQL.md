---
title: "FreeRadius and MySQL"
date: 2009-01-04
forum: Server Platforms
---

### Post by adri_ht_ on 2009-01-04
Hey guys, lately I've been trying to set up a wireless hotspot but I'm getting stuck in the authentication process between FreeRadius and MySQL.

FreeRadius 2.1.0

This is how I built the radius database:

```
# Creating MySQL Scheme (applies to freeradius 2.1.0)
root@UbuntuServer:~ # cat /etc/freeradius/sql/mysql/schema.sql | mysql -u root radius -p
```

Consequently I added an user to radcheck.. I also configured sql.conf accordingly to access the database w/ privileges. I notice that radiusd.conf in 2.1.0 doesn't have authorize nor authenticate sections. I tried without and by adding them to the end with no results.

This is what I get while running freeradius -X and testing an user from the database:

root@UbuntuServer: radtest adm1n MyPassWord localhost 0 radiusecret

```
Ready to process requests.
rad_recv: Access-Request packet from host 127.0.0.1 port 52754, id=160, length=57
        User-Name = "adm1n"
        User-Password = "MyPassWord"
        NAS-IP-Address = 127.0.0.1
        NAS-Port = 0
+- entering group authorize {...}
++[preprocess] returns ok
++[chap] returns noop
++[mschap] returns noop
[suffix] No '@' in User-Name = "adm1n", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] returns noop
[eap] No EAP-Message, not doing EAP
++[eap] returns noop
++[unix] returns updated
++[files] returns noop
++[expiration] returns noop
++[logintime] returns noop
++[pap] returns updated
Found Auth-Type = PAP
+- entering group PAP {...}
[pap] login attempt with password "MyPassWord"
[pap] Using CRYPT encryption.
[pap] Passwords don't match
++[pap] returns reject
Failed to authenticate the user.
Using Post-Auth-Type Reject
+- entering group REJECT {...}
        expand: %{User-Name} -> adm1n
 attr_filter: Matched entry DEFAULT at line 11
++[attr_filter.access_reject] returns updated
Delaying reject of request 1 for 1 seconds
Going to the next request
Waking up in 0.9 seconds.
Sending delayed reject for request 1
Sending Access-Reject of id 160 to 127.0.0.1 port 52754
Waking up in 4.9 seconds.
Cleaning up request 1 ID 160 with timestamp +452

```

Any tips/help will be greatly appreciated. Thanks

---

### Post by adri_ht_ on 2009-01-04
UPDATE: I found the authorize section which was in /etc/freeradius/sites-enabled/default and added the 'sql' line to it. It is working but for some reason a user that has a combination of upper-lower case password is getting rejected while one with just lower case gets accepted. Here is the log attempt:

```
++[sql] returns ok
++[expiration] returns noop
++[logintime] returns noop
++[pap] returns updated
Found Auth-Type = PAP
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!    Replacing User-Password in config items with Cleartext-Password.     !!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!! Please update your configuration so that the "known good"               !!!
!!! clear text password is in Cleartext-Password, and not in User-Password. !!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
+- entering group PAP {...}
[pap] login attempt with password "MyPass"
****[pap] Using CRYPT encryption.****
[pap] Passwords don't match
++[pap] returns reject
Failed to authenticate the user.
Using Post-Auth-Type Reject
+- entering group REJECT {...}
        expand: %{User-Name} -> adm1n
 attr_filter: Matched entry DEFAULT at line 11
++[attr_filter.access_reject] returns updated
Delaying reject of request 6 for 1 seconds
Going to the next request
Waking up in 0.9 seconds.
Sending delayed reject for request 6
Sending Access-Reject of id 99 to 127.0.0.1 port 40604
Waking up in 4.9 seconds.
Cleaning up request 6 ID 99 with timestamp +712
Ready to process requests.

```

The line in bold shows a peculiar difference that takes place in the authentication. The authentications that get accepted are usually passed as clear-text password instead. 

Thanks

---

