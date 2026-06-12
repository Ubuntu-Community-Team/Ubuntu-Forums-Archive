---
title: "Idea: Drop down terminal :D"
date: 2005-05-25
forum: The Cafe
---

### Post by sapo on 2005-05-25
I was in my smoke break when i suddenly had an idea  :grin: 

I was thinking about those trasparent terminal the some people uses as a desktop background... and the an idea come to my mind..

I dont know if it already exists (hope it exist) but it could be a very useful think..

To understand what i m talking about, click on the Search button here in the Ubuntuforums...

Saw how it came down? now...

Why not have a taskbar button, that when clicked pop down a 5 or 6 lines terminal (with no borders if possible).

I think it will be very useful, sometimes you want to edit a file or run some app.. then you click on the button, the terminal comes down (or up if in the bottom bar) you type the comands.. and then hide it again?

I dont know how to program in linux.. but i think that  a lot of ubuntu users here could do it (if it doesnt exist yet).

What do you think about it? i think it would be very very useful for me  :grin:



**###### SOLUTION -> THANX TO 23meg for the script #########**

First be sure to have eterm installed:

```

sudo apt-get install eterm

```

Now create a terminal.sh file and put the contents bellow:

```

#!/bin/bash
ps -e | grep Eterm
x=$?;
if [ $x -eq 1 ]; then
        Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 -f white **--geometry=95x10+280+20** --font-fx none 
else
        killall -9 Eterm
fi

```

Edit the --geometry to change the location where it will open...

I ll explain the geometry so people can make their own behave like it:

Where:
95 = width
10 = number of lines
280 = horizontal position
20 = vertical position

Save your file and type:

```

chmod +x terminal.sh

```


Now you just have to put a Shortcut pointing to it..

if you dont want it to be fully transparent change the shade=0 to shade=50 or shade=80

Now i just click it and it comes down.. here a screenshot  :grin:

[[IMG]http://img81.echo.cx/img81/1705/screenshot12jd.th.png[/IMG]](http://img81.echo.cx/my.php?image=screenshot12jd.png)

---

### Post by HungSquirrel on 2005-05-25
Sounds like a great idea to me.  If it can be implemented in a resource-efficient manner, I am all for it.

---

### Post by WildTangent on 2005-05-25
AVATAR THEIF!!!!!!!!!!!

i too agree with having a drop down terminal, itd be useful....

-Wild

---

### Post by sapo on 2005-05-25
[QUOTE=WildTangent]AVATAR THEIF!!!!!!!!!!!

i too agree with having a drop down terminal, itd be useful....

-Wild[/QUOTE]


you are the thief.. you joined the forum after me  :-# 

Btw.. if this kind of app still doesnt exist i hope somebody could think about programing it  :grin:

---

### Post by WildTangent on 2005-05-25
[QUOTE=sapo]you are the thief.. you joined the forum after me  :-# 

Btw.. if this kind of app still doesnt exist i hope somebody could think about programing it  :grin:[/QUOTE]
maybe so, but you could have set that avatar *after* joining :---) 

-Wild

---

### Post by sonny on 2005-05-25
I just read this and now I remenber those thousands of times when you only need to type 4 lines of code to get things done. It's a very good idea, I can't recall having seing something like it before, but it really should be one of those must have things in ubuntu; with gnomes (cuz kde just have too many eyecandy, one for gnome wouldn't hurt).

---

### Post by sapo on 2005-05-25
[QUOTE=sonny]I just read this and now I remenber those thousands of times when you only need to type 4 lines of code to get things done. It's a very good idea, I can't recall having seing something like it before, but it really should be one of those must have things in ubuntu; with gnomes (cuz kde just have too many eyecandy, one for gnome wouldn't hurt).[/QUOTE]


Thats the point...

Sometimes you just have to kill an app, or start esd, edit something umount a drive...

and you have to open a terminal to do it  ](*,)

---

### Post by Seth on 2005-05-25
[QUOTE=sonny]I just read this and now I remenber those thousands of times when you only need to type 4 lines of code to get things done. It's a very good idea, I can't recall having seing something like it before, but it really should be one of those must have things in ubuntu; with gnomes (cuz kde just have too many eyecandy, one for gnome wouldn't hurt).[/QUOTE]
 You could even have an Exposé-style shortcut, like F12 to drop down a little terminal from the top center of the screen. That'd be money.

---

### Post by sapo on 2005-05-25
[QUOTE=Seth]You could even have an Exposé-style shortcut, like F12 to drop down a little terminal from the top center of the screen. That'd be money.[/QUOTE]


nice idea :grin: 

I see that we could try starting a project to make a terminal like, with some customizations and tools, like staying on top, auto-hide after some time.

And now another idea.. it could be, isntead of a clickable button on the task bar...

hum.. i dont know how to explain it.. btw..

I used to use astonshell instead of explorer in windows... and when you moved the mouse to the left or right edge of the screen, a "notepad" showed up..

it could show up a terminal instead of the notepad ^^

---

### Post by sapo on 2005-05-25
[QUOTE=WildTangent]maybe so, but you could have set that avatar *after* joining :---) 

-Wild[/QUOTE]

A gift for you  :razz: 

[http://xgn.com.br/fabio/bebe/](http://xgn.com.br/fabio/bebe/)

I think i ll change my avatar to the "incoming" one..  :roll:

---

### Post by WildTangent on 2005-05-26
[QUOTE=sapo]A gift for you  :razz: 

[http://xgn.com.br/fabio/bebe/](http://xgn.com.br/fabio/bebe/)

I think i ll change my avatar to the "incoming" one..  :roll:[/QUOTE]
ROTFL! thats awesome, theyre so funny!

-Wild

---

### Post by sapo on 2005-05-26
Any volunteers to code it?  :roll: 

 :?

---

### Post by vague- on 2005-05-26
I remember seeing a terminal that "hid" itself off the top of the screen, and was activated in the same way as autohide toolbar.  It just ran there, I do not think it mattered which terminal.  However, I think it was done by the window manager.  If memory serves me correctly it was FVWM, one of the fairly recent versions.  I think FVWM can work with a Gnome desktop.

---

### Post by 23meg on 2005-05-26
i have Eterm set up to work more or less this way; it just "pops" left aligned rather than top (you could make it top by editing the geometry parameter of course), and you don't see a pretty animation of it sliding into place, but it works fine nevertheless. i have the following in an executable bash script:

```
#!/bin/bash
ps -e | grep Eterm
x=$?;
if [ $x -eq 1 ]; then
        Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 -f white --geometry=90x28+0+376 --font-fx none 
else
        killall -9 Eterm
fi


```

and i have a desktop launcher pointing to this script; you could have a panel one if you so prefer. this sets things up so that if Eterm isn't running, it's launched, with my preferences that you can see as command line parameters, and if it's running, it's terminated. so the launcher acts like a "toggle" button. you could put any application in place of Eterm in the script to make it act like this, in fact.

and i think i have to acknowledge **tread** who helped me set this up here.

---

### Post by sapo on 2005-05-26
> **23meg]i have Eterm set up to work more or less this way said:**
> ; then
        Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 -f white --geometry=90x28+0+376 --font-fx none 
else
        killall -9 Eterm
fi


```


and i have a desktop launcher pointing to this script; you could have a panel one if you so prefer. this sets things up so that if Eterm isn't running, it's launched, with my preferences that you can see as command line parameters, and if it's running, it's terminated. so the launcher acts like a "toggle" button. you could put any application in place of Eterm in the script to make it act like this, in fact.

and i think i have to acknowledge **tread** who helped me set this up here.

Nice.. i ll try it out  :grin:

---

### Post by jkka on 2005-05-26
You guys might wanna try out tilda

[http://tilda.sourceforge.net/](http://tilda.sourceforge.net/)

---

### Post by sapo on 2005-05-26
Man.. thanx a lot.. this is perfect!

I ll explain the geometry so people can make their own behave like it:

```

#!/bin/bash
ps -e | grep Eterm
x=$?;
if [ $x -eq 1 ]; then
        Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 -f white **--geometry=95x10+280+20** --font-fx none 
else
        killall -9 Eterm
fi

```

Where:
95 = width
10 = number of lines
280 = horizontal position
20 = vertical position

Now i just click it and it comes down.. here a screenshot  :grin:

[[IMG]http://img81.echo.cx/img81/1705/screenshot12jd.th.png[/IMG]](http://img81.echo.cx/my.php?image=screenshot12jd.png)

---

### Post by sapo on 2005-05-26
[QUOTE=jkka]You guys might wanna try out tilda

[http://tilda.sourceforge.net/](http://tilda.sourceforge.net/)[/QUOTE]

The 0.6 version didnt compile.. and the .deb one worked.. but i couldnt make it show up in the center of my screen  ](*,)

---

### Post by totalshredder on 2005-05-26
> **sapo]Man.. thanx a lot.. this is perfect!

I ll explain the geometry so people can make their own behave like it:

```

#!/bin/bash
ps -e | grep Eterm
x=$? said:**
> ; then
        Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 -f white **--geometry=95x10+280+20** --font-fx none 
else
        killall -9 Eterm
fi

```

Where:
95 = width
10 = number of lines
280 = horizontal position
20 = vertical position

Now i just click it and it comes down.. here a screenshot  :grin:

[[IMG]http://img81.echo.cx/img81/1705/screenshot12jd.th.png[/IMG]](http://img81.echo.cx/my.php?image=screenshot12jd.png)

What exactly do I do with that? I made a shell script and then stuck a launcher of it on the taskbar, but it either says permission denied, or when I try to run it from terminal, does nothing. 

Luke

---

### Post by sapo on 2005-05-26
[QUOTE=totalshredder]What exactly do I do with that? I made a shell script and then stuck a launcher of it on the taskbar, but it either says permission denied, or when I try to run it from terminal, does nothing. 

Luke[/QUOTE]


first you need eterm installed ;)

```

sudo apt-get install eterm

```

then you need to chmod +x to your script (just change terminal.sh to whatever is the name of your scritp)

```

chmod +x terminal.sh

```


i was thinking here to make a automated script to do it...

Somebody could tell me if its possible to a shell script to detect the screen resolution and open the terminal in the center of screen automaticaly?

it would be easier for newbies to make it work perfectly  :grin:

---

### Post by zaxer on 2005-05-26
Great work guys!

Ill give it a try but an auto script would be great :)

clap clap

---

### Post by totalshredder on 2005-05-26
[QUOTE=sapo]then you need to chmod +x to your script (just change terminal.sh to whatever is the name of your scritp)

```

chmod +x terminal.sh

```[/QUOTE]

Ahhh, thanks for that, I'm ridiculously stupid sometimes :)

Here's a screenshot of mine, it's a pretty sight, great for whatever needs are needed. I'm just NOT a fan of when something is transparent it shows the background instead of the window under it. Oh well, good stuff!!

Luke

---

### Post by sapo on 2005-05-26
[QUOTE=totalshredder]Ahhh, thanks for that, I'm ridiculously stupid sometimes :)

Here's a screenshot of mine, it's a pretty sight, great for whatever needs are needed. I'm just NOT a fan of when something is transparent it shows the background instead of the window under it. Oh well, good stuff!!

Luke[/QUOTE]


Try changing this:
```

--shade=0

```
To:
```

--shade=50

```
or
```

--shade=80

```

I m sure you will like it ;)

---

### Post by Moobert on 2005-05-26
theres also a quake style one:

[http://www.nemohackers.org/kuake.php](http://www.nemohackers.org/kuake.php)

---

### Post by totalshredder on 2005-05-26
> **sapo]Try changing this:
To:
```

--shade=50

```
I m sure you will like it  said:**
> 
Man, it was beautiful, but it took an extra 4 seconds to start up, so I had to it back to zero. Oh the woes of a celeron!! ;)

[QUOTE]theres also a quake style one:

[http://www.nemohackers.org/kuake.php](http://www.nemohackers.org/kuake.php) 
It looks pretty, but seeing most of us are in gnome, and not KDE...

Luke

---

### Post by sapo on 2005-05-26
[QUOTE=totalshredder]Man, it was beautiful, but it took an extra 4 seconds to start up, so I had to it back to zero. Oh the woes of a celeron!! ;)


Luke[/QUOTE]

hum... and if you want it black then.. just remove the --trans option  ;-)

---

### Post by Moobert on 2005-05-26
[QUOTE=totalshredder]
 
It looks pretty, but seeing most of us are in gnome, and not KDE...

[/QUOTE]

yeah seems to run using konsole... might need abit of a depancy. Use fluxbox myself, with similar gtk and qt app themes... I can pick and choose :)

---

### Post by 23meg on 2005-05-26
glad you all are enjoying it.. totalshredder: with that background you may want to make your Eterm font color black by specifying "black" with the -f parameter instead of "white".

---

### Post by trash on 2005-05-26
Great idea!
I still can't get Eterm running on my PPC so here's a commandline time saver for mac folks...

Command line, It's a panel app(right click on panel to add to panel) that puts a command line in your panel... kind of ugly as hell but it works.

---

### Post by 23meg on 2005-05-26
it has its use as a single-line app launcher, but when you're doing common tasks that require terminal output and feedback it won't do the job, unfortunately. alt+f2 does the same, yet doesn't look ugly or take panel space.

---

### Post by trash on 2005-05-26
[QUOTE=23meg]it has its use as a single-line app launcher, but when you're doing common tasks that require terminal output and feedback it won't do the job, unfortunately. alt+f2 does the same, yet doesn't look ugly or take panel space.[/QUOTE]

Ya it's basic for sure but still handy with the history and browse buttons,,, I'd much rather have Eterm but it's not meant to be yet.
I just created an 'autohide' panel with 'expand' deselected and maximum size(120pixels) on the right of my screen... hardly notice it

---

### Post by 23meg on 2005-05-26
cool. check out [this thread](http://www.ubuntuforums.org/showthread.php?t=23910) if you're interested in making that panel totally hidden (it's still up by six pixels by default) and setting its show/hide delay.

---

### Post by TravisNewman on 2005-05-26
So is there any way to keep Eterm from showing in the taskbar? I'm obsessed with keeping it as clean as possible :)

---

### Post by sapo on 2005-05-26
[QUOTE=panickedthumb]So is there any way to keep Eterm from showing in the taskbar? I'm obsessed with keeping it as clean as possible :)[/QUOTE]


I wanna now if there's a way to do it too  :grin:

---

### Post by 23meg on 2005-05-26
sure; install [devil's pie](http://www.burtonini.com/blog/computers/devilspie), and add the following to your .devilspie.xml file (which should reside in your home directory):

```
<flurb name="hide Eterm">
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="window_title" value="Eterm 0.9.2"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionSetWorkspace">
        <property name="pinned" value="TRUE"/>
      </action>
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/> 
        <property name="skip_pager" value="TRUE"/>
      </action>
    </actions>
  </flurb>

```

skip_pager hides the window from the workspace pager, skip_tasklist from the tasklist, and pinned makes it appear on all workspaces. this should be enclosed in <devilspie> </devilspie> tags to work; i've only included my "hide Eterm" flurb above.

---

### Post by TravisNewman on 2005-05-26
I wish eterm had included that functionality by default ;) If I use devil's pie (who the heck came up with that name?) and I want a full on eterm window that DOES show, then I'm screwed :) Unless you can change the window name of eterm through command line.

gonna go man eterm.

---

### Post by 23meg on 2005-05-27
hmm, you could use the -T parameter in Eterm to change the title in your launcher.

---

### Post by sapo on 2005-05-27
[QUOTE=23meg]hmm, you could use the -T parameter in Eterm to change the title in your launcher.[/QUOTE]

wow... i never tought that eterm could be this "powerfull" and could have a lot of customization features like this.. [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img]

---

### Post by 23meg on 2005-05-27
right, that's the point of using Eterm over any other terminal, as is overstressed in the docs; it's completely customizable.

---

### Post by Astrophobos on 2005-05-28
Thanks for all this information, it's very nice.

The only problem I see right now is that some characters in the eterm terminal don't print "normaly".

[http://www.anncse.com/Capture.png](http://www.anncse.com/Capture.png)

It is related to utf-8 or something?

Thanks again.

---

### Post by 23meg on 2005-05-28
i'm experiencing this with some non-western characters too and would like to know if there's a workaround.

---

### Post by 23meg on 2005-06-02
now how about [doing this (almost) with gnome-terminal](http://www.ubuntuforums.org/showthread.php?t=38938)?

---

### Post by Gandalf on 2005-06-10
you can also use devilspie i use it (from the Completely transparent Terminal HOWTO) it is usefull, this way i don't show the terminal in taskbar and i show it in all workspaces,
here's what i did in case you don't know

```

sudo apt-get install devilspie
pico ~/.devilspie.xml

```
insert into it
```

<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">

<devilspie>
  <flurb name="Eterm pinned and no taskbar">
    <matchers>
       <matcher name="DevilsPieMatcherWindowName">
         <property name="application_name" value="Eterm"/>
       </matcher>
    </matchers>
<!-- The action below will pin Eterm to all workspaces-->
     <actions>
         <action name="DevilsPieActionSetWorkspace">
            <property name="pinned" value="TRUE"/>
      </action>
<!-- The action below will remove Eterm from the windows list and the
Workspace Switcher (thanks Trash:)-->
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/>
        <property name="skip_pager" value="TRUE"/>
      </action>
     </actions>
</flurb>
</devilspie>

```

now i changed the terminal.sh to
```

#!/bin/bash
ps -e | grep Eterm
x=$?;
if [ $x -eq 1 ]; then
        devilspie&
Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 -f white --geometry=95x10+280+20 --font-fx none 
else
        killall -9 Eterm
        killall -9 devilspie
fi

```

---

### Post by kungfooguru on 2005-06-21
Hey, I am the developer of Tilda and just got into ubuntu after hearing from friends how good it was, but still a gentoo user for now, ;), ubuntu for my ibook though. 

I would like to suggest trying tilda again, .07 just came out and it is a lot better than past releases. The only dependency you need to install for it is the VTE devel libraries. There is a .deb for it tilda on the sf site as well. Also, it is currently a universal canidate for the next ubuntu release, so hopefully that will work out.

Tristan
[http://tilda.sf.net](http://tilda.sf.net)

---

### Post by sapo on 2005-06-21
> **kungfooguru]Hey, I am the developer of Tilda and just got into ubuntu after hearing from friends how good it was, but still a gentoo user for now,  said:**
> http://tilda.sf.net[/url]


i tried tilda, but uninstalled it cause i dont want the terminal to open "wide" in the screen.. i just want a little terminal in the center of it, or another place and i could find any options in tilda to do it :(

But tilda is a great program  :grin:

---

### Post by bigzak on 2005-06-21
It has occurred to me that the various launcher scripts all have one common failing; if you click them to close, it kills ALL Eterms that are running! If you want eterm as your normal terminal window, then you don't want to have to kill them all to get the little popup one...

A way around this would be to use something akin to:

```

#!/bin/bash

LOCKFILE=~/.etermpopup

if [ -f $LOCKFILE ]
    then
    xargs kill < $LOCKFILE
    rm -f $LOCKFILE
else
    Eterm &
    echo $! > $LOCKFILE
fi

```

This will toggle *one particular instance* of Eterm, without bothering any others that are running.

---

### Post by kungfooguru on 2005-06-21
You can now have tilda open anywhere on your screen and be any size. I saw the screen shot you had and i assure you that tilda can now do that. But i know everyone has different tastes, just wanted to suggest you try it out again. The options are in the config wizard, 'tilda -C', and you can even have each tilda open in a different place and different size if you want multiple terminals to be pulled down with different buttons.

Tristan

---

### Post by TravisNewman on 2005-06-21
it's actually called a tilde, but prounounced like tilda, or closer to til-deh. I'm an idiot, but it took me a minute to figure out what tilda meant before I said it out loud ;)
[http://en.wikipedia.org/wiki/Tilde](http://en.wikipedia.org/wiki/Tilde)

Just in case anyone is wondering.

---

### Post by XDevHald on 2005-06-21
Hmm, this isn't all that bad, makes it easy for quick load ups and sh installs :) Gonna add this to the sessions so that it loads without me having to click ;)

---

### Post by kungfooguru on 2005-06-22
Yes, its tilde but that had been taken at sourceforge. So I thought it humourous to call it Tilda since i knew so many people would go out of their way to correct me :). I do have it in the fequently asked questions about the misspelling.

---

### Post by endy on 2005-06-22
I'm using tilda right now and it rocks! Thanks kungfooguru   :)

---

### Post by cowlip on 2005-06-22
hey yeah it's a good idea.

---

### Post by Buddha on 2005-06-29
thanks for the script... this is great.
is there a way to configure the font size and font color by chance?

thanks.


*edit* 
found the way to change the font color... i hadn't noticed as i'd also changed the transparancy.  doh.

---

### Post by kungfooguru on 2005-07-07
Checkout the cvs, sf.net/projects/tilda, got tabs added and lots of bug fixes. Shoot me some bug reports so I can get the new release out. 

ctrl-t might still not work for opening a tab when you get it but just right click and choose add tab from the menu, I also have a problem with fonts in Ubuntu on PPC but none in Gentoo x86 -- not sure whats up yet.

Tristan

---

### Post by kungfooguru on 2005-07-31
New tilda is out. Added tabs, fixed a lot of bugs -- just check it out. [http://tilda.sf.net](http://tilda.sf.net)

---

### Post by UbuWu on 2005-07-31
Great!

---

### Post by sapo on 2005-07-31
[QUOTE=kungfooguru]New tilda is out. Added tabs, fixed a lot of bugs -- just check it out. [http://tilda.sf.net](http://tilda.sf.net)[/QUOTE]


nice :D

isnt there a deb package or autopackage?  :grin:

---

### Post by kungfooguru on 2005-08-12
Come join me on #tilda irc.oftc.net with all your complaints and suggestions :).

Tristan

---

### Post by tonysathre on 2005-08-15
i used this technique on kde and it worked perfectly, only one problem, i want eterm out of my task list. i have devilspie but i dont really know what to do with it, any ideas would be appreciated

---

### Post by cowlip on 2005-08-15
[QUOTE=sapo]nice :D

isnt there a deb package or autopackage?  :grin:[/QUOTE]


Yes plz make an autopackage :)

---

### Post by ffderrick on 2005-08-30
I remember a program called kuake.  Used it with Kde and gentoo over a year ago.
I'll try "tilde".  
The Eterm scripts are great.
What I have always loved about Linux?  There is alway's a way.  
Thanks.
Derrick

---

### Post by jbrader on 2005-08-31
> **sapo]I was in my smoke break when i suddenly had an idea  :grin: 

I was thinking about those trasparent terminal the some people uses as a desktop background... and the an idea come to my mind..

I dont know if it already exists (hope it exist) but it could be a very useful think..

To understand what i m talking about, click on the Search button here in the Ubuntuforums...

Saw how it came down? now...

Why not have a taskbar button, that when clicked pop down a 5 or 6 lines terminal (with no borders if possible).

I think it will be very useful, sometimes you want to edit a file or run some app.. then you click on the button, the terminal comes down (or up if in the bottom bar) you type the comands.. and then hide it again?

I dont know how to program in linux.. but i think that  a lot of ubuntu users here could do it (if it doesnt exist yet).

What do you think about it? i think it would be very very useful for me  :grin:



**###### SOLUTION -> THANX TO 23meg for the script #########**

First be sure to have eterm installed:

```

sudo apt-get install eterm

```

Now create a terminal.sh file and put the contents bellow:

```

#!/bin/bash
ps -e | grep Eterm
x=$? said:**
> ; then
        Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 -f white **--geometry=95x10+280+20** --font-fx none 
else
        killall -9 Eterm
fi

```

Edit the --geometry to change the location where it will open...

I ll explain the geometry so people can make their own behave like it:

Where:
95 = width
10 = number of lines
280 = horizontal position
20 = vertical position

Save your file and type:

```

chmod +x terminal.sh

```


Now you just have to put a Shortcut pointing to it..

if you dont want it to be fully transparent change the shade=0 to shade=50 or shade=80

Now i just click it and it comes down.. here a screenshot  :grin:

[[IMG]http://img81.echo.cx/img81/1705/screenshot12jd.th.png[/IMG]](http://img81.echo.cx/my.php?image=screenshot12jd.png)
 Just implemented your solution and it's awsome!

---

