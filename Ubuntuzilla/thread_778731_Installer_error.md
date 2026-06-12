---
title: "Installer error"
date: 2008-05-02
forum: Ubuntuzilla
---

### Post by jfg69 on 2008-05-02
I have been receiving an update notice for Tbird yesterday and today. Running thru the process of gksudo thunderbird and checking for updates tells me there is NO update.

OK, on to the problem at hand. While fishing around for an answer to my Tbird update issue, I saw that a [Ubuntuzilla update]("http://sourceforge.net/project/showfiles.php?group_id=202789") was posted, so I decided to upgrade and dl'd the .deb. I am running a amdx64 version of [ubuntu based Ultimate Edition]("http://forumubuntusoftware.info/viewtopic.php?f=2&t=852"). The problem is that deb installer tells me that the version for amd64 is the wrong architecture.

```

jfg69@jfg69-desktop:~$ uname -m
i686
jfg69@jfg69-desktop:~$ ubuntuzilla.py --version
Ubuntuzilla version 4.4.7
Project homepage: http://ubuntuzilla.sourceforge.net/
jfg69@jfg69-desktop:~$ 


```

Any ideas?..

Thanks
j.

---

### Post by nanotube on 2008-05-02
> **jfg69 said:**
> I have been receiving an update notice for Tbird yesterday and today. Running thru the process of gksudo thunderbird and checking for updates tells me there is NO update.

hmm, maybe they haven't pushed it through to the update stream when you tried it... try it again? (it just worked for me)

> 
OK, on to the problem at hand. While fishing around for an answer to my Tbird update issue, I saw that a [Ubuntuzilla update]("http://sourceforge.net/project/showfiles.php?group_id=202789") was posted, so I decided to upgrade and dl'd the .deb. I am running a amdx64 version of [ubuntu based Ultimate Edition]("http://forumubuntusoftware.info/viewtopic.php?f=2&t=852"). The problem is that deb installer tells me that the version for amd64 is the wrong architecture.

```

jfg69@jfg69-desktop:~$ uname -m
i686
jfg69@jfg69-desktop:~$ ubuntuzilla.py --version
Ubuntuzilla version 4.4.7
Project homepage: http://ubuntuzilla.sourceforge.net/
jfg69@jfg69-desktop:~$ 


```

Any ideas?..

Thanks
j.

well, your --version output shows that you are running the latest version... 

but, your uname -m output seems to be the same as the 32bit hardware output (i686 shows up on my 32bit machine as well). i thought the amd64 uname-m is "x86_64", and this is what i'm checking for when doing the ubuntuzilla self-update... 

so, first, are you sure this is a 64bit edition, and second, if yes, then how do you know and how can you check? apparently uname -m is no longer a functional way to detect this.

what version of ubuntu are you running?

---

### Post by jfg69 on 2008-05-02
> **nanotube said:**
> hmm, maybe they haven't pushed it through to the update stream when you tried it... try it again? (it just worked for me)



well, your --version output shows that you are running the latest version... 

but, your uname -m output seems to be the same as the 32bit hardware output (i686 shows up on my 32bit machine as well). i thought the amd64 uname-m is "x86_64", and this is what i'm checking for when doing the ubuntuzilla self-update... 

so, first, are you sure this is a 64bit edition, and second, if yes, then how do you know and how can you check? apparently uname -m is no longer a functional way to detect this.

what version of ubuntu are you running?

OK, well- I have egg on my face here... I should not really do these things till I'm FULLY awake. :mad:

I am indeed running on my 32 bit install, I have a few different ones. I thought I was in the 64.. 

Thanks for the quick reply tho, and I'll mark this as solved.

j.

Quick question tho, when was your latest update/ creation of the deb? I installed this a while back, kinda odd that I have the latest version of the script.. then again, maybe I *did* upgrade it already, since my memory is apparently shot. #-o

---

### Post by nanotube on 2008-05-02
> **jfg69 said:**
> OK, well- I have egg on my face here... I should not really do these things till I'm FULLY awake. :mad:

I am indeed running on my 32 bit install, I have a few different ones. I thought I was in the 64.. 


heh heh... happens to all of us :)
> 
Quick question tho, when was your latest update/ creation of the deb? I installed this a while back, kinda odd that I have the latest version of the script.. then again, maybe I *did* upgrade it already, since my memory is apparently shot. #-o

ubuntuzilla updates itself automatically (checks for update every 24 hours). there's a cron job installed in 
/etc/cron.daily/ubuntuzillaupdatecron
that does that. 

so no, it's not your memory. :)

---

