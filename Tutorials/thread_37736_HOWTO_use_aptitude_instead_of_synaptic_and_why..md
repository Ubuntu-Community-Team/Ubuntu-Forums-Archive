---
title: "HOWTO: use aptitude instead of synaptic and why."
date: 2005-05-28
forum: Tutorials
---

### Post by tread on 2005-05-28
HOWTO: use aptitude instead of synaptic

What is aptitude?
Aptitude is a package manager for Debian and Debian based systems (similar to say, synaptic).

Why should you use aptitude over synaptic/apt-get?
The million dollar reason: it remembers dependencies downloaded to install a particular package and removes them automatically when you remove that package. Synaptic only gives you the history log, and apt-get not even that.
For example:
[I]
I install wmaker using synaptic, it installs libwraster along with it. 
I purge wmaker out using synaptic, it leaves libwraster. I have to manually search for it and uninstall.
[/I] 
Now this may not seem a big deal, but imagine if wmaker had 20 dependencies. 
On the other hand:
[I]
I install wmaker using aptitude, it installs libwraster with it.
I purge wmaker out using aptitude, it figures out libwraster isn't needed anymore, and gets rid of that too.
[/I]

Awesome, isn't it? :)
But I held back from using this rather nifty tool because I didn't want to learn how to use it. Now I can use it, at least to do simple tasks. So I thought I would share that knowledge.

aptitude can run in two modes:

[list=1]
[*]command line mode
I will not write about this, other than to say the commands stay like apt-get .. which means you get aptitude power with apt-get commands.
	For eg.,
	sudo aptitude install wmaker
         sudo aptitude update
         sudo aptitude upgrade

Note: to do a default upgrade, use the commandline above. Pressing U in the gui seems to do a smart upgrade, and that isn't something I always want.

[*]gui mode
You start this with: sudo aptitude

**f10**         : pulls down the menu
Note: it seems f10 pulls down the gnome-terminal menu. If you want to use f10, then you may need to turn off the gnome-terminal menu for the session. Alternately, just click on the aptitude menu, the mouse click works.
**q**	: quit
**u**	: updates package lists
**/**	: search for a package (firefox style)
**n**	: find next 
**f** : forget new packages, useful if you have a habit of peeking into new packages available after each update.

Once you have found your package,
**enter**: to see information about that package
**+**	: mark a package for install or upgrade
**-** (minus)	: mark a package for removal
**_**	 (underscore): mark a package for purging
**:**	: cancel any action on the selected package

**U**: to mark all upgradable packages (for upgrade :))
Once you have marked your changes,
**g**	: apply those changes

If you are in a screen which says displays package information, and you want to go back to the earlier screen, press **f6** or **q**.
[/list] 

Once you press **g**, all the changes get listed. You can modify any of the changes, and then press **g** again to finally apply marked changes. I'll keep adding to this HOWTO as I learn new things, and if you have any suggestions/tips/corrections please add to this thread .. I'll update this post.

---

### Post by Xian on 2005-05-28
[QUOTE=tread]Why should you use aptitude over synaptic/apt-get?
The million dollar reason: it remembers dependencies downloaded to install a particular package and removes them automatically when you remove that package. Synaptic only gives you the history log, and apt-get (as far as I know) not even that.[/QUOTE]
The million and and half dollar reason I'd say. :) Nice job.

---

### Post by tread on 2005-05-28
Thanks .. I had been putting off using aptitude because synaptic is so much easier. I don't think I'll be moving from aptitude for a while now though :)

---

### Post by kvidell on 2005-05-28
But I've removed stuff with apt-get before and it removes all of the stuff that came with the application as long as it's not needed by anything else.

Although, when you do an update in aptitude I will give you that it's a lot prettier if you have terminal colours enabled ;)
- Kev

---

### Post by tread on 2005-05-28
> But I've removed stuff with apt-get before and it removes all of the stuff that came with the application as long as it's not needed by anything else. 

Doesn't work for me then .. I have to remove (using the same wmaker example) libwraster manually.

---

### Post by kvidell on 2005-05-28
ooOoo.. You're right. weird. (I just tried wmaker)
I remember an asterisk removal being quite complete and getting rid of everything.

Odd.
- Kev

---

### Post by bobgreen5s on 2005-05-28
[QUOTE=tread]Why should you use aptitude over synaptic/apt-get?
The million dollar reason: it remembers dependencies downloaded to install a particular package and removes them automatically when you remove tahat package. Synaptic only gives you the history log, and apt-get (as far as I know) not even that. [/QUOTE]

Not to bash apitude but this might not always be a good thing. Lets say you install package **a** and **b** and package **a** and **b** required dependency **a**. If you decide you want to remove package **a** but keep package **b** then dependency **a** is removed so you won't be able to use package **b**. Correct me if I'm mistaken.

---

### Post by willis on 2005-05-28
i've always used apititude, i just find it fast and powerful,

aptitude will only uninstall packages if there aren't conflicts,

it's really easy to tweak various actions by pressing "g" to see what it will do, and then pressing "Esc" changing various packages and then pressing g again to see if you've fixed any inconsistencies etc...  it works really well, espieccally if you're running something like breezy where packages get messed around with a lot

---

### Post by escobar on 2005-06-13
[QUOTE=tread]HOWTO: use aptitude instead of synaptic

What is aptitude?
Aptitude is a package manager for Debian and Debian based systems (similar to say, synaptic).

Why should you use aptitude over synaptic/apt-get?
The million dollar reason: it remembers dependencies downloaded to install a particular package and removes them automatically when you remove that package. Synaptic only gives you the history log, and apt-get not even that.
For example:
[I]
I install wmaker using synaptic, it installs libwraster along with it. 
I purge wmaker out using synaptic, it leaves libwraster. I have to manually search for it and uninstall.
[/I] 
Now this may not seem a big deal, but imagine if wmaker had 20 dependencies. 
On the other hand:
[I]
I install wmaker using aptitude, it installs libwraster with it.
I purge wmaker out using aptitude, it figures out libwraster isn't needed anymore, and gets rid of that too.
[/I]

Awesome, isn't it? :)
But I held back from using this rather nifty tool because I didn't want to learn how to use it. Now I can use it, at least to do simple tasks. So I thought I would share that knowledge.

aptitude can run in two modes:

[list=1]
[*]command line mode
I will not write about this, other than to say the commands stay like apt-get .. which means you get aptitude power with apt-get commands.
	For eg.,
	sudo aptitude install wmaker
[*]gui mode
You start this with: sudo aptitude

**f10**         : pulls down the menu
**q**	: quit
**u**	: updates package lists
**/**	: search for a package (firefox style)
**n**	: find next 
**f** : forget new packages, useful if you have a habit of peeking into new packages available after each update.

Once you have found your package,
**enter**: to see information about that package
**+**	: mark a package for install or upgrade
**-** (minus)	: mark a package for removal
**_**	 (underscore): mark a package for purging
**:**	: cancel any action on the selected package

**U**: to mark all upgradable packages (for upgrade :))
Once you have marked your changes,
**g**	: apply those changes

If you are in a screen which says displays package information, and you want to go back to the earlier screen, press **f6** or **q**.
[/list] 

Once you press **g**, all the changes get listed. You can modify any of the changes, and then press **g** again to finally apply marked changes. I'll keep adding to this HOWTO as I learn new things, and if you have any suggestions/tips/corrections please add to this thread .. I'll update this post.[/QUOTE]

Hate to sound really stupid here. In Aptitude, what's the difference between purging and removing something? Does "purge" remove the dependencies installed with a given package, and "removal" ignore the dependencies but remove the packege itself?

---

### Post by tread on 2005-06-14
Purging removes the config files too, remove doesnt do that. For example, if you install a package and modify some settings remove will keep those changes while purge will get rid of them.

---

### Post by poofyhairguy on 2005-06-14
Here is the billion dollar question:

Is there a way to make Synaptic use aptitude?

---

### Post by tread on 2005-06-14
I doubt it. Both synaptic and aptitude are essentially fronts for apt-get .. synaptic doesn't create apt-get queries and just fire them .. it seems to use libapt-pkg (I'm guessing here, but it seems reasonable)

Maybe the smart packaging system might be better ?

---

### Post by mayco on 2005-06-14
[QUOTE=poofyhairguy]Here is the billion dollar question:

Is there a way to make Synaptic use aptitude?[/QUOTE]
 if you install deborphan, and configure a "Orphaned" filter in the custom view in synaptic, you can see the packages that have no dependencies. But don't just remove all packages there, it is possible that some of them are still neccesary...

---

### Post by Sniffer on 2005-06-14
Thks for letting me know of this one..really great...

Maybe breeze will come with aptitude instead :) 

Just an Idea :) 

Sniff

---

### Post by tread on 2005-06-15
aptitude already exists in your installation .. be it warty or hoary.

---

### Post by christgod on 2005-06-17
Is there a way to install a package from a different depository?
I want to install transcode, but the version from marillat depends on newer versions of libc, libavi etc. than those available in universe. Or should i just download another transcode version and install it manually?

---

### Post by tread on 2005-06-17
Well, you can add extra repositories to /etc/apt/sources.list. Check out the ubuntu unofficial guide ([http://ubuntuguide.org](http://ubuntuguide.org)) for information on how to add extra repos. 

That said, it is usually not a good idea to mix debian and ubuntu repositories any more .. if I want something that isn't in the ubuntu repos, I compile it from source.

---

### Post by Albaraha on 2005-07-08
[QUOTE=tread]
**f10**         : pulls down the menu[/QUOTE]

F10 open the File menu of gnome-terminal. So it's a conflicted shortcut between gnome-terminal and aptitude.

---

### Post by djrosen on 2005-07-09
I have been using aptitude per this thread for every install on a new installation (first post, current MDK user LOVING Ubuntu) All has been going very well. I just recently ran 

```
sudo aptitude install kubuntu-desktop
```
which went ok, but now everytime I run aptitude it wants to UNINSTALL all of KDE. for instance:

```
sinner@hades:~$ sudo aptitude install slrn
Password:
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following packages are unused and will be REMOVED:
  amarok amarok-arts arj arts artsbuilder dcoprss gwenview juk k3b k3blibs
  kaddressbook kaffeine kalarm kappfinder karm kate kaudiocreator kcalc
  kcharselect kcontrol kcron kde-style-lipstik kdeadmin-kfile-plugins
  kdebase-bin kdebase-data kdegraphics kdegraphics-kfile-plugins
  kdemultimedia kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
  kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd
  kdepim-kfile-plugins kdepim-wizards kdeprint kdesktop kdm kfloppy kgamma
  kgpg khelpcenter kicker kitchensync klipper kmenuedit kmilo kmix kmrml
  knetworkconf knewsticker knode knotes kolourpaint konqueror-nsplugins
  konserve konsolekalendar kontact konversation kooka kopete korganizer
  kpager kpdf kpersonalizer kpf kpilot kppp krdc krfb kscd kscreensaver
  kscreensaver-xsavers ksim ksmserver ksnapshot ksplash ksvg ksync
  ksysguard ksysguardd ktnef kubuntu-default-settings kwalletmanager kwin
  kynaptic libarts1-audiofile libarts1-xine libcdio0 libflac++4 libgadu3
  libiso9660-0 libkgantt0 libkipi0 libkonq4 libkpimexchange1 libkscan1
  libmal1 librss1 libruby1.8 libsensors3 libsnmp-base libsnmp5 libsqlite3-0
  libtunepimp-bin libtunepimp2 libxcomposite1 ncompress networkstatus
  openoffice.org-kde poster psutils qca-tls ruby ruby1.8 secpolicy zoo
The following NEW packages will be automatically installed:
  libcanlock2
The following NEW packages will be installed:
  libcanlock2 slrn
0 packages upgraded, 2 newly installed, 117 to remove and 0 not upgraded.
Need to get 831kB of archives. After unpacking 202MB will be freed.
Do you want to continue? [Y/n/?]

```
Can this be fixed?

---

### Post by robertobech on 2005-07-09
Nice idea for a topic. I always wanted to learn how to use aptitude, but I always give up because I think it's too complicated. I hope more people contribute with tips here, so that we all can learn step-by-step how this thing works and its benefits.

---

### Post by geearf on 2005-07-10
I doubt, but as i don't know, is there a way to get something like Kynaptic working on aptitude (it does not have to be kynaptic).

Thanks for this howto.

---

### Post by tread on 2005-07-10
Did you choose to uninstall kubuntu-desktop? Or remove some package that will remove kubuntu-desktop?

If thats the case, aptitude seems to assume that the remaining packages arent needed either.
If I have to break some meta package, I resort to synaptic, but I wish I knew a better solution.
I'll try to find one, till then, if anyone has some more knowledge, feel free to share!

---

### Post by tread on 2005-07-10
Thanks for that info Albaraha. I never use the menu in gnome-terminal, so I didn't know that. I updated the first post to reflect that conflict.

---

### Post by tread on 2005-07-10
djrosen:
I guess your problem is, when you press "g" in aptitude, it shows that most packages will be uninstalled, right? Try to find the metapackage containing these (maybe kde) and then press ":" while that package is selected, at the screen where it is showing changes to be made.

This will cancel the change on the meta package, and then hopefully on the rest as well. Otherwise you may need to do that manually on all packages :(

---

### Post by djrosen on 2005-07-10
tread:

RE: 

> Did you choose to uninstall kubuntu-desktop? Or remove some package that will remove kubuntu-desktop?

If thats the case, aptitude seems to assume that the remaining packages arent needed either.
If I have to break some meta package, I resort to synaptic, but I wish I knew a better solution.
I'll try to find one, till then, if anyone has some more knowledge, feel free to share!

No, I did not try to uninstall kubuntu-desktop but any installtion states those packages arent needed and wants to remove them. 

RE:
> djrosen:
I guess your problem is, when you press "g" in aptitude, it shows that most packages will be uninstalled, right? Try to find the metapackage containing these (maybe kde) and then press ":" while that package is selected, at the screen where it is showing changes to be made.

This will cancel the change on the meta package, and then hopefully on the rest as well. Otherwise you may need to do that manually on all packages

Actually, I was using the command line  
```
sudo aptitude install <package>
```

I will give your suggestion a try next time. ](*,) 

On a side note, before I sent this post I was going to try and install pan to see how that went and I notice that aptitude reports 3 broken packages but synaptic reports 0 broken. Digging deeper reveals those are the firefox packages so I will leave that for another thread.

Thanks for your input thus far! :grin:

---

### Post by manicka on 2005-07-10
[QUOTE=tread]
Awesome, isn't it? :)
[/QUOTE]

Yes it is  \\:D/

---

### Post by manicka on 2005-07-14
[QUOTE=Albaraha]F10 open the File menu of gnome-terminal. So it's a conflicted shortcut between gnome-terminal and aptitude.[/QUOTE]
 I installed and now use xterminal as my default terminal emulator. xterminal allows you to disable the default f10 behaviour of opening the file menu, so that you can access the aptitude menus with the f10 key

---

### Post by duffman25 on 2005-07-14
[QUOTE=manicka]I installed and now use xterminal as my default terminal emulator. xterminal allows you to disable the default f10 behaviour of opening the file menu, so that you can access the aptitude menus with the f10 key[/QUOTE]

You can disable f10 behaviour on gnome-terminal aswell. It's in the edit menu->keyboard shorcuts (I'm figuring out the translation in english my ubuntu box is in spanish :P)

---

### Post by manicka on 2005-07-14
Thanks, missed that one :) (Your translation is perfect as well :) )

---

### Post by tread on 2005-07-31
djrosen: thought of one possible reason for your problem, and I think I should put it up here even if the question is really dated now.

One of the packages in kubuntu-desktop might be uninstallable or broken, that makes aptitude uninstall the whole of kubuntu-desktop since one dependency is failing. This appears to be standard aptitude behavior for any package with failing dependencies.

Could any aptitude-guru please corroborate?

---

### Post by flying_icarus on 2005-08-01
[QUOTE=tread]
Could any aptitude-guru please corroborate?[/QUOTE]

I'm just a begginer also, but what would happen if he tried to "aptitude install kde"?

If that would work (because of the dependency problems), maybe that would install all required kde packages (including the missing ones that cause the dependency problems).

And if kde metapackage draws in too much, maybe kdebase would be enough...

---

### Post by wbiggers on 2005-08-01
I, too, am just a beginner at this but here is what I have learned recently...

I use ubuntu (as opposed to kubuntu) and there is a similar package called ubuntu-desktop.  This is loaded on your system at install and is a way to basically call many other programs that the development community thought would be needed on a typical desktop.  It doesn't mean that ubuntu uses all these packages but rather that they are pre-loaded for your convenience.  I uninstalled openoffice 1.1.3 (so I could upgrade to 1.9.113) and basically just let 'desktop' uninstall but went through and manually verified the applications that I use are still there.

---

### Post by tread on 2005-08-01
Exactly, kubuntu-desktop is just a metapackage, and I guess so is kde. My theory is that some dependency of kubuntu-desktop was borked .. if the package kde doesn't have that dependency it should install fine. Synaptic would probably show the package as broken, but since aptitude does a little bit more, it would try to get rid of kubuntu-desktop thinking that it wont wory because of unresolved dependencies, and then get rid of the rest of the kde packages since they arent needed anymore.

I hope I'm making sense ..

---

### Post by flying_icarus on 2005-08-02
It makes good sense. ;)

Then why not try "aptitude reinstall kubuntu-desktop"? That should pull in all required packages back into place.

---

### Post by wbiggers on 2005-08-03
If you re-install kubuntu-desktop, it will put back the package you were originally trying to uninstall.

---

### Post by Trojan1313 on 2005-08-07
What if two programs have common dependencies? Will it notice that?

---

### Post by tread on 2005-08-07
Thats what apt does anyway. If two programs have the same dependencies, they will share those dependencies.

---

### Post by Trojan1313 on 2005-08-08
[QUOTE=tread]Thats what apt does anyway. If two programs have the same dependencies, they will share those dependencies.[/QUOTE]
 So if Program1 and Program2 use Dependency1 and you delete Program1, then Dependency1 won't disappear?

---

### Post by tread on 2005-08-08
Nope, it shouldn't disappear.

---

### Post by Joshua on 2005-08-23
So why doesn't Ubuntu use aptitude as the background program for it's "Add/Remove Programs" feature instead of apt-get or whatever it uses now?  It seems like a no brainer to me...

One thing that recently happened to me - I installed Quanta (a KDE program for web development).  I wanted to try it out even though I usually use Bluefish.  It downloaded like 17 dependencies.  After I decided I didn't like Quanta, I removed it but it only removed the "quanta" package.  I looked in my "Applications" menu and saw three new KDE programs.  So I found all three of them in the Synaptic GUI and removed them.  Again, there it only removed those three packages.  So unless I'm missing something, there are now 13 packages sitting on my computer not doing anything other than pissing me off and making me feel dirty.  I don't even know what they are, but I know they are hiding on my computer somewhere.

Ok, seriously, it's not really the big of a deal, but COME ON! this is a gripe I've always had with Windows.  Aptitude has been out for a long time now, so I don't understand why no distributions have jumped at this as a way to keep your system "clean."

---

### Post by reztho on 2005-08-24
Hi, i'm new here... I'm spanish so sorry for my english. 

        I just want to show you my problem. I have installed the kubuntu-desktop metapackage with aptitude and i've compiled the last version of k3b, so i tried to uninstall k3b and k3blibs with aptitude. 

And aptitude tries to remove the kubuntu-desktop metapackage too, that's normal for me but the problem is aptitude wants to remove all the programs which comes with the kubuntu-desktop metapackage too. 

Well, I can remove k3b and k3blibs with apt-get, and yes, apt-get uninstall the kubuntu-desktop metapackage but not the programs associated with the metapackage, like i want. But in this way everytime i use aptitude for other things, it wants to remove all the kubuntu-desktop programs, so the entire point of using aptitude for managing packages goes down for me  :?

Thanks in advance.

---

### Post by tread on 2005-08-26
> 
And aptitude tries to remove the kubuntu-desktop metapackage too, that's normal for me but the problem is aptitude wants to remove all the programs which comes with the kubuntu-desktop metapackage too.


Unfortunately, you are right. I suppose there might be an easy way to solve this, but I don't know.

---

### Post by Chozabu on 2006-06-24
hey yall
my aptitude also wanted to remove most of kde (and gnome, and a whole bunch of other stuff!)

after a little messin around (telling it to reinstall kubuntu-desktop etc) i gave up, told it to go ahead!
once it was done i did a lil
sudo aptitude install kubuntu-desktop eclipse superkaramba build-essential linux-k7 nvidia-glx
(the stuff i had seen go missing that i knew i wanted)

when i came back i restarted the computer and all was well :) (well, i used aptitudes gui to reinstall ogre3d, cegui and a bunch of other stuff i fergot about)

only things i notice missing are bagheira(spelling? osx theme for kde, but i was planning on uninstalling soon...) and codeblocks (ill be getting a nightly build again soon)

all in all, very nice, especaly because of the many gigs of unused packages (old libs and lil games i had jsut wanted to try out but CBA to remove) that were lying around

---

### Post by debiannerd on 2007-01-25
> **tread said:**
> Doesn't work for me then .. I have to remove (using the same wmaker example) libwraster manually.

of course next time, use apt-get --purge remove "name of the package"

apt does the same as synaptic, it's just a matter on how to use the commands

---

### Post by BobSongs on 2007-02-09
:idea: A little something to add to the tutorial to make it more "up-to-date". In Dapper Drake (6.06.x) **aptitude** in a command box allows for mouse interaction. No doubt this is true of most versions (Hoary, Warty, Breezy, Edgy and Fiesty). Use it as if it were a windowed application like Synaptic or Firefox. No need to disable terminal menus. Leave F10 out of the picture and use the mouse. :D

Honestly I find it a tad more pleasant to use a mouse in the terminal than F10 in a full screen. Either way works for me... just a personal preference. Here's where DOS experience and old Norton applications come in handy: they used to work this way.

Thanks for the tutorial. No doubt **aptitude** has its quirks. But that's why we use Linux. It's keeps us thinking.

**Edit:** Everything works mouse-wise, including the mouse-wheel. Really: try it, you won't be disappointed. It's totally mouse-friendly.

---

### Post by bubazoo on 2007-05-02
how do you use Aptitude to search?

I am in Aptitude now, and it lets me use the arrow keys to move around, The "search" is up at the top, but how do you get to it?  

I tried "S"  that didn't work,  whats they key to get to the search from the command line?

it just says "C-T Menu"

ok, well, which one of those keys, C-T is Search??? since its not "S"?

Tom

---

### Post by Darwin Award Winner on 2007-05-02
Um, can't you remove orphaned packages with apt-get? ```
sudo apt-get autoremove
```

---

### Post by mincho on 2007-05-02
407 Authentication Error ... Please Help Me.

---

### Post by 5-HT on 2007-05-03
> **bubazoo said:**
> how do you use Aptitude to search? 
 
From its ncurses interface:```
/
```
From the command line: ```
aptitude search <string>
```

[quote=Darwin Award Winner]Um, can't you remove orphaned packages with apt-get?[/quote] You can now, but its a relatively new feature.

---

### Post by dominikgeisler on 2007-12-02
> **Joshua said:**
> 
One thing that recently happened to me - I installed Quanta (a KDE program for web development).  I wanted to try it out even though I usually use Bluefish.  It downloaded like 17 dependencies.  After I decided I didn't like Quanta, I removed it but it only removed the "quanta" package.  I looked in my "Applications" menu and saw three new KDE programs.  So I found all three of them in the Synaptic GUI and removed them.  Again, there it only removed those three packages.  So unless I'm missing something, there are now 13 packages sitting on my computer not doing anything other than pissing me off and making me feel dirty.  I don't even know what they are, but I know they are hiding on my computer somewhere.


I understand the dirty feeling :)

"sudo aptitude install quanta" qields the following on my clean ubuntu 7.10:

```
The following NEW packages will be automatically installed:
  cervisia cvs docbook-defguide gettext kfilereplace klinkstatus kommander 
  kompare kxsldbg libcvsservice0 libtidy-0.99-0 quanta-data tidy 
The following NEW packages will be installed:
  cervisia cvs docbook-defguide gettext kfilereplace klinkstatus kommander 
  kompare kxsldbg libcvsservice0 libtidy-0.99-0 quanta quanta-data tidy 
0 packages upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.8MB of archives. After unpacking 48.4MB will be used.
Do you want to continue? [Y/n/?] 
```

Hope this will help you get rid of them. 

Greetz, 
Dominik

---

### Post by Brando569 on 2007-12-02
i only use aptitude when i cant remember commands for apt-get, otherwise i used synaptic :)

---

### Post by Ocxic on 2007-12-02
i never use aptitiude, tends to remove depedancies that i need for other programs, every time I've used it It's caused me problems

---

### Post by FredWP on 2008-08-20
Thank you.

This was still on my list of things to figure out (or later on if I couldn't figure it out by myself ask on community forums) but now it has been solved.

I'm using Debian, and so far (sadly) the Synaptic Package Manager in Etch does not support any feature to track if the dependencies are no longer used.

---

### Post by Ripose on 2008-08-20
If you uninstall something with Synaptic or you install something useless, Synaptic will show you.

In Synaptic click "STATUS" Is there a "_Not Installed (Residual Config)_" or "_Installed (Local or obsolete)_". If so it is usually stuff you can safely remove.

These choices will not even appear if there is nothing to remove, but may not list everything that could be removed. However I just wanted to let you know it exists.:)

---

### Post by narnie on 2010-03-06
> **Albaraha said:**
> F10 open the File menu of gnome-terminal. So it's a conflicted shortcut between gnome-terminal and aptitude.

You can use Ctrl-t to get the menus as an alternative to F10.

Other alternatives are to run aptitude in xterm or another terminal (I like to use rxvt for running these kind of apps, including midnight commander).

Yours,
Narnie

---

### Post by xxploit on 2010-03-13
Synaptic and apt-get can do what aptitude does. I think sometime in the past it was not so. But synaptic while not removing the depends will tag them under the autoremovable section or what not while apt-get will tell the the packages are no longder neeeded.

Also under apt-get you can easily accomplish the removal of an app by using apt-get --purge remove <appname> or
apt-get --purge autoremove

---

### Post by Kangarooo on 2010-05-22
That Kubuntu package installing and removing one of its programms wanting remove all Kubuntu is a little strange. Why then on installing clean Ubuntu/Xubuntu on removing one package doesnt remove Whole Ubuntu/Xubuntu ?

Actually i can understand that with aptitude package beeing removed witch was installed as dependecy with another package and therefore wants to remove whole package witch installed dependecy
i really can couse thats not what most of users aptitude.
most of them aptitude that installing package theyll have that what they install
programm aptitude is for human aptitude

and still is this bug happening by installing kubuntu-desktop and removing k3b also kubuntu-desktop is being removed?
maybe its fixed couse in synaptic i see kubuntu-desktop has k3b in recommends list and that list is also installed with all what is really needed for kubuntu-desktop in dependecy list

---

### Post by Nivedita.nair on 2010-10-21
Hi
I need a little help  regarding apt-get/aptitude update & upgrade.
I tried searching for the answer but couldn't find it out anywhere.
 
While performing upgrade on a package A, will the system keep a backup of the package before upgrade? If any failure occur during upgrade,will the system be able to boot from the backup code?
 
Thanks in advance!

---

### Post by Dean Wooldridge on 2011-12-06
> **tread said:**
> HOWTO: use aptitude instead of synaptic

Why should you use aptitude over synaptic/apt-get?

Simple. Because you can play Minesweeper while pulling down large packages :D

---

### Post by N00b-un-2 on 2011-12-06
I use the aptitude search function constantly!  I wish I could remove the stupid ubuntu software center, but of course the entire desktop is a dependency for some reason...
literally, ever since I think Ubuntu 10.04 when aptitude was no longer shipped with the default install, aptitude is the very first thing I install even before samba or ubuntu-restricted stuff.

---

