---
title: "Egor's Graphing Calculator 1.4 is out. Give it a try."
date: 2010-02-14
forum: The Cafe
---

### Post by RussianVodka on 2010-02-14
Hey,

I've been developing an open source graphing calculator for the past couple of weeks, and version 1.4 is now out. Most of the changes are geared towards usability, like being able to drag the graph plane with your mouse, rather than having to use the directional buttons.

Here is the complete list of changes since last release:
[LIST]
[*]Changed current x/y coordinates display from tooltip to label. The table pane had to be redrawn every time the tooltip was changed, which caused performance problems.
[*]Can now use mouse to drag graph plane.
[*]Added Right click menues:
[LIST]
[*]Copy expressions, variables, and their values.
[*]Remove rows from expression and variable tables.
[*]Added cut, copy, and paste to input fields.
[/LIST]
[*]Manually asign color to graph.
[/LIST]

And here are the download and info links:
[i][Info Page]("http://epoblaguev.com/?page=Projects/graphCalc.php&subNav=Projects/navBar.php")
[Change Log]("http://docs.google.com/Doc?docid=0Ab4b-lIlp5jXZGRjY2dmcWpfMjNnY3c3cnZjeg&hl=en")
[Download Page]("http://code.google.com/p/graphingcalculator/downloads/list")[/i]

Enjoy.
All input is welcome.

---

### Post by sandyd on 2010-02-16
created deb file.
after a few ](*,)](*,)](*,)
of course since I never compiled java debs before, only normal debs...
p.s. if you could get an icon for the menu, that would be nice.
p.p.s. menu was a pain in the rear to do.
So I did it the cheap way by making debian/rules copy it in....
[s]See Atachment[/s]Link Below
when did ubuntuforums stop alowing debs?


[http://www.mediafire.com/download.php?cfy2dhjinzy](http://www.mediafire.com/download.php?cfy2dhjinzy)
p.p.p.s. will create PPA as soon as my pgp keys are revalidated.
have fun!

---

### Post by sandyd on 2010-02-17
Finished playing with the PPA.

package is called graphcalc

PPA is here: [https://launchpad.net/~dolphinaura/+archive/graphcalc](https://launchpad.net/~dolphinaura/+archive/graphcalc)

---

### Post by RussianVodka on 2010-02-19
Cool, thanks.

Edit: How will updating it work?

---

### Post by sandyd on 2010-02-19
> **RussianVodka said:**
> Cool, thanks.

Edit: How will updating it work?

its updated using debuild -S and dput.
each time the svn repo is updated, the changelog is edited to reflect the new version, and debuild builds the new source packages
dput then updates the PPA with the version debuild just created.
The makefile was generated using mmake, and it worked after hacking and revamping the entire makefile.

oh, and no hardy packages. The rules file is made only for jaunty+

---

### Post by RussianVodka on 2010-02-20
Ah, so it's self building? That's snazzy.

---

### Post by RussianVodka on 2010-02-26
Version 1.7
New release! Many new additions!

Changelog:
[List]
[*]Many minor changes that add usability.
[*]Now using Graphics2D to draw the graphs. Allowing for more rendering possibilities.
[*]Added line thickness settings.
[*]Added option to use anti-aliasing.
[*]Added graph background color settings.
[*]Can now add points to graph and draw lines between them.
[*]Fixed a bunch of stuff.
[/List]

Enjoy. All feedback welcome.

And here are the download and info links:
[i][Info Page]("http://epoblaguev.com/?page=Projects/graphCalc.php&subNav=Projects/navBar.php")
[Change Log]("http://docs.google.com/Doc?docid=0Ab4b-lIlp5jXZGRjY2dmcWpfMjNnY3c3cnZjeg&hl=en")
[Download Page]("http://code.google.com/p/graphingcalculator/downloads/list")[/i]

---

### Post by *Boots* on 2010-02-27
Hello all!!

I'm not a programmer, yet... Could you do me a favor and include in your calculator all the rich features available in graphcalc 4.0 for windows, I'm serious go download it and use it.... after that program I find myself wanting.... even downloaded the so-called linux version(that you have to compile).  Its free for windows, but I've fallen for ubuntu and don't want to go back to windows for much....  tried libinez, extcalc, and qalculate and none of them lived up to graphcalc's hype... plz make that program so I can press a button on my GUI and install it into my accessories!!

Thx:)

Boots

esp like the 3d graphing!!!!!!

---

### Post by Warpnow on 2010-02-27
> ***Boots* said:**
> Hello all!!

I'm not a programmer, yet... Could you do me a favor and include in your calculator all the rich features available in graphcalc 4.0 for windows, I'm serious go download it and use it.... after that program I find myself wanting.... even downloaded the so-called linux version(that you have to compile).  Its free for windows, but I've fallen for ubuntu and don't want to go back to windows for much....  tried libinez, extcalc, and qalculate and none of them lived up to graphcalc's hype... plz make that program so I can press a button on my GUI and install it into my accessories!!

Thx:)

Boots

esp like the 3d graphing!!!!!!

Download the deb file Carlee posted a link to. Then install the file (double click it, opens with gdebi by default). Super easy.

---

### Post by *Boots* on 2010-02-28
I downloaded the calculator. It does as advertised.... even plotted a circle:) I would like you all to try graphcalc 4.0 for windows and see whats up:) that program even does the conversions qualulate does!! When Is 3d comin for yours? Density plots??(graphcalc doesnt' do that one)

Boots:)

---

### Post by RussianVodka on 2010-02-28
> ***Boots* said:**
> I downloaded the calculator. It does as advertised.... even plotted a circle:) I would like you all to try graphcalc 4.0 for windows and see whats up:) that program even does the conversions qualulate does!! When Is 3d comin for yours? Density plots??(graphcalc doesnt' do that one)

Boots:)

Which calculator draws circles, mine or graphCalc?

Also I have graphcalc and I don't really like it. The graphing part seems very rigid and not user friendly, and I just don't like the interface of the calculator part.

Also, if you want to do very complicated calculations, you may as well go to [www.wolframalpha.com](www.wolframalpha.com), which is probably more accurate than any free calculator you're gona find.

---

### Post by *Boots* on 2010-03-01
> **RussianVodka said:**
> Which calculator draws circles, mine or graphCalc?

Also I have graphcalc and I don't really like it. The graphing part seems very rigid and not user friendly, and I just don't like the interface of the calculator part.

Also, if you want to do very complicated calculations, you may as well go to [www.wolframalpha.com]("http://www.wolframalpha.com"), which is probably more accurate than any free calculator you're gona find.

Really? you have graphcalc 4.0.1 from the following url:[http://www.graphcalc.com/](http://www.graphcalc.com/) ??? You think the calculator part is to rigid? Maybe its because that was the first 'computer based' graphing calculator I used, but I think its really good. 

You know you can manipulate 3d plots in graphcalc(i.e. rotate them on all axis, zoom in/out). Oh and the best thing is that its free as in freedom, with linux code already made, but I don't have the brainpower to make it work. Its just sittin there at sourceforge waiting for a smart dude like you to pick up the torch and make it work for a guiphile like me:) 

Really though I'd like to see a calculator with all the functionality of graphcalc 4.0.1, a lot of the features of the TI-89, with now that I know about it, the pure math portions of that wolfram alpha, graphmatica(from ksoft) and you could even make a curve fitting feature. 

 Oh and I did plot a circle on your calculator.  Are 3d plots in the plans for the future? 

Boots

---

### Post by Kdar on 2010-03-01
Really nice software. Spasibo

By the way.. Is there way to trace a graph or maybe to turn on grid? If not, do you plan to implement it some day?

---

### Post by RussianVodka on 2010-03-01
> **Kdar said:**
> Really nice software. Spasibo

By the way.. Is there way to trace a graph or maybe to turn on grid? If not, do you plan to implement it some day?

I was thinking of both of those, but am not yet sure how to accomplish them from a design point of view.

For example, what would be the criteria for drawing the grid? If the graph plane is -10 to 10 on both axis's, then I could draw a grid line at every 1 unit interval. But once I start zooming in, a new interval for drawing the grid would be needed. When would I switch to the new drawing interval, when would I switch back?

Maybe I can divide it up such that if the range of values on the graph is between 10 and 100 the interval is 5. If it's between 100 and 1000, it can be 50. And so on. Mathematically I think that would look something like:
if range is between 10^n and 10^n+2, interval is (10^(n-1))/2.

As far as tracing graphs, I'll figure it out later.

---

### Post by okos on 2010-07-22
Egor!
Great work!
I was just looking for a graphing calc for my son for this coming school year.

Thanks a bunch!

One quick question, are you going to add a print button?

---

