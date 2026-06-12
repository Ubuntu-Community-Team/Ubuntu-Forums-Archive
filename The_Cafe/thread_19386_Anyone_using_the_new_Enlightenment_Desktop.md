---
title: "Anyone using the new Enlightenment Desktop?"
date: 2005-03-11
forum: The Cafe
---

### Post by ixus_123 on 2005-03-11
It just looks swish.  I for one will be trying it out in the next few days

It has been been slashdotted so don't be surprized if the video links dont work.

[video 1](http://www.rasterman.com/files/e17_movie-02.avi) 

[video 2](http://www.rasterman.com/files/e17_movie-03.avi) 

The detail:
[http://enlightenment.org/index.php?session=b67d90ce71&id=9&select=ePortal](http://enlightenment.org/index.php?session=b67d90ce71&id=9&select=ePortal) 

It's got to be compiled from source, I think there's a howto on site.  I probably wont get round to installing untill the middle of next week

---

### Post by paul cooke on 2005-03-11
oh my deity... that'll shut the OSX crowd up... and all those who are claiming that MS's Avalon is the next best thing as well...

---

### Post by jdodson on 2005-03-11
wow, it has come a long way.   good for them, i think that is a pretty nice setup.

---

### Post by TravisNewman on 2005-03-11
OK if that's functional... wow. 

How do they get the moving desktop?

---

### Post by Quest-Master on 2005-03-11
That's quite amazing.

Now, someone make us a .deb for it. :D

---

### Post by bored2k on 2005-03-11
[QUOTE=Quest-Master]That's quite amazing.

Now, someone make us a .deb for it. :D[/QUOTE]
 I wonder how much is the computer's performance compromised by all that eye-candy ...

---

### Post by tim1 on 2005-03-11
[QUOTE=Quest-Master]That's quite amazing.

Now, someone make us a .deb for it. :D[/QUOTE]

I installed it from .debs a few days ago. Just use the search function.

It won't replace your current desktop though, it's still not mature enough.

But its style rock!  :grin: Just this intro animation  ... whoaa

greets, tim

---

### Post by bored2k on 2005-03-11
[QUOTE=tim1]I installed it from .debs a few days ago. Just use the search function.

It won't replace your current desktop though, it's still not mature enough.

But its style rock!  :grin: Just this intro animation  ... whoaa

greets, tim[/QUOTE]
 Intro animation? you mean when the desktop opens like one of those futuristic doors [middle to down/up]? Pretty cool.

---

### Post by darkoptix on 2005-03-11
This looks cool...

---

### Post by Rule on 2005-03-12
THATS WICKED!!!!!!!!!!!!!!!!!!!!! I WANT I WANT!!!

 :mrgreen:  :mrgreen:  :mrgreen:

---

### Post by bored2k on 2005-03-12
[QUOTE=Rule]THATS WICKED!!!!!!!!!!!!!!!!!!!!! I WANT I WANT!!!

 :mrgreen:  :mrgreen:  :mrgreen:[/QUOTE]
 Bear in mind Enlightenment has a more or less complicated learning curve....

---

### Post by ixus_123 on 2005-03-12
[QUOTE=tim1]I installed it from .debs a few days ago. Just use the search function.

It won't replace your current desktop though, it's still not mature enough.

But its style rock!  :grin: Just this intro animation  ... whoaa

greets, tim[/QUOTE]
Really?  Are you sure it was DR17 and not DR16.  I thought it was so new it was only available as source.  DR17 is supposed to be a significant step up from 16, if you know where there is a deb I'd be gratefull for a link please

---

### Post by Rule on 2005-03-12
[QUOTE=bored2k]Bear in mind Enlightenment has a more or less complicated learning curve....[/QUOTE]

thats ok, if I can figure out linux I can figure out Enlightment  :mrgreen:

---

### Post by tim1 on 2005-03-12
[QUOTE=ixus_123]Really?  Are you sure it was DR17 and not DR16.  I thought it was so new it was only available as source.  DR17 is supposed to be a significant step up from 16, if you know where there is a deb I'd be gratefull for a link please[/QUOTE]

Yes I'm pretty sure.

debs are here:
```
deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/
```

you have to add the following lines to your /etc/apt/preferences:
```
Package: enlightenment
Pin: version 0.17.0_pre10*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.17.0_pre10*
Pin-Priority: 999
```

you have to create a .desktop file if you wish to login with gdm in /usr/share/xsessions like this:

```
[Desktop Entry]
Encoding=UTF-8
Name=e17
Comment=
Exec=enlightenment
Icon=
Type=Application

```

greets, tim

---

### Post by bored2k on 2005-03-12
[QUOTE=tim1]Yes I'm pretty sure.

debs are here:
```
deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/
```

you have to add the following lines to your /etc/apt/preferences:
```
Package: enlightenment
Pin: version 0.17.0_pre10*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.17.0_pre10*
Pin-Priority: 999
```

you have to create a .desktop file if you wish to login with gdm in /usr/share/xsessions like this:

```
[Desktop Entry]
Encoding=UTF-8
Name=e17
Comment=
Exec=enlightenment
Icon=
Type=Application

```

greets, tim[/QUOTE]
 Thanks, I'll put Enlightenment to the test in a moment ... 
Can't wait, last time I tried Enlightenment I couldn't find a way to do anything. Now that I remember ... I was just starting to use Linux . No wonder :roll:

---

### Post by paul cooke on 2005-03-12
can I have E17 alongside E16? and what's that bit in the "preferences" do then?

---

### Post by Rule on 2005-03-12
I keep getting this error in synaptic 
enlightenment:
 Depends: libe but it is not going to be installed
 Depends: enlightenment-data but it is not going to be installed
 Depends: libimlib2 but it is not going to be installed

---

### Post by bored2k on 2005-03-12
[QUOTE=Rule]I keep getting this error in synaptic 
enlightenment:
 Depends: libe but it is not going to be installed
 Depends: enlightenment-data but it is not going to be installed
 Depends: libimlib2 but it is not going to be installed[/QUOTE]
 It installed here, it just wouldnt run.
When i select e17 on gdm it opened up gnome.

---

### Post by Zundfolge on 2005-03-12
So how much horsepower does all this take?

Clearly I won't be running this on my PIII 450  ;-)

---

### Post by bobmitch on 2005-03-12
Got it running here no problem.  It is very fast, and very slick - though clearly still pre-alpha.

The flame module doesn`t appear in the menus like the videos I have seen, so I can`t get any of the cool animated background stuff working.

But hey, these drop-shadows are worth it. :D

[edit]  Got the flames and snow effect modules working.  
Just use:  **enlightenment_remote -module-load flame** 
Replace flame with snow for the pretty snowflakes. :)

---

### Post by kassetra on 2005-03-13
[QUOTE=bored2k]last time I tried Enlightenment I couldn't find a way to do anything. Now that I remember ... I was just starting to use Linux . No wonder :roll:[/QUOTE]

The last time I used enlightenment was DR 0.14 then DR 0.15... and then DR 0.16... I loved it.  I talked with the developers.  I created themes, I edited themes... I did bunches and bunches of stuff with it...  Some of it was kinda hard to do, especially in those days, but enlightenment was fun.  In fact, I made my enlightenment look EXACTLY like the sneak preview screenshots of OSX (yes, *before* it was released!) 

... then....  I wanted to do lots of other things and install other programs, and enlightenment just didn't support it, so I started breaking enlightenment in order to run the first Nautilus (and other stuffs)... heh.

So, now, I look at enlightenment and wonder if it will be the same way again.  Yeah, I'll stick with what I have now... maybe vmware test out enlightenment.  heh.

---

### Post by TravisNewman on 2005-03-13
I remember when Gnome used to come with Enlightenment as the Window Manager, then Sawfish, then/now Metacity/Nautilus

It actually seems like Enlightenment has LOST some functionality, but I think they're reworking a lot.

---

### Post by dizzie on 2005-03-14
DR 0.17 or Gnome 2.10 - Tough one... Gnome 2.10 is mature enough :) DR 0.17 aint, but its different (I like all the gadgets and anims and ..... <long list>)

I like em both, Gnome 2.10 is #1 though, i use DR 0.17 'coz its new and very different compared to Gnome/KDE/etc. etc. - "The eyecandy will slow down your PC" ... Well maybe, maybe not. I got a AMD 2400+ and a AMD 1800+ both with 512mb+ so i dont see an issue there (for me that is) - Dont know how DR 0.17 will run on lets say a K6-2/300 (let me know!)

If i want a minimalistic X, i would run Fluxbox/Openbox/Blackbox/<whatever>-box...

If i want a fullblown cpu/mem- demanding fm, i'd pick Gnome/KDE/DR 0.17

They say Gnome 2.10 is rock solid and DR 0.17 is unstable. Maybe true, but DR 0.17 hasnt crashed on my system yet, prolly wont do either :)

Just my 5 cent...

Regards!

---

### Post by bobmitch on 2005-03-14
[QUOTE=dizzie]

They say Gnome 2.10 is rock solid and DR 0.17 is unstable. Maybe true, but DR 0.17 hasnt crashed on my system yet, prolly wont do either :)

Just my 5 cent...

Regards![/QUOTE]

I haven`t had any stability issues either - but all my fonts render incorrectly in firefox (mostly just far too small) - and this is one of my primary apps.  Have you had any similar issues?

---

### Post by dizzie on 2005-03-14
[QUOTE=bobmitch]I haven`t had any stability issues either - but all my fonts render incorrectly in firefox (mostly just far too small) - and this is one of my primary apps.  Have you had any similar issues?[/QUOTE]

Not at all, are you using TT fonts? - Funny that when using Gnome fonts are small here, but CTRL + 'plus/minus' will in/de-crease, font size, so not really an issue either.

What i need/miss, is a config editor/builder, so i can make a massive rightbutton menu (old fluxbox habbit, i cant help it ;o )

Regards...

---

### Post by TravisNewman on 2005-03-14
try running gnome-settings-daemon
That cleared up my font problems in e17

---

### Post by bobmitch on 2005-03-14
Thanks for the tips - I`ll put them into practice when I get home from work. :)

---

### Post by bobmitch on 2005-03-14
[QUOTE=panickedthumb]try running gnome-settings-daemon
That cleared up my font problems in e17[/QUOTE]

Cheers thumb-meister - that did the trick. :)
This version of enlightenment, even in the state it's in, is a very slick and cool desktop.  Not sure I agree with their use of binary .eet files, but it's a price I`ll gladly pay for this kind of eye-candy.

---

### Post by oddabe19 on 2005-03-14
[QUOTE=bobmitch]Cheers thumb-meister - that did the trick. :)
This version of enlightenment, even in the state it's in, is a very slick and cool desktop.  Not sure I agree with their use of binary .eet files, but it's a price I`ll gladly pay for this kind of eye-candy.[/QUOTE]
 very nice!!!

but...
no back grounds? no changing of theme? no way to add programs?

still some more work to go...
actually it's quite stable and solid as it stands now.

---

### Post by bobmitch on 2005-03-14
[QUOTE=oddabe19]very nice!!!

but...
no back grounds? no changing of theme? no way to add programs?

still some more work to go...
actually it's quite stable and solid as it stands now.[/QUOTE]

Changing of backgrounds is possible.  See [here](http://lude.net/edocs/configuration.htm#config_background) .

It's a pain, yes, but someone with sufficient skill should be able to wrap a gui round it.

---

### Post by jdong on 2005-03-14
Oh boy, I sense a backport request coming....

---

### Post by bobmitch on 2005-03-14
[QUOTE=jdong]Oh boy, I sense a backport request coming....[/QUOTE]

Well... while you're here....

;)

---

### Post by bobmitch on 2005-03-14
Ok, I hate to post such big and forum breaking pics, but I thought you might like to see my current e17 'theme'.

This has the flame module running with the plasma preset (all animated naturally) and animated falling snowflakes over the desktop background.

:)

---

### Post by bored2k on 2005-03-14
[QUOTE=bobmitch]Ok, I hate to post such big and forum breaking pics, but I thought you might like to see my current e17 'theme'.

This has the flame module running with the plasma preset (all animated naturally) and animated falling snowflakes over the desktop background.

:)[/QUOTE]

How big is the performance "hit" with all those effects ? [a comparation would be great]

---

### Post by HungSquirrel on 2005-03-14
Is this done by OpenGL, and if so, can I accelerate it somehow using the nvidia drivers?

Edit: the environment is surprisingly snappy and lag-free.  It's a shame it is unusable (for me) for other reasons, namely not being able to get esd to behave for some reason, not knowing how to turn off the god awful sloppy focus, and not having an easy method of editing the menu.

My props to the devs, though, for making these effects really fly!

---

### Post by telmo on 2005-03-15
Ok... I WANT IT NOW!!!!!!!! :D

How about a howto here? ;)

---

### Post by bobmitch on 2005-03-15
I`ll knock together a howto when I get home from work tonight for those who are interested.

As for the window focus, I believe there is no way of changing that at present.

I think it's possible to change the contents of the dock/menus using one of the command line tools, which I`ll hopefully include in the howto.

I`m finding their choice of binary config files more and more puzzling.  Surely loading/parsing time is not that big an issue these days?  Especially for simple text files - I mean I`d understand if the config files were going to be huuuuge, but most of them will just be a couple of hundred lines.  

I mean, if linux isn`t about enjoying editing a good ol' text file, I don`t know what it *is* about.   ;)

As for performance, with the eye candy all turned on, firefox is as snappy as ever.  It looks like the processes for the eye-candy modules have been given low priorities - so they will slow down when things get busy.   Bear in mind, I`m running this on pretty big desktop, and it`s all running in software (there are opengl switches for some modules, but they are highly experimental at the moment) - but the slowdown is, for example, nowhere near using composite on my ati.  Composite on nvidia may be a different kettle of fish due to the hardware accel option, but for ati users wanting drop shadows, e17 is the only option at the moment.

---

### Post by telmo on 2005-03-15
Right On!!! :d

---

### Post by bobmitch on 2005-03-15
[CENTER]**QUICK AND DIRTY E17 HOWTO**[/CENTER]


Add the following line to **/etc/apt/sources.list**:

```
deb http://soulmachine.net/debian unstable/
``` 

Add the following lines to **/etc/apt/preferences**
(If this file doesn`t exist, create it.)
(Don't know how necessary it is, but it worked for me.) :)

```
Package: enlightenment
Pin: version 0.17.0_pre10*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.17.0_pre10*
Pin-Priority: 999
``` 

Create a file called **e17.deskto**p in **/usr/share/xsessions/**
Add the following lines to this file:

```
[Desktop Entry]
Encoding=UTF-8
Name=e17
Comment=
Exec=enlightenment
Icon=
Type=Application
``` 

Using synaptic, install the following packages:

```
enlightenment		0.17.0_pre10-0cvs20050216
enlightenment-data	0.17.0_pre10-0cvs20050216
eutils			0.0.1-0cvs20050215
``` 

E17 should now be available as a session from the gnome login screen. :)

Once in E17, the following commands are useful:

```
**enlightenment_remote -module-load flame**	- *Loads the flame module*. :D
**enlightenment_remote -module-load snow**	- *Loads the snow module*.
**e17setroot -s <imagename>**		- *Loads image, and scales to backdrop*.
(type e17setroot on it's own for other options)
``` 

Once you have loaded a few backgrounds to test with, you can select them easily using the *emblem* E17 background selection tool, as all .eet files created with e17setroot are automatically stored in **$HOME/.e/e/background/**
(Just type **emblem** in the terminal)

[This](http://lude.net/edocs/configuration.htm) is a great resource.

Hope this helps, apologies for any errors. :D

---

### Post by crun on 2005-03-15
Amazing stuff. Your howto worked like a charm bobmitch. With the moving background (as in the first movie), flames and snow turned it all became somewhat sluggish (using Nvidia), though it didn't affect the apps running on top of it.

I also wonder about the binary config files - a strange choice for a Linux WM. It's very stable as far as I can tell and pretty fast, for such an early stage in development it's a great piece of work.

---

### Post by borisb on 2005-03-22
[QUOTE=tim1]I installed it from .debs a few days ago. Just use the search function.

It won't replace your current desktop though, it's still not mature enough.

But its style rock!  :grin: Just this intro animation  ... whoaa

greets, tim[/QUOTE]

Which repositories are you using ?
If i search for it synaptic only lists an older enlightment.

greets boris

---

### Post by rublind on 2005-03-22
... that is freakin' sweet.

---

### Post by bobmitch on 2005-03-22
[QUOTE=borisb]Which repositories are you using ?
If i search for it synaptic only lists an older enlightment.

greets boris[/QUOTE]

See my howto [here](http://www.ubuntuforums.org/showthread.php?t=20216)

---

### Post by poofyhairguy on 2005-03-22
Thanks for the howto. bobmitch. that is some flashy stuff.

---

### Post by fenwik on 2005-06-29
[QUOTE=bobmitch]See my howto [here](http://www.ubuntuforums.org/showthread.php?t=20216)[/QUOTE]
 Bobmitch: Your how to didn't help me. Synaptic only displays enlightenment version 0.16.6

---

### Post by sapo on 2005-06-29
This new elignment uses openGL or something? what about the performance?

---

