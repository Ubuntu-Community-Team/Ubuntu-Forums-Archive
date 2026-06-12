---
title: "New Unity, whitelist disabled = bad"
date: 2013-02-08
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2013-02-08
Anyone else notice multiple missing systray icons now that they've disabled the whitelist feature for the Unity notification area?

I have the latest sni-qt installed, but ktorrent's gone, truecrypt's gone, etc...

I don't think Canonical could have even *thought* of a better way to get me to go try Gnome3 and KDE again.

---

### Post by Paddy Landau on 2013-02-08
OMG, that is a disastrous decision!

I have a couple of applications (such as SpiderOak) that *require* the systray to work properly. Some vital functions are simply unavailable without it.

How do we raise this as a bug? It must be addressed.

---

### Post by dino99 on 2013-02-08
reporting from that page might be the better place

[https://launchpad.net/ayatana](https://launchpad.net/ayatana)

---

### Post by Paddy Landau on 2013-02-08
Thank you, I have reported it.

[https://bugs.launchpad.net/ayatana-ubuntu/+bug/1119420](https://bugs.launchpad.net/ayatana-ubuntu/+bug/1119420)

Please go there and vote for the bug (click the green writing at the top left of the page), and add your comments if applicable.

---

### Post by 3vi1 on 2013-02-08
I voted for your bug and added my own experience.  If people can show enough cases where the apps are not likely to ever get native notification support, perhaps they will reconsider the decision.

In the meantime, the message tray in Gnome 3 has already reminded me of why I don't use it.  I'm off to KDE-land for a bit.

---

### Post by Paddy Landau on 2013-02-08
Thanks, I see there are already four votes for the bug.

Your comment about TrueCrypt is correct; I had forgotten about that point.

I can't think what Canonical was thinking in removing the white list!

---

### Post by castrojo on 2013-02-08
KDE apps should be working, please file that as a bug (the indicators are based on KDE technology, most of the reason for moving to indicators was for a common spec that can be shared.)

Java and Wine apps are whitelisted and should work, as for the rest, the systray has been deprecated since 10.04 and left in for 3 years for apps to catch up.

---

### Post by Paddy Landau on 2013-02-08
> **castrojo said:**
> KDE apps should be working, please file that as a bug
Shouldn't that comment simply be added to the existing bug?

> **castrojo said:**
>  Java and Wine apps are whitelisted and should work, as for the rest, the systray has been deprecated since 10.04 and left in for 3 years for apps to catch up.
Unfortunately, that is not a satisfactory answer. Many applications use the systray — this is a standard feature in Linux and Windows; I don't know about Mac. (I notice that Skype is still white listed.)

For Unity to be useful, it has to work with applications that are established, respected and popular. SpiderOak and TrueCrypt are but two of them (I run four others).

I love Unity and would absolutely hate to have to leave it. But are you saying that the panel is going to be discarded ("the systray has been deprecated since 10.04")? Where will the various indicators go — clock, unified mail, Internet, settings, users? They are still there in 13.04. Will they be moved somewhere else in 13.10?

---

### Post by dino99 on 2013-02-08
As "the  systray has been deprecated since 10.04 and left in for 3 years for apps to catch up"; then we might report that issue against each app still needing the systray to take care of the actual design.

note: i've updated the report with the Castrojo comments above (thanks to refresh our mind)

---

### Post by castrojo on 2013-02-08
> **dino99 said:**
> then we might report that issue against each app still needing the systray to take care of the actual design.

Yep, here's an example: 

- [https://getsatisfaction.com/wakoopa/topics/support_ubuntus_application_indicator](https://getsatisfaction.com/wakoopa/topics/support_ubuntus_application_indicator)

And here's a list of topics links with resources you can send developers to:

- [http://askubuntu.com/questions/16453/how-do-i-migrate-from-systray-to-appindicators](http://askubuntu.com/questions/16453/how-do-i-migrate-from-systray-to-appindicators)

The appindicators have a fallback so it's simple for app authors to support them without breaking older distros.

---

### Post by castrojo on 2013-02-08
> **Paddy Landau said:**
> I love Unity and would absolutely hate to have to leave it. But are you saying that the panel is going to be discarded ("the systray has been deprecated since 10.04")? Where will the various indicators go &#8212; clock, unified mail, Internet, settings, users? They are still there in 13.04. Will they be moved somewhere else in 13.10?

The old systray was replaced with appindicators. The old tray was left there so app authors had time to move to appindicators:

- [https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

The panel isn't going away and icons in the top right aren't going away, the way that they're written is just different and more consistent (so that they get keyboard usability, HUD integration, etc.), instead of a tray and indicators you just have indicators for everything. 

The spec and code samples are mature now, the best thing to do is to point the authors of your favorite apps to the existing spec so they can implement it.

EDIT: and if they need help let me know and I can point them to developer resources to help sort them out.

---

### Post by dino99 on 2013-02-08
> **castrojo said:**
> The old systray was replaced with appindicators. The old tray was left there so app authors had time to move to appindicators:

- [https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

The panel isn't going away and icons in the top right aren't going away, the way that they're written is just different and more consistent (so that they get keyboard usability, HUD integration, etc.), instead of a tray and indicators you just have indicators for everything. 

The spec and code samples are mature now, the best thing to do is to point the authors of your favorite apps to the existing spec so they can implement it.

EDIT: and if they need help let me know and I can point them to developer resources to help sort them out.

Thanks again for the heads up  :D

---

### Post by Paddy Landau on 2013-02-08
> **castrojo said:**
> The spec and code samples are mature now, the best thing to do is to point the authors of your favorite apps to the existing spec so they can implement it.
Is this Linux-wide, or is it Ubuntu only? If it is Ubuntu only, I shall feel uncomfortable with this, as it would feel as though Canonical is dictating to the rest of the Linux community.

---

### Post by Paddy Landau on 2013-02-08
I'd like some help. I have tested 11 applications in 13.04. Please would you list any applications that I might have missed (I'll add them to this post).

I have tested the following:

**DO WORK**

[LIST]
[*] Caffeine
[*]Cuttlefish
[*]Deluge
[*]DropBox
[*]Redshift
[*]SpiderOak
[*]VLC
[/LIST]
 
** DO NOT WORK**

[LIST]
[*] Keyboard Indicators (this is erratic)
[*] ktorrent
[*] TrueCrypt
[*] yad
[/LIST]
 
I also need a reply to my question to **castrojo**: Is this deprecation Linux-wide or is it a unilateral decision by Canonical for Ubuntu? Because when I draft my emails to the relevant developers, I need to know how to word them. Either "Please would you adjust to the standards as described…" or "Please would you add a feature because Canonical is using a non-standard API…"

---

### Post by mc4man on 2013-02-08
In regards to vlc - the sni-qt package has produced an indicator for vlc for quite some time now (3 releases? ) - the indicator was garbage when first introduced & remains so...

---

### Post by Paddy Landau on 2013-02-08
> **mc4man said:**
> the indicator was garbage when first introduced & remains so...
Could you be specific? I have no problems with the VLC indicator; it works perfectly for me. What problems do you have?

---

### Post by castrojo on 2013-02-08
> **Paddy Landau said:**
> I also need a reply to my question to **castrojo**: Is this deprecation Linux-wide or is it a unilateral decision by Canonical for Ubuntu? Because when I draft my emails to the relevant developers, I need to know how to word them. Either "Please would you adjust to the standards as described…" or "Please would you add a feature because Canonical is using a non-standard API…"

There's no such thing as "deprecation Linux wide" because no one can really dictate anything to anybody. It is deprecated in Ubuntu however. The spec is designed so that developers can add support for the appindicator but "fallback" to the old mode if necessary. 

For most bug trackers this is a "wishlist" item, but usually if the developer has to get the app working with KDE anyway appindicators provide a nice clean way for people to do that.

---

### Post by Paddy Landau on 2013-02-08
Thanks for the reply, Castrojo.

If the developers can fall back anyway, and you are white-listing Java and Wine apps anyway, why can't we simply white list other applications? Will there come a time when Java and Wine apps no longer work?

I really don't understand.

I shall draft an email in a couple of days. But I am worried about this.

---

### Post by 3vi1 on 2013-02-08
> **castrojo said:**
> KDE apps should be working, please file that as a bug (the indicators are based on KDE technology, most of the reason for moving to indicators was for a common spec that can be shared.)

I'm not sure that will get much attention from the KDE/ktorrent developers, since ktorrent works fine with KDE, and KDE still supports systray icons even without whitelisting.  This Unity change only broke Unity users.

I even switched back to KDE after using Unity for 2 years, so sadly it's in the best interest of the KDE app developers to not do a thing if they want more users for KDE or other non-Unity desktops.  :\

---

### Post by mc4man on 2013-02-08
> **Paddy Landau said:**
> Could you be specific? I have no problems with the VLC indicator; it works perfectly for me. What problems do you have?
Sure - as seen here
Clicking on the indicator should hide/unhide vlc, it doesn't.(indicators don't 'know' left from right click
The hide/unhide option never changes, always says "Hide ..." even when un-hiding
Stop, previous & next don't work, stop is sorta ok because the play option is actually play/pause.
The status icon however is fully functional, left click to hide/unhide, all the functions work including separate switching  play/pause & stop, ect.
(to some extent mpris2 support makes the loss of status icons a bit more acceptable for media players...

Have returned the systray here to current unity, may be sustainable thru April release, after that maybe not.
(eventually when things are removed the effort needed to return isn't worth it or even  possible.

---

### Post by castrojo on 2013-02-08
> **Paddy Landau said:**
> Thanks for the reply, Castrojo. If the developers can fall back anyway, and you are white-listing Java and Wine apps anyway, why can't we simply white list other applications? Will there come a time when Java and Wine apps no longer work?


The fallback isn't for Ubuntu, the fallback is so the _application itself_ can run properly on systems that don't have appindicator support (like older distros or distros that choose to not support appindicators). This way app authors can support appindicators by adding support for it instead of replacing the old method. 

Wine and Java apps have always had integration problems with desktops that are more major than tray icons, we don't really have a solution to that, and there's not much we can really do there.

---

### Post by ELD on 2013-02-08
This seems like a really really bad change and it will come back to bite Ubuntu. People who use apps that won't get support for an indicator will be forced to use another OS. People don't like having to try to find another app or chase developers to add support for things like this - they would rather move OS.

---

### Post by 3vi1 on 2013-02-08
Gotta agree with ELD.  I actually *like* Unity... I'm the guy that defends it every week in the Linux Action Show IRC... and all this change did for me is make me appreciate how nice KDE is nowadays.

[[IMG]http://i.imgur.com/IKQUweWl.jpg[/IMG]]("http://i.imgur.com/IKQUweW.png")

I hope there's still a chance the backwards compatibility will be reconsidered.  Until then, I'm not recommending Ubuntu to my friends because I don't want to hear them whining at me if the trayicon for their app doesn't work and can't be whitelisted.

---

### Post by castrojo on 2013-02-08
> **3vi1 said:**
> .. and all this change did for me is make me appreciate how nice KDE is nowadays.

Ok so is anyone actually reading my posts or the spec? Appindicators are based on the KDE spec so that the two interoperate. The whole point is to have the applications work the same in both environments.

---

### Post by 3vi1 on 2013-02-08
> **castrojo said:**
> Ok so is anyone actually reading [...] the spec? Appindicators are based on the KDE spec so that the two interoperate. The whole point is to have the applications work the same in both environments.

And are you understanding that the apps still work in KDE (and every other DE) but not Unity?

The other DEs honor the spec, but they don't *kill legacy apps.*

I'm a huge Canonical/Ubuntu fan, but this is wrong.  This isn't even just Windows 8 wrong, this is "We're the Gnome team and you're going to do it this one way" wrong.  If Unity was losing the backwards compatibility to save some memory, I'd accept it... but the feature is still there, just locked out to users that would rather use Unity.

---

### Post by castrojo on 2013-02-08
> **3vi1 said:**
> The other DEs honor the spec, but they don't *kill legacy apps.*


I think you're blowing it out of proportion, a handful of apps can be fixed with relatively little effort. Desktops provide integration points for applications, and those APIs change and update over time. The Dash API changes, the indicator and messaging menus all get minor bumps over time, this is no different than any other software project. 

We've had a concerted effort for the last 3 years (and _two_ LTS releases) to help app authors move their apps over, most of them support it, even closed source applications like Dropbox and Steam. There's always going to be a few apps at the last end of an adoption curve, but luckily by pointing out the new specs to app authors you can help them support it.

---

### Post by 3vi1 on 2013-02-08
> **castrojo said:**
> I think you're blowing it out of proportion, a handful of apps can be fixed with relatively little effort.

I think you're not taking it seriously.  The apps I use, don't work with Unity now, period.  

I've been writing software for 30+ years, I'm quite aware of the environment and all sides of the equation.  From a user perspective, the apps didn't break - Unity did.  It's an arbitrary blockage not enforced by any other desktop.

---

### Post by mc4man on 2013-02-08
This is not atypical of unity dev, it goes on it's way according to plan or plans yet known.
If something is removed that Some like or find useful then generally too bad for them. 
(it's possible for decisions to be reversed, maybe this will, maybe not.
At some point you just move on & use what's provided or what's provided that can be modded or possibly move on from ubuntu/unity if it becomes something one no longer likes or finds interesting..

In this case the systray is still enabled (ATM), only that users can't add to as the schema is gone as is a few bits add. code (not that much really.

So as users you obviously file bugs & hope for the best but best bet is to just put it back yourselves or if still viable thru a ppa  at  release

Again ATM the commit or guts of can be reverted or apps can be added to the systray  which is still there as before with the schema (whitelist.

Or apps can be added back directly in the current source & 'told' to be available in the systray.

Ex. - I want vlc & audacious back in tray so in the source - 
unity-6.12.0daily13.02.07/panel/PanelTray.cpp line 33. 
Edited the blue to reflect an array of 4, added red, built unity, works fine, vlc & aud are back in the systray
```
const std::array<std::string, [COLOR="Blue"]4[/COLOR]> WHITELIST {{ "JavaEmbeddedFrame", "Wine"[COLOR="Red"], "Vlc", "Audacious"[/COLOR] }};
```

---

### Post by Paddy Landau on 2013-02-09
> **mc4man said:**
> ```
const std::array<std::string, [COLOR=Blue]4[/COLOR]> WHITELIST {{ "JavaEmbeddedFrame", "Wine"[COLOR=Red], "Vlc", "Audacious"[/COLOR] }};
```
Gasp! This is *hard-coded?* Really? The white-list is *hard-coded* into the program? Are we back in the early 1980's? :shock:

---

### Post by dpjg on 2013-02-09
I think the main argument for not hardcoding the whitelist is the following: You cannot remove the functionality anyways due to Java and Wine not willing/able to adjust to the new indicator-system. Hence it does not hurt you to give users the ability to edit the whitelist themselves. This *feature* is not exposed via a GUI anyways, which makes it "hard" for lot of people to whitelist this feature. This alone creates pressure to adopt the new system.

---

### Post by Paddy Landau on 2013-02-09
> **dpjg said:**
> I think the main argument for not hardcoding the whitelist is the following&#8230;
The main reason for not hard-coding the white list is decades of solid research into computer science, programming, business IT, maintenance costs, debugging, and maintainability. In this day-and-age, it is bizarre to see something like that hard-coded &#8212; especially when it had been parameterised beforehand.

---

### Post by alphacrucis2 on 2013-02-09
Would this be why pidgin isn't showing up there after I upgraded to RR this afternoon.?

---

### Post by rrnbtter on 2013-02-09
Greetings,

> **alphacrucis2 said:**
> Would this be why pidgin isn't showing up there after I upgraded to RR this afternoon.?

That, Gagim, kopete, Claws-mail and many others. You may feel relieved that many of these already support the Indicator feature but they don't have a Raring release in their PPA or  the Raring repository as of yet. 
All of this is just some of the aggravations of testing and nothing to switch to another OS over.  It looks to me that quite a few Unity features are being added with this release. Until this glitch I have been well pleased. It is a pain not to know if the messenger is logged in or if there is new mail in the inbox.  Time will fix it and time takes time.

---

### Post by ELD on 2013-02-09
> **castrojo said:**
> I think you're blowing it out of proportion, a handful of apps can be fixed with relatively little effort. Desktops provide integration points for applications, and those APIs change and update over time. The Dash API changes, the indicator and messaging menus all get minor bumps over time, this is no different than any other software project. 

We've had a concerted effort for the last 3 years (and _two_ LTS releases) to help app authors move their apps over, most of them support it, even closed source applications like Dropbox and Steam. There's always going to be a few apps at the last end of an adoption curve, but luckily by pointing out the new specs to app authors you can help them support it.

We are not blowing it out of proportion, you are now hard coding something that didn't need to be before. You can't force every app to use it, some apps just don't get updated but are still essential.

I just don't see a valid reason to remove the ability for users to white-list their own apps when you whitelist hard-code java and wine saying they won't be aware of it, it's just wrong. White listing was for slightly more advanced users anyway so what was the harm in keeping it in? Not like it required much effort to maintain now honestly.

Like others pointed out other desktops support legacy icons, i think you guys should too.

I know what i say will fall on deaf ears anyway since i'm just a simple users, but change like this annoys me.

I just hope that anyone using apps that don't support indictors bug the crap out of the developers to add one in or they risk their app becoming useless.

---

### Post by Paddy Landau on 2013-02-09
> **ELD said:**
> I just hope that anyone using apps that don't support indictors bug the crap out of the developers to add one in or they risk their app becoming useless.
The problem is that said developers could just as easily turn around and say, "No. Canonical did this, it's Canonical's problem, and Unity is a crap system anyway; why are you using it?" The fact that I love Unity would be irrelevant to the developer.

This is an unfortunate situation. I shall draft a (polite) email to the developers of the applications that I have found not to work (so far, Keyboard Indicators, ktorrent, TrueCrypt and yad), but I know that in at least two cases, the developers work in their spare time and have little time to make changes just to please Canonical.

I know it was not meant this way, but to the average user and developer, this looks (from the outside) like an arrogant move, and it is unpleasant. Moving from using parameters (proper programming practice) to using hard-coding (deprecated programming practice since the early 1980's — well, technically even before then) just makes it look worse.

---

### Post by mc4man on 2013-02-09
Here's the bug that caused, not all were in agreement (those whose opinion matters that is
[https://bugs.launchpad.net/ayatana-design/+bug/974480](https://bugs.launchpad.net/ayatana-design/+bug/974480)

---

### Post by castrojo on 2013-02-09
> **Paddy Landau said:**
> The problem is that said developers could just as easily turn around and say, "No. Canonical did this, it's Canonical's problem, and Unity is a crap system anyway; why are you using it?" The fact that I love Unity would be irrelevant to the developer.

Plenty of people use Unity, it's in an application author's best interest to work with the default desktop in Ubuntu.

> This is an unfortunate situation. I shall draft a (polite) email to the developers of the applications that I have found not to work (so far, Keyboard Indicators, ktorrent, TrueCrypt and yad), but I know that in at least two cases, the developers work in their spare time and have little time to make changes just to please Canonical.

This isn't just to "please Canonical." Like I said, please read the specs, having a _consistant_ way to do indicators is a win for users, I'll copy them here:

Application indicators are more consistent – no more left and right-click inconsistency. Always left click to see the items.

- Scrubbing – you can click once on an app indicator and scrub left and right through other indicators with your mouse.

- More accessible – importantly, scrubbing also applies to the keyboard: this means you could bind a key to the indicator applet, hit that key and then use the arrow keys to navigate through all the indicators.

- Themable panel icons – you can set a specific icon to be a panel icon for an indicator: this should make it easier for creating single colour panel icons for light and dark themes.

- KDE/GNOME compatibility – KDE applications running in GNOME will have their application notification menus rendered with GTK widgets and vice-versa. 

> I know it was not meant this way, but to the average user and developer, this looks (from the outside) like an arrogant move, and it is unpleasant.

APIs change from time to time, authors are used to it, and we've provided quite a long window for them to add support to apps, and if you look at the number of applications that are supporting appindicators the app developer community have overwhelmingly supported it, other than a few apps that can be fixed.  

> Moving from using parameters (proper programming practice) to using hard-coding (deprecated programming practice since the early 1980's — well, technically even before then) just makes it look worse.

Java and WINE apps will never integrate properly with the desktop, it's been this way since before Unity.

---

### Post by Paddy Landau on 2013-02-09
> **mc4man said:**
> Here's the bug that caused, not all were in agreement (those whose opinion matters that is
[https://bugs.launchpad.net/ayatana-design/+bug/974480](https://bugs.launchpad.net/ayatana-design/+bug/974480)
Thank you.

I have added a comment, which, as you imply, will probably be ignored. But others can add their opinions.

---

### Post by Paddy Landau on 2013-02-09
> **castrojo said:**
> Plenty of people use Unity, it's in an application author's best interest to work with the default desktop in Ubuntu.
Yes, I realise all the benefits. We are not arguing with that. What we are upset about is that a freedom has been removed from us, entirely unnecessarily.

> **castrojo said:**
> This isn't just to "please Canonical."
Sorry; I thought that it was Canonical who introduced these specifications, looking at the links you previously gave. Were these done by the Linux Foundation? If not, who did them?

> **castrojo said:**
>  Like I said, please read the specs, having a _consistant_ way to do indicators is a win for users
Again, not arguing about this! I shall certainly include it in my emails to the developers. But it **does not solve the problem** — on the contrary, this change has **caused new problems**.

> **castrojo said:**
> Java and WINE apps will never integrate properly with the desktop, it's been this way since before Unity.
That is absolutely no reason to hard-code the parameters! If this is how the rest of Unity is run, that may explain (and I don't mean this in a nasty way) why Unity has been so riddled with bugs. Programming absolutely should adhere to standards, including those that have been proven, not only with research but also with the test of time, to work. Hard-coding has been proven to be problematic, and soft-coding to be beneficial.

---

### Post by Paddy Landau on 2013-02-09
Mark Shuttleworth has warned me off. So, I shall be withdrawing from the whitelist topic (although I shall continue to follow it).

If anyone wishes to take over the list and write emails to their developers, please go ahead and do so.

---

### Post by EgoGratis on 2013-02-09
I do understand the frustration of not having the indicator for some apps  anymore and i do understand the fact the window to add indicator support was wide. Probably the remaining apps need some "push" and i guess this "push" has come...

P.S. We must admit indicators in Ubuntu are quite consistent ATM!

---

### Post by cariboo on 2013-02-09
You have to wonder why the creators of applications that don't work with app-indicator haven't updated yet, they've had 3 years notice. Most of them have gone to the trouble to create a .deb, so I can't see it being any harder to modify their programs.

---

### Post by shiznix on 2013-02-10
I hope this evolves into something that works for Ubuntu.
At this present time though it just seems like a poorly thought out decision.

Quite strange really to lock the users out of the applications they want to use because Ubuntu expect the greater software community to implement a Ubuntu only API whose functionality is already covered in the API of the GUI toolkits (eg.GTK/QT).

Maybe all we need is some savvy pro-Ubuntu software developer to create a 'systray-indicator' that resides on the top panel with all the other indicators, but is a placeholder for the thousands of applications that already use their respective GUI toolkit's systray implementation and so will never port to a distro specific API.

---

### Post by alphacrucis2 on 2013-02-11
One issue that this was causing me is cryptkeeper. However I have found an alternative called gnome-encfs-manager. It hasn't been packaged for the normal repos yet but there is a ppa. Seems to work ok.

[https://launchpad.net/~gencfsm/+archive/ppa/+packages](https://launchpad.net/~gencfsm/+archive/ppa/+packages)

---

### Post by Favux on 2013-02-11
Had to write a white list module.  Had to write a Gnome shell extension.

Quick look at the Python code link from post #10.  Is there a Gtk2 appindicator?  Or is AppIndicator3 only Gtk3?

Do I want to spend the time reading through the spec.s?  What if I discover the current implementation of the app.'s system tray icon breaks the intended UI?  Rewrite code just for 13.04?  Course I have to make the cross Distro/Desktop installer detect Raring as a special case (v.s. Precise or Quantal) now.

Or do I say the heck with it?  Becoming more and more tempting.  Only a few thousand users, so hey.

---

### Post by rrnbtter on 2013-02-11
Greetings,
Looks like we got a new Bluetooth Indicator today. From my perspective it is very nice. Hope it is a prelude to the standard for all of the rest that are to come.

---

### Post by diesch on 2013-02-11
> **Favux said:**
> Had to write a white list module.  Had to write a Gnome shell extension.

Quick look at the Python code link from post #10.  Is there a Gtk2 appindicator?  Or is AppIndicator3 only Gtk3?


Use
```
import appindicator
```instead of
```
from gi.repository import AppIndicator3 as appindicator
```if your app is using PyGtk instead of PyGObject.

---

### Post by Favux on 2013-02-11
Thanks diesch.  That's simple enough and helps.

---

### Post by Paddy Landau on 2013-04-11
I have raised requests for both [yad]("http://code.google.com/p/yad/") and [TrueCrypt]("http://www.truecrypt.org/") to change their programs.

You can see [the yad request]("http://code.google.com/p/yad/issues/detail?id=167"), but I cannot find the TrueCrypt request (the [TrueCrypt bug area]("http://www.truecrypt.org/bugs/") does not seem to have listing or search facilities).

Let's hope that the developers accept this change. If not, we have a problem.

---

### Post by ELD on 2013-04-14
X-Chat really needs proper indicator support as well.

---

### Post by Paddy Landau on 2013-04-14
> **ELD said:**
> X-Chat really needs proper indicator support as well.
I don't know xchat; I only know xchat-gnome (they are similar but different). However, both of them have their icons integrated with the messenger icon in the taskbar. I don't know if that would solve your problem.

---

### Post by ELD on 2013-04-14
The X-Chat program only gets an indicator in the messenger icon if you install the package i noted called xchat-indicator which doesn't work correctly - you cannot resume the "closed to tray" x-chat, clicking on the tray icon in the messaging menu opens a new instance = very very annoying.

---

### Post by Paddy Landau on 2013-04-14
> **ELD said:**
> … clicking on the tray icon in the messaging menu opens a new instance = very very annoying.
In that case, I think it would be a good idea for you to raise a bug report. Try raising one with both Ubuntu and XChat and see what happens.

---

### Post by ELD on 2013-04-14
I just did [https://bugs.launchpad.net/ubuntu/+source/xchat-gnome/+bug/1168876](https://bugs.launchpad.net/ubuntu/+source/xchat-gnome/+bug/1168876)

Until then ideally I need to find a client that works properly in the tray so when I close it, it closes to tray and I can re-open :(

---

### Post by Scoobin on 2013-04-14
Problem solved?
[https://bugs.launchpad.net/unity/+bug/974480/comments/42](https://bugs.launchpad.net/unity/+bug/974480/comments/42)

---

### Post by monkeybrain2012 on 2013-04-14
> **Scoobin said:**
> Problem solved?
[https://bugs.launchpad.net/unity/+bug/974480/comments/42](https://bugs.launchpad.net/unity/+bug/974480/comments/42)

ppa is nice, but there is no guaranteed that it will keep up. There was a ppa to put dodged windows back to Unity but that has not been updated for a long time because the maintainer is busy or couldn't keep up with new Unity releases so now it is useless. So the problem is not solved, it is just a temporary solution. I like Unity, but because of things like that I can't recommend to others at this stage, I don't want people to keep ringing me up asking why this or that doesn't work.

---

### Post by tdockery97 on 2013-04-15
Thank you for that systray solution.  Works well.

Re: the Unity window dodge, it was updated and works great with 13.04.

---

### Post by monkeybrain2012 on 2013-04-15
> **tdockery97 said:**
> 

Re: the Unity window dodge, it was updated and works great with 13.04.

Where and when? This ppa is only for Precise and hasn't been updated  since Unity 5.18.0 (not that I cannot do without it, but it is nice when it is around) [https://launchpad.net/~ikarosdev/+archive/unity-revamped](https://launchpad.net/~ikarosdev/+archive/unity-revamped)

---

### Post by Scoobin on 2013-04-15
> **monkeybrain2012 said:**
> ppa is nice, but there is no guaranteed  that it will keep up. There was a ppa to put dodged windows back to  Unity but that has not been updated for a long time because the  maintainer is busy or couldn't keep up with new Unity releases so now it  is useless. So the problem is not solved, it is just a temporary  solution. I like Unity, but because of things like that I can't  recommend to others at this stage, I don't want people to keep ringing  me up asking why this or that doesn't work.
Fair enough. It's a working solution for the time-being at least. But yeah I agree that Canonical have done users a disservice with the removal of the white-list. 

[QUOTE=tdockery97]Thank you for that systray solution.  Works well.

Re: the Unity window dodge, it was updated and works great with 13.04.[/QUOTE]
No problem.

---

### Post by tdockery97 on 2013-04-15
> **monkeybrain2012 said:**
> Where and when? This ppa is only for Precise and hasn't been updated  since Unity 5.18.0 (not that I cannot do without it, but it is nice when it is around) [https://launchpad.net/~ikarosdev/+archive/unity-revamped](https://launchpad.net/~ikarosdev/+archive/unity-revamped)
You can find the .deb files for 32bit and 64bit here:  [http://www.webupd8.org/2013/02/how-to-get-unity-launcher-window-dodge.html](http://www.webupd8.org/2013/02/how-to-get-unity-launcher-window-dodge.html)

---

### Post by Saptrans on 2013-04-29
> **castrojo said:**
> Plenty of people use Unity, it's in an application author's best interest to work with the default desktop in Ubuntu.



This isn't just to "please Canonical." Like I said, please read the specs, having a _consistant_ way to do indicators is a win for users, I'll copy them here:

Application indicators are more consistent – no more left and right-click inconsistency.

IMHO, different behavior for different mouse buttons doesn't feel like inconsistency. Feels more like "functionality". Left click to reveal app, right click for menu. You don't even need to remove functionality to make it work on tablets. You can map right click to long press or double tap. Slide down from tray icon gesture would work even better.

Anyway, I strongly prefer inconsistent tray icon to not existent tray icon.

---

### Post by Paddy Landau on 2013-04-29
> **Saptrans said:**
> I strongly prefer inconsistent tray icon to not existent tray icon.
+1. I don't know why Canonical is trying to tell the user what the user wants. That's the wrong way around, isn't it?

---

### Post by ELD on 2013-04-29
> **Saptrans said:**
> 
Anyway, I strongly prefer inconsistent tray icon to not existent tray icon.

Bingo, try using X-Chat in unity, god damn pain, you have to install a seperate "indicator" that doesn't actually work (yes i've submitted the bug report which is going ignored) you minimize to tray, click the indicator in the message menu...and a new instance opens not the current one...*sigh*.

So I now use **Cinnamon** since it has a proper tray :)

Unity is a real *pain* to actually work with.

---

### Post by recover89 on 2013-06-28
For a TrueCrypt indicator, see ppa:stefansundin/truecrypt. [https://launchpad.net/~stefansundin/+archive/truecrypt](https://launchpad.net/~stefansundin/+archive/truecrypt)

---

