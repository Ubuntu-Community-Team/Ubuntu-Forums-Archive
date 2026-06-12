---
title: "Ubuntu 12.04.2 Samba 4.0.0 and Webmin"
date: 2013-04-17
forum: Server Platforms
---

### Post by Roswebnet on 2013-04-17
[COLOR=#000000][FONT=Calibri]Hi everyone[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]Paul Ferrill in his &#8220;Samba 4 review&#8221;[/FONT][/COLOR]
[[FONT=Calibri][COLOR=#0000ff][http://review.techworld.com/applications/3422029/samba-4-review/?view=review&pn=2](http://review.techworld.com/applications/3422029/samba-4-review/?view=review&pn=2)[/COLOR][/FONT]]("http://review.techworld.com/applications/3422029/samba-4-review/?view=review&pn=2")
[COLOR=#000000][FONT=Calibri]has managed to get work the samba4module of Webmin with samba 4. After long research,I did not find how he did it. (ISC DHCP implementation was much easier)[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]It seems to me the tweak method should be not sodifferent from ISC DHCP. However, I do not know the location of all Samba 4.0.0alpha 18 requested files by Webmin.[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Any help will appreciated.[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]Thank you.[/FONT][/COLOR]
[ATTACH=CONFIG]241472[/ATTACH][ATTACH=CONFIG]241473[/ATTACH]

---

### Post by Roswebnet on 2013-04-21
No one? :(

---

### Post by JnPson on 2013-04-24
You could run ```
locate smb.conf
``` and all the other files in webmin and replace the paths for every module in module configuration of the samba 4 server.  I run Samba 4.0.5 and the path for my version is ```
/usr/local/samba/etc/smb.conf. 
```

//JnPson

---

### Post by Roswebnet on 2013-05-14
[SIZE=3][COLOR=#000000][FONT=Calibri]I saw your message only today. Strange that I did not got a mail... Thank you JnPson, your comment was a very helpful. However I need to run a [/FONT][/COLOR][/SIZE]
```
[SIZE=3][COLOR=#000000][FONT=Calibri]updatedb [/FONT][/COLOR][/SIZE]

```[SIZE=3][COLOR=#000000][FONT=Calibri]command to update a file database to the actual status.
How did you config: Full path to smbd? Package from Ubuntu does not have smbd,nmbd,winbind.

P.S. Maybe you know something about LDAP authentication? I am stack here:
[http://ubuntuforums.org/showthread.php?t=2137560](http://ubuntuforums.org/showthread.php?t=2137560)
[/FONT][/COLOR][/SIZE]

---

### Post by Roswebnet on 2013-05-19
Oh! Understood. You use the git/tar version of samba4. I use Ubuntu 12.04.2  samba4 package. Now it is a 4.0.1 version.

---

### Post by Toxic64 on 2013-05-19
Hi,

Samba 4 from Git is 4.0.5 version.
 I wrote a tutorial (and a script for the lazy) to install it [http://ubuntuforums.org/showthread.php?t=2146198](http://ubuntuforums.org/showthread.php?t=2146198)

anyway ***smb.conf*** is generally located in ***/etc**.*

---

### Post by Roswebnet on 2013-05-24
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT]Hi Toxic64
thank you! I already tried one time to set up from git. And it worked wel, till I reboot the server (US12.04.2). After this I could not start samba4 anymore. However, Samba4 from repository (4.0.1) working good. I cannot manage it from Webmin, but I can add or remove the users, join w8 client from RSAT.
However, I cannot do following things: 
ldap auth from Ubuntu server via putty; 
ldap auth/group from squid.
I followed those tutorials:
[http://zachbethel.com/2013/04/10/linux-ldap-authentication-with-samba4/](http://zachbethel.com/2013/04/10/linux-ldap-authentication-with-samba4/)
[http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing](http://www.linuxgfx.co.uk/karoshi/documentation/wiki/index.php?title=Samba4_Testing)
With no luck. 
In addition, getent passwd on samba4 server working good. But one time more I cannot log in from putty as [EMAIL="administrator@domain.local"]administrator@domain.local[/EMAIL] or domain\administrator  or just administrator. Even other accounts are not working. Access denied. L
However, squid ldap_auth helper working good but only with Administrator account no other will be accepted. According this page:
[http://www1.it.squid-cache.org/Versions/v3/3.1/manuals/squid_ldap_auth.html](http://www1.it.squid-cache.org/Versions/v3/3.1/manuals/squid_ldap_auth.html) 
```
/usr/lib/squid3/squid_ldap_auth -u cn -b "cn=Users,dc=odm,dc=lan" 10.1.1.1
Administrator Pa$$w0rd
OK
```
 
I feel really strange about it.
 
Thank you.

---

### Post by Toxic64 on 2013-05-25
yep your samba server did not start well on 4.0.5 because git doesn't give a start script as it's distribution specific but my script corrects that problem and handles an upstart script for any git version of samba.( for Ubuntu)

for the rest , sorry I don't know.

Edit: maybe this will help: [http://acksyn.org/?p=475](http://acksyn.org/?p=475)

---

### Post by Roswebnet on 2013-05-25
I used this tutorial:
[http://www.jadota.com/2013/01/installing-samba4-on-ubuntu-12-04/](http://www.jadota.com/2013/01/installing-samba4-on-ubuntu-12-04/)
In addition, I did some extra like:
```

# /etc/init.d/apparmor stop
# update-rc.d -f apparmor remove
# aptitude remove apparmor
# aptitude remove apparmor-utils

```
 
I read somewhere that apparmor can cause a problem when working together with git samba.
 
I will report later if I have success on your Edit.

---

