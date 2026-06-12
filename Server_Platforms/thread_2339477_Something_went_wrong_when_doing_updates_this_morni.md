---
title: "Something went wrong when doing updates this morning."
date: 2016-10-09
forum: Server Platforms
---

### Post by irv on 2016-10-09
I was going to install updates on my server this morning when I got these errors.
```
sudo apt-get update
Err:1 http://archive.canonical.com/ubuntu xenial InRelease
  Temporary failure resolving 'archive.canonical.com'
Err:2 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/xenial/InRelease  Temporary failure resolving 'archive.canonical.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

```
Looks like a website is down or I am not getting connected.
I can remote into the server and can get to it over the Internet, so it isn't on my end..
? not sure what's going on. I tried restarting the server a couple of times but it is still happening.

---

### Post by bearlake on 2016-10-09
Hi,

Try a different mirror or wait an hour or so and try again.

I just updated with no issues.

---

### Post by darkod on 2016-10-09
Temporary error resolving probably means you need to check if dns is working correctly. Seems to me the nameserver you are using doesn't resolve. Try it with:
```
nslookup google.com
```

After that also try ping to public IP that doesn't need dns resolving, like:
```
ping -c 4 8.8.8.8
```

That will show you if you really have internet or not, apart from whether dns is working.

---

### Post by irv on 2016-10-09
You are right: Looks like the dns is not working correctly. How can I fix this? Or where do I check this from the command prompt?
```
nslookup google.com
;; connection timed out; no servers could be reached
```

I am on the Internest I can ping the 8.8.8.8

```
ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=48 time=25.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=48 time=24.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=48 time=24.5 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=48 time=24.4 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 24.381/24.785/25.754/0.561 ms
```

---

### Post by irv on 2016-10-09
I did Try this

In /etc/NetworkManager/NetworkManager.conf comment out the line dns=dnsmasq

```
sudo nano /etc/NetworkManager/NetworkManager.conf
```

> [main]
plugins=ifupdown,keyfile,ofono
#dns=dnsmasq
and restart the NetworkManager service.

```
sudo restart network-manager
```
and I got this error:
> restart: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused


---

### Post by darkod on 2016-10-09
We are in the server section, which by default doesn't use Network Manager. Have you added GUI or Network Manager yourself? Or you are running the Desktop OS version?

In the server OS the only relevant file is /etc/network/interfaces but with GUI/Network Manager you control the network settings in NM.

In both cases, the automatic process should put your nameservers in /etc/resolv.conf. You can check that file to check current nameservers used:
```
cat /etc/resolv.conf
```

---

### Post by irv on 2016-10-09
> **darkod said:**
> We are in the server section, which by default doesn't use Network Manager. Have you added GUI or Network Manager yourself? Or you are running the Desktop OS version?

In the server OS the only relevant file is /etc/network/interfaces but with GUI/Network Manager you control the network settings in NM.

In both cases, the automatic process should put your nameservers in /etc/resolv.conf. You can check that file to check current nameservers used:
```
cat /etc/resolv.conf
```

Yes I did install a desktop on my server but it quit working.
When I used the cat /etc/resolv.conf I get this:
```

cat: /etc/resolv.conf: No such file or directory

```

EDIT: I do have a resolv.conf file, but it is empty.

---

### Post by Bashing-om on 2016-10-09
irv; Hey;

A passing thought; a broken symlink ?
What results:
```

ls -l /etc/resolv.conf

```

I do not know how systemd (16.04) handles network-manager . Maybe a learning process here for me also .

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by irv on 2016-10-09
> **Bashing-om said:**
> irv; Hey;

A passing thought; a broken symlink ?
What results:
```

ls -l /etc/resolv.conf

```

I do not know how systemd (16.04) handles network-manager . Maybe a learning process here for me also .

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

Here it is.

```
ls -l /etc/resolv.conf
```
> lrwxrwxrwx 1 root root 29 Sep 15  2014 /etc/resolv.conf -> ../run/resolvconf/resolv.conf

---

### Post by irv on 2016-10-09
Maybe I should just remove the desktop with the command
```
sudo apt-get --purge remove ubuntu-desktop
```
and then try to do an update.

Can't remember the key combo to boot to a prompt? I know I can't boot part way into the desktop to remove it.

EDIT: I tried booting holding the Shift key down and it just booted to the login for the Unity desktop. After loging in it just hang and never goes all the way to the desktop. I can hold down the Ctrl/Alt F2 to get to the command line but I am not sure if I should try removing the  ubuntu desktop?

---

### Post by irv on 2016-10-10
I have tried everything I can think of to fix my server and nothing has worked so far. I don't want to wipe it and start over again. I have had this server up and running for 8 or 10 years now and have put time into getting it the way I want it. Any suggestions would be helpful.

---

### Post by irv on 2016-10-10
I am beating my head against the wall and getting nowhere. I can't install or remove anything from the server. The last thing I tried was:
```
sudo apt-get update --fix-missing
```
and all I get is errors
> Err:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
  Temporary failure resolving 'archive.canonical.com'
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/InRelease](http://archive.canonical.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'archive.canonical.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

I have no idea where to go from here?

---

### Post by darkod on 2016-10-10
How about simply creating /etc/resolv.conf? It's the dirty way, but it should work if the nameserver is the only thing you are missing...
```
sudo nano /etc/resolv.conf
```

In the file put only these two lines:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Save and close the file. Try again to use apt-get... 

This all might be from installing ubuntu-desktop, but I can't be sure... You should really try avoiding adding GUIs on linux servers. Especially in the case of ubuntu the GUI installs NM that tries to take over the network control... And that is serious stuff on a server.

---

### Post by Bashing-om on 2016-10-10
irv; Hey ...

I see no need to re-install .. I see this as a config issue . Unfortunately my knowledge of networking in systemd is minimal at best.
As this is a server a GUI network-manager "should" not be a factor here .. is it ?
show:
```

dpkg -l network-manager
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf

```

We do need to isolate who controls networking .. you or the system .

[INDENT][INDENT]who's the boss
[/INDENT][/INDENT]

---

### Post by irv on 2016-10-10
> **darkod said:**
> How about simply creating /etc/resolv.conf? It's the dirty way, but it should work if the nameserver is the only thing you are missing...
```
sudo nano /etc/resolv.conf
```

In the file put only these two lines:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Save and close the file. Try again to use apt-get... 

This all might be from installing ubuntu-desktop, but I can't be sure... You should really try avoiding adding GUIs on linux servers. Especially in the case of ubuntu the GUI installs NM that tries to take over the network control... And that is serious stuff on a server.
First: I edited the /resolv.conf file and added the two lines to an empty file, save it and then did the second step.
Second: ran sudo apt update and it updated.
Third I ran sudo apt upgrade, and it upgraded everything but on the end I got the error:
> Errors were encountered while processing:
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-42-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

I then restarted the server using the command:
```
sudo shutdown now -r
```
It still hangs on the unity desktop so I want to remove it and i want to make sure I remove it all so what is the right way to do this?

---

### Post by irv on 2016-10-10
Here is what I got with the commands.
> dpkg -l network-manger
dpkg-query: no packages found matching network-manger
irv@wabasha-server:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p3p1
# iface p3p1 inet dhcp
 iface p3p1 inet static
	address 192.168.1.105
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
        nameserver 8.8.8.8 8.8.4.4
        dns-nameservers 8.8.8.8 8.8.4.4


irv@wabasha-server:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
#dns=dnsmasq

[ifupdown]
managed=false


---

### Post by irv on 2016-10-10
Here is what I got with the commands.
> dpkg -l network-manger
dpkg-query: no packages found matching network-manger
irv@wabasha-server:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p3p1
# iface p3p1 inet dhcp
 iface p3p1 inet static
	address 192.168.1.105
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
        nameserver 8.8.8.8 8.8.4.4
        dns-nameservers 8.8.8.8 8.8.4.4


irv@wabasha-server:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
#dns=dnsmasq

[ifupdown]
managed=false


---

### Post by darkod on 2016-10-10
I thought the first thing you try will be removing the ubuntu-desktop package. You didn't need to upgrade the packages...

Now put the nameservers in /etc/resolv.conf again if needed after the reboot, and try something like:
```
sudo apt-get purge ubuntu-desktop
sudo apt-get autoremove
```

Not sure if that removes all packages it installed, but it's a start...

PS. FYI, the parameter 'nameserver' in /etc/network/interfaces is not correct. The parameter used there is 'dns-nameservers'. But in /etc/resolv.conf is 'nameserver 8.8.8.8'.

---

### Post by Bashing-om on 2016-10-10
darkod; irv - Sheeshhh ..

What a confusing issue we have here !
a) network-manager is not installed 
BUT
b) the control file for network-manager is in existence
such that
c) we should direct the system: /etc/NetworkManager/NetworkManager.conf
managed=false <- Default setting, such that NetworkManager controls networking, when set "managed=true" then "/etc/network/interfaces" file is used for control.

in addition to correcting DNS .. should we not remove the /etc/NetworkManager/NetworkManager.conf file ??
I manage my networking and that ^ file is not required in such an instance:
> 
sysop@1404mini:~$ ls -al /etc/NetworkManager/NetworkManager.conf
ls: cannot access /etc/NetworkManager/NetworkManager.conf: No such file or directory
sysop@1404mini:~$



EDIT : Opppss
A typo ! for item a)
"dpkg -l network-manger" should be dpkg -l network-manager . Where the former has a dropped 'a' .
irv. try again .. so we get on the same page .

Mind ya
[INDENT][INDENT][INDENT]what I do not know fills a big big book
[/INDENT][/INDENT][/INDENT]

---

### Post by irv on 2016-10-10
Just to let you know I put the nameserver back in the resolv.conf file and did the purge and autoremove and it removed the desktop and files. I checked the interfaces file and this is what it has in it.
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p3p1
# iface p3p1 inet dhcp
 iface p3p1 inet static
        address 192.168.1.105
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        nameserver 8.8.8.8 8.8.4.4
        dns-nameservers 8.8.8.8 8.8.4.4

I checked the file after I rebooted.
The desktop is now removed but I tried the apt-get again and I am back to getting errors again.
> Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
  Temporary failure resolving 'archive.canonical.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/InRelease](http://archive.canonical.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'archive.canonical.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

If I put the nameserver back in the resolv.conf file it will only be temporary until I reboot again, right? Also if it it is set in the interfaces file why doesn't it work?

---

### Post by darkod on 2016-10-10
Delete the nameserver... line in /etc/network/interfaces and reboot the server again. As I said, that line is wrong. It might not be related to your problem but since it is wrong, remove it. Just the nameserver... The dns-nameserver is the correct one.

Is it possible you're missing the resolvconf package? That is the package that is supposed to put the correct nameservers from dns-nameservers statement into /etc/resolv.conf.
```
sudo apt-get install resolvconf
```

---

### Post by Bashing-om on 2016-10-10
irv; Humm ..

While awaiting darkod's most excellent knowledge and guidance;
I have some doubts about the interface identification " p3p1 " as I expect systemd to use a differing naming convention.
Is that the root of our problem ?
verify that identification :
```

ls -al /sys/class/net
sudo lshw -C network
ip route show

```

[INDENT][INDENT]getting all ducks in a row
[/INDENT][/INDENT]

---

### Post by irv on 2016-10-10
After putting the lines back into the resolv.conf, I can run the sudo apt-get update but when I run the upgrade I see this:
> sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-3.13.0-35-generic linux-image-extra-3.13.0-35-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
8 not fully installed or removed.

It appears I still have 8 apps that are not fully installed or removed. Then at the bottle of the screen went the upgrade is done I have more errors.
> Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-image-4.4.0-36-generic i386 4.4.0-36.55 [17.5 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-image-extra-4.4.0-36-generic i386 4.4.0-36.55 [38.6 MB]
Fetched 56.1 MB in 10s (5,476 kB/s)                                            
(Reading database ... 182144 files and directories currently installed.)
Removing linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-extra-3.13.0-35-generic
 linux-image-3.13.0-35-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by darkod on 2016-10-10
@Bashing-om,

I have seen p3p1 interface in 16.04 so it might be correct. But yes, better to confirm with lshw.

---

### Post by darkod on 2016-10-10
@irv,

If apt-get has any issues usually the first thing to try is:
```
sudo apt-get -f install
```

That will try to solve missing dependancies. But if few kernel packages failed to get removed right now, I wouldn't worry... I would try to get automatic resolv.conf working again. Don't try too much at once. If the majority of packages related to ubuntu-desktop got removed, that's great and should be a big step forward...

If you continue having apt-get errors, please post the whole output.

---

### Post by irv on 2016-10-10
```
sudo lshw -C network
```
Output
> *-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: p3p1
       version: 02
       serial: 00:30:18:ad:bc:1e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.105 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:27 ioport:e800(size=256) memory:dcfff000-dcffffff memory:dcfe0000-dcfeffff memory:dffe0000-dfffffff


---

### Post by irv on 2016-10-10
```
sudo apt-get update
```
Output
> Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
  Temporary failure resolving 'archive.canonical.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Temporary failure resolving 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/InRelease](http://archive.canonical.com/ubuntu/dists/xenial/InRelease)  Temporary failure resolving 'archive.canonical.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by darkod on 2016-10-11
Did you try the apt-get -f install?

Also, the dns errors like in the last post you don't need to post any more, we have established dns is not working as expected. But if there are other type of apt-get errors, like in post #23, it might be good to read the whole error message.

Also, after removing the ubuntu-desktop did you check again if network-manager is still installed and to remove it if it is? When removing it use purge to get rid of the config files too:
```
sudo apt-get purge network-manager
```

---

### Post by irv on 2016-10-11
Yes I did do the apt-get -f install.
I just ran the purge network-manager and got this.
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-35-generic linux-image-4.4.0-36-generic
  linux-image-extra-3.13.0-35-generic linux-image-extra-4.4.0-36-generic
  network-manager*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 306 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 182144 files and directories currently installed.)
Removing linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_fuJMw3/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_fuJMw3/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 255
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-35-generic
 linux-image-3.13.0-35-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by irv on 2016-10-11
you are right on the dpkg error. No matter when I use the apt-get I see this.
> [COLOR="#FF0000"]dpkg: error [/COLOR]processing package linux-image-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-extra-3.13.0-35-generic
 linux-image-3.13.0-35-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by darkod on 2016-10-11
Lets check your root free space. If your root or /boot ran out of space, apt-get gets crazy.
```
df -h
```

If that shows that you do have free space on root and /boot, try this:
```
sudo dpkg --purge linux-image-3.13.0-35-generic
```

If that works try the same for 4.4.0-36 too, because that kernel reported apt-get error too.

---

### Post by Bashing-om on 2016-10-11
irv; darkod; Morning .

How about we re-focus to the kernel issue, and get the kernel and headers straightened out ?
Makes sense to me that we can not do much if the foundation is not there.
To address the kernels, let's look at what is :
```

df -h
df -i
uname -r
dpkg -l | grep linux-
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot

```

From these we should be able to determine what action(s) to take.
Once the foundation is solid we return to the DNS issue .

[INDENT][INDENT]least ways, that is where my mind set is
[/INDENT][/INDENT]

---

### Post by irv on 2016-10-11
Okay, here is the output for all the commands:
> irv@wabasha-server:~$ sudo df -h
[sudo] password for irv: 
Filesystem                            Size  Used Avail Use% Mounted on
udev                                  860M     0  860M   0% /dev
tmpfs                                 176M   19M  158M  11% /run
/dev/mapper/wabasha--server--vg-root  228G  157G   59G  73% /
tmpfs                                 879M     0  879M   0% /dev/shm
tmpfs                                 5.0M  4.0K  5.0M   1% /run/lock
tmpfs                                 879M     0  879M   0% /sys/fs/cgroup
/dev/sda1                             236M  109M  115M  49% /boot
cgmfs                                 100K     0  100K   0% /run/cgmanager/fs
tmpfs                                 176M     0  176M   0% /run/user/1000
irv@wabasha-server:~$ df -i
Filesystem                             Inodes  IUsed    IFree IUse% Mounted on
udev                                   209550    491   209059    1% /dev
tmpfs                                  219620    693   218927    1% /run
/dev/mapper/wabasha--server--vg-root 15138816 342594 14796222    3% /
tmpfs                                  219620      1   219619    1% /dev/shm
tmpfs                                  219620      6   219614    1% /run/lock
tmpfs                                  219620     18   219602    1% /sys/fs/cgroup
/dev/sda1                               62248    310    61938    1% /boot
cgmfs                                  219620     14   219606    1% /run/cgmanager/fs
tmpfs                                  219620      4   219616    1% /run/user/1000
irv@wabasha-server:~$ uname -r
4.4.0-38-generic
irv@wabasha-server:~$ dpkg -l | grep linux-
ii  linux-base                            4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                        1.157.4                                                     all          Firmware for Linux kernel drivers
iU  linux-generic                         4.4.0.42.44                                                 i386         Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-38                4.4.0-38.57                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic        4.4.0-38.57                                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-42                4.4.0-42.62                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-generic        4.4.0-42.62                                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic                 4.4.0.42.44                                                 i386         Generic Linux kernel headers
rc  linux-image-3.13.0-32-generic         3.13.0-32.57                                                i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-3.13.0-35-generic         3.13.0-35.62                                                i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-4.4.0-36-generic          4.4.0-36.55                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-38-generic          4.4.0-38.57                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-4.4.0-42-generic          4.4.0-42.62                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic   3.13.0-32.57                                                i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-extra-3.13.0-35-generic   3.13.0-35.62                                                i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-extra-4.4.0-36-generic    4.4.0-36.55                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic    4.4.0-38.57                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-42-generic    4.4.0-42.62                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-generic                   4.4.0.42.44                                                 i386         Generic Linux kernel image
ii  linux-libc-dev:i386                   4.4.0-42.62                                                 i386         Linux Kernel Headers for development
rc  linux-sound-base                      1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
irv@wabasha-server:~$ ls -al /usr/src
total 24
drwxr-xr-x  6 root root 4096 Oct 10 15:40 .
drwxr-xr-x 10 root root 4096 Oct 10 15:41 ..
drwxr-xr-x 27 root root 4096 Sep 28 17:42 linux-headers-4.4.0-38
drwxr-xr-x  7 root root 4096 Sep 28 17:42 linux-headers-4.4.0-38-generic
drwxr-xr-x 27 root root 4096 Oct 10 13:51 linux-headers-4.4.0-42
drwxr-xr-x  7 root root 4096 Oct 10 13:51 linux-headers-4.4.0-42-generic
irv@wabasha-server:~$ ls -al /lib/modules/
total 16
drwxr-xr-x  4 root root 4096 Oct 10 15:40 .
drwxr-xr-x 25 root root 4096 Oct 10 15:40 ..
drwxr-xr-x  5 root root 4096 Sep 28 17:43 4.4.0-38-generic
drwxr-xr-x  5 root root 4096 Oct 10 15:32 4.4.0-42-generic
irv@wabasha-server:~$ ls -al /boot
total 102148
drwxr-xr-x  4 root root     1024 Oct 11 15:49 .
drwxr-xr-x 22 root root     4096 Oct 10 13:51 ..
-rw-r--r--  1 root root  1238368 Sep  6 13:17 abi-4.4.0-38-generic
-rw-r--r--  1 root root  1238807 Oct  7 19:38 abi-4.4.0-42-generic
-rw-r--r--  1 root root   193157 Sep  6 13:17 config-4.4.0-38-generic
-rw-r--r--  1 root root   193185 Oct  7 19:38 config-4.4.0-42-generic
drwxr-xr-x  5 root root     1024 Sep 28 17:43 grub
-rw-r--r--  1 root root 40281630 Oct  9 07:44 initrd.img-4.4.0-38-generic
-rw-r--r--  1 root root 40686126 Oct 10 15:32 initrd.img-4.4.0-42-generic
drwx------  2 root root    12288 Sep 15  2014 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3089791 Sep  6 13:17 System.map-4.4.0-38-generic
-rw-------  1 root root  3090253 Oct  7 19:38 System.map-4.4.0-42-generic
-rw-------  1 root root  6795680 Sep  6 13:17 vmlinuz-4.4.0-38-generic
-rw-------  1 root root  6796448 Oct  7 19:38 vmlinuz-4.4.0-42-generic


---

### Post by irv on 2016-10-11
Okay, here is the output for all the commands:
> irv@wabasha-server:~$ sudo df -h
[sudo] password for irv: 
Filesystem                            Size  Used Avail Use% Mounted on
udev                                  860M     0  860M   0% /dev
tmpfs                                 176M   19M  158M  11% /run
/dev/mapper/wabasha--server--vg-root  228G  157G   59G  73% /
tmpfs                                 879M     0  879M   0% /dev/shm
tmpfs                                 5.0M  4.0K  5.0M   1% /run/lock
tmpfs                                 879M     0  879M   0% /sys/fs/cgroup
/dev/sda1                             236M  109M  115M  49% /boot
cgmfs                                 100K     0  100K   0% /run/cgmanager/fs
tmpfs                                 176M     0  176M   0% /run/user/1000
irv@wabasha-server:~$ df -i
Filesystem                             Inodes  IUsed    IFree IUse% Mounted on
udev                                   209550    491   209059    1% /dev
tmpfs                                  219620    693   218927    1% /run
/dev/mapper/wabasha--server--vg-root 15138816 342594 14796222    3% /
tmpfs                                  219620      1   219619    1% /dev/shm
tmpfs                                  219620      6   219614    1% /run/lock
tmpfs                                  219620     18   219602    1% /sys/fs/cgroup
/dev/sda1                               62248    310    61938    1% /boot
cgmfs                                  219620     14   219606    1% /run/cgmanager/fs
tmpfs                                  219620      4   219616    1% /run/user/1000
irv@wabasha-server:~$ uname -r
4.4.0-38-generic
irv@wabasha-server:~$ dpkg -l | grep linux-
ii  linux-base                            4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                        1.157.4                                                     all          Firmware for Linux kernel drivers
iU  linux-generic                         4.4.0.42.44                                                 i386         Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-38                4.4.0-38.57                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic        4.4.0-38.57                                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-42                4.4.0-42.62                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-generic        4.4.0-42.62                                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic                 4.4.0.42.44                                                 i386         Generic Linux kernel headers
rc  linux-image-3.13.0-32-generic         3.13.0-32.57                                                i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-3.13.0-35-generic         3.13.0-35.62                                                i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-4.4.0-36-generic          4.4.0-36.55                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-38-generic          4.4.0-38.57                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-4.4.0-42-generic          4.4.0-42.62                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic   3.13.0-32.57                                                i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-extra-3.13.0-35-generic   3.13.0-35.62                                                i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-extra-4.4.0-36-generic    4.4.0-36.55                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic    4.4.0-38.57                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-42-generic    4.4.0-42.62                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-generic                   4.4.0.42.44                                                 i386         Generic Linux kernel image
ii  linux-libc-dev:i386                   4.4.0-42.62                                                 i386         Linux Kernel Headers for development
rc  linux-sound-base                      1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
irv@wabasha-server:~$ ls -al /usr/src
total 24
drwxr-xr-x  6 root root 4096 Oct 10 15:40 .
drwxr-xr-x 10 root root 4096 Oct 10 15:41 ..
drwxr-xr-x 27 root root 4096 Sep 28 17:42 linux-headers-4.4.0-38
drwxr-xr-x  7 root root 4096 Sep 28 17:42 linux-headers-4.4.0-38-generic
drwxr-xr-x 27 root root 4096 Oct 10 13:51 linux-headers-4.4.0-42
drwxr-xr-x  7 root root 4096 Oct 10 13:51 linux-headers-4.4.0-42-generic
irv@wabasha-server:~$ ls -al /lib/modules/
total 16
drwxr-xr-x  4 root root 4096 Oct 10 15:40 .
drwxr-xr-x 25 root root 4096 Oct 10 15:40 ..
drwxr-xr-x  5 root root 4096 Sep 28 17:43 4.4.0-38-generic
drwxr-xr-x  5 root root 4096 Oct 10 15:32 4.4.0-42-generic
irv@wabasha-server:~$ ls -al /boot
total 102148
drwxr-xr-x  4 root root     1024 Oct 11 15:49 .
drwxr-xr-x 22 root root     4096 Oct 10 13:51 ..
-rw-r--r--  1 root root  1238368 Sep  6 13:17 abi-4.4.0-38-generic
-rw-r--r--  1 root root  1238807 Oct  7 19:38 abi-4.4.0-42-generic
-rw-r--r--  1 root root   193157 Sep  6 13:17 config-4.4.0-38-generic
-rw-r--r--  1 root root   193185 Oct  7 19:38 config-4.4.0-42-generic
drwxr-xr-x  5 root root     1024 Sep 28 17:43 grub
-rw-r--r--  1 root root 40281630 Oct  9 07:44 initrd.img-4.4.0-38-generic
-rw-r--r--  1 root root 40686126 Oct 10 15:32 initrd.img-4.4.0-42-generic
drwx------  2 root root    12288 Sep 15  2014 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3089791 Sep  6 13:17 System.map-4.4.0-38-generic
-rw-------  1 root root  3090253 Oct  7 19:38 System.map-4.4.0-42-generic
-rw-------  1 root root  6795680 Sep  6 13:17 vmlinuz-4.4.0-38-generic
-rw-------  1 root root  6796448 Oct  7 19:38 vmlinuz-4.4.0-42-generic


---

### Post by Bashing-om on 2016-10-11
irv; Not to bad !

Look'n much better overall than I had expected.

So, what resulted in purging linux-image-3.13.0-35-generic as directed by darkod?
As we also need to purge " rH linux-image-4.4.0-36-generic  " .

And then get " iF linux-image-4.4.0-42-generic  " fully installed .

One at a time.

[INDENT][INDENT]step by step
[/INDENT][/INDENT]

---

### Post by irv on 2016-10-12
Here is where we are right now.
I purged linux-image-3.13.0-35 and when I ran apt-get update, it ran ok, but remember I still had nameserver in the resolv.conf.

I shutdown the server and restarted it again so nameserver was no longer in resolv.conf and this cause problems running apt-get again.

I then put nameserver back in resolv.conf again and ran apt-get update and it ran okay, but when I ran apt-get upgrade I got the dpkg error again.

I am now going to purge " rH linux-image-4.4.0-36-generic ". Before I do this just wanted to know what the rH and iF was before the linux-image in your post?

---

### Post by darkod on 2016-10-12
I think that might be a typo or copy/paste error. You need to use the exact package name in dpkg, which does not contain rH and iF.

Also, I would suggest running another command too, before trying apt-get upgrade. Your dpkg list shows many linux kernels but the ls of the /boot folder shows only few. Were you sometimes deleting kernel files manually with rm instead of using apt-get to remove and purge them?

I would like you to try something like this, to make sure all dependancies are good and all not needed packages are removed:
```
sudo dpkg --purge linux-image-4.4.0-36-generic
sudo apt-get -f install
sudo apt-get autoremove
```

Right now don't reboot the system often, that way you don't have to put the nameserver back into resolv.conf that often. It stays there until a reboot.

Check out the result of the above commands and after that if apt-get is good we can start working on the nameserver issue.

---

### Post by irv on 2016-10-12
I ran the first command
```
sudo dpkg --purge linux-image-4.4.0-36-generic
```
I see it Failed to process.
> (Reading database ... 182144 files and directories currently installed.)
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--purge):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 linux-image-4.4.0-36-generic

---

### Post by darkod on 2016-10-12
OK. Still try the apt-get autoremove and maybe that can help clean up some packages... After that the apt-get -f install, and report if it throws any errors.

---

### Post by irv on 2016-10-12
```
sudo apt-get autoremove
```
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-35-generic linux-image-4.4.0-36-generic
  linux-image-extra-3.13.0-35-generic linux-image-extra-4.4.0-36-generic
0 upgraded, 0 newly installed, 4 to remove and 20 not upgraded.
8 not fully installed or removed.
After this operation, 306 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 182144 files and directories currently installed.)
Removing linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_PMnSW2/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_PMnSW2/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 255
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-35-generic
 linux-image-3.13.0-35-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
sudo apt-get -f install
```
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-35-generic linux-image-4.4.0-36-generic
  linux-image-extra-3.13.0-35-generic linux-image-extra-4.4.0-36-generic
0 upgraded, 0 newly installed, 4 to remove and 20 not upgraded.
8 not fully installed or removed.
After this operation, 306 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 182144 files and directories currently installed.)
Removing linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_mJBtHv/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_mJBtHv/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 255
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-35-generic
 linux-image-3.13.0-35-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by darkod on 2016-10-12
You can also try this for any interrupted installs:
```
sudo dpkg --configure -a
```

Another thing is that you can try deleting those files that report the error in /var/lib/dpkg/info. I dont think it can hurt the system. They are fol older kernels anyway... But I'm not an expert for dpkg.

---

### Post by irv on 2016-10-12
I am still having problem after trying sudo dpkg --configure -a so I tried
sudo dpkg -i --force-overwrite linux-image-4.4.0-36-generic
but got an error because I wasn't sure where the linux-image file is located, and I am not sure if that will work.
I also check the info file in /var/lib/dpkg and there were no error listed.

---

### Post by darkod on 2016-10-12
I meant the Failed to process message when you were trying the dpkg purge. I wanted to save myself retyping the whole filename. The message contains a file in location /var/lib/dpkg/info/... Check it out and delete it if it's there.

---

### Post by irv on 2016-10-12
It was not there.

---

### Post by Bashing-om on 2016-10-12
irv; Hey .....

I am of the mind that :
> 
Errors were encountered while processing:
linux-image-extra-3.13.0-35-generic
linux-image-3.13.0-35-generic
linux-image-extra-4.4.0-36-generic
linux-image-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

residual files of a bad removal . The parents of these files no longer exist  in either /usr/src, /lib/modules or in /boot .

Let us try the least intrusive means we can to make the package manager happy.
we drop down a level and try:
```

sudo dpkg -P linux-image-3.13.0-35-generic linux-image-extra-3.13.0-35-generic

```
see if the package manager will work for us . Maybe there is not enough left on the system to work with .. and we address the issue directly - breaking the package manager . we would then have to fix the package manager .

[INDENT][INDENT]a must
[INDENT][INDENT][INDENT]make the package manager happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by irv on 2016-10-12
I tried something.
```
sudo dpkg -C
```
And I found this out with the output.
> They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-generic        Complete Generic Linux kernel and headers
 linux-image-extra-4.4.0-42-generic Linux kernel extra modules for version 4.4.
 linux-image-generic  Generic Linux kernel image

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-image-4.4.0-42-generic Linux kernel image for version 4.4.0 on 32 bit x8

The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-image-3.13.0-35-generic Linux kernel image for version 3.13.0 on 32 bit 
 linux-image-4.4.0-36-generic Linux kernel image for version 4.4.0 on 32 bit x8
 linux-image-extra-3.13.0-35-generic Linux kernel extra modules for version 3.1
 linux-image-extra-4.4.0-36-generic Linux kernel extra modules for version 4.4.


when I tried to run
```
sudo dpkg --configure linux-generic
```
I get this error:
> dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.42.44); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-generic

when I try this with linux-image-extra-4.4.0-42-generic, or linux-image-extra-4.4.0-36-generic I get the same error. It seem like I can't remover it and I can't fix the install.

---

### Post by Bashing-om on 2016-10-12
irv; welp:

> 
the packages can be removed using dselect or [color=red]dpkg --remove:[/color]
linux-image-3.13.0-35-generic Linux kernel image for version 3.13.0 on 32 bit 
linux-image-4.4.0-36-generic Linux kernel image for version 4.4.0 on 32 bit x8
linux-image-extra-3.13.0-35-generic Linux kernel extra modules for version 3.1
linux-image-extra-4.4.0-36-generic Linux kernel extra modules for version 4.4.


and back to my post # 45 , where we try the (P)urge option rather than --remove .
What results ?

Maybe also follow the package manager's advise and try and re-install the 2 problematic kernels ??

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by dustbowldarrell on 2016-10-12
irv,

You haven't changed any network configurations before this started did you?  I was getting EXACTLY the same errors and it was a network configuration problem.  Is your server behind a dhcp router where something may have changed?  Mine was a configuration issue for assigning a static IP to my server behind a dhcp router.

---

### Post by irv on 2016-10-13
> **Bashing-om said:**
> irv; welp:



and back to my post # 45 , where we try the (P)urge option rather than --remove .
What results ?

Maybe also follow the package manager's advise and try and re-install the 2 problematic kernels ??

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

I have tried it all, I tried to remove, purge, I tried reinstalling, I check my network connections and setting (nothing changed) I can ping the server, (IP address and domain name) no problem. I can get to my web files via HTTP and FTP, everything is working but I can't use apt-get without errors. I have some security updates and can't get them because of this problem.
When I use the purge on all the problem packages it build a dependency tree for each and then at the end it give me this.
> E: Unable to locate package Linux
E: Unable to locate package kernel
E: Unable to locate package extra
E: Unable to locate package modules
E: Unable to locate package for
E: Unable to locate package version

When I installed the unity desktop it broke something. By removing the desktop it did not fix the problem.
If I can;t remove the problem packages or re-install them is there a way to install a new server over the top of what I have and not change my setting and keep all my data in place.
I just know there is a way to fix this problem, but I just don't know how. Maybe we can backup and start looking at it again.
The only thing that changed as far as the network or setting was, the provider of my Domain name move it and changed the location of my Domain so I lost my DNS setting. I had to go in and put in my static IP for my server and that part was fixed. (This was done at the domain providers site not my network). Now I have no problems getting to my server on my Network or over the Internet so that's not the problem.
I even thought about re-installing the unity desktop on my server again and see if it would fix it.
I will be gone for the day, but if you have any ideas what I can try just post them, please.
Thanks for all the help so far. And I have learned a lot so far about servers from this problem.

---

### Post by Bashing-om on 2016-10-15
irv; Hey ...

I am back .. after real adventures .. A new graphics card, and too new of hardware for open source support in anything less that 16.04. ( come to find out)
And a new SSD and working on making up a new install of 16.04 ( roll my own ) . So I have been having my own trials. I am making good progress, however, on all fronts.

Back to your issue:
The base of anything in linux is the package manager. We must get it right as the 1st priority ! I do think so .

So we return to square 1 :
show us the outputs:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT][INDENT]got to make mother package manager
[INDENT][INDENT][INDENT]Happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by irv on 2016-10-15
> **Bashing-om said:**
> irv; Hey ...

I am back .. after real adventures .. A new graphics card, and too new of hardware for open source support in anything less that 16.04. ( come to find out)
And a new SSD and working on making up a new install of 16.04 ( roll my own ) . So I have been having my own trials. I am making good progress, however, on all fronts.

Back to your issue:
The base of anything in linux is the package manager. We must get it right as the 1st priority ! I do think so .

So we return to square 1 :
show us the outputs:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT][INDENT]got to make mother package manager
[INDENT][INDENT][INDENT]Happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
Okay, lets do it:
```
sudo apt update
```
> Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]   
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [402 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [336 kB]
Fetched 929 kB in 1s (532 kB/s)                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
24 packages can be upgraded. Run 'apt list --upgradable' to see them.

```
sudo apt upgrade
```
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-3.13.0-35-generic linux-image-extra-3.13.0-35-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-43 linux-headers-4.4.0-43-generic
The following packages will be upgraded:
  cloud-initramfs-copymods cloud-initramfs-dyn-netconf
  gir1.2-dbusmenu-glib-0.4 grub-legacy-ec2 kbd libdbd-mysql-perl
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libnm-glib4
  libnm-util2 libpam-systemd libsystemd0 libtracker-sparql-1.0-0 libudev1
  linux-headers-generic linux-libc-dev overlayroot snap-confine systemd
  systemd-sysv tzdata ubuntu-core-launcher udev
24 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 11.8 MB/74.3 MB of archives.
After this operation, 68.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 tzdata all 2016g-0ubuntu0.16.04 [168 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 libdbd-mysql-perl i386 4.033-1ubuntu0.1 [85.7 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-headers-4.4.0-43 all 4.4.0-43.63 [9,948 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-headers-4.4.0-43-generic i386 4.4.0-43.63 [771 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-headers-generic i386 4.4.0.43.45 [2,286 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-libc-dev i386 4.4.0-43.63 [838 kB]
Fetched 11.8 MB in 5s (2,013 kB/s)      
Preconfiguring packages ...
(Reading database ... 182130 files and directories currently installed.)
Removing linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
[COLOR="#FF0000"]Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2[/COLOR]
Removing linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
[COLOR="#FF0000"]Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:[/COLOR]
 linux-image-extra-3.13.0-35-generic
 linux-image-3.13.0-35-generic
[COLOR="#FF0000"]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

```
sudo apt -f install
```
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-35-generic linux-image-4.4.0-36-generic
  linux-image-extra-3.13.0-35-generic linux-image-extra-4.4.0-36-generic
0 upgraded, 0 newly installed, 4 to remove and 24 not upgraded.
6 not fully installed or removed.
After this operation, 306 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 182130 files and directories currently installed.)
Removing linux-image-extra-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
[COLOR="#FF0000"]Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2[/COLOR]
Removing linux-image-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
[COLOR="#FF0000"]Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-35-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-35-generic (--remove):
 subprocess installed post-removal script returned error exit status 2[/COLOR]
Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: [COLOR="#FF0000"]FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
depmod: WARNING: could not open /var/tmp/mkinitramfs_npnqSx/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_npnqSx/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 255
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...[/COLOR]
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 255
[COLOR="#FF0000"]Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.13.0-35-generic
 linux-image-3.13.0-35-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

```
sudo dpkg -C
```
> The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-image-extra-4.4.0-42-generic Linux kernel extra modules for version 4.4.

[COLOR="#FF0000"]The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-image-4.4.0-42-generic Linux kernel image for version 4.4.0 on 32 bit x8

The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-image-3.13.0-35-generic Linux kernel image for version 3.13.0 on 32 bit 
 linux-image-4.4.0-36-generic Linux kernel image for version 4.4.0 on 32 bit x8
 linux-image-extra-3.13.0-35-generic Linux kernel extra modules for version 3.1
 linux-image-extra-4.4.0-36-generic Linux kernel extra modules for version 4.4.[/COLOR]


This is what I am getting with all the commands.

---

### Post by Bashing-om on 2016-10-15
irv; Ho Kay ..

Not looking real bad .. just a couple of old broke kernels .

Once more with feeling -
Post back:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot
dpkg -l | grep linux-

```

see what we have on the system before we go breaking the package manager.

[INDENT][INDENT]round and around we go ->>
[/INDENT][/INDENT]

---

### Post by irv on 2016-10-15
> **Bashing-om said:**
> irv; Ho Kay ..

Not looking real bad .. just a couple of old broke kernels .

Once more with feeling -
Post back:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot
dpkg -l | grep linux-

```

see what we have on the system before we go breaking the package manager.

[INDENT][INDENT]round and around we go ->>
[/INDENT][/INDENT]
```
ls -al /usr/src/
```
> total 24
drwxr-xr-x  6 root root 4096 Oct 10 15:40 .
drwxr-xr-x 10 root root 4096 Oct 10 15:41 ..
drwxr-xr-x 27 root root 4096 Sep 28 17:42 linux-headers-4.4.0-38
drwxr-xr-x  7 root root 4096 Sep 28 17:42 linux-headers-4.4.0-38-generic
drwxr-xr-x 27 root root 4096 Oct 10 13:51 linux-headers-4.4.0-42
drwxr-xr-x  7 root root 4096 Oct 10 13:51 linux-headers-4.4.0-42-generic

```
ls -al /lib/modules/
```
> total 16
drwxr-xr-x  4 root root 4096 Oct 10 15:40 .
drwxr-xr-x 25 root root 4096 Oct 10 15:40 ..
drwxr-xr-x  5 root root 4096 Sep 28 17:43 4.4.0-38-generic
drwxr-xr-x  5 root root 4096 Oct 12 16:08 4.4.0-42-generic

```
ls -al /boot
```
> total 102148
drwxr-xr-x  4 root root     1024 Oct 15 17:45 .
drwxr-xr-x 22 root root     4096 Oct 10 13:51 ..
-rw-r--r--  1 root root  1238368 Sep  6 13:17 abi-4.4.0-38-generic
-rw-r--r--  1 root root  1238807 Oct  7 19:38 abi-4.4.0-42-generic
-rw-r--r--  1 root root   193157 Sep  6 13:17 config-4.4.0-38-generic
-rw-r--r--  1 root root   193185 Oct  7 19:38 config-4.4.0-42-generic
drwxr-xr-x  5 root root     1024 Sep 28 17:43 grub
-rw-r--r--  1 root root 40281630 Oct  9 07:44 initrd.img-4.4.0-38-generic
-rw-r--r--  1 root root 40685820 Oct 12 16:08 initrd.img-4.4.0-42-generic
drwx------  2 root root    12288 Sep 15  2014 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3089791 Sep  6 13:17 System.map-4.4.0-38-generic
-rw-------  1 root root  3090253 Oct  7 19:38 System.map-4.4.0-42-generic
-rw-------  1 root root  6795680 Sep  6 13:17 vmlinuz-4.4.0-38-generic

```
dpkg -l | grep linux-
```
> ii  linux-base                            4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                        1.157.4                                                     all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-38                4.4.0-38.57                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic        4.4.0-38.57                                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-42                4.4.0-42.62                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-generic        4.4.0-42.62                                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic                 4.4.0.42.44                                                 i386         Generic Linux kernel headers
rc  linux-image-3.13.0-32-generic         3.13.0-32.57                                                i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-3.13.0-35-generic         3.13.0-35.62                                                i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-4.4.0-36-generic          4.4.0-36.55                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-38-generic          4.4.0-38.57                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-4.4.0-42-generic          4.4.0-42.62                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic   3.13.0-32.57                                                i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-extra-3.13.0-35-generic   3.13.0-35.62                                                i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rH  linux-image-extra-4.4.0-36-generic    4.4.0-36.55                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic    4.4.0-38.57                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
rU  linux-image-extra-4.4.0-42-generic    4.4.0-42.62                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-libc-dev:i386                   4.4.0-42.62                                                 i386         Linux Kernel Headers for development
rc  linux-sound-base                      1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems


---

### Post by Bashing-om on 2016-10-15
irv; Wekppp ..

we have :
> 
rH linux-image-3.13.0-35-generic 3.13.0-35.62 
rH linux-image-4.4.0-36-generic 

where 'rH' means (r)emoved but still (H)alf-installed , Got to make it all go away //

and we then address :
> 
iF linux-image-4.4.0-42-generic 

where it is desired status (i)installed . but it is only hal(F)-configured.

and as a side issue is " rc linux-sound-base 1.0.25+dfsg-0ubuntu5 all base package for ALSA and OSS sound systems " ; be nice maybe to get sound working ??

OK, again .. what results :
```

sudo dpkg -P linux-image-3.13.0-32-generic linux-image-3.13.0-35-generic linux-image-4.4.0-36-generic 
sudo dpkg -P linux-image-extra-3.13.0-32-generic linux-image-extra-3.13.0-35-generic linux-image-extra-4.4.0-36-generic 

```
depending here is what we do to get the linux-image-4.4.0-42-generic kernel fully installed .

[INDENT][INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by darkod on 2016-10-16
@Bashing, what is getting me worried is that he already tried dpkg -P or dpkg purge and it didn't work. It throws the same Failed to process errors like in post #51.

If those kernels are marked removed but still half installed, would an attempt to reinstall help? Something like:
```
sudo apt-get install --reinstall <package name>
```

If that finishes successfully then he can try removing them and it should work.

---

### Post by irv on 2016-10-16
If I try to install linux-image-3.13.0-32-generic it tells me that:
it is not available but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.

Now if I try to run sudo apt-get install linux-image-3.13.0-35-generic I get this message:
> linux-image-3.13.0-35-generic is already the newest version (3.13.0-35.62).
The following packages will be REMOVED:
  linux-image-3.13.0-35-generic linux-image-4.4.0-36-generic
  linux-image-extra-3.13.0-35-generic linux-image-extra-4.4.0-36-generic
0 upgraded, 0 newly installed, 4 to remove and 24 not upgraded.
6 not fully installed or removed.

So as it runs I get dpkg Errors.
And at the end I end up seeing:
> Errors were encountered while processing:
 linux-image-extra-3.13.0-35-generic
 linux-image-3.13.0-35-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

The same things appen when trying to install linux-image-4.4.0-36-generic

Now when I try to install linux-image-extra-3.13.0-32-generic I get the message that:
Package linux-image-extra-3.13.0-32-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

When I go to install linux-image-extra-3.13.0-35-generic and linux-image-extra-4.4.0-36-generic it is a repeat of above.

Like I said I can't install and I can't remove none of this packages because something is broke in dpkg or something else is wrong.

---

### Post by irv on 2016-10-16
Been doing some reading and it said edit the dpkg status when you can't fix broken packages. So I took a look at the dpkg status file and here is what I did and what I saw.
```
sudo nano /var/lib/dpkg/status
```
When I open the file in nano I looked up the sections in question and here is what I found. Here are two screen shots, I had more but this will tell what I found.
I didn't change anything in the dpkg status file yet, and didn't know if I should.
[ATTACH=CONFIG]271648[/ATTACH][ATTACH=CONFIG]271649[/ATTACH]

---

### Post by Bashing-om on 2016-10-17
irv; Hey ..

As dpkg is ineffective, and there is nothing left of these old kernels we can get a bite on ..I really do not know what else to try.

Editing the status file will not remove the residual files on the system . maybe at best mask them .....


Regretfully, At that point in my response my system froze up --- I have re-installed now / 

to continue .

Not saying we can not try .,. 1st however is make a back up of the status file so we can at least get back to this point if we make a serious goof .
But bear in mind; I do not feel good about this approach .

I do not have a better suggestion .

yuk

---

### Post by irv on 2016-10-17
Between working on a little Dell Inspiron 11, 3000 I picked up and my server I have been keeping myself busy.
When I get some time I am going to backup the server, wipe it clean and reinstall the server software. What ever happen when installing Unity desktop it did damage to the dpkg.
I am believing this is the quickest way to fix it. So at this point, I will mark solved and say a fresh install was the way to solve the problem. 
The thought just came to me, I have to clean up one of my backup drives so I will have room to do a backup.
I am a retired IT guy and it seems I do more IT work at home then I did when I worked for a living. The problem is, no one pays me for doing it now.

---

### Post by jeremy31 on 2016-10-17
I think you should be able to boot into the 4.4.0-38 kernel and have things work for now as that is the newest kernel you have that has a matching linux-image-extra

---

### Post by irv on 2016-10-17
I thought it was booting into the 4.4.0-38 kernel, I am not using a grub on my server. 
I am doing a backup at the moment and it will be running for awhile because I have many many files on my server.

---

### Post by irv on 2016-10-18
Okay, I got it fixed without reinstalling the server. I did what I said in post 57 I cleaned up the dpkg status file did the update and upgrade and it fixed everything but the nameserver setting. I had to
```
sudo nano /etc/resolv.conf
```
and put in the 
> nameserver 8.8.8.8
nameserver 8.8.4.4
My question is, how do I fix this so I don't have to edit the resolv.conf file every time I do a reboot?

This is what my /etc/network/interfaces file looks like.
> This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p3p1
# iface p3p1 inet dhcp
 iface p3p1 inet static
        address 192.168.1.105
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        nameserver 8.8.8.8 8.8.4.4
        dns-nameservers 8.8.8.8 8.8.4.4


---

### Post by darkod on 2016-10-18
From /etc/network/interfaces remove the line:
```
nameserver 8.8.8.8 8.8.4.4
```

That's incorrect syntax for that file, only the line 'dns-nameservers 8.8.8.8 8.8.4.4' should stay, that's the correct one.

After that restart the networking service or if it doesn't want to restart, reboot the server. Then check if /etc/resolv.conf is empty again.

---

### Post by irv on 2016-10-18
I took the line out. When I rebooted the server I made sure the resolv.conf was empty again
But I got the same nameserver error again, I believe if I put it back in the resolv.conf file again the error will go away.

---

### Post by darkod on 2016-10-18
I said to check if /etc/resolv.conf is empty, not the make sure. The goal is not to be empty of course...

I'm not sure if this can be also result of installing unity-desktop because it adds NM to control the network. Maybe it messed up part of the process that reads the /etc/network/interfaces and should populate resolv.conf with what you put in dns-nameservers...

One thing that can be tried is reinstalling resolvconf package that handles that process:
```
sudo apt-get install --reinstall resolvconf
```

Of course, you will need to put a nameserver in resolv.conf manually for that to work. Until you fix this you will need to add nameserver manually after each boot.

---

### Post by irv on 2016-10-19
It turned out to be a simple fix. I read where resolvconf file and resolv.conf step on one another. It said that when resolv.conf is present the resolvconf file will not run. (it has to do with symbolic links). So the simple fix was to just remove the resolv.conf file so it was no longer found and the resolvconf file ran, and I had the nameserver at the bottom of the file. Now when I reboot the server the nameserver is found and everything works.
Now everything is back to normal without a complete reinstall. Thanks to all for the help.
Case closed.

---

### Post by Bashing-om on 2016-10-19
irv; Outstanding !

:)

You do such good work - appreciate too that you provided your solution . Benefits all .

[INDENT][INDENT]ain't no quit 'til
[INDENT][INDENT][INDENT]it's done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by irv on 2016-10-19
I like a good challenge.
Now I have moved on to other problems. But I have them fixed already so don't need help. Now I need to break something so I can fix it.

---

### Post by Bashing-om on 2016-10-19
irv; U huh !

> **irv said:**
> I like a good challenge.
Now I have moved on to other problems. But I have them fixed already so don't need help. Now I need to break something so I can fix it.

Old axiom :
" If it ain't broke, you have not tweaked it enough "

[INDENT][INDENT]now where is that config file ??
[/INDENT][/INDENT]

---

