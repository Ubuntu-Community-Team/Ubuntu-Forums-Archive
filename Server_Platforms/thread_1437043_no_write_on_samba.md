---
title: "no write on samba"
date: 2010-03-23
forum: Server Platforms
---

### Post by doru001 on 2010-03-23
On Ubuntu 8.04 LTS both Desktop and Server I tried this: 
```
net usershare add tst ~/tst dave:F
```and the result was that, from another machine, I could read but could not write to the shared directory. 

I did not modify /etc/samba/smb.conf. 
Permissions look fine for tst: 
drwxr-xr-x 2 dave dave 4096 2010-03-22 18:33 tst

If there is some easy way to make tst writeable over samba, for example by modifying smb.conf, please tell me.

---

### Post by jrssystemsnet on 2010-03-23
Are you certain that you're actually logging in from the remote machine as dave, rather than as the guest user?

Try temporarily chmodding the folder 777, then see if you can create a file in it... and see who owns that file, if you can.

---

### Post by doru001 on 2010-03-23
> **jrssystemsnet said:**
> Are you certain that you're actually logging in from the remote machine as dave, rather than as the guest user?

Try temporarily chmodding the folder 777, then see if you can create a file in it... and see who owns that file, if you can.

Thanks for reply. 
I connect as dave, with a password, so there is no doubt that I access the directory through samba as dave. 
I checked permissions again, owner and group is dave. 
I did 777 again right now, the situation is the same. 

I thought that Gnome or Nautilus are meddling, but on the server I did not installed any GUI. 

I am open to new ideas.

---

### Post by jrssystemsnet on 2010-03-23
> **doru001 said:**
> Thanks for reply. 
I connect as dave, with a password, so there is no doubt that I access the directory through samba as dave.

Sure there is still doubt - if guest logins are allowed, any number of problems could end up in you getting mapped to guest user even if you tried to authenticate as dave.

 
> I did 777 again right now, the situation is the same. OK, now if you couldn't write even with the folder chmod 777, then THAT tells us something.

See if you can find a share definition in /etc/samba/smb.conf to correspond to this.  I'm not actually that familiar with how Samba's "net" command works, but I'm quite familiar with smb.conf. :)

---

### Post by doru001 on 2010-03-24
> **jrssystemsnet said:**
> Sure there is still doubt - if guest logins are allowed, any number of problems could end up in you getting mapped to guest user even if you tried to authenticate as dave.

OK. 

 > **jrssystemsnet said:**
> OK, now if you couldn't write even with the folder chmod 777, then THAT tells us something.

I could not write. 

> **jrssystemsnet said:**
> See if you can find a share definition in /etc/samba/smb.conf to correspond to this.  I'm not actually that familiar with how Samba's "net" command works, but I'm quite familiar with smb.conf. :)

I only want to share a subdirectory of my home directory, from console (text mode, not using Gnome / Nautilus), with write permissions, and only accessible to me. If you know what should I do to /etc/samba/smb.conf to obtain this, please let me know. Samba is quite complicated and I don't have time to learn it now, but all I want to do is to share one directory to one user, so I hope it is possible to do that in a simple way. 

Thanks for your answers, 
Doru

---

### Post by jrssystemsnet on 2010-03-24
In /etc/samba/smb.conf, add a section which looks like this:

```
[sharename]
comment = this is the text I see as a description of the share when I browse it
path = /path/to/share
# note: no "valid users" line necessary if you want all users to be able
# to browse this share
valid users = usernameiwanttoaccessthissstuff
# note: uncomment this if you want users without valid Samba accounts on this
# machine to browse this share
# guest OK = yes
writeable = true
```

If you did not **un**comment "guest OK = yes", you will also need to make Samba accounts for any users who need to browse the share.  First, if there is not already a **system** account, you must create one:

```
you@box:~$ **sudo useradd nameofmynewsambauser**
```

Now you have to create a Samba account for that system account:

```
you~box:$ **sudo smbpasswd -a nameofmynewsambauser**
```

Now you've created your new samba user; this username and password are the credentials that will be needed for anybody browsing into this share (unless you set "guest ok = yes", in which case credentials won't be needed at all).

---

### Post by doru001 on 2010-03-24
Thanks, this looks clear and simple, and I saved it for reference. The smbpasswd was new for me. 
But it still does not work - I can not write. I have even closed down iptables, but in vain. Probably there is a cause hidden somewhere, and smb.conf is not responsible for this. So I will postpone this issue for better times. 
Thanks again for your effort. 

Doru

---

### Post by doru001 on 2010-03-25
Now I can write from XP only, not from another Ubuntu. 

I suppose that: 
```
USER ADD name [password]
```
even though the user was a system user already did the trick. 

However, there is no refresh in XP, I have to do F5 in order to see the changes. 

There are many protocols in samba, and no easy way to know them.

---

### Post by doru001 on 2010-03-29
This is the /etc/samba/smb.conf which I snapped from the Ubuntu 8.04 LTS Desktop machine - which had a shared folder working with write access, configured in the GUI - and copied on the Ubuntu 8.04 LTS Server, and made the write work, too. 

As you see, there is no path in it, because I used: 
net usershare add name path comment username:F
to create the share in /var/lib/samba/usershares/. 
You have to put the comment, otherwise username:F will be seen as a comment, the man net manual should have been [comment [acl]], instead of [comment] [acl]. 
You can list usershares with: 
net usershare info
See man net (usershare). 
You also need to do: 
sudo /etc/init.d/samba restart
after you change smb.conf. 

All that was missing was passdb backend tdbsam. Of course, you might want to encrypt passwords etc. 
[http://www.linuxtopia.org/online_books/network_administration_guides/samba_reference_guide/18_passdb_21.html](http://www.linuxtopia.org/online_books/network_administration_guides/samba_reference_guide/18_passdb_21.html)

```
[global]
#   workgroup = WORKGROUP    
#   server string = %h server (Samba, Ubuntu)
#   dns proxy = no
#   log file = /var/log/samba/log.%m
#   max log size = 1000
#   syslog = 0
#   panic action = /usr/share/samba/panic-action %d
#   encrypt passwords = true
   passdb backend = tdbsam
#   obey pam restrictions = yes
#   invalid users = root
#   unix password sync = yes
#   passwd program = /usr/bin/passwd %u
#   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
#   pam password change = yes
#map to guest = bad user
#   socket options = TCP_NODELAY
#   usershare allow guests = yes
```This is working on XP, too, but only after a few minutes after the change for reading, and after another few minutes after change for writing. Also, you need F5 after every change to see it, unless 
you uncomment the rest and wait a few minutes until it will start to see this, too. It might help to do: 
```
net use \\server\share /delete
net use \\server /delete
net use # lists connections 
```on XP and to reboot XP and linux server.

---

