---
title: "remove anjuta 2.xy.whatever from the repositories"
date: 2006-11-03
forum: Repositories &amp; Backports
---

### Post by rattusdatorum on 2006-11-03
huhu!

are you nuts delivering egdy with anjuta 2.xy.whatever???
I mean I never seen such unstable software in the last 10 years and I used to use winWhatSoFuckingEver and I also programmed some really aweful thingies, but nothing was at least as unstable as this program. 
It crashed and burned at least 5 times in less then 5 minutes!!!

ok, now I installed 1.2.4 (which is really good) and I get the message there is an freaking update available, yeah great, the next time I hit 
sudo apt-get upgrade 
by accident I will get the mess again, this is freaking joke isn't it?

](*,) ](*,) ](*,) ](*,) ](*,) 

so please do something about this, god dammit

some freaking CS student from Europe

---

### Post by Tiede on 2006-11-03
Ok, maybe you should tone it down a bit next time...
This is a [known problem](http://ubuntuforums.org/tags/index.php/anjuta/) that we are all trying to fix. I don't think ranting as such will help towards resolving it. Please refrain.

---

### Post by rattusdatorum on 2006-11-03
I know, that it is a known problem, hence I used some strong language (just discovered Doug Stanhope a few days ago, yeah), because it should be removed from the repositories.

I don't get it, why it is shipped with the standard cd anyway, I didn't know all Ubuntu Users are c/c++ programmers.

---

### Post by rattusdatorum on 2006-11-05
COULD SOMEONE PLEASE GET THE BUGGY ANJUTA OUT OF THE REPOSITORIES!

I don't carel, if you put this buggy version of Anjuta on the cd, 
but I CARE THAT YOU GET "THERE IS AN UPDATE available" message which isn't an update!

What is the sense/reason whatsoever keeping a buggy version in the
repositories and denying the access to a GREAT RUNNING VERSION?

---

### Post by Natas Drol on 2006-11-05
I installed 1.2.4 via checkinstall. After that I created the file /etc/apt/preferences with following content:

Package: anjuta
Pin: version 1.2.4a-1
Pin-Priority: 1001

Package: anjuta-common
Pin: version *
Pin-Priority: -1

The first part pins the old anjuta version and the second part keeps any anjuta-common package from being installed.

hih

---

### Post by matthew on 2006-11-05
> **rattusdatorum said:**
> COULD SOMEONE PLEASE GET THE BUGGY ANJUTA OUT OF THE REPOSITORIES!

I don't carel, if you put this buggy version of Anjuta on the cd, 
but I CARE THAT YOU GET "THERE IS AN UPDATE available" message which isn't an update!

What is the sense/reason whatsoever keeping a buggy version in the
repositories and denying the access to a GREAT RUNNING VERSION?Screaming about it in the forums isn't going to help. Find the package maintainer and make a request (preferably using much more polite language than you are using here if you want a positive response). A good place to start your search for the package maintainer might be [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by daniloeu on 2006-11-06
Hi guys!

I think that everbody know, Anjuta2.0.2 is a total bug, and is not easy to downgrade to anjuta1.2.4 on Edgy.
So I resolve it. I edit some Dapper packages, and create a new package named anjuta1.2.4,  and with 3 easy steps you can install anjuta 1.2.4 on Ubuntu Edgy.

```

echo "deb http://www.danilocesar.com/ubuntu debs/" >> /etc/apt/sources.list
apt-get update
apt-get install anjuta1.2.4
```

If you have any problems, please tell me:
danilo.eu [on] gmail [dot] com

---

### Post by vrun on 2006-11-27
FWIW
...I was fiddling with the 2.02 version myself
couldn't believe what happened, 
blamed it on my own self ;-/
...nevertheless 
DaniloCesars approach seems to be more reasonable
(with a couple of sudos added of course)

Thanks

---

### Post by Duwi on 2006-12-01
DaniloCesars approach worked perfect

thanks a lot

---

