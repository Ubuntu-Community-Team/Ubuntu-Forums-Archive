---
title: "Not able to connect my server machine to other server"
date: 2011-10-21
forum: Server Platforms
---

### Post by Naresh Raj N on 2011-10-21
I am Facing few problems in getting my UBUNTU SERVER 11.10, get connected to Another SERVER Machine.
  
I Installed UBUNTU SERVER 11.10. I went on with applying GUI, GNOME DESKTOP by 
[INDENT]sudo apt-get update
[/INDENT] [INDENT]sudo apt-get install ubuntu-desktop
[/INDENT]   
After the completion of above Installation, I am Facing Few Problems:


1. Not able to connect my server to other server from DESKTOP->FILE->"connect to the SERVER".
  
Displayed As:
  
"Failed to Retrieve Share List from Server"  I selected Type->"Windows Share"
  
I need some Help in Finding a Solution for this above problem. And Guide  my server machine to get Connect to the Other server Machines.
  
  
2. In the Desktop, From Panel, It Shows "WIRED NETWORK" Device Not  Managed.  I tried to Edit the Wired Network by providing the IP Address,  Gatway, Dns etc... still it fails.
I am not able to View the "CONNECTION INFORMATION". When I click "CONNECTION INFORMATION"
  
  
Displayed As:
  
Error displaying connection information:
No valid active connections found!
  
Also help me to Manage my Wired Network Connection & make View my  connection Information Details. The Internet service is available in the  system. And there is No problem in accessing the INTERNET.
  
  
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

### Post by newbie-user on 2011-10-21
Is your other server a Windows server or an Ubuntu machine running samba?  Check to see that either samba is running on the other machine or that your Windows shares are properly set up with the proper permissions.

For the other problem with the network card, the information here helped me out when I had the problem:

[http://www.thebitguru.com/blog/view/328-%22device%20not%20managed%22%20in%20Ubuntu%20Karmic%209.10](http://www.thebitguru.com/blog/view/328-%22device%20not%20managed%22%20in%20Ubuntu%20Karmic%209.10)

---

### Post by BHEJU on 2011-10-21
Try this thread, it worked for me.
I upgraded my client to 11.10 (server is 11.04). And I could not see the shares on my new 11.10. (so other way around compared to your issue)
I just had to mess with config file. details in this tread.
Hope it works for you as wel..


[http://ubuntuforums.org/showthread.php?t=1861985](http://ubuntuforums.org/showthread.php?t=1861985)

Cheers,

---

### Post by Elfy on 2011-10-21
Thread closed. Please do not post duplicates, it dilutes community effort.

---

