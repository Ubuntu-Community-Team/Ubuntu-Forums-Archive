---
title: "PUTTY Access Denied"
date: 2004-12-11
forum: Repositories &amp; Backports
---

### Post by tonym on 2004-12-11
I have three machines,  two were running Debian Sarge and one Windows 98SE.  I could use ssh between the Debian machines and could use PUTTY on Windows to access the other machines.

I have switched one of the Debian machines to Ubuntu.  I can still ssh from the Debian machine to Ubuntu but I cannot use PUTTY to access from Windows  -  I just get "Access Denied".  I have not been able to find anything in logs in  /var/log on the Ubuntu machine and cannot find any reference to this problem anywhere on the Ubuntu site or via Google.

Can anyone suggest where else I should look.

Regards

Tony Middleton.

---

### Post by superTP on 2005-01-11
I had this same problem.  My XP machine at work running PuTTY could not connect to my server at home.  I modified the /etc/ssh/sshd_config file on the server and changed the 'PasswordAuthentication' variable from 'no' to 'yes'.  I then ran '/etc/init.d/ssh restart' to restart the sshd server and I could then connect using PuTTY.  I found a good explanation for the various authentication mechanisms on the debian forums here:

[http://lists.debian.org/debian-security/2002/05/msg00343.html](http://lists.debian.org/debian-security/2002/05/msg00343.html)

Hope this helps,

Thomas

---

### Post by tonym on 2005-03-23
Thanks - this solved my problem.

---

### Post by andrei19787528 on 2007-05-15
> **tonym said:**
> I have three machines,  two were running Debian Sarge and one Windows 98SE.  I could use ssh between the Debian machines and could use PUTTY on Windows to access the other machines.

I have switched one of the Debian machines to Ubuntu.  I can still ssh from the Debian machine to Ubuntu but I cannot use PUTTY to access from Windows  -  I just get &quot;Access Denied&quot;.  I have not been able to find anything in logs in  /var/log on the Ubuntu machine and cannot find any reference to this problem anywhere on the Ubuntu site or via Google.

Can anyone suggest where else I should look.

Regards

Tony Middleton.

snip

---

### Post by rocket123 on 2009-10-22
> **superTP said:**
> I had this same problem.  My XP machine at work running PuTTY could not connect to my server at home.  I modified the /etc/ssh/sshd_config file on the server and changed the 'PasswordAuthentication' variable from 'no' to 'yes'.  I then ran '/etc/init.d/ssh restart' to restart the sshd server and I could then connect using PuTTY.  I found a good explanation for the various authentication mechanisms on the debian forums here:

[http://lists.debian.org/debian-security/2002/05/msg00343.html](http://lists.debian.org/debian-security/2002/05/msg00343.html)

Hope this helps,

Thomas

I'm getting the access denied message too. I did not have a sshd_config file, so i created one in the root of my user account. 'passwordauthentication' is set to yes. 
however, how and where do you run '/etc/init.d/ssh restart'. i don't know where to run commands.

thanks

---

### Post by januzi on 2009-10-26
Just put it into the console (that black window with the white text "bash"). You need root privileges.

---

### Post by wiggie on 2009-11-04
you need to open up a terminal, and type this into it
```
sudo /etc/init.d/ssh restart
```
it will then ask you for a password.

Ok, apart from that I am having the same problem. I changed the ```
/etc/ssh/sshd_config
``` file to allow PasswordAuthentication, restarted ssh but that didn't help.

I can log into the server with putty when I am using the LAN IP address, and that works just fine. But when I use the WAN IP adress, it asks me for the user name, which I provide, and the password, which I also provide, and I am 100% sure both are correct (since they obviously worked through the local access). Furthermore I have tried it at least 15 times, this way eliminating typos, keyboard layout issues and what have you.

Anybody have an Idea?

---

### Post by januzi on 2009-11-04
Take a look at the /var/log/ (maybe messages or sshd.log)
Take a look at the /etc/hosts.deny and /etc/hosts.allow

---

### Post by cariboo on 2009-11-05
I would suggest rocket123 start this thread all over again in [Networking & Wireless]("http:///ubuntuforums.org/forumdisplay.php?f=336"), as you will get better and faster answers to your question there, than you will stuck away on this sub forum.

---

### Post by TheCoolGoof on 2010-08-17
I had this issue and was able to fix it by NOT using the -p option in useradd and usermod to set/change the password.

 -p, --password PASSWORD       use encrypted password for the new password

Instead I created the account then ran sudo passwd <username>

---

### Post by ittopgunii on 2011-12-06
In putty configuration go to Connection, SSH & under Protocol options change Preferred SSH protocol version from 2 to 2 only and then under SSH Auth GSSAPI uncheck the Attemp GSSAPI authentication (SSH-2 only) check box and save.

---

