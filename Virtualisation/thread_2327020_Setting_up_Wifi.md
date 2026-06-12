---
title: "Setting up Wifi"
date: 2016-06-07
forum: Virtualisation
---

### Post by michael_oconnor2 on 2016-06-07
Hello folks, I have recetly got VirtualBox for the purpose of trying out Ubuntu Linux.

My computer is an HP, with Windows10 OS.
My virtual box is set up, and I have a "cable connection" although my actual computer is wirelessely connected.

Anyways, I had a wifi adapter for the purpose of using wi-fi while at school and what not.  Unfortunately the wireless is horrible and I require an adapter to get somewhat decent signal.  

I am trying to get the wifi to work through the adapter, and have been testing out some commands in terminal.
$ ifconfig yeields results for JUSt:
"lo"
"eth0"
and their corresponding values.

I watched a tutorial on youtube, advising me to try some sort of questionable program called aircrack and airmon, to find available wifi networks ( I just want to see mine and my school's::: which I am allowed to use)

airmon yiels three columns: chipset   |    interface   |   drivers

Unfortunately, there are no values below these 3 titles, and evidently my wireless is turned off or something of that nature.  
When I select the adapter from the device menu at the top, it tells me that the usb device failed to attach to the virtual machine.  

Some people have suggested a guest session, but I dont understand how that would help.
Also, any sort of change with my adapter settings would be appreciated, as I clearly have something mixed up.
Adapter 1: NAT
Adapter 2: Bridged Adapter

---

### Post by howefield on 2016-06-07
Thread moved to the "*Virtualisation*" forum.

---

### Post by michael_oconnor2 on 2016-06-07
*{d667ce16-d609-4266-8f84-6805539d390f}* is busy with a previous request. Please try again later.


[TABLE]
[TR]
[TD]Result Code: 
[/TD]
[TD]E_INVALIDARG (0x80070057)
[/TD]
[/TR]
[TR]
[TD]Component: 
[/TD]
[TD]HostUSBDeviceWrap
[/TD]
[/TR]
[TR]
[TD]Interface: 
[/TD]
[TD]IHostUSBDevice {c19073dd-cc7b-431b-98b2-951fda8eab89}
[/TD]
[/TR]
[TR]
[TD]Callee: 
[/TD]
[TD]IConsole {872da645-4a9b-1727-bee2-5585105b9eed}

This error came up when I tried to activate the device
[/TD]
[/TR]
[/TABLE]

---

### Post by MAFoElffen on 2016-06-07
Install the VBox Extension Pack. Make sure you are in the vbos usergroup. (In user prorprties) You can then pass through your usb ports to see your usb network device from the guest.

But... if the host see's the usb NIC, then you should be able to use that connection from Vbox also... My notebook has a Belkin USB 3.0 Eth NIC/USB Hub. I bridge to my wifi port.

---

### Post by michael_oconnor2 on 2016-06-12
Unfortunately, this has not worked yet. I have the extension pack, but my usb adapter doesnt want to pull up any data.  I have also added myseld to the vboxuser group, didnt help.

no chipset, interface or driver is pulling up.  It simply shows nothing under those 3 categories. 
When I open up the VB, I can see the device is checked off.  
I read another forum and it told me to add a filter, which I did, but it didnt seem to do anything. 

Everything looks fine, but it simply doesnt want to work for whatever reason.

---

### Post by kurt18947 on 2016-06-12
Can you disable the onboard wifi adapter, connect the USB adapter in Win 10 and use the 'ethernet' connection for Virtualbox guests?

---

### Post by michael_oconnor2 on 2016-06-12
Well my principle purpose for having this is so I can use an adapter to connect to wifi networks at my school and what not.  For whatever reason, I cannot utilize the adapter to find networks whatsoever.  

For example, if I disconnect my main computer (host) from all networks.  There is no possible way to connect my VB because the adapter does not work at all.  
It shows that it is active in the 'device" settings, but it cannot find any networks, nor is wlan0 even showing up.
I have no chipset, interface, or drivers for this device apparently.

For some reason or another, it wants to run eth connection.  Even on the bottom right, when I hover over the adapter settings, it sais " adapter 1" NAT   - cable disconnected.
I cannot figure out why it insists on searching for eth cable connections rather than automatically pursuing wireless networks.

---

### Post by kurt18947 on 2016-06-13
I'm not sure but I wonder if Virtualbox is even capable of using WiFi directly. I wonder if it's intended to 'plug into' the host system's networking. I've been researching security of virtual hosts and guests. One source likened the way a guest OS sees the host OS in networking terms as like an ethernet adapter (guest O.S.) plugging into a router (host O.S.). The guest should not be able to run code on or otherwise interact with the host O.S.

There might be another feature to explore on Virtualbox. If you highlight a guest O.S. then click on 'settings' -> network, you'll see 4 virtual network adapter. Adapter 1 defaults to NAT. Adapter 2-4 can be:


[LIST=1]
[*]NAT
[*]NAT network
[*]Bridged adapter
[*]Internal Network
[*]Host-only adapter
[*]Generic driver
[/LIST]

You could research or experiment with other choices besides NAT to see if you can get a WiFi connection to the guest without involving the host. I had to select Bridged Adapter to print to a networked printer one time. The printer would be seen when using NAT but wouldn't print. I don't know enough about networking and virtualization to be able to advise further.

---

### Post by MAFoElffen on 2016-06-15
From experience using and setting up hypervisors on students laptops (for their labs) ... It's basically the same in Linux and Windows-- When you select "Bridged Adapter", then you need to point the wiring to which adapter. In the case of those laptops, I set them to their wireless connection's device. As for how many connections you can have, once you set NAT or Bridge to a physical adapter (_DEVICE_ID_#), then it can only bind one connection type to that specific physical adapter. For instance Wan0 to Bridged, Eth0 to NAT, etc.

Does that make sense now?

---

