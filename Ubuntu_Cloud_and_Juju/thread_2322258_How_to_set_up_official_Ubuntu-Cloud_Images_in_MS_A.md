---
title: "How to set up official Ubuntu-Cloud Images in MS Azure"
date: 2016-04-27
forum: Ubuntu Cloud and Juju
---

### Post by Florian_Seifer on 2016-04-27
Hello,

I am trying to setup a custom Linux VM in MS Azure. I found this:
  [https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-create-upload-ubuntu](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-linux-create-upload-ubuntu)
  guide, pointing out that there are Azure-ready Ubuntu Images to be found here:

  [URL="http://cloud-images.ubuntu.com/"]http://cloud-images.ubuntu.com/

[/URL]

I uploaded the vhd file to a blob container and then created a custom ARM-VM using a deplyment script i found online.
Then i enabled the boot diagnostics for the machine and saw that it bootet up.

But when  I try to SSH onto the machine via its public IP, I hit a connection timeout.


Is there something like an official guide on how to setup an ubuntu-cloud image in Azure?

I found this old thread, which was abandoned, so I know somebody got this to work....:
[http://ubuntuforums.org/showthread.php?t=2239220](http://ubuntuforums.org/showthread.php?t=2239220)

Any advice on the proper procedure would be appriciated.
Thank you all in advance!

Regards,
Florian

---

### Post by Florian_Seifer on 2016-05-04
Sooooo,

I guess nobody tried this after all...

Well, hope dies last i guess.





So long,
Florian

---

### Post by Florian_Seifer on 2016-05-10
Should anybody encounter a similar question in the future, I found this here video:
[https://channel9.msdn.com/Blogs/Open/Creating-a-Linux-VM-from-a-custom-image-with-Azure-Resource-Manager-ARM](https://channel9.msdn.com/Blogs/Open/Creating-a-Linux-VM-from-a-custom-image-with-Azure-Resource-Manager-ARM)

and especially the two links to Azure templates below it.

Using the instructions from the Video and the templates I was able to successfully deploy the ubuntu-cloud image to azure and connect to it.


Hope this helps anybody to save a month of their time scouring the web.


Regards,
Florian

---

