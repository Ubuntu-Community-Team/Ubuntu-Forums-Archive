---
title: "Ubuntu 18.04 LTS - DNS Resolution fails, direct IP pinging works"
date: 2021-07-02
forum: Server Platforms
---

### Post by Mongoose088 on 2021-07-02
Hello all, I just uninstalled pivpn and upon reboot, it appears my DNS name resolution is not working anymore.

```

tom@cpu:~$ ping google.com
ping: google.com: Temporary failure in name resolution
tom@cpu:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=114 time=14.4 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=114 time=15.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=114 time=14.2 ms
^Z
[5]+  Stopped                 ping 8.8.8.8


```

I went about attempting to solve this in 2 ways. First, I just verified how my "netplan" was setup. And it looks like this:

```


network:

     version: 2
     ethernets:
        eno1:
            dhcp4: no
            dhcp6: no
            addresses: [192.168.2.60/24, ]
            gateway4:  192.168.2.1
            nameservers:
              addresses: [1.1.1.1, 8.8.4.4]



```

I did a quick "sudo netplan apply" to make sure it was committed, and still the same ping error.

So I went ahead and went for a more brute force method, I stopped the systemd-resolved.service, deleted /etc/resolv.conf, rewrote it to just have "nameserver 8.8.8.8" and restarted the service. I knew this wouldn't persist through reboots, but even this didn't work.

Well, I'm not so savvy on how netplan stuff works, so I'm not sure how to resolve this issue. 

Can you give me some advice? I'd say my experience level is "better than new, but not by much". Thanks as always.

---

### Post by TheFu on 2021-07-03
I see 2 errors.

```
sudo netplan generate
sudo netplan apply --debug
```
```

            addresses: [192.168.2.60/24[COLOR="#FF0000"],[/COLOR] ]
```
and the 
```
  [COLOR="#FF0000"]renderer: networkd[/COLOR]
```
line is missing at the top, indented to the same level as the version.

As for DNS, there are 3 methods available.
systemd-resolved, resolvconf and manually controlling the /etc/resolv.conf.  
The first 2 methods create a symbolic link for the /etc/resolv.conf to where those subsystems can control it. That symlink must exist and one of the programs needs to be configured to control it.  Usually in /etc/systemd/resolved.conf (self explanatory file) or in /etc/resolvconf/ somewhere.  

After picking which of those you want to use, restart the connected service. If there are errors, fix those.  Errors should be displayed immediately, but you can see them using **journalctl -xe** for the most recent service touched.

You can disable the systemd-resolved and/or resolvconf services by stopping, disabling, and "masking" those using systemctl.  Then just ensure that /etc/resolv.conf has nameserver settings like it has for the last 25 yrs.  Probably something like:
```
nameserver 1.1.1.1
nameserver 8.8.4.4
```
for your needs - though I'd stick with any non-Google DNS for privacy reasons.  Of course, if you run a DNS or DNS caching service like a pi-hole on your LAN, then you'd want to do this last solution and point it at the pi-hole server - and only the pi-hole.

---

### Post by Mongoose088 on 2021-07-03
Okay, I've gone through my files using your post as a guidance. Here is what I've done.

First, I updated my *.yaml config, located over at /etc/netplan/:

```

network:

     version: 2
     renderer: networkd
     ethernets:
        eno1:
            dhcp4: no
            dhcp6: no
            addresses: [192.168.2.60/24]
            gateway4:  192.168.2.1
            nameservers:
              addresses: [1.1.1.1, 8.8.4.4]

```

and ran a command to commit the changes:

```
sudo netplan apply
```

Of the three methods, I went with resolvconf. First I restarted the service:

```
sudo systemctl restart resolvconf.service
```

I uncovered a few unrelated errors running:
```
 journalctl -xe
```

I cleaned those up (uninstalled openvpn in this case) and rebooted. I ran the journal command again and I seem to still have DNS issues.

I should note, I hadn't done anything with the systemd-resolved service. Not wanting competing services to interfere with each other in how /etc/resolv.conf is written, I decided to disable it.

```

 sudo systemctl disable systemd-resolved
 sudo systemctl stop systemd-resolved

```

For good measure, I manually deleted /etc/resolv.conf and rebooted to see if resolvconf would auto create one.
But it did not. And I think that's because I disabled systemd-resolved. So instead I just manually created it with nameservers. **And now everything is working!**

But honestly I'm still a little confused and not very well read up on the issue. 

I think the "intended" workflow might be, the systemd-resolved service uses the .yaml file and netplan to "auto generate" a good /etc/resolv.conf?

I decided to run an experiment. I restarted and re-enabled systemd-resolved and changed my nameserver addresses to brand new ones in my .yaml file.
Then I deleted resolv.conf again and rebooted to see what might happen.

When I did that, it did not create a brand new resolv.conf. So now my DNS resolution problem is back. Of course I can just manually create a resolv.conf file and get things working again. But if that's what I need to do, what does "sudo netplan apply" and the "nameservers" section of the .yaml file even do? It appears that I'm just manually forcing things to work.

Edit:

Output of /run/systemd/resolve/resolv.conf:
```

tom@cpu:/etc$ cat /run/systemd/resolve/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients directly to
# all known uplink DNS servers. This file lists all configured search domains.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 208.67.222.222
nameserver 1.1.1.1


```

this matches the name servers that I put in my recently edited yaml file.  I ran this command:
```
 sudo ln -s /run/systemd/resolve/resolv.conf /etc/resolv.conf 
```

And I started testing again. Any changes to the yaml file, and a follow up "sudo netplan apply" immediately updates my resolv.conf through the symlink. I think this is the true, correct behavior. So I will mark this as solved.

Thanks TheFu, you saved me!

---

### Post by TheFu on 2021-07-03
You can't just *netplan apply*.  **netplan generate** is required too!
The netplan manpages are clear.  You'll need to review those to get a clear understanding. **netplan-generate** and **netplan-apply** are MUST READs.

Symbolic links are mandatory to use resolvconf or systemd-resolved.  If you don't set those up correctly, then those tools won't work.  Only 1 should be configured at a time. The other **must** be disabled BEFORE doing anything else.  If not, the other daemon may decide to "fix it".

There are DNS settings in the resolved.conf file. If using that daemon, then use that config file.  The manpage for resolved.conf explains.

---

