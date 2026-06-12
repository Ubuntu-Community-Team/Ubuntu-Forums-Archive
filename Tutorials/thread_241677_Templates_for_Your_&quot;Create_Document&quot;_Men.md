---
title: "Templates for Your &quot;Create Document&quot; Menu"
date: 2006-08-22
forum: Tutorials
---

### Post by stalefries on 2006-08-22
I've made a set of documents for the "Create Document" submenu in the Nautilus context menu. You can read about them and download them [here]("http://stalefries.googlepages.com/howtosnautilustemplates").

Feel free to post your additions and modifications here, and I'll include them in future versions.

Edit: updated the linked page with some links to sites with more templates. (scroll to the bottom).

If you just want the templates now, do the following:

```
wget http://stalefries.googlepages.com/Templatesv4.zip
```

---

### Post by nwgray on 2006-08-23
stalefries
  Thanks for the templates!! I dont' see them though when I right-click on the desktop and select Create Document. I put the folder in /home first and then /home/<username> but neither worked. Do I have to link it somehow? Any other places I should check?

---

### Post by stalefries on 2006-08-23
In "/home/username/Templates" place the documents you want. Make sure to unzip them. Make sure Templates is capitalized.

Also, glad to know that this got posted.

---

### Post by mejy on 2006-08-23
Is there any way to hide the folder?  I think there's a config file you can put in your home directory to hide them in nautilus, but I can't remember the name.  It's not really important, but I find the templates directory annoying :(.

Anyway, great collection of templates!

---

### Post by stalefries on 2006-08-23
I heard of something like that, and would love to have it, but I don't know anything about it. Sorry.

Edit: I usually hate about.com, but this time they managed to shine. Here's a link to some information on the topic.

[http://linux.about.com/library/gnome/blgnome6n6r.htm](http://linux.about.com/library/gnome/blgnome6n6r.htm)

---

### Post by mejy on 2006-08-23
> **stalefries said:**
> I heard of something like that, and would love to have it, but I don't know anything about it. Sorry.

Edit: I usually hate about.com, but this time they managed to shine. Here's a link to some information on the topic.

[http://linux.about.com/library/gnome/blgnome6n6r.htm](http://linux.about.com/library/gnome/blgnome6n6r.htm)

Thats the one!  I'd used it on my Horay -> Breezy install and couldn't find it when I did a fresh dapper install... nice job. :-D

Edit: It even hides them in the browse dialogue - that never worked in Horay/Breezy.

---

### Post by stalefries on 2006-08-24
Good to know it worked. I had wanted to do this previously, but never got around to looking it up. Now I did, and it's great!

I imagine that extra functionality comes from the new version of Gnome/GTK. Each version brings new little tweaks that always make it better.

---

### Post by dj-toonz on 2006-08-24
Hi all, just had a look @ the web site myself and been trying for ages hide the Templates folder from view aswell but everytime i add the . before the folder name the templates dont show up after i log off and log back in :-( on the site aswell it says or create a text file named .hidden in the same folder, and add its name to it, as in the example below:
filename foldername but i havent a clue what to enter for the filename foldername :-( what do i need to do to hide the folder but keep the templates what i want i.e .doc .txt and so on showing up when i right click and create template ? i've been going round and round in cicules for days trying to find it out, i can hide normall folders like the scripts and keep them showing up but not the templates :-( i must of overlooked something bu what, could somebody help me pls thx

---

### Post by SeanHodges on 2006-08-24
Hopefully this will help: [http://openofficetechnology.com/node/50](http://openofficetechnology.com/node/50)

Change Template path to be .Template in the Templates path, then change the actual Template directory to include the dot prefix.

Hopefully the directory should then be hidden.

Sean

---

### Post by dj-toonz on 2006-08-24
found it out after a google search :-p was getting confused as what to put where it says filename foldername for the .hidden file in ~home lol one of the sites it sent me to was gnome-look.org after typing in nautilue templates i just had to add a .hidden (name of file) in home then open it up with gedit and enter Templates (or what folder you want to hide) in the file then save & bob's your uncle , Templates is hidden and still showing up in create documents, phew , anyway now that's sorted good how two btw, learning new stuff about ubuntu every day what i never knew before & people are so helpfull aswell , cheers :-p

---

### Post by stalefries on 2006-08-24
But that only works in OpenOffice. Although, it is a nice feature.

---

### Post by stalefries on 2006-08-25
Just to make sure it shows up on the front page of the Tips 'n' Tricks subforum, I'm posting a reply here to let everyone know I've updated the files.

---

### Post by nwgray on 2006-08-25
> **stalefries said:**
> In "/home/username/Templates" place the documents you want. Make sure to unzip them. Make sure Templates is capitalized.

Also, glad to know that this got posted.

I had to create the folder Templates and then double-click the .zip file to open and then extract to that folder. I originally tried to just right click the zip file, select Extract Here, and then rename the folder to Templates. It is now working fine. 

Thx stalefries!

---

### Post by stalefries on 2006-08-25
Good to know it worked.

---

### Post by slibuntu on 2006-08-25
Love it, easy install, great list, thanks!

---

### Post by judofyr on 2006-08-25
Lovely! Very useful;)

---

### Post by juicymixx on 2006-08-25
Hey stalefries, thanks for putting these templates together!   I noticed that in my Dapper install choosing 'Create Document' will give me the options from the 'Templates' folder only when I'm in a Nautilus window, not on a blank area of the desktop.   Is this normal behavior?:confused: 

Thanks again!:rolleyes:

---

### Post by Kaobear on 2006-08-25
Awesomely done, much kudos

---

### Post by Spudgun on 2006-08-25
Worked great. The advice given on the authors site on how to hide the Templates file also worked.

---

### Post by stalefries on 2006-08-25
juicymixx, it should work, unless you have a program other than nautilus controlling the desktop.
Or. if you have told Nautilus not to put icons on the desktop.

---

### Post by juicymixx on 2006-08-27
Hey stalefries,
Thanks again for the templates!   I've been using them like crazy!
I'm working out of a recent Dapper install.   As far as I know, I have Nautilus controlling the desktop.   Where would I go to find out if Nautilus can put icons on the desktop.   If I create a file or folder using the templates, I can move it to the desktop...   Just not create one on the desktop directly...:confused: 

Thanks!

---

### Post by stalefries on 2006-08-27
Hmm. In a terminal, open "gconf-editor". When it opens, navigate to "apps>nautilus>preferences". In the pane on the right, make sure that "show_desktop" is checked.

---

### Post by stalefries on 2006-08-31
/Update bump!

---

### Post by Frostmourne on 2006-08-31
I keep getting this error when trying to extract the zip, can anyone help me?

```
[/home/caleb/Desktop/Templatesv2.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/caleb/Desktop/Templatesv2.zip or
        /home/caleb/Desktop/Templatesv2.zip.zip, and cannot find /home/caleb/Desktop/Templatesv2.zip.ZIP, period.
```

---

### Post by stalefries on 2006-08-31
Someone PM'ed me about this problem, too. Apparently, Firefox mis-downloads the file, and stops about half-way through. His solution was to use the Firefox extension DownThemAll to download it. He said it worked doing it that way. You can find that extension [here]("https://addons.mozilla.org/firefox/201/").

I would post the file here, but it's just too darn big for the forum limits.

---

### Post by Frostmourne on 2006-08-31
Thank you, I got it working. Instead of downloading more software I simply ran

wget [http://alan.hussey.googlepages.com/Templatesv2.zip](http://alan.hussey.googlepages.com/Templatesv2.zip)

from the terminal.

---

### Post by stalefries on 2006-08-31
Good idea! I should've thought of that. I'll add it to the main post.

---

### Post by stalefries on 2006-10-06
Does anyone know where the tags came from? Did I miss a memo? They're at the top of the page, below "**HOWTOs, Tips & Tricks** The place to find General, KDE, and Gnome Customization Tips & Tricks."

Anyone know what's up?

---

### Post by hikaricore on 2006-11-06
Thank you for these :)  Nice to see that menu not being empty anymore.

---

### Post by stalefries on 2006-11-06
Glad you appreciate it. If I dig up anymore convenient files, I'll make a new version. Feel free to suggest new templates!

---

### Post by stalefries on 2006-12-15
Edited a link in the first post. I plan on uploading a new version in the next few days.

---

### Post by stalefries on 2006-12-15
New version posted! Not much new, I added a .xar file, and slightly reorganized it.

---

### Post by jdralphs on 2006-12-19
I'm getting this error even when using wget.

```
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/jdralphs/Templatesv4.zip or
        /home/jdralphs/Templatesv4.zip.zip, and cannot find /home/jdralphs/Templatesv4.zip.ZIP, period.
```

---

### Post by zerwas on 2006-12-19
Same error here.

---

### Post by zanglang on 2006-12-19
Is the version 4 zip file corrupted/not completely uploaded? The .hidden file is a nice trick though. Ah, something new to learn everyday. :P

---

### Post by stalefries on 2006-12-20
I've uploaded a fixed version. Note to self: test everything before uploading it. :\

---

### Post by Howlin' Hobbit on 2006-12-24
Ok. I have my Templates folder created, a couple templates in it and the folder hidden. It works except I have the same problem as juicymixx, when I click on the desktop to create a document it gives me "no templates installed." In the gconf editor under apps>nautilus>preferences "show_desktop" is checked.

What else am I missing?

---

### Post by stalefries on 2006-12-30
Have you tried logging out/logging back in? If that didn't help, I would file a bug, since there's something wrong.

---

### Post by Howlin' Hobbit on 2006-12-30
> **stalefries said:**
> Have you tried logging out/logging back in?
Several times but I didn't think to re-test until your message came in. Looks like it's working now.

Thanks!

---

### Post by wzzrd on 2006-12-31
Why are most of the OpenDocument templates real templates (ott instead of odt, for example)? I´ld think .odt would be more useful and more used than ott?

---

### Post by stalefries on 2007-01-01
In Openoffice, you can define custom locations for templates. Of course, they have to be real templates to work.

I may make a new version to fix this.

---

### Post by johntheunique on 2008-01-16
I tried this and similar solutions and found it wasn't working for me with Ubuntu 7.10 (Gutsy). After some research I found the solution. This solution also allows the user to hide the templates folder. Just edit ~/.config/user-dirs.dirs and set the XDG_TEMPLATES_DIR to whatever you want it to be. If you want it hidden, just make sure to use a dot directory.

---

### Post by motoperpetuo on 2008-03-01
thanks! this worked like a charm. i'd click on that little "thank you" link to do an official thank you, but it's nowhere to be found.

---

### Post by Palmyra on 2008-03-01
For those who are having a problem with Nautilus recognize the newly extracted templates, understand that there *is* a problem that must be fixed first.  Ideally, you would be able to follow the instructions the OP provided from the beginning and let it be.  Because of an apparent problem with Gutsy, follow the second post in this thread:

[http://ubuntuforums.org/showthread.php?t=590494](http://ubuntuforums.org/showthread.php?t=590494)

The problem is that, after you delete the original templates folder that was created by Ubuntu upon system installation, Nautilus will not recognize any user created templates folder.  Also, a link that designates the templates folder you created is apparently faulty.  The simple change mentioned in the second post in the above thread will solve this.

Now, when you extract templates into the Templates folder, you should be good to go.  If you want to hide the folder, change the link to .Templates, and change the folder in Nautilus to .Templates.  If this is too much of a problem, don't do it.

---

### Post by hezuo on 2009-01-21
Thanks a lot! it did help me.

---

### Post by dimbulb1024 on 2009-03-06
Thanks stalefries. Just what I was looking for.

---

### Post by sanjiro on 2013-01-30
Thanks a lot ! :)

---

### Post by howefield on 2013-01-30
Old thread closed.

---

