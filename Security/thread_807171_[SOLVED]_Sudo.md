---
title: "[SOLVED] Sudo"
date: 2008-05-25
forum: Security
---

### Post by DeMus on 2008-05-25
Hi,

Everytime when I use sudo in a terminal I get the following message:

jan@2-Quad:~$ sudo ls -l
sudo: unable to resolve host 2-Quad
[sudo] password for jan: 

ls -l is just an example instruction.
I gave my computer the name 2-Quad, so that's the host name. But what does the message mean and how can I make it go away? I don't see that something is not working, I just get the message. Can somebody tell me what is wrong, where it is wrong and how to change it?

Thanks,
DeMus

---

### Post by HalPomeranz on 2008-05-25
The error message means that the system is unable to translate your system's hostname into an IP address.  The easiest way to fix this is to update your /etc/hosts file.  Find a line that looks like:

```
127.0.0.1		localhost.localdomain localhost
```

Change it to

```
127.0.0.1		localhost.localdomain localhost 2-Quad
```

That should make the error go away.

---

### Post by molotov00 on 2008-05-25
That seems like a wierd error. Do we know why it happened to him? Seems like something that shouldn't happen. Bug?

M

---

### Post by HalPomeranz on 2008-05-25
> **molotov00 said:**
> That seems like a wierd error. Do we know why it happened to him? Seems like something that shouldn't happen. Bug?

If the original poster changed the system hostname after the initial install, it seems possible to me that the hostname may not have been propagated to all necessary system files.  I'm not sure I'd call it a bug until I know exactly how the hostname change was done.

DeMus, can you describe exactly how you changed the name of your machine?

---

### Post by chrisccoulson on 2008-05-26
Could be related to [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/185209]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/185209")

---

### Post by DeMus on 2008-05-27
> **HalPomeranz said:**
> The error message means that the system is unable to translate your system's hostname into an IP address.  The easiest way to fix this is to update your /etc/hosts file.  Find a line that looks like:

```
127.0.0.1		localhost.localdomain localhost
```

Change it to

```
127.0.0.1		localhost.localdomain localhost 2-Quad
```

That should make the error go away.

I don't know why but it worked. Thanks for the help. Can you also explain it to me?

DeMus

---

### Post by HalPomeranz on 2008-05-27
> **DeMus said:**
> I don't know why but it worked. Thanks for the help. Can you also explain it to me?

Sure.  The problem was that there was no configuration on your system to allow it to convert your machine's hostname into an IP address.  That's what the error message "unable to resolve host 2-Quad" means-- to "resolve" a host means to convert that name into an IP.

Name resolution can happen in any one of several ways.  On many networks you use DNS for name resolution, but there's also networked databases such as LDAP and NIS.  Failing that, you can use /etc/hosts files, which is what I had you configure here.

Each line in the /etc/hosts file lists an IP address and one or more host names associated with that IP.  All I told you to do was to add your machine's hostname to the /etc/hosts entry for the loopback interface (127.0.0.1).  sudo doesn't care which interface IP it gets when trying to resolve your hostname, just that it gets *something *as a result of the lookup.  Once you added the name to a valid entry in the /etc/hosts file, sudo was satisfied and stopped throwing the error.

---

### Post by DeMus on 2008-05-27
> **HalPomeranz said:**
> If the original poster changed the system hostname after the initial install, it seems possible to me that the hostname may not have been propagated to all necessary system files.  I'm not sure I'd call it a bug until I know exactly how the hostname change was done.

DeMus, can you describe exactly how you changed the name of your machine?

No, I can not. It must have happened when I tried to install and configure Samba, but I can not tell you anymore what I had to do to make Samba work. I'm sorry.

DeMus

---

### Post by divadeepak on 2009-02-15
hi,
im a new user of ubuntu and i now have this "unable to resolve host problem". i tried "sudo gedit/etc/hosts" changed the host name in the first line but still no luck.and now i dont know how to find the line 127.0.0.1		localhost.localdomain localhost.

i need urgent help and i need to get rid off a recycler once the terminal starts accepting my commands.

---

### Post by cariboo on 2009-02-15
Press Alt-F2 and type:

```
gksu gedit /etc/hosts
```

this will open /etc/hosts in gedit the file should look something like this:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	jack
192.168.1.200	willy
192.168.1.202	minibuntu
192.168.1.1	router

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Jim

---

### Post by dantattoo on 2009-03-27
OK 
this is solved
Well I have a similar issue but when I look in the file strings there is not hosts or host file do I need to create it or does the alt+F2 method do this 

I have a static address 

I use the kde and gnome desktops and have 2 nic's installed 

I appreciate the assistance

I have recently installed lighttpd and modules for it

---

