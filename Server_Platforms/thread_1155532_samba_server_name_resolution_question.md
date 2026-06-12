---
title: "samba server name resolution question"
date: 2009-05-10
forum: Server Platforms
---

### Post by chemburn on 2009-05-10
Hi, all, as usually I have jumped right in and am now at a point where I can't seem to wrap my brain around a bit of the terminology in smbclient's man, so as usual I would like to say..bare with me if this seems a bit um....well dumb.

So I have ubuntu server 8.10 running with samba as a home file server here, we have several windows and linux machines up righ now. I have all the windows machines seeing the appropriate shares and all seems to be working fine there, the problem is with my ubuntu machines, I keep getting intermittent failures to access the shares when using nautilus. works sometimes, other times it can't seem to find the server.Annoyingly, it will work on the VM of xp on the laptop...just not from ubuntu So I have googled a bit on it, seems I can find it via the ip address on the network ie; //192.168.xxx.xx/music, just not when I try //frankenchrist/music/. So from everything I have been reading I am gathering its just not resolving the dns on the host name correctly. 

Heres where my brain seemed to fall off the bus though, there are several hosts related files in /etc/ on my client machine, and i am getting the impression one of them is where I would simply add something to the effect of "192.168.xxx.xx = frankenchrist" I am just not sure which one (or its entirely likely this is the wrong idea entirely). I know it wouldn't be /etc/hostname since thats what tells my system its name, was just wondering if someone could enlighten me a bit on the the /etc/host.config, /etc/hosts, and the /etc/host.allow *deny?

The server is set to a static IP, all I assume I need is to direct that IP to the unc for the server correct? and if so, where would I put that info?

---

### Post by doas777 on 2009-05-10
your looking for /etc/hosts

this page describes the format: [http://publib.boulder.ibm.com/infocenter/systems/topic/com.ibm.aix.files/doc/aixfiles/hosts.htm](http://publib.boulder.ibm.com/infocenter/systems/topic/com.ibm.aix.files/doc/aixfiles/hosts.htm)

it's really just
```
HostnameA     192.168.0.1
HostnameB     192.168.0.2
```

---

### Post by chemburn on 2009-05-10
woot! thank you!

---

