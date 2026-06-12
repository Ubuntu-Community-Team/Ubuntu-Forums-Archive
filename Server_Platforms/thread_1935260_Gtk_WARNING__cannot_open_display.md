---
title: "Gtk_WARNING **: cannot open display:"
date: 2012-03-03
forum: Server Platforms
---

### Post by watsgoodg on 2012-03-03
Hello everyone,

I have just built out my first Ubuntu Server 11.1 and having trouble configuring file sharing.  I was able to install Samba without any problems however when I try to modify the smb.conf file I get the follow error:

gksu gedit /ect/samba/smb.confsudo
(gksu:18429): Gtk-WARNING **:Cannot open display:

If anyone could help get this server up and running that would be great!



I have read through Apress.Beginning.Ubuntu.Server.Administration.From.Novice.to.Professional

---

### Post by volkswagner on 2012-03-03
> **watsgoodg said:**
> Hello everyone,

I have just built out my first Ubuntu Server 11.1 and having trouble configuring file sharing.  I was able to install Samba without any problems however when I try to modify the smb.conf file I get the follow error:

gksu gedit /ect/samba/smb.confsudo
(gksu:18429): Gtk-WARNING **:Cannot open display:

If anyone could help get this server up and running that would be great!



I have read through Apress.Beginning.Ubuntu.Server.Administration.From.Novice.to.Professional

gedit will only work if you have x server running.  The default server install does not run X windows.  There are other command line editors that are installed by default.  My preference is nano.

Try 
```
sudo nano /etc/samba/smb.conf
```

There is a menu at the bottom for the shortcuts in nano.  <ctrl + o> writes your changes (you will need to press enter to confirm you are writing to the file) and <ctrl + x> will exit.  

Always create a backup before edit.

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

---

### Post by watsgoodg on 2012-03-03
> **volkswagner said:**
> gedit will only work if you have x server running.  The default server install does not run X windows.  There are other command line editors that are installed by default.  My preference is nano.

Try 
```
sudo nano /etc/samba/smb.conf
```

There is a menu at the bottom for the shortcuts in nano.  <ctrl + o> writes your changes (you will need to press enter to confirm you are writing to the file) and <ctrl + x> will exit.  

Always create a backup before edit.

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```

Thank you for the fast response volkswager.  I was able to modify the smb.conf file.  I used this guide to configure the file.  I am able to see the share but the username and password i created does not authenticate.  I just keeps asking for the password.

[http://vassie.name/setting-up-a-simple-samba-share-with-ubuntu](http://vassie.name/setting-up-a-simple-samba-share-with-ubuntu)

---

### Post by volkswagner on 2012-03-04
Do you have a linux user to match your samba user?

Int the tutorial is has you create samba user ben.   This assumes there is a linux user ben.  This is true since the tutorial point the usermap to the same name.

> sudo nano /etc/samba/smbusers

> Then map your** Linux account** to your Windows (Samba) account by adding

```
ben = Ben
```


You can also run testparm to check you samba config.

```
testparm
```

---

### Post by watsgoodg on 2012-03-04
> **volkswagner said:**
> Do you have a linux user to match your samba user?

Int the tutorial is has you create samba user ben.   This assumes there is a linux user ben.  This is true since the tutorial point the usermap to the same name.





```
ben = Ben
```


You can also run testparm to check you samba config.

```
testparm
```

Ok.  That most likely be the issue I am trying to connect from a windows machine.  If that is the case any idea how to configure the smb.conf for a windows user?

thanks,
-J

---

### Post by volkswagner on 2012-03-04
The process is the same.  For SAMBA to work, you need to have a real linux user on the system.  Just add the user with the same name you used when you followed the tutorial.

To add a linux user try:

```
sudo adduser ben
```

You can use the same password as when you created "smbpasswd -a ben".

---

### Post by watsgoodg on 2012-03-04
> **volkswagner said:**
> The process is the same.  For SAMBA to work, you need to have a real linux user on the system.  Just add the user with the same name you used when you followed the tutorial.

To add a linux user try:

```
sudo adduser ben
```

You can use the same password as when you created "smbpasswd -a ben".

I am still not able to access.  I can see the share but the username and password i created test test does not authenticate.  I have tried it from a xp and win7 machine.  I do have a domain running could this cause a conflict?

thanks,
-J

---

### Post by volkswagner on 2012-03-04
First test the user/password works directly on the server.

From the server access the share using smbclient.  You may need to install it if it is not already installed.

```
smbclient //ServernameOrIPaddress/sharename -U ben
```

You should be prompted for your password.  You should then be connected and be able to list files and such.

to exit the smb> prompt.
```
quit
```

Your SAMBA server is joined to a domain?  You may need to add that to the username?  I'm not sure as I have no experience with this type of setup.

---

### Post by watsgoodg on 2012-03-04
> **volkswagner said:**
> First test the user/password works directly on the server.

From the server access the share using smbclient.  You may need to install it if it is not already installed.

```
smbclient //ServernameOrIPaddress/sharename -U ben
```

You should be prompted for your password.  You should then be connected and be able to list files and such.

to exit the smb> prompt.
```
quit
```

Your SAMBA server is joined to a domain?  You may need to add that to the username?  I'm not sure as I have no experience with this type of setup.

Ok.  I tried the username and password to the share and received the following after putting in the password:

tree connect failed: NT_STATUS_BAD_NETWORK_NAME

---

### Post by volkswagner on 2012-03-04
Either your username or password is incorrect or your share path is incorrect.

Try changing the password
```
sudo smbpasswd ben
```

You may try to add your user explicitly in the share definition.

```
valid users = ben, tom, user1
```

So it would like like this in smb.conf

```
[shareName]
	comment = Specific  Users
	path = /path/to/share
	valid users = ben, tom, me, you, user1
	read only = No
	create mask = 0660
	directory mask = 0771
```

Or just one user if that is all you want to have access to it.

---

