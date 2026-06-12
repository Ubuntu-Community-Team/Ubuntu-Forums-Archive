---
title: "dhclient  error"
date: 2008-05-25
forum: Server Platforms
---

### Post by Mr.Carramba on 2008-05-25
Hi!
I have started to read server logs, and find a lot of following error:
dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied

What does it mean, and how to fix it?

---

### Post by Gunman1982 on 2008-05-25
It means that you don't have permission to write the file dhclient.eth0.leases in the directory /var/lib/dhcp3/ .
Did you execute 'sudo dhclient' or just 'dhclient'? You sould have root priviliges if you run this command.

---

### Post by Mr.Carramba on 2008-05-26
> **Gunman1982 said:**
> It means that you don't have permission to write the file dhclient.eth0.leases in the directory /var/lib/dhcp3/ .
Did you execute 'sudo dhclient' or just 'dhclient'? You sould have root priviliges if you run this command.


ok, I haven't stated question clearly, my bad.
I do not execute this command, I found it in sys.log that is why I'm wondering which process is trying to execute and why doesn't it have right permissions?

---

### Post by pdwerryhouse on 2008-05-26
Can you show us a full listing of /var/lib/dhcp3 with ls -la?

Mine, for example is:


```
drwxr-xr-x  2 root root 4096 2008-03-01 19:20 .
drwxr-xr-x 61 root root 4096 2008-05-03 07:45 ..
-rw-r--r--  1 dhcp root  577 2007-07-31 18:32 dhclient.eth0.leases
-rw-r--r--  1 root root    0 2008-03-01 19:20 dhclient.leases
-rw-r--r--  1 dhcp root 9248 2008-05-26 21:20 dhclient.wlan0.leases
```

As you can see, my leases files are owned by the dhcp user. The directory is owned by root, so it might be that if your directory is empty, then dhclient isn't able to write to it.

I suggest the following:

touch /var/lib/dhcp3/dhclieht.eth0.leases
chown dhcp /var/lib/dhcp3/dhclieht.eth0.leases

---

### Post by Mr.Carramba on 2008-05-26
> **pdwerryhouse said:**
> Can you show us a full listing of /var/lib/dhcp3 with ls -la?

Mine, for example is:


```
drwxr-xr-x  2 root root 4096 2008-03-01 19:20 .
drwxr-xr-x 61 root root 4096 2008-05-03 07:45 ..
-rw-r--r--  1 dhcp root  577 2007-07-31 18:32 dhclient.eth0.leases
-rw-r--r--  1 root root    0 2008-03-01 19:20 dhclient.leases
-rw-r--r--  1 dhcp root 9248 2008-05-26 21:20 dhclient.wlan0.leases
```As you can see, my leases files are owned by the dhcp user. The directory is owned by root, so it might be that if your directory is empty, then dhclient isn't able to write to it.

I suggest the following:

touch /var/lib/dhcp3/dhclieht.eth0.leases
chown dhcp /var/lib/dhcp3/dhclieht.eth0.leases

thanks! it seems that this trick fixed the problem :)
and ls -al output showed that everything was owned by root.
Is this a ubuntu bug? shouldn't ownership get assignment for this kind of stuff be during installation, och network configuration?

---

### Post by Krillin on 2008-06-24
I apparently a dhclient error after running 'UPDATED' in KPackage. After rebooting, my network would not come back up.
 
I opened a Kterminal window, ran dhclient and got two permission issues.
 
```
can't create /var/lib/dhcp3/dhcpclient.leases
can't create /var/run/dhcpclient.pid
drop_proviliges: could not get group id: operation not permitted
```
 
After I did a "sudo dhclient" all went ok, well kinda.
 
I ran:
```
touch /var/lib/dhcp3/dhclient.eth0.leases
```
 
But got:
```
can't touch /var/lib/dhcp3/dhclient.eth0.leases : Premission Denied
```
 
So we had to run:
```
sudo touch /var/lib/dhcp3/dhclient.eth0.leases
```
 
Then ran:
```
chown dhcp /var/lib/dhcp3/dhclient.eth0.leases
```
 
I hoped this would fix the issue of booting and getting an IP address, but this did NOT. So I am looking for a solution.
 
Thanks,
Krillin
 
P.S. Please note the word is CLIENT and not CLIEHT. :D

---

### Post by jdpond on 2011-10-18
This is a bug that has been reported several times, including:
[LIST]
[*] [bug 840947]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/840947")
[*] [bug 39249]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/39249")
[/LIST]

And it may go back to being a Debian problem.  Regardless, it still isn't resolved in 11.10, so . . .

The issue is that the dhcp3-client is pointing to a directory that doesn't exist (or hasn't been created by the installation)or that the original ifup command is wrong.

ifup command:
```

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases -1 eth0

```

One workaround (assuming you have root privileges and that the original dhcp client is being run under root user is:

```

sudo mkdir /var/lib/dhcp3/
sudo touch /var/lib/dhcp3/dhclient.eth0.leases

```

---

