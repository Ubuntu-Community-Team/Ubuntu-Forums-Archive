---
title: "Linux Cluster for Batch Image / Photo Resizing using Imagemagick"
date: 2008-11-20
forum: Ubuntu Studio
---

### Post by jfwiedmayer on 2008-11-20
I was considering stealing some cycles from an old P4 Box I have set up as a NAS, my Core 2 Duo Laptop, and my Core Duo Mac Mini.  Here is the detail on each.

[LIST]
[*]NAS (single core P4 1.8 Ghz) 512 Mb Ram / Ubuntu / Striped RAID Array
[*]Core 2 Duo Laptop (2.1 Ghz) 3 GB Ram / Vista / 7200 RPM HD
[*]Core Duo Mac Mini (1.8 Ghz) 2 GB Ram / Mac OS X 10.4 / 5400 RPM HD
[/LIST]

What I would like to do is install VirtualBox create a Virtual Machine on each and then cluster all three together over a 100M/s wired LAN.  I want to use this cluster to transcode movies and music---**but much more importantly i want to process 10,000's of jpg's using imagemagick ** once i get this set up.

Some questions before I get started...
[LIST=1]
[*]Which distro would work best for this?
[*]What do you think the bottlenecks will be for this?
[*]Pros/Cons
[/LIST]

Is there A Better Solution?

Thanks in advance!!!!

---

### Post by jfwiedmayer on 2008-11-25
bump - I would love to do this but really need some help

---

### Post by Stochastic on 2008-11-25
Well the only knowledge I have on the subject was when I looked into setting up a cluster for audio processing.  I had much the same ideas as you, but in the end I was told that audio processing usually can't be divided up into autonomous task packages (to be distributed across the cluster appropriately) as most often the next sample depended upon the output of the last processed sample, so I wouldn't really get much benefit out of a cluster.  I don't know the inner workings of photo processing, but you may want to look into that.  Furthermore, the software that is run on clusters is usually optimized for this type of processing, so you may find Imagemagick to not utilize things as you are hoping.

In the end, you may find that this section of the forums doesn't have the right kind of people to answer your questions.  The Server section of the forums may yield more informed opinions.

As for the distro choice, look into ROCKS [www.rocksclusters.org](www.rocksclusters.org) it's red-hat based, but it seems to be the current favored cluster distro.  This could also lead to finding some other distros: [http://en.wikipedia.org/wiki/Category:Cluster_computing](http://en.wikipedia.org/wiki/Category:Cluster_computing)

I should warn that I looked into doing this about three years ago, so some of my findings might be incorrect by now.  Please let me know how things work out.

Edit: hmm, I just dug out an old linuxjournal magazine (sept 2006) that details a few different clustering methods.  Check out Condor [http://www.cs.wisc.edu/condor/](http://www.cs.wisc.edu/condor/) or some of these article links:
[http://www.linuxjournal.com/article/9828](http://www.linuxjournal.com/article/9828)
[www.linuxjournal.com/article/9135](www.linuxjournal.com/article/9135)
[http://www.linuxjournal.com/node/9058/print](http://www.linuxjournal.com/node/9058/print)
[www.linux.com/articles/56747](www.linux.com/articles/56747)
[www.linux.com/articles/49654](www.linux.com/articles/49654)
I really am just scratching the surface with these links.

---

### Post by rylleman on 2008-11-26
Perhaps it would be an easier solution to set up a render manager/queue tool? That way you have one server which distributes all images over the different clients. It should also work with audio/video.
one render manager is DrQueue ([http://drqueue.org/cwebsite/]("http://drqueue.org/cwebsite/")). It's supposed to be quite good and you can do customised render scripts to use it for any purpose.
It is however quite hard to setup, I haven't managed to get it running properly on my system...

---

