---
title: "Connect to OpenVPN service from Terminal &amp; GUI"
date: 2013-11-05
forum: Sudan Team
---

### Post by zero-n on 2013-11-05
If you want to browse anonymously or access content restricted by geographic location you will need to use a proxy or a VPN service fortunately there are many free VPN Services in this post i will use a free OpenVPN service: [**vpnbook **]("http://vpnbook.com")



**1- Download any of 4 available OpenVPN connection profile from [vpnbook.com]("http://www.vpnbook.com/#openvpn") from openvpn tab and ****don't forget to check username and password**

[IMG]http://i42.tinypic.com/2enuo05.png[/IMG]


**2- Extract .Zip file**:
```
unzip ~/Downloads/YOUR_SELECTED_BUNDLE.zip
```


[B]3- Connecting:
------------------

3A: Connect using terminal:
---------------------------------
[/B]
[LIST]
[*]Open terminal and run the following command to install openvpn package:```
sudo apt-get install openvpn
``` 
[*]connect by using the floowing command and type usernmae and password when prompt```
sudo openvpn --config YOUR_SELECTED_CONNETION_TYPE.ovpn
``` 
[*]if everythign goes well you will see similiar to this:```
Tue Nov  5 20:58:54 2013 [vpnbook.com] Peer Connection Initiated with [AF_INET]198.7.62.204:25000
Tue Nov  5 20:58:56 2013 SENT CONTROL [vpnbook.com]: 'PUSH_REQUEST' (status=1)
Tue Nov  5 20:58:56 2013 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS  8.8.8.8,dhcp-option DNS  8.8.4.4,route 10.10.0.1,topology net30,ping 5,ping-restart 30,ifconfig 10.10.1.146 10.10.1.145'
Tue Nov  5 20:58:56 2013 OPTIONS IMPORT: timers and/or timeouts modified
Tue Nov  5 20:58:56 2013 OPTIONS IMPORT: --ifconfig/up options modified
Tue Nov  5 20:58:56 2013 OPTIONS IMPORT: route options modified
Tue Nov  5 20:58:56 2013 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Tue Nov  5 20:58:56 2013 ROUTE default_gateway=X.X.X.X
Tue Nov  5 20:58:56 2013 TUN/TAP device tun2 opened
Tue Nov  5 20:58:56 2013 TUN/TAP TX queue length set to 100
Tue Nov  5 20:58:56 2013 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Tue Nov  5 20:58:56 2013 /sbin/ifconfig tun2 10.10.1.146 pointopoint 10.10.1.145 mtu 1500
Tue Nov  5 20:58:58 2013 /sbin/route add -net 198.7.62.204 netmask 255.255.255.255 gw 192.168.2.1
Tue Nov  5 20:58:58 2013 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.10.1.145
Tue Nov  5 20:58:58 2013 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.10.1.145
Tue Nov  5 20:58:58 2013 /sbin/route add -net 10.10.0.1 netmask 255.255.255.255 gw 10.10.1.145
[COLOR=#008000]**Tue Nov  5 20:58:58 2013 Initialization Sequence Completed**[/COLOR]


``` 
[*]To [COLOR=#ff0000]**disconnect**[/COLOR] press: **Ctrl+C ** 
[/LIST]



[B]3B: Connect using GUI:
----------------------------
[/B]
[LIST]
[*]install Network manager OpenVPN plugin: ```
sudo apt-get install network-manager-openvpn network-manager-openvpn-gnome&#8206;
``` 
[*]Open any of 4 files availabe after extracting the .ZIP file with a text editor. 
[*]now copy all the text between **<ca>** and **</ca>** and save text in a file name it [COLOR=#ff0000]**ca.crt**[/COLOR] 
[*]copy all the text between **<cert>** and **</cert>** and save text in a file name it [COLOR=#ff0000]**user.crt**[/COLOR] 
[*]copy all the text between **<key>** and **</key>** and save text in a file name it [COLOR=#ff0000]**key.key**[/COLOR] 
[*]Select **Network connection** form upper right corner **>> VPN Connection >> Configure VPN** 
[/LIST]
[IMG]http://i44.tinypic.com/au70hw.png[/IMG]


[LIST]
[*]Select Import and open the same file that we get our ca.crt user.crt and key.key from 
[*]Change authentication to [COLOR=#ff0000]**Password With Certificates (TLS)**[/COLOR] and enter the  [COLOR=#ff0000]username[/COLOR]    and   [COLOR=#ff0000]password[/COLOR] 
[*]For **User Certificate** select user.crt file 
[*]For **CA Certificate** select ca.crt 
[*]For **Private Key** select key.key and click Save. 
[/LIST]
[IMG]http://i43.tinypic.com/16ggbo4.png[/IMG]
[LIST]
[*]Now go to **Network connection** form upper right corner **>> VPN Connection >>** YOUR_VPN_CONNECTION_NAME. 
[*]IF everything goes well a message will appear stating that ([COLOR=#008000]**VPN connection has been successfully established**[/COLOR]). 
[*]To [COLOR=#ff0000]**disconnect**[/COLOR] go to **Network connection** form upper right corner **>> VPN Connection >>** YOUR_VPN_CONNECTION_NAME. 
[/LIST]

---

### Post by suspect x on 2013-11-12
good article Zero

---

