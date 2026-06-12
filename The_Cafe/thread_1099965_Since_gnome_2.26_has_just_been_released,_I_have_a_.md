---
title: "Since gnome 2.26 has just been released, I have a question...."
date: 2009-03-18
forum: The Cafe
---

### Post by civillian on 2009-03-18
I was looking over the gnome 2.26 release notes (improved brasero etc etc) and I was wondering a couple of things. The first is:

How different is the stock gnome desktop to the ubutu desktop? (and which do you prefer?)
I only ask because I was listening to the back catalogue of lugradio and they mentioned that there were some differences and didn't elaborate, and having been 'raised' in linux as an ubuntu user (tried fedora, slackware; ubuntu came out on top) I have only really had experience with ubutntu desktops (some might see this as a shame..to some extent I do too) so I thought I'd ask you lovely people.

AND

If I was going to try debian (thought I might when I have time to fix issues with hardware etc), if I 'upgraded' to debian sid , what's the likelihood I'd run into frequent problems? It seems like an okay system, and I like the 'rolling release' style repos that it uses (in theory) but stability might be an issue...

Thanks!

---

### Post by smartboyathome on 2009-03-18
Look at a screenshot of Foresight Linux, and look at one of Ubuntu. That will easily tell you the differences, since Foresight Linux uses a stock GNOME.

---

### Post by civillian on 2009-03-18
Might have to try foresight out...looks quite nice (just afraid I'll miss the massive ubuntu repos ;_;)

---

### Post by smartboyathome on 2009-03-18
> **C!V!NT said:**
> Might have to try foresight out...looks quite nice (just afraid I'll miss the massive ubuntu repos ;_;)

You probably will, since their repos are quite small. Or... you could package for them. ;)

---

### Post by ssam on 2009-03-18
ubuntu's nautilus is set to browse by default, default gnome opens a new window for each folder.

---

### Post by civillian on 2009-03-18
I may give that a go actually...I'd like to get involved with packaging...it'd be nice to be involved in a distro thats not huge (ubuntu has been a bit har to get involved in since almost all the packages I can think of are bieng maintained :P)

---

### Post by civillian on 2009-03-18
> **ssam said:**
> ubuntu's nautilus is set to browse by default, default gnome opens a new window for each folder.

Thats because spatial filesystem browsing is a pain in the *** :3

---

### Post by Faolan84 on 2009-03-18
I never got the point of a spacial file browser. There is a reason why Windows dropped it in the 95 release and why MacOS also dropped it, and so did every other system. It's torture to use.

---

### Post by civillian on 2009-03-18
Maybse sysadmins like it...they like everything else to be difficult, why not their gui (when they use one...)
> identification based on spatial attributes is a very natural human ability, requiring little or no conscious thought. The ability to recognize and recall locations within the hierarchy based on the appearance and position of folder windows is the primary purpose of the spatial file manager. All of the "rules" and behaviors that define the spatial file manager are designed to ensure that the strengths of the visual/spatial recognition and recall abilities of the human brain are leveraged. The idea is that these abilities are more natural and require "less work" than other forms of recognition based on reading text, maintaining an awareness of "current working directory" (in a command-line environment, for example), relying on the memory of past actions, or any other non-spatial cues

also another reason. (But even MS acknowledge its hard to use XD)

Also, has anyone used foresight linux recently? I'm thinking of giving it a go (either install it alongside my ubuntu install when i install jaunty/debian (any thoughts on sid, people?) or in a vm)

---

### Post by 23meg on 2009-03-18
Live demo images of GNOME 2.26 (including VM images) are available at [http://torrent.gnome.org/](http://torrent.gnome.org/), which may give you an idea.

---

### Post by Kareeser on 2009-03-18
Looks fancy... but nothing really stands out. It seems like gnome.org finally made some of the applications normally bundled with Ubuntu, standard... like Brasero.

---

### Post by civillian on 2009-03-19
I've tried foresight linux with vmware player (I would have used qemu but it was too slow...and I tried virtualbox but it was changing network settings :S so I winped out and took the non-free route. It's not as configurable, but it works a treat as long as you have a blank vmware vmx....) and it seems fairly standard, not so sure about the green, but it just seems like a standard gnome desktop to me, with all the bits I'm familiar with in ubuntu (minus some of the nice config tools...).

---

### Post by esanchez on 2009-03-30
I was also wondering if there's a way so I can use Gnome 2.26 on Hardy Heron(8.04).

Best regards,
 -eduardo s.m.

---

### Post by gnomeuser on 2009-03-30
> **C!V!NT said:**
> I was looking over the gnome 2.26 release notes (improved brasero etc etc) and I was wondering a couple of things. The first is:

How different is the stock gnome desktop to the ubutu desktop? (and which do you prefer?)


I believe gnome uses the new volume applet whereas Ubuntu does not. Additionally Ubuntu feels the need to plaster links to Launchpad all over which I hate. Mostly since Launchpad is both confusing, proprietary and has a tendency to produce the worst amount of bug spam ever (why do I need 10 mails a day basically all informing me of duplicates, the real bug handling and information tracking drowns in useless crap this way - this is a horrible default setting especially since it does not appear that one can turn it off)

Another change is to the fast user switching applet, Ubuntu has made it the default presence and logout/halt entry. This change I rather like, but I wish they had done the work upstream like good Free Software citizens so everyone would have benefits from the debate and implementation instead of this Moses descending from on high bullcrap. 

Ubuntu also adds the Add/Remove applications entry, which ties into heavily dpkg dependent software. I really think this should be replaced upstream with a PackageKit based solution for everyone to enjoy. I believe work in ongoing to add this functionality at least Richard Hughes has been posting something along those lines. It would be nice to have This kind of thing upstream, another advantage would be that as an official blessed dependency, PackageKit would allow GNOME to do some cool integration by default to benefit all users (and potentially cutting down the amount of packages that would be needed to be installed by default for vendors).

Final big change is the notifications, Ubuntu famously did the same thing they did with FUSA here. I really really, if I could have one wish fulfilled, would want Ubuntu to play nice here and do their work upstream from the word go.

Aside that there has been a bit of rearranging in the menus compared to upstream. This largely is a good thing but falls short of solving the problem.

I prefer the upstream GNOME, but that is not to say that Ubuntu doesn't have some nice ideas. It's just that I think they should be the same thing, till they are, I will support upstream and encourage working with them whenever possible.

---

### Post by tdrusk on 2009-03-30
Another distro that uses pure gnome is Fedora if I am not mistaken.

Honestly, I love what Ubuntu has changed about Gnome and I am used to those changes. There is no point in me using a pure Gnome distro if I am fine with Ubuntu's dialect.

---

### Post by gnomeuser on 2009-03-30
> **tdrusk said:**
> Another distro that uses pure gnome is Fedora if I am not mistaken.


Fedora is quite close to upstream, you can go over the changes they apply via their CVS (cvs.fedoraproject.org/viewvc/rpms/<name>/devel). I won't put my hand in the fire to say it's 100% upstream but it's damn close, they do at least change defaults like the theme.

I think the way to see a truly vanilla GNOME is using the GNOME Developers Appliance (torrents.gnome.org I think).

---

### Post by chucky chuckaluck on 2009-03-30
i've only used gnome for any length of time in ubuntu and arch. for me, ubuntu comes with stuff i don't want like evolution (i use gmail), brllty (i'm not blind) and a bunch of other junk i don't need. if i try to get rid of any of it, that removal also causes the removal of the ubuntu-desktop meta package. if i ran *autoremove*, i'd end up losing everything that comes under that package (which is pretty much everything). of course, i could just do a minimal installation of ubuntu and then just add standard gnome, but i can do that in arch, as well. so, i guess ubuntu's gnome is really someone else's idea of how to set up gnome and what packages to use with it vs. setting it up for yourself and deciding what packages you want to use with it.

---

### Post by 23meg on 2009-03-30
[QUOTE=chucky chuckaluck]if i try to get rid of any of it, that removal also causes the removal of the ubuntu-desktop meta package.[/QUOTE]

When did you last try uninstalling those? APT has been using "Recommends" for default packages instead of "Depends" since Fesity (which is to say, for two years), in effect letting you remove default packages without uninstalling ubuntu-desktop, removing which is non-critical anyway and as opposed to the popular myth, won't cause problems with upgrades.

---

### Post by mcduck on 2009-03-30
> **Faolan Devyn Aodfin said:**
> I never got the point of a spacial file browser. There is a reason why Windows dropped it in the 95 release and why MacOS also dropped it, and so did every other system. It's torture to use.

Windows has never had a real spatial file manager. They did use many small windows, but missed most of the spatial metaphor and therefore all the good things about spatial file managers

I bet most people hate spatial file managers because they have bad memories from the half-way solution used in old Windows versions. :P

Since I started using Gnome I've found the spatial mode in Nautilus more and more into my liking. You just need to know the basic shortcuts and tricks (to avoid filling the screen with small windows) and you'll start to see all the benefits it has over browser-based file management.

Edit: I'd actually call the old windows file manager a browser without any browsing tools. It only got 1 of the four basic rules of Spatial file management right and failed miserably on all the others.

1. Each directory is represented by a single window. (This is what Windows did)
2. Each window is unambiguously and irrevocably tied to a single directory. (They failed this one)
3. All window/directory properties, like size, location, content zoom (and background, view style etc) are preserved (they failed this one)
4. Same directory can only be viewed in one window at a time (yep, failed this as well)

Failing on the 3rd rule was probably what made it so bad, as that pretty much takes away all the benefits of spatial file management.

---

### Post by Methuselah on 2009-03-30
Spatial file manager is OK, once you learn that you can easily open a folder while closing the previous one in a single click.
After that, it's pretty much second nature and can be faster since you just opt to retain the previous view or not with each click. So if you'll need to copy something back to a folder higher up in the tree you just retain it and drag from the new window.

I kept the default spatial system when I was using gnome on FreeBSD. However, on ubuntu I also leave it the way it is.

---

### Post by smartboyathome on 2009-03-30
> **esanchez said:**
> I was also wondering if there's a way so I can use Gnome 2.26 on Hardy Heron(8.04).

Best regards,
 -eduardo s.m.

You can try compiling it, but I have a feeling that it will be more work since GNOME requires newer stuff than what Hardy has. In all honesty, I would just recommend going with Jaunty if you really want 2.26.

---

### Post by CraigPaleo on 2009-03-30
Gnomeuser,

By doing the work upstream, do you mean submitting them directly to the Gnome project? Couldn't the Gnome devs just take it and incorporate Ubuntu's changes themselves, or did Ubuntu use a non-free license of some sort?

I do really like the new one-click shutdown/switch user menu that we got in Intrepid. Couldn't any other distro or Gnome itself easily adopt it?

---

### Post by CraigPaleo on 2009-03-30
Regarding the spatial file manager, I'm surprised that vanilla Gnome has this by default. It might be okay once one learns how to use it but the browser setup is more intuitive. It's easy to navigate without having to learn much of anything. It should be the default IMO, especially since Gnome has an emphasis on ease of use.

---

### Post by chucky chuckaluck on 2009-03-30
> **23meg said:**
> When did you last try uninstalling those? APT has been using "Recommends" for default packages instead of "Depends" since Fesity (which is to say, for two years), in effect letting you remove default packages without uninstalling ubuntu-desktop, removing which is non-critical anyway and as opposed to the popular myth, won't cause problems with upgrades.

it's been a while, i guess. so, if i did a standard installation of ubuntu now and did *sudo apt-get remove evolution* and then did *sudo apt-get autoremove* i wouldn't lose a bunch of things i didn't want to uninstall?

---

### Post by Tibuda on 2009-03-30
> **chucky chuckaluck said:**
> it's been a while, i guess. so, if i did a standard installation of ubuntu now and did *sudo apt-get remove evolution* and then did *sudo apt-get autoremove* i wouldn't lose a bunch of things i didn't want to uninstall?

```
$ sudo apt-get remove evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  evolution evolution-exchange evolution-plugins
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 13.5MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```
It didn't removed ubuntu-desktop

---

### Post by 23meg on 2009-03-30
> **chucky chuckaluck said:**
> it's been a while, i guess. so, if i did a standard installation of ubuntu now and did *sudo apt-get remove evolution* and then did *sudo apt-get autoremove* i wouldn't lose a bunch of things i didn't want to uninstall?

No.

---

### Post by chucky chuckaluck on 2009-03-30
well darn! thanks for the correction and my apologies for the inaccuracy.

---

### Post by mcduck on 2009-03-30
> **CraigPaleo said:**
> Regarding the spatial file manager, I'm surprised that vanilla Gnome has this by default. It might be okay once one learns how to use it but the browser setup is more intuitive. It's easy to navigate without having to learn much of anything. It should be the default IMO, especially since Gnome has an emphasis on ease of use.

Actually ease of use and intuitiveness are the main benefits spatial file managers have over browsers. (at least if you haven't been using browsers for al your life). The strict bond between a single directory and a single window makes understading the file system easier for people who are not familiar with computers. Things simply work more like they do in real life. That's why Gnome uses the spatial mode by default.

The only thing that might make things hard with spatial mode is the window clutter. Middle click solves that. Much simpler thing to learn than figuring out the way stuff is arranged into nested directories on your computer..

But this isn't probably the right thread to discuss different file management styles..

---

