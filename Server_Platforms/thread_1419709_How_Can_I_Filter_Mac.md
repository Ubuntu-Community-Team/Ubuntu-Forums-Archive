---
title: "How Can I Filter Mac ?"
date: 2010-03-02
forum: Server Platforms
---

### Post by elmogrem007 on 2010-03-02
[SIZE=4][COLOR=blue]Hi , I Just Installed UBUNTU SERVER 9.10 and I'm installing desktop "[/COLOR][/SIZE][FONT=DejaVuSans][FONT=DejaVuSans]
[FONT=DejaVuSans][SIZE=4][COLOR=blue]sudo apt[/COLOR][/SIZE][/FONT][/FONT][/FONT][SIZE=4][COLOR=blue][FONT=KFGQPCUthmanTahaNaskh][FONT=KFGQPCUthmanTahaNaskh][FONT=KFGQPCUthmanTahaNaskh]-[/FONT][/FONT][/FONT][FONT=DejaVuSans][FONT=DejaVuSans][FONT=DejaVuSans]get install ubuntu[/FONT][/FONT][/FONT][FONT=KFGQPCUthmanTahaNaskh][FONT=KFGQPCUthmanTahaNaskh][FONT=KFGQPCUthmanTahaNaskh]-[/FONT][/FONT][/FONT][/COLOR][/SIZE][FONT=DejaVuSans][FONT=DejaVuSans][FONT=DejaVuSans][SIZE=4][COLOR=blue]desktop[/COLOR][/SIZE][/FONT]
[/FONT][/FONT][SIZE=4][COLOR=blue]" [/COLOR][/SIZE]

[SIZE=4][COLOR=blue]so , my question is how to filter macs of my network "LAN" users[/COLOR][/SIZE]

[SIZE=4][COLOR=blue]I don't need to block macs no , i need to allow macs , I mean i need to allow some macs which i know and trust them "because if i blocked aperson mac he can change it and access to internet"[/COLOR][/SIZE]

[SIZE=4][COLOR=blue]and also , plz if there is any Explanation how to divide bandwidth on users plz i need it and any other useful tips , sorry i just Beginner with ubuntu server and i hope you help me , thanks[/COLOR][/SIZE]

---

### Post by ICEB3AR on 2010-03-02
First of all... a MAC-Address changed is not common. The user had to know a bit about network/hardware to change this. What you Probably mean is IP-Address.

Second: What exactly should the User do or not? So i mean it depends on the services Where you can Block MAC-Addresses. e.g. Do you want run a DHCP-Server? or do you want to share Files in your Network?

---

### Post by elmogrem007 on 2010-03-02
> **ICEB3AR said:**
> First of all... a MAC-Address cannot be changed. This Address is fix and only if you change your Hardware-Interface where you connect to the network there is a "new" MAC-Address. What you Probably mean is IP-Address.
 
Second: What exactly should the User do or not? So i mean it depends on the services Where you can Block MAC-Addresses. e.g. Do you want run a DHCP-Server? or do you want to share Files in your Network?
 
 
First of all : thank you for this fast reply ;)
 
But : How a MAC-Address cannot be changed , then what is this : 
 
[[IMG]http://www.m5zn.com/uploads/2010/3/2/photo/1mtqsqis9ekcoxlxd.jpg[/IMG]](http://www.tobikat.com)
 
here you can put any value and change the mac and the router will read this new value of mac and this pic show you manuly and there are programme do that also .
 
[http://www.m5zn.com/photo_files/2010/3/2/photo/1mtqsqis9ekcoxlxd.jpg](http://www.m5zn.com/photo_files/2010/3/2/photo/1mtqsqis9ekcoxlxd.jpg)
 
and i need to allow Users-MACs to do all servies and the Users-MAC who i will not input (allow ) cann't access to my internet and cannot do any thing or any servies ( downloading , browsing , yahoo , etc )
 
I Hope you understand me ..
 
So Sure i need DHCP-server or any else If  this type of-Server [SIZE=5]Contains these possibilities[/SIZE]

---

### Post by adam814 on 2010-03-02
That's absolutely right.  That's how you would change a MAC address in Windows (although I don't know if every card supports it).  In Linux you can change it with ifconfig.

If I understand correctly what you're hoping to do is whitelist certain MAC addresses that you'll grant network access to while blocking others.  That *might* work as long as it was a wired network and there were no hubs (or switches a user could flood into fail-open), but in a wireless network it would be pointless.  They could just run something like wireshark and see what MAC addresses were allowed and set theirs to one of them.

As for dividing bandwidth it's probably easier just to block/limit problem traffic as it happens.  I don't know of any utility that will assign x% of bandwidth dedicated to user y or anything like that.

---

### Post by cdenley on 2010-03-02
Yes, although each NIC is preprogrammed with a unique MAC, it is not very difficult to use software to change the MAC your system actually uses.

In linux, you filter network packets with iptables. This would restrict access to your Ubuntu system, not your network.
```

man iptables

```
> 
mac
       [!] --mac-source address
              Match source MAC address.  It must be of the form XX:XX:XX:XX:XX:XX.  Note that this only makes sense for packets coming from  an  Ethernet
              device and entering the PREROUTING, FORWARD or INPUT chains.


By "divide bandwidth", I assume you mean traffic shaping. I'm not sure how this can be done if you configure a Linux system as an internet gateway, but I think PFsense would be a good solution for traffic shaping.

---

### Post by elmogrem007 on 2010-03-02
> **adam814 said:**
> 
 
If I understand correctly what you're hoping to do is whitelist certain MAC addresses that you'll grant network access to while blocking others. That *might* work as long as it was a wired network and there were no hubs (or switches a user could flood into fail-open), but in a wireless network it would be pointless. They could just run something like wireshark and see what MAC addresses were allowed and set theirs to one of them.
 

 
My LAN Network consist of router and some switches but no any one of them is wireless (i will take RJ-45 cable from my router to my PC-server and from my PC-Server to my swith and this switch will connect the users )
 
then , can i do whitelist and how ?
 
if cannot is any other way (and take care to point that some users can change mac so i cannot block them if they still apple to change )
 
and about bandwidth i'll see i thought program like 
WEBMIN can do it , right ?
 
I'm sorry but i really need help , thx[FONT=DejaVuSans-Bold][SIZE=4][COLOR=#198b8b][FONT=DejaVuSans-Bold][SIZE=4][COLOR=#198b8b]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by pricetech on 2010-03-02
I'm not sure if you have a compelling reason to go through your Linux box, but you should be able to do much of what you want in your router.  It should have settings that allow you to limit the handing out of IPs to certain MAC addresses and should even let you limit what MACs can access the router, and therefore the network to an extent, that way.

As far a traffic shaping and QOS, you're probably going to have to purchase a high end router for that, though there may well be a way to do it with your Linux box.

And please; plain text works just fine.  Large colorful fonts don't usually help, and may well annoy the very person who might have the answer you are looking for.

---

