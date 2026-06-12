---
title: "VirtualBox, Guest Windows networking and USB issues..."
date: 2008-12-14
forum: Virtualisation
---

### Post by ashwinipn on 2008-12-14
Hi,
I am using Ubuntu Intrepid 64 bit and and learning to solve many a issues. It has been interesting journey so far. Currently, struggling with some virtualization issues. The story goes like this:

As wanted to wean from the "obvious" thrust upon option (Windows) and assert my own choice, my transition to Ubuntu has been a good experience ever since August 2008 when for the fist time I started to venture. Now pretty much I work, enjoy, and everything on ubuntu, that too far far better quality than the previous one, despite of the fact that even the motherboard maker had developed and supplied custom made softwares/drivers for the "market leader". But there are still some things for which I go back to Windows. Among other issues, the most important thing is my VOIP phone (Magicjack) that I use as landline.

For this purpose, I have a dual boot system, the other being Windows Vista Ultimate 32 bit. Previously I have tried WINE but since I don't play games, it was of no use to me. Recently I happen to know about virtual machine and after some 'homework' decided to install VirtualBox (VB, current edition 2.0.6) non OSE (because wanted USB functionality). Currently, I am able to run Windows XP as well as Vista successfully on my system but facing some issues regarding networking and USB issues. First I will talk about networking and then USB.

Although NAT is easily working and I am pretty much able to do things but due to my usages (like softphones and the likes that use UDP port), I am yet to utilize it to the fullest. NAT, although supports UDP, but it is not as reliable and because of that, voice data faces problem with that. I tried networking through Host Interface and tried both the approaches as per the native "Ubuntu" (uml-net) and from "VirtualBox" (bridge-utilities), the two approaches to bridging and interface building (e.g., br0 and vbox0, and br0 and tap0), without success. The bridging is done and I get internet connection to my Host (although networking icon shows no signs for some reason), but it does not get established for the virtual machines. I would really appreciate if anyone help with this.

USB: Although my USB mouse and printer work fine, I have difficulty getting other USB connected peripherals work. Here let me specify a little more with a contexual background. Hopefully it may help in understanding. I currently have few hardwares.

1. Magicjack VOIP phone adapter by Tigerjet (officially supported only on Windows and Apple. My idea to get it captured by VB and work in Windows environment. This way, there will not be any need for the Dual boot and consequent space and time wasting). 

2. Creative Webcam Live Ultra (does not work on Ubuntu at all, from previous to this current installation. My idea was to let it get captured 
by VB and get it worked on Windows, on which, it works reliably). Later I may try getting it worked on Ubuntu as well.

3. Creative Wireless Desktop, Keyboard and Mouse (was working well on Gutsy, worked about 15-30 minutes every bootup on Hardy, not working at all on both Intrepids 32 and 64 bits).

4. Azio Bluetooth Adapter (Cambridge Silicon Radio, Ltd Bluetooth Dongle. Gets recognized on both intrepids 32 and 64 bits as well as on hardy. On 32 bit and hardy 32 bit, it even is able to search for the bluetooth handsfree but I was not successful in pairing. On the other hand, 64 bit fails to show any sign of working other than showing bluetooth icon on the panel on every bootup).

Now, these four as I conveyed, have issues on ubuntu and my idea was whether they can be captured by VB and can work on Windows in the VB or not. On separate Win installations, all of these work fine.

When I attach filters in virtual machine, the machine shows error while booting. If I don't attach filters and try capturing them after Windows boots up, I still get errors... Would really appreciate if anybody helps me out with USB capturing by VB in detail.

My Logitech mouse and Epson printer (both USB connected) have no problem and work fine in Virtual environment.

Thank you very much in advance and anticipation.

Ashwini

---

### Post by Dedoimedo on 2008-12-15
Hello,

I would try to solve one problem at a time.

First, networking. Do you bridge the network interface that you use for internet connection, or another?

You may need forwarding, from host interface to vb interface; they sit on the same subnet, so you may need to allow forwarding on the host to vb interface.

But before that, make sure in the guest that you use the host interface as the default gateway (and the dns).

Do you need help configuring these items?

Dedoimedo

---

### Post by ashwinipn on 2008-12-15
> **Dedoimedo said:**
> Hello,

I would try to solve one problem at a time.

First, networking. Do you bridge the network interface that you use for internet connection, or another?

You may need forwarding, from host interface to vb interface; they sit on the same subnet, so you may need to allow forwarding on the host to vb interface.

But before that, make sure in the guest that you use the host interface as the default gateway (and the dns).

Do you need help configuring these items?

Dedoimedo

Hi Dedoimedo,
thanks for your reply..... yes... I have bridged the interface et0 with br0 and made VB interface as vbox0 and vbox1 (for XP and Vista separately according to VB approach). When vbox0 and vbox1 did not work, I tried tap0 and tap1 (native ubuntu uml-net approach) without success. I am close but feel that I have not got full understanding of this. I would really appreciate if you can help me with configuring. Through settings, I use host interface in guest but may be not establishing right values.. How to do forwarding? Please tell me step by step.... Thank you once again...

Ashwini

---

### Post by Dedoimedo on 2008-12-16
Hello,

OK, let's start with vbox ... Create a bridged interface as instructed in ubuntu community:

[https://wiki.ubuntu.com/VirtualBox](https://wiki.ubuntu.com/VirtualBox)

Print out the ifconfig here for the host.

Configure the guest to use host interface > vbox0 and boot into the guest. Configure the ip in the guest to be on the same segment like the host. Example: host 192.168.1.100, guest 192.168.1.102.

Print out ifconfig for the guest. Also print out /etc/resolv.conf.

Dedoimedo

---

### Post by ashwinipn on 2008-12-18
Hi Dedoimedo,
thanks for your help. I tried the way you instructed. In fact, bridging and virtual interface (vbox1) I had already done before the same way it has been mentioned in the article you suggested.... This times I did it again... and kept it as DHCP (as in the host). The result was no different..... with NAT, it works... with Host Interface, it doesn't. After that, one more change I applied. In VB manual, I had read somewhere that Microsoft removed support for the PCnetIII Fast Ethernet Adapter (default in VB) by AMD in Windows Vista.... and also that Intel PRO/1000 T Server Ethernet Adapter would work in Windows XP without any need to install driver separately. So, I changed it to the Intel one.... Upon bootup, Windows recognized the new hardware and installed the driver on its own (as per the suggestion given in the manual). After that, I tried connecting to the internet in two ways... First, automatically connect to the internet, and the second, supplying IP config. The first one did not work as the adapter said, "non or limited connectivity". After supplying IP [I tried 109 as well as 110 because while restarting network, I read in the terminal window that these virtual interfaces (I made two, vbox0 and vbox1) are on 110 at port 67 (I don't exactly know what these were, no fundamental knowledge about networking terminologies)], the adapter showed that it is connected and firewalled. That meeans to say that it showed all the signs of a successful connection. But my excitement died when I tried loading webpages, which, for some reason, was not successful. It means... not yet connected.... I don't know why exactly it happened?

I used OpenDNS and 192.168.1.1 as default gateway, and 255.255.255.0 as subnet mask. Am I doing anything wrong here?

Now that after bridging, I don't see eth0 in the network configuration window (in fact the icon on the panel indicates no connection on the host despite of able to load webpages and streaming and everything), how do I know about the IP information of my host? Is it supposed to be this way? I mean eth0 is not visible on the host after craeting a bridge. I don't see anything at all in the network configuration window on the host (Ubuntu Intriped Ibex 64 bit).

I am not sure if I made any sense in this message. At times, I percieve that sentence formations are not proper for some unknown reasons... Anyways, please let me know if more clarification is needed.

Ashwini

---

### Post by ashwinipn on 2008-12-30
Hi,
This is an update of the problem I had been facing while configuring Host Interface in the VBox for the Win XP guest in the Intrepid 64 bit host. By trying different permutation and combination, till now I was not able to enable internet on my guest. I could not know what was going wrong... I followed every step precisely as told/stated in various guides/pages. Now the problem seems to have been diagnosed and it was found to be a silly reason. My ufw (Uncomplicated firewall) is the culprit. Since I have enabled it with its default values, it denies all incoming traffic. On host as well as with NAT enabled on the guest it works fine.... but when a host interface is enabled, it treats that adapter differently and somehow does not allow it to function at all... With ufw disabled..... Host Interface works fine...

Now, this gives rise to another query. If I want to keep ufw enabled, how to configure it or specify rules to allow to get the traffic to the host interface on the guest OS? I need some help with this and would be grateful if get some valuable advice.

Ashwini

---

