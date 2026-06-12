---
title: "Do you have *buntu-desktop installed right now?"
date: 2007-05-18
forum: The Cafe
---

### Post by aysiu on 2007-05-18
Just wondering if people keep the default applications installed or not.

*buntu-desktop means...

*ubuntu-desktop* if you're using Ubuntu
*kubuntu-desktop* if you're using Kubuntu
*xubuntu-desktop* if you're using Xubuntu
*edubuntu-desktop* if you're using Edubuntu

From [the Wiki FAQ:](https://help.ubuntu.com/community/CommonQuestions#head-957d1f0d9534d9e9a43a1ade8e3622bc04a8d812) > **What is a meta-package? Is it safe to remove the ubuntu-desktop package?**
A meta-package is a package that doesn't contain applications within itself, but simply depends upon particular versions of other packages, so that when it is installed, it drags all of them in too. The package manager uses it to know which particular packages to install. For example, the ubuntu-desktop metapackage installs the full GNOME desktop environment, with all the other packages that are in a default Ubuntu install. The existence of meta-packages makes it very easy to install other Ubuntu derivatives on your desktop; see below for more information.

It is technically just fine to remove a meta-package, if required, and this shouldn't necessarily cause any problems. However, it is strongly recommended that you reinstall that package if you decide to manually upgrade to another version of Ubuntu. The package manager requires those packages to be installed for it to successfully perform the upgrade. 

I didn't include an option for "I use only the default applications, so I have no reason to even consider removing it." I guess if that applies to you, just choose "I keep it installed for some other reason (please explain)" instead.

---

### Post by earobinson on 2007-05-18
I have the ubuntu-desktop package installed yes if that is the question?

---

### Post by aysiu on 2007-05-18
> **earobinson said:**
> I have the ubuntu-desktop package installed yes if that is the question?
Yes, that's the question. I've edited my first post to clarify the question more.

---

### Post by earobinson on 2007-05-18
Why would you uninstall it? It really dose not take up much space.... 3.5 gigs or so.

---

### Post by aidanr on 2007-05-18
I don't have it installed because I wanted to remove some unused default applications

Not that I need the extra harddisk space, but at the same time I don't like the idea of just having those applications there if they're not going to be used

---

### Post by matthinckley on 2007-05-18
I do not have it installed only because i removed gaim when I installed pidgin..

one unrelated question: I understand why it removed ubuntu-desktop when I removed gaim.. but why did it also remove nautilus-send-to?

---

### Post by Happy_Man on 2007-05-18
I cannot live without Synaptic, and I'm too lazy to uninstall the rest. Actually, aysiu, your post has galvanized me into action: off I go! 

*wanders off to open up Konsole and run sudo aptitude remove ubuntu-desktop && sudo apt-get install synaptic*

---

### Post by ButteBlues on 2007-05-18
> **Happy_Man said:**
> I cannot live without Synaptic, and I'm too lazy to uninstall the rest. Actually, aysiu, your post has galvanized me into action: off I go! 

*wanders off to open up Konsole and run sudo aptitude remove ubuntu-desktop && sudo apt-get install synaptic*
I keep it installed so that I can make sure I get all necessary upgrades in Gutsy.

---

### Post by carlosqueso on 2007-05-18
I have xubuntu-desktop installed because I use the defaults for most things....so it's actually useful for me.

---

### Post by reacocard on 2007-05-18
I don't have it installed. I don't like to have applications that I don't use sitting around (GAIM, fspot, evolution), and I usually do a fresh install for each release. It's easier and less chancy than the upgrade, and with a separate /home partition it's a breeze to restore my settings afterwards.

---

### Post by juxtaposed on 2007-05-18
No (but not for any reason besides I am not using ubuntu).

But if I was, I probably wouldn't (unless it came by default) as I have heard bad things about metapackages...

---

### Post by moffatt666 on 2007-05-18
I have it installed partly because I CBA to remove it and partly because I still use a lot of default programs.

---

### Post by S29K on 2007-05-18
Nope. :)

The first thing I do after an upgrade is turf all the apps I don't use and the extra fonts, etc. that I don't need.  Specifically I get rid of the default audio/video apps in Ubuntu because I much prefer Amarok, K3B and Kaffeine.  Evolution is the next to go and Thunderbird takes it's place.  

Gaim, Ekiga, bittorrent, african/asian fonts, bluetooth support, brltty, compiz (eye-candy not required), deskbar, eog (need Acrobat Reader), gnome-pilot, vim, f-spot, pppoe, accessibility apps and tomboy all get the axe.

I add gthumb, bluefish, Java, mysql-query-browser, Adobe Reader (from Edgy), firefox plugins, audio codecs, wine (for work apps), and gftp.

I like to keep my installed packages as low as possible...less to keep updated so fewer updates.

---

### Post by aysiu on 2007-05-18
> **juxtaposed said:**
> No (but not for any reason besides I am not using ubuntu).

But if I was, I probably wouldn't (unless it came by default) as I have heard bad things about metapackages...
It does come by default. By the way, what bad things have you heard about metapackages? I'm just curious.

---

### Post by jariku on 2007-05-18
In my regular Feisty install, I have ubuntu-desktop installed, but I didn't bother installing it to my Ubuntu Studio install. Since I'm using the Ubuntu Studio computer for audio/video processing only, I decided I don't need all the stuff that comes with ubuntu-desktop, like Evolution, Rhythmbox, the games and so on.

---

### Post by shen-an-doah on 2007-05-18
I don't have it any more as it gets removed when Ubuntu Studio installs "ubuntustudio-desktop"...

---

### Post by PartisanEntity on 2007-05-18
I keep it installed because I did not know (until this thread, thank you aysiu) that you can remove it. However I will keep it as I have more than enough space and it will help to have a  smooth upgrade.

---

### Post by juxtaposed on 2007-05-18
> **aysiu said:**
> It does come by default. By the way, what bad things have you heard about metapackages? I'm just curious.

I am pretty sure this is the one... It's an apt-get vs aptitude discussion on the debian forums.

[http://forums.debian.net/viewtopic.php?t=14036](http://forums.debian.net/viewtopic.php?t=14036)

7 pages long though.

---

### Post by brentoboy on 2007-05-18
> **matthinckley said:**
> I do not have it installed only because i removed gaim when I installed pidgin..

one unrelated question: I understand why it removed ubuntu-desktop when I removed gaim.. but why did it also remove nautilus-send-to?

nautilus send to has gaim is one of the send to destinations. -- I think it should be a meta-package and each possible destination that gets removed shouldnt remove the overall send to option (of course, I dont actually know that removing one removes them all -- I never worried about it much)

it seems that the apps that get "cut" are much the same from person to person

gaim
evolution > thunderbird
brail support
bluetooth
ekiga
tomboy (anything based on mono, and all the libs)
anything based on gcj (gnu java)


I remove ubuntu-minimal because I dont need support for non-linux-native file systems on my linux only boxes. 

In fact, when I go to the meta-packages section in synaptic, I have none of them selected.  Which is not to say that I dont like metapackages.  But I think the ones that are in there by default are overly general to the point of not being helpful after day one.

I'd love to see several more specific metapackages...

bluetooth-support
printing-support
accessibility-support
restricted-codecs  (not illegal, just the "non-free" ones)
restricted-browser-plugins
palm-support
torrent-support
just-gnome  (only those apps that are essential for configuruing and maintaing a functional desktop -- this one probably exists)
debian-minimal (the package set that debian installs with a barebones installation)
ubuntu-community-citizen (launchpad integration, popularity contest... that kind of stuff)


Then, to go one step further, I'd like an easy way to dump the packages that are installed with a metapackage when I remove the metapackage.   For instance, when I remove bluetooth support, it could list all the packages it depends on, in a big list of checkboxes offering to remove the underlying apps.  much the same way that when you pull a dependency, it tells you what would be removed... but in this case, it wouldn't force remove them, it would only recommend, and offer the option to tweak the list.

I guess until I get there, I can use debfoster and deborphan to clean up my install after I pull all the excess stuff.

But I think that, more important than better metapackages, it would be nice if the ubuntu add remove packages "synaptic for newbies" application could remove things rather than just say "sorry, I cant remove that because ... well, its complicated."

After such a negative post, I almost feel I should say that I love Ubuntu because it has such powerful package management and such excellent defaults.   I only vent out all these ideas because you asked. and, all in all Ubuntu is the obvious leader in this particular arena anyway.

---

### Post by theicyj on 2007-05-18
I think there should be another option:  > I leave it installed because I find the default applications useful.   (Or something along those lines.)

---

### Post by brentoboy on 2007-05-18
> **S29K said:**
> Nope. :)

The first thing I do after an upgrade is turf all the apps I don't use and the extra fonts, etc. that I don't need.  Specifically I get rid of the default audio/video apps in Ubuntu because I much prefer Amarok, K3B and Kaffeine.  Evolution is the next to go and Thunderbird takes it's place.  

Gaim, Ekiga, bittorrent, african/asian fonts, bluetooth support, brltty, compiz (eye-candy not required), deskbar, eog (need Acrobat Reader), gnome-pilot, vim, f-spot, pppoe, accessibility apps and tomboy all get the axe.

I add gthumb, bluefish, Java, mysql-query-browser, Adobe Reader (from Edgy), firefox plugins, audio codecs, wine (for work apps), and gftp.



that is almost the exact same list of hacks I do after a fresh install.  Except I dont add wine or gftp (nautilus built in ftp is good enough for me), and I leave vim in case... well Ive never needed it..

I dont add bluefish anymore either because I generally dont work websites anymore.

> 
I like to keep my installed packages as low as possible...less to keep updated so fewer updates.

And, I do it for the same reasons -- except I'll add one more: a package that isnt installed cant be exploited.  I actually got that reasoning from Az like a year ago when he said it was a good reason not to install build-essential by default.  After thinking about it, security risk or not, not having extra stuff is always more secure, so why leave stuff there you dont ever use.

---

### Post by jariku on 2007-05-18
> **brentoboy said:**
> restricted-browser-plugins
This one kind of already exists.

Here are the dependencies for **ubuntu-restricted-extras**:
[LIST]
[*]gstreamer0.10-plugins-ugly
[*]gstreamer0.10-plugins-ugly-multiverse
[*]msttcorefonts
[*]flashplugin-nonfree
[*]sun-java6-plugin
[/LIST]

---

### Post by aysiu on 2007-05-18
> **juxtaposed said:**
> I am pretty sure this is the one... It's an apt-get vs aptitude discussion on the debian forums.

[http://forums.debian.net/viewtopic.php?t=14036](http://forums.debian.net/viewtopic.php?t=14036)

7 pages long though.
I only skimmed through the thread (but I did skim through all seven pages). I didn't see anything bad about metapackages there--only bad things about how *aptitude* handles them.

---

### Post by juxtaposed on 2007-05-18
> **aysiu said:**
> I only skimmed through the thread (but I did skim through all seven pages). I didn't see anything bad about metapackages there--only bad things about how *aptitude* handles them.

Yea, it has alot of that, but I am pretty sure there is a bit there with a couple posts saying something like "while metapackages are good for newbies, I think we all agree it's best not to use them" or something.

I didn't want to post a link to a page and have someone read all 7 pages only to find it wasn't there, but I remember reading something like that, and I am pretty sure it was on that thread. I read it either yesterday or the day before.

---

### Post by ep2011 on 2007-05-18
I keep it installed because a few of the reasons:

- I have enough Hard Drive Space
- I use a lot of the default programs
- It makes upgrading easy

---

### Post by brentoboy on 2007-05-18
> **ep2011 said:**
> - It makes upgrading easy

I'm not entirely sure the metapackages are needed in order for upgrades to go easily.

when I jumped from breezy to dapper, update manager added lots of stuff that I didnt think belonged because I didnt have the metapackeges, but lots of the new stuff was added anyway....

and, the jump from edgy to feisty was really crazy (of cource, the servers were probably swamped) but it was going to take "9 days" do download all the new packages via update-manager using the little "update me" option.   When 9 days increased to 15 days, I grabbed the feisty cd via ktorrent, an hour later I cut the power and installed from CD (you cant back out of the update after it starts apt-getting packages, and the download time was rising instead of falling.

If your data is always on its own partiton, then the easiest (and fastest) way to update is to get a CD and do it that way, at least then all those packages are zipped down into a happy little squashed file system.  And, reinstalling via CD makes the argument for easier upgrade via meta-packages a little bit shaky.

oh, and I have one more metapackage idea to add to the list.... :)

arnie's-favorite-packages  (all the automatix stuff -- but that one will probably never make the official metapackage list.)

---

### Post by smbm on 2007-05-18
I removed it so I could uninstall some unwanted/needed stuff and just keep things how I like them.

---

### Post by steven8 on 2007-05-18
I chose for another reason, because there was no 'just because I like it' option.

---

### Post by aysiu on 2007-05-18
> **steven8 said:**
> I chose for another reason, because there was no 'just because I like it' option.
Sorry--my own bias came through in omitting that option.

---

### Post by RedSquirrel on 2007-05-18
I do the barebones install + Fluxbox. (Well, it's a LAMP server, so not *really* barebones, but pretty close.)

---

### Post by keithpeter on 2007-05-19
I use Xubuntu and I do have the Xubuntu Feisty desktop installed. But, I use OpenOffice a lot and I rarely use AbiWord or Gnumeric. 

Any chance of an 'advanced' install or upgrade option to select just the packages I need on top of a basic xorg/gdm/xubuntu install?

---

### Post by Arisna on 2007-05-19
I have plenty of hard drive space and use most/all of the default Kubuntu applications.  There's no reason for me to uninstall kubuntu-desktop.

---

### Post by enopepsoo on 2007-05-19
I generally install a lot of crap from the repos (games mostly), and eventually something wants to remove ubuntu-desktop.  I just let it happen.  It's never caused a problem.  And yes, I do clean installs when new releases come out (although I never ever used feisty except on da notebook).

---

### Post by mech7 on 2007-05-19
I needed to uninstall it i think because off PIDGIN i dont have any idea why 0_o

---

