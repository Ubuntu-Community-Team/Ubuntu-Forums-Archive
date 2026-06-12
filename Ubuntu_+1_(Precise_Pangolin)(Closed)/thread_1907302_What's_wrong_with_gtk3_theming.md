---
title: "What's wrong with gtk3 theming?"
date: 2012-01-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tista on 2012-01-11
Guys,

I've updated my PP today, then gtk3 theming seemed to be broken especially "GtkMenubar" and some panels which're using menu, menuitem, menubar theming... X(

[IMG]http://oi42.tinypic.com/10h7qbn.jpg[/IMG]

Please see my screenshot showed nautilus's menubar... Yeah in "Green Area" seems normal along with my theming, but, in "Red Area", seems to be forced "Dark Foreground" instead of "Light Foreground" what I've defined...

Does anybody know the solution and/or evil ?!

Cheers,
Tista

P.S - I've been using Ricotz's PPA (testing stage) and Gnome3 PPA, and Yesterday (before updating) I could confirm that issue didn't appear... I've read some git diffs, so gtk+ seemed to be rapidly updated in many stuff, but unfortunately I didn't have any clue to solve this issue... Help!!

---

### Post by Harry33 on 2012-01-11
Hi Tista,

The bug is in the git version of the GTK+3 from the Ricotz Testing PPA.
It has been there from yesterday and it persists.
The last working git version is git20110108.69a52957.
That is what I use.

You can also see problems with Nautilus (the background color when selecting any icon).

---

### Post by paul_in_london on 2012-01-11
> **tista said:**
> Guys,

I've updated my PP today, then gtk3 theming seemed to be broken especially "GtkMenubar" and some panels which're using menu, menuitem, menubar theming... X(

[IMG]http://oi42.tinypic.com/10h7qbn.jpg[/IMG]

Please see my screenshot showed nautilus's menubar... Yeah in "Green Area" seems normal along with my theming, but, in "Red Area", seems to be forced "Dark Foreground" instead of "Light Foreground" what I've defined...

Does anybody know the solution and/or evil ?!

Cheers,
Tista

P.S - I've been using Ricotz's PPA (testing stage) and Gnome3 PPA, and Yesterday (before updating) I could confirm that issue didn't appear... I've read some git diffs, so gtk+ seemed to be rapidly updated in many stuff, but unfortunately I didn't have any clue to solve this issue... Help!!

Hi tista,

Yes, I'm seeing this sort of thing with gnome-terminal (which now only lets me paste via middle mouse click). I'm using the ricotz testing ppa, but I disabled the gnome3-team ppa a while back.

Cheers,

Paul

---

### Post by Harry33 on 2012-01-11
The Ricotz Testing PPA is going through a number of updates continuously.
I believe this will be fixed soon.

---

### Post by paul_in_london on 2012-01-11
> **Harry33 said:**
> The Ricotz Testing PPA is going through a number of updates continuously.
I believe this will be fixed soon.

Yes, I assumed it would Harry. It's not a big problem. :)

---

### Post by tista on 2012-01-11
Hi guys,

Good to know guys Harry and Paul. ;)
OK... I also hope this minor issue would be fixed in near future...

---

### Post by jbicha on 2012-01-12
Yes, the Ricotz Testing PPA includes several basically nightly builds which have a higher chance of being broken. You're a bit safer if you stick with just the GNOME3 PPA which has a bit more testing.

---

### Post by Harry33 on 2012-01-12
Yes it is because there is no GTK+3 version in the Gnome3 PPA.
And this is a GTK+3 bug.
Not even todays update of GTK+3 git version in the Testing PPA did help.

Nautilus fails to show selected files or directories.
On desktop I can see the background of the selected items is white.
And because the background in the Nautilus window is also white, the selection cannot be seen.

---

### Post by Harry33 on 2012-01-14
This issue is solved now.
The Ricotz Gnome-shell Testing PPA has new versions of GTK+3 (git 20120113) and also gnome-themes-standard (git 20120114).
These work well.

---

### Post by zika on 2012-01-14
> **Harry33 said:**
> This issue is solved now.
The Ricotz Gnome-shell Testing PPA has new versions of GTK+3 (git 20120113) and also gnome-themes-standard (git 20120114).
These work well.Hmmm, not yet... ;)

---

### Post by Harry33 on 2012-01-14
> **zika said:**
> Hmmm, not yet... ;)

Here they work OK. Nautilus and desktop are just fine now.
Could you specify, what is not working.

---

### Post by zika on 2012-01-14
> **Harry33 said:**
> Here they work OK. Nautilus and desktop are just fine now.
Could you specify, what is not working.I will once I get back to that environment... Working (now) in other... Sorry...
I knew You could be impatient so I've checked. In Ambiance problem with darkness persists.3I do not even rember when I did set Ambiance... In default theme A*... (did not remember the name) all is OK...
Adwaita is the name... ;)
In LighDM login window there is also problem with no highlight in menu... I did not try to change theme there...

---

### Post by Harry33 on 2012-01-15
> **zika said:**
> I will once I get back to that environment... Working (now) in other... Sorry...
I knew You could be impatient so I've checked. In Ambiance problem with darkness persists.3I do not even rember when I did set Ambiance... In default theme A*... (did not remember the name) all is OK...
Adwaita is the name... ;)
In LighDM login window there is also problem with no highlight in menu... I did not try to change theme there...

Right, I am using Adwaita theme. That surely works fine.

---

### Post by gumshore on 2012-01-29
Sorry to bump this thread, but this is like the only place I have seen this issue brought up lol. I have this issue using the same PPAs in oneiric, so I assume this is a bug. Has it been reported on Launchpad or GNOME Bugzilla yet? If so, can I get a link to it?

---

### Post by jbicha on 2012-01-29
You're trying to use a Precise PPA on Oneiric? Why? and which PPA in particular are you using?

The theme issue is fixed in gnome-themes-standard (Adwaita) and light-themes (Ambiance) in Precise but it's probably less hassle to just run Precise than try to mix bits and pieces of Oneiric and Precise.

---

### Post by gumshore on 2012-01-29
> **jbicha said:**
> You're trying to use a Precise PPA on Oneiric? Why? and which PPA in particular are you using?

The theme issue is fixed in gnome-themes-standard (Adwaita) and light-themes (Ambiance) in Precise but it's probably less hassle to just run Precise than try to mix bits and pieces of Oneiric and Precise.
To be honest, I don't know. I always like to use the newest thing even if it don't work right. Livin on the edge, you know. However, I've been using experimental packages for as long as I can remember, and I have had very few issues. 

Anyway, on topic, I don't use Precise packages in oneiric. The PPAs I was referring to are [https://launchpad.net/~gnome3-team/+archive/gnome3?field.series_filter=oneiric]("https://launchpad.net/%7Egnome3-team/+archive/gnome3?field.series_filter=oneiric") and [https://launchpad.net/~ricotz/+archive/testing?field.series_filter=oneiric]("https://launchpad.net/%7Ericotz/+archive/testing?field.series_filter=oneiric")

Bug wise, since I assume the GTK3 version is also compiled against Precise, the issue exists there as well. If it does, that's a bug in my opinion.

Oh, and for what it might be worth, I usually use the light themes evolved ppa.

EDIT: Just to clarify, I'm talking about gtk3 itself, not gtk3 themes.

---

### Post by snkiz on 2012-01-29
I'm not using any gtk3 ppa's. Upadated last night and I have similar issues with my themes. I haven't checked out light-themes lately, but I don't see why it matters it appears to be a gtk issue not a theme issue.

---

### Post by jbicha on 2012-01-29
gumshore, I'm not really using Oneiric but it looks like Ricotz' testing PPA for Oneiric has the latest light-themes which was adapted for GTK 3.3.8. I'm guessing you have the same problem we had in this forum thread, except in reverse. Try installing light-themes 0.1.8.25 and see if that fixes it for you.

---

### Post by gumshore on 2012-01-29
> **snkiz said:**
> I'm not using any gtk3 ppa's. Upadated last night and I have similar issues with my themes. I haven't checked out light-themes lately, but I don't see why it matters it appears to be a gtk issue not a theme issue.
checked out as in looked at or compiled from source?

---

### Post by gumshore on 2012-01-29
> **jbicha said:**
> gumshore, I'm not really using Oneiric but it looks like Ricotz' testing PPA for Oneiric has the latest light-themes which was adapted for GTK 3.3.8. I'm guessing you have the same problem we had in this forum thread, except in reverse. Try installing light-themes 0.1.8.25 and see if that fixes it for you.
Thanks. I will look into that. I, however, am still confused as to how this all started. Is it an issue with gtk3 or was it an issue with light-themes?

EDIT: Crap. Sorry for double-posting

---

### Post by jbicha on 2012-01-29
Never mind my previous comment. Ricotz' testing PPA for Oneiric includes the latest Git snapshot of GTK 3.3. So I wouldn't use it unless you want bleeding edge code.

Ricotz says that GTK 3.3 broke light-themes again but this hasn't been fixed in light-themes yet since the lastest GTK 3.3 has not had a release tarball yet (and therefore isn't in the normal Precise archives yet either). So either ppa-purge ricotz-testing or wait, maybe a week or two.

---

### Post by snkiz on 2012-01-29
> **gumshore said:**
> checked out as in looked at or compiled from source?

As in used light themes, My gtk is all vanilla precise repos. My theme is from gnome-look. That being said when the issue first occurred I noted the same kind of breakage with light themes as mine. Mine has not improved I don't see how changing the theme would matter, its not being parsed properly.

It's still early so I'm not worried yet. but clearly gtk is messed up.

---

### Post by jbicha on 2012-01-29
I wouldn't say GTK is broken; GTK 3.3 is still in development and the GTK developers can change things from one release to the next. The themes you are using don't support the latest GTK 3.3 builds. You're welcome to use Adwaita, Ambiance, or Radiance or wait for your theme developer to update his themes which might not happen until after GTK 3.4 is final.

By the way, except for the accessibility themes, GNOME ships without a theme switcher and with only one theme named Adwaita, which means something like "one and only."

---

### Post by snkiz on 2012-01-29
> **jbicha said:**
> I wouldn't say GTK is broken; GTK 3.3 is still in development and the GTK developers can change things from one release to the next. The themes you are using don't support the latest GTK 3.3 builds. You're welcome to use Adwaita, Ambiance, or Radiance or wait for your theme developer to update his themes which might not happen until after GTK 3.4 is final.

By the way, except for the accessibility themes, GNOME ships without a theme switcher and with only one theme named Adwaita, which means something like "one and only."

I know it isn't, it said 3.2 updated on jan 11. it worked for about a week. But you can't tell me 3.3 isn't suffering issues when one coulor is defined for an element and another appears. I'm not about to rewrite a theme to account for bugs in gtk. I've got no problem waiting it out. I was just pointing out that it isn't just ricotz's ppa. BTW I just checked Ambiance is still messed up, thou not in the same way as my theme anymore... its worse.

---

### Post by VinDSL on 2012-01-29
The problem I've been having, for a week or so, is anything and everything that involves transparency/opacity.  And, that is most things, these days.

Let me give you an extreme example...


Here's what I see when I open a terminal.

[INDENT][IMG]http://vindsl.com/images/opacify1.png[/IMG][/INDENT]



And, this is what I see after correcting it with the *mouseover-alt-scroll-wheel* trick.

[INDENT][IMG]http://vindsl.com/images/opacify2.png[/IMG][/INDENT]


The terminal, pictured in the 2nd screenie, is how it should appear, every time I open it -- no fiddling around envolved!

Everything else does this too, to one degree or another -- drives me crazy when I have multiple apps open!  It's 3D hell!

Oh, well, this too shall pass...  :D

---

### Post by snkiz on 2012-01-29
Ya I get that too. I also made the mistake of turning on transparency for window decorations, now even after attempting to turn it off they still react this way. My conkies are supposed to dynamically resize, that doesn't work anymore. (1.8.1 from natty 1.8.2 is just fubared.) I'm starting to think they don't test anything in unity except default settings, stray from those and its a nightmare.

---

### Post by VinDSL on 2012-01-29
> **gumshore said:**
> I've been using experimental packages for as long as I can remember, and I have had very few issues.
Heh!  You must be a lucky soul!  :)

I have had nothing BUT issues with the alphas, for as long as I can remember.

12.04 has been a snooze, so far.  ZZZZZZZzzzzzzzzzzz...

I can't wait for the 12.10 toolchain to be uploaded! ;)

---

### Post by VinDSL on 2012-01-29
> **snkiz said:**
> Ya I get that too. I also made the mistake of turning on transparency for window decorations, now even after attempting to turn it off they still react this way.
This seems to help...  ;)


[INDENT][IMG]http://vindsl.com/images/gconf-editor-26-jan-2012.png[/IMG][/INDENT]

---

### Post by cariboo on 2012-01-30
> **snkiz said:**
> Ya I get that too. I also made the mistake of turning on transparency for window decorations, now even after attempting to turn it off they still react this way. My conkies are supposed to dynamically resize, that doesn't work anymore. (1.8.1 from natty 1.8.2 is just fubared.) I'm starting to think they don't test anything in unity except default settings, stray from those and its a nightmare.

Who is this **they** you are speaking of? If you want things tested before you use them, join the [QA team]("http://qa.ubuntu.com/") and see if you can get a test suite setup to test whatever its you think should be tested.

---

### Post by gumshore on 2012-01-30
> **cariboo907 said:**
> Who is this **they** you are speaking of? If you want things tested before you use them, join the [QA team]("http://qa.ubuntu.com/") and see if you can get a test suite setup to test whatever its you think should be tested.
That's one of the reasons I always use experimental packages. The only way to test if experimental versions are ready for daily use is to use them daily, report bugs against the software, and test again. Eventually, things work.

---

### Post by snkiz on 2012-01-30
> **cariboo907 said:**
> Who is this **they** you are speaking of? If you want things tested before you use them, join the [QA team]("http://qa.ubuntu.com/") and see if you can get a test suite setup to test whatever its you think should be tested.

No thanks, been there done that. It's no fun talking to a brick wall. My days of bug reporting are done, its not worth the headache if your lucky enough to even get a response.

---

### Post by jbicha on 2012-01-30
Consider yourself lucky. Your complaint just got a response, hopefully without a headache. :-)

---

### Post by VinDSL on 2012-02-05
> **snkiz said:**
> Ya I get that too. I also made the mistake of turning on transparency for window decorations, now even after attempting to turn it off they still react this way.[...]
Well, I don't know what changed, but... everything is back to normal (for now).

I was in a whimsical mood, this afternoon, and installed the latest Linux 3.3 "999" daily mainline kernel.

3.3 dumped all my DKMS info then refused to build the nVidia modules.  Then, for the hell of it, I did an omnibus update.

After restarting Ubu, Synaptic refused to run, because Linux 3.3 was improperly installed, and it couldn't find the location of something-or-another.  So I booted into various Linux 3.2 installs, and fiddled around... blah, blah, blah.

Anyway, I finally purged 3.3 and rebuilt the nVidia modules on all my 3.2 installs.

Now, Unity (under Linux 3.2.0.14) looks just fine!  Matter of fact, I'm thinking about turning the transparency back on in Metacity.

Like I said, I don't know what fixed it, although I did see some Unity downloads in the omnibus update... maybe they fixed it.

**Edit**

Turned the transparency back on, in Metacity (.075 opacity) and it's working great!  ;)

---

### Post by kansasnoob on 2012-02-05
> **snkiz said:**
> No thanks, been there done that. It's no fun talking to a brick wall. My days of bug reporting are done, its not worth the headache if your lucky enough to even get a response.

Sometimes it takes more finesse than muscle to bring down a wall :)

I never give up :guitar:

---

