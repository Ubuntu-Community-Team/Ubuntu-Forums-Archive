---
title: "hercules rmx and mixxx"
date: 2008-08-04
forum: Ubuntu Studio
---

### Post by jocheem67 on 2008-08-04
Though I have my hercules rmx working as a soundcard and working with jack, I 'm not able to use the console as such. For that midi has to be in order, and that's where it goes wrong. Or not even wrong , I just don't know what to do next. There is supposed to be midi support for the rmx in hardy, through the package of libdjconsole, but I think this only applies to the hercules mk series.
I found a patch on the mixxx-devel pages, but I don't know how to apply it.
( Something with "udev" which is very new to me....)

Anyone who knows more about the rmx in ubuntu???

---

### Post by Stochastic on 2008-08-05
could you post the page you found the patch?

Edit: hmm I just found this page: [http://www.mail-archive.com/mixxx-devel@lists.sourceforge.net/msg00974.html](http://www.mail-archive.com/mixxx-devel@lists.sourceforge.net/msg00974.html) which suggests > Any beta3 package should work with the RMX
and hardy only has beta2 as it's default, so you need to download a newer version of mixxx from their website: [www.mixxx.org](www.mixxx.org)

---

### Post by jocheem67 on 2008-08-05
Actually I 've got the beta4 installed. I've seen the site you're referring to but I interpret it like one still needs to get midi working overall, or make a midi mapping or something.
In mixxx I cannot select the hercules rmx as a device but the "midi mapping" is selected.
I've been searching and found that one has to have libdjconsole installed which is in synaptic. doesn't help though.
No problems here with jack icm with mixxx though.

---

### Post by Stochastic on 2008-08-05
There's nothing in that page about midi mappings so I think you don't need to worry about that.  The directions given are very vague "apply the patch to udev" etc...

On this page: [http://www.mixxx.org/wiki/doku.php/hardware_compatibility](http://www.mixxx.org/wiki/doku.php/hardware_compatibility) it claims that the RMX needs a newer libdjconsole installed (currently it's the BZR version) that you can download by doing ```
bzr branch lp:libdjconsole
```
Here's the BZR page for libdjconsole: [https://code.launchpad.net/~libdjconsole/libdjconsole/trunk](https://code.launchpad.net/~libdjconsole/libdjconsole/trunk)

Eventually this controller will "just work", but because it was released recently, it takes a bit of time for the code to be incorporated into the repos.

---

### Post by jocheem67 on 2008-08-06
First of all, thanks for thinking with me on this thing.:)

As a matter of fact, I compiled the latest libdjconsole yesterday and after that --- what the heck -- the beta 4 of mixxx. Was not an easy thing to do by the way.Lots of not so clear dependencies.
Did not make mixxx "see" my hercules Rmx I'm afraid.
I found a tip on the mixxx forums to just use another mapping, and I found a little discussion on launchpad between the developers on the bugs with the new Rmx. It seems they provide a working connection in the final 1.6.0 release of mixxx. Just have to wait for that one then.

So okay, that's it then.

But still, you're saying that there's no need for some midi connection working on ubuntu?? Just to be clear...

---

### Post by Stochastic on 2008-08-06
> **jocheem67 said:**
> But still, you're saying that there's no need for some midi connection working on ubuntu?? Just to be clear...

From what I understand of the situation - probably many of the sources you've been looking at are much better educated on the matter - the controller is not driven through a midi route but rather a direct hardware layer (that libdjconsole provides).  I think that's a question for the mixxx mailing list to answer definitively.

---

### Post by jocheem67 on 2008-08-06
Okay I'll turn to those guys overthere....thanks.

---

### Post by jocheem67 on 2008-08-18
Just for the ones in a similar situation, or are thinking to get themselves a hercules rmx:

It's solved now, the howto is on the mixxx.org forums...
It's just a matter of adjusting a xml-file, and installing an up to date "libdjconsole"

So good news, and a not too complicated solution.

---

### Post by diskotek on 2008-08-27
i think it's working with mixxx 1.6
[http://mixxx.org/wiki/doku.php/hardware_compatibility](http://mixxx.org/wiki/doku.php/hardware_compatibility)

---

