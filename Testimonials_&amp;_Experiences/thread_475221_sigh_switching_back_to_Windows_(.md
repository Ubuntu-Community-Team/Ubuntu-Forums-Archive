---
title: "*sigh* switching back to Windows :("
date: 2007-06-15
forum: Testimonials &amp; Experiences
---

### Post by tdrusk on 2007-06-15
For the past 3 weeks I have been using Ubuntu. I have really liked it. My main goal was to use it for mostly everything I use Windows for (audio management, audio recording, video converting). I have learned a lot, and I will most definitely keep using Ubuntu on my server. 

I realized that over these past 3 weeks (I have been using ubuntu off and on for about 2 years now, doing this windows to ubuntu to windows pattern) that I am spending so much time working away on Ubuntu that I am not accomplishing any of my goals. It's not that I am incapable of doing what I want in Ubuntu, it's that I spend countless hours working on getting it to work that I forget my original intentions. Grant it, I have used Windows WAY longer than Ubuntu, but I am better with it. All of the software I get on Windows is either open source or free. 

Ubuntu is not 100% compatible with my hardware yet either. I am having trouble shutting the laptop lid and going into hybernate and suspend. It's a hit or miss thing. I need to be able to shut it and walk away,  not shut it, check it, see that it didn't hybernate, open it, shut it, check it, etc. 

I also keep getting errors that noone on the forum or irc has given me an answer to yet. i keep getting Segmentation fault (core dumped) while uploading to Revver in Firefox. It also just closes programs when I give it a job too big. 

All in all, it is a great OS, but it still isn't up to my par yet. I will check it out when the next LTS comes out. I understand that Feisty is unstable because it has all this new (awesome) software. I trust that the next LTS will kick ***, so I will be back when that arrives.

Much love for Ubuntu, keep up the good work!

---

### Post by vexorian on 2007-06-16
> 
I also keep getting errors that noone on the forum or irc has given me an answer to yet. i keep getting Segmentation fault (core dumped) while uploading to Revver in Firefox. It also just closes programs when I give it a job too big.

Run memtest, it should be an option if you installed ubuntu, you'd be surprised about the amount of failed RAM chips and laptops with those. If not then you probably used too little swap and you got few memory, perhaps try xubuntu or something lighted.

--
hybernate issues are also something that could come from bad RAM.
> 
All of the software I get on Windows is either open source or free. 

Then it is most likely in Linux as well, else could you name those apps ?

> 
I realized that over these past 3 weeks (I have been using ubuntu off and on for about 2 years now, doing this windows to ubuntu to windows pattern) that I am spending so much time working away on Ubuntu that I am not accomplishing any of my goals. It's not that I am incapable of doing what I want in Ubuntu, it's that I spend countless hours working on getting it to work that I forget my original intentions. Grant it, I have used Windows WAY longer than Ubuntu, but I am better with it. All of the software I get on Windows is either open source or free.

Something I don't yet notice is how you noticed it after 2 years?

..
Feisty is not supposed to be unstable, I thought edgy was, for me it is not unstable so I am not sure about this, I guess it depends on hardware, anyways bye and give it a try when the next LTS comes back, but first make sure to check your RAM memory.

---

### Post by loell on 2007-06-16
good attitude, see you in the next LTS ;)

---

### Post by vexorian on 2007-06-16
> I realized that over these past 3 weeks (I have been using ubuntu off and on for about 2 years now, doing this windows to ubuntu to windows pattern) that I am spending so much time working away on Ubuntu that I am not accomplishing any of my goals. It's not that I am incapable of doing what I want in Ubuntu, it's that I spend countless hours working on getting it to work that I forget my original intentions. Grant it, I have used Windows WAY longer than Ubuntu, but I am better with it. All of the software I get on Windows is either open source or free.

Just wanted to say, try making a detailed comment about the things that hold you back in Ubuntu unlike windows' if you point out the things that wasted your time it would be more likely they get fixed later.

---

### Post by tdrusk on 2007-06-16
So I ran the memtest and I got something that I probably should worry about...
```
Unable to malloc 3803185152 bytes.
Unable to malloc 3798990848 bytes.
Unable to malloc 3794796544 bytes.
Unable to malloc 3790602240 bytes.
Unable to malloc 3786407936 bytes.
Unable to malloc 3782213632 bytes.
Unable to malloc 3778019328 bytes.
Unable to malloc 3773825024 bytes.
Unable to malloc 3769630720 bytes.
Unable to malloc 3765436416 bytes.
Unable to malloc 3761242112 bytes.
Unable to malloc 3757047808 bytes.
Unable to malloc 3752853504 bytes.
Unable to malloc 3748659200 bytes.
Unable to malloc 3744464896 bytes.
Unable to malloc 3740270592 bytes.
Unable to malloc 3736076288 bytes.
Unable to malloc 3731881984 bytes.
Unable to malloc 3727687680 bytes.
Unable to malloc 3723493376 bytes.
Unable to malloc 3719299072 bytes.
Unable to malloc 3715104768 bytes.
Unable to malloc 3710910464 bytes.
Unable to malloc 3706716160 bytes.
Unable to malloc 3702521856 bytes.
Unable to malloc 3698327552 bytes.
Unable to malloc 3694133248 bytes.
Unable to malloc 3689938944 bytes.
Unable to malloc 3685744640 bytes.
Unable to malloc 3681550336 bytes.
Unable to malloc 3677356032 bytes.
Unable to malloc 3673161728 bytes.
Unable to malloc 3668967424 bytes.
Unable to malloc 3664773120 bytes.
Unable to malloc 3660578816 bytes.
Unable to malloc 3656384512 bytes.
Unable to malloc 3652190208 bytes.
Unable to malloc 3647995904 bytes.
Unable to malloc 3643801600 bytes.
Unable to malloc 3639607296 bytes.
Unable to malloc 3635412992 bytes.
Unable to malloc 3631218688 bytes.
Unable to malloc 3627024384 bytes.
Unable to malloc 3622830080 bytes.
Unable to malloc 3618635776 bytes.
Unable to malloc 3614441472 bytes.
Unable to malloc 3610247168 bytes.
Unable to malloc 3606052864 bytes.
Unable to malloc 3601858560 bytes.
Unable to malloc 3597664256 bytes.
Unable to malloc 3593469952 bytes.
Unable to malloc 3589275648 bytes.
Unable to malloc 3585081344 bytes.
Unable to malloc 3580887040 bytes.
Unable to malloc 3576692736 bytes.
Unable to malloc 3572498432 bytes.
Unable to malloc 3568304128 bytes.
Unable to malloc 3564109824 bytes.
Unable to malloc 3559915520 bytes.
Unable to malloc 3555721216 bytes.
Unable to malloc 3551526912 bytes.
Unable to malloc 3547332608 bytes.
Unable to malloc 3543138304 bytes.
Unable to malloc 3538944000 bytes.
Unable to malloc 3534749696 bytes.
Unable to malloc 3530555392 bytes.
Unable to malloc 3526361088 bytes.
Unable to malloc 3522166784 bytes.
Unable to malloc 3517972480 bytes.
Unable to malloc 3513778176 bytes.
Unable to malloc 3509583872 bytes.
Unable to malloc 3505389568 bytes.
Unable to malloc 3501195264 bytes.
Unable to malloc 3497000960 bytes.
Unable to malloc 3492806656 bytes.
Unable to malloc 3488612352 bytes.
Unable to malloc 3484418048 bytes.
Unable to malloc 3480223744 bytes.
Unable to malloc 3476029440 bytes.
Unable to malloc 3471835136 bytes.
Unable to malloc 3467640832 bytes.
Unable to malloc 3463446528 bytes.
Unable to malloc 3459252224 bytes.
Unable to malloc 3455057920 bytes.
Unable to malloc 3450863616 bytes.
Unable to malloc 3446669312 bytes.
Unable to malloc 3442475008 bytes.
Unable to malloc 3438280704 bytes.
Unable to malloc 3434086400 bytes.
Unable to malloc 3429892096 bytes.
Unable to malloc 3425697792 bytes.
Unable to malloc 3421503488 bytes.
Unable to malloc 3417309184 bytes.
Unable to malloc 3413114880 bytes.
Unable to malloc 3408920576 bytes.
Unable to malloc 3404726272 bytes.
Unable to malloc 3400531968 bytes.
Unable to malloc 3396337664 bytes.
Unable to malloc 3392143360 bytes.
Unable to malloc 3387949056 bytes.
Unable to malloc 3383754752 bytes.
Unable to malloc 3379560448 bytes.
Unable to malloc 3375366144 bytes.
Unable to malloc 3371171840 bytes.
Unable to malloc 3366977536 bytes.
Unable to malloc 3362783232 bytes.
Unable to malloc 3358588928 bytes.
Unable to malloc 3354394624 bytes.
Unable to malloc 3350200320 bytes.
Unable to malloc 3346006016 bytes.
Unable to malloc 3341811712 bytes.
Unable to malloc 3337617408 bytes.
Unable to malloc 3333423104 bytes.
Unable to malloc 3329228800 bytes.
Unable to malloc 3325034496 bytes.
Unable to malloc 3320840192 bytes.
Unable to malloc 3316645888 bytes.
Unable to malloc 3312451584 bytes.
Unable to malloc 3308257280 bytes.
Unable to malloc 3304062976 bytes.
Unable to malloc 3299868672 bytes.
Unable to malloc 3295674368 bytes.
Unable to malloc 3291480064 bytes.
Unable to malloc 3287285760 bytes.
Unable to malloc 3283091456 bytes.
Unable to malloc 3278897152 bytes.
Unable to malloc 3274702848 bytes.
Unable to malloc 3270508544 bytes.
Unable to malloc 3266314240 bytes.
Unable to malloc 3262119936 bytes.
Unable to malloc 3257925632 bytes.
Unable to malloc 3253731328 bytes.
Unable to malloc 3249537024 bytes.
Unable to malloc 3245342720 bytes.
Unable to malloc 3241148416 bytes.
Unable to malloc 3236954112 bytes.
Unable to malloc 3232759808 bytes.
Unable to malloc 3228565504 bytes.
Unable to malloc 3224371200 bytes.
Unable to malloc 3220176896 bytes.
Unable to malloc 3215982592 bytes.
Unable to malloc 3211788288 bytes.
Unable to malloc 3207593984 bytes.
Unable to malloc 3203399680 bytes.
Unable to malloc 3199205376 bytes.
Unable to malloc 3195011072 bytes.
Unable to malloc 3190816768 bytes.
Unable to malloc 3186622464 bytes.
Unable to malloc 3182428160 bytes.
Unable to malloc 3178233856 bytes.
Unable to malloc 3174039552 bytes.
Unable to malloc 3169845248 bytes.
Unable to malloc 3165650944 bytes.
Unable to malloc 3161456640 bytes.
Unable to malloc 3157262336 bytes.
Unable to malloc 3153068032 bytes.
Unable to malloc 3148873728 bytes.
Unable to malloc 3144679424 bytes.
Unable to malloc 3140485120 bytes.
Unable to malloc 3136290816 bytes.
Unable to malloc 3132096512 bytes.
Unable to malloc 3127902208 bytes.
Unable to malloc 3123707904 bytes.
Unable to malloc 3119513600 bytes.
Unable to malloc 3115319296 bytes.
Unable to malloc 3111124992 bytes.
Unable to malloc 3106930688 bytes.
Unable to malloc 3102736384 bytes.
Unable to malloc 3098542080 bytes.
Unable to malloc 3094347776 bytes.
Unable to malloc 3090153472 bytes.
Unable to malloc 3085959168 bytes.
Unable to malloc 3081764864 bytes.
Unable to malloc 3077570560 bytes.
Unable to malloc 3073376256 bytes.
Unable to malloc 3069181952 bytes.
Unable to malloc 3064987648 bytes.
Unable to malloc 3060793344 bytes.
Unable to malloc 3056599040 bytes.
Unable to malloc 3052404736 bytes.
Unable to malloc 3048210432 bytes.
Unable to malloc 3044016128 bytes.
Unable to malloc 3039821824 bytes.
Unable to malloc 3035627520 bytes.
Unable to malloc 3031433216 bytes.
Unable to malloc 3027238912 bytes.
Unable to malloc 3023044608 bytes.
Unable to malloc 3018850304 bytes.
Unable to malloc 3014656000 bytes.
Unable to malloc 3010461696 bytes.
Unable to malloc 3006267392 bytes.
Unable to malloc 3002073088 bytes.
Unable to malloc 2997878784 bytes.
Unable to malloc 2993684480 bytes.
Unable to malloc 2989490176 bytes.
Unable to malloc 2985295872 bytes.
Unable to malloc 2981101568 bytes.
Unable to malloc 2976907264 bytes.
Unable to malloc 2972712960 bytes.
Unable to malloc 2968518656 bytes.
Unable to malloc 2964324352 bytes.
Unable to malloc 2960130048 bytes.
Unable to malloc 2955935744 bytes.
Unable to malloc 2951741440 bytes.
Unable to malloc 2947547136 bytes.
Unable to malloc 2943352832 bytes.
Unable to malloc 2939158528 bytes.
Unable to malloc 2934964224 bytes.
Unable to malloc 2930769920 bytes.
Unable to malloc 2926575616 bytes.
Unable to malloc 2922381312 bytes.
Unable to malloc 2918187008 bytes.
Unable to malloc 2913992704 bytes.
Unable to malloc 2909798400 bytes.
Unable to malloc 2905604096 bytes.
Unable to malloc 2901409792 bytes.
Unable to malloc 2897215488 bytes.
Unable to malloc 2893021184 bytes.
Unable to malloc 2888826880 bytes.
Unable to malloc 2884632576 bytes.
Unable to malloc 2880438272 bytes.
Unable to malloc 2876243968 bytes.
Unable to malloc 2872049664 bytes.
Unable to malloc 2867855360 bytes.
Unable to malloc 2863661056 bytes.
Unable to malloc 2859466752 bytes.
Unable to malloc 2855272448 bytes.
Unable to malloc 2851078144 bytes.
Unable to malloc 2846883840 bytes.
Unable to malloc 2842689536 bytes.
Unable to malloc 2838495232 bytes.
Unable to malloc 2834300928 bytes.
Unable to malloc 2830106624 bytes.
Unable to malloc 2825912320 bytes.
Unable to malloc 2821718016 bytes.
Unable to malloc 2817523712 bytes.
Unable to malloc 2813329408 bytes.
Unable to malloc 2809135104 bytes.
Unable to malloc 2804940800 bytes.
Unable to malloc 2800746496 bytes.
Unable to malloc 2796552192 bytes.
Unable to malloc 2792357888 bytes.
Unable to malloc 2788163584 bytes.
Unable to malloc 2783969280 bytes.
Unable to malloc 2779774976 bytes.
Unable to malloc 2775580672 bytes.
Unable to malloc 2771386368 bytes.
Unable to malloc 2767192064 bytes.
Unable to malloc 2762997760 bytes.
Unable to malloc 2758803456 bytes.
Unable to malloc 2754609152 bytes.
Unable to malloc 2750414848 bytes.
Unable to malloc 2746220544 bytes.
Unable to malloc 2742026240 bytes.
Unable to malloc 2737831936 bytes.
Unable to malloc 2733637632 bytes.
Unable to malloc 2729443328 bytes.
Unable to malloc 2725249024 bytes.
Unable to malloc 2721054720 bytes.
Unable to malloc 2716860416 bytes.
Unable to malloc 2712666112 bytes.
Unable to malloc 2708471808 bytes.
Unable to malloc 2704277504 bytes.
Unable to malloc 2700083200 bytes.
Unable to malloc 2695888896 bytes.
Unable to malloc 2691694592 bytes.
Unable to malloc 2687500288 bytes.
Unable to malloc 2683305984 bytes.
Unable to malloc 2679111680 bytes.
Unable to malloc 2674917376 bytes.
Unable to malloc 2670723072 bytes.
Unable to malloc 2666528768 bytes.
Unable to malloc 2662334464 bytes.
Unable to malloc 2658140160 bytes.
Unable to malloc 2653945856 bytes.
Unable to malloc 2649751552 bytes.
Unable to malloc 2645557248 bytes.
Unable to malloc 2641362944 bytes.
Unable to malloc 2637168640 bytes.
Unable to malloc 2632974336 bytes.
Unable to malloc 2628780032 bytes.
Unable to malloc 2624585728 bytes.
Unable to malloc 2620391424 bytes.
Unable to malloc 2616197120 bytes.
Unable to malloc 2612002816 bytes.
Unable to malloc 2607808512 bytes.
Unable to malloc 2603614208 bytes.
Unable to malloc 2599419904 bytes.
Unable to malloc 2595225600 bytes.
Unable to malloc 2591031296 bytes.
Unable to malloc 2586836992 bytes.
Unable to malloc 2582642688 bytes.
Unable to malloc 2578448384 bytes.
Unable to malloc 2574254080 bytes.
Unable to malloc 2570059776 bytes.
Unable to malloc 2565865472 bytes.
Unable to malloc 2561671168 bytes.
Unable to malloc 2557476864 bytes.
Unable to malloc 2553282560 bytes.
Unable to malloc 2549088256 bytes.
Unable to malloc 2544893952 bytes.
Unable to malloc 2540699648 bytes.
Unable to malloc 2536505344 bytes.
Unable to malloc 2532311040 bytes.
Unable to malloc 2528116736 bytes.
Unable to malloc 2523922432 bytes.
Unable to malloc 2519728128 bytes.
Unable to malloc 2515533824 bytes.
Unable to malloc 2511339520 bytes.
Unable to malloc 2507145216 bytes.
Unable to malloc 2502950912 bytes.
Unable to malloc 2498756608 bytes.
Unable to malloc 2494562304 bytes.
Unable to malloc 2490368000 bytes.
Unable to malloc 2486173696 bytes.
Unable to malloc 2481979392 bytes.
Unable to malloc 2477785088 bytes.
Unable to malloc 2473590784 bytes.
Unable to malloc 2469396480 bytes.
Unable to malloc 2465202176 bytes.
Unable to malloc 2461007872 bytes.
Unable to malloc 2456813568 bytes.
Unable to malloc 2452619264 bytes.
Unable to malloc 2448424960 bytes.
Unable to malloc 2444230656 bytes.
Unable to malloc 2440036352 bytes.
Unable to malloc 2435842048 bytes.
Unable to malloc 2431647744 bytes.
Unable to malloc 2427453440 bytes.
Unable to malloc 2423259136 bytes.
Unable to malloc 2419064832 bytes.
Unable to malloc 2414870528 bytes.
Unable to malloc 2410676224 bytes.
Unable to malloc 2406481920 bytes.
Unable to malloc 2402287616 bytes.
Unable to malloc 2398093312 bytes.
Unable to malloc 2393899008 bytes.
Unable to malloc 2389704704 bytes.
Unable to malloc 2385510400 bytes.
Unable to malloc 2381316096 bytes.
Unable to malloc 2377121792 bytes.
Unable to malloc 2372927488 bytes.
Unable to malloc 2368733184 bytes.
Unable to malloc 2364538880 bytes.
Unable to malloc 2360344576 bytes.
Unable to malloc 2356150272 bytes.
Unable to malloc 2351955968 bytes.
Unable to malloc 2347761664 bytes.
Unable to malloc 2343567360 bytes.
Unable to malloc 2339373056 bytes.
Unable to malloc 2335178752 bytes.
Unable to malloc 2330984448 bytes.
Unable to malloc 2326790144 bytes.
Unable to malloc 2322595840 bytes.
Unable to malloc 2318401536 bytes.
Unable to malloc 2314207232 bytes.
Unable to malloc 2310012928 bytes.
Unable to malloc 2305818624 bytes.
Unable to malloc 2301624320 bytes.
Unable to malloc 2297430016 bytes.
Unable to malloc 2293235712 bytes.
Unable to malloc 2289041408 bytes.
Unable to malloc 2284847104 bytes.
Unable to malloc 2280652800 bytes.
Unable to malloc 2276458496 bytes.
Unable to malloc 2272264192 bytes.
Unable to malloc 2268069888 bytes.
Unable to malloc 2263875584 bytes.
Unable to malloc 2259681280 bytes.
Unable to malloc 2255486976 bytes.
Unable to malloc 2251292672 bytes.
Unable to malloc 2247098368 bytes.
Unable to malloc 2242904064 bytes.
Unable to malloc 2238709760 bytes.
Unable to malloc 2234515456 bytes.
Unable to malloc 2230321152 bytes.
Unable to malloc 2226126848 bytes.
Unable to malloc 2221932544 bytes.
Unable to malloc 2217738240 bytes.
Unable to malloc 2213543936 bytes.
Unable to malloc 2209349632 bytes.
Unable to malloc 2205155328 bytes.
Unable to malloc 2200961024 bytes.
Unable to malloc 2196766720 bytes.
Unable to malloc 2192572416 bytes.
Unable to malloc 2188378112 bytes.
Unable to malloc 2184183808 bytes.
Unable to malloc 2179989504 bytes.
Unable to malloc 2175795200 bytes.
Unable to malloc 2171600896 bytes.
Unable to malloc 2167406592 bytes.
Unable to malloc 2163212288 bytes.
Unable to malloc 2159017984 bytes.
Unable to malloc 2154823680 bytes.
Unable to malloc 2150629376 bytes.
Unable to malloc 2146435072 bytes.
Unable to malloc 2142240768 bytes.
Unable to malloc 2138046464 bytes.
Unable to malloc 2133852160 bytes.
Unable to malloc 2129657856 bytes.
Unable to malloc 2125463552 bytes.
Unable to malloc 2121269248 bytes.
Unable to malloc 2117074944 bytes.
Unable to malloc 2112880640 bytes.
Unable to malloc 2108686336 bytes.
Unable to malloc 2104492032 bytes.
Unable to malloc 2100297728 bytes.
Unable to malloc 2096103424 bytes.
Unable to malloc 2091909120 bytes.
Unable to malloc 2087714816 bytes.
Unable to malloc 2083520512 bytes.
Unable to malloc 2079326208 bytes.
Unable to malloc 2075131904 bytes.
Unable to malloc 2070937600 bytes.
Unable to malloc 2066743296 bytes.
Unable to malloc 2062548992 bytes.
Unable to malloc 2058354688 bytes.
Unable to malloc 2054160384 bytes.
Unable to malloc 2049966080 bytes.
Unable to malloc 2045771776 bytes.
Unable to malloc 2041577472 bytes.
Unable to malloc 2037383168 bytes.
Unable to malloc 2033188864 bytes.
Unable to malloc 2028994560 bytes.
Unable to malloc 2024800256 bytes.
Unable to malloc 2020605952 bytes.
Unable to malloc 2016411648 bytes.
Unable to malloc 2012217344 bytes.
Unable to malloc 2008023040 bytes.
Unable to malloc 2003828736 bytes.
Unable to malloc 1999634432 bytes.
Unable to malloc 1995440128 bytes.
Unable to malloc 1991245824 bytes.
Unable to malloc 1987051520 bytes.
Unable to malloc 1982857216 bytes.
Unable to malloc 1978662912 bytes.
Unable to malloc 1974468608 bytes.
Unable to malloc 1970274304 bytes.
Unable to malloc 1966080000 bytes.
Unable to malloc 1961885696 bytes.
Unable to malloc 1957691392 bytes.
Unable to malloc 1953497088 bytes.
Unable to malloc 1949302784 bytes.
Unable to malloc 1945108480 bytes.
Unable to malloc 1940914176 bytes.
Unable to malloc 1936719872 bytes.
Unable to malloc 1932525568 bytes.
Unable to malloc 1928331264 bytes.
Unable to malloc 1924136960 bytes.
Unable to malloc 1919942656 bytes.
Unable to malloc 1915748352 bytes.
Unable to malloc 1911554048 bytes.
Unable to malloc 1907359744 bytes.
Unable to malloc 1903165440 bytes.
Unable to malloc 1898971136 bytes.
Unable to malloc 1894776832 bytes.
Unable to malloc 1890582528 bytes.
Unable to malloc 1886388224 bytes.
Unable to malloc 1882193920 bytes.
Unable to malloc 1877999616 bytes.
Unable to malloc 1873805312 bytes.
Unable to malloc 1869611008 bytes.
Unable to malloc 1865416704 bytes.
Unable to malloc 1861222400 bytes.
Unable to malloc 1857028096 bytes.
Unable to malloc 1852833792 bytes.
Unable to malloc 1848639488 bytes.
Unable to malloc 1844445184 bytes.
Unable to malloc 1840250880 bytes.
Unable to malloc 1836056576 bytes.
Unable to malloc 1831862272 bytes.
Unable to malloc 1827667968 bytes.
Unable to malloc 1823473664 bytes.
Unable to malloc 1819279360 bytes.
Unable to malloc 1815085056 bytes.
Unable to malloc 1810890752 bytes.
Unable to malloc 1806696448 bytes.
Unable to malloc 1802502144 bytes.
Unable to malloc 1798307840 bytes.
Unable to malloc 1794113536 bytes.
Unable to malloc 1789919232 bytes.
Unable to malloc 1785724928 bytes.
Unable to malloc 1781530624 bytes.
Unable to malloc 1777336320 bytes.
Unable to malloc 1773142016 bytes.
Unable to malloc 1768947712 bytes.
Unable to malloc 1764753408 bytes.
Unable to malloc 1760559104 bytes.
Unable to malloc 1756364800 bytes.
Unable to malloc 1752170496 bytes.
Unable to malloc 1747976192 bytes.
Unable to malloc 1743781888 bytes.
Unable to malloc 1739587584 bytes.
Unable to malloc 1735393280 bytes.
Unable to malloc 1731198976 bytes.
Unable to malloc 1727004672 bytes.
Unable to malloc 1722810368 bytes.
Unable to malloc 1718616064 bytes.
Allocated 1714421760 bytes...trying mlock...Killed

```

I guess that means something is wrong? I wonder how I can fix that.



Oh and to answer the other question, I use a lot of apps that are in Linux on Ubuntu, but they keep crashing in Ubuntu so they are useless. But we may have found that problem.

Last night I popped in the Windows install cd, hit the red button to shut down, and then hit cancel. I like Ubuntu too much.

---

