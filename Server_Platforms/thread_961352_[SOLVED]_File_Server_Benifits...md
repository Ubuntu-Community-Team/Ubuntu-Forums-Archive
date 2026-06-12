---
title: "[SOLVED] File Server Benifits..?"
date: 2008-10-28
forum: Server Platforms
---

### Post by brhartin on 2008-10-28
If you want to stream any media or access any shares using ubuntu, what are the benefits of setting a file server then just enabling a shared drive ..for accessing media tomb or g streamer, etc...THX

---

### Post by lunarcloud on 2008-10-28
The idea is to have a dedicated machine setup for just serving files. Generally, file servers are faster than "easy" means of sharing. a good samba/ftp server is worth having in the house.

---

### Post by lykwydchykyn on 2008-10-28
When you set up a shared drive, you are creating a file server.  Having a separate machine for this is just a question of resource management.

---

### Post by Kellemora on 2008-10-28
Hi BrH

That is EXACTLY what we are looking into doing here.  I'm in the process of studying various methods right now of ways to implement it most effectively.

Here is the PROBLEM with using shared drives or folders over a simple LAN!
Each employee needs to know on Which Computer the files they need to work on, and on which drive in that computer they are located before they can even begin to search for the required file.

This is ONE of the reasons I switched my entire office over to Ubuntu to start with.  I have each drive and/or folder required for use at each work station auto-Mount to their destop.  They don't need to know where it is or find it, because it's right there on their desktop.  Until a reboot, then I have to set it up again.

Now, by my way of thinking, IF I had a File Server, everyone can look TO the File Server for the drive or file they need, regardless of where in the building or on what computer the file really is, as the File Server would act as a redirector and/or MOUNT all drives and folders on itself.

Since I know NOTHING about Servers, I downloaded and started playing with Edubuntu, mainly to see how they did things.  Figured it would help me understand servers a little better, working with one that runs out of the box.  I've learned a LOT, but don't want to go the THIN CLIENT route with a Main BIG Server.  To me it would mean I probably need a CLUSTER server which would be WAY over my head.  BUT with SMART TERMINALS and using a File Server more as a Repository of f
This is Time consuming and costly!

---

### Post by Kellemora on 2008-10-28
iles. That would probably be the best way for me to go!

TTUL
Gary

---

### Post by brhartin on 2008-10-28
I see your points on resources and access but then another question would be.. If you have users or groups to only access X drive or X folder.. in Ubuntu SRV, is that a all day process to configure? I know in a WIN AD environment its pretty simple.

Sorry if im not correctly explaining what i need to do..i'm  trying to figure out the best way to stream media and have access to documents on a dedicated server with access restrictions to groups or Users in a mixed Linux & WINS environment  where the file server will be ubuntu...THX

---

### Post by lykwydchykyn on 2008-10-29
The tricky part there is figuring out how you want to determine who is who between desktops and servers; in other words, centralized authentication.  Microsoft sells AD as a packaged system for this and of course the Windows clients are all integrated into the server environment.  With Linux it's not so integrated, and when you throw Windows clients into the mix it gets a bit hairier.  

That said, it can be done in Samba, but there are some pitfalls to look out for.  I would highly recommend checking out the "Samba by example" guide from the samba project as a starting point.

---

### Post by alienprdkt on 2008-10-29
I'd recommend this [http://oreilly.com/catalog/samba/chapter/book/index.html](http://oreilly.com/catalog/samba/chapter/book/index.html)

---

### Post by travelinman81 on 2008-10-29
I have a samba setup with mix Linux/Wins workstations. It works great I am basically using it for the same setup as you. I have a file server setup that handles all the media and files for all other computers. It's not really  that hard to set up it works very reliably so far it has been up and running for over a year now, the only time the server has ever went down is for a kernel upgrade or power outage.It gets a little weird when you start setting up user permissions. I have mine set up so my user account on any computer in the house has full read/write privileges and everyone else just has read privileges. I have two kids that could destroy anything. It works good I have the file server set up to auto mount the drive that contains all this information then I just made Fstab entries into the Linux workstations setting the permissions as user so whoever is logged in has there permission set. I mapped the drives on the wins computers and everything works great since the media drive is mounted I can put CD's, DVD's, Flash media anything that mounts to media into the server and it can be accessed from any computer in the house. It works well requires little maintenance, and is very convenient. Fully recommend a samba server for that situation.

---

### Post by Robstarusa on 2008-10-29
I think the advantages are speed & scalability

downside? Complexity.

---

### Post by alienprdkt on 2008-10-29
> **Robstarusa said:**
> I think the advantages are speed & scalability

downside? Complexity.
not to complex unless you are trying to integrate with Microsoft AD Authentication, but for file sharing for Samba Users  setup is fairly easy.

---

