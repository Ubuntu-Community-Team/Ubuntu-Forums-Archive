---
title: "Remote Desktop Connection"
date: 2011-05-05
forum: Server Platforms
---

### Post by Gotlieb on 2011-05-05
Hi,


I have a problem with my Terminal Server Client, I cannot seem to connect to any windows server via IP address. Can anyone please recommend any tool I could use to connect? I need to work on the server for admin interfaces example Admin Kits for workspace protection 

Please!!

---

### Post by arrrghhh on 2011-05-05
> **Gotlieb said:**
> Hi,


I have a problem with my Terminal Server Client, I cannot seem to connect to any windows server via IP address. Can anyone please recommend any tool I could use to connect? I need to work on the server for admin interfaces example Admin Kits for workspace protection 

Please!!

Terminal Server Client on Ubuntu Server...?

Ubuntu Server has no GUI, so I don't see how you would be connecting to Windows boxes thru Ubuntu Server.

---

### Post by Gotlieb on 2011-05-06
Is it impossible?

---

### Post by spynappels on 2011-05-06
Could you explain what you are trying to do in a little more detail? As Aaaarghh said, Ubuntu server has no GUI by default, and administration is normally done through SSH.

Are you trying to administer other (Windows) servers from the Ubuntu Server via RDP? Can you not use RDP on your client computer? There are several RDP solutions available for Ubuntu Desktop....

---

### Post by Gotlieb on 2011-05-06
Yes I am trying to administer other windows server!
Thanks

---

### Post by spynappels on 2011-05-06
Ok, well, that can't be done directly from an Ubuntu Server without installing a Desktop Environment, or at least X server and using X forwarding over SSH. Installing a DE on a production server is not recommended from both a resources and an attack vector/security point of view. Using X forwarding could be cumbersome, depending on your network speed.

Could I ask why you don't just use RDP on a client computer to access the Windows servers?

---

### Post by velle frak on 2011-05-06
Have you tried pinging the Windows Server from you linux client? Is RDP activated on your Windows Server? What's the exact error message?

---

### Post by Gotlieb on 2011-05-06
@spynappels >> I cannot connect using RDP either and @velle frak I just tried that now and yes I can ping it.

---

### Post by spynappels on 2011-05-06
You are running Ubuntu Desktop?
Cayou RDP from a Windows machine to the servers?

---

### Post by arrrghhh on 2011-05-06
> **spynappels said:**
> Ok, well, that can't be done directly from an Ubuntu Server without installing a Desktop Environment, or at least X server and using X forwarding over SSH. Installing a DE on a production server is not recommended from both a resources and an attack vector/security point of view. Using X forwarding could be cumbersome, depending on your network speed.

Could I ask why you don't just use RDP on a client computer to access the Windows servers?

This ^^^

So on your machine, why not RDP straight to the Windows servers?  Why are you trying to RDP thru the Ubuntu Server...?  Seems like that's adding a completely unnecessary layer of complexity, unless I'm missing something...

---

### Post by velle frak on 2011-05-06
> **Gotlieb said:**
> @spynappels >> I cannot connect using RDP either and @velle frak I just tried that now and yes I can ping it.

Ok, so the program won't run because it doesn't know the --F option (which does not exists). Did you set this option, anywhere (go through all the tabs and look for anything that looks like --F).

@aaaaarghhhh, I think GotLieb is trying to connect a ubuntu desktop directly to a Windows server using Terminal Server Client, but I could be mistaken.

---

### Post by arrrghhh on 2011-05-06
> **velle frak said:**
> @aaaaarghhhh, I think GotLieb is trying to connect a ubuntu desktop directly to a Windows server using Terminal Server Client, but I could be mistaken.

Ah.  If that's the case, why is this in the Ubuntu Server section?  heh.

I'd like to hear from the OP what they're trying to do - be verbose!

---

### Post by velle frak on 2011-05-08
> **arrrghhh said:**
> Ah.  If that's the case, why is this in the Ubuntu Server section?  heh.

I'd like to hear from the OP what they're trying to do - be verbose!

You're right, need to be sure there. Altough I can't really think of a reason for a ubuntu server.

Maybe the OP can clarify.....is there an ubuntu server somewhere in this story?

---

### Post by Gotlieb on 2011-06-10
Hi all,

Solved the problem. The --F-- means full screen mode and for that I had to disable it to start in its own desired screen size

---

