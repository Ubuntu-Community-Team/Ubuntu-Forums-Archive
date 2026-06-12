---
title: "Error Message"
date: 2009-01-14
forum: System76 Support
---

### Post by mysteriousdarren on 2009-01-14
My computer is giving me an error message when it tries to authenticate itself. 

This is the error. 


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://planet76.com](http://planet76.com) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 176A5C84ED67C9ED

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/Release.gpg](http://playonlinux.botux.net/dists/hardy/Release.gpg)  Could not resolve 'playonlinux.botux.net'

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_US.bz2](http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'playonlinux.botux.net'

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://planet76.com/repositories/./Release](http://planet76.com/repositories/./Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

THx for the help.

---

### Post by thomasaaron on 2009-01-14
First, make sure you're on the Internet. Go to Firefox to test. The lack of an Internet connection could be the cause of some or all of these errors.

This command should fix the gpg key error...

```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

...it's all one long command.

Going to System > Admin > Software Sources > Updates and unchecking the CDROM line will fix the CDROM error. You need to be updating from online anyway, not from the CDROM.


After doing these things run updates again and see what happens.

---

### Post by mysteriousdarren on 2009-01-16
I am running Ubuntu 64-Bit, my system 76 model number is....where do u find that on the computer? 

I am upgrading to 8.10, and will try again later. The new error messages will be posted soon. Thanks for the yep.

---

### Post by thomasaaron on 2009-01-16
Did you try what I suggested?

---

### Post by eyecreate on 2009-01-17
well..one thing I know that is part of the problem is that your repository URL for playonlinux is wrong. I got confused when they changed it a little bit back, and there wasn't much indication they changed it. The new repository is listed on their site, which is in the two commands below that will update your URL.

```
sudo wget http://deb.mulx.net/playonlinux_hardy.list -O /etc/apt/sources.list.d/playonlinux.list
wget -q http://deb.mulx.net/pol.gpg -O- | sudo apt-key add -
```

---

### Post by mysteriousdarren on 2009-01-19
I upgraded to 8.10 and and playonlinux is not working at all. I was wondering if i should remove it, and then reinstall. Also my NVIDIA graphics card seems to not be working very well because the graphics card seems to put me into low graphics mode everytime it starts up.

---

### Post by thomasaaron on 2009-01-19
Did you go to System > Administration > Hardware and enable the -177 nVidia driver?

---

### Post by mysteriousdarren on 2009-01-19
yes, i enabled that driver right after i upgraded.

---

### Post by thomasaaron on 2009-01-19
> the graphics card seems to put me into low graphics mode everytime it starts up

Are you booting with an external monitor connected? If so, disconnect it and see if you have the same problem.

> 
I upgraded to 8.10 and and playonlinux is not working at all

After looking at their available downloads, it looks like they have one for Hardy and one for Gutsy, but not one in Intrepid's repository.

When you click on the Ubuntu icon, did you install the .deb version or one of the others?

I know virtually nothing about playonlinux, but that's my initial guess.

---

### Post by mysteriousdarren on 2009-01-19
This computer is a laptop, I do not use an external monitor. I was wondering if I could go back to hardy since i am having so much trouble with intrepid. I use playonlinux for almost all the programs that I have.

---

### Post by thomasaaron on 2009-01-19
I don't know if you can go to Hardy. I still don't know what kind of computer you have. :popcorn:

Do you have a System76 machine? If so, go to System > Administration > System76 Driver and click the "About" button. That will tell you.

---

### Post by mysteriousdarren on 2009-01-19
Serval Performance
system model: serp4
processor CPU Version
Memory 4050228 kb
156 GB hard drive?

---

### Post by thomasaaron on 2009-01-20
You can definitely go back to Hardy with the SerP4. Just install and run the System76 Driver after imaging it.

Follow these instructions:
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by mysteriousdarren on 2009-01-21
I followed the instructions after burning the image to a disk, and am unable to install ubuntu from the menu. I tried all three options, and none of them worked. I was wondering if there was another way to get 8.04 since going to 8.10 had so many problems for me.

---

### Post by thomasaaron on 2009-01-21
Whenever you try something and it doesn't work, please explain exactly what you are seeing. What does it do? Did you get error messages, etc.... Otherwise, it's really difficult to figure out what is going on.

---

### Post by mysteriousdarren on 2009-01-21
The menu starts up I press "Demo and Full Instillation," then press reboot now. 

I get this error message that says C:/windows/microsoft.NET/framework/v2.50727/mscorwks.dll could not be loaded. 

The menu starts up I press "Demo and Full Instillation," then press manually reboot later. 

Of course this does nothing at all. I try to boot from the live cd. It flashes extracting, and does nothing until it closes itself down.

---

### Post by thomasaaron on 2009-01-21
mysteriousdarren, you are being very mysterious.

All of the above posts indicate you are wanting to install Ubuntu 8.04.
Those error messages indicate you are using a Windows disk or something.

In order to help you, I need you to give me a complete description of what you are trying to accomplish, what disks you have, etc... 

Instructions for installing Ubuntu on your computer are here...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

It may clear some things up for you.

---

### Post by mysteriousdarren on 2009-01-21
so no going back to hardy? or just go to 8.10? what about the problems with wine?

---

### Post by thomasaaron on 2009-01-21
mysteriousdarren, you are being very mysterious.

All of the above posts indicate you are wanting to install Ubuntu 8.04.
Those error messages indicate you are using a Windows disk or something.

In order to help you, I need you to give me a complete description of what you are trying to accomplish, what disks you have, etc...

Instructions for installing Ubuntu on your computer are here...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

It may clear some things up for you.

---

### Post by mysteriousdarren on 2009-01-21
i just downloaded the /tmp/ubuntu-8.04.1-alternate-amd64.iso.torrent, i was wondering if this is the correct torrent to reinstall hardy. I was also wondering what the procedure is to reinstall it.

---

### Post by thomasaaron on 2009-01-22
Here is what you need to do to install Hardy:

You can download a CD image for Ubuntu here...
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Download the 64-bit CD. You do NOT need the alternate CD.

Once you've downloaded the CD image, you will need to burn it to a CD. However, it must be burned as an *image* and not as a *data * CD. Otherwise, it will not be bootable. Instructions for this vary based on which operating system you are using to burn the CD. Instructions for various operating systems are here.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Here are instructions for re-imaging your machine...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

---

### Post by mysteriousdarren on 2009-01-24
Thanks for the help even though it took me awhile. 



System76 Rocks

---

