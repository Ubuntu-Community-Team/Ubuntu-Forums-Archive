---
title: "Unable to see server from windows network"
date: 2006-07-28
forum: Server Platforms
---

### Post by Dave S on 2006-07-28
Hi Guys,

I have just reinstalled Ubuntu desktop onto a 21 Win XP Home edition network. 

All clients have static IP addresses. The Server popped up with one automatically once installed?!! Which does relate to the other ip addresses/

The Ubuntu machine can see and access all clients with no problem, which is great.

However, the clients cannot see the server in Network Neighbourhood at all. 

I can ping the server from the clients and get responce.

I have added a share folder, and made the Server a Wins machine, in fact at this stage I have tried all other options too, but am not getting anywhere. 

The server can see the clients, but the clients cannot see the server.

Does anyone have an idea as to what the problem might be?

I am also not use to not having access to the samba config file as I am unfamilier with not being root and it says only root can change it. I have tried the sudo command but to no avail. Can someone also tell me how to do this?

Thanks, the main thing is getting the clients access to the server as its just going to be a file server.

Thanks for having a think about this one,

Regards

Dave

---

### Post by joshchernoff on 2006-07-28
I think you use samba?

---

### Post by chrisfay on 2006-07-30
Why don't you have root to the server? Have you not set your root passwd or something? 

If not:

"sudo passwd" in terminal and you can set it. 

To modify the file in nautilus you will have to open a terminal session and type "sudo nautilus". Then enter the root password you just created and you can edit it that way.

---

