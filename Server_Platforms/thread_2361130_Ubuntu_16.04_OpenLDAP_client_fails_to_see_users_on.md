---
title: "Ubuntu 16.04: OpenLDAP client fails to see users on OpenLDAP Server"
date: 2017-05-12
forum: Server Platforms
---

### Post by bo-guo on 2017-05-12
[COLOR=#000000][FONT=&amp]We have OpenLDAP Server and phpLDAPAdmin installed on a Ubuntu 16.04 server and were able to add OUs and Users.

[/FONT][/COLOR][COLOR=#000000][FONT=&amp]On my Ubuntu 16.04 desktop client, I installed OpenLDAP Client per instruction at [/FONT][/COLOR][https://www.server-world.info/en/note?os=Ubuntu_16.04&p=openldap&f=3](https://www.server-world.info/en/note?os=Ubuntu_16.04&p=openldap&f=3)[COLOR=#000000][FONT=&amp].

I was able to access ldap through commands such as 
[/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]ldapsearch -x -h superior -b "dc=gisticinc,dc=com"[/FONT][/COLOR]
```

However, ```
[COLOR=#000000][FONT=&amp]getent passwd[/FONT][/COLOR]
``` would not show any [COLOR=#000000][FONT=&amp]user from the LDAP Server.  And [/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]su <uid>[/FONT][/COLOR]
```[COLOR=#000000] would give the [/COLOR]"[COLOR=#000000][FONT=&amp][FONT=courier new]No passwd entry for user <uid>[/FONT]"[/FONT][/COLOR] error.

I would appreciate any suggestions!

Incidentally, [COLOR=#000000][FONT=&amp]I found installing OpenLDAP client was more troublesome than installing the server.   Wonder if anyone has found ways to automate the OpenLDAP client deployment on multiple desktops? 
  
[/FONT][/COLOR]

---

### Post by TheFu on 2017-05-12
Did you remember the PAM stuff? That's all I got.

---

### Post by bo-guo on 2017-05-13
Yes, I did the PAM configuration stuff by following the instructions in the referenced link.

---

### Post by bo-guo on 2017-05-13
I dug further and found the fix to be install [COLOR=#333333][FONT=monospace]nss-pam-ldapd [FONT=arial]instead of [/FONT][/FONT][/COLOR][COLOR=#333333][FONT=monospace]nss-pam-ldap[FONT=arial], [/FONT][FONT=arial]per this [/FONT][Discussion]("https://askubuntu.com/questions/797896/16-04-server-enabling-ldap-authentication-causes-systemd-logind-to-fail/810478#810478") 
[/FONT][/COLOR]
```
sudo apt-get -y install libnss-ldapd libpam-ldap ldap-utils nslcd
```

Then add a line to [FONT=&amp]/etc/pam.d/common-session 
[/FONT]
```
[FONT=&amp]session required pam_mkhomedir.so skel=/etc/skel umask=0022[/FONT]
```

---

### Post by bo-guo on 2017-05-17
Correction and additional notes-

The installation did not work on 14.04!  I only realize this when the server failed to start after a reboot.  

So I upgrade it 14.04 to 16.04 and apply the client installation.  This worked ONLY after I renamed /etc/pam.d/common-* files before installing the client.  Apparently, we need to ensure fresh pam.d/common- files.

Hope this helps.

---

