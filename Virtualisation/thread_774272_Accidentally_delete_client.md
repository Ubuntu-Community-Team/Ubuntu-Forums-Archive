---
title: "Accidentally delete client    ?"
date: 2008-04-29
forum: Virtualisation
---

### Post by bluewhale on 2008-04-29
I had two clients in this VMWare Workstation 6 unit yesterday. Today I have one. I'm trying to figure out what occured, even as I beat my head against the wall.  ](*,)](*,)  

The client was W2K Pro, almost fully tuned out. I had gone into it to disable USB as I thought that might be contributing to an ongoing problem I have syncing my PDA up in the other client, XP.  

Assuming I did somehow manage to delete the client: is there a recovery bin to bring it back from?

#-o

---

### Post by fjgaude on 2008-04-29
That file is likely around 10GBs. Big. It might be in your Trash Bin, but I doubt it.

How do you have Ubuntu setup to handle trash?

---

### Post by bluewhale on 2008-04-29
No, nothing that large in trash. 
I'm using the default Gutsy trash protocols: not certain what that means.

---

### Post by fjgaude on 2008-04-29
The default trash setup should permit you to get back anything deleted. What shows in the Trash Can?

---

### Post by bluewhale on 2008-04-30
i found them earlier today, however still do not have a tab referring to this client in VMWare W/S. 

Might you know which file I need to refer to in order to add the client back to my clients?

---

### Post by fjgaude on 2008-04-30
Do a search with either locate or whereis for the name you gave the client.

I can't remember where the default directory is, as I always put the clients into my /home folder. Could be something like /usr/lib then the name of the folders that hold clients.

---

### Post by bluewhale on 2008-04-30
> Do a search with either locate or whereis for the name you gave
> the client.

No, I've found the files. I'm just not sure which file is executed to start that VM client. ?

---

### Post by fjgaude on 2008-04-30
Well, I unloaded VMware server, and then clicked on many of the vmware files and none would bring up the console. No program in any list was able to run the .vmx or .vmdk files. So... I'm lost... I know in Gutsy you could do what I was trying to do.

I guess the console looks at the .vmx file to know where to look for the file it wishes to load. You can see that in the .vmx file in a text editor. I guess there is no associations any more. So be it...

---

