---
title: "no such file or directory"
date: 2010-01-05
forum: Server Platforms
---

### Post by bluedrakonis on 2010-01-05
i decide to use an ubunt 9 instead of 6 for a server, i am following along on this tutorial: [http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-3-p3) 

i am on step 7, when i go to run this command:
/etc/init.d/hostname.sh start

i get:
-bash: /etc/init.d/hostname.sh: no file or directory found


any ideas?

---

### Post by cj13579 on 2010-01-05
I think that you are meant to replace with "hostname" with your hostname e.g. me.homlinux.org.

But I honestly don't see the point in the step. Once you have configured your static IP you should be all set. Changing your /etc/hosts file is only necessary if you are going to be accessing sites via your hostname from that machine.

I think that it is more likely that you will need to change the /etc/hosts file on the other machines on your network if they are going to be accessing sites/other things on that server using the hostname instead of the IP.

---

### Post by bluedrakonis on 2010-01-05
i tried that but no luck, if it is in fact not neccessary then it wouldnt be a problem i know that the machine will be contacting other sites over the internet and that it will host a webpage or a few depending on what  i decide to do with it, but thanks for the try

---

### Post by volkswagner on 2010-01-05
Try rebooting the server.  I know it's not windows, but...

try 

```
ls /etc/init.d/hostname*
```

It should be there.

The step has some importance, and you do want the 
```
hostname
```

and

```
hostname -f
```

To match as in the tutorial.

---

### Post by bluedrakonis on 2010-01-05
it say: 

ls: cannot access /etc/init.d/hostname*: no such file or directory

i even tried switching hostname to my hostname and no luck

---

### Post by hardev on 2010-01-06
Don't think "/etc/init.d/hostname.sh" is available in Karmic Koala (9.10). Reboot the machine for hostname changes to take effect.

---

### Post by BkkBonanza on 2010-01-06
Your local hostname isn't relevant for serving web sites anyway.
You can type "hostname" to see what the name is but it won't have any bearing on websites you choose to serve. 
The names you serve will be defined by the apache conf when you get that setup.
The hostname defined in /etc/hostname will be used by local LAN traffic.

---

### Post by bluedrakonis on 2010-01-06
so then it doesnt matter that when i type hostname and then run hostname -f that one gives me server1 while the other gives me server1.example.com then?

---

### Post by BkkBonanza on 2010-01-06
That's normal. The -f gives the FQDN and uses the resolv.conf to join the domain to the system name. See "man hostname" for info.

---

### Post by bluedrakonis on 2010-01-06
man i feel stupid i was follwing a guide for the wrong release thanks for the help guys

---

