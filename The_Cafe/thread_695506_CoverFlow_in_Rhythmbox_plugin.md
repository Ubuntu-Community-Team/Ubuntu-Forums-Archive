---
title: "CoverFlow in Rhythmbox plugin"
date: 2008-02-13
forum: The Cafe
---

### Post by bwiklak on 2008-02-13
Hi,
I'm working on CoverFlow plugin for rhythmbox.
For now i have OpenGL/gtkglext engine that shows jpegs from directory.
You can see my scrrenshot with actual program.


I would like to steel some code from visualization plugin to integrate my
engine with RB.


I will inform You about progress.

What do You think?

This info is also on [http://bugzilla.gnome.org/show_bug.cgi?id=516186](http://bugzilla.gnome.org/show_bug.cgi?id=516186)

---

### Post by /dev/clast on 2008-02-13
nice work! :-)
you should get in contact with Mirco "macslow" Müller. he's working on a feature like that for rhythmbox (there is a spec for it for hardy).
seems like duplictated work.

---

### Post by rubicon on 2008-02-13
> **/dev/clast said:**
> nice work! :-)
you should get in contact with Mirco "macslow" Müller. he's working on a feature like that for rhythmbox (there is a spec for it for hardy).
seems like duplictated work.
+1

**bwiklak**, you definitely must cooperate with macslow! His project is called "Sparkle".
Here's blueprint: [https://blueprints.launchpad.net/ubuntu/+spec/hardy-sparkle](https://blueprints.launchpad.net/ubuntu/+spec/hardy-sparkle)

---

### Post by bwiklak on 2008-02-13
I have written a mail to MacSlow. We will see. 
I would like to have betha version as soon as possible. Mac i much more experienced then me, but maybe has less time. I think maybe I would write a code and he could guide me.

---

### Post by PmDematagoda on 2008-02-13
This thread has been moved to the Community Cafe as it is not a support thread and it can receive better attention at the Community Cafe.

---

### Post by | MM | on 2008-02-13
Hi,

I just saw this on the Rhythmbox mailing list.

[QUOTE="Mirco "MacSlow" Müller"]
	Right now sparkle is on hold, because I'm busy with higher-prio tasks.
But I will return to working on sparkle in the next few days. At some
point I will update the rhythmbox-wiki with information gathered writing
sparkle (likely to happen after I've finished the plugin) so others will
not have to go through the same pain I had  :) 

	Regarding clutter, it could be done using it - clutter is getting
better all the time - but there are still some bits missing
(multitexture-support/"texture-compositing", camera-object/paths), which
I absolutely want to use in sparkle. Therefore I will stick to pure
OpenGL for the time being.

	But I can imagine I'll port a future revision of sparkle to using
clutter. There are a few features I'd like to add to clutter, but that's
scheduled for after sparkle... and if I find the time to work on those. 

Best regards...

Mirco "MacSlow" Müller[/QUOTE]

There are a couple of screenshots attached.
[http://macslow.thepimp.net/shots/sparkle-2.png](http://macslow.thepimp.net/shots/sparkle-2.png)
[http://macslow.thepimp.net/shots/sparkle-1.png](http://macslow.thepimp.net/shots/sparkle-1.png)

---

### Post by koleoptero on 2008-02-13
Wow, really impressive work bwiklak! :) This will be a good addition to RB.

On another note, can't someone just make an equaliser for rhythmbox? It can't be more complicated than this... :(

---

### Post by aimran on 2008-02-13
I love rhythmbox even more now :)

---

### Post by macogw on 2008-02-13
Can you select what disc you want to play using it?  From the screenshot, it looks like it's just displaying what disc you're using or something.

---

### Post by pt123 on 2008-02-13
This is awesome. I am really liking RB with it's drag and drop feature for covers. Way ahead of other Gnome Mp3 players.

Is it possible to post the code so one can use it on a directory independent of RB.

This feature would be very useful in a Gallery/Photo application to browse through your photos rapidly.

Thanks

---

### Post by bwiklak on 2008-02-14
**to macogw:** 
screenshot shows program as it is for now. It opens GTK window with OpenGL widget that shows jpegs from directory. One can switch from one cover to another like in iTunes.

Right now I'm fighting with RB plugin architecture. MocSlow warned me that GL part is only a SMALL think, and he was right unfortunately.  

I dont know yet if I'll manage to help MacSlow with his work or if I'll do may own plugin. I would like to write it in pure C, and make whole thig quite simple. MacSlow is thinking about Python and advanced features (or maybe I'm wrong).

**to pt123:**
Wow I did not thought about it :).
I'll post code as soon as I'll clean it a little. I'm not sure it it's suitable for   Gallery/Photo application. It loads only 12 jpegs and tries to load other when they are to be shown. I have several problems with it because not every bitmap can be OpenGL texture. Some of my covers are shown very poor and I don't know yet if it is libjpg or my OpenGL code problem.



I would like to concentrate on integration with RB. To do it i have to hack visualizer plugin code. Please be patient, I'm working very hard to do it, but I have also another work and I'm trying to end my masters thesis. 

I really would like to have this plugin right now but I'm just too poor GTK programmer. I'm still learning.

---

### Post by bwiklak on 2008-02-15
I was wrong, MacSlow writes his plugin in C.

---

### Post by pt123 on 2008-02-15
> **bwiklak said:**
> 
I'll post code as soon as I'll clean it a little. I'm not sure it it's suitable for   Gallery/Photo application. It loads only 12 jpegs and tries to load other when they are to be shown..

Thanks much appreciated

---

### Post by bwiklak on 2008-02-15
I finally managed to break into visualization plugin and to draw
widget inside RB :)

I'm getting a strange problem.
Widget that I'm drawing is for sure gl widget (OpenGl program are
running little frickish in compiz).
I can also draw green background setting glClearColor( 0.0f, 1.0f,
0.0f, 0.0f ); and glClear( GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT
);

But I cant draw any object. None poligon I'm creating is visible.
glGetError() == 0 all time.

Maybe someone has some ideas?
The same code in simple gtk window works good, perespective and other
things are set correct.

---

### Post by pt123 on 2008-02-15
you might have better luck here:
[http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

---

### Post by bwiklak on 2008-02-16
Hey people, Check out this!!!
Plugin is in RB window.

Still, covers are just jpegs from directory.
Plugin is useless but this screenshot shows, it is possible to draw gl in RB,

I'm working very hard to add some usable actions and to overcome problems.

In several days I would like to show some code, maybe someone will be able to help then.

People from rhythmbox-devel complain that I'm posting screenshots in this forum, but I really dont know where to place them and where to place code so please tell me.
Rhythmbox C plugins has to be place in RB source tree so it us useless to place code at sourceforge. I'm a noobie so need help.

Thanks.

---

### Post by bwiklak on 2008-02-16
Oh, ok,ok, adding attachments on [http://bugzilla.gnome.org](http://bugzilla.gnome.org) is easy,

An enhanceent bug is there [http://bugzilla.gnome.org/show_bug.cgi?id=516186](http://bugzilla.gnome.org/show_bug.cgi?id=516186)

I'll post news here and on bugzilla.

---

### Post by pt123 on 2008-02-21
Wow that looks promising. Hopefully RB developers would be helpful to you. This could help kill all the other gnome media players.

---

### Post by bwiklak on 2008-02-29
I'm working now with my friend to develop some smart cover loading code. Please be patient.

---

### Post by bwiklak on 2008-03-10
Good news Everyone!

In spite of my laziness, we have real milestone in case of CoverFlow in Rhythmbox. Grzes Furga, who's not so prejudiced against Python as I am, worked nights and days long to give u some CoverFlowish feeling in RB.

Don't postpone, and check out betha at [http://code.google.com/p/rhythmboxcoverflow/](http://code.google.com/p/rhythmboxcoverflow/)

I have strong wish to do the same in C, I hope I'll find some time soon.

Regards, Bartek

---

### Post by DarthTibault on 2008-03-10
I just tested it, controlling it hasn't been implemented I presume?
> The plugin fetches covers downloaded by cover art display plugin (most of them since I don't escape artist / album names) 
That would be 2 covers from my entire library. All my covers are placed in the album's directory. You will add support for those covers in the future, right?

Looking good so far, I can't wait to see a fully functional release :)

---

### Post by pt123 on 2008-03-10
> **bwiklak said:**
> Good news Everyone!
Don't postpone, and check out betha at [http://code.google.com/p/rhythmboxcoverflow/](http://code.google.com/p/rhythmboxcoverflow/)

I have strong wish to do the same in C, I hope I'll find some time soon.

Regards, Bartek

That is great news, can't wait to get home and try it out.

---

### Post by justsomedude on 2008-03-10
Great to see you're putting the effort in this. :)

I can't get this to work though, same error message on Hardy Heron and Arch:

```
Traceback (most recent call last):
  File "/home/marv/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/__init__.py", line 25, in <module>
    from flow_widget import CoverFlowWidget
  File "/home/marv/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/flow_widget.py", line 28, in <module>
    import gtk.gtkgl        
ImportError: No module named gtkgl

(rhythmbox:9223): Rhythmbox-WARNING **: Could not load plugin rhythmboxcoverflow


(rhythmbox:9223): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Cover flow'
```

Am I missing some dependencies?

---

### Post by gzy on 2008-03-11
Search synaptic for gtkglext1 (shared libraries) and gtkglext1-python (glext python bindings) and You should be fine.

As for cover art in the album folder - I'll try to add that asap, although that'll be just a temporary fix. 

I don't have any cover files in my music folder - I keep all the cover's in id3 tags. The way to get this right is wait until rhythmbox fully supports coverart.

---

### Post by pt123 on 2008-03-11
when I tried it on hardy
when to plugins and selected Cover Flow
Dialog box: Unable to activate the plugin Cover Flow
I got the following error.
```

ImportError: No module named rhythmboxcoverflow

(rhythmbox:11503): Rhythmbox-WARNING **: Could not load plugin rhythmboxcoverflow
(rhythmbox:11503): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Cover flow'

```

I downloaded all the files from:
[http://rhythmboxcoverflow.googlecode.com/svn/trunk/](http://rhythmboxcoverflow.googlecode.com/svn/trunk/)

I also used synaptic to install the gtkglext1 (shared libraries) and gtkglext1-python

Which file contains the rhythmboxcoverflow module

**Edit**
Ok The website is not clear for people that don't have an SVN app.

I think you are meant to create a folder in the plugins folder called rhythmboxcoverflow
and drop all the files there. 

Now I a getting another different error
```

raceback (most recent call last):
  File "/home/r/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/__init__.py", line 25, in <module>
    from flow_widget import CoverFlowWidget
  File "/home/r/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/flow_widget.py", line 30, in <module>
    from OpenGL.GL import *
ImportError: No module named OpenGL.GL


```

**Edit 2 **
Ok fixed that by installing python-OpenGL thru synaptic. 

Now it loads up but it just has black box in RB
Terminal output
```

ile "/home/r/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/__init__.py", line 98, in source_changed
    self.flow_widget.load_covers(songs)
  File "/homer/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/flow_widget.py", line 83, in load_covers
    self.engine.load_covers(songs)
  File "/home/r/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/flow_engine.py", line 166, in load_covers
    entryid, self.texture_cache.get(art,al), art, al, t))
  File "/home/r/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/flow_engine.py", line 74, in get
    self.textures[offset] = glGenTextures(1)
IndexError: list assignment index out of range

```
Note I have all my covers in the rhythmbox/covers folder

---

### Post by gzy on 2008-03-11
yeah pt123, 
To sum up so far you need:
python,
gtkglext1
gtkglext1-python
python-opengl

(i thought python opengl is a dependency of gtkgl)


As for the other error You were getting I just fixed the svn, there was a 100 cover limit - it's gone now. 
(I someday hope to code smarter texture handling), for now the plugin will load all the covers from the current playlist, so if Your rb opens in the main library, it might take a while before You see anything (If You don't try to switch to a playlist and then back again)

---

### Post by pt123 on 2008-03-11
Thanks that works. Very smooth too. 
Well done, you got the hard part done, getting it to display the images in a coverflow manner. 

Now it's all the customisation and back end.

---

### Post by justsomedude on 2008-03-11
Thanks, it works now.

Doesn't work on Arch though, I get
```
ImportError: No module named ImageFont
```
there. 

But it does well on Hardy, good work guys. :)

EDIT: Installing

pil

did the trick on Arch.

---

### Post by NeroAQuila on 2008-03-13
Please, help me - what's this?

```
Traceback (most recent call last):
  File "/home/jan/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/__init__.py", line 25, in <module>
    from flow_widget import CoverFlowWidget
  File "/home/jan/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/flow_widget.py", line 34, in <module>
    from flow_engine import CoverFlowEngine
  File "/home/jan/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/flow_engine.py", line 29, in <module>
    import glFreeType
  File "/home/jan/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/glFreeType.py", line 13, in <module>
    import ImageFont
ImportError: No module named ImageFont

(rhythmbox:6870): Rhythmbox-WARNING **: Could not load plugin rhythmboxcoverflow


(rhythmbox:6870): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Cover flow'

```

---

### Post by quinnten83 on 2008-03-13
i just can't seem to find the dowload files.
I went to google, but I can't see them there.
anybody willing to point me in the right direction?

---

### Post by DarthTibault on 2008-03-13
> **NeroAQuila said:**
> Please, help me - what's this?

```
...
ImportError: No module named ImageFont
...

```

Obviously you're missing the ImageFont module, a few posts up justsomedude said that installing python-imaging did the trick, so try that.

> **quinnten83 said:**
> i just can't seem to find the dowload files.
I went to google, but I can't see them there.
anybody willing to point me in the right direction?
You have to download the source. You won't have to compile anything as it's written in Python.

This should install everything::
```
svn checkout http://rhythmboxcoverflow.googlecode.com/svn/trunk/ ~/.gnome2/rhythmbox/plugins/rhythmboxcoverflow
```

---

### Post by clebersantz on 2008-03-14
This is Very very amazing !!!!!  nice work !!!!

Who need iTunes now ? :)

Some suggestions:
Scrollbar integrated with music list selection
Group cover by Album, not by music

Good luck,
Cleber.

---

### Post by puccaso on 2008-03-14
```
(02:16:04) [0x80dc408] [rb_python_module_init] rb-python-module.c:387: Init of python module
Traceback (most recent call last):
  File "/home/mahir/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/__init__.py", line 25, in <module>
    from flow_widget import CoverFlowWidget
  File "/home/mahir/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/flow_widget.py", line 30, in <module>
    from OpenGL.GL import *
  File "/usr/lib/python2.5/site-packages/OpenGL/GL/__init__.py", line 2, in <module>
    from OpenGL.raw.GL import *
  File "/usr/lib/python2.5/site-packages/OpenGL/raw/GL/__init__.py", line 6, in <module>
    from OpenGL.raw.GL.constants import *
  File "/usr/lib/python2.5/site-packages/OpenGL/raw/GL/constants.py", line 7, in <module>
    from OpenGL import platform, arrays
  File "/usr/lib/python2.5/site-packages/OpenGL/platform/__init__.py", line 57, in <module>
    _load()
  File "/usr/lib/python2.5/site-packages/OpenGL/platform/__init__.py", line 53, in _load
    sys.platform, os.name,
RuntimeError: Unable to find an implementation for the 'linux2' ('posix') platform

(rhythmbox:8465): Rhythmbox-WARNING **: Could not load plugin rhythmboxcoverflow

(02:16:04) [0x80dc408] [rb_python_module_finalize] rb-python-module.c:394: Finalizing python module (null)

(rhythmbox:8465): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Cover flow'

```


this is my output.. any help please?

---

### Post by bwiklak on 2008-03-15
> **puccaso said:**
> ```
(02:16:04) [0x80dc408] [rb_python_module_init] rb-python-module.c:387: Init of python module

RuntimeError: Unable to find an implementation for the 'linux2' ('posix') platform


```

this is my output.. any help please?

I found BUG #195270, they say:


This bug was fixed in the package pyopengl - 3.0.0~b1-0ubuntu2

---------------
pyopengl (3.0.0~b1-0ubuntu2) hardy; urgency=low

  * debian/rules:
    - Removed "mv" of .egg-info directory in
      common-binary-post-install-indep, which caused broken symlinks in
      /usr/lib/python2.5/site-packages/PyOpenGL-3.0.0b1-py2.5.egg-info/.
      According to snapshot.debian.org the first package introducing this had
      already the "Where does this come from" comment in it (3.0.0~a6-1).
      The links where broken in 3.0.0~a6, too, but it did not depend on the
      OpenGL.platform.implementation feature. (LP: #195270)
    - clean target:
      - remove workaround for cdbs bug, which is fixed already
      - Do not remove setup.cfg from PyOpenGL.egg-info/SOURCES.txt.
        I could not find a reference why it was added and other packages
        do not remove it, too.
  * debian/control:
    - Standards-Version 3.7.3
    - Moved Homepage from Description to control field
  * Modify Maintainer value to match the DebianMaintainerField
    specification.

 -- Daniel Hahler <ubuntu@thequod.de> Wed, 27 Feb 2008 01:43:32 +0100


Maybe getting   pyopengl - 3.0.0~b1-0ubuntu2 will solve your problem.

---

### Post by puccaso on 2008-03-15
the problem seemed to sort it self out somehow, 
thanks for the reply.. 

but now - i dont see any cover images, just the gnome foot...

any ideas about that?

and im not able to browse through them.. just view them... is that all this does? lol:popcorn:

---

### Post by bwiklak on 2008-03-16
> **puccaso said:**
> the problem seemed to sort it self out somehow, 
thanks for the reply.. 

but now - i dont see any cover images, just the gnome foot...

any ideas about that?

and im not able to browse through them.. just view them... is that all this does? lol:popcorn:

At the moment covers are read from ~/gnome2/rhythmbox/covers folder where coverart plugin stores them. You shoul have coverart plugin enabled to make Rhythmbox download covers. In future it should be solved via id3 tags coverart.

---

### Post by bwiklak on 2008-03-16
> **puccaso said:**
> 
and im not able to browse through them.. just view them... is that all this does? lol:popcorn:

Puccaso, patience. We are only people! Grzes Furga's work is in progress, I will also try to do what I can to help him somehow. 
We are not sure if blowsing via coverflow is real such a good idea.
If anyone has some new thoughts/ideas please post. 
First of all I would like to have one civer per album not per song. When song changes maybe some aniomation (cover flipping or something). We will see.

Regards, Bartek

---

### Post by andrek on 2008-03-16
Glad to see somebody from Poland who does a major contribute to develop gnome's eyecandiness ;) Cheers.

---

### Post by QwUo173Hy on 2008-03-17
> **bwiklak said:**
> 
We are not sure if blowsing via coverflow is real such a good idea.
If anyone has some new thoughts/ideas please post. 


I think that browsing via coverflow is a must. People usually browse their physical music collection visually and to give them this same "interface" on the computer would be excellent.

If coverflow is not used to provide an interface, then it becomes trivial eyecandy. Please make this functionality at least an option if not the default behaviour.

Good luck with the project,
Jarlath

---

### Post by clebersantz on 2008-03-18
With CoverFlow plugin i`m getting a very high CPU usage (more than 40% for rythmbox), without CoverFlow i get above 2%.

---

### Post by Depressed Man on 2008-03-18
> **jarlath said:**
> I think that browsing via coverflow is a must. People usually browse their physical music collection visually and to give them this same "interface" on the computer would be excellent.

If coverflow is not used to provide an interface, then it becomes trivial eyecandy. Please make this functionality at least an option if not the default behaviour.

Good luck with the project,
Jarlath

I guess. My music collection is to big to scroll visually, I wouldn't know what half the album covers are. :lolflag:

> **clebersantz said:**
> This is Very very amazing !!!!!  nice work !!!!

Who need iTunes now ? :)

Some suggestions:
Scrollbar integrated with music list selection
Group cover by Album, not by music

Good luck,
Cleber.

You'd need iTunes if you have a modern iPod. :P


But this is awesome. I look forward to seeing where this goes.

---

### Post by gzy on 2008-03-19
> **Depressed Man said:**
> 
You'd need iTunes if you have a modern iPod. :P

I have a 6th gen classic (a1238) and loading it with mp3s and movies with floola on ubuntu :)

---

### Post by quinnten83 on 2008-03-19
> **DarthTibault said:**
> Obviously you're missing the ImageFont module, a few posts up justsomedude said that installing python-imaging did the trick, so try that.


You have to download the source. You won't have to compile anything as it's written in Python.

This should install everything::
```
svn checkout http://rhythmboxcoverflow.googlecode.com/svn/trunk/ ~/.gnome2/rhythmbox/plugins/rhythmboxcoverflow
```

When I try the svn command above it installs well, but when I try to select the plugin i get an error msg that the plugin could not be loaded.
I actually also manually created the folder and added the code, and I got the same error.

EDIT: It's worth noting that I didn't have a folder called "plugins" and that that had to be created manually.
The other plugins are not placed inside this folder. When I place the rythmboxcoverflow folder in the rhythmbox root, I can't see the coverflow plugin.
This might need some testing, I would definitely be willing to give a hand here (since i can't program for $h17).

---

### Post by mderezynski on 2008-04-02
Hey!

I'm porting the plugin to our own player, MPX ([http://mpx.backtrace.info](http://mpx.backtrace.info)) (The player itself is work in progress!)
.

So far i can basically load it, and i've replaced the cover loading code with our own interfaces, but when starting the plugin i get this error from Python:

```
File "/usr/local/share/mpx/scripts/rhythmboxcoverflow/flow_widget.py", line 111, in on_configure_event
    gldrawable.gl_begin(glcontext)     
AttributeError: 'NoneType' object has no attribute 'gl_begin'
Traceback (most recent call last):
  File "/usr/local/share/mpx/scripts/rhythmboxcoverflow/flow_widget.py", line 127, in on_realize
    if not gldrawable.gl_begin(glcontext):
AttributeError: 'NoneType' object has no attribute 'gl_begin'
```

It seems the GL widget can not create a gldrawable, but i don't really know why; i think it's being added to the main GUI just like in RB... i would really like to make this work but i don't know what's wrong.. Plz help!

Milosz

---

### Post by olavjunior on 2008-04-06
> **quinnten83 said:**
> When I try the svn command above it installs well, but when I try to select the plugin i get an error msg that the plugin could not be loaded.
I actually also manually created the folder and added the code, and I got the same error.

EDIT: It's worth noting that I didn't have a folder called "plugins" and that that had to be created manually.
The other plugins are not placed inside this folder. When I place the rythmboxcoverflow folder in the rhythmbox root, I can't see the coverflow plugin.
This might need some testing, I would definitely be willing to give a hand here (since i can't program for $h17).

You're prob. missing the python dependencies. 
python,
gtkglext1
gtkglext1-python
python-opengl
python-imaging

I also agree that scrolling the album collection is a must. For now this plugin doesn't do much, but thanks for the great start! I've been missing thisl. Also would like if it could be scaled and launched full screen

---

### Post by quinnten83 on 2008-04-07
well, i was missing python imaging and python-opengl, the others i wasn't.
I will try again and see if it works now.

---

### Post by quinnten83 on 2008-04-07
So, I installed from svn.
And it works, sorta.
It's very buggy though.
the problems and issues I have with it are as follow:
- the pictures of the covers are very small
- the coverflow isn't rendered right, sometimes I lose the interface
- for every song in an album, the cover is displayed, so it doesn't group all the  
  songs for one album.

having said that, this Idea is AWESOME! (sure it's been done before, but who cares?).
And rhythmbox itself is quite young, so errors are to be expected.
Well done and keep developing.

---

### Post by nilsja on 2008-04-29
i would love this feature so much! if there is any way to help you as an non programmer, let me know it. i mean by testing or sending pizza or coffee...

please, make coverflow possible in rhythmbox, that would be such great.

thanks,

nils

---

### Post by b3n87 on 2008-05-04
Im using the plugin, its awesome!
the only down side is that it doesnt update the cover art work when RB downloads the covers for new songs!

apart from that its awesome!!

---

### Post by sceo on 2008-05-16
I just wanted to say Kudos to this development effort.  This thing is going to be mega awesome when all the features are implemented.  It's a little screwy for me (I'm running compiz on an Intel 800 so I think it's that, actually, and not your plugin), but I'm getting a new video card soon and I bet there will be much improvement.

On Hardy in Synaptic you need libgtkglext1 (not just 'gtkglext1' as some other posts mention).

Is there somewhere I can keep up with the development, or should I just svn checkout every few weeks?

---

### Post by olavjunior on 2008-05-20
What's up with the dev? Is it stopped?

---

### Post by quinnten83 on 2008-05-20
> **olavjunior said:**
> What's up with the dev? Is it stopped?

I dunno...
who do we have to threaten to get this to work stablelike and proper?
i'm not adverse to use extreme violence...

---

### Post by b3n87 on 2008-05-20
ive been playing with it; trying to get it to show only one cover of each album, but my python skills are non-existent if not, zero.

---

### Post by bwiklak on 2008-06-05
We are having end-of-term examinations now :)
And response was not very big.

We can get back to work in 2-3 weeks but we would like to get some kind of wish-list from you.

If this plugin is really needed please write.

Bartek & Grzes

---

### Post by Redrazor39 on 2008-06-05
Cool! There's something called hardy-sparkle that's just like that but it looks a little different from coverflow.

I don't think we should copy apple completely. At least make the coverflow look different. Instead of a row of tilted albums, make two stacks of albums and when you hit the arrow keys one flips up from the stack and the one that was there before flips back to the other stack. I think that would be better, otherwise mac lovers would call us cheap copiers of their "Oh so mighty OS X".

---

### Post by shadowh511 on 2008-06-06
I would honestly pay for a stable coverflow in rhythmbox

---

### Post by quinnten83 on 2008-06-06
Noted, 
I will create a list of wishes and put it on the forums.
if you have a launchpad account thingie let us know.

---

### Post by brian g on 2008-06-06
> **shadowh511 said:**
> i Would Honestly Pay For A Stable Coverflow In Rhythmbox

+1

---

### Post by QwUo173Hy on 2008-06-07
I would definitely use it if it was available in package format. I would also submit bug reports / feature requests. But as I said earlier, for me it would need to be a usable interface for my music collection.

There's  a program called Elisa which has a coverflow implementation, but it's not quite polished yet. If you browse quickly for example the covers are shown as blank. They have a launchpad account and a homepage [http://elisa.fluendo.com/](http://elisa.fluendo.com/)

---

### Post by _DD_ on 2008-06-07
> **jarlath said:**
> If you browse quickly for example the covers are shown as blank./[/url]

Bah, happens in the real thing too. When I've used coverflow in iTunes it always seems laggy the first time you scroll through quickly while it fails to keep up with loading them to RAM, but once they're off the drive and into the memory then it becomes smooth.

That's an idea. I wonder if you could do a kind of prefetch/defrag thing where it blocks all the cover art in one lump on the drive so it can just do a continuous read and not have to jump. Maybe a long way off seeing as the actual cover flow isn't fully implemented yet, but might be an idea to speed things up in the future.

---

### Post by olavjunior on 2008-06-11
Would be nice with a full-screen experience, like a party view. Or that it would cover the whole browser-view. 

I really like the apple flow layout...

---

### Post by cozmicharlie on 2008-07-23
Thanks so much for all the hard work you have put into this.  It would really be great to get this functional.  If I knew how to code I would help.

I installed cover flow and it shows up in RB - but, all I see are the gnome footprint images.  I have the cover art in the folders (they show up in RB). I copied and pasted the cover art to the ~/.gnome/rythmbox/plugins/rythmbocoverflow folder (the files are just named cover.png - I only have 1 cover in the folder).  I also added the cover in the tags but still no cover image in coverflow on RB.  All I see are the gnome footprint images.

Also, I would agree with those that have suggested browsing capability.  That would be great.

Thanks again

---

### Post by conorsulli on 2008-07-29
Very Very good work! I hope you make good progress with this! And could I suggest the ability to integrate it into the actual player window? Kind of like the options in the "visualization" feature, of coarse its still early days yet.

Good luck!

---

### Post by crhylove on 2008-08-02
This looks promising.  Can I have this plugin with ProjectM pulsating in the background on one side of my compiz cube?  Thanks in advance.

rhY

---

### Post by conorsulli on 2008-10-04
Hey could I mension that there is a feature like this fully working for songbird-linux already, maybe the guy could help you out? I dont know the ins and outs of this, but It would be worth trying to port some if his code if he would let you!

---

### Post by quinnten83 on 2008-10-10
To the original poster:
is development still ongoing?

---

### Post by Elric27 on 2008-12-25
After trying many audio players on gnome and/or mpd, I have to say rhythmbox is the most complete of all,  awesome. However, it is this coverflow Ive been missing hte most, and the fact that RB only shows what's playing cover, unlike ario, bluemindo, or listen. Anyway, keep up the work please. Just say if it's dropped or not.
Cheers for the efforts

---

### Post by SnakeArtworX on 2009-01-11
I would like to see CoverFlow in Rhythmbox soon. I'm "mac-geek" and ubuntu user. I'm using the 2nd. generation iPod nano (4Gb) and it works perfect with Rhythmbox, but I think that RB should have a better visualization plugins, CoverFlow and Video podcasts support. The most comfortable situation would be, when apple will decide to create Linux port of iTunes. Until it happens, RB is in my opinion "iTunes for Linux".

---

### Post by lubosz on 2009-01-25
[http://code.google.com/p/rhythmboxcoverflow/](http://code.google.com/p/rhythmboxcoverflow/)

---

### Post by lordcoste on 2009-03-25
I have seen on the project page that the last update was on October 2008, so I have decided to work on the code. :guitar:

Here is what I have done so far:
[LIST]
[*]adapted it to work with the last version of Rhythmbox (now shows again covers and not only gnome's symbols).
[*]now shows one cover per album and not one per song
[*]changed a little the effect, there is more space between covers.
[*]also the covers are bigger than in the original version
[*]implemented mouse control:[LIST]
[*]one click to select a cover and animate to it
[*]a second click on the selected cover to play the first song of that album
[/LIST]
[/LIST]

[Here is a video]("http://www.youtube.com/watch?v=xlPMu8gncfY")

There isn't a download yet, this is my first python program so I have to test it before publish, I must also ask Grzes Furga if it's ok for him if I public this or if he's still working on his version.

bye ;-)

---

### Post by pt123 on 2009-03-25
Great news, I doubt if you need his permission if it is open sourced. I doubt if he is working on it either, it has been so long.

---

### Post by racoq on 2009-03-25
The Video looks promising!

Keep the good work mate! ;)




> **lordcoste said:**
> I have seen on the project page that the last update was on October 2008, so I have decided to work on the code. :guitar:

Here is what I have done so far:
[LIST]
[*]adapted it to work with the last version of Rhythmbox (now shows again covers and not only gnome's symbols).
[*]now shows one cover per album and not one per song
[*]changed a little the effect, there is more space between covers.
[*]also the covers are bigger than in the original version
[*]implemented mouse control:[LIST]
[*]one click to select a cover and animate to it
[*]a second click on the selected cover to play the first song of that album
[/LIST]
[/LIST]

[Here is a video]("http://www.youtube.com/watch?v=xlPMu8gncfY")

There isn't a download yet, this is my first python program so I have to test it before publish, I must also ask Grzes Furga if it's ok for him if I public this or if he's still working on his version.

bye ;-)

---

### Post by QwUo173Hy on 2009-03-26
Wow, that does look good. Thanks for this!

Is this version downloadable yet?

---

### Post by dalailama333 on 2009-04-04
Wow! I'm waiting for any downloadable plugin!! Keep on the good work!!

---

### Post by TheWitchdoktor on 2009-05-08
I Can't wait! Good luck man!

---

### Post by AndThenWhat on 2009-05-11
This is the plugin I have been waiting for!  Thanks for working on this!!

Keep us updated on the progress, as it seems like it is nearing completion or at least a usable state.

---

### Post by pt123 on 2009-05-11
lordcoste has made 1 post in the forum, so either project is dead or a hoax, why do other posters keep bumping this thread

---

### Post by fillintheblanks on 2009-05-31
> svn checkout [http://rhythmboxcoverflow.googlecode.com/svn/trunk/](http://rhythmboxcoverflow.googlecode.com/svn/trunk/) rhythmboxcoverflow


Doesn't want to accept mouse input events on mine. but so far so good, 

looks pretty promising! :)

---

### Post by manuw2009 on 2010-01-25
Hi guys,

Slightly off topic, but as the cover flow project seems to be stalled,  this is just to let you know I posted recently on my update of a nice cover grid view :
[INDENT][http://ubuntuforums.org/showthread.php?t=1381198](http://ubuntuforums.org/showthread.php?t=1381198)
[/INDENT]

---

### Post by nilsja on 2010-01-25
i solved it by switching to [http://getsongbird.com/](http://getsongbird.com/)

---

### Post by pt123 on 2010-01-25
manuw2009 nicw work, I haven't tried it yet but you are better off posting about it in the community cafe section of this forum
[http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)

 and or in the dev. programming section 
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

so this plugin can be incorporated in the default package for Rhythmbox.

A readme file on how to install would be helpful.

---

### Post by afrodeity on 2010-03-07
Nothing to download at google code? Is the project dormant?

---

### Post by ctrlmd on 2010-03-07
i saw the video it's taking the full screen view in order to show the cover flow 
what if i don't want to see the artist/album menus and i want to see 
the cover flow and the a songs list of each album ? 

still clutterflow on banshee better
[http://www.youtube.com/watch?v=fItEpHSOTHw](http://www.youtube.com/watch?v=fItEpHSOTHw)

---

### Post by afrodeity on 2010-03-07
Why are the Rythmbox plugins so lame? Thought there would a lot more development around this application?

---

### Post by manuw2009 on 2010-05-19
Hi guys,

I eventually tweaked the old rhythmbox version...
This is just a very first step towards a working coverflow
Still missing :
1/ proper way to retrieve the album art (here reading the album art cache directory)
2/ working interactions (click & double click seem to work but not precise enough regarding the album width : double click on central album should play the album, click left or right should "flow" to next/previous album)
3/ looking for a way to enlarge the flow widget height....

---

### Post by Excedio on 2010-05-19
> **manuw2009 said:**
> Hi guys,
 
I eventually tweaked the old rhythmbox version...
This is just a very first step towards a working coverflow
Still missing :
1/ proper way to retrieve the album art (here reading the album art cache directory)
2/ working interactions (click & double click seem to work but not precise enough regarding the album width : double click on central album should play the album, click left or right should "flow" to next/previous album)
3/ looking for a way to enlarge the flow widget height....
 
Trying to use this but getting an error message.
 
> **Plugin Error**
 
Unable to activate plugin Art Flow

---

### Post by manuw2009 on 2010-05-19
Hi
you're probably missing some dependancies...running rhythmbox from the console with debug traces will help : rhythmbox -d

---

### Post by afrodeity on 2010-05-19
I've placed it in .gnome2/rythmbox/plugins now what?

---

### Post by Excedio on 2010-05-19
> **manuw2009 said:**
> Hi
you're probably missing some dependancies...running rhythmbox from the console with debug traces will help : rhythmbox -d

I ran the code and got no errors on the initial loading of the program. However, when I try to activate the plugin, I get this error:
```
File "/home/excedio/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/__init__.py", line 25, in <module>
    from flow_widget import CoverFlowWidget
  File "/home/excedio/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/flow_widget.py", line 28, in <module>
    import gtk.gtkgl        
ImportError: No module named gtkgl

(rhythmbox:2625): Rhythmbox-WARNING **: Could not load plugin artflow

(23:54:42) [0xa85040] [rb_python_module_finalize] rb-python-module.c:427: Finalizing python module (null)

(rhythmbox:2625): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Art flow'
```

---

### Post by Excedio on 2010-05-19
> **afrodeity said:**
> I've placed it in .gnome2/rythmbox/plugins now what?

Restart Rhythmbox. Then go to Edit > Plugins. Check Art Flow.

---

### Post by afrodeity on 2010-05-20
Nice work. Its a great start to producing a working coverflow plugin. At the moment it just shows generic file/icon. Would love to showcase this on U8UNTU eLXER when its ready, maybe a preview for my readers?

---

### Post by afrodeity on 2010-05-25
Been debugging my xsession since upgrading to Lucid. Found some interesting warning/error linked to the plugin:

```
(evolution-alarm-notify:2628): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running...
Traceback (most recent call last):
  File "/home/afrodeity/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/__init__.py", line 100, in source_changed
    self.flow_widget.load_covers(songs)
  File "/home/afrodeity/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/flow_widget.py", line 93, in load_covers
    self.engine.load_covers(songs)
AttributeError: 'NoneType' object has no attribute 'load_covers'
Traceback (most recent call last):
  File "/home/afrodeity/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/__init__.py", line 100, in source_changed
    self.flow_widget.load_covers(songs)
  File "/home/afrodeity/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/flow_widget.py", line 93, in load_covers
    self.engine.load_covers(songs)
AttributeError: 'NoneType' object has no attribute 'load_covers'
[Debug 14:06:22.539] Acquiring org.freedesktop.DBus session instance
[Debug 14:06:22.547] Starting org.bansheeproject.CollectionIndexer
Traceback (most recent call last):
  File "/home/afrodeity/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/__init__.py", line 100, in source_changed
    self.flow_widget.load_covers(songs)
  File "/home/afrodeity/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/flow_widget.py", line 93, in load_covers
    self.engine.load_covers(songs)
AttributeError: 'NoneType' object has no attribute 'load_covers'

```

---

### Post by manuw2009 on 2010-05-28
Hi guys,

Does anyone know how to superimpose a few icons with the current opengl flow widget ?
I have been trying things but without success...(like adding a child gtk.Image)
I'd like to add some skip to last/first cover and maybe a search widget

---

### Post by kapcom01 on 2010-06-01
> **Excedio said:**
> I ran the code and got no errors on the initial loading of the program. However, when I try to activate the plugin, I get this error:
```
File "/home/excedio/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/__init__.py", line 25, in <module>
    from flow_widget import CoverFlowWidget
  File "/home/excedio/.gnome2/rhythmbox/plugins/rhythmboxcoverflow/artflow/flow_widget.py", line 28, in <module>
    import gtk.gtkgl        
ImportError: No module named gtkgl

(rhythmbox:2625): Rhythmbox-WARNING **: Could not load plugin artflow

(23:54:42) [0xa85040] [rb_python_module_finalize] rb-python-module.c:427: Finalizing python module (null)

(rhythmbox:2625): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Art flow'
```

go to synaptic and search for **python gtkgl**. In my Ubuntu 10.04 found the package **python-gtkglext1**. Install the package and it will work.

---

### Post by Excedio on 2010-06-01
> **kapcom01 said:**
> go to synaptic and search for **python gtkgl**. In my Ubuntu 10.04 found the package **python-gtkglext1**. Install the package and it will work.

Awesome! This worked for me. However...I'm not getting any album art. Now to figure that out ;-)

---

### Post by kapcom01 on 2010-06-01
> **Excedio said:**
> Awesome! This worked for me. However...I'm not getting any album art. Now to figure that out ;-)

As i read in line 55 of flow_engine.py file:
```
self._cover_dir = "%s/.cache/rhythmbox/covers/" % os.getenv("HOME")
``` it seems that it dispays covers that are in your /home/.cache/rhythmbox/covers/ folder. I think this is the place where the covers fetched from the internet (last.fm) are saved. So if have disabled the cover plugin then you will not see anything on coverflow. Enable it by going Edit>Addons>cover (or something like that.. im in greek UI..) 

I think its easy to modify this and make it possible to look at other folders too. Lets see what manuw2009 says.

---

### Post by yamfox on 2010-06-01
[IMG]http://img338.imageshack.us/img338/7065/yesqs.jpg[/IMG]

---

### Post by manuw2009 on 2010-06-02
Glad you like it...;)
I think it still deserves some polishing i.e. add widgets to skip to first/last album, fast forward/backward.
Does anyone know how to achieve this ?

---

### Post by kapcom01 on 2010-06-02
I have some problems. I think we must first solve the problems and then we can improve it.

1)Some albums wont play on double click. I havent found the cause yet.

2)The covers source must change so it can show covers that are not on /home/.cache/rhythmbox/covers/. How does rhytmbox do it?

3)I cant go directly to an album by clicking on it. The single click just goes to next or previous on the coverflow.

I will try to help with my little knowledge..

---

### Post by just_nadir on 2010-07-06
this project that you are working on ... it's great ... I just want to ask are you still working on it ... I like it ... hope you will release new testing cover flow ... this one is amazing for now ...
THANK YOU !

---

### Post by just_nadir on 2010-07-07
I want to ask you something ... you already have code for cover flow ... and when it be done ... could you make this cover flow but for nautilus or nautilus elementary ???

---

### Post by manuw2009 on 2010-07-09
Hi,

Glad you like it !
Unfortunately, I'm quite stuck there (no time + poor python knowledge).
So I think I should upload my CF version to googlecode or something and maybe start a new thread to ask for contribution.
Nice improvements should be : small widgets below to skip to last/first track, improve song /album titles display, etc...

---

### Post by manuw2009 on 2010-07-13
Hi again,

This is to let you know that I have uploaded the project to google.code there :
[http://code.google.com/p/rhythmbox-coverflow-plugin/](http://code.google.com/p/rhythmbox-coverflow-plugin/)
If anyone is willing to go on with the project, just let me know I'll add you as project member...;)
See ya

---

### Post by nilsja on 2010-07-13
hi manuw2009,

great! but shouldn't the plugin be downloadable at [http://code.google.com/p/rhythmbox-coverflow-plugin/downloads/list](http://code.google.com/p/rhythmbox-coverflow-plugin/downloads/list)?

nils

---

### Post by manuw2009 on 2010-07-13
Well, I know...But I still need to learn how to populate the google.code download section ;)
You can still retrieve the plugin with :
svn checkout ***http***://rhythmbox-coverflow-plugin.googlecode.com/svn/trunk/  rhythmbox-coverflow-plugin

---

### Post by search66 on 2010-07-20
I've installed the plugin, but none of the artwork is showing. Any hints you could provide?  I've read about putting your album art into a specific folder... Is there an easy way to do this?  With thousands of albums; it would be quite a job!

:)

---

### Post by manuw2009 on 2010-07-21
> **search66 said:**
> I've installed the plugin, but none of the artwork is showing. Any hints you could provide?  I've read about putting your album art into a specific folder... Is there an easy way to do this?  With thousands of albums; it would be quite a job!

:)

Could you please try to change the following line in flow_engine.py :
*self._cover_dir = "%s/.cache/rhythmbox/covers/" % os.getenv("HOME")*
into :
*self._cover_dir = "%s/**[COLOR=Red].gnome2[/COLOR]**/rhythmbox/covers/" % os.getenv("HOME")*

and tell me if this solves your problem ?

Another option would be to activate the official cover display plugin (as this is the one populating the cache I think)

---

### Post by search66 on 2010-07-21
Thanks for the response, but sadly no... It didn't fix it.  When I enable the officer 'cover art' plugin, I have no problems viewing the album art (within that plugin).. However, any other plugin that uses album art (like Desktop Art or AWN progress % art) displays nothing.

:(

---

### Post by search66 on 2010-07-21
> **search66 said:**
> Thanks for the response, but sadly no... It didn't fix it.  When I enable the officer 'cover art' plugin, I have no problems viewing the album art (within that plugin).. However, any other plugin that uses album art (like Desktop Art or AWN progress % art) displays nothing.

:(

I just found something very odd... When playing a song/track... If I have the "Cover Art" plugin enabled; it will show the album fine (within it's own plugin)... However, it won't save to ~/cache/rhythmbox/covers... BUT... if I turn the plugin off and then on; it DOES save a copy of the album art... Thats the only way I've found to get the album art to save... Anyone have a clue?  I think once I fix that, I'm golden.

---

### Post by n1k0z on 2011-10-27
Hi,

Thank you for this wonderful plugin! From what I have seen in the images is a complete boost for Rhythmbox.

However, I was not able to see the plugin. When I activate it, I see no change in the rhythmbox GUI!

Would you happen to have any clues?

Thank you!
Nikos

---

