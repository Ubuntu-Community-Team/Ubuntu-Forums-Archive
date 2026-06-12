---
title: "beowulf cluster server"
date: 2005-05-11
forum: Server Platforms
---

### Post by WildTangent on 2005-05-11
my school will be getting rid of about 60 old computers, i hope to get at least 5 of them (i have contacts in the school, my aunt is the librarian)

here are the specs:
Manufacturer: Seanix
CPU: Celeron 600 mhz (not sure what socket, ive never opened one of these computers up)
RAM: not sure exactly, best guess 128 MB
HDD: again, not sure, best guess 10-20 GB
all have graphics and network cards

one project ive always wanted to attempt is to make a beowulf type cluster server, and id like to use ubuntu to do it. being the linux n00b that i am, i do not know much about how to do this, other than the physical arrangement of the computers (one server, usually behind a firewall controlling multiple nodes). if anyone can provide me with helpful advice (other than "dont try it", im very determined ;) ) or websites. once again, i am a n00b, i dont know how to modify my kernel are complex stuff like that, so if thats involved, ill need to be told how to do it. as long as its only command line things i need to do, i should be fine :)

as for the hardware, i am planning on using an old P1 200 mhz box for the firewall, and i will be upgrading the CPU in the server to a P3, add more memory, and a bigger hard drive

**EDIT:** OK, im pretty much completely changing the plan. i am now going to use openMosix for the load sharing. i havent read much about it, but im reading a large article with how-tos and all that jazz. ill post here if i need more help :)

any help will be greatly appreciated.

-Wild

---

### Post by WildTangent on 2005-05-11
reading this article, i come to the conclusion that all i need to do is apt-get install openmosix to get the software, but how do i use it?

-Wild

---

### Post by dewey on 2005-05-11
Clusters can be pretty hardcore, but the fact that you're using similar computers makes it much easier.  Read some of this article, I know it's for gentoo, but it's openmosix, and there may be some usefull information.
[http://www.gentoo.org/doc/en/openmosix-howto.xml](http://www.gentoo.org/doc/en/openmosix-howto.xml)

Edit:  Here's another gentoo article on HPC (High Powered Computing) or clustering.
[http://www.gentoo.org/doc/en/hpc-howto.xml](http://www.gentoo.org/doc/en/hpc-howto.xml)

---

### Post by rich on 2005-05-12
I know that you know, but I'm going to say it anyway.


Why ?


If there isn't a task, how will you know that it's worked ? Putting the enourmous complication of clustering to one side, I think that what you need are some metrics.

For example,

You decide to use an mp3 encoding or other  intensive app. You run it on one box and it takes 50 minutes. You run it on a cluster of 5 identical boxes and it takes 10 minutes. Have you "won" ? What if it takes 11 mins, or 9 ?

Clusters are fairly heavy salad because they are used for heavy tasks. You need to have a task

(a) to give it some point
(b) to know if it's worked




still, enjoy.


Rich

---

### Post by dataw0lf on 2005-05-12
[QUOTE=rich]I know that you know, but I'm going to say it anyway.


Why ?


If there isn't a task, how will you know that it's worked ? Putting the enourmous complication of clustering to one side, I think that what you need are some metrics.

For example,

You decide to use an mp3 encoding or other  intensive app. You run it on one box and it takes 50 minutes. You run it on a cluster of 5 identical boxes and it takes 10 minutes. Have you "won" ? What if it takes 11 mins, or 9 ?

Clusters are fairly heavy salad because they are used for heavy tasks. You need to have a task

(a) to give it some point
(b) to know if it's worked




still, enjoy.


Rich[/QUOTE]


Um...

How about the pursuit of knowledge?  Curiousity?  Or just plain coolness factor?  He asked specifically for people not to advise against it, so I'm curious as to why you still decided to post.  You CAN ensure it worked with a variety of diagnostic tools.  Now onto the main topic.

I've heard of OpenMosix being implemented on Ubuntu.  I've set it up on Debian machines before, and it wasn't as hard as some might lead you to believe.   Just ensure that you apply the correct OpenMosix patch, and you're probably going to become very adept at tweaking kernel configs.  [Here](http://episteme.arstechnica.com/eve/ubb.x/a/tpc/f/96509133/m/692005320731/r/858008072731) 's a link to an outside forum thread that discusses Ubuntu + OpenMosix.

---

### Post by WildTangent on 2005-05-12
thanks for the replies so far guys. as for a task, i have many many gigabytes of WMA and OOG audio files that i want to re-encode to MP3 if i can do it in even half the time id be happy, because ive used new knowledge to accomplish something. theres no better feeling than that. (with your clothes on anyway)

-Wild

---

### Post by dewey on 2005-05-14
Be sure to tell us how it works out, an Ubuntu cluster would be a pretty interesting thing.

---

### Post by sciurus on 2005-05-19
If your new to Linux and new to clustering, you should take advantage of a toolkit such as [ROCKS](http://www.rocksclusters.org/)  or [OSCAR](https://oscar.openclustergroup.org/) and get a good book like O'Reilly's [High Performance Linux Clusters](http://www.oreilly.com/catalog/highperlinuxc/). ROCKS is simpler to set up, but OSCAR makes it easier for you to use openMosix. I believe there's an ongoing OSCAR port to Debian.

---

### Post by jkndrkn on 2005-06-14
Hi, I've lately considered possibly building a cluster using ubuntu as well. Did you ever start building your own? If so, how is it going?

Thanks.

---

### Post by LordHunter317 on 2005-06-14
First off, don't use your cluster for converting lossly audio to another format.  The output will be crap because the input is crap (in a relative sense).  GIGO and all that.

Second off, MP3 encoding cannot be parallelized without a serious loss of quality, so using a cluster tradtionally is out for this task. 

You could treat your cluster as a grid though and do it that way... where all the nodes are essentially working independent problems.

---

### Post by nexuslite on 2005-12-13
OK I have done a beowulf with slack its not that involved

 you get ssh setup so you can secure shell between computers without passwords requires making an authorized_key file pasting all the keys from all the systems into it

next you get all the time synced up easy with ubuntu because it does it allready off of the main server 

then you compile the beowulf libraries maybe ubuntu has this already compiled i dont know 

and then you compile a test program the tells you if your computers are working as a beowulf 

I just started working on a 2 computer beowulf setup a few minutes ago i have 1 account secure shelling without passwords but i need to make a global authorized key file so all accounts automaticly sync up I will try and post more later on how i got it all working if i do

---

### Post by WildTangent on 2005-12-15
Woah....blast from the past...

Well, I suppose I owe an update:
I never did go through with it, as I wasn't able to get the computers. Oh well. Also...the applications for a cluster are rather limited for myself.

-Wild

---

### Post by SnEptUne on 2006-03-01
[QUOTE=LordHunter317]First off, don't use your cluster for converting lossly audio to another format.  The output will be crap because the input is crap (in a relative sense).  GIGO and all that.

Second off, MP3 encoding cannot be parallelized without a serious loss of quality, so using a cluster tradtionally is out for this task. 

You could treat your cluster as a grid though and do it that way... where all the nodes are essentially working independent problems.[/QUOTE]

I don't understand how clustering audio encoding will affect the audio quality.  If that's the case, the cpus must be executing instructions incorrectly if it is in a clustering?  I don't really understand, could you elabourate?

---

### Post by atoponce on 2006-03-05
I'm going to bump this thread, instead of opening a new one.

I am interested in HPC, and would like to know what tools I need to get an OpenMosix cluster up an running.  But before I even choose OpenMosix, I am also considering Beowulf.

Basically, I have heard that OpenMosix runs at the kernel level, and apps don't need to be modified to take advantage of the cluster.  I have heard apps in Beowulf clusters do need to be modified.  If this is the case, then I am interested in OpenMosix.

Can someone help me?  I am new to HPC, but would love to get a cluster up and running using Ubuntu on two nodes.

Thanks.

---

### Post by Hentai_Jeff on 2006-05-11
I'm also intrested in this and was wondering the right procedure for the nodes, is it ok to have one computer use the GUI while the rest use server?

---

### Post by erikpiper on 2006-07-26
Well... I am intersted too...

BUMPIDY!

---

### Post by harisund on 2006-07-26
Personally, I would suggest you try out before hand a regular cluster linux distribution (such as ROCKS or something). Ubuntu doesn't have (yet) that feature. 

Besides how do you intend to parallelize your code? Using MPI or something?

---

### Post by LordHunter317 on 2006-07-27
> **SnEptUne said:**
> I don't understand how clustering audio encoding will affect the audio quality.MP3 encoding is serial in nature: information from the previously encoding frame is needed to encode the next frame.  Not having this data effects output quality.

> If that's the case, the cpus must be executing instructions incorrectly if it is in a clustering?Nope.  Serial dependencies exist all the time.  HEre's a simple example:```
a = 3 + x;
y = 3 + a;
```You can't execute those instructions simulatenously.  I can't solve for 'y' until I know what 'a' is.

---

### Post by makhand on 2006-07-31
I'd also like to know how to do this. I would prefer a setup where I dont have to modify any of my code, but just throw stuff at the cluster and have it do it. I have more than enough genuine use for it. I do signal/video/image processing for my research. There are things that I run that take up to a week to finish. Cutting that time would be fantastic.

---

### Post by rengolin on 2006-08-11
Hi Wild,

I'm building a Beowulf cluster with Ubuntu 6.06 with 5 nodes (4+1), maybe we can share experiences. 

This is the cluster:
[http://www.systemcall.com.br/MiddleEarth/](http://www.systemcall.com.br/MiddleEarth/)

And this where I'll post my progress:
[http://rengolin.homelinux.net/rengolin/](http://rengolin.homelinux.net/rengolin/)

---

