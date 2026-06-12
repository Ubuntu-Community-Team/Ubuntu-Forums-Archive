---
title: "Looking for a clone server"
date: 2009-03-13
forum: Server Platforms
---

### Post by cazz on 2009-03-13
Do anyone know a very good clone program that can clone many workstation to image and back?

I have try Clonezilla but I dont get that to work because I dont want to use it as a NAT or a DHCP, just like to have it to work as a normal clone server with one NIC.

I have look at PING but is not support multicast and if I going to clone about 30 computer in a room at the sametime it going to get alot of work for the server, speciel if I going to use SAMBA.

Some friend of my have try FOG but they have problem with it, I dont know what the problem is so I can't write it down here.

So can someone tell me what program I can use to run on a server that help me easy to clone computer with help of PXE so I dont need any disk, USB, or CDROM/DVD to boot from the networks computer.

---

### Post by HermanAB on 2009-03-13
Well, nothing is ever easy.

For PXE, you need to run a DHCP and TFTP server and DNS will also help.

Cheers,

Herman

---

### Post by daboroe on 2009-03-13
> **HermanAB said:**
> Well, nothing is ever easy.

For PXE, you need to run a DHCP and TFTP server and DNS will also help.

Cheers,

Herman
so to do a clone server that uses multicasting a person need to run the clone program on the server, a dns server, a dhcp server and a tftp server.

or

do you just need a dhcp and dns server on the network and the tftp server on the ubuntu server?

---

### Post by HermanAB on 2009-03-14
You can put everything on a different machine if you want.

Cheers,

H.

---

### Post by cazz on 2009-03-14
> **HermanAB said:**
> You can put everything on a different machine if you want.

Cheers,

H.

Hi

Yes I have already a DHCP server AND DNS server

I just have to add a TFTP server and a clone program

---

### Post by daboroe on 2009-03-14
what is a good tftp server then for ubuntu?

could someone write up a tutorial to do all this?. I am going to guess alot of people would use it and need it right now.

---

### Post by cazz on 2009-03-14
> **daboroe said:**
> what is a good tftp server then for ubuntu?

could someone write up a tutorial to do all this?. I am going to guess alot of people would use it and need it right now.

well you have this
[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

But to make it work for me I still have a server that I can send and reserve image of the client disk.

---

### Post by daboroe on 2009-03-14
so the your server runs the tftp server? what tftp client do you use on the windows os based machines?

---

### Post by cazz on 2009-03-14
> **daboroe said:**
> so the your server runs the tftp server? what tftp client do you use on the windows os based machines?

Well yes I have try some tftp server but I like to have one in all packet but not the DHCP

I use PXE in my client so I dont need to use any USB,CDROM or anything else.

Right now I trying FOG but I can't do so much more then install on a server I have it at home and take it to my job on Monday because I have to change the DHCP server and at home I just use a normal router as my DHCP server and I can't add so much information on it like I can with our 2003 DHCP server at my job.

---

### Post by daboroe on 2009-03-14
all in one packet what do you mean?

to do your imaging, what do you have all on your server 


what is not on your server.


how do you set up for pxe or is that boot to lan?

---

### Post by cazz on 2009-03-14
> **daboroe said:**
> all in one packet what do you mean?

to do your imaging, what do you have all on your server 


what is not on your server.


how do you set up for pxe or is that boot to lan?

Like now I going to try FOG but when I install it I did not pick that is going to install a DHCP service on the server.
So now I have a nice GUI, tftp server, a program that compress and create image file and a client that can boot from LAN.

So on the Ubuntu server I have install I have that I want.

**Ubuntu server** - tftp server, Control Panel, imagecreate and client that can boot from LAN

**Win2003 server** - DHCP server

**(I dont know if we use a Linux or win) server** - DNS server

FOG, Clonezilla and PING have a client that I can boot from LAN so I dont need anything else when I need to clone a workstation to the server.

More information about FOG is here [http://www.fogproject.org/](http://www.fogproject.org/)

---

### Post by HermanAB on 2009-03-14
The easiest way to clone over a network is with 'dd' and netcat.  You don't need anything else and you'll find that the complex programs like clonezilla is usually just a wrapper around these simple programs:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

Cheers,

Herman

---

### Post by windependence on 2009-03-15
[http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html)

-Tim

---

### Post by Cheesemill on 2009-03-15
+1 for FOG

I discovered it about 6 months ago and have to say it's a brilliant piece of software, especially as we can still use our Win 2003 server for DHCP duties.

Where I work we can now re-image all 300 workstations in under an hour, it's so much better than having to spend hours trying to fix corrupt windows installations and root out viruses. In fact we now re-image all machines once a week as part of company policy.

It also taught the users pretty quickly not to save any work locally on their machines :D

Cheesemill.

---

### Post by cazz on 2009-03-15
yes what I have see I like FOG too with a very nice control panel so I going to try it tomorrow.

That I read about 'dd' and netcat sound very nice and maybe try that someday, one thing I dont like is I have to create a boot USB or CD to use it but that is ok.

---

### Post by Roasted on 2009-04-04
I know you said that you have friends who had problems with FOG, but I'd be VERY curious to hear what problems they had.

I use Clonezilla LiveCD every day of my life at work. I love it. Their server side was a different story. The DRBL setup and the lengthy configuration setup was crazy, and I could never get it to work. After four months of troubleshooting in my free time and a few weekends here and there, I got it to work, only to find it messed up the MBR when it was cloned, so I had a useless image.

So now, I use FOG at work, which only took me 2 hours to get Ubuntu installed, FOG installed, configured, and already imaging my first computer. I've imaged several hundred machines of different make and models. Granted, we're using Windows 2000 Pro + XP Pro at work, and I know FOG is more oriented towards Windows cloning, but it's so nice having an Ubuntu image server (basically, my laptop) with a 24 port gig switch and just blast an image out to a few PCs on my workbench and bam, they're ready to go... and from what I understand, FOG does support Linux, just not to the extent of Windows. It's nice having a single NTFS partition option being resizable, so if a computer that came with an 80gb drive goes down, and I only have a 40gb drive sitting around, at least I can use that 40gb drive as a temporary until we get more 80s in. Of course, this is only true if the amount of the data on the image does not exceed 40gb. Then, we have a problem. I don't believe the Linux side has that much capability (yet) but it's a great product to check out.

The only issue I've ran into is 1 computer having an issue with it, which this same computer has issues with Clonezilla LiveCD being cloned too = the Dell Optiplex 740, which thankfully we're not getting anymore of due to lengthy problems. But I've found I had to flash the BIOS back to 1.1.8 for it to work with the FOG PS kernel. Other than that, every computer I've tried has worked. I had an older Compaq give me some error once, but it still cloned just fine.

I strongly recommend you try out FOG. I use it every day at work and it has made my job exponentially easier. If you have any questions, you can PM me, post here, or hit up the FOG forum on sourceforge.

EDIT - Just another thing to tack in there, I'm not running FOG on our "network." Instead, I have Ubuntu/FOG installed on my laptop with a "library" of images on computers that I commonly run into at work, along with a 24 port gig switch that I clone with. I typically do my cloning in the tech room by my desk, but at least I only have to grab my laptop + a switch to make it a mobile imaging solution if I have to drag it out to another school to redo a library or something. So I basically run everything on a localized LAN without any external access.

---

### Post by cazz on 2009-04-04
well what I did remember about FOG that I get it to work to create image from PC but did not get it to restore it to the PC.

I dont remember what was wrong


we have licens for about 300-400 för norton ghost so my other co-worker did say that I dont need to use FOG to that problem anymore.

---

### Post by Roasted on 2009-04-05
It's easy to restore it to the pc. Once you upload it and it saves, go back to the star where your tasks are and hit list hosts. From there you will see the registered hosts with the system. Whichever one you want to deploy, just hit deploy, reboot the system over the network and it takes off.

I used to use Ghost at my last job. I find FOG to be easier to manage and quicker at getting the job done. Even if Ghost was free, FOG would take the cake, IMO. That just may be biased talk from a Linux fan, but it is what it is.

---

