---
title: "Add Repository Problem"
date: 2007-03-31
forum: Repositories &amp; Backports
---

### Post by BeatnikBandit on 2007-03-31
I Just revived my old computer and used Edgy, I am not new to ubuntu i have used badger and dapper with no problem. I added the extra repository's through synaptic which i am familiar with but by no means a pro. It tells me the repository's have been added but when i look for my programs i would like they don't show up. I haven't used a Linux system in about a year i would say, My Linux programming skills are very limited but i was able to do what i wanted before but now my limited knowledge is rusty and i am attempting on using the newest version.... maybe thats not smart but all i need help with is to get my repository's straight i haven't messed with it very much and i installed yesterday so after knowing my circumstances i ask your help on how to fix my repository's? I want to add all the ubuntu repository's and if anyone knows a repository that i can get the drivers for nvidia 3d cards i would like to do that too. to me this doesn't seem like it should be a problem as i never needed help before. but anything is appreciated i know this should be easy maybe ive become a tard lol. After i get the repository's squared away (all i need is unrar) maybe someone can give me some tips on nvidia 3d drivers i have a geforce 3 ti 300 128 mb. So in all if anyone can help me just get my repository's going correctly, (one reason i don't think they are set is because I've been trying to install unrar and rar using this command after adding the repository's in synaptic "apt-get install rar unrar" and i get an unavailable message) maybe i can get some help with rar and getting my 3d drivers working. i would also like to install wine but again its unavailable even though synaptic says i have all repository's enabled. I'm sorry for this convoluted post with terrible grammar but I'm franticly trying to get this going while i type this so thank you in advance for even reading this and much love to anyone who replies and tries to help. 
:-({|=  I suck lol

---

### Post by eljalill on 2007-03-31
The problem might be, that you have to update the synaptics or apt-get archives after adding repositories.
Either do ```
 apt-get update
```
or click on reload in synaptics.

If this doesn't help you might want to have a look at your souces.list, instead of doin it in synaptics. Check, whether all the repositories you want to have are indeed in there (/etc/apt/sources.list) and add them if not.

---

### Post by BeatnikBandit on 2007-03-31
I think that is the thing that i either forgot or the previous versions updated automatically when you add the new repository. so i believe that was it, before you posted i found and used this tutorial to do the same thing but i chose to use the repository's that were listed from the uk instead of the us i don't know if there is a point but the tutorials said it had the nvidia drivers (i don't know)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

### Post by BeatnikBandit on 2007-03-31
i decided to stay with the gb server for now the how to wiki said it was different but in what way i haven't found out yet

---

