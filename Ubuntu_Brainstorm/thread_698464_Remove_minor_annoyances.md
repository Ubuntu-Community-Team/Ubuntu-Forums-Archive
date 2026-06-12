---
title: "Remove minor annoyances"
date: 2008-02-16
forum: Ubuntu Brainstorm
---

### Post by steve196 on 2008-02-16
Just to avoid people going through the same rituals constantly

* Do not do anything with the system time during setup or bootup. It is extremely annoying. Wait for the user to do something about it if it is wrong.
* Give the user a chance to tell the system, what resolutions and frequencies his monitor is capable of. Do not just let the software guess it.
* Do not start indexing right away. It is extremely annoying if this activity starts before you can turn it off, and it doesn't even tell you, where its databases are, so you cannot even delete them and reclaim the space.
* Have nautilus default to list view with preview turned off and a tree on the left. That is how everyone i know wants it.
* Have the annoying and dangerous password remembering function in firefox off by default.
* Have compiz off by default. It leads to weird stuff, like dialogue fields forgetting their entries in completely unrelated programs.

* Give people a choice between several network managers. For me, for example, dhcpcd is the only one that works. It would be great, if i could replace the default one with that or another from inside the control panel. (ok, for this last one, i do not know, how many people need that and it may be too few, for it to be worth the effort)

---

### Post by smartboyathome on 2008-02-16
> **steve196 said:**
> * Do not do anything with the system time during setup or bootup. It is extremely annoying. Wait for the user to do something about it if it is wrong.

I like that it makes the system time my time by default. Why should it be up to the user to set the time when it can be done automatically?

> **steve196 said:**
> * Give the user a chance to tell the system, what resolutions and frequencies his monitor is capable of. Do not just let the software guess it.

This can lead to problems, since some graphics cards (like my NVidia card) need proprietary drivers from NVidia in order to use the monitor's resolution, and when the user selects the monitor's resolution, it can crash X.

> **steve196 said:**
> * Have nautilus default to list view with preview turned off and a tree on the left. That is how everyone i know wants it.

I like nautalus' preview tree view. It seems more "organized" to me. I do a lot of picture editing, and have a lot of other files on my system, and this helps me find them quickly and easily.

> **steve196 said:**
> * Have the annoying and dangerous password remembering function in firefox off by default.

I also like to use the password remembering in firefox since I am lazy and don't want to keep having to enter my username and password each time I visit a site.

> **steve196 said:**
> * Have compiz off by default. It leads to weird stuff, like dialogue fields forgetting their entries in completely unrelated programs.

I use Compiz a lot on newer machines, and have never seen anything like this happen. Compiz is one of the biggest attractors for new users to use Linux, and I think it would be a bad move to get rid of it on systems that can handle it.

> **steve196 said:**
> * Give people a choice between several network managers. For me, for example, dhcpcd is the only one that works. It would be great, if i could replace the default one with that or another from inside the control panel. (ok, for this last one, i do not know, how many people need that and it may be too few, for it to be worth the effort)

You mean network managers as in ones like WICD and Network Manager? This is being discussed in another thread, and WICD and Network Manager conflict as they provide the same functions, and both being used on the same system can screw it up.

---

### Post by chrisccoulson on 2008-02-16
> **steve196 said:**
> * Give the user a chance to tell the system, what resolutions and frequencies his monitor is capable of. Do not just let the software guess it.
This would take us back to the dark ages, where users have to manually edit their xorg.conf. What happens if a user plugs their laptop in to an external monitor? I think they'd just want it to work, rather than have to tell the computer what resolutions and frequencies it supports.

> **steve196 said:**
> *Do not start indexing right away. It is extremely annoying if this activity starts before you can turn it off, and it doesn't even tell you, where its databases are, so you cannot even delete them and reclaim the space.
Turning off indexing by default might save you 30 seconds. Turning it off by default may also make the feature undiscoverable for some new users. I'd rather it was provided by default, but easy to disable for the users who don't want it. Also, Tracker tells you when it is indexing in Hardy, via an icon in the notification area. The icon also allows you to pause indexing.

> **steve196 said:**
> *Have nautilus default to list view with preview turned off and a tree on the left. That is how everyone i know wants it.
This is all down to personal preference. My girlfriend prefers icon view with previews, I prefer icon view with previews in some folders and list view in other folders. So, everyone has different tastes. The default will *never* please everyone.

> **steve196 said:**
> * Have compiz off by default. It leads to weird stuff, like dialogue fields forgetting their entries in completely unrelated programs.
I agree with smartboyathome. Compiz is an important feature for a lot of new users. A lot of people run it without any issues on supported hardware. It doesn't run by default on unsupported hardware. If you're having issues like this on supported hardware, then file a bug. Disabling Compiz by default for everyone because YOU have a problem, does not help anyone.

> **steve196 said:**
> * Give people a choice between several network managers. For me, for example, dhcpcd is the only one that works. It would be great, if i could replace the default one with that or another from inside the control panel. (ok, for this last one, i do not know, how many people need that and it may be too few, for it to be worth the effort)
No, it's not worth the effort. Please say what doesn't work for you in the default Network Manager. If you do that, then Network Manager could be improved, which may benefit everyone.

---

### Post by steeleyuk on 2008-02-17
Isn't there a delay on indexing for 45 seconds until after the system has started anyway? Thats the default that Tracker 0.6.4 sets for me.

---

### Post by steve196 on 2008-02-17
The problem with automatic time and screen resolution settings is, of course, that the computer often does it wrong. 

The automatic clock insists on daylight saving time in the middle of winter. I can fix that, by selecting a time zone west of me as long as it is winter, but that is a somewhat unelegant solution. I don't complain about that. Automagical programs getting stuff wrong is normal on any OS and fixing  a few specific bugs will not change that rule. Furthermore during setup (at least with wubi) ubuntu sets the time without asking me for the timezone, which is pointless.

Screen resolution is the same thing. Here,  Ubuntu just greatly underestimates what my monitor is capable of (my old one and new one alike). Windows the same, but on windows i can do things like force it to show all resolutions, expand the frequency list to show all etc. It gives me warning messages, but then it does it. 

The nautilus default thing may be a matter of taste. Though i had to look for some time, to figure out how to get the tree. At first (long ago) i thought, it was malfunctioning because i could not get branches to open up, until i realized there was no tree view.


I think turning compiz off is very important. For example if i add nameservers to the network panel, they are forgotten as soon as the panel is closed, if compiz is on (this is on hh alpha, so it might improve, once the official version comes out, but it is just one example). I immediately guessed right, that compiz was the culprit, and you would too probably, but an average user, who doesn't know it, will never guess, that "desktop effects" are the cause for this problem. In three years things might be different, but compiz as it is now should be for advanced users.

The password remembering function is easy to turn on if you need it, but it is a dangerous default. I have seen horrible examples of people exposing their email accounts with that. You would delete those passwords before giving your laptop to someone else for fixing some problem, for example. Some would just not think that far.

The network manager issue really seems limited to my provider (or my brand of cable modem, i don't know), who just does not accept dhclient. I do not know why and i cannot find out, because customer support is Windows only. It would be great for me, to have dhcpcd on the cd instead of having to copy it from somewhere, but since the problem is apparently not more widespread, it is not really important.

---

### Post by mangar on 2008-02-17
Steve:
I think that what you actually want is workaround for some bugs you've 
encountered.. adding a preference toggle for each bug is not the right way to fix bugs.

If you want those bugs to be fixed, submit bug reports to launchpad.net (and if you have the time and inclination - patches will probably be happily accepted)- this way the problem will be fixed not only for you, but for other people with the same problems (the timezone problem and the monitor resolution seems to be very fixable, and will benefit other people as well).

About Nautilus default look - you've described Windows Explorer default arrangement in Windows Xp - it's a matter of preference - I prefer a List view, with The bookmark side panel. When I use windows, I use qttabbar and qtaddressbar in order to add crumbread view and tabs to Windows Explorer (which than looks very much like Nautilus).

About passwords - Ubuntu is a desktop OS, and therefore meant to be used with a different account for each user - password exposure will happen in very limited use cases  - when using a non-limited account in a Kiosk, for example, and that's about it.

---

### Post by steve196 on 2008-02-17
Except for the clock thing, the "bugs" i describe happened on my computer with any ubuntu version since breezy badger (i once made a bug report about the dhclient thing), although they were all, except dapper, fresh installs. The screen resolution thing happens to win2k too (only it is easily fixable there) so it cannot be an ubuntu thing. Point is, these things do not happen to other people. Other things happen to other people.

The main problem is, there is no middle ground. Either you can do some easy primitive settings to customize a system that is assumed to be perfectly working, or you can go into total expert mode, read fat books and edit configuration files by hand. Troubleshooting is supposed to be done by experts only, and i think, that is not realistic in most scenarios.

---

