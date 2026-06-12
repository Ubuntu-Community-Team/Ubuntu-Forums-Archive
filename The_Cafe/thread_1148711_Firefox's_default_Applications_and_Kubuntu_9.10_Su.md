---
title: "Firefox's default Applications and Kubuntu: 9.10 Suggestions"
date: 2009-05-04
forum: The Cafe
---

### Post by jbrown96 on 2009-05-04
I seriously doubt this is the appropriate place to suggest this, but perhaps someone can point me in the right direction. 

I've always liked KDE a lot more than Gnome, and since KDE 4.2 is very usable (arguable I suppose), I've been using it quite a bit lately. However, I've run into some serious usability problems with Firefox. I know that it isn't the default browser, and although Konqueror is good (I really do like it), most (or atleast a lot) people still use Firefox, especially for flash support, etc.

Here's the problem: Firefox doesn't know about any KDE programs. Here's just the best example I can think of. If I download a .torrent file in Ubunutu, Firefox knows that Transmission should be associated with it. Very reasonable and really good for new users. They probably don't know what program to use, which makes it really important that they be given an option to immediately open that file. However, in Kubuntu, even though Ktorrent is installed by default, Firefox doesn't know about it. Furthermore, with the "complicated" directory structure (I'm talking about new users here) in Linux, they would never be able to find /usr/bin/ktorrent to assosicate Firefox with Ktorrent. The only option is to download the file then open it, or I suppose have Ktorrent watch a folder (not simple!).

There are a lot of other examples, but I'm using Mandriva right now, so I can't determine which programs. Yet, it seems like all the KDE apps are unknown; whereas, the cross-platform (cross-DE?) apps like OO.org are known.

Where would I submit a bug report/feature request to have better default behavior for Firefox in future versions? 
Eventually, it would be really cool to have some script run with apt-get similar to what happens with UFW (where installing something like openssh-server automatically opens port 22). The idea would be that if I download an application that supports filetype X, and I don't have a default application in Firefox for filetype X, then apt-get should automatically modify the Firefox profile. I don't mean that it would automatically open the file, but it should at least have the application listed, so a user doesn't get an error if they try to open it instead of saving. This is much more ambitious than just having a better default profile, but I'm looking for an opensource project for the summer, so maybe that's something I could work on.

---

### Post by lzfy on 2009-05-04
I know that openSUSE doesn't have this problem. Last time I used it it did recognize the KDE apps.

---

### Post by mister_pink on 2009-05-04
I'd submit this as a bug report on launchpad. The features you mention in ubuntu are provided by the package ubufox. So kubuntu could have kubufox to do the same thing. Shouldn't be too hard to make from ubufox either really. Might have a look now in fact - make sure if you report this on launchpad that you link it in this thread, I'd be interested to have a look.

---

