---
title: "ssh &amp; ldap errors, need help please"
date: 2012-10-29
forum: Server Platforms
---

### Post by sjhupp on 2012-10-29
Backgournd:

I am an admitted linux noob, but have made good progress over the past couple years (havetheknowhow site is very helpful), and now I'm a happy user of ubuntu server (12.04) on my little HP microserver, just used at home as a media server. It's been humming away for some time, but I decided to whack on Zentyal, as I was planning to upgrade it's role to a home gateway also.
But that presented issues with samba (had samba3 running, zentyal has samba4 = broken shares/configs), and after securing my preferred gateway device (Juniper SRX), I wanted to resume the server only role.
So I tried to purge Zentyal, with moderate success. 

I now find I have issues getting in via SSH - I get the prompt for password, enter it, but it seems to hang for ages, then disconnect from server. Even sudo can take a long time for password recognition.
I really need ssh access, as box is headless.

trying cat /var/log/auth.log I see
....
Oct 29 20:54:01 Holly cron[1371]: nss_ldap: could not connect to any LDAP server as cn=zentyal,dc=zentyal-domain,dc=lan - Can't contact LDAP server
Oct 29 20:54:01 Holly cron[1371]: nss_ldap: failed to bind to LDAP server ldapi://%2fvar%2frun%2fslapd%2fldapi: Can't contact LDAP server
Oct 29 20:54:01 Holly cron[1371]: nss_ldap: could not search LDAP server - Server is unavailable

So some zentyal config remains, but there's no zentyal packages loaded to remove. Is this related to ssh hangs?

What I want to do is blow away ldap, as don't believe I've set that up before, but some google only found the same question, or how to set it up. Do I need it?
Any suggestions?

With no remote access, I can only run commands at home at night, but happy to gather any useful intel that could help.
Thanks.

---

