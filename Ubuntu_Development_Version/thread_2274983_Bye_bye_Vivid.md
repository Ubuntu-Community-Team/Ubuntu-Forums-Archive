---
title: "Bye bye Vivid"
date: 2015-04-23
forum: Ubuntu Development Version
---

### Post by Elfy on 2015-04-23
you were fun for a while.

---

### Post by slickymaster on 2015-04-23
Like a good friend of mine always says> See you next later!

---

### Post by ventrical on 2015-04-23
> **Elfy said:**
> you were fun for a while.

ummmm...yea....eh ...ahhhh .. but ....hrrmmmn   th, th, this cycle really caused me to stutter ... a lot :) lol hehehe ...  it was more like a barrel full of tarantulas than it was east african monkeys . :)

Hey hey for the Monkeys ! :)

Regards..

---

### Post by PaulW2U on 2015-04-23
> **Elfy said:**
> you were fun for a while.

The first development cycle where I've not run Ubuntu or Kubuntu but Xubuntu.

Now that we're moving on do I jump ship to Xubuntu or try that shiny new Plasma 5 desktop that I'm forever being told is the most beautiful desktop ever?  :confused:

---

### Post by slickymaster on 2015-04-23
> **PaulW2U said:**
> The first development cycle where I've not run Ubuntu or Kubuntu but Xubuntu.

Now that we're moving on do I jump ship to Xubuntu or try that shiny new Plasma 5 desktop that I'm forever being told is the most beautiful desktop ever?  :confused:
One should not mess with a winning formula PaulW2U. ;)

---

### Post by sammiev on 2015-04-23
Bring on the next!! :P

---

### Post by rrnbtter on 2015-04-23
Greetings, 
I have been using the Development version since Karmic and for a change I sure would hate to loose this currently awesome OS. I just installed it on a SSD for my wife's five year old Intel Atom powered Netbook with two gig of ram and it is like a new fully loaded computer. This is a fine release and it is going to be hard to give up. At least for a week or two :)

---

### Post by QDR06VV9 on 2015-04-23
Elfy is this just a joke
Code name  ][B]Wibbly Whinocewos 
[FONT=comic sans ms]Tell me it's not So..:shock: [/FONT]
[/B]

---

### Post by QIII on 2015-04-23
Canonical is currently in contract negotiations with Warner Bros for "Wascawy Wabbit".

---

### Post by sgage on 2015-04-23
Winsome Wallaby.

Gotta be.

---

### Post by Elfy on 2015-04-23
> **runrickus said:**
> Elfy is this just a joke
Code name  ][B]Wibbly Whinocewos 
[FONT=comic sans ms]Tell me it's not So..:shock: [/FONT]
[/B]

:)

I could say - could be, but then people might think I know more.

If the next version is Wibbly Whinocewos I'll eat your hat

---

### Post by QDR06VV9 on 2015-04-23
> **Elfy said:**
> :)

I could say - could be, but then people might think I know more.

If the next version is Wibbly Whinocewos I'll eat your hat
Awesome! Your safe though I do not wear Hats;)
Ooopps Outside of Tinfoil LOL

---

### Post by slickymaster on 2015-04-23
> **QIII said:**
> Canonical is currently in contract negotiations with Warner Bros for "Wascawy Wabbit".
This one would have my +1, for sure.

---

### Post by QDR06VV9 on 2015-04-23
+2  I can hear Elmer Fuud now!
Qlll can put a smile on my face from time to time!

---

### Post by oldos2er on 2015-04-23
I vote for Woozy Wombat.

---

### Post by QIII on 2015-04-23
Wiley Wapiti

---

### Post by Chanath on 2015-04-24
The sources.list has vivid in it, while python-apt/Ubuntu.info has devel (Suite: devel) in it, so if I just change vivid to devel in sources.list, I could simply move on to the next development, couldn't I? I could keep on having a rolling distro.

---

### Post by zika on 2015-04-24
> **Chanath said:**
> The sources.list has vivid in it, while python-apt/Ubuntu.info has devel (Suite: devel) in it, so if I just change vivid to devel in sources.list, I could simply move on to the next development, couldn't I? I could keep on having a rolling distro.As far as I can [see]("http://archive.ubuntu.com/ubuntu/ubuntu/dists/"): no...
Not to mention that, of course, I've tried it... ;)

---

### Post by Chanath on 2015-04-24
> **zika said:**
> As far as I can [see]("http://archive.ubuntu.com/ubuntu/ubuntu/dists/"): no...
Not to mention that, of course, I've tried it... ;)

I see the same in Trusty python-apt, there is a 'devel' in it too. It could mean there must be a devel repo?
In the Index, vivid and devel are the same...

---

### Post by zika on 2015-04-24
> **Chanath said:**
> I see the same in Trusty python-apt, there is a 'devel' in it too. It could mean there must be a devel repo?You could put in that file even Suite: Zika but that does not mean that there is a branch on that repo's tree...
Waiting for [FONT=arial][COLOR=#000000]Wibbly Whinocewos: 15.10 ... What You see in that file is an atavism from the idea that U could become rolling that died months ago. O&O...
You could ask incurable optimists here that tried almost everything even though it was impossible from the very beginning... ;) In order that to work support on the other side of Your wire (repos) is needed.
[/COLOR][/FONT]:p

---

### Post by Chanath on 2015-04-24
> **zika said:**
> You could put in that file even Suite: Zika but that does not mean that there is a branch on that repo's tree...
Waiting for [FONT=arial][COLOR=#000000]Wibbly Whinocewos: 15.10 ... What You see in that file is an atavism from the idea that U could become rolling that died months ago. O&O...
You could ask incurable optimists here that tried almost everything even though it was impossible from the very beginning... ;) In order that to work support on the other side of Your wire (repos) is needed.
[/COLOR][/FONT]:p

Okay, okay!
We are now saying bye to Vivid here, so let me ask few more questions. 
What if I change trusty to devel in trusty sources.list, wouldn't it update to vivid? Or the next 15.10?
In the Index, vivid and devel look the same.

---

### Post by grahammechanical on 2015-04-24
> What if I change trusty to devel in trusty sources.list, wouldn't it update to vivid? Or the next 15.10?

It would try to upgrade trusty to vivid but it may fail considering the big code differences between the two. It has no choice but to change all the libraries. It would be an interesting experiment but I would not do it with an install that I wanted to keep. This is the command that I shall use to turn at least one install of vivid into wcodename

```
sudo sed -i 's/vivid/wcodename/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

I might even throw in apt-get dist-upgrade. There are devel repositories. They are used especially for the Ubuntu phone. I do have another install of vivid sitting on devel repositories just to see what happens in the next few days. I might roll over. It did 26 weeks or so ago. An install went from Utopic to Vivid on the devel repositories. I am not sure how useful it is to have a desktop Ubuntu on devel repositories.

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/image-channels/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/image-channels/)

Regards.

---

### Post by Chanath on 2015-04-24
I know about this;
```
sudo sed -i 's/vivid/wcodename/g' /etc/apt/sources.list
```
I've been doing some upgrades that way until trusty, but don't want to break trusty with vivid attached to it, as trusty is going to live for next few years. I might play with upgrading vivid to the next 15.10, but wait for the next LTS to upgrade from trusty.
Anyway, I was just asking a question, as it is now bye-bye vivid.;)
Thank you for the reply.

EDIT: considering trusty, I had a problem of upgrading to the next kernel, when upgrading from 14.04.1 to 14.04.2, I had to manually install kernel 3.16

---

### Post by sudodus on 2015-04-27
I like(d) you Vivid :KS

---

### Post by enricobe on 2015-04-28
Hi all,
when we can install 15.10? 
I'm really uncomfortable with a stable version :D

---

### Post by grahammechanical on 2015-04-28
> **enricobe said:**
> Hi all,
when we can install 15.10? 
I'm really uncomfortable with a stable version :D

I am sitting here bored wanting to know the same thing. We need a code name for the repositories. I have just been reading this. I think it will complicate things as regards to repositories. 

[http://www.itworld.com/article/2914850/linux/is-ubuntu-moving-away-from-deb-packages-here-is-the-complete-story.html](http://www.itworld.com/article/2914850/linux/is-ubuntu-moving-away-from-deb-packages-here-is-the-complete-story.html)

[https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo](https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo)

But then again, may be not. It will all need testing. Bring on the fun! Online summit sessions to watch out for

[http://summit.ubuntu.com/uos-1505/track/convergence/](http://summit.ubuntu.com/uos-1505/track/convergence/)

And there was I thinking: "Snappy core? That's for the Cloud. Not interested." How wrong can I be? Don't answer that! :)

Regards.

---

### Post by Elfy on 2015-04-28
> **grahammechanical said:**
> I am sitting here bored wanting to know the same thing. We need a code name for the repositories. I have just been reading this. I think it will complicate things as regards to repositories. 

[http://www.itworld.com/article/2914850/linux/is-ubuntu-moving-away-from-deb-packages-here-is-the-complete-story.html](http://www.itworld.com/article/2914850/linux/is-ubuntu-moving-away-from-deb-packages-here-is-the-complete-story.html)

[https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo](https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo)

But then again, may be not. It will all need testing. Bring on the fun! Online summit sessions to watch out for

[http://summit.ubuntu.com/uos-1505/track/convergence/](http://summit.ubuntu.com/uos-1505/track/convergence/)

And there was I thinking: "Snappy core? That's for the Cloud. Not interested." How wrong can I be? Don't answer that! :)

Regards.

and over here in not Ubuntu land I'm full of "if it hurts flavors in any direct way, that's a bug" at the moment :p

---

### Post by grahammechanical on 2015-04-28
It certainly would be a bug. This may reassure but time will tell. 

> **Q:** What about the impact  of that in other ubuntu editions (kubuntu, xubuntu)? Everyone is  supposed to move to snappy and abandon apt/dpkg?

**A:** The flavors won't be affected unless they choose to add snappy support themselves to get its benefits.



[http://www.webupd8.org/2015/04/ubuntu-desktop-to-eventually-switch-to.html#more](http://www.webupd8.org/2015/04/ubuntu-desktop-to-eventually-switch-to.html#more)

---

### Post by ventrical on 2015-04-28
> **grahammechanical said:**
> I am sitting here bored wanting to know the same thing. We need a code name for the repositories. I have just been reading this. I think it will complicate things as regards to repositories. 

[http://www.itworld.com/article/2914850/linux/is-ubuntu-moving-away-from-deb-packages-here-is-the-complete-story.html](http://www.itworld.com/article/2914850/linux/is-ubuntu-moving-away-from-deb-packages-here-is-the-complete-story.html)

[https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo](https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo)

But then again, may be not. It will all need testing. Bring on the fun! Online summit sessions to watch out for

[http://summit.ubuntu.com/uos-1505/track/convergence/](http://summit.ubuntu.com/uos-1505/track/convergence/)

And there was I thinking: "Snappy core? That's for the Cloud. Not interested." How wrong can I be? Don't answer that! :)

Regards.


Is it really all that bad?

> 

Canonical will offer a traditional 16.04 Debian package edition and a  Snappy desktop so users can choose whichever version they want. Since  16.04 will be LTS it will be critical for Canonical to not ‘touch’ the  users who want to use the traditional desktop and at the same time offer  an LTS release of Snappy to those who want to climb up the evolutionary  ladder.



Yup .. it will be fun for sure. :)

---

### Post by craig10x on 2015-04-29
And "snappy" will bring us the rolling ubuntu we all so much wanted to see happen...based on the article, you should have the option available to select when 16.04 LTS is released....it will be your choice...non-rolling ubuntu or rolling ubuntu :D

---

### Post by ventrical on 2015-04-29
> **craig10x said:**
> And "snappy" will bring us the rolling ubuntu we all so much wanted to see happen...based on the article, you should have the option available to select when 16.04 LTS is released....it will be your choice...non-rolling ubuntu or rolling ubuntu :D

heheh ... I get vertigo just thinking about it :)

Regards..

---

### Post by craig10x on 2015-04-29
Yeah, me too, ventrical ;) :mrgreen:

---

### Post by grahammechanical on 2015-04-29
I cannot think of a reason why Ubuntu on Snappy Personal would have interim releases. 15.10 could well be the last interim release.

---

### Post by ventrical on 2015-04-29
Yeah .. that makes sense.

Regards..

---

### Post by craig10x on 2015-04-30
Yes, it would seem to me that what they would do is eliminate the 6 month version and instead have two choices....
Example:  16.04 LTS (which would work the same way as it does now) and 16.04 LTS Snappy Personal (for those who want a rolling ubuntu)...

The schedule on LTS would continue with a new one every 2 years...with the 2 editions being offered...your choice...
And instead of new versions every 6 months, they would only need to revise the iso image to bring it up to date (so that anyone installing fresh wouldn't have a lot of catching up to do as far as updates) much as is done with most "rolling style" distros...

And if you install the snappy edition, well then you wouldn't need to install it every 2 years for the latest one ;)
You would always be "latest" :D

---

### Post by craig10x on 2015-05-02
It probably won't be too long before you will have 15.10 snappy daily build isos for you testers to play with ;)

---

### Post by zika on 2015-05-02
> **craig10x said:**
> It probably won't be too long before you will have 15.10 snappy daily build isos for you testers to play with ;)You know something new about &#8222;regular&#8220; +1? I even contemplated starting playing with Snappy... ;)

---

### Post by grahammechanical on 2015-05-02
I have been re-reading the Reddit conversation between Will Cook and the author of webupd8 and this is what I see:

> **Q: **What happens after Ubuntu  16.04 (assuming Mir and Unity 8 land as default)? Are there going to be  two branches, one with click packages, one with deb?

**A:** That is the plan, yes, but the details still need to be worked out at UOS.

I keep in mind that only taxes and death are certain, nontheless it seems that there will be two branches of U+1 to test over the coming year. When development is done in the open, then we notice the false starts that would otherwise be hidden. We wait and see.

Regards.

---

### Post by sammiev on 2015-05-02
> **grahammechanical said:**
> I have been re-reading the Reddit conversation between Will Cook and the author of webupd8 and this is what I see:



I keep in mind that only taxes and death are certain, nontheless it seems that there will be two branches of U+1 to test over the coming year. When development is done in the open, then we notice the false starts that would otherwise be hidden. We wait and see.

Regards.

Great read and Great find.

---

### Post by craig10x on 2015-05-02
Yep...i had read that ubuntu next would soon become ubuntu snappy and you should be getting 15.10 daily build isos during this development cycle...
With luck, it will be available for general consumption when 16.04 LTS is released and the general user will be able to choose between downloading ubuntu 16.04 LTS (same as before) or 16.04 LTS Snappy (the 'rolling" version)... :D

---

### Post by bennachie on 2015-05-03
**Witless Wallaby** would be more appropriate (for the animal, not the OS). I have to dodge dozens of the b------s on my way to work every morning.

---

### Post by ventrical on 2015-05-03
Whats that ol'e saying .. 'It don't mean a thing if you ain't got that spring .. do wah do wah do wahhh... :)

jk

Regards..

---

### Post by syntaxerror74 on 2015-05-03
> **bennachie said:**
> **Witless Wallaby** would be more appropriate (for the animal, not the OS). I have to dodge dozens of the b------s on my way to work every morning.

Haha ... or **Witless Wombat** (or even *Waucous Wombat *for the numerous Elmer fans on here). Yet another OZ animal, chums!

And what about the Waterbuck? It's an animal endemic to South Africa, the country where MarkS was born as well.

---

### Post by zika on 2015-05-29
At this moment my machine is saying: bye bye Vivid:```
:~$ cat /etc/lsb-release DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu Wily Werewolf (development branch)"
```I've caught first glimpse of WW while dist-upgrade is taking its course... ;)
Bigger job is going to be just (house)keeping PPAs in sync with this weekend decision of mine... ;)

---

### Post by MikeMecanic on 2015-05-29
Receive my best of luck Zika, because what's next door is the best Operating System Ubuntu ever built: Ubuntu 16.04 LTS

---

