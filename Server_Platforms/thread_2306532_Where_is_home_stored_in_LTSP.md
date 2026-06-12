---
title: "Where is /home stored in LTSP???"
date: 2015-12-16
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2015-12-16
I am looking into LTSP for potential deployment at my house. I currently have a Virtualbox environment all set up that I am playing with. PfSense router vm for the wan, the lan goes to both the Ubuntu LTSP server, and a PXE booting client without any hard drive. It all works great.

I had to follow both the Debian wiki and the Ubuntu guides to get this working, both leave out some parts it seems. I set the NFS share to be read / write in hopes of persistence. It worked, I have /home/$USER persistence in the chroot. Ideally I would like to be able to backup the entire chroot /home to a NAS as well. However regardless of what I create or put in the /home/$USER inside of the client box (logged into the ltsp server)... Nothing shows up in the /home/$USER folder when I look in it manually from inside the server vm. It's like it doesn't exist, however if I login through the client it is all there. 

Ultimately I need to know where these files are being stored so I can setup a proper backup solution. Does anyone know where they are? Or rather, why aren't they showing up when I browse the folder inside the chroot? Better yet, would it be possible to link a folder from the ltsp server itself, into the chroot and work that way? Would appreciate ideas and suggestions on how best to accomplish the goal.

---

### Post by slickymaster on 2015-12-16
Have you checked in```
/opt/ltsp/<architecture>/
```

---

### Post by Tadaen_Sylvermane on 2015-12-17
Solved it. I kept thinking it would store it in that location as well. I'm not going to try to understand how this works, but it is using the servers /home/$USER instead of in the chroot directories. So I just need to set the server to backup /home to the NAS and it will take care of everything from there.

---

