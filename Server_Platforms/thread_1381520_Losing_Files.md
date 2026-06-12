---
title: "Losing Files"
date: 2010-01-14
forum: Server Platforms
---

### Post by Skylerzio on 2010-01-14
I have 64-bit ubuntu 9.10 server edition running in a media server for my house.  But over the last few months I've discovered that its loosing files!  Its not all files, Just music.  It will lose anywhere from about half an album the every song in the folder, leaving the artwork if it was in there.  

At first i thought It was iTunes reorganizing my files, but thats not the case, as i've looked around for them, and told iTunes pretty much to stop messing with my file locations.  whats going on?  

My boss who's pretty Linux savvy says that 9.10 is really buggy.  I've tried doing updates (sudo apt-get update/upgrade) but its still losing music.

Please help!

Any other information that you may need, please ask for/explain how i can get it to you.  I'm not that good with linux, my only experience being setting up my media server.

Additional info: Installed on server is Deluge, Samba, and maybe one other thing that i can't remember.  with a 1.5Tb HDD and 1gb of Ram

---

### Post by Skylerzio on 2010-01-19
Cheap Bump,  I see a lot of people looking...

---

### Post by Grenage on 2010-01-19
I've never seen a case in either Windows or Linux where the OS was randomly removing files.  If you don't have some funky management scripts in there, I would suspect whatever applications were accessing them.

Is itunes via wine or the network?

---

### Post by Skylerzio on 2010-01-29
iTunes is accessing across the network from Windows XP machines.  no special scripts that I have installed.

---

### Post by BobVila on 2010-01-29
> **Skylerzio said:**
> iTunes is accessing across the network from Windows XP machines.  no special scripts that I have installed.

Have you checked messages to see if the hdd is crapping out?

I'm not super familiar with iTunes' auto-management stuff, 'cause I always shut if off, but is it, by chance, moving files from the server onto your local machine in the iTunes folder buried in mydocs?

---

### Post by Skylerzio on 2010-02-01
pretty sure its not iTunes, i checked the local iTunes folder and theres not anything there, i even told iTunes to default its music location to the server directory, and have turned off the auto management as well.

But how would i check for messages on my HDD?  i hope its not going bad already, i just got it about 6 months ago!

---

### Post by BobVila on 2010-02-02
With smartmontools, you can get SMART to check the health of the drive. You may need to install it first.

[http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu](http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu)

---

### Post by Skylerzio on 2010-02-04
hmm,  Well it looks okay.

if you need the actual results, I can get them to you by the weekend (I checked it before I left for work this morning)

Anything else I can try?

---

### Post by doas777 on 2010-02-04
I kinda suspect the network link/share, rather than that files are actually disappearing, but when using itunes all conventional logic is out the window.

---

### Post by BobVila on 2010-02-05
> **doas777 said:**
> I kinda suspect the network link/share, rather than that files are actually disappearing, but when using itunes all conventional logic is out the window.

Amen to that. 

Skylerzio, the smart output wouldn't hurt,  but it usually makes things pretty obvious when there's a problem. 

I assume you've ssh'd into the server and checked the output of ls on one or more of the directories in question just to make sure the data was gone, no? Just want to make sure windows isn't screwing with things and making the files hidden or some nonsense like that.

---

### Post by Skylerzio on 2010-02-12
"Checked the output of ls"?

is that part of the SMART HDD test? I'll have to run it again and look, i was only looking for something that blatently said their was an error.  Didn't really know what else I was looking for.

By ssh do you mean something like puTTy?  Thats what I'm using to get into it.

and LoL to the iTunes comment,  the only reason I even have it is the Mrs. loves her iPod.

---

