---
title: "Compatible Hardware List Application with cool features.."
date: 2005-10-12
forum: The Cafe
---

### Post by thieummm on 2005-10-12
One original idea to make hardware work with Ubuntu: make an application that lists all the hardware that is currently compatible with Linux (and supported by Ubuntu).  

In this application, it will be possible to search for a device using hints such as hardware type, brand, etc... The app could contain links to vendor websites, etc... 

This way users will be sure their new device will be supported. 

Example: I want to buy a webcam, I open the application "Choose New Hardware for Ubuntu", I type "webcam" in the search box, a list of all supported webcams is displayed, I choose the Philips SuperCam 12, because I know it's good and it's supported by Ubuntu !! Then when I receive it, I plug it in, and it works right out of the box!!!! 

And if Ubuntu becomes *really* popular, vendor really will want to be on this list so maybe they will start to contribute to make Linux Drivers !!

---

### Post by nocturn on 2005-10-12
[QUOTE=thieummm]
Example: I want to buy a webcam, I open the application "Choose New Hardware for Ubuntu", I type "webcam" in the search box, a list of all supported webcams is displayed, I choose the Philips SuperCam 12, because I know it's good and it's supported by Ubuntu !! Then when I receive it, I plug it in, and it works right out of the box!!!! 

And if Ubuntu becomes *really* popular, vendor really will want to be on this list so maybe they will start to contribute to make Linux Drivers !![/QUOTE]

Though this is a good idea and making the app itself is doable, there are some problems with this.

1# The app is rather simple, the difficulty is maintaining the database behind it.  By the time a product is tested and rated as Linux-friendly, it might already be out of production.  

2# A lot of manufacturers are sloppy with model numbers.  For example, their are multiple versions of the SMC 2835 card out there, only one has a Nitro chipset that is natively supported by the kernel.  The other ones have to use Ndiswrapper.
The database would raise the false expectation that such models would work, only disappointing the user when he bought a different version of the model.

---

### Post by thieummm on 2005-10-12
[QUOTE=nocturn]Though this is a good idea and making the app itself is doable, there are some problems with this.

1# The app is rather simple, the difficulty is maintaining the database behind it.  By the time a product is tested and rated as Linux-friendly, it might already be out of production.  [/QUOTE]

This could be a community database, with users updating the database as they get their hardware working with ubuntu (without modifications), possibly through a moderator. Some Ubuntu guys, or even some Canonical guys could help with that as well ??

[QUOTE=nocturn]2# A lot of manufacturers are sloppy with model numbers.  For example, their are multiple versions of the SMC 2835 card out there, only one has a Nitro chipset that is natively supported by the kernel.  The other ones have to use Ndiswrapper.
The database would raise the false expectation that such models would work, only disappointing the user when he bought a different version of the model.[/QUOTE]

Yes it would be an advisory database... It has always been like that so far in the Linux Community so why not ?


This app could also be web based something like hardware.ubuntu.com, like packages.ubuntu.com (same type of interface but for hardware devices instead of package)...
 THAT would be great indeed !!!!

---

### Post by asimon on 2005-10-12
[QUOTE=thieummm]This app could also be web based something like hardware.ubuntu.com, like packages.ubuntu.com (same type of interface but for hardware devices instead of package)...
 THAT would be great indeed !!!![/QUOTE]
SUSE has something like this since many years: [SUSE LINUX: hardware compatibility list](http://hardwaredb.suse.de/index.php?LANG=en_UK). I remember using the german version of that a lot when buying hardware in the 90s. :)

---

### Post by GeneralZod on 2005-10-12
Here is a stupidly huge list of wireless cards and their compatibilty status:

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

---

### Post by thieummm on 2005-10-12
Thanks for the link,

yes this could be something like this,

but a lot better !!!!

---

### Post by drucer on 2005-10-12
This is not a bad idea at all! I support it 100%.

Ubuntu user base is quite huge, so I think it would be possible to create such a database relatively quickly.

---

### Post by tehwa on 2005-10-12
[[IMG]http://img439.imageshack.us/img439/83/collection2mf.th.png[/IMG]](http://img439.imageshack.us/my.php?image=collection2mf.png)

Apparently Canonical have been doing something similar. I wonder if they are going to use the data for this purpose though.

---

### Post by Orunitia on 2005-10-12
I think Linuxquestions.org has something like this on their forums.

---

### Post by thieummm on 2005-10-12
[QUOTE=tehwa][[IMG]http://img439.imageshack.us/img439/83/collection2mf.th.png[/IMG]](http://img439.imageshack.us/my.php?image=collection2mf.png)

Apparently Canonical have been doing something similar. I wonder if they are going to use the data for this purpose though.[/QUOTE]

Hi tehwa,

where does this screenshot comes from ?
It looks like a Gnome App, and I'm using KDE...

Thanks, that looks great !

---

### Post by tehwa on 2005-10-12
[QUOTE=thieummm]Hi tehwa,

where does this screenshot comes from ?
It looks like a Gnome App, and I'm using KDE...

Thanks, that looks great ![/QUOTE]
It's in Hoary default (and probably Breezy) under:

System Tools > Ubuntu Device Database

It's a great idea, I really hope Canonical are going to use this data for the purpose that you proposed. It is one of the few positive approaches I have come across to pressuring device manufacturers to add linux to their compatability lists.

---

### Post by tehwa on 2005-10-12
Sorry to double post, but after some very brief investigation:

1. It appears that the device database in Ubuntu is primarily used by the Ubuntu developers.

2. The site which houses that data is [http://hwdb.ubuntu.com/](http://hwdb.ubuntu.com/) which at this time, is undergoing maintenance, probably stays in that state though (?).

3. It appears that the format of the device database entries of users is XML, which would make extracting and manipulating the (probably massive amounts of) data that has already been collected by Canonical about Ubuntu users hardware easier than any other format, IMHO.

Perhaps something could be arranged here...

---

### Post by WirelessMike on 2005-10-12
Perhaps a sub-forum could be created here to host such a database...

Sort of like this one:
[http://www.linuxcompatible.org/](http://www.linuxcompatible.org/)

Of course, the above database is continuously developing and does recognize the Ubuntu distro, already, so to create yet another one might seem superfluous.

---

### Post by Stormy Eyes on 2005-10-12
[QUOTE=thieummm]One original idea to make hardware work with Ubuntu: make an application that lists all the hardware that is currently compatible with Linux (and supported by Ubuntu).  

In this application, it will be possible to search for a device using hints such as hardware type, brand, etc... The app could contain links to vendor websites, etc... 

This way users will be sure their new device will be supported. [/QUOTE]

Dumb question, but why not use Google to search for compatible gear? I do it all the time.

---

### Post by thieummm on 2005-10-12
[QUOTE=Stormy Eyes]Dumb question, but why not use Google to search for compatible gear? I do it all the time.[/QUOTE]

Because you are a computer-savvy guy ! You know how to use Google, etc...
Ubuntu is all about making things easy for any people...

Also, it might be good to have a centralised, "trusted" (sort of) database, that is, an Ubuntu-centric database.

We are talking about Ubuntu here, not Linux Kernel Drivers that are spread all over the net...

---

### Post by Stormy Eyes on 2005-10-12
[QUOTE=thieummm]Also, it might be good to have a centralised, "trusted" (sort of) database, that is, an Ubuntu-centric database.[/QUOTE]

Sure, an Ubuntu HCL (hardware compatibility list) might be a good idea, but it requires manpower. Somebody has to compile it and then maintain it. And the guy who's working on the HCL *isn't* working on bugfixes or new features.

---

### Post by thieummm on 2005-10-12
[QUOTE=WirelessMike]Perhaps a sub-forum could be created here to host such a database...

Sort of like this one:
[http://www.linuxcompatible.org/](http://www.linuxcompatible.org/)

Of course, the above database is continuously developing and does recognize the Ubuntu distro, already, so to create yet another one might seem superfluous.[/QUOTE]

I am going to repeat myself, but linuxcompatible.org is not going to be used by the new_guy_who_has_just_switched_to_ubuntu ...

This Hardware Compatibility list should be labeled as "Ubuntu Compatibility List" and its access should be easy from within the (K)Ubuntu Desktop (web or native app).

OK so the Current Ubuntu Hardware Database might be a good start. They could provide a user front end to their database, with information only relevant to user (e.g. supported, partly supported, not supported..., Device ID, Vendor ID, Vendor Name....)...

Maybe we should talk to them ?

---

### Post by thieummm on 2005-10-12
[QUOTE=Stormy Eyes]Sure, an Ubuntu HCL (hardware compatibility list) might be a good idea, but it requires manpower. Somebody has to compile it and then maintain it. And the guy who's working on the HCL *isn't* working on bugfixes or new features.[/QUOTE]

yes, it definitely needs manpower !
... like every (new) feature does !!!

---

### Post by Stormy Eyes on 2005-10-12
[QUOTE=thieummm]I am going to repeat myself, but linuxcompatible.org is not going to be used by the new_guy_who_has_just_switched_to_ubuntu ...[/QUOTE]

The new_guy_who_has_just_switched_to_ubuntu usually doesn't read the documentation already provided, and often asks questions on the forums that can be answered by looking at the Wiki, the FAQs, or by reading the Ubuntu Guide. Wouldn't the HCL you propose be one more bit of documentation that the newbies don't read?

---

### Post by thieummm on 2005-10-12
[QUOTE=Stormy Eyes]The new_guy_who_has_just_switched_to_ubuntu usually doesn't read the documentation already provided, and often asks questions on the forums that can be answered by looking at the Wiki, the FAQs, or by reading the Ubuntu Guide. Wouldn't the HCL you propose be one more bit of documentation that the newbies don't read?[/QUOTE]

I don't know. It depends on how this new information is presented.
If it's an icon on the Desktop "Buy New Hardware", the user will probably be intrigued, and if the interface is friendly, the user will easily get familiar with the application...
It can be a highly "marketed" feature on Ubuntu's website...

Maybe it will not be addressed to the new_guy_etc but the same guy who has passed a few steps in Linux Knowledge... A more conscious user that knows that Hardware Devices are quite problematic in Linux...without wanting to waste his time to know more... I don't know... 

This is a positive discussion. Let's go on guys.

---

### Post by drucer on 2005-10-12
Linuxcompatible.org's website is very confusing and distractive. It rather pushes you away than welcomes you warmly. Ubuntu is about making it easy for humans to use their computers.

I say it would be better to have our own Ubuntu hardware compatibility database/application. It should be easy to use and it should follow the common Ubuntu theme.

---

### Post by ghee22 on 2005-10-12
To involve the new user, we have to come to them. this means in ubuntu, we should have a link to this website in the Gnome Menu under help stating, "Purchasing New Hardware?"

---

### Post by darkmatter on 2005-10-12
What we really need is to have a distinct Help menu under System. Other than a shortcut to yelp, It should have a link to the How To's on the wiki (once the are finished/organized), a link to the forums, link to a hardware compatibility database, etc. It would be much more useful and convenient for a new user, and would help to enrich their Ubuntu experience.

---

### Post by poofyhairguy on 2005-10-12
Does this not do the job?:

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by matthew on 2005-10-12
[quote=poofyhairguy]Does this not do the job?:

[https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport")[/quote]
Thank you! I was just about to post that same link with a recommendation that everyone interested in helping let others know what does/doesn't work with Ubuntu contribute to the wiki.

---

### Post by samb0057 on 2007-07-28
Have you guys checked out  [http://www.ubuntuhcl.org]("http://www.ubuntuhcl.org").

Not much hardware yet, but it has a very nice and feature-filled design, wheres the ubuntu hardware wiki seems a little underdeveloped. I posted reviews for all the hardware ive used under ubuntu, i encourage others to do the same.

---

### Post by vjones777 on 2007-09-03
There is an ubuntu hardware database, but I'm not sure if its active.  Some other info is in this thread [http://ubuntuforums.org/showthread.php?t=182834]("http://ubuntuforums.org/showthread.php?t=182834")

---

