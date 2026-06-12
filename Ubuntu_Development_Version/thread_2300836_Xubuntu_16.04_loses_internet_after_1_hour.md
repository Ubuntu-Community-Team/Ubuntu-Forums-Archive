---
title: "Xubuntu 16.04 loses internet after 1 hour"
date: 2015-10-28
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2015-10-28
I installed the final release DVD for Wily and this started happening. At first I thought it was an anomaly.

So a couple days ago I changed sources to Xenial and it's still doing it. I have a conky that tells me how long the system has been up so I know now.
Any time after a hour I lose internet connectivity and have to reboot if I want internet access.

Is any one else having this problem or know how I fix it?

Regards

---

### Post by slickymaster on 2015-10-28
I have a fresh 16.04 VBox (2015-10-27 image) running continuously for nine and half hours now, without any connectivity issues.

---

### Post by Cavsfan on 2015-10-28
I don't know why it's doing this but every hour and 2 or 10 minutes or whatever no internet. My conky even displays the alert that there's no internet.

Maybe a bigger hammer? :P

---

### Post by Cavsfan on 2015-10-28
I had it plugged directly into my modem which I didn't use to do.
But, I can't see that being the problem. My son has a beast of a PC and we upgraded internet speeds to 150mbps down and 15mbps up but my ethernet card is only 10/100MB so I couldn't get that anyway.

He gets like 189mbps down while testing.

I'll just leave it plugged into the wireless router like I use to do and see what happens.

---

### Post by QDR06VV9 on 2015-10-28
I too was seeing this a couple of days ago.
Don't know if this was a fix or not, but I have to have openvpn and gnome-openvpn network-manager and after those were installed
problem gone.
My cards
```
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller           driver: sky2
           IF: eno1 state: down mac: 90:fb:a6:4b:3d:38
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
           IF: enp4s6 state: unknown speed: 100 M
```
Card being used now is Realtek RTL
See this in gentoo also.

---

### Post by Cavsfan on 2015-10-28
> **runrickus said:**
> I too was seeing this a couple of days ago.
Don't know if this was a fix or not, but I have to have openvpn and gnome-openvpn network-manager and after those were installed
problem gone.
My cards
```
Network:   Card-1: Marvell 88E8071 PCI-E Gigabit Ethernet Controller           driver: sky2
           IF: eno1 state: down mac: 90:fb:a6:4b:3d:38
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
           IF: enp4s6 state: unknown speed: 100 M
```
Card being used now is Realtek RTL
See this in gentoo also.

This is what I have:
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 529c
    Physical Slot: 33
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at e800 [size=256]
    Memory at febff000 (64-bit, non-prefetchable) [size=4K]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169

```
If it happens again which most likely it will, I'll install openvpn. I checked apt-cache policy and it didn't show gnome-openvpn as being available.

---

### Post by flocculant on 2015-10-28
> **Cavsfan said:**
> ...

Is any one else having this problem or know how I fix it?

Regards

As far as an issue - this machine was turned on at ~07:00 it's now ~20:00 and is normal no connection problems. 

If you've got an issue it's going to be hardware based in the beginning. 

Check the logs when you lose connectivity. 

Check the interwebs for your hardware.

---

### Post by zika on 2015-10-28
> **Cavsfan said:**
> If it happens again which most likely it will, **I'll install openvpn**. I checked apt-cache policy and it didn't show gnome-openvpn as being available.```
:~$ aptitude search key_word openvpn
p  gadmin-openvpn-client                                                                                                                                  - GTK+ configuration tool for openvpn (client)                                                                                                                    
p   gadmin-openvpn-client:i386                                                                                                                             - GTK+ configuration tool for openvpn (client)                                                                                                                    
p   gadmin-openvpn-client-dbg                                                                                                                              - GTK+ configuration tool for openvpn (debug for client)                                                                                                          
p   gadmin-openvpn-client-dbg:i386                                                                                                                         - GTK+ configuration tool for openvpn (debug for client)                                                                                                          
p   gadmin-openvpn-server                                                                                                                                  - GTK+ configuration tool for openvpn (server)                                                                                                                    
p   gadmin-openvpn-server:i386                                                                                                                             - GTK+ configuration tool for openvpn (server)                                                                                                                    
p   gadmin-openvpn-server-dbg                                                                                                                              - GTK+ configuration tool for openvpn (debug for server)                                                                                                          
p   gadmin-openvpn-server-dbg:i386                                                                                                                         - GTK+ configuration tool for openvpn (debug for server)                                                                                                          
p   network-manager-openvpn                                                                                                                                - network management framework (OpenVPN plugin core)                                                                                                              
p   network-manager-openvpn:i386                                                                                                                           - network management framework (OpenVPN plugin core)                                                                                                              
p   network-manager-openvpn-gnome                                                                                                                          - network management framework (OpenVPN plugin GNOME GUI)                                                                                                         
p   network-manager-openvpn-gnome:i386                                                                                                                     - network management framework (OpenVPN plugin GNOME GUI)                                                                                                         
p   openvpn                                                                                                                                                - virtual private network daemon                                                                                                                                  
p   openvpn:i386                                                                                                                                           - virtual private network daemon                                                                                                                                  
p   openvpn-auth-ldap                                                                                                                                      - OpenVPN LDAP authentication module                                                                                                                              
p   openvpn-auth-ldap:i386                                                                                                                                 - OpenVPN LDAP authentication module                                                                                                                              
p   openvpn-auth-radius                                                                                                                                    - OpenVPN RADIUS authentication module                                                                                                                            
p   openvpn-auth-radius:i386                                                                                                                               - OpenVPN RADIUS authentication module                                                                                                                            
p   openvpn-auth-radius-dbg                                                                                                                                - debugging symbols for openvpn-plugin-radius                                                                                                                     
p   openvpn-auth-radius-dbg:i386                                                                                                                           - debugging symbols for openvpn-plugin-radius                                                                                                                     
p   openvpn-blacklist                                                                                                                                      - list of blacklisted OpenVPN RSA shared keys 
```What would be reason to install openvpn packages if You do not use OpenVPN? Do You? If You, never the less, do install those packages do check If You do have that openvpn daemon running... ;) Also, check if NM is using plugin installed. It should be enabled in /etc/NetworkManager/NetworkManager.conf (in appropriate section). Do check also which connection is NM using and if there is some switch of NIC added in upgrade so that it makes NIC go to sleep... And so on. In my book installing plugins that are not to be used is on the end of list and is marked &#8222;desperate moves&#8220;... ;)
> **flocculant said:**
> As far as an issue - this machine was turned on at ~07:00 it's now ~20:00 and is normal no connection problems. 
If you've got an issue it's going to be hardware based in the beginning. 
Check the logs when you lose connectivity. 
Check the interwebs for your hardware.Exactly...

---

### Post by Cavsfan on 2015-10-28
It's never done this in Arch, Windows 10 or even Wily before that final release ISO was installed. But, I've been up now for 2 hours and it hasn't stayed connected this long.

I don't understand how this could affect it but it's plugged into the wireless router like it always has been prior to the modem upgrade.

I know I cannot connect to my wireless printer without being plugged into the wireless router. So, maybe it's fixed.

---

### Post by QDR06VV9 on 2015-10-28
openvpn and networkmanager-openvpn  and [COLOR=#000000][FONT=Ubuntu Mono]network-manager-openvpn-gnome [/FONT][/COLOR]were needed for my VPN service only.
Sorry should have been a little clearer on that. and those could be named a little differently I'm on Arch today.
Regards

---

### Post by Cavsfan on 2015-10-29
OK, thanks for the explanation.

I believe the problem is solved. 

[[IMG]http://www.speedtest.net/result/4787052183.png[/IMG]]("http://www.speedtest.net/my-result/4787052183")

---

### Post by flocculant on 2015-10-29
> **Cavsfan said:**
> OK, thanks for the explanation.

I believe the problem is solved. 


what did you do to fix it?

---

### Post by Cavsfan on 2015-10-29
> **flocculant said:**
> what did you do to fix it?

Not completely sure. I had plugged the ethernet cable back into the router as it's been since 2009. I had it plugged directly into the modem for about a week.
I don't think that would make a difference. Maybe it just fixed itself IDK.

But, it's fixed.

---

### Post by flocculant on 2015-10-29
so - given you've not done anything else it's likely 


> **flocculant said:**
> ...
If you've got an issue it's going to be hardware based in the beginning. ...

:)

Just so you know, we are concentrating on apps/packages this cycle - we're not pushing iso testing for xubuntu. Bit pointless given the numbers of people we have available when the image is much of a muchness for globalbuntu.

So expect me and slickymaster to ask things ;)

---

### Post by Cavsfan on 2015-10-30
Fine with me. I don't plan to install from ISO before alpha or beta at the earliest. If this goes bad so be it. :)

But, this definitly was not hardware related otherwise Arch Linux and Windows 10 would have done the same thing and they never once had a problem with internet access. ;)

---

