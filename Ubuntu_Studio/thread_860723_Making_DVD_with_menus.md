---
title: "Making DVD with menus"
date: 2008-07-15
forum: Ubuntu Studio
---

### Post by gaspard.leon on 2008-07-15
Hi,

I've been tasked with creating a set of 3 DVDs

The source files are (50 per DVD) in MP4 and QuickTime MOV format...

(So I'll need to transcode them into MPEG-2)

Then I need to create a menu system with around 8 categories and up to 12 titles per subcategory...

I usually use DeVeDe for single title DVDs and stuff as It's simple and does the transcoding for you... but it only supports up to 12 *NAMED* titles (one level menu system)...

I have tried tovid GUI for it's support of more complex menus but it was a little messy, I will probably use it if nothing else is better...

I have looked at KDE DVD Authoring Wizard, but:
[LIST]
[*] it's a KDE app, so if there is a GTK/GNOME app I would use that first..
[*] don't know if it's limited to a certain number of titles.
[*] I will be trying it anyway most likely.
[/LIST]

So:

1. What's a good all-in-one tool for this type of stuff?
2. Failing all-in-one are there GUI tools for transcoding batches and Authoring DVDs with "complex" menus?
3. Anyone have favourites?

Cheers,

Gaspard

---

### Post by stinger30au on 2008-07-15
i dont know if this may help you or not

[http://ubuntustudio.org/](http://ubuntustudio.org/)


it would be awesome if we could install this to our 8.04 install from the shell

---

### Post by stinger30au on 2008-07-15
ah ha!!

a little reading and i found it can be installed from shell

[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy)

yee-haw!

---

### Post by fenian on 2008-07-16
Take a look at [DVDStyler]("http://www.dvdstyler.de/") and ['Q' DVD-Author]("http://qdvdauthor.sourceforge.net/")

---

### Post by alegallo on 2008-07-16
I quote fenian, as long as we talk about DVDStyler ;)
It allows you to make multiple menus and also to use "vmMenus" (VMG menus) and "menus" (VTS menus). 
I am not quite sure about the difference, but I understood it's a kind of hierarchy; anyway there's a great deal of info on the .pdf manual ;)
And it works well for me, which helps ;)

---

### Post by gaspard.leon on 2008-07-16
Well in the end everything I used was either:

1. too simple and couldn't handle 50 titles
2. too complex to learn in one night, or annoying non-intuitive interface
3. buggy or not packaged so hard to install/resolve dependencies
4. no longer supported by the developers.

So I ended up using tovid... which surprisingly has the right balance of being easy to use and supporting all formats with being powerful enough to handle 50 title DVD with 8 menus

Using the tovid GUI (which unfortunately doesn't support saving files) I was able to whip up a script to transcode, scale, and author the first of 3 discs (I ran out of time)

So I didn't get any sleep, but I got 1 DVD authored, and fixed 4 bugs in tovid which was satisfying in itself.

mostly font/imagemagick related bugs.

but anyway the reason I didn't complete the other 2 discs is because upon running the long transcode for the second disc, I discovered a problem with the audio on about 10 of the files, the transcode was failing with some error... So now I've got to learn how to use the command lines of MEncoder or FFMpeg quickly to try and fix those files, and then I can continue...

I'm thinking I like the idea of tovid, a simple wrapper with a bit of power...

QDVDAuthor looked too hard for average use, and it didn't support all my input files out of the box.

MANDVD looked cool, but not quite powerful enough and the non-supported files again... I'm beginning to think that it might be good for someone to make an EASY gui encoder for batches of files... would make importing into the many authoring packages easier... I'll have to brush up on my linux development skills perhaps...

...

no sleep leads to long posts.

---

### Post by Terry19 on 2008-07-17
> **gaspard.leon said:**
> Hi,

I've been tasked with creating a set of 3 DVDs

The source files are (50 per DVD) in MP4 and QuickTime MOV format...

(So I'll need to transcode them into MPEG-2)

Then I need to create a menu system with around 8 categories and up to 12 titles per subcategory...

I usually use DeVeDe for single title DVDs and stuff as It's simple and does the transcoding for you... but it only supports up to 12 *NAMED* titles (one level menu system)...

I have tried tovid GUI for it's support of more complex menus but it was a little messy, I will probably use it if nothing else is better...

I have looked at KDE DVD Authoring Wizard, but:
[LIST]
[*] it's a KDE app, so if there is a GTK/GNOME app I would use that first..
[*] don't know if it's limited to a certain number of titles.
[*] I will be trying it anyway most likely.
[/LIST]

So:

1. What's a good all-in-one tool for this type of stuff?
2. Failing all-in-one are there GUI tools for transcoding batches and Authoring DVDs with "complex" menus?
3. Anyone have favourites?

Cheers,

Gaspard
I know how to do this. Find manDVD and install it. it works with linux and mac OS so i has to be good.

---

### Post by gaspard.leon on 2008-07-17
Well as usual it's a case of old packages... since the release version package of tovid is (v 031)
the SVN version of tovid has had most of those bugs fixed (I'm told 8 months ago...) LOL

oh well so I've downloaded the latest SVN tovid, and I've almost got it running I'll report back if it's fixed or better.

In either case, the end result was pretty good for that first disc, the menu works fine..

As I may have mentioned before, I tried MANDVD and it looked good, but it didn't handle my MOV and MP4 files... and it's little preview had no drag handle... otherwise looks very slick.

:popcorn:

---

### Post by alegallo on 2008-07-18
I still suggest DVDStyler, although I don't think it can handle .mov and .mp4 files.

I'm afraid you will have to transcode them first.

ManDVD is nice, but you can just build up 1 menu.
Moreover, in its menus you have to be really careful about spacing between the titles buttons.
I made them too near to each other, and my dvd box would select one and skip the next, jumping to the third one.

---

