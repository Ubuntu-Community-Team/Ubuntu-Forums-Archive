---
title: "Cinelerra-CV will not make Ubuntu/Ubuntu Studio-Feisty"
date: 2007-02-14
forum: The Cafe
---

### Post by MetalMusicAddict on 2007-02-14
Due to _many_ issues [Cinelerra-CV]("http://cvs.cinelerra.org/") will not be able to make the Feisty Ubuntu/[Ubuntu Studio]("http://ubuntustudio.org/") release cycle.

This has been a major blow to the Ubuntu Studio team but there's just too much to work out thats beyond our control atm.

Also, once we do work things out it might end up in Multiverse meaning Ubuntu Studio will not be able to ship it.

Sad day.

---

### Post by BarfBag on 2007-02-14
By no means am I interested in video editing, but the tools have always intrigued me.  Is this based on Cine Paint?

---

### Post by Polygon on 2007-02-14
> Also, once we do work things out it might end up in Multiverse meaning Ubuntu Studio will not be able to ship it.

why not?

---

### Post by maruchan on 2007-02-14
>Is this based on Cine Paint?

Nope, it's a completely different software package. Cinepaint was based on GIMP originally, I believe, but now it's going through a major rewrite. 

Cinelerra's name just sounds similar, that's all. :)

---

### Post by MetalMusicAddict on 2007-02-14
> **Polygon said:**
> why not?

Because its where non-free things go. Like some codecs.

---

### Post by jcconnor on 2007-02-15
Actually, I wonder if the question was why won't it make it?

I'm intrigued by this too.  I use Sony software on a dual boot Win partition on my machine but was interested in using Cinelerra because of the Linux support (and OSS).  I haven't installed it yet but was wondering if there are major bugs in there that would make me want to hold off on the installation a bit??  The 'Studio" version looked very interesting but without the video editor would kinda be a bust.

So, what's the skinny on that??

John

---

### Post by MetalMusicAddict on 2007-02-16
We will be replacing Cinelerra with LiVES for now.

The issue with Cinelerra is its licenses. The main license file states that everything is GPL but the program uses things which clearly are not. ie: MS fonts.

Thats just the start though. We have to do a full review of 3000 (maybe more) some odd files. It takes time. We want to do it right and not rush it.

---

### Post by DoctorMO on 2007-02-16
It's good to see you guys conducting a popper review and I'm sure the CV will remove any of these problems in future versions.

To be honest it's about time there was a CV version, it should have happened years ago, the original developer is not a very friendly bloke to post patches to and his insistence on not updating the graphics from the current pathetic state is inane.

---

### Post by MetalMusicAddict on 2007-02-16
> **DoctorMO said:**
> It's good to see you guys conducting a popper review and I'm sure the CV will remove any of these problems in future versions.
Its a massive pain. Im unsure though if our changes will be accepted in the CV version. I think our version will be a fork. I just dont know.
> To be honest it's about time there was a CV version, it should have happened years ago,
The -CV version is a "friendly fork" but it really needs to clean things up.
> the original developer is not a very friendly bloke to post patches to
No. He isnt. He told us to go get Shuttleworth another space mission.
> and his insistence on not updating the graphics from the current pathetic state is inane.
I think that is in the name of stability.

---

### Post by tatau on 2007-02-19
That is sad news. I was really looking forward to giving Ubuntu Studio a real "go" and, admittedly, cinelerra was the main draw card. However, the other apps like gimp, blender, rosegarden? are more than enough reason to trial it out.

---

### Post by BOBSONATOR on 2007-02-19
I am a pretty advanced user with Vegas, and it is a large reason why i am currently dualbooting feisty/xp. 

Do you think this will be able to cope with my vegas skills well?

---

### Post by P_Badger on 2007-02-20
Lives certainly looks better than Cinerella, but how is it stability-wise? I've never been able to get it working properly, myself.

---

### Post by MetalMusicAddict on 2007-02-20
> **BOBSONATOR said:**
> I am a pretty advanced user with Vegas, and it is a large reason why i am currently dualbooting feisty/xp. 

Do you think this will be able to cope with my vegas skills well?
I would tend to give Vegas the edge here but I havent really got to dive into Cinelerra with all the work on the project itself lately. :)
> **P_Badger said:**
> Lives certainly looks better than Cinerella, but how is it stability-wise? I've never been able to get it working properly, myself.
The thing that really sucks is that we are forced to go with [PiTiVi]("http://pitivi.sourceforge.net/") now as LiVES has a mplayer dependency and throws it into Multiverse. :(

So **Officially** [PiTiVi]("http://pitivi.sourceforge.net/") is going to replace Cinelerra-CV as the NVE in Ubuntu Studio.

God. You guys dont even know what a mess this 1 aspect has been.

---

### Post by eriqk on 2007-02-20
Cinelerra is a bit tempramental. I have problems playing back DV files with it- They load OK, and play back perfectly the first time, but after reopening the program all that plays is sound.

I'm not too familiar with Lives and PiTiVi, but isn't KDEnlive an option, otherwise? Or is it too KDE centric, what with Ubuntu Studio being Gnome based?

Groet, Erik

---

### Post by P_Badger on 2007-02-20
> **MetalMusicAddict said:**
> I would tend to give Vegas the edge here but I havent really got to dive into Cinelerra with all the work on the project itself lately. :)

The thing that really sucks is that we are forced to go with [PiTiVi]("http://pitivi.sourceforge.net/") now as LiVES has a mplayer dependency and throws it into Multiverse. :(

So **Officially** [PiTiVi]("http://pitivi.sourceforge.net/") is going to replace Cinelerra-CV as the NVE in Ubuntu Studio.

God. You guys dont even know what a mess this 1 aspect has been.

Aye, with all the searching I've done looking for good open-source, and otherwise, NVE's, I can sympathize a bit. But yeah, is Kdenlive an option? So far it's the best open-source nve I've found.

---

### Post by MetalMusicAddict on 2007-02-20
> **P_Badger said:**
> Aye, with all the searching I've done looking for good open-source, and otherwise, NVE's, I can sympathize a bit. But yeah, is Kdenlive an option? So far it's the best open-source nve I've found.
We are going with PiTiVi because its currently in the Ubuntu-Feisty repos and Kdenlive isnt. Its slightly a Gnome integration thing but more so a time based decision as freeze is in 2 days and we simply dont have time for a new package.

---

### Post by justin whitaker on 2007-02-20
You know, I'm just getting into this, but it looks like you guys are doing the right thing.

---

### Post by MetalMusicAddict on 2007-02-20
Now also dont let this announcement lead anyone to believe that we will stop work on Cinelerra-CV. It simply means it will not make this release and will go into Feisty+1.

---

### Post by eriqk on 2007-02-20
Roger that. Thanks for the hard work by the way. Looking forward to rocking the Studio come April.

Groet, Erik

---

