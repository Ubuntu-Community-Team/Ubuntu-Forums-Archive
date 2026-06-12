---
title: "server clustering"
date: 2010-11-18
forum: Server Platforms
---

### Post by risen75 on 2010-11-18
Ok guys/gals, I'm trying to figure out how to setup a small cluster.  Basically a rendering/encoding farm (I'm sick of 2-3 encoding and longer rendering times and i have two server boxes just sitting here doing nothing).  Now I'm having trouble even finding information on how to go about setting it up. 

I've come across SLURM.. but i'm not sure if this is the right setup to use (or even how to set it up for that matter) and I'm hoping that someone out there has either done this already with ubuntu or even with another distro, to point me in the right direction. And yes I have googled the crap out of this issue to no avail.  

If anyone has done this before please let me know and point me in the right direction. 

Thank you everybody in advance for your help and support.

---

### Post by reddevil2064 on 2010-11-19
Googling "linux cluster" got me this on the first page [Render Cluster]("http://helmer.sfe.se/"). Most of the configuring is finding a multi-threaded renderer. [This]("http://www.drqueue.org/cwebsite/about_drqueue.php") is the software he used to achieve the rendering farm. I would suggest googling rendering farm as that returned more hits pertinent to what you want. Also keep in mind the software you are wanting to use would need to be supported by the cluster. I have a little experience setting up a compute cluster (as in, in my room) and getting it configured was simple enough (using cluster knoppix) but getting any software to actually utilize the available horsepower was a different story.

---

### Post by lukeiamyourfather on 2010-11-19
Most rendering farms and transcoding farms will have one task on one machine, but working on a lot of tasks overall. If you're looking to speed up rendering of a single frame or transcoding of a single video then the best option would be to upgrade the workstation rather than try and distribute a single frame and/or a single video over multiple nodes.

---

### Post by risen75 on 2010-11-19
Yeah i've found that one (after posting) I haven't had the time to read through everything on it... however i did find DVD::RIP has a cluster setup for doing the exact thing i want to do... now the fun part... setting up ssh to not need a password so that i can send the commands with it :) oh well.. 

Thanks for your replies guys..

---

### Post by risen75 on 2010-11-22
Ok.. so after getting it half setup... i realized that this program wouldn't do what i need it to do... 

soo... any more help would be great :)

I mean there's got to be a bunch of us out here who have 10-15 other boxes laying around doing nothing.. shouldn't we be doing something with these damn things?  :)

so any other ideas for setting up a cluster would be great..

I've found this [http://www.linux.com/community/blogs/Building-a-Beowulf-Cluster-in-just-13-steps-.html]("http://www.linux.com/community/blogs/Building-a-Beowulf-Cluster-in-just-13-steps-.html")

but it's kind of outdated (it's how to set it up with 8.10 and well.. quite frankly one of the programs listed in there i can't find)

---

### Post by lukeiamyourfather on 2010-11-23
> **risen75 said:**
> 
I mean there's got to be a bunch of us out here who have 10-15 other boxes laying around doing nothing.. shouldn't we be doing something with these damn things?  :)


What ***exactly*** are you trying to speed up? Most computing tasks are not easily done in parallel. Or if they are it takes a lot of communication between the threads so the parallel operations scale well only to local processors (not networked machines). Otherwise the network communication takes more time than the extra processing would benefit the overall performance.

To work around the huge overhead of the networking there are specialized low latency networks like InfiniBand (used in supercomputers). This comes at a huge cost though and is very cumbersome to develop for (compared to a single machine). So long story short, you won't be able to use those extra machines for much. There's no silver bullet to make a bunch of old hardware act like a faster and newer machine.

Some tasks that are parallel friendly can be distributed across the older machines with a queue manager but not many tasks will fit that model. Which leads me back to the first question. What are you trying to do, because that will determine if you are able to take advantage of the older machines or not.

---

### Post by risen75 on 2010-11-25
What I'd like to do is speed up both my 3d rendering and my video encoding.  and what i mean for the video encoding is i have a bunch of avi's that i'd like to put into dvd's and right now.. the encoding is taking about 3 hours to do (yes i'm putting more on there than is supposed to fit so it's going on as lower quality) and rendering 3d animations that i've done (those take a day or two right now) 
So what i figure is that the 3d rendering and the video encoding are pretty much the same thing when it comes down to number crunching (aka one frame at a time) so it shouldn't be too hard to do something like the guy at [http://helmer.sfe.se/]("http://helmer.sfe.se/") did... now i'm not going to setup a single big box like he did.. but i do have a few old p4's laying around and that's what i'm trying to do...

though he's not doing video encoding... i don't see that being much if any different than the 3d rendering.... 

so yeah.. would dr queue be the answer? from what i understand of the program... it breaks up the job into it's different frames and sends one frame to each core and just does it over and over again until the whole job is done... if i'm understanding it right.. that would be the way to go... (now that i'm completely exhausted and that's when i do my best thinking... but i know i have more reading to do on it) i'm just trying to figure it all out 

(that and the experience of knowing howto and actually doing it are things i enjoy doing.. so it's really half for practical and half for academic reasons....)

Pardon the rambling and half-incoherent thoughts... it was time for bed about 6 hours ago......

---

### Post by lukeiamyourfather on 2010-11-28
> **risen75 said:**
> What I'd like to do is speed up both my 3d rendering and my video encoding.  and what i mean for the video encoding is i have a bunch of avi's that i'd like to put into dvd's and right now.. the encoding is taking about 3 hours to do (yes i'm putting more on there than is supposed to fit so it's going on as lower quality) and rendering 3d animations that i've done (those take a day or two right now) 
So what i figure is that the 3d rendering and the video encoding are pretty much the same thing when it comes down to number crunching (aka one frame at a time) so it shouldn't be too hard to do something like the guy at [http://helmer.sfe.se/]("http://helmer.sfe.se/") did... now i'm not going to setup a single big box like he did.. but i do have a few old p4's laying around and that's what i'm trying to do...

though he's not doing video encoding... i don't see that being much if any different than the 3d rendering.... 


Videos are typically encoded one stream at a time instead of one frame at a time like 3D renders. Though some encoders use only one processor so you could speed that up just by running multiple encoders on one system. Or running one stream per core per system.

If the 3D rendered frames are too complex then they will run out of memory on the older P4 systems. Even if they don't run out of memory a $200 Phenom II six core would be faster than ten of those P4 systems. All of those older systems will use a lot of power which will ad up very quickly on the electric bill compared to a single newer system (approximately 2000 watts versus 200 watts).

> **risen75 said:**
> 
so yeah.. would dr queue be the answer? from what i understand of the program... it breaks up the job into it's different frames and sends one frame to each core and just does it over and over again until the whole job is done... if i'm understanding it right.. that would be the way to go... (now that i'm completely exhausted and that's when i do my best thinking... but i know i have more reading to do on it) i'm just trying to figure it all out 


A few months ago I would've said Sun Grid Engine, which became Oracle Grid Engine, which is no longer open source (don't you love Oracle?). DrQueue is a decent option. A queue manager is broken down like this. The highest level of organization is a job which contains tasks. The job might be to render a 3D sequence of 100 frames. The tasks within the job will be for each frame. Frame 1 is a task within the job, frame 2 is another task within the same job, and so on. Each task is a command line sent to the shell of the system that gets run. You'll have to setup the structure for those commands plus the script/utility to populate the jobs and tasks. Depending on what you're using there might already be tools to submit jobs to DrQueue out there.

Back to the bit about the electricity use. The older P4 systems are free but will cost substantially more to run. If you will be using this a lot you should calculate how long it will take for those systems to use $500 worth of electricity. At that point you could've bought a newer machine that is faster and more efficient instead. Like I said before, there's no silver bullet that will allow you to use old computing power. Even if you get it working technically it will be very inefficient compared to the newer machines.

---

### Post by risen75 on 2010-11-28
And there's the key.. buying a new system is out of my reach right now (as i DJ one night a week and have two kids) but the old systems that i have is the option to go with as i don't pay the electric bill... (i know it's kinda lame and makes a few people jealous, but hey it's the situation i'm in) and besides.. when i can get the $$ for the better systems... hrmm.. adding on to the cluster anyone? 

but the real question i have is if it is possible to use that for say the video encoding? just for example....

6 episodes of a TV show = 4.5 hours of video
1 dvd = up to 4 hours of video (doesn't ever fit right at that.. but hypothetically)
encoding to fit with current system 2.5-4 hours (using DeVede) 

now yes i know that upgrading would help.. but.. when the systems that would be going with it have cores that actually run faster than the dual-core i have right now with the same amount of RAM per core.. i figure that it should (in theory not taking into account the bottle neck of the network) cut the encoding time down exponentially for each core.. (yes there is a point where it's retarded and doesn't make enough of a difference) but if i could shave off say 40 mins to an hour with the three extra boxes that i have.... it would be worth it to me just in the fact of knowing how to do it... (thats more about what i want to do.. is figure out how to setup something like this, plus actually using it...)

and the reason i can't seem to figure out why it shouldn't work.. is because DeVede.. is a gui front end for some encoding tools that already run multi threaded (sorry can't remember what packages it uses or i'd post it). so that says to me that it should be possible without much hassle if i could get the system to see all of the boxes as a single system (oh yeah the old single system image idea)

i know that it's "possible" it's just figuring out how to do it and send it back and forth between systems.. and seeing as how i'm not a programmer i don't have a clue where to start writing my own interface for it... 

and besides.. i already have one of the boxes i'm going to use setup running as a web/rsync/file server and 90% of the time it's doing absolutely nothing.. but it's got to be turned on and running so the extra power it would take shouldn't be too much more than it is now.. (yes i know extra load = extra power consumption)  

wow i just noticed how much i ramble on and on on here... please pardon it and if you have any ideas.. let me know....

---

### Post by lukeiamyourfather on 2010-11-29
> **risen75 said:**
> 
now yes i know that upgrading would help.. but.. when the systems that would be going with it have cores that actually run faster than the dual-core i have right now with the same amount of RAM per core.. i figure that it should (in theory not taking into account the bottle neck of the network) cut the encoding time down exponentially for each core.. (yes there is a point where it's retarded and doesn't make enough of a difference) but if i could shave off say 40 mins to an hour with the three extra boxes that i have.... it would be worth it to me just in the fact of knowing how to do it... (thats more about what i want to do.. is figure out how to setup something like this, plus actually using it...)


If you encode each stream on each machine separate then yeah, there could be some performance improvements. Though processor clock speed is not an indication of actual performance. Note in order to use for example five machines you'll need at least five video streams to encode.

> **risen75 said:**
> 
i know that it's "possible" it's just figuring out how to do it and send it back and forth between systems.. and seeing as how i'm not a programmer i don't have a clue where to start writing my own interface for it... 


That is what a queue manager is for. Look at the documentation for a queue manager as to how to set it up. Though if your goal is saving an hour or two on encoding you might find that setting up a queue manager is a waste of your time because it might take hundreds of hours to learn what you need to learn and set everything up.  

> **risen75 said:**
> 
wow i just noticed how much i ramble on and on on here... please pardon it and if you have any ideas.. let me know....

I feel like a broken record here. There's no silver bullet, no quick answer, no easy solution. You're looking for a ghost. To setup a cluster it will take a lot of time and effort and in your situation you won't benefit that much from it considering an upgraded workstation would outperform the entire cluster and would be easier to setup (regardless of who pays for the electricity).

---

### Post by risen75 on 2010-11-29
ok so you didn't read the part i put in there about the fact that 90%of this is just that i want to figure out how to do it? i'm employed one day a week and i'm running out of things to do!!! this is something to do.. i'm just looking for some help with it.

---

### Post by lukeiamyourfather on 2010-11-29
> **risen75 said:**
> ok so you didn't read the part i put in there about the fact that 90%of this is just that i want to figure out how to do it? i'm employed one day a week and i'm running out of things to do!!! this is something to do.. i'm just looking for some help with it.

[QUOTE=lukeiamyourfather]That is what a queue manager is for. Look at the documentation for a queue manager as to how to set it up.
[/QUOTE]

Take some initiative. :roll:

[https://ssl.drqueue.org/redmine/projects/drqueue/wiki/Documentation](https://ssl.drqueue.org/redmine/projects/drqueue/wiki/Documentation)

---

