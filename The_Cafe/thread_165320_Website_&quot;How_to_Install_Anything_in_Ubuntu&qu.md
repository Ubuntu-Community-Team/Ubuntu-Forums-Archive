---
title: "Website: &quot;How to Install Anything in Ubuntu&quot;"
date: 2006-04-24
forum: The Cafe
---

### Post by mostwanted on 2006-04-24
I've created a guide that explores different ways of installing software in Ubuntu. It's aimed at newbies, is very graphical and hopefully also very easy to follow. You can find it at:

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by Reaver on 2006-04-24
Excellent guide! Thanks very much. A more in depth read is due later. From what i skimmed it might finally unravel the mysteries to me of the various ways of installing. :cool:

---

### Post by dermotti on 2006-04-24
Looks sexy!

---

### Post by mjm115 on 2006-04-24
This is very well written!  Thanks a lot.

---

### Post by pshnfry on 2006-04-24
Thanks, very readable and informative.

You mention the package "build-essential" but I couldn't find that (universe repositories enabled and searched after list updated).  Have I misread or missed a repository?

Cheers,

Peter.

---

### Post by Bloch on 2006-04-24
Good work. Deinitely needed. I'm sending a copy to a friend.
I see Dapper Drake will have an automatic installer for .deb packages: I was just now explaining dpkg -i to him, and I could see his face grow longer.

---

### Post by gr0kzer0 on 2006-04-24
> You mention the package "build-essential" but I couldn't find that (universe repositories enabled and searched after list updated). Have I misread or missed a repository?

It should definitely be there somewhere. When I installed build-essential, I didn't have  internet access, just the install CD that Canonical mailed me. But in Synaptic, build-essential was there on the list, and I just had to mark it for installation.

Maybe in terminal the command

```
sudo apt-get install build-essential
```

would do it for you?

---

### Post by pshnfry on 2006-04-24
My first apt-get!  Running now.  Thanks.

Peter.

---

### Post by dralaroc on 2006-04-24
Thanks man!  Just what I needed!

---

### Post by gr0kzer0 on 2006-04-24
Mostwanted: definitely a good idea. There's a lot of information around about installing the various packages (.deb, .rpm, tar.gz, etc) but, when I was learning how to do it, the info was here and there... didn't seem to be a "one-stop shop" to go to to learn how to install whatever from wherever.

And now, thanks to you, there is! What you gotta do now is make sure it's prominently and adequately linked to, so newbies can find out about it and use it. I'll put the link in my sig for sure.

---

### Post by mostwanted on 2006-04-24
[QUOTE=gr0kzer0]Mostwanted: definitely a good idea. There's a lot of information around about installing the various packages (.deb, .rpm, tar.gz, etc) but, when I was learning how to do it, the info was here and there... didn't seem to be a "one-stop shop" to go to to learn how to install whatever from wherever.

And now, thanks to you, there is! What you gotta do now is make sure it's prominently and adequately linked to, so newbies can find out about it and use it. I'll put the link in my sig for sure.[/QUOTE]

Good idea, I'll add it to my signature as well.

I plan to further develop the guide when I get the time, so autopackage and other more obscure formats are covered as well.

To everyone else: good to see it is of some use to someone :) I'd planned to make this guide a long time ago, but it wasn't until yesterday I started crafting it out.

---

### Post by Rinzwind on 2006-04-24
mostwanted: very clear story and you have a very nice way of explaining.

Some small additions that might be worth adding: where you speak about installing themes you can also add login screens, and screensavers.
And another addition might be gnome-art (system/prefrences/art manager) for THE place to go for backgrounds and themes.

Why do you tell us to "Forget all about Windows" and then refer 6 times to Windows.
I'd ditch those comments :)

---

### Post by Rinzwind on 2006-04-24
and I posted your webpage here:
[http://forum.fok.nl/topic/848008/1/50#37254768](http://forum.fok.nl/topic/848008/1/50#37254768)
It's a dutch forum with lots of linux newbies there :)

---

### Post by mostwanted on 2006-04-24
[QUOTE=Rinzwind]mostwanted: very clear story and you have a very nice way of explaining.

Some small additions that might be worth adding: where you speak about installing themes you can also add login screens, and screensavers.
And another addition might be gnome-art (system/prefrences/art manager) for THE place to go for backgrounds and themes.[/QUOTE]

Good idea. That'll probably come in the next revision.

[QUOTE=Rinzwind]Why do you tell us to "Forget all about Windows" and then refer 6 times to Windows.
I'd ditch those comments :)[/QUOTE]

Hehe, maybe I should edit that section a bit :p

---

### Post by aysiu on 2006-04-24
Love your guide.

Screenshots are always great for new users, and I think your explanations are good--solid step-by-step instructions.

Two things, though: 

1. You say > If the user carl wants to install an RPM called test.rpm located on his desktop, he will enter alien -i /home/carl/Desktop/test.rpm Since this tutorial is aimed at Ubuntu users, shouldn't it say ```
sudo alien -i /home/carl/Desktop/test.rpm
```?

2. I like the installing themes part, but it doesn't seem to go with installing software (which the rest of the page is dedicated to). Maybe it should have its own page in "How to customize Ubuntu"?

---

### Post by mostwanted on 2006-04-24
[QUOTE=aysiu]Love your guide.

Screenshots are always great for new users, and I think your explanations are good--solid step-by-step instructions.

Two things, though: 

1. You say  Since this tutorial is aimed at Ubuntu users, shouldn't it say ```
sudo alien -i /home/carl/Desktop/test.rpm
```?

2. I like the installing themes part, but it doesn't seem to go with installing software (which the rest of the page is dedicated to). Maybe it should have its own page in "How to customize Ubuntu"?[/QUOTE]

You're right about the alien thing, need to change that.

About the themes: I basically included them because otherwise new users could mistake them for being source code packages. Better to correct that assumption right there, than after trying to install it like a source package.

---

### Post by aysiu on 2006-04-24
[QUOTE=mostwanted]
About the themes: I basically included them because otherwise new users could mistake them for being source code packages. Better to correct that assumption right there, than after trying to install it like a source package.[/QUOTE] No, I get your point.

Maybe you could do something like a little tag at the end of the installing from source thing to say "If you have a .tar.gz that's a theme, read more here" and then link to a "How to customize Gnome" section? Well, I guess you have to have that section first!

Well, ultimately, it's your call.

---

### Post by engla on 2006-04-24
That looks sexy!

Just to try to improve this masterwork, I spotted two typos for you:
> You need to install the package called menu and **possible** restart X (ctrl + alt + **shift**) for it to show up.
Yeah, isn't it ctrl-alt-backspace? I don't want to test right now though.

---

### Post by Rinzwind on 2006-04-24
Yeah shift doesn't work :D (I tried ;) )

OH and I can think of 1 thing missing:

offline installation. 

Maybe you could you also add something about offline installation: downloading DEBs and adding cdrom to the sources.list and install from cdrom.

This is the place to download deb's but I don't know how big it ALL is and if it's possible to FTP all the files;
[http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

---

### Post by alvid on 2006-04-24
great guide.
thanks,
alvid

---

### Post by adamkane on 2006-04-24
Possibly need more warning about dpkg. 

A new user should never use dpkg without checking for dependencies first. Can a user use build-deps with dpkg? (I'm ignorant regarding this.) A new user shouldn't even know about dpkg really.

After a while autorepo should be used to handle a user's stray debs, but that's an intermediate topic.

You should also add a warning to new users that installing an rpm via alien will often not work as well as non-ubuntu deb files for that matter. This usually has to do with needed libraries not being installed, or not having the libraries in a place that the package knows where to look.

If you're advising new users how to install, then you should advise them how to uninstall as well. Uninstalling is an even weaker area than installing. 

Some advice on uninstalling automatix apps would be in order.

---

### Post by Biltong (Dee) on 2006-04-24
After downloading the opera.deb a couple of times and getting nowhere I gave up in disgust, figuring out that I really was a dumb blonde. (It's just hair dye I swear...)

Then I discovered the **ultimate guide**!!

I followed the instructions and now I too have seen the light - (and Opera, obtained by adding extra repositories)

Thank you for your time and effort!:)

---

### Post by confused57 on 2006-04-24
Great guide, thanks.  Wanted to get thread renewed, should be a helpful howto for anyone new to Ubuntu & needing to know installation guidelines in a very easy to follow graphical format.

---

### Post by user1397 on 2006-04-24
Really, really good guide, just one suggestion.

You should explain in the "Theme" part that you just have to drag and drop the compressed file, as in do not extract the file, and then drag and drop.

---

### Post by ncappel1 on 2006-04-24
Excellent guide, thank you very much for writing it. I will recommend it to people who need help installing packages.

---

### Post by catlett on 2006-04-24
Looks like I'll have a 2nd most used link in forums. First link is Automatix second is Monkeyblog. Great work!@!!!=D>

---

### Post by NeoGreen on 2006-04-24
Thanks:)

---

### Post by mostwanted on 2006-04-25
[QUOTE=adamkane]Possibly need more warning about dpkg. 

A new user should never use dpkg without checking for dependencies first. Can a user use build-deps with dpkg? (I'm ignorant regarding this.) A new user shouldn't even know about dpkg really.[/QUOTE]

I agree and that's why I first explain about Gdebi. In a couple of months everyone is going to be using Dapper anyway.

[QUOTE=adamkane]You should also add a warning to new users that installing an rpm via alien will often not work as well as non-ubuntu deb files for that matter. This usually has to do with needed libraries not being installed, or not having the libraries in a place that the package knows where to look.[/QUOTE]

I'm sure it does say that RPMs aren't guaranteed to work.

[QUOTE=adamkane]If you're advising new users how to install, then you should advise them how to uninstall as well. Uninstalling is an even weaker area than installing. 

Some advice on uninstalling automatix apps would be in order.[/QUOTE]

The guide is too general to explain about Automatix; Arnieboy will have to make such a page himself. Also, I don't approve of Automatix, I think it keeps newbies ignorant to a lot of things.

But something in the appendix about uninstalling debs and so on should be in order.

---

### Post by strider_am on 2006-04-26
Thanks A Lot Dude!! Very Well Written.

---

### Post by ubuntuuser on 2006-04-26
Nice work. I got one thing you might want to add: 
In your tutorial you mention gdebui, that will be in Dapper. For all those Breezy users out there who want to have a graphical way to install single debs. there is gdeb. Just type ```
sudo apt-get install gdeb gnome-apt
```and you have it. On my PC (and probably on most other PCs, too) the archive manager is set as default app for deb-packages. Right click on one .deb-file, then select properties -> Open with... and select gdeb instead.
Maybe this is worth mentioning in your tutorial, at least until dapper is out.

---

### Post by mostwanted on 2006-04-26
[QUOTE=ubuntuuser]Nice work. I got one thing you might want to add: 
In your tutorial you mention gdebui, that will be in Dapper. For all those Breezy users out there who want to have a graphical way to install single debs. there is gdeb. Just type ```
sudo apt-get install gdeb gnome-apt
```and you have it. On my PC (and probably on most other PCs, too) the archive manager is set as default app for deb-packages. Right click on one .deb-file, then select properties -> Open with... and select gdeb instead.
Maybe this is worth mentioning in your tutorial, at least until dapper is out.[/QUOTE]

Yes I know that there is a similar app in the Breezy repositories. I didn't add it because I wanted to have a simple explanation for each package type, but maybe I'll add a way to install it in the appendix.

---

### Post by engla on 2006-05-04
It is a very cool document. I've already posted that here, but I reread the document and I think it captures it all in a nice way and with the right priorities. So once again, good work!

I'm posting now though because I found I miss one thing.. the license. Why not smack on a  CC-BY-SA tag on that document (or other proper license that can make it distributable with Ubuntu) so that others can take this and distribute it. It's made to be read and used -- and perhaps make a derivate version for the upcoming versions of Ubuntu. Simply, it's in the spirit, it would be nice ;-)

---

### Post by mostwanted on 2006-09-23
My **crap** host somehow messed up the renewal of my domain name which means the site is unaccessible from the former domain name... I feel really bad about this =/

This temporary domain name leads to the same page:

[http://htmldesign.dk/blog3/ubuntu/installing/](http://htmldesign.dk/blog3/ubuntu/installing/)

Just FYI if you want to refer people to the page or maybe if you link to it in your signature.

---

### Post by Obor on 2006-09-23
good to know, I'm sending people there quite often. Are you gonna put it back on the old address in future?

---

### Post by mostwanted on 2006-09-23
As soon as my host fixes it. It's kinda out of my hands.

I've paid them money in the hosting plan to renew the domain several weeks ago, but they haven't done anything about it yet.

---

### Post by user1397 on 2006-09-28
this site: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) appears to no longer be working.  it takes you to some weird, suspicios looking website.  whatsup with this?  that site was a major help to all newcomers in ubuntu, and it would be devastating to lose such a guide.  it looks like the author put a lot of time and effort into making it so comprehensive.

so, wtf happened?

---

### Post by x64Jimbo on 2006-09-28
Looks like their domain expired and their hosting company put up a placeholder. Sorry, dude.

---

### Post by amohanty on 2006-09-28
> This domain name expired on Sep 21, 2006
Click here to renew it.

on the top right corner. sombody forgot a payment :)

AM

---

### Post by aysiu on 2006-09-28
It's temporary new home is here:
[http://htmldesign.dk/blog3/ubuntu/installing/](http://htmldesign.dk/blog3/ubuntu/installing/)

---

### Post by Sef on 2006-09-28
Thank you for the link, Aysiu.:D  I was tired of ](*,) because it had disappeared.

---

### Post by aysiu on 2006-09-28
Explanation [here](http://www.ubuntuforums.org/showthread.php?t=263425).

---

### Post by mostwanted on 2006-09-28
The communcation between me and the host is turning into a real farce. I was told, after they had forgot to renew the domain and it was already down, that it would take only 24 hours for it to be back up - 3 days have now gone by since I received that email.

I write them every day and ask what's taking so long and they are quick to reply "It should be fixed now, isn't it working on your computer?" and I go to the site and see that nothing has changed.

I'm thinking about cancelling the deal with them and ordering the domain through someone else, but I'm not sure how much additional delay that would add up to.

How can someone be so amateurish? Or is losing customers just a sport to them?

Anyway, I just wrote them a really angry email, hope that'll make shake them a little.

---

### Post by Josh1 on 2006-09-28
> **mostwanted said:**
> The communcation between me and the host is turning into a real farce. I was told, after they had forgot to renew the domain and it was already down, that it would take only 24 hours for it to be back up - 3 days have now gone by since I received that email.

I write them every day and ask what's taking so long and they are quick to reply "It should be fixed now, isn't it working on your computer?" and I go to the site and see that nothing has changed.

I'm thinking about cancelling the deal with them and ordering the domain through someone else, but I'm not sure how much additional delay that would add up to.

How can someone be so amateurish? Or is losing customers just a sport to them?

Anyway, I just wrote them a really angry email, hope that'll make shake them a little.

Whos the horrid host? Got to add it to my "hosts to never order".

---

### Post by Brunellus on 2006-09-28
> **Josh1 said:**
> Whos the horrid host? Got to add it to my "hosts to never order".
nice.  an ubuntu blacklist:  "Never buy from these vendors"

---

### Post by Josh1 on 2006-09-28
> **Brunellus said:**
> nice.  an ubuntu blacklist:  "Never buy from these vendors"

1) Microsoft :-D

---

### Post by aysiu on 2006-09-28
Not quite sure what you were paying or how many features you  need, but [ICDSoft](http://www.icdsoft.com/) has been a great host to me for years. That's where I host Psychocats.

---

### Post by user1397 on 2006-09-28
man, just to think about it, all those beginners here are going to a useless link, and following people's unintentionally mis-linked signatures!!!

its horrible!

i guess ill just keep my sig tho, since the page will prob be back up soon (even tho it doesnt sound like it!)

good luck mostwanted, all of us here are suffering too...

---

### Post by mostwanted on 2006-09-29
Ok, it's back up now!

In the next few days I'll see how many visitors I've lost, I reckon this affair has driven a great deal of them away >_>

---

### Post by user1397 on 2006-09-29
> **mostwanted said:**
> Ok, it's back up now!

In the next few days I'll see how many visitors I've lost, I reckon this affair has driven a great deal of them away >_>awesome man, i hope noone has changed their sigs because of this incident

---

### Post by fokuslee on 2007-01-02
How to install ANYTHING in Ubuntu!  Copy and Pasted b/c the site is down.  (i take no credit for any of these good work)  
featured in the guide titled 
Ubuntu Survival 101 (a newb's friendly guide to ubunt) [http://www.ubuntuforums.org/showthread.php?t=330206](http://www.ubuntuforums.org/showthread.php?t=330206)

A graphical guide for all newbies with a Windows background using Ubuntu

The Applications menuHaving trouble figuring out how to install anything in Ubuntu? Have you been thinking questions like these? "Where's the EXE?", "Where do I need to extract this to?", "How do I run it?", "Where did it go?", "Why is it so complicated?" Is it really? It's just as easy in Ubuntu as it is in Windows, only different, and that is what this guide will teach you all about.

    * The package manager
    * Installing software with Synaptic
          o The 3 steps: Search, mark and apply
          o But what if my program isn't available through Synaptic?
          o I installed it, but where did my program go?
          o How do I uninstall the program?
    * Installing software with the terminal
    * Installing a package manually (.deb, .rpm, .tar.gz, .sh, .bin, .exe, ...)
    * Appendix
          o Enabling extra repositories
          o Using CDs as offline repositories
          o Navigating the terminal
          o Adding a launcher/shortcut to your desktop

The package manager

Linux applications are almost all open source [1] and they're, unlike typical Windows programs, highly dependant on external libraries to work. You don't have to understand what libraries are, but just that Windows programs typically include parts of libraries in their installers, taking up lots of space after they've been installed because the same libraries have duplicates many places on your harddisk; Linux programs usually don't do this.

Most Linux operating systems have evolved a system where you can download the program, along with any needed dependencies, without having duplicates scattered all over your harddisk saving you lots of space. At the same time, this system allows you to have a central location from which to install and update packages. This system is called the package manager and on Ubuntu you'll meet it in the form of apt-get, aptitude, Add/Remove..., Update Manager and Synaptic. All these programs are frontends to the same package manager[2] built right into Ubuntu.
Installing software with Synaptic

Synaptic is a graphical program for installing packages and probably the one you'll feel the most comfortable with. You can launch it from System &#8594; Administration &#8594; Synaptic Package Manager (paths will vary depending on your locale, the System menu is the third menu on the menubar at the very top of your screen); as a safety precaution it will ask you for your password before proceeding! It's not because it's dangerous, Ubuntu is just very strict with trying to keep you, and more importantly, non-administrator users, from messing up your system.
Synaptic Package manager

The Synaptic Package Manager
The 3 steps: Search, mark and apply

   1. The Search icon in SynapticFirst you search for the package you want to install. Note that there are thousands of themes, applications, libaries and documentation available right away in Synaptic. All of these packages are located on the Ubuntu servers for you to download and update; the package manager essentially works like a kind of improved Windows update that will not only keep your operating system updated, but also all of the non-critical programs you've installed through it. You can find packages by looking for them inside the categories on the sidebar to the left or search for them. Click the search icon in the toolbar to search.
      The search popup in Synaptic

      The search popup that will pop up when you hit search
   2. When you've found the package you want to install, right-click on it and mark it to be installed. Most likely it will inform you of a bunch of dependencies that will also be installed in the same procedure; this is all being taken care of automatically! Note that you can also remove packages in the same way (right-clicking and selecting remove instead). Also note that you can mark more than one package to be installed, speeding up the install procedure significantly.
      Selecting a package for installation in Synaptic

      Selecting a package for installation in Synaptic
   3. The Apply icon in SynapticOnce you have marked all the packages you want to install, you can click the apply icon. This will download, install and set up everything! It's that easy.

But what if my program isn't available through Synaptic?

Trust me, it probably is. If it isn't, here are some of the reasons why it's not and how to fix it:

    * The Ubuntu package manager gets its package lists from the main Ubuntu repositories, but there are more repositories than just these default ones. There are even more official Ubuntu repositories! Try enabling extra repositories before you give up all hope!
    * If you're not connected to the Internet, you're not completely out of luck. There is a chance that your package is available on a CD.
    * Even if the package is not available in any repositories, you can still do the old Windows trick: installing it manually. But remember, there are more types of package-formats in Linux than you can think of. You might want to look at the explanation of how you go about installing a package manually.

I installed it, but where did my program go?

Usually your Applications menu is updated with a launcher to your new program, but sometimes this doesn't happen automatically. Here are some ways to find a link to your new program:

    * The Debian menuInstall the Debian menu. The Debian menu has a much more thorough list of your installed applications, and it will be available as a category in your existing Applications menu. You need to install the package called menu and possibly restart X (ctrl + alt + backspace) for it to show up.
    * They will very likely be available as a terminal command with the same name as the package. Try running the package name as a command in the terminal. Say I've installed the package muine[3] through Synaptic, then I open up the terminal and enter muine ending with a press on the return/enter key. Muine fires up. Note that the application will close when you close the terminal window! To avoid this behavior, press Alt + F2 and the Run Application window will show up; Type in muine to start it. Sometimes the command isn't called exactly the same as the package; try typing the beginning letters and then press tab twice. This will either give you the name of the command or a list of names to choose from.
    * Right-click on your package in Synaptic, select Properties from the menu and click on the tab labeled Installed Files. There will be a list of installed programs; the ones installed inside the folder /usr/bin are most likely the name(s) of the command(s).
      The properties of the music player Muine

      The installed files of the music player Muine

How do I uninstall the program?

When you want to remove a program, you do exactly the same as when installing - just select Mark for Removal instead of Mark for Installation in step 2. If you want to remove configuration files as well (maybe you want some weird modifications undone) select Mark for Complete Removal. Remember to apply the changes!
Installing software with the terminal

Very often, you'll see other Ubuntu users saying "You can install program ABC with this code ..." and then they'll provide you with a command you can input in the terminal. This not unlike what Synaptic does. In fact, Synaptic uses these commands below the friendly user interface! You can find the terminal at Applications &#8594; Accessories &#8594; Terminal. The two commands that you can use are:

sudo apt-get install ABC and sudo aptitude install ABC

ABC is just a fictious package in this case, not a real one. The sudo part of the command means you temporarily grant super-user/administrator rights to the command, provided you supply a correct user password. It's the same thing that happens when you open up Synaptic, only in the terminal instead! If you run aptitude by itself like this sudo aptitude, you get something that looks like a command-line version of Synaptic.
Aptitude package manager

The Aptitude user interface

It's also possible to search from the command-line like it is in Synaptic. Try this:

apt-cache search ABC or aptitude search ABC

To uninstall a package:

sudo apt-get remove ABC and sudo aptitude remove ABC

Removing configuration files as well:

sudo apt-get remove --purge ABC and sudo aptitude purge ABC

Though the command-line can be scary for new users, as you can see it's fairly simple and straight-forward to use and has many of the same features as Synaptic when it comes to installing software. Some users prefer installing software through the terminal, others don't. You decide for yourself what you like best.
Installing a package manually

Are you absolutely sure you can't find the package in Synaptic? Did you try enabling extra repositories? If you've tried all this with little or no success, here's how you do it the Windows-style way. Download a package (.deb, .rpm, .tar.gz, .sh, .bin, .exe) and let's have a look.
Installing a ...

Debian Package (.deb)
    When you download a program with the package manager, you actually download Debian packages! It's possible to install individual Debian packages you've downloaded yourself, but unless they're built specifically for Ubuntu, they're not guaranteed to work. Installing them is rather simple in Ubuntu 6.06 Dapper Drake: double-click the package in Nautilus or on your desktop and a package installer will show up:
    Gdebi Debian package installer

    The Debian Package installer (GDebI)
    You simply press Install Package to install. If you have a missing dependency, it will inform you of that. It will also inform you if there's a newer version available from the repositories!

    Another way to install a Debian package is to use the command dpkg which is what the package manager uses to manipulate Debian packages (or short: debs). The syntax is as follows: if your package is located on your desktop and your username is carl, then you install the package test.deb with dpkg -i /home/carl/Desktop/test.deb. You need to take care of dependencies yourself, so it's not the optimal way of installing software. 
RPM Package (.rpm)
    RPM is another popular way of packaging software, and it's used by popular distributions such as Fedora Core, SUSE Linux and Mandriva. RPM is not used by the Ubuntu Package Manager, but there does exist a command for converting an RPM into a Deb; this doesn't mean that any RPM will work on your system, though! The same program can also install the RPM directly so that you won't have to do this yourself. The command is not available right away so you'll need to install it yourself - the package is called alien and is of course available through Synaptic. If the user carl wants to install an RPM called test.rpm located on his desktop, he will enter sudo alien -i /home/carl/Desktop/test.rpm.
Desktop Theme (.tar, .tar.gz, .tgz, ...)
    Installing themes[4] is relatively painless in Gnome. You open the Theme Preferences which you'll find at System &#8594; Preferences &#8594; Theme. With this application you can change icons, controls and window borders to your liking. To install your theme, simply drag and drop the package onto the Theme Preferences window and confirm the dialog window that pops up. To use your new theme, edit one of the existing themes to use your new icons, controls or window borders.
    Installing a new desktop theme

    Click Install to install the new desktop theme
Login Screen Theme (.tar, .tar.gz, .tgz, ...)
    Installing themes for your login screen is as simple as installing desktop themes. You open up Login Window Preferences in System &#8594; Administration &#8594; Login Screen and drag and drop your theme onto the window. Confirm the dialog window that pops up. To use your new theme, select it in the list of themes.
    Installing a new login screen theme

    Click Install to install the new login screen theme
Source Package (.tar, .tar.gz, .tgz, ...)
    Sometimes all you've got is a package full of uncompiled source code. Luckily, you don't need to be a programmer to know how to compile and install a package with source code. Back in the old days, this was the only way to install software on Linux and there is a standard way of installing these files. It will not work in every case, but it will in most (if you have the right dependencies installed). To compile a package you must first extract it somewhere. This is easily done, simply right-click on the package and select Extract Here.
    Extracting a package
    To proceed you must have the compiler tools installed. They all come with the package build-essential, available in Synaptic. When you're sure you have the compiler tools installed, you fire up the terminal and change directory to the one you've just extracted (if you're not sure how to do that see: Navigating the terminal. When you're in the correct directory you execute a configure script: ./configure. Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways:

    Normal install: If you want to install it the normal "primitive" way, type sudo make install. To remove the temporary files you run make clean. To uninstall the program you run sudo make uninstall. These two clean-up commands don't always work, though, the programmer needs to have enabled them.

    Package manager install: If you want to install it in a way that means it can be easily removed from inside the package manager, first install the package checkinstall. To install the package type sudo checkinstall. This will take slightly longer than a normal install and quite possibly you'll have to supply a description of the application yourself (and edit the other information slightly). If the need arises, this will be easy to take care of from inside the checkinstall program. 
Shell Script Installer (.sh, .bash)
    You can run the shell script inside a terminal with the command sh. If the script is called test.sh and is on the desktop of user carl, you can install it with sh /home/carl/Desktop/test.sh.
Binary Installer (.bin, ...)
    If the installer is called test.bin and is located on the user carl's desktop, you can run it inside your terminal with /home/carl/Desktop/test.bin. Keep in mind that the installer might not have permission to execute in your file-system. To change permissions so that the file is executable, you right-click on the file on the desktop and select Properties; a window will open. Click on the tab labeled Permissions inside the window. There will be some boxes you can tick which tell the system what you're allowed to do with the file. Tick the box that says Execute outside the label that says Owner.
    Changing permissions on a file

    Permissions are tied to every file in the file-system
    You can also run the command chmod +x /home/carl/Desktop/test.bin to make the file executable.
Windows Executable (.exe)
    If you, after having searched around the Internet for a Linux version or a viable Linux replacement for the Windows program you want to install, find that there is no Linux program that will replace it, there is a slight chance the Windows executable will run on Linux[5]. This is not a proper solution to your problem, not in any way, but for some people it's the only way. To run Windows executables you need to install a package called wine. When that is done, run the command wine PATH in the terminal where PATH is the path to your EXE. If the user carl has an EXE called test.exe inside his home folder, he'll run the command wine /home/carl/test.exe to execute it. Be adviced that running Windows programs in WINE is often very buggy and probably won't work to your satisfaction; very often it doesn't work at all!

    If the executable you ran was an installer wizard, your program will be installed in a hidden folder located inside your home folder. If the user carl has installed a program called Test, it will probably be installed to the folder "/home/carl/.wine/drive_c/Program Files/Test" (remember to include quotes around paths with spaces in them when typing them in a terminal). EXEs from inside this folder can be run with wine. You might want to create at launcher/shortcut for your desktop to easily start up your app. Here is a Windows program run with wine:
    The Windows application Graph

    The Windows application Graph

Appendix

The following isn't directly connected to installing software and themes.
Enabling extra repositories

On a standard Ubuntu installation, Ubuntu is configured to use the main repository. There are however, other official repositories (or sections on the Ubuntu server) that aren't available right away. There is one called Universe which is the largest one. It's a pool of community-maintained software, but it is not officially supported by Ubuntu. There is also a section called Multiverse which has software under questionable licences. The third section is called Restricted and is a very small pool of software with restricted copyright.

To enable the rest of the Ubuntu repositories you open Synaptic and select an option in its menubar: Settings &#8594; Repositories. Here is a list of the current repositories. To enable the missing section select each of the packages that are labeled binary, click on Edit and tick the boxes outside the sections of the Ubuntu repositories you want to enable.
Enabling the universe and multiverse repositories

Enabling the universe, restricted and multiverse repositories

When you're done, Synaptic will probably ask you to reload your list of packages; agree to do that. Now your list of available packages should have increased significantly.
Using CDs as offline package repositories

The best way to install new software in Ubuntu is to be connected to the Internet, but sometimes this is not possible. When you install Ubuntu the first time, your install CD should have been added as a repository. If it isn't, you can add it from the same window you enable extra repositories from. There's a button labeled Add CDrom; press this, insert your install CD and it will be added to the repositories.
Adding a CD to the package manager

Adding a CD to the package manager

You can now install software through Synaptic without being connected to the Internet, provided the install CD is inserted. Note that the install CD has software solely from the main repository, not Universe, Multiverse or Restricted! There is an ongoing project to create an Addon CD or DVD with select packages from the other sections of the Ubuntu repositories. You can download a preliminary CD ISO file for Ubuntu 5.10 'Breezy Badger' and try it out if you want to, but this guide will not go further into the subject[6].
Navigating the terminal

The standard terminal on Ubuntu is Gnome Terminal which can be found in Applications &#8594; Accessories &#8594; Terminal. A terminal is in a way very similar to a file manager in that it's always inside a specific folder and is able to navigate to other folders and do regular file management. By default it will be inside your home folder when you run it. To confirm that your terminal is indeed browsing your home folder, type pwd ending with a press on enter. The pwd command will output the path to the current folder.

To see a list of files and directories inside the current directory, run the command ls. If you want to navigate up the directory tree run cd ... If you want to navigate down the directory tree run cd NAME where NAME is the name of the folder you want to navigate to. Example: if Tom is inside his home folder and there's a directory called test inside it, he will run cd test to change directory. If he wants to go back he can run cd ... I he ever gets lost he can run cd by itself; this will take him back to his home folder.
Adding a launcher/shortcut to your desktop

These are well-known from Windows. Launchers are shortcuts to your application allowing you to easily run it. To add a launcher, right-click somewhere on your desktop and select Create Launcher.... This will open a dialog from which you can enter information about the launcher. Remember to enter a name as well as a path to the executable. This is what carl would enter if he wanted a launcher for the executable named test located in his home folder:
Creating a new launcher

Creating a new launcher
Why I created this guide

The easiest way to help a new user install something is to provide a command that will accomplish it. That is not in my opinion the best way to make a new user understand how Ubuntu works. It's also sad how you can leave the impression that Ubuntu needs to be used through a command-line for the simplest of tasks, when capable graphical tools exist for the same purposes. I hope this guide will help new users understand everything a little bit better. As they say in China: "Give a man a fish and you feed him for a day. Teach a man to fish and you feed him for a lifetime."
Changelog

    * Revision 1 (2006-05-06): Changed the introduction slightly, added list of contents, added part about checkinstall.
    * Revision 2 (2006-05-14): Linked to all important sections at the top of the page (BTW thanks to the bloke who put this on digg.com and to all those who dugg it!)

Created by Simon Gray © 2006

Notes:

   1. Open source implies that the software is available under an open source license, meaning anyone is free to look at, modify, copy and redistribute the code under the terms of the license. Open source is considered the most transparent and effective way of developing software today. Ubuntu is entirely made up of open source software (abbreviated OSS).
   2. Advanced Package Manager or APT is what empowers many popular Linux distributions. It was first seen in Debian (that's where the name of the packaging format, deb, came from) but is now also used by other popular distributions such as Ubuntu, Knoppix, Linspire and Mepis. Another popular package manager is RPM (RPM Package manager, a recursive acronym) which is used by Fedora Core, SUSE Linux and Mandriva.
   3. Muine is a music player and a great way to enjoy your music. It has a simple interface, is very intuitive, focuses on listening to albums and doesn't come with a lot of statistical information. It's light as a feather and makes you enjoy music, without the music managing gaining all your focus. If you want a killer music jukebox with more features than you can imagine, take a look at Amarok instead.
   4. If you're looking for themes, take a look at Gnome Look or art.gnome.org. The window border theme I used for the screenshots in this guide is called Shiny Cairo and can be obtained at the Ubuntu Forums.
   5. The WINE developers keep a very handy database where the users can submit small reviews of their experiences with all sorts of programs and games when run with WINE. It also includes tips on how to get some of the more difficult applications running in WINE. If you're a web developer and need to see what your sites look like in Internet Explorer 6, there is a script available for installing it.
   6. As of now, the addon CD is entirely unofficial and created by a some very helpful users in the Ubuntu community. There is work on creating a "Breezy Badger" version, but no "Dapper Drake" is being developed on yet! See the progress so far.

---

### Post by aysiu on 2007-01-02
There's no need to reproduce the entire document here.

You can just view [the Google cache of the page](http://72.14.253.104/search?q=cache:DmPDS6o8cpMJ:monkeyblog.org/ubuntu/installing/+site:monkeyblog.org+install+anything&hl=en&gl=us&ct=clnk&cd=1&lr=lang_en&client=firefox-a)

By the way, I've moved this thread to the HowTo section and retitled it appropriately.

*mostwanted*, did your domain name ever get renewed? Or is this just a temporary down-time?

---

### Post by fokuslee on 2007-01-02
ok cool im gonna use ur post for my guide hope u don't mind

---

### Post by aysiu on 2007-01-03
Anyone know of a working mirror of the site? The Google cache doesn't have images, as far as I can tell, and the screenshots were really what set that page apart.

---

### Post by Athanasius on 2007-01-03
The link is dead, i cannot connect to it for some reason.  Oh darn.. I guess I should have read the earlier posts, now I see what is going on.  

This should go on Psychocats

---

### Post by aysiu on 2007-01-08
Update: Almost a week later, still can't get to MonkeyBlog.

Anyone know of existing mirrors of the site?

---

### Post by iGama on 2007-01-08
I have the portuguese version that uses the same images 

[http://www.guiaubuntupt.org/wiki/index.php?title=Como_instalar_tudo_em_Ubuntu](http://www.guiaubuntupt.org/wiki/index.php?title=Como_instalar_tudo_em_Ubuntu)

---

### Post by mostwanted on 2007-01-21
I am the author the guide [COLOR="Red"]How to install anything in Ubuntu[/COLOR] which was previously located at [http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing), but which is no more because my web host is run by a bunch of idiots (long story...).

The site has been down for a month now, so I thought it was time to do something about it, which is why I'm releasing the guide to the public domain so anyone who is willing to can host it or just use parts of it in other guides. I don't need accreditation.

I have a tar.gz bundle which contains the index file, all of the images and the GIF videos. I'm going to speak with the author of the Hungarian translation to see if he's willing to release his work as well. Need somewhere to upload it so can anyone advice me on what to do...? It's too big to fit as an attachment.

Hope someone will notice this, otherwise the guide is no more!

Thank you very much!

---

### Post by GStubbs43 on 2007-01-21
Hey, that was a great guide, I used to use it a lot and have new ubuntu'ers use it as well! I hope someone can host it!

---

### Post by rickmans on 2007-01-21
How much traffic would the site take a month?

---

### Post by Canis familiaris on 2007-01-21
I managed to get hold of this guide when the server was down through the cached pages in google :lolflag: 
Anyways thanks for making this great guide

---

### Post by Canis familiaris on 2007-01-21
> **mostwanted said:**
> I am the author the guide [COLOR="Red"]How to install anything in Ubuntu[/COLOR] which was previously located at [http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing), but which is no more because my web host is run by a bunch of idiots (long story...).

The site has been down for a month now, so I thought it was time to do something about it, which is why I'm releasing the guide to the public domain so anyone who is willing to can host it or just use parts of it in other guides. I don't need accreditation.

I have a tar.gz bundle which contains the index file, all of the images and the GIF videos. I'm going to speak with the author of the Hungarian translation to see if he's willing to release his work as well. Need somewhere to upload it so can anyone advice me on what to do...? It's too big to fit as an attachment.

Hope someone will notice this, otherwise the guide is no more!

Thank you very much!

Why don't you publish this guide in PDF format for free in [lulu.com]("http://www.lulu.com/")
Also you may try alteast publish the text in a good blogging site such as blogger.com

---

### Post by mostwanted on 2007-01-21
> **rickmans said:**
> How much traffic would the site take a month?

About 30 GB.

---

### Post by mostwanted on 2007-01-21
> **Anurag_panda said:**
> Why don't you publish this guide in PDF format for free in [lulu.com]("http://www.lulu.com/")
Also you may try alteast publish the text in a good blogging site such as blogger.com

Well, it's a lot of work to convert a big hand-coded HTML file into other formats, but I'll look into it.

---

### Post by matthew on 2007-01-21
I always appreciated your guide. I don't have time to maintain it myself but I will put out some feelers and see if anyone I know is interested. I would like to see this brought back online somewhere.

---

### Post by ssam on 2007-01-21
is it not possible to intergrate this into the wiki?

i have 20Gb/month of web hosting from 1and1.co.uk, of which most of it is spare. i could give you FTP access to a subdirectory. PM me in your you are interested.

---

### Post by mostwanted on 2007-01-21
Ok, the whole thing can be downloaded here: [http://htmldesign.dk/how_to_install_anything_in_ubuntu.tar.gz](http://htmldesign.dk/how_to_install_anything_in_ubuntu.tar.gz)

Yeah, it could probably be integrated into the wiki. I don't have time to do it right now, but if anyone has they can of course go and do that :)

---

### Post by Canis familiaris on 2007-01-21
For temporary basis, I've posted the guide here (courtesy: google cache):
EDIT: I put it in another host. Probably a permanant home
I know it's unimpressive because of lack of the images but anyone who wants to read it... :wink: 

I will try to publish it with images somewhere as quickly as possible with images.
(I am giving full credit to the actual author)

EDIT: I've now hosted it here with images, movies and all: [http://amitech.50webs.com/](http://amitech.50webs.com/)

---

### Post by matthew on 2007-01-21
> **mostwanted said:**
> Ok, the whole thing can be downloaded here: [http://htmldesign.dk/how_to_install_anything_in_ubuntu.tar.gz](http://htmldesign.dk/how_to_install_anything_in_ubuntu.tar.gz)

Yeah, it could probably be integrated into the wiki. I don't have time to do it right now, but if anyone has they can of course go and do that :)That's awesome. Thanks!

I put up a temporary mirror until the site finds a long-term new home. EDIT #2: It's found a permanent home! *link deleted*

EDIT: I see Anurag_panda beat me to it. I didn't mean to steal his idea. I don't think it will hurt to have it available several places, though...at least until it finds a new maintainer.

---

### Post by mostwanted on 2007-01-21
No I don't think it'll hurt at all, but at least one permanent URL would probably be favourable.

Thanks for helping out all of you!

---

### Post by Phatfiddler on 2007-01-21
I could always host it on my site, CutlerSoftware.com

I have over a Terabyte of bandwidth per month - I think it would suffice.

---

### Post by dorcssa on 2007-01-21
Hmm, there was a hungarian translation of the guide? Good to know it. :D

---

### Post by Phatfiddler on 2007-01-21
Went ahead and hosted it for you.  Consider it a permanent home ):P 

[http://www.cutlersoftware.com/ubuntuinstall](http://www.cutlersoftware.com/ubuntuinstall)

---

### Post by dorcssa on 2007-01-21
The hungarian link doesn't work. :(

---

### Post by Phatfiddler on 2007-01-21
Yeah, it wasn't included in the tar.gz file.  He has to wait until the original author releases it.

---

### Post by maniacmusician on 2007-01-21
That's a really great guide! I'm working on a series of guides myself. Since this is now public domain, I'm assuming I can incorporate it into my guides as well? That'd be great. Thanks for your contribution to Ubuntu, it's a great thing.

---

### Post by Polygon on 2007-01-21
i think it would be better if it was implemented into the ubuntu wiki as well, that way if whoever is hosting it ever leaves for some mysterious reason, and they don't keep the server running, we have a permanent copy :D

ill work on it next weekend if no one else does it before then.

---

### Post by aysiu on 2007-01-21
> **Polygon said:**
> i think it would be better if it was implemented into the ubuntu wiki as well, that way if whoever is hosting it ever leaves for some mysterious reason, and they don't keep the server running, we have a permanent copy :D

ill work on it next weekend if no one else does it before then.
Would it make sense to modify this page or to link off of it?
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Phatfiddler on 2007-01-21
It would probably be best to implement it into the current "Installing Software" Wiki, since the page you refer to is rather small and lacks detailed information.  The guide that is being passed on in this thread contains "videos" (actually gif animations) that really help new users, and seems to be much more detailed.  In the meantime, we have several mirrors of the guide for users to refer to until the completion of the wiki.

---

### Post by matthew on 2007-01-22
> **Phatfiddler said:**
> Went ahead and hosted it for you.  Consider it a permanent home ):P 

[http://www.cutlersoftware.com/ubuntuinstall](http://www.cutlersoftware.com/ubuntuinstall)Excellent! I'll leave it up on my site for a day or two until I have a chance to replace it with a redirect to yours.

EDIT: I didn't see any traffic since Phatfiddler was so quick so my mirror has just disappeared. Thanks again for being so generous!

---

### Post by mostwanted on 2007-01-22
> **maniacmusician said:**
>  Since this is now public domain, I'm assuming I can incorporate it into my guides as well?

Yes, of course! :)

---

### Post by Tomosaur on 2007-01-22
> **mostwanted said:**
> Well, it's a lot of work to convert a big hand-coded HTML file into other formats, but I'll look into it.

Not with html2text!

---

### Post by iGama on 2007-01-22
I've made the translation to the Portuguese version, If help is needed to update the text or something you can count on me :)

---

### Post by mostwanted on 2007-01-24
[http://digg.com/linux_unix/How_to_install_ANYTHING_in_Ubuntu_3](http://digg.com/linux_unix/How_to_install_ANYTHING_in_Ubuntu_3)

Just found this...!

---

### Post by matthew on 2007-01-24
> **mostwanted said:**
> [http://digg.com/linux_unix/How_to_install_ANYTHING_in_Ubuntu_3](http://digg.com/linux_unix/How_to_install_ANYTHING_in_Ubuntu_3)

Just found this...!I gave it a digg!

---

### Post by lyceum on 2007-01-24
Very nice guide!

---

### Post by Phatfiddler on 2007-01-24
Very cool!  Since it was put on Digg, the Install Guide ALONE took up 8GB of bandwidth yesterday, with over 300,000 views and 13,000 unique visitors.

iGama - Thank you for your help in this!  The translated version has received thousands of hits as well.

---

### Post by Phatfiddler on 2007-01-24
**Here are the stats for just yesterday.  They are VERY interesting**

[IMG]http://cutlersoftware.com/images/stats.png[/IMG]

---

### Post by matthew on 2007-01-24
> **Phatfiddler said:**
> **Here are the stats for just yesterday.  They are VERY interesting**
68.7% viewing with Windows. Fascinating...and promising.

---

### Post by AgenT on 2007-01-24
Very impressive work.

Does anyone know how those gif screencasts were made? What tools were involved in the making of those screencasts?

---

### Post by Phatfiddler on 2007-01-24
> **AgenT said:**
> Very impressive work.

Does anyone know how those gif screencasts were made? What tools were involved in the making of those screencasts?
You can do it in gimp by making each step of the animation as a seperate layer.  Save the file as a .gif and it will give you the option to make it an animation.  I believe there is also ware out there that converts video to .gif, but I can't remember off the top of my head.

---

### Post by mostwanted on 2007-01-24
I used Byzanz for the GIF screencasts. Did it mainly because Istanbul wouldn't work on my machine, but also because GIF is supported by all major browsers without any plugins or codecs.

---

### Post by AgenT on 2007-01-24
> **mostwanted said:**
> I used Byzanz for the GIF screencasts. Did it mainly because Istanbul wouldn't work on my machine, but also because GIF is supported by all major browsers without any plugins or codecs.
Thank you for the Byzanz information.

Converting any movie into gif, jpg, etc. can be done via mplayer. mplayer is able to convert a movie on a per-frame basis into individual image files. Using gimp or imagemagick (just a wild guess on the latter) one could then create a large one file gif animation. The advantage to this would be the ability to edit before creating a gif file. It may even be possible to do the whole conversion in mplayer.

---

### Post by kevCast on 2007-01-24
Amazing guide, thank you for sharing again.

---

### Post by iGama on 2007-01-26
> **Phatfiddler said:**
> Very cool!  Since it was put on Digg, the Install Guide ALONE took up 8GB of bandwidth yesterday, with over 300,000 views and 13,000 unique visitors.

iGama - Thank you for your help in this!  The translated version has received thousands of hits as well.

Yep , the Portuguese community has been using the guide daily for newbies :)

---

### Post by boredandblogging.com on 2007-01-27
Looks like this has been taken care of, but are there other projects that need to be hosted? I think I could find some room and bandwidth.

---

### Post by mostwanted on 2007-02-06
I would just like to point out that the site is back up for now and that a link to a Spanish translation has been added to the page:

[http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

---

### Post by aysiu on 2007-02-06
> **mostwanted said:**
> I would just like to point out that the site is back up for now and that a link to a Spanish translation has been added to the page:

[http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)
So do you have a new host?

---

### Post by mostwanted on 2007-02-06
> **aysiu said:**
> So do you have a new host?

No same old crappy host for now, but I'm in the market for another one right now :)

---

### Post by BWF89 on 2007-02-06
Thanks for the guide.

It'll come in handy.

---

### Post by bcnaat on 2007-02-11
> **mostwanted said:**
> No same old crappy host for now, but I'm in the market for another one right now :)

I use IPowerWeb as my host. Anyway, just wanted to let you know that I stuck it up on my site if needed. The addy is: [http://kaybyrd.com/ubuntu](http://kaybyrd.com/ubuntu)

I do need to go in the index and give the proper credit for you writing it.

~Kay

Apparently my webserver is run by idiots, too. I can barely access my own site now that they've 'upgraded' the servers so ... this link doesn't work anymore. Sorry.

---

### Post by petri on 2007-02-17
Well, it works for now on [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by charlie85254 on 2007-03-02
Only 30 GB a month?  PM me and let me know how to get ahold of the files to throw them up on my server.  30 GB a month is nothing for me as I am allowed 1 TB a month and my server doesn't go down and is very fast...So please get ahold of me and let me know.
Thanks

---

### Post by boredandblogging.com on 2007-03-02
Yeah, that bandwidth limit is pretty low. I've got over a TB of bandwidth/month of my hosting too, so let us know if you need to move it.

---

### Post by charlie85254 on 2007-03-02
I've got a group of users I'm pretty sure that will maintain it as well...If not I could do it myself with no problem.

---

### Post by XTREEM|RAGE on 2007-05-23
i just want to thank the creator of this tut.
This is really a nice1 :)

---

### Post by Y2J on 2007-06-25
A graphical guide for all new users with a Windows background using Ubuntu.

[How to install ANYTHING in Ubuntu!]("http://cutlersoftware.com/ubuntuinstall/")

I think adding this to your bookmarks/del.icio.us will be a great idea. :D

Regards,

---

### Post by DocBob on 2008-05-08
Stumbled upon this along my internet travels. Found it interesting, just thought i'd share. Hope it helps.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

:KS

---

### Post by zerubbabel on 2008-08-28
Does anyone have a pdf of "How to Install Anything in Ubuntu"? The link to the article on monkeyblog.org still doesn't work...

---

### Post by aysiu on 2008-08-28
> **zerubbabel said:**
> Does anyone have a pdf of "How to Install Anything in Ubuntu"? The link to the article on monkeyblog.org still doesn't work...
Even the Google cache isn't loading the page fully. I thought there used to be a mirror at cutlersoftware.com, but I can't find that either.

In the meantime, if you're looking for a software installation guide, try this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by J_romeo on 2008-08-29
> **iGama said:**
> I have the portuguese version that uses the same images 

[http://www.guiaubuntupt.org/wiki/index.php?title=Como_instalar_tudo_em_Ubuntu](http://www.guiaubuntupt.org/wiki/index.php?title=Como_instalar_tudo_em_Ubuntu)

Well I'm brand new here and I just used Google's language tools to translate the web page from Portuguese to English. Hope it helps.

---

### Post by uncleclinto on 2008-08-31
Okay,

I'm kicking myself right now for not saving a local copy of Monkey Blog's article How to install anything in ubuntu ([http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)).  This thing was my bible because it was totally innovative in the world of Linux how to and documentation (it had screen shots and instructions that didn't assume I was a command line wizard).  The official documentation on installing from the source tar.gz or from red hat .rpm files is about as worthwhile as a warm bucket of hamster vomit.  Did anyone save, back-up, or republish this info??  What the heck happened to monkey blog???  I need to update flash player, and since adobe doesn't release a .deb file, I'm in serious need of these instructions.

Clint

---

### Post by damis648 on 2008-08-31
To update flash player, first remove the old one. For simplicity's sake, I will give you a command for terminal:
```
sudo apt-get remove flashplayer-nonfree
```. Now download the .tar.gz from adobe and save it somewhere. Then right click on your desktop and select extract here. Rename the newly created folder to "flashinstall" and copy it to your home directory (for simplicity's sake). Now, again in terminal, type:
```
cd ~/flashinstall
```and enter. Now type:
```
chmod +x flashplayer-installer.run
```
and finally:
```
./flashplayer-installer.run
```
Cheers!

---

### Post by bodhi.zazen on 2008-08-31
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

### Post by mb_webguy on 2008-08-31
[Google cached version]("http://64.233.167.104/search?q=cache:IfbspYjsGWIJ:www.monkeyblog.org/ubuntu/installing.html+site:monkeyblog.org&hl=en&ct=clnk&cd=4&gl=us&client=firefox-a")
[Wayback Machine (Internet Archive) version, 14-Feb-2008]("http://web.archive.org/web/20080214235528/http://monkeyblog.org/ubuntu/installing/")

---

### Post by uncleclinto on 2008-09-01
Okay, first of all, many many thanks to mb_webguy and bodhi.zazen for answering my question.  I'm not marking this thread solved yet, though, thanks to damis648, who assuming that I was a command line wizard (I pointed out in my initial post that this was not true).  Like a sheep to the slaughter, though, I followed damis648's advice.  Of course, as often is the case, the first part worked beautifully, flash player is certainly gone (incidentally, it's the flash plugin that i need, but that's a different story). The bugger is, the second half of his quality instructions don't work for the installer I have, synaptic says the flash player package is gone, and I'm screwed, blued and tatooed.  Here's what I downloaded from adobe: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)


Could anyone tell me how to:

A: update my flash plugin
B: get my *%#@ flash player back!!

---

### Post by Peter09 on 2008-09-01
Hi.
does  

```
sudo apt-get install flashplugin-nonfree
```

get what you want?

---

### Post by toolisima on 2008-09-01
Hello, I have the same issue going on here...
I did

 sudo apt-get install flashplugin-nonfree

and apparently downloaded successfully but not installed!

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

help! anyone?

---

### Post by RachedTN on 2009-01-01
The URL that you mentioned doesn't talk about : how to install anything in Ubuntu !!

---

### Post by howefield on 2009-01-01
Looks more like spam.

---

### Post by jimmy the saint on 2009-01-15
I was just curious.  I went looking for the guide and it is gone.  e-how did a shady thing and made a useless article and gave it the same name.  It just walks you through 6 steps for installing packages via synaptic.  I tried to give them a good text lashing, but it wasn't worth creating an account.  I knew I should have pdf'd it.  
oh well

If anyone had the forethought to do so, or knows of a working mirror, let me know.  Thanks.

---

### Post by thomasr on 2009-01-15
[http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/](http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/)

---

### Post by jimmy the saint on 2009-01-15
Hey thanks man.  I found that site while looking for the origional.  I set my father up with an Ubuntu desktop and he likes it, but he is coming from windows (and was never really comfortable with it) and I liked how the article explained everything in simple, approachable terms.  It's a shame the site is down.  At least the core info is there.

---

### Post by Sorivenul on 2009-01-15
I've been looking for this as well as a reference for my wife. I haven't had any luck, even with Google cache.

The "next best things" I have found, however are:
[http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/](http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/)
[http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html)
And of course the official documentation.

---

### Post by jimmy the saint on 2009-01-16
I think the Godawski one is a little more approachable.  I will use that.  Thanks guys!

---

### Post by rburkartjo on 2009-01-16
thom, tks also for that link i loved that site and too bad it is down/cheesemaker

---

### Post by Sorivenul on 2009-01-16
> **jimmy the saint said:**
> I think the Godawski one is a little more approachable.  I will use that.  Thanks guys!
Also, follow the links he includes at the bottom, I believe they are to community documentation and the Psychocats tutorials. 

Put 'em together, and what have you got? Bippity-boppity-buntu.

---

### Post by iaculallad on 2009-01-16
Here's an additional link: [Psychocat's Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by Sef on 2009-01-16
[How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html")

---

### Post by Keen101 on 2009-01-16
also look into [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

Full Circle has lots of good articles for people new to Linux. They give lots of tips.

---

### Post by jimmy the saint on 2009-01-28
Sef, I wish the thanks were still around.  I have been looking for that for a while.  Im going to pdf it.  Good stuff!

---

### Post by Telengard C64 on 2009-06-17
This link no longer works. Is there an updated version of the article, or at least a non-dead link somewhere? Google is failing me, but I'll keep searching.
:sad:

---

### Post by jerrrys on 2009-06-17
link works

---

### Post by raymondh on 2009-06-17
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by jdarias on 2009-06-17
Hehehehe...
Whe i saw the title, i really thought of anything. I mean **ANYTHING.**
I got happy too soon :lolflag:

---

### Post by Telengard C64 on 2009-06-17
> **jerrrys said:**
> link works

I call BS! It's a lousy "search" page  :mad:

---

### Post by jerrrys on 2009-06-17
but it works

---

### Post by CylnZ on 2009-06-18
Hi, I found this site for my Mother. Almost any app you can think of for Ubuntu 9.04 in a very clean nice format. She finds things on it quite simply. [http://appnr.com](http://appnr.com)

It's almost like a repo web frontend or something.

---

