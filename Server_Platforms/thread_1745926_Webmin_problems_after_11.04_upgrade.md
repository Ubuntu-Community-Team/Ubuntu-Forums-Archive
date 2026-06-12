---
title: "Webmin problems after 11.04 upgrade"
date: 2011-05-01
forum: Server Platforms
---

### Post by theprintingplace on 2011-05-01
Hello everyone. I just upgraded to 11.04 and everything seems to be working OK except I can no longer log into Webmin. I tried uninstalling it and re-installing but it didn't make any difference. All I get is "Login failed. Please try again."

I have rebooted several times to no avail. I can login via terminal or ssh with no problem and everything I am trying worked before the upgrade. Any solutions?

Thanks!

---

### Post by elico on 2011-05-01
it seems like webmin is not working with 11?
try 
[http://sourceforge.net/projects/webadmin/forums/forum/55377/topic/4497498/](http://sourceforge.net/projects/webadmin/forums/forum/55377/topic/4497498/)

and if you do ask me try to look at the webmin logs...
also..
try installing lynx and acces
apt-get install lynx
lynx [https://localhost:10000](https://localhost:10000)
it's a text based web browser that works ok with webmin.

---

### Post by collisionystm on 2011-05-01
> **theprintingplace said:**
> Hello everyone. I just upgraded to 11.04 and everything seems to be working OK except I can no longer log into Webmin. I tried uninstalling it and re-installing but it didn't make any difference. All I get is "Login failed. Please try again."

I have rebooted several times to no avail. I can login via terminal or ssh with no problem and everything I am trying worked before the upgrade. Any solutions?

Thanks!

Probably permissions on the webmin folder.

---

### Post by James78 on 2011-05-01
Do keep in mind though that Webmin only officially supports LTS releases so..

---

### Post by Demented ZA on 2011-05-02
I had this exact same problem and my solution was exactly the same as in elico's link, except I found it out the hard way. 

On one of my servers this didn't work though. Logging in as root for the moment. No big deal: its not connected to external networks as I'm in the process of replacing it with a new server.

---

### Post by Dawbs on 2011-05-08
Had the same problem with 11.04 server
 
I think I read somewhere that it's because the root user account wasn't activated before the first install of webmin.
 
I believe this only effects the webmin root account NOT your systems root account.
 
Solution that worked for me:
 
@ terminal screen:
sudo find / -name changepass.pl     (=   /usr/share/webmin)
cd /usr/share/webmin
sudo find / -name miniserv.conf       (=   /etc/webmin/)
sudo ./changepass.pl /etc/webmin/ root typeyourpasswordhere
 
If your found files are in a different place then obviously change the location.
 
Hope this helps

---

### Post by rb1234 on 2011-05-16
I had the same problem after 11.04 upgrade.

After adding my accont to th users group, now I can login with my user name.

---

### Post by tallthom on 2011-07-10
Has anyone got any newer solutions to this problem?  I just started having this problem after upgrading to 11.04 a few days ago.  

In particular, I don't want to enable root access on the server, so I'd like to try and fix it by figuring out why Webmin doesn't authorize correctly using the /etc/passwd file once the upgrade finished.

The miniserv.error and miniserv.log show nothing during start up or authentication failure that indicates a problem.  Is there somewhere else I can look to troubleshoot this problem?

---

### Post by NZReaction on 2011-07-11
> **tallthom said:**
> Has anyone got any newer solutions to this problem?  I just started having this problem after upgrading to 11.04 a few days ago.  

In particular, I don't want to enable root access on the server, so I'd like to try and fix it by figuring out why Webmin doesn't authorize correctly using the /etc/passwd file once the upgrade finished.

The miniserv.error and miniserv.log show nothing during start up or authentication failure that indicates a problem.  Is there somewhere else I can look to troubleshoot this problem?

sudo ./changepass.pl /etc/webmin/ youruser typeyourpasswordhere

Please see this link for more details [https://help.ubuntu.com/community/WebminWithoutARootAccount](https://help.ubuntu.com/community/WebminWithoutARootAccount)

---

### Post by AllGamer on 2011-08-14
the solution that worked for me was

```
sudo passwd root
```

---

### Post by Cas07 on 2011-08-28
I found a much simpler workaround for this in [Bug #748615]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/748615/comments/9").

Open the sudoers file for editing:

```
sudo visudo 
```

then add the following line, replacing ***admin*** with your own login username:

```
admin ALL=(ALL) ALL
```

---

