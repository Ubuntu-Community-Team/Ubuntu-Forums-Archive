---
title: "looking for &quot;Linuxsampler&quot;  64bit  .deb  on Karmic"
date: 2010-03-29
forum: Ubuntu Studio
---

### Post by DerLinDau on 2010-03-29
Hi there!

I've still reading here a lot as a guest but not finding the right stuff.
So i register this forum to ask my burning question.

Where to find a Linux-sampler .deb for 64bit Karmic ?
It isn't in the normal repos also not in the real cool "philip5 PPA".  
And all the links I find were dead links.

Unfortunately I'm not able to compile it by myself 'cause I'm not familiar with this.

So is there any one to give me an hint?


Sorry for my bad English and kind regards yours 

DerLinDau

---

### Post by ajgreeny on 2010-03-29
Plenty of info here for you to sift through.
[http://www.google.co.uk/search?q=Linux-sampler.deb&ie=UTF-8](http://www.google.co.uk/search?q=Linux-sampler.deb&ie=UTF-8)

---

### Post by AutoStatic on 2010-03-29
Hello DerLinDau you can find it in my PPA: [https://launchpad.net/~autostatic/+archive/ppa/+packages](https://launchpad.net/~autostatic/+archive/ppa/+packages)

---

### Post by DerLinDau on 2010-03-29
Hello ajgreeny,

many thx for helping so at great length.

Smashing in some google-urls is not the way of ubuntu or is it?

English is a foreign-language to me and it is hard for me to remember
the right words i've learned over more than 20 years ago.
And trust me it's a lot harder to write it down.
So please be patient with me for making lot of mistakes.

At first i read a lot in the entirely known forums ....with no result.
Second i read a lot in the wonderful world of google ....with no result.

Yes you are right, there are results to get linuxsampler on 64bit but most
of them tell me to compile it from the scratch and the others are totally outdated or not very useful for Karmic.

Third i tried to ask here in the forum ...........in resulting someone says
"Go and use google!"

In my opinion your answer was not the right way of ubuntu community.
In my naturally spoken forum it is always "cool" to give an helping hand
to people they asking for.

Greetings from Germany 

DerLinDau

---

### Post by DerLinDau on 2010-03-29
Hi AutoStatic,

many thanks to you for the ppa !

I'll give it a try in a couple of hours.

But now i have to go to the snail-mail office .....:popcorn: 

Later i'll be back and report to you.

So far 

Best regards



DerLinDau

---

### Post by AutoStatic on 2010-03-29
Hello DerLinDau, you're welcome. Best is to download the separate packages and install those one by one.

[https://launchpad.net/~autostatic/+archive/ppa/+files/liblinuxsampler_1.0.0~autostatic2_amd64.deb](https://launchpad.net/~autostatic/+archive/ppa/+files/liblinuxsampler_1.0.0~autostatic2_amd64.deb)
[https://launchpad.net/~autostatic/+archive/ppa/+files/linuxsampler_1.0.0~autostatic2_amd64.deb](https://launchpad.net/~autostatic/+archive/ppa/+files/linuxsampler_1.0.0~autostatic2_amd64.deb)
[https://launchpad.net/~autostatic/+archive/ppa/+files/libgig6_3.3.0-1~autostatic0_amd64.deb](https://launchpad.net/~autostatic/+archive/ppa/+files/libgig6_3.3.0-1~autostatic0_amd64.deb)

---

### Post by DerLinDau on 2010-03-29
Thank you AutoStatic,

should i install the debs you listed it or is it
equal in witch order i have to do it?
(OMG strange this phrase, isn't it?)



Sorry  :-\"




Greetings from your neighbor


DerLinDau

EDIT: I think it is senseless to say i'm back .............

EDIT2: Do u know why linuxsampler ist not in the official repos from ubuntustudio?

---

### Post by AutoStatic on 2010-03-29
> **DerLinDau said:**
> Thank you AutoStatic,

should i install the debs you listed it or is it
equal in witch order i have to do it?You need to install libgig6 first, then liblinuxsampler and then linux-sampler itself. Then you also need something to play the GIG files with like Qsampler or JSampler (I use the [Fantasia]("http://downloads.sourceforge.net/jsampler/Fantasia-0.9.jar") package).

> **DerLinDau said:**
> EDIT2: Do u know why linuxsampler ist not in the official repos from ubuntustudio?Because of the exception they have in their license: [http://linuxsampler.org/downloads.html](http://linuxsampler.org/downloads.html)
It doesn't comply with Ubuntu's standards.

---

### Post by DerLinDau on 2010-03-29
I love you AutoStatic ! 

YMMD   it runs very very cool.

I'm so happy for working now with it.

I can't say it enough :  Thank you so much, and let's :guitar: 





You're the best man! (Or maybe girl?)


Thank you so much.


Greetings from Germany  ):P


DerLinDau

---

### Post by philip5 on 2010-03-29
> **DerLinDau said:**
> I love you AutoStatic ! 

You're the best man! (Or maybe girl?)

That was a bit funny! AutoStatic might be the bearded lady! How could I have missed that! :D

Anyway, I have Linuxsampler 1.0.0 and Fantasia 0.9 (frontend for Linuxsampler) on my todo-list of packages to make. I have already made most things for them but haven't tried them out so I know they work as good as I want before I upload them. Hopefully I will have them with the rest of my stuff on my PPA rather soon.

---

### Post by AutoStatic on 2010-03-29
> **philip5 said:**
> That was a bit funny! AutoStatic might be the bearded lady! How could I have missed that! :D[http://www.imdb.com/title/tt0094012/quotes?qt0467049](http://www.imdb.com/title/tt0094012/quotes?qt0467049)


And DerLinDau, you're welcome!

---

### Post by ajgreeny on 2010-03-29
Sorry if you thought my reply was a waste of time, but it was meant with good will.  There was no real way to know from your original post whether you had done much searching, so I simply stuck in the link to the first web page that appeared when I did a quick search for linuxsampler.deb.

You would be surprised, (or perhaps you wouldn't),  how many times people ask questions here on the forum without having done any searching first for themselves.

Sorry again for being of no use to you this time; I did not mean to upset you, but I am glad that your difficulty is now sorted out.

---

### Post by DerLinDau on 2010-03-30
Sorry for that AutoStatic!

I really don't want to pique you, but in the net you never know.....:o

And thanks a lot.


Greetings from Germany


DerLinDau




@ ajgreeny

Doesn't matter, everyone has sometimes a bad day and yesterday was yours.

---

### Post by Capoeira on 2010-03-30
> **DerLinDau said:**
> 

@ ajgreeny

Doesn't matter, everyone has sometimes a bad day and yesterday was yours.

you are verry agressive, don't you see? "mach mal halblang"

---

