---
title: "Server Advice"
date: 2011-01-05
forum: Server Platforms
---

### Post by mclimber43 on 2011-01-05
I am setting up my first network and I need some advice - I am setting up a server for a small lab (10-20 client machines, Linux and Windows XP/7).  I need file sharing and printer sharing, and I would like user authentication.  I would also like all computers to connect to the internet by packet forwarding through the server (maybe this is not the greatest idea?).  Finally, I would like to be able to securely expand the network in the future to clients who are not physically connected to the same router/hub.  Perhaps SSH would be ok for this, I am not sure.

Do you have any recommendations for the server?  I am familiar with Samba and NFS, and I would like to run the server on a linux box.

Thank you ever so much for your help!

---

### Post by kevinthecomputerguy on 2011-01-05
Give this a read
[http://woodel.com](http://woodel.com)
 
Best of luck
 
-KevinTheComputerGuy

---

### Post by HermanAB on 2011-01-05
Well, the best advice I can give you is to start off with a VMware install so that you can do each major function on a separate VM.  That will allow you to easily move functions to new kit when the business has grown and needs more oomph.

MS Windows cannot do NIS or NIS+, it only does Kerberos+LDAP, so your only solution is Active Directory.  Active directory comes in two flavours.  Samba only does the first one, which should be good enough.  You can even download a fully functional authentication VM from the Mandriva web site, but you can roll your own by following the guides on the Samba web site.

Hope that helps!

---

### Post by tgalati4 on 2011-01-06
[http://freenas.org](http://freenas.org)

---

### Post by mdlueck on 2011-01-06
If you need to share printers, AVOID getting Samba involved! I have been using Samba since 3.0.2, and the build currently in 10.04 server gives me fits. A downgrade from our server running 9.04.

I have gone to printing directly to CUPS to get printing working again. Check out: [http://www.lueckdatasystems.com/HOW-TO_Connect_Windows_to_a_CUPS_Network_Printer](http://www.lueckdatasystems.com/HOW-TO_Connect_Windows_to_a_CUPS_Network_Printer)

Samba still seems to work well for file sharing.

The one downside to directly printing through CUPS is there is no centralized / automated way to handle Windows client print drivers.

---

### Post by mclimber43 on 2011-01-08
Thank you all very much for your advice.  It is greatly appreciated.

---

