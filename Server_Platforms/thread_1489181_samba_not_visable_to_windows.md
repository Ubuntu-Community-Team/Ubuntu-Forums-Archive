---
title: "samba not visable to windows"
date: 2010-05-20
forum: Server Platforms
---

### Post by Strongman332 on 2010-05-20
hello all
i am trying the set up a simple home server and I can see it on windows computers, also i cannot accesses it with its name only its ip

```
[global]
browseable = yes
security = share
workgroup = WORKGROUP

[files]
guest ok = yes
path = /srv/Samba/files
read only = no
browsable = yes
public = yes
writable = yes
```

---

### Post by CharlesA on 2010-05-20
Have you started nmbd?

I ended up setting up a local DNS server since I was having problems with name resolution.

---

### Post by Strongman332 on 2010-05-20
no i have never heard of it, i would try it now but i am away from the server right now, any advice on how to set it up.

---

### Post by CharlesA on 2010-05-20
You can check to see if it is running with this command:

```
service nmbd status
```

If it isn't running, you can start it with this:

```
sudo service nmbd start
```

---

### Post by dtfinch on 2010-05-20
A last resort (and generally accepted wrong way to do it) would be to give your Ubuntu system a static IP and edit %windir%\system32\drivers\etc\lmhosts (no extension) on Windows to associate the name with the IP.

---

### Post by CharlesA on 2010-05-20
You wouldn't need to edit lmhosts. Edit the hosts file instead.

---

### Post by Strongman332 on 2010-05-20
I have it running. but it hasn't fixed the problem.

---

### Post by CharlesA on 2010-05-21
You'd need to either run a local dns server or add an entry into the hosts file.

---

### Post by Strongman332 on 2010-05-22
well looks like i am going to have to Google how to do that. well any ways thanks for all your help. and if any one has a good guy for dns noobs, it would be nice to have

---

### Post by bab1 on 2010-05-22
> **Strongman332 said:**
> well looks like i am going to have to Google how to do that. well any ways thanks for all your help. and if any one has a good guy for dns noobs, it would be nice to have

There really are no comprehensive guides to setting up name services for small LAN networks.  I believe that's because there is more than one way to do it correctly and they conflict with each other.  In addition there is plenty of misinformation that has been repeated long enough to become close to gospel.  Some of that misinformation (opinion) is already this thread.

That being said, lets see if we can get this accomplished.  There are a few items we need to get started.  

We will need to know: [LIST]
[*]How many hosts (both clients and servers) are in your network?
[*]How you are handling IP addressing in this network now(e.g. static or dynamic)?
[*]Do you have hosts the come and go from the network (Laptops, iPhones, etc.)
[*] What is the make and model of the router you are using in the network?
[*] How are you creating the Samba shares; with smb.conf or Nautilus?
[*] Is the smb.conf file you attached the entire file? 
[/LIST]

Be as specific as you can with the answers.

---

### Post by CharlesA on 2010-05-22
> **bab1 said:**
> In addition there is plenty of misinformation that has been repeated long enough to become close to gospel.  Some of that misinformation (opinion) is already this thread.

Can you elaborate, please. :)

---

