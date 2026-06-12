---
title: "Data security question"
date: 2014-06-26
forum: Security
---

### Post by amtrakuk on 2014-06-26
hi there,

I've happily used Ubuntu 14.4.4 for about a year and am concerned with with banter going around the net about search strings being sent to the outside world.  I'm a bit confused and worried as I assumed Ubuntu user privacy as a core value, so I have some questions hopefully someone will be able to shed some light on.


[LIST]
[*]Is data being sent
[*]Who is it being sent to
[*]If it is being sent, at what point is there data encrypted
[*]What, if any data is being gathered
[*]If data is being gathered, how secure is the data being held
[*]Are 3rd parties being supplied with data
[*]What is the potential for a personal profile creating.
[/LIST]

I use 14.4.4.  From what I can see the fuss is over the Lenses introduced in later versions but does this also apply to earlier versions?  I don't have anything to hide except my banking details etc.  I switched to Ubuntu for the inherent security and ease of use.

Thanks

---

### Post by open2reason on 2014-06-26
Hi, a good place to get an overview about privacy is to be found [http://www.ubuntu.com/legal/terms-and-policies/privacy-policy](http://www.ubuntu.com/legal/terms-and-policies/privacy-policy) and a visit to System Settings > Security & Privacy will allow you to have some control of what is logged and shared.

---

### Post by uRock on 2014-06-26
You may be thinking of the Amazon shopping lens. For more info and how to remove it, check this link. [http://askubuntu.com/questions/192269/how-can-i-remove-amazon-search-results-from-the-dash-or-disable-the-feature](http://askubuntu.com/questions/192269/how-can-i-remove-amazon-search-results-from-the-dash-or-disable-the-feature)

To remove it copy and paste the following into a terminal```
sudo apt-get remove unity-lens-shopping
```

---

### Post by deadflowr on 2014-06-26
> **amtrakuk said:**
> 
I use 14.4.4.  From what I can see the fuss is over the Lenses introduced in later versions but does this also apply to earlier versions?  I don't have anything to hide except my banking details etc.  I switched to Ubuntu for the inherent security and ease of use.

Thanks

I guess you mean 12.04, since I have no idea what 14.4.4 is.
In that case, no the online search feature is not implemented in the 12.04 release.
The only online search that came with 12.04 is for videos, which you can filter down to just local if you want.
The video lens for for 12.04 seems to be isolated from the rest of the dash, since you have to actually be within the video lens to search videos. As opposed to simply running a search and results coming up, like newer versions do.
But that's just my observation.

---

### Post by mastablasta on 2014-06-27
if you want some privacy you need to unplug the internet cable, get offline. otherwise there is "tons" of private data being shared arround.

system itself is not sharing any data. even these searches in unity lens are no different than if you use Google to search. only in this case amazon get's this data so they can ptut books, songs you might like in searches.

many people complain about this but on the other hand many people didn't use internet in the 90's and don't know how bad the untargeted adds were. all those pop up windows offering various enlargements or free pictures of naked women etc.

---

