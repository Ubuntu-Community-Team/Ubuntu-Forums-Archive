---
title: "Root user account visible in Users list"
date: 2009-02-20
forum: Security
---

### Post by VicVega on 2009-02-20
I fear that I may have done something stupid, and I need some help sorting it out. I recently installed Openssh-server on my desktop so that I can tunnel to it from my laptop. I am running Ubuntu 7.10 on the desktop. I just noticed that in System>Administration>Users and Groups, that There are two accounts. First is the root account and then my user account. The root account is not grayed out like it is on my laptop installation of 8.10. I don't recall ever enabling the root account although it is possible.

I need some advice to correct this if possible. I am aware of the implications of running as root and I use sudo when necessary.

Thanks

---

### Post by cariboo on 2009-02-20
The quick way to check if you have enabled the root account is to open a Applications-->Accessories-->Termianl and type:

```
sudo cat /etc/shadow
```

and check to see if root has a password, the output for an unmodified root account should look like this

```
root:!:14286:0:99999:7:::
```

Jim

---

### Post by VicVega on 2009-02-20
OK, it looks similar, however there are about 30 entries. Does it mean that root is enabled? If so, how do I lock it down.

Thanks

---

### Post by Nepherte on 2009-02-20
There are multiple entries because there are multiple users. For each user that exists on your system there is an entry in that file.

---

### Post by VicVega on 2009-02-20
I only have 2 users on this computer, myself and root. However, when I type the following command, there are about 30 entries.
```
sudo cat /etc/shadow

```
The entries look like services, ie. ```
sys:*:13964:0:99999:7:::
```

Does this mean that those services are running as root? If so, is this something I need to change?

Thanks

---

### Post by cdenley on 2009-02-20
```

sudo getent shadow root

```

---

### Post by VicVega on 2009-02-20
> **cdenley said:**
> ```

sudo getent shadow root

```

Here is what I have done so far:

```
sudo cat /etc/shadow
```

Output of above command:

```
root:!:13964:0:99999:7:::
daemon:*:13964:0:99999:7:::
bin:*:13964:0:99999:7:::
sys:*:13964:0:99999:7:::
sync:*:13964:0:99999:7:::
games:*:13964:0:99999:7:::
man:*:13964:0:99999:7:::
lp:*:13964:0:99999:7:::
mail:*:13964:0:99999:7:::
news:*:13964:0:99999:7:::
uucp:*:13964:0:99999:7:::
proxy:*:13964:0:99999:7:::
www-data:*:13964:0:99999:7:::
backup:*:13964:0:99999:7:::
list:*:13964:0:99999:7:::
irc:*:13964:0:99999:7:::
gnats:*:13964:0:99999:7:::
nobody:*:13964:0:99999:7:::
dhcp:!:13964:0:99999:7:::
syslog:!:13964:0:99999:7:::
klog:!:13964:0:99999:7:::
messagebus:!:13964:0:99999:7:::
hplip:!:13964:0:99999:7:::
avahi-autoipd:!:13964:0:99999:7:::
avahi:!:13964:0:99999:7:::
haldaemon:!:13964:0:99999:7:::
gdm:!:13964:0:99999:7:::
user_name:$xxx//:13964:0:99999:7::: (modified by me)
statd:!:13968:0:99999:7:::
sshd:!:14274:0:99999:7:::

```

Command:

```
sudo getent shadow root
```

Output of above command:

```
root:!:13964:0:99999:7:::
```


The above command lists the entry for root, but I am not sure what to do with this info. I need to determine if the root account is enabled and if it is, how to lock it down to the default state.

Thanks

---

### Post by kpatz on 2009-02-20
The exclamation point between the first two colons means the account is locked.

So: root:!:... is locked, while root:(gibberish):... isn't.

---

### Post by VicVega on 2009-02-20
So that would mean my root account is locked. I am just wondering why it is not grayed out in System>Administration>Users and Groups. Would that be the default result in Gutsy?

---

### Post by Nepherte on 2009-02-21
> **VicVega said:**
> I only have 2 users on this computer, myself and root. However, when I type the following command, there are about 30 entries.
```
sudo cat /etc/shadow

```
The entries look like services, ie. ```
sys:*:13964:0:99999:7:::
```

Does this mean that those services are running as root? If so, is this something I need to change?

Thanks
A lot of services run under their own user. That way they only have access to what they need and nothing else.

---

### Post by VicVega on 2009-02-21
Ok, I would like to thank everyone for the response and clearing that up for me. I am going to mark this as solved.

Thanks Again,
Dan

---

