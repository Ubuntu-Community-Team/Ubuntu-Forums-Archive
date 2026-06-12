---
title: "LTSP install cannot recognize more than one NIC"
date: 2012-03-09
forum: Server Platforms
---

### Post by ceaecc on 2012-03-09
Installing Edubuntu 11.10 on a Del Optiplex 755 with mainboard network  connector plus another network card plugged into a PCI slot, only one  network connection is not "unavailable" at a time. Whether I boot up  with the internet line connected to eth1 (the connector embedded on the  mainboard) or to eth0 (the PCI card) always the one connected to the  internet is declared as "connected" and the other "unavailable." This is  the case whether I am installing Edubuntu on the hard disk and choose  to include LTSP, or whether I have booted from the DVD and click to test  LTSP. I get the same results from nm-tool, except that the term for  State is "unmanaged" instead of "unavailable" when I make no attempt to  use LTSP.

I did find some references to "unavailable" or a few to "eth0  unavailable" in Ubuntu forums, but the replies seem to focus on complex  steps to install drivers made for Windows rather than included with  Edubuntu. Since the problem is reversible, depending on which network  connector I choose to plug my intenet cable into, I wonder if someone  might know about something simple I overlook, or if there it is a known  issue with Dell Optiplex. I can provide some readouts to terminal  commands. I want this server to have two separate networks, one for the  internet and the other LTSP. As it stands, as soon as LTSP is set up the  internet connection is shut off because only one NCI is available. I  did read about the possibility of eth0:1 but I do not want to use that  workaround. This Core-duo computer should be able to handle two NCI  connections.

At the moment with eth1 being used for the internet -- but it is the same situation but reversed when I plug it into the other connector -- here is a nm-tool readout:

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unmanaged
  Default:           no
  HW Address:        00:21:9B:3F:31:F3

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:E0:4C:89:3B:79

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         xx.xx.xxx.177
    Prefix:          24 (255.255.255.0)
    Gateway:         27.100.134.1

    DNS:             xxx.xxx.101.2
    DNS:             xxx.xxx.252.2

---------------------------------------------

Thank you.

---

