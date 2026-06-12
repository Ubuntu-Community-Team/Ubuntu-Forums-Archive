---
title: "Bind9 Unable To Start"
date: 2009-06-17
forum: Server Platforms
---

### Post by SoulMazer on 2009-06-17
So, I recently installed an Ubuntu Jaunty Server and ticked the boxes that said "DNS Server" and "LAMP Server". But now when I try to start bind9, it says it fails ("rndc: neither /etc/bind/rndc.conf nor /etc/bind/rndc.key was found"). I read around on some forums and tried to run "sudo rndc-confgen -a" to generate a new key. As a result, I got "rndc-confgen: unable to create "/etc/bind/rndc.key"

 Here is the last few lines of my error log after running "/etc/init.d/bind9 start".

> 
loading configuration from '/etc/bind/named.conf'
non:0: open: /etc/bind/named.conf: permission denied
loading configuration: permission denied
exiting (due to fatal errors)


By simply looking at the log, I thought it was some sort of permissions problem but I don't know why, as I ran "sudo /etc/init.d/bind9 start" (note the sudo).


My /etc/default/bind9 file:
> 
# run resolvconf?
RESOLVCONF=yes

# startup options for the server
OPTIONS="-u bind-t /var/lib/named"


 So, what is going on here and how can I fix it?

Thank you very much in advance.

---

### Post by terazen on 2009-06-17
What are the permissions on the /etc/bind folder?

---

### Post by SoulMazer on 2009-06-18
It is "-rw-r--r-- root root". I am pretty sure that means it is owned and read/write for root, and read only for everybody else.

---

### Post by gombadi on 2009-06-18
> 
It is "-rw-r--r-- root root"


For a directory/folder like /etc/bind it will start with a "d" i.e. something like 

```

human@dave:~$ ls -ld bind
drwxr-xr-x 2 human human 4096 2009-06-18 19:12 bind

```

It will also need the "x" so programs can list the directory contents.

---

### Post by terazen on 2009-06-18
You posted the user was Bind so that user should have at least read permissions.

---

