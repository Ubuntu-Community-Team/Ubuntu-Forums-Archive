---
title: "Last-exit 1.0 is out! (Gnome Last.fm radio)"
date: 2006-07-10
forum: The Cafe
---

### Post by mostwanted on 2006-07-10
Much more stable. Here is a link to the official (and very pretty I might add:P) site:

[http://www.o-hand.com/~iain/last-exit/](http://www.o-hand.com/~iain/last-exit/)

And here is a link to a nice Dapper deb:

[http://burtonini.com/debian/dapper/last-exit_1.0-1_i386.deb](http://burtonini.com/debian/dapper/last-exit_1.0-1_i386.deb)

[SIZE="7"]**Update!!! Version 2.0**[/SIZE]
Here is version 2.0, which I presume is a response to the new official player from Last.fm. It adds a nice notification icon and notifications with images! It's also more stable, the upgrade to the new Last.fm player seems to have made 1.0 unstable.

I made a deb from the sources this time as I couldn't find a precompiled one; you can download it at my site:

[http://monkeyblog.org/ubuntu/downloads/last-exit_2.0-1_i386.deb](http://monkeyblog.org/ubuntu/downloads/last-exit_2.0-1_i386.deb)

I'm not sure what the dependencies are and I don't want to ruin the package with the wrong dependencies, but you definitely need Gstreamer 0.10 stuff and dbus. These are the dependencies for 1.0, you can add them yourself if you like:

libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), libfontconfig1 (>= 2.3.0), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>= 2.10.0), libgstreamer0.10-0 (>= 0.10.6), libgtk2.0-0 (>= 2.8.0), liborbit2 (>= 1:2.10.0), libpango1.0-0 (>= 1.12.2), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.24), libxrandr2, libxrender1, zlib1g (>= 1:1.2.1), mono-jit (>= 1.0), libgconf2.0-cil (>= 2.7.90), libglade2.0-cil (>= 2.7.90), libglib2.0-cil (>= 2.7.90), libgnome2.0-cil (>= 2.7.90), libgtk2.0-cil (>= 2.7.90), mono-classlib-1.0 (>= 1.0), gconf2 (>= 2.12.1-4ubuntu1)

---

### Post by mostwanted on 2006-07-10
*bump*

---

### Post by croak77 on 2006-07-10
Thanks for the heads up.

---

### Post by Brunellus on 2006-07-10
w00t.  that's getting tested as soon as I get home.

---

### Post by codypumper on 2006-07-10
Trying it right now...

---

### Post by byen on 2006-07-10
NICE! Thanks for the Heads up buddy!

---

### Post by idn on 2006-07-10
Thanks for this!

---

### Post by Mathias-K on 2006-07-10
Nice :)

---

### Post by nosami on 2006-07-10
The deb works great. Good timing too as the official last.fm player has been rather flaky lately!

---

### Post by zenwhen on 2006-07-10
This is really nice. Deb works great!

---

### Post by Brunellus on 2006-07-10
the .deb is awesome, and runs better than the proper last.fm player.  I am impressed.

Thanks very much for this.  whom do we contact to put this into the universe repo?

---

### Post by newagelink on 2006-07-14
> **mostwanted said:**
> And here is a link to a nice Dapper deb:

[http://burtonini.com/debian/dapper/last-exit_1.0-1_i386.deb](http://burtonini.com/debian/dapper/last-exit_1.0-1_i386.deb)I'm getting no sound from this program ...?

---

### Post by GarethMB on 2006-07-14
That site is ace. All dev's should be like that guy.

---

### Post by newagelink on 2006-07-30
How do you uninstall it? I installed it, it doesn't work, and Last.fm Player is fine for me for now ... Whenever I click a station link from the last.fm website, it opens it in this Last-exit program, which doesn't work.

I go to Applications > Add/Remove... and it doesn't seem to be listed there!

How do I remove Last-exit from my computer ...?

---

### Post by Polygon on 2006-07-30
if you used a .deb it should be in synaptic manager, just search for last-exit and it should be there, and just right click > remove

if you used the .tar.gz or whatever, just simply remove the folder

---

### Post by newagelink on 2006-07-30
Thanks; the Synaptic Package Manager thing worked ... That was really easy!

... but now lastfm://artists/873,1000009,831,5477,1014421,1000123,4468,1000127,4061,4209,1005754,1001419,1015111,1000024,1001646,979,976,1000062,1274 isn't opening in anything, which makes me think I need to configure Firefox (v1.5.0.5) to open the protocol with Last.fm Player ... any ideas? (Sorry, I suppose this is getting off-topic.)

edit: nevermind. went into About:Config and fixed it in Firefox. Wish last-exit would've actually worked!

---

### Post by mostwanted on 2006-08-02
Version 2.0.1 is now out, check first post for deb.

---

### Post by Kayne on 2006-08-02
Great app.

I never really expected much from last.fm and its system but now I listen to more and more unknown songs that actually meet my taste.

---

### Post by Mathias-K on 2006-08-02
> **mostwanted said:**
> Version 2.0.1 is now out, check first post for deb.

Thanks for the heads up and for the deb file. I've got two questions, the first being what justifies the jump from 1.0 to 2.0.1? To me it seems to be like a 1.1? The app is GNOMEish in the extreme with no "preferences", that would be a start for a whole new release :)

Also, when I installed the 1.0 deb, i got an entry in the "Applications -> Sound and Video" menu. With the new deb, I get nothing. I tried removing and reinstalling the program, but the problem seems to remain. Am i doing something wrong?

---

### Post by mostwanted on 2006-08-02
> **Mathias-K said:**
> Thanks for the heads up and for the deb file. I've got two questions, the first being what justifies the jump from 1.0 to 2.0.1? To me it seems to be like a 1.1? The app is GNOMEish in the extreme with no "preferences", that would be a start for a whole new release :)

Also, when I installed the 1.0 deb, i got an entry in the "Applications -> Sound and Video" menu. With the new deb, I get nothing. I tried removing and reinstalling the program, but the problem seems to remain. Am i doing something wrong?

I wouldn't know =/

Anyway, the notification icon is enough to justify it for me. That way I can hide the app so it doesn't sit in my task bar. It's also more stable as mentioned before and I think it supports some of the new stuff that Last.fm 2 comes with.

You could always try compiling yourself, that's one sure way to get most depencies right at least.

---

### Post by UbuWu on 2006-08-02
Last-exit 2.0 is now in the Edgy universe repo's!

---

### Post by Mathias-K on 2006-08-03
> **mostwanted said:**
> You could always try compiling yourself, that's one sure way to get most depencies right at least.

GDebi seems to think that all dependencies are satisfied.. Hm, I'll just make a custom launcher for my panel, the icon gets really ugly at 50px anyway.

---

### Post by Mathias-K on 2006-08-03
> **UbuWu said:**
> Last-exit 2.0 is now in the Edgy universe repo's!

Thanks for the heads up. It's really nice to have it supported platform wide :)

---

### Post by mostwanted on 2006-08-03
Hm, I feel compelled to say that the official Last.fm player is out in version 1 for Linux now:

[http://www.last.fm/tools/downloads/?showplatform=Linux](http://www.last.fm/tools/downloads/?showplatform=Linux)

It has more features than Last-exit, but it uses Qt instead so it doesn't integrate with your theme. It doesn't have nice notifications too and I've found some bugs already =/

---

### Post by UbuWu on 2006-08-04
> **mostwanted said:**
> Hm, I feel compelled to say that the official Last.fm player is out in version 1 for Linux now:


And that one is in the edgy repo's as well now!

---

### Post by mustang on 2006-08-04
That is the coolest website EVER haha

---

### Post by Mathias-K on 2006-08-04
Both v1 and v2 of Last-Exit seem flawed to me. Am I the only one only getting a song half the time I ask the program to start playing my neighbour radio? :(

---

### Post by newagelink on 2006-08-06
> **Mathias-K said:**
> Both v1 and v2 of Last-Exit seem flawed to me. Am I the only one only getting a song half the time I ask the program to start playing my neighbour radio? :(It never worked for me, either, which is why I've been using /home/daniel/Programs/Last.fm-1.1.4/player ... but if it's in the repositories (that's what Applications > Add/Remove ... uses, correct?), I might give it another try next month ...

---

### Post by Mathias-K on 2006-08-06
> **newagelink said:**
> It never worked for me, either, which is why I've been using /home/daniel/Programs/Last.fm-1.1.4/player ... but if it's in the repositories (that's what Applications > Add/Remove ... uses, correct?), I might give it another try next month ...

It seems to have started working for me, lately. That's nice, but the program is still having slowdowns sometimes..

---

### Post by arsolto on 2006-08-15
Hello, [mostwanted](http://www.ubuntuforums.org/member.php?u=11323), I am thankful to it for having if dedicated to put the addresses for download of the Last-Exit, as well as related the basic dependences for the execution of player. 

I adopted the installation method below and everything occurred well:

1. I installed the package [ ** last-exit_1.0-1_i386.deb ** ]( http://burtonini.com/debian/dapper/last-exit_1.0-1_i386.deb) for the Gdebi. 

2. Later I installed the package [ ** last-exit_2.0-1_i386.deb ** ]( http://monkeyblog.org/ubuntu/downloads/last-exit_2.0-1_i386.deb) for the Gdebi. 

At last, safe Last-Exit gnomo-sapiens.

---

