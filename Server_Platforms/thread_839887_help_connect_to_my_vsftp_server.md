---
title: "help connect to my vsftp server"
date: 2008-06-24
forum: Server Platforms
---

### Post by DFord425 on 2008-06-24
I am able to connect to it from the same machine using localhost. But if i try to connect from my XP computer, i cant. My XP computer is wirelessly connected to the router that is connected to my modem. My server is connected to another router which is set up as a wireless bridge, and the firewall is turned off on the wireless bridge. Is there any other configuation that i need to do to the routers? I followed tha instructions on the Ubuntu help documentation: [https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html).

**Edit: And i want to eventually be able to connect to it from outside my network, is there anything else i need to configure to do that?

---

### Post by DFord425 on 2008-06-25
Any one have any ideas what i could try?

---

### Post by weryl on 2008-06-25
Have you forwarded port 22 to your server? If not, you have to configure you router to do so.

Actually I dont know what port's needed for vsftp; i dont even know what it is. But for fpt it should be 21 and 22 for sftp.

Edit:
Oh ok youre using vsftp, now i get it. Yup, you need to forward port 22.

---

### Post by DFord425 on 2008-06-25
In my router which is connected to the modem, i have it fowarded for all ftp, i should probably change it for my wireless bridge too, right? Thanks.

---

### Post by unixbills on 2008-06-25
Try connecting from the same machine but use the IP address and not "localhost".  Is it that connections are only allowed from localhost?

---

### Post by DFord425 on 2008-06-25
I will try that and the port fowarding later when i get out of work, thanks for you input.

---

### Post by chuck jessup on 2008-06-25
if you have dsl you may haveto set the modem to PPPoE, due to a built in firewall, i had to do this to my dsl modem it takes a bit to understand set the router with the isp log in crudentials, and the modem is just the box... this may be a fix...

---

### Post by DFord425 on 2008-06-25
I tried to connect to the FTP server from the same computer, not using the localhost ip, that worked.

I set up port fowarding in both my routers. The router connected to the modem fowards to the bridge router, which then fowards it to my computer, that didnt work. I tried it where the first router fowarded it to my comp, but that didnt work either. 

I do have DSL, but have not yet tried to configure the modem as mentioned above. But i dont see how i should have to if the connection is coming from the same network. But i will try that later.

Are there any other ideas?

---

### Post by DFord425 on 2008-06-26
> **chuck jessup said:**
> if you have dsl you may haveto set the modem to PPPoE, due to a built in firewall, i had to do this to my dsl modem it takes a bit to understand set the router with the isp log in crudentials, and the modem is just the box... this may be a fix...
Im not sure what you mean by this, do you think you could explain it in a little more depth.

---

### Post by chuck jessup on 2008-06-30
PPPoE is a setting you have that makes teh modem a straight through box. When you get the modem from say ATT, it comes set up for a home user, the modem has a firmware firewall that can be turned off if you need to (i.e to turn home service i-net only' into a working broadcasting unit.) You would then have to set up the service to dial out of the router. This will allow you to broadcast the server over the internet. this should only need to be done when you have home service with companies like att yahoo dsl. basicly you log into the modem and set it to PPPoE and then log out, sign into the router. You must now use the router as your dialing service, so you need to set the router up with the user name and password to use the internet. this should only be done if you know what you are doing, as you may not be able to reset the modem back to the original settings. 

PPPoE allows the modem that would normally only do incomming to allow out going broadcast from the router. the router will do the broadcasting... this is why you may need to set up for PPPoE.

let me know if this helped you or made things worse... :P

---

### Post by chuck jessup on 2008-06-30
Oh and one other thing try hooking the computer up wired, the wireless may have a fit with heavy bandwith. wired connections tend to be the best for data transfers.

Jesse Fender
----------------------------------------

---

