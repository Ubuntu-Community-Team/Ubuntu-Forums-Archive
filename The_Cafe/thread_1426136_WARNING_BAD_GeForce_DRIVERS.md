---
title: "WARNING: BAD GeForce DRIVERS"
date: 2010-03-09
forum: The Cafe
---

### Post by ubunterooster on 2010-03-09
[http://maximumpc.com/article/news/nvidia_removes_linux_solaris_drivers_due_overheating_bug](http://maximumpc.com/article/news/nvidia_removes_linux_solaris_drivers_due_overheating_bug)

&#8593;I have warned you and cannot in any way be responsible if your card melts.

---

### Post by swoll1980 on 2010-03-09
The bug you are speaking of affects Windows machines running a particular driver. It was said the bug may effect 10.04 users, but mine has not climbed over 50 degrees, and that's running it on the performance setting. I notice that article doesn't even mention Windows.

---

### Post by Phrea on 2010-03-09
You gotta love the fanless low budget cards.

---

### Post by ubunterooster on 2010-03-09
> **swoll1980 said:**
> The bug you are speaking of affects Windows machines 
?
 I did not get that from the article, please give a referrence

> 
 mine has not climbed over 50 degrees, and that's running it on the performance setting. 


Nvidia's own site says it has overheating with some not all, but details are vague

> 
I notice that article doesn't even mention Windows.

because it was not about Windows

---

### Post by swoll1980 on 2010-03-09
> **ubunterooster said:**
> ?

because it was not about Windows

Of course not. Now you have to ask yourself why. Go to the NVIDIA forums if you need reference.

---

### Post by falconindy on 2010-03-09
> **ubunterooster said:**
> ?
 I did not get that from the article, please give a referrence



Nvidia's own site says it has overheating with some not all, but details are vague



because it was not about Windows
The article first mentions the 196 series WHQL driver (Windows), and then says the recall extends to the 195 series Linux drivers as well.

Affected or not, I'm not taking a chance.

---

### Post by RiceMonster on 2010-03-09
I just checked my driver version. Luckily I don't seem to be affected, but it's still worrying.

Pretty crazy stuff.

---

### Post by ubunterooster on 2010-03-09
> **falconindy said:**
> the article first mentions the 196 series whql driver (windows), and then says the recall extends to the 195 series linux drivers as well.

Affected or not, i'm not taking a chance.
+1

---

### Post by swoll1980 on 2010-03-09
> **RiceMonster said:**
> I just checked my driver version. Luckily I don't seem to be affected, but it's still worrying.

Pretty crazy stuff.

I learned of this a few days ago, but was not able to find any *nix users complaining that they were affected by it.

---

### Post by KinKiac on 2010-03-09
Lol.  Thats why I use the drivers in the repos and NOT the Nvidia drivers.  The article states that it is the 196 and 195 version that are affected.  If im not mistaken the repos still recommend 180 or something like that, so anyone who just installed from the repos should be fine keeping their existing drivers.  I may be wrong though.

---

### Post by #11u-max on 2010-03-09
mine got to 70*c but didnt melt..

had that problem with any linux OS.. switched to solaris, never had a problem.. switched back to windows and the card runs cool for what temperature it usually was [IMG]http://linsux.org/forum/public/style_emoticons/default/ohai.gif[/IMG]

---

### Post by swoll1980 on 2010-03-09
> **#11u-max said:**
> mine got to 70*c but didnt melt..

had that problem with any linux OS.. switched to solaris, never had a problem.. switched back to windows and the card runs cool for what temperature it usually was [IMG]http://linsux.org/forum/public/style_emoticons/default/ohai.gif[/IMG]

70 C is fine.

---

### Post by #11u-max on 2010-03-09
> **swoll1980 said:**
> 70 C is fine.
i had my safe temoerature set low, i have it set at 70. the card usually runs right at 55 on a normal day :\

---

### Post by cascade9 on 2010-03-09
70C isnt bad. I've seen nVidia cards hit 100C+. Hot country + crowded case + 3D studio max rendering, and no, it wasnt my computer.  

> **KinKiac said:**
> Lol. Thats why I use the drivers in the repos and NOT the Nvidia drivers. The article states that it is the 196 and 195 version that are affected. If im not mistaken the repos still recommend 180 or something like that, so anyone who just installed from the repos should be fine keeping their existing drivers. I may be wrong though.

190.xx is the current version in the repos. The bug doesnt affect the 190.xx or earlier linux drivers (or windows drivers for that matter, its only 195.xx on linux and 196.xx on windows).

---

### Post by swoll1980 on 2010-03-09
> **cascade9 said:**
> 70C isnt bad. I've seen nVidia cards hit 100C+. Hot country + crowded case + 3D studio max rendering, and no, it wasnt my computer.  


100 C is useually the performce theshhold on nvidia cards. Any hotter they begin to slow down.

---

### Post by ubunterooster on 2010-03-09
> **KinKiac said:**
> Lol.  Thats why I use the drivers in the repos and NOT the Nvidia drivers.  The article states that it is the 196 and 195 version that are affected.  If im not mistaken the repos still recommend 180 or something like that, so anyone who just installed from the repos should be fine keeping their existing drivers.  I may be wrong though.
the repos are safer I also believe

---

### Post by aklo on 2010-03-10
i'm using 1.8.5 and i'm not upgrading anytime soon. 
If it ain't broke, don't fix it.

---

### Post by Khakilang on 2010-03-10
That's why I have extra fan on my CPU to prevent things like this from happening. Precaution is always better than cure.

---

### Post by 3rdalbum on 2010-03-10
I guess that's just uncovered a problem with using PPAs to add Nvidia drivers. I use a PPA and apparently my driver version is 190.53, but it also contains the 195 driver. Now, I bet that PPA is still offering the 195 driver, even after its recall.

---

### Post by jwbrase on 2010-03-10
> **swoll1980 said:**
> 100 C is useually the performce theshhold on nvidia cards. Any hotter they begin to slow down.

Can anyone say what the safe operating limit is? I suppose it must be different for different models, but where could I find that out?

---

### Post by cascade9 on 2010-03-10
For the newer nVidia cards, check here-

[http://www.nvidia.com/object/geforce_family.html](http://www.nvidia.com/object/geforce_family.html)

Click on the card you want to check, then go to the "specification" tab (under the main pic of the card). Scroll down to "thermal and power specs". 

I'm 99.99% sure that the max temp for the 8xxx, 9xxx, 100 series, 200 series and 300 series is 105C (for desktop cards, I wouldnt know about mobile GPUs) Well, thats what nVidia says anyway, I would bet that you can go a tiny bit higher and not kill your card.....but that would be a Bad Idea IMO. 

The nVidia drivers have a 'shutdown threshold' as well. If your card hit that, it shuts down (obviously LOL). My 8600GT is set at 115C. You might be able to change that with some sort of tool, but I wouldnt know- even my passive cooled 8600GT has never gone above 90C so I've never bothed looking into it. (that was a VERY hot day, and playing 3D games for a few hours) 
 
For the older cards, I'm pretty sure that max temp is different. IIRC the max temp on the 6800GT was 115/120C. nVidia has removed the detailed spec sheet for the 'legacy' models so I cant be sure of that.

---

