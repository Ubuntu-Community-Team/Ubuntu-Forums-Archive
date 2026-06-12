---
title: "I may need to temporarily stop testing 13.04."
date: 2012-12-28
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2012-12-28
Had to switch my Cell Phone Provider from Verizon Wireless to Sprint after I had a Disagreement with Verizon about Data Overages with my Verizon IPhone 5, I currently do NOT have a Personal Hotspot for my new Sprint IPhone 5 and as a result may need to temporarily stop testing 13.04 until I can get one added to my new Sprint IPhone 5. Just FYI.

---

### Post by kevpan815 on 2012-12-28
Problem Solved, I called Sprint and had them add-on their 6 GB Personal Hotspot.

---

### Post by grahammechanical on 2012-12-29
Data download limits held back my testing. I have had to increase/change my arrangement with my ISP.

Regards.

---

### Post by ventrical on 2012-12-29
> **grahammechanical said:**
> Data download limits held back my testing. I have had to increase/change my arrangement with my ISP.

Regards.

 With as many machines as I am running/updating/upgrading/testing ,  I really have to pay the piper.  However.. I have a lot of hot-spots about this area which defray  those costs. Every little bit helps. I really have to work a budget here. Updating and upgrading Ubuntu is not for free but  it is all worth while as I see it.

---

### Post by cariboo on 2012-12-29
ventrical, it sounds like you need something like [apt-cacher-NG]("http://www.unix-ag.uni-kl.de/~bloch/acng/html/index.html"), you just download the updates once, and store them on a central system, then install the updates on other system from your central repository.

---

### Post by ventrical on 2012-12-31
> **cariboo907 said:**
> ventrical, it sounds like you need something like [apt-cacher-NG]("http://www.unix-ag.uni-kl.de/%7Ebloch/acng/html/index.html"), you just download the updates once, and store them on a central system, then install the updates on other system from your central repository.


 Aww .. geee.. yes .. you are right! :) But I have  different installs at different stages .. meaning that I may update one install on one day but not all installs everyday. So would there not be a syncing problem here?

(reason) The reason I do not update all systems in unison is that I like to allow a current install go through an aging process for a few days or weeks .. and then update ..so I assume there would definitely be holes if I used a central repo.  This gives me a better before and after perspective with installs running at different stages of development.

However, I will look into your suggestion.

Thank you.

---

### Post by pressureman on 2012-12-31
What does apt-cacher offer that a simple caching HTTP proxy like squid wouldn't do?

I used to do a lot of Debian testing netinstalls at a previous job, and we simply had a squid proxy on the network, which, over time, accumulated most of the common packages in its cache.

---

### Post by ventrical on 2012-12-31
From Installing squid:

"The feasibility of caching depends on two or more users visiting the same page while the object is still on disk."

 This has saved me a lot of time.  The apt-cache and squid alternatives to creating a central repository would of course save some bandwidth with a normal network but  not with the way my network is setup.

---

### Post by Lars Noodén on 2012-12-31
> **pressureman said:**
> What does apt-cacher offer that a simple caching HTTP proxy like squid wouldn't do?

I used to do a lot of Debian testing netinstalls at a previous job, and we simply had a squid proxy on the network, which, over time, accumulated most of the common packages in its cache.

squid or varnish should also work just fine.  If I recall correctly the main difference is retrieval speed where apt-cacher / apt-cacher-ng has specialized only in .deb packages.  Just make sure that the cache is large enough if you are using squid or varnish, it needs to be big enough to handle a few updates.  If you are doing a network installation, then it needs to be large enough to handle the whole system.

---

