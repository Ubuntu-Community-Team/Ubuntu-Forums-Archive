---
title: "W: Failed to fetch on apt-get update and no connection to my Minecraft server."
date: 2015-09-11
forum: Server Platforms
---

### Post by jonathan_3 on 2015-09-11
Hello, Im new to the forum but have used it without having an account for a long time when getting myself into problems with my server. I dont know much about running a server, but I am very willing to learn and getting better in it. 

 I have some difficulties with getting my server to work after I updated some ubuntu server packages through Webmin. 
I decided to install Webmin to be able to use the graphical interface for my Minecraft server. 
I dont know if this is the reason but now I get the following message when trying to run **sudo apt-get update**

_I basically have two problems:_

1. Im not able to use **sudo apt-get update**

2. Im not able to log into my Minecraft server, even though it is online. 

And I wonder if these two problems could be connected in some way?

The problem with my Minecraft server is that I get a message saying 
> Failed to connect to the server
Authentication servers are down. Please try again later, sorry!
I reckon this has to do with my update through Webmin which was what I was just doing while this happened. I have read at the Minecraft forums that this is something Ill just have to wait for getting fixed at its own, but I doubt that its something else than something I have done with the server. When logging into my client the Server are there as Online, but when I try to connect I get this message. When I log into my **screen** where I run the MC-server Everything seems to be all right except from the message telling me the same there that it was an attempt to log in, but that it was rejected because of authentication problems. I realize that this might be a situation for the other forum, but I can help thinking that I might solve this by solving the problem with how my **apt-get update** is not functioning either.

When I run sudo apt-get update I get the following error:
```
base@ubuntu:~$ sudo apt-get update
Err http://security.ubuntu.com vivid-security InRelease


Err http://download.webmin.com sarge InRelease


Err http://webmin.mirror.somersettechsolutions.co.uk sarge InRelease


Err http://security.ubuntu.com vivid-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://webmin.mirror.somersettechsolutions.co.uk sarge Release.gpg
  Temporary failure resolving 'webmin.mirror.somersettechsolutions.co.uk'
Err http://download.webmin.com sarge Release.gpg
  Temporary failure resolving 'download.webmin.com'
Err http://no.archive.ubuntu.com vivid InRelease


Err http://no.archive.ubuntu.com vivid-updates InRelease


Err http://no.archive.ubuntu.com vivid-backports InRelease


Err http://no.archive.ubuntu.com vivid Release.gpg
  Temporary failure resolving 'no.archive.ubuntu.com'
Err http://no.archive.ubuntu.com vivid-updates Release.gpg
  Temporary failure resolving 'no.archive.ubuntu.com'
Err http://no.archive.ubuntu.com vivid-backports Release.gpg
  Temporary failure resolving 'no.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/vivid/InRelease


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/vivid-updates/InRelease


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/vivid-backports/InRelease


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/vivid-security/InRelease


W: Failed to fetch http://download.webmin.com/download/repository/dists/sarge/InRelease


W: Failed to fetch http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/InRelease


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/vivid-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'


W: Failed to fetch http://download.webmin.com/download/repository/dists/sarge/Release.gpg  Temporary failure resolving 'download.webmin.com'


W: Failed to fetch http://webmin.mirror.somersettechsolutions.co.uk/repository/dists/sarge/Release.gpg  Temporary failure resolving 'webmin.mirror.somersettechsolutions.co.uk'


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/vivid/Release.gpg  Temporary failure resolving 'no.archive.ubuntu.com'


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/vivid-updates/Release.gpg  Temporary failure resolving 'no.archive.ubuntu.com'


W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/vivid-backports/Release.gpg  Temporary failure resolving 'no.archive.ubuntu.com'


W: Some index files failed to download. They have been ignored, or old ones used instead.



```

I have tried a whole lot of possible solutions but think I need some guidance about how to approach this matter first hand, other than just looking at other threads which I have been doing most of this day today without any result. 

All help is fully appreciated! :)

Oh, yeah.. My Teamspeak server is functioning as it should. So are my ssh login which I use to connect to the server.


Regard Jonathan.

---

### Post by darkod on 2015-09-11
1. Even if you use webmin for certain MC tasks, I suggest you minimize its use. For example, never do updates through it, do it over standard ssh session.

2. The error messages mention vivid, so I assume you are using 15.04 server. Best practice is always to use LTS release for stable servers, in this case 14.04 LTS. No need to install the latest server version.

3. Connect through ssh and try something like:
```
sudo dpkg-reconfigure -a
sudo apt-get install -f
```

That should try to reconfigure all pending packages and fix apt missing dependancies, etc. So if it gets you anywhere.

PS. Also did you check if the server dns is working fine? The errors complain on resolution which might be dns related. From the ssh session try to ping domains like yahoo.com or google.com or any other. See if it resolves it to an IP.

---

### Post by jonathan_3 on 2015-09-11
I see. I should probably have used the 14.04 server yes, but now its done and I can not be bothered to change it at this moment. Maybe Ill use some time on doing it later on. Ill have to think more about how to perform the downgrade. 

I tried the **[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg-reconfigure -a [/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]but it only gave me this message: [/FONT][/COLOR]**Unknown option: a**
Am I supposed to write something more to it? I tried without the -a but it only tells me to specify a package to reconfigure. I dont see which kind of package this should be. I was going to install an other version of Java, but I guess the **apt-get update** should work even though without any further install progression? I tried to write **[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install -f[/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono] but it doesnt install anything. Is there some more information I could provide?

When I try to install a package now it only tells me that it was unable to locate the package, which I guess is logical since I am unable to perform [/FONT][/COLOR]**sudo apt-get update**.[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]When I try to ping I get this message: **ping: unknown host google.com**. I have tried to search for clues about how to solve this too at the web but am unable to find something that can seem to help me.

---

### Post by darkod on 2015-09-11
The '-a' was correct, it stands for --all to replace any package that might need to be reconfigured (because you don't know if there is any, so you can't specify package name).

But the ping shows a lot, you don't seem to have dns. Please post output of:
```
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by jonathan_3 on 2015-09-11
Okay, this is starting to make a kind of sense for me too. The first **[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/resolv.conf[/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono] is empty ( I guess it should contain some info?):[/FONT][/COLOR]

```
username@ubuntu:~$ cat /etc/resolv.conf# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
username@ubuntu:~$
```


[FONT=arial]The second, **[COLOR=#000000]cat /etc/network/interfaces [/COLOR]**[/FONT][COLOR=#000000][FONT=Ubuntu Mono][FONT=arial]shows this:[/FONT]
[/FONT][/COLOR]```
username@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
allow-hotplug eth0
auto eth0
iface eth0 inet static
        address MY_PUBLIC_IP
        netmask MY_NETMASK
        gateway MY_GATEWAY


username@ubuntu:~$ #
``` 

[FONT=arial][COLOR=#000000]By the way, Thanks for helping! I hope we solve this problem of mine!

I replaced the address, netmask, gateway and my username with something else, but its my public IP that stands as address. The one I connect through ssh with.[/COLOR][/FONT]

---

### Post by darkod on 2015-09-11
Ok, we are getting somewhere. You have a static IP for the server, which is correct because you don't want it to change. What you are missing is the nameservers to use. You can use for example two of Google's public nameservers. Edit the interfaces file and for eth0 after the gateway, add the line:
```
   dns-nameservers 8.8.8.8 8.8.4.4
```

Restart networking with:
```
sudo service networking restart
```

Check if resolv.conf now has the nameservers and if ping works. If all is good, try the above commands and also the apt update again. Also do apt-get dist-upgrade which will upgrade all needed packages.

If after restarting networking by any chance you can't connect, use the provider panel and reboot the server.

---

### Post by jonathan_3 on 2015-09-11
Great! That did the trick! Everything works as it should again now! Thank you very much!
The [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/resolv.conf now shows:
[/FONT][/COLOR]```
nameserver 8.8.8.8
nameserver 8.8.4.4

```
[COLOR=#000000][FONT=Ubuntu Mono]
And the cat /etc/network/interfaces[/FONT][/COLOR] shows:
```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
allow-hotplug eth0
auto eth0
iface eth0 inet static
        address my public ip
        netmask my netmask
        gateway my gateway
        dns-nameservers 8.8.8.8 8.8.4.4



``` 

Ping works! **apt-get update** works! [COLOR=#000000][FONT=Ubuntu Mono][FONT=arial]And Minecraft server is working again :)

Thank you!


Regards Jonathan.
[/FONT]
[/FONT][/COLOR]

---

### Post by darkod on 2015-09-11
Great. You're welcome. You can mark the thread as Solved in Thread Tools, above your first post.

---

