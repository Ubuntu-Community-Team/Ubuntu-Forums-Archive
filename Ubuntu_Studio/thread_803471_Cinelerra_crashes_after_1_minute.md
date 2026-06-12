---
title: "Cinelerra crashes after 1 minute"
date: 2008-05-22
forum: Ubuntu Studio
---

### Post by SlappyPappy on 2008-05-22
I installed Cinelerra and imported a DV clip and blammo! It crashed after 1 minute.

Kdenlive lasts 4 minutes before it bellies up. 

I'm guessing that Ubuntu is not ready for video editing. Damn shame. I've been really impressed with what it can do up to this point. Clearly Mac and Windows have a lock on video editing at this point. Kdenlive is very feature rich and pretty intuitive in the way it works. Cinelerra from what little I saw of it is a bit confusing. 

I hope some developers out there are listening. An equivalent to iMovie on Linux would be a killer app!   :)

---

### Post by eye208 on 2008-05-28
> **SlappyPappy said:**
> I'm guessing that Ubuntu is not ready for video editing.
I'm guessing that you have not yet looked at Blender. ;)

---

### Post by cybercookie72 on 2008-05-28
um i think he is talking about video edit stuffs.... :KS not the 3d stuffs.. blender is sweet though

as for the DV stuff yeah there are a few things out there (ie... ones you talked about) but it seems to be a hit and miss... on one of my machines I can get cinelerra to work and the other its a crash city.  I have yet to find a reliable way to with my sony HD cam... mts file support is little scarce but hey... can't complain too much I get to make dvds for free... lol well besides the cost of the cam

---

### Post by eye208 on 2008-05-28
> **cybercookie72 said:**
> um i think he is talking about video edit stuffs.... :KS not the 3d stuffs..
I'm guessing that you have not yet looked at Blender either. ;)

---

### Post by ubundah001g on 2008-05-28
Read the manuals for Cinelerra on some settings that may help and some ways to use Cinelerra. There are several things that can make it crash, and one is running large video files, such as DV, that eat up a ton of your system memory. Does your system have enough RAM to do video editing, and does your system have a fast enough processor and good I/O bus throughput? If not, video editing can be an intensive overload on your system. Other than that, you might try Lives to see if it will edit the clip without crashing.

[http://cinelerra.org/docs.php](http://cinelerra.org/docs.php)

---

### Post by eye208 on 2008-05-28
> **ubundah001g said:**
> There are several things that can make it crash, and one is running large video files, such as DV, that eat up a ton of your system memory. Does your system have enough RAM to do video editing, and does your system have a fast enough processor and good I/O bus throughput? If not, video editing can be an intensive overload on your system.
Blender supports proxy editing to work around these resource bottlenecks.

---

### Post by keykero on 2008-05-28
> **eye208 said:**
> Blender supports proxy editing to work around these resource bottlenecks.

He wasn't asking about Blender though, was he?

---

### Post by cotcot on 2008-05-28
> **SlappyPappy said:**
> I installed Cinelerra and imported a DV clip and blammo! It crashed after 1 minute.

Kdenlive lasts 4 minutes before it bellies up. 

I'm guessing that Ubuntu is not ready for video editing. Damn shame. I've been really impressed with what it can do up to this point. Clearly Mac and Windows have a lock on video editing at this point. Kdenlive is very feature rich and pretty intuitive in the way it works. Cinelerra from what little I saw of it is a bit confusing. 

I hope some developers out there are listening. An equivalent to iMovie on Linux would be a killer app!   :)

Both apps work fine on my desktop. I compiled cinelerra myself. Then I checked the settings as described in the very good cinelerra manual. Kdenlive worked with the version from the repos.
I discovered recently the Blender Video Sequence Editor. It is easy to check it. The 2.46 version is out. There is only an issue with sound :
The solution is to place the variable SDL_AUDIODRIVER=alsa in /etc/environment, restart the computer and launch blender.
Success !

---

### Post by eye208 on 2008-05-29
> **cotcot said:**
> The 2.46 version is out. There is only an issue with sound :
The solution is to place the variable SDL_AUDIODRIVER=alsa in /etc/environment, restart the computer and launch blender.
Success !
2.46 does not require SDL_AUDIODRIVER any more. If the variable is not set, ALSA will be used by default.

> **keykero said:**
> He wasn't asking about Blender though, was he?
He was asking about a feature-rich video editor that doesn't crash all the time like Cinelerra and Kdenlive. Correct me if I'm wrong, but currently Blender is the only OSS video editor on Linux that got past the experimental stage and proved its usefulness in real-world projects.

---

