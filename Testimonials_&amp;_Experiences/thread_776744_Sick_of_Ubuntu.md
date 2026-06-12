---
title: "Sick of Ubuntu"
date: 2008-04-30
forum: Testimonials &amp; Experiences
---

### Post by explicit10 on 2008-04-30
Is there any way to get rid of Ubuntu and get back vista.. im sick of not being able to do anything because i cant get java to work and although some people have been trying to help nothing is working..:confused:

---

### Post by ebelog on 2008-04-30
1. Insert Vista install CD
2. Format drive
3. Install Windows

If you want to try to work out issues you have with Ubuntu, this is a good place. If you want to just complain about it and start a Windows vs. Linux war, then you should try to find a Windows forum where people may be more receptive to your views.

---

### Post by jcwmoore on 2008-04-30
sure you can get back to windows, but we need to know what set up you have... do you dual boot now? did you install over vista? and if so do you have a legal means of installing vista?  need some more information.

I looked at you java problems post, and my guess is that you don't have all the repositories enabled, but maybe you already looked into that

---

### Post by explicit10 on 2008-04-30
I Would rather be using Ubuntu.. I made a post so i could get help and out of 110+ views i had 2 people try to help... so if anyone can fix my java problem  im all for it.. but i have tryed everything..

---

### Post by explicit10 on 2008-04-30
> **jcwmoore said:**
> sure you can get back to windows, but we need to know what set up you have... do you dual boot now? did you install over vista? and if so do you have a legal means of installing vista?  need some more information.

I looked at you java problems post, and my guess is that you don't have all the repositories enabled, but maybe you already looked into that

All ive been getting is error after error.. is there anyway to completely reinstall ubuntu so that maybe some of these errors will be gone?

---

### Post by jcwmoore on 2008-04-30
> **explicit10 said:**
> All ive been getting is error after error.. is there anyway to completely reinstall ubuntu so that maybe some of these errors will be gone?

sure... pop the disk back in and do a fresh install, when you get done and reboot, enable the universe and multiverse repositories.  The Sun version of java, what you want to install, is not open source and therefore not available in from the default software repositories.  Sun java is located in the multiverse.

---

### Post by Sef on 2008-04-30
> All ive been getting is error after error.. is there anyway to completely reinstall ubuntu so that maybe some of these errors will be gone?

1) Could you provide a link to your post where you have the problems listed.   

2) Run the live cd and do you have any problems running Ubuntu on that?  Note: you settings will not saved on the live cd.

---

### Post by explicit10 on 2008-04-30
> **jcwmoore said:**
> sure... pop the disk back in and do a fresh install, when you get done and reboot, enable the universe and multiverse repositories.  The Sun version of java, what you want to install, is not open source and therefore not available in from the default software repositories.  Sun java is located in the multiverse.

How do i enable the universe and multiverse.. i think i was in the right place but i got anuther error.. I was in...System -- Admin -- Software sources.

---

### Post by explicit10 on 2008-04-30
[http://ubuntuforums.org/showthread.php?p=4848379#post4848379](http://ubuntuforums.org/showthread.php?p=4848379#post4848379)

---

### Post by jcwmoore on 2008-04-30
> **explicit10 said:**
> How do i enable the universe and multiverse.. i think i was in the right place but i got anuther error.. I was in...System -- Admin -- Software sources.

that is correct, just make sure all the boxes are checked and reload when you close out of that window.

what error?

---

### Post by explicit10 on 2008-04-30
Please follow the link i posted above for my other post, it has some of the errors i have gotten.

---

### Post by black3ug on 2008-04-30
Not to be insulting but that is the LAMEST question I've read in the forums. 

You have GOT to be flamebaiting.

But in case you REALLY are serious (and since UBUNTUers are such nice people), do what **ebelog** said. 

> 1. Insert Vista install CD
2. Format drive
3. Install Windows


---

### Post by jcwmoore on 2008-04-30
looks like you are hitting repositories that don't exist (at least not any more)

please post you're sources.list file by running the following command from a terminal...
```
gedit /etc/apt/sources.list
```
just copy and paste what's in that file

---

### Post by Jammerdelray on 2008-04-30
Insert windows cd, type mbr and it will restore the Vista Boot Loader.

---

### Post by explicit10 on 2008-04-30
> **jcwmoore said:**
> looks like you are hitting repositories that don't exist (at least not any more)

please post you're sources.list file by running the following command from a terminal...
```
gedit /etc/apt/sources.list
```
just copy and paste what's in that file


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) gutsy universe restricted main
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) gutsy multiverse
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) gutsy-security main restricted
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) gutsy-security universe
deb [http://gulus.usherbrooke.ca/ubuntu/](http://gulus.usherbrooke.ca/ubuntu/) gutsy-security multiverse
# deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main

---

### Post by explicit10 on 2008-04-30
> **black3ug said:**
> Not to be insulting but that is the LAMEST question I've read in the forums. 

You have GOT to be flamebaiting.

But in case you REALLY are serious (and since UBUNTUers are such nice people), do what **ebelog** said.

Accualy.. i am kinda screwed for getting the vista os back -_- i lost the cd.. so i have been trying to make this work..

---

### Post by jcwmoore on 2008-04-30
> **explicit10 said:**
> 
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted


this line has caught my attention.  when installing you were unable to hit the Canada repositories (I have seen this when I install without a network connection) I'm assuming you are in Canada, so the official repositories are what you see above, ca.archive.ubuntu.com.... i think you need to reload your sources list.

I will run this myself to verify it does work, wait a bit before trying it your self.

EDIT: I would recommend against this advice and i have removed it, it cause errors when I tried it
I would still suggest that you reload you sources because you are not using the official ubuntu servers.

---

### Post by jcwmoore on 2008-05-01
another idea, have you ran
```
sudo apt-get update
```
that will update you repositories, but you will get errors if the CD is not loaded.

---

### Post by azimuth on 2008-05-01
> **explicit10 said:**
> Accualy.. i am kinda screwed for getting the vista os back -_- i lost the cd.. so i have been trying to make this work..

After starting this thread with a title of "Sick of Ubuntu", this last post is funny. I don't mean to make light of your plight, but you have a true knack for satire. Now with that out of the way, just follow the advice the nice folks here have been giving you and everything will turn out fine. Saving people's posteriors is what they do best.

---

### Post by DMK62 on 2008-05-01
He's been trying for a few days to get things working and I think his level of frustration was peaking when he made this post. Myself and a couple other members are making progress in getting his issues resolved in his other post requesting technical assistance.

The University of Calgary and Canadian Main repositories are either down or under a heavy load. I had him change to gulus.usherbrooke.ca and those are working properly.

Dale

---

### Post by Riffer on 2008-05-01
He should go to "Main Server" instead of the canadian one.  I always had trouble with the canadain mirrors.

System > Administration >  Software sources ... in the box that is labeled "DownLoad From"

---

### Post by iSplicer on 2008-05-01
Its funny how these types of threads are really popular... lol

Anyway, I suggest you dont give up, there are many of us here that are willing to help you out. For free.

---

### Post by Riffer on 2008-05-01
Also folks if he has been trying to fix things and has been asking for help then please a little patience and sympathy.  He is allowed to vent, we've all been there.

On the same note if someone is ranting and hasn't tried to fix things or ask for help, feel free that person is fair game :guitar:

---

### Post by ShodanjoDM on 2008-05-01
+1 for the main server

I think it's a safe bet to include main server (archive.canonical.com) in the repository besides the nearest mirror.

---

### Post by DMK62 on 2008-05-01
I had him change to a fast canadian mirror. The Canadian Main can be slow and I have had some issues with it in the past. I recommended gulus.usherbrooke.ca as it is reliable and I never went under 800k with it even during the last week with Heron. Having package downloads timeout would have just made things more frustrating.

He has Java installed now and is working on a few other items.

Dale

---

