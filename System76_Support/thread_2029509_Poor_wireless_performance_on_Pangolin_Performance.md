---
title: "Poor wireless performance on Pangolin Performance"
date: 2012-07-19
forum: System76 Support
---

### Post by p_hudson on 2012-07-19
Greetings all. I have a Pangolin computer running 10.04 that I have loved. Somewhat recently is has developed an annoying habit of disconnecting from the router, or slowing to the point where the internet is unusable. Reconnecting to the wireless network, or even turning wireless off then on, will help.

Any ideas on steps to take? the router seems to be fine; other computers connect with no issues.

---

### Post by Bucky Ball on 2012-07-19
When it next disconnects (you could also do this when it just get slow or wobbly), stop what you are doing and immediately open a terminal and issue this:

```
dmesg
```You should see the disconnect down there near the bottom of the read out. Post the last part of the readout here along with the output of these two commands. please:

```
iwconfig
sudo lshw -C network
```;)

---

### Post by gaussian on 2012-07-19
Does Pangolin have an Intel Wireless card? Try the following: 
1) make a file in /etc/modprobe.d called iwl.conf containing:
```

options iwlagn 11n_disable50=1 swcrypto50=1 

```

2) Reboot and check if things are better.

If you upgrade to 12.04 the line to add would be
```

options iwlwifi 11n_disable=1

```

What this does it disables the newest (802.11N) wireless mode and forces the use of 802.11G mode. Unfortunately in my experience 802.11N support in Linux is still shaky, at least for Intel cards. The good news, at least for my own use, is that a reliable 54MBs 802.11G connection is plenty fast.


Added caveat: I should state that I had not had success with 802.11N connection in my home network with Linux+Intel Cards (two different computers). Via Google I can find that I am not the only one with problems, but it would not seem like everyone is having these problems. So YMMV: it might be specific to a particular router etc.

---

### Post by p_hudson on 2012-07-27
> **Bucky Ball said:**
> When it next disconnects (you could also do this when it just get slow or wobbly), stop what you are doing and immediately open a terminal and issue this:

```
dmesg
```You should see the disconnect down there near the bottom of the read out. Post the last part of the readout here along with the output of these two commands. please:

```
iwconfig
sudo lshw -C network
```;)
Thanks for the reply. on the first one, what exactly am I looking for? Keep in mind, I am not an everyday command-line user.

iwconfig yields this:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"lothrik"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 58:6D:8F:8A:76:1F   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

result for the 2nd command is
> *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:9a:c9:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.110 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f0300000-f0301fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:07:00.5
       logical name: eth0
       version: 03
       serial: 00:90:f5:a1:0f:05
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 memory:f0400000-f0403fff ioport:4400(size=128) ioport:4000(size=256)


---

### Post by gaussian on 2012-07-27
Your problems look identical to what I was having (N-connection, connection speed 1Mbs). Try the following (since you can always undo this by just rebooting your computer):

```

sudo rmmod iwlagn

```

You will loose your wireless connection when you do that.

```

sudo modprobe iwlagn 11n_disable50=1 swcrypto50=1

```

And reconnect. Test if this makes it work better.

---

### Post by p_hudson on 2012-08-19
^^ what you posted in the last post seems to have done the trick. any way to make this permanent?


Also, a few unrelated questions:
1) any way to PERMANENTLY save the wireless password? it asks for it every time
2) any way to disable key ring? I never even set it up, it keeps asking for it

---

### Post by gaussian on 2012-08-20
To make changes permanent, refer to post #3 of this thread. Don't know the answers to other questions.

---

