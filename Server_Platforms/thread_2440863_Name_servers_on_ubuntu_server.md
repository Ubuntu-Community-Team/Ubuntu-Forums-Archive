---
title: "Name servers on ubuntu server?"
date: 2020-04-16
forum: Server Platforms
---

### Post by josephchrzempiec on 2020-04-16
Hello I'm trying to figure out how i can make my own name servers for my domain to point to my local at home/Office web server. I do have Static ip address. But everything i found so far is for dns for pihole. Other things i found is kinda incomplete. The one place i found online only shows to have the name servers/dns on the same system as my apache webs site. Is there a palce i can go to and learn how to setup a name server? Unless I'm asking the wrong question in google search I'm finding the wrong things.


Joseph

---

### Post by TheFu on 2020-04-16
There are 3 ways to have name resolution work on a Linux internal network.
[LIST]
[*]/etc/hosts on every machine
[*]Run a named service, like BiND or ProDNS
[*]run Avahi on **every device** and get used to {hostname}.local names  Avahi is the Linux "ZeroConf" program.
[*]Have your home-Router do DNS
[*]install something like pi-hole for a local DNS
[/LIST]

BiND is a pain to configure, and commonly hacked when accessed by the internet, so most people just use pre-existing solutions.  The 2nd time i was hacked, they came in using BiND.

Not all home routers have DNS capabilities.  Some may (dd-wrt), but require fairly complex text setups. [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) shows the setup for an old version config. i think setting up BiND is harder.

Almost every network would be improved by a pi-hole-like DNS system, so if it was me, I&#8217;d create a LXD container running the pi-hole system and use that for internal DNS too. Heck, think i need to do that for my LAN.

A pi-hole doesn't have to run on a raspberry-pi, if that isn't clear.

---

### Post by TheFu on 2020-04-16
So, setup an LXD container with a pi-hole instance inside following this:
[https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337](https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337)
it was pretty easy.  Have a few of my DHCP machines using it, but need to enable DNS-over-HTTPs before moving some servers to it.

i'm not thrilled with the added storage layers that LXD seems to really want.
```
disk -- partition --- lvm --- lv --- zfs --- container
```
but figure that can be fixed.  Really wanted an LV to be used specifically for this container, but I’m new with lxd. They really want us to use zfs.
i already had a bridge on the physical machine. it hosts about 10 VMs (kvm) already, so hooking up lxd to use that wasn't hard.

The only thing that didn't work as expected was the pi-hole wasn't providing DNS on the LAN interface, so i had to manually enable that in the [http://pihole/admin](http://pihole/admin) webpage.  Also had to set a static ip for the container.  Did that in the expected netplan file.

Now, how to run a local DNS inside the pi-hole is next. ................

---

### Post by TheFu on 2020-04-16
[https://discourse.pi-hole.net/t/howto-using-pi-hole-as-lan-dns-server/533](https://discourse.pi-hole.net/t/howto-using-pi-hole-as-lan-dns-server/533) has instructions to add a local DNS to the pi-hole.  Wow, was that trivial.
```
# more /etc/dnsmasq.d/02-lan.conf 
addn-hosts=/etc/pihole/lan.list
```

Then create the /etc/pihole/lan.list just like any /etc/hosts, just missing all the localhost stuff for IPv4 and IPv6. For example:

```
172.22.22.31 monowall monowall.my.lan
172.22.22.32 sovereign sovereign.my.lan
172.22.22.33 mattermost mattermost.my.lan
172.22.22.34 nextcloud  nextcloud.my.lan

```
They say to add your internal LAN domain to the file. I didn't add that initially.  Some things broke, so I added them in. Then had to fix the /etc/resolv.conf  *search my.lan* line.
Then just restart the dns ....```

# pihole restartdns
```

From the time I searched, read, and had the local DNS working, was about 4 minutes.

---

### Post by aljames2 on 2020-04-16
Good stuff & great guidance @TheFu

I’m considering this myself.  I currently have a DNS resolver server running on my pfSense router which handles all the DNS resolution.  But, thinking about this as a side project.

---

### Post by Doug S on 2020-04-18
> **TheFu said:**
> BiND is a pain to configure, and commonly hacked when accessed by the internet, so most people just use pre-existing solutions.  The 2nd time i was hacked, they came in using BiND.I use bind for my LAN only, and leave the external DNS stuff to my domain name registrar and ISP.

Then, and for example, anyone with a portable device doesn't have to worry about how to access the externally facing web server, as DNS lookups return a local address when they are on the local LAN and return the external address when they are somewhere else.

I used the [ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/dns.html") as the main reference.

---

