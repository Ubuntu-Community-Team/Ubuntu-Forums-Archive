---
title: "ccsm cheap shot"
date: 2013-03-03
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-03-03
I just noticed in the  *new* ccsm the 'Wizard' option with the dialog box:

'wastes resources to create fancy particle system for wizard wannbes'

Some persons consider ccsm and it's effects as an assistive tecnology, especially for persons who are vision impaired.  I mean .. do the developers really have nothing better to do (like fix some major bugs) than to play with us like this ?

---

### Post by GameX2 on 2013-03-03
> **ventrical said:**
> I just noticed in the  *new* ccsm the 'Wizard' option with the dialog box:

'wastes resources to create fancy particle system for wizard wannbes'

Some persons consider ccsm and it's effects as an assistive tecnology, especially for persons who are vision impaired.  I mean .. do the developers really have nothing better to do (like fix some major bugs) than to play with us like this ?

The "Wizard" CCSM effect, from what I know, is Beta/Unstable for now, and is not part of the default CCSM installation.
Maybe it's now an official plugin, I don't know.  I guess it's developped by users like me and you - perhaps not the CCSM maintainers.  Just guessing.

---

### Post by ventrical on 2013-03-03
It's been a  long cycle. Mabey the devs are just bored. btw .. it works ! :) lol Now I got more 'razzle and dazzle' to show  new Ubuntu prospects.  I guess this is one of the surprises they were talking about early on in the cycle. :)

---

### Post by cariboo on 2013-03-03
What version are you using, as I have CCSM 0.9.9.0, here and I don't have any wizards of any sort. Could you possibly have proposed enabled?

---

### Post by Fitoschido on 2013-03-03
lol, well, AFAIK there are one or two community guys trying to revive some of the old Compiz&#8217;s plugins to the new codebase. :)

---

### Post by pqwoerituytrueiwoq on 2013-03-03
> **cariboo907 said:**
> What version are you using, as I have CCSM  0.9.9.0, here and I don't have any wizards of any sort. Could you  possibly have proposed enabled?i think it is in the non-default plugins, i tried it months ago it was amusing, but not useful/prstical

---

### Post by mc4man on 2013-03-03
From 4 yrs. ago -  showmouse > wizard
[http://forum.compiz.org/viewtopic.php?t=8846](http://forum.compiz.org/viewtopic.php?t=8846)

Same .xml back then as now
```
<plugin name="wizard" useBcop="true">
		<_short>Wizard</_short>
		<_long>Wastes resources to create fancy particle systems for wizard-wannabes :)</_long>
		<category>Effects</category>
```

---

### Post by rrnbtter on 2013-03-04
Greetings,
I expect that ccsm just like the kernel and most anything else regarding modern programming is modular. So that one feature is probably someones pet project. I'm thinking that even though we use these things as open source, those individual devs own copy rights on parts of that code. I'm thinking that the final features are more dependent on some individual efforts than corporate design. That is why some new things appear and old things may disappear or get better. This unmanagablity that we love is what commercial software devs hate. I say, keep your acceptance high and your expectations low and you will be happy. Just my Opinion.
P.S. 
And I'm happy!

---

### Post by ventrical on 2013-03-04
@cariboo907

  I have no idea how (proposed) repos  became enabled because I do not recall enabling them - but yes, proposed is enabled.

and...

---

### Post by ventrical on 2013-03-04
Here is the menu:

---

### Post by stinkeye on 2013-03-04
The wizard plugin is in the **compiz-plugins** package, which is not installed by default and includes wobbly windows, fire, water ,cube and
a few others.
Comes from the universe repo.

---

### Post by ventrical on 2013-03-04
> **stinkeye said:**
> The wizard plugin is in the **compiz-plugins** package, which is not installed by default and includes wobbly windows, fire, water ,cube and
a few others.
Comes from the universe repo.


Yes .. the extras..

---

### Post by stinkeye on 2013-03-04
Yeah, **compiz-plugins** replaced **compiz-plugins-extra** and I think 
Canonical only focus on the **compiz-plugins-default**.

---

### Post by ventrical on 2013-03-04
ahh yes.. just seen that .. compiz-plugins-extra now a transitional dummy pkg.

I think my point was missed :)  I was just making a note about the dialogue box when you hover over the 'wizard' icon on the menu.   I would just think that the devs might have better things to do like -fix some bugs  with SDC- :) lol

---

### Post by stinkeye on 2013-03-04
I see that now. Looks like a bit of a dig between developers.

---

### Post by ventrical on 2013-03-04
> **stinkeye said:**
> I see that now. Looks like a bit of a dig between developers.

Thank you !!!! Thats exactly it.  Point understood.

---

### Post by EgoGratis on 2013-03-04
> ccsm cheap shot

First i thought oh no what did the devs do now. What was removed and why will i not be able to use CCSM anymore. Then further i read the thread more and more i understood that after a long long time it looks like actually CCSM will gain a feature!

 [http://www.youtube.com/watch?v=JsRo2890sv4](http://www.youtube.com/watch?v=JsRo2890sv4)

Fantastic thing! Now only if GNOME devs would add some new cool feature to Nautilus handling the desktop like grid of icons and not a mess of icons or something like that. That would restore my faith in the project. ;)

---

### Post by ventrical on 2013-03-04
> **EgoGratis said:**
> First i thought oh no what did the devs do now. What was removed and why will i not be able to use CCSM anymore. Then further i read the thread more and more i understood that after a long long time it looks like actually CCSM will gain a feature!

 [http://www.youtube.com/watch?v=JsRo2890sv4](http://www.youtube.com/watch?v=JsRo2890sv4)

Fantastic thing! Now only if GNOME devs would add some new cool feature to Nautilus handling the desktop like grid of icons and not a mess of icons or something like that. That would restore my faith in the project. ;)

 Obviously wayland has proven to not be the cure all for the compositor problems and I more or less knew that they would eventually lean back on somthing that works, that being compiz for ubuntu unity desktop. Yes.. it is refreshing to see that there are still some willing to lay up some code for compiz. At this point , the current state of ubuntu+unity depends on it. As for the future .... maybe a trimed down version of compiz or even wayland.

---

### Post by EgoGratis on 2013-03-04
Actually i did try Weston, MPlayer and some HD videos few days back and it works just fine. Compiz probably should get Wayland backend or Weston should get more plugins and control panel. ;)

---

### Post by mc4man on 2013-03-04
Just to note - 
The description was penned by the person who created wizard plugin from the showmouse plugin & was done tonuge in cheek (read the link  I posted
Nothing to do with anybody, (dev or otherwise),  currently managing this or any plugin

---

### Post by ventrical on 2013-03-04
> **mc4man said:**
> Just to note - 
The description was penned by the person who created wizard plugin from the showmouse plugin & was done tonuge in cheek (read the link  I posted
Nothing to do with anybody, (dev or otherwise),  currently managing this or any plugin


Thanks for your point of veiw mac4man.

Where is the link?

---

### Post by zika on 2013-03-04
sorry, mea culpa...

---

### Post by ventrical on 2013-03-04
> **zika said:**
> sorry, mea culpa...


Why ... commng from you it is not a cheap shot at all. It is just your wrye and witty genius humour at it's best! :) lol

nice work btw ...even for us noob wizards.. hahaehaeheh  :)

---

### Post by EgoGratis on 2013-03-04
[https://wiki.ubuntu.com/UnityNextSpec](https://wiki.ubuntu.com/UnityNextSpec)

[https://wiki.ubuntu.com/MirSpec](https://wiki.ubuntu.com/MirSpec)

Looks like Compiz well we should enjoy it while it lasts. We will see how it ends up but Compiz and Files managing desktop and adding functionality to it well this will probably not happen.

---

### Post by ventrical on 2013-03-04
ahhhh .. Oct. 2013 ... legacy mode... can't wait ! :)  I thought this was legacy mode :) lol

---

### Post by mc4man on 2013-03-04
> **ventrical said:**
> Thanks for your point of veiw mac4man.

Where is the link?
No really a point of view, just the factual history so to speak
[http://ubuntuforums.org/showthread.php?t=2122023&p=12540203&viewfull=1#post12540203](http://ubuntuforums.org/showthread.php?t=2122023&p=12540203&viewfull=1#post12540203)

---

### Post by ventrical on 2013-03-04
yeah ... thanks for that. 4 years ago ?!  Never seen it once and I have had proposed repos enabled before .. so I am assuming that they put it up in the repos, took it down from the repos , then put it back up.. beats me!!?? I'm just a beta tester.  First time I have ever seen it. Unity and compiz are getting so much heat right now that maybe I just let this stuff slide too much. If the devs want to bring wayland on then they should just bring it on and stop fudging about it. Wayland, compiz, X , Mir ..  whatever ... let's rock.!

---

