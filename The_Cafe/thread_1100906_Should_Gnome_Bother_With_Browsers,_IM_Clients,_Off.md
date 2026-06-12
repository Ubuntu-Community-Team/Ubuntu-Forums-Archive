---
title: "Should Gnome Bother With Browsers, IM Clients, Office Software, Etc?"
date: 2009-03-19
forum: The Cafe
---

### Post by Mark76 on 2009-03-19
Let's face it. Install any distro with Gnome as the default desktop and the packagers have already chosen Firefox, Pidgin and OpenOffice.org for you. Since there isn't the same integration between appliances for Gnome as there is between ones for KDE does it really make sense for the Gnome developers to continue working on apps like Epiphany, Telepathy and Gnome Office (Abiword and Gnumeric) as purely Gnome apps. Or should they just bite the bullet and make them desktop agnostic GTK apps (i.e. replace all Gnome dependencies with GTK ones)?

Or should the Gnome people push harder to get their stuff included as the default apps in Gnome based distros?

---

### Post by TheIdiotThatIsMe on 2009-03-19
I personally use most of Gnome Office (Evolution, Abiword, and Gnumeric), especially over OpenOffice (personal preference). What I'd really like is to see them push better integration with the desktop or with each other, and that's about it. Most distributions use other software mostly because it's more popular. I mean, seriously, not shipping Firefox as default? I don't personally use it (I use Epiphany), but it's easy to see why most people do and why most distros ship with it. Same for Pidgin (although I believe that was actually changed now to Gnome's default in Ubuntu). 

One of the main things I loved about KDE was tight application integration. Alas, my love for Ubuntu surpasses that, and I've heard far too many mixed stories of KDE on an Ubuntu base :-(

Anyways, now that I went way off topic, I don't know anyone who uses much of Gnome Office outside of Gnome (with the exception of some people using Abiword on Windows), so I'm not sure it'd really be worth the extra trouble to change much for the sake of less dependencies. And having said that, I'm not really sure it's dependant on Gnome, and not just GTK, is it? In Windows you only have to have GTK? (Yes, I'm not much of a techie).

---

### Post by Yashiro on 2009-03-19
It's upto the project directors and the people that donate their free time to the project.

---

### Post by interllect on 2009-03-19
I hope Gnome does something to keep up with kde, some type of innovation unique to Gnome that once someone has tried can never live without agian :D

---

### Post by Tibuda on 2009-03-19
About Office:
Both Abiword and Gnumeric are installed by default in Xubuntu intrepid (not sure about older versions). I don't think there are Gnome deps, as "Gnome Office" is only a name. "Gnome Office" apps are developed by different people, and are not integrated.

About IM:
Now that empathy supports voice and video, I guess many people will start using it. Pidgin has more features, but voice and video is a requirement for many people.

About Browsers:
There are many people complaining about Firefox performance in Linux. That's a good reason to keep and improve Epiphany. I just can't wait for a stable Epiphany webkit support.

---

### Post by Dr Small on 2009-03-19
The world should be without GNOME dependencies. I'll take GTK any day.

---

### Post by days_of_ruin on 2009-03-19
> **Dr Small said:**
> The world should be without GNOME dependencies. I'll take GTK any day.

They are phasing out the gnome libraries:D
Don't have a link but I read it somewhere on the gnome site today.

---

### Post by cardinals_fan on 2009-03-19
> **days_of_ruin said:**
> They are phasing out the gnome libraries:D
Don't have a link but I read it somewhere on the gnome site today.
[http://library.gnome.org/misc/release-notes/2.26/](http://library.gnome.org/misc/release-notes/2.26/)
> Fixing Usage of Deprecated Libraries

Starting with GNOME 3.0, various deprecated parts of GNOME will be removed. These deprecated components include GNOME-specific libraries such as libgnome, libgnomeui, libgnomeprint, libgnomeprintui, libglade and libgnomevfs. For applications that ship as part of the GNOME Desktop, a number of cleanup tasks have been carried out to ensure no deprecated code is used. This will ensure the smooth transition to GNOME 3.0.

Developers are strongly urged to follow this example in their own applications too. Furthermore, for any developers (or potential developers) who wish to help us out, the GNOME goals wiki page lists the various tasks that are yet to be completed.

---

### Post by sertse on 2009-03-19
Abiword and Gnumeric are as ubiquitous among any distro that markets as light as openoffice is among full featured distros...

Agreed of gnome/gtk. One of the main advantages of gtk is that it can is be taken outside Gnome. You can see this in the number of non Gnome desktops using gtk apps vs Non KDE desktops using qt...

---

### Post by Tibuda on 2009-03-20
I was wrong. There are gnome dependencies in both Gnumeric and Abiword.
Gnumeric depends on: libgnome2-0, libgnomeui-0, libgnomevfs2-0
Abiword depends on: libgnomecanvas2-0, libgnomeprint2.2-0, and libgnomeprintui2.2-0
These are the dependencies with gnome in the name, maybe there are more.

---

### Post by billgoldberg on 2009-03-20
> **Mark76 said:**
> Let's face it. Install any distro with Gnome as the default desktop and the packagers have already chosen Firefox, Pidgin and OpenOffice.org for you. Since there isn't the same integration between appliances for Gnome as there is between ones for KDE does it really make sense for the Gnome developers to continue working on apps like Epiphany, Telepathy and Gnome Office (Abiword and Gnumeric) as purely Gnome apps. Or should they just bite the bullet and make them desktop agnostic GTK apps (i.e. replace all Gnome dependencies with GTK ones)?

Or should the Gnome people push harder to get their stuff included as the default apps in Gnome based distros?

Sure they should.

Gnome is a Desktop Enviroment and it should have those in it.

Epiphany, Pidgin, ... are great applications.

---

### Post by Mr. Picklesworth on 2009-03-20
> **Mark76 said:**
> Let's face it. Install any distro with Gnome as the default desktop and the packagers have already chosen Firefox, Pidgin and OpenOffice.org for you. Since there isn't the same integration between appliances for Gnome as there is between ones for KDE does it really make sense for the Gnome developers to continue working on apps like Epiphany, Telepathy and Gnome Office (Abiword and Gnumeric) as purely Gnome apps. Or should they just bite the bullet and make them desktop agnostic GTK apps (i.e. replace all Gnome dependencies with GTK ones)?

Or should the Gnome people push harder to get their stuff included as the default apps in Gnome based distros?

But that's exactly the point: To make things integrate better for improved user interface. Epiphany is making *leaps* now, with its own Awesome Bar (except better :P) for example. The 2.27 - 2.28 cycle should be the last step towards integrating WebkitGtk to the core GNOME experience, and Epiphany is right there.

The Telepathy project is actually desktop neutral. It's developed with GNOME very much in mind, but the idea is to have something that works everywhere (including mobile) and can stretch to all sorts of uses.

Like Epiphany, Telepathy is (potentially) vastly superior to the competition when run on its target platform because other applications in GNOME (will) work with it for magical things. The outcome is that the user can just click through tasks like silk and only has to tell the computer anything once, if at all.

With regards to user experience on the desktop, Firefox and OpenOffice are both horrendously detrimental. They are inconsistent, they are ugly and they lack any hint of integration.

---

### Post by chucky chuckaluck on 2009-03-20
gnome should, xfce shouldn't. mark, isn't xfce heading more in the direction you're suggesting gnome should go?

---

### Post by Mark76 on 2009-03-20
I know they've recently adopted Midori as a browser. But they've always had their own apps for some things (there's a whole list of them on the xfce site) and used common GTK apps for other things.

It's good that Telepathy is going to be desktop neutral, the GOffice suite should follow suit.  It's just a shame the front end (empathy) is still a bit buggy.

To me Gnome and xfce are two different takes on the GTK desktop, with xfce being closer to one of the boxes (the option to use a right click applications menu instead of a panel applications menu) and Gnome being more like Windows (start menu on panel). It makes sense that they should share apps where appropriate. Obviously the creators of xfce are striving for lightness (despite the best efforts of the Xubuntu builders :p ). So they're going to choose lighter default apps than the Gnome maintainers will choose.

---

### Post by pt123 on 2009-03-20
> **Mr. Picklesworth said:**
> But that's exactly the point: To make things integrate better for improved user interface. Epiphany is making *leaps* now, with its own Awesome Bar (except better :P) for example. The 2.27 - 2.28 cycle should be the last step towards integrating WebkitGtk to the core GNOME experience, and Epiphany is right there.

With regards to user experience on the desktop, Firefox and OpenOffice are both horrendously detrimental. They are inconsistent, they are ugly and they lack any hint of integration.

Epiphany is a great example as to why they shouldn't. There were like little kids jumping on the new fad "Webkit". Epiphany Webkit was meant to be in 2.22, underestimating how far back their DE is, it is still not ready for 2.26. As for their awesome bar it is basically just "recoding" what Firefox has already done. There is still a bug with it indexing URLs of iframes:
[http://arstechnica.com/open-source/reviews/2009/03/hands-on-gnome-226-brings-incremental-improvement.ars/2](http://arstechnica.com/open-source/reviews/2009/03/hands-on-gnome-226-brings-incremental-improvement.ars/2)  

Rather than wasting resources in trying to compete with popular open source applications Gnome should be trying to help in assisting in porting the application. 

They should also be using these resources to fix  deficiencies in the DE. 
Like the not being able to set the number of lines scrolled by the mousewheel. (This interestingly is one of the issues with porting  Webkit to Epiphany, because Mozilla's Gecko had ability to "override" the number of lines scroll by the mouse wheel. But webkit expects the DE to handle this.)

Not being able to configure different wallpapers on multiple monitors or different workspaces. Should be what Gnome should be working on or the mouse wheel deficiency.

The problem with open source is that there are too many instances of "reinventing the wheel", what is disheartening is when large foundations like Gnome take part it in. Rather than assisting other open source projects.

---

### Post by interllect on 2009-03-20
> **pt123 said:**
> Epiphany is a great example as to why they shouldn't. There were like little kids jumping on the new fad "Webkit". Epiphany Webkit was meant to be in 2.22, underestimating how far back their DE is, it is still not ready for 2.26. As for their awesome bar it is basically just "recoding" what Firefox has already done. There is still a bug with it indexing URLs of iframes:
[http://arstechnica.com/open-source/reviews/2009/03/hands-on-gnome-226-brings-incremental-improvement.ars/2](http://arstechnica.com/open-source/reviews/2009/03/hands-on-gnome-226-brings-incremental-improvement.ars/2)  

Rather than wasting resources in trying to compete with popular open source applications Gnome should be trying to help in assisting in porting the application. 

They should also be using these resources to fix  deficiencies in the DE. 
Like the not being able to set the number of lines scrolled by the mousewheel. (This interestingly is one of the issues with porting  Webkit to Epiphany, because Mozilla's Gecko had ability to "override" the number of lines scroll by the mouse wheel. But webkit expects the DE to handle this.)

Not being able to configure different wallpapers on multiple monitors or different workspaces. Should be what Gnome should be working on or the mouse wheel deficiency.

The problem with open source is that there are too many instances of "reinventing the wheel", what is disheartening is when large foundations like Gnome take part it in. Rather than assisting other open source projects.


Webkit is just a port from kde who do are doing a fine job, even though i use xfce it must be said

---

### Post by pt123 on 2009-03-20
> **interllect said:**
> Webkit is just a port from kde who do are doing a fine job, even though i use xfce it must be said

No it isn't webkit is mainly developed by Apple who forked KDE's KHTML. Webkit had become far superior and it was difficult for KDE to port the changes back in to KHTML, that KDE dumped KHTML in favour of Webkit. 

Now Google is also a big player in Webkit.

---

### Post by Mr. Picklesworth on 2009-03-20
> **pt123 said:**
> Epiphany is a great example as to why they shouldn't. There were like little kids jumping on the new fad "Webkit". Epiphany Webkit was meant to be in 2.22, underestimating how far back their DE is, it is still not ready for 2.26. As for their awesome bar it is basically just "recoding" what Firefox has already done. There is still a bug with it indexing URLs of iframes:
[http://arstechnica.com/open-source/reviews/2009/03/hands-on-gnome-226-brings-incremental-improvement.ars/2](http://arstechnica.com/open-source/reviews/2009/03/hands-on-gnome-226-brings-incremental-improvement.ars/2)  

Rather than wasting resources in trying to compete with popular open source applications Gnome should be trying to help in assisting in porting the application. 

But that's exactly what they have been doing, up until now. Firefox's renderer is available as a detached component, precisely because it would be stupid (in hundreds of ways) to directly port the browser. Epiphany at the moment is Firefox for GNOME, in the sense that it uses the ready-made renderer and javascript component Firefox is best known for. The rest is a friendly interface tied closely to the GNOME platform with proper use of dbus (including to subscribe to RSS feeds), real MIME type handling and GTK+.
If they had tried to somehow shoehorn that into Firefox, they would still be at square 1.

As for switching to Webkit, there are very good reasons to do so including the fact that the rest of the GNOME platform is moving that way, too. (Devhelp is using WebkitGTK in Jaunty, for example).
There is nothing child-like in accepting that a goal was misdirected and proceeding to support the Gecko version of the browser as default.

Who is this "they," anyway? A free software project like GNOME doesn't just redirect resources like a typical corporation can. Novell or RedHat could, naturally, but from GNOME's perspective, contributors are contributors. It should be noted, of course, that MANY of the applications shipped with GNOME are developed by projects rather distinct from the platform people; they just guarantee to be nice and synchronize releases with GNOME.

---

### Post by interllect on 2009-03-20
> **pt123 said:**
> No it isn't webkit is mainly developed by Apple who forked KDE's KHTML. Webkit had become far superior and it was difficult for KDE to port the changes back in to KHTML, that KDE dumped KHTML in favour of Webkit. 

Now Google is also a big player in Webkit.

I was getting info from here, it sounds to me like kde/konqueror are the founders of this innovation

[http://en.wikipedia.org/wiki/WebKit](http://en.wikipedia.org/wiki/WebKit)

---

### Post by pt123 on 2009-03-20
> **Mr. Picklesworth said:**
> But that's exactly what they have been doing, up until now. Firefox's renderer is available as a detached component, precisely because it would be stupid (in hundreds of ways) to directly port the browser. Epiphany at the moment is Firefox for GNOME, in the sense that it uses the ready-made renderer and javascript component Firefox is best known for. The rest is a friendly interface tied closely to the GNOME platform with proper use of dbus (including to subscribe to RSS feeds), real MIME type handling and GTK+.
If they had tried to somehow shoehorn that into Firefox, they would still be at square 1.
That is why they shouldn't have messed it with it in beginning. Only tried assisting Firefox with it's Linux GTK version. They should be building components than the final application. Like the keyhole type back button in the Windows version of Firefox.
Has epiphany gained any marketshare from Firefox in the Gnome Broswer market? **No.**

Then you have this bungling with the webkit nonsense, which was highlighted by this example: Gecko allowed you to override the mousewheel lines scrolled by using about:config. So this worked in Epiphany until last year when a serious bug prevented you from entering values into it
[https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/201396](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/201396)

What was their developers response: "They were more interested in webkit and they weren't going to fix Gecko bugs. 

So now we have Epiphany which is bugged implementation of Gecko and an incomplete version of Webkit. The user is left with 2 half working applications compared to a user on Apple or Windows. 

> 
As for switching to Webkit, there are very good reasons to do so including the fact that the rest of the GNOME platform is moving that way, too. (Devhelp is using WebkitGTK in Jaunty, for example).
There is nothing child-like in accepting that a goal was misdirected and proceeding to support the Gecko version of the browser as default.

I got no issue with them working on WebkitGTK component but they shouldn't be wasting time on a application such as Epiphany-Webkit.
Now you have Google which will release an open source Linux version of it's webkit based broswer, hopefully the dreamers at Gnome don't think their Epiphany-Webkit has got any chance against Google's chrome. 

Till companies like Canonical that are interested in non-business desktop market have considerable influence over Gnome, the Linux desktop will continue to suffer.  Gnome as it currently stands is in no position to take the next leap in the Linux desktop by catering to influx of new users from Windows.

---

### Post by pt123 on 2009-03-20
> **interllect said:**
> I was getting info from here, it sounds to me like kde/konqueror are the founders of this innovation

[http://en.wikipedia.org/wiki/WebKit](http://en.wikipedia.org/wiki/WebKit)

You original post :
> 
Webkit is just a port from kde who do are doing a fine job, even though i use xfce it must be said

doesn't sound anything like that is on that page. 

Webkit was forked but it has changed massively, because of Apple, so saying "KDE are doing a fine job in regards to it" is very misleading.

---

### Post by Mr. Picklesworth on 2009-03-20
> **pt123 said:**
> That is why they shouldn't have messed it with it in beginning. Only tried assisting Firefox with it's Linux GTK version. They should be building components than the final application. Like the keyhole type back button in the Windows version of Firefox.
Has epiphany gained any marketshare from Firefox in the Gnome Broswer market? **No.**

Then you have this bungling with the webkit nonsense, which was highlighted by this example: Gecko allowed you to override the mousewheel lines scrolled by using about:config. So this worked in Epiphany until last year when a serious bug prevented you from entering values into it
[https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/201396](https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/201396)

What was their developers response: "They were more interested in webkit and they were going to fix Gecko bugs. 

So now we have Epiphany which is bugged implementation of Gecko and an incomplete version of Webkit. The user is left with 2 half working applications compared to a user on Apple or Windows. 


I got no issue with them working on WebkitGTK component but they shouldn't be wasting time on a application such as Epiphany-Webkit.

I didn't know about that particular bug report. Thanks...
You're missing an important detail, though: WebKitGTK is a key platform thing and it's where most of the focus is now going (not Epiphany specifically). Using WebKitGTK, Epiphany becomes rather simple so is not a "waste of time" at all.

Further, as I mentioned, porting Firefox to feel native in Linux with GNOME would be a tremendously pointless task. The GTK version is still using XUL, which is plain not adequate for a default application. (Not that I have a vendetta against non-standard UIs. I love Blender, for example. However, for apps like the web browser, being native is rather necessary).
In Firefox today aboard GNOME, context menus feel wrong, tabs behave wrong, toolbars disobey global settings (text beside icons!), menu accellerators cannot be changed and there are countless other inconsistencies.

That stuff could all be patched, giving us "Firefox 3.0 for GNOME" (and a demand for a name change, resulting in FireGnome or some such). However, I get the distinct impression that such patching would lead to a completely unsupportable, unstable application riddled with exceptions and "maybes".

---

### Post by cardinals_fan on 2009-03-20
> **Mark76 said:**
> I know they've recently adopted Midori as a browser. But they've always had their own apps for some things (there's a whole list of them on the xfce site) and used common GTK apps for other things.

It's good that Telepathy is going to be desktop neutral, the GOffice suite should follow suit.  It's just a shame the front end (empathy) is still a bit buggy.

To me Gnome and xfce are two different takes on the GTK desktop, with xfce being closer to one of the boxes (the option to use a right click applications menu instead of a panel applications menu) and Gnome being more like Windows (start menu on panel). It makes sense that they should share apps where appropriate. Obviously the creators of xfce are striving for lightness (despite the best efforts of the Xubuntu builders :p ). So they're going to choose lighter default apps than the Gnome maintainers will choose.
What makes Xfce different is modularity.  Fully-loaded Xfce isn't really any lighter than GNOME, but it is designed to be totally modular so you can pick and choose the components you need.

---

### Post by olejorgen on 2009-03-21
I think gnome should make most of their applications more desktop agnostic. I realise integration is good, but it doesn't have to cripple the application outside of Gnome.

---

