---
title: "Virtualbox Printer Sharing"
date: 2012-03-26
forum: Virtualisation
---

### Post by Bobhuber on 2012-03-26
This topic has as many posts as Linux itself but as usual this old man is still in the dark.
I have a USB printer NOT supported in Linux. I have Windows XP and Windows 7 installed in the latest addition of VB with printing working in both with the correct drivers for the printer (Dell Multifunction Laser). I have shared folders set up in both WinXP guest  and Win7 guest VB machines so that I can access the Ubuntu folders that I store the files I need to print. In the past I have been saving the files I need to print in the shared folder in PDF format,opening VB and printing the file. What I want to do is print directly from the Ubuntu host to the VB guest printer. Doesn't matter which guest, whatever is easier to set up. I do have an Apache server setup for web development but wanted to stay away from Samba networking if possible (not in my field of expertise) . Appreciate any help.

---

### Post by nothingspecial on 2012-03-27
*Thread moved to **Virtualization**.*

---

### Post by Jake.Debord on 2012-03-28
Samba is going to be the easiest way to do it. You really don't need expertise to get samba up and running. It was one of the first things I learned to do in linux (thanks to great tuts). I would suggest going ahead and setting up Samba and just adding the printer through samba. I didn't notice what version of Ubuntu you are running but I attached a link to an easy tutorial that should help.

[https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

---

### Post by Habitual on 2012-03-29
> **Bobhuber said:**
> ...What I want to do is print directly from the Ubuntu host to the VB guest printer. ...

You realize that this will require the the guest be running every time you want to print?

---

### Post by Bobhuber on 2012-03-29
> **Habitual said:**
> You realize that this will require the the guest be running every time you want to print?
Yes . I have to open the guest now anyway to print the files I've copied to the shared folder. I was just trying to save a step. Replacing a Laser printer that will work with Ubuntu is just out of the equation . There is a whole bunch of posts out there to go from the WinXP guest to a Ubuntu host but not the other way. Since the most recent versions of VB support folder sharing between the host and guest it seems there should be a way. Samba seems great for different machines on the same network but not really setup for a VB on the same machine that's sharing the same USB port. I may try and fool with it a bit but for right now its just as easy to open VB and print from the shared folder. Thanks for the input.

---

