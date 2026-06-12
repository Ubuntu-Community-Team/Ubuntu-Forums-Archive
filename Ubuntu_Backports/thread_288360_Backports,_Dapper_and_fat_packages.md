---
title: "Backports, Dapper and fat packages"
date: 2006-10-29
forum: Ubuntu Backports
---

### Post by calvinpriest on 2006-10-29
So it's not too surprising that Firefox 2.0 will not be backported to Dapper, given all the many interdependies associated with it.  Enough said -- it's just not going to happen.

HOWEVER, this brings up the age old problem of what typical users are supposed to do if they want the stability of a longer-term distribution (Dapper in this case) but want to install the new version of one of their favorite programs.

The solution we are recommending to people involves downloading from the Firefox site and following a HowTo to change program links, etc.

While this will work for people, it is off-putting and seems unnecessarily complicated, especially for recent Windows refugees who are used to having one simple method of installing software (though it admittedly involves a lot of mouse clicking).  There are lots of solutions to this problem out there -- Klik, script installers (like Firefox), Autopackage.  But why have a lot of different solutions, when apt works so well?

So here's my question...  Why can't we have a new repository for exactly these situations?  It would install all necessary (redundent) files and dependencies (just like the Firefix installer does), but as part of one big package, thus taking up extra space but not affecting other applications like a backport would.  The description of the repository in Synaptic and sources.list would make clear its downsides.  And to install these applications you'd have to specifically choose them (much like you used to specifically have to choose php5 over php4).  So in the case of Firefox 2 the package could be called firefox2.  When installed, the symlink for firefox would be overwritten to point to the new binary.

If the program ever did get backported, or if the person dist-upgrades, then this package would be removed.

Of course these packages would be big and inherently ugly because of their redundency, but that's what happens when someone follows the Firefox2 HowTo.

The repository could be called Fatports :-), or if that's not PC enough, maybe Nonintegrated or some such.

Any thoughts?  Am I missing something obvious?

---

### Post by yabbadabbadont on 2006-10-29
A simpler solution would be to just staticly link the package when it was compiled for inclusion in the "Fat Package Repo".  Then there is only one package to install and no deps to worry about.  Less likely to mess up the rest of the system that way too.

---

### Post by calvinpriest on 2006-10-29
Sounds good to me.

---

### Post by doundounba on 2006-10-31
This would be really fantastic.  Staticly linking binaries meant for inclusion in Fatports (as suggested above) seems like it would get around many dependency issues. Unless I am also missing something...

---

### Post by calvinpriest on 2006-11-07
The primary reason I suggested this is that it's clear to me that 6 month release cycles are not ideal for business environments.  You can never do enough testing, and a rapid release cycle makes quality control very very difficult.  The open source world has a lot of 6 and 12 month release cycles because of the decentralized nature of development and because geeks don't mind (or even prefer it).  But non-geeks prefer that things work as reliably as possible.

I hate to say it, but the traditional release model makes a lot of sense.  You want to be keep the base of your system stable for long periods of time, with maximum quality control when you do upgrade.  This is one thing that Mac and Windows have right.

And so Ubuntu has quite sensibly implemented their LTS model.  It's a great model, but it currently still has the shortcoming that backports are scarce.  And very popular applications like Firefox2 will never be backported because of dependency issues.

It just seems to me that there are a lot of very smart people involved in the Ubuntu project.  Let's do BETTER than the other distributions.  Let's offer a long-term release that is not only stable, but is also supported by up-to-date packages of popular apps.  It doesn't have to be every application.  If Ubuntu doesn't backport the latest xChat, not many will really care.  But if we want our stable release to be perceived as up-to-date, we do need to find a way for users to easily upgrade to Firefox 2 and other such headline-makers.

I don't suppose I am posting this in the most ideal of locations...  Anyone know where the that would be?

---

### Post by jdong on 2006-11-09
If you slot a firefox2 package by the firefox package, how do you remove firefox2 when time comes for the Edgy or Feisty or whatever upgrade?

Other than that, it's a good idea, and it's done with quite a few packages (think of gtk1 / 2)

---

### Post by calvinpriest on 2006-11-10
This is where my knowledge of the details of packaging may be a little shaky, so excuse me if I am off base on this, but please let me know...

My thought would be to have a firefox2 package in the next few releases which would be a dummy package pointing to the regular firefox package.  That would cause firefox2 to be removed and firefox back to normal.

If that isn't technically possible, could the ubuntu-desktop metapackage do the work of replacing firefox2 with firefox?

---

### Post by calvinpriest on 2006-11-18
It seems to me another option in implementing this is simply to include these "fat packages" in the existing Backports repositories.  If they are given unique names like Firefox2, for example (instead of Firefox), then they wouldn't be automatically installed.

The important thing is that LTS users have access to very popular packages like Firefox2 even if they don't lend themselves to the normal Backport packaging process.

So far, since no one has responded saying that this isn't technically possible, I'm assuming we are simply facing a resource shortage?  Too many packages, too little time?

I guess it depends on how serious Ubuntu is about it's LTS commitment.  There aren't many packages like Firefox2 which require this strategy.  Why not bite the bullet and do it?  

On the other hand, if there is an unsurmountable technical hurdle, it would be good to know what it is so other options can be considered...

---

### Post by jdong on 2006-11-18
As backports maintainer, the issues I still have with it are:

(1) Upgradability: I've yet to see a good solution for removing the Firefox 2.0 backport on upgrade to a future distribution. Not everyone uses the metapackages, so we can't rely on them. Not every upgrades with dist-upgrader, so we can't use that to do a manual override. It's possible to use a Conflicts: in Edgy/Feisty packages to deal with it, but that will likely violate parts of the packaging policy (but may be our only viable option)

(2) Plugin compatibility: /usr/lib/firefox/plugins is where plugins are installed by default. If we add a /usr/lib/firefox2/plugins, somehow all the plugins need to be aware of this location. There's no decent way to synchronize the two.

(3) Moving the existing firefox out of the way? If we install a firefox2, that still leaves the problem of /usr/bin/firefox pointing to default firefox, and a lot of programs are preconfigured to invoke /usr/bin/firefox as the browser, requiring user intervention.


There may also be other issues that I simply don't have the technical skills to foresee... Talking to Ian Jackson, the Firefox maintainer, about your idea might be your best bet. But I know with this current proposal, there's no way I can pitch this convincingly to core developers or the Tech board.

---

### Post by calvinpriest on 2006-11-19
Thanks for your detailed reply jdong.

Here are some thoughts on these issues:
1) I guess I don't understand why a "Conflicts" would violate packaging policy, but it sounds like the best choice.  As for ubuntu-desktop, we are recommending its use, and if someone doesn't have it installed before a dist-upgrade the worst that happens is that Firefox2 doesn't get removed and they have to remove it manually, or just allow it to hang around and take up space.  The taking up of wasted space is already happening on a much larger scale to anyone who uses apt/Synaptic instead of aptitude when they remove many packages (i.e., the majority of users).
2) What is done with php4/php5 are separate packages for additional modules.  It seems logical to do the same with Firefox2.  Have seperate Firefox2-plugins packages and install them in /usr/lib/Firefox2/plugins.  There could be one package that includes the most popular plugins (for simplicity) and additional packages for less popular ones, or it could be entirely granular.
3) I assumed in my proposal that /usr/bin/firefox would be changed to point to Firefox2.  Is there some reason this would be bad?  The Firefox libraries would still be in their normal place for those applications needing them.  If this doesn't work, an alternative might be to add an additional menu item for Firefox 2.0 and perhaps a post-install note telling the user that in order to run Firefox2 they will need to specifically choose it.  Anyone following the manual installation instructions would be in the same boat.

I think we need to keep in mind that even though this may not be a perfect solution, the alternative we are recommending is even more of a hack (installing the Firefox binaries).  Since it's in a non-supported repository already, and the user is having to take the additional step of selecting the Firefox2 package a certain amount of imperfection is not unreasonable to expect.

---

### Post by jdong on 2006-11-19
Your idea definitely has merit and if the developers cooperate, these are simple to sort out. I suggest you put something about this on the Tech Board agenda and attend a Tech Board meeting (or try to first talk it out with iwj and the other devs that attend to firefox) regarding this proposal.

The way it stands, the Backports repository is not allowed to accept packages that aren't direct descendants of the Ubuntu development repositories, so I can't handle it here, sorry :(


Good luck , and hope to see it go forward :)

---

