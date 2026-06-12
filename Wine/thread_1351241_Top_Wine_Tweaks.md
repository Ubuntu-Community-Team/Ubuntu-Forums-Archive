---
title: "Top Wine Tweaks?"
date: 2009-12-10
forum: Wine
---

### Post by Intel91 on 2009-12-10
I've tried to find tutorials and lists online of the best, and most effective, wine tweaks. Tweaks that actually make a difference in running more apps better with less errors. I am including tweaks like .net that might make the difference between an app running or not at all. I don't care about size of the tweaks, I would just like to hear what people have to say about what tweaks they think are best. 

One more thing, is it uncommon for wine to not return your system specs? Every time I try and run 3D Mark 03 according to the appdb, it always gives me a system error, couldn't return the system specs. I am relatively confident my wine is broken, because other apps I used to use don't work anymore, in fact no 3D app works for me anymore. I am going to do a fresh install and check if that fixes it. The First paragraph is what is really important.

Thanks,
Intel

---

### Post by beastrace91 on 2009-12-10
In general the two things to do to get the most out of your Wine are to ensure you always have the latest Wine Version & driver version for your graphics card.

Beyond this most all performance tweaks are per-application (in fact some tweaks help some applications hurt others). Be sure to check the [AppDB](appdb.winehq.org/) regarding what ever application you are trying to run regarding further tweaks

Also remember not *everything* runs properly under Wine.

Regards,
~Jeff

---

### Post by Intel91 on 2009-12-10
Based on your posts and articles you seem to know fairly enough about wine. I have used it for awhile (maybe the same time since we are both 91s), but I know there are inherent differences between wine, and wine-based compatibility layers (for which people pay). I guess I am asking the quick question: Is there any way to close the gap? Source patches, anything? I haven't looked at the source code yet, I have been too busy writing my own stuff recently. I know a fair amount about wine, and how it works, I am just not above asking specialists a question like this. I've got a project coming out soon and I am trying to maximize efficiency of all areas, especially above my scope of knowledge.

Thanks,
Intel

---

### Post by beastrace91 on 2009-12-10
I guess I not 100% sure what exactly you are looking/asking for. Is there an easy way to make plain Wine 100% as effect/stable as something such as [Codeweaver](http://www.codeweavers.com/)'s [CXGames](http://www.codeweavers.com/products/cxgames/)? Not really, [Play on Linux](http://playonlinux.com/en/) is attempting to do so - however from personal experience I've found it doesn't really work much better than default Wine from an experienced user's standpoint.

Hope some of the above is helpful to what you where asking about...

Cheers,
~Jeff

---

### Post by HighCommander540 on 2009-12-10
> **Intel91 said:**
> Based on your posts and articles you seem to know fairly enough about wine. I have used it for awhile (maybe the same time since we are both 91s), but I know there are inherent differences between wine, and wine-based compatibility layers (for which people pay). I guess I am asking the quick question: Is there any way to close the gap? Source patches, anything? I haven't looked at the source code yet, I have been too busy writing my own stuff recently. I know a fair amount about wine, and how it works, I am just not above asking specialists a question like this. I've got a project coming out soon and I am trying to maximize efficiency of all areas, especially above my scope of knowledge.

Thanks,
Intel

If you are talking about making applications on Windows that you want to run well under Wine. It is best to try and not use so much proprietary Windows languages, like the .net's. Because those change a lot and Wine has not had much success in porting them (other than just having the users download the .dll's). You can always try to use the Wine libraries to compile a Linux version (as that is what the Wine project started as).

Other than that, there really aren't that big of gaps between Wine and the other Win-based applications. Because the others really just focus on a few programs they deem beneficial for making money. Like games or Office. They just make per-program tweaks that you can load separately. There is nothing really special about the other Wine-based apps.

> **beastrace91 said:**
> I guess I not 100% sure what exactly you are looking/asking for. Is there an easy way to make plain Wine 100% as effect/stable as something such as [Codeweaver](http://www.codeweavers.com/)'s [CXGames](http://www.codeweavers.com/products/cxgames/)? Not really, [Play on Linux](http://playonlinux.com/en/) is attempting to do so - however from personal experience I've found it doesn't really work much better than default Wine from an experienced user's standpoint.

Hope some of the above is helpful to what you where asking about...

Cheers,
~Jeff

Um, well actually on the CodeWeaver's note. Anything that CodeWeaver find they send the patches back to Wine. Pretty much anything they find that improves it, they tell the Wine developers about it. Not everything of course, because they are trying to make money. But if you actually look at the list of developers for CodeWeaver all of them actively release patches for Wine as well.

Now other platforms like Cedega or PlayOnLinux. They run there own stuff. Cedega more than PlayOnLinux, becaue Cedega split off a long time ago and make their own stuff.

PlayonLinux is just a free version of CodeWeaver's programs really.

---

### Post by beastrace91 on 2009-12-10
> **HighCommander540 said:**
> PlayonLinux is just a free version of CodeWeaver's programs really.

Not at all. Play on Linux is basically just a GUI front end for the already existing versions of Wine. While Codeweavers also provides a GUI like POL they also test their new releases against backwards compatibility (thus resulting in greater stability from release to release). Also Wine the current release of Crossover (8.x) is based on Wine 1.1.25 it has quite a few patches added to it to tweak performance in many common games that are run under Wine that they "support"

And yes Codeweavers does contribute code back to the Wine project - the also host WineHq.org and the head of the Wine project works for Codeweavers ;)

Cedega is a different story entirely... But that is a rant for a different day ;)

~Jeff

---

### Post by HighCommander540 on 2009-12-10
> **beastrace91 said:**
> Not at all. Play on Linux is basically just a GUI front end for the already existing versions of Wine. While Codeweavers also provides a GUI like POL they also test their new releases against backwards compatibility (thus resulting in greater stability from release to release). Also Wine the current release of Crossover (8.x) is based on Wine 1.1.25 it has quite a few patches added to it to tweak performance in many common games that are run under Wine that they "support"

And yes Codeweavers does contribute code back to the Wine project - the also host WineHq.org and the head of the Wine project works for Codeweavers ;)

Cedega is a different story entirely... But that is a rant for a different day ;)

~Jeff

Haha, yeah. Sorry, I didn't mean it is exactly the same. I should have clarified, I meant in the since that they both use the same basic principle versus just Wine. They implement different configs for each application that is installed. Yes, Crossover is way more advanced because they added a bunch of stuff to it.

Yup, that is why I like that dual-wine opportunity since Codeweaver and Wine are practically the same. Which is why Wine doesn't have a standard Mac distro release only Crossover. I think its cool that they do both.

Yeah, I agree on the cedega thing. I also really don't like them.

---

