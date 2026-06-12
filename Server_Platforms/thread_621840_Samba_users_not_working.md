---
title: "Samba users not working"
date: 2007-11-24
forum: Server Platforms
---

### Post by kenshin666 on 2007-11-24
Hello everybody,

I just installed samba on my ubuntu 7.10,
and i have one question:

My new users are not working in samba.

i added user (sudo useradd user)
maked smbpasswd (sudo smbpasswd -a user)

added share:
[Buhaltere]
comment = Buhaltere
path = /home/samba/buhaltere
browseable = yes
guest ok = no
valid users = buhaltere
writable = yes
create mask = 0700
directory mask = 0700

When am login am entering user and password pressing enter
windows asking for login and password and repeat that question.
So i cannot login.

Now i dunno where i make mistake or config file or my system setting.

My smb conf is here: [http://rafb.net/p/aee9xh47.html](http://rafb.net/p/aee9xh47.html)

Please help me

---

### Post by jonandrews on 2007-11-24
Hi. As well as adding a user, my understanding is that you have to enable the user as well, using

sudo smbpasswd -L -e logname  

(Use your own Ubuntu log-in name instead of logname )


I've shown the full process on my XP/Ubuntu networking guide at

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)


Hope that helps.

---

### Post by HermanAB on 2007-11-24
See this: [http://www.aeronetworks.ca/samba-debug-howto.html](http://www.aeronetworks.ca/samba-debug-howto.html)

and this: [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

Cheers,

H.

---

### Post by kenshin666 on 2007-11-26
Thanks for help..
But its not working for me.

I now have ~10users
and working only one.

I created new user

Added smb passwd
sudo smbpasswd -L -a logname

Enabled
sudo smbpasswd -L -e logname

Added share:

[naujokas]
        comment = Dalintis su..
        writeable = yes
        valid users = naujokas
        path = /home/naujokas


When am tried to get inside the folder at windows i get error:
" \\server is not accessible. You might not have permission to use the network resource. Contact the administrator of the server to find out if you have access permissions". 

Plese help me. Thanks

---

### Post by HermanAB on 2007-11-26
This is a network configuration problem, not a Samba problem.  Test things with ping and telnet.  Ensure that the machines are in the same subnet. Check the firewall settings - Samba runs mostly on port 445.

Cheers,

Herman

---

### Post by kenshin666 on 2007-11-26
Yes i see now,
But when i upload file or create dir i not see new files/dirs until  i refresh network dir.
Where now should be mistake?

---

### Post by crouton on 2007-11-29
I think that's an issue with the client rather than with Samba.

---

