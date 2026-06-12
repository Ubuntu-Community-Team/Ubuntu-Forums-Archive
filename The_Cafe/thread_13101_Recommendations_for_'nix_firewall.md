---
title: "Recommendations for 'nix firewall"
date: 2005-01-28
forum: The Cafe
---

### Post by Dylanby on 2005-01-28
I'm downloading a few firewalls to try them out.

I'd like to use an old system I have lying around for firewall, dhcp, etc.

So far I'm looking at SmoothWall, IPCop, ClarkConnect, m0n0wall & Devil-Linux.

Anyone tried these? I was interested in hearing feedback from others who've used them.

My networking skills are about average.

---

### Post by az on 2005-01-28
Ubuntu has shorewall in universe.  Install shorewall and shorewall doc and you'll be doing firewalling as well as NAT in minutes.  Add to that dnsmasq and you are good to go.

I think firestarter does NAT, too.  It is in the backports.

You can also use guarddog, if you are used to a gui.
You will need guidedog, too for NAT (masquerading :  Internet connection sharing)

---

### Post by Dylanby on 2005-01-28
Thanks azz. I've download the shorewall-doc & will read it later.

The target machine is old so I'm not sure I can pare Ubuntu down as much as I'd like too. Trial & error!

---

### Post by az on 2005-01-28
I'm running a webserver (Drupal on apache using mysql) on a 200 MHz pentium 1.  It is my router.  It runs Ubuntu.

Of course, I do not have any graphical environment installed - which is why I use shorewall.

Boot the installer and start the install with "custom"

---

### Post by thomasmathiesen on 2005-03-28
I am running IPCop, and I just love it.
It's a 40MB cd iso, and when installed, I think it's about 110MB.
Be careful installing it, cause it will trash your partitions without asking you first (DON"T think this will be dual boot).

It can pick up almost any NIC in the world (from my experince).
Mine is connected to an ADSL connection, and it's been up for ages.

The only problem I am having is that the VPN solution ain't easy, if you want to connect a linux client (road-warrior) to it. M0n0Wall has BOTH pptp and ipsec vpn's, whilst ipcop only has ipsec (currently openswan). The issue with this is that it seems to be a pain to setup on a linux client.

I used to run smoothwall, but as the maker charges money for most interesting features, I stick with something that is totally free. I think IPCop is a fork of Smoothwall.. or at least used to be.

M0n0Wall is based on FreeBSD, whilst IPCop was based on RedHat 7.4 (I think ipcop 1.4 is based on Linux From Scratch).

Setting up Ubuntu/Fedora as firwall vs. installing a plain firewall os->
It's just alot easier installing a distro that is made to be a firewall (and only a firewall). I ran a redhat9 and then fedora box as a firewall, and it works.. but it's more of a hazzle if things go wrong (I used to be more of a newbie back then).\

Good luck!

---

### Post by jdong on 2005-03-28
IPCop is my first choice on older hardware (<75MHz), but for systems faster than that, I build them from Ubuntu with grsecurity-patched kernels and Shorewall.

---

### Post by tkiesel on 2005-03-28
I've been interested in using an old box for a firewall, mainly to get traffic shaping/bandwidth shaping features so the family's online games and web browsing don't slow down when someone's pulling a big download (i.e. me grabbing or seeding the latest Ubuntu .iso on Bittorrent. heehee.)

I'm given pause though (code for "my wife had a salient point when we discussed it") at the probable energy cost of using an old computer as a router.  If the old box costs more to run for a couple of years than a purchased router would cost up-front plus running juice (A linksys with 3rd party firmware to get me the aforementioned bandwidth shaping), then I'm just tossing money away for the "cool factor" of having a linux router.

I can attest to the general fun factor of running 'nix firewalls, though. Well before Linux was even on my radar, my roomate was running Debian for his personal machine and had our apartment Internet access routed through an old Sun SPARCstation that he'd commandered as a firewall. :)

---

### Post by garyng on 2005-03-28
[QUOTE=tkiesel]I've been interested in using an old box for a firewall, mainly to get traffic shaping/bandwidth shaping features so the family's online games and web browsing don't slow down when someone's pulling a big download (i.e. me grabbing or seeding the latest Ubuntu .iso on Bittorrent. heehee.)

I'm given pause though (code for "my wife had a salient point when we discussed it") at the probable energy cost of using an old computer as a router.  If the old box costs more to run for a couple of years than a purchased router would cost up-front plus running juice (A linksys with 3rd party firmware to get me the aforementioned bandwidth shaping), then I'm just tossing money away for the "cool factor" of having a linux router.

I can attest to the general fun factor of running 'nix firewalls, though. Well before Linux was even on my radar, my roomate was running Debian for his personal machine and had our apartment Internet access routed through an old Sun SPARCstation that he'd commandered as a firewall. :)[/QUOTE]

linksys WRT54G, you can run linux on it with 100% control. I once even tried nfs mounted a debian woody to play around. I use openwrt as the base distro which has everything one needs. Consume less than 10W(max, more like 5-7 normally).   It pays for itself in a year time in the electricity bill, in my area. And I still have all the cool factors I want.

---

### Post by tkiesel on 2005-03-28
[QUOTE=garyng]linksys WRT54G, you can run linux on it with 100% control. I once even tried nfs mounted a debian woody to play around. I use openwrt as the base distro which has everything one needs. Consume less than 10W(max, more like 5-7 normally).   It pays for itself in a year time in the electricity bill, in my area. And I still have all the cool factors I want.[/QUOTE]

I'm gonna look into that one. That'll take quite a bit of messing with and tweaking to do what I think I want it, but what a learning experience!!

---

