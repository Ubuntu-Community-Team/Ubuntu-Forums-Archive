---
title: "Ubuntu Server Intranet Question"
date: 2009-10-11
forum: Server Platforms
---

### Post by rewsay on 2009-10-11
I'm setting up a PowerEdge300 running Ubuntu Jaunty Jackalope, which will be transferred to another under-construction office once it's done, so I gotta have it set up here at my home.

The purpose of the server is to host the website for the www and an intranet for appointment management, confidential data storage, etc. For this reason I ordered the server with 2 separate 250GB HDDs. 

So dev/sda is all up and running, but I'm having a lil bit of trouble mounting dev/sdb for I can't figure out the proper structure to it running the way I want it to.

I yet have to get a unique IP for the server to be visible for the world wide web, which I'll be taking care of once it's set up in it's permanent physical place because the ISP might be different.

So for the moment, if I access the server at 192.168.0.10 it shows /home/myuser/web. What would be the best way to have the world wide web access the website directory in one HDD and the local network access the intranet from the other HDD?

---

### Post by Millage on 2009-10-15
I'm no genius, but I'd use Apache's virtual hosts to point to a directory on the other drive.

---

### Post by lykwydchykyn on 2009-10-15
Personally, if I were setting up a production server with only two hard drives, I'd set them up in RAID 1.  Is there any reason to put the two sites on separate hard drives?  How much data are we talking about?

As the previous poster said, you need to use virtual hosts (decent article on this here: [http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1) )

Then have your internal DNS pointing to the name that brings up the intranet, and your external DNS pointing to the name that brings up the public website.

---

