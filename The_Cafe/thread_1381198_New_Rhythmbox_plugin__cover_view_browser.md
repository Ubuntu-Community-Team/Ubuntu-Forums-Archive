---
title: "New Rhythmbox plugin : cover view browser"
date: 2010-01-14
forum: The Cafe
---

### Post by manuw2009 on 2010-01-14
Hi all,

After long hours trying to understand (I know nothing about python...), Alexandre Rosenfeld's previous work on the coverart_browser plugin I eventually came up with a new updated version :
1. NEW : enabling to display a nice cover view pane in rhythmbox (see attachment)
2. a button enables to download missing covers (original plugin purpose)
3. NEW : double clicking on an album cover enables to play it
4. NEW : drag & dropping pictures from the internet onto the cover image enables to replace cover art
Well, this is still beta I guess and seems buggy but it mostly works.
I'd like to incorporate drag'n dropping over ipod to copy entire albums to the ipo/MTP library but I'm still not sure how to achieve that...
Hope (some of) you enjoy it...

Google code page : [http://code.google.com/p/rhythmbox-cover-art-browser/](http://code.google.com/p/rhythmbox-cover-art-browser/)

---

### Post by clicker4721 on 2010-01-31
I downloaded it and have to ask a stupid question:  to where do I extract it?

---

### Post by manuw2009 on 2010-02-01
Hi,

You need to extract it to :
[B]*.gnome2/apps/[I]rhythmbox*/[I]plugins/

[/I][/I][/B][I]Then you'll have to activate the plugin in Rhythmbox
[/I]

---

### Post by clicker4721 on 2010-02-01
Ahh, wonderful, I should have expected that. :P Thanks.

---

### Post by manuw2009 on 2010-02-06
Hi again,

c'mon guys, anybody interested in adding further possibilities ?
(for instance, how would we enable drag/drop over mtp/ipod from the cover view ?)
Does anyone know how to use libgpod/pythongpod from a rhythmbox addon ?
manu

---

### Post by Shpongle on 2010-02-06
very nice !, il be sure to check this out next time i use rhythmbox , on kde with amarok at the min, coincidentally im learning python as i type this. keep up the good work =D>

---

### Post by ctrlmd on 2010-02-07
hi 
i downloaded the plugin but there isn't a folder called apps inside .gnome2 
so where do i have to extract it

---

### Post by manuw2009 on 2010-02-07
Hi ctrlmd,

I think it's either in 
.gnome2/rhythmbox/plugins/ 
or 
.gconf/apps/rhythmbox/plugins

I don't really understand why we have those two...
Maybe the 2nd one is just a result of the activation of the plugins in .gnome2

---

### Post by sigurnjak on 2010-02-07
Does anyone get this error :Unable to activate plugin Cover Art Browser  ?

---

### Post by ctrlmd on 2010-02-07
> **manuw2009 said:**
> Hi ctrlmd,

I think it's either in 
.gnome2/rhythmbox/plugins/ 
or 
.gconf/apps/rhythmbox/plugins

I don't really understand why we have those two...
Maybe the 2nd one is just a result of the activation of the plugins in .gnome2
i copied the plug-in to the specified directory and it didn't show up in rhythm media player plugins

---

### Post by manuw2009 on 2010-02-07
Sigurnjak
you probably have some missing dependancies
could you please run rhythmbox from the console with debug traces on ?
(rhythmbox -d or something...)

---

### Post by sigurnjak on 2010-02-07
I got it work sort of by placing it here /usr/lib/rhythmbox/plugins . Here is output from starting Rhythmbox via terminal :
andrey@andrey-desktop:~$ rhythmbox

** (rhythmbox:11926): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:11926): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
/usr/lib/rhythmbox/plugins/artdisplay_browser/__init__.py:24: DeprecationWarning: the sets module is deprecated
  from sets import Set

---

### Post by rupeshk_19 on 2010-02-11
The cover view pane is a great idea and looks very nice. I have a suggestion - the browser should show the cover art stored in the user's music folders as folder.jpg. This is the same logic used by the cover art plugin.

Coincidentally last week I also uploaded a plugin based on the context pane plugin which searches the web for the album art of the currently playing song using google search apis. From the resulting images, one can then choose an image to set it as album art. Project details are here [http://code.google.com/p/albumartsearch/](http://code.google.com/p/albumartsearch/)

May be the user can use the cover art browser to view his collection and the album art search to choose his album art. Just a thought.

---

### Post by saturnblackhole on 2010-02-12
great idea and thanks for your hard work but.....its not working the buttons (fetch and cancel) are not clickable and there it only shows a few album covers (4 out of 238  ).

EDIT: it seems to work after pressing the plug-in icon 10times lol i can live with it.

---

### Post by smif1984 on 2010-02-13
I have the same problem: no clickable buttons and absolutely no cover art. Running on Karmic..

---

### Post by Psyphre on 2010-02-13
also same problem with no clickable buttons. I'm running Jaunty.

---

### Post by manuw2009 on 2010-02-13
Hi,

Buttons get clickable only once all albums have been loaded in the grid view...but I know it sometimes gets stuck because of some albums !
by pass : close the grid view and retrieve missing covers (the one that seem to get the thing stuck) from the album art plugin.
if someone is willing to help...
Also I'm currently trying to implement some kind of copyTo (ipod, mp3 media device) through contextual menu, but apart form listing the devices, I just can't get a grip on the RBSource to trigger the album tracks transfer

If anybody wants to contribute :D, I created a google code project :
[http://code.google.com/p/rhythmbox-cover-art-browser/](http://code.google.com/p/rhythmbox-cover-art-browser/)
thanx

---

### Post by Psyphre on 2010-02-13
> **manuw2009 said:**
> Hi,

Buttons get clickable only once all albums have been loaded in the grid view...but I know it sometimes gets stuck because of some albums !
by pass : close the grid view and retrieve missing covers (the one that seem to get the thing stuck) from the album art plugin.
if someone is willing to help...
Also I'm currently trying to implement some kind of copyTo (ipod, mp3 media device) through contextual menu, but apart form listing the devices, I just can't get a grip on the RBSource to trigger the album tracks transfer

If anybody wants to contribute :D, I created a google code project :
[http://code.google.com/p/rhythmbox-cover-art-browser/](http://code.google.com/p/rhythmbox-cover-art-browser/)
thanx

Thanks for the tip, and I appreciate the hard work, its a good project.

Unfortunately it still does not work. I removed all albums apart from 1. The cover does not show, even though it shows in the coverart side panel and also there is a folder.jpg file.

---

### Post by manuw2009 on 2010-02-14
Strange....
Could you try to assign a cover by drag &drop from a web image ?
I'm pretty sure the bug is related to specific album names...what is your locale ?
I guess we need some support from a python expert...!

---

### Post by Psyphre on 2010-02-14
> **manuw2009 said:**
> Strange....
Could you try to assign a cover by drag &drop from a web image ?
I'm pretty sure the bug is related to specific album names...what is your locale ?
I guess we need some support from a python expert...!

I tried dragging and dropping from both the web and from an image file on my desktop, neither worked.

The locale of the album is:

/media/sdb1/My Music/Daft Punk/Discovery

What kind of album names cause trouble?

---

### Post by kio_http on 2010-02-14
Looks too much like iTunes and therefore not original.

---

### Post by manuw2009 on 2010-02-14
I have no idea ... I guess you should run rhythmbox -d and look at the traces in the console window...
On the mtp/iPod transfer front does anyone have an idea on how to retrieve easily the sources to copy entries to ?

---

### Post by zob on 2010-02-15
Really cool. I'd wish it worked for me. Does anyone actually have this working.
It just downloads 7 albumcovers and stops there.

When I run rhythmbox -d I get a lot of these lines:
```
(16:36:21) [0x7fea351af6c0] [CoverArtBrowserPlugin.album_load] .gnome2/rhythmbox/plugins/artdisplay_browser/__init__.py:570: CoverArtBrowser DEBUG - album_load()
(16:36:21) [0x7fea351af6c0] [CoverArtBrowserPlugin.album_load] .gnome2/rhythmbox/plugins/artdisplay_browser/__init__.py:570: CoverArtBrowser DEBUG - album_load()
(16:36:21) [0x7fea351af6c0] [CoverArtBrowserPlugin.album_load] .gnome2/rhythmbox/plugins/artdisplay_browser/__init__.py:570: CoverArtBrowser DEBUG - album_load()
(16:36:21) [0x7fea351af6c0] [CoverArtBrowserPlugin.album_load] .gnome2/rhythmbox/plugins/artdisplay_browser/__init__.py:570: CoverArtBrowser DEBUG - album_load()

```

After a thousand lines or so of that, I get:
```
(16:40:18) [0x1aa9040] [paned_size_allocate_cb] rb-shell.c:2663: paned position 374
(16:40:18) [0x1aa9040] [paned_size_allocate_cb] rb-shell.c:2664: right_paned position 1373

```
I don't know if that's an error.

Please give me instructions if you want me to help debugging. I'm not the only one: [http://www.omgubuntu.co.uk/2010/02/rhythmbox-cover-art-browser.html](http://www.omgubuntu.co.uk/2010/02/rhythmbox-cover-art-browser.html)
As you can see in the comments, it doesn't really work for anyone - or so it seems. Might be working for a lot of people, who doesn't bother to comment.
I would like to know if anyone has had any succes.

---

### Post by thatguruguy on 2010-02-15
> **kio_http said:**
> Looks too much like iTunes and therefore not original.

I've never understood claims like this one.  Sometimes, a program does something a particular way because it's a logical way to do something.  The fact that other programs do something in a similar way is not a bad thing, if it's the most logical way to do it.


EDIT: I guess the point I'm trying (perhaps poorly) to make is, the question should not necessarily be, "Is it original?" but instead should be, "Is it useful and/or functional?"

---

### Post by manuw2009 on 2010-02-15
Thanx thatguruguy :)
I just can't see the point either...

Anyhow, on a more constructive front :
it turns out I'm unable to access the rhythmbox sources (to perform a transfer to the media devices).
It seems I'm facing quite a common bug :
ERROR:/build/buildd/pygobject-2.18.0/gobject/pygobject.c:924:pygobject_new_full: assertion failed: (tp != NULL)
when trying to access my ipod source

even in a the console debug window, a plain 
shell.get_property('selected-source')
is giving the same result...
And so are a lot of plugins as Google suggests

---

### Post by Shpongle on 2010-02-15
> **thatguruguy said:**
> I've never understood claims like this one.  Sometimes, a program does something a particular way because it's a logical way to do something.  The fact that other programs do something in a similar way is not a bad thing, if it's the most logical way to do it.


EDIT: I guess the point I'm trying (perhaps poorly) to make is, the question should not necessarily be, "Is it original?" but instead should be, "Is it useful and/or functional?"

well said!

---

### Post by zob on 2010-02-15
Could someone confirm that they have made this work?
I just need to know if it downloads (or shows from jpg in folder) ALL or MOST of the covers in your collection.

---

### Post by manuw2009 on 2010-02-17
hi zob,

Could you please try again using the latest google.code version ?
I had stall issue at the beginning because of the threads used in the original code.
They have not disappeared completely, but seem to happen less often...
As I said before, some albums seem to cause problems, the by-pass I found was to assign an album art through the album art plugin.

---

### Post by zob on 2010-02-17
I know this is lazy but I can't seem to find it on google code.
I got my version from your dropbox folder I think, from the link he gives on this site:
[http://www.omgubuntu.co.uk/2010/02/rhythmbox-cover-art-browser.html](http://www.omgubuntu.co.uk/2010/02/rhythmbox-cover-art-browser.html)
Could you please post a link to the version, that you would like me to test, and that I will be happy to test;)

EDIT: Sorry. I just noticed that you left a comment on that site with the link. I will install tomorrow and tell how it works out.
[http://code.google.com/p/rhythmbox-cover-art-browser/](http://code.google.com/p/rhythmbox-cover-art-browser/)
But it sure looks great. Beautiful work.

---

### Post by zob on 2010-02-18
Sorry, I still have no luck. It doesn't download anything. Please tell me if there is anything I can do to test.

---

### Post by manuw2009 on 2010-02-19
Hi,

Sorry to hear the bad news...
Could you please try again with the attached .py version ?
(run rhythmbox -D[FONT=monospace] [/FONT]artdisplay_browser)
This won't work any better, but it will display traces & hopefully will tell us where it gets stuck...
Could you please also attach a screenshot of the pane before the fetch is launched & one afterwards ?
Also are you sure the album art display plugin is activated ?

---

### Post by Pott on 2010-02-19
Funny thing here.
It worked when I extracted to gnome2/plugins, but copied itself to gconf/apps/rhythmbox/plugins. It doesn't work if it's only in one of these folders.

Now it works but it doesn't see many of the cover arts. 
I have all my cover art embedded in the ID3 tags of my MP3s... so I'm guessing it doesn't recognize these..?

---

### Post by manuw2009 on 2010-02-19
Strange...I guess some gentle Rhythmbox developper could tell us where we're meant to put the plugins !
about the embedded art : tha answer is no, since I'm actually relying on rhythmbox album covers database, and I guess this implies embedded covers are not handled

---

### Post by Pott on 2010-02-19
DOH :( Guess it's hopeless for me then... Rhythmbox won't see embedded art until 0.12.6, which I can't get yet. I use it instead of gmusicbrowser because it works with Conky (just a bit of fun) but I guess gmusicbrowser is the best music player I tried so far... :/ 

Thanks for the help and the plugin!

---

### Post by kyleabaker on 2010-04-14
Has this plugin been improved at all in the last 2 months? It looks like its partially working and attempted to fetch covers the first time I ran it, but now its got both buttons disabled as others are experiencing.

I thought we might see some community members help pick up the slack on this by now. :P

---

### Post by manuw2009 on 2010-04-15
Hi,

Well, the truth is I eventually left rhythmbox for amarok...since amarok 2.3 now handles my ipod touch pretty well ;) and amarok collection system is way more powerful
Actually, I worked on this instead:

[http://www.ubuntuhq.com/content/amarok-231-get-cover-bling](http://www.ubuntuhq.com/content/amarok-231-get-cover-bling)

Last time I checked rhythmbox though, I still had the crash preventing me from scanning library sources and I gave up (I wanted to add to the album grid a "transfer to ipod" command)

---

### Post by joetraff on 2010-05-20
I have got my solution.
Thank you all:)

---

### Post by joey-elijah on 2010-06-01
Sad to see this cease - was a promising plugin :)

---

### Post by manuw2009 on 2010-06-02
Well, I guess there's bound to be anyone willing to finish the work...?
The reasons why I don't feel like working on it anymore :
1. Python...my knowledge is sooo limited
2. and of course, I'm really liking Amarok 2.3 now ! It's so powerful, efficient and well, awesome too. It really does everything I need, and it does it well. I'm strongly recommanding it to anyone (and the development on it is VERY active)

---

### Post by kyleabaker on 2010-06-02
I'd take it up, but I've already got like 10 other projects that I'm juggling right now. I really wanted to see this project go far though. Rhythmbox is my favorite music app!

---

### Post by FokkerCharlie on 2010-10-27
Is this project dead?

A real shame if so, as it's a really good idea, and one area the Banshee beats Rhythmbox.

I don't have the skills to take it forward myself, and was very disappointed when I found that the plugin didn't work properly for me :(

Hope that someone will take a new interest.

Charlie

---

### Post by FokkerCharlie on 2010-10-27
Ah!

Good news- just found this:

[http://sourceforge.net/projects/rhythmarty/](http://sourceforge.net/projects/rhythmarty/)

Charlie

---

