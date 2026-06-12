---
title: "Hacker on my gateway?"
date: 2008-12-10
forum: Server Platforms
---

### Post by Shwick2 on 2008-12-10
I'm running fully update Ubuntu 8.04 (as of today).

I did a "users" out of the blue and saw "root shwick shwick" and I only had two ssh sessions open to my gateway.

I checked if there was an additional ssh client running, as that is the only thing that I have exposed on the internet side:

```

root      6069     1  0 Dec09 ?        00:00:00 sshd: shwick [priv]
shwick    6071  6069  0 Dec09 ?        00:00:01 sshd: shwick@pts/0
root     13731     1  0 Dec09 ?        00:00:00 sshd: shwick [priv]
shwick   13734 13731  0 Dec09 ?        00:00:00 sshd: shwick@pts/2
root     14653     1  0 Dec09 ?        00:00:00 /usr/sbin/sshd

```

Looks like just my two shwick clients.

I get an email whenever someone logs on via ssh, so I checked all those, no suspicious ips.  Also grepped auth.* and saw only logins from my ip on the lan.

I installed rkhunter, did a scan and got 0 rootkits found, but got a warning on hidden folders:

```

   Checking for hidden files and directories       [ Warning ]
[19:57:09] Warning: Hidden directory found: /dev/.static
[19:57:09] Warning: Hidden directory found: /dev/.udev
[19:57:09] Warning: Hidden directory found: /dev/.initramfs

```

Is there a way to check exactly how the root user is logged in right now, and what it is doing?

I recently installed x11vnc and made a failed startup script for it, could that be doing something?

Thanks.

---

### Post by hictio on 2008-12-10
> **Shwick2 said:**
> 
I installed rkhunter, did a scan and got 0 rootkits found, but got a warning on hidden folders:

```

   Checking for hidden files and directories       [ Warning ]
[19:57:09] Warning: Hidden directory found: /dev/.static
[19:57:09] Warning: Hidden directory found: /dev/.udev
[19:57:09] Warning: Hidden directory found: /dev/.initramfs

```



Have you checked what's inside of those directories?
Another thing, if you have been compromised, and the sh*t head was a bit competent, this might be the first thing to erase, but you should check anyway, issue on the console or terminal the commands:

who
last
lastlog

Also, it is very useful to limit, via /etc/ssh/sshd_config, the users who are allowed to login via SSH.
Use the 'AllowUsers' directive.

---

### Post by hictio on 2008-12-10
> **Shwick2 said:**
> 
I installed rkhunter, did a scan and got 0 rootkits found, but got a warning on hidden folders:

```

   Checking for hidden files and directories       [ Warning ]
[19:57:09] Warning: Hidden directory found: /dev/.static
[19:57:09] Warning: Hidden directory found: /dev/.udev
[19:57:09] Warning: Hidden directory found: /dev/.initramfs

```


Just checked on my Root Kit Hunter setup, those hidden directories are pretty common, you should edit, via sudo, the config file '/etc/rkhunter.conf' to skip getting warnings on those dirs.

But don't take my word, do a Google on that, security its capital.

Once you are sure, you have to edit the above configuration file, and uncomment the lines:

```

#ALLOWHIDDENDIR=/dev/.udev
#ALLOWHIDDENDIR=/dev/.static
#ALLOWHIDDENDIR=/dev/.initramfs

```

---

### Post by Shwick2 on 2008-12-10
I started another x11vnc session and I see another shwick user. I think my startup script started a sudo x11, which is why I saw the extra root user.

Thanks for the help.

---

### Post by kustomjs on 2008-12-15
other thing you could do is if you have a router turn off any open ports from internet site and keep the connection inside of the network like internal not external access. because for me I am currently behind a linksys router and only port I have open is 80 and rest of the ports are closed off like port 21,22 etc.....

---

### Post by albandy on 2008-12-15
do a finger from console and see where the users are connected.

sudo apt-get install finger
finger

---

