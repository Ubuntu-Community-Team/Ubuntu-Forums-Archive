---
title: "Awesome screenshot app for Linux released!"
date: 2009-03-05
forum: The Cafe
---

### Post by Vadi on 2009-03-05
Just thought I'd point this out to anyone who ever deals with screenshots. This app is designed to make everything around them easy :popcorn:

**Site:** [http://shutter-project.org/](http://shutter-project.org/)

**Digg to tell others**: [http://digg.com/linux_unix/Awesome_screenshot_app_for_Linux_released#](http://digg.com/linux_unix/Awesome_screenshot_app_for_Linux_released#)

Latest update:
> This is the first release of Shutter as it is - we've just renamed it from GScrot. So you'll now find it called Shutter inder Applications &#9656; Accessories, along with a nicer new logo (thanks to Pascal Grochol for the design).

Major updates in this release are printing support, support for a whole lot of formats to save pictures in, support for watching changes to files (open the screenshot externally in gimp, save it - and shutter updates its copy), integration with GVFS (you can upload sites that you've connected to via Places &#9656; Connect), better recognition for programs that can open a picture, faster thumbnail creation, and improved dialogs!

As if that weren't enough, here is the full changelog detailing every item updated:

  * General changes
    -- Rebranding from GScrot to Shutter
    -- Exports to and opens all file formats supported by gdk-pixbuf
    -- Added native printing support (instead of gtklp)
    -- Watch opened files via GnomeVFS File Monitor to monitor changes
    -- Integration of GNOME Virtual File System and
       GNOME authentication manager (LP: #310780)
    -- Respect non-rectangular windows (XSHAPE)
       when using metacity (LP: #260771)
    -- Use themeable icons wherever its is possible
    -- Use systemwide MIME Information instead of config file
    -- Move screenshots to trash instead of deleting them (LP: #313003)
    -- Faster thumbail creation and caching
       (improves gui startup when a lot of files are in last session)
    -- Improved Dialogs (e.g. Settings Dialog)
    -- Show context menu for each file in session tab (right click)
  * Gui improvements
    Show current profile in statusbar (LP: #279271)
    Second toolbar removed (LP: #311626)
    Progress bars (LP: #310299)
    -- LP: #311627
    -- LP: #312966
    -- LP: #313346
    -- LP: #326758
  * Drawing Tool
    Scale uniformly (LP: #310708)
    Added standard actions (copy, cut, paste, delete) (LP: #313343)
    Added censor tool to hide private data (LP: #317659)
    -- LP: #310717
    -- LP: #310721
    -- LP: #311574
    -- LP: #311576
    -- LP: #311577
    -- LP: #311580
  * Miscellaneous
    Shutter shows up in GNOME add/remove (LP: #322388)
    Repository is not signed (thanks to the LP Team) (LP: #312681)
  * Plugins
    New hard shadow plugin (thanks to Tualatrix) (LP: #331914)
  * Fixed bugs
    -- LP: #303090
    -- LP: #313761
    -- LP: #316917
    -- LP: #336120
    -- LP: #336126
    -- LP: #336121
    -- LP: #336118
    -- LP: #336133
    -- LP: #336124
  * updated translations

---

### Post by Polygon on 2009-03-05
can it really take screenshots of entire websites? If so thats incredibly awesome.

also the name is a lot better.

---

### Post by damis648 on 2009-03-05
> **Polygon said:**
> can it really take screenshots of entire websites? If so thats incredibly awesome.

also the name is a lot better.

Thank you so much for picking shutter, :popcorn:

---

### Post by Excedio on 2009-03-05
This seems like a pretty awesome program. I think i'm gonna go ahead and try it out. :D

---

### Post by Vadi on 2009-03-05
> **Polygon said:**
> can it really take screenshots of entire websites? If so thats incredibly awesome.

also the name is a lot better.

Yes, yes it can.

---

### Post by Vadi on 2009-03-05
> **damis648 said:**
> Thank you so much for picking shutter, :popcorn:

Thanks for helping us out man ;)

---

### Post by doorknob60 on 2009-03-05
Nice, I got older version installed, awaiting the AUR PKGBUILD maintainer to update it now :-)

---

### Post by Vadi on 2009-03-05
> **doorknob60 said:**
> Nice, I got older version installed, awaiting the AUR PKGBUILD maintainer to update it now :-)

Yeah that would be great. Share the post on Arch forums too ;)

---

### Post by 5BallJuggler on 2009-03-05
Just installed shutter, looks like a top quality app.

Thanks

---

### Post by BGFG on 2009-03-05
Just today i was reminiscing on my support .doc creation days with snagit. Nice to see a high quality app in Linux. No use for it yet but very glad that the option is there.

Thanks to the Shutter team.

---

### Post by hotweiss on 2009-03-05
Very nice! Thanks.

---

### Post by chucky chuckaluck on 2009-03-05
is this a gui version of scrot, or can it do things that scrot can't?

---

### Post by kavon89 on 2009-03-05
I followed [these]("http://shutter-project.org/faq-help/ppa-installation-guide/") instructions to get it installed, but I used the correct (or so I think) repository for intrepid instead of hardy in the example obviously. The key said OK so I assume that worked...

shutter doesn't show up in a search and I've reloaded several times and restarted Synaptic... what is wrong?

(a crude screenshot attached)

---

### Post by JackieChan on 2009-03-06
Hmm...

---

### Post by kostkon on 2009-03-06
> **kavon89 said:**
> I followed [these]("http://shutter-project.org/faq-help/ppa-installation-guide/") instructions to get it installed, but I used the correct (or so I think) repository for intrepid instead of hardy in the example obviously. The key said OK so I assume that worked...

shutter doesn't show up in a search and I've reloaded several times and restarted Synaptic... what is wrong?

(a crude screenshot attached)
Use the search option to find it and not the quick-search...

---

### Post by adamlau on 2009-03-06
Way too many deps and slow as a turtle. Xfce Screenshooter 1.5.1 (standalone) is much cleaner, lighter and faster, even with Xfce deps.

---

### Post by mario.kemper on 2009-03-06
> **kavon89 said:**
> 

shutter doesn't show up in a search and I've reloaded several times and restarted Synaptic... what is wrong?



Please use the search option instead of quick search as kostkon already suggested.
You can even install Shutter via terminal by entering:
```
sudo apt-get install shutter
```

Greetings
Mario

---

### Post by mario.kemper on 2009-03-06
> **chucky chuckaluck said:**
> is this a gui version of scrot, or can it do things that scrot can't?

No, it is an independent application which is offering a lot more features than scrot (terminal based app):

You can take a screenshot of a specific area, window, your whole screen, or even of a website - apply different effects to it, draw on it to highlight points, and then upload to an image hosting site, all within one window.


Just give it a try ;)

Greetings
Mario

---

### Post by mario.kemper on 2009-03-06
> **adamlau said:**
> Way too many deps and slow as a turtle. Xfce Screenshooter 1.5.1 (standalone) is much cleaner, lighter and faster, even with Xfce deps.

Due to the fact that Shutter offers features (embedded image editing tool, image uploading, plugin interface to add effects, session design etc.) that Xfce does not have there are some more dependencies.

Shutter is intended for people who need a bit more than standard tools (delivered within a Desktop Environment) are offering.

Greetings
Mario

---

### Post by sertse on 2009-03-06
It's good that both shutter and xfce screenshot exist.

Shutter is probably the most advanced screenshooting app around, and does everything and more. 

Xfce screenshot on the other hand finally gives people a GUI screenshot app with minimal dependencies. 

They are clearly made for different purposes...

---

### Post by Scubdup on 2009-03-06
> **kavon89 said:**
> Shutter doesn't show up in a search and I've reloaded several times and restarted Synaptic... what is wrong?
Their instructions say to click [the link]("apt:shutter"). Did you try that?

---

### Post by Polygon on 2009-03-06
im trying to set it to upload to my imageshack account, why do i have enter that url? they have phased out the url login thing and now they use a regular login/password....as i can't find my email that contained my login url, is there some way to retrieve it?

---

### Post by joey-elijah on 2009-03-06
I've used gScrot on and off for a while but it was sooooooo slow and overly complicated JUSt to take a section of the screen or a window. This is an area where Windows's Snipping Tool certainly wins.

HOWEVER, i'm off to download shutter and see whether things have improved! A great snipping tool is something desperately needed in linux for all us reviewers etc!

EDIT: It's nice. Still takes far too long to load up and process a grab... still it's an obvious improvement - and an awesome new logo!

---

### Post by ELD on 2009-03-06
Looks like a pretty dam good program, well done!

---

### Post by Vadi on 2009-03-06
> **joey-elijah said:**
> EDIT: It's nice. Still takes far too long to load up and process a grab... still it's an obvious improvement - and an awesome new logo!

Yeah, imagemagick makes it a bit slow. Taking a fullscreen screenshot (2700ish by 1000ish) makes it use the cpu for 2-3s. But some speed improvements were done and we're always on the lookout for more ;)

---

### Post by mario.kemper on 2009-03-06
> **Polygon said:**
> im trying to set it to upload to my imageshack account, why do i have enter that url? they have phased out the url login thing and now they use a regular login/password....as i can't find my email that contained my login url, is there some way to retrieve it?

I am afraid uploading to imageshack is broken in Shutter 0.70. Sorry for that. 
I've just opened a bug for this, so you can track the status here:

[https://bugs.launchpad.net/shutter/+bug/338829]("https://bugs.launchpad.net/shutter/+bug/338829")

I'll try to fix this as soon as possible.

Greetings
Mario

---

### Post by Vadi on 2009-03-06
edit: double

---

### Post by kavon89 on 2009-03-06
> **mario.kemper said:**
> Please use the search option instead of quick search as kostkon already suggested.
You can even install Shutter via terminal by entering:
```
sudo apt-get install shutter
```

Greetings
Mario

Worked thanks!

---

### Post by Therion on 2009-03-06
Wow, this is **slick**!  Very nice...

---

