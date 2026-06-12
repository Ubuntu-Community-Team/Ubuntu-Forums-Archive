---
title: "Creating a 6-pc Server"
date: 2007-12-19
forum: Server Platforms
---

### Post by brycematheson on 2007-12-19
I've been using Ubuntu for about the past 6-7 months now. I started with Fiesty Fawn (7.04) and then recently upgraded to Gutsy Gibbon (7.10). I know VERY little about networking and servers.

The main reason I'm asking for your guys' help is for a school project. Wanting to learn more about servers and networking under Linux I decided that I would do this as my semester project. The problem is that I have absolutely no idea how to start...

I have 5 older computers (Pentium 3's, 600MHz, 128MB of RAM). I also have one more recent type computer (Pentium 4, 2.0GHz, 256MB of RAM). My goal for this project is to install Xubuntu 7.10 on the older 5 computers and then install Ubuntu Server 7.10 on the Pentium 4 system. I want to be able to network all of these computers together so that they can all share files and connect to each other, and also so that we could be able to play a fairly simple game over the network.

Now, here is my problem again. I have no idea where to start. I have these 6 computers, a switch, and a bunch of ethernet cords. Is that all I need? What about the Server version of Ubuntu? I've heard in the past that it's all only command line. I'm sort of confused on where to start or even if I'm making the correct beginning steps. If anybody could help me out, that would be GREAT!

Thanks a bunch.

---

### Post by HermanAB on 2007-12-19
Cluster Knoppix is one possibility.  It is old, out of date and unmaintained I think, but if your hardware is also old, then it should still work.  So I believe that all you would need is 6 copies of the last Cluster Knoppix.

Cheers,

Herman

---

### Post by brycematheson on 2007-12-19
> **HermanAB said:**
> Cluster Knoppix is one possibility.  It is old, out of date and unmaintained I think, but if your hardware is also old, then it should still work.  So I believe that all you would need is 6 copies of the last Cluster Knoppix.

Cheers,

Herman

Wait...is 'Cluster Knoppix' another Linux distribution? Why would I want to use that over Xubuntu? Isn't Xubuntu good enough for my other old systems? It seems like it would run great on them...

---

### Post by foxylad on 2007-12-19
Cluster Knoppix is good if you have very low spec PCs, booting from hte network for instance. That might make a good project too, but it sounds like you want a simpler network.

I'm not going to attempt to explain all you need to know here, because they are much better explained elsewhere. Try googling for "networking howto", and look for articles that explain DHCP, routing and gateways at a level that you understand.

While you are reading all that, you can install Xubuntu on all the PCs - I wouldn't bother with the server version if you are unused to the command line, you can run all the server stuff you need on a standard install and use a GUI.

---

### Post by brycematheson on 2007-12-19
Wow! This Cluster Knoppix sounds like a VERY interesting thing. In the future I will be looking into booting from a network and that will be very interesting to use and so I will keep that in mind. Thank you very much.

So the Ubuntu Server isn't really needed? I knew ahead of time that the server version was all command line and so I was just hoping that maybe I could like...install a GUI for the server using the command, "sudo apt-get install gnome-desktop" or something like that. Would that work or is it still just pointless?

Thanks for all your help!!

---

### Post by HermanAB on 2007-12-19
Just go to the Cluster Knoppix web site and read a bit, then you'll quickly see why I recommend it.  It is very similar to Ubuntu.

---

### Post by Zarathu on 2007-12-19
Can you not just use a simple router or a switch?  I'd use that...pop an Ethernet cable in each of them, grab a DHCP address, and you're done.  You could do that with any distro.

---

### Post by brycematheson on 2007-12-19
Wow! That really is pretty cool. I think you guys may have actually convinced me. I now have a few questions though.

Is this Cluster Knoppix an actual operating system or is it just a boot loader which allows me to boot from a PC off of the network?

And how would I set it up? Like, the website advertises that no hard drives are needed in the PCs, because it's all done over the network. How would I set up the first initial computer and set it to be used as the main image for all the other PCs to boot from?

This is actually very interesting and something that I'm liking! VERY nice!

---

