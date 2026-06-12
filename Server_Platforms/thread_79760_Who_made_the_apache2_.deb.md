---
title: "Who made the apache2 .deb ??"
date: 2005-10-20
forum: Server Platforms
---

### Post by dbee on 2005-10-20
I can't help thinking that whoever built the apache2.deb was playing a cruel joke on the rest of us. The .deb is an absoulte mess, for me the php mod doesn't work by default and the files are strewn all across my computer in completely obscure and counter-intuitive places.

They also seem to have renamed executables and they didn't see fit to include an installation description with their package. So the chances of finding anything approaches zero.

Sorry, I'm just venting here ... does anyone have the same problem ??

---

### Post by az on 2005-10-20
Did you install all the neccessary php packages?

libapache2-mod-php4

and a2enmod enables the modules you want.

---

### Post by LordHunter317 on 2005-10-20
[QUOTE=dbee]I can't help thinking that whoever built the apache2.deb was playing a cruel joke on the rest of us.[/quote]No, they're just packging software correctly.

> The .deb is an absoulte mess,No, it isn't.  Especially compared to the mess RH produces.

>  for me the php mod doesn't work by defaultI know this seems to be a common problem here, but I'd just like to note that I've never seen the module **not** be enabled correctly unless I'd played around in a way I knew I shouldn't have.

> and the files are strewn all across my computer in completely obscure and counter-intuitive places.They're exactly where they belong.  What do you find counter-intuitive?

> They also seem to have renamed executablesHow else do you support Apache2 and 1.3 on teh same distro?

> and they didn't see fit to include an installation description with their package. So the chances of finding anything approaches zero.Did you look at the documentation in /usr/share/doc/apache2?  

Actually, I know the answer to that is no.  Your rant would be a little more justified if you'd spent even a marginal amount of time trying the standard places for information.

---

### Post by dbee on 2005-10-20
Like I said earlier, this probably is just a rant. But I'm having some 'difficulties' with apache at the moment and the very strange install of the synaptic .deb isn't helping. It doesn't help either that I'm creating my own .debs at the same time but there you go I guess.

As per synaptic though, why is the apache executable all alone in /usr/lib ??
Why isn't there proper documentation in the synaptic-properties-installed files tab ??
Why does the LoadModule directive point to another LoadModule file on the system that is commented out by default ?
ETC...

I just find it a bit strange. Why not install apache to 

/usr/local/apache*

and put in a nice

/etc/init.d/apache*

and provide a working libphp

NB: just out of curiosity - where is the .deb for PHP5 ?
I'm configuring php myself anyway so I'm not too pushed one way or the other - just curious.

OK rant over ... thanks guys !!

---

### Post by LordHunter317 on 2005-10-20
[QUOTE=dbee] It doesn't help either that I'm creating my own .debs at the same time but there you go I guess.[/quote]No, it doesn't.  Describing in clear detail what you're trying to do and what exactly you did to accomplish would help you resolve your issues though.

> As per synaptic though, why is the apache executable all alone in /usr/lib ??It's not on my Debian box (I don't have a Ubuntu box to trivally check ATM).  What package are you looking at?

> Why isn't there proper documentation in the synaptic-properties-installed files tab ??I don't know what synaptic's problem is, but all packages must put at least a changelog and copyright file in /usr/share/doc/package.

> Why does the LoadModule directive point to another LoadModule file on the system that is commented out by default ?Because it makes module managment  far eaiser.  I don't have to edit a text file to install/uninstall modules, and it makes moving modules into other packages incredible easy, as they can just add/remove text files, instead of having to edit one nasty, monolithic file.

> /usr/local/apache*Because distributions aren't allowed to touch /usr/local, period.  No one does that. 

> and provide a working libphpBecause not everyone that runs Apache  wants php.  And as I've said, I've never had any problems with the provided PHP4 module or php4 packages, so I have troubles figuring out what everyone's issues are here.

You really ought to spend some time reading the Debian policy guides, which will give you a far deeper explanation as to why things are packaged the way they are.

---

### Post by dbee on 2005-10-21
I didn't know that the /usr/local was off limits to distro's. I think maybe you are right about me reading up on some Debian guidelines. 

But the fact that some things tend not to work straight off synaptic, and others have mods missing etc... tends to preclude me not building my own apache.

I find it all a little bit too complicated to be honest, but then I still haven't figured out how to use the vBulletin quote function, so maybe I'm not the best judge of how complex the system really is ... :smile:

---

### Post by LordHunter317 on 2005-10-21
[QUOTE=dbee]But the fact that some things tend not to work straight off synaptic, and others have mods missing etc...[/quote]Debian and Ubuntu package more DSOs than anyone else for Apache.

> tends to preclude me not building my own apache.There's no need to build the apache core ever.  Debian's apache is setup to allow you to build DSOs.

---

### Post by SuperMike on 2005-11-25
LordHunter317,

You weren't having a problem with your libapache2-mod-php(x) file, were you? I was. I think there's a bug. I finally got it to work after multiple attempts to uninstall and reinstall. Here's my story and I hope it helps...

I think I'm seeing a pattern of an undocumented Ubuntu Breezy bug in PHP5 and PHP4 installs with the libapache2-mod-php4 or libapache2-mod-php5. If you uninstall and reinstall multiple times, you'll find that it just sort of works if you repeat the process several times. I had to repeat the same exact process like 5 times on my PC before it just worked. And when you uninstall PHP, it will warn you that libapache2-mod-php(x) didn't get installed in the first place, so it can't remove it.

My running theory here is that either there's a bug in the Canonical web farm with some of the mirror servers we're hitting. I cannot figure out any other reason why the libapache2-mod-php(x) would install one time and not another.

And if you do a search on ubuntuforums.org, you'll find that a lot of people are having this issue. The net effect of this is that even though you have installed Apache2, PHP(x), and libapache2-mod-php(x), and have cleared your Firefox cache, you find that Firefox still asks you what to do with the PHP file, instead of Apache2 pre-processing it at the server. This is because the libapache2-mod-php(x) is failing to be compiled and inserted properly into the Apache2 framework -- even though you can clearly see the various .conf files are properly updated and the libphp(x).so file is in the proper place.

I finally got my PHP4 to work in Breezy. A couple days ago, I also had my PHP5 working too. So it *can* be done. Just keep playing with Synaptic and the install, trying different ways to install it, or install just what you need first and add other extra PHP items you need as you go. You'll find if you keep fighting with it for like 4 hours, it finally just *works*, somehow.

I wish there was a way I could easily report this as a bug to be checked. If you all know where to post this, let me know. The bug can be easily reproduced. Just upgrade from Hoary (with a loaded PHP4 install) to Breezy, and then uninstall completely the PHP4 and/or PHP5. Then, reboot. Then, try to install PHP4 again with Universe option enabled. Or, for that matter, try on a separate PC to install PHP5 again. Both PHP4 and PHP5 will intermittently have the same issue of not compiling the libapache2-mod-php(x) file properly.

I'd also like to know how I can become a tester for Canonical's PHP installs. It sounds like they didn't test this very well and could stand to have a developer help them.

---

### Post by LordHunter317 on 2005-11-25
**SuperMike:** Even though you were trying to be helpful, please don't post the same post to several Apache threads ever again.  It makes the response(s) harder to find and the flow of all the conversations more difficult to follow.
[QUOTE=SuperMike]You weren't having a problem with your libapache2-mod-php(x) file, were you?[/quote]No, I'm not.

> I was. I think there's a bug.I don't, but I'd still love to see a header or TCP dump of what's happening here.

> And when you uninstall PHP, it will warn you that libapache2-mod-php(x) didn't get installed in the first place, so it can't remove it.What warning is this, as this could be really helpful.  Without seeing these messages, it's impossible to solve these sort of problems.

> My running theory here is that either there's a bug in the Canonical web farm with some of the mirror servers we're hitting. I cannot figure out any other reason why the libapache2-mod-php(x) would install one time and not another.Nope, that shouldn't be possible.  APT refuses to install a package that has an md5sum that doesn't match the package list.  This means that getting a broken package would be awefuly hard unless a mirror was compromised.

> This is because the libapache2-mod-php(x) is failing to be compiled and inserted properly into the Apache2 frameworkThat's impossible: it's already compiled, and if Apache couldn't load it, no PHP pages would work ever, if the server even started.

> I wish there was a way I could easily report this as a bug to be checked. If you all know where to post this, let me know. The bug can be easily reproduced.Show those messages you talked about.  From a dist-upgrade install, running an 'apt-get install apache2 libapache2-mod-php4' and then an immediate uninstall and posting the entire session would be a good start.

> I'd also like to know how I can become a tester for Canonical's PHP installs. It sounds like they didn't test this very well and could stand to have a developer help them.The packages in Universe are essentially Debian rebuilds, so no.  And you're no developer qualified to do the work.

---

### Post by SuperMike on 2005-11-25
Well, since there's an md5sum going on, I guess my theory about this or that Canonical server having an issue seems to be ruled out.

I'll try to find the time to take my PHP4, which appears to be working fine, and uninstall it and reinstall it, dumping out a report each time so that everyone can see how following a scientific method of installation and uninstallation leads to random results with this install until finally it just works.

---

### Post by Kronocide on 2005-11-26
Why can't debian distros install to /usr/local? Does that mean that the standard Apache dist from ASF is "bad"?

---

### Post by LordHunter317 on 2005-11-26
[QUOTE=Kronocide]Why can't debian distros install to /usr/local? Does that mean that the standard Apache dist from ASF is "bad"?[/QUOTE]/usr/local is reserved for software compiled by the system administrator.

Programs installed by a packaging system are to be installed into /usr, by the filesystem standard.

---

### Post by Kronocide on 2005-11-27
I see. So according to this principle it's proper that the ASF dist installs in /usr/local/apache2.

---

