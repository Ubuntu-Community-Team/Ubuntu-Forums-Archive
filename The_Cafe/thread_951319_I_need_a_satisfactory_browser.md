---
title: "I need a satisfactory browser"
date: 2008-10-18
forum: The Cafe
---

### Post by JeffoOfMetal on 2008-10-18
Well, I'm sad now, because I used to think Linux had some good browsers available.

But then something went wrong with my beloved Firefox. It must've gotten updated, and now it lags like never before. I need a fast, yet elegant browser.

And why is Firefox so awfully slow all of a sudden?

---

### Post by Frak on 2008-10-18
Anything that uses Webkit as an engine.

---

### Post by MaxIBoy on 2008-10-18
For fast and elegant, you can't beat Links. Screenshots:

---

### Post by crimesaucer on 2008-10-18
> **JeffoOfMetal said:**
> Well, I'm sad now, because I used to think Linux had some good browsers available.

But then something went wrong with my beloved Firefox. It must've gotten updated, and now it lags like never before. I need a fast, yet elegant browser.

And why is Firefox so awfully slow all of a sudden?

You could always build firefox from source, use a mozconfig with optomized settings, and C[XX]FLAGS for your processor.

Here is the mozconfig from an Arch package: [http://aur.archlinux.org/packages/firefox-optimized/firefox-optimized/mozconfig](http://aur.archlinux.org/packages/firefox-optimized/firefox-optimized/mozconfig)

..... and the whole package for any Archlinux users: [http://aur.archlinux.org/packages.php?ID=18090](http://aur.archlinux.org/packages.php?ID=18090)


I'm using it (with a few different settings and CFLAGS), and it's very fast.

---

### Post by chucky chuckaluck on 2008-10-18
opera's great and on some machines, can be perceived to be faster than firefox.

---

### Post by crimesaucer on 2008-10-18
> **MaxIBoy said:**
> For fast and elegant, you can't beat Links. Screenshots:

Links is perfect for fixing your system from console..... if you need to check a wiki page, or download something.


Am I able to import Firefox bookmarks to Links?

---

### Post by MaxIBoy on 2008-10-18
As far as I know, no. However, you can alias commonly used webpages to links by creating a file called ~/.bash_aliases if you don't have one, and then adding something along these lines to the file:
```
alias google='links http://www.google.com'
alias slashdot='links http://slashdot.org'
```
etc. 
After that, just type the name of the alias into a terminal and links will pop up and load that page. Plus links has its own built-in bookmarks feature.


Links is great for recovery if you're stuck in text mode, but it's also great if you want pages to load fast. It doesn't load images or animations (though you can use links to download them and then view them with other programs,) so for those with slow Internet it's a lifesaver.

---

### Post by JeffoOfMetal on 2008-10-18
Okay, so I've used Opera, and it's painfully slow, even slower than Firefox, and I probably won't consider Links anytime in the near future.

My primary browsers at the moment are Galeon and Midori, neither of which are rather good browsers.

What I feel like doing is reinstalling Ubuntu or installing Linux Mint on this machine. I love Ubuntu, but I have to say it lags quite often and my browsers quit all the time. What's all this about? Might it have to do with AWN?

---

### Post by MaxIBoy on 2008-10-18
A good, lightweight **graphical** browser is dillo. That ought to do it for you.


Also, if you have poor performance, try installing LXDE from Synaptic. The interface is a little bit too Windows-like for my tastes, but it's very fast.

---

### Post by th3james on 2008-10-18
> **JeffoOfMetal said:**
> 
What I feel like doing is reinstalling Ubuntu or installing Linux Mint on this machine. I love Ubuntu, but I have to say it lags quite often and my browsers quit all the time. What's all this about? Might it have to do with AWN?

Crashing is very probably attributable to flash, try install the new deb for flash 10 from adobe.

The lagging thing is strange, is it just firefox, or is it everything that lags? cuz either way, it isnt normal behavior

---

### Post by JeffoOfMetal on 2008-10-18
> **th3james said:**
> Crashing is very probably attributable to flash, try install the new deb for flash 10 from adobe.

The lagging thing is strange, is it just firefox, or is it everything that lags? cuz either way, it isnt normal behavior

Well, Firefox lags, and so does Galeon. Midori is decent, however. Pretty much anything Gecko-based lags horribly. I don't get it. Does this have anything to do with a Celeron M processor?

---

### Post by th3james on 2008-10-18
When you say lags, do u mean the (down)loading of the pages, or just the rendering and general performance?
Celeron Ms are by no means the fastest processors, but the performance should be decent. Perhaps you should give swiftfox a try, it's a custom compiled firefox, and might rid you of the issue you're having

---

### Post by crimesaucer on 2008-10-18
> **MaxIBoy said:**
> As far as I know, no. However, you can alias commonly used webpages to links by creating a file called ~/.bash_aliases if you don't have one, and then adding something along these lines to the file:
```
alias google='links http://www.google.com'
alias slashdot='links http://slashdot.org'
```
etc. 
After that, just type the name of the alias into a terminal and links will pop up and load that page. Plus links has its own built-in bookmarks feature.


Links is great for recovery if you're stuck in text mode, but it's also great if you want pages to load fast. It doesn't load images or animations (though you can use links to download them and then view them with other programs,) so for those with slow Internet it's a lifesaver.

Thanks, I'll try that.


@ JeffoOfMetal: When I had a Celeron M, I used Swiftfox and Swiftweasel and they were fast.


I see that you use Midori, I always thought that was super fast like Epiphany.... just not finished yet.


Maybe something else is keeping things slow. Back when I had my laptop with the Celeron M and only 512MB RAM, whenever Firefox/Swiftfox/Swiftweasel would have a few tabs open, or any large image files, it would always start to use my SWAP file..... even if I still hadn't used a lot of the 512 MB RAM....


Whenever it did this, it would make my computer so slow..... firefox would become ridiculously slow. I fixed that back then by changing the swappiness to about 20. Then Firefox wouldn't be moved over to the SWAP file..... and it stayed fast. Occasionally if a gigantic page opened while there were already a bunch of tabs open, then it would move to SWAP.

in /etc/sysctl.conf

```
vm.swappiness=20
```

---

### Post by Frak on 2008-10-18
> **JeffoOfMetal said:**
> Well, Firefox lags, and so does Galeon. Midori is decent, however. Pretty much anything Gecko-based lags horribly. I don't get it. Does this have anything to do with a Celeron M processor?
A lot of web page rendering relies on your caches a bit more than your speed. Turns out Celerons have high clock rates but low cache sizes, which renders some of that speed useless. If you cannot store an instruction in the cache, it cannot be run in the next cycle.

Therefore, a celeron 2GHz is slower than a centrino at 2GHz, just becaues of its L2 cache. (and maybe it's L3 if your motherboard supports it)

---

### Post by Canis familiaris on 2008-10-18
IMO Opera. I think you should give it a shot.

---

### Post by gjoellee on 2008-10-18
Opera 9.6 and Firefox 3.1 (not Firefox 3.0) is great

---

### Post by LaRoza on 2008-10-18
If you want a satisfactory browser, use Firefox. If you want the best, use Opera.

---

### Post by adamogardner on 2008-10-18
> **MaxIBoy said:**
> For fast and elegant, you can't beat Links. Screenshots:

How do I get it?  Which version do I download?  Do I need to compile it?  How?

---

### Post by LaRoza on 2008-10-18
> **adamogardner said:**
> How do I get it?  Which version do I download?  Do I need to compile it?  How?

Synaptic broken?

I also recommend links2 (which is both graphical and textual).

---

### Post by init1 on 2008-10-18
Actually, you probably need a new distro. Hardy is LETHARGIC on my Celeron laptop. Debian runs way faster. 
There's also HV3, which runs OK
[http://tkhtml.tcl.tk/hv3.html](http://tkhtml.tcl.tk/hv3.html)

---

### Post by doorknob60 on 2008-10-18
> **init1 said:**
> Actually, you probably need a new distro. Hardy is LETHARGIC on my Celeron laptop. Debian runs way faster. 
There's also HV3, which runs OK
[http://tkhtml.tcl.tk/hv3.html](http://tkhtml.tcl.tk/hv3.html)

Ubuntu can be good at that sometimes :-P Maybe try Debian or Arch.

---

