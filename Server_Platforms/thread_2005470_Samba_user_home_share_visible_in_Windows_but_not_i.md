---
title: "Samba user home share visible in Windows but not in Ubuntu"
date: 2012-06-17
forum: Server Platforms
---

### Post by d4wntracker on 2012-06-17
I've used the standard options in smb.conf to enable sharing of the user's home folder.
```

security = user

[homes]
    comment = Home directories
    browsable = no
    writable = yes

...
    valid users = %S
```


When I use Windows' file explorer to connect to the server, it sees the Home directory of the user (+ the public share).

But when I connect my Ubuntu machine to the server, it will only show the public share, not the Home directory. Even though both machines are connecting to the server with the same account.

What could cause this?

---

### Post by Morbius1 on 2012-06-17
One doesn't browse to a [homes] share. One has to ask for it explicitly.

A Windows client does that by design since it sends the Windows' user's local login username and password automatically - without being asked - when it probes the LAN.

Linux / Samba thinks that's goofy, so to reproduce on Linux what windows does ask for it a special way:
```
nautilus smb://server-name/user-name
```

---

### Post by volkswagner on 2012-06-17
You can access it by specifying the path as Morbius1 mentioned, or you can change the smb.conf to allow the share to be browsable.

Change:

```
browsable = no
```

to

```
browsable = yes
```

Then restart SAMBA.

Also It helps to have the username and password match the SAMBA server with the client pc you are using.

---

### Post by Morbius1 on 2012-06-18
> **volkswagner said:**
> You can access it by specifying the path as Morbius1 mentioned, or you can change the smb.conf to allow the share to be browsable.

Change:

```
browsable = no
```to

```
browsable = yes
```Then restart SAMBA.

Also It helps to have the username and password match the SAMBA server with the client pc you are using.
You can set it to browseable if you want to and the remote Linux user will in fact see that a "homes" share exists but when he tries to access it he will get the following message:
> Failed to open "homes"
Failed to mount Windows share.Why? 

Because there is nothing in [homes]. The user's home directory share is created "on the fly" when the remote user asks for it - and asks for it by user name. A Windows client does this naturally whereas Linux does not. So Linux always has to pass the user name when asking for the share:
```
 nautilus smb://server-name/user-name
```Note: that's not "server-name/share-name" - you have to specify the user-name instead.

---

### Post by d4wntracker on 2012-06-18
Wow! I learn so much here in so little time. :)

Thanks guys! Will try some different settings when I get home.

[SIZE="1"]Sidenote: My Windows clients use the same username and password as the Ubuntu server.[/SIZE]

---

### Post by Morbius1 on 2012-06-18
> **d4wntracker said:**
> [SIZE=1]Sidenote: My Windows clients use the same username and password as the Ubuntu server.[/SIZE]
Just so there's no confusion about this the way the standard [homes] share works there must be a server user created that matches the client user's name - Linux clients as well. That's the only way they will get a home directory to access.

Then that user will have to be added to the samba password database. The passwords can match if you want but that's not required.

---

### Post by d4wntracker on 2012-06-18
> **Morbius1 said:**
> Just so there's no confusion about this the way the standard [homes] share works there must be a server user created that matches the client user's name - Linux clients as well. That's the only way they will get a home directory to access.

Then that user will have to be added to the samba password database. The passwords can match if you want but that's not required.

Please elaborate the above.
Adding the user to the Samba password database?

-----

While installing my server I made sure that when asked to create the initial user I entered the username that I use on my Windows machines.
i.e.: richard

So on my Windows machines, my Ubuntu laptop and the Ubuntu server I have 1 user with the username "richard". And each machine uses the same password for this user.

I've enable the [homes] share that comes with the Samba configuration.
```

[homes]
   comment = Home Directories
   path = /home/%S
   writable = yes
   guest ok = no
   read only = no
   create mask = 0755
   directory mask = 0755
   valid users = %S
```

On my Windows system I can see the [homes] share, connect to it, and even map it as network drive to auto-connect whenever I log into Windows.

On my Ubuntu laptop I can browse the shares and see the [homes] share. But when I double click to connect it gives an error "Failed to mount Windows share".

While double clicking the [pub] share opens it up.

```
[pub]
    comment = Public Network Share
    path = /var/shares/pub
    browsable = yes
    guest ok = no
    create mask = 0655
    directory mask = 0755
    writable = yes
```

Oh, and yes, you've probably noticed. I'm pretty new at Ubuntu server management. I wish to learn, but online documentation fails me. Therefore I hope some people here can tell me what I'm doing wrong when it comes to setting up home-shares for users.

---

### Post by Morbius1 on 2012-06-18
> Please elaborate the above.
Adding the user to the Samba password database?The way this is done on a standard server is for every remote client:
** You create a user on the server itself complete with his own home directory.
** Then you add that Linux user to the samba database:
```
sudo smbpasswd -a user-name
```It appears that you did the first part but not the second part. The only thing I can think of that would make this work is if you had the following package installed: **libpam-smbpass** which forces the samba password to match the login password for that linux user. I don't like libpam-smbpass for that reason but they didn't give me a vote on the matter and I'm kind of surprised it's installed by default.
> So on my Windows machines, my Ubuntu laptop and the Ubuntu server I have  1 user with the username "richard". And each machine uses the same  password for this user.
Well, you didn't need to create a [homes] share in that case since there is only one user. You could have created a share of your home directory instead. Two different things.
> 
[homes]    
comment = Home Directories    
path = /home/%S    
writable = yes    
guest ok = no    
read only = no    
create mask = 0755    
directory mask = 0755 
   valid users = %SThat will work I suppose but you are defeating the reason the [homes] share was created. [homes] shares traditionally don't have paths. They don't need them. With [homes] a share of the users' home directory will be created automatically by samba when asked for by the client.

Windows automatically does that but for your linux client you need to ask for it explicitly:
```
nautilus smb://server-name/richard
```If you want it to show up and act like your [pub] share then don't use a [homes] share. Simply share your home directory:
```
[MyHome]
path = /home/richard
read only = no
valid users = richard
```[COLOR=Blue][I]
As a side note[/I][/COLOR]: The [homes] share was created to reduce the maintenance effort on system administrators in an enterprise environment. Instead of having to create a separate home share for every single user you would use the [homes] share and simply add users to the server and set the samba password. Samba does the rest and creates the share automatically.

---

### Post by d4wntracker on 2012-06-22
If you want it to show up and act like your [pub] share then don't use a [homes] share. Simply share your home directory:
```
[MyHome]
path = /home/richard
read only = no
valid users = richard
```

/\
||
||
this.fixed.it!

Thanks! :)

---

