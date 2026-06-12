---
title: "shared folders with vmware and windows 98"
date: 2008-02-09
forum: Virtualisation
---

### Post by yoramfr on 2008-02-09
I use vmware server on ubuntu with windows 98 installed on it,
But i didn't find any way to share folders between the two.
so what I'm asking is if you can give me guides on how to do it.
I also need a USB support in the virtual machine so if you have a guide of that to, please post it.

thanks!

---

### Post by fjgaude on 2008-02-09
One way to share folders is through Samba in Ubuntu. Go to System/Administration/Shared Folders and set them up.

Then in Windows go to the Network in Windows Explorer or what it is called in 98. I haven't used such since about 1998. You will see your WORKGROUP that you set in Ubuntu. From there any problem can access your files that are in the shared folders.

Another way is to go through the NAT using the IP addresses of Windows which you can find out at the Windows command line with the **ipconfig** command.

Let's face it, there's lots to learn in order to do what you wish. So...

---

### Post by Mujaheiden on 2008-08-31
you can more also set up an ssh server, and then download winscp in a box.

---

