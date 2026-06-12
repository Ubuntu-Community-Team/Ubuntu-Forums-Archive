---
title: "Announcing: yet another application launcher"
date: 2008-08-11
forum: The Cafe
---

### Post by dracule on 2008-08-11
I was away w/ very slow internet so i whipped up this:

[[img]http://img392.imageshack.us/img392/4564/screenshot1wm2.png[/img]](http://imageshack.us)

It is pronounced ya'all like in Southern USA.

it stands for yet another application launcher

You are meant to associate file extensions and folders with each launcher. 

for example, associate *.doc w/ Word to have a list of all your documents that you can then launch with word (or open office :) )
[[img]http://img511.imageshack.us/img511/1356/screenshot2ih7.png[/img]](http://imageshack.us)

It features text filtering so just start typing the name of the app to auto locate it.

[[img]http://img207.imageshack.us/img207/1577/screenshot3hv2.png[/img]](http://imageshack.us)

You can also edit the launchers (lol i couldnt install a gui library because of the slow internet :p)

[[img]http://img207.imageshack.us/img207/3973/screenshot4uq5.png[/img]](http://imageshack.us)


Known issues:
memory usage
it may just crash because of invalid configuration (in that case run setup.bat again)
you cant see the launcher's names

This is like alpha software. I made it for my own personal use but i thought I would give it to you guys too. :)

It includes crystal icons, but you can use what ever you want. Ijust liked the looks of them.

also sorry of the border sucks or anything, I made it. :P

I probably wont be able to fix any bugs for a day or two, so just post them if you have any.
I havent tested the .zip file so it may not work, idk.
I have only tested this on vista.

[old first release](http://www.wikiupload.com/download_page.php?id=51809)
EDIT:
new release (same as in post #2):
[dont use](http://www.wikiupload.com/download_page.php?id=51845)
Alt:
[yaal.zip](http://www.filefactory.com/file/695c41/n/yaal_zip)

Lite version (w/o icons)
[yaal.zip](http://www.filefactory.com/file/c1c31e/n/yaal_zip)


Corrected Setup (w/o unneeded zip files) in an exe form:
[setup.zip](http://www.filefactory.com/file/cb1d56/n/setup_zip)


to install from the setup.exe:
run setup.exe
go through the dialog till you finish
read the readme
press F9 to bring up yaal

the hotkey can be changed by changing the properties on the desktop.









As many have pointed out, this is for windows only. 
This project is written in python, and the only reason it is not on linux is because my computer broke and I needed a portable developing environment as I went from computer to computer. 
I plan on making this in Linux as soon as my computer comes back to me (at least 3 more days). As I have said it is written in python so only around 5-6 lines need to be changed in order for this to work in linux.

---

### Post by dracule on 2008-08-11
[http://www.wikiupload.com/download_page.php?id=51845](http://www.wikiupload.com/download_page.php?id=51845)

Fixed issue w/ default launchers.

Now to launch any file or folder with default app:
put file as command

put * as extension

---

### Post by SunnyRabbiera on 2008-08-11
This is a windows app, and we are interested how?

---

### Post by Delever on 2008-08-11
Who is going to install Yet Another Application Launcher on Windows? :lolflag:

Google results for "Yet Another Application Launcher": 104.000

---

### Post by Newuser1111 on 2008-08-11
> **SunnyRabbiera said:**
> This is a windows app, and we are interested how?WINE? Unless that can't run it.

EDIT:
SiteAdvisor says that the site it's being hosted on is dangerous. [Link](http://www.siteadvisor.com/sites/wikiupload.com?ref=safe&client_ver=FF_26.6_6274&locale=en-US&premium=false&client_type=FF&aff_id=0)
But that site might only be bad to Windows.(So don't go to it in Windows)

---

### Post by dracule on 2008-08-11
lol, my linux computer is in the shop so i wont have it for another 3-5 days :(

but this is written in python w/ pyglet so it will be easy to port. All I would have to do is change about 5 lines (it currently uses a windows library for copy and past and to find out the documents folder) but I dont have linux to test it.

I dont want it to be main stream because:
I have no money for hosting
I have no money for domain
I dont have enough time to help a bunch of people.

I just wrote it for my own personal use because I didnt want to use my mouse to launch emulators. now all i have to do is set up mednafen and have the extensions link to it and i dont have to mess w/ the command line anymore.

---

### Post by phrostbyte on 2008-08-11
Nice work.

---

### Post by Snoophyx on 2008-08-11
nice,keep working! a.deb soon????

---

### Post by Newuser1111 on 2008-08-11
The ZIP file won't open.

---

### Post by dracule on 2008-08-11
> **Newuser1111 said:**
> The ZIP file won't open.

try this:
[yaal.zip](http://www.filefactory.com/file/695c41/n/yaal_zip)

Lite version (w/o icons)
[yaal.zip](http://www.filefactory.com/file/c1c31e/n/yaal_zip)

I never had trouble w/ wikiupload before, but it seems to like timeout halfway through.

---

### Post by Newuser1111 on 2008-08-11
> **dracule said:**
> try this:
[yaal.zip](http://www.filefactory.com/file/695c41/n/yaal_zip)

Lite version (w/o icons)
[yaal.zip](http://www.filefactory.com/file/c1c31e/n/yaal_zip)

I never had trouble w/ wikiupload before, but it seems to like timeout halfway through.The one I downloaded from "wikiupload" was 1.7MB while the one at "FileFactory" is 33.85 MB.

Just asking, Don't you know of any SAFE upload sites?

---

### Post by smartboyathome on 2008-08-11
> **dracule said:**
> try this:
[yaal.zip](http://www.filefactory.com/file/695c41/n/yaal_zip)

Lite version (w/o icons)
[yaal.zip](http://www.filefactory.com/file/c1c31e/n/yaal_zip)

I never had trouble w/ wikiupload before, but it seems to like timeout halfway through.

It downloads fine for me from here, and opens correctly. Just letting any skiddish people know. :)

---

### Post by 50words on 2008-08-11
Why not start a project on Sourceforge?

---

### Post by smartboyathome on 2008-08-11
Also, please make it compatible with Linux? I can test it. You don't have to maintain it, just provide it to us. :)

---

### Post by dracule on 2008-08-11
> **smartboyathome said:**
> Also, please make it compatible with Linux? I can test it. You don't have to maintain it, just provide it to us. :)

yeah, I will make it available for linux.
I use linux exclusively on my main machine so believe me when I say it will be on linux. :D

Here is what I plan to release (soon):
1) display launcher's name
2) provide more options for launch commands
3) linux support
4) reduce size
5) reduce memory footprint
6) create a better GUI
7) create a browse thing for choosing icon



I was going to start a sourceforge project but got confused when I had to choose a license.

---

### Post by dracule on 2008-08-12
Anyways, I made an installer for fun:
[setup.zip](http://www.filefactory.com/file/cb1d56/n/setup_zip)

it automatically does everything for you, so all you have to do is 
1)unpack and double click setup.exe to bring up the install dialog
2)press F9 to bring it up (i dont think f9 is used for anything)

lol, the program uses compressed libraries which are kept in zip files, so when i was trying to save them i accidently doubled the size. so i stripped them all out
now it is only 13mb w/ all the icons.

---

