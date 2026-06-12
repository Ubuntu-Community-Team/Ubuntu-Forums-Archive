---
title: "Mobuntu - should there be a laptop distro?"
date: 2006-11-13
forum: The Cafe
---

### Post by xdevnull on 2006-11-13
I don't know if this has been suggested and shot down before, or even if it is necessary, but I as I did my first install of Ubuntu (Edgy) on my laptop a few weeks ago, I found myself confronting a curious issue.  Ubuntu is a relatively small install, consistently limiting itself to a single CD, which I think is a good idea.  However I found myself missing and wanting some programs and dealing with some configuration issues that I did not encounter when installing the significantly heftier Suse 10.1.  I was frankly surprised that NetworkManager was not installed (had to download it), and I also had problems with my screen because its native resolution is 1280x768, and apparently the Ubuntu installer only recognizes the more typical aspect ratios and did/could not detect wide screen, something more prevalent in laptops than desktops (ended up editing my xorg.conf).  

So I found myself wondering if perhaps Ubuntu should have a laptop friendly, laptop focused option, in the same way it has a KDE/Xfce and education distribution.  This distribution could focus on laptop centric issues: wireless networking, widescreen LCD displays, external monitor interface, bluetooth, and particular laptop hardware issues - laptop lids, special keys, remotes, etc.  It could provide 3D windowing (aiglx, xgl, compiz &c.) with options that are turned down for the lower powered 3D cards.  Some of these things are implemented more or less in Ubuntu and other distributions, but I wonder if anyone is focusing on them in particular.  

I don't have a strong technical background when it comes to distribution installations, and all of what is involved, so I can't comment in particular on what this might mean.  The question to me seems to be whether the primary ubuntu distro would be different enough from a laptop focused distro to make a difference - and then, of course, who would do the work :).  However, I know more and more people who use their laptop as their primary workstation, and I think if Ubuntu developed a distribution that was focused on making things work right out of the box for laptops as well as it does for desktops, it might win some more friends.

---

### Post by prizrak on 2006-11-13
You know I had a topic on something like that a while ago, only I was saying that there should be one for tablets and HTPC's. In your case it's basically a hardware recognition issue. I was wondering why Network-Manager isn't on as a default myself it seems useful for either laptops or desktops. As in the other thread the debate basically boiled down to a better installer with better hardware support. The only thing that seems to actually be necessary from a functional point of view is HTPC Ubuntu as it would have to include different software.

---

### Post by Bezmotivnik on 2006-11-13
This would be wildly premature until wireless is **much** better supported.

---

### Post by barsanuphe on 2006-11-13
whatever is decided i think the word mobuntu sounds too much like [Mobutu]("http://en.wikipedia.org/wiki/Mobutu_Sese_Seko"), and you probably dont want that.

---

### Post by prizrak on 2006-11-14
> **Bezmotivnik said:**
> This would be wildly premature until wireless is **much** better supported.

Get Centrino. Hell the only feasible laptops as far as performance/battery life are Centrino anyways.

---

### Post by kitsos on 2006-11-14
> **prizrak said:**
>  As in the other thread the debate basically boiled down to a better installer with better hardware support.

I agree! I've been using ubuntu on an acer 5021 since the Hoary days and i must say that laptop support was horrible back then. I had problems with almost everything: from the speedstepping, to the harddisk spindown/the ATA100, graphics card, wireless, acpi, hinernate etc. It seems that there has been a **lot** of effort for better hardware support...with edgy everything works almost out of the box....only this Wifi always seems to be a pain.

---

### Post by Gargamella on 2006-11-14
In my opinion, this may happen in future when distro will have to be more specialized on a type of hardware and to work better at first boot

---

### Post by mostwanted on 2006-11-14
NetworkManager required you to enter a password every time you log on last I used it. Has this been fixed yet?

---

### Post by dannyboy79 on 2006-11-14
i would have to say that there already is a good laptop version, it's called Xubuntu. this is just my opinion though. i don't see a need for them to make a distro for every alternative there exists out there today. they make some basic os's and then you can customize and do what you want with it, that's why there is apt-get, aptitude, wget, etc etc. it's all free so take what they have already made (a lot of hard work) and do what you want and you can tell people that you made mobuntu yourself.

edited: "tell people that you made mobuntu yourself." this is a just a figure of speech, i don't know what ramifications there are for trying to do this depending on the license and such.

---

### Post by zachtib on 2006-11-14
in my experience, Ubuntu is very laptop friendly to begin with.  It ships with gnome-power-manager, all my laptop's special keys work fine, and are actually recognized by ubuntu, and the only thing I have to do following installation is to apt-get install networkmanager-gnome

---

### Post by chaosgeisterchen on 2006-11-14
The things that have to be improved from my point of view are:

**Power Management**
Ubuntu and Linux in general lack Power Management software as far as I know. Mechanics just as automatically dimming the display and sending the notebook into suspend to RAM or lateron to HDD are things that keep me from using Linux on my notebook.

**Suspending *all* machines**

Suspend to RAM should be a lot faster, just like the MacBook performs using OS X. And it should be available for all notebooks, not only on several of them. Mine for instance does neither hibernate nor suspend itself under Linux.

**Better Network-Management**

This is almost realized. Network Management is good now but it could be somewhat better.

**Special functions**

This is very hard to implement as each and every vendor sells its notebooks with different special features. Mine for instance has got buttons to turn Wireless LAN off, control the behaviour of the fan and to activate/deactivate the touchpad entirely. Things like these ought to work just like they work under Windows. 


If Linux and Ubuntu can solve all the listed problems it will be no big deal to come to a point where Linux gets notebooks to get more out of their battery power as Linux as a whole has bigger potentical in powersaving and ressource-friendly computing than Windows Vista will ever have. I would be very happy seeing this all happen soon.

---

### Post by zachtib on 2006-11-14
> **chaosgeisterchen said:**
> The things that have to be improved from my point of view are:

**Power Management**
Ubuntu and Linux in general lack Power Management software as far as I know. Mechanics just as automatically dimming the display and sending the notebook into suspend to RAM or lateron to HDD are things that keep me from using Linux on my notebook.

Those work perfectly for me, gnome-power-manager works nicely> 

**Suspending *all* machines**

Suspend to RAM should be a lot faster, just like the MacBook performs using OS X. And it should be available for all notebooks, not only on several of them. Mine for instance does neither hibernate nor suspend itself under Linux.

Ubuntu will never realize the same level of support that OS X has.  Apple makes both the hardware and the software, so naturally, they will work well together.  Why do you think OS X rarely, if ever, has any compatibility issues?  The issues with suspend, btw, are largely due to graphics drivers, which we have little control over.> 

**Better Network-Management**

This is almost realized. Network Management is good now but it could be somewhat better.

NetworkManager FTW!
as soon as network-manager incorporates functionality for static ip addresses (which I'm surprised they haven't done already), then it should be installed by default on Ubuntu > 

**Special functions**

This is very hard to implement as each and every vendor sells its notebooks with different special features. Mine for instance has got buttons to turn Wireless LAN off, control the behaviour of the fan and to activate/deactivate the touchpad entirely. Things like these ought to work just like they work under Windows. 

_All_ the special buttons on my Thinkpad work perfectly.  In fact, Ubuntu now gives me visual feedback when I use the volume or screen brightness buttons in GNOME> 

If Linux and Ubuntu can solve all the listed problems it will be no big deal to come to a point where Linux gets notebooks to get more out of their battery power as Linux as a whole has bigger potentical in powersaving and ressource-friendly computing than Windows Vista will ever have. I would be very happy seeing this all happen soon.

As I sort of mentioned earlier, these are all changes that should go directly into Ubuntu.  I think we have too many "flavors" as it is, and there's no need to make yet another one.

---

### Post by chaosgeisterchen on 2006-11-14
It's great that it all works for you, so you can tell me that your display is able to automatically lower brightness when not used and it's going automatically into suspend if you want it to do so?

I am very sad that I experience quite the opposite as I initially wanted to buy a notebook solely for using it with Ubuntu :(

---

### Post by prizrak on 2006-11-14
> > > Power Management
Ubuntu and Linux in general lack Power Management software as far as I know. Mechanics just as automatically dimming the display and sending the notebook into suspend to RAM or lateron to HDD are things that keep me from using Linux on my notebook.
Gnome-Power-Manager (installed by default) allows you to change those options. As far as power profiles Linux doesn't have any because it doesn't need any. The CPU will run at the lowest possible speed by default and step up as needed. 
> Suspending all machines

Suspend to RAM should be a lot faster, just like the MacBook performs using OS X. And it should be available for all notebooks, not only on several of them. Mine for instance does neither hibernate nor suspend itself under Linux.

This is a hardware issue, each manufacturer implements ACPI in their own way and in many cases the specs are closed. In my experience suspend to RAM is pretty quick but hibernation takes longer than shutting down then starting up and opening all of the stuff you had opened. 
> Better Network-Management

This is almost realized. Network Management is good now but it could be somewhat better.
Agree it does lack certain features. Also the Gnome-Keyring-Manager should be able to be set to not ask for a password. This mainly has to do with storing WPA/WEP keys for NM (well in thise case it can do alot more). 
> Special functions

This is very hard to implement as each and every vendor sells its notebooks with different special features. Mine for instance has got buttons to turn Wireless LAN off, control the behaviour of the fan and to activate/deactivate the touchpad entirely. Things like these ought to work just like they work under Windows.


That's a driver issue, on one of my laptops almost all of the keys work as they should. Turn off wi-fi/touchpad doesn't work at all. On my other laptop none of them work.

---

### Post by prizrak on 2006-11-14
> **chaosgeisterchen said:**
> It's great that it all works for you, so you can tell me that your display is able to automatically lower brightness when not used and it's going automatically into suspend if you want it to do so?

I am very sad that I experience quite the opposite as I initially wanted to buy a notebook solely for using it with Ubuntu :(

You need to do research when using alternative OS. I been mostly lucky with the hardware but on my last purchase I actually did some searching to make sure that what I wanted to get would work with Ubuntu.

---

### Post by zachtib on 2006-11-14
> **chaosgeisterchen said:**
> It's great that it all works for you, so you can tell me that your display is able to automatically lower brightness when not used and it's going automatically into suspend if you want it to do so?

I'm not sure if this is rhetorical or not...
But yeah, my display automatically dims when removed from its power source, and suspend to disk has always worked well for me> 

I am very sad that I experience quite the opposite as I initially wanted to buy a notebook solely for using it with Ubuntu :(

If you haven't bought one yet, look at either a Thinkpad or a System76 notebook, as both should have near-flawless Linux support.

---

### Post by chaosgeisterchen on 2006-11-14
I have already bought one, it's rather badly supported. You get me wrong, displays almost always dim if they are removed from their power source.

But under Windows I can configure it in a way that it dims down to about 20% of the brightness in about 6 seconds if I do no input for a certain period of time (for me it's 30 seconds). I have not yet seen that under Linux.

And as far as I know the display consumes quite the most of the power in a notebook. It would be very useful to have that under Linux also to save power and longer battery life. 

@prizrak:

Thanks for your opinion. It will not work as perfect as it maybe should be, suspend level of a MacBook can sadly not be achieved as it seems :(

---

### Post by Henry Rayker on 2006-11-14
I'd like if the installation would auto-run a dpgk-reconfigure xserver-xorg. That is the only thing I have to run through to get my display and touchpad working flawlessly. The touchpad actually works better than I have been able to get it to work in Windows (two- and three-finger taps for middle and right click, respectively).

My wireless cards' drivers leave a bit to be desired, but that's not the OS's fault.

Suspend and hibernate didn't work at all in Breezy, sort of worked in Dapper and work pretty well in Edgy. I see and upward trend, so I'm happy with that. My processor scales pretty well (but I can't seem to change the frequency manually if the AC adapter isn't plugged in...but that's not too bad; it scales automatically).

As for a separate flavor, I vote no. I'd like a little more configuration during the install (as I remember, Breezy had more setup in the installation), but I don't think it's really different enough to warrant a separate installation.

EDIT: I think there is a "dim screen when idle" box on the General tab of the options. I wonder if this can be configured to do what you want?

---

### Post by prizrak on 2006-11-14
> **chaosgeisterchen said:**
> I have already bought one, it's rather badly supported. You get me wrong, displays almost always dim if they are removed from their power source.

But under Windows I can configure it in a way that it dims down to about 20% of the brightness in about 6 seconds if I do no input for a certain period of time (for me it's 30 seconds). I have not yet seen that under Linux.

And as far as I know the display consumes quite the most of the power in a notebook. It would be very useful to have that under Linux also to save power and longer battery life. 

@prizrak:

Thanks for your opinion. It will not work as perfect as it maybe should be, suspend level of a MacBook can sadly not be achieved as it seems :(

Oh there is an automatic screen dimming time out, no GUI front end as far as I know though, I'm sure there is a script to edit somewhere. So far my beef is kind of retarded handling of battery alarms. I have an older Toshiba with a half dead battery that tends to discharge normally to about 70% and then jump down to 3. The default battery warning is 15% and critical 10% (I think don't remember) if the battery goes past that in one leap neither alarm will be tripped and the computer won't do the selected action on critical battery (in my case hibernate). That's something that needs to be fixed and is probably no more than an if statement somewhere.

---

### Post by chaosgeisterchen on 2006-11-14
Oh, I talk about Battery Miser which is a third party application. It enables automatic screen dimming. I am confindent that such software can be developed under Linux as well, but it goes quite deep into system programming in pure C - I have no idea of realising such a task.

---

### Post by public_void on 2006-11-14
The power management on my laptop isn't great. The battery/plug icon in the tray doesn't all ways change when changing from mains to battery. Sometimes the icon says mains at startup, when in fact its battery, and so I think its plugged when its not. The percentage left figure isn't accurate either (Windows isn't much better, it seem to fluctuate alot). 

Other than that my Ubuntu install is good, however I don't know if my wireless works, never tried it.

---

### Post by prizrak on 2006-11-14
> **chaosgeisterchen said:**
> Oh, I talk about Battery Miser which is a third party application. It enables automatic screen dimming. I am confindent that such software can be developed under Linux as well, but it goes quite deep into system programming in pure C - I have no idea of realising such a task.

Actually ACPI, in Ubuntu at least, is controlled via scripts. Back in Breezy times I actually edited them to change the behavior. Auto dimming is pretty easy, and there is support for it already it just needs an interface to change settings.

---

### Post by darkhatter on 2006-11-14
Isn't the new version of ubuntu working on better support for laptops. If they just copy what Novell did with their Linux that will be perfect.

---

### Post by xdevnull on 2006-11-14
I appreciate the feedback: on the name - I thought of Mobubuntu - but thought it might sound like mob - as in a group of angry people - but really, who cares what it is called.

There are two issues I think: 
One is hardware support.  This is obviuosly a complex issue dealing with not only the variety of hardware but how open the drivers are.  Intel graphics and centrinos tend to work great out of the box because intel provides enough info to make open-source drivers - so I looked for this when buying my laptop.  One the other hand, I wonder where the bulk of effort is going in hardware support and whether the Ubuntu developers have much to do with it.  It seems to me that more effort is being put into desktop hardware than laptop; though that may just be an impression.  Part of that is that we are dealing with a community and not single "corporation," and the other might have to do with the complexity of laptop hardware.  However, I think if Ubuntu began a laptop push/project/initiative, it might go a long way to improving things.  Though I also have to admit that things have come a long way, and Edgy supports a lot of things that Suse10.1 didn't - the gnome keyboard short-cuts thing is brilliant.

Second is package selection.  Maybe NetworkManager wasn't included because it can't be guaranteed to work, and with limited space it was dropped.  Maybe the same thing happened with installed support for widescreen monitors.  On the other hand, both of these things worked out-of-the-box with Suse10.1 - but they had a whole DVD of space to put programs.  I also don't know if bluetooth packages are included.  Downloading and installing these things isn't difficult - if you know what you're looking for - but I don't know if we can say that Ubuntu works out-of-the-box for even supported laptops if you have to download a package to make supported hardware work right.

---

### Post by chaosgeisterchen on 2006-11-15
> **prizrak said:**
> Actually ACPI, in Ubuntu at least, is controlled via scripts. Back in Breezy times I actually edited them to change the behavior. Auto dimming is pretty easy, and there is support for it already it just needs an interface to change settings.

I will watch out for it. Maybe I will suggest that as an option for the KDE powersaving daemon.

---

### Post by 23meg on 2006-11-15
Most common laptop woes are caused by lack of open specs and drivers and bad implementations of common specs such as ACPI, and there's no need for a separate laptop distro; laptop users make up a very large portion of the user base, and we wouldn't want to readjust things to make them work for that portion and take those things out of the standard distribution. 

Remember, derivatives should be only resorted to if absolutely needed, and if the advantages of deriving outweigh the disadvantages. It's best if laptop related fixes go straight into Ubuntu (and other distros), Ubuntu detects whether you're running a laptop at install time (already happening) and behaves accordingly, and Network Manager is installed by default (already coming up in Feisty).

---

### Post by prizrak on 2006-11-15
Laptops are not all that different from desktops actually. OS X, Windows and Linux all ship the same OS for both there isn't much need for a laptop only distro. Bluetooth is problematic most likely because of the drivers, I know that on my machine the problem is the little BT button that turns it on. Until that button is pressed BT won't be recognized as even installed into the system and I got no driver to make the button work so....

---

### Post by yachoo on 2006-11-16
As I know Ubuntu doesn't support many laptops. I haven't supported neither brightness changing nor fn keys, becouse of there is no acpi module for Toshiba laptops with phoenix bios. !@$!%^&%$#@!

Yes I think only-laptop distro is very good idea. There is a lot of unnecessary modules in kernel, and many more should be in.
I suggest not to name it neither Mobuntu nor Mobubuntu, becouse people won't like it.

---

### Post by prizrak on 2006-11-16
> **yachoo said:**
> As I know Ubuntu doesn't support many laptops. I haven't supported neither brightness changing nor fn keys, becouse of there is no acpi module for Toshiba laptops with phoenix bios. !@$!%^&%$#@!

Yes I think only-laptop distro is very good idea. There is a lot of unnecessary modules in kernel, and many more should be in.
I suggest not to name it neither Mobuntu nor Mobubuntu, becouse people won't like it.

Only the modules that are used by something are loaded so they are not really useless and as they take about 1MB total (if that) there isn't a space waste either.

---

### Post by xdevnull on 2006-11-17
I'm glad they've added Network Manager into default Feisty, and I agree that 1: it is better to have hardware support be the same across Ubuntu flavors and 2: making a new derivative should be a kind of last resort and it is better to keep things simple.  I didn't really know enough about the guts of the Ubuntu install to know if it really made sense, and each distro will have its advantages and disadvantages, I was just interested in hearing some pros and cons.  However, I did notice a few things that, in comparing it to other distros, seemed a pretty big ommission for someone that uses primarily a laptop.  There were just things in the default packages that seemed missing to me for a complete distro.  I knew enough to solve the problems and install the software, but I wonder if someone new to linux wouldn't have just given up.  

Wasn't there an optional DVD for an early Ubuntu version, that you could download in lieu of the CD.  I seem to remember it had several additional packages.  I haven't seen that for edgy.  At least not when I downloaded it.

---

### Post by calande on 2006-12-14
ROTF!! :mrgreen:
Almost same name as **_[African dictator]("http://fr.wikipedia.org/wiki/Mobutu_Sese_Seko")_**

[IMG]http://img218.imageshack.us/img218/8657/mobuntuaj1.png[/IMG]

---

### Post by happy-and-lost on 2006-12-14
> **barsanuphe said:**
> whatever is decided i think the word mobuntu sounds too much like [Mobutu]("http://en.wikipedia.org/wiki/Mobutu_Sese_Seko"), and you probably dont want that.

PortUbuntu?
Notebuntu?

---

### Post by jstad on 2006-12-14
I think that a laptop distro right now would be a waste. The only real lacking functionality is in network-manager (lack of some visual network support, ex. PEAP/MSCHAPV2 (2 stage auth)) and instead of focusing on making the changes by making a new distro would be better served by contributing to that particular project. Just my 2 cents.

---

### Post by calande on 2006-12-14
There are already tens of Ubuntu distros... It's wiser to concentrate on just one good project and to revamp it rather than diluting the effort.

---

