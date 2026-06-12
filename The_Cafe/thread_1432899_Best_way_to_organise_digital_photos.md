---
title: "Best way to organise digital photos"
date: 2010-03-18
forum: The Cafe
---

### Post by finite9 on 2010-03-18
I really need a good system to be able to store my photos.

I see this question a lot and I have not yet found a good answer.  I plug in my SD card and use gthumb to import the photos into my Pictures folder.

I like this system, where gthumb creates a datestamp folder, because in my opinion, the folder structure should be transparent and should not need to be in a particular oder to be able to find photos, like rows in a database, however, the *primary* use of stored digital photos is finding the photos you want to look at.

This is where I come unstuck:  What do you define as being a useful searchable parameter:

1. the date the photo was taken e.g. christmas day or other known date?

2. the location a photo was taken?

3. tag based searches?

Date is easy because its in the EXIF, but location and tags need to be manually assigned during import.  If you are strict enough with tagging and location, is the above enough to easily find the right photos?

What do you do about location?  Are free text strings really an option?  What if you don't remember the text you wrote for the location?  What if it was "Ma's Cafe" but you can't remember the name of the cafe?

Gthumb is really bad on the search capabilities, but it is without doubt the fastest viewer available from what I have tried.

Does anyone have any better suggestions for how to make searches easier?

---

### Post by ratcheer on 2010-03-18
> **finite9 said:**
> Does anyone have any better suggestions for how to make searches easier?

I don't. Over the years, I have tried all the ways you mentioned and something is always lacking. I have settled on folders by year and month but, when photos become several years old, it is sometimes difficult to remember what year you are trying to look for, much less the month.

I thought tags would be great, but it is a pain to assign several tags to each photo. Again, after a while, your tagging system that seemed to be so great (I'm talking about your personal tags that you devise to categorize each photo) becomes a jumbled mess.

This really seems to be an area of software design where someone needs to come up with a "killer app".

Tim

---

### Post by joshedmonds on 2010-03-18
My photo workflow goes something like this:

[LIST]
[*]Get photos from camera/hard-drive etc.
[*]Clean up cruft (e.g. search and delete thumbs.db files)
[*]Check the date and time are correct, and adjust with jhead if necessary
[*]Rename the files with jhead using YYMMDDhhmmss_timezone_originalfilename format
[*]Change all filenames including extensions to lowercase
[*]Organise into folder hierarchy
-Year (e.g. 2010 = '2010')
--Month (e.g. January = '201010')
---1. Earliest_Event_Name (e.g. 'Mannys_Birthday_2010)
---2. Next_Event_Name 
etc.[/LIST]
This allows free text in the folder name (without needing to use metadata/tags) and I personally don't need organisation below the month level. Although I repeat the year a number of times, I find it easier to navigate. If I needed to I could easily find all photos from New Zealand for example, by searching for the timezone.

---

### Post by StuartN on 2010-03-18
I do the same, with folders called camera/YYYY-MM-DD (event), such as "Nikon/2010-03-17 St Patrick's Day"

But I also add short text files with the same name as the photo to be described, or 0.txt to describe the folder. Then I create .png images of all the descriptions:

```
find ~/Photographs -name "*.txt" -exec txt2png.sh {} \;
```

(Obviously your images must not be .png images or they will be overwritten).

You can do absolutely anything you like within the txt files (including deleting the lot), such as strict dictionary tags, loose location names, geo-coordinates or garbled text, and find it with:

```
grep -ir "MyTag-MyValue" ~/photographs/*.txt
```

If you **grep -l** (to return file names) and pipe through sed -e "s/txt/jpg/" then you get a list of matching images.

---

### Post by finite9 on 2010-03-18
> **ratcheer said:**
> 
I thought tags would be great, but it is a pain to assign several tags to each photo. Again, after a while, your tagging system that seemed to be so great (I'm talking about your personal tags that you devise to categorize each photo) becomes a jumbled mess.
Tim

Totally agree.  But I think it is the tag _implementation_ that is the bottleneck here.  I can't speak for other apps as I use EOG exclusively, but as far as I can remember most apps are the same in that they make you highlight several photos then then open a seperate dialogbox to choose from a list of random tags which is quite time consuming.

The idea I have in mind is that someone should develop an app where instead of a simple list of tags, they would be more dynamic in nature, whereby several dialog box lists would open up *but not disallow focus on the main browser window* and each dialog box could contain similar groupings of tags (people, events etc).  My thinking is that you could select several tags at once and select several photos at once to apply the tags to, because I think this would dramatically decrease the time taken to tag images.  Sometimes I have a 100 images that I import at once and it becomes a real PITA to tag them all using current methods.

I think F-spots tag method is better than gThumbs but I prefer gThumb more due to it's speed and efficiency.

I think geotagging is the next big thing, after having seen the newest Nikon camera that uses GPS to geotag images, so this would remove one manual aspect of metadata entry/searching based on location.

It would be great if you could find photos by popping up a Google Earth integrater where your image geotags were automatically displayed on the globe.

> 
My photo workflow goes something like this:

    * Get photos from camera/hard-drive etc.
    * Clean up cruft (e.g. search and delete thumbs.db files)
    * Check the date and time are correct, and adjust with jhead if necessary
    * Rename the files with jhead using YYMMDDhhmmss_timezone_originalfilename format
    * Change all filenames including extensions to lowercase
    * Organise into folder hierarchy
      -Year (e.g. 2010 = '2010')
      --Month (e.g. January = '201010')
      ---1. Earliest_Event_Name (e.g. 'Mannys_Birthday_2010)
      ---2. Next_Event_Name
      etc.


It seems like quite a lot of work just to get the photos onto your hard disc?  For all the steps you mention, the result is that you transferred your images to your folder.  I acheive the same result by letting gThumb autostart when I pop in my SD card and clicking the "import" button, which is one step.  I realise that you're changing the names (I hope you script that?), but is the auto-naming scheme of gThumb so bad that it needs changing?  I am worried that if I make my structure dependant on exact folder naming conventions, then it will eventually become unmanageable.  Maybe it's a bad work habit working as a DBA, but I prefer unstructured storage :)

> 
I do the same, with folders called camera/YYYY-MM-DD (event), such as "Nikon/2010-03-17 St Patrick's Day"

But I also add short text files with the same name as the photo to be described, or 0.txt to describe the folder. Then I create .png images of all the descriptions


Isn't that quite a lot of work to create all the text files?  Especially if you have a text file per photo.  If you import 200 images you took one day and a large proportion are test images that you want to keep but are part of a series, do you create text files for them?  If it gets too much work, there is a risk that you just don't do it and then the whole system breaks down.

Like with tagging at the moment: It requires a lot of self-discipline otherwise your entire "search" ability breaks down over time.  But your idea of being able to search the _filesystem_ independantly of any specific app is a really good one, which I hadn't thought of!  One of the risks with a photo app is that you become dependant on it, and if it disappears, your entire structure breaks down.  gThumb might be free software but if the maintainers decide to drop it and nobody develops it further, then your a bit stuffed, but filesystem searches will always be possible :)

Is there any tool that can inject free text labels into the metadata so that you don't have to fill up a filesystem of images with loads of text files?  Any tools that can read EXIF data from the filesystem?  That would be useful.

Some of the problems I currently have after accumulating 10 years of digital family photos is that I cannot remember which year, let alone which month, I went to Thomas the Tank Engine theme park with my son.  I can't remember which dates I took photos of my Collie that passed away last year if I get a bit sentimental and want to see all photos of her.  I think that creating tags for every "event" is a sure way to bog down the functions simplicity.


I tried a new version of Picassa last year (linux version) and it did facial recognition, but it only worked if the image of the persons face took up a certain percentage of the image and the background was uncluttered, but if this feature could be improved, then we could eventually have auto-person tagging.

In conjunction with auto geotagging, this would bring us a long way to efficient import and easy searching of images.

Wow, hope you all didn't fall asleep...I sort of got carried away there.

---

### Post by joshedmonds on 2010-03-18
> **finite9 said:**
> if I get a bit sentimental...

I find it nice to have to browse for photos, you often come across someting you wouldn't otherwise, especially if you would generally just search by tag (and you can marvel at how quickly time goes 'Was it really that long ago?')

> **finite9 said:**
> It seems like quite a lot of work just to get the photos onto your hard disc? For all the steps you mention, the result is that you transferred your images to your folder.

True, but I can add photos from other sources e.g. other people's cameras, using the same process (even adjusting by seconds if necessary) and have a photographic record in chronological order.

Removing the cruft becomes necessary when you do this, otherwise you end up with thumbs.db, hpothb07.tif, hpothb07.dat, picasa.ini, digiclip.dz etc. ad nauseum from a million different camera and software types scattered throughout.

Lowercase is useful if you want to do any other batch processing at a later date, otherwise you have to run the same action for .jpg and .JPG separately.

> **finite9 said:**
> Is there any tool that can inject free text labels into the metadata

If I want to share my photos or mix them with someone else's, I also use exiftool to add author/artist/creator + CC-BY-SA copyright information.

Exiftool will edit whatever field you like. I'm sure there are front-ends, however the cli syntax is very simple, for example:

```
exiftool -overwrite_original -comment='Insert comment text here' *.jpg
```

The -overwrite_original flag refers to the file, not existing comment text.

---

### Post by StuartN on 2010-03-19
> **finite9 said:**
> Isn't that quite a lot of work to create all the text files?  Especially if you have a text file per photo.

No, I don't find any difficulty managing this and I have thousands of photos from the 1980s to the present (plus postcards, paintings and other kinds of collected imagery). Very few photographs require a description, so mostly I have one text file per directory describing the location, event, camera and lens. I describe interesting photos, processed images and the first photo of a sequence.

On the rare occasions that I want to (e.g. when experimenting with macro exposure settings) I have run a command like **exiv2 pr -Pnt $file | grep -w "\(ExposureTime\|FNumber\|ExposureProgram\|DateTimeOriginal\|ExposureMode\|FlashSetting\|FocalLength\|ISOSpeed\|ShootingMode\|VariProgram\)"** to create a text description of every single file. And, of course **convert -resize 640x480 -gravity center -extent 640x480 $file thumb_$file** will make a thumbnail in the same location. These are in a script to describe a group of files (describe *.JPG) and I suppose the script could grab and write location etc into the text files it creates.

The huge advantage I find with this scheme is that creating a .png image of each text file means that the descriptions appear in a slideshow, light table or whatever image browser I use, without any compatibility issues. In most folders I see a png file with an event description and then all my pictures, with a new png description at the start of each sequence. In experimental folders I see all my exposure settings next to each image without fiddling with EXIF property menus.

At present I am not at all happy with the incompatible ways different programs handle tagging and meta tagging.

---

### Post by finite9 on 2010-03-19
> **joshedmonds said:**
> I find it nice to have to browse for photos, you often come across someting you wouldn't otherwise, especially if you would generally just search by tag (and you can marvel at how quickly time goes 'Was it really that long ago?')


So true!


> **joshedmonds said:**
> Removing the cruft becomes necessary when you do this, otherwise you end up with thumbs.db, hpothb07.tif, hpothb07.dat, picasa.ini, digiclip.dz etc.


Doesn't this only apply if you have opened the memory card as a filesystem and copied the files by hand?  When I run gThumbs import tool, it only gets the actual images and not any other uneccessary files

> **joshedmonds said:**
> If I want to share my photos or mix them with someone else's, I also use exiftool to add author/artist/creator + CC-BY-SA copyright information.


Thanks for the tip!  Sounds useful, and I spend most of my time in a tty so cli is not an issue.

Going back to search:  I once asked the developers of Eye of Gnome if they would consider adding a function to search on a date range, as you can only currently search for all images before a certain date or after a certain date.  Unfortunately, his response was basically "these are the dev tools you need to use to implement it: have fun".  He wasn't unfriendly, but the assumption that everyone is a programmer was quite apparent, which was a shame.

I wish gThumb would get some more love because I think it has much more potential than F-spot (urggh, Mono :evil: ) and is "free" compared to Picassa, but both Picassa and F-spot have overtaken gThumb in terms of features even if there performance implementation are not as good as gThumb/EOG's.

---

### Post by SirPecanGum on 2010-06-25
I copy the photos in to  year/month/  folders and then I use tags which I add with Windows Photo Gallery. In Linux the best I have found so far is jBrout for tagging and gthumb for viewing. Picasa is best for searching tags but in my experience it will overwrite tags from other apps if you try to add a tag with it.

[http://jbrout.manatlan.com/download](http://jbrout.manatlan.com/download)
[http://code.google.com/p/jbrout/](http://code.google.com/p/jbrout/)

---

### Post by philinux on 2010-06-25
I use gthumb or nautilus. I use a folder titled year month day plus name of event e.g. Holiday spain or somebodies party etc. Easy to identify stuff years after.

Moved to the cafe.

---

### Post by yester64 on 2010-06-25
It becomes difficult if you did not shot the photos and have little to no information to them.
I have a collection of negative slides which i did not converted so far. Because it so long ago and not all that easy to classify.

Tagging is good, but you have to do it manually. Because auto tagging only works from a camera to sort by date or the like.
Thats why i like programs where you have a general database so you see the pictures and don't have to poke every folder.
So far, this is one bad ride in linux. All the applications i have seen are somewhat ok, but not to the level i experienced on Windows.
So far, i gave up and don't sort them anymore. I use right now gthumb or geeqie. And i think thats the key. You have to use more than one app to archive your goal with fotos on linux. At least as free goes.

(no i don't like picasa)

---

### Post by eeperson on 2010-06-25
> **finite9 said:**
> 
I tried a new version of Picassa last year (linux version) and it did facial recognition, but it only worked if the image of the persons face took up a certain percentage of the image and the background was uncluttered, but if this feature could be improved, then we could eventually have auto-person tagging.


Digikam has some interesting fuzzy search features that let you search for photos by draw sketches of what you are looking for or by using a base image to search for photos of similar content.  I'm not sure how well it works in general since I haven't used it much.  I imagine it would work better for some photos than others.

---

### Post by Rackstar on 2010-06-26
I let Bibble organize my photos in this structure:
[YEAR]/[monthshort] [YEAR]/[EVENT]

So I have:
2010/jun 2010/Birthday Michael

But I do use a lot of metadata so I can query for certain persons, places, types of subject, ... in Bibble.

In my opinion this is the best way, but it is time consuming, but then again priceless if you have huge amounts of pictures.

---

### Post by StuartN on 2010-06-26
> **yester64 said:**
> And i think thats the key. You have to use more than one app to archive your goal with fotos on linux. At least as free goes.

That is absolutely right - I think that archiving means having an organisation and data collection that is independent of **any** application.

I have postcards, paintings and graphics that are not photographs in my collection.

I rely on the directory structure (camera/yyyy-mm-dd event name), where camera can also be "scanner" or "museum-slides". I try to ensure that all filenames are unique within the collection, and no images are duplicated. I also add little text files and txt2png to put these into the visual image stream, so descriptions appear on the light-table and in slideshows.

---

### Post by squilookle on 2010-06-26
I have always just copied the pphoto's from the camera to my pictures folder on the computer. 

Recently, I have found that this is an area where the Libraries in Windows 7 are quite helpful.

---

