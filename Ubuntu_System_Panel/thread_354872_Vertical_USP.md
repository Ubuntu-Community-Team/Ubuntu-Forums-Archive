---
title: "Vertical USP"
date: 2007-02-06
forum: Ubuntu System Panel
---

### Post by chanders on 2007-02-06
Me working on the secret sauce ;-)

[[IMG]http://img397.imageshack.us/img397/9959/screenshotxt2.th.png[/IMG]]("http://img397.imageshack.us/my.php?image=screenshotxt2.png")

---

### Post by delfick on 2007-02-06
cool, though isnt that already possible ????

........(cue to spill secret features :D)

---

### Post by liljoe76 on 2007-02-06
that sure is purdy.

---

### Post by rai4shu2 on 2007-02-07
Almost thought I was looking at a Mac there.

---

### Post by Malac on 2007-02-07
> **delfick said:**
> cool, though isnt that already possible ????

........(cue to spill secret features :D)
Note the lower right (transparent window) :)
Not the USP menu.

---

### Post by delfick on 2007-02-07
> **Malac said:**
> Note the lower right (transparent window) :)
Not the USP menu.


k then....what is that ??

---

### Post by chanders on 2007-02-07
> **delfick said:**
> k then....what is that ??

**That** my friend, is the answer to all your transparency wishes [-o<

---

### Post by ADRez on 2007-02-07
Cool!
Is that real transparency (like gnome terminal with beryl/compiz) or it shows allways the background?

---

### Post by delfick on 2007-02-07
> **chanders said:**
> **That** my friend, is the answer to all your transparency wishes [-o<

hehehe, that sounds very very very cool :D

please explain more :D

(about to explode with excitement :D (lol))

---

### Post by chanders on 2007-02-07
> **ADRez said:**
> Cool!
Is that real transparency (like gnome terminal with beryl/compiz) or it shows allways the background?

Yup! It's USP2 supporting TRUE Alpha transparencies from the ground up. It is going to take some work but Malac and myself already have a roadmap. I will post up more as it unfolds...

Plugins will requite only slight modification, and themes will not be difficult to design.

---

### Post by delfick on 2007-02-07
> **chanders said:**
> Yup! It's USP2 supporting TRUE Alpha transparencies from the ground up. It is going to take some work but Malac and myself already have a roadmap. I will post up more as it unfolds...

Plugins will requite only slight modification, and themes will not be difficult to design.

:D :D :D :D

---

### Post by chanders on 2007-02-09
I am so excited that roberTO created the very first theme for USP! This should keep you all happy until we get transparency fully supported. In the mean time here is my progress to date. It's not much but it's progress ;-)

[IMG]http://img67.imageshack.us/img67/5444/trydt6.png[/IMG]

---

### Post by delfick on 2007-02-09
> **chanders said:**
> I am so excited that roberTO created the very first theme for USP! This should keep you all happy until we get transparency fully supported. In the mean time here is my progress to date. It's not much but it's progress ;-)

[IMG]http://img67.imageshack.us/img67/5444/trydt6.png[/IMG]

YAY! more to drool over :D :D :p

---

### Post by chanders on 2007-02-09
I think i am getting the hang of it... Hopefully some more screenies soon ;-)

---

### Post by chanders on 2007-02-12
\\:D/
[[IMG]http://img355.imageshack.us/img355/4057/51969643se1.png[/IMG]]("http://imageshack.us")

---

### Post by cmost on 2007-02-12
Oooooh's and Ahhhhh's  :-)

When, when?!?!?

---

### Post by delfick on 2007-02-12
> **cmost said:**
> Oooooh's and Ahhhhh's  :-)

ditto :D

(though you can't really see the transparency in that shot.....put a tree behind it :D :p)


(though i'm liking the way the plugins look :D)

---

### Post by Malac on 2007-02-13
> **delfick said:**
> ditto :D

(though you can't really see the transparency in that shot.....put a tree behind it :D :p)
How about a whole landscape, will that do? :)
[ATTACH]25187[/ATTACH]

---

### Post by delfick on 2007-02-13
> **Malac said:**
> How about a whole landscape, will that do? :)
[ATTACH]25187[/ATTACH]

o yes, that will do :D :D :D

that look very cool :D

(excitement reaching astronomical heights :P :D)

though what's with the applications plugin ??

---

### Post by Malac on 2007-02-13
> **delfick said:**
> though what's with the applications plugin ??
Not finished yet. 
Give us a chance this is new stuff to us. :D
Here we go....fixed.
[ATTACH]25194[/ATTACH]

---

### Post by zekopeko on 2007-02-13
> **delfick said:**
> ditto :D

(though you can't really see the transparency in that shot.....put a tree behind it :D :p)


you and trees :grin: ,hehe

---

### Post by delfick on 2007-02-13
> **zekopeko said:**
> you and trees :grin: ,hehe

????

---

### Post by delfick on 2007-02-13
> **Malac said:**
> Not finished yet. 
Give us a chance this is new stuff to us. :D
Here we go....fixed.
[ATTACH]25194[/ATTACH]

thought so :D

*excitement went too high.....i exploded... :D*

---

### Post by zekopeko on 2007-02-14
> **delfick said:**
> ????

beryl... tree in the cube... :)

---

### Post by delfick on 2007-02-14
> **zekopeko said:**
> beryl... tree in the cube... :)

i thought that's what you were referring to :D

trees are cool :D

(hehe, i'm not a hippy :D)

---

### Post by chanders on 2007-02-14
Here is my first real theme (with a rough theme file). To create themes is pretty simple. Each plugin is made up of two parts. The Heading part, and the Content part.

Essentially the theme is a cairo drawing routine for each. In this theme, we see a gray rounded rectangle on the top with text rendered in the heading, and a white rectangle rounded on the bottom for the content.

Pretty easy, i'd say!  Comments welcome.

[IMG]http://img212.imageshack.us/img212/9431/firstthemeti4.png[/IMG]

Anyone with a cairo routine to do a rectangle with a gradient to give a reflective look?

---

### Post by delfick on 2007-02-14
nice !! :D

how easy is it to configure transparency in the theme ?? :D

---

### Post by chanders on 2007-02-14
> **delfick said:**
> nice !! :D

how easy is it to configure transparency in the theme ?? :D

Every item has a transparency value ;-)

---

### Post by delfick on 2007-02-14
> **chanders said:**
> Every item has a transparency value ;-)

*dancing with joy* :D

---

### Post by chanders on 2007-02-15
Here is my initial drag and drop video for plugins. You cannot see the icon pointer for some reason but when you drag, an icon shows up so you know the plugin is being dragged.

I tried to post it up on youtube it it wont let me. Maybe someone can?

Thanks!

---

### Post by Malac on 2007-02-15
> **chanders said:**
> Here is my initial drag and drop video for plugins. You cannot see the icon pointer for some reason but when you drag, an icon shows up so you know the plugin is being dragged.

I tried to post it up on youtube it it wont let me. Maybe someone can?

Thanks!
That is sooooo sweet chanders, heehee. =D>
Looking really cool. :cool:

Can you re-arrange the plugin order like that too?
Excellent work. \\:D/

P.S. I think we need to announce a feature freeze on USP2 soon, with say a week for final requests/bugs and release it to beta.
If only so I can concentrate on USP3. :D

---

### Post by delfick on 2007-02-15
> **Malac said:**
> Can you re-arrange the plugin order like that too?

that would be very cool... :D :D


> Excellent work. \\:D/

too right :D.. that's awsome chanders !!!

and to imagine how far the usp has gone since the beginning ! :D

---

### Post by chanders on 2007-02-22
Ok guys, here is the next video of USP3 pre pre alpha ;-) Tell me what you think. 

[http://www.sharebigfile.com/file/90150/test2-mpeg-tar-bz2.html](http://www.sharebigfile.com/file/90150/test2-mpeg-tar-bz2.html)

---

### Post by delfick on 2007-02-22
> **chanders said:**
> Ok guys, here is the next video of USP3 pre pre alpha ;-) Tell me what you think. 

[http://www.sharebigfile.com/file/90150/test2-mpeg-tar-bz2.html](http://www.sharebigfile.com/file/90150/test2-mpeg-tar-bz2.html)

awsome :D :D

(here's a better place to download it from [http://delfick.videos.googlepages.com/usp3video.tar.bz2](http://delfick.videos.googlepages.com/usp3video.tar.bz2) :D)

will it (obviously in the future :D) be made so that as you drag the plugins, the other plugins move out of the way ?? (as in fluid motion ??)

:D

can't wait to test it for real ! :D

---

### Post by PsyberOneZero on 2007-02-22
> **chanders said:**
> Ok guys, here is the next video of USP3 pre pre alpha ;-) Tell me what you think. 

[http://www.sharebigfile.com/file/90150/test2-mpeg-tar-bz2.html](http://www.sharebigfile.com/file/90150/test2-mpeg-tar-bz2.html)

OK, That's awesome!

I was doing a little thinking about USP, and I am making a few mock-ups for 3.  Would it be possible to make the plugin containers uniform in size i.e.
Single Full Height, Single Half Height and Double Full height (I'll put up the mock-ups later)
this way the panels will fit together in perfect units.  The big reason for this is I really like the double wide panel in SLAB. and it will make configuration much easier than having to adjust the pixel values in uspconfig. I hate to give credence to the flame wars but there is almost TOO much configurability for each plugin. With drag-n-drop placement and uniform sizes, that will cut out a lot of the annoying options.

Great work so far.

EDIT: Also is this still coded in Python or are you moving to C/C++?

---

### Post by chanders on 2007-02-22
All still in python. I find python so much easier to program in, edit and most of all to share.

>  will it (obviously in the future :grin:) be made so that as you drag the plugins, the other plugins move out of the way ?? (as in fluid motion ??)This is possible but you have to remember that it is a mix of PyGTK and cairo drawing so animation amongst widgets etc might be a little difficult. If it was all drawn from scratch like a screenlet say, it would have been much easier..

@ PsyberOneZero, I am looking forward to your mockups. Fixed sized plugins is actually a good idea and you are right, it would make it so much easier for USPConfig (I can see Malac rejoicing ;-))  It might make it a bit hrd to build certain plugins to fit EXACTLY to the defined sizes though... We will see as it develops...

As for the video it is waaay mor fluid in real time, and the best part is, all USP2 plugins are 100% compitable \\:D/

---

### Post by plun on 2007-02-22
> **chanders said:**
> 
As for the video it is waaay mor fluid in real time, and the best part is, all USP2 plugins are 100% compitable \\:D/

Well... time for a pre-Alpha....:) 

Uploaded to You Tube.

[http://www.youtube.com/watch?v=BBSm5RZ2fDs](http://www.youtube.com/watch?v=BBSm5RZ2fDs)

=D>

---

### Post by delfick on 2007-02-22
> **chanders said:**
> This is possible but you have to remember that it is a mix of PyGTK and cairo drawing so animation amongst widgets etc might be a little difficult. If it was all drawn from scratch like a screenlet say, it would have been much easier.

well since you've added all my long term wishes (mainly transparency and compact list) i suppose i need a new long-term wish :D

this is it :D :D :p

> As for the video it is waaay mor fluid in real time, and the best part is, all USP2 plugins are 100% compitable \\:D/

awsome :D !!!!!! :D

---

### Post by PsyberOneZero on 2007-02-23
Here's a rough mock-up with a few dimensions, I'll have more showing the different configurations (Not sure about tabs yet) 
[[IMG]http://img134.imageshack.us/img134/2944/usp3mockuppd0.th.png[/IMG]](http://img134.imageshack.us/my.php?image=usp3mockuppd0.png)

---

### Post by chanders on 2007-02-23
Looks great!  I especially like the themed buttons, and this is what I will be trying to get done next. I will post up a roadmap in a little while. I can definitely see the fixed plugin sizes working. And it should not be difficult to get older plugins to conform ;-)

---

### Post by delfick on 2007-02-23
> **PsyberOneZero said:**
> Here's a rough mock-up with a few dimensions, I'll have more showing the different configurations (Not sure about tabs yet) 
[[IMG]http://img134.imageshack.us/img134/2944/usp3mockuppd0.th.png[/IMG]](http://img134.imageshack.us/my.php?image=usp3mockuppd0.png)

very nice :D

with such a plan, would it also be possible to define more than 2 columns ?? :D

---

### Post by PsyberOneZero on 2007-02-23
chanders can better answer that but in theory you could make a triple wide plugin (Recent or Tracker/Beagle would be the only ones I really can think of.) but it should be possible.

I'll have a few more mock-ups of just the menu over the next few days, and I'll try a triple ;)

---

### Post by perfran on 2007-02-23
Hello,:) 
I have a little bug concerning the search box.
I saw on Chander's capture on the first page of this thread that the search box of usp is active with Beryl enabled.
When I use metacity, I can filter the applications normally by entering something in the search box, but when I switch to Beryl, there is no more colored frame around the search box and no more cursor to write text into it, so when I try to fill the box with some text, it doesn't work and nothing happens. :( It is the same problem when I run usp with the keybinding even with metacity. 
It seems to work with Chanders, so maybe it's due to a wrong Beryl configuration?
When I type usp run-in-a-window, I've got the following message:
```
perfran@blue:~ usp run-in-a-window
/usr/bin/usp:31: RuntimeWarning: Python C API version mismatch for module _keybinder: This Python has API version 1012, module _keybinder has version 1013.
  from _keybinder import tomboy_keybinder_bind as bindkey
*********** PLEASE IGNORE THE ABOVE WARNING **************
********** IT SHOULD NOT EFFECT USP OPERATION ************
```
Here some captures
[IMG]http://perfran.zitroogu.net/images/Yes.png[/IMG]
[IMG]http://perfran.zitroogu.net/images/No.png[/IMG]
Does somebody see the problem? :confused:
Thank you in advance for your help
and sorry for my bad english

---

### Post by PsyberOneZero on 2007-02-23
@ perfran: As far as the key binding problem, it looks like Tomboy is using the same key binding.
Try quitting Tomboy and then run usp run-in-a-window, but if it's a global key binding registered with the system than just change USP's in gconf.
Just try a few and see what's not taken, beryl uses a LOT of key bindings but there is sure to be something.

@ chanders/Malac: is there a way to disable the key binding?

---

### Post by chanders on 2007-02-23
Not sure about disabling the key binding. I will have to talk to **malac** about that.

As for **perfran** that problem is in your Beryl config. You need to set the "Focus stealing" to "None" for it to work...

---

### Post by PsyberOneZero on 2007-02-23
OK, here's a Triple Wide / Full Height plug-in just for delfick.
[[IMG]http://img468.imageshack.us/img468/198/usp3mockupbeaglemh3.th.png[/IMG]](http://img468.imageshack.us/my.php?image=usp3mockupbeaglemh3.png)

Again, these are just mock-ups for USP3.

---

### Post by delfick on 2007-02-23
> **PsyberOneZero said:**
> OK, here's a Triple Wide / Full Height plug-in 

nice :D

though that way it's still 2 columns of icons :D

> just for delfick.

hehehe :D thnx :D

---

### Post by perfran on 2007-02-24
[QUOTE=chanders;2200571As for **perfran** that problem is in your Beryl config. You need to set the "Focus stealing" to "None" for it to work...[/QUOTE]

Thank you very much Chanders :grin: , it was that problem indeed, now it works fine with beryl (search field active, even with the keybinding).

@ PsyberOneZero : I don't use tomboy, and I tried other keybindings, but the error in usp run-in-a-window is the same :confused: And I still have the same problem (search field not active) when I launch USP with different keybindings when I use metacity:-? . The keybinding works, but there's that problem of search box whereas when I launch USP by clicking on the USP button, the search box is active.
It is not very important because I use beryl more often than metacity, but I would like to understand the problem :)

---

### Post by PsyberOneZero on 2007-02-24
I've been doing some more work on the mock-ups (I'll have more up tonight). and I've hit on some new sizes for the fixed width plugins.

Single Width / Half Height : 245 x 215
Single Width / Full Height : 245 x 440
Double Width / Half Height : 500 x 215
Double Width / Full Height : 500 x 440
Triple Width / Half Height : 755 x 215
Triple Width / Full Heght : 755 x 440
Borders/padding : 10px

or here's a formula for any combination

(245 * (width)) + (10 * (width - 1)) = Total Width of plug-in
(215 * (height)) + (10 * (height - 1)) = Total Height of plug-in

---

### Post by chanders on 2007-02-24
Looking forward to it ;-)

---

### Post by PsyberOneZero on 2007-02-24
I keep forgetting does :wink: mean sarcasm, as in this guy is wasting his time?
well, whatever it's my time to waste

Here's an idea for recent and notes
[[IMG]http://img91.imageshack.us/img91/4966/usp3recentnotesob2.th.png[/IMG]](http://img91.imageshack.us/my.php?image=usp3recentnotesob2.png)

---

### Post by chanders on 2007-02-24
This mockup rocks! I will try my best to get USP3 there, but I know the Drawing will be a lot of work. So this is a callout to all CAIRO programmers to jump right in in helping to create custom widgets as  they are the only way we'll be able to get the drawing down to a T.

As for the custom sizes and three wide - totally doable ;-)

---

### Post by delfick on 2007-02-25
> **chanders said:**
> As for the custom sizes and three wide - totally doable ;-)

awsome :D


and i'm loving your mockups PsyberOneZero :D :D

---

### Post by H.E. Pennypacker on 2007-02-25
> **PsyberOneZero said:**
> I keep forgetting does :wink: mean sarcasm, as in this guy is wasting his time?
well, whatever it's my time to waste


Don't rely on online emoticons to express feelings well.  They are often deceptive, and some people don't know how to properly use emoticons.  Some emoticons give an improper impression, confusing people.

---

### Post by PsyberOneZero on 2007-02-25
> **H.E. Pennypacker said:**
> Don't rely on online emoticons to express feelings well.  They are often deceptive, and some people don't know how to properly use emoticons.  Some emoticons give an improper impression, confusing people.
[Off Topic]

It's more that different people use different expressions in different ways. It's just hard to tell what their use is unless you talk with that person more than just in the forums.  It wasn't an insult and chanders talked to me so It's OK.

I rarely use them outside of :) , :(  and :confused: 

[/Off Topic]

---

### Post by _profox on 2007-02-28
Seriously, you're doing great stuff, here!!
I am very jealous of the youtube video... Do you think it will be hard to integrate this into KDE? If it's all cairo (and no Gtk widgets) it should look pretty good in KDE, I think?

Yea, I switched back to KDE...
I'm glad you're still working on USP though!

---

### Post by DerSkw on 2007-03-06
anything new on usp3?

---

### Post by Malac on 2007-03-06
Myself and chanders are working on some new stuff for USP3.
Due to some strange quirk of the gtk.Notebook(used for the tab pages) refusing to use transparency it looks like we may have to write our own set of widgets completely.
The downside is this will be a little more time consuming but the upside is hopefully more scope for "theme-ability".:)

---

### Post by delfick on 2007-03-06
> **Malac said:**
> Myself and chanders are working on some new stuff for USP3.

excellent :D

> Due to some strange quirk of the gtk.Notebook(used for the tab pages) refusing to use transparency 

well that's a bit rude, you should slap gtk.Notebook :p :D

> it looks like we may have to write our own set of widgets completely.
The downside is this will be a little more time consuming but the upside is hopefully more scope for "theme-ability".:)

take as much time as you need :D

---

### Post by Malac on 2007-03-06
> **delfick said:**
> well that's a bit rude, you should slap gtk.Notebook :p :D
I've tried that repeatedly, but it's definitely a stubborn little ......... widget. :)

---

### Post by delfick on 2007-03-07
> **Malac]Due to some strange quirk of the gtk.Notebook(used for the tab pages) refusing to use transparency
[QUOTE=delfick]well that's a bit rude, you should slap gtk.Notebook 
[QUOTE=Malac said:**
> I've tried that repeatedly, but it's definitely a stubborn little ......... widget. :)[/QUOTE][/QUOTE]

lol :D

hang it by it's legs over the side of a building, that'll make it cooperate :D :D :p

---

### Post by EnigMattic on 2008-07-11
Hey, haven't seen any news in a loooong while. Is this a dead project, or still ongoing? Thanks

---

### Post by Malac on 2008-07-14
> **EnigMattic said:**
> Hey, haven't seen any news in a loooong while. Is this a dead project, or still ongoing? Thanks
Yes still here trying to trap bugs and get to a proper repo release.

---

### Post by EnigMattic on 2008-07-14
Thank goodness for that! This is a great project!!!

---

### Post by Malac on 2008-07-17
> **EnigMattic said:**
> Thank goodness for that! This is a great project!!!
Thank you

---

### Post by zekopeko on 2008-07-19
soooo.... where is it hosted? linky please. also are we getting USP3 with the super cool transparency or something else? please give more info. this was/is an awesome project.

---

### Post by Malac on 2008-07-20
> **zekopeko said:**
> soooo.... where is it hosted? linky please. also are we getting USP3 with the super cool transparency or something else? please give more info. this was/is an awesome project.
Go here for latest Download/Installation instructions for USP2:
[]("http://code.google.com/p/ubuntu-system-panel/")[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

I am going to get the updated source from chanders for USP3 a.s.a.p.

I'd really like to draw a line under USP2 and get it packaged into .deb and hosted in the repos too, if only so I could move onto USP3 completely. :)
Any help in getting said package in the repos would be greatly appreciated from any.

---

### Post by EnigMattic on 2008-07-21
Amen to that!!! :)
You guys are doing such a great job!!!

> **Malac said:**
> Go here for latest Download/Installation instructions for USP2:
[]("http://code.google.com/p/ubuntu-system-panel/")[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

I am going to get the updated source from chanders for USP3 a.s.a.p.

I'd really like to draw a line under USP2 and get it packaged into .deb and hosted in the repos too, if only so I could move onto USP3 completely. :)
Any help in getting said package in the repos would be greatly appreciated from any.

---

