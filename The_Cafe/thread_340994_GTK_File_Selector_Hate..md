---
title: "GTK File Selector Hate."
date: 2007-01-18
forum: The Cafe
---

### Post by darkninja on 2007-01-18
Am I the only one here who absolutely hates the GTK file selector?:evil: 

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23325&stc=1&d=1169098862[/IMG]

Let's start off with the simple mode. I see a picture I want to save on the net. I already have a subfolder for aircraft pictures under Pictures/Aviation, however if I have been using another folder previously (Pictures/Computers) I can only select that folder or the root Pictures folder.

I guess I could create a Nautilus bookmark for every single one of my subfolders, however the list would get way too long. I'd have to have a Pictures/Cats, Pictures/Photos/Holidays, /Pictures/Aviation/Fighters etc...

Other users might have directories like /Documents/TPS Reports/2004/March/2-12/ for example!

Sure it looks simple, but it has next to no functionality. I can only save to a bookmark folder or previously used subfolder.

Even if I want the same subfolder as last time any full file selector should still remember my previously used folder.

To do anything worthwhile with it I'd have to click to go to the "Browse for Other Folders" option.

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23324&stc=1&d=1169098197[/IMG]

Next up, let's just say I want to edit a specific picture in GIMP. How is having a little "Image Preview" going to help me if I've got a folder filled with hundreds of pictures?

Also, why does the file selector use List-view to do this when Nautilus uses Icon-view by default? In the modern world of multimedia and simple usability, why are we sticking to the older list-view for simple desktop tasks?

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23323&stc=1&d=1169098197[/IMG]

What I'd like to see would be the "simple mode" scrapped all together, and make the GTK file selector basically a slightly stripped down version of Nautilus, with Icon View by default.

I'd like to file a bug report/wish-list, however knowing most stubborn GNOME devs I don't see it going anywhere.

---

### Post by maniacmusician on 2007-01-18
the one in KDE is a little better, but an overhaul would still be nice.

---

### Post by bionnaki on 2007-01-18
I see you collect images of helicopters.

---

### Post by blackened on 2007-01-18
This has also been bothering me lately. I think you beat me to the punch.

I wouldn't even mind it if the dialog were to intuit a directory for the file you're trying to save (sortof like Azureus does with torrent files).

---

### Post by siimo on 2007-01-18
KDE has just copied the windows file selector.  It is ancient but it works well for hierarchical file systems that we use.  It's like GTK have re-invented the wheel except they haven't invented the tyre yet and it makes for a really bumpy ride. :mrgreen:  ](*,)

---

### Post by ffi on 2007-01-18
> **darkninja said:**
> Am I the only one here who absolutely hates the GTK file selector?:evil: 


No :-D 

I actually found a way to make FF use the KDE file-selecter, I will see if I can find it if you are interested...

---

### Post by ffi on 2007-01-18
can't find it anymore but i might have found something even better:

[http://kde-apps.org/content/show.php?content=36077](http://kde-apps.org/content/show.php?content=36077)

---

### Post by shining on 2007-01-18
This looks very hackish :)

> 
The 'Portland' freedesktop project will undoubtedly come up with a far better solution. But until then, you can give this a try.


So I'll just wait and see.

This point comes back endlessly when kde/qt users say what they dislike about gnome/gtk. What I don't really know is what most gnome/gtk fans think.
Anyway, I just hope that either the gtk file selector will be improved, or that there will be a proper way to replace it, so that kde/qt fans can't complain about that anymore :)

---

### Post by pmj on 2007-01-18
I guess I'm a Gnome fan, and I don't care much since I rarely ever use the thing.

I just have to say, though, that thumbnails in the file selector would be a disaster. If I want to open a file in a folder with 5000 pictures in it, I don't want to wait several minutes while it loads the thumbnails, at which point the file selector will use a hundred megs of RAM. Really, the only thing I can think of that I want changed immediately is that it should remember if you want the simple or "advanced" view and give it to you right away.

---

### Post by darkninja on 2007-01-18
> **pmj said:**
> I guess I'm a Gnome fan, and I don't care much since I rarely ever use the thing.

I just have to say, though, that thumbnails in the file selector would be a disaster. If I want to open a file in a folder with 5000 pictures in it, I don't want to wait several minutes while it loads the thumbnails, at which point the file selector will use a hundred megs of RAM. Really, the only thing I can think of that I want changed immediately is that it should remember if you want the simple or "advanced" view and give it to you right away.


I disagree. I've got a folder (on a NTFS-3G mounted filesystem no less) that contains 663 images, and it only takes about 15 seconds to generate all the thumbnails from scratch and Nautilus remains totally responsive while doing it, prioritising the images in view.

I don't notice any unusually high RAM usage from Nautilus

The vast majority of folders will have much less images then that.

I'd much rather take a slight delay then manually going through such a folder in list view trying to find the right image. My current solution is to run Nautilus to find the image I want then copy+paste it into whatever needs it.

---

### Post by pmj on 2007-01-18
> **darkninja said:**
> I disagree. I've got a folder (on a NTFS-3G mounted filesystem no less) that contains 663 images, and it only takes about 15 seconds to generate all the thumbnails from scratch and Nautilus remains totally responsive while doing it, prioritising the images in view.

I don't notice any unusually high RAM usage from Nautilus

The vast majority of folders will have much less images then that.

I'd much rather take a slight delay then manually going through such a folder in list view trying to find the right image. My current solution is to run Nautilus to find the image I want then copy+paste it into whatever needs it.

Now open the folder again. You'll notice that Nautilus is frozen while it loads the *already* generated thumbnails. During this time, every other Nautilus window and the desktop will also be frozen. Please, go ahead, stuff a few thousand pictures in the same folder, let Nautilus make the thumbnails for them all, restart Nautilus (so that nothing is cached in RAM) and open it again and see how long it takes. I think you'll be surprised, and not in a good way.

Oh, and Nautilus is using some 200MB RAM for me right now, because I've browsed around in folders with MANY images in them.

---

### Post by darkninja on 2007-01-18
> **pmj said:**
> Now open the folder again. You'll notice that Nautilus is frozen while it loads the *already* generated thumbnails. During this time, every other Nautilus window and the desktop will also be frozen. Please, go ahead, stuff a few thousand pictures in the same folder, let Nautilus make the thumbnails for them all, restart Nautilus (so that nothing is cached in RAM) and open it again and see how long it takes. I think you'll be surprised, and not in a good way.

Oh, and Nautilus is using some 200MB RAM for me right now, because I've browsed around in folders with MANY images in them.

OK, I've done a reset and run a test.

Initial startup (desktop only): 4.4MB
Nautilus browsing home folder: 8.9MB
Browsing folder with 23 images: 10.1MB
293 items: 19.9MB
663 items: 53.1MB
4469 items: 181MB

Even with the 4469 items generated by the search they took only about a minute to thumbnail and going back to view them causes them to start to appear within about 5 seconds and finish in about 10.

Putting 1353 in a single folder, restarting Nautilus and re-opening it gets them up in about 5 seconds too.

Not perfect but quite good. Uses a fair bit of RAM but is still plenty fast.

Perhaps Feisty's Nautilus has had some major performance improvements?

At the risk of going off topic...

---

### Post by pmj on 2007-01-18
> **darkninja said:**
> At the risk of going off topic...
Too late. ;)
Nautilus is strange, speed-wise. When you've just started it it's pretty fast, but the longer you use it the slower it gets. Even something as simple as opening a mostly empty home folder can take several seconds if Nautilus has been running and been used heavily for a couple of days. Why this is I don't know.

Anyway, my quick test: I opened a folder on my desktop containing 1032 images, and it took 21 seconds. That is precisely 21 seconds more than I want to wait for my file selector to become usable.

I'm all in favor of improvements to the file selector, but I don't think thumbnailing is an improvement. When I want to open or save a file I want to do it immediately; anything that slows the process down is bad.

---

### Post by darkninja on 2007-01-18
> **pmj said:**
> Too late. ;)
Nautilus is strange, speed-wise. When you've just started it it's pretty fast, but the longer you use it the slower it gets. Even something as simple as opening a mostly empty home folder can take several seconds if Nautilus has been running and been used heavily for a couple of days. Why this is I don't know.

Anyway, my quick test: I opened a folder on my desktop containing 1032 images, and it took 21 seconds. That is precisely 21 seconds more than I want to wait for my file selector to become usable.

I'm all in favor of improvements to the file selector, but I don't think thumbnailing is an improvement. When I want to open or save a file I want to do it immediately; anything that slows the process down is bad.

Or perhaps the better idea is to sort your images better so you don't have 1032 in one folder :p 

I could see your argument about waiting for thumbnails making sense on something like XFCE, but on GNOME the focus seems to be on usability rather then raw performance.

Also if you wanted to open a picture for editing without knowing it's filename I'd imagine it would be somewhat painful to go through a list of 1032 images with the little single image preview in order to find the right one.

I do agree that Nautilus has always been a bit weird and has only became a decent file manager recently. I'm a bit of a fan of it's interface, combining the simplicity of OSX Finder and the functionality of Explorer.

---

### Post by ComplexNumber on 2007-01-18
[quote=darkninja]Am I the only one here who absolutely hates the GTK file selector?[/quote]
yes you are.


[quote=darkninja]Sure it looks simple, but it has next to no functionality. I can only save to a bookmark folder or previously used subfolder.[/quote]
press that little button(circled in green in the screenshot) in the top left hand corner. when you do, up pops that thing circled in red (see screenshot)


[QUOTE=pmj]
Nautilus is strange, speed-wise. [/QUOTE]
in tests, it has been proven to be considerbly faster than konqueror for almost all operations.

---

### Post by darkninja on 2007-01-18
> **ComplexNumber said:**
> 
press that little button(circled in green in the screenshot) in the top left hand corner. when you do, up pops that thing circled in red (see screenshot)

I wasn't talking about that at all. I was referring to the first image, the simple GTK file-save dialog.

My point was how can I tell what an image is (aside from the filename) from the list view as pictured in the second image.

---

### Post by ComplexNumber on 2007-01-18
> **darkninja said:**
> I wasn't talking about that at all. I was referring to the first image, the simple GTK file-save dialog.

so what were you talking about when you said this " I can only save to a bookmark folder or previously used subfolder"?
you were talking about it not having that address bar that you failed to notice about.


> **darkninja said:**
> 
My point was how can I tell what an image is (aside from the filename) from the list view as pictured in the second image.
psychic powers. alternatively, you could open up nautilus and cut and paste the location into the address bar. how do you think other file managers do it?

---

### Post by darkninja on 2007-01-18
> **ComplexNumber said:**
> so what were you talking about when you said this " I can only save to a bookmark folder or previously used subfolder"?
you were talking about it not having that address bar that you failed to notice about.


Without clicking expanding the simple file view pictured in the first image it is impossible to save anywhere other then a bookmarked folder or the previously used.

I don't see the point in having the simple mode as the complex mode still remembers the previously used folder and can do everything else much better.

> **ComplexNumber said:**
> 
psychic powers. alternatively, you could open up nautilus and cut and paste the location into the address bar. how do you think other file managers do it?

But doesn't that defy the entire point of having a graphical file selection utility in GTK?

KDE's file chooser is basically a stripped down Konqueror which show image previews. Copying and pasting is an option yes, but I hardly think it's an acceptable one.

Not to mention that your strategy sounds like a usability nightmare.

---

### Post by ComplexNumber on 2007-01-18
as your're the usability expert, what do you suggest?

---

### Post by darkninja on 2007-01-18
> **ComplexNumber said:**
> as your're the usability expert, what do you suggest?

Well I don't claim to be a usability expert by any means (though I did study a unit of it at uni), however I have personally found this particular GTK interface to be much more frustrating for very common user tasks then it's equivalents in KDE and Windows.

Here is a rough mockup of what I feel would be a better interface for most users. It would obviously need some review.

Note that it's a bit wider then it should be, I think it would default to a 3 image width.

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23346&stc=1&d=1169126569[/IMG]

---

### Post by picpak on 2007-01-18
^ That's perfect.

All we need is a way to change the location bar to a typable toolbar style (or even better, have it change on the fly with Nautilus/Thunar), and it's even more perfect.

---

### Post by Miguel on 2007-01-18
I also don't like the simple mode, but the worst part IMHO is that, although you select "one-click behaviour" for your desktop, GTk-file-chooser still works with two clicks. It's dumb and inconsistent. Nevertheless, I'm against thumbnail mode in gtk-file-chooser.

BTW: I also tend to have lots of pictures of planes and F1 cars (man, I love the Eagle Weslake T1G) and F1 tests tend to be difficult to sort unless you follow a logical naming order. In your case, the only logical asociations I could make are:
1107*.jpg -> MiG 29
1108*.jpg -> Sukhoi planes

2nd BTW: Is the top right one a MiG-29M? If it's the right variant and good res, could you send it to me?

---

### Post by ComplexNumber on 2007-01-18
> **picpak said:**
> ^ That's perfect.

All we need is a way to change the location bar to a typable toolbar style (or even better, have it change on the fly with Nautilus/Thunar), and it's even more perfect.
see post 15



> however I have personally found this particular GTK interface to be much more frustrating for very common user tasks then it's equivalents in KDE and Windows.its exactly the same with kde in that respect.  kde doesn't show icon view either. it drastically reduces the overhead, and i suppose that it the main reason.

---

### Post by darkninja on 2007-01-18
> **picpak said:**
> ^ That's perfect.

All we need is a way to change the location bar to a typable toolbar style (or even better, have it change on the fly with Nautilus/Thunar), and it's even more perfect.

I'd assume that either clicking the paper-and-pen or crtl+L would bring up the text entry mode as per Nautilus.


> **Miguel said:**
> I also don't like the simple mode, but the worst part IMHO is that, although you select "one-click behaviour" for your desktop, GTk-file-chooser still works with two clicks. It's dumb and inconsistent. Nevertheless, I'm against thumbnail mode in gtk-file-chooser.

BTW: I also tend to have lots of pictures of planes and F1 cars (man, I love the Eagle Weslake T1G) and F1 tests tend to be difficult to sort unless you follow a logical naming order. In your case, the only logical asociations I could make are:
1107*.jpg -> MiG 29
1108*.jpg -> Sukhoi planes

2nd BTW: Is the top right one a MiG-29M? If it's the right variant and good res, could you send it to me?

Well there should be a "View as List" option right where the "View as Icons" option is if you really want to use a list. I feel that icons are a better idea for new users though I am willing to debate this.

Not sure exactly which model the MiG is. Also my folders aren't quiet as organised as I might have made them out to be :p 

> **ComplexNumber said:**
> see post 15



its exactly the same with kde in that respect.  kde doesn't show icon view either.

It's been a while since I've used KDE but I believe one of the icons allows you to choose between thumbnail mode, list mode and others. I circled it in the attached picture.

Overhead is a bit of an issue yes, however as I've tested it isn't too bad (as long as you don't have more then 1000 pictures in a single directory :p) . For browsing Nautilus defaults to icon view.

Windows does default to list view as well. The only thing different with GTK is that it doesn't offer you any option for non-list views.

Whenever I want to open a image I always have to switch over to icon view in KDE/Win.

I've also attached a slightly skinnier version of my previous UI mockup.
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23352&stc=1&d=1169128727[/IMG]

---

### Post by Miguel on 2007-01-18
> **darkninja said:**
> 
Not sure exactly which model the MiG is. Also my folders aren't quiet as organised as I might have made them out to be :p 

Thanks for the image, darkninga. I'd bet it's a UB variant (twin seat trainer). Mmm, nope, I'm wrong. According to [this site](http://www.aviation.ru/MiG/), it is the B variant (twin seater, attack role).

---

### Post by ComplexNumber on 2007-01-18
**darkninja**
if it did show icon view, you would wish that it would be file view. from a usability point of view, the gtk/gnome devs have got it spot on. nobody wants to wait about 5-20 minutes for all the icons to load in the files selector when they know the file the want to select. 

also, at no time do i ever remember the kde file selector ever being capable of viewing icons no matter how its tweaked. are you sure?  its also probably the reason why it is has a preview pane instead.

---

### Post by Kindred on 2007-01-18
I really don't like that first dialog when you go to save something, i'd much rather it came up with the full file chooser right away, change that and I would be happy enough.

---

### Post by darkninja on 2007-01-18
> **ComplexNumber said:**
> **darkninja**
if it did show icon view, you would wish that it would be file view. from a usability point of view, the gtk/gnome devs have got it spot on. nobody wants to wait about 5-20 minutes for all the icons to load in the files selector when they know the file the want to select. 

also, at no time do i ever remember the kde file selector ever being capable of viewing icons no matter how its tweaked. probably because it can't.  its also probably the reason why it is has a preview pane instead.

See post #12. Even with 4469 images it starts to appears on screen in about 5 seconds and takes about 30 to fully thumbnail them all. The vast majority of use will be in folders with under a hundred items so I don't really see the point of this argument.

Nautilus already browses with images on. Even on older systems this should have acceptable performance.

I'm really certain that KDE apps have a icon view (like Konqueror) remembering from my KDE days. Selecting the icon view makes the preview pane go away.

I don't have an install of KDE on me. I might fire up a livecd and have a look, or could a Kubuntu user confirm for me?

---

### Post by Erunno on 2007-01-18
I'm not sure right now if that is what you are looking for (only 2 hours of sleep tonight ;) ):

[IMG]http://img223.imageshack.us/img223/197/demoup5.jpg[/IMG]

---

### Post by darkninja on 2007-01-18
> **Erunno said:**
> I'm not sure right now if that is what you are looking for (only 2 hours of sleep tonight ;) ):

[IMG]http://img223.imageshack.us/img223/197/demoup5.jpg[/IMG]

Ah, thanks.

You right click on the file area background and select "Large Icons" and then "Thumbnail Previews".

---

### Post by ComplexNumber on 2007-01-18
ok. i stand corrected on the icon view. but like i was saying, who would want [_that_ ]("http://www.kde-forum.org/thread.php?threadid=15837")problem from a usability point of view?

---

### Post by Erunno on 2007-01-18
This behaviour is customizable. It depends on the file size whether the icons will be resolved and displayed (I think GNOME has something similar in Nautilus). The preview in the file selector is turned off by default in Kubuntu and in file browser mode it only resolves images up to around 5 MB I think.

---

### Post by darkninja on 2007-01-18
> **Erunno said:**
> This behaviour is customizable. It depends on the file size whether the icons will be resolved and displayed (I think GNOME has something similar in Nautilus). The preview in the file selector is turned off by default in Kubuntu and in file browser mode it only resolves images up to around 5 MB I think.

Exactly. Under Nautilus preferences there is an option to set the maximum file size to thumbnail, which I believe is about 5MB or so is the default.

The KDE bug ComplexNumber bought up is just that, a bug. It is not normal behaviour nor representative of icon views as a whole.

---

### Post by ComplexNumber on 2007-01-18
> **Erunno said:**
> This behaviour is customizable. It depends on the file size whether the icons will be resolved and displayed (I think GNOME has something similar in Nautilus).
yes, but only for an individual image...which doesn't really come in handy when goes up(or down) a level into a directory of 5000 images.

---

### Post by darkninja on 2007-01-18
> **ComplexNumber said:**
> yes, but only for an individual icon...which doesn't really come in handy when goes up a level into a directory of 5000 images.

Which comes up in 5-10 seconds (on Feisty). Hardly the 5-30 minutes you were talking about earlier.

The icons in view load first while the rest load in the background.

Most users won't have that many images on their entire system, let alone a single folder.

I'm not against keeping list-mode as an option. I just feel that for newbies and graphics icons are better and the speed sacrifice is not significant.

Well I'd better get some sleep.

---

### Post by ComplexNumber on 2007-01-18
<accidental double post>. why can't members have the faciity to delete their own posts?

---

### Post by ComplexNumber on 2007-01-18
>  Most users won't have that many images on their entire system, let alone a single folder.go to .thumbnails/normal, /usr/share/pixmaps, .fonts, etc

---

### Post by Erunno on 2007-01-18
Well, GNOME and KDE share that problem. I wish both DEs would implement Windows' per folder view settings. The distributor could turn off thumbnails for potentially long-loading folders by default then.

---

### Post by ComplexNumber on 2007-01-18
> **Erunno said:**
> Well, GNOME and KDE share that problem. I wish both DEs would implement Windows' per folder view settings. The distributor could turn off thumbnails for potentially long-loading folders by default then.
i'm happy with the way things are, but what about those using kde? nautilus handles it fine, whilst konqueror has often crashed on me when opening up my wallpaper folder, font folder, etc.

---

### Post by GeneralZod on 2007-01-18
> **Erunno said:**
> Well, GNOME and KDE share that problem. I wish both DEs would implement Windows' per folder view settings. The distributor could turn off thumbnails for potentially long-loading folders by default then.

I think a recent patch means that SVN Dolphin will remember View Mode (thumbnail, list, tree etc) and directory sort order for all directories, including system ones.  I can't remember whether the patch will be ported to Konqueror.

Someone once made a nice patch where the icons in the current view port were thumbnailed first, and when you moved the viewport to another point in your huge folder of pictures, it would stop the old thumbnailing task and re-start thumbnailing only those that were visible.  I don't know if it's going into Konqueror or Dolphin, though.  It ameliorates the problem of entering a huge directory of images.

---

### Post by ComplexNumber on 2007-01-18
> I think a recent patch means that SVN Dolphin will remember View Mode (thumbnail, list, tree etc) and directory sort order for all directories, including system ones.that can be configured in 'profiles' can't it? i know nautilus remembers by default which directories are list view and which are icon view because it goes by the last time the directory was opened.

---

### Post by GeneralZod on 2007-01-18
> **ComplexNumber said:**
> that can be configured in 'profiles' can't it? i know nautilus remembers by default which directories are list view and which are icon view because it goes by the last time the directory was opened.

Konqueror currently (and for quite a while, now) uses the ugly method of "remembering" which View Mode is used in a given directory by actually writing a file (called .directory) in each folder it visits (assuming the user has configured it to remember the per-folder View Mode).  No stable release includes the sorting mode in this file, if I recall, so the sorting mode cannot be remembered.  Apart from the intrinsic ugliness of this method, it also means that the View Mode can only be stored for folders for which the user has write-access.  

The Dolphin solution fixes all of this and is better than Konqueror's current solution, thankfully :)

---

### Post by ComplexNumber on 2007-01-18
i wouldn't call it ugly at all.  i don't remember konqueror remembering the view (EDIT: no wonder. "it also means that the View Mode can only be stored for folders for which the user has write-access"). nautilus remembers them all.

---

### Post by Erunno on 2007-01-18
> **GeneralZod said:**
> Apart from the intrinsic ugliness of this method, it also means that the View Mode can only be stored for folders for which the user has write-access.

Sorry for going offtopic but your comment made me chuckle a bit after reading [this]("http://behindkde.org/people/danimo/") today on the newest episode of "People Behind KDE". :p 

> I also like the pragmatic way decisions are often made and the commitment to technical excellence.

---

### Post by GeneralZod on 2007-01-18
> **Erunno said:**
> Sorry for going offtopic but your comment made me chuckle a bit after reading [this]("http://behindkde.org/people/danimo/") today on the newest episode of "People Behind KDE". :p

Hehe - well, the commitment is there, it just takes a few years ;)

---

### Post by PatrickMay16 on 2007-01-18
The file selector could be much better if there was a thumbnail image view. Also, the thumbnail view must be fast and use only a small amount of RAM. They could do this by making the thumbnails very small or low quality, I guess.

Just compare Nautilus's thumbnail view to Windows 2000's explorer thumbnail view. Windows 2000's one is much much faster.

I hope some developers see me saying this. If you're a developer, first I'd like to say thanks for everything you've done. Second I'd like you to think over my suggestion.

---

### Post by darkninja on 2007-01-18
> **ComplexNumber said:**
> go to .thumbnails/normal, /usr/share/pixmaps, .fonts, etc

The Nautilus list mode uses thumbnails too.

I also seriously doubt that users will be frequently go browsing through their hidden thumbnails directory. It would be trivial to implement some "if items > 1000 use list mode" code. Alternativly it would also be easy to split the thumbnails up into 16 smaller directories based on their first hexadecimal number.

Or do the Windows thing and add a Thumbs.db to each directory (ugh...)

/usr/share/pixmaps has less then 200 tiny pictures in a single directory and was instant.

.fonts is only for user-installed fonts, I doubt most users will want that many and even for those who do the delay still isn't bad by any means.

Feisty Nautilus does remember whether to view a folder as list or icons.

Thumbnails are very fast, and RAM usage only become an issue with more then a few thousand files. I don't think their are major technical flaws with this idea. It's more a question of if it's truly better for usability?

---

### Post by thechris on 2007-03-19
Are there any gconf or gtkrc settings to fix the 2-click dialog issues?  I don't want to have a list of 100+ favorite places.  I just want the dialog to open in "advanced" mode by default, as I will use "simple" mode less than 10% of the time.  I realize that gnome's got this kick of "make things simple", but this is a case where the attempt has done the exact opposite -- instead of making things simple all it has done is make me click a button every time i save a file to get past the "simplicity".

And for me, this is a large enough issue to keep me from using gnome.  every time i save a file I become annoyed.  After a few hours I just move back to KDE.

---

### Post by ComplexNumber on 2007-03-19
> **thechris said:**
> Are there any gconf or gtkrc settings to fix the 2-click dialog issues?  I don't want to have a list of 100+ favorite places.  I just want the dialog to open in "advanced" mode by default, as I will use "simple" mode less than 10% of the time.  I realize that gnome's got this kick of "make things simple", but this is a case where the attempt has done the exact opposite -- instead of making things simple all it has done is make me click a button every time i save a file to get past the "simplicity".

And for me, this is a large enough issue to keep me from using gnome.  every time i save a file I become annoyed.  After a few hours I just move back to KDE.
what "2-click dialogue issue"?

---

### Post by argie on 2007-03-19
I agree completely with the OP. Now that I'm used to Gnome, I click the "Browse for other folders" button by involuntary reflex. The simple mode has _never_ been what I wanted.

EDIT:

a - bi, the "2-click issue" is probably having to click "Browse for other folders" before being able to save where you want.

---

### Post by thechris on 2007-03-19
> **ComplexNumber said:**
> what "2-click dialogue issue"?

to save files, i must click "advanced mode", then find the location, then save.  i guess thats more than 2 clicks.  I mean to refer to the issue that, while gnome/gtk will remeber everything else about the user experience, it will always forget the last mode for the file dialog.

I really hate having two save dialogs, and find its just easier to always click "advanced mode" as I have folders with the same name.  I consciously will never use the default "simple" mode because of this.

as such, i've been a large KDE user.  Still, it might be nice to evaluate Gnome again, but this dialog is a showstopper.  I know that I will end up saving files.


as for the preview thing, I don't care if its an option.  Previews and icon view are the second thing i turn off in winXP/KDE/Nautilus.  The first is spatial browsing.  Don't use these features, and they take up screen space.  So long as I can use my computer the way I can already, I am happy.

---

### Post by cowlip on 2007-03-19
I agree with you 100%, OP, about the list thumbnails and the other things you mentioned.  Also, in Dapper Drake I also couldn't open, right click, edit, copy cut paste, files in the file selector, which I can with windows and I believe KDE's file selector.

Firefox began copying this stupid functionality when you try to add a bookmark too, which annoyed me so much that I had to download an extension called "OpenBook" to remedy it.

---

### Post by Choad on 2007-03-19
is it just me or does the file selector lag like a mofo

core2duo and a 7600 go, it is the slowest pos on my system.

im talking about this dialog

[img]http://img352.imageshack.us/img352/6308/screenshot1bg1.png[/img]

i hate it with a passion. 5 seconds to load that dialog, and if i had dared to scroll it it would have been like wading through humus.

---

### Post by ssam on 2007-03-19
sorry if this has been said already

in feisty (gnome 2.18 ) the save box remembers it's state. this means you only have set it to browse mode once :-)

---

### Post by gaspard.leon on 2008-10-21
Windows XP: [COLOR="Navy"]Usable[/COLOR]
Windows Vista: [COLOR="DarkSlateGray"]Usable but annoying[/COLOR]
KDE: [COLOR="DimGray"]Like Windows XP I think?[/COLOR]
OSX: [COLOR="Sienna"]Can't remember[/COLOR]
GTK+ (used by GNOME): [COLOR="Red"]CRAP!![/COLOR]

The GTK file chooser, how I hate thee, let me count the ways
[LIST=1]
[*]No Previews, just try browsing for a digital photo sometime!
[*]No file operations, such as rename FFS
[*]Can't rename new folder if accidentally named wrong
[*]No useful columns or column config, no times in date columns
[*]Sometimes doesn't start typing in the correct box so you have to click in file name, then type
[*]laggy and crap just like the rest of GTK
[/LIST]

---

### Post by oomingmak on 2008-10-22
> **darkninja said:**
> Am I the only one here who absolutely hates the GTK file selector? :evil: 

No, you are not. My hatred for it knows no bounds.



> **darkninja said:**
> What I'd like to see would be the "simple mode" scrapped all together, and make the GTK file selector basically a slightly stripped down version of Nautilus

I'm way ahead of you.

[**[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=403111[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=403111")



> **darkninja said:**
>  I'd like to file a bug report/wish-list, however knowing most stubborn GNOME devs I don't see it going anywhere.
Let me sum up the experience with an icon ....

](*,)

---

### Post by bruce89 on 2008-10-22
> **gaspard.leon said:**
> 
No Previews, just try browsing for a digital photo sometime!


It is up to the individual program to implement this.

> **gaspard.leon said:**
> 
laggy and crap just like the rest of GTK


Patches welcome.

---

### Post by Mr. Picklesworth on 2008-10-22
On the bright side, you can drag and drop files into (and out of) any of those selectors. Particularly fun is dropping a file into the very simple combo box one.

---

### Post by bruce89 on 2008-10-22
Saying as GTK+ 3.0 is round the corner, someone should actually file a feature request about this, but not in a nasty "you're stupid" way.

---

### Post by Mr. Picklesworth on 2008-10-22
There was a Google Summer of Code project where a student created a media tray for this type of thing, similar to what there is in MacOS (except cooler). Not sure where that got to, but it would be good to have it and the file dialogs cooperating on a user interface level.

As is, the simple menu with bookmarked locations is beneficial on a user interface front. The file save dialog relies on a mishmash of all sorts of information located all over the place, which is not really a user friendly concept. At least not friendly for the hopeless tunnel-vision users who really need user friendly software ;)

If those preloaded media locations were more useful, more magical, as a media tray would do, I think people would like the design a lot more.

However, while the File Chooser Button (as in the Save Screenshot dialog) is really cool, this is *not good* when we look at the surrounding picture. This is not as good as the menu bar, for example, which has a similar kind of simplicity. The menu bar does really well because it starts off with three choices for context, so it can be really organized and really streamlined and the user doesn't have to make any guesses; the very first button he clicks on (Applications, Places or System) is completely clear in what it will hold before it opens.

The file save dialog, on the other hand, is more like the Start menu. It begins with a tiny list of possibilities, and if that fails it throws an enormous, complicated heap of buttons and dials at the user. Furthermore, it has two points of entry and it is designed in such a way that the user has to go through both. If the first one fails, he tries the second one. The second one suddenly branches off in a million directions: Photos, music, programs, settings, downloads, network places... many of which are not the ways he had managed his photos, music, programs or settings before (which all have their own relevant GUI tools that are not the file manager). That is not good.

It isn't easy to cook up a solid solution, though, particularly without wanting to reinvent the wheel. Maybe someone will get a good idea! I have to admit I have one but it's one of those impossible ideas that would require the whole universe to change polarity.

One thing this dialog should do for the time being is to add an "Other..." option below the File Chooser Button lookalike beside the "Save in folder" label. Clicking that could unfold the Browse for More Folders expander below. Doesn't seem like much, but at least this would streamline the thing somewhat rather than having two different methods of finding the same files presented in the same dialog.

---

### Post by gaspard.leon on 2008-10-22
> **bruce89 said:**
> It is up to the individual program to implement this.



Patches welcome.

Sorry to come off as rude, not trying to step on anyone's toes, just the name of the thread I was contributing too.

I would work on this, but:
1. I'm not a C developer, so have a lot of learning to do.
2. Don't have much free time, working full time.
3. If I did learn how to develop C, chances are if I developed a patch it would get stuck in the quagmire of GNOME/GTK politics/policies.
4. If I learn C I will probably try to develop a drop-in replacement of the GTK file selector and distribute it via PPA...
(long term plans)

In the mean time, I'm just getting my hate on :popcorn:

---

### Post by Christmas on 2008-10-22
Perfectly, completely agree with OP. Another annoying thing specific to Firefox this time:

Go to File -> Save Page As (or right click an image, then Save Image As), create a new folder in the window that appears, enter a name, hit enter, than (without moving the mouse cursor from above the Create Folder button) try to click on it again to create a new directory. You will actually have to move the mouse pointer away, then go back over the button.

The same exact thing happens in other GTK applications like XChat, for example.

---

### Post by bruce89 on 2008-10-22
> **Christmas said:**
> Perfectly, completely agree with OP. Another annoying thing specific to Firefox this time:

Go to File -> Save Page As (or right click an image, then Save Image As), create a new folder in the window that appears, enter a name, hit enter, than (without moving the mouse cursor from above the Create Folder button) try to click on it again to create a new directory. You will actually have to move the mouse pointer away, then go back over the button.

The same exact thing happens in other GTK applications like XChat, for example.

In other words, it's not "specific to Firefox".

See [http://www.kryogenix.org/days/2007/09/25/1440](http://www.kryogenix.org/days/2007/09/25/1440)

---

### Post by Christmas on 2008-10-22
[quote=bruce89]In other words, it's not "specific to Firefox".[/quote]
Yes, my mistake.

---

### Post by bruce89 on 2008-10-22
This has been discussed before :
[Bug requesting delete and rename]("http://bugzilla.gnome.org/show_bug.cgi?id=325150")
[Bug requesting more flexible columns]("http://bugzilla.gnome.org/show_bug.cgi?id=141155")

> GTK File Selector Hate.

This isn't the way to win friends and influence people.

---

### Post by Karelia on 2009-07-16
> **bruce89 said:**
> This isn't the way to win friends and influence people.
"Hate" is a sincere word. I hate GTK file chooser too! Especially because bug report with suggestion about thumbs exists untill 2005 ([http://bugzilla.gnome.org/show_bug.cgi?id=315207](http://bugzilla.gnome.org/show_bug.cgi?id=315207)) and nothing still have been done by developers. That kind of disregarding and ignoring the users' wish is shameful and ridiculous.

---

### Post by GeneralZod on 2009-07-16
> **Karelia said:**
> "Hate" is a sincere word. I hate GTK file chooser too! Especially because bug report with suggestion about thumbs exists untill 2005 ([http://bugzilla.gnome.org/show_bug.cgi?id=315207](http://bugzilla.gnome.org/show_bug.cgi?id=315207)) and nothing still have been done by developers. That kind of disregarding and ignoring the users' wish is shameful and ridiculous.

Sounds like the devs want it, but no one has the time to do it - a very common situation with volunteer-driven development.  Branding this as "disregarding and ignoring the users' wish" is unfair - maybe even "shameful and ridiculous", in fact :p

---

### Post by Karelia on 2009-07-16
> **GeneralZod said:**
> Sounds like the devs want it, but no one has the time to do it - a very common situation with volunteer-driven development.
No time for more than 4 years? :)

And they made tabbed browsing, and compact view, and even a number of little unimportant improvements in some widgets, other than FileChooser. So when they want smth, they have time for it.

Also, is GNOME really volunteer driven or sponsored by RedHat, or just the gnome.org is hosted by RedHat__?

---

### Post by Kazade on 2009-07-16
Choosing a directory is even worse. To select the directory you have to basically go up a level, select it then click open. If you double click it, it obviously browses into the folder rather than selecting it. Why the directory selection isn't a tree view is beyond me, that would make so much more sense! It just looks like they wrote the file selector and then tried to bend it to fit directories aswell.

Also, speaking of tree views, how come in Nautilus I can change the left side bar from "Places" to "Tree" but I can't do that in the file chooser?

---

### Post by Karelia on 2009-07-16
By the way, user **oomingmak** said all that one have to know about devs here: [http://ubuntuforums.org/showpost.php?p=2957787&postcount=39](http://ubuntuforums.org/showpost.php?p=2957787&postcount=39)

---

