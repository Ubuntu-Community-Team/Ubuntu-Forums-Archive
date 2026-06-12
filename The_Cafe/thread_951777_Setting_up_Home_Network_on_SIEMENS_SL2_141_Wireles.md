---
title: "Setting up Home Network on SIEMENS SL2_141 Wireless Router."
date: 2008-10-18
forum: The Cafe
---

### Post by kagashe on 2008-10-18
Today I have set up Home Network consisting of two Laptops and one Desktop on SIEMENS SL2_141 Wireless Router at my daughter's residence in Bhubaneswar.

The Router arrived with default settings in Bridge Mode. In Bridge Mode ISP userid and password is supposed to be given from the computer, therefore, only one machine could be connected to internet. I tested the internet connection through one Laptop and then used it to configure the router to alter the WAN settings from Bridge Mode to PPPoE. After changing the mode and rebooting the router it logged into ISP account and surfing could be done from the two Laptops and the Desktop connected through NIC to the router.

The next step was to prevent the neighbor from surfing the net on his Laptop using our router. The router was showing the MAC addresses of the two connected Laptops. I entered the MAC numbers in the MAC Filter and enabled the filter allowing access only to these machines.

I also changed the Admin password of the router, otherwise, a smart neighbor could easily disable the Mac filter of the router and surf from his Laptop.

Following security features are available on the router:

   >  Wireless -- Security

    This page allows you to configure security features of the wireless LAN interface. You can sets the network authentication method, selecting data encryption, specify whether a network key is required to authenticate to this wireless network and specify the encryption strength.
    Click "Apply" to configure the wireless security options.

    Select SSID: 	
      	 
    Network Authentication: 	

    WPA2 Preauthentication: 	
    Network Re-auth Interval: 	
    WPA Pre-Shared Key: 		   	Click here to display
    WPA Group Rekey Interval: 	
    RADIUS Server IP Address: 	
    RADIUS Port: 	
    RADIUS Key: 	
    WPA Encryption: 	
    WEP Encryption: 	
    Encryption Strength: 	
    Current Network Key: 	
    Network Key 1: 	
    Network Key 2: 	
    Network Key 3: 	
    Network Key 4: 	
     	Enter 13 ASCII characters or 26 hexadecimal digits for 128-bit encryption keys
     	Enter 5 ASCII characters or 10 hexadecimal digits for 64-bit encryption keys

I would like to know what else needs to be done.

kagashe

---

### Post by gletob on 2008-10-18
I think mac filtering is a good thing but you should set up WPA security also

---

