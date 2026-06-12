---
title: "VMware Ubunto 10 server"
date: 2011-02-16
forum: Server Platforms
---

### Post by coop9653 on 2011-02-16
I am attempting to test Zimbra, to do this I need an install of Ubuntu  server.

I set up a VM with 10G of space.
I then installed server I read that if I did not use the full space on partition I could grow it later.  So I used 9G  of my 10 available.

I performed the install.  Got the DNS working. Installed Desktop,  (because for the life of me I could not get the blasted samba to work, so could not copy the zimbra tar file to the server)

Using desktop, (which I like, security non withstanding)  I copied the zimbra install.
When I ran it, it said I only had 3M left for space I needed 5.
UH OH

so then I researched how to grow partitions and it seemed gparted was the way to go.

I had two partitions, one small flagged boot
the other was large,  

I tried resizing the large one, and it said success
but I still only had 3M  free space

So I tried to resize the boot partition.

That was a mistake, because now my system will not boot. It drops me to an (inittramfs)  prompt.  and of course I am totally screwed!!!   But this is what testing if for right?  (what dont kill you makes you... crazy)

So I can start over (VMware is great)
What I would like to know is what is the best way to install on VMware  so I can grow my space later if needed?

PS... if there is an easy way to recover my current mess up, that would be nice as well.

Thanks

---

### Post by sikander3786 on 2011-02-16
Welcome to the forums :-)

I have never ever used VMware. I am a [Virtualbox]("http://virtualbox.org") die hard fan and it has an option for Dynamically expanding storage drives which grow in size as you add data. See here for a snapshot.

[http://2.bp.blogspot.com/_Aq4pKLMYUTk/TUJ_IXw3r3I/AAAAAAAAACE/RFPnvWE9f8I/s1600/storage+type.png](http://2.bp.blogspot.com/_Aq4pKLMYUTk/TUJ_IXw3r3I/AAAAAAAAACE/RFPnvWE9f8I/s1600/storage+type.png)

I believe there should also be such an option in VMware but not sure where it is.

Other than that, expanding drives using gparted in a Virtual machine is not the safest route to go as you are already dealing with Virtual Hard disks and I am not sure about the success rate of gparted with that.

---

### Post by coop9653 on 2011-02-16
virtualbox is nice, but I needed some VMware specific features.... 
regardless, VMware does allow you to give my space to a Virtual Machine.

I did that,  added 10G to the Virtual Machine.
when you go into Ubuntu,  the 10G shows up a unallocated space.

So you should be able to simply resize the partition into that space

I am guessing I was using the wrong partition scheme and formatting to allow this in the first place.  So i am hoping someone can tell me the best way to start, before I reinstall and try again.

---

### Post by elico on 2011-02-16
well i recommend to you the trunkey linux ubutnu base appliance 
[http://www.turnkeylinux.org/zimbra](http://www.turnkeylinux.org/zimbra)

---

### Post by hostingservices on 2011-02-17
If you don't mind me asking, for your server you said you got the DNS working, does that mean you can connect to the server through your external IP address? If so, would you mind assisting me with getting my server accessible to the internet? I've been struggling with this problem for three days straight and finally decided to come on to these forums.

---

### Post by coop9653 on 2011-02-17
elico

Thanks i tried that first.  and its a awesome product.  
That does NOT support Outlook!  
It was also limited in other areas!

So it did not work for me.

---

### Post by coop9653 on 2011-02-17
Hostingservices....
I got the system to access the internet.
and I was able to nslookup my own internal

I never tried the external IP..  I had not even bothered routing an IP to it on my firewall yet.

the instructions I used were called ubuntu 8.04 lts sever (hardy herom) install guide-zimbra.

---

