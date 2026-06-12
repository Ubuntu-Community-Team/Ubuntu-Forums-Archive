---
title: "Gnome Entanglements"
date: 2006-10-20
forum: The Cafe
---

### Post by localuser on 2006-10-20
So, I removed the Firefox and Evolution packages using Synaptics Package Manager.  I then tried to open a Terminal and File Browser and got errors.  I also noticed that some items in the preferences menu disappeared.

When I went back into the package manager, I found that Gnome itself was removed as part of the Firefox/Evolution removal.  I know, I know, I should have paid more attention to the package dependencies, but I didn't.

When I reinstalled the Gnome package, both Firefox and Evolution were also reinstalled.

The question is why is Gnome tied so closely to Firefox and Evolution?  Shouldn't they be distinct and completely separate?

---

### Post by fuscia on 2006-10-20
i dumped evolution without a problem (i f***in' hate evolution).

---

### Post by ComplexNumber on 2006-10-20
>  The question is why is Gnome tied so closely to Firefox and Evolution?its not. its probably a ubuntu problem, not a gnome problem because i can uninstall both ok without affecting gnome much.

---

### Post by localuser on 2006-10-20
> **fuscia said:**
> i dumped evolution without a problem (i f***in' hate evolution).

Hmmmm...strange.  Which version are you running?

---

### Post by fuscia on 2006-10-20
> **localuser said:**
> Hmmmm...strange.  Which version are you running?

dapper, but i dumped it on breezy, as well.

---

### Post by Wolki on 2006-10-20
> **localuser said:**
> The question is why is Gnome tied so closely to Firefox and Evolution?  Shouldn't they be distinct and completely separate?

Evolution is part of GNOME. Some elements of Evolution have grown roots into the core, especially evolution-data-server which now serves data for much more than Evo itself. In edgy however, this seems to be removable more easily, at the cost of potentially losing functionality. The Evolution Frontend should removable without problems.

Firefox is not only Firefox, but also provides the gecko rendering engine. Every GNOME program that uses gecko - pretty much every program that renders HTML ever - thus depends on Firefox. A standalone Gecko is now available, but since Firefox can't use it yet it would double the amount of maintenance necessary for developers and packagers. With Firefox 3.0 (hopefully some time next year), this will likely be possible, and Firefox should be removable.

---

### Post by ComplexNumber on 2006-10-20
oh, i forgot to say. i agree with fuscia in that evolution is crap. i never use the beast. i prefer lighterweight and seperate apps to do the same job.

---

### Post by localuser on 2006-10-20
> **Wolki said:**
> The Evolution Frontend should removable without problems.

If I wanted to remove just the front end, which package would I mark?  When I mark the Evolution package for removal, I get a notice that states that both Gnome and Gnome Desktop Environment will be removed.  

I downloaded Firefox 2.0 and am getting conflicts with the 1.5 version that's part of the distro.  Is there any way to get rid of the old version and have the system use the new version?

---

### Post by Wolki on 2006-10-21
> **localuser said:**
> If I wanted to remove just the front end, which package would I mark?  When I mark the Evolution package for removal, I get a notice that states that both Gnome and Gnome Desktop Environment will be removed. 

Hm, that should work. Are you sure that they are not just metapackages?

> I downloaded Firefox 2.0 and am getting conflicts with the 1.5 version that's part of the distro.  Is there any way to get rid of the old version and have the system use the new version?

Basically no, since all programs using firefox would have to be adapted to the new version. You should be able to run a firefox entirely from your home though.
Edgy will have 2.0 too, so it might make more sense to just wait till next thursday and update, than traing to do that migration by hand.

---

### Post by localuser on 2006-10-21
Yes, it seems that you are correct Wolki.  I will wait for the new version.

But what of the upcoming (maybe) split from Firefox?  What if I won't want to use IceWeasel and will want to use Firefox.  Will I have a choice?

This all just seems a little strange and definitely surprising to me.  When Microsoft tied IE to their platform the world went into a tizzy, with the anti-Microsoft crowd up in arms, law suits by competitors, and a general "Microsoft is evil and this is why" mentality.

Now I find the exact same thing in Gnome.  I understand about the Gecko rendering engine and how important it is.  But I wonder how KDE handles this?

By they way, the fact that I can switch desktop environments is in itself a vast improvement over Windows.  So this isn't an anti Linux post by any stretch, but the tie-in of the desktop to a particular version of a particular browser is, in my very humble opinion, not a good design.

---

### Post by Wolki on 2006-10-21
> **localuser said:**
> 
Now I find the exact same thing in Gnome.  I understand about the Gecko rendering engine and how important it is.  But I wonder how KDE handles this?

They have their own html rendering engine, KHTML. It's also used by apple, with modifications.

> So this isn't an anti Linux post by any stretch, but the tie-in of the desktop to a particular version of a particular browser is, in my very humble opinion, not a good design.

It's not. You should be able to use either Seamonkey or Firefox, and in several different versions. It's a compile-time dependency, however, so you'd have to recompile the affected parts of your system.
(AFAIR some projects are removing Seamonkey support, because in prectice everyone is using firefox to provide gecko, but in theory it would be possible)

And yes, it's a questionable design to bundle a library and a browser in that way. Fixing it is on Mozilla's agenda, but it doesn't seem to be top priority.

---

### Post by .t. on 2006-10-21
I believe Ubuntu and Firefox should both be built against XULRunner, so that Firefox acts as a front-end, and can be removed easily. XULRunner is a set of libs, so GNOME shouldn't care if XULRunner was used and Firefox was removed. But that's not how it is...

---

### Post by jdong on 2006-10-21
XulRunner didn't stabilize to any appreciable degree while Edgy was in development... I see no reason why Edgy+1 wouldn't be XulRunner based.

---

### Post by localuser on 2006-10-22
Now when I try to remove Rhythmbox, I get a dependency with Gnome as well ](*,) 

Please tell me that I'm mistaken and that Gnome doesn't also require rhythmbox to be installed.

I think it may be time to move to KDE.

---

### Post by jdong on 2006-10-22
```

jdong@shuttle:~$ sudo  apt-get remove rhythmbox -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  rhythmbox ubuntu-desktop
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  rhythmbox ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Remv ubuntu-desktop [1.30]
Remv rhythmbox [0.9.6-0ubuntu4]

```

From what I see, no, ryhthmbox has no dependencies with GNOME. Nor does Evolution:

```

jdong@shuttle:~$ sudo  apt-get remove evolution -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  evolution-exchange evolution ubuntu-desktop evolution-plugins
  nautilus-sendto
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  evolution evolution-exchange evolution-plugins nautilus-sendto
  ubuntu-desktop
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Remv ubuntu-desktop [1.30]
Remv nautilus-sendto [0.7-2ubuntu6]
Remv evolution-plugins [2.8.1-0ubuntu4]
Remv evolution-exchange [2.8.1-0ubuntu1]
Remv evolution [2.8.1-0ubuntu4]

```

---

### Post by localuser on 2006-10-22
Well then, what's different about using the Package Manager?  I went forward with the removal thinking that it wouldn't possibly remove Gnome, but alas and alack, it absolutely did.

[ATTACH]17998[/ATTACH]

[ATTACH]17999[/ATTACH]

---

### Post by .t. on 2006-10-22
Those are just metapackages. It doesn't matter if they're removed.

---

### Post by Rui Pais on 2006-10-22
hi, either gnome and gnome-desktop-environment are metapackages.
You can remove them safety with either apt-get or synaptic (they wont' remove nothing).

btw i think those 2 specifically are deprecated metapackages. You should use ubuntu-desktop instead of gnome + gnome-desktop-environment.

---

### Post by localuser on 2006-10-22
> You can remove them safety with either apt-get or synaptic (they wont' remove nothing).

> Those are just metapackages. It doesn't matter if they're removed.

Well, something mattered to the system, I'm afraid.

I too thought that nothing would be removed, but after the removal much of my functionality was removed as well.  For example, I could no longer start terminal, nor nautilus.

[Edit] I should have elaborated...I meant that I couldn't start nautilus browser.  I never tested any other part of nautilus.

---

### Post by Rui Pais on 2006-10-22
> **localuser said:**
> Well, something mattered to the system, I'm afraid.

I too thought that nothing would be removed, but after the removal much of my functionality was removed as well.  For example, I could no longer start terminal, nor nautilus.

try to remove those two (gnome and gnome-desktop-environment) and install ubuntu-desktop. That will ensure all gnome is ok.

Then uninstall ubuntu-desktop with apt-get or synaptic. After that you could uninstall evolution, firefox and rythmbox without problems.

---

### Post by prizrak on 2006-10-22
The deal with DE's vs WM's is the fact that they try to provide an integrated environment. That of course leads to interdependant applications. KDE is not different. The whole point is that if you choose Gnome for example when your system loads it will load most of the shared libraries with (aside from perhaps those that are not frequently used) so that when you open programs the only parts that are loaded are the ones that are unique. This decreases start up times and is generally better on resources.

---

### Post by .t. on 2006-10-22
I recommend to use aptitude over apt-get. It handles dependencies better. In your case, what probably happened was that apparently "unused" packages were removed...

---

### Post by Rui Pais on 2006-10-22
> **.t. said:**
> I recommend to use aptitude over apt-get. It handles dependencies better. In your case, what probably happened was that apparently "unused" packages were removed...

Exactly. I was tempted to suggest the same but one minor problem could appear. 

aptitude is better to install ubuntu-desktop, but to uninstall it later (only the metapackage) you should not use aptitude but apt-get or synaptic. 
aptitude remove will remove again all gnome (cause of course it keep track of all dependencies of the metapackage)

---

### Post by localuser on 2006-10-22
> **Rui Pais said:**
> ...Then uninstall ubuntu-desktop with apt-get or synaptic.

Should I assume that you meant to *install* ubuntu-desktop?

---

### Post by Rui Pais on 2006-10-22
> **localuser said:**
> Should I assume that you meant to *install* ubuntu-desktop?

First **install** to get all gnome correctly. (A metapackage is an enpty package with a list of recommended packages that are installed automaticaly) Aptitude is a better choice here.

_Then **uninstall**_ it with apt-get (there is a flag to aptitude i think to do the same but don't know exactly) to allow you to uninstall particular packages of that list :)

A metapackage is only need to install a full set of packages. Keep it after that only shorts your choice of install/remove apps.


Check this, do:
```
 apt-cache show ubuntu-desktop
```
and read the last paragraph of the output.

---

### Post by localuser on 2006-10-23
> **Rui Pais said:**
> First **install** to get all gnome correctly. (A metapackage is an enpty package with a list of recommended packages that are installed automaticaly) Aptitude is a better choice here.

_Then **uninstall**_ it with apt-get (there is a flag to aptitude i think to do the same but don't know exactly) to allow you to uninstall particular packages of that list

Okay, that did it.  Thanks.  Its somewhat of a convoluted way to do things and hardly intuitive, but it is what it is.

I was able to remove Rhythmbox and Evolution in this way, but Firefox must stay due to its dependencies.

---

### Post by nocturn on 2006-10-23
> **ComplexNumber said:**
> oh, i forgot to say. i agree with fuscia in that evolution is crap. i never use the beast. i prefer lighterweight and seperate apps to do the same job.

I love evolution, though I see your point.
But, as I use meeting requests, the line between appointments, mails and tasks is blurry.

The fact that it syncs perfectly to my palm is great.

But opinions differ off course.

---

### Post by Rui Pais on 2006-10-23
> **localuser said:**
> Okay, that did it.  Thanks.  Its somewhat of a convoluted way to do things and hardly intuitive, but it is what it is.
Glad it worked :)
It's a little twisted yes but it's a simple way of tied groups of packages for a purpose, a DE, a subset type of installation, all artwork related packages, etc... the boring part is name not being much explicit. 
And should exist a light version for gnome like Gentoo have.  

Don't forget that you need to reinstall ubuntu-desktop if you plan to upgrade for Edgy using aptitude or update-manager (if you forget a warning should appear asking for it) 
 
> I was able to remove Rhythmbox and Evolution in this way, but Firefox must stay due to its dependencies.

Yes, you are right. I uninstall firefox on previous version of ubuntu, but in dapper it removes a lot of other things (yelp, gnome-app-install, etc.) 
But you can have both version at same time. 
Just download from mozilla site and uncompress to /opt/ and make a starter on menus/desktop. It works ok here. I've got ubuntu version, swiftfox2 and portuguese firefox from mozilla site all side by side and they work flawless.

---

### Post by localuser on 2006-10-23
> **Rui Pais said:**
> I've got ubuntu version, swiftfox2 and portuguese firefox from mozilla site all side by side and they work flawless.

Yes, I've had Firefox 2.0 running in parallel but have found that occasionally (not often) the system will start up the 1.5 version rather than the 2.0 version when I click a link.  That's the reason I started looking into this whole thing in the first place.

In any case, thanks again for your insight.

---

### Post by Rui Pais on 2006-10-23
No problem. 
try this recommendations [here]("https://help.ubuntu.com/community/FirefoxNewVersion"). 
It's old howto for install ff 1.5 on 1.0.7 days but i think it's the same procedures for replace default 1.5 by the new 2.

Have fun.

---

### Post by prizrak on 2006-10-23
> **nocturn said:**
> I love evolution, though I see your point.
But, as I use meeting requests, the line between appointments, mails and tasks is blurry.

The fact that it syncs perfectly to my palm is great.

But opinions differ off course.
Evolution sux! 
REASON: It doesn't work with gmail. It makes no sense that it would not have the options necessary to setup a Gmail account. It's nothing but regular POP/SMTP protocols with secure connections/authentication. 

I suppose the good news is that Eudora Mail will from now on be based on Thunderbird, which means porting possibilities.

---

### Post by Wolki on 2006-10-23
> **prizrak said:**
> Evolution sux! 
REASON: It doesn't work with gmail. It makes no sense that it would not have the options necessary to setup a Gmail account. It's nothing but regular POP/SMTP protocols with secure connections/authentication. 

You must be doing something wrong then... Evo and gmail work together fine here.

[edit] or maybe I misunderstood you? I can't setup a gmail account from Evolution, I can only send and receive mail through it. Is there an email client where you can setup a gmail account?

---

