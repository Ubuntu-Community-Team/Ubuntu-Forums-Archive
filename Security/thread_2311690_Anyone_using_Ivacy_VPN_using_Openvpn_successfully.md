---
title: "Anyone using Ivacy VPN using Openvpn successfully?"
date: 2016-01-29
forum: Security
---

### Post by ultragamer2 on 2016-01-29
I bought an ivacy vpn subscription on special and I have loaded the openvpn configuration file via the standard import vpn configuration but I can't connect.

Has anyone got this vpn going with openvpn in ubuntu, are there are extra things you have to change in the configuration?

I have openvpn setup properly because I've used it successfully before with another vpn.

---

### Post by patrikmellq on 2016-01-29
I use "SecurityKISS" and they have a very good howto with Pictures and others say PIA is best provider of VPN.
It works great for me and i just did what the howto told me to do - with SecurityKISS you can open account and test for free - you get 300 MB each day.
I Think "PIA" also have a test period.

Here is the link where there is a discussion about which VPN is best and many members say PIA is good - if i remember it correct you can connect 5 devices for a price around 70 Euro - not sure you have to read for your self.
SecurityKISS allow you to connect so many devices as they have servers, i have it on my mobile phone and IMAC computer running Ubuntu and one Laptop with Ubuntu.

Read this topic [SIZE=3]http://ubuntuforums.org/showthread.php?t=2310121
[/SIZE]

---

### Post by ultragamer2 on 2016-01-30
Thanks for the link I've bookmarked it for future reference. But I already bought an ivacy subscription on special, if anyone reads this thread and has worked out how to use Ivacy with Openvpn in ubuntu please say how. Thanks

I followed these instruction in Lubuntu but can't get it to work.

[COLOR=#000000][FONT=Helvetica]For OpenVPN on Linux. Please follow the given steps:[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]1. Click on Dash, Search for Terminal and open it.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]2. Insert command:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]sudo apt-get install network-manager-openvpn[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]and hit enter[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]3. Type &#8220;Y&#8221; and hit enter to continue[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]4. Once installation completes, close Terminal and download the required OpenVPN[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]5. Extract the downloaded file.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]6. Do the following:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Click on &#8220;Network Connection Icon&#8230;&#8220;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Go to VPN Connections and select &#8220;Configure VPN&#8230;&#8220;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]7. Click on &#8220;Add&#8220;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]8. Click on drop down menu.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]9. Select &#8220;OpenVPN&#8221; and click &#8220;Create&#8220;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]10. Insert the following info:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Insert Connection name: PureVPN OpenVPN[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Insert desired Gateway: Open .ovpn file from OpenVPN folder to get the server address[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Select Type: Password from drop down menu[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Insert Username provided by PureVPN[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Insert Password provided by PureVPN[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Click on folder icon from CA Certificate[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]11. Go to OpenVPN downloadeds folder, select ca.crt and click &#8220;Open&#8220;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]12. Click on &#8220;Advanced.&#8220;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]13. From General tab select following options:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Check Use custom gateway port: For UDP insert 53 and For TCP insert 80[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Check Use LZO data compression[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]14. From Security tab select following options:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    From Cipher: Select AES-256-CBC or desired encryption[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    From HMAC Authentication: Select SHA-1[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]15. Form TLS Authentication tab:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Select Use additional TLS authentication[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Click on folder icon next to Key File[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]16. Go to OpenVPN downloaded folder, select Wdc.key and click &#8220;Open&#8220;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]17. Do the following:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Select &#8220;1&#8221; from Key Direction[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Click on &#8220;OK&#8220;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]18. Click on &#8220;Save&#8230;&#8221; and close the &#8220;Network Connections&#8221; window[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]19. Now:[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Click on &#8220;Network Connection Icon&#8230;&#8220;[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]&#8226;    Go to VPN Connections and select newly created &#8220;PureVPN OpenVPN&#8221; connection.


[COLOR=#000000][FONT=Helvetica]And for the OpenVPN files. Please follow this link: [/FONT][/COLOR][URL="https://support.ivacy.com/kb/openvpn-files-for-windows-routers-ios-linux-and-mac/"]https://support.ivacy.com/kb/openvpn-files-for-windows-routers-ios-linux-and-mac/
[/URL]

Got it working in the end.
[/FONT][/COLOR]

---

### Post by kindas33 on 2016-07-12
I have been using open and it's working well, I even created a custom opvn files for those downloaded online are not stable, In other case why not consider using HTTP injector it's a better alternative to open vpn you have the room to create your custom ssh read more for better understanding here [http://www.naijaspecs.com/http-injector-configure-file/](http://www.naijaspecs.com/http-injector-configure-file/)

---

