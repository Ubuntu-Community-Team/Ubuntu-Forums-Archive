---
title: "Post your GRUB bootsplash image!"
date: 2006-06-20
forum: The Cafe
---

### Post by glotz on 2006-06-20
Howdy!

Just had a little laugh with [GRUB bootsplash images](https://help.ubuntu.com/community/GrubHowto#head-860336ddfd132cb25712427a8c583398cee6fd96) and GIMP'd together this:

Now, you post your schtuff! :shock:

---

### Post by aysiu on 2006-06-20
Modified from the Tux-Mania GDM/KDM themes' background.

---

### Post by glotz on 2006-10-28
Looks like splash images are rather unpopular... :)

---

### Post by aysiu on 2006-10-28
Two people have them!

---

### Post by rfruth on 2006-10-28
one day i'll get brave and add a custom XPM file ...

---

### Post by moffa on 2006-10-28
Here is mine. Its a nice ubuntu splash screen.

I think by default Ubuntu should have a grub splash screen.  Most people, including me, find the default black screen horrid.

---

### Post by Herman on 2006-10-28
Here are mine, these are made to fit the rectangle in the Grub menu in Edgy,  Dapper, and even updated Breezy  Ubuntu or Kubuntu. 
They leave lines of text easily readable.[IMG]http://users.bigpond.net.au/hermanzone/p15/Ubuntusplash.xpm[/IMG]
[URL="http://users.bigpond.net.au/hermanzone/p15/Kubuntusplash.xpm.gz"]
[/URL]

---

### Post by ember on 2006-10-28
> **aysiu said:**
> Modified from the Tux-Mania GDM/KDM themes' background.

Note to myself: I should steal this image ...

Looks great :)

---

### Post by hearnden on 2006-10-28
For people that made their own usplash image, what tool did you use to get the right palette?  The Ubuntu version of GIMP doesn't have that Palette Editor or whatever it is that lets you shift the colors around...  I'm just lucky that the palette I got from color indexing works ok with the text, progress bars etc etc.

---

### Post by glotz on 2006-10-28
You're wrong hearnden

[quote="[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)"]To get GIMP to use only a 14 color palette, right click on your file and press ALT+I and put 14 where it says "Generate Optimal Palette:" on the top of the menu. If ALT+I doesn't get you there then right click on the image and go to:

Image-->Mode-->Indexed

Specify you want 14 colors and then if you want (*recommended*) select NO DITHERING. This will tell the gimp not to try to guess colors in between areas. It is also possible that you tell them gimp what colors you want in your 14-color pallete, I actually had to do this for one of my images and I replaced a dark color for a light one. :) The GIMP ROCKS![/quote]

(actually the number of the colors can be up to 16 if no background colors are used)

---

### Post by glotz on 2006-10-28
Please edit your posts to **include both**, an attached **thumbnail** and an attached **file** as e.g. in my post. :) This will make this thread as easy to use as possible. I'm looking forward seeing many more gorgeous designs! Does Edgy come with a grub boot image by the way?

---

### Post by Dual Cortex on 2006-10-29
At what part of the boot sequence are these  splash screens supposed to appear? Only when you press ESC?

---

### Post by glotz on 2006-10-29
Yeah, you need to hit esc if you have the hiddenmenu in use. They're right there at the beginning when you select what kernel to boot.

---

### Post by picpak on 2006-10-29
[img]http://www.schultz-net.dk/images/grub/ubuntu.gif[/img]
[ubuntu.xpm.gz](http://www.schultz-net.dk/downloads/grub/ubuntu.xpm.gz)

---

### Post by hearnden on 2006-10-30
> **glotz said:**
> You're wrong hearnden

What I meant was that (according to [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)) there is a later version of GIMP (2.3.10, my up-to-date Ubuntu version is 2.2.11) that lets you rearrange the order/indices of the colours in the colormap by simple dragging.  

> 
The development version of GIMP (CVS or version 2.3.10 or later) has a new plug-in which lets you drag entries in the colormap (palette) to rearrange them. This plug-in is helpful in making these splash images. It is called "Rearrange Colormap" and is available in the image menu at Colors->Map->Rearrange Colormap. You _may_ have to save to a different format other than PNG though and convert back to PNG using a different program as the PNG export plug-in may rearrange the colormap.


This sounds like you just get GIMP to colour-index the image, then you can just drag the colours around according to the roles of each colour index (bg colour, progress bar colour, etc).  This sounds much easier than

[LIST=1]
[*]Letting GIMP apply colour indexing
[*]Recording on a piece of paper the colours GIMP decided to use
[*]Creating your own palette with those colours in the order you want
[*]Re-doing the colour indexing with the new palette
[/LIST]

which is the only way I can see in the current GIMP version to apply custom ordering to the palette that is generated from colour indexing.  Is there an easier way?

So what I was interested in hearing is, for people using the current version of GIMP in the repositories (2.2.11), if there is an easy way to let GIMP decide on which colours should be used in colour indexing, and then being able to manually specify the indices of those colours.

---

### Post by hearnden on 2006-10-30
Oh, whoops, my bad.  This thread is about GRUB bootsplash images, not USplash.... *sigh*

---

### Post by ice60 on 2006-10-30
i used this one when i had ubuntu, it matched the other stuff i'd done.
[http://www.gnome-look.org/content/show.php?content=35814](http://www.gnome-look.org/content/show.php?content=35814)

---

### Post by Footissimo on 2006-10-30
I use a GFXboot theme from [here](http://ubuntuforums.org/showpost.php?p=1272301&postcount=71)

Looks like this:

[img]http://www.ubuntuforums.org/attachment.php?attachmentid=12947&d=1153265746[/img]

---

### Post by 1slyfox on 2007-04-04
Here is one I worked on tonight.  Takes a bit of time getting something to look good with only a 14 color palette.  I'm a big Matrix fan.  The shaded area fits nicely in the grub border, hope you enjoy it.

Sly

---

### Post by FuturePilot on 2007-04-05
Here's mine

---

### Post by feldegast on 2007-04-24
i put my grub bootsplash here (to save duplication) 
[KDE Look : Kubuntu 7.04 Grub Bootscreen]("http://www.kde-look.org/content/show.php?content=56843")

[IMG]http://www.kde-look.org/CONTENT/content-pre1/56843-1.jpg[/IMG]

---

### Post by eracerbit on 2007-05-07
modified from the levitating gnu found at [http://www.gnu.org/graphics/meditate.html](http://www.gnu.org/graphics/meditate.html)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32071&stc=1&d=1178596619[/IMG]

---

### Post by eracerbit on 2007-05-08
Another grub bootsplash featuring Nevrax Design Team's levitating gnu ([http://www.gnu.org/graphics/meditate.html](http://www.gnu.org/graphics/meditate.html)). 
The shaded rectangle fits nicely in the OS selection box. Color scheme is intended to compliment the default ubuntu color scheme.
 
[img]http://ubuntuforums.org/attachment.php?attachmentid=32121&stc=1&d=1178669603[/img]

---

### Post by dangerousnerd on 2007-05-08
> **eracerbit said:**
> modified from the levitating gnu found at [http://www.gnu.org/graphics/meditate.html](http://www.gnu.org/graphics/meditate.html)



Nice.  Stealing this one... :)

---

### Post by eracerbit on 2007-05-08
dangerousnerd: thanks. im in the mood to do a few more of these, stay tuned ;)

this guy's next
[img]http://www.gnu.org/graphics/listen-tiny.jpg[/img]

---

### Post by sandman55 on 2007-05-08
I'm studying this and when I work it out I will put one on my PC. 
One question does the image carry through to get rid of the black screen prior to the logon? That screen is a worry after I make a change I worry that its all I will get.

---

### Post by eracerbit on 2007-05-08
> **sandman55 said:**
> One question does the image carry through to get rid of the black screen prior to the logon?

The image only appears on the grub boot menu (where you would pick from for example WinXP Pro / Ubuntu 7.04 Feisty Fawn ;) )

---

### Post by eracerbit on 2007-05-09
from [http://www.gnu.org/graphics/listen.html](http://www.gnu.org/graphics/listen.html)

[img]http://ubuntuforums.org/attachment.php?attachmentid=32128&stc=1&d=1178683955[/img]

---

### Post by eracerbit on 2007-05-09
chillax pt 2

[img]http://ubuntuforums.org/attachment.php?attachmentid=32132&stc=1&d=1178687188[/img]

---

### Post by Herman on 2007-05-09
Hello eracerbit, 
Hey, cool! Nice images - beautiful -  100%!  Thanks ! I'm grabbing a copy of each of  them !   :guitar:

Hello sandman55,
You asked:
> I'm studying this and when I work it out I will put one on my PC. 
One question does the image carry through to get rid of the black screen prior to the logon? That screen is a worry after I make a change I worry that its all I will get.The images will be showing 'behind' your Grub Menu __, as if your  Grub menu is transparent. You will still see the text box and the lines to select an operating system like in feldegast's illustration, and the splashimage will be in the background, replacing the blackness.

If you need Ubuntu specific instructions about how to put on of these in your PC, click the following link, [Add a splashimage to the GRUB menu]("http://users.bigpond.net.au/hermanzone/p15.htm#splash").  

Adding the  command for the splashimage to your /boot/grub/menu.lst file is quite simple, but it would still be a wise precaution to get yourself a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") first and have it ready before editing your /boot/grub/menu.lst. Sometimes even the best of us make our systems temporarily unbootable after we make a silly error when typing the line for the new splashimage. If you have a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") ready it won't be any problem. You can also boot up by using [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") if you don't have a Super Grub Disk, but it requires a little more learning.

Also explained in that first link is how to view your splashimages without needing to take the time to edit your menu.lst with the splashimage command. That saves a lot of time if you have several splashimage you want to try out.

Not mentioned in that first link,it is also possible to make yourself a grub bootsplash image slide show by downloading lots of these beautiful splashimages and making several copies of you menu.lst file and naming them sequentially. For example menu.lst, menu.lsta, menu.lstb, menu.lstc, and so on. Each copy of your menu.lst has a command for a different splashimage. You then add a 'configfile' command to your boot entries to direct grub to the next menu.lst and hence the next splashimage.  A 'configfile' command in your boot entries would look something like this,
```
configfile     (hd0,1)/boot/grub/menu.lsta
```
Where: (hd0,1) is your Ubuntu partition, replace this partition number with the correct number for your Ubuntu partition if your computer has different partition numbers.
And near the bottom of menu.lsta, you would insert,
```
configfile     (hd0,1)/boot/grub/menu.lstb
``` and so on...

Regards, Herman :)

---

### Post by eracerbit on 2007-05-09
> **Herman said:**
> Hello eracerbit, 
Hey, cool! Nice images - beautiful -  100%!  Thanks ! I'm grabbing a copy of each of  them !   :guitar:
Thanks, Herman! Can't take credit for the original designs of course but im glad you enjoyed the bootsplashes ;)

> **Herman said:**
> Not mentioned in that first link,it is also possible to make yourself a grub bootsplash image slide show...
Thanks for the tip =)

:edit:
Herman, SandMan: i've been changing my grub bootsplash all around these last couple days, and i haven't had to edit any grub config files. all you have to do to get grub to load a custom image is put anything.xpm.gz in the /boot/grub directory. Your whatever.xpm.gz can be a symlink to an xpm.gz in the /boot/grub/splashimages directory. Just thought i should share. ([http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image/](http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image/))
:/edit:

Out of curiosity: how many people viewing this thread found it irrelevant because they use Gfxboot?

---

### Post by ceelo on 2007-05-09
The popular DebBlue splash theme (except mine doesn't have the GNOME foot).

[img]http://img205.imageshack.us/img205/2228/grubgnomedebbluekx7.jpg[/img]

I'm going to use those GNU pics, I've seen them before but always in a smaller resolution. Thanks to eracerbit for posting them!

---

### Post by sandman55 on 2007-05-09
Thanks for your reply acerbit and thanks for your detailed reply Herman I will be making a Grub bootsplash image.
I have one more question Is there a way to replace the black screen that appears prior to login so that a person can see that some thing is happening not that a person thinks and sweats that they did some thing wrong

---

### Post by sandman55 on 2007-05-09
Thanks for that followup eracerbit.

---

### Post by sandman55 on 2007-05-11
Well here is my bootsplash for the moment.
I had some fun and games doing it. [This Page](http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image/) gave an automatic way of doing it but I wanted to do it manually so I did sudo apt-get install grub-splashimages (I realise now I should have changed that to my home directory) so with Alt + F2 gksudo nautilus I cut and pasted the folder to my home folder. Then I followed [Herman's guide](http://users.bigpond.net.au/hermanzone/p15.htm#splash) only I wasn't sure where in the Grub menu list to put it after a couple of attempts I found it was the top of the list this was made further complicated by the way my partitions are numbered it ended up being hd0,5 but my root partition is the third partition I would have thought it would be hd0,3 I have a 2 HDD's I checked them with Acronis Disk Director and GParted here is how Gparted see's them Its interesting how it see's the PATA Drive as SATA

First drive (PATA)
/dev/sda1   ntfs WinXP
/dev/sda2   extended
/dev/sda5   ntfs My Documents
/dev/sda6   ext Root
/dev/sda7   ext Home
/dev/sda8   Swap

Second drive (SATA)
/dev/sdb1   extended
/dev/sdb5   fat32 (Windows page file)
/dev/sdb6   ntfs  (WinXP backup)
/dev/sdb7   ntfs  (My Documents backup)
/dev/sdb8   fat32 (Ubuntu Windows go between)

in the first drive it skipped the numbering /dev/sda3 and /dev/sda4 and in the second drive it skipped /dev/sdb2 and /dev/sdb3 and /dev/sdb4.

Its not a real worry but I would be interested if someone can tell me why I had to choose hd05 instead of hd03 for my root partition and why gparted didn't number my partitions on my PATA drive sda1,2,3,4,5,6 and on my SATA drive sdb1,2,3,4,5.

As I said its not a worry just interesting. Thanks for any comments

---

### Post by sandman55 on 2007-05-11
Try again I had to change the permissions :)
Edit its late I will do this tomorrow
[img]http://ubuntuforums.org/attachment.php?attachmentid=32374&d=1178932097[/img]

---

### Post by DizzyTech on 2007-06-01
I call this "Winbuntu Splash".  Since I only designed it for my computer, it's horizontally shrunken to look better at 1280x800.

---

### Post by FuturePilot on 2007-06-01
I don't know if anyone knows about this but there's a secret grub splash image located in /usr/share/pixmaps/grub/ :p

---

### Post by dbbolton on 2007-06-01
it is NES time.

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/superc.png[/IMG]

[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/ff1.png[/IMG]

---

### Post by Herman on 2007-06-02
With all these beautiful splashimages people are posting I wanted to share some information about how to set the color for the text and rectangle and the selection bar in our grub menus to whatever colors we like.
This can really add the finishing touches to someone's splashimage efforts and help show any splashimage off to it's very best effect! 

The 'foregound' or our grub menu is the upper-left faces of the lettering and the big rectangle.
The 'background' includes the big selection bar we use to hilite the entry we want to boot as well as the shadows in the lower-right of each letter and the big rectangle.
The 'border' doesn't show up too much in my computers when I use a 640x480 pixel image but it does show a little column at the right of my monitor and a narrow line across the very bottom. It's black by default. I didn't show the use of the 'border' command in the example below but it works the same way as the other two and you can use it if you like, just add it the same as the other two.

We can set these colors by adding the appropriate commands in our /boot/grub/menu.lst files. For example something like this will do it, 
```
splashimage=(hd0,1)/boot/Ubuntusplash.xpm.gz
[COLOR=Red][B]foreground ffe4b5
background f4a460[/B][/COLOR]
```Here are links to a couple of sites where there are color charts for choosing our colors and the corresponding code we need to type in to our menu.lst files, 

Color Codes: [http://www.pitt.edu/~nisg/cis/web/cgi/rgb.html]("http://www.pitt.edu/%7Enisg/cis/web/cgi/rgb.html")

Web Diner's hex code color chart: [http://www.webdiner.com/annexe/hexcode/hexcode.htm](http://www.webdiner.com/annexe/hexcode/hexcode.htm)

It is a good idea (and saves a lot of time), to try out our color combinations out first using the same commands I just posted, but in [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
 (just press your 'c' key from your grub menu and type in those commands one at a time and hit 'enter', then 'Esc' to return to your Grub menu and check it out. You can duck backwards and forwards as many times as you like until you get your colors right.

Have fun everyone,
Regards, Herman :D

---

### Post by WakkiTabakki on 2007-06-02
Hi all
While on the subject, let me push a little for a a splash randomizing script I posted a while back... Didn't attract much attention, though...

[http://ubuntuforums.org/showthread.php?t=402874](http://ubuntuforums.org/showthread.php?t=402874)

Cheers
/N

---

### Post by dbbolton on 2007-06-02
> **Herman said:**
> With all these beautiful splashimages people are posting I wanted to share some information about how to set the color for the text and rectangle and the selection bar in our grub menus to whatever colors we like.
This can really add the finishing touches to someone's splashimage efforts and help show any splashimage off to it's very best effect! 

The 'foregound' or our grub menu is the upper-left faces of the lettering and the big rectangle.
The 'background' includes the big selection bar we use to hilite the entry we want to boot as well as the shadows in the lower-right of each letter and the big rectangle.
The 'border' doesn't show up too much in my computers when I use a 640x480 pixel image but it does show a little column at the right of my monitor and a narrow line across the very bottom. It's black by default. I didn't show the use of the 'border' command in the example below but it works the same way as the other two and you can use it if you like, just add it the same as the other two.

We can set these colors by adding the appropriate commands in our /boot/grub/menu.lst files. For example something like this will do it, 
```
splashimage=(hd0,1)/boot/Ubuntusplash.xpm.gz
[COLOR=Red][B]foreground ffe4b5
background f4a460[/B][/COLOR]
```Here are links to a couple of sites where there are color charts for choosing our colors and the corresponding code we need to type in to our menu.lst files, 

Color Codes: [http://www.pitt.edu/~nisg/cis/web/cgi/rgb.html]("http://www.pitt.edu/%7Enisg/cis/web/cgi/rgb.html")

Web Diner's hex code color chart: [http://www.webdiner.com/annexe/hexcode/hexcode.htm](http://www.webdiner.com/annexe/hexcode/hexcode.htm)

It is a good idea (and saves a lot of time), to try out our color combinations out first using the same commands I just posted, but in [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
 (just press your 'c' key from your grub menu and type in those commands one at a time and hit 'enter', then 'Esc' to return to your Grub menu and check it out. You can duck backwards and forwards as many times as you like until you get your colors right.

Have fun everyone,
Regards, Herman :D
great tip!

---

### Post by FuturePilot on 2007-06-02
> **dbbolton said:**
> great tip!
+1:)

---

### Post by Herman on 2007-06-03
Hello WakkiTabakki,
Thanks for that splash randomization script, that sounds like something worth trying out, it would make booting up more interesting., especially for everyone here who love splashimages. :D

I have another one or two commands that help with showing splashimages nicely.
If you have a nice splashimage but the rectangle in the grub menu that the operating system titles are printed in happens to be in the way of an important part of the picture, you can either make a new splashimage with the subject of the picture in a different spot, or you can move that rectangle.
The rectangle can be moved around somewhat and made larger or smaller too.

Grub's** viewport**  command is for controlling the position and size of the rectangle that the text fits inside in the Grub Menu when we use a splashimage. 

examples, 
viewport 0 0 66 16 
gives a small rectangle in the upper left of the screen.

viewport 3 3 80 30 
means you will have the largest rectangle in the middle of the screen

viewport 11 6 80 30 
gives you a large rectangle in the lower right of the screen

I couldn't get it to accept any numbers for a small rectangle in the lower right though, sorry. For in between settings you'll just have to fiddle around and experiment a little, like I did.

The syntax for viewport is like this,
viewport x0   y0   x1    y1

The numbers range between,
viewport 0-11 0-6 66-80 16-30

x0 sets the left-right positioning for the left side of the rectangle. 
In my tests the smallest number I could set for this parameter was 0 and the largest was 11,
although sometimes a number less than 11 had to be settled for, depending on the other parameters.

y0 sets the up and down position for the rectangle.
A 0 entered here makes the rectangle appear as close as possible to the top of the monitor.
The number 6 was the largest number I could get it to accept, which made the rectangle lower.

x1 can be in the range from 66-80 and sets the width of the rectangle. 

y1 can be a number in the range between 16 and 30 and sets the height for the rectangle.

This command can also be run from Grub's Command Line Interface to experiment with it until you get your viewport right for your splashimage.
After that you can add it to your /boot/grub/menu.lst somewhere around your splashimage command.

Another grub command that works when splashimages are used is: shade 0 and: shade 1 Those commands toggle the shadows under and to the right of the font and the rectangle. I like mine to always have the shade, I think it always looks better, but there are exceptions to every rule.

I think that's all the grub commands that helps splashimages about covered now, keep up the fantastic work all you wonderful splashimage artists! I'm not much of an artist myself so all I can help you with is this command line stuff.
Regards, Herman :D

---

### Post by Herman on 2008-12-07
**Making a splashimage from a photograph**
A black and white photograph of something makes a good splashimage.
We can use an image that's black and white already, or we can take a full color image and open it in GIMP and change it into black and white by converting it to 'grayscale'.
Just go 'Image'-->'Mode'-->'grayscale', in GIMP.

If we just try to use a full color photo as-is, we will lose a lot of the details of the picture when we convert it to indexed 14 color mode to turn it into a splashimage. (Most of them go all blurry, but sometimes we're lucky and it's not too bad).
By using a black and white photo and adding just one color to it to tint it, we can retain the shapes of the objects in the image much better.

Make sure you make a backup of the photo first, because turning it into a splashimage will ruin the image as a photo, and besides, if you make a mistake you can always just make another copy of the backup and start again.

I'm just using one I found on the internet. I went into Google and clicked on 'images', and did an image search for 'Tall Ships', and looked around until I found a nice big one I liked and then I downloaded it.

It's best to begin with an image that's 3/4 as high as it is wide, because the splashimage will be 640x480. A larger image can be cropped and resized smaller, but if it's a small image already, you might be limited with how much you can do with it.
If your image or photo doesn't have that ratio but you can crop it to that profile without ruining it then well and good. 
Photographers usually take photos with their subject about in the center.
For a good grub splash, the subject of the picture should be a little towards the lower left ideally, to be seen, because the text in the GRUB menu is mostly in the upper right.
If you have a nice large image to start with, you might be able to crop some of the left-hand side off the image so that the subject will be on the right-hand side.

The crop tool in GIMP can be started from GIMP's toolbox, or use the keyboard shorcut 'shift+c'. Click on the image and drag the crop tool diagonally from one corner to the other corner of the imaginary rectangle that you want to keep.
There is a field showing the dimensions in pixels for the cropped area at the bottom of the panel. Again, try to make it 3/4 as high as it is wide.
Nothing will happen until you press 'enter', so you can have a lot of tries before you get it right. Even then, you can use ctrl+z to go back if you need to.

If you need to scale the image, go 'Image'--'Scale Image', and then when you type in your new width, (640 pixels), the height field should automatically change to 480.
When you're ready, hit the 'scale' button and your image will be rescaled.

Okay, so now we have our photo changed into black and white, and cropped and/or resized to 640x480 pixels.
We will click 'save as' now and give the image a new name. You can name your image anything you like, but let's give it an '.xcf' filename extension for now. GIMP's native format is.xcf

Now for the next trick, we're going to tint the photo with some color.
With the .xcf copy of the image open in GIMP, go 'Image'-->'Mode', and select 'RGB'.
Open Firefox and Google '256 color chart', or use [this one]("http://www.eloquentvisions.com/html/mycolors.html"), to pick a color.
I'm picking out 'midnight blue, which the chart says is html code #191970.
To make GIMP load that color, I double-click on GIMP's color switcher, (it looks like two rectangles overlapping each other diagonally at the corners), and I type or paste in '191970' in the 'HTMLnotation' field, then click on the arrow button just below it to load the color, and click 'okay'.

You might want some other color, I'm working with a photo of a sailing ship, and blue seems like a good color for that. For a steam engine you might want brown to give it the antique look. Use any color you think will show the image off to the best effect.

In the 'Channels, Layers and Paths box, I add a new layer.
Then I go over to the toolbox and select the bucket fill tool, (or use the 'shift+b' keyboard shortcut for it).
I fill the new layer with midnight blue.
Then, looking in the 'Channels, Layers and Paths box, above the new layer, you'll see the opacity slider. 
Slide the opacity to the left until you can see your image and adjust it to the right or left until you have the image tinted as dark as you like or a faintly as you like.
When you're happy with it, go 'Layer'-->'Merge down', (in the main image window).

Nearly finished!
Next, go 'Image'-->'Mode'-->'Indexed', and set the spinbox to 14 colors. Hit 'Convert'.
Then go 'File'-->'Save as', and change the filename extension from .xcf to .xpm, and click 'okay'.
Now you can close GIMP if you want.

Gzip the image by issuing the gzip command on it or right-click and click 'create archive, and set the spinbox to '.gz', and click 'create.

All done, all there is left to do is to copy the splashimage to out /boot/grub directory, edit our /boot/grub/menu.lst file, and see how it looks.
(You can just leave it where it is and reboot and type the command to load it from GRUB's command line if you prefer, that has already been explained eariler in this thread).
My new splashimage looks best with foreground and background color settings of 87ceeb and 0000ff. (That has been explained earlier in this thread also).

For example,
```
splashimage (hdx,y)/boot/grub/nightship.xpm.gz
foreground 87ceeb
background 0000ff
```
Here's a thumbnail of my new splashimage, 
[IMG]http://users.bigpond.net.au/hermanzone/p15/nightshipThumb.png[/IMG]
nightship.xpm.gz

---

### Post by Herman on 2008-12-13
:) Making a splashimage with a sailing ship in it reminded me of my own seagoing years and whet my appetite for more. I like to see sailing ships with all their sails out, so I just had to make another one. 
(Besides, I'm from Nova Scotia - I can't help it).
(Well, I'm Dutch-NovaScotian-Australian). :)

This one is the 'Duyfken', which was the small but fast Dutch sailing ship, in which Captain Willem Janszoon and his crew became the first Europeans to discover Australia in 1606.
Links: [The Original Duyfken]("http://www.duyfken.com/original/"), and [The Duyfken]("http://www.nla.gov.au/exhibitions/southland/Exp-The_Duyfken.html"). If you use Google you will find a lot more info, (of course).

I actually put a lot of my own work into this one. 
It's based on a real picture of the ocean, a real picture of the moon, and a real picture of the Duyfken replica, which sails out of the port of Cairns, North Queeensland Australia.
I had to re-draw each mast and rigging and sails on different layers in GIMP and then combine all the layers. I looked at lot of other pictures of the rigging to make it as authentic as I could. It was worth it. If I stare at it too long I almost get the feeling it's moving.

In my opinion, this splashimage looks best with foreground faebd7 and background 8b8378.
For example,
```
splashimage (hdx,y)/boot/grub/moonlight.voyager.xpm.gz
foreground faedb7
background 8b8378
```[IMG]http://users.bigpond.net.au/hermanzone/p15/moonlight.voyager.png[/IMG]
moonlight.voyager.xpm.gz

---

