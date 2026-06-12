---
title: "ubunto 9.10 under vmware/xp cannot connect internet"
date: 2009-12-07
forum: Virtualisation
---

### Post by tedchyn on 2009-12-07
I installed vmware 1.0.4 under window xp(32bits) and ubunto 9.10. when I click firefox for internet [www.yahoo.com]("http://www.yahoo.com") and got server not found error msg. I am new to ubunto and wonderring Is there anything I need to do to make ubunto connect to internet. I am not using wireless connection.
 
thanks ted

---

### Post by Nxion on 2009-12-07
So to make sure I understand, your Windows XP works fine on the network but the Ubuntu does not? Did you make sure that you added a network card when you built the virtual machine? In VMware you have to make sure you add a network interface otherwise it wont connect to your network or the internet.

---

### Post by ankur1990 on 2009-12-07
if u r using a ppoe connctions then u can made ppoe compatible with the ubuntu setting by running  into the pppoeconf root.......
it will detect it settings automatically and then wiill run smoothly by the commands mentions there :p

---

### Post by LunaticHiatus on 2009-12-07
I had this same problem. Install the guest editions and it should work.

---

### Post by LunaticHiatus on 2009-12-07
oh, my bad, I thought you where using virtualbox. Ignore what I said earlier.

---

### Post by Nxion on 2009-12-07
Actually out of the box, Ubuntu works with out the vmware tools OR guest additions.

---

### Post by ankur1990 on 2009-12-08
method to enter the pppoeconf root:
1.connet the ethernet/ dsl/datacardwire with your system.
2.open the terminal
3.type sudo pppoeconf
4. it will show all the conncetions it will found
5. then just follow the instructiions
6.during this process when your configuration has been corrected then it will show you the keywods "pon-dsl-provider" to turn on the net and "poff" to turn it off. remember the keywords bcoz they are imp
7.Always use these keywords in terminal then for connectiong and disconnecting rather simply try to connect from the toolbar
8. this whole process works very smoothly and enjoy ur surfing ;)


if ur problem got solved by doing this change the status of this thread to "solved" so that other can use it under the solved category.
:KS

---

### Post by Nxion on 2009-12-08
Not sure why the pppoe instructions are relevant in this thread. The original poster didn't ask about pppoe unless I missed something...

---

### Post by tedchyn on 2009-12-08
> **LunaticHiatus said:**
> I had this same problem. Install the guest editions and it should work.
 
 
I use 9.10 iso image from ubunto. what is ubunto guest edition and where do I get it ?

---

### Post by tedchyn on 2009-12-08
> **Nxion said:**
> So to make sure I understand, your Windows XP works fine on the network but the Ubuntu does not? Did you make sure that you added a network card when you built the virtual machine? In VMware you have to make sure you add a network interface otherwise it wont connect to your network or the internet.
 
 
I installed ubunto under vmware and vmware is using bridged network and wondering whether I still need to add network card ?

---

### Post by ankur1990 on 2009-12-08
no i dont think so.
bridge network is set by the company servers and they change their settings according to that only
so i dont think there is a need......
i also wanna know the confirmed answer of thisquestion.....
plz reply soon :)

---

### Post by tedchyn on 2009-12-10
> **ankur1990 said:**
> method to enter the pppoeconf root:
1.connet the ethernet/ dsl/datacardwire with your system.
2.open the terminal
3.type sudo pppoeconf
4. it will show all the conncetions it will found
5. then just follow the instructiions
6.during this process when your configuration has been corrected then it will show you the keywods "pon-dsl-provider" to turn on the net and "poff" to turn it off. remember the keywords bcoz they are imp
7.Always use these keywords in terminal then for connectiong and disconnecting rather simply try to connect from the toolbar
8. this whole process works very smoothly and enjoy ur surfing ;)
 
 
if ur problem got solved by doing this change the status of this thread to "solved" so that other can use it under the solved category.
:KS
 
I ran sudo pppoeconf => found eth0=> scn interface but the access concentrator of your provider did not respond.

---

### Post by ankur1990 on 2009-12-11
ohk....
at the end of the configuration it shows a msg of the commands which will access and kill your network.........
above i gave the "pon dsl-provider" is just and exmaple......
check out of urs

---

### Post by SRK91 on 2009-12-28
i confured pppoe as u said.then i entered...
"pon dsl-provider" - it says rp-pppoe loaded.
when i enter "plog" to see the status.....this is what i see ...

"plugin rp-pppoe.so loaded.
 RP-PPPoE plugin version 3.8 compiled against pppd 2.4.5
 pppd 2.4.5 strted by user,uid 1000
 PPP session is 1019
 conected to (mac addr) via interfacce eth0
 using interface ppp1
 conect: ppp1<-->eth0 "

bu when i start firefox it says "server not found "
i have selected bridge connection in Vmware settings ...
i use dial-up in my host pc (windows xp)

plsz help me...

---

### Post by Hopping_Ubu on 2009-12-29
> **tedchyn said:**
> I installed ubunto under vmware and vmware is using bridged network and wondering whether I still need to add network card ?

tedchyn,

VMware is using the bridge network configuration, you still need to add a network card to your virtual Ubuntu and choose the appropriate network card that VMware is using. By default VMware creates three network configurations, host, bridged and NAT. The bridged will allow your virtual computer to get it's own IP address. The NAT will create psudo secure connection through your existing computer's network connection. The host will only let you talk to the host (like a management connection). Your choice of poison, bridged or NAT will get you out onto the network.

---

### Post by paldoon on 2010-02-01
This is an easy fix. The problem is not with the guest OS but with the virtualized hardware created by VMware. Ubuntu does not "see" the virtual NIC so Ubunru can't get a DHCP address for the NIC. 

The fix is to edit the .vmx file (settings file) for the virtual machine in question. The .vmx file is created by VMWare in the Virtual Machines folder on your host PC. 

Open the .vmx file with a text editor and insert the line shown below. This setting is for the first virtual network card. i.e ethernet0.   virtualDev= "e1000" is a generic network card for which Ubuntu 9.10 has the drivers.

Here is the line to add to the .vmx file:

 Ethernet0.virtualDev = "e1000"




 Save the .vmx file and boot the virtual machine. Confirm the ip address of the NIC in ubuntu. Open Mozilla and surf! 


  By the way, this fix also works for Windows Vista and 7 virtual machines.

---

