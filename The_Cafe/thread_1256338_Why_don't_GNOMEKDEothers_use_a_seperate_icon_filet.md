---
title: "Why don't GNOME/KDE/others use a seperate icon filetype?"
date: 2009-09-02
forum: The Cafe
---

### Post by Fzang on 2009-09-02
Sorry, I am not sure where else I could get some sort of an answer, so I'm posting here.

First, tl;dr - Why doesn't Linux use a real icon format instead of .svg and .png?

Now to the wall...

Why in the world does Linux desktop environments use .svg and .png for icons throughout the system? Both Windows and Mac OS use specific icon files to store multiple icons in one. The advantages of an icon file such as .ico and .icns is that they contain all the icon images in one file, instead of 3 or 4 separate images in many separate directories, for 16px, 32px, 48px and above. As Linux is highly customizable in every aspect I don't see why we have to change the icon in 5 different locations to see the full effect.

I understand that .svg is scalable and can be upscaled to enormous sizes if desired, but is this really necessary? .ico and .icns can contain small and sharp sizes as well as large and detailed sizes.

---

### Post by juancarlospaco on 2009-09-02
Because on Linux, File extension doesn't matter.
*Can be .png .svg .ubuntu .lol .nothing*

It uses magic numbers.

---

### Post by JillSwift on 2009-09-02
Why write a whole new decoder library for an icon image format when all those other open standard libraries already exist? Why create a new editor for icon formats when GIMP and InkScape already exist?

SVG, being vector graphics, are so much smaller than raster graphic files, and scale well enough to cover the range very well, so it saves a lot of space.

On the whole, given reduced coding time, reduced library clutter, and reduced need for specialty applications, I think the GNOME/KDE/etc. way is a bit better.

---

### Post by Mark76 on 2009-09-02
I'd like to know why they don't just use .svgs by default and get rid of all those redundant .png and .xpm icons in different sizes.

---

### Post by SunnyRabbiera on 2009-09-02
I will also say that I think the Linux icon format is better then Windows or OSX because you dont need a special editor to edit the icons on your system.

> **Mark76 said:**
> I'd like to know why they don't just use .svgs by default and get rid of all those redundant .png and .xpm icons in different sizes.

I dunno there might be some good reason for keeping .png and .xpm

---

### Post by JillSwift on 2009-09-02
> **Mark76 said:**
> I'd like to know why they don't just use .svgs by default and get rid of all those redundant .png and .xpm icons in different sizes.
I thought that's the way it was all headed, for a bit there. Then the .png files came rushing back in. Perhaps the artists just like GIMP (or other raster image program) better.

---

### Post by RiceMonster on 2009-09-02
Yeah I think it would make a lot of sense, so having a bunch of files for different sizes could be eliminated, but the disadvantage would be what SunnyRabbiera said here:

> **SunnyRabbiera said:**
> I will also say that I think the Linux icon format is better then Windows or OSX because you dont need a special editor to edit the icons on your system.

However, I wonder how hard this would be to have implemented in inkscape or the gimp or something? Probably not too hard. I could see it being implemented if freedesktop.org adopted it as a standard. Who knows?

---

### Post by Dragonbite on 2009-09-02
I like the .svg idea.

The only reason I could see going with a .ico is if there is a difference in rendering speed or weight on the desktop environment.

---

### Post by Skripka on 2009-09-02
> **JillSwift said:**
> 

SVG, being vector graphics, are so much smaller than raster graphic files, and scale well enough to cover the range very well, so it saves a lot of space.


Vector graphics, by definition, scale infinitely :)

---

### Post by Fzang on 2009-09-02
If your system runs slower because it has to render .ico instead of .svg you really really REALLY need a new computer. 1 MB more or less system-wide does not matter in 2009.

And I don't know what's meant with "special editor". It's only special because no one has made it yet. Mac OS comes with all the tools (except an actual image editor like PS or GIMP) to view icons in different sizes and compose them together. Windows fails with the preinstalled software, like always.

I don't see why these "special editors" are somehow impossible to develop for Linux.

---

### Post by Whiffle on 2009-09-02
Why limit yourself to the finite number of sizes you can stick in an ico file, when you can use an svg and have any and every size, with no increased demand on memory?  

Multiple size directories with png's are easily dealt with a script, and perform the same thing as having multiple sizes in an ico file, without having a specialized editor/file format.

I guess I just don't see what advantage there is to something like an ico format.

---

### Post by Perfect Storm on 2009-09-02
I like how it is now. Morely (is that word?) because I custom diffrent sets of icons depending on their sizes. I uses diffren types of icons for 16x16 and 22x22 because (most) stylish icons looks bad at that size. Therefore changed them to something simpler and cleaner for that sizes.


Here's what I'm talking about; [http://www.imageviper.com/displayimage/143116/0/Kubuntu-kde4.3-290809-02.png](http://www.imageviper.com/displayimage/143116/0/Kubuntu-kde4.3-290809-02.png)
Note the system tray icons. They are simple compared the rest.

---

### Post by JillSwift on 2009-09-02
> **Skripka said:**
> Vector graphics, by definition, scale infinitely :)
In the context of vectors, yes.

But as those vectors must be rasterized, you bump into the problem of aliasing at smaller sizes. That's what I mean when I say "well enough", the smaller sizes occasionally leave a little something to be desired.

---

### Post by JillSwift on 2009-09-02
> **Fzang said:**
> If your system runs slower because it has to render .ico instead of .svg you really really REALLY need a new computer. 1 MB more or less system-wide does not matter in 2009.

And I don't know what's meant with "special editor". It's only special because no one has made it yet. Mac OS comes with all the tools (except an actual image editor like PS or GIMP) to view icons in different sizes and compose them together. Windows fails with the preinstalled software, like always.

I don't see why these "special editors" are somehow impossible to develop for Linux.
Never assume that a megabyte means nothing in any day and age. Being efficient means being supportive of more platforms. :)

Those special editors are in no way impossible, and no one made that claim. The question is: Why bother when the current system works just dandy and with less effort?

---

### Post by insane_alien on 2009-09-02
thats what anti-aliasing is all about.

---

### Post by Wolki on 2009-09-02
> **insane_alien said:**
> thats what anti-aliasing is all about.

But it makes things look blurry, especially at small sizes. See for example [http://www.firewheeldesign.com/sparkplug/2006/April/icon_design_bitmap_vs_vector.php](http://www.firewheeldesign.com/sparkplug/2006/April/icon_design_bitmap_vs_vector.php)

---

### Post by Skripka on 2009-09-02
> **JillSwift said:**
> In the context of vectors, yes.

But as those vectors must be rasterized, you bump into the problem of aliasing at smaller sizes. That's what I mean when I say "well enough", the smaller sizes occasionally leave a little something to be desired.

That is when ya need to get a bigger & better LCD panel, grasshopper.  That ain't a problem with your SVG icons, that is a hardware limitation imposed on them. ;)

---

### Post by JillSwift on 2009-09-02
> **Skripka said:**
> That is when ya need to get a bigger & better LCD panel, grasshopper.  That ain't a problem with your SVG icons, that is a hardware limitation imposed on them. ;)
Alternatively, I could just not wear my glasses. Then they'd be blurry at every size and I'd have no reason to complain ;)

---

### Post by MaxIBoy on 2009-09-02
I know Haiku has a vector format which is optimized to be efficient for small images. One of the developers put it this way (more or less, I can't remember exactly how he phrased it.) "If you use it for icons, it's fine, but if you use it for anything big with lots of detail, it's going to suck, big time." It was in a Google Tech Talk video, you could look it up if you wanted to.

So there's a pre-existing format for these.

However, I think that, in most cases, the benefits of using an existing standard outweigh the benefits of creating "yet another format." And with OpenVG soon to be hardware-accelerated in many video drivers, the overhead of rendering SVG will soon be negligible.

---

### Post by days_of_ruin on 2009-09-02
> **Mark76 said:**
> I'd like to know why they don't just use .svgs by default and get rid of all those redundant .png and .xpm icons in different sizes.

Because scaling an svg to small sizes looks like CRAP.

---

### Post by Gen2ly on 2009-09-02
> **Mark76 said:**
> I'd like to know why they don't just use .svgs by default and get rid of all those redundant .png and .xpm icons in different sizes.

> **Skripka said:**
> That is when ya need to get a bigger & better LCD panel, grasshopper.  That ain't a problem with your SVG icons, that is a hardware limitation imposed on them. ;)

Well imposing people to use specific hardware isn't very Linux-like ;).  Yeah, svg's don't scale well for small sizes so netbooks... would have problems with them.  I wondered why they just didn't use gimps native .xcf and just use layers like .ico's do instead of having a number of scattered icons in several places.  Hopefully this is something developers are thinking about.

---

### Post by Tipped OuT on 2009-09-02
> **Gen2ly said:**
> Well imposing people to use specific hardware isn't very Linux-like ;).  Yeah, svg's don't scale well for small sizes so netbooks... would have problems with them.  I wondered why they just didn't use gimps native .xcf and just use layers like .ico's do instead of having a number of scattered icons in several places.  Hopefully this is something developers are thinking about.

+1

Very messy having 70+ icons (and the majority of them are the same icons in different sizes) in one folder.

Open up your minds, accept change. Change is good. ;)

---

### Post by Warpnow on 2009-09-03
A unified package for multiple icons would be better, but no proprietary format. A tgz file with an xml file and the icons would do well.

---

### Post by Exodist on 2009-09-03
SVG are my fav choose, but SVGs are slighty harder to draw. At least for me I have heck of a time in Inkscape. But I can work GIMP like magick. So theres why we have multiple choices.

---

### Post by Fzang on 2009-09-03
Quality at small sizes does matter, just as much as the bigger sizes. While big sizes emphasize on quality the small sizes emphasize on sharpness.

Take a look at this:

[IMG]http://pixelresort.com/external/manila.png[/IMG]

I think it's a common belief that "with .svg I can just up/downscale my icons all I want, yay". The truth is, to make a good icon you make **a lot** of good icons of different sizes, and then merge them together into one icon. Each size is a new icon and tells its own story.

Quality should never be lowered, regardless the work it takes. Every application in Mac OS has its own beautiful and highly detailed icon. Maybe it takes much longer to make these icons, instead of someone pulling off a one-man-full-icon-set for linux, but in the end it really pays off IMO. If you don't start you'll never hit the finish line anyway.

---

### Post by JillSwift on 2009-09-03
I'm thinking a fab way about it would be png icons for 22x22 and 16x16 (perhaps 32x32 as well), with an svg to handle anything larger.

big plus: We can do that now =^_^=

---

### Post by lykwydchykyn on 2009-09-03
> **Warpnow said:**
> A unified package for multiple icons would be better, but no proprietary format. A tgz file with an xml file and the icons would do well.

So in other words, add an extra layer of processing to every loading of an icon just because someone doesn't like the idea of having a folder full of icons somewhere on his/her system?

I'm all for change and improvements (yay svg!) but I don't see a compelling problem with the current system...

Frankly I don't like the way icons are bundled up in Windows.  I hate playing "guess-which-dll-contains-the-icon" when I need to put a custom icon on a shortcut.  With discrete files, I can search or browse for the file I need.

---

### Post by Chronon on 2009-09-03
> **lykwydchykyn said:**
> 
Frankly I don't like the way icons are bundled up in Windows.  I hate playing "guess-which-dll-contains-the-icon" when I need to put a custom icon on a shortcut.  With discrete files, I can search or browse for the file I need.

Good point.

---

### Post by Chronon on 2009-09-03
> **Skripka said:**
> That is when ya need to get a bigger & better LCD panel, grasshopper.  That ain't a problem with your SVG icons, that is a hardware limitation imposed on them. ;)

The basic point remains, though.  You lose fidelity when trying to encode a path as a set of pixels as the number of pixels becomes small.  You have no such problem when scaling up since a large collection of pixels approximates a continuum of points.

---

### Post by Gen2ly on 2009-09-03
Hmm, maybe we should bring this to the [GNOME Usability Project]("http://live.gnome.org/UsabilityProject") which maintains the GNOME Human Interface Guidelines.  Be interested to see if they got something like this in the works.

---

### Post by Fzang on 2009-09-04
> **lykwydchykyn said:**
> So in other words, add an extra layer of processing to every loading of an icon just because someone doesn't like the idea of having a folder full of icons somewhere on his/her system?

You seriously need a new computer then. The subject is not to maintain backwards compatibility back to 1990. Even hardware advances.

> **lykwydchykyn said:**
> Frankly I don't like the way icons are bundled up in Windows. I hate playing "guess-which-dll-contains-the-icon" when I need to put a custom icon on a shortcut. With discrete files, I can search or browse for the file I need.

Icon libs aren't necessarily required, I don't even think Mac OS uses them.

---

### Post by Xbehave on 2009-09-04
> **Fzang said:**
> You seriously need a new computer then. The subject is not to maintain backwards compatibility back to 1990. Even hardware advances.
why make something perform worse, just because you can?
svgs have there places, but fixed size pngs are best suited for icons everywhere (some people use linux/gnome on old/embeded systems/phones.

> A unified package for multiple icons would be better, but no proprietary format. A tgz file with an xml file and the icons would do well.
Erm that is what we have look around, [http://www.kde-look.org/index.php?xcontentmode=27](http://www.kde-look.org/index.php?xcontentmode=27)
a tar.gz file containing a index.theme file (which is just a specially formated txt file, no need to use XML on something this simple.

---

### Post by lykwydchykyn on 2009-09-04
> **Fzang said:**
> You seriously need a new computer then. The subject is not to maintain backwards compatibility back to 1990. Even hardware advances.

I'm just not seeing the compelling advantage, regardless of whether the processing cost in question is deemed significant.  Everything adds up.

So explain to me why we need this change?

---

### Post by jonian_g on 2009-09-04
> **lykwydchykyn said:**
> I'm just not seeing the compelling advantage, regardless of whether the processing cost in question is deemed significant.  Everything adds up.

So explain to me why we need this change?

To make icon developers life harder! The system we have is the best for me.
I create icons and the proccedure I follow is:
Create an icon in all sizes in one single svg. Then use a script to export ,the big sized one in svg and the others in png, and in their folders.

That is a very easy way to create icons. I can for example create 100 icons in svg, run the script once (excactly this command -> ./render.py *.svg) and have 100 icons in different sizes placed in the appropriate folders.

See how it works: [http://jimmac.musichall.cz/log/?p=436](http://jimmac.musichall.cz/log/?p=436)

---

### Post by Mornedhel on 2009-09-04
> **Fzang said:**
> You seriously need a new computer then. The subject is not to maintain backwards compatibility back to 1990. Even hardware advances.

Icon libs aren't necessarily required, I don't even think Mac OS uses them.

You're contradicting yourself.  If you want the extra layer, which you'll get if you use a new or existing mipmap format, you'll need an icon library.  No way around it.  You need some way of opening the icon file and extracting the bitmap you want.  You need libs to open image files as well, by the way (look at all the libpng-*, libjpeg-*, etc. packages), so using a different library wouldn't add significant overhead other than the process of extracting the correct bitmap from your mipmap icon.  I have no idea how computationally expensive it is to render vector graphics.

I agree that SVG files will look like crap at low resolutions, but by your own admission, hardware advances, so low resolutions will soon not be a problem anymore, right ?

(Another poster said already that SVG looks bad at low resolutions. I'll add that when scaled up too much, SVG also begins to look too vector-y -- you're expecting to see some details on an image of that size.)

But seriously, what's the big difference between /icons/everything_in_a_file.ico and /icons/everything_in_several_folders/size/this_size.ico ?

---

### Post by Gen2ly on 2009-09-04
> **jonian_g said:**
> To make icon developers life harder! The system we have is the best for me.
I create icons and the proccedure I follow is:
Create an icon in all sizes in one single svg. Then use a script to export ,the big sized one in svg and the others in png, and in their folders.

That is a very easy way to create icons. I can for example create 100 icons in svg, run the script once (excactly this command -> ./render.py *.svg) and have 100 icons in different sizes placed in the appropriate folders.

See how it works: [http://jimmac.musichall.cz/log/?p=436](http://jimmac.musichall.cz/log/?p=436)

I think the point being that it would be handier to just edit or build one single file than to edit organize a whole bunch of them.  Icon artists don't necessarily know how to script or should have to.  To have a single file with layers (for example) that have multiple png sizes and an svg would be very handy to edit and create.

---

### Post by MikeTheC on 2009-09-04
I would far prefer ANY OS use SVG and PNG as their principle icon formats because it allows one to create an image that's either vector or raster in nature without needing to be compatible with some platform-centric data format or, as Jill has already pointed out up-thread, another decoder library having to be created.

And besides, what makes the OP think you need multiple files for icons? You can use any size image (AFAIK with no or no significant restriction) as your icon source, and Gnome, etc., will scale it as appropriate.

What's the problem? I fail to see one.

---

### Post by JillSwift on 2009-09-04
> **Gen2ly said:**
> I think the point being that it would be handier to just edit or build one single file than to edit organize a whole bunch of them.  Icon artists don't necessarily know how to script or should have to.  To have a single file with layers (for example) that have multiple png sizes and an svg would be very handy to edit and create.
That script already exists, though. The icon artist doesn't need to know scripting or programming.

It still boils down to one thing: What's the advantage of adding additional computing time and an additional layer of complexity when storing the icons in folders achieves the same thing?

---

### Post by kirsis on 2009-09-04
Why is this even a discussion?

Ico has less features than other, more modern formats, and there's no advantage at all to using it for icons.

If the only thing you dislike is the folder clutter and want to pack em together, well, there's a format for that too, and it's called Tar. (why icons are not packed on gnome is another question. I don't know nor do i think it matters, but the means are there, without using a new format). 

Sometimes it's ok to reinvent the wheel, if you end up with a better wheel. However Tar and existing image formats is something so fundamental and cover so many use cases there's really no need to come up with something new.

---

### Post by Gen2ly on 2009-09-04
> **JillSwift said:**
> That script already exists, though. The icon artist doesn't need to know scripting or programming.

It still boils down to one thing: What's the advantage of adding additional computing time and an additional layer of complexity when storing the icons in folders achieves the same thing?

I hear what you're saying, Jill.  I would wonder if the graphic artist would know about it though.  I don't think I'd be too far off thinking that most icon artists now probably: create each icon individual, save that icon (after navigating several folders), and then move that folder after creating the appropriate directories...  It is common now for companies to provide artists with environments that enable creativity as artists are either poor at it or are just not concerned about the peculiarities that are needed to do so.

> **kirsis said:**
> Why is this even a discussion?

kirsis, I'm thinking you haven't read the thread.

> **kirsis said:**
> Ico has less features than other, more modern formats, and there's no advantage at all to using it for icons.

What features you talking about?  Could you define 'more modern formats'?  Anyhow, if you read the thread you know that we aren't discussing using the .ico format but trying to discover how to build icons quicker with less management tasks.

> **kirsis said:**
> If the only thing you dislike is the folder clutter and want to pack em together, well, there's a format for that too, and it's called Tar....

Well, this necessarily isn't such a bad idea.  Since I don't think that GIMP supports vector graphics putting a wrapper around the png and svg files (basically what a .tar is) isn't such a bad concept.

---

### Post by JillSwift on 2009-09-04
> **Gen2ly said:**
> I hear what you're saying, Jill.  I would wonder if the graphic artist would know about it though.  I don't think I'd be too far off thinking that most icon artists now probably: create each icon individual, save that icon (after navigating several folders), and then move that folder after creating the appropriate directories...  It is common now for companies to provide artists with environments that enable creativity as artists are either poor at it or are just not concerned about the peculiarities that are needed to do so.
I think you're underestimating artists. Any good artist gets to know the medium, and it's not like folks are hiding the tools that make it all easier.

On the other hand, making a new format and the tools necessary to editing that format produces *exactly* the same situation. Only one factor worse, it's not obvious how to edit the new format. GIMP and to a lesser degree InkScape are commonly installed because they are broadly useful. Editing a png or svg is then a matter of a double-click. But something as specific as an icon specialty file editor... well, you'd have to learn about that before you could even get started.

---

### Post by Fzang on 2009-09-05
> **Mornedhel said:**
> You're contradicting yourself.  If you want the extra layer, which you'll get if you use a new or existing mipmap format, you'll need an icon library.  No way around it.  You need some way of opening the icon file and extracting the bitmap you want.  You need libs to open image files as well, by the way (look at all the libpng-*, libjpeg-*, etc. packages), so using a different library wouldn't add significant overhead other than the process of extracting the correct bitmap from your mipmap icon.  I have no idea how computationally expensive it is to render vector graphics.

Sorry, I must've expressed myself in an unclear manner. With icon library I mean the libraries that bind them together, such as .dll and .icl on windows, not system libraries.

> **MikeTheC said:**
> And besides, what makes the OP think you need multiple files for icons? You can use any size image (AFAIK with no or no significant restriction) as your icon source, and Gnome, etc., will scale it as appropriate.

I'm sorry, but I think you've missed the whole art/design thing. Go read up here [http://psd.tutsplus.com/articles/7-principles-of-effective-icon-design/](http://psd.tutsplus.com/articles/7-principles-of-effective-icon-design/) or something...

---

### Post by kirsis on 2009-09-07
> **Gen2ly said:**
> 
kirsis, I'm thinking you haven't read the thread.


My apologies, I indeed glanced over a few posts only. From the first post I got the impression that the OP is advocating the use of a special-purpose icon library format (not necessarily .ico).

As for the actual issue, I suppose that should be up to artists. As the icon end user, I don't have to deal with the filesystem nor do I want to. It works for me. If the artists prefer to pack em up, then by all means.

Some people have mentioned that a packed icon library would create unnecessary overhead. This is not necessarily true. The tar format is not compressed, so there is barely any overhead in extracting the icons (no point in gzipping, for example, the icon archive since the images are already in an optimized format). 

Keep in mind that icons in a tar archive would be all stored in one place on the hdd and could be read in one fell swoop, wheras reading icons stored as seperate files might require the storage device to perform more operations to read em (seeking operations).

I'm no expert on storage devices, of course, but I believe that whatever small overhead there'd be from reading tar archives, would be offset by the possibility of reading all the icons in one read operation.

Also, GTK likely provides API functions for loading icons, so a change in the system shouldn't afect any existing apps.

To sum my opinion up - it's up to icon creators. End-users are unlikely to have good reasons to want a change in the way icons are stored.

---

### Post by Mornedhel on 2009-09-07
> **kirsis said:**
> As for the actual issue, I suppose that should be up to artists. As the icon end user, I don't have to deal with the filesystem nor do I want to. It works for me. If the artists prefer to pack em up, then by all means.

It affects developers and end users too. *You* may not want to deal with the filesystem, but Linux is meant to be tinkerer-friendly.

> **kirsis said:**
> Some people have mentioned that a packed icon library would create unnecessary overhead. This is not necessarily true. The tar format is not compressed, so there is barely any overhead in extracting the icons (no point in gzipping, for example, the icon archive since the images are already in an optimized format).

This is true. There is also no advantage to using a tar containing a hierarchy of folders, instead of manipulating the hierarchy directly.

> **kirsis said:**
> Keep in mind that icons in a tar archive would be all stored in one place on the hdd and could be read in one fell swoop, wheras reading icons stored as seperate files might require the storage device to perform more operations to read em (seeking operations).

This is also true, but I can think of no situation where it might be useful to load at once all icons from a theme, or all icon sizes from an icon. Icons are typically fetched only when necessary. There is no point in creating a buffer and filling it with all your icons.

> **kirsis said:**
> Also, GTK likely provides API functions for loading icons, so a change in the system shouldn't afect any existing apps.

Unfortunately, there are still apps out there that do not use the GTK API for everything. The way it is now, icons don't need to be packaged differently for other toolkits, too.

> **kirsis said:**
> To sum my opinion up - it's up to icon creators. End-users are unlikely to have good reasons to want a change in the way icons are stored.

Icon creators won't care, developers will. Artists are just that : people with the creative skills to produce artistic works, for instance icons. If an artist happens to be a developer, good for him, but don't assume all artists are developers and vice-versa.

---

### Post by kirsis on 2009-09-07
> **Mornedhel said:**
> It affects developers and end users too. *You* may not want to deal with the filesystem, but Linux is meant to be tinkerer-friendly.


Gnome may be meant to be tinker friendly, Linux is definitely all about being practical.

However, Gnome has never struck me as being very tinker friendly either; other aspects usually take precedence and sometimes eliminate the "tinker-friendly" aspect completely (hence its reputation as being less configurable than KDE).

Micromanaging icons is an activity that, I suspect, will be of interest to the absolute minority of users (not talking about installing icon themes here, which is something a lot of people do and is unrelated). In my opinion this absolute minority (of which the majority are likely icon artists) can be inconvenienced (managing packed icons is not any less tinker-friendly than managing a hierarchy in the file system) if that eases the job of those who create the icons.

> **Mornedhel said:**
> 
This is true. There is also no advantage to using a tar containing a hierarchy of folders, instead of manipulating the hierarchy directly.


The sole advantage I can think of is that all the icons for a specific application can be replaced/moved/copied by replacing/moving/copying one file. Also, I don't suppose a folder hierarchy is necessary in TAR. I suspect a strict naming scheme would suffice.


> **Mornedhel said:**
> 
This is also true, but I can think of no situation where it might be useful to load at once all icons from a theme, or all icon sizes from an icon. Icons are typically fetched only when necessary. There is no point in creating a buffer and filling it with all your icons.


True. 


> **Mornedhel said:**
> 
Unfortunately, there are still apps out there that do not use the GTK API for everything. The way it is now, icons don't need to be packaged differently for other toolkits, too.


Indeed. A change would require a change in the FreeDesktop specification and then there'd be a transition period where some apps would occasionally have missing icons.

This is a good reason not to change anything.

> **Mornedhel said:**
> 
Icon creators won't care, developers will. Artists are just that : people with the creative skills to produce artistic works, for instance icons. If an artist happens to be a developer, good for him, but don't assume all artists are developers and vice-versa.

I don't know about the artists, but I don't see why developers would care much. Basically only the widget toolkits would need any changing, and I think the changes would be very minor. (as for apps that don't use their widget toolkit api to load icons - shame on them and maybe a change like this would encourage them to utilize their platform of choice properly).

So again - I can imagine only the icon creators being bothered about having to maintain a file hierarchy instead of a tar archive or vice-versa (no programming involved here). If they're not bothered, good. What we have now works very good.

---

### Post by ceramicm on 2009-09-07
> On the other hand, making a new format and the tools necessary to editing that format produces exactly the same situation. Only one factor worse, it's not obvious how to edit the new format.

> Why write a whole new decoder library... Why create a new editor for icon formats...

> And I don't know what's meant with "special editor". It's only special because no one has made it yet. 

I know the discussion has moved on past this a bit, but as far as .ico files go, I've never had any problems opening and editing them in GIMP--no new tools/libraries required.

---

### Post by Mornedhel on 2009-09-07
> **kirsis said:**
> Gnome may be meant to be tinker friendly, Linux is definitely all about being practical.

However, Gnome has never struck me as being very tinker friendly either; other aspects usually take precedence and sometimes eliminate the "tinker-friendly" aspect completely (hence its reputation as being less configurable than KDE).

Micromanaging icons is an activity that, I suspect, will be of interest to the absolute minority of users (not talking about installing icon themes here, which is something a lot of people do and is unrelated). In my opinion this absolute minority (of which the majority are likely icon artists) can be inconvenienced (managing packed icons is not any less tinker-friendly than managing a hierarchy in the file system) if that eases the job of those who create the icons.

I don't think Gnome was ever meant to be tinker friendly, but Linux certainly was, and still is. Being tinker friendly is a good part of being practical : it means you have access not only to high-level applications, but low-level tools as well. (Gnome definitely deserves its reputation of being less configurable than KDE, although KDE could do with a little less configurability sometimes...)

I agree that micromanaging icons, as you put it, will be of interest to almost no one. However, with the current scheme of things, it remains available. In my opinion, changing the icon system to a tar or tar-like system doesn't add any functionality and removes some (however seldom used).

> **kirsis said:**
> The sole advantage I can think of is that all the icons for a specific application can be replaced/moved/copied by replacing/moving/copying one file. Also, I don't suppose a folder hierarchy is necessary in TAR. I suspect a strict naming scheme would suffice.

A strict naming scheme would suffice, yes. It would also work instead of folder hierarchies, without bringing tar into the mix.

Moving all the icons for a specific application can still be achieved, with a folder hierarchy, simply by moving the top folder.

> **kirsis said:**
> I don't know about the artists, but I don't see why developers would care much. Basically only the widget toolkits would need any changing, and I think the changes would be very minor. (as for apps that don't use their widget toolkit api to load icons - shame on them and maybe a change like this would encourage them to utilize their platform of choice properly).

Artists would probably not care too much because it's not their job to package the icon set, it's the distribution maintainer's (in theory). Furthermore, as someone else on this thread has pointed out, tools are available to automate this process, so artists really don't have to do any work (besides the actual designing of icons, obviously).

Although I never tried packaging an icon set nor have I designed one, so if any icon designer reads this thread, let me know if I'm speaking out of my posterior.

As for developers, you have to remember that not everyone out there uses GTK+ or Qt, nor do they want to. The other day I wrote a (very dumb) elisp function to display notifications when my media player (emacs -- that's right, my media player is emacs) starts playing a new track. The notification displays the album cover art, or the emacs icon if no cover is available. As it is now, all I had to do was display a PNG. I don't use a toolkit to display icons, because I don't have one.

One last thing. Currently there is a fallback system of sorts for icons. Applications come with their own icon, but icon sets can override them and use an icon that is more in harmony with the icon set's overall theme. I think the fact that it can be possible to have to look in several places for the correct icon means that adding a layer (looking inside the tar file) could start being a significant overhead. I don't know if it can be necessary to look in more than two places, but if it is, icon loading might be significantly slowed.

---

### Post by Mark76 on 2009-09-07
Never mind the file format, how about someone gets to work producing an icon set that's less cartoony or less ripped off from OSX than most of the current ones?

---

### Post by Xbehave on 2009-09-07
> **Mark76 said:**
> Never mind the file format, how about someone gets to work producing an icon set that's less cartoony or less ripped off from OSX than most of the current ones?

Have a look [here]("http://www.kde-look.org/index.php?xcontentmode=22x27&PHPSESSID=b623e1e15b2a2ae407ecbad21137ca78"), personally i like oxygen!

> I agree that micromanaging icons, as you put it, will be of interest to almost no one. While I agree, one use immediately springs to mind, having a simple/hi contrast theme for small icons, but keep a nice detailed theme for larger ones, while you could produce a new theme for this just editing/renaming the files in your icon folders.

PNG for your common icon sizes = win
SVG for those places where the icon may need to be anysize = double win

---

