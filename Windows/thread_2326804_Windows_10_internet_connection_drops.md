---
title: "Windows 10 internet connection drops"
date: 2016-06-04
forum: Windows
---

### Post by tech291083 on 2016-06-04
Hi Friends,

I had Windows 7 Home Basic (64 Bit) on my pc just a few days ago, which has been upgraded to Windows 10. But whenever I use the internet via a LAN connection to a router, I get disconnected after a certain period of time for no apparent reason. I went into Control Panel > Device Manager > Nerwork Adapters. Right-click on it and tried to update it, but it said its already updated. For example, please have a look at the below image, its for example only. 


[http://images.dailytech.com/nimage/Windows_10_Build_10061_Device_Manager_Wide.png](http://images.dailytech.com/nimage/Windows_10_Build_10061_Device_Manager_Wide.png)

My motherboard is - Gigabyte GA-H61M-S1

[URL="http://www.gigabyte.in/products/product-page.aspx?pid=4127#ov"]http://www.gigabyte.in/products/product-page.aspx?pid=4127#ov
[/URL]
I know tat it does not support Windows 10. Under the Specification link, you should find this 

"Operating System : Support for Microsoft® Windows® 8/7/Vista/XP"

[http://http://www.gigabyte.in/products/product-page.aspx?pid=4127#sp](http://http://www.gigabyte.in/products/product-page.aspx?pid=4127#sp)

What should I do now? Otherwise Windows 10 seems to be working fine. I also have 4 GB of DDR3 RAM and 500 GB HDD with Intel I3 3220 CPU with more than 3.0 GHz speed. Anyone has had this sort of problem with Gigabyte motherboards? Please help me. Thanks.

---

### Post by tech291083 on 2016-06-05
Friends,

I also tried updating network adapters both as a normal user and administrator, plus I did execute a command, which I came across in a YouTube video. Please have a look at the screenshots below, which will give a clear idea as to what I have tried so far to resolve this very issue. 

Please feel free to send me your suggestions if any.

Thanks.

[http://postimg.org/gallery/cikyez3g/90fedf83/](http://postimg.org/gallery/cikyez3g/90fedf83/)

Below are the YouTube videos, from which I have taken the suggestions.

[https://www.youtube.com/watch?v=UhiFGpOBbDo](https://www.youtube.com/watch?v=UhiFGpOBbDo)

(Control Panel > Network and Sharing Center > Troubleshoot problems)
======================================================================================================
======================================================================================================
[https://www.youtube.com/watch?v=rWGX20Pn9Nw](https://www.youtube.com/watch?v=rWGX20Pn9Nw)

(#netsh winsock reset catalog)

no restart required then,

(#netsh int ip reset reset.log)
======================================================================================================
======================================================================================================
[https://www.youtube.com/watch?v=G3DpeeXLSDM](https://www.youtube.com/watch?v=G3DpeeXLSDM) 

(#netsh int ip reset c:\resetLog.txt)

no restart required then,

(#regedit.exe)
======================================================================================================
======================================================================================================
[https://www.youtube.com/watch?v=yTyhDAOz4s8](https://www.youtube.com/watch?v=yTyhDAOz4s8)

#Disable netbios over TCP/IP

restart the pc then,

(#netsh winsock reset)

restart the pc then,

(#netsh int ip reset c:\resetLog.txt)

no restart required then,

(#regedit.exe)

no restart required then,

(#netsh int ip reset c:\resetLog.txt)

restart the pc then, it should be working fine.
======================================================================================================
===========================================

---

### Post by tech291083 on 2016-06-08
Friends,

I tried all the instructions give in all 4 YouTube videos, but nothing works. Whenever I start my PC, internet connection is there, but I get disconnected every 2 hours for some weird reason. 

I tried the Troubleshoot Problems option in Control Panel > Network and Sharing Center, but it gave me this error "one or more network protocols are missing on this computer"

It looks something like the below image,

[URL="http://www.tenforums.com/attachments/network-sharing/51326d1448960184t-network-protocols-error2.png"]http://www.tenforums.com/attachments/network-sharing/51326d1448960184t-network-protocols-error2.png


[/URL]Here is how the Troubleshoot Problems option in Control Panel > Network and Sharing Center looks like, this is not a screen shot from my own PC. But hope this will help you understand my issue better.

[http://www.tenforums.com/attachments/tutorials/45708d1446322754-network-profile-name-rename-windows-10-a-network_and_sharing_center-ethernet.png](http://www.tenforums.com/attachments/tutorials/45708d1446322754-network-profile-name-rename-windows-10-a-network_and_sharing_center-ethernet.png)

Please help me, thanks.

---

### Post by X-RED_Tech on 2016-06-13
Perhaps you have better results in Windows forums, since this is all about Windows, isn't it?

---

### Post by tech291083 on 2016-06-14
Yes, I think so, thanks a lot.

---

