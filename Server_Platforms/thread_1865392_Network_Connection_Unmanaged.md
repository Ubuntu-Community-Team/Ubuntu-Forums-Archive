---
title: "Network Connection Unmanaged"
date: 2011-10-20
forum: Server Platforms
---

### Post by Naresh Raj N on 2011-10-20
I am Facing few problems in getting my UBUNTU SERVER 11.10, get connected to Another SERVER Machine.
  
I Installed UBUNTU SERVER 11.10. I went on with applying GUI, GNOME DESKTOP by [INDENT]sudo apt-get update
[/INDENT][INDENT]sudo apt-get install ubuntu-desktop
[/INDENT]After the completion of above Installation, I am Facing Few Problems:


1. Not able to connect my server to other server from DESKTOP->FILE->"connect to the SERVER".
  
Displayed As:
  
"Failed to Retrieve Share List from Server"  I selected Type->"Windows Share"
  
I need some Help in Finding a Solution for this above problem. And Guide   my server machine to get Connect to the Other server Machines.
  
  
2. In the Desktop, From Panel, It Shows "WIRED NETWORK" Device Not   Managed.  I tried to Edit the Wired Network by providing the IP Address,   Gatway, Dns etc... still it fails.
I am not able to View the "CONNECTION INFORMATION". When I click "CONNECTION INFORMATION"
  
  
Displayed As:
  
Error displaying connection information:
No valid active connections found!
  
Also help me to Manage my Wired Network Connection & make View my   connection Information Details. The Internet service is available in the   system. And there is No problem in accessing the INTERNET.
  
  
Code:
 	cat /etc/network/interfaces 
 
Result:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp



Pls anyone help me in finding a solution for the above problems that i am facing.



Regards,
Naresh.

---

### Post by volkswagner on 2011-10-20
When you select "connect to server" are you trying to connect to the server from a client machine?  Please give a little  more detail about this step.

From your server post the output of:

```
cat /etc/network/interfaces
```

Please explain are you just trying to get your ip, (use ifconfig)?

```
ifconfig
```

---

### Post by Naresh Raj N on 2011-10-20
Thank u for the response... actually i hav installled a SERVER VERSION of ubuntu 11.10 to my system.. and logged on as a SERVER

Later I followed with this command 

1. sudo apt-get update
2. sudo apt-get install ubuntu-desktop

After the successful Installation of GUI. I am trying to connect my Server Machine to Another Server Machine. But its not possible.

 and also i cannot able to ENABLE/DISABLE my Wired Network too


the output for the command is cat /etc/network/interfaces


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

thank You

---

### Post by volkswagner on 2011-10-21
If you want network manager to handle you NIC, you should comment out the info in /etc/network/interfaces.

Should look like this:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
```

Then restart networking and network manger, or just reboot for good measure.

---

### Post by Naresh Raj N on 2011-10-24
Ur Suggestion did not work. Please Help me.

Here is an Clear Detail of what i had done,

I am Facing few problems in getting my UBUNTU SERVER 11.10, get connected to Another SERVER Machine.
  
I Installed UBUNTU SERVER 11.10. I went on with applying GUI, GNOME DESKTOP by [INDENT]sudo apt-get update
[/INDENT][INDENT]sudo apt-get install ubuntu-desktop
[/INDENT]After the completion of above Installation, I am Facing Few Problems:


1. Not able to connect my server to other server from DESKTOP->FILE->"connect to the SERVER".
  
Displayed As:
  
"Failed to Retrieve Share List from Server"  I selected Type->"Windows Share"
  
I need some Help in Finding a Solution for this above problem. And Guide   my server machine to get Connect to the Other server Machines.
  
  
2. In the Desktop, From Panel, It Shows "WIRED NETWORK" Device Not   Managed.  I tried to Edit the Wired Network by providing the IP Address,   Gatway, Dns etc... still it fails.
I am not able to View the "CONNECTION INFORMATION". When I click "CONNECTION INFORMATION"
  
  
Displayed As:
  
Error displaying connection information:
No valid active connections found!
  
Also help me to Manage my Wired Network Connection & make View my   connection Information Details. The Internet service is available in the   system. And there is No problem in accessing the INTERNET.
  
  
Code:
 	cat /etc/network/interfaces 
 
Result:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp



Pls anyone help me in finding a solution for the above problems that i am facing.



Regards,
Naresh.

---

### Post by volkswagner on 2011-10-24
Please lets address one issue at a time.

What type of server are you trying to connect to?  Windows, linux, or other?  Please give details.

Is the machine you are tying to connect to able to share files with other computers on the LAN?

Can you connect to the server via it's ip address.

From you Ubuntu machine open file browser and hit <crl> + l, this will open location window.  Here you can type smb//192.168.1.1xx/foldername.

Also from your UbuntuServer open file browser and select Network, what to you see here?

---

