---
title: "DNS Client Setup In Ubuntu Server"
date: 2013-06-06
forum: Server Platforms
---

### Post by springshades on 2013-06-06
Hi all,

Not sure if this is the best section of the forum to post something like this, and I imagine it's probably not a particularly difficult issue, but my google-fu has failed me.

I'm using Ubuntu Server 12.04, and there is a small issue which leads me to suspect that I must have the DNS settings incorrect somewhere in my configuration. In the server room that I am using, I am normally able to connect via ssh to a machine on the *local* network with a shortened command:

ssh username@servername

However, on the server that I have set up, *outgoing* connections to other machines on the *local* network require:

ssh [email]username@servername.domain.name[/email]

Note the addition of the domain name. Incoming connections to this machines that I've set up still work with the shortened version, it is only outgoing connections which give the normal error:

ssh: Could not resolve hostname servername: Name or service not known


Currently, the way that I've attempted to set this machine up is to manually edit:

/etc/network/interfaces

It contains the lines:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address
    netmask
    gateway
    dns-nameservers
```

I've omitted the actual IP addresses. So with this set up, all incoming tests appears to work, and all outgoing connections work as long as the full domain is specified. However, all the other machines on this local network are able to make outgoing connections on the local network using only the server name without the full domain. Also, note that this machine is not supposed to be functioning as a DNS Server (unless I've somehow messed something up).

This wouldn't be a big deal except that I'll be building more machines to be installed there, and I'd like to get the loose ends nailed down. Most of the expertise at the location is with Red Hat/CentOS or Novell, and most of the distros seem to have slight differences in the way they do these sorts of things.

Thanks for any help.

---

### Post by matt_symes on 2013-06-06
Thread moved to **server platforms**.

I have left a redirect in networking and wireless as well.

---

### Post by Doug S on 2013-06-06
Have a look at [this]("http://ubuntuforums.org/showthread.php?t=2067993&highlight=dns-search") and [this]("http://ubuntuforums.org/showthread.php?t=2112686&highlight=dig") threads.
I think you want a dns-search directive in your /etc/network/interfaces file.

---

### Post by papibe on 2013-06-06
Hi springshades.

My first guesses would be that either you are not using the same DNS as the other servers, the other servers have custom lines on their /etc/hosts, or you are missing a search field in your resolv.conf

In any case, may be explaining how the name resolution works it could offer more ideas.

The rules on how to resolve a name are set in this file:
```
/etc/nsswitch.conf
```
Specifically in the line:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
In this case, it start using files. That means /etc/hosts. You could set up a custom resolutions that supersede the others. For example,
```
192.168.1.51    machine
192.168.1.52    server
```
Then, since avahi is installed, it would try to resolve the address by using the 'zero configuration' protocol (.local domains).

Finally, it would try using the name service.

Since you are not using DHCP, this line on your /etc/network/interfaces:
```
dns-nameservers 192.168.1.1
```
would end up in this file:
```
/etc/resolv.conf
```
in a line like this:
```
nameserver 192.168.1.1
```
Note that in 12.04+ this file should be a symbolic link:
```
ls -l /etc/resolv.conf 
lrwxrwxrwx 1 root root 29 May 15  2012 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
```
When you are using DHCP, you also receive a search domain, which is usually added to this file in a line like this:
```
search domain.name
```
That way any domainless name, like 'servername', would be transform into 'servername.domain.name', before being sent to the DNS.

Since you are not using DHCP, in order to the 'search' domain to be added to /etc/resolv.conf, you need to add that information manually to '/etc/network/interface':
```
...
iface eth0 inet static
    ...
    dns-search  domain.name
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by springshades on 2013-06-06
Thanks very much. I think that the dns-search line is indeed the culprit. Unfortunately, I won't be able to test for several days when I can do a reboot of the machine and services, but I'm about 99.9% sure that is the issue. I had already checked that resolv.conf was being modified correctly (and I know that DNS is mostly working, or else using the full domain names wouldn't connect me to remote servers either). It's one of those options that I didn't come across in the "man interfaces" page, and the fact that it's probably rare outside of server usage explains why I didn't come across it easily via google. Thanks again.

---

### Post by papibe on 2013-06-06
You don't need to restart the machine to apply that change.

Modify your /etc/network/interfaces, and then run:
```
sudo service networking restart 
```
Regards.

---

