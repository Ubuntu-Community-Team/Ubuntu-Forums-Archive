---
title: "Feature Complete or Obsolete?"
date: 2009-09-09
forum: The Cafe
---

### Post by sertse on 2009-09-09
What do you think of functional software which is no longer developed on? Do you think they should be removed because the project is dead, or kept because it works well? Is it a problem?

It got me wondering the other day because I have some apps which is no longer developed, yet it does what I need it to do, and in a way there no problem with it not developed any more, since it completed what it was originally made to do.

For me, it's wbar. It hasn't had a change since 2007 yet it set out to be a light, simple, pretty launch bar and it fulfils this role perfectly. It has done everything it needs to do, further development since really required.

Another case would be docker/trayer, which is intended to be a stand alone system tray, and it does this. There's nothing to developed on after, and hence unchanged in ages. Is this an issue? 

Or Mirage, a simple image viewer. It doesn't need to do anything else. It's complete. 

I found there is a tendency for maintainers to drop projects simply because it is not longer being developed. Imo, it is a bit unfortunate. Share your thoughts.  

(Note: I'm avoiding cases like xmms/xmms2 or Amarok because there an active upstream, even through the old version being dropped and the new version is a complete rewrite, which may or may not be better. That's another discussion.)

---

### Post by MikeTheC on 2009-09-09
There's a ton of CLI software out there for which there is effectively no development which are still quite useful, capable and compatible.

Of course, that's easier to pull off with text-mode software. GUI-based items are harder because there's a LOT more sitting between them and the system which can cause breakage.

But I'd say that as long as an app is compatible and sufficiently useful, it should be provided for the community's use.

---

### Post by yabbadabbadont on 2009-09-09
> **MikeTheC said:**
> But I'd say that as long as an app is compatible and sufficiently useful, it should be provided for the community's use.

This, and as long as it doesn't have any security issues, then it should stay.  Security issues in unmaintained software is the main reason I have seen for packages being dropped.

---

### Post by 3rdalbum on 2009-09-09
Pythoncard isn't maintained, but I get a lot of use out of it. It's not even feature-complete. Of course, the popularity-contest tells the Ubuntu developers what packages get installed, and so I guess if it goes one release without anyone downloading it, then it should be dumped.

---

### Post by joey-elijah on 2009-09-09
What an amazing thread title!!

---

### Post by schauerlich on 2009-09-09
I think what most people are afraid of is becoming dependent on software that is no longer developed, and then having some other software that it depends on or interacts with change. Then the program no longer does what it once did, and there's no developer to put out a patch. For instance, what if something changed in the X stack that made wbar not work anymore? Someone would have to adopt the project, or you'd have to use old builds of X, effectively giving you old, obsolete software that will eventually have the same problem with something else, etc.

---

### Post by 23meg on 2009-09-09
It depends on what you mean by "removed" (from where?), possible security impact per use scenario, and amount of investment in terms of learning effort and compatibility with other software.

[QUOTE=sertse]I found there is a tendency for maintainers to drop projects simply because it is not longer being developed. Imo, it is a bit unfortunate. [/QUOTE]

The only way to continue maintaining a project no longer being developed upstream is to *become* the de facto upstream, which can mean a workload a maintainer is not willing to or simply cannot take on.

---

### Post by Screwdriver0815 on 2009-09-09
isn't Rhythmbox replaced by Banshee in Karmic because Rhythmbox is no more developed?

why is it replaced? Is it for security reasons? Is Rhythmbox then at least still available in the repo?

But AFAIK Acidrip (its the best ripping program for me) for example is also not developed anymore but still exists in the repo...

---

### Post by 23meg on 2009-09-09
> **Screwdriver0815]isn't Rhythmbox replaced by Banshee in Karmic[/quote]

It isn't said:**
> because Rhythmbox is no more developed?

No, Rhythmbox is still being developed.

[QUOTE=Screwdriver0815  ]why is it replaced? Is it for security reasons? [/QUOTE]

Because the Desktop Team no longer thinks it's the best default application.

[QUOTE=Screwdriver0815  ]Is Rhythmbox then at least still available in the repo?[/QUOTE]

It will be.

---

### Post by chucky chuckaluck on 2009-09-09
if something works the way you want it to, you should be relieved that it's no longer being developed (less chance of them ruining it).

---

### Post by Screwdriver0815 on 2009-09-09
> **23meg said:**
> It isn't; the replacement was deferred.



No, Rhythmbox is still being developed.



Because the Desktop Team no longer thinks it's the best default application.



It will be.

okay, thanks for the clearification!

---

### Post by ynnhoj on 2009-09-09
> **chucky chuckaluck said:**
> if something works the way you want it to, you should be relieved that it's no longer being developed (less chance of them ruining it).
heh, very true. though it is nice if somebody is still keeping an eye out for potential security issues and/or bugs that pop up because of changes made to libraries/programs that are dependencies.

---

### Post by Ozor Mox on 2009-09-09
I don't see why the fact that some software is no longer developed should be a reason not to use it anymore. This is especially true if it is FOSS, since the code is still there, it hasn't disappeared.

I think sometimes people think they are forced to upgrade to newer things. Rhythmbox (when there was talk of development stopping), KDE 4 when that came out, the newest versions of Ubuntu... Why? If the older versions work, keep using them for now. Same also goes for buying new computers.

---

### Post by bluenova on 2009-09-09
Amarok 1.4? A stable music player used by 10,000's of people. It was removed from the repositories because the developers stopped working on it to focus on 2.0 which is currently feature-less in comparision.

I understand the worry regarding security and stale projects, but there are 1000's of apps in the repos which do not see active development yet they still remain in there. Seems to me it's one rule for some apps and another rule for others.

---

