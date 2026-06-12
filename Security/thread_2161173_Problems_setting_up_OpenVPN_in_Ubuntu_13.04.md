---
title: "Problems setting up OpenVPN in Ubuntu 13.04"
date: 2013-07-09
forum: Security
---

### Post by Traxster on 2013-07-09
here are the directions I followed per vpn service provider directions.

OpenVPN Setup for Linux
Ubuntu Directions
1. Open Terminal
2. Type: sudo apt-get install network-manager-openvpn
3. Press Y to continue.
4. Type: sudo restart network-manager
5. Download BTGuard certificate (CA) by typing: sudo wget -O /etc/openvpn/btguard.ca.crt [http://btguard.com/btguard.ca.crt](http://btguard.com/btguard.ca.crt)
6. Click on the Network Manager icon, expand VPN Connections, and choose Configure VPN
7. A Network Connections window will appear with the VPN tab open. Click Add. 8. A Choose A VPN Connection Type window will open. Select OpenVPN in the drop-down menu and click Create..
9. In the Editing VPN connection window, enter the following:
Connection name: BTGuard VPN
Gateway: vpn.btguard.com
Optional: To manually select your server location, please use ca.vpn.btguard.com for Canada or eu.vpn.btguard.com for Europe or sg.vpn.btguard.com for Singapore.
Type: select Password
User name: your username
Password: your_password
CA Certificate: browse and select this file: /etc/openvpn/btguard.ca.crt
11. Click Save.


before I executed these instructions, I installed the virtual private network daemon openvpn available from the app store ( i realize that this is a command line utility)  the other program installed per instructions is suppose to be the gui. 

 However, when I goto network manger-->VPN Connections --> configure VPN, then ADD, a dialog box comes up, (choose a connection type) The dialog box displays a message "If you are creating a VPN, and the VPN connection you wish to create does not appear in the list, you may not have the correct VPN plugin installed. 

When I click create, under VPN, 'OpenVPN' is not there. The instructions I followed seemed to have gone well. did not see any errors.

Any Help would be greatly appreciated as I need to get this going as soon as possible.


traxster

---

### Post by Traxster on 2013-07-09
Ok guys, for some reason, i fudged the first try. I uninstalled everything then re installed according to instructions, and the openvpn option appeared in the network manager.

---

### Post by dpjg on 2013-09-25
I had the same problem as described above. After purging network-manager-openvpn and reinstalling it together with network-manager-openvpn-gnome everthing works as expected.

---

### Post by redditcoruum on 2013-11-06
I am a novice when it comes to Linux, but can follow directions pretty well. I am using Private Internet Access as my VPN provider, I follow the below instructions... (yes I understand it is for 12.04 and I am using 13.04)
[h=3]Ubuntu Linux 12.04: OpenVPN via Network Manager Setup[/h] 
[LIST=1]
[*]Open a **Terminal**, and run: sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome.  This will prompt for both your password, and a Y/n answer, please provide it with your password, and Y
[*]Once installed, open **System Settings**, then **Network**
[*]Press the **+** symbol to add a new connection, and select the **VPN Interface**, then press **Create**
[*]Choose **OpenVPN** as your VPN Connection Type, and press **Create**
[*]The following will walk you though all configuration steps needed for the PIA VPN.
[LIST=1]
[*]**Gateway**:  Select one of the **Hostnames** provided on the [Network page]("https://payments.privateinternetaccess.com/pages/network")
[*]Authentication
[LIST=1]
[*]Type: Password
[*]Username: The username provided with the PIA account
[*]Password: The password provided with the PIA account
[*]CA Certificate: Downloaded this [zip file ]("https://payments.privateinternetaccess.com/openvpn/openvpn.zip") and extract the **ca.crt** file to somewhere it won't be deleted. We suggest your Home folder.  If you extract this to your home folder, when searching for it, please click on your username on the left side, which will take you right to the home folder, then select the ca.crt file from the options on the right.
[/LIST]
      
[*]Advanced: Under the general tab, check the **Use LZO data compression**
[*]IPv4 Settings:
[LIST=1]
[*]Method: **Automatic (VPN) Addresses Only**
[/LIST]
     
[/LIST]
 
[*]Press **Save**.  If you chose to have your password saved it may ask for you to verify your password to open your keyring.
[/LIST]

My issue is that I can do all of the above, but there is no "**Save**" button available to me.

Do I need to start over, possibly purging what I installed (and if so could someone assist me in the proper command line to purge what I've done)

---

