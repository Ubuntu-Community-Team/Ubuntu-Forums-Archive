---
title: "FOG server - Fatal Error: Failed to mount NFS Volume."
date: 2011-12-21
forum: Server Platforms
---

### Post by Nikolai D. on 2011-12-21
Hi guys and girls,
lady's and gentleman, :)

I have successfully installed Ubuntu desktop 10.04 LTS in a VMware ESX virtual machine. And then i installed latest FOG server on it. A view days ago. Also tested it and it works. Pulled and Deployed an image. Without sysprep. Just pull and push for the sake of testing. Which is good. :)

I have also another Windows File-Server. And a shared FogImages folder there that i mounted in Ubuntu so that i could use it for images i pull. But it gives me the following error since i (with my collegue) have setup to automatically mount the share on Ubuntu.
Error "Fatal Error: Failed to mount NFS Volume."

My collegue is a littlebit more expirienced Linux than i am. So for him it was question of minutes which for me could be hours. So he fast fixed it here.

What did we do:
we added fogpw text tile to the /etc/ folder. And then added this line to fstab in /etc/:
//FileserverIPADRESS/FogImages   /media/fogimages cifs   credentials=/etc/fogpw, defaults 0   0
and then renamed the images folder on the root to images.old and made a symbolic link to the /media/fogimages. I also have copyed the dev folder and everything from images.old to images new. Which is on the share now. So i can go to images folder (symbolic link) on the root of Ubuntu server and i land in the Windows share.

The share has the following perpisiions:
Share rights - everyone full controll
Security rights - Modify (for the user in fogpw file in the /etc/)

When fog is pxe booting this is what it prints:
Mounting File System ... mount: FileserverIP:/images/dev failed, reason given by server: Permission denied.
mount: mounting FileServerIP:/images/dev/ on /images failed: Bad file descript
Done
Checking Mounted Filesystem ...
An error has been detected!
Fatal Error: Failed to mount NFS Volume.
Computer will reboot in 1 minute.

Any suggestions where to look further? Or some one having more experience can give an advice? :)

Will be much appreciated,
Thanks in advance,
Nikolai

---

### Post by Nikolai D. on 2011-12-25
totally no replies hm,
to complicated or something? :)

---

### Post by Nikolai D. on 2012-01-09
anyone? :)

---

### Post by ajcke on 2012-02-15
Did you get this figured out?  I have the same problem.  I followed [http://fogproject.org/wiki/index.php?title=Image_Upload:_Error_Checking_Mount](http://fogproject.org/wiki/index.php?title=Image_Upload:_Error_Checking_Mount).  My .mntcheck files are 0kb.  What's supposed to be in these?  I have not been able to correct this problem since I mounted a network share to my images directory and copied all my images to it last week.

---

