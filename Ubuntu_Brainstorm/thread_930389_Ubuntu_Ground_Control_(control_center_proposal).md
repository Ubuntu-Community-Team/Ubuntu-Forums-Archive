---
title: "Ubuntu Ground Control (control center proposal)"
date: 2008-09-26
forum: Ubuntu Brainstorm
---

### Post by SunnyRabbiera on 2008-09-26
Maybe its time I combine a few ideas I have and make them one.
If its one thing I think Ubuntu needs I think its a control center, but one BETTER then gnome control center.
So I propose Ubuntu Ground Control as an idea, a super control center built for Ubuntu to make it easy and fun for the new user.
Here is how I see it, take the basic ideas of Drakconfig, the mandriva control center and merge them with some ideas that I have seen for Ubuntu like Ubuntu tweak.

The basic idea:
The control center itself should be simplistic but customizable, a customizable interface is something that drakconfig lacks.
If you change the iconset it should change inside this control center.
Also have something that can change more complex settings like monitor or sound without the need of the default gnome apps that dont have as many options.
It should overall be a hybrid of drakconfig and Ubuntu tweak.

Ideas borrowed from drakconfig:
Monitor settings: a better way to set up the monitor, with displayconfig-gtk gone and the default screen resolution app severely limited there needs to be a new application for editing monitor preferences for the local user and the administrator.
Sound configuration: Pulse and alsa have caused a lot of issues and even though the sound server selection tool provided by gnome does a basic job there needs to be something that can change all aspects of the system sound.
Like start up volume, system sounds and the like. This can hopefully improve Gnomes Volume Applet a bit too, like help enable extra devices and such.

Ideas from Ubuntu tweak:
Add/remove: with the next synaptic featuring a quick search function add/remove is a little less needed in the future releases of Ubuntu, plus I have always seen it as a hindrance.
Maybe if we can make a menu or something with two options:
basic installer (add/remove) or advanced installer (synaptic)
replace the add/remove option in the menus with this "Ground control" app to encourage new users not to use add/remove as a primary.
Computer information: change the host name of the computer, change user information, make things easier for people who like to mess around with their computers a bit.
Desktop icons: helps the user make desktop icons for home folders, trash bins and even links to applications if we are talking about deperate beginners. No more going into gconf editor, no more having to figure out how to use gconf editor... that thing is great for advanced users but for beginners its a nightmare.
Templates installer: helps install extra templates
Font installer: we have been lacking a good one, its time to get one.

My own ideas:
Easycenter (aka Rocketship): provides Medibuntu integration, Canonical store access and Codec buying via partners(for those who want codecs "legally")
Astronaut: Provides easy and direct access to support via both the forums and the IRC chat.
Venture: The all in one package converter, provides tools to convert RPM packages, download tools to help compile from source, and other stuff to help the newbie install packages that are not on the repositories... heck throw in a easy way to install and configure wine in there too.
Enterprise: to provide... shock enterprise support for businesses ;)

---

### Post by smartboyathome on 2008-09-26
I like most of the ideas you posted, until I got to your own ideas. Medibuntu integration is not going to happen, and for two good reasons (if you look at it from Canonical's point of view). The first is that Canonical is a business, and like any business, they want to make money. In order to do that, one of the things they are doing is selling legally licensed codecs. If they were to provide the free, illegal (in a lot of countries, including the UK), unlicensed codecs, then people would just look past the licensed codecs and go for the unlicensed one. The second is because the Medibuntu repository is not run by Ubuntu. Using any third party repositories is frowned upon by Ubuntu for good reason (quality control). The second reason could also apply to Venture (easy converting RPM to DEB and checkinstall). Other than that, I like the idea and have been wishing there was something to the ability of Drakconf for Ubuntu. That was my favorite part of SAM Linux.

---

### Post by SunnyRabbiera on 2008-09-26
> **smartboyathome said:**
> I like most of the ideas you posted, until I got to your own ideas. Medibuntu integration is not going to happen, and for two good reasons (if you look at it from Canonical's point of view). The first is that Canonical is a business, and like any business, they want to make money. In order to do that, one of the things they are doing is selling legally licensed codecs. If they were to provide the free, illegal (in a lot of countries, including the UK), unlicensed codecs, then people would just look past the licensed codecs and go for the unlicensed one. The second is because the Medibuntu repository is not run by Ubuntu. Using any third party repositories is frowned upon by Ubuntu for good reason (quality control). The second reason could also apply to Venture (easy converting RPM to DEB and checkinstall). Other than that, I like the idea and have been wishing there was something to the ability of Drakconf for Ubuntu. That was my favorite part of SAM Linux.

Well maybe there should be an easier way to add extra repositories then like medibuntu for beginners so they wont have to touch the terminal.
As for venture it could be used as a front end for alien or checkinstall, so that cuts down the terminal use for that part too.
Venture should help install source packages or RPM's and make them manageable for the new user, the confusion of RPM and tar packages is what throws people off so maybe there should be a non CLI frontend to checkinstall and Alien

---

### Post by smartboyathome on 2008-09-26
> **SunnyRabbiera said:**
> Well maybe there should be an easier way to add extra repositories then like medibuntu for beginners so they wont have to touch the terminal.

There already is the Software Sources tool (System > Administration > Software Sources). Just add the specific line given by the repository.

> **SunnyRabbiera said:**
> As for venture it could be used as a front end for alien or checkinstall, so that cuts down the terminal use for that part too.
Venture should help install source packages or RPM's and make them manageable for the new user, the confusion of RPM and tar packages is what throws people off so maybe there should be a non CLI frontend to checkinstall and Alien

Yes, it could do this, but then again including this by default would mean we would support Checkinstall and Alien, which imo isn't a good idea since they can be error prone and not always work. Especially with the checkinstall frontend, compiling from source would have to be done manually due to dependencies not being able to be detected easily. You would still have to run ./configure or ./autogen.sh, and then do make before you use checkinstall.


Not trying to belittle your idea, just pointing out the flaws. :)

---

### Post by SunnyRabbiera on 2008-09-27
> **smartboyathome said:**
> There already is the Software Sources tool (System > Administration > Software Sources). Just add the specific line given by the repository.



Yes, it could do this, but then again including this by default would mean we would support Checkinstall and Alien, which imo isn't a good idea since they can be error prone and not always work. Especially with the checkinstall frontend, compiling from source would have to be done manually due to dependencies not being able to be detected easily. You would still have to run ./configure or ./autogen.sh, and then do make before you use checkinstall.


Not trying to belittle your idea, just pointing out the flaws. :)

Well at least give alien a frontend, I know its not always on par but it will help out when there is a package someone needs that is RPM only.
As for checkinstall and compiling, at least lets try to make it somewhat easier for the newbie to convert source packages without the terminal.
I am just thinking of something that could be useful to newcommers here, I know both ideas are not perfect but its better then scaring newbies with a terminal.
I have always wondered why alien has not got a gui yet, it seriously needs one. I know the flaws in alien yes but it does the job most of the time when it is needed.

---

