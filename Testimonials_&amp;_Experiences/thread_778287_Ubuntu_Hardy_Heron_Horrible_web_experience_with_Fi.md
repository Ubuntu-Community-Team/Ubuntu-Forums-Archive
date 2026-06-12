---
title: "Ubuntu Hardy Heron: Horrible web experience with Firefox, horrible experience"
date: 2008-05-01
forum: Testimonials &amp; Experiences
---

### Post by berlinbrown on 2008-05-01
Who do you blame?  Adobe Flash, Firefox, the Ubuntu version of FF?

I don't know; but I would just like to say, the bugs with firefox make for a horrible web experience, a horrible experience over all.

From reading the forums, it looks like flash might be the issue and the main culprit.

That is fine, but aren't the people that create Ubuntu big enough to give Adobe a call and try to work out the issue.

Sorry for the rant, but I am frustrated.  I don't think I have ever used a piece of software that has crashed 5 minutes after use and then opened up again to crash again.  What was my crime.  I don't know; clicking on links?

I know I will get flamed for this, but I just gave my honest opinion.  I have dealt with this issue for every FF upgrade since the early FF2 releases.  Every time, epic fail.

I even had FF3b5 from Mozilla's site and I deleted it, thinking the Heron version would have better integration.  That was a big mistake.

Anybody, who is new to Ubuntu; there are going to be issues that the reporters won't tell you about.  Don't believe the hype.  Please, I am just trying to help you out.

I will continue to use Ubuntu, as I haven't owned a Windows system since 2000 or so; so I don't hate it overall, there are just aspects that certain products couldn't get away with.  I even posted about this on the ubuntu.brainstorms, along with a million other people.  I guess that didn't get through.

Back on topic; my issue is that FF on Heron sucks and I don't feel like going threw 500 browsers to browse the web. 

I will use Lynx or Emacs I guess.  I give up.

---

### Post by bikeboy on 2008-05-01
Do you have *libflashsupport* installed? That's known to increase crashes with Flash.

---

### Post by berlinbrown on 2008-05-01
I have no idea.  I did the heron upgrade; I haven't touched the configuration since those changes.

I probably had many revisions of the adobe nonfree plugin.

Let me waste my time with a fix that I know won't work.

---

### Post by IcemanV9 on 2008-05-02
You did not answer bikeboy's question. Anyway, libflashsupport is _known_ as the cause for the Firefox to exit unexpectedly.
```
sudo aptitude remove libflashsupport
```

---

### Post by berlinbrown on 2008-05-02
Reading state information... Done
Package libflashsupport is not installed, so not removed
The following packages were automatically installed and are no longer required:
  postgresql-client-8.2 postgresql-8.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Did that answer your question?

---

### Post by Saint Angeles on 2008-05-02
> **berlinbrown said:**
> Anybody, who is new to Ubuntu; there are going to be issues that the reporters won't tell you about.  Don't believe the hype.  Please, I am just trying to help you out.

This is complete FUD. please don't "help" anybody anymore. you aren't very good at it. just because a small percentage of hardy users are having trouble, it DOES NOT mean that everybody is going to have problems. lemme show you an example.

5% != 100%

see? 5 is not equal to a hundred.

you have a terrible immature attitude. somebody here tried to help you out with the libflashsupport thing and you replied like a smartass. now i don't see why anybody would WANT to help you. have a nice day.

---

### Post by Jack78 on 2008-05-02
I use Fx3b5 as the primary browser on 3 computers... my experience has been excellent so far.

---

### Post by MNICY on 2008-05-02
> **IcemanV9 said:**
> You did not answer bikeboy's question. Anyway, libflashsupport is _known_ as the cause for the Firefox to exit unexpectedly.
```
sudo aptitude remove libflashsupport
```

I wonder if that is why firefox locks up sometimes when im on youtube..
It only happens occasionally though - and it is not a big deal. Just kind of annoying. And by no means makes browsing hte internet in Ubuntu suck.

---

### Post by vikasmk on 2008-05-02
same here , firefox 3 crashed about 10 times, and i'm getting really frustrated with it , maybe devs shouldn't have put a beta version into a LTS version of ubuntu....

---

### Post by MNICY on 2008-05-02
Well, no..
I think firefox 3 beta is very stable. I have had much less crashes then on Internet Explorer on my windows PC in the time since i instlaled Hardy (and i use ubuntu much, much more then windows).

ANyway, this problem i am refering to happend in Firefox 2 in Feisty and Gutsy as well.

---

### Post by vexorian on 2008-05-02
To me;
Hardy + firefox 3b5 = good.
Hardy + compiz = sort of good
Hardy + firefox 3b5 + compiz = OMG wtf freezes every two minutes.

So, my answer was to disable compiz, also, you are not ellaborating at all, you are also very ambiguous, you don't say what sites make you crash, in one place you say that every release since FF2 has been bad for you but later you also say that this is only a problem with firefox on Hardy Heron

> I even posted about this on the ubuntu.brainstorms, along with a million other people.I am yet to find out what "this" means, also, you used brainstorm for a bug report, so don't be surprised if it gets ignored, it is also the case if you use use the ubuntuforums testimonials for so.

> same here , firefox 3 crashed about 10 times, and i'm getting really frustrated with it , maybe devs shouldn't have put a beta version into a LTS version of ubuntu....LTS means long term support, in other words it'll last for long without getting obsolete, for some reason people think it LTS means "ultimate stability since the beginning of its life cycle."

About periodic crashes, there's a file you can remove to fix it, the info is somewhere around these forums, search for firefox crash or something like that.

---

### Post by robertchahine on 2008-05-02
i'm permanantly using opera because a swf problem on my FF3beta5.
but i don't think you should blame even adobe or FF3, it might be a problem from pc (not the hardware), but maybe some configuration might be wrong like mine here :
[http://ubuntuforums.org/showthread.php?p=4863477#post4863477](http://ubuntuforums.org/showthread.php?p=4863477#post4863477)

---

### Post by IcemanV9 on 2008-05-02
@berlinbrown: Ok, since the libflashsupport is not installed. Then you need to investigate further to narrow down the problem that you were having with Firefox 3. In the terminal, type ...
```
firefox-3
```
that way you can see what spits out the error message. I believe you can figure it out from there on. Good luck.

---

### Post by markinhos_mrk on 2008-05-02
Well... I'm using ubuntu 8.04 since its RC1 release, and had many problems with Firefox & Flash, mainly sound-related... then i installed libflashsupport and now everything works fine! no lockups and stuff... go figure!

---

### Post by robertchahine on 2008-05-02
> **robertchahine said:**
> i'm permanantly using opera because a swf problem on my FF3beta5.
but i don't think you should blame even adobe or FF3, it might be a problem from pc (not the hardware), but maybe some configuration might be wrong like mine here :
[http://ubuntuforums.org/showthread.php?p=4863477#post4863477](http://ubuntuforums.org/showthread.php?p=4863477#post4863477)
now i fixed my problem, and the swf and FF3 works like a charm.
i think it's better that opera

---

### Post by bikeboy on 2008-05-02
Vexorian, I think what you're referring to at the end of your post could be the file *urlclassifier3.sqlite*. Some people are having intermittent (though regular at times) transient browser freezes that seem to be related to the size of this file blowing out.

The workaround is to disable phishing detection, but I can't remember which of the two option in the Security preferences you need to use.

---

