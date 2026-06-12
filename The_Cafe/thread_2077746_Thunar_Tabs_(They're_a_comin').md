---
title: "Thunar Tabs (They're a comin')"
date: 2012-10-29
forum: The Cafe
---

### Post by Toz on 2012-10-29
See: [http://forum.xfce.org/viewtopic.php?id=7552]("http://forum.xfce.org/viewtopic.php?id=7552") 

and: [https://plus.google.com/u/0/115410781201569373644/posts/9HwQPbVBUnt]("https://plus.google.com/u/0/115410781201569373644/posts/9HwQPbVBUnt").

---

### Post by Elfy on 2012-10-29
Nice.

The double partition bug is on it's way to a fix as well - so that's 2 plus's from me :)

---

### Post by neu5eeCh on 2012-10-29
That's cool -- a welcome and needed feature. If you're following this, let us know when the feature becomes available and how to install it.

---

### Post by johnnybgoode83 on 2012-10-29
What about bookmarks/favourites?  That's what I want.

---

### Post by mamamia88 on 2012-10-29
> **johnnybgoode83 said:**
> What about bookmarks/favourites?  That's what I want.

you already have bookmarks just drag your folder into sidebar

---

### Post by pqwoerituytrueiwoq on 2012-10-29
Tabs and double partition fix, i can't wait for that, sinuously anyone got a source download and compile instructions for making a deb out of it

---

### Post by mikodo on 2012-10-29
"Double partition fix"

Is [This]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375") it?

---

### Post by pqwoerituytrueiwoq on 2012-10-29
sounds like it, in my 12.10 install it is not as bad as it was in the beta
it shows up on my desktop and hitting f5 removes the duplicates usually (not sure if it works if they are mounted)

---

### Post by Toz on 2012-10-29
> **VTPoet said:**
> That's cool -- a welcome and needed feature. If you're following this, let us know when the feature becomes available and how to install it.

It's available in git now - if you like building from git. See the git repository at: [http://git.xfce.org/]("http://git.xfce.org/") and instructions at: [http://docs.xfce.org/xfce/building]("http://docs.xfce.org/xfce/building").

Obligatory screeny: [[img]http://en.zimagez.com/miniature/s654.png[/img]](http://en.zimagez.com/zimage/s654.php)

Otherwise, we'll have to wait until its added to the repositories or someone creates a PPA for it.

---

### Post by Elfy on 2012-10-30
> **mikodo said:**
> "Double partition fix"

Is [This]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/1039375") it?

Yes, fix will be in proposed apparently, if you want to you can also do 

[http://askubuntu.com/questions/207296/after-upgrade-to-xubuntu-12-10-i-have-2-mount-points-for-each-partition](http://askubuntu.com/questions/207296/after-upgrade-to-xubuntu-12-10-i-have-2-mount-points-for-each-partition)

---

### Post by kow777 on 2012-10-30
XFCE is looking more and more enticing...

---

### Post by johnnybgoode83 on 2012-10-30
> **mamamia88 said:**
> you already have bookmarks just drag your folder into sidebar

It doesn't stay there when I log out and in again.

---

### Post by mamamia88 on 2012-10-30
> **johnnybgoode83 said:**
> It doesn't stay there when I log out and in again.
weird i never bothered to check that

---

### Post by neu5eeCh on 2012-10-30
> **Toz said:**
> It's available in git now - if you like building from git. See the git repository at: [http://git.xfce.org/](http://git.xfce.org/) and instructions at: [http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building).

Otherwise, we'll have to wait until its added to the repositories or someone creates a PPA for it.

Thanks Toz. I've never built from git but how hard can it be? What could _possibly_ go wrong? ;) It's time I learned.

**Edit: **Toz, what's the app called? I'm looking under Thunar plugins, but not finding it.

---

### Post by pqwoerituytrueiwoq on 2012-10-30
> **Toz said:**
> It's available in git now - if you like building from git. See the git repository at: [http://git.xfce.org/](http://git.xfce.org/) and instructions at: [http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building).

Obligatory screeny: [[IMG]http://en.zimagez.com/miniature/s654.png[/IMG]]("http://en.zimagez.com/zimage/s654.php")

Otherwise, we'll have to wait until its added to the repositories or someone creates a PPA for it.
does clicking middle clicking (button 2) on a folder open it in tab
does [Ctrll]+[T] open a tab?
EDIT:
AWESOME A EDITABLE LOCATION BAR!!!
someone said it will be in proposed soon, how soon is soon?

so i do this:
```
git clone git://git.xfce.org/xfce/thunar
export PKG_CONFIG_PATH="/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH"
cd thunar
./configure --prefix=/usr/local --enable-maintainer-mode
```
where is configure ?

---

### Post by Erik1984 on 2012-10-30
> **kow777 said:**
> XFCE is looking more and more enticing...

Lets say they don't make it any easier to pick a DE :P

---

### Post by Toz on 2012-10-31
> **pqwoerituytrueiwoq said:**
> does clicking middle clicking (button 2) on a folder open it in tab
does [Ctrll]+[T] open a tab?
EDIT:
AWESOME A EDITABLE LOCATION BAR!!!
someone said it will be in proposed soon, how soon is soon?

so i do this:
```
git clone git://git.xfce.org/xfce/thunar
export PKG_CONFIG_PATH="/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH"
cd thunar
./configure --prefix=/usr/local --enable-maintainer-mode
```
where is configure ?

**First, an apology**. I just noticed that the screenshot above is actually showing pcmanfm, not the new thunar (it has been a very, very long week). I will try to post back an screenshot of thunar later when I have access to the VM.

As for building, I've found that I need to build all of Xfce (because of dependencies) and not just one component.

---

### Post by Toz on 2012-10-31
Okay. Here is the correct image (thunar with tabs built from git):

[[img]http://en.zimagez.com/miniature/s655.png[/img]](http://en.zimagez.com/zimage/s655.php)

> **pqwoerituytrueiwoq said:**
> does clicking middle clicking (button 2) on a folder open it in tab
No.
> does [Ctrll]+[T] open a tab?
Yes it does, it creates a new tab and displays the current folder.

---

### Post by pqwoerituytrueiwoq on 2012-10-31
> **Toz said:**
> Okay. Here is the correct image (thunar with tabs built from git):

[[IMG]http://en.zimagez.com/miniature/s655.png[/IMG]]("http://en.zimagez.com/zimage/s655.php")


how did you get a editable address bar in the other one?
[s]if that is a 64bit system could you share the compiled thunar with me (preferably with editable address bar)
or give me compile instructions (including apt-get install [depends for compiling])[/s]
could you upload the thunar executable you compiled? (it should fit in the attachment size limit here in a .tar.gz)
*hopes for a 64bit file*

edit:
installed [pcmanfm]("apt:pcmanfm") and i am happy

---

### Post by Toz on 2012-10-31
> **pqwoerituytrueiwoq said:**
> how did you get a editable address bar in the other one?
You can do that with the current version of thunar (View -> Location Selector -> Toolbar Style)
> [s]if that is a 64bit system could you share the compiled thunar with me (preferably with editable address bar)
or give me compile instructions (including apt-get install [depends for compiling])[/s]
could you upload the thunar executable you compiled? (it should fit in the attachment size limit here in a .tar.gz)
*hopes for a 64bit file*
I don't think this will work. The new thunar depends on at least a new version of exo that needs to be built from source as well. 


> edit:
installed [pcmanfm]("apt:pcmanfm") and i am happy
Yes, pcmanfm is a good program.

---

### Post by pqwoerituytrueiwoq on 2012-10-31
> **Toz said:**
> You can do that with the current version of thunar (View -> Location Selector -> Toolbar Style)
thanks, that always annoyed me
that version of xeo depend on anything special?

---

### Post by BrokenKingpin on 2012-10-31
awesome.

---

### Post by Toz on 2012-10-31
> **pqwoerituytrueiwoq said:**
> thanks, that always annoyed me
that version of xeo depend on anything special?
I'm not sure what the new exo libraries are dependent on - I got tired of trying to trace back the dependencies and decided to just build all of Xfce (plus the few plugins that I use) instead.

---

### Post by pqwoerituytrueiwoq on 2012-11-01
know a way to have PCManFM open a new window instead of a tab (in another workspace) if there is not a PCManFM window on the current workspace?

---

### Post by Toz on 2012-11-01
> **pqwoerituytrueiwoq said:**
> know a way to have PCManFM open a new window instead of a tab (in another workspace) if there is not a PCManFM window on the current workspace?

If I understand correctly...

If I have pcmanfm open on another workspace, and click the icon to start a new instance of pcmanfm on the current workspace, I get a new instance of the app on my current workspace. This is the standard behaviour for me.

---

### Post by Copper Bezel on 2012-11-01
No experience with pcmanfm, but gedit and Chrome always opened new tabs for me instead, and all I had to do to fix this was to add --new-window to the exec lines of their .desktops.

---

### Post by pqwoerituytrueiwoq on 2012-11-01
> **Toz said:**
> If I understand correctly...

If I have pcmanfm open on another workspace, and click the icon to start a new instance of pcmanfm on the current workspace, I get a new instance of the app on my current workspace. This is the standard behaviour for me.
maybe cause i am using compiz - [http://i.imgur.com/rJBp6.png](http://i.imgur.com/rJBp6.png)
[Recording]("http://yourupload.com/embed/88417eb3e6ef7f891c2e6ad0c3a2612b&width=1920&height=1080") 16.2MB mp4 video in 1080p
if you dont want to play it is flash pause it and use this
[http://ubuntuforums.org/showthread.php?t=2078303](http://ubuntuforums.org/showthread.php?t=2078303)

edit:
on my laptop (no compiz) it switches to the workspace that pcmanfm is on

---

### Post by samalex on 2012-11-02
Nice to hear.  Honestly though Thunar is the one part of XFCE I have the most problems and crashes with, but it is nice none the less and tabbed browsing will be a pleasant feature to have.

---

### Post by bmeakings on 2012-11-04
This is excellent news. The lack of tabs was a deal breaker when I moved to Xfce and after trying other FM's I held on to Nautilus and am currently using Nemo.

I'll definitely be looking forward to when it's released.

---

### Post by Toz on 2012-11-05
Looks like the PPA is ready: [http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html]("http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html").

---

### Post by pqwoerituytrueiwoq on 2012-11-05
> **Toz said:**
> Looks like the PPA is ready: [http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html](http://www.webupd8.org/2012/11/install-thunar-with-tabs-support-in.html).
WOOT, thanks for posting

---

### Post by mips on 2012-11-06
I would actually prefer a dual pane to tabs but that's just me.

---

### Post by pqwoerituytrueiwoq on 2012-11-09
> **mips said:**
> I would actually prefer a dual pane to tabs but that's just me.
i am just happy to have, but that would be nice

anyway middle clicking a folder does open in tab, it is just a double click
edit -> preferences -> behavior

---

### Post by malspa on 2012-11-09
> **mips said:**
> I would actually prefer a dual pane to tabs but that's just me.

Me, too. The lack of extra panes is one of the main reasons I don't use Thunar.

---

### Post by mamamia88 on 2012-12-03
Not to revive a dead thread but recent update brought this to arch sweet

---

