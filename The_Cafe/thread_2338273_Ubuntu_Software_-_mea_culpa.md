---
title: "Ubuntu Software - mea culpa"
date: 2016-09-26
forum: The Cafe
---

### Post by ventrical on 2016-09-26
All,

  Just doing some house cleaning here. Hope I am not off topic. I ran into a dilemma with netflix and a new client. The dilemma is that netflix was "supposed" to work out of the box on a  browser but  it does not. There is all sorts of conflicting info about Chrome and Firefox and user agent switching .. which is all very confusing for a noob who is trying to migrate away from Windows 10 stack. So new info says Firefox has the problem solved with it's new ver 49 with DRM and Widevine... nope .. don't work. So further research says google-chrome-stable will work out of the box. Ok.. go to Ubuntu Software (center) and no google-chrome.  How convenient. So then I have to download google-chrome-stable and it automagically installs itself into the Ubuntu Software app. it then has to be installed from Ubuntu Software!!

  Trying to explain this to a noob client is like trying to teach Latin  to an Eskimo!

 Now during last development I tried and tried to bridge the gap with developers when considering this new mass Exodus from Windows 10 but somehow I got diverted to the lore of unity8 desktop and started spending hours and hours there working with it while letting other bugs just more or less slip through the net. This is no fault of Ubuntu or Canonical. There were bugs and problems and rather than get on the devs backs .. I let them slide.

  And I am stunned that it would take a netflix fail to get my attention back on these bugs.

 I offer my apologies to the Ubuntu Community and will commit try to try harder in getting these bugs fixed.

Regards..
Ventrical

---

### Post by user1397 on 2016-09-26
Yea, still not sure about the Firefox thing.  I now have firefox 49 as well (came as a normal update on my 16.04 laptop).  When I try playing a video in netflix it asks me to install Silverlight.  I've attached a screenshot (again, this is a pristine Firefox version 49 on Ubuntu 16.04).

Chrome works perfectly for netflix, and I don't bother with the Ubuntu software center or whatever it's called now.  I just install gdebi first, then download Chrome from their website, and I select to open with gdebi (I then usually make gdebi the default for opening .deb files).  It installs perfectly, adds its own repository as well so that it can be updated like any other app.

I find gdebi to be more noob friendly than the software center for installing a .deb from an external source.  I use synaptic for everything else.

---

### Post by ventrical on 2016-09-26
here is out of the box fix.. [https://ubuntuforums.org/showthread.php?t=2338211&p=13550031#post13550031](https://ubuntuforums.org/showthread.php?t=2338211&p=13550031#post13550031)

Mea culpa no more :)

regards..

---

### Post by ventrical on 2016-09-26
> **user1397 said:**
> Yea, still not sure about the Firefox thing.  I now have firefox 49 as well (came as a normal update on my 16.04 laptop).  When I try playing a video in netflix it asks me to install Silverlight.  I've attached a screenshot (again, this is a pristine Firefox version 49 on Ubuntu 16.04).

Chrome works perfectly for netflix, and I don't bother with the Ubuntu software center or whatever it's called now.  I just install gdebi first, then download Chrome from their website, and I select to open with gdebi (I then usually make gdebi the default for opening .deb files).  It installs perfectly, adds its own repository as well so that it can be updated like any other app.



Yes.. thats it .. you had it already. I was just taken aback that google-chrome wasn't in repos.. and xenial gives a third party software warning ... so  it's play and then you pay :)

Regards..

---

### Post by oldos2er on 2016-09-26
No Google software has ever been in the default repos; this is nothing new.

---

### Post by ventrical on 2016-09-26
> **oldos2er said:**
> No Google software has ever been in the default repos; this is nothing new.

but this is from google site..

---

### Post by user1397 on 2016-09-27
> **ventrical said:**
> but this is from google site..
That's open source software under the Apache license released by Google and packaged for the ubuntu repos.  It's not directly from Google's website such as Google Chrome, which is also proprietary.

---

### Post by ventrical on 2016-09-27
> **user1397 said:**
> That's open source software under the Apache license released by Google and packaged for the ubuntu repos.  It's not directly from Google's website such as Google Chrome, which is also proprietary.

Yes.. I stand corrected... plus those were in the repos because I was doing some work with touch images so they were imported.

My bad...

Mea culpa once again ..

:)

Regards..

---

### Post by oldos2er on 2016-09-27
Google: Maybe not evil, but definitely confusing. I learned something too, ventrical.  :)

---

### Post by ventrical on 2016-09-28
> **oldos2er said:**
> Google: Maybe not evil, but definitely confusing. I learned something too, ventrical.  :)

I am not a fan of google Chrome but when I seen netflix  run out of the box without all the headaches.. then .. yes .. I learned somthing too. :)

Regards..

---

