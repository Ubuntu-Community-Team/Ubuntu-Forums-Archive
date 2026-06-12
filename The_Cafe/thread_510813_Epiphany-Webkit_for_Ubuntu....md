---
title: "Epiphany-Webkit for Ubuntu...?"
date: 2007-07-27
forum: The Cafe
---

### Post by kripkenstein on 2007-07-27
So, looks like a version of Epiphany that uses Webkit (instead of Firefox's Gecko) is very close to reality: [article on Ars]("http://arstechnica.com/journals/linux.ars/2007/07/26/using-epiphany-with-webkit?bub").

In the article there are links to details, as well as how to compile a very preliminary version. I got stuck somewhere in the process, sadly - will any brave soul succeed and post a .deb for the rest of us? :)

---

### Post by mrgnash on 2007-07-27
> There are still a number of bugs that in the WebKit GTK port. For instance, HTML frames are not yet supported--a deficiency that some might consider a feature.

:lolflag: Word to that.

Well I'd love to test this out if any ingenious soul can post a deb. The Epiphany project has endeared itself to me of late, and perhaps this move could bring some additional refinements to distinguish it further, and maybe even put it ahead, of its canine cousin.

---

### Post by Bou on 2007-07-27
Totally unrelated post, but do you Aussies know our national hottie Elsa Pataky?

---

### Post by mrgnash on 2007-07-27
> **Bou said:**
> Totally unrelated post, but do you Aussies know our national hottie Elsa Pataky?

Do you mean, 'how' do we know? I suspect most of my fellow Australians are not aware of Elsa's existence, but being an avid watcher of international cinema, I first saw Elsa in *Romasanta, la caza de la bestia*, and finding her quite winning, subsequently sought out her other films such as *Ninette* and *Beyond Reanimator*. I even sat through the otherwise unendurable *Snakes on a Plane* because she was in it.

Anyway, better not hijack the thread.

---

### Post by Spr0k3t on 2007-07-27
This would be like having konq for gnome... or so I'm guessing.  Does that mean Apple is finally giving back to it's new /roots/?

---

### Post by izanbardprince on 2007-07-27
Webkit wouldn't need to be ported back to Linux if Apple actually played nice and gave back to the KHTML source.

Instead they forked it in secret, made a full year's worth of code changes, then threw the K Desktop project an obscenely large monolithic patch, which contained so many code changes, that combined with the fact that Konqueror/KHTML had been in parallel development for that year, added up to make the code essentially worthless, after picking through the whole mess, they managed to incorporate a few significant patches back into KHTML, but nothing to bring it up to where Apple's Webkit is.

Apple has been pretty much doing the bare minimum amount they can possibly get away with to remain technically in compliance with the license of all the open source code they've hijacked.

---

### Post by mrgnash on 2007-07-27
> **izanbardprince said:**
> Webkit wouldn't need to be ported back to Linux if Apple actually played nice and gave back to the KHTML source.

Instead they forked it in secret, made a full year's worth of code changes, then threw the K Desktop project an obscenely large monolithic patch, which contained so many code changes, that combined with the fact that Konqueror/KHTML had been in parallel development for that year, added up to make the code essentially worthless, after picking through the whole mess, they managed to incorporate a few significant patches back into KHTML, but nothing to bring it up to where Apple's Webkit is.

Apple has been pretty much doing the bare minimum amount they can possibly get away with to remain technically in compliance with the license of all the open source code they've hijacked.

No big surprises there; Apple play the zero-sum game better than anyone.

---

### Post by kripkenstein on 2007-07-27
> **izanbardprince said:**
> Apple has been pretty much doing the bare minimum amount they can possibly get away with to remain technically in compliance with the license of all the open source code they've hijacked.

Yep, you can't trust a for-profit entity to do any otherwise. But the GPL license is strong enough to 'keep them honest'; Webkit is also GPL, and KDE is moving to use Webkit now. So all of Apple's work will benefit the FOSS community.

---

### Post by bonzodog on 2007-07-27
Yes, because KHTML is now part of webkit -- they announced that a merger is taking place soon.

So, this is interesting, as I would certainly be looking at this.

---

### Post by Extreme Coder on 2007-07-27
> **Spr0k3t said:**
> This would be like having konq for gnome... or so I'm guessing.  Does that mean Apple is finally giving back to it's new /roots/?
Apple has nothing to do with Epiphany having a WebKit version.

---

### Post by izanbardprince on 2007-07-28
I find it disguisting that the K Desktop project will be ditching all their hard work, giving up, and using Apple's Webkit.

---

### Post by runningwithscissors on 2007-07-28
> **izanbardprince said:**
> I find it disguisting that the K Desktop project will be ditching all their hard work, giving up, and using Apple's Webkit.
To be honest, I find it disgusting as well. They're mainly moving because Qt is incorporating webkit into its libraries.
So, a corporate love-in between Trolltech and Apple will have KDE move to WebKit. It would be interesting to know if the infrastructure for WebKit development is controlled by Apple or KDE.

---

### Post by luca.b on 2007-07-28
Don't spread FUD. The people who are working on Qt WebKit include Lars Knoll (the *creator* of KHTML) and Zack Rusin (the one who made the blog post about Apple's bad policies). Also if you read the Ars Technica article, it said that some of the features from KHTML need to be ported to WebKit before even thinking of a merger.
That said, I believe that Apple may have been forced to play nice after those lamentations, as they are number one at lock-in, even better than Microsoft.

---

### Post by tehkain on 2007-07-28
Webkit is still very much based off of khtml(tho long departed) so I feel it is great to merge the code base for a better KHTML of the future.. They are not 'ditching' all their hard work to go with a webkit. It does not make sense for the KHTML guys to advance current khtml when there is a good code base built on their own core that gives these features that they can mix in with their current base. It would be a waist development effort.

---

### Post by izanbardprince on 2007-07-28
It's not gonna work quit that well I'm afraid, thats what happens when you fork, you get years down the road and have two completely different products, essentially Apple has KHTML by the balls now.

---

### Post by Extreme Coder on 2007-07-28
> **izanbardprince said:**
> It's not gonna work quit that well I'm afraid, thats what happens when you fork, you get years down the road and have two completely different products, essentially Apple has KHTML by the balls now.
And Apple has KHTML 'by the balls now' because?
Because the things KHTML has and WebKit doesn't will be merged into it, so that KDE, Nokia, Trolltech and Apple will have a shared codebase?

---

### Post by ButteBlues on 2007-07-28
> **izanbardprince said:**
> It's not gonna work quit that well I'm afraid, thats what happens when you fork, you get years down the road and have two completely different products, essentially Apple has KHTML by the balls now.
Try reading the GPL some time.

---

### Post by uggeli on 2007-08-02
Do you think that this gtk port of webkit will be stable enough to hit in gutsys repos? After all for mediaplayer there is allready pagages for totem-gstreamer and totem-xine, so why not make epiphany-webkit allso available for browser?

---

### Post by d.e.hillshafer on 2007-08-02
This is exciting news, but the Gutsy feature freeze is August 16, just a few weeks away. Unless Epiphany-Webkit makes significant progress before then, I think it imprudent to allow it in Gutsy. After all, we don't even have a binary right now.

---

### Post by kripkenstein on 2007-08-03
Looks like there might be another way to run WebCore on Linux (except for Konqueror, of course), [OWB]("http://www.sand-labs.org/OWBAL_doc/index.html").

Perhaps Epiphany-WebCore could be made on this foundation? They have an abstraction layer that might be helpful.

---

### Post by uggeli on 2007-08-03
> **d.e.hillshafer said:**
> This is exciting news, but the Gutsy feature freeze is August 16, just a few weeks away. Unless Epiphany-Webkit makes significant progress before then, I think it imprudent to allow it in Gutsy. After all, we don't even have a binary right now.

Yea it's for Gutsy +1 more likely then. It's just that when there is exciting news like this, you can't help yourself for  being unpatient. But let's hope the best even if it is miracle if it comes true. :)

---

### Post by motang on 2007-08-12
Epiphany with Webkit would be cool to use.  Especially for us web developers who are Gnome fans. ;-)

---

### Post by argie on 2007-08-12
I'd love to have Epiphany with Webkit, or just any Gnome browser that can do shadows. I like shadows.

---

