---
title: "unity8 borks system erratic"
date: 2014-04-26
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-04-26
After downloading and installing unity-system-co and mir and then unity8 it borks the system. You can't shut down properly and there are all kinds of 'debounce' errors and then you loose your mouse. To get your mouse back you actually have to go to the top right hand icon, choose shutdown, then click the shutdown icon and you will get your mouse back - even after removing mir,compositor and unity8 , and it will not shut down unless hard shutdown.

---

### Post by grahammechanical on 2014-04-26
I have not installed Unity 8 since our early experiments. I was playing back a recent Ubuntu engineering hangout and Xmir and Unity 8 was mentioned as still being in the archives. I did not get any impression that it was being developed. Nothing was said about it not being developed either. But I am not sure of the usefulness of that Unity 8 code. I think that attention is elsewhere; the phone/tablet and now convergence. Remember, it was originally intended for Xmir to be default for 14.04. The devs gave up on that. Now, I guess they are pushing for convergence and that might leave that Unity 8 code up a creek without a paddle.

I have installed that Unity 8 preview session and it is broken as far as my machine is concerned. Does not come up to any kind of desktop. Sometimes I need to hard power off although the other day I could get to a tty. I do see that some mir libraries and unity system compositor are being held back. May be those updates will improve things.

Regards.

---

### Post by ventrical on 2014-04-26
Agreed. I had it working great near the middle of the last cycle. I dropped 'mir' (unity-system-co) during the last cycle because of that awful cursor bug. Now, it's as worse as ever with the exception of intel graphics. So nVidia is in the dog house (as we say in Canada) once again.:)lol

Regards..

---

### Post by ventrical on 2014-04-26
> **grahammechanical said:**
>  The devs gave up on that. Now, I guess they are pushing for convergence and that might leave that Unity 8 code up a creek without a paddle.

Regards.


 According to wixipedia, mir was developed to enable the development of Unity8! The next generation of the Unity Interface.

Ahhh .. found what I was looking for.

> 

In March 2014 [Mark Shuttleworth]("http://en.wikipedia.org/wiki/Mark_Shuttleworth")  confirmed that Mir development had been delayed and that it was now  forecast to be default for desktop use in Ubuntu 16.04 LTS, expected to  be released in 

April 2016


[http://en.wikipedia.org/wiki/Mir_%28software%29](http://en.wikipedia.org/wiki/Mir_%28software%29)

whew!


[SUP][/SUP][SUP][URL="http://en.wikipedia.org/wiki/Mir_%28software%29#cite_note-25"]
[/URL][/SUP]

---

### Post by grahammechanical on 2014-04-26
I watched that Mark Shuttleworth interview, whatever you call it. I came away with a slightly different understanding to some of those reporting what he said. I think that he was commenting on LTS releases. The fact that Mir will not be in 14.04 (as originally intended) and not back-ported to 14.04 through the length of its support period. So, that will mean that the first LTS release to run on Mir/Unity 8 will be 16.04.

I think that it is a mistake to conclude that 14.10 or 15.04 or 15.10 will not be running on Mir/Unity 8, as some are understanding Mark's comment. Interim releases are now being used to trial new stuff. And then there is this:

> [COLOR=#333333][FONT=Lucida Grande]it&#8217;s time to open the floodgates to _umpteen pent-up change_s and begin shaping our next show ... [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]But the point of spring cleaning is to make room for fresh ideas and new art, and our _next release has to raise the roof_ in that regard. And what a spectacular time to be unleashing creativity in Ubuntu. We have the _foundations of convergence_ so beautifully demonstrated by our core apps teams &#8211; with examples that shine on phone and tablet and PC ... [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]time to _refresh the foundations_ of the next generation of Linux: faster, smaller, better scaled and better maintained ... [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]time to walk a little uphill and, thereby, upstream. Time _to purge_ the ugsome and _prune_ the unusable ... [/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]since we&#8217;re getting that _once-every-two-years_ chance to make fresh starts and dream unconstrained dreams about what the future should look like,[/FONT][/COLOR]

[http://www.markshuttleworth.com/](http://www.markshuttleworth.com/)

The development version is where all this change and innovation is trialled.

---

### Post by ventrical on 2014-04-26
> **grahammechanical said:**
> 

The development version is where all this change and innovation is trialled.

 Thanks Graham,

 I had read that at Mark's blog.  I agree, and that is why we are here .. but I think it prudent that we should be wary (or made wary) when certain development componets will brake our systems. Mir&Unity8 as they are now in Utopic will break 'some' systems.  Others may fare better with different machines. I'm all for Mir and Unity8 but I can't bust something that's already busted :)lol

---

### Post by grahammechanical on 2014-04-27
I have just resurrected one of my trusty installs with Xmir + Unity 8 + Ubuntu SDK + emulator and managed to upgrade to 14.04 LTS and then on to Utopic. At first it lost Compiz + Unity but I have flashback installed but I got login bounce with Flashback (Compiz) but I was able to get in using Flashback (Metacity) and dist-upgrade solved both the update to 14.04 LTS and then to Utopic.

I login just fine with Unity 8. I ran some glmark2 tests and got slightly better results than with Xmir + Unity 7. I found that we need more than one run of glmark2. 

Regards.

---

