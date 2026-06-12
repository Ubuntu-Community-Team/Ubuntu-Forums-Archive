---
title: "No Compiz Panic!!"
date: 2012-11-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2012-11-23
I'm almost in tears ! :) Just amazing work. Compiz now works on this one machine so smoothly where it was really sluggish before and when enable cube/rotate... !! No Panic or crash!

Way things look so far, Raring has already superseded Precise and Quantal. My hat is off to Mark and the Unity team and Sam S.

---

### Post by fjgaude on 2012-11-23
Well, for me and my Intel graphics Compiz uses over 20% of my quad-core CPU, not good. OTOH all seem to be very quick and we can be sure the CPU usage will be fixed. After all, it's Intel. <smile>

---

### Post by ventrical on 2012-11-23
Very low stats here for a single core.

---

### Post by ventrical on 2012-11-23
Enabling wobbly windows and 3d windows just about does it in :) Some amazing affects there. Looks like still some work ahead...

---

### Post by fjgaude on 2012-11-24
After today's update compiz is using about 1% of CPU. So the fix came quickly. Speed, quickness is not an issue, very fast code.

---

### Post by ventrical on 2012-11-24
I aquired an old Intel 64bit 554 with HT. I'm going to slip that in and see what happens.

---

### Post by ventrical on 2012-11-24
I got this when enable/disable 3D windows.

edit: argghh man .. youtube is being really fussy now with new cameras. back to my Nokia fake Blueberry! :)

[http://www.youtube.com/watch?v=-jKLr-3Hrn8&feature=youtu.be](http://www.youtube.com/watch?v=-jKLr-3Hrn8&feature=youtu.be)

---

### Post by jerrylamos on 2012-11-24
> **fjgaude said:**
> Well, for me and my Intel graphics Compiz uses over 20% of my quad-core CPU, not good. OTOH all seem to be very quick and we can be sure the CPU usage will be fixed. After all, it's Intel. <smile>

Dumb question - can you get 400% utilization on a quad-core?

Or does 20% mean 20% on each one of the cores at once?

This is a dual core with Compiz rattling about 8% +/- is that 8% of one processor or 8% of both - on 
Intel Corporation Atom Processor 1.6 gHz D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
No clue what intel graphics that is.  

Of course my Android tablet's Nvidia Tegra 1 gHz processor/graphics runs rings around it, I don't know if that's no compiz/unity in Android or a much better processor/graphics integration.

Both are dual core 1 Gb memory...Oh, all I've got up is Firefox entering this post and top on a terminal window.

---

### Post by cariboo on 2012-11-24
> **jerrylamos said:**
> Dumb question - can you get 400% utilization on a quad-core?

Or does 20% mean 20% on each one of the cores at once?

This is a dual core with Compiz rattling about 8% +/- is that 8% of one processor or 8% of both - on 
Intel Corporation Atom Processor 1.6 gHz D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
No clue what intel graphics that is.  

Of course my Android tablet's Nvidia Tegra 1 gHz processor/graphics runs rings around it, I don't know if that's no compiz/unity in Android or a much better processor/graphics integration.

Both are dual core 1 Gb memory...Oh, all I've got up is Firefox entering this post and top on a terminal window.

That's kind of strange, my netbook has an atom 270, single core with hyperthreading, so it shows two cores, and a 945 graphics chip set, compiz at idle shows .3 - 1.3% cpu usage. I'm just setting Ubuntu up on it, as I really don't see any speed advantage with Xubuntu.

When comparing your tablet to your netbook, you are comparing apples to oranges. My tablet, Eeepad Transformer Prime runs ice cream sandwich supplied from the manufacturer, if you had just installed Android 4+ from google, that wasn't optimized for the system you would see the same types of perceived problems, you see with your netbook.

It's all wlel and good to check what kind of resources your system is using, but how does it work in day to day usage? Do you find that it generally feels like it's running in molasses, or does it run well enough that you don't really have any complaints, aside from a pre-conceived notion?

---

### Post by fjgaude on 2012-11-25
> **jerrylamos said:**
> Dumb question - can you get 400% utilization on a quad-core?

Or does 20% mean 20% on each one of the cores at once?

This is a dual core with Compiz rattling about 8% +/- is that 8% of one processor or 8% of both - on 
Intel Corporation Atom Processor 1.6 gHz D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
No clue what intel graphics that is.  

Of course my Android tablet's Nvidia Tegra 1 gHz processor/graphics runs rings around it, I don't know if that's no compiz/unity in Android or a much better processor/graphics integration.

Both are dual core 1 Gb memory...Oh, all I've got up is Firefox entering this post and top on a terminal window.

For a quad-core when 20% is stated it points to each core at 20%. It could mean at one core is at 100% when 25% is stated. Anyway, 13.04 is running nicely now that that issue with compiz is fixed on my Intel HD3000 graphics box.

---

### Post by jpeddicord on 2012-11-25
> **jerrylamos said:**
> Dumb question - can you get 400% utilization on a quad-core?

Or does 20% mean 20% on each one of the cores at once?

The short answer is yes, but it depends on the utility you're looking at.

Most utilities will show you total load in units of cores, so 100% (or 1.00 load) means one core is fully utilized. On a quad-core machine, you can see up to 400%, and on a 16-core, 1600%, etc.

20% utilization typically means 20% of one core.

However, if you're reading the graphs in GNOME's system monitor (or htop) that break things down by core, those will show you the utilization for each core separately, and only go up to 100%.

For a rough estimate of load, you can add these numbers up and divide by 100, but the load averages from `uptime` and `w` will take a little bit of time to show those numbers since they're sampled over a longer span of time.

---

### Post by screaminj3sus on 2012-12-01
The unity dash is still incredibly sluggish on my older laptop (intel ironlake graphics) :( The compiz effects like scale, wall, cube etc... have always been smooth for me, its just the dash thats terrible.

On my newer ivybridge laptop compiz/unity runs totally smooth on both 12.10 and 13.04 though.

---

### Post by ventrical on 2012-12-01
I just wanted to make a note that this performance observation with Compiz seems to be a day by day  activity that changes when major updates are aligned on the pipes. It is hard to determine why it will run so fast on one day and then crawl at a snails pace on another.

 Certainly it is easy to determine why compiz  runs slower on older machines and simply, the hardware can't handle the Unity &Compiz co-existing together. Any graphics hardware 256MB or under is going to have a hard time competing.

---

### Post by VinDSL on 2012-12-01
> **ventrical said:**
> I'm almost in tears ! :) Just amazing work. 

Compiz now works on this one machine so smoothly where it was really sluggish before and when enable cube/rotate... !! 

No Panic or crash!
Soooooo...

You're saying, it's safe to play around with Compiz again?!?!?

Or, are you saying, you've figured out how to tip-toe through the minefield without triggering any explosions?

I haven't *tried* invoking the "cube" in (like) a year.

I clicked something-or-another in Compiz, a month or so ago, to see what it would do, and spent the rest of the day trying to get my 3D desktop back. LoL!  :D

---

### Post by ventrical on 2012-12-01
> **VinDSL said:**
> Soooooo...

You're saying, it's safe to play around with Compiz again?!?!?

Or, are you saying, you've figured out how to tip-toe through the minefield without triggering any explosions?

I haven't *tried* invoking the "cube" in (like) a year.

I clicked something-or-another in Compiz, a month or so ago, to see what it would do, and spent the rest of the day trying to get my 3D desktop back. LoL!  :D

lol :) 

Whats that olde saying .. umm .. "stuff rolls downhill".. :) Well.. we both know that 'stuff' happens!! :) in the repos and no matter how hard they smoketest the next batch of updates and kernels there will always be the chance that  a compiz zinger will get through and foobar our desktops .. :)  so .. we have to tip toe around a bit . However .. even doing this does not guarantee that we won't step in a pile of it now and again :)

lol

---

### Post by ventrical on 2012-12-01
> **VinDSL said:**
> Soooooo...

You're saying, it's safe to play around with Compiz again?!?!?

Or, are you saying, you've figured out how to tip-toe through the minefield without triggering any explosions?

I haven't *tried* invoking the "cube" in (like) a year.

I clicked something-or-another in Compiz, a month or so ago, to see what it would do, and spent the rest of the day trying to get my 3D desktop back. LoL!  :D


3D windows will make compiz do this weird hack when you try to rotate cube. even in quantal.. it's in rough shape.

At least on iNtel chipset graphics.

Also on ATi ..>effects>  3D windows will break.

---

### Post by VinDSL on 2012-12-01
> **ventrical said:**
> 3D windows will make compiz do this weird hack when you try to rotate cube. even in quantal.. it's in rough shape.

At least on iNtel chipset graphics.

Also on ATi ..>effects>  3D windows will break.
Hrm...

You're sending a mixed message, bro!
[LIST]
[*]Compiz is working smoothly, but...
[*]Compiz is in rough shape, and...
[*]Rotating cube will break 3D windows, "at least on Intel chipset graphics"!
[/LIST]

Let me rephrase the question...

I generally bang out Unity 3D themes at a rate of 1 per-day.  I take screenies, then start all over again.

I've spent 2-days on my most recent theme, which means I like it a lot (and don't want to crash my 3D desktop).

The only reason I'm bothering to ask you about your confusing declarations is, I think this mesmerizing theme would lend itself to a Compiz rotating cube treatment, but... I don't want to crash my desktop, based on your assertion that Compiz is working smoothly now.


**Here is a clean screen...**
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-dec-2012-0(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-dec-2012-0.png")[/INDENT]


**A dirty screen (please note the warning dialog)...**
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-dec-2012-1.png")[/INDENT]


**And, the custom Expo...**
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-dec-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-dec-2012-2.png")[/INDENT]


Question:  Is Compiz really working smoothly now, or not :confused:

It's a simple "yes" or "no" question...  ;)

---

### Post by ventrical on 2012-12-01
> **VinDSL said:**
> Hrm...

You're sending a mixed message, bro!
[LIST]
[*]Compiz is working smoothly, but...
[*]Compiz is in rough shape, and...
[*]Rotating cube will break 3D windows, "at least on Intel chipset graphics"!
[/LIST]

Let me rephrase the question...

I generally bang out Unity 3D themes at a rate of 1 per-day.  I take screenies, then start all over again.

I've spent 2-days on my most recent theme, which means I like it a lot (and don't want to crash my 3D desktop).

The only reason I'm bothering to ask you about your confusing declarations is, I think this mesmerizing theme would lend itself to a Compiz rotating cube treatment, but... I don't want to crash my desktop, based on your assertion that Compiz is working smoothly now.


**Here is a clean screen...**[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-dec-2012-0(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-dec-2012-0.png")[/INDENT]**A dirty screen (please note the warning dialog)...**[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-dec-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-dec-2012-1.png")[/INDENT]**And, the custom Expo...**[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-dec-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-dec-2012-2.png")[/INDENT]You've applied for membership here, on Ubu Forums. I know you wish to place a positive spin on Unity, and pad your "bean" count.  But, please provide a cogent answer.

Question:  Is Compiz really working smoothly now, or not :confused:

It's a simple "yes" or "no" question...


 @VinDSl

 The original title of this thread was 'no compiz panic!'  
 One of our beloved  moderators took it upon themselves to change the topic title to 'Compiz working smoothly'. Now .. please stay with me here for a moment. I do not fault the staff or admins for changing the title because , perhaps my original topic title was obscure.

2. At the initial stage of install the Nov23 daily and installing compiz it WAS working exceptionally well. Let me explain.   I had enabled Cube and Cube Rotate and Wobbly and there was no *stall* or *reset* routine that usually takes place (as which has been happening since Oneiric Ocelot) . Setting a compiz setting in ccsm would crash/reset compiz. On the Nov23/2012 daily  ISO there was this smooth transition , or, no  compiz panic (as I call  the reset).  Since then (along with upgrades and running 3D Windows) there has been deprecations and regressions that I have no control over. So, to answer your question - No!  - Compiz is not working smoothly.

 As for your comment about me padding my "bean count". I don't know what to say. Perhaps I may seem to be an over-enthusiastic troll of some sort.  I do not intend to come across that way.  But I must confess  ... that if it seems like I am eating crow and kissing **** a little more than usual :).. then you are correct.  Yes , I would like to become an Ubuntu member, and I am trying my best, (feel like a cat on a hot tin roof sometimes) .. but I hope it will get better from here on in. :)
 
My apologies (kiss) :) if I have obsfucated the issue or have not clearly presented the clear documentation to my assumptions.

Regards..

Ventrical

---

### Post by ventrical on 2012-12-01
> **VinDSL said:**
> Hrm...

The only reason I'm bothering to ask you about your confusing declarations is, I think this mesmerizing theme would lend itself to a Compiz rotating cube treatment, but... I don't want to crash my desktop, based on your assertion that Compiz is working smoothly now[B] 

@vindsl

   I had put this up back several messages ago. Did you not see it?

[http://ubuntuforums.org/showpost.php?p=12371055&postcount=7](http://ubuntuforums.org/showpost.php?p=12371055&postcount=7)
[/B]

---

### Post by mc4man on 2012-12-01
> **VinDSL said:**
> 
I haven't *tried* invoking the "cube" in (like) a year.

I use rotate here instead of wall & it needs something to rotate, so cube.
Rarely have any issue enabling thru ccsm, certainly nothing a log out/in doesn't resolve.

Way here - 
open ccsm
disable the unity plugin
disable wall, enable rotate/cube
change 2x2 to 1x4 in general options
re-enable the unity plugin

Most times unity comes right back or in a few sec.'s or so. If it 
doesn't after 10 sec's or so, (rare),  I just log out/in & all is well.

(- the one plugin that still consistently  hangs up compiz is disabling the grid plugin which I do separately & many times need a log out/in to finish.

---

### Post by VinDSL on 2012-12-01
> **ventrical said:**
> My apologies (kiss) :)
No, my apologies!  You weren't supposed to see that.

I was so wound up, I had to get off the computer and ride my beach cruiser around the lake for 30 minutes.  When I got back, I redacted those comments.  My bad, not yours!

In MY defense (and this is no kidding) as soon as I left my house, I was buzzed by an unmarked, black helicopter, flying approx. 200 feet AGL.   Plus, there were four jets crisscrossing the sky, laying chemtrails overhead.  Maybe I was part of a PSYOP, or something.  LoL!  :D

Just one of those days, you know?  Sorry...

---

### Post by VinDSL on 2012-12-01
> **mc4man said:**
> I use rotate here instead of wall & it needs something to rotate, so cube.
Rarely have any issue enabling thru ccsm, certainly nothing a log out/in doesn't resolve.

Way here - 
open ccsm
disable the unity plugin
disable wall, enable rotate/cube
change 2x2 to 1x4 in general options
re-enable the unity plugin

Most times unity comes right back or in a few sec.'s or so. If it 
doesn't after 10 sec's or so, (rare),  I just log out/in & all is well.

(- the one plugin that still consistently  hangs up compiz is disabling the grid plugin which I do separately & many times need a log out/in to finish.
Worked!  Thanks!


**The Cube...**
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-1-dec-2012-4(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-1-dec-2012-4.png")[/INDENT]


Now, I need to remember all the little tricks, to make it look good...  :)

---

### Post by VinDSL on 2012-12-02
@ ventrical & mc4man

I'm happy with the rotating cube, so far, but now it's time to start working on the reflection, deformation, caps, and so forth and so on. 

As started earlier, I haven't played with the "cube" in a year or more.

First thing, this morning, I went searching for the "cubeaddon" plugin.  I'm running...

```
vindsl@Zuul:~$ apt-cache policy compiz
compiz:
  Installed: 1:0.9.8.4+bzr3412-0ubuntu1
  Candidate: 1:0.9.8.4+bzr3412-0ubuntu1
```

All I can find are plugins for Compiz  0.9.5.92

Example:  [https://launchpad.net/compiz-cubeaddon-plugin](https://launchpad.net/compiz-cubeaddon-plugin)

What are you guys using?!?!?

Did you downgrade your Compiz package?

Or, are we too far out on the fringe edge of computing for stuff like that?

**EDIT**

Whoa!  N/M

Doing a little research... it's pretty bad when the Compiz maintainers are throwing in the towel.

I *feel* like I'm playing with fire and knives -- tinkering around with these unsupported plugins.

I'm gonna get burned and sliced, if I continue down this path. Heh!

Not to mention, four desktops just doesn't cut it for me.  That's kiddie-stuff, and sphere vs. cube looks like grunt!

Soooo, what's the point, you know?!?!?

Think I'll leave "well enough" alone...  ;)

---

### Post by mc4man on 2012-12-02
> **VinDSL said:**
> @ ventrical & mc4man

I'm happy with the rotating cube, so far, but now it's time to start working on the reflection, deformation, caps, and so forth and so on. 

As started earlier, I haven't played with the "cube" in a year or more.

First thing, this morning, I went searching for the "cubeaddon" plugin.  I'm running...

```
vindsl@Zuul:~$ apt-cache policy compiz
compiz:
  Installed: 1:0.9.8.4+bzr3412-0ubuntu1
  Candidate: 1:0.9.8.4+bzr3412-0ubuntu1
```

All I can find are plugins for Compiz  0.9.5.92

Example:  [https://launchpad.net/compiz-cubeaddon-plugin](https://launchpad.net/compiz-cubeaddon-plugin)

What are you guys using?!?!?

Did you downgrade your Compiz package?

Or, are we too far out on the fringe edge of computing for stuff like that?

Myself just use cube for rotate, specifically 'scroll on desktop' which is not that good with wall.
So haven't paid much attention other than many plugins are no longer provided, ie. you're on your own.

As far as the plugins provided thru  "compiz-plugins" package - they are Not supported atm. One can file a bug on if desired but whether attended to is a matter of time/interest of the few who actually know enough to address.

One current ex. would be the commands plugin. Set commands/bindings tend to disappear after a while. Whether I file on is debatable, have found a semi-workaround for the one main one I use
(it enables scale > pull all windows from a window group from all viewports

Some of the plugins you've mentioned may work if installed, may not. Also the change to dconf from gconf could present some issue with older plugins.

There also is some sort of 'disconnect' between dconf & compiz settings
Changes made thru ccsm usually will then be reflected in dconf but in the absence of ccsm making changes thru dconf is a bit obscure or in some cases not possible??

---

### Post by VinDSL on 2012-12-02
Thanks, mc4man!  I edited the post (above yours).

Heh!  We must have been "two-fingering" (the keyboard) at the same time.  LoL!  :D

Compiz is stable enough to switch back n' forth between the four-sided "cube" and my nine-desktop "wall" without crashing the 3D desktop.  Sooo, I'll use the "cube" for nostalgia, and the "wall" when I need to get some work done.

Having played around with Compiz, last night & today, the trick *seems* to be to disable the Unity plugin, before clicking on things and/or making any changes, and re-enabling it when you're done.  I haven't experienced any explosions doing things this way.

Anyway, thanks for the input!  It's nice to have the "cube" on call again...  ;)

---

### Post by ventrical on 2012-12-02
> **VinDSL said:**
> @ ventrical & mc4man

I'm happy with the rotating cube, so far, but now it's time to start working on the reflection, deformation, caps, and so forth and so on. 

As started earlier, I haven't played with the "cube" in a year or more.

First thing, this morning, I went searching for the "cubeaddon" plugin.  I'm running...

```
vindsl@Zuul:~$ apt-cache policy compiz
compiz:
  Installed: 1:0.9.8.4+bzr3412-0ubuntu1
  Candidate: 1:0.9.8.4+bzr3412-0ubuntu1
```All I can find are plugins for Compiz  0.9.5.92

Example:  [https://launchpad.net/compiz-cubeaddon-plugin](https://launchpad.net/compiz-cubeaddon-plugin)

What are you guys using?!?!?

Did you downgrade your Compiz package?

Or, are we too far out on the fringe edge of computing for stuff like that?

**EDIT**

Whoa!  N/M

Doing a little research... it's pretty bad when the Compiz maintainers are throwing in the towel.

I *feel* like I'm playing with fire and knives -- tinkering around with these unsupported plugins.

I'm gonna get burned and sliced, if I continue down this path. Heh!

Not to mention, four desktops just doesn't cut it for me.  That's kiddie-stuff, and sphere vs. cube looks like grunt!

Soooo, what's the point, you know?!?!?

Think I'll leave "well enough" alone...  ;)


  I 'm using pretty well the same stuff you are. I basically use compiz to test my graphics adapter hardware.  It's pretty neat some of the stuff one can do.  Looks like raring is having a tougher time with other features that are available.  I know during Precise Pangolin beta testing that a  few developers set out to  obsolete ccsm. That was quite a debate. So far, on my nvidia Gforce 210/218 I am only having problems with 3D windows.  A lot of the older features were taken out during the quantal  testings.

"Doing a little research... it's pretty bad when the Compiz maintainers are throwing in the towel."

 Wow .. I never thought it would come to that.

 Thanks for noting that.

Regards,
ventrical

---

### Post by VinDSL on 2012-12-02
> **ventrical said:**
> > "Doing a little research... it's pretty bad when the Compiz maintainers are throwing in the towel."

 Wow .. I never thought it would come to that.

 Thanks for noting that.

Heh!  Shall we avail ourselves?  :D

SOURCE:  [http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/#comments](http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/#comments)
[QUOTE=smspillaz]
Hmm, I think you misunderstand my point [...]

Maintaining this stuff is a huge drag on our development manpower. 

**[COLOR="Red"]Finding people to work on compiz is hard, and at the moment there are only two full-time maintainers.[/COLOR]** 

Our to priorities right now are fixing bugs, updating core to work with the evolving desktop architecture and making compiz scream performance wise (I&#8217;ll post a bit on this in a while). We&#8217;ll keep maintaining the more popular stuff (as we already do now), but I&#8217;m looking for people who would be willing to maintain the stuff we don&#8217;t enable by default. If there is such a strong base of users who love this stuff, then there must be someone out there who would be willing to volunteer to keep it up to date.

So. Are there?[/QUOTE]

---

### Post by ventrical on 2012-12-02
> **VinDSL said:**
> Heh!  Shall we avail ourselves?  :D

SOURCE:  [http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/#comments](http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/#comments)

Sam S. wrote:
"Generally speaking you&#8217;ll only really need to know your way around  C++. For some of the more complex plugins, a good understanding of  graphics math and linear algebra is useful, especially plugins that make  heavy use of vertex transformations. Very few of the plugins use openGL  directly. You&#8217;ll know instantly when you see it.
 I&#8217;m always available on #compiz-dev and #ubuntu-desktop . We use a  code-review process in launchpad and require anything that touches the  default usecase in ubuntu to come with unit tests (unless explicitly  excepted)."


 I really do not think it is this complicated, mind you my C++ skills have been sitting on the shelf for some time. My observation at this point is that there has been an obsoletion of macros , that Unity DE has more or less invaded or replaced  the greater numbers of ccsm macros and, rather than patch them, remove those features from ccsm to make Unity *appear* faster.


 In Precise 12.04LTS most (if not all) of the plugins are working just fine.


My suggestions(s) would be this:


Install the newer raring 13.04 kernelRCs on a 12.04 machine and test ccsm features and determine if those features will run smoothly with the RCs (I'll do this as a preliminary since I have the hardware resources). If some of these tests show positive results then the kernel infrastructure can be ruled out as the culprit for the deprecated current plugin features with 13.04 and more attention can be given to Unity/Compiz Core, to be investigated as the culprit for the regressions in ccsm
-plugins in particular.


Secondly, implement some newer macros on some of the existing plugins that get away from the <super><alt><ctrl> and <tab> keys for the purpose of validating the declaration that hooks to  the most recent plugins have been supplemented or altogether terminated. ( I can also do some of this).


After  a few tests , if results are promising, then perhaps looking at the code would be the next step if these plugins could not be adequately patched, perhaps even using a ppa.


*note*


 I had read the messages in that link and obviously a lot of Ubuntu and Linux users feel strongly about vintage compiz plugins.


What do you think?

---

### Post by ventrical on 2012-12-02
Ok.. I tired to bust ccsm  in 12.04 using the raring ringtail 3.7.RC7 kernel. No go.

ps.. Nokia is not the best camera. Also... I was trying to hit some initiate keys that required two hands .. so it was awkward. Be patient :)

[http://www.youtube.com/watch?v=m18JQ-jhOLQ&feature=youtu.be](http://www.youtube.com/watch?v=m18JQ-jhOLQ&feature=youtu.be)

Quote:
                                                                      Originally Posted by **smspillaz**                                      
                 [I]Hmm, I think you misunderstand my point [...]

Maintaining this stuff is a huge drag on our development manpower. 

**[COLOR=Red]Finding people to work on compiz is hard, and at the moment there are only two full-time maintainers.[/COLOR]** 

Our to priorities right now are fixing bugs, updating core to work with  the evolving desktop architecture and making compiz scream performance  wise (I&#8217;ll post a bit on this in a while). We&#8217;ll keep maintaining the  more popular stuff (as we already do now), but I&#8217;m looking for people  who would be willing to maintain the stuff we don&#8217;t enable by default.  If there is such a strong base of users who love this stuff, then there  must be someone out there who would be willing to volunteer to keep it  up to date.

So. Are there?"

--------------------------------

In light of the way ccsm behaves on PP 12.04LTS .. with the new Raring 3.7RC7 kernel.. I just don't get it.  I am assuming that  some of the devs decided to try a Unity hack (secret skunks works -remember?!) and decided to throw some of the ccsm legacies into the trash bin.

regards..


[/I]

---

### Post by ventrical on 2012-12-02
Just a side note.. I got the PC I tested this procedure on from the side of the road. It was an orphan rebuilt from scrap.

---

### Post by ventrical on 2012-12-05
Downgrading the previous versions of compiz and plugins will remove compiz , unity and ubuntu-desktop. So I would assume that  the software sources and inner workings of the repositores is locking this option out by default. This may be prerequisite to  prevent any interfection with current depends, however, I fail to see the logic in this at this current point - so I will attempt to  to follow through with the process and see how badly it breaks this install.

On topic.. compiz still is not panicing  but 3D Windows option is still borkfurcated :)

---

### Post by mc4man on 2012-12-05
> **ventrical said:**
> Downgrading the previous versions of compiz and plugins will remove compiz , unity and ubuntu-desktop. So I would assume that  the software sources and inner workings of the repositores is locking this option out by default. This may be prerequisite to  prevent any interfection with current depends, however, I fail to see the logic in this at this current point - so I will attempt to  to follow through with the process and see how badly it breaks this install.

On topic.. compiz still is not panicing  but 3D Windows option is still borkfurcated :)
You can't use the older (pre GLES) compiz in 13.04 or 12.10

As far as the plugins still in the source but not available, they fall into 2 types - 
These won't build let alone work without a re-write
> # temporarily disable plugins that aren't ported yed
set (COMPIZ_DISABLE_PLUGIN_ANIMATIONADDON ON)
set (COMPIZ_DISABLE_PLUGIN_BICUBIC ON)
set (COMPIZ_DISABLE_PLUGIN_BLUR ON)
set (COMPIZ_DISABLE_PLUGIN_COLORFILTER ON)
set (COMPIZ_DISABLE_PLUGIN_CUBEADDON ON)
set (COMPIZ_DISABLE_PLUGIN_GEARS ON)
set (COMPIZ_DISABLE_PLUGIN_GROUP ON)
set (COMPIZ_DISABLE_PLUGIN_LOGINOUT ON)
set (COMPIZ_DISABLE_PLUGIN_REFLEX ON)
set (COMPIZ_DISABLE_PLUGIN_THUMBNAIL ON)
set (COMPIZ_DISABLE_PLUGIN_STACKSWITCH ON)
set (COMPIZ_DISABLE_PLUGIN_WALLPAPER ON)
set (COMPIZ_DISABLE_PLUGIN_TRIP ON)

These would likely build but won't work correctly or at all
> # disable plugins which won't work on ES2 builds
if (BUILD_GLES)

    set (COMPIZ_DISABLE_PLUGIN_TD ON)
    set (COMPIZ_DISABLE_PLUGIN_COLORFILTER ON)
    set (COMPIZ_DISABLE_PLUGIN_MBLUR ON)
    set (COMPIZ_DISABLE_PLUGIN_BENCH ON)
    set (COMPIZ_DISABLE_PLUGIN_FIREPAINT ON)
    set (COMPIZ_DISABLE_PLUGIN_SHOWREPAINT ON)
    set (COMPIZ_DISABLE_PLUGIN_WIDGET ON)
    set (COMPIZ_DISABLE_PLUGIN_SHOWMOUSE ON)
    set (COMPIZ_DISABLE_PLUGIN_SPLASH ON)

That's just the way it is & will be. 
Plugins in the compiz-plugins package do work but if they break then fixing will be slow at best..

---

### Post by ventrical on 2012-12-05
From:

[http://gatt.is/2011/10/10/porting-opengl-rendering-to-opengl-es-2-0/](http://gatt.is/2011/10/10/porting-opengl-rendering-to-opengl-es-2-0/)

"
OpenGL ES 2.0 also doesn&#8217;t do our matrix homework for us, so we have to  write all the linear algebra to get the modelview, projection, and  texture matrices in a form we can pass to our programmed shader.  I  won&#8217;t go into details on how to do this, but you can find most of the  OpenGL 1.0 functions like glPushMatrix, glPopMatrix, glMultMatrix,  glTranslatef, glRotatef, glOrthof, etc implemented in [milkshake.js]("http://github.com/gattis/milkshake/blob/master/milkshake.js")."


It's sad that nobody though of building a converter to do the vertex transformations from open GL or perhaps it not that simple.

Thanks mac4man

---

### Post by ventrical on 2012-12-05
I tried to install the glmark2-es2 package and  the library needs a ppa so it will not install unless you install the ppa. seeing that this would not provide any progress to current situation, I aborted that test.

---

### Post by jpeddicord on 2012-12-05
> **ventrical said:**
> From:

[http://gatt.is/2011/10/10/porting-opengl-rendering-to-opengl-es-2-0/](http://gatt.is/2011/10/10/porting-opengl-rendering-to-opengl-es-2-0/)

"
OpenGL ES 2.0 also doesn&#8217;t do our matrix homework for us, so we have to  write all the linear algebra to get the modelview, projection, and  texture matrices in a form we can pass to our programmed shader.  I  won&#8217;t go into details on how to do this, but you can find most of the  OpenGL 1.0 functions like glPushMatrix, glPopMatrix, glMultMatrix,  glTranslatef, glRotatef, glOrthof, etc implemented in [milkshake.js]("http://github.com/gattis/milkshake/blob/master/milkshake.js")."


It's sad that nobody though of building a converter to do the vertex transformations from open GL or perhaps it not that simple.

Thanks mac4man

[http://glm.g-truc.net/](http://glm.g-truc.net/) would beg to differ.

I've used GLM for my own GL projects; it does everything you have have missed from classic-GL (projection, gluLookAt, etc) and more.

The matrix math itself isn't all that difficult to figure out in any case; there's a pretty standard 4d-projection matrix setup you can find all over the internet.

---

### Post by ventrical on 2012-12-06
> **jpeddicord said:**
> [http://glm.g-truc.net/](http://glm.g-truc.net/) would beg to differ.

I've used GLM for my own GL projects; it does everything you have have missed from classic-GL (projection, gluLookAt, etc) and more.

The matrix math itself isn't all that difficult to figure out in any case; there's a pretty standard 4d-projection matrix setup you can find all over the internet.

Thanks jpeddicord.

 I used to  do my own graphics in 1990 using the LINE command in GWBASIC.! lol :)

 Part of it is learning some of the new scripts. It would take some time. However I think there are probably some other methods  (which I will explore) that  may not be so painstaking.

---

### Post by ventrical on 2012-12-08
Across the board compiz updates  does nothing really to fix 3D windows  effect.

---

