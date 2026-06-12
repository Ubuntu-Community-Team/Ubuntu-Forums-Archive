---
title: "Unattended upgrade proxy settings"
date: 2023-02-15
forum: Server Platforms
---

### Post by julian-g71 on 2023-02-15
Hi - I wonder if someone could help me with an issue I've just spotted with of our Ubuntu servers that use a proxy for internet access. I'm using some custom settings with unattended upgrades to update packages over night. On machines that have direct internet access it's working perfectly. However for machines that have to use a proxy to get out to the internet it's failing and I can see why, just not how to fix it.

I can see that the apt-daily.service has a ExecStartPre as such:

ExecStartPre=-/usr/lib/apt/apt-helper wait-online

If I check the systemctl status of the service or indeed run the above command it fails with:

Process: 2666860 ExecStartPre=/usr/lib/apt/apt-helper wait-online (code=exited, status=100)

Or from the CLI:

/usr/lib/apt/apt-helper wait-online
E: Sub-process nm-online returned an error code (1)
echo $?
100

I suspect this is because the command is trying to go direct to the internet and not via the proxy. If I run apt update or upgrade commands these work fine because I have a /etc/apt/apt.conf.d/proxy.conf file configured.

I read somewhere that apt-help wait-online randomly picks an entry out of the sources.list file and tries to connect to it.

So my question is, is there a way to tell apt-helper to use the proxy settings?

I did try this but alas it also fails.

/usr/lib/apt/apt-helper -o Acquire::HTTP::proxy="http://<our-working-proxy>:3128" wait-online

Any help would be greatly appreciated, thanks.

---

### Post by LHammonds on 2023-02-16
Can you see any denies on the proxy?  Maybe the proxy is blocking traffic.  Just grabbing at straws....I don't run an Internet proxy.

LHammonds

---

### Post by julian-g71 on 2023-02-19
So I've figured this one out, spent sometime yesterday going over it. The command that was failing was:

/usr/lib/apt/apt-helper wait-online

So I ran this with a strace in front of it and I could then see that a call to the command nm-online was being made, and from the man-page "nm-online - ask NetworkManager whether the network is connected"

BUT I'm not using network-manager to manage my network connections, as part of our server build process we switch to networkd in the netplan config files.

So a quick search and I needed to do the following:

systemctl stop NetworkManager.service
systemctl stop NetworkManager-wait-online.service
systemctl stop NetworkManager-dispatcher.service
systemctl stop network-manager.service
systemctl disable NetworkManager.service
systemctl disable NetworkManager-wait-online.service
systemctl disable NetworkManager-dispatcher.service
systemctl disable network-manager.service
apt-get purge network-manager
apt autoremove
reboot

As soon as the server came back up and I run this command now:

/usr/lib/apt/apt-helper wait-online

It works perfectly and my apt-daily service is working as expected. The initial thought it could be proxy related did kind of make sense, but a red herring this time. Glad it's sorted now.

---

