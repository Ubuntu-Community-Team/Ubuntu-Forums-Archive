---
title: "Connecting to my ReadyNas NV+ server"
date: 2011-03-10
forum: Security
---

### Post by mastia on 2011-03-10
Hi,

I have been connecting fine to the Nas server using Windows XP. The problem there was viruses getting across with ease. I recently started using Ubuntu and cannot get through to stuff on the server with it.

The data is in folders that are password protected. I cannot get past the password prompt using the same correct password I use on XP.  

Both the server and desktop are on the same workgroup. It is a fresh ubuntu copy so I do not think the firewall in there since I cannot even find it.

Please help, thanks.

---

### Post by cariboo on 2011-03-10
I'm assuming that you are connecting to the nas with smbclient. Hve you created a samba password? To do so, open a terminal and type;

```
sudo smbpasswd -a <user_name>
```

then enable the password:

```
sudo smbpasswd -e <user_name>
```

---

### Post by hawkmage on 2011-03-10
How are you trying to mount the share?  Is it as a "Windows Share"

Since you were using windows you have at least have CIFS enabled.  If it is only CIFS is enabled then you will need to mount it with using the type "cifs".  The user and password should be the same as you used from Windows.  There is also a ReadyNAS forum at [http://www.readynas.com/forum/](http://www.readynas.com/forum/)

---

### Post by mastia on 2011-03-11
Thanks for the replies.

I did try setting the smb username and password but still no luck.

The server does mount. I can get to the shared folders. What i find rather awkward is that even for a folder that is not password protected, I still cannot get access.

Below are screen shots, hopefully they'l yield more insight.

Another thing I don't get is the domain field, am in a workgroup!

---

### Post by shutterbc on 2011-03-12
At first I was assuming you had user based security, but then I noticed it was share level security.  There's actually a solution posted on the forums, have you taken a look at this yet?

[http://ubuntuforums.org/showthread.php?t=1170587](http://ubuntuforums.org/showthread.php?t=1170587)

Add the following lines to /etc/samba/smb.conf
[global]
# THE LANMAN FIX
client lanman auth = yes
client ntlmv2 auth = no

---

### Post by mastia on 2011-03-28
Brilliant man, works like a charm. Thanks

---

