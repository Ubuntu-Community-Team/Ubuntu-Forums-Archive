---
title: "September 2008 Desktop Screenshot Thread"
date: 2008-08-31
forum: The Cafe
---

### Post by ayoli on 2008-08-31
Rules:

       [LIST=1]
[*]Forum guidelines on content apply. In other words, safe for kids and safe for work.
[*]Try not to quote embedded images; take a moment to snip them out.
[*]Off-topic posts will be edited or moved.
[*]Thumbnail your image, or use the forum's attachment system. Full-size embedded images are annoying and will be snipped mercilessly.
[*]Take a moment and tell everyone the details of your desktop, such as the theme name, the wallpaper name, the icons and any programs you're using in the image.
[/LIST]
Enjoy!

---

### Post by ayoli on 2008-08-31
Trying to make a murinna version of glow (ice). other details in the screenshot.
[URL="http://ayozone.org/gallery/screenshots-september-2008"]
[IMG]http://ayozone.org/wp-content/gallery/screenshots-september-2008/thumbs/thumbs_31082008.png[/IMG][/URL]

---

### Post by Prefix100 on 2008-08-31
Heres mine, although still 7 minutes 'till the first for me =D

---

### Post by phrostbyte on 2008-08-31
Here is me running WinXP and Ubuntu at the same time, with WinXP on one side of the Compiz cube:

I am not sure where the wallpaper is, but I got it from gnome-look.org
The theme is the standard emerald theme.

---

### Post by Prefix100 on 2008-08-31
> **phrostbyte said:**
> Here is me running WinXP and Ubuntu at the same time, with WinXP on one side of the Compiz cube:

[[IMG]http://img175.imageshack.us/img175/3230/desktopmo4.th.png[/IMG]](http://img175.imageshack.us/my.php?image=desktopmo4.png)

Virtual box right?

If virtual boxes could do games, it'd be the best thing ever.

---

### Post by EnGorDiaz on 2008-08-31
my desktop as is in the screenshot

---

### Post by What is in a name? on 2008-08-31
A question I didn't arrive on time to answer, from the last month's screenshots thread:

> **KneeTie said:**
> im wondering if you can release a version that doesnt have " black menu " or black bar where file,edit,view etc. are just the same grayish color all around , i want to use this gtk badly. If you dont have time or for whatever reason is there any way i can do this myself ?

Basically, all you'd have to do is find the section saying:

```
style "clearlooks-menubar"
{
	bg[SELECTED] = @selected_bg_color
	bg[NORMAL]   = "#3C3C3C"
	bg[PRELIGHT] = @selected_bg_color
	bg[ACTIVE]   = "#333333"
	bg[INSENSITIVE] = "#3C3C3C"
	fg[NORMAL]   = "#D4D4D4"
	fg[PRELIGHT] = @selected_fg_color
	fg[SELECTED] = @selected_fg_color
	fg[ACTIVE]   = @selected_fg_color
	fg[INSENSITIVE] = "#666666"
	text[NORMAL]   = @text_color
	text[PRELIGHT] = lighter (@selected_bg_color)
	text[SELECTED] = lighter (@selected_bg_color)
	text[ACTIVE]   = lighter (@selected_bg_color)
	text[INSENSITIVE] = "#666666"
	
	engine "clearlooks"
	{
		hint	= "menubar"
		radius	= 2.0
	}
}
```

And replace it by:

```
style "clearlooks-menubar"
{
	engine "clearlooks"
	{
		hint	= "menubar"
		radius	= 2.0
	}
}
```

Then it SHOULD work. I didn't test that yet, though. I might publish a version of ClearGlow with normal menubars after I test it and if I find it works, aesthetically speaking. Let me know if my suggestion worked, too.

---

### Post by EnGorDiaz on 2008-08-31
> **Prefix100 said:**
> Heres mine, although still 7 minutes 'till the first for me =D

wtf lol :P the wallpaper

---

### Post by Prefix100 on 2008-08-31
> **EnGorDiaz said:**
> wtf lol :P the wallpaper

You act like you've never seen a floating 'phant before =D.

---

### Post by OutOfReach on 2008-08-31
New month, new look. :)
GTK Theme: Shiki-Colors, Shiki-Brave
Icons: GNOME-Brave (part of Gnome-Colors)
Emerald Theme: Shiki-Brave (Came included with Shiki-Colors)
Wallpaper: The infamous wallpaper used by willwill in that mockup

---

### Post by KneeTie on 2008-08-31
> **What is in a name? said:**
> A question I didn't arrive on time to answer, from the last month's screenshots thread:



Basically, all you'd have to do is find the section saying:

```
style "clearlooks-menubar"
{
	bg[SELECTED] = @selected_bg_color
	bg[NORMAL]   = "#3C3C3C"
	bg[PRELIGHT] = @selected_bg_color
	bg[ACTIVE]   = "#333333"
	bg[INSENSITIVE] = "#3C3C3C"
	fg[NORMAL]   = "#D4D4D4"
	fg[PRELIGHT] = @selected_fg_color
	fg[SELECTED] = @selected_fg_color
	fg[ACTIVE]   = @selected_fg_color
	fg[INSENSITIVE] = "#666666"
	text[NORMAL]   = @text_color
	text[PRELIGHT] = lighter (@selected_bg_color)
	text[SELECTED] = lighter (@selected_bg_color)
	text[ACTIVE]   = lighter (@selected_bg_color)
	text[INSENSITIVE] = "#666666"
	
	engine "clearlooks"
	{
		hint	= "menubar"
		radius	= 2.0
	}
}
```

And replace it by:

```
style "clearlooks-menubar"
{
	engine "clearlooks"
	{
		hint	= "menubar"
		radius	= 2.0
	}
}
```

Then it SHOULD work. I didn't test that yet, though. I might publish a version of ClearGlow with normal menubars after I test it and if I find it works, aesthetically speaking. Let me know if my suggestion worked, too.


i tried that with clearglow green and the gtk theme looks like windows 95 after i tried it.

---

### Post by Muppeteer on 2008-08-31
My Arch system :)

---

### Post by PilotJLR on 2008-08-31
I like the clean look... other than too many documents on the desktop.

---

### Post by What is in a name? on 2008-08-31
I've been porting ClearGlow to the SVN version of the Murrine engine. In fact, considering that I want to keep the current, fully standard-compatible ClearGlow, perhaps I could call this new idea MurrineGlow, dunno. Two of the available colors. I'm using the pink one now:

[[img]http://xs230.xs.to/xs230/08350/ecra556.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs230&d=08350&f=ecra556.png) [[img]http://xs130.xs.to/xs130/08350/ecra2339.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs130&d=08350&f=ecra2339.png)

The **new** Murrine is probably the best engine that GTK+ ever had. I love those textures and the way colors ended up looking like, and, and, and... :p

---

### Post by What is in a name? on 2008-08-31
> **KneeTie said:**
> i tried that with clearglow green and the gtk theme looks like windows 95 after i tried it.

OK. As I said, I didn't test that myself, for the reasons implied in the post I just published before this one. I will take a look on that. Sorry.

---

### Post by raul_ on 2008-08-31
Just a repost from last month. I like to show off

---

### Post by Koori23 on 2008-08-31
Elegant Dark Gray GTK theme

Opera 9.52

HandleGotD font

---

### Post by perfectska04@hotmail.com on 2008-08-31
> **What is in a name? said:**
> 
The **new** Murrine is probably the best engine that GTK+ ever had. I love those textures and the way colors ended up looking like, and, and, and... :p

Murrine SVN is great, but there's still at least two bugs that are real show-stoppers. One would be that a ton of options haven't been ported to its clearlooks/nodoka styles and the other thing is that it still doesn't have the nice outlines (that clearlooks and nodoka have) instead of ugly dotted lines. I'm sure once these get fixed there will be no more reason to use anything else, but the developer hasn't released a snapshot in months so I've no idea where development is headed.

---

### Post by What is in a name? on 2008-08-31
> **perfectska04@hotmail.com said:**
> Murrine SVN is great, but there's still at least two bugs that are real show-stoppers. One would be that a ton of options haven't been ported to its clearlooks/nodoka styles and the other thing is that it still doesn't have the nice outlines (that clearlooks and nodoka have) instead of ugly dotted lines. I'm sure once these get fixed there will be no more reason to use anything else, but the developer hasn't released a snapshot in months so I've no idea where development is headed.

Yeah, those dotted lines, you're right! I never liked them. I hope Cimitan gets rid of them soon. The Murrine style with the right gradients does a good impersonation of Clearlooks, though, I think, the Nodoka style doesn't seem to do much more besides a certain liquid look in some selected areas. And that's something the highlight_ratio parameter always allowed to do anyway. Let's hope...

---

### Post by KneeTie on 2008-08-31
> **What is in a name? said:**
> OK. As I said, I didn't test that myself, for the reasons implied in the post I just published before this one. I will take a look on that. Sorry.
No prob. just letting you know  , anyways great theme , and could you tell me the name of your icon theme ?

---

### Post by voteforpedro36 on 2008-08-31
[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_8-31-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/8-31-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_8-31-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/8-31-08-media.png)

From just a minute ago in the August one.

---

### Post by What is in a name? on 2008-08-31
> **KneeTie said:**
> No prob. just letting you know  , anyways great theme , and could you tell me the name of your icon theme ?

It's Eikon, a personal collection of many icons from several sets that I found across the Web since June last year, when i started using Linux.

---

### Post by SomeGuyDude on 2008-08-31
GTK: ClearGlow Brave
Icons: Gnome-Look Brave
Pointer - Grounation
MPD + Sonata
AWN - Liquid Black Glass
Font - UnDotum
Conky - Two of 'em
Wallpaper - Something off of DA, the link was in the August thread.

---

### Post by herbster on 2008-08-31
[[img]http://img175.imageshack.us/img175/7037/desktop083108combinedthib2.png[/img]](http://herbster.deviantart.com/art/Desktop-09-01-08-96655748)

---

### Post by Giant Speck on 2008-08-31
> **What is in a name? said:**
> I've been porting ClearGlow to the SVN version of the Murrine engine. In fact, considering that I want to keep the current, fully standard-compatible ClearGlow, perhaps I could call this new idea MurrineGlow, dunno. Two of the available colors. I'm using the pink one now:

[[img]http://xs230.xs.to/xs230/08350/ecra556.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs230&d=08350&f=ecra556.png) [[img]http://xs130.xs.to/xs130/08350/ecra2339.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs130&d=08350&f=ecra2339.png)

The **new** Murrine is probably the best engine that GTK+ ever had. I love those textures and the way colors ended up looking like, and, and, and... :p

I don't even like pink, but I have to say the pink one looks fantastic!

---

### Post by Yes on 2008-08-31
> **herbster said:**
> [[img]http://img175.imageshack.us/img175/7037/desktop083108combinedthib2.png[/img]](http://herbster.deviantart.com/art/Desktop-09-01-08-96655748)

Very nice.  How do you get Google to look like that?

---

### Post by XVII on 2008-08-31
> **herbster said:**
> [[img]http://img175.imageshack.us/img175/7037/desktop083108combinedthib2.png[/img]](http://herbster.deviantart.com/art/Desktop-09-01-08-96655748)

Could you tell me the name of the terminal program that you are using to monitor your internet connection?

---

### Post by Patricrawley on 2008-08-31
September theme. More vibrant than usual.

Wallpaper: Sunburn 2
Emerald: Burnt (Made myself)
GTK: Customized clearlooks
Icons: Foxtrot

---

### Post by Bachstelze on 2008-08-31
Bow before your queen, /c/!

Oops, I got them mixed up... or did I?

---

### Post by perfectska04@hotmail.com on 2008-08-31
> **HymnToLife said:**
> Bow before your queen, /c/!

Oops, I got them mixed up... or did I?

You can **never** go wrong with a Yotsuba desktop. (Edit: Even if it's vistaids.)

---

### Post by etnlIcarus on 2008-09-01
Win:

[[IMG]http://img98.imageshack.us/img98/4871/desklae7.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=desklae7.jpg)

*nix:

[[IMG]http://img401.imageshack.us/img401/5292/screennixcl8.th.jpg[/IMG]](http://img401.imageshack.us/my.php?image=screennixcl8.jpg)

---

### Post by Truedream on 2008-09-01
Theme: Clearlooks
Icons: Eikon
Wall: Marionette

[[IMG]http://img84.imageshack.us/img84/7985/screenshotpf7.th.png[/IMG]](http://img84.imageshack.us/my.php?image=screenshotpf7.png) [[IMG]http://img502.imageshack.us/img502/5228/screenshot2fl7.th.png[/IMG]](http://img502.imageshack.us/my.php?image=screenshot2fl7.png)

---

### Post by Hund on 2008-09-01
[[IMG]http://tn3-2.deviantart.com/fs37/300W/f/2008/243/7/0/704571296662c40b6e497982de8d9e42.png[/IMG]](http://ebupof.deviantart.com/art/My-Desktop-080830-96467346)

Info in the screenshot.

---

### Post by eightmillion on 2008-09-01
I've been working on my steampunkish theme. The pocket watch actually tells the time and clicking on the compass brings up the kmenu.

---

### Post by Sand Lee on 2008-09-01
[SIZE="2"]***Death Note***[/SIZE]
[SIZE="1"]*A desktop based off the anime...*[/SIZE]
Theme: [ClearGlow]("http://gnome-look.org/content/show.php/ClearGlow?content=88122")

**Update:**
I've had a change of heart. Current desktop:
Icons: Somatic
Theme: Shiki-Brave
Wall : Fall by David Lanham

---

### Post by Trail on 2008-09-01
I am still using this:

(Stock KDE4 with a few more plasmoids from repos)

---

### Post by Barrucadu on 2008-09-01
[center][[img]http://blog.yarrt.com/wp-content/screenshots/september-2008-thumb.png[/img]](http://blog.yarrt.com/wp-content/screenshots/september-2008.png)[/center]

**GTK Theme:** LiteGNOME (modified)
**Icon Theme:** Minimal Perception Glossy
**Emerald Theme:** DarkLegacyMod
**Fonts:** Anorexia (emerald), Nimbus Sans L (applications & documents), Liberation Sans (desktop), Anorexia (fixed width)

---

### Post by billgoldberg on 2008-09-01
> **eightmillion said:**
> I've been working on my steampunkish theme. The pocket watch actually tells the time and clicking on the compass brings up the kmenu.

I wouldn't use it, but it looks nice and original.

---

### Post by Hells_Dark on 2008-09-01
[[img]http://pix.nofrag.com/6/8/c/537b53a9edefb672b23aa17ff998a.png[/img]](http://pix.nofrag.com/a/3/a/0426080de6254ebb68d5b4cf8ae3c.jpg)

---

### Post by What is in a name? on 2008-09-01
> **eightmillion said:**
> I've been working on my steampunkish theme. The pocket watch actually tells the time and clicking on the compass brings up the kmenu.

The kind of concept you're applying in your desktop could be used in so many ways that it really excites me. And I'm glad KDE 4 is ready to allow that kind of original, unique look. I worry about the apparent lack of room in the screen with all those widgets, being the notification tray plasmoid the most critical example to me (I like to have it always visible somewhere, to easily click on any of the tray icons in case they start flashing with an update alert or something) and also the lack of a tasklist, but then again, considering your screen has the same resolution as mine, I guess it's not too much of a problem. I really love that "age of Discoveries" look. So I might try that one day. There are so many visual metaphors made possible by KDE4.

KDE4 really is qualifying itself to gradually become the "professional-looking" desktop environment in the open source world.

Where did you get the pictures of the compass and the pocket clock from, by the way?

---

### Post by el mariachi on 2008-09-01
WhatIIAN: have you released your murrine theme or is it still a wip? ;D if you need beta testing you know where to look hehe

---

### Post by What is in a name? on 2008-09-01
> **el mariachi said:**
> WhatIIAN: have you released your murrine theme or is it still a wip? ;D if you need beta testing you know where to look hehe

Well, I'm thinking of releasing it today, or as soon as possible anyway. I'm still "intensively" using it in order to find out if it can be safely released without major disappointments.

I'm glad it pleased you, by the way, hehe.

---

### Post by el mariachi on 2008-09-01
it did :D 
dunno if it'll make me switch from aurora-based glow (I made my own version, with other colors), I love the fading effect of buttons and check boxes

---

### Post by ayoli on 2008-09-01
> **el mariachi said:**
> it did :D 
dunno if it'll make me switch from aurora-based glow (I made my own version, with other colors), I love the fading effect of buttons and check boxes

I made my own version of glow with murrine svn engine (see first post in this thread). 
Actually I love it, it is fast and doesn't have the issue you can have with aurora in some apps, but I prefer the aurora entry boxes.

---

### Post by urukrama on 2008-09-01
Awesome 2.3. Details in the second screenshot. The wallpaper and the Gtk theme (which is not visible) are homemade.

---

### Post by Prefix100 on 2008-09-01
> **etnlIcarus said:**
> Win:

[[IMG]http://img98.imageshack.us/img98/4871/desklae7.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=desklae7.jpg)

how.
how..
how did you get windows to look like that?

---

### Post by MrSweet on 2008-09-01
> **Prefix100 said:**
> how.
how..
how did you get windows to look like that?

I was wondering the same thing.  I have never seen a Win Desktop that looked like that.  Just having the multiple workspaces would be a plus.  That  is something I always miss whenever I have to drop back into Windows.  Linux is spoiling me.  :)

Mr. Sweet

---

### Post by rpainter on 2008-09-01
Here's mine.

Background is from Gnome-Look
Icons are UltimateGnome
Running AWN
Window XP running in VirtualBox on the right side of cube.

Hope you like it.

---

### Post by tehforum on 2008-09-01
> **EnGorDiaz said:**
> my desktop as is in the screenshot

Wow, where did you get the theme from?

> **PilotJLR said:**
> I like the clean look... other than too many documents on the desktop.

What wallpaper is that?

---

### Post by billgoldberg on 2008-09-01
> **MrSweet said:**
> I was wondering the same thing.  I have never seen a Win Desktop that looked like that.  Just having the multiple workspaces would be a plus.  That  is something I always miss whenever I have to drop back into Windows.  Linux is spoiling me.  :)

Mr. Sweet

I think it's just one of those skins applied by cpu hogging third party apps.

I doubt he has real multiple wordspaces.

---

### Post by Nevon on 2008-09-01
> **billgoldberg said:**
> I think it's just one of those skins applied by cpu hogging third party apps.

I doubt he has real multiple wordspaces.

I think he's probably changed window manager from Explorer to openbox or some other *box. My ex-girlfriend did that on her laptop.

---

### Post by etnlIcarus on 2008-09-01
> **billgoldberg said:**
> My current gnome desktop with compiz fusion.

I also added a screenshot from Boxee while listening to my favorite hardcore track of all time on last.fm, just because I can.

I don't know about you, but I find it more pleasing to look at the face of Charlize Theron than some blue stripes or wood....could you hook me up with wallpaper #2? <.<

> **Prefix100 said:**
> how.
how..
how did you get windows to look like that?

> **MrSweet said:**
> I was wondering the same thing.  I have never seen a Win Desktop that looked like that.  Just having the multiple workspaces would be a plus.  That  is something I always miss whenever I have to drop back into Windows.  Linux is spoiling me.  :)

Mr. Sweet

> **billgoldberg said:**
> I think it's just one of those skins applied by cpu hogging third party apps.

I doubt he has real multiple wordspaces.

Real multiple workspaces and no, it doesn't technically hog my cpus. The bblean code base does have some minor memory management issues but all the bb4win variants replace the explorer shell, rather than running over it like Window Blinds.

[http://www.lostinthebox.com/viewtopic.php?f=3&t=2907](http://www.lostinthebox.com/viewtopic.php?f=3&t=2907)
[http://bb4win.sourceforge.net/plugins.html](http://bb4win.sourceforge.net/plugins.html)

File manager is A43 (A34?) if anyone's wondering.

---

### Post by Prefix100 on 2008-09-01
> **etnlIcarus said:**
> 
Real multiple workspaces and no, it doesn't technically hog my cpus. The bblean code base does have some minor memory management issues but all the bb4win variants replace the explorer shell, rather than running over it like Window Blinds.

[http://www.lostinthebox.com/viewtopic.php?f=3&t=2907](http://www.lostinthebox.com/viewtopic.php?f=3&t=2907)
[http://bb4win.sourceforge.net/plugins.html](http://bb4win.sourceforge.net/plugins.html)

File manager is A43 (A34?) if anyone's wondering.

Cya guys!

---

### Post by Shippou on 2008-09-01
Here is my desktop at the moment.

---

### Post by billgoldberg on 2008-09-01
> **etnlIcarus said:**
> ...could you hook me up with wallpaper #2? <.<







Real multiple workspaces and no, it doesn't technically hog my cpus. The bblean code base does have some minor memory management issues but all the bb4win variants replace the explorer shell, rather than running over it like Window Blinds.

[http://www.lostinthebox.com/viewtopic.php?f=3&t=2907](http://www.lostinthebox.com/viewtopic.php?f=3&t=2907)
[http://bb4win.sourceforge.net/plugins.html](http://bb4win.sourceforge.net/plugins.html)

File manager is A43 (A34?) if anyone's wondering.

Oh I thought it was WindowsBlinds. 

I've done the shell thing before, it's still windows :p

--

The wallpaper came from skins.be, but I've uploaded it because I can't be bother to search for it on their site.

[Link]("http://linuxowns.files.wordpress.com/2008/09/2.jpg").

---

### Post by Dark Hornet on 2008-09-01
I am running Ubuntu 8.04 x64 on a dual monitor set up (24", and 22") using Twinview...my desktop is as follows..

--Compiz Fusion with the additional plugins enabled (sphere, etc)
--Slickness Black as a Theme--I got this from [www.gnome-look.org](www.gnome-look.org)
--Random icon set from gnome-look (I can't remember the exact name at the moment.)
--Desktop is a lightning pic that I found from a post on Tombunutu's Blog I think...great shot..or (Photoshop job...:))

At anyrate, I like it for now, but I am sure I will change it in a week or two, as I am prone to do...

Darkhornet

---

### Post by etnlIcarus on 2008-09-01
> **billgoldberg said:**
> Oh, I didn't knew that could be done in Windows.

--

The wallpaper came from skins.be, but I've uploaded it because I can't be bother to search for it on their site.


[Link]("http://linuxowns.files.wordpress.com/2008/09/2.jpg").
For the whole workspaces on windows thing, interestingly enough, MS released the *Virtual Desktop Manager* as a powertoy. However, it's rather limited in functionality (can't move windows between workspeaces, etc).

And cheers for the wall.

---

### Post by tehforum on 2008-09-01
Here is my desktop.

---

### Post by adityakavoor on 2008-09-01
> **Prefix100 said:**
> Heres mine, although still 7 minutes 'till the first for me =D

PLease share the wallapaper

---

### Post by BLTicklemonster on 2008-09-01
Three shots of Ubuntu Gnome, awn, compiz with different background on one of them. 

[[IMG]http://img174.imageshack.us/img174/8241/screenshotex8.th.png[/IMG]](http://img174.imageshack.us/my.php?image=screenshotex8.png)

[[IMG]http://img174.imageshack.us/img174/9035/screenshot1zz7.th.png[/IMG]](http://img174.imageshack.us/my.php?image=screenshot1zz7.png)

[[IMG]http://img384.imageshack.us/img384/2865/screenshotym4.th.png[/IMG]](http://img384.imageshack.us/my.php?image=screenshotym4.png)

Forgive me on the last one. I used an OzOs wallpaper with my own twist to it. "earthrise from the moon"

---

### Post by Prefix100 on 2008-09-01
> **adityakavoor said:**
> PLease share the wallapaper

Here you are.

I got it off [digg]("http://digg.com/arts_culture/What_an_Elephant_Can_Do_at_18_000_KM_from_Earth_PIC") the other day.

Enjoy!

---

### Post by skitzware on 2008-09-01
[[IMG]http://img383.imageshack.us/img383/5137/sshotud1.th.png[/IMG]](http://img383.imageshack.us/my.php?image=sshotud1.png)

Openbox, Pypanel, Conky

Openbox theme by me
GTK theme Royalty by thrynk at dev-art

---

### Post by chucky chuckaluck on 2008-09-01
openbox, pypanel, nova-gold gtk and ob themes, firefox. the wallpaper is a tiling of a franz xaver messerschmidt bust. he was a 18th century german sculptor whose most famous works, busts of himself with a variety of grimaces, were thought to be unfortunately inspired by the paranoid delusions and hallucinations he began to suffer around the age of thirty. in my view, there is an underpinning of sarcasm in his work and i suspect he might have been playing his audience a bit. either way, it's a singular output that i've enjoyed for a long time.

[[IMG]http://b.imagehost.org/t/0970/franzscr2.jpg[/IMG]](http://b.imagehost.org/view/0970/franzscr2.jpg)

---

### Post by BOBSONATOR on 2008-09-01
> **What is in a name? said:**
> I've been porting ClearGlow to the SVN version of the Murrine engine. In fact, considering that I want to keep the current, fully standard-compatible ClearGlow, perhaps I could call this new idea MurrineGlow, dunno. Two of the available colors. I'm using the pink one now:

[[img]http://xs230.xs.to/xs230/08350/ecra556.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs230&d=08350&f=ecra556.png) [[img]http://xs130.xs.to/xs130/08350/ecra2339.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs130&d=08350&f=ecra2339.png)

The **new** Murrine is probably the best engine that GTK+ ever had. I love those textures and the way colors ended up looking like, and, and, and... :p

Might I Ask,

Where do you find murrine svn?

---

### Post by etnlIcarus on 2008-09-01
Heavily inspired by one of the last screenshots posted in last month's thread. Can't remember which user posted it and I can't find the August thread so if your name is Daniel and that's your screenshot visible in my screenshot; thankyou for the inspiration and sorry for the lack of credit.


[url=http://img58.imageshack.us/img58/5640/newscreenlt6.jpg][img]http://img58.imageshack.us/img58/2402/newscreensmallsh4.jpg[/img]
http://img58.imageshack.us/img58/5640/newscreenlt6.jpg[/url]

---

### Post by herbster on 2008-09-01
> **Yes said:**
> Very nice.  How do you get Google to look like that?

It's using the Stylish extension, one of the Google userstyles.

> **XVII said:**
> Could you tell me the name of the terminal program that you are using to monitor your internet connection?

nload.

---

### Post by What is in a name? on 2008-09-01
> **BOBSONATOR said:**
> Might I Ask,

Where do you find murrine svn?

You either use Subversion for yourself to get the engine, typing this command on the terminal...

```
svn checkout http://svn.gnome.org/svn/murrine/trunk/ murrine
```

... and then compiling the engine...

```
cd murrine
./autogen.sh --enable-animation [NOTE: add --prefix=/usr too, if you wish]
make
sudo make install

```

... or if you are using Ubuntu, you can find a repos with some .deb packages and download and install the one that suits your PC's architecture. I, for instance, am using a package I downloaded from the following PPA: [http://ppa.launchpad.net/kwwii/ubuntu/pool/main/g/gtk2-engines-murrine/](http://ppa.launchpad.net/kwwii/ubuntu/pool/main/g/gtk2-engines-murrine/)

---

### Post by supersonicdarky on 2008-09-01
[[IMG]http://img.photobucket.com/albums/v242/supersonicdarky/september_08_thumb.png[/IMG]](http://supersonicdarky.deviantart.com/art/September-2008-96711189)
wall: no idea
gtk: vorta
icons: micro
openbox: bright side (modded)

pcmanfm, transmission (I'm working on that ratio...), pidgin, gmplayer, conky, pypanel

---

### Post by dhysk on 2008-09-01
I posted my laptops last month so i figured I'd post my desktops this month.

Unfortunately my video card sucks to bad to use compiz with dual screens so I'm using metacity.

My first monitor is 19 in but my second monitor is only 15 in.  So the screen shot with windows xp is actually taking up the whole screen.  In the second shot you can tell how long the screen is by the bar at the top and the bottom of the screen is right under the date.

---

### Post by BOBSONATOR on 2008-09-01
well, here is my shot at the glow frenzy :)

thanks What is in a name?

---

### Post by earthpigg on 2008-09-01
just threw this one together in kolorpaint for myself.

nothing really groundbreaking, but i thought i'd share :)

intended for those with 2 monitors: 1050x3360

if anyone has a blue or icy ubuntu logo to match her eyes, that would be awesome.

thumb:
[IMG]http://i109.photobucket.com/albums/n59/earthpiglite/ubuntudarkthumb.jpg[/IMG]

full size 1050x3360, about 500k:
[http://i109.photobucket.com/albums/n59/earthpiglite/ubuntudark-1.jpg](http://i109.photobucket.com/albums/n59/earthpiglite/ubuntudark-1.jpg)

---

### Post by Raffles10 on 2008-09-01
My Linux Mint desk, no fancy effects, I like to keep things simple.

---

### Post by KneeTie on 2008-09-01
September desktop : Some influences from What is in a name ? great themer.

---

### Post by fedex1993 on 2008-09-01
> **earthpigg said:**
> just threw this one together in kolorpaint for myself.

nothing really groundbreaking, but i thought i'd share :)

intended for those with 2 monitors: 1050x3360

if anyone has a blue or icy ubuntu logo to match her eyes, that would be awesome.

thumb:
[IMG]http://i109.photobucket.com/albums/n59/earthpiglite/ubuntudarkthumb.jpg[/IMG]

full size 1050x3360, about 500k:
[http://i109.photobucket.com/albums/n59/earthpiglite/ubuntudark-1.jpg](http://i109.photobucket.com/albums/n59/earthpiglite/ubuntudark-1.jpg)
backgrounds i want :) where did you get them from ?

---

### Post by eightmillion on 2008-09-01
> **What is in a name? said:**
> The kind of concept you're applying in your desktop could be used in so many ways that it really excites me. And I'm glad KDE 4 is ready to allow that kind of original, unique look. I worry about the apparent lack of room in the screen with all those widgets, being the notification tray plasmoid the most critical example to me (I like to have it always visible somewhere, to easily click on any of the tray icons in case they start flashing with an update alert or something) and also the lack of a tasklist, but then again, considering your screen has the same resolution as mine, I guess it's not too much of a problem. I really love that "age of Discoveries" look. So I might try that one day. There are so many visual metaphors made possible by KDE4.

KDE4 really is qualifying itself to gradually become the "professional-looking" desktop environment in the open source world.

Where did you get the pictures of the compass and the pocket clock from, by the way?

Thanks. When people talk of space on the desktop, I'm always wondering, space for what? For me the desktop is the jumping off point, the launching area. I recently installed Ubuntu netbook remix in a virtual machine and I was really impressed how well it works even on a full size computer. With it, there is no desktop at all, just a launch area and your applications. It's quite interesting.

 As for your concerns about the system tray, the popups actually pop up over all the desktop windows, and I can hit a button at any time to minimize all windows. It's not much different than running a panel that autohides. I just wish they'd fix the drawing issues with it so it doesn't look so ugly. Also, I actually do have a tasklist. I'm using cairo dock set to auto hide. I originally started using it because I didn't like that I couldn't hide the kde4 panel, but now I don't see myself going back even when they do add that functionality. Between cairo dock, yakuake and krunner, I rarely even use the kmenu. 

I'm really impressed with KDE 4. You can put anything anywhere. It's all modular. If you don't like how an application's laid out, you can move it all around on the fly just by picking up a part of an application and dropping it somewhere else. I may have to make a video of this, because I've never seen it demoed anywhere.

I found the compass and pocket watch on Google image search. I cut them out and added drop shadow so that they'd look realistic on the desktop. I can upload the cutouts with or without shadow if you'd like.

---

### Post by Caseyjp on 2008-09-01
My September Look:

Hardy 8.04
Theme:
GTK 2+
Orange -LiNstaBlackPlastic
Icons - black-white 2 Neon
Pointer - DMZ-Black
Compiz .7.6 + Emerald window manager
Theme: Overglossed 
wallpaper - from Interfacelift.com
AWN - latest trunk
Screenlets - .1.2

---

### Post by kamitsukai on 2008-09-01
Here's my September desktop :)

---

### Post by dbbolton on 2008-09-01
> **etnlIcarus said:**
> Heavily inspired by one of the last screenshots posted in last month's thread. Can't remember which user posted it and I can't find the August thread so if your name is Daniel and that's your screenshot visible in my screenshot; thankyou for the inspiration and sorry for the lack of credit.


[url=http://img58.imageshack.us/img58/5640/newscreenlt6.jpg][img]http://img58.imageshack.us/img58/2402/newscreensmallsh4.jpg[/img]
http://img58.imageshack.us/img58/5640/newscreenlt6.jpg[/url]
I'm Daniel. Our screenshots go well together :D

---

### Post by earthpigg on 2008-09-01
> **fedex1993 said:**
> backgrounds i want :) where did you get them from ?

4chan, of all places. ;)

---

### Post by el mariachi on 2008-09-01
lol biggest site on the web xD

---

### Post by eightmillion on 2008-09-01
> **earthpigg said:**
> just threw this one together in kolorpaint for myself.

nothing really groundbreaking, but i thought i'd share :)

intended for those with 2 monitors: 1050x3360

if anyone has a blue or icy ubuntu logo to match her eyes, that would be awesome.

thumb:
[IMG]http://i109.photobucket.com/albums/n59/earthpiglite/ubuntudarkthumb.jpg[/IMG]

full size 1050x3360, about 500k:
[http://i109.photobucket.com/albums/n59/earthpiglite/ubuntudark-1.jpg](http://i109.photobucket.com/albums/n59/earthpiglite/ubuntudark-1.jpg)

How is this for an icy blue ubuntu logo?

---

### Post by Drone4four on 2008-09-01
Check out Ubuntu developer Sayak Banerjee's panel in _[this]("http://i30.tinypic.com/2ni8gnr.jpg")_ screenshot of his desktop.  I spotted this screenshot on _[a blog entry dated 7 July]("http://sayakb.blogspot.com/2008/07/blank.html")_.  How do I make my panel look like Sayak Banerjee's?

---

### Post by earthpigg on 2008-09-01
> **eightmillion said:**
> How is this for an icy blue ubuntu logo?

that'll work! ty

---

### Post by elmer_42 on 2008-09-01
Finally got around to working on a new desktop. I'm saying it's minimalistic, but that's just a fancy way of saying half-baked :lol:

If anybody wants any more information about this, feel free to PM me, I'd love to answer any questions you have.
```
 Ubuntu 8.04.1
 
 Openbox:  BlackWhite
 Apps:     Openbox, PyPanel, Conky, xcompmgr
           Firefox, Qalculate, AbiWord
 Gtk:      BlackWhite
 Icons:    ALLBLACK
 Wall:     Self made
 Fonts:    AquaBase, Lucida, Bitstream
```
[[img]http://arch.kimag.es/resized/51341480.png[/img]](http://arch.kimag.es/share/51341480.png)

[[img]http://arch.kimag.es/resized/85268275.png[/img]](http://arch.kimag.es/share/85268275.png)

---

### Post by Neurotripsick on 2008-09-01
here's mine.

xfce
gtk & emerald: shiki-human
wallpaper comes from mandolux.com
icons: gnome-colors human

---

### Post by cardinals_fan on 2008-09-01
@elmer_42: Nice one!

---

### Post by Dark Hornet on 2008-09-01
> **dhysk said:**
> I posted my laptops last month so i figured I'd post my desktops this month.

Unfortunately my video card sucks to bad to use compiz with dual screens so I'm using metacity.

My first monitor is 19 in but my second monitor is only 15 in.  So the screen shot with windows xp is actually taking up the whole screen.  In the second shot you can tell how long the screen is by the bar at the top and the bottom of the screen is right under the date.

Can you link to your background...I like it!

Darkhornet

---

### Post by elmer_42 on 2008-09-01
> **cardinals_fan said:**
> @elmer_42: Nice one!
Thanks, I'm glad you like it. I was looking around for a more artsy wallpaper, but I couldn't find one that quite matched the rest of the desktop. I've dabbled around making wallpapers before, and when I found out that you could get the font Ubuntu used for it's logo I decided to do this. I'm considering adding some color, maybe a little glow, but I kind of like how simple it is.

---

### Post by JillSwift on 2008-09-01
After my last dark theme I decided that I like milk. Yes. Milk! With a little blue for color.

---

### Post by chucky chuckaluck on 2008-09-01
openbox, pypanel (deadbinkies font). don't remember where i got the wallpaper or even what it originally looked like.

[[IMG]http://b.imagehost.org/t/0869/handscr.jpg[/IMG]](http://b.imagehost.org/view/0869/handscr.jpg)

---

### Post by RiceMonster on 2008-09-01
> **JillSwift said:**
> After my last dark theme I decided that I like milk. Yes. Milk! With a little blue for color.

Very nice.

---

### Post by JillSwift on 2008-09-01
> **RiceMonster said:**
> Very nice.=^_^= Thanks!

---

### Post by BlackLLama on 2008-09-01
not on my machine currently, but i do have this [http://www.youtube.com/watch?v=frpHI0hb1kI](http://www.youtube.com/watch?v=frpHI0hb1kI)

---

### Post by perfectska04@hotmail.com on 2008-09-01
This is my desktop for September. Not much out of the ordinary, just the latest versions of my Shiki-Colors GTK and GNOME-Colors icons with some screenlets to the sides. I am, however, trying out my new GDM and an incredible companion cube wallpaper.

---

### Post by What is in a name? on 2008-09-02
> **perfectska04@hotmail.com said:**
> This is my desktop for September. Not much out of the ordinary, just the latest versions of my Shiki-Colors GTK and GNOME-Colors icons with some screenlets to the sides. I am, however, trying out my new GDM and an incredible companion cube wallpaper.

Sufjan Stevens :KS
Awesome.

---

### Post by OZFive on 2008-09-02
Nothing too creative but I do so think that THIS theme should be 8.10 Intrepid Ibex

Here is my WillWill100 Intrepid Ibex Desktop...

Emerald: 86854-Intrepid Will-mod
GTK2: Willibex-Dark
Icons: Gnome-Human
Font: Lucida Sans
Background: Ibex Wallpaper - WillWill100
Cairo Dock

---

### Post by chucky chuckaluck on 2008-09-02
switched from firefox to opera, so i had to match the theming a little more. i changed the orange color in elegant brit to blue. the icons are vista. openbox and pypanel. don't know where i got the pic for the wallpaper.

[[IMG]http://b.imagehost.org/t/0231/peasscr.jpg[/IMG]](http://b.imagehost.org/view/0231/peasscr.jpg) [[IMG]http://b.imagehost.org/t/0431/peasscr2.jpg[/IMG]](http://b.imagehost.org/view/0431/peasscr2.jpg)

---

### Post by Chibone on 2008-09-02
Inspired by OutOfReach for the most part...just different wallpaper

GTK: Shiki-Colors, Shiki-Brave
Icons: GNOME-Brave (part of Gnome-Colors)
Emerald Theme: Shiki-Brave (Came included with Shiki-Colors)
Wallpaper: OS X Server Aurora

[ATTACH]83728[/ATTACH]

---

### Post by PurposeOfReason on 2008-09-02
Minor changes to conky and added a tray. It looks out of place but is useful for pidgin and sonata. Any ideas to make it fit? Or ways to manage those apps?

Had to slightly resize the image and it went blurry. Sorry.

---

### Post by TheSlipstream on 2008-09-02
Ubuntu, with XP as a guest Virtual Box. I just need that sweet, sweet creative suite. Mmm... unholy desktop...

GTK/Metacity: Nodoka Brave Compact
Icons: Elementary

Gotta remember to theme XP, such an eyesore. Unfortunately, it doesn't work right with Compiz, goodbye sweet Emerald. We shall meet again.

---

### Post by armageddon08 on 2008-09-02
These are mine for the month: 
1. KDE-Desktop: Glassified theme
2. GNOME-Desktop: Futurelooks2 theme
3. GNOME with Compiz-Fusion
4. XFCE-Desktop: Dr. Aqua-Vista theme

Quite simplistic this time!:)

---

### Post by lode on 2008-09-02
I've got a quick and probably easy question (which, I thought, I might as well ask here). How do you disable the opacity of window decorations (of inactive windows)? The answer can't be too difficult, I still can't seem to find it, however...

---

### Post by Prefix100 on 2008-09-02
> **PurposeOfReason said:**
> Minor changes to conky and added a tray. It looks out of place but is useful for pidgin and sonata. Any ideas to make it fit? Or ways to manage those apps?

Had to slightly resize the image and it went blurry. Sorry.

I want a desktop like that.

---

### Post by What is in a name? on 2008-09-02
> **lode said:**
> I've got a quick and probably easy question (which, I thought, I might as well ask here). How do you disable the opacity of window decorations (of inactive windows)? The answer can't be too difficult, I still can't seem to find it, however...

You're using Metacity's compositor, is it?

If so, please open GConf, look at the left pane with the treeview, open the Apps folder and then scroll down to open another folder called gwd. Click on it and look at the options' section. There you'll find an option saying "metacity_theme_opacity". Change its value to 1. It should do the trick.

---

### Post by urukrama on 2008-09-02
Here is my latest Openbox theme and desktop. I'm trying something darker.

Details are in the second screenshot. I forget where the wallpaper is from.

Feedback is welcome :)

---

### Post by el mariachi on 2008-09-02
real dark hehe

---

### Post by What is in a name? on 2008-09-02
MurrineGlow's premiere: [http://www.gnome-look.org/content/show.php?content=88406](http://www.gnome-look.org/content/show.php?content=88406)

---

### Post by dhysk on 2008-09-02
> **Dark Hornet said:**
> Can you link to your background...I like it!

Darkhornet

[http://www.compiz-themes.org/content/show.php/Starry+Death+Valley?content=58369](http://www.compiz-themes.org/content/show.php/Starry+Death+Valley?content=58369)

Its actually a skydome but is perfect for dual screen setup.

---

### Post by lode on 2008-09-02
> **What is in a name? said:**
> You're using Metacity's compositor, is it?

If so, please open GConf, look at the left pane with the treeview, open the Apps folder and then scroll down to open another folder called gwd. Click on it and look at the options' section. There you'll find an option saying "metacity_theme_opacity". Change its value to 1. It should do the trick.

Thanks!

For this post -- and the beautiful theme ;)

(MurrineGlow, Anivers typeface)

---

### Post by BOBSONATOR on 2008-09-02
> **What is in a name? said:**
> MurrineGlow's premiere: [http://www.gnome-look.org/content/show.php?content=88406](http://www.gnome-look.org/content/show.php?content=88406)

Thanks, now i built a desktop around your models. :)

[[img]http://xs331.xs.to/xs331/08362/murrineglow596.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs331&d=08362&f=murrineglow596.png)

---

### Post by PurposeOfReason on 2008-09-02
> **Prefix100 said:**
> I want a desktop like that.
Thank you.

It's not hard. Use XFCE or Gnome with no panels and throw in conky.

---

### Post by What is in a name? on 2008-09-02
> **BOBSONATOR said:**
> Thanks, now i built a desktop around your models. :)

[[img]http://xs331.xs.to/xs331/08362/murrineglow596.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs331&d=08362&f=murrineglow596.png)

Hey, thanks! What's that wallpaper, btw?

---

### Post by el mariachi on 2008-09-02
is that metacity available for xfwm4?

---

### Post by perfectska04@hotmail.com on 2008-09-02
> **What is in a name? said:**
> MurrineGlow's premiere: [http://www.gnome-look.org/content/show.php?content=88406](http://www.gnome-look.org/content/show.php?content=88406)

Looks great. Perhaps one suggestion; try changing the metacity buttons and the panel fonts to a "#D4D4D4" color, since the rest of the fonts in dark areas are that color instead of white. Alternately, you can do it the other way around (turning the D4 colors into white). It's really minor, but it would give off a more consistent look.

---

### Post by What is in a name? on 2008-09-02
> **el mariachi said:**
> is that metacity available for xfwm4?

As far as I know, no, not yet. I definitely want to try to port it. In case someone wants to help on that regard, I'll certainly appreciate.

Really, it disheartens me that there is no Xfwm4 version yet, since I used to dwell around Xfwm4 most of the time until very recently (and I might come back to it again). Most themers seem to ignore the existence of Xfce, and I don't want to make the same mistake.

EDIT: When I started doing themes, for instance, I went to the other extreme: I always took some time to make a Metacity version for them. Perhaps because I never really got around the code.

---

### Post by What is in a name? on 2008-09-02
> **perfectska04@hotmail.com said:**
> Looks great. Perhaps one suggestion; try changing the metacity buttons and the panel fonts to a "#D4D4D4" color, since the rest of the fonts in dark areas are that color instead of white. Alternately, you can do it the other way around (turning the D4 colors into white). It's really minor, but it would give off a more consistent look.

**Thanks** a lot! Yes, good point, and well thought. I will take care of it soon.

When I changed the buttons of the Metacity theme, I originally thought that the original ones were actually white with some transparency level, which was what I tried to reproduce. My mistake, then.

---

### Post by BOBSONATOR on 2008-09-02
> **What is in a name? said:**
> Hey, thanks! What's that wallpaper, btw?

[http://interfacelift.com/wallpaper_beta/details/833/pink_flowers.html](http://interfacelift.com/wallpaper_beta/details/833/pink_flowers.html)
:popcorn:

---

### Post by perfectska04@hotmail.com on 2008-09-02
> **What is in a name? said:**
> **Thanks** a lot! Yes, good point, and well thought. I will take care of it soon.

When I changed the buttons of the Metacity theme, I originally thought that the original ones were actually white with some transparency level, which was what I tried to reproduce. My mistake, then.

No problem. Also, implementing through-border for the new murrine scrollbars is a genius idea. I had the new scrollbars already in Shiki, but it didn't look quite right until I added that tweak.

---

### Post by urukrama on 2008-09-02
> **el mariachi said:**
> real dark hehe

I liked it so dark for about two hours. 

I'm back to my *Children of the Earth* theme, which I absolutely love :)

---

### Post by el mariachi on 2008-09-02
what's the bar below? panel?

---

### Post by urukrama on 2008-09-02
> **el mariachi said:**
> what's the bar below? panel?

It is a combination of bbdock (hacked so its default icon size is 24x24 instead of 64x64), lal, bbpager, and docker, all loaded into Openbox' dock which autohides.

All the icons of bbdock raise (and bring to the current workspace) a running instance of the app and only launch a new one if there is none.

---

### Post by el mariachi on 2008-09-02
cool :D
btw do you know where the desktop launchers are stored? I think they are *.desktop files which are used by xfce4-menu and gnome-menu to display the installed apps.

---

### Post by ayoli on 2008-09-02
> **el mariachi said:**
> cool :D
btw do you know where the desktop launchers are stored? I think they are *.desktop files which are used by xfce4-menu and gnome-menu to display the installed apps.

all .desktop files are stored in /usr/share/applications I believe.

---

### Post by el mariachi on 2008-09-02
that's it thanks!

---

### Post by Prefix100 on 2008-09-02
> **PurposeOfReason said:**
> Thank you.

It's not hard. Use XFCE or Gnome with no panels and throw in conky.

No panels?

That's crazy talk.

---

### Post by PurposeOfReason on 2008-09-02
> **Prefix100 said:**
> No panels?

That's crazy talk.
Give me one good thing that a panel is needed for? I have workspaces, conky, and alt-tab.

---

### Post by Prefix100 on 2008-09-02
> **PurposeOfReason said:**
> Give me one good thing that a panel is needed for? I have workspaces, conky, and alt-tab.

Notification area, and to launch programs?

---

### Post by SomeGuyDude on 2008-09-02
> **PurposeOfReason said:**
> Give me one good thing that a panel is needed for? I have workspaces, conky, and alt-tab.

I'll say this: I haven't found a good replacement for the notification area. AWN lets you use it, but the thing looks goofy as yet.

---

### Post by Prefix100 on 2008-09-02
How do I delete my last panel?

I'm in Gnome.

---

### Post by PurposeOfReason on 2008-09-02
> **Prefix100 said:**
> How do I delete my last panel?

I'm in Gnome.
gnome-session-remove gnome-panel

---

### Post by PurposeOfReason on 2008-09-02
> **SomeGuyDude said:**
> I'll say this: I haven't found a good replacement for the notification area. AWN lets you use it, but the thing looks goofy as yet.
stalonetray
trayer
docker
pypanel

---

### Post by RiceMonster on 2008-09-02
> **Prefix100 said:**
> No panels?

That's crazy talk.

No, not really.

> **Prefix100 said:**
> Notification area, and to launch programs?
Notification area is the only one I need, and I use stalonetray in openbox to solve that problem. Just a tray, no panels. Oh, and to launch programs, I use keyboard shortcuts and the root menu (right click on the desktop)

---

### Post by Prefix100 on 2008-09-02
Cheers,

I have to say I am liking this so far.

But what do you use instead of notification area?

EDIT: Is there something similar to stalonetray for gnome?

---

### Post by PurposeOfReason on 2008-09-02
> **Prefix100 said:**
> Cheers,

I have to say I am liking this so far.

But what do you use instead of notification area?
See above. :)

---

### Post by Prefix100 on 2008-09-02
Ok, I'm using Stalonetray now, it's pretty sweet.

```
stalonetray -t --window-layer bottom
```

Heres my Desktop now.

---

### Post by Hells_Dark on 2008-09-02
> **What is in a name? said:**
> MurrineGlow's premiere: [http://www.gnome-look.org/content/show.php?content=88406](http://www.gnome-look.org/content/show.php?content=88406)

My new theme ;)
I told you i love it.

---

### Post by eightmillion on 2008-09-02
I've been working on an icon theme to go with my theme and a slight modification of my window decorations. By the way, What is in a name? do you ever do emerald themes to match your metacity themes?

---

### Post by What is in a name? on 2008-09-02
> **eightmillion said:**
> By the way, What is in a name? do you ever do emerald themes to match your metacity themes?

Well, I'd like to release an Emerald theme for my recent themes, and also a Xfwm4 theme... And an Openbox theme... And a Fluxbox theme... And... You get the idea.

There's so much stuff to do. I'm trying to find time to at least do the first two, while still outlining some ideas for any eventual future GTK themes.

---

### Post by chronographer on 2008-09-02
Got new machine: Q9300, 4gb ddr1066, gtx9800+, 700 gb + 400gb. runs like quicksilver! But needs the intrepid kernel for hard drive controller.

Wanted to chow of virtualbox 'seamless' mode with google chrome, runs faster than firefox 3 (I am being converted rapidly, love firefox, can't wait for Google Chrome native Linux!)

avant, sonata, background fractal from [http://www.deviantart.com/#order=9&q=fractal]("http://www.deviantart.com/#order=9&q=fractal")

---

### Post by perfectska04@hotmail.com on 2008-09-02
> **What is in a name? said:**
> Well, I'd like to release an Emerald theme for my recent themes, and also a Xfwm4 theme... And an Openbox theme... And a Fluxbox theme... And... You get the idea.

There's so much stuff to do. I'm trying to find time to at least do the first two, while still outlining some ideas for any eventual future GTK themes.

You can use my Shiki emerald themes as a base, they should match your metacity well if you replace my buttons for yours. Do tell me if you ever complete an xfwm, since that's the one thing I'm missing and I've no knowledge at all for working with that.

---

### Post by JillSwift on 2008-09-02
> **eightmillion said:**
> I've been working on an icon theme to go with my theme and a slight modification of my window decorations. By the way, What is in a name? do you ever do emerald themes to match your metacity themes?Those icons are gorgeous!

---

### Post by ArtF10 on 2008-09-02
> **JillSwift said:**
> After my last dark theme I decided that I like milk. Yes. Milk! With a little blue for color.

Do you have a link to the Milk theme?  Is it usable with XFCE?

---

### Post by Giant Speck on 2008-09-02
> **chronographer said:**
> Got new machine: Q9300, 4gb ddr1066, gtx9800+, 700 gb + 400gb. runs like quicksilver! But needs the intrepid kernel for hard drive controller.

Wanted to chow of virtualbox 'seamless' mode with google chrome, runs faster than firefox 3 (I am being converted rapidly, love firefox, can't wait for Google Chrome native Linux!)

avant, sonata, background fractal from [http://www.deviantart.com/#order=9&q=fractal]("http://www.deviantart.com/#order=9&q=fractal")

That Virtualbox seamless mode screenshot looks totally awesome!

---

### Post by JillSwift on 2008-09-02
> **ArtF10 said:**
> Do you have a link to the Milk theme?  Is it usable with XFCE?

Window Decoration (KWin): kwin-style-blended (In the repositories)
***XFWM4 version [here]("http://www.xfce-look.org/content/show.php/Blended+Theme+for+XFWM4?content=32838").
Widget Style: [Domino ]("http://www.kde-look.org/content/show.php?content=42804")
***GTK version [here]("http://www.xfce-look.org/content/show.php/G-DOMINO+1.0?content=83372").
Icons: [DarkGlass Reworked]("http://www.kde-look.org/content/show.php?content=67902")
(Couldn't find one for XFCE)

Hope that helps! =^_^=

---

### Post by Giant Speck on 2008-09-03
I've decided that instead of radically changing my theme and colors every couple of weeks, I will work to make my current theme look as perfect as possible.

Emerald:  Ish Aqua (modified)
Icons: Crystal Project
KDE Widget Style:  Serenity
Wallpaper: New York 2011
Font: Calibri Bold 10

---

### Post by chucky chuckaluck on 2008-09-03
pekwm, SONA-red theme, a blue version of elegant-brit gtk, firefox, quodlibet and pypanel.

[[IMG]http://b.imagehost.org/t/0262/pekscr1.jpg[/IMG]](http://b.imagehost.org/view/0262/pekscr1.jpg) [[IMG]http://b.imagehost.org/t/0653/pekscr2.jpg[/IMG]](http://b.imagehost.org/view/0653/pekscr2.jpg)

---

### Post by unca.paka on 2008-09-03
Here it is for September. Didnt think Id like a pink theme, but Ill be damned it works.
Heres to What is in a Name for the gorgeous Murrine theme. Keep up the good work man.

[[IMG]http://img93.imageshack.us/img93/7781/200809022229441680x1050mn0.th.png[/IMG]](http://img93.imageshack.us/my.php?image=200809022229441680x1050mn0.png)

---

### Post by rjmdomingo2003 on 2008-09-03
> **urukrama said:**
> Here is my latest Openbox theme and desktop. I'm trying something darker.

Details are in the second screenshot. I forget where the wallpaper is from.

Feedback is welcome :)
This would definitely fit my wallpaper-less desktop. Fantastic!:KS

---

### Post by blackvd on 2008-09-03
Anyone here know how to change the notebook border color on Tilda? Want to get it from grey to white but not sure how. I checked the config file but it doesnt have a color option.

---

### Post by BOBSONATOR on 2008-09-03
Murrina Glow Pink With rgba enabled, looks nice by me :)

[[img]http://xs131.xs.to/xs131/08363/rgba928.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs131&d=08363&f=rgba928.png)

---

### Post by rangalo on 2008-09-03
> **urukrama said:**
> Here is my latest Openbox theme and desktop. I'm trying something darker.

Details are in the second screenshot. I forget where the wallpaper is from.

Feedback is welcome :)

How do you get that tabbed terminal on the right screenshot with [New][*1][2] .. etc caption ? Is it a separate terminal-emulator program ?

regards,
Hardik

---

### Post by myusername on 2008-09-03
Arch Lxde with wbar

---

### Post by Hire on 2008-09-03
[[IMG]http://www.okiwii.net/images/i0pdl68g0molmczn3bf_thumb.jpg[/IMG]](http://www.okiwii.net/viewer.php?file=i0pdl68g0molmczn3bf.jpg)

---

### Post by etnlIcarus on 2008-09-03
> **ayoli said:**
> all .desktop files are stored in /usr/share/applications I believe.

It's best not to overwrite them unless absolutely necessary, though.

~/.local/share/applications/ is a better way to add extra launchers. Copy launchers from /usr/share/applications/ to ~/.local/share/applications/ and set NoDisplay=true to hide them.

---

### Post by Muppeteer on 2008-09-03
Need some inspiration.

---

### Post by urukrama on 2008-09-03
> **rangalo said:**
> How do you get that tabbed terminal on the right screenshot with [New][*1][2] .. etc caption ? Is it a separate terminal-emulator program ?

That is a tabbed urxvt (rxvt-unicode in the repositories). I've since changed the colour settings, but here is the relevant section from my ~/.Xdefaults file that governs urxvt:

> ###############
###  urxvt  ###
###############
URxvt*font:		xft:DejaVu Sans Mono:size=7:VL Gothic:size=7:antialias=true:hinting=true
URxvt*boldFont: 	xft:DejaVu Sans Mono:size=7:VL Gothic:size=7:antialias=true:bold:hinting=true
URxvt*background:	#FCFCFC
URxvt*foreground:	#39331B
URxvt*color0:		#39331B
URxvt*color1:		#39331B
URxvt*color2:		#B5AA74
URxvt*color3:		#FCFCFC
URxvt*fading:    	10
URxvt*tintColor: 	#FCFCFC
URxvt*shading:    	100
URxvt*inheritPixmap: 	False
URxvt*cursorBlink:      False
URxvt*cutchars:		`'",;@&*=|?()<>[]{}

URxvt*scrollstyle:	plain
URxvt*mouseWheelScrollPage:	False
URxvt*jumpScroll:       False
URxvt*skipScroll:       False
URxvt*scrollBar: 	False
URxvt*scrollTtyOutput:      False
URxvt*secondaryScroll:	  False

URxvt.perl-ext-common:	default,tabbed
URxvt.tabbed.tabbar-fg:         1
URxvt.tabbed.tabbar-bg:         3
URxvt.tabbed.tab-fg:            2
URxvt.tabbed.tab-bg:            1

URxvt*urlLauncher:	opera
URxvt*saveLines::       32767


---

### Post by rangalo on 2008-09-03
Hi urukrama,

> **urukrama said:**
> That is a tabbed urxvt (rxvt-unicode in the repositories). I've since changed the colour settings, but here is the relevant section from my ~/.Xdefaults file that governs urxvt:

Thanks for the quick answer. I have already installed rxvt-uniocode , but it is not tabbed. I also find mrxvt in the repos, it also has tabs, but looks completely different. Which package are you talking about? I am on Gutsy.



regards,
Hardik

---

### Post by Giant Speck on 2008-09-03
> **myusername said:**
> Arch Lxde with wbar

The theme is nice in all, but how in the heck are you able to see what's in your taskbar when the text color matches the panel color?

---

### Post by urukrama on 2008-09-03
> **rangalo said:**
> Thanks for the quick answer. I have already installed rxvt-uniocode , but it is not tabbed. I also find mrxvt in the repos, it also has tabs, but looks completely different. Which package are you talking about? I am on Gutsy.

Urxvt needs to be compiled with perl support (which I believe is default in the Ubuntu repositories version; it is in any case in Hardy).

Try launching urxvt with the command *urxvt -pe tabbed* or add the following lines to your .Xdefaults file (as above in my example):

```
URxvt.perl-ext-common: default,tabbed
```

[This page]("http://linux.die.net/man/7/urxvt") has been really helpful in understanding the potentials of urxvt.

See also *man urxvtperl* for more perl-based options.

---

### Post by rangalo on 2008-09-03
Thanks a lot, this helped.

---

### Post by olieviya on 2008-09-03
**Controls**: Human-Murrine

**Window Border**: X-Colors

**Icons**: Tango

**Wallpaper**: Desktopography Brisa

**Desktop Icons**: Home=Somatic, Project=dimpoart.deviantart

---

### Post by twntyonejay on 2008-09-03
My settings for September

---

### Post by chucky chuckaluck on 2008-09-03
> **twntyonejay said:**
> My settings for September

what kind of car is that?

---

### Post by vishzilla on 2008-09-03
GTK: Murrine Clean
OB: Breathe
Icons: Kamel
[center][[IMG]http://b.imagehost.org/t/0278/2008-09-04-002256_1024x768_scrot.jpg[/IMG]](http://b.imagehost.org/view/0278/2008-09-04-002256_1024x768_scrot.png) [[IMG]http://b.imagehost.org/t/0294/2008-09-04-002417_1024x768_scrot.jpg[/IMG]](http://b.imagehost.org/view/0294/2008-09-04-002417_1024x768_scrot.png)[/center]

---

### Post by perfectska04@hotmail.com on 2008-09-03
Just trying out some new settings, and giving AWN dock another chance. It really cleans things up, since I don't need tray icons/ launchers any more.

---

### Post by mthei on 2008-09-03
Debian Lenny. It's nice to be back to the Debian-based world. Fedora is great, but there were too many unneeded processes running that couldn't be stopped, even when stripped down.

Icons: Crashbit.
Wallpaper: Modified version of [Under the Weather](http://zilla774.deviantart.com/art/under-the-weather-14796956) by Zilla774 from DeviantArt.

---

### Post by John.Michael.Kane on 2008-09-03
> **chucky chuckaluck said:**
> what kind of car is that?

Looks like a modified Toyota Corolla Dx E70 series.

---

### Post by SomeGuyDude on 2008-09-03
Minor set of changes, but it's new, so hey.

GTK: MurrineGlow
Icons: OxygenRefit2
Sonata+MPD
Conky
AWN: Liquid Glass Black
Wallpaper: Off of DA
Firefox: Hide Menubar extension and combine stop/reload/throbber UserStyle

---

### Post by myusername on 2008-09-03
> **Giant Speck said:**
> The theme is nice in all, but how in the heck are you able to see what's in your taskbar when the text color matches the panel color?

thats just when the apps are minimized

---

### Post by washeddang on 2008-09-03
Here's mine:
GTK & Metacity: Shiki-Colors Brave
AWN: Default
Icons: Recolored Mac4Lin
Wallpaper: My own

---

### Post by twntyonejay on 2008-09-03
> **chucky chuckaluck said:**
> what kind of car is that?

1982 Toyota Corolla, that pic was taken on Aug 31. at a car show

---

### Post by Patricrawley on 2008-09-03
What is the best way to create your own openbox themes?

---

### Post by dbbolton on 2008-09-03
> **Patricrawley said:**
> What is the best way to create your own openbox themes?
Tweak the hell out of an existing one :D

You can find out just about everything you need to know here: [http://icculus.org/openbox/index.php/Help:Themes](http://icculus.org/openbox/index.php/Help:Themes)

---

### Post by RiceMonster on 2008-09-03
> **Patricrawley said:**
> What is the best way to create your own openbox themes?

Look at the themerc of other Openbox themes, and also check out the link dbbolton posted. Openbox themes are really easy to make :).

---

### Post by Pandemic187 on 2008-09-03
> **armageddon08 said:**
> These are mine for the month: 
1. KDE-Desktop: Glassified theme
2. GNOME-Desktop: Futurelooks2 theme
3. GNOME with Compiz-Fusion
4. XFCE-Desktop: Dr. Aqua-Vista theme

Quite simplistic this time!:)
I'm a KDE n00b. How did you get your window to look like that in the first screenshot?

---

### Post by [S]Duke on 2008-09-03
Not too much different from August.

New background/Icons.

I'm really loving Shiki, so I doubt I'll change it anytime soon.

---

### Post by Pandemic187 on 2008-09-03
I've noticed a lot of you are using Openbox with Pypanel, but these are new to me. What is so great about them?

---

### Post by RiceMonster on 2008-09-03
> **Pandemic187 said:**
> I've noticed a lot of you are using Openbox with Pypanel, but these are new to me. What is so great about them?

Try and find out. Openbox is very lightweight, minimal, and configurable.

---

### Post by Truedream on 2008-09-03
> **Muppeteer said:**
> Need some inspiration.

[[IMG]http://img382.imageshack.us/img382/3584/screenshotyv5.th.jpg[/IMG]](http://img382.imageshack.us/my.php?image=screenshotyv5.jpg)

is that the now playing screenlet on bottom left hand side?

---

### Post by lzfy on 2008-09-03
> **Pandemic187 said:**
> I'm a KDE n00b. How did you get your window to look like that in the first screenshot?

That's KDE4 with the folder view plasmoid. You need KDE 4.1 for that.

---

### Post by BLTicklemonster on 2008-09-03
[[IMG]http://img411.imageshack.us/img411/999/screenshotut2.th.png[/IMG]](http://img411.imageshack.us/my.php?image=screenshotut2.png)

wall paper unabashedly stolen from this site because it's a cool picture...

[http://www.thesun.co.uk/sol/homepage/features/article1630897.ece](http://www.thesun.co.uk/sol/homepage/features/article1630897.ece)

... might as well use the picture if we're all gonna die anyway, huh?

---

### Post by Pandemic187 on 2008-09-03
> **lzfy said:**
> That's KDE4 with the folder view plasmoid. You need KDE 4.1 for that.
Thanks. Yeah, I've used KDE 4 before, so I recognized it as such. Plasmoids, on the other hand...those are something I'm gonna have to look into.

---

### Post by chucky chuckaluck on 2008-09-03
> **Pandemic187 said:**
> I've noticed a lot of you are using Openbox with Pypanel, but these are new to me. What is so great about them?

well, openbox gives you access to your apps and pypanel tells you what time it is.

---

### Post by bfc on 2008-09-04
My desktop for September.....

[[img]http://i37.tinypic.com/ilhr4h.png[/img]](http://i37.tinypic.com/2vljhua.png)

---

### Post by wenuswilson on 2008-09-04
found the wallpaper on deviant art... one of my favorite ones of all time.

---

### Post by easybake on 2008-09-04
Going with a dark theme for the first time.
[[IMG]http://img390.imageshack.us/img390/5646/screenshotbp5.th.png[/IMG]](http://img390.imageshack.us/img390/5646/screenshotbp5.png)[[IMG]http://img242.imageshack.us/img242/5985/screenshot2du7.th.png[/IMG]](http://img242.imageshack.us/img242/5985/screenshot2du7.png)

---

### Post by dlm4849 on 2008-09-04
Heres mine for now.

---

### Post by Hells_Dark on 2008-09-04
[[img]http://pix.nofrag.com/f/1/9/44ebbbcf1c5b1ecf1a76aef43f12b.png[/img]](http://hellsdark.deviantart.com/art/03-09-08-Simply-Linux-96894789)

---

### Post by vishzilla on 2008-09-04
> **Hells_Dark said:**
> [[img]http://pix.nofrag.com/f/1/9/44ebbbcf1c5b1ecf1a76aef43f12b.png[/img]](http://hellsdark.deviantart.com/art/03-09-08-Simply-Linux-96894789)

I always wanted to ask. What add-on do you use for the firefox bookmark buttons?

---

### Post by Prefix100 on 2008-09-04
Seeing as my thread is a ghost town, I'll post here.

Some of you are using the NowPlaying screenlet, but I've never been able to get this to work with the latest banshee, have you guys?

---

### Post by Nevon on 2008-09-04
> **Hells_Dark said:**
> [[img]http://pix.nofrag.com/f/1/9/44ebbbcf1c5b1ecf1a76aef43f12b.png[/img]](http://hellsdark.deviantart.com/art/03-09-08-Simply-Linux-96894789)

Could you give me a link to that emerald theme?

---

### Post by Hells_Dark on 2008-09-04
> **Nevon said:**
> Could you give me a link to that emerald theme?
[here](http://www.gnome-look.org/content/show.php/Gommoso-Colors?content=78091)
> **vishzilla said:**
> I always wanted to ask. What add-on do you use for the firefox bookmark buttons?
No add on. Just simple bookmarks, and i removed the text in order to have just the icons.

---

### Post by vishzilla on 2008-09-04
> **Hells_Dark said:**
> No add on. Just simple bookmarks, and i removed the text in order to have just the icons.
Thanks I didn't know we could do that, or never tried it before

---

### Post by god0fgod on 2008-09-04
OS X theme and a some sort of Safari skin for Opera. Background is a picture of Positano in the south of Italy. I visited there went I went a few weeks back.

---

### Post by Lux_Deluxe on 2008-09-04
My Sep. Desktop

[[IMG]http://img3.imagebanana.com/img/xmqatc66/thumb/Bildschirmfoto.png[/IMG]](http://luxdeluxe.deviantart.com/art/Screen-Sep-97016282)

---

### Post by maxclimber1w on 2008-09-04
> **raul_ said:**
> Just a repost from last month. I like to show off

What font are you using? It looks great!

---

### Post by urukrama on 2008-09-04
Awesome 2.3, nice and dark. :twisted:

Details in the first screenshot. The wallpaper is *hsetroot -solid "#08090A"*.

(Such a consistently dark desktop is very pleasant on the eyes, I must say!)

---

### Post by el mariachi on 2008-09-04
if you use w3m to view google.com haha :p

---

### Post by elmer_42 on 2008-09-05
I got an oldish junker box, and I'm revitalizing it with Xubuntu. Currently it looks like this:
[[img]http://arch.kimag.es/resized/37826910.png[/img]](http://arch.kimag.es/share/37826910.png)

I'm going to be installing and configuring Openbox tomorrow. Wish me luck!

---

### Post by BLTicklemonster on 2008-09-05
> **easybake said:**
> Going with a dark theme for the first time.
[[IMG]http://img390.imageshack.us/img390/5646/screenshotbp5.th.png[/IMG]](http://img390.imageshack.us/img390/5646/screenshotbp5.png)[[IMG]http://img242.imageshack.us/img242/5985/screenshot2du7.th.png[/IMG]](http://img242.imageshack.us/img242/5985/screenshot2du7.png)

Cool UT logo!

---

### Post by Savel on 2008-09-05
Debian Lenny :tongue:

[ATTACH]84104[/ATTACH][ATTACH]84105[/ATTACH]

---

### Post by easybake on 2008-09-05
> **BLTicklemonster said:**
> Cool UT logo!

Thanks. Got it from [Here]("http://fireesper.deviantart.com/art/Unreal-Wallpaper-77505183")

---

### Post by Chokkan on 2008-09-05
Elegant Brit (who doesn't love it?) Gion Icons and [Mist wallpaper]("http://phpscriptcoder.deviantart.com/art/Mist-88466510").
[[IMG]http://farm4.static.flickr.com/3148/2829453655_2dbf309d72_m.jpg[/IMG]]("http://www.flickr.com/photos/shashinpapa/2829453655/sizes/l/")

I've a little script to easily change wallpaper and conky at the same time so my desktop changes a lot.

---

### Post by TheSlipstream on 2008-09-05
I love Openbox. I want to shout it in the streets, but it's late and I'm tired, so I'll just post it. Thank you so much, Urukrama, you deserve a medal! :D

Gtk: Nova Gold
Openbox: Nova Gold
Conky
Visibility

Does anyone know how I can capture my menu in a screenshot? It doesn't seem to stay on PrtSc.

---

### Post by urukrama on 2008-09-05
> **el mariachi said:**
> if you use w3m to view google.com haha :p

Or you can use [userstyles]("http://userstyles.org/")

> **Chokkan said:**
> [Mist wallpaper]("http://phpscriptcoder.deviantart.com/art/Mist-88466510").

Thank you for linking to this wallpaper; I was looking for something like that. I now use it on my Openbox desktop. :-)

For those who are interested (yes, all two of you ;-)), I've uploaded the Mythos [Openbox]("http://box-look.org/content/show.php/Mythos?content=88560") and [Gtk themes]("http://gnome-look.org/content/show.php/show.php?content=88562").

---

### Post by Chokkan on 2008-09-05
No problem, and very nice it looks on your desktop too. :)

---

### Post by Darkade on 2008-09-05
I'm at the laptop now so that's the pic

I'm using arch, openbox, fbpanel, and conky let's keep it simple :D:D

---

### Post by Hells_Dark on 2008-09-05
> **TheSlipstream said:**
> 
Does anyone know how I can capture my menu in a screenshot? It doesn't seem to stay on PrtSc.
> sudo apt-get install scrot
scrot -cd3
And open your menu.

---

### Post by michaelramm on 2008-09-05
> **elmer_42 said:**
> I got an oldish junker box, and I'm revitalizing it with Xubuntu. Currently it looks like this:
[[img]http://arch.kimag.es/resized/37826910.png[/img]](http://arch.kimag.es/share/37826910.png)

I'm going to be installing and configuring Openbox tomorrow. Wish me luck!

Check out [Crunchbang Linux]("http://crunchbang.org/projects/linux"). It is Openbox built on top of Ubuntu 8.04. Very slick and nice.

Michael

---

### Post by weboide on 2008-09-05
Hi, here's my desktop screenshot on my laptop, just set up yesterday using :

Ubuntu 8.04.1
Openbox 3.4.7.2 (compiled from source)
pypanel
xfce4-terminal
swiftfox

theme: airborne
wallpaper: paris from interfacelift

---

### Post by l0co on 2008-09-05
After some work for my wife:

[[IMG]http://img111.imageshack.us/img111/4964/l0cosm5.th.png[/IMG]](http://img111.imageshack.us/my.php?image=l0cosm5.png)

---

### Post by chucky chuckaluck on 2008-09-05
openbox, pypanel, feh, xterm, opera, thunar. dyne ob theme, a gray version of elegant brit gtk, 2dark is the opera skin. no idea where i got the wallpaper (shown in feh). it took a little work, but i think i managed to intergrate opera into an essentially gtk set of looks.

[[IMG]http://b.imagehost.org/t/0321/greyscr.jpg[/IMG]](http://b.imagehost.org/view/0321/greyscr.jpg)

---

### Post by dhazin on 2008-09-05
Here is mine:

[[IMG]http://img380.imageshack.us/img380/9764/screenshotrx1.th.png[/IMG]](http://img380.imageshack.us/my.php?image=screenshotrx1.png)


Ubuntu 8.04
AWN
Screenlets
Dropline Neu icons
Wallpaper taken somewhere from devianart :)

---

### Post by ayoli on 2008-09-05
> **chucky chuckaluck said:**
> openbox, pypanel, feh, xterm, opera, thunar. dyne ob theme, a gray version of elegant brit gtk, 2dark is the opera skin. no idea where i got the wallpaper (shown in feh). it took a little work, but i think i managed to intergrate opera into an essentially gtk set of looks.

[[IMG]http://b.imagehost.org/t/0321/greyscr.jpg[/IMG]](http://b.imagehost.org/view/0321/greyscr.jpg)

If I remind well, this wallpaper is called block 23 from customize.org.

---

### Post by Tuning_In on 2008-09-05
> **chucky chuckaluck said:**
> openbox, pypanel (deadbinkies font). don't remember where i got the wallpaper or even what it originally looked like.

[[IMG]http://b.imagehost.org/t/0869/handscr.jpg[/IMG]](http://b.imagehost.org/view/0869/handscr.jpg)

A really nice wall you got there. Can you upload it?

---

### Post by conundrumx on 2008-09-05
[[IMG]http://img356.imageshack.us/img356/8896/screenshotqy2.th.png[/IMG]](http://img356.imageshack.us/img356/8896/screenshotqy2.png)

No, it's not really a secret!

Thanks for the wallpaper, Perfect Ska.  When are you going to make a Usplash out of it?  ;)

---

### Post by perfectska04@hotmail.com on 2008-09-05
> **conundrumx said:**
> 
Thanks for the wallpaper, Perfect Ska.  When are you going to make a Usplash out of it?  ;)

Soon. But this time I won't make colored usplashes, I'll use a dark grey background and use a layout similar to the GDM's.

---

### Post by conundrumx on 2008-09-05
Good deal!  I've been using the GNOME Colors ones since release, though I modified the progress bars so they stand out from the background.  :)

---

### Post by mthei on 2008-09-05
Returned to Fedora, as I usually do. Frankly, if I do go back to the Debian world, I'd rather be using Ubuntu, as only Ubuntu and Fedora run better on my machine than others.

---

### Post by indecisive on 2008-09-05
I'm on green right now.  Much thanks for What is in a name?'s themes.

---

### Post by ahaslam on 2008-09-05
Modified Murrina-Tangoesque ob3.
Minor mods to MurrinaFancyEarth GTK.
Selection of Tango(ish) icons.

Running the usual suspects of pypanel & conky.

---

### Post by Muppeteer on 2008-09-05
> **Truedream said:**
> [[IMG]http://img382.imageshack.us/img382/3584/screenshotyv5.th.jpg[/IMG]](http://img382.imageshack.us/my.php?image=screenshotyv5.jpg)

is that the now playing screenlet on bottom left hand side?

Yeah it is. I'm using the Nowplaying theme called 'Vinyl' :)

---

### Post by collinp on 2008-09-05
My desktop, updated for fall coming in this month :). It has the usual, Gnome (Yeah, big surprise lol) and Compiz. Didnt feel like enabling anything more because I am trying to cut down on the clutter on my desktop. Background is a path of trees with a verse from the Book of Isaiah from the Bible.

---

### Post by voteforpedro36 on 2008-09-05
> **ahaslam said:**
> Modified Murrina-Tangoesque ob3.
Minor mods to MurrinaFancyEarth GTK.
Selection of Tango(ish) icons.

Running the usual suspects of pypanel & conky.

[OT] I love The Racounters, if you look closely in some of my screens they're playing [/OT]. I'll also reserve this space for a screen shot.

Awesome:

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-5-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-5-08-bare.png)
[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-5-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-5-08-media.png)

---

### Post by skitzware on 2008-09-05
[[IMG]http://img113.imageshack.us/img113/6121/sshotuh9.th.png[/IMG]](http://img113.imageshack.us/my.php?image=sshotuh9.png)

Fluxbox Royalty theme
Thunar
Bash
Sonata

---

### Post by NWAdawg on 2008-09-05
Its basic. I'm trying for the Brushed Aluminum look.
Theme:Brushedchrome3/Crux with gmetalik icons. 
Background: Brushed Aluminum with tag Photoshopped in.

---

### Post by G@B0 on 2008-09-06
Here's mine:



Just a simple setup with Linux Mint Xfce almost all by default except the icon theme.
Conky is missing here, maybe latter I'll include it.

---

### Post by hemajang on 2008-09-06
Hello,

I'm thinking of switching to Openbox, from compiz-emerald, I've been hearing alot of Openbox and would like to give it a go.

Do I need to uninstall compiz and emerald in order to use Openbox, if so is there a thorough guide on this?

Any other input advice on making the switch will be greatly appreciated.

Thx

---

### Post by vishzilla on 2008-09-06
> **hemajang said:**
> Hello,

I'm thinking of switching to Openbox, from compiz-emerald, I've been hearing alot of Openbox and would like to give it a go.

Do I need to uninstall compiz and emerald in order to use Openbox, if so is there a thorough guide on this?

Any other input advice on making the switch will be greatly appreciated.

Thx

no need to uninstall. follow this guide by Urukrama [[link]("http://urukrama.wordpress.com/openbox-guide/")]

---

### Post by PurposeOfReason on 2008-09-06
Found a way to make the system tray fit. Nothing really changed as this theme may be a keeper.

---

### Post by ad_267 on 2008-09-06
Here's mine. It's quite similar to a few others at the moment. Using Clear-Glow Pink and metacity with compositing, Eikon icon set, background is off Customize.org somewhere. Screenshot shows the international space station in Celestia.

---

### Post by aschwerin.moses on 2008-09-06
My Desktop

---

### Post by awakatanka on 2008-09-06
KDE 4.1.1 on kubuntu
Glassified theme for plasma

---

### Post by ellalan on 2008-09-06
Here is mine.

---

### Post by lucazade on 2008-09-06
September asks for a new desktop, here is it! :)

---

### Post by el mariachi on 2008-09-06
[http://wooko.deviantart.com/art/GAAW-97035227](http://wooko.deviantart.com/art/GAAW-97035227) is anyone familiar with this wallpaper? I saw it a long time ago but now can't find it

---

### Post by funkameleon on 2008-09-06
my september 2008 desktop screenshot ...

---

### Post by lzfy on 2008-09-06
> **el mariachi said:**
> [http://wooko.deviantart.com/art/GAAW-97035227](http://wooko.deviantart.com/art/GAAW-97035227) is anyone familiar with this wallpaper? I saw it a long time ago but now can't find it

I know it's from sxc.hu  but maybe this one is a little bit tweaked.

---

### Post by John.Michael.Kane on 2008-09-06
> **el mariachi said:**
> [http://wooko.deviantart.com/art/GAAW-97035227](http://wooko.deviantart.com/art/GAAW-97035227) is anyone familiar with this wallpaper? I saw it a long time ago but now can't find it

[Morning dew]("http://00wolf00.deviantart.com/art/Morning-dew-84832417")

---

### Post by hellion0 on 2008-09-06
I decided to go back to the green.

[[IMG]http://img337.imageshack.us/img337/6057/200809060552201280x1024xt4.th.jpg[/IMG]](http://img337.imageshack.us/my.php?image=200809060552201280x1024xt4.jpg)

GTK: [Foregreener](http://xfce-look.org/content/show.php/Foregreen?content=85199)
XFCE: Symphony, as always...
Icons: [Oxygen-Refit 2 Orange Version](http://www.gnome-look.org/content/show.php/Oxygen-Refit+2+-+Orange+Version?content=83003)
XMMS: [Almond-Aluminum Green (De-branded)](http://gnome-look.org/content/show.php/AA+Skin+Pack+(De-branded)?content=88480)
Wallpaper: [Double Rainbow](http://interfacelift.com/wallpaper_beta/details/1635/double_rainbow.html)
Window font: Segoe UI
Terminal font: Fixed
Conky font: Roadgeek Series D, Roadgeek Series EM

---

### Post by billgoldberg on 2008-09-06
Laptop:

[[img]http://xs131.xs.to/xs131/08363/screenkl499.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs131&d=08363&f=screenkl499.png)

Wallpaper

[http://www.skins.be/brittany-murphy/wallpapers/page/3/](http://www.skins.be/brittany-murphy/wallpapers/page/3/)

---

### Post by AlexR1 on 2008-09-06
> **el mariachi said:**
> [http://wooko.deviantart.com/art/GAAW-97035227](http://wooko.deviantart.com/art/GAAW-97035227) is anyone familiar with this wallpaper? I saw it a long time ago but now can't find it

Here is the link for the paper clicky [http://customize.org/wallpapers/58138](http://customize.org/wallpapers/58138)
lately customize.org opening slow, if you have trouble downloading wallpaper send me an e-mail and I will send wall to you.

---

### Post by billgoldberg on 2008-09-06
> **AlexR1 said:**
> Here is the link for the paper clicky [http://customize.org/wallpapers/58138](http://customize.org/wallpapers/58138)
lately customize.org opening slow, if you have trouble downloading wallpaper send me an e-mail and I will send wall to you.

Lately? Customize.org has been slow as long as I can remember.

---

### Post by plb on 2008-09-06
> **billgoldberg said:**
> Lately? Customize.org has been slow as long as I can remember.

Agreed. I usually just browse deviantart but occasionally like to venture over to customize.org and for as many years as I've gone there it's always been slow. I've also always hated the layout.

---

### Post by el mariachi on 2008-09-06
+1 : /

---

### Post by el mariachi on 2008-09-06
found out that my DSC-P10 has more to it than "point-and-click" :D

---

### Post by chucky chuckaluck on 2008-09-06
> **ayoli said:**
> If I remind well, this wallpaper is called block 23 from customize.org.

i think that's right. i changed the name when i put the elk in, so i can't say for sure.


> **Tuning_In said:**
> A really nice wall you got there. Can you upload it?

thanks. 

[[IMG]http://b.imagehost.org/t/0253/mirror2.jpg[/IMG]](http://b.imagehost.org/view/0253/mirror2.png)

---

### Post by Tuning_In on 2008-09-06
> **chucky chuckaluck said:**
> i think that's right. i changed the name when i put the elk in, so i can't say for sure.




thanks. 

[[IMG]http://b.imagehost.org/t/0253/mirror2.jpg[/IMG]](http://b.imagehost.org/view/0253/mirror2.png)

Thank you:)

---

### Post by meborc on 2008-09-06
> **aschwerin.moses said:**
> My Desktop

nice work... what is that font in your terminal?

---

### Post by chucky chuckaluck on 2008-09-06
openbox, xterm (cplay, scrot), thunar, elegant brit (blued version) ob+gtk themes and a bust of franz xaver messerschmidt (i distorted the shape to fit the tiling in. it's not like someone making that face is going to care. besides, he's long gone).

[[IMG]http://b.imagehost.org/t/0431/xaverscr.jpg[/IMG]](http://b.imagehost.org/view/0431/xaverscr.jpg)


-----------

my pleasure, tuning_in.

---

### Post by Mazza558 on 2008-09-06
I'm on intrepid, and that unfortunately means no fglrx ATI driver, and so no Compiz for a few weeks. I've had to create a non-compiz futurelooks theme very quickly.

I'm not sure where the wallpaper was from, but can upload it at 1280x800 if anyone wants it.

---

### Post by indecisive on 2008-09-06
Please do upload it.  Also, is the picture available in any other resolutions, and where did you you get it?

---

### Post by Mazza558 on 2008-09-06
> **indecisive said:**
> Please do upload it.  Also, is the picture available in any other resolutions, and where did you you get it?

I'll try and find it.

EDIT: Here you go...

[http://dawn42.deviantart.com/art/Conquer-the-World-93339066]("http://dawn42.deviantart.com/art/Conquer-the-World-93339066")

---

### Post by eightmillion on 2008-09-06
I've got this picture in super mega huge size. :lolflag:

[[img]http://xs331.xs.to/xs331/08366/1218073286385384.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs331&d=08366&f=1218073286385384.jpg)

---

### Post by chucky chuckaluck on 2008-09-06
miro and elegant brit.

[[IMG]http://b.imagehost.org/t/0004/dogscr.jpg[/IMG]](http://b.imagehost.org/view/0004/dogscr.jpg)

---

### Post by andamaru on 2008-09-06
> **billgoldberg said:**
> 

Wallpaper

[http://www.skins.be/brittany-murphy/wallpapers/page/3/](http://www.skins.be/brittany-murphy/wallpapers/page/3/)

Google Browser doesn't like the site your wallpapers are on. I hope it's just a false positive.

EDIT: Firefox 3 doesn't seem to care, and avast didn't stop anything so I think it's ok. Sorry about the scare

---

### Post by chucky chuckaluck on 2008-09-06
this wallpaper reminds me of playing badminton with my sister, when we were kids, in our upstairs bathroom. needless to say, i hope, we had considerably less room. remarkably, we got quite a few volleys going even though one of us was usually standing in the bath tub.

[[IMG]http://b.imagehost.org/t/0803/badmscr.jpg[/IMG]](http://b.imagehost.org/view/0803/badmscr.jpg)

---

### Post by Bart_D on 2008-09-06
> **PurposeOfReason said:**
> Found a way to make the system tray fit. Nothing really changed as this theme may be a keeper.

Another one of the best screenshots I've seen in these threads(I'll always pick minimalistic), although I prefer your August Conky setup to this one.

---

### Post by ddnev45 on 2008-09-07
Going BW this month.

---

### Post by Dark Aspect on 2008-09-07
I am just making small changes to what already had at this point:

[[IMG]http://img178.imageshack.us/img178/5255/desktopcompizoa1.th.png[/IMG]](http://img178.imageshack.us/my.php?image=desktopcompizoa1.png)

I basically modified this Conky file,

[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html")

So no need to upload it,

---

### Post by Giant Speck on 2008-09-07
Still working on perfecting my KDE desktop without drastically changing it.

I found out something wonderful about the widget style called Serenity.  I can have buttons on my panel!

What I've changed this time:

[LIST]
[*]changed my icons
[*]changed the panel color
[*]made a new wallpaper
[*]installed KBFX to get a really cool K-menu button
[*]installed MurrineGlow for my GTK apps
[*]altered my color scheme to match the MurrineGlow theme
[*]changed my Firefox theme to Elementary
[/LIST]

---

### Post by cistym on 2008-09-07
Theme: Murrina Dark² Blue
Emerald: New Wave (nwe.3.4 truglass engine)
Icons:  black-white 2 Gloss
Wallpaper: [http://tarantisticremnants.deviantart.com/art/Angel-of-the-Dawn-91743635]("http://tarantisticremnants.deviantart.com/art/Angel-of-the-Dawn-91743635")
Font: FreeSans
Screenlets

---

### Post by etnlIcarus on 2008-09-07
> **cistym said:**
> Theme: Murrina Dark² Blue
Emerald: New Wave (nwe.3.4 truglass engine)
Icons:  black-white 2 Gloss
Wallpaper: [http://tarantisticremnants.deviantart.com/art/Angel-of-the-Dawn-91743635]("http://tarantisticremnants.deviantart.com/art/Angel-of-the-Dawn-91743635")
Font: FreeSans
Screenlets

Too small to see anything.

---

### Post by aschwerin.moses on 2008-09-07
LCD font
[http://www.dafont.com/lcd-lcd-mono.font](http://www.dafont.com/lcd-lcd-mono.font)

---

### Post by aschwerin.moses on 2008-09-07
> **meborc said:**
> nice work... what is that font in your terminal?
LCD Font
[http://www.dafont.com/lcd-lcd-mono.font](http://www.dafont.com/lcd-lcd-mono.font)

---

### Post by markp1989 on 2008-09-07
OS: hardy 64 bit
wm: Compiz fusion stand alone
GTK: Slickness-black
icons: black white 2
emerald: blackminimal, from gnome look
wallpaper: file is called wings.jpg, not sure were i got it from 
dock: fbpanel 

anything else you wana know just ask

---

### Post by nolimit974 on 2008-09-07
OS: 8.0.4
wm: fluxbox
dock: gdesklets dock

---

### Post by misfitpierce on 2008-09-07
My KDE4 desktop with Kubuntu

Batman wall from 4chan rest is stock KDE4

---

### Post by tdrusk on 2008-09-07
Theme: [Nimbus]("http://gnome-look.org/content/show.php/Nimbus?content=87634")
Icons: [nuoveXT.2.2]("http://gnome-look.org/content/show.php/nuoveXT+2?content=56625")
Wallpaper: [DRM-x]("http://gnome-look.org/content/show.php/DRM-X?content=78226")

The only thing I don't like is the orange loading bars and orange in firefox back and forward.

---

### Post by Muppeteer on 2008-09-07
Finally found a theme/color scheme i'm happy with :)

---

### Post by Killeroid on 2008-09-07
> **misfitpierce said:**
> My KDE4 desktop with Kubuntu

Batman wall from 4chan rest is stock KDE4

Can I get a link for the wallpaper ?It would really compliment my desktop.Thanks

---

### Post by yabbadabbadont on 2008-09-07
> **chucky chuckaluck said:**
> this wallpaper reminds me of playing badminton with my sister, when we were kids, in our upstairs bathroom. needless to say, i hope, we had considerably less room. remarkably, we got quite a few volleys going even though one of us was usually standing in the bath tub.

[[IMG]http://b.imagehost.org/t/0803/badmscr.jpg[/IMG]](http://b.imagehost.org/view/0803/badmscr.jpg)

I remember when the citizens of Kansas City were told by the Nelson that they were "uncultured" and "had no taste" when they complained about the money spent on those stupid shuttlecock "sculptures".  Needless to say, attendance at the Nelson art gallery dropped significantly right afterwards.  :lol:  (It eventually returned to normal levels)

---

### Post by GrouchoMarx on 2008-09-07
GTK:Timond-Black
Metacity:Candido-Selected
Wallpaper: Off the internet?

---

### Post by raul_ on 2008-09-07
> **el mariachi said:**
> found out that my DSC-P10 has more to it than "point-and-click" :D

Nice Pessoa photo :P

---

### Post by voteforpedro36 on 2008-09-07
> **GrouchoMarx said:**
> GTK:Timond-Black
Metacity:Candido-Selected
Wallpaper: Off the internet?

That picture amuses me every time I see it.

---

### Post by el mariachi on 2008-09-07
thanks ;)

---

### Post by motang on 2008-09-07
Well since I just got the Asus Eee Box, I have been playing around with that and not touched my theme on my regular Ubuntu box or my notebook.  I put Xubuntu on my Eee Box, left the theme default as I like it and also the left the Tango icons.  I took off the clock and added the cairo clock and my back ground if fall2 by David Lanham, I really like the wallpaper as it looks hand drawn and goes well with Xubuntu. Of course I have compiz-fusion running...can't compute without it. ;)

---

### Post by GrouchoMarx on 2008-09-07
> **voteforpedro36 said:**
> That picture amuses me every time I see it.

It's a classic!

More fun...

[http://farm1.static.flickr.com/123/369326634_f71399ec1d_o.jpg]("http://farm1.static.flickr.com/123/369326634_f71399ec1d_o.jpg")

---

### Post by whitefang5412 on 2008-09-07
Simple and Functional.

---

### Post by voteforpedro36 on 2008-09-07
> **GrouchoMarx said:**
> It's a classic!

More fun...

[http://farm1.static.flickr.com/123/369326634_f71399ec1d_o.jpg]("http://farm1.static.flickr.com/123/369326634_f71399ec1d_o.jpg")

Wow, that's awesome. I would've never thought about that. Now I'm gonna go track down that picture of the Star Wars Band, unless you would care to upload it for me?

EDIT: Found it, made it my wall, took screenshot:

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-7-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-7-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-7-08-web.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-7-08-web.png)

---

### Post by GrouchoMarx on 2008-09-07
> **voteforpedro36 said:**
> Wow, that's awesome. I would've never thought about that. Now I'm gonna go track down that picture of the Star Wars Band, unless you would care to upload it for me?

I believe this was it: [http://www.houseofodd.com/wp-content/uploads/2007/10/star_wars_rocks_hugh_fleming.jpg]("http://www.houseofodd.com/wp-content/uploads/2007/10/star_wars_rocks_hugh_fleming.jpg")

(or you can Google "Hugh Fleming").

---

### Post by voteforpedro36 on 2008-09-07
> **GrouchoMarx said:**
> I believe this was it: [http://www.houseofodd.com/wp-content/uploads/2007/10/star_wars_rocks_hugh_fleming.jpg]("http://www.houseofodd.com/wp-content/uploads/2007/10/star_wars_rocks_hugh_fleming.jpg")

(or you can Google "Hugh Fleming").

Thanks a lot, here's another screenshot (back to 3 screenshots an attempt for a while):

Blah nevermind, I got it to take the shot fine with Mplayer, but now Photobucket won't upload the new file :(.

---

### Post by aristotlewilde on 2008-09-07
Wow.  Can't believe I waited this far into September to update my desktop.

Openbox (Loma Theme)
Tint
Wallpaper from Interfacelift
Conky

---

### Post by chucky chuckaluck on 2008-09-07
> **yabbadabbadont said:**
> I remember when the citizens of Kansas City were told by the Nelson that they were "uncultured" and "had no taste" when they complained about the money spent on those stupid shuttlecock "sculptures".  Needless to say, attendance at the Nelson art gallery dropped significantly right afterwards.  :lol:  (It eventually returned to normal levels)

meh, let 'em eat cake!

[[IMG]http://b.imagehost.org/t/0624/Cake.jpg[/IMG]](http://b.imagehost.org/view/0624/Cake.jpg)

---

### Post by Cosay on 2008-09-07
[IMG]http://farm4.static.flickr.com/3050/2837847215_6b1761b836.jpg[/IMG]
[Flickr]("http://www.flickr.com/photos/cosay-nold/2837847215/")

Evilwm; Rxvt-Unicode; Conky; Screen; Top.
Wallpaper by Mandolux.

---

### Post by etnlIcarus on 2008-09-07
> **yabbadabbadont said:**
> I remember when the citizens of Kansas City were told by the Nelson that they were "uncultured" and "had no taste" when they complained about the money spent on those stupid shuttlecock "sculptures".  Needless to say, attendance at the Nelson art gallery dropped significantly right afterwards.  :lol:  (It eventually returned to normal levels)a) What's stupid about them?
b) Why is, "sculptures", in inverted commas?

> **motang said:**
> Well since I just got the Asus Eee Box, I have been playing around with that and not touched my theme on my regular Ubuntu box or my notebook.  I put Xubuntu on my Eee Box, left the theme default as I like it and also the left the Tango icons.  I took off the clock and added the cairo clock and my back ground if fall2 by David Lanhma, I really like the wallpaper as it looks hand drawn and goes well with Xubuntu. Of course I have compiz-fusion running...can't compute without it. ;)Wait, is that screenshot of your Eee or your other PCs? I wasn't aware the Eees came in a 1440*900 variety.

---

### Post by Giant Speck on 2008-09-07
> **aristotlewilde said:**
> Wow.  Can't believe I waited this far into September to update my desktop.

Openbox (Loma Theme)
Tint
Wallpaper from Interfacelift
Conky

That is nice.

---

### Post by doorknob60 on 2008-09-08
Kubuntu 8.10 Alpha, KDE4 FTW! :KS

[[IMG]http://img230.imageshack.us/img230/6444/screenshotme9.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=screenshotme9.jpg)

---

### Post by zmjjmz on 2008-09-08
Running twin on mah Thinkpad T20...

---

### Post by andrek on 2008-09-08
> **etnlIcarus said:**
> Wait, is that screenshot of your Eee or your other PCs? I wasn't aware the Eees came in a 1440*900 variety.

I guess it's an Eee BOX ( PC ) connected to an external display, not the notebook.

---

### Post by wipeout140 on 2008-09-08
> **Mazza558 said:**
> I'm on intrepid, and that unfortunately means no fglrx ATI driver, and so no Compiz for a few weeks. I've had to create a non-compiz futurelooks theme very quickly.

I'm not sure where the wallpaper was from, but can upload it at 1280x800 if anyone wants it.

Could upload that theme also what icon theme do you use?

Thanks

---

### Post by DJ_Peng on 2008-09-08
> **Mazza558 said:**
> I'll try and find it.

EDIT: Here you go...

[http://dawn42.deviantart.com/art/Conquer-the-World-93339066](http://dawn42.deviantart.com/art/Conquer-the-World-93339066)
Thanks for the link. I had to add that to my wallpaper rotation.

> **ddnev45 said:**
> Going BW this month.
Very nice. Could you pls post a link to the wallpaper?

> **Giant Speck said:**
> Still working on perfecting my KDE desktop without drastically changing it.

I found out something wonderful about the widget style called Serenity.  I can have buttons on my panel!

What I've changed this time:

[LIST]
[*]changed my icons
[*]changed the panel color
[*]made a new wallpaper
[*]installed KBFX to get a really cool K-menu button
[*]installed MurrineGlow for my GTK apps
[*]altered my color scheme to match the MurrineGlow theme
[*]changed my Firefox theme to Elementary
[/LIST]

I love that wallpaper, especially with 9/11 coming up in a few days! Care to share it with us?

> **aschwerin.moses said:**
> LCD Font
[http://www.dafont.com/lcd-lcd-mono.font](http://www.dafont.com/lcd-lcd-mono.font)
I needed a good LCD font. Thanks.

> **tdrusk said:**
> Theme: [Nimbus]("http://gnome-look.org/content/show.php/Nimbus?content=87634")
Icons: [nuoveXT.2.2]("http://gnome-look.org/content/show.php/nuoveXT+2?content=56625")
Wallpaper: [DRM-x]("http://gnome-look.org/content/show.php/DRM-X?content=78226")

The only thing I don't like is the orange loading bars and orange in firefox back and forward.
Awesome 'pape!

> **GrouchoMarx said:**
> GTK:Timond-Black
Metacity:Candido-Selected
Wallpaper: Off the internet?

> **GrouchoMarx said:**
> I believe this was it: [http://www.houseofodd.com/wp-content/uploads/2007/10/star_wars_rocks_hugh_fleming.jpg](http://www.houseofodd.com/wp-content/uploads/2007/10/star_wars_rocks_hugh_fleming.jpg)

(or you can Google "Hugh Fleming").
Thank you! Yet another wallpaper has just been added to my rotation. :guitar:

---

### Post by dbbolton on 2008-09-08
> **doorknob60 said:**
> Kubuntu 8.10 Alpha, KDE4 FTW! :KS

[[IMG]http://img230.imageshack.us/img230/6444/screenshotme9.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=screenshotme9.jpg)
I didn't know that people still played Runescape.

---

### Post by ellalan on 2008-09-08
My recent desktop screen shot.

---

### Post by etnlIcarus on 2008-09-08
Something a bit more colourful than usual.

[[IMG]http://img47.imageshack.us/img47/5968/screenshotvz0.th.png[/IMG]](http://img47.imageshack.us/my.php?image=screenshotvz0.png)

---

### Post by rjmdomingo2003 on 2008-09-08
OB, wall from deviantart (Minimalism), conky, tint, x'mission...

---

### Post by ayoli on 2008-09-08
trying a wallpaper found few pages ago.
running, pidginscreenlet, conky, themepreview, screen., ...
[[IMG]http://ayozone.org/wp-content/gallery/screenshots-september-2008/thumbs/thumbs_08092008.png[/IMG]]("http://ayozone.org/gallery/screenshots-september-2008")

---

### Post by djdez92 on 2008-09-08
> **Muppeteer said:**
> My Arch system :)

May I ask what wallpaper that is? =)

---

### Post by chucky chuckaluck on 2008-09-08
details in terminal.

[[IMG]http://b.imagehost.org/t/0291/xfrothscr.jpg[/IMG]](http://b.imagehost.org/view/0291/xfrothscr.jpg)

---

### Post by AlexR1 on 2008-09-08
September Desktop

I started doing this to show,brown desktop can be nice nad shiny, tell me what do you think?
Info about Gtk theme can be found in terminal window.
Enjoy

---

### Post by markp1989 on 2008-09-08
a few changes i made today 

OS: hardy 64 bit
wm: Compiz fusion stand alone
GTK: Slickness-black
icons: black white 2
emerald: something i just made 
wallpaper: none  
dock: fbpanel 

anything else you wana know just ask

---

### Post by El_Belgicano on 2008-09-08
> **rjmdomingo2003 said:**
> OB, wall from deviantart (Minimalism), conky, tint, x'mission...

Mind sharing your .conkyrc? I'd like to get just the enveloppe lol and your reminder's thing...
TIA

---

### Post by indecisive on 2008-09-08
Comparing this months screenshots to last, I think the general taste of this community has improved.

---

### Post by urukrama on 2008-09-08
> **rjmdomingo2003 said:**
> OB, wall from deviantart (Minimalism), conky, tint, x'mission...

Looks very good. Do you have a link to the wallpaper?

**Chucky:** nice desktop too.

---

### Post by generollins on 2008-09-08
> **OutOfReach said:**
> New month, new look. :)
GTK Theme: Shiki-Colors, Shiki-Brave
Icons: GNOME-Brave (part of Gnome-Colors)
Emerald Theme: Shiki-Brave (Came included with Shiki-Colors)
Wallpaper: The infamous wallpaper used by willwill in that mockup


Thats cool how did u get the bar at the top (panel) black??

---

### Post by gjoellee on 2008-09-08
My Intrepid Ibex desktop (window open)

---

### Post by ellalan on 2008-09-08
Alexr1
Very nice DT,I like it.

---

### Post by ddnev45 on 2008-09-08
Fond a better looking wallpaper at gnome-look.org this morning (30118-fyre-gimp.jpg) so I made a few minor tweaks

For DJ_Peng: I couldn't locate my previous wallpaper at gnome-look, so I'll attempt to attach it.

Window mananger is OpenBox, Black-Aurora theme, tint and pypanel (systray only).

---

### Post by bluebyt on 2008-09-08
Desktop for September!

[http://screenshots.haque.net/screenshots/view/33775/]("http://screenshots.haque.net/screenshots/view/33775/")
[IMG]http://screenshots.haque.net/screenshots/thumb/33775/thumb-33775.jpg[/IMG]

---

### Post by awakatanka on 2008-09-08
kubuntu Intrepid alpha 5

---

### Post by voteforpedro36 on 2008-09-08
For some reason Photobucket decided to change my last screenshot of MPlayer, so here's yesterday again, I suppose everyone will know what I'm watching?:

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-7-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-7-08-media.png)
(lulz at my failure to be able to take a screenshot)

But today I installed Compiz Fusion, and am using it + emerald + awn. It runs much faster than with GNOME on Ubuntu, although I've had a couple of slowdowns.

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-8-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-8-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-8-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-8-08-media.png)

---

### Post by rjmdomingo2003 on 2008-09-09
> **urukrama said:**
> Looks very good. Do you have a link to the wallpaper?

**Chucky:** nice desktop too.

[http://plonko.deviantart.com/art/Minimalism-96905158](http://plonko.deviantart.com/art/Minimalism-96905158)

Cheers!

---

### Post by andrek on 2008-09-09
> **bluebyt said:**
> Desktop for September!

[http://screenshots.haque.net/screenshots/view/33775/]("http://screenshots.haque.net/screenshots/view/33775/")
[IMG]http://screenshots.haque.net/screenshots/thumb/33775/thumb-33775.jpg[/IMG]

Wow man, this dock looks astonishing ! Would you mind sharing with me the secret of it? You know, what's that dock and what's this theme. I'd be grateful.

---

### Post by crodway on 2008-09-09
> **PurposeOfReason said:**
> Found a way to make the system tray fit. Nothing really changed as this theme may be a keeper.

[Nabbed screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=84252&d=1220682753")

I've looked back through this thread and cant see that this wallpaper has been posted anywhere, and it's not mentioned on PurposeOfReason's DA page. Can anyone point me in the right direction?

cheers

---

### Post by rjmdomingo2003 on 2008-09-09
> **El_Belgicano said:**
> Mind sharing your .conkyrc? I'd like to get just the enveloppe lol and your reminder's thing...
TIA
Check this out for the low-down on Remind: [http://www.roaringpenguin.com/products/remind](http://www.roaringpenguin.com/products/remind)

---

### Post by What is in a name? on 2008-09-09
GTK and Metacity themes: Ubuntu Dust
Wallpaper: Breta
Icon theme: Eikon 2 (I'm getting excited with the way it's turning out; I'm still not so sure about the archive icons)
Font: Calibri bold, size 8

[[IMG]http://b.imagehost.org/t/0591/ecra.jpg[/IMG]](http://b.imagehost.org/view/0591/ecra.png)

---

### Post by Casper Hansen on 2008-09-09
Here's my desktop for September:

[[img]http://img74.imageshack.us/img74/4077/desktop8septemperjw2.th.png[/img]](http://img74.imageshack.us/my.php?image=desktop8septemperjw2.png)

GTK: Glossy - modified the colours.

Selected items background - #C3D9FF
Selected items text - #9D9D9D
All other backgrounds - #ffffff
All other text - #000000
 
Emerald: Googol. You can find it here: [http://gnome-look.org/content/show.php/Googol?content=83847](http://gnome-look.org/content/show.php/Googol?content=83847)

Wallpaper: Distro Balls Blue 1440x900. You can find it here: [http://gnome-look.org/content/show.php/Distro+balls?content=74628](http://gnome-look.org/content/show.php/Distro+balls?content=74628)

Icons: Deviant Oxygen. You can find it here: [http://gnome-look.org/content/show.php/deviant-oxygen?content=88575](http://gnome-look.org/content/show.php/deviant-oxygen?content=88575)

EDIT:

Mac OSX panelbackgrounds.

---

### Post by etnlIcarus on 2008-09-09
> **What is in a name? said:**
> GTK and Metacity themes: Ubuntu Dust
Wallpaper: Breta
Icon theme: Eikon 2 (I'm getting excited with the way it's turning out; I'm still not so sure about the archive icons)
Font: Calibri bold, size 8

[[IMG]http://b.imagehost.org/t/0591/ecra.jpg[/IMG]](http://b.imagehost.org/view/0591/ecra.png)

The bulls**t sickness as always, man. Although, considered a flat toolbar style?

[[IMG]http://img504.imageshack.us/img504/4632/screenyg7.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=screenyg7.jpg)

---

### Post by What is in a name? on 2008-09-09
> **etnlIcarus said:**
> The bulls**t sickness as always, man. Although, considered a flat toolbar style?

[[IMG]http://img504.imageshack.us/img504/4632/screenyg7.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=screenyg7.jpg)

The GTK theme in my screenshot isn't mine, it's been around on the Ubuntu artwork wiki for some time now. But yeah, I might tweak it to my taste for my personal use, as soon as Eikon lets me take a rest.

Thanks for the comment!

---

### Post by Truedream on 2008-09-09
> **What is in a name? said:**
> The GTK theme in my screenshot isn't mine, it's been around on the Ubuntu artwork wiki for some time now. But yeah, I might tweak it to my taste for my personal use, as soon as Eikon lets me take a rest.

Thanks for the comment!

Eikon2 looks *awesome* from that screen shot. Keep up the good work!

---

### Post by indecisive on 2008-09-09
> **ddnev45 said:**
> Fond a better looking wallpaper at gnome-look.org this morning (30118-fyre-gimp.jpg) so I made a few minor tweaks

For DJ_Peng: I couldn't locate my previous wallpaper at gnome-look, so I'll attempt to attach it.

Window mananger is OpenBox, Black-Aurora theme, tint and pypanel (systray only).

Where is the wallpaper from the first screenshot?

---

### Post by indecisive on 2008-09-09
> **etnlIcarus said:**
> The bulls**t sickness as always, man. Although, considered a flat toolbar style?

[[IMG]http://img504.imageshack.us/img504/4632/screenyg7.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=screenyg7.jpg)

Where is your wallpaper?

---

### Post by PurposeOfReason on 2008-09-09
> **indecisive said:**
> Where is your wallpaper?
Second!

---

### Post by Ub1476 on 2008-09-09
That wallpaper is from [interfacelift]("http://interfacelift.com/wallpaper_beta/downloads/date/any/").

---

### Post by indecisive on 2008-09-09
> **What is in a name? said:**
> The kind of concept you're applying in your desktop could be used in so many ways that it really excites me. And I'm glad KDE 4 is ready to allow that kind of original, unique look. I worry about the apparent lack of room in the screen with all those widgets, being the notification tray plasmoid the most critical example to me (I like to have it always visible somewhere, to easily click on any of the tray icons in case they start flashing with an update alert or something) and also the lack of a tasklist, but then again, considering your screen has the same resolution as mine, I guess it's not too much of a problem. I really love that "age of Discoveries" look. So I might try that one day. There are so many visual metaphors made possible by KDE4.

KDE4 really is qualifying itself to gradually become the "professional-looking" desktop environment in the open source world.

Where did you get the pictures of the compass and the pocket clock from, by the way?

How is KDE 4 original???  KDE has been a copy of the Windows desktop for a long time.  Also, how does it look any any more professional, especially with all its bugs and quirks and crashes.

---

### Post by shizakapayou on 2008-09-09
> **whitefang5412 said:**
> Simple and Functional.

That background is awesome - any chance you have a link to it?

Here's mine:
Dock: awn
Theme: SlicknesS [http://www.gnome-look.org/content/show.php/SlicknesS?content=71993](http://www.gnome-look.org/content/show.php/SlicknesS?content=71993)
Background: artwork for 'The Force Unleashed'

---

### Post by ZarathustraDK on 2008-09-09
Some more anime-desktop. This is a dual-monitor one. Left part is my computer-monitor (1440x900 19 inch), right part is my TV (1360x768 32 inch). All nicely stitched together with Twinview :)

Wallpapers from [http://www.animepaper.net/galleries/wallpapers/tags/cc](http://www.animepaper.net/galleries/wallpapers/tags/cc)

Theme is Shiki-wise from gnome-look.org

---

### Post by ayoli on 2008-09-09
> **indecisive said:**
> How is KDE 4 original???  KDE has been a copy of the Windows desktop for a long time.  Also, how does it look any any more professional, especially with all its bugs and quirks and crashes.

It is a good question.
Btw, I beleive that probably all DE have bugs and quirks and crashes.

---

### Post by Mazza558 on 2008-09-09
> **Ub1476 said:**
> That wallpaper is from [interfacelift]("http://interfacelift.com/wallpaper_beta/downloads/date/any/").

I found that earlier today - it works brilliantly as a wallpaper.

---

### Post by youngalfred on 2008-09-09
Eeepc has changed again.  more compact and exotic :)
theme: clearglow blue
icons: jungle
cursor: oxy-white
emerald: soft&clear (tweaked height)
its very usable and kinda matches the eeepc well :p

---

### Post by bluebyt on 2008-09-09
> **andrek said:**
> Wow man, this dock looks astonishing ! Would you mind sharing with me the secret of it? You know, what's that dock and what's this theme. I'd be grateful.

This is cairo-dock:
[http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en]("http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en")

The background of cairo-dock:
[http://stinky9.deviantart.com/art/Striped-84306524]("http://stinky9.deviantart.com/art/Striped-84306524")

Indicator of the dock:
[http://enzofx.deviantart.com/art/Mod-your-Dock-94794197]("http://enzofx.deviantart.com/art/Mod-your-Dock-94794197")

If you need more help, let me know!

---

### Post by Opeth115 on 2008-09-09
> **bluebyt said:**
> This is cairo-dock:
[http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en]("http://www.cairo-dock.org/ww_page.php?p=Accueil&lang=en")

The background of cairo-dock:
[http://stinky9.deviantart.com/art/Striped-84306524]("http://stinky9.deviantart.com/art/Striped-84306524")

Indicator of the dock:
[http://enzofx.deviantart.com/art/Mod-your-Dock-94794197]("http://enzofx.deviantart.com/art/Mod-your-Dock-94794197")

If you need more help, let me know!

Hey do you know of some sort of guide to configuring Cairo Dock or would you be able to help us set it up as you did, i've installed it but it's rather confusing, with a million options lol.

---

### Post by elmer_42 on 2008-09-09
Since my Ubuntu desktop hasn't changed much, here's a shot from my Windows partition:
[[img]http://arch.kimag.es/resized/11382670.png[/img]](http://arch.kimag.es/share/11382670.png)

---

### Post by Muppeteer on 2008-09-09
Some updates, loving cairo-dock at the minute :)

---

### Post by What is in a name? on 2008-09-09
> **Muppeteer said:**
> Some updates, loving cairo-dock at the minute :)

Could you please give us a link to that wallpaper?
Thanks in advance.

---

### Post by alejandro.mc on 2008-09-09
Minimal
10 walls



Cheers!

---

### Post by Muppeteer on 2008-09-09
> **What is in a name? said:**
> Could you please give us a link to that wallpaper?
Thanks in advance.

Sure thing...

[http://img28.picoodle.com/data/img28/3/9/9/f_Tetrism_40eff7b.jpg]("http://img28.picoodle.com/data/img28/3/9/9/f_Tetrism_40eff7b.jpg")

---

### Post by Stan_1936 on 2008-09-09
> **alejandro.mc said:**
> Minimal
10 walls....

:lolflag:

@the first screenshot:  Could there BE more minimal!!!

---

### Post by Patricrawley on 2008-09-10
Found a picture someone drew of Edward Norton in Fight Club using stumble upon and it inspired me to use this theme.

GTK: Customized clearlooks
Emerald: Custom
Icons: Foxtrot
AWN, VLC (-I ncurses)

---

### Post by etnlIcarus on 2008-09-10
> **Ub1476 said:**
> That wallpaper is from [interfacelift]("http://interfacelift.com/wallpaper_beta/downloads/date/any/").
Eey, bet me to it.
> **indecisive said:**
> 1 - How is KDE 4 original???  
2 - KDE has been a copy of the Windows desktop for a long time.  
3 - Also, how does it look any any more professional, 
4 - especially with all its bugs and quirks and crashes.

Without starting a KDE/Gnome/whatever debate:

1 - He didn't state that KDE *is* original; rather, that it *allowed* for original layouts and styles (at least more extensively than KDE3).

2 - KDE borrows a lot from Windows' explorer shell. So what? As long as they don't borrow past Win95/98, that's not a bad thing.

3 - I agree that KDE4 looks more professional; the desktop layout and look has been *designed*. Beyond mere immediate function, the clean and well-defined components are conducive to using the desktop as a work environment 'with an OS/Desktop that doesn't get in the way', to paraphrase the old axiom.

4 - Bugs, quirks and crashes do not intersect the look of an app/environment as they do it's functionality. Show me the bugs in a static KDE screenshot.

> **ZarathustraDK said:**
> Some more anime-desktop. This is a dual-monitor one. Left part is my computer-monitor (1440x900 19 inch), right part is my TV (1360x768 32 inch). All nicely stitched together with Twinview :)

Wallpapers from [http://www.animepaper.net/galleries/wallpapers/tags/cc](http://www.animepaper.net/galleries/wallpapers/tags/cc)

Theme is Shiki-wise from gnome-look.org

You're my hero. Love those walls.

---

### Post by skitzware on 2008-09-10
[[IMG]http://img84.imageshack.us/img84/457/sshothi2.th.png[/IMG]](http://img84.imageshack.us/my.php?image=sshothi2.png)

Mmm... Fluxbox...

---

### Post by ddnev45 on 2008-09-10
> **indecisive said:**
> Where is the wallpaper from the first screenshot?

It's at gnome-look.org as well; Title: 30118-fyre-gimp.jpg

---

### Post by mrgnash on 2008-09-10
[IMG]http://i35.tinypic.com/344fdpe.png[/IMG]

```

 Metacity:              NewHuman
  GTK:                   Light Glow Ibex
  Font (Apps):           Droid Sans 11
  Font (Terminal):       Droid Sans Mono 12
  Icons:                 gnome-human
  Wall:                  kristin-kreuk-1600x1200-31600.jpg

```

---

### Post by myusername on 2008-09-10
> **skitzware said:**
> [[IMG]http://img84.imageshack.us/img84/457/sshothi2.th.png[/IMG]](http://img84.imageshack.us/my.php?image=sshothi2.png)

Mmm... Fluxbox...

beautiful

---

### Post by el mariachi on 2008-09-10
> **Patricrawley said:**
> Found a picture someone drew of Edward Norton in Fight Club using stumble upon and it inspired me to use this theme.

GTK: Customized clearlooks
Emerald: Custom
Icons: Foxtrot
AWN, VLC (-I ncurses)
my absolute favorite movie :D

---

### Post by chucky chuckaluck on 2008-09-10
> **alejandro.mc said:**
> Minimal
10 walls



Cheers!

the one on the right reminds me of laser tag.

---

### Post by etnlIcarus on 2008-09-10
[[IMG]http://img362.imageshack.us/img362/7740/toolbarrx3.th.jpg[/IMG]](http://img362.imageshack.us/my.php?image=toolbarrx3.jpg)

Can someone please explain why Thunar and PCmanFM still show toolbars as icons, rather than text? I've set the toolbars to text in xfce-mcs-manager; gconf-editor (some apps designed for Gnome need this eg. baobab) and in my .gtkrc-2.0. I've also logged out and restarted X.

---

### Post by raul_ on 2008-09-10
I just came across this thread

[http://ubuntuforums.org/showthread.php?t=915928]("http://ubuntuforums.org/showthread.php?t=915928")

the site linked has some pretty unimpressive Windows and Mac shots. I think we should make some publicity :p

---

### Post by elmer_42 on 2008-09-10
Got a bit of time to work on my desktop. I'm not sure the wallpaper really matches well, I'm either going to find or make a new one. How do you all like it so far, though?
[[img]http://arch.kimag.es/resized/13873996.png[/img]](http://arch.kimag.es/share/13873996.png)

---

### Post by raul_ on 2008-09-10
I just posted my desktop and the comments are pretty self explanatory:

> Never heard of Arch Linux. That theme you have there is pretty bad *** though. 

Posted by: maclover 


---

### Post by elmer_42 on 2008-09-10
Wow, record time on finding a new wallpaper. I'm surprised. How do you think this one matches?
[[img]http://arch.kimag.es/resized/92798694.png[/img]](http://arch.kimag.es/share/92798694.png)
[SIZE="1"]NOTE: I realize my conky is misaligned by a bit in this picture, it's fixed now[/SIZE]

---

### Post by andrek on 2008-09-10
> **elmer_42 said:**
> Wow, record time on finding a new wallpaper. I'm surprised. How do you think this one matches?
(image)
[SIZE="1"]NOTE: I realize my conky is misaligned by a bit in this picture, it's fixed now[/SIZE]

What's the panel you're using here?

---

### Post by elmer_42 on 2008-09-10
That would PyPanel. Here is my .pypanelrc, which I modified to match my Openbox theme:
```
#------------------------------------------------------------------------------
#
#                         PyPanel v2.4 Configuration
#
# This configuration file is a Python script that will be executed when
# PyPanel is started.  In order for PyPanel to start properly, make sure that
# this file contains proper Python formatting and no syntax errors.
#------------------------------------------------------------------------------
VERSION         = 2.4           # Config file version

#------------------------------------------------------------------------------
# Colors: Format is hex triplet - 0xrrggbb
#------------------------------------------------------------------------------
BG_COLOR        = "0x272c30"    # Panel background and tinting color
TASK_COLOR      = "0x9394a2"    # Normal task name color 
FOCUSED_COLOR   = "0xbfc0d0"    # Focused task name color
SHADED_COLOR    = "0x9394a2"    # Shaded task name color 
MINIMIZED_COLOR = "0x9394a2"    # Minimized task name color 
DESKTOP_COLOR   = "0x272c30"    # Desktop name color
CLOCK_COLOR     = "0xe6e6e6"    # Clock text color
LINE_COLOR      = "0x9394a2"    # Vertical line color

# Text Shadow Colors
TASK_SHADOW_COLOR      = "0xffffff"
FOCUSED_SHADOW_COLOR   = "0xffffff"
SHADED_SHADOW_COLOR    = "0xffffff"
MINIMIZED_SHADOW_COLOR = "0xffffff" 
DESKTOP_SHADOW_COLOR   = "0xffffff"
CLOCK_SHADOW_COLOR     = "0xffffff"

#------------------------------------------------------------------------------
# Panel Spacing and Location Options: Measured in pixels
#------------------------------------------------------------------------------
P_LOCATION      = 1             # Panel placement: 0 = top, 1 = bottom
P_WIDTH         = 1300          # Panel width: 0 = Use full screen width
P_START         = 70            # Starting X coordinate of the panel
P_SPACER        = 6             # Spacing between panel objects
P_HEIGHT        = 24            # Panel height

#------------------------------------------------------------------------------
# Icon Size Options: Measured in pixels
#------------------------------------------------------------------------------
I_HEIGHT        = 16            # Panel application icon height
I_WIDTH         = 16            # Panel application icon Width 
APPL_I_HEIGHT   = 24            # Application launcher icon height
APPL_I_WIDTH    = 24            # Application launcher icon width
TRAY_I_HEIGHT   = 24            # System tray icon height (usually 16 or 24)
TRAY_I_WIDTH    = 24            # System tray icon width  (usually 16 or 24)
                                # If TRAY_I_WIDTH is set to 0, then the
                                # width specified by the tray app will be used
                                
#------------------------------------------------------------------------------
# Panel Clock Format: 'man strftime' for detailed formatting options and help
#------------------------------------------------------------------------------
CLOCK_FORMAT    = "%Y-%m-%d %H:%M"    # Ex: 2004-09-25 17:45 

#------------------------------------------------------------------------------
# Clock Delay: Seconds between each clock update during periods of inactivity
#------------------------------------------------------------------------------
CLOCK_DELAY     = 20

#------------------------------------------------------------------------------
# Hidden Application List: Apps listed here will not be display on the panel
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
# Ex: ["xmms", "xine", "gDesklets"]
#------------------------------------------------------------------------------
HIDE_LIST       = []            
                   
#------------------------------------------------------------------------------
# Hidden Panel Size: Size of the panel when it's hidden/minimized
#------------------------------------------------------------------------------
HIDDEN_SIZE     = 2

#------------------------------------------------------------------------------
# Panel Text Font: This option takes either a traditional or Xft font string 
# Ex: "-schumacher-clean-medium-r-normal-*-12-*-*-*-*-*-*-*"
#     "aquafont-8" 
#------------------------------------------------------------------------------
FONT            = "AquaBase-9"

#------------------------------------------------------------------------------
# Show All Applications: Show apps from all desktops or just the current
# 0: Disabled - Only applications on the current desktop will be displayed
# 1: Enabled  - Selected apps are moved to the current desktop
# 2: Enabled  - Current desktop is changed to the selected apps desktop
#------------------------------------------------------------------------------
SHOWALL         = 0             # 0, 1 or 2 - see descriptions above

#------------------------------------------------------------------------------
# Show Minimized/Iconified Applications: Show only minimized apps or all apps
# 0: Disabled - Show all applications on the panel
# 1: Enabled  - Show only minimized apps on the panel
#------------------------------------------------------------------------------
SHOWMINIMIZED   = 0

#------------------------------------------------------------------------------
# Application Icon List: List of custom icons for specific applications
# The application name is its WM_CLASS name, use 'xprop' to find WM_CLASS
#
# The "default" entry is used for applications with no icon.  If left "",
# PyPanel will use the default icon distributed with the source.
#
# Add entries using the following format -
#     "<application name>" : "<full path to icon>",
#------------------------------------------------------------------------------
ICON_LIST       = {
                   "default" : "",
                   "example" : "/usr/share/imlib2/data/images/audio.png",
                  }
                  
#------------------------------------------------------------------------------
# Application Launch List: Ordered list of icons and applications for the
#                          application launcher.
# 
# Add entries using the following format -
#     ("<executable>", "<full path to icon>")
#------------------------------------------------------------------------------
LAUNCH_LIST     = [
                   ("gimp-2.2", "/usr/share/imlib2/data/images/paper.png"), 
                  ]

#------------------------------------------------------------------------------
# Background Alpha/Shade Level: 0 (Fully Translucent) -> 255 (Fully Opaque)
# BG_COLOR is used for tinting
#------------------------------------------------------------------------------
SHADE           = 255

#------------------------------------------------------------------------------
# Misc. Options: 1 = Enabled/Yes, 0 = Disabled/No
#------------------------------------------------------------------------------
ABOVE           = 1             # Panel is always above other apps
APPICONS        = 0             # Show application icons
AUTOHIDE        = 0             # Autohide uses the CLOCK_DELAY timer above
SHADOWS         = 0             # Show text shadows
SHOWLINES       = 0             # Show object seperation lines
SHOWBORDER      = 0             # Show a border around the panel

#------------------------------------------------------------------------------
# Desktop Names: Configure the names of your desktops
# If the option is [], PyPanel will attempt to use the desktop name specified
# by the XServer, if that fails it will use the desktop number as its name
# Ex. ["One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight"]
#------------------------------------------------------------------------------
DESKTOP_NAMES   = ["1", "1", "1", "1"]

#------------------------------------------------------------------------------
# Panel Layout:       -----------------------------------
#                     [  1  ][  2  ][  3  ][  4  ][  5  ]
#                     -----------------------------------
#
# The panel layout is split into 5 sections numbered 1, 2, 3, 4 or 5 as shown
# in the diagram above.  Each of the following objects can be enabled by
# assigning it a section number or disabled by assigning it 0:
#------------------------------------------------------------------------------
DESKTOP         = 1             # Desktop name section
TASKS           = 2             # Task names section 
TRAY            = 0             # System tray section
CLOCK           = 0             # Clock section
LAUNCHER        = 0             # Application launcher section

#------------------------------------------------------------------------------
#                       Button Event Function Definitions
#------------------------------------------------------------------------------
# Left click   - button 1 
# Middle click - button 2
# Right click  - button 3
# Wheel up     - button 4
# Wheel down   - button 5 
#
# changeDesktop(x)
# - Change Desktop: Increase or decrease the current desktop by 'x' amount
# 
# toggleShade(task)
# - Shade or Unshade an application
#
# toggleHidden()
# - Minimize the panel to the top or bottom depending on its start location
#
# toggleMinimize(task, traise=1)
# - Minimize or Unminimize an application and optionally raise it
#
# taskRaise(task, focus=1)
# - Raise an application to the top of the window list and optionally focus it 
#
# taskLower(task, focus=0)
# - Lower an app to the bottom of the window list and optionally focus it
#
# taskFocus(task)
# - Give focus to the selected application, if it has focus then minimize it
#
# showDesktop()
# - Toggle between hiding and unhiding ALL applications
#------------------------------------------------------------------------------

#----------------------------------
def desktopButtonEvent(pp, button):
#----------------------------------
    """ Button event handler for the panel's desktop object """
        
    if button == 1:
        pp.changeDesktop(-1)
    elif button == 2:
        pp.changeDesktop(2)
    elif button == 3:
        pp.changeDesktop(1)
    elif button == 4:
        pp.changeDesktop(1)
    elif button == 5:
        pp.changeDesktop(-1)
        
#--------------------------------
def clockButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel's clock object """
    
    if button == 1:
        os.system("xclock &")
    elif button == 2:
        pass
    elif button == 3:
        pp.toggleHidden()  
    elif button == 4:
        pp.showDesktop()
    elif button == 5:
        pp.showDesktop()
        
#--------------------------------
def panelButtonEvent(pp, button):
#--------------------------------
    """ Button event handler for the panel with no active tasks """
    
    if button == 1:
        pass
    elif button == 2:
        pass
    elif button == 3:
        pass
    elif button == 4:
        pass
    elif button == 5:
        pass
        
#-------------------------------------
def taskButtonEvent(pp, button, task):
#-------------------------------------
    """ Button event handler for the panel's tasks """
    
    if button == 1:
        pp.taskFocus(task)
    elif button == 2:
        # Destroy the application
        task.obj.destroy()
    elif button == 3:
        # Ex. - XMMS doesn't shade, so we want to minimize it instead and
        #       still use button 3 to shade other applications
        #       task.tclass is the tasks class name (WM_CLASS)
        if "xmms" in task.tclass:
            pp.toggleMinimize(task)
        else:
            pp.toggleShade(task)
    elif button == 4:
        pp.taskRaise(task, focus=1)
    elif button == 5:
        pp.taskLower(task, focus=0)
```

---

### Post by vishzilla on 2008-09-10
Back to good ol' GNOME for a change

[[img]http://xs231.xs.to/xs231/08373/ubuntu_sept697.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs231&d=08373&f=ubuntu_sept697.png) [[img]http://xs331.xs.to/xs331/08373/ubuntu_sept01915.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs331&d=08373&f=ubuntu_sept01915.png)

---

### Post by billgoldberg on 2008-09-10
[http://www.ourdesktops.com/desktops/58151fbd-6fb9-44a1-90a2-2189ec959fdd.jpg](http://www.ourdesktops.com/desktops/58151fbd-6fb9-44a1-90a2-2189ec959fdd.jpg)

---

### Post by elmer_42 on 2008-09-10
I wouldn't exactly classify that link as safe for work, Bill.

---

### Post by billgoldberg on 2008-09-10
> **elmer_42 said:**
> I wouldn't exactly classify that link as safe for work, Bill.

Why would that be?

---

### Post by meborc on 2008-09-10
> **billgoldberg said:**
> Why would that be?

probably because of the girl in the wall :D

---

### Post by billgoldberg on 2008-09-10
> **meborc said:**
> probably because of the girl in the wall :D

She has clothes on, I don't see the problem. Unless a women is nsfw.

:p

---

### Post by el mariachi on 2008-09-10
dock?

---

### Post by Casper Hansen on 2008-09-10
Desktop on my laptop:

[[IMG]http://img229.imageshack.us/img229/9524/desktop10septemberyc8.th.png[/IMG]](http://img229.imageshack.us/my.php?image=desktop10septemberyc8.png)

---

### Post by el mariachi on 2008-09-10
is it possible to use custom indicators with awn?
I can't set an "active icon" if that's it

---

### Post by Patricrawley on 2008-09-10
> **vishzilla said:**
> Back to good ol' GNOME for a change


What's your icon theme?

---

### Post by bluebyt on 2008-09-10
> **Opeth115 said:**
> Hey do you know of some sort of guide to configuring Cairo Dock or would you be able to help us set it up as you did, i've installed it but it's rather confusing, with a million options lol.

You can change the background in background tab and the indicator in indicator tab.

For more help you can ask questions to the cairo-dock forum, it is mostly in French but can you can post in English everybody are very friendly there.

[http://www.cairo-dock.org/bg_forumlist.php]("http://www.cairo-dock.org/bg_forumlist.php")

---

### Post by ddnev45 on 2008-09-10
Setting up Openbox made me feel nostalgic for my old favorite Fvwm, so I put it on my laptop.

---

### Post by lega on 2008-09-10
> **What is in a name? said:**
> GTK and Metacity themes: Ubuntu Dust
Wallpaper: Breta
Icon theme: Eikon 2 (I'm getting excited with the way it's turning out; I'm still not so sure about the archive icons)
Font: Calibri bold, size 8

[[IMG]http://b.imagehost.org/t/0591/ecra.jpg[/IMG]](http://b.imagehost.org/view/0591/ecra.png)
the icon of that forecast is on the top panel, is an applet? you can tell me the name and the link where you find it? thanks!

---

### Post by What is in a name? on 2008-09-10
> **lega said:**
> the icon of that forecast is on the top panel, is an applet? you can tell me the name and the link where you find it? thanks!

That is the regular weather applet with a 128 pixels icon.
The weather icons on Eikon are left that big on purpose because I like that effect you noticed on the panel.

---

### Post by ad_267 on 2008-09-10
I just discovered the hydroxygen icons. MurrineGlow Pink with hydroxygen icons. Wallpaper was from someone else in this thread.

---

### Post by SomeGuyDude on 2008-09-10
> **ad_267 said:**
> I just discovered the hydroxygen icons. MurrineGlow Pink with hydroxygen icons. Wallpaper was from someone else in this thread.

The Hydroxygen icon set is pretty dang amazing. I just threw it onto my setup and am loving it.

---

### Post by vietseo on 2008-09-10
vote for Casper Hansen's desktop

---

### Post by whitefang5412 on 2008-09-10
I smell jealousy already.

Fedora core 9
Theme is clear glow green
Trans bar with a few icons, window selector, and that application list at the right.
Gdesklets clock.
Background came from gnomelook.org

---

### Post by vishzilla on 2008-09-10
> **Patricrawley said:**
> What's your icon theme?

Crashbit

---

### Post by dbbolton on 2008-09-10
> **el mariachi said:**
> is it possible to use custom indicators with awn?
I can't set an "active icon" if that's it
I think changing the arrow color/offset is about as "custom" as you can get, sadly.

---

### Post by etnlIcarus on 2008-09-10
> **vishzilla said:**
> Back to good ol' GNOME for a change

[[img]http://xs231.xs.to/xs231/08373/ubuntu_sept697.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs231&d=08373&f=ubuntu_sept697.png) [[img]http://xs331.xs.to/xs331/08373/ubuntu_sept01915.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs331&d=08373&f=ubuntu_sept01915.png)
Eey, a smashmethod wallpaper. love that guy. Wish he'd made more than 3 decent wallpapers, though.
> **billgoldberg said:**
> She has clothes on, I don't see the problem. Unless a women is nsfw.

:p

Perhaps Elmer is Iranian. :P

---

### Post by elmer_42 on 2008-09-11
> **etnlIcarus said:**
> [QUOTE=billgoldberg;5763194]She has clothes on, I don't see the problem. Unless a women is nsfw. :p
Perhaps Elmer is Iranian. :p[/QUOTE]
Nope, but if I was an employer and I saw that on somebody's screen, there would be some explaining to do about why the employee was looking at pictures of half-naked women.

---

### Post by etnlIcarus on 2008-09-11
> **elmer_42 said:**
> Nope, but if I was an employer and I saw that on somebody's screen, there would be some explaining to do about why the employee was looking at pictures of half-naked women.

You'd make a *terrible* boss. I suppose you'd have something to say about the empty beer cans and the hooker under my desk as well, huh?

---

### Post by kuad on 2008-09-11
> **el mariachi said:**
> dock?

Is the wallpaper from The Place Promised in Our Early Days?

---

### Post by el mariachi on 2008-09-11
> **dbbolton said:**
> I think changing the arrow color/offset is about as "custom" as you can get, sadly.
:(
> **kuad said:**
> Is the wallpaper from The Place Promised in Our Early Days?
it is:KS

---

### Post by Macintosh Sauce on 2008-09-11
> **tehforum said:**
> Here is my desktop.

If you want the real thing, get a real Mac. ;)

[[IMG]http://www.jamesnrhodes.com/personal/james/macosx/desktops/macdesktop_09112008_small.png[/IMG]]("http://www.jamesnrhodes.com/personal/james/macosx/desktops/macdesktop_09112008.png")

---

### Post by el mariachi on 2008-09-11
aww but they cost so much :'(

---

### Post by TheSlipstream on 2008-09-11
Unfortunately this is a recent install, and I don't have the programs to make sophisticated screenshots (still looking for a good music manager with no GNOME or KDE deps that isn't Exaile). Openbox, btw.

GTK: Murrina-Black
Openbox theme: Anuri-1
Icons: Areo

---

### Post by joninkrakow on 2008-09-11
Here's mine. An entirely new computer. I never thought I would go back to Gnome, but it's running fine on my MSI Wind. Theme is Shiki-wise, including icons. Only "customization is the DMZ black mouse. I believe the desktop background, however, is one of the defaults from the default Windows install--only thing worth having from there. ;-)

(both clean and dirty shots...)

---

### Post by johnny9794 on 2008-09-11
not much here.

---

### Post by Mark76 on 2008-09-11
**OS:** Ubuntu Hardy Minimal
**Desktop Environment:** ROX
**Top Panel:** ROX Panel with RETicker running
**Bottom Panel:** ROX Panel with various ROX applets (from left to right (after filer icons): NetStat, hddtemp, Load, Mem, FreeFS, Dev(ice)Tray, Pager, TaskTray, Weather, SystemTrayN (with Memo and Gajim running), Clock, ROX-Session and System)
**Pinboard Background Manager:** XPlanet
**Window Manager:** OroboROX with RISCOS theme
**Pinboard Icons:** Applications' own.
**Pinboard Font:** URW Chancery L Bold Italic 16
**GTK Theme:** Industrial.

Nothing fancy, but it suits me

---

### Post by xen14 on 2008-09-11
my first attempt at customizing. :)

Theme: [Metrosuave]("http://gnome-look.org/content/show.php/Metrosuave?content=77585") with [ClearGlow]("http://gnome-look.org/content/show.php/ClearGlow?content=88122")
Wallpaper: an old favorite pic, all credit goes to the author (which sadly I dont remember)
Screenlets: ClockRing and Circle Sensors.

---

### Post by elmer_42 on 2008-09-11
> **etnlIcarus said:**
> I suppose you'd have something to say about the empty beer cans and the hooker under my desk as well, huh?
I might, it depends on the day. :p

---

### Post by mrgnash on 2008-09-11
[IMG]http://i37.tinypic.com/2vxixrl.png[/IMG]

```

  Metacity:              Tango
  GTK:                   chrome-like
  Font (Apps):           Droid Sans 11
  Font (Terminal):       Droid Sans Mono 12
  Icons:                 gnome-brave
  Wall:                  vladstudio_black_hole_1600x1200.jpg

```

---

### Post by Macintosh Sauce on 2008-09-11
> **el mariachi said:**
> aww but they cost so much :'(

Not really. When I bought my Mac Pro, I compared it to a similarly equipped DELL system - the Mac Pro was cheaper by $500. :) Of course, over the last year I have added 16 GB of RAM and new 1.0 TB HDs - not terribly expensive but well worth it IMO.

If you need a Mac you could get the iMac - it is a nice system. If I did not have a Mac Pro, I'd get one of the new iMacs.

---

### Post by ddnev45 on 2008-09-11
> **etnlIcarus said:**
> You'd make a *terrible* boss. I suppose you'd have something to say about the empty beer cans and the hooker under my desk as well, huh?

All I'd have to say is -- "Are you hiring?"

---

### Post by el mariachi on 2008-09-11
> **Macintosh Sauce said:**
> Not really. When I bought my Mac Pro, I compared it to a similarly equipped DELL system - the Mac Pro was cheaper by $500. :) Of course, over the last year I have added 16 GB of RAM and new 1.0 TB HDs - not terribly expensive but well worth it IMO.

If you need a Mac you could get the iMac - it is a nice system. If I did not have a Mac Pro, I'd get one of the new iMacs.
I wanted a Macbook but for the same price I can get a Vaio with more horsepower, more hd space, more memory, more....

---

### Post by chucky chuckaluck on 2008-09-11
> **TheSlipstream said:**
> (still looking for a good music manager with no GNOME or KDE deps that isn't Exaile).

what about something like mpd, or cplay?

---

### Post by boobuntu on 2008-09-11
Here is my latest:

[http://www.ourdesktops.com/desktop_user.aspx?user=boobunt]("http://www.ourdesktops.com/desktop_user.aspx?user=boobuntu")u

---

### Post by indecisive on 2008-09-11
Why would anyone want a Mac aside from the shiny desktop?  If that is worth so much more money, grow up.  I have a Mac and the shiny desktop really gets old quick, and I feel Linux is so superior, especially when you find the maturity to look past a little uglier of a desktop.

---

### Post by Killeroid on 2008-09-11
Here's mine

[[IMG]http://farm4.static.flickr.com/3044/2848353561_e022cbcfa3.jpg[/IMG]](http://farm4.static.flickr.com/3044/2848353561_687127214c_o.png)

[[IMG]http://farm4.static.flickr.com/3203/2849190224_515d2b3da8.jpg[/IMG]](http://farm4.static.flickr.com/3203/2849190224_6c3f7cc0b0_o.png)

GTK/Metacity : **[Elegant Blue]("http://gnome-look.org/content/show.php/Elegant-Blue?content=85622")**
Font: **Calibri**

Using tint as my panel and trayer as my system tray.
Got the desktop off deviantart, forgot the authors name. PM me if you want the wallpaper and I will send it to you.

---

### Post by boobuntu on 2008-09-11
> **indecisive said:**
> Why would anyone want a Mac aside from the shiny desktop?  If that is worth so much more money, grow up.  I have a Mac and the shiny desktop really gets old quick, and I feel Linux is so superior, especially when you find the maturity to look past a little uglier of a desktop.

It's a desktop... take a deep breath...

---

### Post by el mariachi on 2008-09-11
> **indecisive said:**
> Why would anyone want a Mac aside from the shiny desktop?  If that is worth so much more money, grow up.  I have a Mac and the shiny desktop really gets old quick, and I feel Linux is so superior, especially when you find the maturity to look past a little uglier of a desktop.
I hate OpenOffice :(
I like iWork
I hate when this sort of thing happens to me lol

---

### Post by PurposeOfReason on 2008-09-11
> **indecisive said:**
> Why would anyone want a Mac aside from the shiny desktop?  If that is worth so much more money, grow up.  I have a Mac and the shiny desktop really gets old quick, and I feel Linux is so superior, especially when you find the maturity to look past a little uglier of a desktop.
Are you kidding? Linux is NOT for everyone. There is a 100% chance that everything the mac comes with will just work. People need that.

---

### Post by What is in a name? on 2008-09-11
> **el mariachi said:**
> I hate OpenOffice :(
I like iWork
I hate when this sort of thing happens to me lol

...and I think the first time I actually liked to have OpenOffice running in front of me for more than 10 minutes was when I installed the last beta.

And anyway, it still doesn't totally feel "right" to me. Which is a shame, because otherwise OpenOffice.org Writer would probably be my most used app (considering I'm a pseudo-writer myself). It is not.

Yes. Sometimes I do use Gedit for the task. How odd is that?

---

### Post by PurposeOfReason on 2008-09-11
> **What is in a name? said:**
> ...and I think the first time I actually liked to have OpenOffice running in front of me for more than 10 minutes was when I installed the last beta.

And anyway, it still doesn't totally feel "right" to me. Which is a shame, because otherwise OpenOffice.org Writer would probably be my most used app (considering I'm a pseudo-writer myself). It is not.

Yes. Sometimes I do use Gedit for the task. How odd is that?
Considering gedit is the best, not odd at all. :)

Any idea when eikon2 will be out?

---

### Post by What is in a name? on 2008-09-11
> **PurposeOfReason said:**
> Considering gedit is the best, not odd at all. :)

Any idea when eikon2 will be out?

Pretty soon, like... Today, perhaps. I'm just ironing some details, but overally speaking it already looks pretty good to me and for most applications. And it is a major overhaul from the first days of Eikon.

---

### Post by el mariachi on 2008-09-11
Eikon sounds like Icon for us Portuguese chaps :D but I wonder how english people would say it haha
(I'm also using the Beta wiian)

---

### Post by ad_267 on 2008-09-11
Wasn't there legal issues with the first eikon set so that it couldn't be included on gnome-look etc. Will this be the case with eikon2?

---

### Post by What is in a name? on 2008-09-11
> **el mariachi said:**
> Eikon sounds like Icon for us Portuguese chaps :D but I wonder how english people would say it haha
(I'm also using the Beta wiian)

Just as a matter of curiosity, I actually baptized Eikon after the Greek word for "image".

Not that it is important, of course.
Oh, and the beta version had some bugs. Including several symlinks pointing to nowhere (more exactly, to an absolute path inside of MY home folder). Awful.

---

### Post by dbbolton on 2008-09-11
> **el mariachi said:**
> Eikon sounds like Icon for us Portuguese chaps :D but I wonder how english people would say it haha
(I'm also using the Beta wiian)
To German speakers it sounds something like "EYE-cone" :lol:

---

### Post by What is in a name? on 2008-09-11
> **ad_267 said:**
> Wasn't there legal issues with the first eikon set so that it couldn't be included on gnome-look etc. Will this be the case with eikon2?

Most likely, yes. But this time I'll try to keep the link in a more visible location, like at the descriptions of my themes, over here in the forum, etc. I just won't put up a special page just for Eikon. At least not for now. I'm still open to suggestions. Yes, I know many many people have been posting icon sets using proprietary material for ages on the most visible places, including some really ugly ones from Vista (yes, I find many of them even worse than the XP ones) and the most über-shiny, glossy, Aqua-ish and dated icons from the Mac world, and they never had problems. I'm just worried with the fact that some of the authors of the icons I used (many of my sources are anonymous web artists like myself) and then modified for Eikon probably didn't allow that kind of use of their work. Am I being too nit-picky?

---

### Post by chucky chuckaluck on 2008-09-11
xfce and my cat, jimmy.

[[IMG]http://c.imagehost.org/t/0669/jimmyscr.jpg[/IMG]](http://c.imagehost.org/view/0669/jimmyscr.jpg)

---

### Post by Mark76 on 2008-09-11
Man. You live in a really low-res neighbourhood :lol:

---

### Post by elmer_42 on 2008-09-11
> **el mariachi said:**
> Eikon sounds like Icon for us Portuguese chaps :D but I wonder how english people would say it haha
I've always thought that it was supposed to be said like the word "icon" because it was a set of icons. While I'm not English, I am a native English speaker, but I imagine those crazy Brits (:p) would have a different way of saying it.

---

### Post by ad_267 on 2008-09-11
> **What is in a name? said:**
> Most likely, yes. But this time I'll try to keep the link in a more visible location, like at the descriptions of my themes, over here in the forum, etc. I just won't put up a special page just for Eikon. At least not for now. I'm still open to suggestions. Yes, I know many many people have been posting icon sets using proprietary material for ages on the most visible places, including some really ugly ones from Vista (yes, I find many of them even worse than the XP ones) and the most über-shiny, glossy, Aqua-ish and dated icons from the Mac world, and they never had problems. I'm just worried with the fact that some of the authors of the icons I used (many of my sources are anonymous web artists like myself) and then modified for Eikon probably didn't allow that kind of use of their work. Am I being too nit-picky?

That sounds fair enough really, I'm sure most of the artists wouldn't have a problem with it but it's hard to know unless you can contact all of them. And yeah there's a lot of far more dodgy icon sets on gnome-look.

---

### Post by Bart_D on 2008-09-11
> **Mark76 said:**
> Man. You live in a really low-res neighbourhood :lol:

Hahahaha!!!

---

### Post by el mariachi on 2008-09-11
> **What is in a name? said:**
> Just as a matter of curiosity, I actually baptized Eikon after the Greek word for "image".

Not that it is important, of course.
Oh, and the beta version had some bugs. Including several symlinks pointing to nowhere (more exactly, to an absolute path inside of MY home folder). Awful.
that's the root word for the portuguese ícone (icon), that's why I said that hehe very clever of you actually:KS (and the greeks of course hehe)

---

### Post by mike1234 on 2008-09-11
> **supersonicdarky said:**
> [[IMG]http://img.photobucket.com/albums/v242/supersonicdarky/september_08_thumb.png[/IMG]]("http://supersonicdarky.deviantart.com/art/September-2008-96711189")
wall: no idea
gtk: vorta
icons: micro
openbox: bright side (modded)

pcmanfm, transmission (I'm working on that ratio...), pidgin, gmplayer, conky, pypanel


"wall: no idea"?

 Might look on your hard drive. I bet it's there. :) I want to see more wallpapers on here. I get bored easily.

M.

---

### Post by What is in a name? on 2008-09-11
> **el mariachi said:**
> that's the root word for the portuguese ícone (icon), that's why I said that hehe very clever of you actually:KS (and the greeks of course hehe)

Ah, those Greeks, Romans and Arabians sure left us a great heritage, didn't they?...
And now that I think of it, I think "eikon" is indeed pronounced the same way we do in Portuguese (the "ei" ditongue is said like a simple "i", like the sound from the words with "ee" in the English language; just like the Greek "ai" is pronounced like an "eh").

I also believe I haven't been sleeping enough. :s

Ah well. Enough of my ramblings.

**Eikon2, Release Candidate 1**: [http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html](http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html)

It's a premiere, hehe.

EDIT: I'd just like to know the correct names of the icons that affect the following three areas:

- the Authorizations icon, under System > Administration on the GNOME menu;
- the Network icon, also under System > Administration;
- and the Autostarted Apps icon of Xfce's settings dialog.

Thanks in advance, in case someone knows the answer.

---

### Post by mike1234 on 2008-09-11
Sweet! I've been looking for pic on left for a long time.

Thanks,

M.

---

### Post by mike1234 on 2008-09-11
> **fedex1993 said:**
> backgrounds i want :) where did you get them from ?


 Copy, save, use Gimp.

M.

---

### Post by ad_267 on 2008-09-11
> **What is in a name? said:**
> 
**Eikon2, Release Candidate 1**: [http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html](http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html)


Nice work thanks! Only one small issue I've found so far is that there isn't a rhythmbox-notplaying.png (I just symlink that to rhythmbox.png) so that the system tray icon changes to the default rhythmbox icon when it's not playing.

---

### Post by mike1234 on 2008-09-11
> **el mariachi said:**
> [http://wooko.deviantart.com/art/GAAW-97035227](http://wooko.deviantart.com/art/GAAW-97035227) is anyone familiar with this wallpaper? I saw it a long time ago but now can't find it


here. 
click on image "see full size"


M.
[http://images.google.com/imgres?imgurl=http://bp3.blogger.com/_-L1Z7tBgfdU/SDutApyUBNI/AAAAAAAAAyo/ou_GZsviB-Q/s400/morning%2Bdew.png&imgrefurl=http://www.geekai.com/2008_05_01_archive.html&h=200&w=355&sz=123&hl=en&start=52&um=1&usg=__ZHVjkSGJB06skNtEinWfQDT9Z5c=&tbnid=jtKt3HMgYPIx3M:&tbnh=68&tbnw=121&prev=/images%3Fq%3Dwallpaper%2B-%2Bmorning%2Bdew%26start%3D40%26ndsp%3D20%26um%3D1%26hl%3Den%26suggon%3D0%26safe%3Doff%26sa%3DN]("http://images.google.com/imgres?imgurl=http://bp3.blogger.com/_-L1Z7tBgfdU/SDutApyUBNI/AAAAAAAAAyo/ou_GZsviB-Q/s400/morning%2Bdew.png&imgrefurl=http://www.geekai.com/2008_05_01_archive.html&h=200&w=355&sz=123&hl=en&start=52&um=1&usg=__ZHVjkSGJB06skNtEinWfQDT9Z5c=&tbnid=jtKt3HMgYPIx3M:&tbnh=68&tbnw=121&prev=/images%3Fq%3Dwallpaper%2B-%2Bmorning%2Bdew%26start%3D40%26ndsp%3D20%26um%3D1%26hl%3Den%26suggon%3D0%26safe%3Doff%26sa%3DN")

---

### Post by perfectska04@hotmail.com on 2008-09-11
> **What is in a name? said:**
> EDIT: I'd just like to know the correct names of the icons that affect the following three areas:

- the Authorizations icon, under System > Administration on the GNOME menu;
- the Network icon, also under System > Administration;
- and the Autostarted Apps icon of Xfce's settings dialog.

Authorizations: gtk-dialog-authentication.svg
Network: preferences-system-network.svg
Autostarted Apps: No idea. I've been looking for this one myself, so if you do find out, let me know.

---

### Post by What is in a name? on 2008-09-11
> **perfectska04@hotmail.com said:**
> Authorizations: gtk-dialog-authentication.svg
Network: preferences-system-network.svg
Autostarted Apps: No idea. I've been looking for this one myself, so if you do find out, let me know.

Oh WOW, I'm so thankful!!!! Thanks a whole lot!!!!

EDIT: Eureka!!!

The name of Xfce's autostart editor's icon... After all, the answer was so simple that I'm almost ashamed:
**xfce4-autostart-editor**

---

### Post by indecisive on 2008-09-11
What do you all think of a desktop that is based on the Blender User Interface? Also, I was thinking about making the Desktop in 3D view and organizing the icons or even elements within windows by AI?

---

### Post by dbbolton on 2008-09-11
> **What is in a name? said:**
> Ah, those Greeks, Romans and Arabians sure left us a great heritage, didn't they?...
And now that I think of it, I think "eikon" is indeed pronounced the same way we do in Portuguese (the "ei" ditongue is said like a simple "i", like the sound from the words with "ee" in the English language; just like the Greek "ai" is pronounced like an "eh").

I also believe I haven't been sleeping enough. :s

Ah well. Enough of my ramblings.

**Eikon2, Release Candidate 1**: [http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html](http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html)

It's a premiere, hehe.

EDIT: I'd just like to know the correct names of the icons that affect the following three areas:

- the Authorizations icon, under System > Administration on the GNOME menu;
- the Network icon, also under System > Administration;
- and the Autostarted Apps icon of Xfce's settings dialog.

Thanks in advance, in case someone knows the answer.
Looks great. You might want to include .../status/user-trash-full.png or the trash applets in AWN revert to the ugly tango icon.

---

### Post by What is in a name? on 2008-09-11
> **dbbolton said:**
> Looks great. You might want to include .../status/user-trash-full.png or the trash applets in AWN revert to the ugly tango icon.

Thanks!
I already have an icon named user-trash-full.png in the theme. It is inside of the Places folder, though. Could that be the issue?

---

### Post by 71CH on 2008-09-11
Hey looks great.  I rearranged some of the icons to better suit my tastes.  Thanks a bunch for Eikon2.  :)

---

### Post by 71CH on 2008-09-11
BTW, any way to use these icons for Evolution?  The icons in Evolution stay the same...

---

### Post by What is in a name? on 2008-09-11
> **71CH said:**
> BTW, any way to use these icons for Evolution?  The icons in Evolution stay the same...

I'm still trying to take care of it. Since I essentially only use webmail, and especially because Evolution was always a pain whenever I wanted to create a new GTK theme, I did not make it one of my first priorities when I decided to give a new life to Eikon. But it should be addressed soon. Thanks for caring.

Meanwhile, you could try to observe other icon themes and try to reproduce the necessary symlinks and so on with your personal copy of Eikon. That's what I will do, anyway. It might be a bit time consuming, though, I tell you that. OxygenRefit2 includes a folder just with icons for Evolution. That should make it easier to observe and learn. I hope.

---

### Post by dbbolton on 2008-09-11
> **What is in a name? said:**
> Thanks!
I already have an icon named user-trash-full.png in the theme. It is inside of the Places folder, though. Could that be the issue?
I think so. The trash applet picks up the icon from Crashbit, which has all the "trash full" icons in the status folder (the places folder only has the "empty" icons).

---

### Post by Truedream on 2008-09-11
how can I change the icon for .lit (e-book) file types? It just shows up as blank :(

---

### Post by 71CH on 2008-09-11
> **Truedream said:**
> how can I change the icon for .lit (e-book) file types? It just shows up as blank :(

Can you even open .lit files?

---

### Post by Truedream on 2008-09-11
> **71CH said:**
> Can you even open .lit files?

yiph! MSreader under wine + custom action in Thunar. In nautilus just double click.

---

### Post by 71CH on 2008-09-11
sounds good.  I might have to try that.

---

### Post by Truedream on 2008-09-11
Just install [msreader]("http://www.microsoft.com/reader/downloads/pc.mspx") and  in case it closes as soon as it opens drop "*msvcirt.dll*" file in the directory.

---

### Post by Giant Speck on 2008-09-11
> **What is in a name? said:**
> Ah, those Greeks, Romans and Arabians sure left us a great heritage, didn't they?...
And now that I think of it, I think "eikon" is indeed pronounced the same way we do in Portuguese (the "ei" ditongue is said like a simple "i", like the sound from the words with "ee" in the English language; just like the Greek "ai" is pronounced like an "eh").

I also believe I haven't been sleeping enough. :s

Ah well. Enough of my ramblings.

**Eikon2, Release Candidate 1**: [http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html](http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html)

It's a premiere, hehe.

EDIT: I'd just like to know the correct names of the icons that affect the following three areas:

- the Authorizations icon, under System > Administration on the GNOME menu;
- the Network icon, also under System > Administration;
- and the Autostarted Apps icon of Xfce's settings dialog.

Thanks in advance, in case someone knows the answer.

Any chance you know how to use these in Kubuntu?  Because they way you've structured the files, it won't install under Control Center like many GNOME icon themes do.  I don't want to have to change the icon of each filetype individually!

---

### Post by dbbolton on 2008-09-11
> **Giant Speck said:**
> Any chance you know how to use these in Kubuntu?  Because they way you've structured the files, it won't install under Control Center like many GNOME icon themes do.  I don't want to have to change the icon of each filetype individually!
You could try the Breathless icon set for KDE. A lot of those icons are similar to Eikon.

---

### Post by Giant Speck on 2008-09-11
> **dbbolton said:**
> You could try the Breathless icon set for KDE. A lot of those icons are similar to Eikon.

A lot, but not all.  Especially for folders.  The folder icons in the Breathless set are absolutely ugly.  The way folder icons look is actually one of my top criteria when it comes to choosing an icon theme, and I love the way Eikon's folders look, in combination with all the other icons in the set.

---

### Post by mrgnash on 2008-09-11
[IMG]http://i35.tinypic.com/2lm8b5k.png[/IMG]

New window decoration; makes it look a little bit more authentic ;)

---

### Post by myusername on 2008-09-11
are you running chrome??

---

### Post by mrgnash on 2008-09-11
> **myusername said:**
> are you running chrome??

No, it's just Firefox dressed up like Chrome.

---

### Post by etnlIcarus on 2008-09-12
Newie:

[[IMG]http://img377.imageshack.us/img377/5672/screenshotlb4.th.jpg[/IMG]](http://img377.imageshack.us/my.php?image=screenshotlb4.jpg)

---

### Post by dbbolton on 2008-09-12
> **Giant Speck said:**
> A lot, but not all.  Especially for folders.  The folder icons in the Breathless set are absolutely ugly.  The way folder icons look is actually one of my top criteria when it comes to choosing an icon theme, and I love the way Eikon's folders look, in combination with all the other icons in the set.
It's easy enough to fix. Just switch Breathless/128x128/filesystems/folder.png with the icon you want before you run the buildscript.

---

### Post by Giant Speck on 2008-09-12
I think I've really done it this time.

I made some major improvements to my Kubuntu desktop.

I really wish I could figure out how to remove the drop-down menu button from the knewsticker applet, though.

I don't know why I've been on a World Trade Center screenshot fix lately, but I think this latest one is one of the best.

---

### Post by Islington on 2008-09-12
haven't posted in a while. Been working on a wallpaper or two, some icons and such... :)

---

### Post by myusername on 2008-09-12
that wallpaper looks nice. but i think it needs a slightly darker color and more of a gradient

---

### Post by PurposeOfReason on 2008-09-12
Not sure if anyone on these forums liked my emerald theme but here it is.

[http://gnome-look.org/content/show.php?content=89069](http://gnome-look.org/content/show.php?content=89069)

---

### Post by eightmillion on 2008-09-12
> **PurposeOfReason said:**
> Not sure if anyone on these forums liked my emerald theme but here it is.

[http://gnome-look.org/content/show.php?content=89069](http://gnome-look.org/content/show.php?content=89069)

It looks nice. I made a few modifications and threw this together.

---

### Post by ad_267 on 2008-09-12
> **Islington said:**
> haven't posted in a while. Been working on a wallpaper or two, some icons and such... :)

I love the wallpaper, can you upload it?

---

### Post by Nepherte on 2008-09-12
> **PurposeOfReason said:**
> Not sure if anyone on these forums liked my emerald theme but here it is.

[http://gnome-look.org/content/show.php?content=89069](http://gnome-look.org/content/show.php?content=89069)
It looks very good! I've always liked your desktops, very sober and simplistic. Just the way I want desktops to be.

---

### Post by What is in a name? on 2008-09-12
Oh my goodness, I've only been away like 8 hours to finally have some rest and there's already so much to do.

> **Giant Speck said:**
> Any chance you know how to use these in Kubuntu?  Because they way you've structured the files, it won't install under Control Center like many GNOME icon themes do.  I don't want to have to change the icon of each filetype individually!

Well, to be honest and to confess my own ignorance... **I didn't know you could use GNOME icon themes under KDE**. I mean, I knew some were theoretically installable, but you'd end up with many icons being reverted to the (ugly Crystal) default anyway. And since last time I checked it KDE3 didnt' respect some specifications of the OpenDesktop icon naming (correct me if I'm wrong), that just pushed me away from that desktop environment altogether, considering there isn't a single icon theme for KDE3 that I really enjoy (KDE4's Oxygen pleases me a lot, though, and that is a miracle for a default theme). That said, I'm going to check the structure of KDE icon themes, try out some symlinking and, well, from what I can see, change the icon of each filetype individually myself!

---

### Post by eightmillion on 2008-09-12
> **What is in a name? said:**
> 
Well, to be honest and to confess my own ignorance... **I didn't know you could use GNOME icon themes under KDE**. I mean, I knew some were theoretically installable, but you'd end up with many icons being reverted to the (ugly Crystal) default anyway. And since last time I checked it KDE3 didnt' respect some specifications of the OpenDesktop icon naming (correct me if I'm wrong), that just pushed me away from that desktop environment altogether, considering there isn't a single icon theme for KDE3 that I really enjoy (KDE4's Oxygen pleases me a lot, though, and that is a miracle for a default theme). That said, I'm going to check the structure of KDE icon themes, try out some symlinking and, well, from what I can see, change the icon of each filetype individually myself!

It's strange that the KDE 3 icon specification is different from the freedesktop.org specification since it was originally based on KDE. The good news is that the KDE 4 specification seems to be much closer. From my experimentation it appears that Gnome icon themes are pretty much directly installable in KDE 4. I've just been changing the inherits line in the index file to include Oxygen.

---

### Post by lzfy on 2008-09-12
Not much changed since last month :)

[[IMG]http://img128.imageshack.us/img128/728/shot5cf1.th.png[/IMG]](http://img128.imageshack.us/my.php?image=shot5cf1.png)

---

### Post by ddnev45 on 2008-09-12
> **What is in a name? said:**
> Ah, those Greeks, Romans and Arabians sure left us a great heritage, didn't they?...
And now that I think of it, I think "eikon" is indeed pronounced the same way we do in Portuguese (the "ei" ditongue is said like a simple "i", like the sound from the words with "ee" in the English language; just like the Greek "ai" is pronounced like an "eh").

I also believe I haven't been sleeping enough. :s

Ah well. Enough of my ramblings.

**Eikon2, Release Candidate 1**: [http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html](http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html)

It's a premiere, hehe.

EDIT: I'd just like to know the correct names of the icons that affect the following three areas:

- the Authorizations icon, under System > Administration on the GNOME menu;
- the Network icon, also under System > Administration;
- and the Autostarted Apps icon of Xfce's settings dialog.

Thanks in advance, in case someone knows the answer.

This is a really nice set of icons; couldn't wait to try them out so I converted a couple to use with XP at work (bottom of screenshot).

---

### Post by Mazza558 on 2008-09-12
> **What is in a name? said:**
> Ah, those Greeks, Romans and Arabians sure left us a great heritage, didn't they?...
And now that I think of it, I think "eikon" is indeed pronounced the same way we do in Portuguese (the "ei" ditongue is said like a simple "i", like the sound from the words with "ee" in the English language; just like the Greek "ai" is pronounced like an "eh").

I also believe I haven't been sleeping enough. :s

Ah well. Enough of my ramblings.

**Eikon2, Release Candidate 1**: [http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html](http://www.uploading.com/files/84PKH5T2/Eikon2-RC1.tar.gz.html)

It's a premiere, hehe.

EDIT: I'd just like to know the correct names of the icons that affect the following three areas:

- the Authorizations icon, under System > Administration on the GNOME menu;
- the Network icon, also under System > Administration;
- and the Autostarted Apps icon of Xfce's settings dialog.

Thanks in advance, in case someone knows the answer.

Could you upload somewhere else? That link isn't working for me. Perhaps filedropper?

---

### Post by What is in a name? on 2008-09-12
> **Mazza558 said:**
> Could you upload somewhere else? That link isn't working for me. Perhaps filedropper?

Filedropper crashes my browser (Firefox) no matter how many times I try. Like MediaFire has, recently. Do you have any other filehosting suggestion?

---

### Post by vishzilla on 2008-09-12
> **What is in a name? said:**
> Filedropper crashes my browser (Firefox) no matter how many times I try. Like MediaFire has, recently. Do you have any other filehosting suggestion?

[drop.io]("http://drop.io") has worked well for my documents atleast. try it. you can administer your own page with a lone-password (no registering) only

---

### Post by What is in a name? on 2008-09-12
> **vishzilla said:**
> [drop.io]("http://drop.io") has worked well for my documents atleast. try it. you can administer your own page with a lone-password (no registering) only

Currently, both the Flash-based uploaders at Drop.io and Filedropper freeze my whole browser (it's indifferent whether I use Flash 9 or 10RC). I'm trying out the HTML alternative at Drop.io. Let's see.

I'm exhausted.

EDIT: It worked. Thanks, vishzilla!
[http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)

---

### Post by Mazza558 on 2008-09-12
> **What is in a name? said:**
> Currently, both the Flash-based uploaders at Drop.io and Filedropper freeze my whole browser (it's indifferent whether I use Flash 9 or 10RC). I'm trying out the HTML alternative at Drop.io. Let's see.

I'm exhausted.

EDIT: It worked. Thanks, vishzilla!
[http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)

Yay! A working link!

---

### Post by Mazza558 on 2008-09-12
Ubuntu Dust + Eikon2 = WIN.

It's amazing how far Linux has come. :)

My Futurelooks theme pack is losing ground fast...

---

### Post by indecisive on 2008-09-12
Here's my screen shot as of now.
Icons:  Crashbit
Theme:  Ubuntu Dust
Wallpaper:  From the Incoming Desktop Submissions for Intrepid

---

### Post by el mariachi on 2008-09-12
> **indecisive said:**
> **Here's my screen shot as of now.**
Icons:  Crashbit
Theme:  Ubuntu Dust
Wallpaper:  From the Incoming Desktop Submissions for Intrepid
maybe not :p

---

### Post by indecisive on 2008-09-12
(Forgot attachment)

---

### Post by AlexR1 on 2008-09-12
> **indecisive said:**
> Here's my screen shot as of now.
Icons:  Crashbit
Theme:  Ubuntu Dust
Wallpaper:  From the Incoming Desktop Submissions for Intrepid

Where is your screenshot?
Is it shy, and hiding somewhere?

OK now I see it.

---

### Post by Giant Speck on 2008-09-12
Grr!  I really want the Eikon icons for my Kubuntu, but I can't find a way to convert the GNOME icon theme to a KDE icon theme.

---

### Post by Bart_D on 2008-09-12
What's the big deal about Eikon icons?

---

### Post by indecisive on 2008-09-12
Why do you use KDE (not starting a KDE vs. GNOME war, just out of academic curiosity)?

---

### Post by indecisive on 2008-09-12
In response to you signature, why should we?

---

### Post by I wanted to leave on 2008-09-12
My desktop to date
Wallpaper = Chicago_fair
Icons = Gion
Theme = Overglossed

Only thing I couldn't achieve is the transparent Gnome background

---

### Post by mrgnash on 2008-09-12
> **Bart_D said:**
> What's the big deal about Eikon icons?

Not sure. They look very OSX-ey to me.

---

### Post by What is in a name? on 2008-09-12
Back to Xfce, for now:

[[IMG]http://c.imagehost.org/t/0809/ecra.jpg[/IMG]](http://c.imagehost.org/view/0809/ecra.png) [[IMG]http://c.imagehost.org/t/0479/ecra2.jpg[/IMG]](http://c.imagehost.org/view/0479/ecra2.png)

Wallpaper: "The Bloch", from... somewhere on DeviantART or Customize.org, I guess;
GTK theme: a modified version of Ubuntu Dust;
Xfwm4 theme: Glow Dark
Icon theme: the not so special Eikon2 set;
Font: Calibri bold, size 8 (Liberation Sans bold, size 9, on Gedit).

---

### Post by Islington on 2008-09-12
> **myusername said:**
> that wallpaper looks nice. but i think it needs a slightly darker color and more of a gradient

Is this better? :confused: I have never been good with wallpapers.


To the person that wanted the wallpaper, I am attaching a messy svg. If you wish I can upload the actual sketch as well.


edit: damn svg is too big, where is a good place to up an svg?

---

### Post by dbbolton on 2008-09-12
> **Giant Speck said:**
> Grr!  I really want the Eikon icons for my Kubuntu, but I can't find a way to convert the GNOME icon theme to a KDE icon theme.
Again, it would be much easier to change a few icons in Breathless and re-run the buildscript. 

To convert it between a KDE icon theme, you would need to create an "index.desktop" file and do a whole lot of renaming.

---

### Post by Stan_1936 on 2008-09-12
Can the Eikon2 GNOME icons be used on Fluxbox/Openbox?

---

### Post by Megaton on 2008-09-12
Intrepid Ibex Alpha on my Acer Aspire One.
Theme is a modified Dust (borderless)
Font is Purisa

[[IMG]http://img388.imageshack.us/img388/6193/desktopxj4.th.png[/IMG]](http://img388.imageshack.us/my.php?image=desktopxj4.png)


[[IMG]http://img152.imageshack.us/img152/6808/screenshotbusyyz0.th.png[/IMG]](http://img152.imageshack.us/my.php?image=screenshotbusyyz0.png)

It is very basic because of the netbook's lower res. Unfortunately netbook-remix died after I upgraded to Ibex, so this was thrown together last minute.:(

---

### Post by dbbolton on 2008-09-12
> **Stan_1936 said:**
> Can the Eikon2 GNOME icons be used on Fluxbox/Openbox?
A "Gnome" icon theme should work with any GTK application.

---

### Post by indecisive on 2008-09-12
I think the Crashbit icon set is nicer than Eikon, as it is more clean and consistent.  Does anyone agree of differ upon reasonable grounds (if so, please explain why)?

---

### Post by Giant Speck on 2008-09-12
> **indecisive said:**
> I think the Crashbit icon set is nicer than Eikon, as it is more clean and consistent.  Does anyone agree of differ upon reasonable grounds (if so, please explain why)?

Why do you insist on collecting people's opinions?

Anyway, I've decided that I'm going to try to use the Breathless icon theme as a shell to create an Eikon theme for Kubuntu.  I've never done something this complicated before.  Fingers are crossed!

---

### Post by 71CH on 2008-09-12
> **What is in a name? said:**
> Back to Xfce, for now:

[[IMG]http://c.imagehost.org/t/0809/ecra.jpg[/IMG]](http://c.imagehost.org/view/0809/ecra.png) [[IMG]http://c.imagehost.org/t/0479/ecra2.jpg[/IMG]](http://c.imagehost.org/view/0479/ecra2.png)

Wallpaper: "The Bloch", from... somewhere on DeviantART or Customize.org, I guess;
GTK theme: a modified version of Ubuntu Dust;
Xfwm4 theme: Glow Dark
Icon theme: ***the not so special Eikon2 set***;
Font: Calibri bold, size 8 (Liberation Sans bold, size 9, on Gedit).

Hey man.  I like it. Don't listen to these other guys. I'm patiently waiting for the final release.  :)

---

### Post by Opeth115 on 2008-09-12
> **What is in a name? said:**
> Back to Xfce, for now:

[[IMG]http://c.imagehost.org/t/0809/ecra.jpg[/IMG]](http://c.imagehost.org/view/0809/ecra.png) [[IMG]http://c.imagehost.org/t/0479/ecra2.jpg[/IMG]](http://c.imagehost.org/view/0479/ecra2.png)

Wallpaper: "The Bloch", from... somewhere on DeviantART or Customize.org, I guess;
GTK theme: a modified version of Ubuntu Dust;
Xfwm4 theme: Glow Dark
Icon theme: the not so special Eikon2 set;
Font: Calibri bold, size 8 (Liberation Sans bold, size 9, on Gedit).

wow that is freaking nice looking man....  Would you send me that gtk?

---

### Post by Truedream on 2008-09-12
> **Truedream said:**
> how can I change the icon for .lit (e-book) file type? It just shows up as blank :(

anybody?

---

### Post by crimesaucer on 2008-09-12
[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-1.png[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8.png)

---

### Post by nelamvr6 on 2008-09-12
Here's mine:
[img]http://homepage.ct.metrocast.net/~nelamvr6//Screenshot.png[img width=560 height=360][/img]

Linux Mint Elyssa 5.0 Xfce CE

---

### Post by Giant Speck on 2008-09-12
I didn't think I'd make much progress this quickly.

It's far from complete, but at least it can be installed from the Control Center.

Introducing Eikon Beta 1 for KDE!

---

### Post by dbbolton on 2008-09-13
> **Giant Speck said:**
> 
Anyway, I've decided that I'm going to try to use the Breathless icon theme as a shell to create an Eikon theme for Kubuntu.

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/picard.jpg[/IMG]

---

### Post by Giant Speck on 2008-09-13
> **dbbolton said:**
> [IMG]http://i103.photobucket.com/albums/m128/envyouraudience/picard.jpg[/IMG]

What?  Pissed off that I didn't immediately give you credit or say thank you?  Well, thank you, dbbolton, for suggesting the idea.  It led me in the direction I needed to go.

It turns out it wouldn't have even worked in the first place, because the Breathless theme contains a lot more icons than the Eikon theme, so sorting out the correct icons would have taken forever.

However, I did find a "blank" buildset on KDE-Look.org that allowed me to port all of the icons from the Eikon theme over and enter values in the buildset file and .desktop file.

The Eikon theme now installs correctly using the Control Center.  The only task left is that I have to go through and rename all of the icons that have conflicting filenames so that it'll work fully in Kubuntu.

---

### Post by hanzomon4 on 2008-09-13
> **ayoli said:**
> Trying to make a murinna version of glow (ice). other details in the screenshot.
[URL="http://ayozone.org/gallery/screenshots-september-2008"]
[IMG]http://ayozone.org/wp-content/gallery/screenshots-september-2008/thumbs/thumbs_31082008.png[/IMG][/URL]

What is that chat app?

---

### Post by dbbolton on 2008-09-13
> **Giant Speck said:**
> What?  Pissed off that I didn't immediately give you credit or say thank you?

No, I'm actually relieved that you finally figured it out. I've just been spending too much time on the Debian forums. Not really used to telling people how to do something several times. Anyway, congratulations.

---

### Post by Giant Speck on 2008-09-13
> **dbbolton said:**
> No, I'm actually relieved that you finally figured it out. I've just been spending too much time on the Debian forums. Not really used to telling people how to do something several times. Anyway, congratulations.

Well, I figured if I was to get the icon theme to work, I was going to have to try to restructure it myself.  I'm sorry if I came off as rude in my last post.

I think I'm going to take my time on it, too, because I've never made an icon theme before, and it already seems difficult.  #-o

---

### Post by Killeroid on 2008-09-13
> **hanzomon4 said:**
> What is that chat app?
Thats the pidgin screenlet

---

### Post by Frantic_Earthling on 2008-09-13
Nothing fancy really. 
I am using the Echo icon theme.


[http://img399.imageshack.us/my.php?image=screenshotof5.png](http://img399.imageshack.us/my.php?image=screenshotof5.png)

---

### Post by vishzilla on 2008-09-13
> **Giant Speck said:**
> I didn't think I'd make much progress this quickly.

It's far from complete, but at least it can be installed from the Control Center.

Introducing Eikon Beta 1 for KDE!

Nice. Shouldn't you rename it to 'Keikon' to avoid ambiguity? ;)

---

### Post by lzfy on 2008-09-13
> **Giant Speck said:**
> I didn't think I'd make much progress this quickly.

It's far from complete, but at least it can be installed from the Control Center.

Introducing Eikon Beta 1 for KDE!

Great :) Can't wait to try it.

---

### Post by dualpretop on 2008-09-13
Kubuntu KDE4.1

[[IMG]http://img153.imageshack.us/img153/3554/111ee3.th.jpg[/IMG]](http://img153.imageshack.us/my.php?image=111ee3.jpg)

---

### Post by simtaalo on 2008-09-13
ubuntu studio controls
custom colours
AgingGorilla window borders
ubuntu studio icons

[IMG]http://i3.photobucket.com/albums/y63/simta/screenshot1.jpg[/IMG]

---

### Post by ChanServ on 2008-09-13
nice fresh install of ubuntu :)
[[img]http://www.postimage.org/aV1rrq6S.jpg[/img]](http://www.postimage.org/image.php?v=aV1rrq6S)

---

### Post by elmer_42 on 2008-09-13
At first I was going to ask why your username in that shot was ChanServ, and then I read your username. >.<

---

### Post by What is in a name? on 2008-09-13
> **Opeth115 said:**
> wow that is freaking nice looking man....  Would you send me that gtk?

Thanks... and sure!
Here's the theme:

---

### Post by What is in a name? on 2008-09-13
> **Truedream said:**
> anybody?

Sorry for taking so long to find an answer. There are other filetypes associated to Windows programs which are displayed with blank icons. For instance, the .veg files I generate with Sony Vegas 5 through Wine also have the same look. I tried to create a "application-x-ms-reader.png" icon, but somehow it didn't have any results (I downloaded some .lit file from the Web to make the test). Was I out of luck? You can try it on your side, perhaps I did something wrong (that or the ebook I downloaded was fake :s ).

---

### Post by urukrama on 2008-09-13
> **crimesaucer said:**
> [img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-1.png[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8.png)

It has been a long time since we've seen some of your desktops, crimesaucer! [COLOR="Gray"](Or did I just miss them all?)[/COLOR]

What font are you using in your Gtk theme?

---

### Post by dbbolton on 2008-09-13
> **ChanServ said:**
> nice fresh install of ubuntu :)
[[img]http://www.postimage.org/aV1rrq6S.jpg[/img]](http://www.postimage.org/image.php?v=aV1rrq6S)
So YOU'RE the guy who pm's me everytime I join #ubuntu.

---

### Post by indecisive on 2008-09-13
> **Giant Speck said:**
> Why do you insist on collecting people's opinions?

They can be interesting and educational.

---

### Post by billgoldberg on 2008-09-13
> **dualpretop said:**
> Kubuntu KDE4.1

[[IMG]http://img153.imageshack.us/img153/3554/111ee3.th.jpg[/IMG]](http://img153.imageshack.us/my.php?image=111ee3.jpg)

Ah so there he is, the sole kde 4.1 user.

lol

Kde 4.1 looks promising and good, but it's too buggy.

---

### Post by Bart_D on 2008-09-13
> **What is in a name? said:**
> Back to Xfce, for now:...
Icon theme: the not so special Eikon2 set...

Ha ha ha Mr. Eikon2 icon creator!   Ha ha ha.........

---

### Post by 71CH on 2008-09-13
> **What is in a name? said:**
> Thanks... and sure!
Here's the theme:

Do you have an emerald for this?

---

### Post by What is in a name? on 2008-09-13
> **71CH said:**
> Do you have an emerald for this?

Well, unfortunately no, I haven't. At the screenshots I was using Glow Dark Xfwm4. I never created an equivalent Emerald theme for it. I'm not sure if Ubuntu Dust is packaged with an Emerald theme. Probably it does and I just discarded it as soon as I extracted the tar.gz because I don't use Emerald. Let's see...

*goes to GNOME-Look.org*

The description of the theme doesn't mention Emerald, so... I'm sorry I can't help. For now, at least.

---

### Post by ChanServ on 2008-09-13
> **elmer_42 said:**
> At first I was going to ask why your username in that shot was ChanServ, and then I read your username. >.<

> **dbbolton said:**
> So YOU'RE the guy who pm's me everytime I join #ubuntu.

:razz:

---

### Post by boobuntu on 2008-09-13
> **ChanServ said:**
> :razz:

You should make pedobear your wallpaper.

---

### Post by JohnUK89 on 2008-09-13
Ubuntu Intrepid Alpha - can you tell I like purple? :)

(The white stripe at the bottom right is caused by different resolutions on screens, stupid Twinview :-\)

---

### Post by dbbolton on 2008-09-13
> **What is in a name? said:**
> Well, unfortunately no, I haven't. At the screenshots I was using Glow Dark Xfwm4. I never created an equivalent Emerald theme for it. I'm not sure if Ubuntu Dust is packaged with an Emerald theme. Probably it does and I just discarded it as soon as I extracted the tar.gz because I don't use Emerald. Let's see...

*goes to GNOME-Look.org*

The description of the theme doesn't mention Emerald, so... I'm sorry I can't help. For now, at least.
I quickly made an emerald theme that blends with the Aurora version of Dust. Not sure if it works with the others, but anyone is welcome to give it a go.

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/dustemerald.png[/IMG]

---

### Post by el mariachi on 2008-09-13
I really need to learn how to theme xfwm4 ...

---

### Post by jakupl on 2008-09-13
I usually like to keep things simple, but it really is fun playing with compiz once in a while. I love having my stuff white and clean/simple.

---

### Post by 71CH on 2008-09-13
> **dbbolton said:**
> I quickly made an emerald theme that blends with the Aurora version of Dust. Not sure if it works with the others, but anyone is welcome to give it a go.

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/dustemerald.png[/IMG]

Thanks!  It's not bad.

---

### Post by Perfex on 2008-09-13
[[IMG]http://img521.imageshack.us/img521/3923/screenshotxc9.th.png[/IMG]](http://img521.imageshack.us/my.php?image=screenshotxc9.png)

---

### Post by urukrama on 2008-09-13
> **el mariachi said:**
> I really need to learn how to theme xfwm4 ...

Just use Openbox :p

---

### Post by lackoblacko on 2008-09-13
Here is mine

---

### Post by el mariachi on 2008-09-13
> **urukrama said:**
> Just use Openbox :p
hehe I'm on a more "chic" phase right now and I need pixmaps and useless docks:lolflag:

---

### Post by Giant Speck on 2008-09-13
> **lzfy said:**
> Great :) Can't wait to try it.

Thanks!  It's going to be a while before it looks good enough to release.  There are a lot of things I have to rename and sort out.

> **vishzilla said:**
> Nice. Shouldn't you rename it to 'Keikon' to avoid ambiguity? ;)

I was thinking of naming it eiKon.  :p

Here is a current screenshot of the action:

---

### Post by urukrama on 2008-09-13
> **Truedream said:**
> anybody?

Perhaps [this thread]("http://ubuntuforums.org/showthread.php?t=916847") proves useful.

---

### Post by kk0sse54 on 2008-09-13
Deviating away from openbox this month and using KDE 4.1  in Slackware 12.1
[ATTACH]85137[/ATTACH]

---

### Post by crimesaucer on 2008-09-13
> **urukrama said:**
> It has been a long time since we've seen some of your desktops, crimesaucer! [COLOR="Gray"](Or did I just miss them all?)[/COLOR]

What font are you using in your Gtk theme?

I haven't posted any screenshots in a long time so I don't think you have missed any.


Here is a link to the font called eurofurence: [http://www.dafont.com/eurofurence.font](http://www.dafont.com/eurofurence.font)

---

### Post by Truedream on 2008-09-13
> **What is in a name? said:**
> Sorry for taking so long to find an answer. There are other filetypes associated to Windows programs which are displayed with blank icons. For instance, the .veg files I generate with Sony Vegas 5 through Wine also have the same look. I tried to create a "application-x-ms-reader.png" icon, but somehow it didn't have any results (I downloaded some .lit file from the Web to make the test). Was I out of luck? You can try it on your side, perhaps I did something wrong (that or the ebook I downloaded was fake :s ).

I believe its  msreader not ms-reader. maybe thats why?

> **urukrama said:**
> Perhaps [this thread]("http://ubuntuforums.org/showthread.php?t=916847") proves useful.

thx. I got it working. Just had to create a new mime type for msreader :)

---

### Post by PurposeOfReason on 2008-09-13
I had a habit of never covering conky so it became better to use a panel for space. The wallpaper was me bored after reading about hl2ep3.
[[img]http://xs331.xs.to/xs331/08376/screenshot836.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs331&d=08376&f=screenshot836.png)

---

### Post by voteforpedro36 on 2008-09-13
> **PurposeOfReason said:**
> I had a habit of never covering conky so it became better to use a panel for space. The wallpaper was me bored after reading about hl2ep3.
*snip*

That's really good. I liked it before too, but the text definitely makes it look better IMO. Here's mine, back to Openbox after going to Awesome, C-F, then Awesome again.

I'm using a *barely* modified version of Glow Lava (I changed one value to match the wall a little better) I believe, that was made by WiiaN? if I remember right.

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-13-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-13-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-13-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-13-08-media.png)

---

### Post by aschwerin.moses on 2008-09-14
I like to keep it simple...

---

### Post by vishzilla on 2008-09-14
GTK: Dust Aurora
Icons: Crashbit Ubuntu
AWN

[CENTER][[IMG]http://c.imagehost.org/t/0495/sept14.jpg[/IMG]](http://c.imagehost.org/view/0495/sept14.png) [[IMG]http://c.imagehost.org/t/0833/sept14_01.jpg[/IMG]](http://c.imagehost.org/view/0833/sept14_01.png)[/CENTER]

---

### Post by crimesaucer on 2008-09-14
[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-11-1.jpg[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-11.jpg](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-11.jpg)


[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10-1.png[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10.png)

---

### Post by skitzware on 2008-09-14
[[IMG]http://img261.imageshack.us/img261/4827/asnsshotyt3.th.png[/IMG]](http://img261.imageshack.us/my.php?image=asnsshotyt3.png)

Been working on a theme for fb

---

### Post by Barrucadu on 2008-09-14
> **vishzilla said:**
> GTK: Dust Aurora
Icons: Crashbit Ubuntu
AWN

What Emerald theme is that?

---

### Post by What is in a name? on 2008-09-14
> **vishzilla said:**
> GTK: Dust Aurora
Icons: Crashbit Ubuntu
AWN

[CENTER][[IMG]http://c.imagehost.org/t/0495/sept14.jpg[/IMG]](http://c.imagehost.org/view/0495/sept14.png) [[IMG]http://c.imagehost.org/t/0833/sept14_01.jpg[/IMG]](http://c.imagehost.org/view/0833/sept14_01.png)[/CENTER]

Where did you get that wallpaper from? Thanks in advance.

---

### Post by Zero Prime on 2008-09-14
GTK: BlackGarden 
[http://www.gnome-look.org/content/show.php/BlackGarden?content=89218&PHPSESSID=dba1f48369843f4a6bfc121e615634bd](http://www.gnome-look.org/content/show.php/BlackGarden?content=89218&PHPSESSID=dba1f48369843f4a6bfc121e615634bd)

Emerald: KOREMIN
[http://www.gnome-look.org/content/show.php/KOREMIN+Emerald+Compiz-Fusion+theme?content=65646](http://www.gnome-look.org/content/show.php/KOREMIN+Emerald+Compiz-Fusion+theme?content=65646)

Wallpaper: Linux Behind Curtain
[http://www.gnome-look.org/content/show.php/Linux+Behind+Curtain?content=89251](http://www.gnome-look.org/content/show.php/Linux+Behind+Curtain?content=89251)

[IMG]http://i34.photobucket.com/albums/d139/ZeroPrime/Screenshot-6.jpg[/IMG]

---

### Post by spiderbatdad on 2008-09-14
Intrepid. New-Human theme.

---

### Post by vishzilla on 2008-09-14
> **What is in a name? said:**
> Where did you get that wallpaper from? Thanks in advance.

from socwall i guess. you will have a hard time find the wall as it doesn't have a name. so i have attached it

---

### Post by vishzilla on 2008-09-14
> **Barrucadu said:**
> What Emerald theme is that?
That's a plain ol' Metacity that came with the Dust theme

---

### Post by Mazza558 on 2008-09-14
I didn't like the toolbars in Ubuntu Dust, so I started to mod it. It now looks like a cross between DUst and NewWave (without the gradient thingy).

I also turned the Futurelooks Emerald theme dark, with very nice results. I haven't done the window buttons yet, but it should look nice when I'm finished.

My mod, more than anything, shows how much space is wasted with nautilus's layout...

---

### Post by What is in a name? on 2008-09-14
> **Mazza558 said:**
> 
My mod, more than anything, shows how much space is wasted with nautilus's layout...

I guess that's one of the reasons I end up going back to Xfce every once in a while. Yes, I know I can use Thunar with GNOME, but since it's not easy or perhaps even possible to completely make GNOME use Thunar as its default file browser, using Xfce altogether becomes more practical.

Nautilus and the GNOME Panel can sometimes be a pain. How about that bug with the GNOME menu applet (the Applications/Places/System thingy) which prevents the panel to be sized down? Are there any indications that it will be solved anytime soon?

---

### Post by markp1989 on 2008-09-14
> **Zero Prime said:**
> GTK: BlackGarden 
[http://www.gnome-look.org/content/show.php/BlackGarden?content=89218&PHPSESSID=dba1f48369843f4a6bfc121e615634bd](http://www.gnome-look.org/content/show.php/BlackGarden?content=89218&PHPSESSID=dba1f48369843f4a6bfc121e615634bd)

Emerald: KOREMIN
[http://www.gnome-look.org/content/show.php/KOREMIN+Emerald+Compiz-Fusion+theme?content=65646](http://www.gnome-look.org/content/show.php/KOREMIN+Emerald+Compiz-Fusion+theme?content=65646)

Wallpaper: Linux Behind Curtain
[http://www.gnome-look.org/content/show.php/Linux+Behind+Curtain?content=89251](http://www.gnome-look.org/content/show.php/Linux+Behind+Curtain?content=89251)

[http://i34.photobucket.com/albums/d139/ZeroPrime/Screenshot-6.jpg](http://i34.photobucket.com/albums/d139/ZeroPrime/Screenshot-6.jpg)

thats a very nice gtk theme, has replaced slickness black on my desktop:



OS: hardy 64 bit
wm: Compiz fusion stand alone
GTK: BlackGarden 
icons: black white 2
emerald: something i made
wallpaper: none
dock: fbpanel 

apps: firefox, uxterm, pcmanfm, emesene 

any other info you want just ask

---

### Post by Opeth115 on 2008-09-14
> **voteforpedro36 said:**
> That's really good. I liked it before too, but the text definitely makes it look better IMO. Here's mine, back to Openbox after going to Awesome, C-F, then Awesome again.

I'm using a *barely* modified version of Glow Lava (I changed one value to match the wall a little better) I believe, that was made by WiiaN? if I remember right.

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-13-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-13-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-13-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-13-08-media.png)

Nice wall could you link it?

and thanks for the theme What is in a name? !

---

### Post by klange on 2008-09-14
I finally took some reasonably good pictures of my workspace, so I thought I'd share the panoramic I made, as well as a complete over view of my systems.
[[img]http://desk.oasis-games.com/th_desk.png[/img]](http://desk.oasis-games.com/desk.png)
(Warning: 5MB PNG)

Taken with flash and image stabilizer on a Canon PowerShot S5iS (all the power of an SLR, with the price tag of a compact) with all the lights on in my basement, only minutes before a brown out that killed my server one of my desktops, Compiz on my other desktop, and both my router and cable modem.

Stitched with Hugin, the actual stitch line is visible on the left set of drawers (right side).

Anyway, the pic itself shows my laptop, my two desktops (box farthest left and right), my server (second from left), and my two budget 22" LCDs (ViewSonic VA2226w, $250). My laptop has the same wallpaper as the LCD on the left.

Also pictured: Wacom Bamboo tablet, TI-nSpire CAS graphing calculator, Canon MP500 (I don't know what all the fuss is about Canon printers, I've never had problems with mine), and my rather cheap old DBL pro speakers (which are wired to both desktops).

**Desktop details**:
GTK theme is ClearGlow with a custom green. Icons are Tango. All three computers run Compiz (from git) with the same setup.

**System details**:
Laptop ("AcerLaptop") is an Acer Aspire 5610, US model, with an Intel Core Duo ("Centrino Duo"), 1.73GHz, 1GB RAM, 120GB HDD. Intel 945 graphics. Runs Intrepid. 12V DC input.

Desktop on the left ("OasisB") is a Pentium 4, 1.8GHz, 2GB DDR400 RAM, 40GB HDD. nVidia GeForce FX 5200, PCI. Runs Hardy.1. 500 watt PSU.

Desktop on the right ("OasisA") is an AMD Athlon XP 2000+, 1.6GHz, 512MB DDR RAM, 120GB HDD. ATI Radeon x800 AIW (which the inputs don't work on), AGP. Runs Hardy.1. 250 watt PSU.

Server ("Oasis-Games.com") is an AMD Athlon XP 1500+, 1.3GHz, 512MB DDR RAM, 40GB HDD. No graphics card (not even integrated). Runs Hardy.1, originally desktop, but with everything desktop-related stripped as of now. 500 watt PSU.

---

### Post by Hells_Dark on 2008-09-14
> **Mazza558 said:**
> 
My mod, more than anything, shows how much space is wasted with nautilus's layout...

Ho yes..

See my (clumsy) report : [http://bugzilla.gnome.org/show_bug.cgi?id=552093](http://bugzilla.gnome.org/show_bug.cgi?id=552093) ! :P

---

### Post by voteforpedro36 on 2008-09-14
> **Opeth115 said:**
> Nice wall could you link it?

and thanks for the theme What is in a name? !

Yeah sure, [here]("http://gangsterserver.com/?p=235") it is. It also comes in some other colors, you can look for yourself on that site.

---

### Post by eightmillion on 2008-09-14
Here's something I've been working on. I've attached the folder icon too, in case anyone wants to use it.

---

### Post by Mark76 on 2008-09-14
Groovy.

But what the second one supposed to be a folder for?

---

### Post by el mariachi on 2008-09-14
> **eightmillion said:**
> Here's something I've been working on. I've attached the folder icon too, in case anyone wants to use it.
kdock?

---

### Post by indecisive on 2008-09-14
Here is my desktop as of now, and I think it is my favorite so far.

Dust
Crashbit Ubuntu Icons
Wallpaper from Gnome-Look.org

---

### Post by indecisive on 2008-09-14
I forgot my screenshot again!

---

### Post by eightmillion on 2008-09-14
> **Mark76 said:**
> Groovy.

But what the second one supposed to be a folder for?

The folder is just something that I made. I put it there so that anyone that wants to use it can.

> **el mariachi said:**
> kdock?

It's cairo dock.

---

### Post by Giant Speck on 2008-09-14
> **indecisive said:**
> I forgot my screenshot again!

That's a color you don't see too often, and it looks great!

The theme would look a lot better with another font, though.

---

### Post by Stan_1936 on 2008-09-14
> **What is in a name? said:**
> Back to Xfce, for now:

[[IMG]http://c.imagehost.org/t/0809/ecra.jpg[/IMG]](http://c.imagehost.org/view/0809/ecra.png) [[IMG]http://c.imagehost.org/t/0479/ecra2.jpg[/IMG]](http://c.imagehost.org/view/0479/ecra2.png)

Wallpaper: "The Bloch", from... somewhere on DeviantART or Customize.org, I guess;
GTK theme: a modified version of Ubuntu Dust;
Xfwm4 theme: Glow Dark
Icon theme: the not so special Eikon2 set;
**Font: Calibri** bold, size 8 (Liberation Sans bold, size 9, on Gedit).

GREAT SCREENSHOT!!!  The GTK is amazing and so are the icons.

**Do you have a link to that Calibri font?  If you do, could you please post it?**

---

### Post by el mariachi on 2008-09-14
Calibri comes with Windows Vista/Office 2007/Powerpoint Viewer, it is thus proprietary

---

### Post by dbbolton on 2008-09-14
> **WindowsSucks said:**
> I finally took some reasonably good pictures of my workspace, so I thought I'd share the panoramic I made, as well as a complete over view of my systems.
[[img]http://desk.oasis-games.com/th_desk.png[/img]](http://desk.oasis-games.com/desk.png)
(Warning: 5MB PNG)

Taken with flash and image stabilizer on a Canon PowerShot S5iS (all the power of an SLR, with the price tag of a compact) with all the lights on in my basement, only minutes before a brown out that killed my server one of my desktops, Compiz on my other desktop, and both my router and cable modem.

Stitched with Hugin, the actual stitch line is visible on the left set of drawers (right side).

Anyway, the pic itself shows my laptop, my two desktops (box farthest left and right), my server (second from left), and my two budget 22" LCDs (ViewSonic VA2226w, $250). My laptop has the same wallpaper as the LCD on the left.

Also pictured: Wacom Bamboo tablet, TI-nSpire CAS graphing calculator, Canon MP500 (I don't know what all the fuss is about Canon printers, I've never had problems with mine), and my rather cheap old DBL pro speakers (which are wired to both desktops).

**Desktop details**:
GTK theme is ClearGlow with a custom green. Icons are Tango. All three computers run Compiz (from git) with the same setup.

**System details**:
Laptop ("AcerLaptop") is an Acer Aspire 5610, US model, with an Intel Core Duo ("Centrino Duo"), 1.73GHz, 1GB RAM, 120GB HDD. Intel 945 graphics. Runs Intrepid. 12V DC input.

Desktop on the left ("OasisB") is a Pentium 4, 1.8GHz, 2GB DDR400 RAM, 40GB HDD. nVidia GeForce FX 5200, PCI. Runs Hardy.1. 500 watt PSU.

Desktop on the right ("OasisA") is an AMD Athlon XP 2000+, 1.6GHz, 512MB DDR RAM, 120GB HDD. ATI Radeon x800 AIW (which the inputs don't work on), AGP. Runs Hardy.1. 250 watt PSU.

Server ("Oasis-Games.com") is an AMD Athlon XP 1500+, 1.3GHz, 512MB DDR RAM, 40GB HDD. No graphics card (not even integrated). Runs Hardy.1, originally desktop, but with everything desktop-related stripped as of now. 500 watt PSU.
Maybe just me, but the pics aren't showing up.

Also, I thought you might find this thread of interest: [http://ubuntuforums.org/showthread.php?t=914437](http://ubuntuforums.org/showthread.php?t=914437)

---

### Post by meborc on 2008-09-14
elive 1.8.8 development

i have no idea what the theme is :) i guess it is elive default... i have not changed anything except added some applications to the panel

running like lightning :guitar:

---

### Post by Stan_1936 on 2008-09-14
> **el mariachi said:**
> Calibri comes with Windows Vista/Office 2007/Powerpoint Viewer, it is thus proprietary

I guess I'm out of luck with the font then.  Thanks for the quick reply.

---

### Post by voteforpedro36 on 2008-09-14
> **Stan_1936 said:**
> I guess I'm out of luck with the font then.  Thanks for the quick reply.

You can install it, it just isn't quite legal. I'm sure Google can help you there.

Changed a couple small things, shot coming when it uploads.

---

### Post by bsell on 2008-09-14
Here's my current desktop. Best of all worlds.

---

### Post by voteforpedro36 on 2008-09-14
[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-14-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-14-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-14-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-14-08-media.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-14-08-web.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-14-08-web.png)

*points for people who notice the difference*

I hate editing in when there is a post below my old one. BTW bsell, that is Windows, right? Else how did you get Paint.NET in Linux?

---

### Post by Giant Speck on 2008-09-14
> **bsell said:**
> Here's my current desktop. Best of all worlds.

Is that the Zune theme for XP?

---

### Post by bsell on 2008-09-14
> **Giant Speck said:**
> Is that the Zune theme for XP?

Yes

---

### Post by Bart_D on 2008-09-14
> **voteforpedro36 said:**
> [[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-14-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-14-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-14-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-14-08-media.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-14-08-web.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-14-08-web.png)

***points for people who notice the difference***

I hate editing in when there is a post below my old one. BTW bsell, that is Windows, right? Else how did you get Paint.NET in Linux?
**You changed the OpenBox theme(?).**

---

### Post by Giant Speck on 2008-09-14
> **bsell said:**
> Yes

Well, it looks awesome.

---

### Post by Nythain on 2008-09-15
> **markp1989 said:**
> thats a very nice gtk theme, has replaced slickness black on my desktop:



OS: hardy 64 bit
wm: Compiz fusion stand alone
GTK: BlackGarden 
icons: black white 2
emerald: something i made
wallpaper: none
dock: fbpanel 

apps: firefox, uxterm, pcmanfm, emesene 

any other info you want just ask
that is the hotness... if only you designed fluxbox themes instead of emerald :P good work

---

### Post by ODF on 2008-09-15
Still need to work a lot on the conky

---

### Post by broken tibula on 2008-09-15
Got mine!  Yay!  Darkish...  Um.  I like it.

---

### Post by skitzware on 2008-09-15
[[IMG]http://img392.imageshack.us/img392/8712/sshotkr3.th.png[/IMG]](http://img392.imageshack.us/my.php?image=sshotkr3.png)

The fluxbox theme is ready for testing if anyone is interested

---

### Post by BOBSONATOR on 2008-09-15
I still love murrina glow colors!

What is in a Name?, the new icons look fantastic!

---

### Post by ddnev45 on 2008-09-15
Had to do a re-install on the laptop and went with Debian Lenny this time.
Fvwm w/ trayer.

---

### Post by billgoldberg on 2008-09-15
> **bsell said:**
> Here's my current desktop. Best of all worlds.

Link to wallpaper?

---

### Post by markp1989 on 2008-09-15
> **Nythain said:**
> that is the hotness... if only you designed fluxbox themes instead of emerald :P good work

Thankyou, I dont use fluxbox , but i do use openbox on my laptops, so i may make one for openbox when i have time, nd learn how to

---

### Post by klange on 2008-09-15
> **dbbolton said:**
> Maybe just me, but the pics aren't showing up.

Also, I thought you might find this thread of interest: [http://ubuntuforums.org/showthread.php?t=914437](http://ubuntuforums.org/showthread.php?t=914437)
Power's been out here for over 12 hours. I just noticed that thread and will probably repost later today.

---

### Post by Stolie on 2008-09-15
Here's mine.. Not a whole lot going on, standard default Emerald theme, compiz-fusion for some minor effects.. The desktop is one devoted to the great Doctor Steel, our future World Emperor.

[IMG]http://i24.photobucket.com/albums/c1/stolieman/September2008.png[/IMG]

---

### Post by What is in a name? on 2008-09-15
> **Stan_1936 said:**
> I guess I'm out of luck with the font then.  Thanks for the quick reply.

You can always check your PM's.

---

### Post by AptlyNamed on 2008-09-15
[[IMG]http://img392.imageshack.us/img392/3720/screenshotgb3.th.png[/IMG]](http://img392.imageshack.us/my.php?image=screenshotgb3.png)

What you see:

Desktop-environment: XFCE
GTK2+ theme: modified Clearlooks-Lemon-Graphite
Emerald theme: Gommoso
Iconset: mist (from package 'gnome-themes')
Background: [[COLOR="Blue"]link[/COLOR]]("http://epheus.deviantart.com/art/Leafie-PRO-79868546")
BMPx media player (great for last.fm)

---

### Post by etnlIcarus on 2008-09-15
Slightly OT but just reading Phoronix's breakdown of the current changes in Xfce 4.6-alpha, I'm pissed; Xfwm4 can now be resized from the top window border.

It drives me up the wall when all I want to do is move a window without worrying if my cursor is 1px too close to the top edge of the window border.

Hopefully the changes don't make xfwm as clumsy as compiz; if your cursor is hovering over the resize area of the top border, scrollwheel initiated window shading is disabled.

---

### Post by liyanricaoqiyue1314 on 2008-09-15
[size=2]Nude-calendar 1177, human and Shouzu the third "Battle of Lawson," Lawson barriers on the ground before the start of the Gap. [Runescape Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)This is a historic campaign, the campaign is "human beast seven years of war" in the first three major campaigns, the history of bare-called "people's car used to launch the war." [Runescape Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php)Because, the bare-three million migrant workers has made in a month-20,000 warships, and timely expansion to the navy,[Runescape Powerleveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) so that mankind has made the absolute superiority in the sea, with both sides of the back to. And the barren Shouzufengru the mainland until the 37th of the people of God the outbreak of war. [runescape shop](http://www.runescape-shop.com/)And it is precisely because of this campaign, the first time in the bare-war history, referred to the "Portland Ruo-yun," the name, many historians experts to the expansion of the war of special significance. Some people even said that, if not the war, as there will be a great hero was inspired by, of course, will be impossible for a human return to the mainland seven glorious history. [age of conan power leveling](http://www.aoc-power-leveling.org)Moreover, we said to this great man, in this war also made a bit of good results? [Runescape Gold Farm](http://www.runescape-shop.com/runescape-gold-farm/runescape-gold-farm.php)Portland Ruo-yun from Lawson on the Fort Fangyanwangqu, with both sides of the narrow ground to beat the Shouzu row over the army. [aoc power leveling](http://www.aoc-power-leveling.org)A tall face of ferocious ethnic people Zhengning the claws, but the body is more moderate and flexible people who foot, body, wrapped in a layer of black scales in the long tentacles of the Long Tuzhuo ethnic people. Of course, the master control of the air wing wizard and although their number less, but also with the team in the final, when prone radio ready siege of human soldiers guarding the wall. [/size][size=2][buy age of conan power leveling](http://www.aoc-power-leveling.org)Mankind's troops began to open Lawson barriers, 200,000 of the green collar Tieqi, hidden in two wings of the Tieqi second only to God bow of the 50,000 camp bow riders, and are in the final of the 300,000 Yazhen infantry. [buy aoc power leveling](http://www.aoc-power-leveling.org)Interval between the two sides about two kilometers distance from each other to see the other side of the bright banner of omnipresent there shaking. Ma Si Ming and the anger of the arms occasionally break out the [Runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)sound of the collision, but the two sides is almost non-soldiers heard voices, the silence before the war that is reinforced by the kind of Qishixiongxiong Fengyuyulai. [Runescape Mini Game](http://www.runescape-shop.com/rs-mini-game/runescape-mini-game.php)The weather has also Laicourenao this time, to beat the dark clouds gradually from the [Rs Power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) floating over the horizon, live coverage of the original is also clear skies, Yuan Yidian gradually so that the soldiers almost clear of each other's faces, the temperature suddenly dropped. So many people and irritable, even more tense over the past fainted. [Rs Gold](http://www.runescape-shop.com/runescape-gold/runescape-gold.php)Line-up finish. Last night talk election effort a silvery white armor, general Pigua&#24471;&#19981;skin to stay one point, struggling carrying a spear, at the moment Lawson body trembling from the Fort-Ruo-yun, although aware that this time only The first student, is not played with, but on the battlefield or Sheyu powerful Shaqi, the lack of tension in the Tuiruan body. [/size]

---

### Post by AptlyNamed on 2008-09-15
> **etnlIcarus said:**
> Slightly OT but just reading Phoronix's breakdown of the current changes in Xfce 4.6-alpha, I'm pissed; Xfwm4 can now be resized from the top window border.

It drives me up the wall when all I want to do is move a window without worrying if my cursor is 1px too close to the top edge of the window border.

Hopefully the changes don't make xfwm as clumsy as compiz; if your cursor is hovering over the resize area of the top border, scrollwheel initiated window shading is disabled.

I never noticed that but it seems like no Linux windowmanager gets these things right. Just like with the lack of Fitt's law support in Compiz, i.e. when you maximize Firefox and fling the mouse to the right end of the screen and want to drag the scrollbar you can't because right-most column of pixels doesn't respond to clicks.

---

### Post by meborc on 2008-09-15
> **etnlIcarus said:**
> Slightly OT but just reading Phoronix's breakdown of the current changes in Xfce 4.6-alpha, I'm pissed; Xfwm4 can now be resized from the top window border.

It drives me up the wall when all I want to do is move a window without worrying if my cursor is 1px too close to the top edge of the window border.

Hopefully the changes don't make xfwm as clumsy as compiz; if your cursor is hovering over the resize area of the top border, scrollwheel initiated window shading is disabled.

i have long given up on moving windows from the title... i always use the alt+left-click+drag combo... faster, safer, cleaner... and alt+middle-click+drag to resize

---

### Post by etnlIcarus on 2008-09-15
I've got alt-middle-click set to drop the window to the bottom of the stack and alt-right-click to resize but that doesn't help when I'm feeling like a lazy c**t (which is most of the time) and just want to lay back in my chair and only use the mouse.

---

### Post by DJ_Peng on 2008-09-15
> **bsell said:**
> Here's my current desktop. Best of all worlds.
KILLER wallpaper! Would you mind sharing it?

> **broken tibula said:**
> Got mine!  Yay!  Darkish...  Um.  I like it.
Love that wallpaper! May I get a link pls?

My schedule is about to stop being so crazy so I hope to have my desktop pic up by the end of the week.

---

### Post by Bart_D on 2008-09-15
> **BOBSONATOR said:**
> I still love murrina glow colors!

What is in a Name?, the new icons look fantastic!

What font size(mainly for the panel at the bottom of the screen) are you using in that screenshot?

---

### Post by rjmdomingo2003 on 2008-09-15
New Openbox mess, conky (lower left-hand), x'mission (upper left-hand), tint, GTK - Glow Cinder...

---

### Post by overdrank on 2008-09-15
Intrepid

---

### Post by What is in a name? on 2008-09-15
> **rjmdomingo2003 said:**
> New Openbox mess, conky (lower left-hand), x'mission (upper right-hand), tint, GTK - Glow Cinder...

That's a very creative wallpaper. I like it!

---

### Post by a0peter on 2008-09-15
> **rjmdomingo2003 said:**
> New Openbox mess, conky (lower left-hand), x'mission (upper right-hand), tint, GTK - Glow Cinder...

Is that pypanel? Would mind sharing your config if it is?

---

### Post by BlackLLama on 2008-09-15
what do poeple think of the desktop i just made, using GIMP:guitar:

---

### Post by voteforpedro36 on 2008-09-15
> **Bart_D said:**
> **You changed the OpenBox theme(?).**


Nope, lol.

---

### Post by mp3_freak_721 on 2008-09-15
> **twntyonejay said:**
> My settings for September

Can I get that wallpaper in your screenshot?

---

### Post by BOBSONATOR on 2008-09-15
> **Bart_D said:**
> What font size(mainly for the panel at the bottom of the screen) are you using in that screenshot?

Calibri Bold, Size 8.4, im on 1680x1050 on a 15.4 inch screen

---

### Post by bsell on 2008-09-15
> **DJ_Peng said:**
> KILLER wallpaper! Would you mind sharing it?


Love that wallpaper! May I get a link pls?

My schedule is about to stop being so crazy so I hope to have my desktop pic up by the end of the week.

[MacBuntu wallpapers]("http://picasaweb.google.com/samzaphu/LeopardAndHardyHeron#")

I think the Hardy Heron was done in Illustrator. The wallpaper I'm using in the screenshot is clearly a Photoshop creation.

---

### Post by banewman on 2008-09-15
Found an old wallpaper and made a new fluxbox theme for it.

---

### Post by Hund on 2008-09-15
[[img]http://tn3-2.deviantart.com/fs36/300W/f/2008/259/3/e/3e655d771094c3fcc294efae524cced2.png[/img]](http://ebupof.deviantart.com/art/My-Desktop-080915-98048556)

Info in the screenshot.

---

### Post by graphic23 on 2008-09-15
8.04
Dust (Sept. 14th Version)
Eikon 2 (from this thread)

---

### Post by Islington on 2008-09-15
> **What is in a name? said:**
> You can always check your PM's.

actually one can do this to get the microsoft fonts:

Firstly, download the [microsoft office compatibility pack]("http://www.microsoft.com/downloads/details.aspx?FamilyId=941B3470-3AE9-4AEE-8F43-C6BB74CD1466&displaylang=en"), and install cabextract from your distribution's package managers.

Now, create a new directory, or do this in /tmp, because it's going to tar bomb on you. You have been warned.

$ cabextract FileFormatConverters.exe
$ cabextract O12Conv.cab

Now that you have an ungodly mess of files everywhere, use find to install them:

$ mkdir -p ~/.fonts
$ find . \( -iname "*.ttf" -or -iname "*.ttc" \) -exec cp \{\} ~/.fonts \;
$ fc-cache

[URL="http://www.reddit.com/r/linux/comments/71j7j/ask_linux_what_are_your_favourite/c05fxfc"]
(source)[/URL]

---

### Post by p_quarles on 2008-09-15
My most recent setup.

---

### Post by BOBSONATOR on 2008-09-16
Still going murrinaGlow & Eikon crazy!,

wallpaper by ether @ deviantart :)

---

### Post by rjmdomingo2003 on 2008-09-16
> **What is in a name? said:**
> That's a very creative wallpaper. I like it!
Got it from deviantart :KS

---

### Post by rjmdomingo2003 on 2008-09-16
> **a0peter said:**
> Is that pypanel? Would mind sharing your config if it is?
Sorry but that isn't pypanel, that is tint (task manager).

---

### Post by Mark76 on 2008-09-16
> **BOBSONATOR said:**
> Still going murrinaGlow & Eikon crazy!,

wallpaper by ether @ deviantart :)
What's shayan file browser?

---

### Post by BOBSONATOR on 2008-09-16
> **Mark76 said:**
> What's shayan file browser?

Shayan is my name lol.

The filebrowser is just nautilus. :)

---

### Post by aschwerin.moses on 2008-09-16
Well, you did not ask me.. anyways,here you go

---

### Post by Möller on 2008-09-16
Openbox, bmpanel. Some Deviantart-wallpaper I think, can't remember.

---

### Post by aschwerin.moses on 2008-09-16
well, even you did not ask.. anyways.. this is for the others who like the wallpaper

[http://n4u2k.deviantart.com/art/Earth-64857484](http://n4u2k.deviantart.com/art/Earth-64857484)

---

### Post by ayoli on 2008-09-16
infos in the screenshot.
[[IMG]http://ayozone.org/wp-content/gallery/screenshots-september-2008/thumbs/thumbs_16092008.png[/IMG]]("http://ayozone.org/gallery/screenshots-september-2008")

---

### Post by etnlIcarus on 2008-09-16
> **Möller said:**
> Openbox, bmpanel. Some Deviantart-wallpaper I think, can't remember.
You don't actually have the wallpaper; only it's preview. Download the .zip and get the full-size, tag-free version.

---

### Post by billgoldberg on 2008-09-16
My laptop

[[IMG]http://www.ourdesktops.com/desktops/thumb_large/734cfa3b-2202-4d33-876f-3fb899dbbcca_thumblarge.jpg[/IMG]]("http://www.ourdesktops.com/desktops/734cfa3b-2202-4d33-876f-3fb899dbbcca.jpg")

---

### Post by clipse on 2008-09-16
Here is mine.

---

### Post by el mariachi on 2008-09-16
murrine-svn stopped working for me :( all murrine themes aren't working :(:(

---

### Post by Bart_D on 2008-09-16
> **clipse said:**
> Here is mine.

```
home@home
```

That's a terrible username, especially for a beginner.  It utterly butchered me......

---

### Post by Stan_1936 on 2008-09-16
> **clipse said:**
> Here is mine.

That is a great desktop you've got.  I have two questions:

Q1.  Could you please post your conkyrc setup?

Q2.  Also, could you please explain how you got your terminal embedded in the wallpaper?

---

### Post by perfectska04@hotmail.com on 2008-09-16
> **el mariachi said:**
> murrine-svn stopped working for me :( all murrine themes aren't working :(:(

The latest revision of murrine-svn renamed the setting "style" to "profile", so pretty much every theme that has a "style =" won't work anymore.

---

### Post by etnlIcarus on 2008-09-16
Got bored and decided to install KDE 4.1

[[IMG]http://img156.imageshack.us/img156/4209/screenshoted4.th.jpg[/IMG]](http://img156.imageshack.us/my.php?image=screenshoted4.jpg)

As much as I love K's new direction, *jesus f**king christ*, this is unstable. It makes Compiz looks like a mature product. Also, coming from Xfce; no amount of eye-candy can mask how much slower and less responsive things are (possibly in-part because of the eye-candy).

Anyway, since I've already had two X crashes and I appear to be missing a daemon since my display settings are forgotten between sessions, I don't think KDE4 is going to be anymore than a passing curiosity at this time.

---

### Post by What is in a name? on 2008-09-16
> **perfectska04@hotmail.com said:**
> The latest revision of murrine-svn renamed the setting "style" to "profile", so pretty much every theme that has a "style =" won't work anymore.

[B]Oh.
My.
doG.[/B]

*WIIAN avoids going to GNOME-Look.org in order to have some more time to get prepared for the avalanche of negative comments, bomb threats and flying knives*

---

### Post by a0peter on 2008-09-16
Here is one of my desktops:
[IMG]http://farm4.static.flickr.com/3004/2863019118_5444b7d6b1_d.jpg[/IMG]

OS: Crunchbang Linux
GTK: Nova-Arch
Openbox: Arch-Blue
Icons: Tango
Wallpaper: [Rainbowfest]("http://manicho.deviantart.com/art/Rainbowfest-wall-67367936")
Apps: Quod Libet, Lxterminal, Gmrun, Pypanel.

---

### Post by Daisuke_Aramaki on 2008-09-16
OS - Ubuntu Hardy Heron
Desktop - KDE 3.5.10
Style - Domino-Light Grey
WinDec - Domino
Icons - Reflections B&W
WP - Spotlight
App. Font - Liberation Sans 9
Terminal Font - Lucida Console 7
[CENTER]
[[IMG]http://img217.imageshack.us/img217/9439/snapshot3ig2.th.png[/IMG]](http://img217.imageshack.us/my.php?image=snapshot3ig2.png)[/CENTER]

---

### Post by perfectska04@hotmail.com on 2008-09-16
> **What is in a name? said:**
> [B]Oh.
My.
doG.[/B]

*WIIAN avoids going to GNOME-Look.org in order to have some more time to get prepared for the avalanche of negative comments, bomb threats and flying knifes*

Hahaha, yeah, pretty much. You can always use hilight and gradient ratios instead of the styles/profiles. That way you won't have to make two versions of your themes (one for pre rev. 66, and one for post rev. 66). I think that even intrepid's "newhuman" and "human-murrine" are useless after the new revision.

---

### Post by boobuntu on 2008-09-16
> **a0peter said:**
> Here is one of my desktops:

OS: Crunchbang Linux
GTK: Nova-Arch
Openbox: Arch-Blue
Icons: Tango
Wallpaper: [Rainbowfest]("http://manicho.deviantart.com/art/Rainbowfest-wall-67367936")
Apps: Quod Libet, Lxterminal, Gmrun, Pypanel.

I'm loving that wallpaper!

---

### Post by chucky chuckaluck on 2008-09-16
openbox, clearlooks-olive gtk, elegant-brit ob, quodlibet, pypanel, xterm. i made the wallpaper from a photograph using the colors of the gtk theme.

[[IMG]http://c.imagehost.org/t/0149/ec-ol-scr.jpg[/IMG]](http://c.imagehost.org/view/0149/ec-ol-scr.jpg)

---

### Post by indecisive on 2008-09-16
> **What is in a name? said:**
> *WIIAN avoids going to GNOME-Look.org in order to have some more time to get prepared for the avalanche of negative comments, bomb threats and flying knives*
Pardon me?

---

### Post by PurposeOfReason on 2008-09-16
> **indecisive said:**
> Pardon me?
The new murrina breaks his theme and people will think its his fault.

---

### Post by clipse on 2008-09-16
> **Bart_D said:**
> ```
home@home
```

That's a terrible username, especially for a beginner.  It utterly butchered me......

Yeah, I know. It was when I first started in Ubuntu......and Linux for that matter. I have scewed that OS beyond belief with all my experimentation. I think I finally have a good idea on how I want to it too look and what I want it to do. Now I'm going to wipe that partition clean, start over and make things the way I want and leave it......for awhile anyway. :D One of the things I'm going to change is the username. ;)

> **Stan_1936 said:**
> That is a great desktop you've got.  I have two questions:

Q1.  Could you please post your conkyrc setup?

Q2.  Also, could you please explain how you got your terminal embedded in the wallpaper?


I just copied a conkyrc in the thread "Show your Conkyrc files" or something like that. It was a newer one (couple weeks old maybe) Right now I'm in my XP partition so I can't get it my .conkyrc file. 

AS for the embedded terminal, I followed the instruction found [here. ]("http://ubuntuforums.org/showthread.php?t=202249&highlight=terminal+desktop")

---

### Post by eightmillion on 2008-09-16
> **Daisuke_Aramaki said:**
> OS - Ubuntu Hardy Heron
Desktop - KDE 3.5.10
Style - Domino-Light Grey
WinDec - Domino
Icons - Reflections B&W
WP - Spotlight
App. Font - Liberation Sans 9
Terminal Font - Lucida Console 7
[CENTER]
[[IMG]http://img217.imageshack.us/img217/9439/snapshot3ig2.th.png[/IMG]](http://img217.imageshack.us/my.php?image=snapshot3ig2.png)[/CENTER]

I love that wallpaper. Mind sharing it?

---

### Post by indecisive on 2008-09-16
> **WindowsSucks said:**
> Power's been out here for over 12 hours.
Same

---

### Post by indecisive on 2008-09-16
> **Giant Speck said:**
> That's a color you don't see too often, and it looks great!

The theme would look a lot better with another font, though.

How's this?

---

### Post by eightmillion on 2008-09-16
> **indecisive said:**
> How's this?

That's nice. What font is that?

---

### Post by etnlIcarus on 2008-09-16
> **Daisuke_Aramaki said:**
> OS - Ubuntu Hardy Heron
Desktop - KDE 3.5.10
Style - Domino-Light Grey
WinDec - Domino
Icons - Reflections B&W
WP - Spotlight
App. Font - Liberation Sans 9
Terminal Font - Lucida Console 7
[CENTER]
[[IMG]http://img217.imageshack.us/img217/9439/snapshot3ig2.th.png[/IMG]](http://img217.imageshack.us/my.php?image=snapshot3ig2.png)[/CENTER]

This is the least K-looking KDE desktop I've ever seen. Extremely well done.

---

### Post by dlm4849 on 2008-09-17
> **eightmillion said:**
> That's nice. What font is that?

Thats Avant Garde

---

### Post by Giant Speck on 2008-09-17
> **indecisive said:**
> How's this?

That is much, much better!

It pains me to see someone post a really nice screenshot showing they worked to make their desktop look nice, only to be disappointed to find that they are still using the default font.

Ubuntu's default font is ugly.  It just.... is.

---

### Post by markp1989 on 2008-09-17
few changes to the colour since last time 

OS: hardy 64 bit
wm: Compiz fusion stand alone
GTK: industrial with colour change 
icons: black white 2
emerald: something i made, dont need a maximize or minimize button, if i want to maximize i just double click the title bar, and to minimize i just use the dock 
wallpaper: file is called 01638_darkknight_2880x900.jpg not sure were i got it from 
dock: fbpanel 

apps: firefox, uxterm, pcmanfm, emesene , conky, feh 


any other info you want just ask


What you all think?


onky problem i have is that i cannot read text in emesene if they other person has black text, which is about 80% of them. any way i can override my contacts font colour?

---

### Post by t_k on 2008-09-17
[[img]http://bildr.no/thumb/256150.jpeg[/img]](http://bildr.no/view/256150)

---

### Post by skitzware on 2008-09-17
[[IMG]http://img247.imageshack.us/img247/9607/sshotki7.th.png[/IMG]](http://img247.imageshack.us/my.php?image=sshotki7.png)

The future Mrs Skitzware....


hehe... I wished...

---

### Post by Daisuke_Aramaki on 2008-09-17
> **eightmillion said:**
> I love that wallpaper. Mind sharing it?

Here's the link for the wall mate!

[http://smert1012.deviantart.com/art/Spotlight-WallPack-98100957]("http://smert1012.deviantart.com/art/Spotlight-WallPack-98100957")

---

### Post by Daisuke_Aramaki on 2008-09-17
> **etnlIcarus said:**
> This is the least K-looking KDE desktop I've ever seen. Extremely well done.

thanx! it was inspired by linuxfever's reflektions iconset at kde-look.

---

### Post by eightmillion on 2008-09-17
> **skitzware said:**
> [[IMG]http://img247.imageshack.us/img247/9607/sshotki7.th.png[/IMG]](http://img247.imageshack.us/my.php?image=sshotki7.png)

I was listening to that exact song when I saw your screenshot. I love Bon Iver.
> **Daisuke_Aramaki said:**
> Here's the link for the wall mate!

[http://smert1012.deviantart.com/art/Spotlight-WallPack-98100957]("http://smert1012.deviantart.com/art/Spotlight-WallPack-98100957")

Thanks!

---

### Post by raul_ on 2008-09-17
> **t_k said:**
> [[img]http://bildr.no/thumb/256150.jpeg[/img]](http://bildr.no/view/256150)

Interesting arrangement of widgets

---

### Post by Mark76 on 2008-09-17
Wait.

Are those application launchers in a directory?

Have the KDE people been trawling obscure old OSes (in this case RISCOS) for new interface ideas? :)

---

### Post by youngalfred on 2008-09-17
eeepc again. (701)

---

### Post by Daisuke_Aramaki on 2008-09-17
> **youngalfred said:**
> eeepc again. (701)

sweet! i am buying 901 next month and will install ubuntu immediately! :)

---

### Post by karth on 2008-09-17
New desktop, switched to fluxbox (click for larger size)

[LIST][*]WM: fluxbox (hardy repos) running along with xcompmgr
[*]Gtk: kryan
[*]fluxbox theme: royalty
[*]Wallpaper: customize.org
[*]Icons: hydroxygen 1.0.1[/LIST]

[[img]http://www.karthanis.net/upload_images/screens/clean.png[/img] ](http://www.karthanis.net/upload_images/screens/clean-big.png)[[img]http://www.karthanis.net/upload_images/screens/busybis.png[/img]](http://www.karthanis.net/upload_images/screens/busybis-big.png)

---

### Post by raul_ on 2008-09-17
> **youngalfred said:**
> eeepc again. (701)

That's just plain sexy. If only my laptop wasn't so new...

---

### Post by markp1989 on 2008-09-17
on my eee pc. 

OS: hardy 32 bit, with array kernel 
wm: Openbox
ob theme: onyx
GTK: wii black
icons: nuoveXT-1.6 
wallpaper: dont have one 
dock: fbpanel 

apps: firefox, uxterm, conky, wicd 


almost done, just looking for a light battery applet any suggestions? 

tell me what you think

---

### Post by vishzilla on 2008-09-17
My current desktop:
[[IMG]http://www.ourdesktops.com/desktops/thumb_medium/569e6b45-a7af-4041-8127-a0d88c6ce89a_thumbmedium.jpg[/IMG]](http://www.ourdesktops.com/desktop_user.aspx?user=vishal)

---

### Post by PurposeOfReason on 2008-09-17
WIAN, did you make the weather icons for Eikon or find them as I noticed that the fog icon isn't in it.

---

### Post by What is in a name? on 2008-09-17
> **PurposeOfReason said:**
> WIAN, did you make the weather icons for Eikon or find them as I noticed that the fog icon isn't in it.

I found them somewhere, and yes, I'm still trying to find something for the fog icon.

Here's my current desktop.

[[IMG]http://c.imagehost.org/t/0012/ecra.jpg[/IMG]](http://c.imagehost.org/view/0012/ecra.png)

Not much different from before, except for the wallpaper (the file's name is "canrun.png", but I can't recall where the heck did I download it), and also an attempt to reinvent the TextMate icon in order to come up with something more suitable for a text editor (Gedit and so on).

I'm also trying out ncmpc, and that dropdown terminal is actually stjerm. I'd probably use Gimmix if I wanted an elegant GUI for mpd, but Gimmix's tray icon's background is always gray, no matter what, in my end. Any clue?
And Hauschka is just wonderful, btw.

EDIT: I obviously forgot that ncmpc and Gimmix do not do audioscrobbling with Last.fm. ARGH.

---

### Post by 71CH on 2008-09-17
> **What is in a name? said:**
> I found them somewhere, and yes, I'm still trying to find something for the fog icon.

Here's my current desktop.

[[IMG]http://c.imagehost.org/t/0012/ecra.jpg[/IMG]](http://c.imagehost.org/view/0012/ecra.png)

Not much different from before, except for the wallpaper (the file's name is "canrun.png", but I can't recall where the heck did I download it), and also an attempt to reinvent the TextMate icon in order to come up with something more suitable for a text editor (Gedit and so on).

I'm also trying out ncmpc, and that dropdown terminal is actually stjerm.
And Hauschka is just wonderful, btw.

Hi
Do you know when you'll release the final version of Eikon2?

---

### Post by What is in a name? on 2008-09-17
> **71CH said:**
> Hi
Do you know when you'll release the final version of Eikon2?

I don't really know. I've been busy with some issues of my own, like trying to find a job, etc., so I'm working a tad slower. Sorry.

---

### Post by chucky chuckaluck on 2008-09-17
openbox, arch.blue ob theme, blue version of elegant brit gtk, quodlibet and pypanel (nimbus sans l font for everything). the wallpaper is a theo den boon painting tiled.

[[IMG]http://c.imagehost.org/t/0168/alphascr.jpg[/IMG]](http://c.imagehost.org/view/0168/alphascr.jpg)

---

### Post by 71CH on 2008-09-17
> **What is in a name? said:**
> I don't really know. I've been busy with some issues of my own, like trying to find a job, etc., so I'm working a tad slower. Sorry.

Sounds good.  No rush. :)

---

### Post by Savel on 2008-09-17
GTK: Lighting
Icons: Oxigen Refit

[ATTACH]85562[/ATTACH][ATTACH]85563[/ATTACH]

:confused:

---

### Post by indecisive on 2008-09-17
> **dlm4849 said:**
> Thats Avant Garde

No, it is URW Gothic L.

---

### Post by armageddon08 on 2008-09-17
Going with KDE4.1.1 for now:

---

### Post by sixstorm on 2008-09-17
My Ubuntu laptop

Ubuntu 8.04
AWN
Rhythmbox
VLC 9.02
"Dust" Theme
Myraid Pro Font

---

### Post by dbbolton on 2008-09-17
> **youngalfred said:**
> eeepc again. (701)
Do you have a link to that wallpaper?

---

### Post by nizaam on 2008-09-17
Hi.  this is my current desktop.

ubuntu 8.04
awn for the launcher
shiki-colors for the theme
chromifox for the firefox theme
gnome-colors for the icon theme.

---

### Post by Giant Speck on 2008-09-17
> **nizaam said:**
> Hi.  this is my current desktop.

ubuntu 8.04
awn for the launcher
shiki-colors for the theme
chromifox for the firefox theme
gnome-colors for the icon theme.

That is unbelievably awesome.

---

### Post by indecisive on 2008-09-17
> **dbbolton said:**
> Do you have a link to that wallpaper?

That wallpaper is under the Dream entry for the incoming artwork in Intrepid:  [https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Dream_Wallpaper](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Dream_Wallpaper).

---

### Post by Daisuke_Aramaki on 2008-09-17
posted my KDE desktop earlier! now its Gnome! All details in Terminal
[CENTER]
[[IMG]http://img369.imageshack.us/img369/7366/200809180001311680x1050xc0.th.png[/IMG]](http://img369.imageshack.us/my.php?image=200809180001311680x1050xc0.png)[/CENTER]

---

### Post by Daisuke_Aramaki on 2008-09-17
Here's the Wall link btw! [http://tinkupuri.deviantart.com/art/Apple-DNA-Red-Apple-24154715]("http://tinkupuri.deviantart.com/art/Apple-DNA-Red-Apple-24154715")

i am no apple fan boy, just that loved the WP, thats all. so no flaming please! :D

---

### Post by Stan_1936 on 2008-09-17
> **sixstorm said:**
> My Ubuntu laptop

Ubuntu 8.04
AWN
Rhythmbox
VLC 9.02
"Dust" Theme
Myraid Pro Font

Do you have a link to that wallpaper?  Could you please post it?

---

### Post by SpenceMakesSense on 2008-09-17
Metal Theme
Death note>Everything

---

### Post by etnlIcarus on 2008-09-17
> **karth said:**
> New desktop, switched to fluxbox (click for larger size)

[LIST][*]WM: fluxbox (hardy repos) running along with xcompmgr
[*]Gtk: kryan
[*]fluxbox theme: royalty
[*]Wallpaper: customize.org
[*]Icons: hydroxygen 1.0.1[/LIST]

[[img]http://www.karthanis.net/upload_images/screens/clean.png[/img] ](http://www.karthanis.net/upload_images/screens/clean-big.png)[[img]http://www.karthanis.net/upload_images/screens/busybis.png[/img]](http://www.karthanis.net/upload_images/screens/busybis-big.png)

Love it. My half-arsed attempts at getting fluxbox into a usable state have only resulted in my breaking it.

---

### Post by youngalfred on 2008-09-17
> **dbbolton said:**
> Do you have a link to that wallpaper?

Yup.  [https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Dream_Wallpaper](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Dream_Wallpaper)

From the Incoming Intrepid Artwork on the ubuntu wiki.  Great place for wallpapers and themes :)  (check out the dust theme.  Great dark theme thats easy to read.

---

### Post by Patricrawley on 2008-09-17
Decided to check out what Glow is like

Emerald: Glow
GTK: Glow Ice
Wallpaper: Something from DeviantArt
Icons: HumanElephant - Marine

---

### Post by Madwida on 2008-09-17
Here's mine on my EEE PC 701 4gb

---

### Post by Madwida on 2008-09-17
Sorry--posted wrong image.

---

### Post by Patricrawley on 2008-09-17
What was that glow theme I was seeing everywhere with the color bar accross the top?

---

### Post by myusername on 2008-09-17
openbox

---

### Post by Nythain on 2008-09-17
not sure if i've posted any of mine lately...
been pretty slow but here we go

---

### Post by Mark76 on 2008-09-18
> **Madwida said:**
> Sorry--posted wrong image.


Is that a panel or a dock with some kind of scroll plugin?

---

### Post by mewithafez on 2008-09-18
> **Patricrawley said:**
> What was that glow theme I was seeing everywhere with the color bar accross the top?

It could either be shiki-colors or clearglow/murrineglow, both are on gnome-look.org.

---

### Post by aschwerin.moses on 2008-09-18
> **Patricrawley said:**
> Decided to check out what Glow is like

Emerald: Glow
GTK: Glow Ice
Wallpaper: Something from DeviantArt
Icons: HumanElephant - Marine
Can you please tell me which movie player is that.. I've been looking for a borderless player like in ur pic..

---

### Post by phisphere on 2008-09-18
[[img]http://phisphere.org/shots/ubuntu-thumb.png[/img]](http://phisphere.org/shots/ubuntu.png)

simple and practical setup.

---

### Post by Patricrawley on 2008-09-18
> **aschwerin.moses said:**
> Can you please tell me which movie player is that.. I've been looking for a borderless player like in ur pic..

VLC ran through a minimized terminal, the command is -I ncurses

---

### Post by Madwida on 2008-09-18
> **Mark76 said:**
> Is that a panel or a dock with some kind of scroll plugin?

It's a panel with expand unchecked using the dust theme.  I found that on the little eee pc screen a panel works much better than a dock.  

Anyone know how to get rid of the top panel and transfer the wireless connection icon to the bottom panel?  I did this once before but now cannot recall how.  Thanks

---

### Post by Kooothor on 2008-09-18
Here is mine :)

---

### Post by ayoli on 2008-09-18
> **Madwida said:**
> It's a panel with expand unchecked using the dust theme.  I found that on the little eee pc screen a panel works much better than a dock.  

Anyone know how to get rid of the top panel and transfer the wireless connection icon to the bottom panel?  I did this once before but now cannot recall how.  Thanks

right click on an applet pops up a menu, make sure that the applet is not locked to the panel in that menu, after, pick "move" then drag and drop your applet to your bottom panel.
to remove a panel, right click on an empty space on this panel and select "remove this panel" in the pop up menu.
(the labels in these menus may differ a little because english isn't my native language).

---

### Post by Madwida on 2008-09-18
> **ayoli said:**
> right click on an applet pops up a menu, make sure that the applet is not locked to the panel in that menu, after, pick "move" then drag and drop your applet to your bottom panel.
to remove a panel, right click on an empty space on this panel and select "remove this panel" in the pop up menu.
(the labels in these menus may differ a little because english isn't my native language).

Thanks for this.  I have tried to use this method--as it works for just about all other applets--but the default wireless/network manager applet seems to want to stay where it is, i.e. there is no option to unlock, remove, move, etc. And in the applet menu--from where you can choose extra applets--there is no such applet.  I'll try again tonight--I'm on my Mac now.

---

### Post by ddnev45 on 2008-09-18
> **Madwida said:**
> Thanks for this.  I have tried to use this method--as it works for just about all other applets--but the default wireless/network manager applet seems to want to stay where it is, i.e. there is no option to unlock, remove, move, etc. And in the applet menu--from where you can choose extra applets--there is no such applet.  I'll try again tonight--I'm on my Mac now.

Perhaps you need to move the entire "system notification" tray to the desired panel.

---

### Post by ayoli on 2008-09-18
> **Madwida said:**
> Thanks for this.  I have tried to use this method--as it works for just about all other applets--but the default wireless/network manager applet seems to want to stay where it is, i.e. there is no option to unlock, remove, move, etc. And in the applet menu--from where you can choose extra applets--there is no such applet.  I'll try again tonight--I'm on my Mac now.

this is not an applet but an application in your system tray notification applet, you have to right click on the left of the tray notification applet to see the menu that allow to move it.

---

### Post by urukrama on 2008-09-18
Openbox 3.4.7 with the Salvage Openbox and Gtk theme (one of my favorite Openbox themes!), Corbel fonts, and a wallpaper based on an image I once found online.

---

### Post by Madwida on 2008-09-18
> **ddnev45 said:**
> Perhaps you need to move the entire "system notification" tray to the desired panel.

Hi 

Could you please explain--I'm not sure what this means.  Thanks

---

### Post by Mark76 on 2008-09-18
Your system tray is a panel applet. Just remove it and then add it to the bottom panel.

---

### Post by Do Androids Dream? on 2008-09-18
Here's mine, first Ubuntu desktop.
Running on a Toshiba laptop and loving it !=D>

---

### Post by Madwida on 2008-09-18
> **Mark76 said:**
> Your system tray is a panel applet. Just remove it and then add it to the bottom panel.

Thanks.  I'll give this a try.

---

### Post by ddnev45 on 2008-09-18
> **ayoli said:**
> this is not an applet but an application in your system tray notification applet, you have to right click on the left of the tray notification applet to see the menu that allow to move it.

> **Mark76 said:**
> Your system tray is a panel applet. Just remove it and then add it to the bottom panel.

Yes, this is what I was referring to.

---

### Post by Patricrawley on 2008-09-18
Bit of an update switched my icons set to Eikon, I also switched from emerald to GTK Window Decorator for a bit to use the ClearGlow widow border with the Glow Ice color set. Other than that everything is still the same. I was wondering, how do you build your own GTK window borders and controls?

---

### Post by Bart_D on 2008-09-18
> **phisphere said:**
> [[img]http://phisphere.org/shots/ubuntu-thumb.png[/img]](http://phisphere.org/shots/ubuntu.png)

simple and practical setup.

Can you post your theme and wallpaper information?(GTK?, WM?)

---

### Post by Mos_Barbuta on 2008-09-18
> **urukrama said:**
> Openbox 3.4.7 with the Salvage Openbox and Gtk theme (one of my favorite Openbox themes!), Corbel fonts, and a wallpaper based on an image I once found online.


...the Simplicity...
 must...   get...   rid...   of unnecessary things in   my life


Seriously, great great stuff ! 
Always inspiring

---

### Post by phisphere on 2008-09-18
> **Bart_D said:**
> Can you post your theme and wallpaper information?(GTK?, WM?)
sure, gtk theme is [dust]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/DustTheme") and wallpaper can be found [here]("http://oliuss.deviantart.com/art/Wood-Wallpaper-2-87623810").

other than that, it's just plain simple gnome desktop (made for productivity).

---

### Post by skitzware on 2008-09-18
[[IMG]http://www.ourdesktops.com/desktops/thumb_medium/6765e9de-5800-46de-948f-2dc5e494946d_thumbmedium.jpg[/IMG]](http://www.ourdesktops.com/desktop_user.aspx?user=skitzware)

GTK & fluxbox theme are Mire v2

---

### Post by urukrama on 2008-09-18
> **Mos_Barbuta said:**
> ...the Simplicity...
 must...   get...   rid...   of unnecessary things in   my life

Seriously, great great stuff ! 
Always inspiring

Thank you.

---

### Post by svlad cjelli on 2008-09-18
Its Arch but its Linux... And my Ubuntu-Desk looks similar...

So here you are...


Simple and Stupid:


[[img]http://ubuntu-pics.de/thumb/3405/bildschirmfoto_2_MFIi5V.png[/img]](http://ubuntu-pics.de/bild/3405/bildschirmfoto_2_MFIi5V.png)

[[img]http://ubuntu-pics.de/thumb/3404/bildschirmfoto_Xpa8dT.png[/img]](http://ubuntu-pics.de/bild/3404/bildschirmfoto_Xpa8dT.png)



My big problem is, that the icon-themes on gnome-look suck a lot.

I am changing between crashbit and Oxygen Refit... and thats all...


Does anyone know other sites to get a stylish icon theme?
exept deviant-art and customize.org?

---

### Post by el mariachi on 2008-09-18
> **urukrama said:**
> Openbox 3.4.7 with the Salvage Openbox and Gtk theme (one of my favorite Openbox themes!), Corbel fonts, and a wallpaper based on an image I once found online.
great to see you're still active :D great shot
cool wally too :D

---

### Post by jvc26 on 2008-09-18
> **sixstorm said:**
> 
Ubuntu 8.04
AWN
Rhythmbox
VLC 9.02
"Dust" Theme
Myraid Pro Font

Do you have a link to that wallpaper - its pretty quality!

Il

---

### Post by sixstorm on 2008-09-18
[http://interfacelift.com/wallpaper_beta/details/1659/the_earth.html](http://interfacelift.com/wallpaper_beta/details/1659/the_earth.html)

---

### Post by raul_ on 2008-09-18
Mainly to show off Lancelot, a KMenu alternative.

while we're at it [http://br.youtube.com/watch?v=BQAObTzlI50]("http://br.youtube.com/watch?v=BQAObTzlI50")

---

### Post by 71CH on 2008-09-18
rawr.

---

### Post by PatrickMoore on 2008-09-18
heres mine, ive been playing around with it all day.i think its pretty hip

---

### Post by jordanmthomas on 2008-09-19
> **What is in a name? said:**
> 
EDIT: I obviously forgot that ncmpc and Gimmix do not do audioscrobbling with Last.fm. ARGH.

Why not use mpdscribble?  If someone's already suggested it, disregard this.

---

### Post by cardinals_fan on 2008-09-19
In honor of the LHC, a new wallpaper:

[[img]http://xs231.xs.to/xs231/08385/28-09-18-08417.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs231&d=08385&f=28-09-18-08417.jpg)

Otherwise, it's my usual Xfce with my favorite Conky config.

---

### Post by UrbanSlayer on 2008-09-19
My current - 

[[IMG]http://www.urbanslayer.com/images/Desktops/Ubuntu/Thumbs/tn_Eclair190908.jpg[/IMG]]("http://www.urbanslayer.com/images/Desktops/Ubuntu/Eclair190908.jpg")

[[IMG]http://www.urbanslayer.com/images/Desktops/Ubuntu/Thumbs/tn_Eclair190908Apps.jpg[/IMG]]("http://www.urbanslayer.com/images/Desktops/Ubuntu/Eclair190908Apps.jpg")

Have switched from KDE4.1 to Openbox.  Still using some KDE4 apps though.

```
Openbox - Glow Ibex
GTK - QtCurve
QT3 - QtCurve
QT4 - QtCurve
Font - Purisa
Icons - Oxygen / OxygenRefit
Dock - XFCE

```

---

### Post by PurposeOfReason on 2008-09-19
I made a fog icon for all who are using the eikon theme. Because of how it scales on the panel you don't see the sharp edge.

EDIT-Made a night one though I don't think the weather switches between day and night with fog.

---

### Post by urukrama on 2008-09-19
> **el mariachi said:**
> great to see you're still active :D great shot
cool wally too :D

Thank you, mariachi.

I've been busy, and spend a lot less time online these days. Life is a lot more peaceful without the internet. ;-)

---

### Post by rjmdomingo2003 on 2008-09-19
GTK & OB theme - Modded Mythos, wallpaper from jackrebel, conky, tint, x'mission...

---

### Post by Daisuke_Aramaki on 2008-09-19
> **rjmdomingo2003 said:**
> GTK & OB theme - Modded Mythos, wallpaper from jackrebel, conky, tint, x'mission...

this is great! minimalism at its best!

---

### Post by Islington on 2008-09-19
icons: nuo dropline
wall:  theoneIhavebeenworkingonandneedsaname.png
gtk:  clearglow orange
emerald: modified clearglow

---

### Post by markp1989 on 2008-09-19
am i the only person who cannot see the thumbnails?

---

### Post by raul_ on 2008-09-19
> **markp1989 said:**
> am i the only person who cannot see the thumbnails?

I guess...

---

### Post by Islington on 2008-09-19
> **markp1989 said:**
> am i the only person who cannot see the thumbnails?

if you doubleclick you should be able to see the whole image.

---

### Post by markp1989 on 2008-09-19
i have attached a screen shot to explain what i mean

---

### Post by rjmdomingo2003 on 2008-09-19
> **markp1989 said:**
> i have attached a screen shot to explain what i mean
Dunno, Daisuke commented on the same screenie so he/she has seen it.

---

### Post by Daisuke_Aramaki on 2008-09-19
> **rjmdomingo2003 said:**
> Dunno, Daisuke commented on the same screenie so he/she has seen it.

he is rite! :)

---

### Post by erykroom on 2008-09-19
Icons: Modified leopard icons v_0.a3
Wallpaper: a photo from flickr

---

### Post by Whiffle on 2008-09-19
Openbox
tint 
stallonetray
wallpeper: [http://popartmachine.com/machine/daily/061708/fire_skull.jpg](http://popartmachine.com/machine/daily/061708/fire_skull.jpg)

screenshot: [http://www.resnet.trinity.edu/avaselaa/2008-09-19-111316_1024x768_scrot.png](http://www.resnet.trinity.edu/avaselaa/2008-09-19-111316_1024x768_scrot.png)

---

### Post by chucky chuckaluck on 2008-09-19
openbox, pypanel and the wallpaper is a tiled detail from a gottfried helnwein mixed media piece. the ob and gtk themes are edited versions of elegant brit to match the wallpaper.

[[IMG]http://b.imagehost.org/t/0296/skywardscr.jpg[/IMG]](http://b.imagehost.org/view/0296/skywardscr.jpg) [[IMG]http://b.imagehost.org/t/0890/skywardscr2.jpg[/IMG]](http://b.imagehost.org/view/0890/skywardscr2.jpg)

---

### Post by ayoli on 2008-09-19
> **markp1989 said:**
> i have attached a screen shot to explain what i mean

actually, you don't see avatars too, maybe something blocks images on your side ?

---

### Post by What is in a name? on 2008-09-19
...And here I am on GNOME again:

[[IMG]http://b.imagehost.org/t/0271/ecra.jpg[/IMG]](http://b.imagehost.org/view/0271/ecra.png)

Just modded a bit the Fresh2.0 GTK theme, from Clearlooks to Murrine, from blue to red-orange-ish, etc., my usual trend. I'm also trying out the Museo font (free download at [http://www.myfonts.com/fonts/exljbris/museo/](http://www.myfonts.com/fonts/exljbris/museo/) ) to see how it behaves on a desktop context.

And thanks for the suggestion about mpdscribble. Will take a look. Meanwhile I just took away the cover art from Sonata in order to make it slightly more pleasant to look at (weird taste, I know).

---

### Post by markp1989 on 2008-09-19
"actually, you don't see avatars too, maybe something blocks images on your side ?"

It its fine on all sites except this one:S 

it was working fine till they made all the name piratey, and now i can see avatars, quote buttons,report.thanks,edit the logo at the top.

i duno know whats happened, i havnt changed anything at this end, but it seems that i am the only person who is havin this problem 

i started a thread about it here [http://ubuntuforums.org/showthread.php?p=5819274](http://ubuntuforums.org/showthread.php?p=5819274)

---

### Post by vishzilla on 2008-09-19
> **What is in a name? said:**
> [[IMG]http://b.imagehost.org/t/0271/ecra.jpg[/IMG]](http://b.imagehost.org/view/0271/ecra.png)

Just modded a bit the Fresh2.0 GTK theme, from Clearlooks to Murrine, from blue to red-orange-ish, etc., my usual trend. I'm also trying out the Museo font (free download at [http://www.myfonts.com/fonts/exljbris/museo/](http://www.myfonts.com/fonts/exljbris/museo/) ) to see how it behaves on a desktop context.

And thanks for the suggestion about mpdscribble. Will take a look. Meanwhile I just took away the cover art from Sonata in order to make it slightly more pleasant to look at (weird taste, I know).

Dude, your desktops always rocks. It makes the Gnome dual panels look good.

---

### Post by ayoli on 2008-09-19
> **What is in a name? said:**
> ...And here I am on GNOME again:

[[IMG]http://b.imagehost.org/t/0271/ecra.jpg[/IMG]](http://b.imagehost.org/view/0271/ecra.png)

Just modded a bit the Fresh2.0 GTK theme, from Clearlooks to Murrine, from blue to red-orange-ish, etc., my usual trend. I'm also trying out the Museo font (free download at [http://www.myfonts.com/fonts/exljbris/museo/](http://www.myfonts.com/fonts/exljbris/museo/) ) to see how it behaves on a desktop context.

And thanks for the suggestion about mpdscribble. Will take a look. Meanwhile I just took away the cover art from Sonata in order to make it slightly more pleasant to look at (weird taste, I know).

Nice one again (except maybe I'm not a fan of this font).
Btw, one question : 
How do you manage to have different colors for the date and the time in your panel ?

---

### Post by What is in a name? on 2008-09-19
> **ayoli said:**
> Nice one again (except maybe I'm not a fan of this font).
Btw, one question : 
How do you manage to have different colors for the date and the time in your panel ?

Open the Gconf-editor and then keep opening the folders on the left pane until you get to the clock applet:

>> apps > panel > applets > clock_screen0 [or something similar on your PC] > prefs

Be sure that the format of the clock is set to "custom", and then focus on the "custom_format" parameter. The colors are set inside of <span> tags. Like this:

```
<span color="#db7729">%A, %d %B</span>   %H:%M %Z  
```

Instead of that color, you can choose the one you prefer, and repeat the procedure every time you need to add a different color to the text in the clock.

OFF-TOPIC: ***The Poop Deck?***... What?
EDIT TO THE OFF-TOPIC: So this is the International Talk Like a Pirate Day... Some people have too much free time on their hands.

---

### Post by Sephoroth on 2008-09-19
Ahoy, enter the spirit matey.  That desktop be worth pillaging!

---

### Post by ayoli on 2008-09-19
little changes, and a new wall (from flickr, but streched, and not with this name).
[[IMG]http://ayozone.org/wp-content/gallery/screenshots-september-2008/thumbs/thumbs_19092008.png[/IMG]]("http://ayozone.org/gallery/screenshots-september-2008")
additional infos in the screenshot.

---

### Post by namegame on 2008-09-19
Here is what I have now. I decided to go with a blue theme...

conky
emerald, compiz, etc.

---

### Post by Madwida on 2008-09-19
> **namegame said:**
> Here is what I have now. I decided to go with a blue theme...

conky
emerald, compiz, etc.

It's likely that this has been discussed somewhere, but: how did you get the translucent terminal?  Thanks

---

### Post by namegame on 2008-09-19
> **Madwida said:**
> It's likely that this has been discussed somewhere, but: how did you get the translucent terminal?  Thanks

Open up a terminal, go to Edit->Current Profile->Effects, and it's the third choice I think...

---

### Post by Madwida on 2008-09-19
> **namegame said:**
> Open up a terminal, go to Edit->Current Profile->Effects, and it's the third choice I think...
Perfect--thanks!

---

### Post by 71CH on 2008-09-19
This is a bit OT but how do you have different terminal colors like you have in Linux Mint?  (actually I would like it exactly like Linux Mint).  Thanks.

---

### Post by Bart_D on 2008-09-19
> **What is in a name? said:**
> ...And here I am on GNOME again:

[[IMG]http://b.imagehost.org/t/0271/ecra.jpg[/IMG]](http://b.imagehost.org/view/0271/ecra.png)

Just modded a bit the Fresh2.0 GTK theme, from Clearlooks to Murrine, from blue to red-orange-ish, etc., my usual trend. I'm also trying out the Museo font (free download at [http://www.myfonts.com/fonts/exljbris/museo/](http://www.myfonts.com/fonts/exljbris/museo/) ) to see how it behaves on a desktop context.

And thanks for the suggestion about mpdscribble. Will take a look. Meanwhile I just took away the cover art from Sonata in order to make it slightly more pleasant to look at (weird taste, I know).

That is a fantastic wallpaper....do you have a link to it?

---

### Post by What is in a name? on 2008-09-19
> **Bart_D said:**
> That is a fantastic wallpaper....do you have a link to it?

Hi! I don't remember where did I get it from, but I'm uploading the wallpaper as an attachment:

---

### Post by Joe_archer on 2008-09-19
Wallpaper from interfacelift
ring sensor screenlets
Soft and Clear emerald theme
NuoveXT 2 icons

dual screen setup 2560x1024

---

### Post by svlad cjelli on 2008-09-19
> **What is in a name? said:**
> ...And here I am on GNOME again:

[[IMG]http://b.imagehost.org/t/0271/ecra.jpg[/IMG]](http://b.imagehost.org/view/0271/ecra.png)

Just modded a bit the Fresh2.0 GTK theme, from Clearlooks to Murrine, from blue to red-orange-ish, etc., my usual trend. I'm also trying out the Museo font (free download at [http://www.myfonts.com/fonts/exljbris/museo/](http://www.myfonts.com/fonts/exljbris/museo/) ) to see how it behaves on a desktop context.

And thanks for the suggestion about mpdscribble. Will take a look. Meanwhile I just took away the cover art from Sonata in order to make it slightly more pleasant to look at (weird taste, I know).

Which icon-Teme do you use?

---

### Post by el mariachi on 2008-09-19
Eikon 2;)

---

### Post by RequinB4 on 2008-09-19
attached

---

### Post by Opeth115 on 2008-09-19
New desk, haven't posted one for a while =P . Comments?

[IMG]http://tn3-2.deviantart.com/fs36/300W/f/2008/263/4/9/Desk___Sept_19th_by_Opeth115.png[/IMG]

[http://opeth115.deviantart.com/art/Desk-Sept-19th-98416786](http://opeth115.deviantart.com/art/Desk-Sept-19th-98416786)

---

### Post by BOBSONATOR on 2008-09-20
> **What is in a name? said:**
> ...And here I am on GNOME again:

[[IMG]http://b.imagehost.org/t/0271/ecra.jpg[/IMG]](http://b.imagehost.org/view/0271/ecra.png)

Just modded a bit the Fresh2.0 GTK theme, from Clearlooks to Murrine, from blue to red-orange-ish, etc., my usual trend. I'm also trying out the Museo font (free download at [http://www.myfonts.com/fonts/exljbris/museo/](http://www.myfonts.com/fonts/exljbris/museo/) ) to see how it behaves on a desktop context.

And thanks for the suggestion about mpdscribble. Will take a look. Meanwhile I just took away the cover art from Sonata in order to make it slightly more pleasant to look at (weird taste, I know).

Nice one man, Can Der Sexi is awesome!

---

### Post by Giant Speck on 2008-09-20
Damn.  I wish GTK themes could be ported to KDE.

What is in a Name, your themes are simply the best.

---

### Post by kanpachi on 2008-09-20
running hardy on a mac mini
theme is murrina-brave with same icons
i found this cool wallpaper on flickr =^.^=

---

### Post by olskar on 2008-09-20
> **kanpachi said:**
> running hardy on a mac mini
theme is murrina-brave with same icons
i found this cool wallpaper on flickr =^.^=

Wow I never realized cats have a hairy tongue :)

---

### Post by Giant Speck on 2008-09-20
> **kanpachi said:**
> running hardy on a mac mini
theme is murrina-brave with same icons
i found this cool wallpaper on flickr =^.^=

Dear Lord, it's ghost kitteh!

---

### Post by Giant Speck on 2008-09-20
Did some work on my theme and desktop today.

- new wallpaper
- new panel color
- adjusted theme colors
- created new Emerald theme

---

### Post by eightmillion on 2008-09-20
Here's a colour you don't see very often. Deep dark red. It has a kind of theatrical feel to it.

---

### Post by mrgnash on 2008-09-20
[IMG]http://i35.tinypic.com/119nwj7.png[/IMG]

```

  Metacity:              chrome-like
  GTK:                   chrome-like
  Font (Apps):           Droid Sans 11
  Font (Terminal):       Droid Sans Mono 12
  Icons:                 UltimateGnome
  Wall:                  Ubuntu-Blubuntu_1600x1200.png

```

---

### Post by RequinB4 on 2008-09-20
> **eightmillion said:**
> Here's a colour you don't see very often. Deep dark red. It has a kind of theatrical feel to it.

Do you still have a source for that compiz theme or wallpaper?  That's one of the better black and red theme's i've seen.

---

### Post by eightmillion on 2008-09-20
> **RequinB4 said:**
> Do you still have a source for that compiz theme or wallpaper?  That's one of the better black and red theme's i've seen.

Thanks. Here's the links:

[Wallpaper]("http://allhopeislost.deviantart.com/art/DES-Dedication-Set-82381277")
[Skydome]("http://allhopeislost.deviantart.com/art/DES-Dedication-Set-82381277")
[Emerald theme]("http://api.compiz-themes.org/content/show.php/Kore+Suite?content=54701&PHPSESSID=0aad7152d8643b23de2fd72e1e5601df")

---

### Post by Mark76 on 2008-09-20
Openbox plus feh, trayer, tint2, dclock and idesk

[[img]http://xs231.xs.to/xs231/08386/2008-09-20-170058_1280x1024_scrot466.png[/img]](http://xs.to)

And a shot with an actual window open

---

### Post by What is in a name? on 2008-09-20
So I was trying out this concept with the Open Document logo, to finally stop avoiding OO.o because of the repelling effect of the icons, and...

[[IMG]http://b.imagehost.org/t/0491/ecra.jpg[/IMG]](http://b.imagehost.org/view/0491/ecra.png)

---

### Post by meborc on 2008-09-20
> **What is in a name? said:**
> So I was trying out this concept with the Open Document logo, to finally stop avoiding OO.o because of the repelling effect of the icons, and...

really impressive! =D>

---

### Post by Jackelope on 2008-09-20
Check it out:

[[img]http://xs231.xs.to/xs231/08386/my_desktop430.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs231&d=08386&f=my_desktop430.png)

GTK/Metacity: [The new Dust theme, modified for less purpleish tones]("http://www.gnome-look.org/content/show.php/Ubuntu+Dust?content=88790")
Walpaper: [Wanted]("http://www.gnome-look.org/content/show.php/Wanted?content=89060")
Icons: [Black White 2 Style]("http://www.gnome-look.org/content/show.php/black-white+2+Style?content=72619")
Font: Arial

---

### Post by el mariachi on 2008-09-20
now to find better fitting dock icons

---

### Post by aschwerin.moses on 2008-09-20
> **What is in a name? said:**
> So I was trying out this concept with the Open Document logo, to finally stop avoiding OO.o because of the repelling effect of the icons, and...

[[IMG]http://b.imagehost.org/t/0491/ecra.jpg[/IMG]](http://b.imagehost.org/view/0491/ecra.png)
Can you give me link to those icons please...

---

### Post by ayoli on 2008-09-20
> **What is in a name? said:**
> So I was trying out this concept with the Open Document logo, to finally stop avoiding OO.o because of the repelling effect of the icons, and...

[[IMG]http://b.imagehost.org/t/0491/ecra.jpg[/IMG]](http://b.imagehost.org/view/0491/ecra.png)

nifty :)

---

### Post by What is in a name? on 2008-09-20
> **aschwerin.moses said:**
> Can you give me link to those icons please...

Sure. Just go to my drop.io address: [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)
Then download the file named Eikon2-RC3-r20080920.tar.gz. Enjoy!

---

### Post by Daisuke_Aramaki on 2008-09-20
> **Giant Speck said:**
> Did some work on my theme and desktop today.

- new wallpaper
- new panel color
- adjusted theme colors
- created new Emerald theme

awesome! planning to post ur color scheme and the rest? :)

---

### Post by 71CH on 2008-09-20
> **What is in a name? said:**
> Sure. Just go to my drop.io address: [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)
Then download the file named Eikon2-RC3-r20080920.tar.gz. Enjoy!

Is RC3 the latest?  Just asking cuz I think I installed RC1.

---

### Post by What is in a name? on 2008-09-20
> **71CH said:**
> Is RC3 the latest?  Just asking cuz I think I installed RC1.

Yes, RC3 is the latest version. Considering how long I'm taking to perfect Eikon, I end up tweaking already existing icons instead of adding the ones that are still lacking, so the so-called "release candidates" are multiplying themselves, a bit more than I wanted to.

---

### Post by aschwerin.moses on 2008-09-20
> **What is in a name? said:**
> Sure. Just go to my drop.io address: [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)
Then download the file named Eikon2-RC3-r20080920.tar.gz. Enjoy!
Thanks buddy

---

### Post by voteforpedro36 on 2008-09-20
GNOME for the first time in a while.

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-20-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-20-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-20-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-20-08-media.png)

---

### Post by jamescbjr on 2008-09-20
My first one.


[[IMG]http://img441.imageshack.us/img441/594/screenshot7lq8.th.png[/IMG]](http://img441.imageshack.us/my.php?image=screenshot7lq8.png)

---

### Post by aschwerin.moses on 2008-09-20
> **What is in a name? said:**
> Yes, RC3 is the latest version. Considering how long I'm taking to perfect Eikon, I end up tweaking already existing icons instead of adding the ones that are still lacking, so the so-called "release candidates" are multiplying themselves, a bit more than I wanted to.
Hey... can you please tell me the name of the icons ..the iphone type icons

---

### Post by aschwerin.moses on 2008-09-20
> **aschwerin.moses said:**
> Hey... can you please tell me the name of the icons ..the iphone type icons
Im sorry..i got it...

---

### Post by Vorian on 2008-09-20
new toy

---

### Post by Islington on 2008-09-20
> **Vorian said:**
> new toy

am I missing something here?

---

### Post by Giant Speck on 2008-09-20
> **Islington said:**
> am I missing something here?

Dude, you can't see it?

It's obvious that it's an uh....... you know..... yeah.

---

### Post by vishzilla on 2008-09-20
**Details provided by OurDesktops.com**

Icons: Eikon2
GTK: Didymous
[[IMG]http://www.ourdesktops.com/desktops/thumb_medium/aecc8c06-57a6-4e62-aa81-02f139a4247c_thumbmedium.jpg[/IMG]](http://www.ourdesktops.com/desktop_user.aspx?user=vishal)

---

### Post by ddnev45 on 2008-09-21
Some minor tweaks to my Open Box setup.

"Fall is Awesome" theme, tint, trayer, conky, xine.

---

### Post by Mark76 on 2008-09-21
Tweaked mine to add various dockapps to the openbox dock (which is set to autohide)

---

### Post by scouser73 on 2008-09-21
I'm using a customised version of Glossy with Gnome Colours Wine folders.[Screenlets] Perfect Clock with a black style, Clear Calendar, Uptime. The wallpaper is Ubuntu Sky [http://www.ubuntu-art.org/content/show.php/Ubuntu%27s+Sky?content=63987]("http://www.ubuntu-art.org/content/show.php/Ubuntu%27s+Sky?content=63987")

---

### Post by cawill on 2008-09-21
[[IMG]http://img504.imageshack.us/img504/2375/septff2.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=septff2.jpg)[[IMG]http://img504.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Compiz, xfdesktop, xfce panel, AWN, conky.

GTK Theme is Elegant Glow.

---

### Post by markp1989 on 2008-09-21
eee using touch screen only, because i plan to  convert it in to a  tablet 

details :

-os  hardy
gtk: black garden
wm: openbox
obtheme: onyx
icons : nuovext

for some reason, after i rotate the screen the fonts get big

---

### Post by raul_ on 2008-09-21
> **markp1989 said:**
> eee using touch screen only, because i plan to  convert it in to a  tablet 

details :

-os  hardy
gtk: black garden
wm: openbox
obtheme: onyx
icons : nuovext

image?

---

### Post by markp1989 on 2008-09-21
> **raul_ said:**
> image?

forgot to add pictures  sorted now

---

### Post by macvr on 2008-09-21
hi,
details>
icons: Aero-CrazyFolk-RC1[but had to correct most of the icons since the theme was RC1]
emerald window borders:VistaQ


PS:i know the wallpaper is a bit loud!!!

---

### Post by Koori23 on 2008-09-21
I'm still liking my setup. 

elegant_dark_gray by UbuForum's own Herbster


XFCE Hardy, Icons HighContrastInverse, Font HandleGotD

I got the wallpaper from interfacelift

---

### Post by voteforpedro36 on 2008-09-21
Back to Openbox, this is based on WiIaN?'s last screenshot, the wall + colors are taken from it. Now I'm thinking Tint should be rounded, but I'll play with it later.

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-21-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-21-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-21-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-21-08-media.png)

---

### Post by easybake on 2008-09-21
Fluxbox (menu still needs work)

Murrina-DarkBlue

3 Conkys.

[Wallpaper]("http://artgerm.deviantart.com/art/Pepper-Mono-18130376")

[[IMG]http://img502.imageshack.us/img502/8763/screenshot1zh4.th.png[/IMG]](http://img502.imageshack.us/img502/8763/screenshot1zh4.png)[[IMG]http://img502.imageshack.us/img502/9542/screenshot2bp1.th.png[/IMG]](http://img502.imageshack.us/img502/9542/screenshot2bp1.png)

---

### Post by klange on 2008-09-21
> **markp1989 said:**
> eee using touch screen only, because i plan to  convert it in to a  tablet 

details :

-os  hardy
gtk: black garden
wm: openbox
obtheme: onyx
icons : nuovext

for some reason, after i rotate the screen the fonts get big

You should look at the Matchbox window manager. It works quite nicely for a small tablet configuration and has its own dock and keyboard.

---

### Post by mccord on 2008-09-21
[[img]http://i33.tinypic.com/hrbms4.png[/img]]("http://i35.tinypic.com/9to3l3.png")

openbox (mire_v2_orange theme)
tint2
trayer
conky

---

### Post by el mariachi on 2008-09-21
mccord: very nice, what you did with tint and conky :D

---

### Post by narf41 on 2008-09-21
my (x)ubuntu-09-screeny

[[img]http://ubuntu-pics.de/thumb/3463/s080921_0rR14B.png[/img]](http://ubuntu-pics.de/bild/3463/s080921_0rR14B.png)

xfce with gnome-panel and conky
i use a full-transparent xfce-panel on the right side, so maximized windows dont overlap the sidebar.
and i made a wallpaper changer with cron, so my xfce-background changes every 5 minutes, using the wp´s from the xfce-wallpaper-list at random.
gtk/emerald:"hyo", icons:"royal-preview"

---

### Post by el mariachi on 2008-09-21
you don't need to use a transparent xfce-panel.. just set the size of the border in xfce settings

---

### Post by narf41 on 2008-09-21
yeah i know, but it does not work with compiz :(

---

### Post by el mariachi on 2008-09-21
aaaah riiight compiz the little-big-devil :p

---

### Post by narf41 on 2008-09-21
yepp, but i luv it...so i have to use this crook :D

---

### Post by hellokitty1001 on 2008-09-21
[http://sikh.myminicity.com/tra](http://sikh.myminicity.com/tra)

---

### Post by RiceMonster on 2008-09-21
I think the xfwm4 compositor looks nice enough on its own. No compiz in Xfce for me :)

---

### Post by schmolch on 2008-09-21
> **markp1989 said:**
> 
for some reason, after i rotate the screen the fonts get big

I experienced the same thing.
I filed a bug a while ago but never got a reaction.

---

### Post by Mark76 on 2008-09-21
I installed Gkrellm. It fits very nicely in the OpenBox dock :D

---

### Post by el mariachi on 2008-09-21
> **RiceMonster said:**
> I think the xfwm4 compositor looks nice enough on its own. No compiz in Xfce for me :)
too bad there aren't that many themes like for metacity or emerald :(

---

### Post by RiceMonster on 2008-09-21
> **el mariachi said:**
> too bad there aren't that many themes like for metacity or emerald :(

Yeah, that's a definite downside for sure.

---

### Post by el mariachi on 2008-09-21
I think I've found them. :D
Still using Glow_dark for xfwm4
MurrineGlow Orange for GTK
dock is awn 
dock icons are __ecqlipse_2___PNG_by_chrfb :D
app icons are Eikon2 rc3 (currently)
music playing: Silence is Sexy  - Ages (free legal download on Mininova.org :D cool band!)

---

### Post by FlamingTeddiz on 2008-09-21
Mine. guess i'm a little sensitive about my personal details... some blurring.

---

### Post by Iandefor on 2008-09-21
Glossy GTK/Metacity, GNOME-Brave icon theme, Trebuchet MS font, and [Outta Space Blue wallpaper by Infinise Design]("http://www.infinisedesign.net/downloads/view/outta_space/").

---

### Post by skitzware on 2008-09-21
[[IMG]http://img404.imageshack.us/img404/1182/sshotfl6.th.png[/IMG]](http://img404.imageshack.us/my.php?image=sshotfl6.png)[[IMG]http://img404.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by SomeGuyDude on 2008-09-22
Mild changes.

GTK - Ubuntu Dust
Icons - Crashbit
Wallpaper - something off Interfacelift

---

### Post by BOBSONATOR on 2008-09-22
Yea, as you can see, i hopped on the fresh train.

im back to the minimal look for now :)

(most on gnome-look)
GTK: Fresh-Dark 
Icons: Gnome-Colors-Brave
Wallpaper: by j3concepts @ Deviant-art
fonts: Myriad Pro (great one!) and Monaco (great terminal!)

---

### Post by aschwerin.moses on 2008-09-22
> **Koori23 said:**
> I'm still liking my setup. 

elegant_dark_gray by UbuForum's own Herbster


XFCE Hardy, Icons HighContrastInverse, Font HandleGotD

I got the wallpaper from interfacelift
Can you please tell me the name of that music play..looks really nice

---

### Post by Daisuke_Aramaki on 2008-09-22
> **skitzware said:**
> [[IMG]http://img404.imageshack.us/img404/1182/sshotfl6.th.png[/IMG]](http://img404.imageshack.us/my.php?image=sshotfl6.png)[[IMG]http://img404.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

nice setup of flatwillow! :)

---

### Post by Daisuke_Aramaki on 2008-09-22
> **narf41 said:**
> my (x)ubuntu-09-screeny

[[img]http://ubuntu-pics.de/thumb/3463/s080921_0rR14B.png[/img]](http://ubuntu-pics.de/bild/3463/s080921_0rR14B.png)

xfce with gnome-panel and conky
i use a full-transparent xfce-panel on the right side, so maximized windows dont overlap the sidebar.
and i made a wallpaper changer with cron, so my xfce-background changes every 5 minutes, using the wp´s from the xfce-wallpaper-list at random.
gtk/emerald:"hyo", icons:"royal-preview"

love the hostname! :p

---

### Post by Koori23 on 2008-09-22
> **aschwerin.moses said:**
> Can you please tell me the name of that music play..looks really nice

Oh, all it is really is Totem or "Movie Player" with all the controls hidden.

In totem, ctrl + H hides the controls. If you go to Edit - Preferences Display tab.. Change that to monoscope using the dropdown box.. That's all.

---

### Post by narf41 on 2008-09-22
> **Daisuke_Aramaki said:**
> love the hostname! :p

pinky says "thx, NARF", i hope u like the desk too
(and the computername is "brauerei", =german for brewery hehe)

---

### Post by Daisuke_Aramaki on 2008-09-22
> **narf41 said:**
> pinky says "thx, NARF", i hope u like the desk too
(and the computername is "brauerei", =german for brewery hehe)

he he he! i live very close to the dinkelacker brauerei in stuttgart! :p the desk is cool too!

---

### Post by narf41 on 2008-09-22
> **Daisuke_Aramaki said:**
> he he he! i live very close to the dinkelacker brauerei in stuttgart! :p the desk is cool too!

und ich in dresden lol, radeberger bier

---

### Post by etnlIcarus on 2008-09-22
> **el mariachi said:**
> too bad there aren't that many themes like for metacity or emerald :(Honestly, if you can't create or port an Xfwm4 theme, I don't believe you're really trying. The only shortcoming of Xfwm is it's strictly pixmaps so any curved or diagonal highlights visible in themes for other WMs won't be able to be reproduced with xfwm.

---

### Post by boobuntu on 2008-09-22
**Details provided by OurDesktops.com**

I just reinstalled the latest version of Ubuntu and slapped this sweet wall up.  I'm not a huge fan of flaunting browser wallpapers but I love this particular FF one.
[[IMG]http://www.ourdesktops.com/desktops/thumb_medium/113fd130-a727-4fb5-9533-fde409ac7738_thumbmedium.jpg[/IMG]](http://www.ourdesktops.com/desktop_user.aspx?user=boobuntu)

---

### Post by OrangeCrate on 2008-09-22
Well, I keep trying dark themes, but when I open a white web page, it's like someone shining a flashlight in my eyes. So for work, something simple, and light in color...

Intrepid Ibex
MurrinaVerdeOlivo theme
Tango icons
XP blue background
Masao Ido woodblock print

---

### Post by SpenceMakesSense on 2008-09-22
> **Do Androids Dream? said:**
> Here's mine, first Ubuntu desktop.
Running on a Toshiba laptop and loving it !=D>

That is really frickin cool:D

---

### Post by Daisuke_Aramaki on 2008-09-22
Was in a mood for a dark desktop! so here it is! Details are in the terminal!
[CENTER]
[[IMG]http://img530.imageshack.us/img530/253/200809222018071680x1050ro5.th.png[/IMG]](http://img530.imageshack.us/my.php?image=200809222018071680x1050ro5.png)[[IMG]http://img530.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/CENTER]

---

### Post by Daisuke_Aramaki on 2008-09-22
here's the link for the Wall btw!

[http://rotane.deviantart.com/art/Jedi-vs-Sith-WP-pack-wide-20636679]("http://rotane.deviantart.com/art/Jedi-vs-Sith-WP-pack-wide-20636679")

---

### Post by tryorke on 2008-09-22
**Choppy Vid:** [http://www.youtube.com/watch?v=B5Cd_lNe9Hg](http://www.youtube.com/watch?v=B5Cd_lNe9Hg)
**Screenshot:** [http://bboxnet.no-ip.org/~tryorke/desktop-82208.png](http://bboxnet.no-ip.org/~tryorke/desktop-82208.png)

More or less a copy/paste from the video description:
* Compiz Fusion (Desktop Cube among others)
* Conky Scripts
* Shiki Human GTK2+ Theme
* Terminal Desktop (via Compiz)

I don't really like the whole "let's make my linux desktop look like the Mac OS X / Windows Vista" trend, so I tried to stay away from that.
- I edited the wallpaper (in GIMP) based on a couple images I downloaded from a wallpaper site.
- I combined the default top and bottom panels into the bottom panel by removing all the application launchers and shrinking the menu.
- The icons along the top are just app launchers on a simple transparent panel, no fancy widgets involved. AWN is just too OS X.
- The desktop is indeed a terminal screen; that's a combination of a custom gnome-terminal profile and some clever Compiz settings.
- The system display on the right is a self-written Conky script (Conky is a lightweight system monitor)
- The music display above the bottom panel is another self-written Conky script that interacts with mpd (Music Player Daemon)
- Normally I have Conky showing me my external IP address; I have a Sticky Note covering it for security purposes :)

---

### Post by andrek on 2008-09-22
**tryorke**, what's the font you're using in your terminal?

---

### Post by tryorke on 2008-09-22
System font is Segoe UI, and Terminal font is Consolas.
They're some of the system fonts for Windows Vista - I just happen to like them better than the Ubuntu Defaults.

Consolas is pretty tough to get ahold of; I had to download and cabextract a powerpoint viewer just to get at it.

---

### Post by elijathegold on 2008-09-22
Here are some screenshots from my lappy

[One showing Dock](http://img187.imageshack.us/my.php?image=dt1ob8.png)
[Two browsing the interweb](http://img362.imageshack.us/my.php?image=dt2wx9.png)
[Three editing source code](http://img90.imageshack.us/my.php?image=dt3oo4.png)

---

### Post by Daisuke_Aramaki on 2008-09-22
> **eightmillion said:**
> Here's a colour you don't see very often. Deep dark red. It has a kind of theatrical feel to it.

thats a great shot 8mil! gotta question tho! can u please pass on ur domino config?

---

### Post by perfectska04@hotmail.com on 2008-09-22
> **tryorke said:**
> 
More or less a copy/paste from the video description:
* Compiz Fusion (Desktop Cube among others)
* Conky Scripts
* Shiki Human GTK2+ Theme
* Terminal Desktop (via Compiz)


Wow. Just, wow. That looks incredibly functional and attractive. It's most definitely inspiring me to install conky and try out a similar configuration.

---

### Post by eightmillion on 2008-09-22
> **Daisuke_Aramaki said:**
> thats a great shot 8mil! gotta question tho! can u please pass on ur domino config?


Thanks. Here's my domino config.

---

### Post by Daisuke_Aramaki on 2008-09-22
> **eightmillion said:**
> Thanks. Here's my domino config.

fantastic mate! thanx!:) color scheme wud be great as well! sorry for the trouble again mate!

---

### Post by Daisuke_Aramaki on 2008-09-22
> **eightmillion said:**
> Thanks. Here's my domino config.

it says that the file is binary and corrupted mate! :(

---

### Post by jordanmthomas on 2008-09-22
> **Daisuke_Aramaki said:**
> it says that the file is binary and corrupted mate! :(

[COLOR="Silver"]You need to untar it:
```
tar xvf ~/Desktop/domino_oxygen_darkrc.tar
```[/COLOR]

 nevermind, it still seems a little messed up, sorry.

---

### Post by Daisuke_Aramaki on 2008-09-22
> **jordanmthomas said:**
> [COLOR="Silver"]You need to untar it:
```
tar xvf ~/Desktop/domino_oxygen_darkrc.tar
```[/COLOR]

 nevermind, it still seems a little messed up, sorry.

i was talkin about the config file then mate, not the archive! :)

---

### Post by eightmillion on 2008-09-22
> **Daisuke_Aramaki said:**
> it says that the file is binary and corrupted mate! :(

Yeah, you have to untar it first. I've attached the color scheme too. There's one for KDE 3 and KDE 4 included.

---

### Post by Daisuke_Aramaki on 2008-09-22
> **eightmillion said:**
> Yeah, you have to untar it first. I've attached the color scheme too. There's one for KDE 3 and KDE 4 included.

the color scheme is fine man! but the dominoconfig is corrupted, and of course i know that u need to untar it first.

---

### Post by eightmillion on 2008-09-22
> **Daisuke_Aramaki said:**
> the color scheme is fine man! but the dominoconfig is corrupted, and of course i know that u need to untar it first.

Looks like it is corrupted. This one should work.

---

### Post by Daisuke_Aramaki on 2008-09-22
> **eightmillion said:**
> Looks like it is corrupted. This one should work.

thanx 8mil! this one works! :)

---

### Post by What is in a name? on 2008-09-22
On today's revision of Eikon2:

[[IMG]http://b.imagehost.org/t/0825/ecra.jpg[/IMG]](http://b.imagehost.org/view/0825/ecra.png)

I decided to try out and develop this concept for the emblems that people more likely really use as badges. I also replaced some other icons. Perhaps more importantly, I moved around a bit the icons between folders, so I hope that AWN bug with the trash bin icon will finally be solved.

The complete icon set is available to be downloaded at the usual place: [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)
Today's revision (r20080923) is compressed in the tar.bz2 format, for size-related reasons. You may wish to backup and remove your current copy of Eikon from your ~/.icons folder before putting the new version there.

---

### Post by Daisuke_Aramaki on 2008-09-22
> **What is in a name? said:**
> On today's revision of Eikon2:

[[IMG]http://b.imagehost.org/t/0825/ecra.jpg[/IMG]](http://b.imagehost.org/view/0825/ecra.png)

I decided to try out and develop this concept for the emblems that people more likely really use as badges. I also replaced some other icons. Perhaps more importantly, I moved around a bit the icons between folders, so I hope that AWN bug with the trash bin icon will finally be solved.

The complete icon set is available to be downloaded at the usual place: [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)
Today's revision (r20080923) is compressed in the tar.bz2 format, for size-related reasons. You may wish to backup and remove your current copy of Eikon from your ~/.icons folder before putting the new version there.

another ace update mate! :) eikon is one of the best icon themes thats out there! :guitar: btw r u planning to post some kde themes? loved ur passion red theme!:)

---

### Post by What is in a name? on 2008-09-22
> **Daisuke_Aramaki said:**
> another ace update mate! :) eikon is one of the best icon themes thats out there! :guitar: btw r u planning to post some kde themes? loved ur passion red theme!:)

I might eventually create new KDE themes, but it's more likely that I will do that with KDE4 (since it's supposed to slowly replace KDE3). I don't know that much about what are the available options in the Oxygen style. I know Domino was and is very customizable, so I hope something at least similar will be possible with KDE4. Overally speaking, it's a very promising desktop environment in what concerns it's look and feel.

And... Thanks for the compliments too!

---

### Post by Daisuke_Aramaki on 2008-09-22
> **What is in a name? said:**
> I might eventually create new KDE themes, but it's more likely that I will do that with KDE4 (since it's supposed to slowly replace KDE3). I don't know that much about what are the available options in the Oxygen style. I know Domino was and is very customizable, so I hope something at least similar will be possible with KDE4. Overally speaking, it's a very promising desktop environment in what concerns it's look and feel.

And... Thanks for the compliments too!

ur rite! i alternate between kde 3.5.10 and 4.1 all the time. but somehow feel more accustomed to 3.5 due to uniformity and less breaking up! i hope 4.1 eventually grwos into something that is truly crash free. ad yeah, the theming for 4.1 is still at its infancy. xcept for bespin and skulpture there are not many themes, but i just hope somehow domino might get a facelift and gets ported to 4.1. dekorator is already available for 4.1 so domino shudn't be far behind, just my hope!:)

---

### Post by SomeGuyDude on 2008-09-22
That icon set is pretty excellent. Flows fantastically with the MurrineGlow Brave theme.

Not feeling this "Fresh" theme, though. Fat scrollbar, bold menu font for some reason, the metacity feels awkward.

---

### Post by mrgnash on 2008-09-22
> **What is in a name? said:**
> On today's revision of Eikon2:

[[IMG]http://b.imagehost.org/t/0825/ecra.jpg[/IMG]](http://b.imagehost.org/view/0825/ecra.png)

I decided to try out and develop this concept for the emblems that people more likely really use as badges. I also replaced some other icons. Perhaps more importantly, I moved around a bit the icons between folders, so I hope that AWN bug with the trash bin icon will finally be solved.

The complete icon set is available to be downloaded at the usual place: [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)
Today's revision (r20080923) is compressed in the tar.bz2 format, for size-related reasons. You may wish to backup and remove your current copy of Eikon from your ~/.icons folder before putting the new version there.

The emblems/badges look great.

---

### Post by skitzware on 2008-09-22
[[IMG]http://img223.imageshack.us/img223/9996/sshotiw2.th.png[/IMG]](http://img223.imageshack.us/my.php?image=sshotiw2.png)[[IMG]http://img223.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Thought I'd port another theme for fluxbox...

---

### Post by What is in a name? on 2008-09-22
> **SomeGuyDude said:**
> That icon set is pretty excellent. Flows fantastically with the MurrineGlow Brave theme.

Not feeling this "Fresh" theme, though. Fat scrollbar, bold menu font for some reason, the metacity feels awkward.

Really, thanks a **lot** for the compliments.

I'm not the original author of Fresh2.0, though. In case you're really referring to the mod I'm using on my screenshots, I'm sorry. If not, well... I apologise for the unnecessary comment, anyway. :p

EDIT: BTW, nice avatar. I also love René Magritte.

---

### Post by dlm4849 on 2008-09-22
Here's mine

- slightly modified Eikon for Icons
- some background off of interfacelift.com
- shiki-brave for metacity/gtk theme
- CG for mouse
- stalonetray for sys tray at bottom left
- and of course conky at the top

---

### Post by Mr.Crowley on 2008-09-23
Finally got around to changing mine.

[[IMG]http://b.imagehost.org/t/0134/2008-09-22-232241_1280x1024_scrot.jpg[/IMG]](http://b.imagehost.org/view/0134/2008-09-22-232241_1280x1024_scrot.png)

---

### Post by BOBSONATOR on 2008-09-23
> **skitzware said:**
> [[IMG]http://img223.imageshack.us/img223/9996/sshotiw2.th.png[/IMG]](http://img223.imageshack.us/my.php?image=sshotiw2.png)[[IMG]http://img223.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Thought I'd port another theme for fluxbox...

Nice flux setup!

two problems though, fonts are too small, and arsenal > chelski :P

---

### Post by p_quarles on 2008-09-23
Just for fun: Konqueror running in Windows XP sp2 via X forwarding.

---

### Post by SomeGuyDude on 2008-09-23
> **What is in a name? said:**
> Really, thanks a **lot** for the compliments.

I'm not the original author of Fresh2.0, though. In case you're really referring to the mod I'm using on my screenshots, I'm sorry. If not, well... I apologise for the unnecessary comment, anyway. :p

EDIT: BTW, nice avatar. I also love René Magritte.

No prob! I wasn't sure if you were or not, I remember you'd made a few already and it struck me as possible. I also notice that a lot of people were hopping on the bandwagon (much as they did with Shiki-Colors and ClearGlow before that), but I just don't get it. Seems like a Frankenstein theme to me: pluck an emerald theme here, a scrollbar there...

Thank ya sir. Best self-portrait of all time. :KS

---

### Post by TheSlipstream on 2008-09-23
Hey, What's in a name?

I love Eikon a lot, it's brilliant, but the only thing that bothers me is when I use Firefox, the close button on the tabs are red circles. I think a better choice would be an X, just for the sake of tradition. 

Keep up the great work though, you've done huge things for the theming scene in Linux, and brought many different flavours we wouldn't have gotten otherwise. 

Cheers!

---

### Post by Mos_Barbuta on 2008-09-23
...bought a new laptop...installed ubuntu
so, for history's sake, here is my gnome desktop for the few hours before I set up openbox and pekwm, in all their desktop-right-clicking glory

Clearlooks human dark with meliae icons
I don't remember where I got the wallpaper, it's a photo of a Ganesha statue

[[IMG]http://img26.picoodle.com/data/img26/3/9/22/t_230908cleanm_9ffe7f5.png[/IMG]](http://www.picoodle.com/view.php?img=/3/9/22/f_230908cleanm_9ffe7f5.png&srv=img26)

[[IMG]http://img29.picoodle.com/data/img29/3/9/22/t_230908dirtym_832913a.png[/IMG]](http://www.picoodle.com/view.php?img=/3/9/22/f_230908dirtym_832913a.png&srv=img29)

---

### Post by pt123 on 2008-09-23
> **What is in a name? said:**
> On today's revision of Eikon2:


Nice set but I notice many themes including this are never able to change the ugly icons of Rhythmbox. 

i.e. the Shuffle, Repeat and Broswe ( most ugliest Icon)

---

### Post by skitzware on 2008-09-23
[[IMG]http://img221.imageshack.us/img221/8849/sshot3ic0.th.png[/IMG]](http://img221.imageshack.us/my.php?image=sshot3ic0.png)[[IMG]http://img221.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Made my own theme for fluxbox.. may release it if i get enough interest in it... oh and by the way? bobsonator? chelski? I was into chels long before any russian was... I remember the bad times in the old second div... playing scunthope away.. heh

---

### Post by Piraja on 2008-09-23
Rather basic Gnome Ubuntu, except for the great ibex photo I found and gimped for my Intrepid desktop, courtesy of Ian Spare (see his blog [SnowSlider]("http://snowslider.net/2008/06/05/zinal-cabane-du-petit-mountet-2/") for even more gorgeous ibex pictures).

[[IMG]http://www.aijaa.com/img/t/00521/2784069.t.png[/IMG]](http://www.aijaa.com/v.php?i=2784069.png)

Below's the plain background. The colour I used for Gimp's "Colourify" function is the Ubuntu "default yellow", #ffb515:

[[IMG]http://www.aijaa.com/img/t/00445/2783968.t.jpg[/IMG]](http://www.aijaa.com/v.php?i=2783968.jpg)

Thanks to Ian for sharing the photo!

P.S. Later I [updated]("http://www.aijaa.com/v.php?i=2800847.png") the panels a little bit.

---

### Post by SirBismuth on 2008-09-23
My work desktop attached!

Shortcut is there because I need to use it so friggin' much! :D

Only thing that isn't really running is VirtualBox, must get my XP .vdi up and running, and then will be able to can Windoze entirely!. 

B

---

### Post by boobuntu on 2008-09-23
> **Piraja said:**
> Rather basic Gnome Ubuntu, except for the great ibex photo I found and gimped for my Intrepid desktop, courtesy of Ian Spare (see his blog [SnowSlider]("http://snowslider.net/2008/06/05/zinal-cabane-du-petit-mountet-2/") for even more gorgeous ibex pictures).

[[IMG]http://www.aijaa.com/img/t/00521/2784069.t.png[/IMG]](http://www.aijaa.com/v.php?i=2784069.png)

Below's the plain background. The colour is the Ubuntu "default yellow", #fb515:

[[IMG]http://www.aijaa.com/img/t/00445/2783968.t.jpg[/IMG]](http://www.aijaa.com/v.php?i=2783968.jpg)

Thanks to Ian for sharing the photo!

That desktop is a bit scary for my taste :P

---

### Post by karth on 2008-09-23
> **mccord said:**
> [[img]http://i33.tinypic.com/hrbms4.png[/img]]("http://i35.tinypic.com/9to3l3.png")

openbox (mire_v2_orange theme)
tint2
trayer
conky

I actually like this a lot. Would you mind if I asked you where you found the background picture, your conky setup, and your tint setup?

---

### Post by Piraja on 2008-09-23
> **boobuntu said:**
> That desktop is a bit scary for my taste :P

Oh well... How 'bout a monster firefox burning up the globe... Talkin' 'bout scary, huh?

> [Check out my current desktop!]("http://www.ourdesktops.com/desktop_user.aspx?user=boobuntu")

To be serious, your wallpaper's very impressive.

---

### Post by boobuntu on 2008-09-23
> **Piraja said:**
> Oh well... How 'bout a monster firefox burning up the globe... Talkin' 'bout scary, huh?



To be serious, your wallpaper's very impressive.

Haha.  Thanks, yeah I usually don't care for the 'show off your browser' type wallpapers but that one stuck out to me.

---

### Post by Perfect Storm on 2008-09-23
> **SirBismuth said:**
> My work desktop attached!

Shortcut is there because I need to use it so friggin' much! :D

Only thing that isn't really running is VirtualBox, must get my XP .vdi up and running, and then will be able to can Windoze entirely!. 

B

Wallpaper?

---

### Post by clipse on 2008-09-23
Here is mine. I'm pretty happy with it for now. I'll probably change it soon either way though. :D

---

### Post by Daisuke_Aramaki on 2008-09-23
> **karth said:**
> I actually like this a lot. Would you mind if I asked you where you found the background picture, your conky setup, and your tint setup?

concur with Karth! the wall luks impressive! :)

---

### Post by mccord on 2008-09-23
> **karth said:**
> I actually like this a lot. Would you mind if I asked you where you found the background picture, your conky setup, and your tint setup?
i don't mind at all :)

[http://dotfiles.org/~mccord/.conkyrc](http://dotfiles.org/~mccord/.conkyrc)
[http://dotfiles.org/~mccord/tintrc](http://dotfiles.org/~mccord/tintrc)
wallpaper: [http://stilleswasser.deviantart.com/art/black-fairy-wallpaper-II-88942940](http://stilleswasser.deviantart.com/art/black-fairy-wallpaper-II-88942940) 
it's 4:3 aspect ratio though, so you have to crop & scale or better use the [liquidrescale addon]("http://liquidrescale.wikidot.com/") in gimp to get it to a widescreen ratio

i quite like her style, this wallpaper is pretty cool too: [http://stilleswasser.deviantart.com/art/weird-wallpaper-version-64862052](http://stilleswasser.deviantart.com/art/weird-wallpaper-version-64862052)

found her wallpapers through [http://pixelgirlpresents.com/](http://pixelgirlpresents.com/) :)

---

### Post by What is in a name? on 2008-09-23
> **TheSlipstream said:**
> Hey, What's in a name?

I love Eikon a lot, it's brilliant, but the only thing that bothers me is when I use Firefox, the close button on the tabs are red circles. I think a better choice would be an X, just for the sake of tradition. 

Keep up the great work though, you've done huge things for the theming scene in Linux, and brought many different flavours we wouldn't have gotten otherwise. 

Cheers!

> **pt123 said:**
> Nice set but I notice many themes including this are never able to change the ugly icons of Rhythmbox. 

i.e. the Shuffle, Repeat and Broswe ( most ugliest Icon)

How's this for an improvement?

[[IMG]http://b.imagehost.org/t/0485/ecra.jpg[/IMG]](http://b.imagehost.org/view/0485/ecra.png)

---

### Post by Iceni on 2008-09-23
Running latest 8.10 build, Tilda, Gnome-Do and small conky config. After using only Do for the last month or so I removed the standard menu, just wasn't using it anymore.

Wallpaper from dektopography.

---

### Post by Daisuke_Aramaki on 2008-09-23
> **What is in a name? said:**
> How's this for an improvement?

[[IMG]http://b.imagehost.org/t/0485/ecra.jpg[/IMG]](http://b.imagehost.org/view/0485/ecra.png)

holy "insert xpletive" thats impressive man! :)

---

### Post by Daisuke_Aramaki on 2008-09-23
My Current Setup:

KDE3.5.10. Style - Domino. Icons - Snowish for KDE. App Font - HandelgotD Light. Terminal Font - Lucida Console. WP - Flora Nine

[CENTER][[IMG]http://img66.imageshack.us/img66/6181/200809231841071680x1050aq9.th.png[/IMG]](http://img66.imageshack.us/my.php?image=200809231841071680x1050aq9.png)[[IMG]http://img66.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/CENTER]

---

### Post by etnlIcarus on 2008-09-23
Not a major update by any means. I've warmed to WIIAN?'s Eikon suite, though I'd still prefer non-diagonal angled folder icons. I know he's included some alt folders in the icon set, I'm just yet to get around to checking them out.

[url=http://img140.imageshack.us/img140/6898/screenuu8.jpg][img]http://img255.imageshack.us/img255/3714/screensas8.jpg[/img]
http://img140.imageshack.us/img140/6898/screenuu8.jpg[/url]

---

### Post by Mark76 on 2008-09-23
Some minor tweaks to Tint

---

### Post by aschwerin.moses on 2008-09-23
My Desktop... Let me know if i can improve it..

---

### Post by Mark76 on 2008-09-23
Maybe make it bigger?

Just saying.

---

### Post by etnlIcarus on 2008-09-23
I'd also take two of those panels and scrap them.

---

### Post by aschwerin.moses on 2008-09-23
Why is the attachment so small.. any ways.. here the bigger one.. let me know how to make it better...

---

### Post by Mark76 on 2008-09-23
Yeah. You need less panels.

The new attachment is much better. :)

---

### Post by Electric Bill on 2008-09-23
One of my photos, awn-manager, custom theme.
 
Click pic to see full size.
 
[[IMG]http://newportyachtdirectory.com/Ubuntu_Forums/Sept_Desktop-sm.jpg[/IMG]]("http://newportyachtdirectory.com/Ubuntu_Forums/Sept_Desktop.jpg")
 
Bill

---

### Post by Mark76 on 2008-09-23
Do you know a Magnetic Tom?

That's a real person's name, by the way.

---

### Post by herbster on 2008-09-23
[[IMG]http://i36.tinypic.com/10e0i2w.jpg[/IMG]](http://herbster.deviantart.com/art/Desktop-09-23-08-98783801)

---

### Post by Giant Speck on 2008-09-23
> **aschwerin.moses said:**
> Why is the attachment so small.. any ways.. here the bigger one.. let me know how to make it better...

I love what you did at the bottom of the screen with the two panels.

---

### Post by SomeGuyDude on 2008-09-23
> **What is in a name? said:**
> How's this for an improvement?

[[IMG]http://b.imagehost.org/t/0485/ecra.jpg[/IMG]](http://b.imagehost.org/view/0485/ecra.png)

The GTK looks like Fresh, but the scrollbars are a lot nicer. What's the mod?

I swear there's been a rash of excellent GTK/icon themes in the past few weeks, I'd been using TheRob's various black&white themes for about 7 months and now I'm actually putting color in there. :guitar:

---

### Post by What is in a name? on 2008-09-23
> **SomeGuyDude said:**
> The GTK looks like Fresh, but the scrollbars are a lot nicer. What's the mod?

I swear there's been a rash of excellent GTK/icon themes in the past few weeks, I'd been using TheRob's various black&white themes for about 7 months and now I'm actually putting color in there. :guitar:

Well, that is actually a modification of Fresh I made for personal use. I ported it entirely to the SVN version of the Murrine engine (instead of the Clearlooks and Aurora elements of the original theme) and I used a warmer colour for the highlights.

Since you're asking, I decided to upload that theme to my Drop.io account (it's been such a valuable Swiss knife, I'm so thankful to whoever suggested Drop.io to me), so you can grab it at [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)

Enjoy!

---

### Post by SomeGuyDude on 2008-09-23
Sexcellent, here's my setup now. Three comments, though, all of which involve the icons:

[LIST=1]
[*]That red button is just odd. Seems to represent quit/shutdown. What's up?
[*]Any way to make folder icons for home/downloads/images/etc?
[*]Not huge on the colored media controls, but that's pretty minor and it's just me.
[/LIST]

---

### Post by What is in a name? on 2008-09-23
> **SomeGuyDude said:**
> Sexcellent, here's my setup now. Three comments, though, all of which involve the icons:

[LIST=1]
[*]That red button is just odd. Seems to represent quit/shutdown. What's up?
[*]Any way to make folder icons for home/downloads/images/etc?
[*]Not huge on the colored media controls, but that's pretty minor and it's just me.
[/LIST]

1. Which red button? The "close" one, for tabs and panes and all? If so, I noticed that your screenshot still features the old round red button Eikon used to have until... This afternoon. I tried a different solution after someone said it did look odd (was it you? I don't remember at the moment). Have you downloaded that update yet? I know it's a very recent update, so it's likely most people didn't notice it yet.

2. As for the folder icons, I personally just use emblems for them, when under Xfce (for GNOME, read below), but I have been noticing that some icon themes feature some folder icons named like "folder-downloads.png", "folder-images", "folder-music". Now, does GNOME automatically apply those icons after detecting the name of the different folders, or are those icons there only for the user to manually apply them as he wishes? Anyway, I might create that kind of icons soon. In my PC, when I'm using GNOME, I just use some of Eikon's emblems as folder icons (using the first tab of the Properties dialog, you know).

3. Considering the amount of things I have already changed from Eikon to Eikon2, it's likely I will eventually get fed up with the media control icons myself, in the future. :p

---

### Post by jakonj on 2008-09-23
wm: openbox
openbox theme: arch blue
gtk2- murrine s (i edited murrine x theme)
font- Clean font (Cool font from artwiz package ([http://www.google.com/search?q=artwiz+fonts](http://www.google.com/search?q=artwiz+fonts))
terminal is tilda.
icons: Tango (the one from ubuntu repos)

p.s. My power is great :) (i got inspiration from my last dnd session :) )

---

### Post by SomeGuyDude on 2008-09-23
> **What is in a name? said:**
> 1. Which red button? The "close" one, for tabs and panes and all? If so, I noticed that your screenshot still features the old round red button Eikon used to have until... This afternoon. I tried a different solution after someone said it did look odd (was it you? I don't remember at the moment). Have you downloaded that update yet? I know it's a very recent update, so it's likely most people didn't notice it yet.

2. As for the folder icons, I personally just use emblems for them, when under Xfce (for GNOME, read below), but I have been noticing that some icon themes feature some folder icons named like "folder-downloads.png", "folder-images", "folder-music". Now, does GNOME automatically apply those icons after detecting the name of the different folders, or are those icons there only for the user to manually apply them as he wishes? Anyway, I might create that kind of icons soon. In my PC, when I'm using GNOME, I just use some of Eikon's emblems as folder icons (using the first tab of the Properties dialog, you know).

3. Considering the amount of things I have already changed from Eikon to Eikon2, it's likely I will eventually get fed up with the media control icons myself, in the future. :p

1) As it turns out, AWN somehow doesn't catch on that it should use the quit/logout button. I just popped it on there and it's the blue down-arrow now. Although the new X is nice!

2) You have to manually set the folder icons; Oxygen-Refit has a pretty nice set, as does the fork Hydroxygen. I think they look nicer than emblems since they're not in a corner, but I can see how it'd be annoying to add another set of icons to a package. Still, it's what keeps me from being totally satisfied with Gnome-Colors and Crashbit.

3) Every change has been a welcome improvement, so I look forward to future versions! Bookmarked your depot for themes, gonna keep an eye on 'em. 


Another thing: what tools do you use for making GTK/metacity themes? That's something I'd like to fiddle with, but never seen a usable guide.

---

### Post by TheSlipstream on 2008-09-23
> **etnlIcarus said:**
> Not a major update by any means. I've warmed to WIIAN?'s Eikon suite, though I'd still prefer non-diagonal angled folder icons. I know he's included some alt folders in the icon set, I'm just yet to get around to checking them out.

Love it. Beautiful. :)

I don't suppose you could share your conkyrc? I've been wondering how to get those little status bars.

> **What is in a name? said:**
> How's this for an improvement?

It's excellent. I'll get the new one as soon as my laziness goes below critical mass. :P

---

### Post by What is in a name? on 2008-09-23
> **SomeGuyDude said:**
> 
Another thing: what tools do you use for making GTK/metacity themes? That's something I'd like to fiddle with, but never seen a usable guide.

Well, I don't use anything special besides Gedit, that is... I just dive into the code and start tweaking. Of course it takes time. There are still a lot of options I don't know how to work with, but nonetheless I try to learn from what I observe in other themes. One hint, though: the new Murrine engine is just wonderful. As soon as the author gets rid of the "ant trail"-like border around the highlighted buttons, it will be nearly perfect. I used to be a great fan of Aurora, but nowadays I don't use anything but Murrine. My taste also changed a lot these last few months (even weeks).

Oh, well, I almost forgot, installing **The Widget Factory** is always helpful. It's an app that does previews of GTK themes. It shows several fake widgets, like check-boxes, scrollbars, menus, buttons, tabs and all that, and then it applies a certain theme to those widgets in order to let us know how will it look on a real application. So it's something you might want to run along with your preferred text editor, to test your theme each time you save some new detail in the code.

Metacity themes always puzzled me. I know that it's supposed to be logical and all that, considering they're just XML files, but I always give up when I take a look at the code. In fact, I only made about 2 or 3 themes during my short "career" as a themer. And they were awfully based on already existing themes as well. It's one of my greatest weaknesses, as I once stated.

---

### Post by isaacj87 on 2008-09-23
My current deskie as of 09/23/2008

---

### Post by pt123 on 2008-09-23
> **What is in a name? said:**
> How's this for an improvement?

[[IMG]http://b.imagehost.org/t/0485/ecra.jpg[/IMG]](http://b.imagehost.org/view/0485/ecra.png)

Wow that is beautiful, so if I get the latest RC of Eikon: 
eikon2-rc3-r20080923b.tar.bz2  
from [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)

would it look like that.

Thanks

---

### Post by What is in a name? on 2008-09-23
> **pt123 said:**
> Wow that is beautiful, so if I get the latest RC of Eikon: 
eikon2-rc3-r20080923b.tar.bz2  
from [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)

would it look like that.

Thanks

That is correct. :)

---

### Post by aschwerin.moses on 2008-09-24
> **Giant Speck said:**
> I love what you did at the bottom of the screen with the two panels.
Thank you.. good u liked it.. infact im trying it look like HP's Touchsmart UI

---

### Post by skitzware on 2008-09-24
[[IMG]http://img211.imageshack.us/img211/2576/screenshotvp6.th.png[/IMG]](http://img211.imageshack.us/my.php?image=screenshotvp6.png)[[IMG]http://img211.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Thought I'd get away from fluxbox for a while...

---

### Post by ayoli on 2008-09-24
> **skitzware said:**
> [[IMG]http://img211.imageshack.us/img211/2576/screenshotvp6.th.png[/IMG]](http://img211.imageshack.us/my.php?image=screenshotvp6.png)[[IMG]http://img211.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Thought I'd get away from fluxbox for a while...

Nice one, would you mind sharing some infos about it (theme, wall, icons, ...) ?

---

### Post by eightmillion on 2008-09-24
I've been hacking together this plasmoid...

---

### Post by Daisuke_Aramaki on 2008-09-24
This time its Gnome!

Theme Details in Terminal
[CENTER]
[[IMG]http://img140.imageshack.us/img140/9414/200809241220541680x1050lx9.th.jpg[/IMG]](http://img140.imageshack.us/my.php?image=200809241220541680x1050lx9.jpg)[[IMG]http://img140.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/CENTER]

---

### Post by vishzilla on 2008-09-24
GTK: Kin Tonic
Icons: Tangerine

[[IMG]http://www.ourdesktops.com/desktops/thumb_medium/04433fa2-8d95-48ea-a3ca-f89dbec5eae4_thumbmedium.jpg[/IMG]](http://www.ourdesktops.com/desktop_user.aspx?user=vishal)

---

### Post by Isaac_x on 2008-09-24
[[IMG]http://img530.imageshack.us/img530/7010/previewza6.png[/IMG]]("http://img213.imageshack.us/img213/5053/200809241501281360x768skq0.png")
GTK: glossy
Metacity: Unity
Icons: AER-OS-XK with Nimbus as fallback for missing icons
Wallpaper: [Wikimedia]("http://commons.wikimedia.org/wiki/Image:Copper_Beech_Fagus_sylvatica_f._purpurea_Autumn_Leaves_3008px.jpg")

The large fonts are used for readability at five to ten feet on a 32" monitor.

---

### Post by Opeth115 on 2008-09-24
> **isaacj87 said:**
> My current deskie as of 09/23/2008

is that awn? and if so how did you change the indicators?

---

### Post by skitzware on 2008-09-24
> 
Quote:
Originally Posted by skitzware

Thought I'd get away from fluxbox for a while...
Nice one, would you mind sharing some infos about it (theme, wall, icons, ...) ?

Emerald theme is Ion by fratrip | fratrip.deviantart.com
GTK theme is Alpha by fratrip | fratrip.deviantart.com
Wall is from the SONA pack @ deviantart.com
Icons are from [http://www.4impressions.net](http://www.4impressions.net)

& I've been messing about with the gnome panel too...

[[IMG]http://img294.imageshack.us/img294/861/screenshotag2.th.png[/IMG]](http://img294.imageshack.us/my.php?image=screenshotag2.png)[[IMG]http://img294.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by billgoldberg on 2008-09-24
Details available on request (pm me).

---

### Post by isaacj87 on 2008-09-24
> **Opeth115 said:**
> is that awn? and if so how did you change the indicators?

Yup. It's AWN. In order to achieve the look you'll have to compile from [this]("https://code.launchpad.net/~meek./awn/bar-customization") branch and follow [these]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=18&page=6&isLive=true#23961") instructions.

---

### Post by Opeth115 on 2008-09-24
> **isaacj87 said:**
> Yup. It's AWN. In order to achieve the look you'll have to compile from [this]("https://code.launchpad.net/~meek./awn/bar-customization") branch and follow [these]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=18&page=6&isLive=true#23961") instructions.

where is the actual source on there, so i can compile it.  I can't seem to find it lol

---

### Post by gogadan on 2008-09-24
this is mine i hope you all like it :)

---

### Post by vishzilla on 2008-09-24
> **isaacj87 said:**
> My current deskie as of 09/23/2008
share info on that GTK and font plz?

---

### Post by ayoli on 2008-09-24
Found a wall suitable for this new autumn season, other infos in the screenshot.
[[IMG]http://ayozone.org/wp-content/gallery/screenshots-september-2008/thumbs/thumbs_24092008.png[/IMG]]("http://ayozone.org/gallery/screenshots-september-2008")

---

### Post by Tuning_In on 2008-09-24
Here is mine. Simple but pleasing:)

It's based on the Intuition theme. Gtk, metacity, wall etc can be found [here]("http://www.gnome-look.org/content/show.php/Intuition?content=84386")
Icons are Mac4lin.

Enjoy!

---

### Post by walkerk on 2008-09-24
Openbox

OB: Breathe Green (slightly modified)
GTK: Breathe Green
Wall: Afternoon Shadows (interfacelift.com)
Icons: nuoveXT2.2

---

### Post by Daisuke_Aramaki on 2008-09-24
> **isaacj87 said:**
> My current deskie as of 09/23/2008

post the details please! and the wall too!

---

### Post by Bart_D on 2008-09-24
> **walkerk said:**
> Openbox

OB: Breathe Green (slightly modified)
GTK: Breathe Green
Wall: Afternoon Shadows (interfacelift.com)
Icons: nuoveXT2.2

What font are you using?

---

### Post by Giant Speck on 2008-09-24
> **Isaac_x said:**
> [[IMG]http://img530.imageshack.us/img530/7010/previewza6.png[/IMG]]("http://img213.imageshack.us/img213/5053/200809241501281360x768skq0.png")
GTK: glossy
Metacity: Unity
Icons: AER-OS-XK with Nimbus as fallback for missing icons
Wallpaper: [Wikimedia]("http://commons.wikimedia.org/wiki/Image:Copper_Beech_Fagus_sylvatica_f._purpurea_Autumn_Leaves_3008px.jpg")

The large fonts are used for readability at five to ten feet on a 32" monitor.

I really like that Metacity.  It reminds me of a boxy version of Windows Vista Basic (sans the Aero effects).

---

### Post by boobuntu on 2008-09-24
> **gogadan said:**
> this is mine i hope you all like it :)

What the heck is that cube deal about?  Sorry, I'm new... looks freaking amazing.  Hard to setup?

---

### Post by Daisuke_Aramaki on 2008-09-24
Nothin special here! 

[CENTER][[IMG]http://img20.imageshack.us/img20/5143/200809250152361280x1024se9.th.png[/IMG]](http://img20.imageshack.us/my.php?image=200809250152361280x1024se9.png)[[IMG]http://img20.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/CENTER]

---

### Post by voteforpedro36 on 2008-09-24
[[img]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-24-08-bare.png[/img]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-24-08-bare.png)

[[img]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-24-08-media.png[/img]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-24-08-media.png)

---

### Post by eightmillion on 2008-09-24
> **voteforpedro36 said:**
> [[img]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-24-08-bare.png[/img]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-24-08-bare.png)

[[img]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-24-08-media.png[/img]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-24-08-media.png)

You mind sharing that wallpaper?

---

### Post by Yes on 2008-09-24
> **Daisuke_Aramaki said:**
> Nothin special here! 

[CENTER][[IMG]http://img20.imageshack.us/img20/5143/200809250152361280x1024se9.th.png[/IMG]](http://img20.imageshack.us/my.php?image=200809250152361280x1024se9.png)[[IMG]http://img20.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/CENTER]

Nice, can I get your .bashrc?

Mine...

[[IMG]http://b.imagehost.org/t/0091/9_24_08_1.jpg[/IMG]](http://b.imagehost.org/view/0091/9_24_08_1.png) [[IMG]http://b.imagehost.org/t/0141/9_24_08_2.jpg[/IMG]](http://b.imagehost.org/view/0141/9_24_08_2.png)

Very nice icons, What's in a Name?

---

### Post by myusername on 2008-09-24
> **voteforpedro36 said:**
> [[img]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-24-08-bare.png[/img]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-24-08-bare.png)

[[img]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-24-08-media.png[/img]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-24-08-media.png)

it may be pink. but its beautiful.
could i get some info?

---

### Post by nbock01 on 2008-09-25
Just installed Ubuntun on my Dell Dimension 8300

Quick spec list:

P4 3.0
2gb RAM
120 GB SATA, 750 GB SATA, 160 GB ATA, 80 GB ATA
nVidia 7600 GS 512mb
Creative Audigy 2

Works great!

---

### Post by cobra741 on 2008-09-25
Here's my September theme & wallpaper :)

---

### Post by Giant Speck on 2008-09-25
I wanted to show the current progress with my desktop.

The icons on the desktop I made by myself (and oddly enough remind me of the TNT logo).  :)  The KDE style is Serenity, and the Emerald theme is of my own creation called Elegant Glow, which is a mod of Darklight.

The font, of course, is Calibri 9 Bold.

The dock on the side is Cairo-dock, which by the way, I have a question for.  How do you give Cairo-dock a soft glow around the edge?  I tried to apply the drop shadow effects from Compiz onto it and it didn't work.

---

### Post by SomeGuyDude on 2008-09-25
Only font changes and a minor conky tweak, but man does it feel nicer. I removed the download speed from my Conky because I realized I almost never look there. For the most part all the info I need is CPU usage, memory, the date, temperature, battery, and network connection. I'd like to add more, but I dunno what else I really need to know.

GTK: WiaN's Fresh2.0 mod
AWN: Liquid-Glas Black
Icons: Eikon
Wallpaper: Something off Interfacelift
Desktop fonts: UnDotum
Conky font: Andrew, from DaFont.com

The Timeless font was really pretty, but absolutely IMPOSSIBLE to read. This works a hell of a lot better.

---

### Post by walkerk on 2008-09-25
> **Bart_D said:**
> What font are you using?

Tahoma

---

### Post by ayoli on 2008-09-25
Another recent screenshots website : [http://www.linuxshot.org/](http://www.linuxshot.org/)

---

### Post by vishzilla on 2008-09-25
> **ayoli said:**
> Another recent screenshots website : [http://www.linuxshot.org/](http://www.linuxshot.org/)
those screens from fergo are weird and amazing

---

### Post by ayoli on 2008-09-25
> **vishzilla said:**
> those screens from fergo are weird and amazing
yeah, it also looks like he's almost the only poster, so we may post some screenies there. I did :)

---

### Post by vishzilla on 2008-09-25
> **ayoli said:**
> yeah, it also looks like he's almost the only poster, so we may post some screenies there. I did :)

as per the footer there were only 3 people online on that website! :D

---

### Post by etnlIcarus on 2008-09-25
Hell, it looks like the only people using ourdesktops.com are all users of this forum as well.

---

### Post by uberdonkey5 on 2008-09-25
how do I delete duplicate posts? sorry!

---

### Post by uberdonkey5 on 2008-09-25
nothing special here I am afraid... I just like to keep it clean & simple. Metacity pilgrim and wallpaper from gnome-art site. Transparency on the side bars

---

### Post by PocketDog on 2008-09-25
[[IMG]http://img219.imageshack.us/img219/8614/screenshotdesktopoe1.th.png[/IMG]](http://img219.imageshack.us/img219/8614/screenshotdesktopoe1.png)[[IMG]http://img219.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Mac4Lin theme, slightly edited 'Shake_Your_Booty' wallpaper (wrong original aspect ratio for widescreen). Also, I've since deleted one of the two weather gadgets, I didn't notice those :lol:

---

### Post by Daisuke_Aramaki on 2008-09-25
> **eightmillion said:**
> You mind sharing that wallpaper?

hope he doesn't mind!

here's the link for the wall!

[http://skm-industries.deviantart.com/art/Light-Combustion-RELEASE-59431465]("http://skm-industries.deviantart.com/art/Light-Combustion-RELEASE-59431465")

---

### Post by mp3_freak_721 on 2008-09-25
> **Mark76 said:**
> Some minor tweaks to Tint

Are you using trayer as your system tray? If so, how did you make it look like that?

---

### Post by Mark76 on 2008-09-25
I have to go out soon. So I will tell you later.

---

### Post by Mark76 on 2008-09-25
Okay. I'll do it now

Paste this into your startup file and alter as desired

trayer --edge bottom --align right --widthtype request --heighttype request --transparent true  --alpha 255 --SetDockType false --margin 1 --distance 1 --SetPartialStrut true &

---

### Post by isaacj87 on 2008-09-25
> **Opeth115 said:**
> where is the actual source on there, so i can compile it.  I can't seem to find it lol

Hey, there's a line that indicates the command to checkout the branch (using BZR). Make sure you have all the necessary deps installed and do this to check out the developmental code:

```
bzr branch lp:~meek./awn/bar-customization
```

As requested, here are the details on my deskie:

Theme: Glow Sand Dark (slightly modified to make the icons larger)
Cursor: Gruppled
Iconset: Mostly Clearlooks OSX, but it's a custom pack I threw together
Wallpaper: Can be found [here]("http://img2.socwall.com/Abstract/General/200819021754-6253.jpg")
Dock: modified AWN

Also running CF 0.7.9

---

### Post by markp1989 on 2008-09-25
my white eee,

os: 32bit hardy
WM: openbox
obtheme: onyx-black
gtk-theme: Clearlooks flat compact
icons: Allblack
dock: fbpanel
network manager: Wicd
battery applet: still looking for one
wallpaper: none

---

### Post by Truedream on 2008-09-25
here's mine. Kinda stuck with this theme for now cuz I like it too much.

details in the 2nd pic.

---

### Post by Cosay on 2008-09-25
[IMG]http://farm4.static.flickr.com/3136/2887691765_9898f55000_m.jpg[/IMG]
[Clean]("http://www.flickr.com/photos/cosay-nold/2887691765/")

[IMG]http://farm4.static.flickr.com/3124/2887691769_a505162b76_m.jpg[/IMG]
[Busy]("http://www.flickr.com/photos/cosay-nold/2887691769/")

Arch Linux x64 and Xfce4.
WP: Christy/Waves - Left Monitor by Mando Gomez (mandolux.com).

Yes, I liked BeOS. :)

---

### Post by voteforpedro36 on 2008-09-25
> **Daisuke_Aramaki said:**
> hope he doesn't mind!

here's the link for the wall!

[http://skm-industries.deviantart.com/art/Light-Combustion-RELEASE-59431465]("http://skm-industries.deviantart.com/art/Light-Combustion-RELEASE-59431465")

If you're going to post it, at least post the right wall. Mine actually came from [here]("http://pak3man.blogspot.com/2007/08/pink-combustion-wallpapers.html"), although it may be a mod of that other one.

[QUOTE=myusername]it may be pink. but its beautiful.
could i get some info?[/QUOTE]

Yeah, sure:

Openbox: Slightly modded [Lessr Magenta]("http://www.box-look.org/content/show.php/Lessr+Theme+Pack?content=87524") (just changed the background of the titlebar text)
GTK: [Glow Flower]("http://www.gnome-look.org/content/show.php/Glow?content=85996")
Wall is linked above.
Icons (which you can't see): [Eikon2]("http://drop.io/fmrbpensador")

Anything else?

---

### Post by chucky chuckaluck on 2008-09-25
openbox, pypanel, nimbus mono l. the wallpaper is a slightly distorted drew ernst painting.

[[IMG]http://b.imagehost.org/t/0654/trainscr.jpg[/IMG]](http://b.imagehost.org/view/0654/trainscr.jpg)

---

### Post by Daisuke_Aramaki on 2008-09-25
> **voteforpedro36 said:**
> If you're going to post it, at least post the right wall. Mine actually came from [here]("http://pak3man.blogspot.com/2007/08/pink-combustion-wallpapers.html"), although it may be a mod of that other one.



Yeah, sure:

Openbox: Slightly modded [Lessr Magenta]("http://www.box-look.org/content/show.php/Lessr+Theme+Pack?content=87524") (just changed the background of the titlebar text)
GTK: [Glow Flower]("http://www.gnome-look.org/content/show.php/Glow?content=85996")
Wall is linked above.
Icons (which you can't see): [Eikon2]("http://drop.io/fmrbpensador")

Anything else?

this is what happens if u post a hasty reply without checking the link first!:( the link that i posted is the DA page where the original author of the Light Combustion series, of which Pink Combustion is just one variant, posted his artwork! wherever possible isn't it ok to credit the original author of a certain artwork? Go check it out urself before commenting!

---

### Post by el mariachi on 2008-09-25
> **Cosay said:**
> 
Arch Linux x64 and Xfce4.
WP: Christy/Waves - Left Monitor by Mando Gomez (mandolux.com).

Yes, I liked BeOS. :)
you actually have a folder named Porn? how cute xD

---

### Post by Daisuke_Aramaki on 2008-09-25
> **markp1989 said:**
> my white eee,

os: 32bit hardy
WM: openbox
obtheme: onyx-black
gtk-theme: Clearlooks flat compact
icons: Allblack
dock: fbpanel
network manager: Wicd
battery applet: still looking for one
wallpaper: none


is the clearlooks engine installed? coz it doesn't luk like dat from ur screen!

---

### Post by markp1989 on 2008-09-25
> **Daisuke_Aramaki said:**
> is the clearlooks engine installed? coz it doesn't luk like dat from ur screen!

that was a slight cock up , attached proper screen

my white eee,

os: 32bit hardy
WM: openbox
obtheme: onyx-black
gtk-theme: Clearlooks flat compact
icons: Allblack
dock: fbpanel
network manager: Wicd
battery applet: still looking for one
wallpaper: none

---

### Post by eightmillion on 2008-09-25
I thought I'd show off my wallpaper that I just created. I'd appreciate any feedback on it.

---

### Post by chucky chuckaluck on 2008-09-25
> **eightmillion said:**
> I thought I'd show off my wallpaper that I just created. I'd appreciate any feedback on it.

very nice. has some subtle escher like qualities to it.

---

### Post by myusername on 2008-09-25
> **eightmillion said:**
> I thought I'd show off my wallpaper that I just created. I'd appreciate any feedback on it.

wow i like that wallpaper alot. great job

---

### Post by markp1989 on 2008-09-25
> **eightmillion said:**
> I thought I'd show off my wallpaper that I just created. I'd appreciate any feedback on it.

looks very nice, what others have you madE?

---

### Post by eightmillion on 2008-09-25
> **markp1989 said:**
> looks very nice, what others have you madE?

Thanks. I haven't really done all that much wallpaper-wise. This idea has been brewing for a while. I've been wanting to do something like it since I created this diagram of the planets to scale that I've attached.

---

### Post by billgoldberg on 2008-09-25
> **eightmillion said:**
> I thought I'd show off my wallpaper that I just created. I'd appreciate any feedback on it.

The transition between the wood and the background doesn't seem right.

I can't put my finger on it, but something is missing.

Also, I would go with a slightly darker shade of wood.

Once the rough edges are solved, it will make a killer wallpaper.

---

### Post by klange on 2008-09-25
> **billgoldberg said:**
> The transition between the wood and the background doesn't seem right.

I can't put my finger on it, but something is missing.

Also, I would go with a slightly darker shade of wood.

Once the rough edges are solved, it will make a killer wallpaper.

The problem is a lack of ambient occlusion. Both the wall and the floor should get a little darker at the edge due to less reflected light.

---

### Post by eightmillion on 2008-09-25
> **billgoldberg said:**
> The transition between the wood and the background doesn't seem right.

I can't put my finger on it, but something is missing.

Also, I would go with a slightly darker shade of wood.
I was thinking that too. I was planning on putting a baseboard there, but I couldn't find a good source image. I think I've figured it out though. I just added some shadow there.

---

### Post by klange on 2008-09-25
> **eightmillion said:**
> I was thinking that too. I was planning on putting a baseboard there, but I couldn't find a good source image. I think I've figured it out though. I just added some shadow there.

You need to darken the bottom of the wall - ambient occlusion, see my previous post.

---

### Post by eightmillion on 2008-09-25
> **WindowsSucks said:**
> You need to darken the bottom of the wall - ambient occlusion, see my previous post.

Thanks for the reply. I did darken the wall and the floor. Do you think it needs more?

---

### Post by klange on 2008-09-25
> **eightmillion said:**
> Thanks for the reply. I did darken the wall and the floor. Do you think it needs more?

I think it would help.

---

### Post by eightmillion on 2008-09-25
How's this?

---

### Post by billgoldberg on 2008-09-25
> **eightmillion said:**
> How's this?

Looks much better.

I still think the transition between the wood and background needs something done to it.

---

### Post by klange on 2008-09-25
> **eightmillion said:**
> How's this?
Better. Let's reduce chain posting and move any further comments/criticisms to PMs, shall we?

---

### Post by eightmillion on 2008-09-25
> **WindowsSucks said:**
> Better. Let's reduce chain posting and move any further comments/criticisms to PMs, shall we?

Yes, I've created a thread in art and design.

[http://ubuntuforums.org/showthread.php?t=930100]("http://ubuntuforums.org/showthread.php?t=930100")

---

### Post by boobuntu on 2008-09-25
> **eightmillion said:**
> How's this?

I like that a lot.  I'm a fan of the wood wallpapers and your globe looks great.

Off topic - I hit the front page of ourdesktops!  woot!

---

### Post by Cosay on 2008-09-25
> **el mariachi said:**
> you actually have a folder named Porn? how cute xD

Yes.... cute. :mrgreen:

---

### Post by p_quarles on 2008-09-25
One more screenie this month. This is my favorite setup in some time.

---

### Post by urukrama on 2008-09-26
Openbox 3.4.7, with the Children of the Earth Openbox and Gtk themes, Corbel fonts, and a wallpaper from Customize.org (tinted with hsetroot). The icons are something I've been playing with; perhaps I'll turn it into a (nearly) full icon theme eventually, perhaps this is as far as I get with it.

---

### Post by RiceMonster on 2008-09-26
> **urukrama said:**
> Openbox 3.4.7, with the Children of the Earth Openbox and Gtk themes, Corbel fonts, and a wallpaper from Customize.org (tinted with hsetroot). The icons are something I've been playing with; perhaps I'll turn it into a (nearly) full icon theme eventually, perhaps this is as far as I get with it.

Those icons look awesome

---

### Post by Daisuke_Aramaki on 2008-09-26
final screen from me this month! 
[CENTER]
[[IMG]http://img515.imageshack.us/img515/461/snapshot4qr6.th.png[/IMG]](http://img515.imageshack.us/my.php?image=snapshot4qr6.png)[[IMG]http://img515.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/CENTER]

---

### Post by Frunktz on 2008-09-26
@daisuke
Very cool, can you post font settings (control center, .fonts.conf)?

Thanks

---

### Post by davidryder on 2008-09-26
My first screenshot ever!

[size=3][Full size here](http://www.phpstory.net/graphics/ss_Sep_26_2008_0945.png)[/size]

---

### Post by Daisuke_Aramaki on 2008-09-26
> **Frunktz said:**
> @daisuke
Very cool, can you post font settings (control center, .fonts.conf)?

Thanks

thanx mate! Applications font is HandelGotDLig 9. The console font is Lucida Console 7. i use system settings for anti-aliasing, and forced to 96dpi.

---

### Post by quemaneumaticos on 2008-09-26
hi everyone. Here my desktop:

[img]http://img175.imageshack.us/img175/2493/pantallazo1rm8.png[/img]

---

### Post by Opeth115 on 2008-09-26
> **eightmillion said:**
> How's this?

That looks great for the transition from the floor to the wall you could just put like a little floor board so you can really tell that the floor stops and it starts going up the wall.

---

### Post by ddnev45 on 2008-09-26
> **p_quarles said:**
> One more screenie this month. This is my favorite setup in some time.

Can you post a link to the wallpaper and your .conkyrc?

---

### Post by myusername on 2008-09-26
finally got my desktop the way i wanted...well for now

---

### Post by vishzilla on 2008-09-26
@myusername: nice. why are the tasks on the panel blank?

---

### Post by davidryder on 2008-09-26
Poorly designed theme

---

### Post by crimesaucer on 2008-09-26
[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-9-4.png[/IMG]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-9-3.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-9-3.png)

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-3.png[/IMG]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-2.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-2.png)

---

### Post by raul_ on 2008-09-26
> **vishzilla said:**
> @myusername: nice. why are the tasks on the panel blank?

They're not....

---

### Post by myusername on 2008-09-26
> **vishzilla said:**
> @myusername: nice. why are the tasks on the panel blank?

because its a bug in lxpanel. i got used to it though. makes it look cleaner

---

### Post by Opeth115 on 2008-09-26
New desk for autumn my favorite season =)

[IMG]http://tn3-1.deviantart.com/fs37/300W/f/2008/270/f/e/Arch___MLDY_by_Opeth115.png[/IMG]

[http://opeth115.deviantart.com/art/Arch-MLDY-99042822]("http://opeth115.deviantart.com/art/Arch-MLDY-99042822")

---

### Post by ayoli on 2008-09-26
> **Opeth115 said:**
> New desk for autumn my favorite season =)

[http://tn3-1.deviantart.com/fs37/300W/f/2008/270/f/e/Arch___MLDY_by_Opeth115.png](http://tn3-1.deviantart.com/fs37/300W/f/2008/270/f/e/Arch___MLDY_by_Opeth115.png)

[http://opeth115.deviantart.com/art/Arch-MLDY-99042822]("http://opeth115.deviantart.com/art/Arch-MLDY-99042822")

nice, and .... black :)
details ?

---

### Post by Giant Speck on 2008-09-26
> **crimesaucer said:**
> [IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-9-4.png[/IMG]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-9-3.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-9-3.png)

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-3.png[/IMG]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-2.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-2.png)

My only gripe is that you went with an illegible font for the titlebar, but then stuck with the default Sans font for everything else.

Also, because of your wallpaper (which is still really nice), you can't easily read your Conky.

---

### Post by Sealbhach on 2008-09-26
Just where I'm at right now, recently added a background image to the terminal (swimming penguins).

Compiz, New Wave theme. Livestation TV viewer running.

All fairly standard.

.

---

### Post by davidryder on 2008-09-26
Alright I've made some pretty big changes but I think I'm finally done - for now. :D

[http://www.phpstory.net/graphics/ss_Sep_26_2008_2246.png](http://www.phpstory.net/graphics/ss_Sep_26_2008_2246.png)
[http://www.phpstory.net/graphics/ss_Sep_26_2008_2248.png](http://www.phpstory.net/graphics/ss_Sep_26_2008_2248.png)

---

### Post by crimesaucer on 2008-09-26
> **Giant Speck said:**
> My only gripe is that you went with an illegible font for the titlebar, but then stuck with the default Sans font for everything else.

Also, because of your wallpaper (which is still really nice), you can't easily read your Conky.

Well, I was trying the default sans 8 font for my first time, the conkyrc that I wrote used to use a different font called "eurofurence 9 (bold)" so I might change it back or find something else. Sans 8 is a little thin and difficult to read on such a light wallpaper.


I personally really like the graffiti font I used for the titlebar called "Juice", and I find it one of the best and most readable art fonts out there. It's more of a style customization that takes a very minimal desktop and gives it a bit of personality. Sort of a desktop feng shui.

---

### Post by perfectska04@hotmail.com on 2008-09-27
I'm going green the rest of the month. Back to the same basic GNOME layout.. I just can't commit to docks or screenlets for more than a week, maybe there's something wrong with me.

GTK: Shiki-Colors 2.0
Metacity: Shiki-Colors Easy Metacity
Icons: Gnome-Wise
Font: Free Sans 8px with subpixel hinting and autohinting enabled.

---

### Post by What is in a name? on 2008-09-27
> **perfectska04@hotmail.com said:**
> I'm going green the rest of the month. Back to the same basic GNOME layout.. I just can't commit to docks or screenlets for more than a week, maybe there's something wrong with me.

GTK: Shiki-Colors 2.0
Metacity: Shiki-Colors Easy Metacity
Icons: Gnome-Wise
Font: Free Sans 8px with subpixel hinting and autohinting enabled.

Nothing wrong in your desktop at all. Even the fact you like Beirut is awesome. :D

---

### Post by davidryder on 2008-09-27
I am not a huge fan of screenlets as they sit on my desktop - which I only see immediately after login - and take up resources. Avant (AWM) however has blown my mind so far.

---

### Post by aschwerin.moses on 2008-09-27
Just changed a few things.. just trying out a different look..

---

### Post by ayoli on 2008-09-27
Autumn isn't my favourite season, but is great source of colored wallpaper :)

[[IMG]http://ayozone.org/wp-content/gallery/screenshots-september-2008/thumbs/thumbs_27092008.png[/IMG]]("http://ayozone.org/gallery/screenshots-september-2008")

---

### Post by urukrama on 2008-09-27
> **RiceMonster said:**
> Those icons look awesome

Thank you. Here are a few more of the set.

---

### Post by boobuntu on 2008-09-27
> **ayoli said:**
> Autumn isn't my favourite season, but is great source of colored wallpaper :)

[[IMG]http://ayozone.org/wp-content/gallery/screenshots-september-2008/thumbs/thumbs_27092008.png[/IMG]]("http://ayozone.org/gallery/screenshots-september-2008")


That's a great desktop man.

You have a link to that wallpaper?

---

### Post by raul_ on 2008-09-27
What can I say? It's my type of desktop..

EDIT: Updated plasma theme and forgot to update the screenshot

---

### Post by boobuntu on 2008-09-27
> **raul_ said:**
> What can I say? It's my type of desktop..

Yeah I've seen yours around - nice shot.  I would have that all summer long.  You need a good fall wallpaper now with that theme.

---

### Post by perfectska04@hotmail.com on 2008-09-27
> **What is in a name? said:**
> Nothing wrong in your desktop at all. Even the fact you like Beirut is awesome. :D

Thanks! and Beirut is indeed awesome.

Off topic: I made a firefox userstyle for Shiki and other themes like it. It fixes many of the bugs that firefox gets from the hybrid design. You can find it here, in case you want to get rid of those firefox annoyances in Clear/Murrineglow. [http://userstyles.org/styles/10822]("http://userstyles.org/styles/10822")

---

### Post by raul_ on 2008-09-27
> **boobuntu said:**
> Yeah I've seen yours around - nice shot.  I would have that all summer long.  You need a good fall wallpaper now with that theme.

Well, it's about 25º here :D hurray for mediterranean weather

---

### Post by boobuntu on 2008-09-27
> **raul_ said:**
> Well, it's about 25º here :D hurray for mediterranean weather

LOL, oh man.  I thought I had it bad because it's in the 60's now.

---

### Post by raul_ on 2008-09-27
25ºC btw

---

### Post by myusername on 2008-09-27
> **raul_ said:**
> 25ºC btw

rofl

---

### Post by ayoli on 2008-09-27
> **boobuntu said:**
> That's a great desktop man.

You have a link to that wallpaper?

thank you, here you go : 
[http://upload.wikimedia.org/wikipedia/commons/c/cf/BigtoothMaple0309210085.JPG](http://upload.wikimedia.org/wikipedia/commons/c/cf/BigtoothMaple0309210085.JPG)

edit: this one actually is not in a large resolution, but that's ok on my 1280x800

---

### Post by etnlIcarus on 2008-09-27
Probably last screen for the month. Nothing too special. NFI where the wallpaper is from.

[url=http://img354.imageshack.us/img354/7426/screenhl4.png][img]http://img354.imageshack.us/img354/6048/screenswp3.png[/img]
http://img354.imageshack.us/img354/7426/screenhl4.png[/url]

---

### Post by chucky chuckaluck on 2008-09-27
gnome on arch, glider metacity, a slate version of elegant brit, no idea where i got the wallpaper.

[[IMG]http://b.imagehost.org/t/0604/gnomescr.jpg[/IMG]](http://b.imagehost.org/view/0604/gnomescr.jpg)

---

### Post by What is in a name? on 2008-09-27
> **perfectska04@hotmail.com said:**
> Thanks! and Beirut is indeed awesome.

Off topic: I made a firefox userstyle for Shiki and other themes like it. It fixes many of the bugs that firefox gets from the hybrid design. You can find it here, in case you want to get rid of those firefox annoyances in Clear/Murrineglow. [http://userstyles.org/styles/10822]("http://userstyles.org/styles/10822")

You mean, issues like the "add bookmark dialog", and other elements from the interface (that you brilliantly solved with userChrome.css file that you created and published with your theme)? Does this mean that the userstyle you made automatically takes care of all those settings?

---

### Post by darweth on 2008-09-27
> **ayoli said:**
> Autumn isn't my favourite season, but is great source of colored wallpaper :)

[[IMG]http://ayozone.org/wp-content/gallery/screenshots-september-2008/thumbs/thumbs_27092008.png[/IMG]]("http://ayozone.org/gallery/screenshots-september-2008")

So --- is there an easy way to use those Adium visual styles for Pidgin?  How did you do it?  Is it stable?

---

### Post by raul_ on 2008-09-27
> **raul_ said:**
> 25ºC btw

And it just started raining...you jinxed it boobuntu!

---

### Post by perfectska04@hotmail.com on 2008-09-27
> **What is in a name? said:**
> You mean, issues like the "add bookmark dialog", and other elements from the interface (that you brilliantly solved with userChrome.css file that you created and published with your theme)? Does this mean that the userstyle you made automatically takes care of all those settings?

Yes. An userstyle is the same as userChrome.css, only that it's easier to preview/edit through Stylish extension. This is pretty much an update of the workaround I posted earlier.. Now it takes the correct text colors automatically from the theme. The awesomebar and autocomplete were also fixed to look like treeview elements.

That should pretty much solve 90% of issues with hybrid themes. The only thing left is to find out the correct hook for the edit bookmark popup's background... I've managed to set a light background, but there's always a dark 4px border around the popup no matter what I do. The site info's background can be easily changed, so I'll do that as well once I figure out the bookmark popup.

---

### Post by knavarathna92 on 2008-09-27
very gamer visual style I think (especially if you know what this is related to):KS.

---

### Post by markp1989 on 2008-09-27
In the middle of re themeing my desktop:

GTK: Industrial with colour change
Emerald: Somthing i made
Icon theme: currently black-white2 (looking for a new one)

are there any icon packs that people would recommend that will compliment this theme?

---

### Post by ayoli on 2008-09-27
> **darweth said:**
> So --- is there an easy way to use those Adium visual styles for Pidgin?  How did you do it?  Is it stable?

It is a screenlet. You can find it here : [http://gnome-look.org/content/show.php/PidginScreenlet?content=72611](http://gnome-look.org/content/show.php/PidginScreenlet?content=72611)

---

### Post by olskar on 2008-09-27
> **knavarathna92 said:**
> very gamer visual style I think (especially if you know what this is related to):KS.


What icontheme?

---

### Post by skitzware on 2008-09-27
[[IMG]http://img228.imageshack.us/img228/3570/screenshothe1.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshothe1.png)[[IMG]http://img228.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Not much of a change from my last screenie.. Just sad to hear the news today... RIP Paul...

---

### Post by RiceMonster on 2008-09-27
> **skitzware said:**
> [[IMG]http://img228.imageshack.us/img228/3570/screenshothe1.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshothe1.png)[[IMG]http://img228.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Not much of a change from my last screenie.. Just sad to hear the news today... RIP Paul...

looks really good! Mind posting the info (gtk theme, icons, etc)?

---

### Post by dbbolton on 2008-09-27
> **skitzware said:**
> [[IMG]http://img228.imageshack.us/img228/3570/screenshothe1.th.png[/IMG]](http://img228.imageshack.us/my.php?image=screenshothe1.png)[[IMG]http://img228.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Not much of a change from my last screenie.. Just sad to hear the news today... RIP Paul...
Where did you get those icons? Also, is that one of the Segoe fonts?

---

### Post by Nythain on 2008-09-27
Here's my latest and probably gonna last a bit, im diggin it

---

### Post by urukrama on 2008-09-27
> **Nythain said:**
> Here's my latest and probably gonna last a bit, im diggin it

Would you mind posting your screenrc?

---

### Post by skitzware on 2008-09-27
> 
Quote:
Originally Posted by skitzware
Not much of a change from my last screenie.. Just sad to hear the news today... RIP Paul...
looks really good! Mind posting the info (gtk theme, icons, etc)?

> 
Quote:
Originally Posted by skitzware
Not much of a change from my last screenie.. Just sad to hear the news today... RIP Paul...
Where did you get those icons? Also, is that one of the Segoe fonts?

GTK Theme is a mix of Alpha & Ion, both by fratrip | fratrip.deviantart.com
Emerald is Ion by fratrip too
Icons are from FOUR08 [http://www.4impressions.net](http://www.4impressions.net) and AllGrey
Fonts are Lucida Grande @ 8.6pt & Trebuchet MS 9pt

---

### Post by aschwerin.moses on 2008-09-27
> **Nythain said:**
> Here's my latest and probably gonna last a bit, im diggin it
okay... this is really cool.. are those terminal screenlets???

---

### Post by bp1509 on 2008-09-27
openbox with fawn theme from box-look.

---

### Post by dbbolton on 2008-09-27
> **bp1509 said:**
> openbox with fawn theme from box-look.
Interesting IRC topic...

---

### Post by bp1509 on 2008-09-27
> **dbbolton said:**
> Interesting IRC topic...

lol that room is a trip.

---

### Post by BOBSONATOR on 2008-09-27
Here is my "New Wave" look, fresh from Gnome-look.org
the fonts are myriad pro, the background is from interfacelift.org

---

### Post by chris200x9 on 2008-09-27
> **AlexR1 said:**
> September Desktop

I started doing this to show,brown desktop can be nice nad shiny, tell me what do you think?
Info about Gtk theme can be found in terminal window.
Enjoy

I LOVE that first background do you have a link?

---

### Post by voteforpedro36 on 2008-09-27
Slight change in some fonts.

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-27-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-27-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-27-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-27-08-media.png)

---

### Post by Perpetual on 2008-09-27
> **Hells_Dark said:**
> [[img]http://pix.nofrag.com/6/8/c/537b53a9edefb672b23aa17ff998a.png[/img]](http://pix.nofrag.com/a/3/a/0426080de6254ebb68d5b4cf8ae3c.jpg)

I like that a lot!  Nice work.

---

### Post by dbbolton on 2008-09-27
> **BOBSONATOR said:**
> Here is my "New Wave" look, fresh from Gnome-look.org
the fonts are myriad pro, the background is from interfacelift.org
How did you get the pointer to show up in the screenshot?

---

### Post by vishzilla on 2008-09-28
GTK: Slickness
Icons: B&W 2 Style

[CENTER][[IMG]http://www.ourdesktops.com/desktops/thumb_medium/dff7d16f-ada0-4cf2-b08f-008f72ad5a6a_thumbmedium.jpg[/IMG]](http://www.ourdesktops.com/desktop_user.aspx?user=vishal)[/CENTER]

---

### Post by crimesaucer on 2008-09-28
Wallpaper is from deviantART
All other themes are custom. (modified murrine, transparent UbuntuStudio icons, matching Arch-xfce4 logos, and emerald truglass theme)
The font is called eurofurence.


[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-15-2.png[/IMG]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-15-1.jpg](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-15-1.jpg)

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-13-1.png[/IMG]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-13.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-13.png)

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-12-1.png[/IMG]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-12.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-12.png)

---

### Post by joebodo on 2008-09-28
eee pc 900 + modified netbook remix
[[IMG]http://img523.imageshack.us/img523/8272/screenshot2hh1.th.png[/IMG]](http://img523.imageshack.us/my.php?image=screenshot2hh1.png)[[IMG]http://img523.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by ayoli on 2008-09-28
> **joebodo said:**
> eee pc 900 + modified netbook remix
[http://img507.imageshack.us/img507/8449/screenshot2fs6.png](http://imageshack.us)

please, use thumbnails.

---

### Post by etnlIcarus on 2008-09-28
It's only 100KB.

Also, looking really slick, Joebodo.

---

### Post by vishzilla on 2008-09-28
@joebodo: awesome!

---

### Post by chucky chuckaluck on 2008-09-28
jwm, urxvt, opera (chrome skin), gimp (blue version of elegant brit). don't remember where i got the wallpaper.

[[IMG]http://b.imagehost.org/t/0155/labscr1.jpg[/IMG]](http://b.imagehost.org/view/0155/labscr1.jpg) [[IMG]http://b.imagehost.org/t/0072/labscr2.jpg[/IMG]](http://b.imagehost.org/view/0072/labscr2.jpg)

---

### Post by raul_ on 2008-09-28
> **joebodo said:**
> eee pc 900 + modified netbook remix
[[IMG]http://img523.imageshack.us/img523/8272/screenshot2hh1.th.png[/IMG]](http://img523.imageshack.us/my.php?image=screenshot2hh1.png)[[IMG]http://img523.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

nice space usage :)

---

### Post by Perfect Storm on 2008-09-28
Going for a bit city/industrial look;

[[img]http://www.imageviper.com/displayimage/128246/0/2008-Sep-28-shot2-pre.jpg[/img]](http://www.imageviper.com/displayimage/128245/0/2008-Sep-28-shot2.jpg)
click to enlarge 1680x1050 pix

---

### Post by Mazza558 on 2008-09-28
Nothing much has changed since last time. I just have too much work to do. Plus, I still can't find a better GTK theme than Clearlooks. Everything else has slight annoyances that turn into faults and force me to switch back. The Eikon theme is great, but the wireless and volume icons don't work with light themes. I'll mod it a bit later. 

On the emerald side of things, I've moved the futurelooks emerald theme to truglass, and the window titles now have a nice glassy look to them. If anyone wants the emerald theme, just ask and I'll upload it. The wallpaper's from Interfacelift.com.

---

### Post by knavarathna92 on 2008-09-28
> **olskar said:**
> What icontheme?

eikon version 2.0 i saw a thread on the forums a while back with a link.  Its not on gnome-look though :-(

---

### Post by skitzware on 2008-09-28
[[IMG]http://img504.imageshack.us/img504/3876/sshotoo7.th.png[/IMG]](http://img504.imageshack.us/my.php?image=sshotoo7.png)[[IMG]http://img504.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Couldn't resist another port of a fluxbox theme...
GTK is Mythos

---

### Post by Perpetual on 2008-09-28
> **Mazza558 said:**
> Nothing much has changed since last time. I just have too much work to do. Plus, I still can't find a better GTK theme than Clearlooks. Everything else has slight annoyances that turn into faults and force me to switch back. The Eikon theme is great, but the wireless and volume icons don't work with light themes. I'll mod it a bit later. 

On the emerald side of things, I've moved the futurelooks emerald theme to truglass, and the window titles now have a nice glassy look to them. If anyone wants the emerald theme, just ask and I'll upload it. The wallpaper's from Interfacelift.com.

Mazza, what panel are you using?

---

### Post by Mazza558 on 2008-09-28
> **Perpetual said:**
> Mazza, what panel are you using?

I'm using the gnome panel with a custom image.

Did you mean what menu? It's Ubuntu System Panel.

---

### Post by aschwerin.moses on 2008-09-28
> **Artificial Intelligence said:**
> Going for a bit city/industrial look;

[[img]http://www.imageviper.com/displayimage/128246/0/2008-Sep-28-shot2-pre.jpg[/img]](http://www.imageviper.com/displayimage/128245/0/2008-Sep-28-shot2.jpg)
click to enlarge 1680x1050 pix
Can you please give me the wallpapers link...

---

### Post by Perfect Storm on 2008-09-28
> **aschwerin.moses said:**
> Can you please give me the wallpapers link...

[HDR image of New York's 9th Avenue.](http://interfacelift.com/wallpaper/details.php?id=01324)
Works best for HD/widescreen

---

### Post by olskar on 2008-09-28
> **knavarathna92 said:**
> eikon version 2.0 i saw a thread on the forums a while back with a link.  Its not on gnome-look though :-(

Propably because of permissionproblems, can you upload it somewhere and upload it somewhere? :)

---

### Post by PurposeOfReason on 2008-09-28
I don't remember if I saw it here but I saw a conky that had a mpd script that would show an icon for play or pause. It might have been on deviantart. Either way, I can't find it. Does anyone know what I'm talking about?

---

### Post by dbbolton on 2008-09-28
Giving Cairo Dock a go

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/sshot/th_2008-09-28-142329_1280x960_scrot.png[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/sshot/2008-09-28-142329_1280x960_scrot.png)

---

### Post by Daisuke_Aramaki on 2008-09-28
> **dbbolton said:**
> Giving Cairo Dock a go

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/sshot/th_2008-09-28-142329_1280x960_scrot.png[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/sshot/2008-09-28-142329_1280x960_scrot.png)

Sleek! :D

---

### Post by Daisuke_Aramaki on 2008-09-28
Tryin out dwm rite now! haven't customized nething yet! will do so in the next couple of days!

[CENTER][[IMG]http://img176.imageshack.us/img176/7929/screenoneai2.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenoneai2.png)[[IMG]http://img176.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

[[IMG]http://img176.imageshack.us/img176/8949/screenfinalja1.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenfinalja1.png)[[IMG]http://img176.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)[/CENTER]

---

### Post by What is in a name? on 2008-09-28
> **olskar said:**
> Propably because of permissionproblems, can you upload it somewhere and upload it somewhere? :)

As it was also mentioned some pages ago, I'm uploading all new versions of Eikon2 at my drop.io page. Here's the link: [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)

---

### Post by BOBSONATOR on 2008-09-28
> **dbbolton said:**
> How did you get the pointer to show up in the screenshot?

i have no clue, i just hit prntscreen, and it just did

---

### Post by urukrama on 2008-09-28
Here is one for all you command line and tiling wm enthusiasts.

I've recently started using [dvtm]("http://www.brain-dump.org/projects/dvtm/"), a tiling "window" manager for the console, that resembles dwm in some respects. I've been using it in my tty consoles, which usually have some command line apps running while I work in X. Dvtm is neat, and I much prefer it over screen on bigger terminals or consoles. You can easily switch between layouts (different tiling modes, maximized, etc.), iconify windows, or adjust the sizes of windows, and when you use it in X, you can use your mouse as well.

Since taking a screenshot of a tty is a bit cumbersome, the sceenshot shows dvtm running in urxvt in Awesome, to give you an idea of what it looks like.

---

### Post by el mariachi on 2008-09-28
> **Artificial Intelligence said:**
> Going for a bit city/industrial look;


click to enlarge 1680x1050 pix
what's your terminal font?

---

### Post by crimesaucer on 2008-09-28
Check out my Archxfce4 Murrine gmail:

[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-16b.png[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-16a.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-16a.png)

---

### Post by dbbolton on 2008-09-28
> **Daisuke_Aramaki said:**
> Sleek! :D
Danke :D

---

### Post by Opeth115 on 2008-09-28
> **crimesaucer said:**
> Check out my Archxfce4 Murrine gmail:

[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-16b.png[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-16a.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-16a.png)

How may this be done?

---

### Post by el mariachi on 2008-09-28
+1! stylish?

---

### Post by Truedream on 2008-09-28
> **What is in a name? said:**
> As it was also mentioned some pages ago, I'm uploading all new versions of Eikon2 at my drop.io page. Here's the link: [http://drop.io/fmrbpensador](http://drop.io/fmrbpensador)

whats new/changed? Could you please post the changes cuz every time I install Eikon theme I've to replace some of the icons with my own.
Thanks

---

### Post by crimesaucer on 2008-09-28
> **Opeth115 said:**
> How may this be done?

To change your gmail, get the Firefox extension called Stylish, and then click find styles when on your Gmail2 page.


It will take you to their user scripts page for Gmail and Gmail2.


Then I chose the script called "Brownie": [http://userstyles.org/styles/10529](http://userstyles.org/styles/10529)


Load it into Stylish as "Preview",

copy the script to mousepad or gedit, 

take an app like "agave" to find out what colors to edit.

change all of the colors with the text editor to your colors.

change the main font to your special font.

remove the whole "button" section to use your linux gtk buttons.

then pasted the new script over the old "Brownie" script.

click preview again to see the changes, if you make an error it will tell you and you can fix it.


Then, for the logo use this Stylish script: [http://userstyles.org/styles/4579](http://userstyles.org/styles/4579)

..... just follow instructions. In Arch, base64 was already installed as part of the coreutils package, all I had to do was make a .png image that was 143x59, save it and then run in a terminal:

```
base64 gmail-image.png
```

Then paste the result into the part that looks the exact same.

You should be all done now.

---

### Post by steveneddy on 2008-09-28
> **chucky chuckaluck said:**
> xfce and my cat, jimmy.



I don't have a cat, but my brother is named Jimmy.

[IMG]http://oidiota.files.wordpress.com/2007/07/messy-desk.jpg[/IMG]

I just cleaned it off yesterday so i could get some work done.

Should have seen it before.

---

### Post by el mariachi on 2008-09-28
that's what I call "art moderne" xD

---

### Post by boobuntu on 2008-09-28
> **voteforpedro36 said:**
> Slight change in some fonts.

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-27-08-bare.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-27-08-bare.png)

[[IMG]http://i460.photobucket.com/albums/qq330/voteforpedro36/th_9-27-08-media.png[/IMG]](http://i460.photobucket.com/albums/qq330/voteforpedro36/9-27-08-media.png)

Do you have the wall for this?  I love it.

---

### Post by voteforpedro36 on 2008-09-28
> **boobuntu said:**
> Do you have the wall for this?  I love it.

[Here it is](http://pak3man.blogspot.com/2007/08/pink-combustion-wallpapers.html&usg=AFQjCNGeIYWqw_5XWQX-ofXBDWfPlLPr2w).

---

### Post by theoniq on 2008-09-28
[[img]http://dreamscan.net/pics/main.php?g2_view=core.DownloadItem&g2_itemId=167&g2_serialNumber=2[/img]](http://dreamscan.net/pics/main.php?g2_itemId=164&g2_imageViewsIndex=2)

Archlinux on my Dell XPS M1530 laptop
Openbox & Gnome panel

---

### Post by RiceMonster on 2008-09-28
Archlinux with Openbox

OB: Breathe
GTK: Breathe
Icons: All Black

[[img]http://xs231.xs.to/xs231/08390/2008-09-28-210912_1280x800_scrot903.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs231&d=08390&f=2008-09-28-210912_1280x800_scrot903.png) [[img]http://xs231.xs.to/xs231/08390/2008-09-28-210903_1280x800_scrot614.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs231&d=08390&f=2008-09-28-210903_1280x800_scrot614.png)

---

### Post by raul_ on 2008-09-28
It almost looks as if there are more Arch than Ubuntu users in this thread.

---

### Post by crimesaucer on 2008-09-28
> **BOBSONATOR said:**
> Here is my "New Wave" look, fresh from Gnome-look.org
the fonts are myriad pro, the background is from interfacelift.org

This is a good look for the ubuntu orange/brown/black.


You see a lot of people complain about ubuntu, some complain about the colors, others complain about the gtk, and others complain about the wallpaper....


This "New Wave" look is the direction I think the default ubuntu theme should go.


Basically, a nice wallpaper that matches the human icons, and a clean minimal gtk theme with a modern look.

---

### Post by BOBSONATOR on 2008-09-28
> **crimesaucer said:**
> This is a good look for the ubuntu orange/brown/black.


You see a lot of people complain about ubuntu, some complain about the colors, others complain about the gtk, and others complain about the wallpaper....


This "New Wave" look is the direction I think the default ubuntu theme should go.


Basically, a nice wallpaper that matches the human icons, and a clean minimal gtk theme with a modern look.

Thanks, here is the Elementary_Human icon theme with it, looks great imo:D

---

### Post by Nythain on 2008-09-28
> **urukrama said:**
> Would you mind posting your screenrc?
sure, here's the relevant parts
```

# ===============================================================
# VARIABLES - Boolean values (on/off)
# ===============================================================
  autodetach            on              # default: on
# crlf                  off             # default: off
# deflogin              off             # default: on
# defsilence            off             # default: off
# hardcopy_append       on              # default: off
# nethack               on              # default: off
  startup_message       off             # default: on
  termcapinfo xterm ti@:te@
  vbell                 off             # default: ???
#
# ===============================================================
# VARIABLES - Number values
# ===============================================================
  defscrollback         3000            # default: 100
# msgminwait            3               # default: 1
  silencewait           15              # default: 30
#
# ===============================
# Hardstatus Line and sorendition
# ===============================
#
# Prints the window names and highlight the current window in yellow.
# On the right there is the time in green and the date in yellow.
#
  hardstatus alwayslastline "%{= 9g}%?%-Lw%?%{+b 9c}%n$ %t %?(%u)%?%{= 9g}%?%+Lw%?"
#
# Colorize the "messages" and "text marking":
# Example:  Blue bg, white fg
#  sorendition gK
#
# ===============================================================
# Launch Apps:
# ===============================================================
#
# Desktop Bash
  screen -t Desktop 1
#
# SSH to Server
  screen -t Server 2 ssh rune@apollo
#
# SSH to Shell
  screen -t Shell 3 
#
# SSH to Server for rTorrent
  screen -t rTorrent 4 ssh rune@apollo
#

```
basically just runs 4 shells, one for my desktop, one that ssh's over to my server, one for connecting to my shell/hosting account, and a seperate one for my server that attaches a screen on the server running rtorrent

the .bashrc command prompt on my desktop is green and the server is blue so i can quickly and easily recognize wich shell im, and rtorrent is run in a seperate screen actually onthe server so i can attatch from remote locations for administration or just check up on torrents

---

### Post by Perfect Storm on 2008-09-28
> **el mariachi said:**
> what's your terminal font?

Monospace size 7

---

### Post by crimesaucer on 2008-09-29
> **BOBSONATOR said:**
> Thanks, here is the Elementary_Human icon theme with it, looks great imo:D

Very nice again. The default Ubuntu theme should definitely be something like this.


A nice wallapaer with good color and a clear picture that shows off a good monitor. A minimal, modern, gtk theme that can look good with any style wallpaper and icon pack.... and doesn't even need compositing. 

And of course the unique "human" orange icons that make ubuntu so different than all of the blue distro's. I also like the use of the light brown in the gtk theme.

---

### Post by mrgnash on 2008-09-29
[IMG]http://i38.tinypic.com/juwjuf.png[/IMG]

---

### Post by Daisuke_Aramaki on 2008-09-29
@mrgnash

pardon my ignorance. who's the babe?

---

### Post by rjmdomingo2003 on 2008-09-29
> **Daisuke_Aramaki said:**
> @mrgnash

pardon my ignorance. who's the babe?
Kristin Kreuk

---

### Post by WWSmith36 on 2008-09-29
Winubuntu

[ATTACH]86710[/ATTACH]

---

### Post by DJ_Peng on 2008-09-29
I know, I still need to get a pic taken of my desktop this month. I can't believe it's almost the end of the month already. :(

> **Artificial Intelligence said:**
> [HDR image of New York's 9th Avenue.]("http://interfacelift.com/wallpaper/details.php?id=01324")
Works best for HD/widescreen
Awesome wallpaper. I love how Interfacelift has images in so many sizes. I was able to get one for my 1280x1024 desktop without having to get it into Gimp to resize/crop it.

> **steveneddy said:**
> I just cleaned it off yesterday so i could get some work done.

Should have seen it before.
LMAO!

> **Daisuke_Aramaki said:**
> @mrgnash

pardon my ignorance. who's the babe?
I wondered the same thing. Thanks for asking for all of us who "wanted to know". :popcorn:

---

### Post by chucky chuckaluck on 2008-09-29
> **Daisuke_Aramaki said:**
> @mrgnash

pardon my ignorance. who's the babe?

[steve]kreuky![/irwin]

---

### Post by urukrama on 2008-09-29
> **Nythain said:**
> sure, here's the relevant parts

Thank you.

---

### Post by boobuntu on 2008-09-29
Don't recall if I shared this one.  I'll probably keep this for another few days and then change it when we roll into October.  I need some foliage to look at.

**About** 
I just reinstalled the latest version of Ubuntu and slapped this sweet wall up!  I'm not a huge fan of flaunting browser wallpapers but I love this particular FF one!

**Wallpaper** 
[http://www.gnome-look.org/CONTENT/content-files/71793-firefox_nebula_1920_1200.jpg](http://www.gnome-look.org/CONTENT/content-files/71793-firefox_nebula_1920_1200.jpg)

[[IMG]http://www.ourdesktops.com/desktops/thumb_medium/113fd130-a727-4fb5-9533-fde409ac7738_thumbmedium.jpg[/IMG]](http://www.ourdesktops.com/desktop_user.aspx?user=boobuntu)

---

### Post by lzfy on 2008-09-29
> **Mazza558 said:**
> Nothing much has changed since last time. I just have too much work to do. Plus, I still can't find a better GTK theme than Clearlooks. Everything else has slight annoyances that turn into faults and force me to switch back. The Eikon theme is great, but the wireless and volume icons don't work with light themes. I'll mod it a bit later. 

On the emerald side of things, I've moved the futurelooks emerald theme to truglass, and the window titles now have a nice glassy look to them. If anyone wants the emerald theme, just ask and I'll upload it. The wallpaper's from Interfacelift.com.

In my opinion this is the most professional looking Gnome desktop. I wouldn't mind seeing this as the default theme of Ubuntu.

---

### Post by markp1989 on 2008-09-29
my Desktop

os: 64bit hardy
WM: compiz
emerald: somthing i just made 
gtk-theme: Industrial, with a colour change 
icons: blackwhite2
dock: fbpanel
wallpaper: think it was on interface lift 

apps: firefox, xfce terminal, emesene, fbpanel, conky, feh

---

### Post by el mariachi on 2008-09-29
wow I'm running Winxp, arch and suse all at the same time xD 3 desks in one hehe gotta love vbox

---

### Post by NintendoTogepi on 2008-09-29
[IMG]http://img.photobucket.com/albums/v367/amethystjewel/zdesktopbackground.png[/IMG]

Yeah, I use Windows. :D

---

### Post by Koori23 on 2008-09-29
If you're gonna use the Royale Theme.. At least use the black version..

I think it's called Royale Noir or something like that.

---

### Post by raul_ on 2008-09-29
> **NintendoTogepi said:**
> [IMG]http://img.photobucket.com/albums/v367/amethystjewel/zdesktopbackground.png[/IMG]

Yeah, I use Windows. :D

You must have gone through a lot of trouble to get your taskbar pimped like that!

---

### Post by el mariachi on 2008-09-29
I think you can download that theme

---

### Post by Mark76 on 2008-09-29
Stripped it down a tad (still got a dock full of stuff though :D)

[[img]http://xs131.xs.to/xs131/08401/bare899.png[/img]](http://xs.to)

---

### Post by blakjesus on 2008-09-29
I guess ill post my desktop before September is over. :)

[[IMG]http://img219.imageshack.us/img219/8210/screenshot2ul2.th.jpg[/IMG]](http://img219.imageshack.us/my.php?image=screenshot2ul2.jpg)[[IMG]http://img219.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

The theme is a mix of Murrina glossy and a custom window border i found on the internet, i dont remember where. Im also obviously using AWN. (i thinks it goes well with ubuntu) and of obviously thats a terminal with transparency turned on.:D

---

### Post by narf41 on 2008-09-29
autumn desk

[[img]http://ubuntu-pics.de/thumb/3844/080928_239E0q.png[/img]](http://ubuntu-pics.de/bild/3844/080928_239E0q.png)

---

### Post by PurposeOfReason on 2008-09-29
> **narf41 said:**
> autumn desk

[[IMG]http://ubuntu-pics.de/thumb/3844/080928_239E0q.png[/IMG]]("http://ubuntu-pics.de/bild/3844/080928_239E0q.png")
Wallpaper?

---

### Post by NintendoTogepi on 2008-09-29
> **el mariachi said:**
> I think you can download that theme

It came with my Windows XP Media Center edition, actually, as the default theme.

I much prefer it to the normal Windows XP theme.

---

### Post by raul_ on 2008-09-29
> **NintendoTogepi said:**
> It came with my Windows XP Media Center edition, actually, as the default theme.

I much prefer it to the normal Windows XP theme.

I actually thought it was the default one :redface:

---

### Post by skitzware on 2008-09-29
[[IMG]http://img220.imageshack.us/img220/5853/screenshotoj6.th.png[/IMG]](http://img220.imageshack.us/my.php?image=screenshotoj6.png)[[IMG]http://img220.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Think I'm taking this blank n white vibe too far...

---

### Post by RiceMonster on 2008-09-29
> **skitzware said:**
> [[IMG]http://img220.imageshack.us/img220/5853/screenshotoj6.th.png[/IMG]](http://img220.imageshack.us/my.php?image=screenshotoj6.png)[[IMG]http://img220.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Think I'm taking this blank n white vibe too far...

Love it. Mind posting the details (gtk theme, icon theme, etc)?

---

### Post by Truedream on 2008-09-29
last one for Sept

---

### Post by Mr.Crowley on 2008-09-29
Some small changes. Figured I'd upload one more for September.

[[IMG]http://b.imagehost.org/t/0316/2008-09-29-212441_1280x1024_scrot.jpg[/IMG]](http://b.imagehost.org/view/0316/2008-09-29-212441_1280x1024_scrot.png)

---

### Post by BilliShere on 2008-09-30
[[IMG]http://img297.imageshack.us/img297/9639/screenshot70xo8.png[/IMG]]("http://billishere.deviantart.com/art/Dust-maxxed-out-99188717")

This is probably gonna be my october desktop for a while too!

---

### Post by Giant Speck on 2008-09-30
> **skitzware said:**
> [[IMG]http://img220.imageshack.us/img220/5853/screenshotoj6.th.png[/IMG]](http://img220.imageshack.us/my.php?image=screenshotoj6.png)[[IMG]http://img220.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Think I'm taking this blank n white vibe too far...

Is that Ali Larter?

---

### Post by chucky chuckaluck on 2008-09-30
openbox, xfce panel and terminal, quodlibet. the gtk theme is a slate colored variation i made of elegant brit, as is the openbox theme. the font is nimbus sans l. the wallpaper is one that i think came from interfacelift. i altered the salutation to better fit my lifestyle.

[[IMG]http://b.imagehost.org/t/0367/stupidscr.jpg[/IMG]](http://b.imagehost.org/view/0367/stupidscr.jpg)

---

### Post by Patricrawley on 2008-09-30
My new Wristcutters background!

---

### Post by myusername on 2008-09-30
last of the month for me...i went with tint2

---

### Post by urukrama on 2008-09-30
> **chucky chuckaluck said:**
> openbox, xfce panel and terminal, quodlibet. the gtk theme is a slate colored variation i made of elegant brit, as is the openbox theme. the font is nimbus sans l. the wallpaper is one that i think came from interfacelift. i altered the salutation to better fit my lifestyle.

[[IMG]http://b.imagehost.org/t/0367/stupidscr.jpg[/IMG]](http://b.imagehost.org/view/0367/stupidscr.jpg)

That is quite nice. Can you upload those themes somewhere? (Btw, did you know your window decorations and your Gtk theme have a different shade of gray?)

---

### Post by skitzware on 2008-09-30
>  Originally Posted by skitzware  View Post


Think I'm taking this blank n white vibe too far...
Love it. Mind posting the details (gtk theme, icon theme, etc)?

I've already posted the icons but its still at FOUR08
gtk theme is a modded Ion by fratrip.deviantart.com

 Originally Posted by skitzware
Think I'm taking this blank n white vibe too far...
Is that Ali Larter?

No its the next Mrs Skitzware, Alessandra Ambrosio

---

### Post by andrek on 2008-09-30
> **BilliShere said:**
> [[IMG]http://img297.imageshack.us/img297/9639/screenshot70xo8.png[/IMG]]("http://billishere.deviantart.com/art/Dust-maxxed-out-99188717")

This is probably gonna be my october desktop for a while too!

Looks ultra cool. Actually, I've left some words on dA ( my nickname - solidslash )

---

### Post by chucky chuckaluck on 2008-09-30
> **urukrama said:**
> That is quite nice. Can you upload those themes somewhere? (Btw, did you know your window decorations and your Gtk theme have a different shade of gray?)

they're both gray??? holy poop, batman! j/k, i knew that. making the gray of the win.dec. a lighter shade of gray from the toolbar gives the appearance that the toolbar is inset. 

attached are the themes (let me know if i blew it. i think i did it right). thanks for the compliment.

---

### Post by What is in a name? on 2008-09-30
I'll have to agree with Andrek. It is great indeed. Thumbs up!

---

### Post by urukrama on 2008-09-30
> **chucky chuckaluck said:**
> attached are the themes (let me know if i blew it. i think i did it right). thanks for the compliment.

Thank you. I'll try it out later. 

Here is an update on my current desktop.

---

### Post by kk0sse54 on 2008-09-30
NetBSD 4.0 with xfce4

[ATTACH]86843[/ATTACH]

---

### Post by narf41 on 2008-09-30
> **PurposeOfReason said:**
> Wallpaper?
[http://ultraviolett.deviantart.com/art/feels-like-autumn-wallpaper-91436886](http://ultraviolett.deviantart.com/art/feels-like-autumn-wallpaper-91436886)

---

### Post by crimesaucer on 2008-09-30
> **C!oud said:**
> NetBSD 4.0 with xfce4

[ATTACH]86843[/ATTACH]

I've always wanted to try a BSD distro. Is it fast?

---

### Post by kk0sse54 on 2008-09-30
> **crimesaucer said:**
> I've always wanted to try a BSD distro. Is it fast?

Yes and I'm only running it in vmware server until I can free up a primary partition. NetBSD has easily become my distro of choice as it's very small clean and fast. It's a very bare bones installed system that requires a lot of configuration so it turns out the way you want it to be. If you don't enjoy using vi with no gui by default then you might want to check out some of the more "user friendly" OS's like PC-BSD(there was just a new release featuring KDE 4.1) or DesktopBSD.

---

### Post by crimesaucer on 2008-09-30
> **C!oud said:**
> Yes and I'm only running it in vmware server until I can free up a primary partition. NetBSD has easily become my distro of choice as it's very small clean and fast. It's a very bare bones installed system that requires a lot of configuration so it turns out the way you want it to be. If you don't enjoy using vi with no gui by default then you might want to check out some of the more "user friendly" OS's like PC-BSD(there was just a new release featuring KDE 4.1) or DesktopBSD.

I use nano when I install Arch with no gui, I'm very comfortable using console apps like midnight commander and links, as for vi, I'm learning it.... but it's very different to have to insert code rather than just move the cursor around and type.....

I do think vi is the better editor, I just don't have the "modes" memorized yet, so whenever I want to do something in console, nano is faster for me. 


I am going to stop using nano though, ever since it updated in Arch, it doesn't wrap anymore with the nano -w option..... which can really screw something up.

---

### Post by raul_ on 2008-09-30
> **C!oud said:**
> Yes and I'm only running it in vmware server until I can free up a primary partition. NetBSD has easily become my distro of choice as it's very small clean and fast. It's a very bare bones installed system that requires a lot of configuration so it turns out the way you want it to be. If you don't enjoy using vi with no gui by default then you might want to check out some of the more "user friendly" OS's like PC-BSD(there was just a new release featuring KDE 4.1) or DesktopBSD.

Sounds like Arch

---

### Post by kk0sse54 on 2008-09-30
> **crimesaucer said:**
> I use nano when I install Arch with no gui, I'm very comfortable using console apps like midnight commander and links, as for vi, I'm learning it.... but it's very different to have to insert code rather than just move the cursor around and type.....

I do think vi is the better editor, I just don't have the "modes" memorized yet, so whenever I want to do something in console, nano is faster for me. 


I am going to stop using nano though, ever since it updated in Arch, it doesn't wrap anymore with the nano -w option..... which can really screw something up.

I'm no vi power user at all and quite frankly was a bit overwhelmed at first since I had never really used vi much but the best thing to have is a quick reference sheet for vi in front of you for post installation configuration and the nice handy dandy NetBSD [Guide]("http://www.netbsd.org/docs/guide/en/index.html") for both during and after the installation.

> Sounds like Arch 

Yes the idea of starting out with a small base system and building it from there is similiar to the Arch philosophy but they are still two very different Os's. For example Arch is a rolling release distro with updates that one could say are on the bleeding edge while NetBSD is a more stable system and depending on which repo you use for pkgsrc, contains older more stable software which is a double edged sword in both aspects.

---

### Post by ayoli on 2008-09-30
> **C!oud said:**
> 
Yes the idea of starting out with a small base system and building it from there is similiar to the Arch philosophy but they are still two very different Os's. For example Arch is a rolling release distro with updates that one could say are on the bleeding edge while NetBSD is a more stable system and depending on which repo you use for pkgsrc, contains older more stable software which is a double edged sword in both aspects.

sounds like slackware :)

---

### Post by kk0sse54 on 2008-09-30
> **ayoli said:**
> sounds like slackware :)

Except with a package management system that automatically resolves dependencies ;)

---

### Post by crimesaucer on 2008-09-30
> **C!oud said:**
> I'm no vi power user at all and quite frankly was a bit overwhelmed at first since I had never really used vi much but the best thing to have is a quick reference sheet for vi in front of you for post installation configuration and the nice handy dandy NetBSD [Guide]("http://www.netbsd.org/docs/guide/en/index.html") for both during and after the installation.

Thanks, I'll check it out.


> you might want to check out some of the more "user friendly" OS's like PC-BSD

Well..... I like a challenge.... right now I use Archlinux (for a year now) with my own custom vanilla linux AMD64 kernel with a zen2 patch.... nice settings, cflags/mflags, 1000HZ timing..... I have about 80% of my computer compiled using custom CFLAGS/CXXFLAGS.... Firefox-optimized for my Turion64x2 TL-60.... xfce4 optimized....slim instead of GDM.... barely any gnome.... so basically everything is super fast.


I'm just wondering if the BSD's are as fast/or faster than Arch?


.... also to keep this on topic of screenshots, this is my newest Arch wallpaper that I made using a deviantART wallpaper from here: [http://mtbird.deviantart.com/art/Striped-99008447](http://mtbird.deviantart.com/art/Striped-99008447)

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-19-1.png[/IMG]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-19.jpg](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-19.jpg)

---

### Post by techmarks on 2008-09-30
[URL="http://www.plot3d.net/scr01.png"][IMG]http://www.plot3d.net/scr01-s.png[/IMG]
[/URL]

FreeBSD 7.0 with Ice Window Manager and the Rox desktop.

:mrgreen:

---

### Post by kk0sse54 on 2008-09-30
> **crimesaucer said:**
> 
[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-19-1.png[/IMG]


Hey can you post your conky? As for things being fast or not, take away most of the factors like DE's and WM's installed and what's left between the two base systems I really do not know which one would be faster. You could probably do some sort of benchmark test if you're really interested otherwise it's just a matter of opinion.

---

### Post by crimesaucer on 2008-09-30
> **C!oud said:**
> Hey can you post your conky? As for things being fast or not, take away most of the factors like DE's and WM's installed and what's left between the two base systems I really do not know which one would be faster. You could probably do some sort of benchmark test if you're really interested otherwise it's just a matter of opinion.

Yeah, I was just looking at a comparison of FreeBSD and NetBSD, I think I would probably try FreeBSD first just because it was modular and had more file system options: [http://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems#General_information](http://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems#General_information)


They both look solid, and might be something new to try.


Here is my conky script, it uses the font called eurofurence:

```

# Archlinux-CONKY
# A comprehensive conky script, configured for use on
# Archlinux, without the need for any external scripts.
#
# Based on the conky settings and conky variables web pages.
# INCLUDES:
# -cached memory, uptime, date/time, file system stats, nvidia temp , dual core
# 
#
# 
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
#own_window_type normal
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
# I think the "use spacer" option only works with mono fonts.
use_spacer none
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=4
xftfont eurofurence:size=10

# Update interval in seconds
update_interval 1.0

# Minimum size of text area

minimum_size 855 

maximum_width 200


# Draw shades? was no
draw_shades yes

# Text stuff
# amplifies text if yes was no
draw_outline no 
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase


# border margins
#border_margin 0

# border width
#border_width 0

# Default colors and also border colors
#default_shade_color a7d9a3
default_outline_color FF00F9
default_color FFFFFF



# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 0
gap_y 10
	

# Text alpha when using Xft
xftalpha 1


# drawn 1 pixel border around graphs or not was no on screenshot guide
draw_graph_borders no

# stuff after 'TEXT' will be formatted on screen


TEXT
${time %b %d %Y}${alignr 3}${time %l:%M %p}${font}
Uptime${alignr 3}${uptime}

Archlinux${alignr 3}${kernel}

Arch x86_64${alignr 3} ${fs_size}
${offset 24}used =${alignr 3}${fs_used}
${offset 24}free =${alignr 3}${fs_free}
Vista 64bit${alignr 3} ${fs_size /mnt/windows}
${offset 24}used =${alignr 3}${fs_used /mnt/windows}
${offset 24}free =${alignr 3}${fs_free /mnt/windows}

Nvidia Gpu:
${execi 1 nvidia-settings -q [GPU:0]/GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2} Celsius
CPU Core0:  
${execi 1 sensors | grep "Core0" | cut -c14-20}
CPU Core1:  
${execi 1 sensors | grep "Core1" | cut -c14-20}

${alignc}-CPU ${freq_g cpu0}  GHz-

-CPU0 ${cpubar cpu0 10,100 FFFFFF FFFFFF}${alignr 3} ${cpu cpu0}%
-CPU1 ${cpubar cpu1 10,100 FFFFFF FFFFFF}${alignr 3} ${cpu cpu1}%

${top name 1}${alignr 3}${top cpu 1}%

${top name 2}${alignr 3}${top cpu 2}%

${top name 3}${alignr 3}${top cpu 3}%

${top name 4}${alignr 3}${top cpu 4}%

${top name 5}${alignr 3}${top cpu 5}%

${top name 6}${alignr 3}${top cpu 6}%

${alignc}-MEM-
-RAM TOTAL  ${alignr 3}${memmax}
-RAM        ${alignr 3}${mem}
-CACHE      ${alignr 3}${cached}
-SWAP TOTAL ${alignr 3}${swapmax}
-SWAP       ${alignr 3}${swap}

${top_mem name 1}${alignr 3}${top_mem mem 1}%

${top_mem name 2}${alignr 3}${top_mem mem 2}%

${top_mem name 3}${alignr 3}${top_mem mem 3}%

${top_mem name 4}${alignr 3}${top_mem mem 4}%

${top_mem name 5}${alignr 3}${top_mem mem 5}%

${top_mem name 6}${alignr 3}${top_mem mem 6}%


``` 


EDIT: I cleaned it up a bit.

---

### Post by kk0sse54 on 2008-09-30
Sweet thanks :D ,FreeBSD makes a great system too, polishlinux.org is great in allowing one to compare OS's

---

### Post by crimesaucer on 2008-09-30
> **C!oud said:**
> Sweet thanks :D ,FreeBSD makes a great system too, polishlinux.org is great in allowing one to compare OS's

Thanks for polishlinux.org

Yeah, I'm really liking the ABS ports system of Arch, I pretty much use it and the AUR exclusively to build from source with my custom flags.


But it's nice to have regular pacman and the repo's as a solid backup.

---

### Post by savagenator on 2008-09-30
Here is my desktop. Arch linux, with gnome, avant window navigator, a conky stolen from page 110 in this thread (notice i haven't configured it yet. Credit crimesaucer for it)


[[IMG]http://img20.imageshack.us/img20/2015/desktopgnopmemacct0.th.png[/IMG]](http://img20.imageshack.us/my.php?image=desktopgnopmemacct0.png)[[IMG]http://img20.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Notice my RAM usage....

---

### Post by crimesaucer on 2008-09-30
> **savagenator said:**
> Here is my desktop. Arch linux, with gnome, avant window navigator, a conky stolen from page 110 in this thread (notice i haven't configured it yet. Credit crimesaucer for it)


[[IMG]http://img20.imageshack.us/img20/2015/desktopgnopmemacct0.th.png[/IMG]](http://img20.imageshack.us/my.php?image=desktopgnopmemacct0.png)[[IMG]http://img20.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Notice my RAM usage....

Not stolen.... given. Enjoy.


..... also, if anybody liked my Murrine gtk from a few pages back, here is a link to the gtkrc that I made: [http://crimesaucer.deviantart.com/art/MurrineNEW-silver-99217330](http://crimesaucer.deviantart.com/art/MurrineNEW-silver-99217330)

icons: [http://crimesaucer.deviantart.com/art/MurrineNEW-silver-buttons-99437382](http://crimesaucer.deviantart.com/art/MurrineNEW-silver-buttons-99437382)

I wish I could share the icons, but gnome-looks.org had a limit on upload sizes and I don't feel like finding a web host.

---

