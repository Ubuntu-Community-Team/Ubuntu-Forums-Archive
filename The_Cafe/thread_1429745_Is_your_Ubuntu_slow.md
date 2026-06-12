---
title: "Is your Ubuntu slow?"
date: 2010-03-14
forum: The Cafe
---

### Post by yester64 on 2010-03-14
I get kinda turned off with my ubuntu right now.
Its mainly nautilus i am guessing, but folders with lots of files takes for ever to read.
I spend like 5 minutes for opening a folder and to work with the folder.
Or is the filesystem (ext4).

Are you having the same issue or did you solve it? I don't recall windows that slow.
Speed is really an issue. arrrg...

---

### Post by MooPi on 2010-03-14
A large number of files will slow things down yes. Another thing might be that your hard drive is filling up. So how full is your drive ? My Ubuntu is very fast :p

---

### Post by kaldor on 2010-03-14
On one computer, Ubuntu is quite slow. 512 MB with 3 Ghz processor; it should be better. 

Fedora ran *flawlessly* on the exact same machine. Ubuntu feels like a memory hog, yet the recommended system requirements are lower for Ubuntu.

---

### Post by yester64 on 2010-03-14
i have 256 Gb free. Isn't really full.
My specs are like this.
4GB memory, dual core 3.1 ghz, 64bit ubuntu.
If i recall, everytime i have a folder with a lot of files (>1000) its slow slow slow.
I checked brainstorm and you find this issue there too. so its not just me imagening.
In my case its photos and i have lots of them.
In windows i never had it that slow and with slow i mean waiting for deleting files for 5 minutes before i can touch the folder again.
Mm.... :sad:

---

### Post by kerry_s on 2010-03-14
> **yester64 said:**
> i have 256 Gb free. Isn't really full.
My specs are like this.
4GB memory, dual core 3.1 ghz, 64bit ubuntu.
If i recall, everytime i have a folder with a lot of files (>1000) its slow slow slow.
I checked brainstorm and you find this issue there too. so its not just me imagening.
In my case its photos and i have lots of them.
In windows i never had it that slow and with slow i mean waiting for deleting files for 5 minutes before i can touch the folder again.
Mm.... :sad:

you cold try separating your images into several folders, to help speed things up.

---

### Post by NightwishFan on 2010-03-14
Actually, it was fairly slow on my desktop. It only had 900mb of RAM, and 64-bit crams a bit in there. On my laptop, I had to resort to a xorg edgers ppa to get 3d performance, so I switched to another OS. I still like Ubuntu, it is much more user friendly than some realize.

---

### Post by Ric_NYC on 2010-03-14
No... And that's one thing I like about Ubuntu.

---

### Post by LADmaticCA on 2010-03-14
You could always try another file browser like pcman or thunar. Or you could try shrinking the thumbnail preview size of the images.

---

### Post by J_Stanton on 2010-03-14
mine is fast.

---

### Post by Shpongle on 2010-03-14
try turning off pic previews , it might speed it up, or maybe use an app to manage your photos . hope you get it sorted anyway

---

### Post by qyot27 on 2010-03-14
It's just Nautilus.  I have a folder with just over a thousand music files in it, and Nautilus takes forever to cache and display them all (and I have it set to display in Detailed List view).  Dolphin, on the other hand, loads the contents of the folder near-instantly.

---

### Post by 2hot6ft2 on 2010-03-14
Mine is fast.
You can make nautilus faster by doing a little tweaking.

Edit > Preferences
Display tab > Icon Captions:
Limit or set all options to none

Preview tab
Set each to never, or use only those you really need.

And
View
Choose either list or compact instead of icons.

---

### Post by NightwishFan on 2010-03-14
My milage varies. Nautilus seems overall faster than Dolphin, but I never open directories much bigger than /usr/share/doc.

Try this tweak on a desktop to improve file manager performance:

For a temporary test, lost on a reboot, do:
```
sudo sysctl vm.vfs_cache_pressure=50
```

To make it permanent do:
```
sudo su
```
then
```
echo 'vm.vfs_cache_pressure = 50' >> /etc/sysctl.conf
```

To undo it, open /etc/sysctl.conf as root, and delete the bottom line that says vm.vfs_cache_pressure = 50

---

### Post by mikewhatever on 2010-03-14
Mine is not slow, but I don't have folders with 1000 files in them. In fact, that sounds like a really messy storage scheme. How do you find files in there?

---

### Post by nmccrina on 2010-03-14
> **mikewhatever said:**
> Mine is not slow, but I don't have folders with 1000 files in them. In fact, that sounds like a really messy storage scheme. How do you find files in there?

Try opening /usr/bin ;)

---

### Post by Meshach on 2010-03-14
My Ubuntu (Karmic Koala) is freshly re-installed so it's really really fast.

---

### Post by prshah on 2010-03-14
> **yester64 said:**
> a folder with a lot of files (>1000) its slow slow slow.

Same problem here; I have a photos folder for each year (2006, 2007, 2008..) and opening the folder, even with previews turned off and no subfolders, takes ages (about 45~75 seconds) to create the list of files.

And I'm still using ext3, so I guess that the filesystem is not an issue.

---

### Post by yester64 on 2010-03-14
As far as filesystem goes, mine are ext4. But i hear that certain filesystem are better for certain tasks. So perhaps i should've mixed it.

Do you all have ext4 or ext3? Or do you use a different one?
Yes, i do have a lot of items in a folder. But i try to diverse them somehow. But to do that, i have to go into the folder. So if nautilus is overburdend with that, what can i do?
My stand is that a file manager should be fast. Especially today where you easy can have hundereds of pictures from a weekend with your camera.
The system should work for me and not the other way around.
But i try all solutions that get presented here. If one works i let you know.

---

### Post by mikewhatever on 2010-03-14
> **nmccrina said:**
> Try opening /usr/bin ;)

Just did. It took about 5-6 seconds, and gave a vivid representation of what it's like to scroll through a messy folder. Luckily, I never have to, however, it seems like the OP's main issue is thumbnails. What is the output of **du -hs ~/.thumbnails/**?

---

### Post by yester64 on 2010-03-14
> **mikewhatever said:**
> Just did. It took about 5-6 seconds, and gave a vivid representation of what it's like to scroll through a messy folder. Luckily, I never have to, however, it seems like the OP's main issue is thumbnails. What is the output of **du -hs ~/.thumbnails/**?
here we go
> 716K    /root/.thumbnails/

---

### Post by richs-lxh on 2010-03-14
To speed up Ubuntu itself you could shutdown services/daemons that start at boot, for nautilus try "list" view as default instead of thumbnails.

Regarding photos specifically, our family desktop is Ubuntu KK, it has a separate Ext3 80Gb harddrive for storage and we access all our photos from Picasa. We also have an external 320Gb harddrive which is also Ext3 (by choice for stability).
They all get indexed and then later on only the newest photos get added if you tell it to watch certain directories for new additions. You could also use other Photo viewers.

If you wish to try a lighter file manager, try Pcmanfm, or as I use on Fluxbox desktop, Xfe which is super lightweight but is fully featured.

---

### Post by VCoolio on 2010-03-14
My ubuntu isn't slow, mainly because I hardly use any apps that come with ubuntu by default. Your slow nautilus performance can have something to do with your icon theme too; see if changing it makes a difference. Also try the latest thunar as an alternative if you need network browsing and sharing capabilities, else the one in the repos will do too.

---

### Post by yester64 on 2010-03-14
> **VCoolio said:**
> My ubuntu isn't slow, mainly because I hardly use any apps that come with ubuntu by default. Your slow nautilus performance can have something to do with your icon theme too; see if changing it makes a difference. Also try the latest thunar as an alternative if you need network browsing and sharing capabilities, else the one in the repos will do too.

well, i have now a folder which has about 30000 files in it. I would like to sort this folder out since i always push that for some other day.
I disabled now almost everything in nautilus. No previews at all. Just plain text and no thumbnails.
Nautilus is still working for about 3 minutes now with no files shown up.
I get the impression that it is also ext4, since most of you have ext3 running.
I mean it can not be that i have problems and none of you have. So i must doing something wrong that i can get not results.
What do photographers who have maybe more that i have? 
Oh i tried also gnome commander (which i like) but even that gets stuck in the loading.
Like i said, i think i am doing something wrong and i consider to reinstall the system.

---

### Post by Post Monkeh on 2010-03-14
> **yester64 said:**
> well, i have now a folder which has about 30000 files in it. I would like to sort this folder out since i always push that for some other day.
I disabled now almost everything in nautilus. No previews at all. Just plain text and no thumbnails.
Nautilus is still working for about 3 minutes now with no files shown up.
I get the impression that it is also ext4, since most of you have ext3 running.
I mean it can not be that i have problems and none of you have. So i must doing something wrong that i can get not results.
What do photographers who have maybe more that i have? 
Oh i tried also gnome commander (which i like) but even that gets stuck in the loading.
Like i said, i think i am doing something wrong and i consider to reinstall the system.

i think the problem is the number of files - no one else is dealing with that many, so it's hard to compare experiences.

i do find nautilus a little clunky sometimes, have you tried pcmanfm or thunar? they're a LOT quicker dealing with multiple files.

---

### Post by mikewhatever on 2010-03-14
> **yester64 said:**
> here we go
716K /root/.thumbnails/ 

I didn't ask for .thumbnails from /root, obviously, there is nothing there. Anyway, I think 30,000 photos in one folder is insane. ;)
Just my humble opinion.

---

### Post by Post Monkeh on 2010-03-14
> **mikewhatever said:**
> I didn't ask for .thumbnails from /root, obviously, there is nothing there. Anyway, I think 30,000 photos in one folder is insane. ;)
Just my humble opinion.

if he can open the same folder in windows with minimal delay, he should be able to do it in ubuntu too.

---

### Post by richs-lxh on 2010-03-14
If he can open it in Windows it's probably an ntfs file system. Maybe there is an ntfs-3g problem?

---

### Post by qyot27 on 2010-03-14
> **mikewhatever said:**
> Mine is not slow, but I don't have folders with 1000 files in them. In fact, that sounds like a really messy storage scheme. How do you find files in there?
Alphabetically, %artist% - %title%.  But it's not 'messy', it's just dedicated to one and only one purpose.  I hardly ever alter what's in there (save to add to it), or can do so remotely, so trying to find things in it is rather simple.  As they're *music* files, playlists and Jump to file functions help a lot.

And technically, the music folder I'm talking about is a copy of select stuff I want to use with Songbird or sync with my iPod with gtkpod.  My full digital music collection is easily several times larger, although I don't have an exact number.

---

### Post by Post Monkeh on 2010-03-14
> **richs-lxh said:**
> If he can open it in Windows it's probably an ntfs file system. Maybe there is an ntfs-3g problem?

it's a nautilus problem i think, i have similar delays opening folders with massive numbers of files, but thunar, and particularly pcmanfm, are far faster.

---

### Post by mikewhatever on 2010-03-14
> **qyot27 said:**
> Alphabetically, %artist% - %title%.  But it's not 'messy', it's just dedicated to one and only one purpose.  I hardly ever alter what's in there (save to add to it), or can do so remotely, so trying to find things in it is rather simple.  As they're *music* files, playlists and Jump to file functions help a lot.

And technically, the music folder I'm talking about is a copy of select stuff I want to use with Songbird or sync with my iPod with gtkpod.  My full digital music collection is easily several times larger, although I don't have an exact number.

Are you saying that you have a folder with a pile of mp3s inside, say 10,000, and no subfolders, and you open it in Nautilus and start sorting by title and artist? That's insane too.:)
I have a music collection myself, but everything is in order there, every artist and every album gets a separate folder. Real easy to browse even in Nautilus.

---

### Post by MooPi on 2010-03-14
I just performed a simple test.  I grabbed my stop watch and opened /usr/bin. Took 11 seconds to display all 1590 files. I use pcmanfm and not Nautilus. For the most part PCmanFM is fairly fast with minimal lag.

---

### Post by _h_ on 2010-03-14
> **MooPi said:**
> I just performed a simple test.  I grabbed my stop watch and opened /usr/bin. Took 11 seconds to display all 1590 files. I use pcmanfm and not Nautilus. For the most part PCmanFM is fairly fast with minimal lag.

Interesting. It took me 5-6 seconds to read 1,344 files in my /usr/bin with Nautilus.

---

### Post by swoll1980 on 2010-03-14
> **_h_ said:**
> Interesting. It took me 5-6 seconds to read 1,344 files in my /usr/bin with Nautilus.

1692 files in my /usr/bin took 12 seconds.

---

### Post by xpod on 2010-03-14
> **MooPi said:**
> I just performed a simple test.  I grabbed my stop watch and opened /usr/bin. Took 11 seconds to display all 1590 files. I use pcmanfm and not Nautilus. For the most part PCmanFM is fairly fast with minimal lag.

With a standard Ubuntu/Gnome setup on my Desktop Nautilus took 7 seconds with 2,260 files and PCMan File Manager on my laptop, with LXDE, was less than a second with only 1178.

EDIT: Just tried on a Toshiba laptop with same 1.7Ghz/512MB as the Compaq, with the same lxde/pcmanfm setup and it too was pretty much instantaneous although it`s install is still quite fresh and only has 922 files.

---

### Post by NightwishFan on 2010-03-14
'/usr/bin' with 1358 items loaded in just under 6 seconds. Using Nautilus 2.28.4 on Debian Sid with ext4 filesystem.

---

### Post by impert on 2010-03-14
> I just performed a simple test. I grabbed my stop watch and opened /usr/bin. Took 11 seconds to display all 1590 files

I don't have a watch of any sort, but it takes less than a second with Nautilus on my low-end machine after some of the tweaks on this thread. As fast as thunar in Sidux, for instance.

---

### Post by HoboJ on 2010-03-14
I just fooled around with nautilus by opening up several folders full of pictures. Took about 20 seconds to get ~400 thumbnails up but beyond that no major slowness.

---

### Post by qyot27 on 2010-03-14
> **mikewhatever said:**
> Are you saying that you have a folder with a pile of mp3s inside, say 10,000, and no subfolders, and you open it in Nautilus and start sorting by title and artist? That's insane too.:)
I have a music collection myself, but everything is in order there, every artist and every album gets a separate folder. Real easy to browse even in Nautilus.
Not quite (and most of the time when I open a folder in a file browser, I order them by Date Modified, they're just *named* %artist% - %title%).  As I actually get these files from iTunes/Amazon MP3/my own CDs/whathaveyou, I just rename them to %artist% - %title%, so that when they finally trickle down to any folders later, they still retain that nomenclature.  There's a system to all the sorts of organization that go on for everything I do with files, but trying to explain it is rather odd and would take too long (also, it applies more to the Windows side of my computer than the Ubuntu side; once things hit external drives, the organization is much simpler).  In general, my computing habits are *extremely* file manager-based rather than desktop-based.  I almost feel naked if I'm using an OS and don't have the file manager open (unless I have a good reason *not* to, anyway).

The main part of the collection is on a 30 GB external (in truth, though, this 'main part' is probably a little less than half, size-wise - it's just the most that resides in one place; it's also where the oldest stuff is, covering approximately 2000-early 2007 with some stragglers from subsequent years).  It's got one folder on it with all the songs in it (and indeed, no subfolders), and on the root of that drive is a set of playlists, some of which have all the files in said folder in them.  I then open these playlists in Winamp, Audacious, Songbird, or so on.  All such searching takes place in the music player rather than the file browser.  If I have to do custom playlists I can use this as a reference to compose the playlists manually.

---

### Post by mamamia88 on 2010-03-15
my ubuntu is faster than windows 7 and osx by a long run. one of the main reasons i run it.

---

### Post by witeshark17 on 2010-03-15
No slowness here... :popcorn:

---

### Post by etnlIcarus on 2010-03-15
I've got an Athlon 2800+ w/ 512mb of RAM.

The most dramatic performance increases have come from:
- Setting swappiness to 100 (google it).
- Installing rcconf and using it to disable, "on demand", a CPU scaler, which adversely affects many applications and makes Firefox damn near unusable.

---

### Post by Psumi on 2010-03-15
> **etnlIcarus said:**
> I've got an Athlon 2800+ w/ 512mb of RAM.

The most dramatic performance increases have come from:
- Setting swappiness to 100 (google it).
- Installing rcconf and using it to disable, "on demand", a CPU scaler, which adversely affects many applications and makes Firefox damn near unusable.

does turning off ondemand via rcconf disable it permanently or do we have to edit something else?

also, do we have to restart to see the effect?

---

### Post by etnlIcarus on 2010-03-15
Permanent. Not sure if you have to restart.

---

### Post by Psumi on 2010-03-15
disabling ondemand does make it slightly faster; but because I use flash, and my computer doesn't meet the recommended specifications (2 GHz processor single-core) flash takes up half my CPU still.

My IBM T41 has a 1.60 GHz single-core (Not HT, so no precious logical cores to save me.)

---

### Post by etnlIcarus on 2010-03-15
Have you considered Flashblock? Sensible FF extension, makes it so only the flash content you choose to load... well, loads. That sentence got away from me. >.>

---

### Post by wojox on 2010-03-15
> **etnlIcarus said:**
> I've got an Athlon 2800+ w/ 512mb of RAM.

The most dramatic performance increases have come from:
- Setting swappiness to 100 (google it).


Set it to 100 or 10?

---

### Post by Psumi on 2010-03-15
> **etnlIcarus said:**
> Have you considered Flashblock? Sensible FF extension, makes it so only the flash content you choose to load... well, loads. That sentence got away from me. >.>

No. I need flash on some sites I visit due to their navigation being flash (IE: PlayStation Network Forums, Homestarrunner.com, etc.)

I'm staying without a flash blocker until I decide to get one. Also, I have my hosts file edited to have all those ad sites blocked.

---

### Post by etnlIcarus on 2010-03-15
> **wojox said:**
> Set it to 100 or 10?

100. It Causes aggressive disk caching while idling.

10 will make your system choke the moment it begins to run low on RAM, as it suddenly has to take a large portion of CPU time to transfer a lot of cached data in the RAM, to disk. It's been my anecdotal observation that it's also worse at choosing what to cache to disk, resulting in long pauses when switching apps.

With 512mb of RAM, 1gb of swap and swappiness set to 10, your RAM will have to be about 80-90% full, before it'll start transferring data to swap. Even once it's done what it needs to do, once your swap is 5% full, you start noticing a performance drain, as your RAM is nearly full and it's constantly swapping stuff in and out. 

With the above config and swappiness set to 100, you'll see the swap usage slowly increase once you're using more than about 50% of your RAM. However, there won't be a noticeable performance drain until your swap is about 20% full (you RAM will probably be about 70-80% full at this point).

Keep in-mind the swap is twice the size of the RAM so double all the swap percentages I've listed here.

So swappiness set to 10, gives you 512 * .85 + 1024 * .05 = 486mb of memory usage before your system turns to mud. You might as well not bother with swap at all.

Swappiness of 100 gives you 512 * .75 + 1024 * .20 = 588mb of memory usage, before things turn to mud.

It's worth pointing out that a swappiness of 100 gives you caching behaviour very similar to that of a stock XP install. If you're one of the people who's complained that XP seems faster than Ubuntu, that's a large part of the reason.

---

### Post by mikewhatever on 2010-03-15
etnlIcarus, swappiness=100 makes sense with 512MB of RAM or less. However, the OP has reported having 4GB, eight times that amount, so why would it matter in his case? Even with 1GB of RAM, you should be OK with swappiness varying from 40 to 60.

---

### Post by yester64 on 2010-03-15
> **etnlIcarus said:**
> I've got an Athlon 2800+ w/ 512mb of RAM.

The most dramatic performance increases have come from:
- Setting swappiness to 100 (google it).
- Installing rcconf and using it to disable, "on demand", a CPU scaler, which adversely affects many applications and makes Firefox damn near unusable.


I have to excuse myself for being a little absent.
I will try out the settings you pointed out. It will hopefully lead to a more speedier result.
What borthers me a little is, that it seems that the problem i have, no one else has.
I do grab a lot of things from newsgroups too and if i grab a whole newsgroup you can easely get over 1000 items.
What i want to say with that is, that it is not organizing but rather receiving a chunck of items and having to sort them out later.
But what gives me the creeps is that even after i disabled all thumbnails in nautilus and everything is on off it still takes a couple of minutes before i see any item.
Perhaps i have a old system or i did something wrong or i do not know...

I post my system specs if that helps. 
The reason for my posting was not ranting about it, but to find a solution to the problem.

---

### Post by Ginsly on 2010-03-15
Does it take that long every time you open that folder, or just the first time?
Opening /usr/bin in thunar for me (Xubuntu) took 11 seconds with 1492 files, but the second time it was only 1.7 seconds. Maybe there is cachey thingy stuff (*insert correct technical term*) going on in Nautilus too?

Also agree with Post Monkeh and VCoolio in giving thunar a go. It seemed to me to be just as quick with Gnome the last time I used it, and not many dependancies

---

### Post by yester64 on 2010-03-15
I think i found the solution. that is if you can sacrifice thumbnails.

You need to use the gconf-editor and edit under ***apps*** ~ ***nautilus*** ~ ***preferences*** ~ ***thumbnail-limit*** and set it to '**0**'
Then its right away present what ever and how many items you have in the folder.

---

### Post by PC_load_letter on 2010-03-15
> **MooPi said:**
> A large number of files will slow things down yes. Another thing might be that your hard drive is filling up. So how full is your drive ? My Ubuntu is very fast :p

+1, my Karmic 64bit install is REALLY fast, I'm blown away. I opened a folder from Docky, it has 624 desktop wallpaper images, and it completely opened, in list view, almost instantaneously. Took like 3~4 seconds more to render all the icons.

---

### Post by etnlIcarus on 2010-03-15
> **mikewhatever said:**
> etnlIcarus, swappiness=100 makes sense with 512MB of RAM or less. However, the OP has reported having 4GB, eight times that amount, so why would it matter in his case? Even with 1GB of RAM, you should be OK with swappiness varying from 40 to 60.

I never said it would. See my original post and the one above yours. I've disclaimed multiple times that that is my PC w/ 512mb of RAM.

---

### Post by stephenmac7 on 2010-04-05
My ubuntu is not that fast but it can still open a file considering I have a super slow computer. I have windows on this computer but it is so slow it won't boot. I have 512 mb of random access memory

---

