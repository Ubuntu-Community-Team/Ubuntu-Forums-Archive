---
title: "Ubuntu dedicated proxy server in US for use in China."
date: 2011-01-11
forum: Server Platforms
---

### Post by endor43 on 2011-01-11
TO ADMINS: There is another post like this in the networking section, but I think it's more appropriate here. So feel free to delete that one.

Hey all,

I have a question to pose. But first, I'll let you know what im working with:

Intel Core 2 Extreme QX6700 2.93ghz
Nvidia nforce 680i SLI Chipset (has integrated gigabit ethernet)
4Gb DDR2 RAM 800mhz
Dual 8800GTX in SLI
Desktop Maverick x64

I live in the US and have done so for most of my life. As such I am used to free and unrestricted internet access, at high speeds. I will soon be moving to China for about a year, and am aware that they are no so fortunate with regards to the above. I understand that speed is always going to be more of an issue with internet in China, but I'm more concerned about unrestricted access (New sites, facebook, youtube,torrent(all totally legal files of course)).

So here's the question:
How can I use ubuntu with my machine to set up a dedicated proxy server that I leave in the states, in order to be able to connect to its global ip with various programs (firefox[using foxyproxy etc], transmission,qtbittorrent, etc)when im in China, in order to have unrestricted access?

I would assume switching to server edition is part of this process, but im pretty much in the dark here. I'd really appreciate some help.

Thank you,
Endor

---

### Post by Thirtysixway on 2011-01-11
> **endor43 said:**
> TO ADMINS: There is another post like this in the networking section, but I think it's more appropriate here. So feel free to delete that one.

Hey all,

I have a question to pose. But first, I'll let you know what im working with:

Intel Core 2 Extreme QX6700 2.93ghz
Nvidia nforce 680i SLI Chipset (has integrated gigabit ethernet)
4Gb DDR2 RAM 800mhz
Dual 8800GTX in SLI
Desktop Maverick x64

I live in the US and have done so for most of my life. As such I am used to free and unrestricted internet access, at high speeds. I will soon be moving to China for about a year, and am aware that they are no so fortunate with regards to the above. I understand that speed is always going to be more of an issue with internet in China, but I'm more concerned about unrestricted access (New sites, facebook, youtube,torrent(all totally legal files of course)).

So here's the question:
How can I use ubuntu with my machine to set up a dedicated proxy server that I leave in the states, in order to be able to connect to its global ip with various programs (firefox[using foxyproxy etc], transmission,qtbittorrent, etc)when im in China, in order to have unrestricted access?

I would assume switching to server edition is part of this process, but im pretty much in the dark here. I'd really appreciate some help.

Thank you,
Endor

There are a couple of options
- vpn
- ssh tunnel
- remote desktop (if you're using desktop version as the 'server')

The fastest and easiest, imo, is ssh tunnel.  All you need to do is forward port 22 from your router to the 'server'.  Then install openssh on the 'server'.

Then from your client machine, you can type in terminal
```
ssh -D 8080 -l myserverusername your.ip.address.here
```
Then from inside firefox or chrome or whatever, you set your SOCKS host as 127.0.0.1 port 8080.  Bam, encrypted tunnel to the states!

Just watch out because this doesn't tunnel DNS requests, so if they filter by dns you may need to look into other ways to proxy or find some unblocked dns servers (or even use hosts file to manually point domains to ip addresses)

Also you may want to look into something like dyndns.org or no-ip.com if your 'server' uses dhcp from the isp to get its IP address.

good luck!

---

### Post by Kljuka on 2011-01-11
I think Thirtysixway explained really great.

Just to add:
if you want DNS requests being tunneled through ssh tunnel as well, you must just configure your browser to do so (for web browsing of course). In firefox, you just enter address:
```
about:config
```And Change network.proxy.socks_remote_dns from false to true.

---

### Post by solongsoho on 2011-10-25
I am just curious if this works in 11.10. I am also in China for a year and I can't bare their restrictions anymore.

---

### Post by Lars Noodén on 2011-10-25
> **solongsoho said:**
> I am just curious if this works in 11.10. 

Using SSH as a SOCKS proxy as described above works in all versions of Ubuntu.  You just need an outside machine to connect to using SSH.

---

