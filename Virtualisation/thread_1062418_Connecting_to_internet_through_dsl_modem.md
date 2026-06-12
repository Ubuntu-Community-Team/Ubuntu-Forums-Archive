---
title: "Connecting to internet through dsl modem"
date: 2009-02-06
forum: Virtualisation
---

### Post by nshailesh on 2009-02-06
I have installed ubuntu on windows host using virtual box.
But I am not able to connect to the internet .
I have a dsl modem and I want ubuntu to the internet directly.
I went to the network manager and supplied the proper addresses .
But when I enter hostname (name of my pc) and the domain name (isp name ) in respective fields in the general tab and I can't do sudo.
It says unable to resolve the host.

I tried entering hostname.domainname leaving the domain name field empty but that also did not solve my problem..

So what should I do ?????????

---

### Post by Shazaam on 2009-02-06
Normally a virtual machine uses the host (Windows in your case) for networking/internet connections. Connect to the internet in Windows. Configure the virtual machine to use NAT networking (VM>Settings>Network>Adapter1>Attatched to>NAT) then start the vm. Open Network Manager in the vm and configure the "wired" connection for dhcp.
Make sure all programs that need to use the internet in the virtual machine (Firefox, Pidgin, etc) are configured to "directly connect", use system proxy settings or connect through the local network in their respective configs/options.

---

### Post by superprash2003 on 2009-02-07
what sort of connection is it ??DSL??go to the terminal and type ifconfig and post output.. in windows do you require a dialer to connect to the internet or does internet work as soon as your modem is switched on?>

---

### Post by nshailesh on 2009-02-08
The network settings for vm are vm->network ->Adapter1->intel pto 100MT Desktop->NAT.
I have selected dhcp in the network manager.
But when I do sudo pppoeconf , it gives following message

" Sorry ,I scanned the interface but the access concentrator of your device did not respond .Please check your network and modem cables.Another reason may be another running pppoe process which controls the modem ."

I am using my dsl modem in windows for internet access

---

### Post by nshailesh on 2009-02-08
I have now this strange problem .

I am not able to open the firefox in ubuntu.
when I click on the firefox icon , initially it just says starting firefox and after some time nothing happens the dialog also closes.


I typed firefox in terminal it says 
No protocol specified ,
Error : cannot open display : : 0.0

---

### Post by superprash2003 on 2009-02-08
ifconfig output?

---

