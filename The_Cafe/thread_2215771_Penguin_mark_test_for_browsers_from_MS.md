---
title: "Penguin mark test for browsers from MS"
date: 2014-04-08
forum: The Cafe
---

### Post by sdowney717 on 2014-04-08
[http://ie.microsoft.com/testdrive/Performance/PenguinMark/Default.html](http://ie.microsoft.com/testdrive/Performance/PenguinMark/Default.html)

Funny how they use penquins which are Linux mascot.

Not sure if it is testing properly, but I get a 0 running chrome version 33 on ubuntu with core2duo 3.5ghz 64 bit.
The scores they show are much higher.
Found this out by reading here
[http://www.pcmag.com/article2/0,2817,2427058,00.asp](http://www.pcmag.com/article2/0,2817,2427058,00.asp)

---

### Post by su:bhatta on 2014-04-08
:)

Using Firefox-Nightly aka Firefox-trunk 31 got a 0.

Wondering if it is designed to give IE11 a perfect 10 :)

---

### Post by ajgreeny on 2014-04-08
My Firefox 28 just got 117, so how much does all this depend on the hardware underneath the browser?

I'm on a fairly fast i5-3570K with 8GB ram and I wonder if that, or a genuine 20Mb/s web connection makes a difference to the score.

---

### Post by carl4926 on 2014-04-08
29
On openSUSE 13.1 _64
Chrome 33

---

### Post by carl4926 on 2014-04-08
22
openSUSE 13.1
Firefox 28

---

### Post by su:bhatta on 2014-04-08
[ATTACH=CONFIG]251833[/ATTACH]

Google Chrome, still got a zero !
:confused:

---

### Post by Old_Grey_Wolf on 2014-04-08
On Chrome 33 I was getting between 118 and 123. I noticed that all 4 cores went to 30%. They normally run at 1 or 2%. The network showed less than 300 B/s inbound and less than 100 B/s outbound.

---

### Post by coldcritter64 on 2014-04-08
> **sdowney717 said:**
> ...
Funny how they use penquins which are Linux mascot.
...

Yeah, watching the little guy in the blue beany/scarf with "that E" on it ...  :-s.

Mozilla firefox 31 (Nightly), 1st go got a 6 at full desktop sized window, 2nd go in a much smaller window, 10. Third go in a tiny window 17; this is on quite old desktop hardware and a slow net connection.

Cheers.

---

### Post by Old_Grey_Wolf on 2014-04-08
Ran Firefox 28 and got a 60. I closed Firefox, opened Chrome, and ran it from Chrome 33 and got 131 this time. Network traffic is low so I doubt my 50 mbps network has anything to do with it. I noticed that Firefox didn't balance across the cores as well as Chrome for some reason.

---

### Post by cariboo on 2014-04-08
I'm running chromium 33 on Trusty,  I go a 66. :)

---

### Post by echotech2 on 2014-04-09
Ubuntu 13.10 - Q9300 Quad Core @ 3 Ghz. - GTX650 Ti video - 5Mb/sec connection = 26 singing penguins.

---

### Post by SurfaceUnits on 2014-04-09
**Score in milleseconds**
 (lower is better)

So if you scored 0, you are the bomb

---

### Post by estamets on 2014-04-10
185 on Chrome 34 on Trusty.. Guess that means I suck.

---

### Post by pqwoerituytrueiwoq on 2014-04-10
my firefox got a 32 
you need hardware acceleration support
i am assuming this is a FPS score
Phenom II 965 @3.7GHz w/ 650 TI Boost @1215MHz 1920x1080 screen

---

### Post by CharlesA on 2014-04-10
83 on this old i5 laptop with FF 28.

Also: Chipmunks ftw!

---

### Post by QIII on 2014-04-11
I got a zero with FF28.  Does that mean I have to take the test again for half credit?

Looks like the load all went to my GPU and was accelerated.  GPU went up to 27% (HD 5870).  CPU was around 20% (1100T)

Speed test shows 61Mbps.

---

### Post by mattlach on 2014-04-11
Chromium 33, 165.

I'm not sure how it measures the score, so this number is rather meaningless to me.

[img]https://farm4.staticflickr.com/3779/13784518533_384e2b4b1c_o.jpg[/img]

---

### Post by mattlach on 2014-04-11
> **mattlach said:**
> Chromium 33, 165.

I'm not sure how it measures the score, so this number is rather meaningless to me.

[img]https://farm4.staticflickr.com/3779/13784518533_384e2b4b1c_o.jpg[/img]


So based on the article linked by OP, this is simply a benchmark for in browser GPU acceleration.

I re-ran the benchmark above in chrome 33 on windows.   The score went up from 165 to 180.

Then I ran it in ie11, and well, the results are below

[img]https://farm4.staticflickr.com/3763/13784675303_1436a50ac5_o.jpg[/img]

There may be some truth to what they are saying about IE11 being better at GPU acceleration in a browser window (or the benchmark is just horribly biased, who knows?), but honestly, that isn't something I use at all often (if at all).  I'm still sticking with Chromium in Linux :p

---

### Post by coldcritter64 on 2014-04-11
> **mattlach said:**
> So based on the article linked by OP, this is simply a benchmark for in browser GPU acceleration.

I re-ran the benchmark above in chrome 33 on windows.   The score went up from 165 to 180.

Then I ran it in ie11, and well, the results are below
<snip-image>
There may be some truth to what they are saying about IE11 being better at GPU acceleration in a browser window (or the **benchmark is just horribly biased**, who knows?), but honestly, that isn't something I use at all often (if at all).  I'm still sticking with Chromium in Linux :p

Going on that score, I'd put money on what is bolded ;). So my score of "6" is now looking pretty poor :)

---

### Post by mattlach on 2014-04-11
> **coldcritter64 said:**
> Going on that score, I'd put money on what is bolded ;). So my score of "6" is now looking pretty poor :)

Well, to be fair my Geforce GTX Titan is a bit higher end than what most people use, which is probably responsible for the score being quite that high...

---

### Post by coldcritter64 on 2014-04-11
> **mattlach said:**
> Well, to be fair my Geforce GTX Titan is a bit higher end than what most people use, which is probably responsible for the score being quite that high...

Chrome <1000, same machine (?) IE >28000 ... :-k ... naaaaah, I'll stick with the bolded ... :lol:

---

### Post by mattlach on 2014-04-11
> **coldcritter64 said:**
> Chrome <1000, same machine (?) IE >28000 ... :-k ... naaaaah, I'll stick with the bolded ... :lol:

Could very well be, but that difference could also be explained by proper hardware GPU acceleration, and running it on the CPU.   There is probably some bias involved, after all it IS a Microsoft benchmark, but I'm not discounting that there may be some real GPU acceleration benefit going on here as well.

---

### Post by cAzJJBx on 2014-04-13
Qupzilla, not Safari. 


[IMG]http://i.imgur.com/67EZvh2.png[/IMG]

---

