---
title: "adesklets -&gt; verse of the day on Desktop!"
date: 2006-12-27
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2006-12-27
Hey, for anyone interested.  I was playing around with adesklets today, and modified and existing one called news feed to display Bible verses on your desktop from an RSS feed.  It is the King James Version, modifying it to display others is rather simple, you will have to visit the website and plug a different rss feed into the config.txt.  No guarantees as I'm not a programmer.  Works great on my computer.  Attached is a screen shot so you can see it in action :D.  If you want the tarball you can get it [here.]("http://www.rices4peru.com/ftf/goodnewsfeed-0.0.4.tar")  Enjoy!  If I could figure out how to manipulate it enough to use the .sword text from GnomeSword, or Bible time, I would, but I don't know that much about what I'm doing.  Oh, I renamed it goodnewsfeed  instead of the newsfeed it was called. :)  Enjoy.


Shane

---

### Post by ubuntu27 on 2006-12-28
Good job Shane. :)

---

### Post by shane2peru on 2006-12-28
Here is a little How to:

Ok here are some simple instructions for installing and using the goodnewsfeed desklet.  After you download it and save it in /home/username  you are going to want to extract it.  Either open your favorite file manager, and right click on the file named goodnewsfeed.... .tar  and select extract here.  Or, if you prefer the terminal you can type:```
tar -xvf goodnewsfeed(tab)
```  Where you see (tab) hit the tab key and it will finish that file name for you.  

Ok, once it is extracted, you will want to keep it in a place where you won't delete it.  That is the reason I keep all mine in a folder called .desklets.  If you want to make that folder you can type in the terminal: ```
mkdir .desklets
``` - Note you should be in your home directory for this.  

Next lets move this newly extracted folder to the newly created folder.  In the terminal we are going to put:```
mv goodnewsfeed(tab) ~/.desklets/
``` ;) don't forget about the tab key trick.

(This step can be skipped it is configuration, or done later.)
Now if you want to configure your desklet with another translation it can be done.  You are going to need to search for another Verse of the Day rss feed with the translation you want, I would do this in advance.  This is really just an RSS feed desklet, and we are using Bible verses.  In the terminal we are going to type:```
cd ~/.desklets/goodnewsfeed(tab)
```  Next we are going type/paste into a terminal:```
gedit config.txt
``` scroll down to the part where you see this text:** 'url': 'http://mybiblescripture.com/rss/bible.php?fmt=daily&trans=KJV'}**  You are going to have to Search for your own Bible verse of the Day rss feed.  Probably if you just search you will find one.  Next look for the rss feed button on the web page you found, right click on that link and select **copy link location**  now we are going to plug that link into this line that we have found.  We are only going to replace between the ' apostrophes ' without overwriting them.  You can modify the other settings as you want, they have to do with size, font color etc.  Now we are going to Save and close the geditor.  

Now to get adesklets working in **GNOME** we are going to open the file manager (click on Places - Home)  and that will get us where we need to be.  Now click on **view - show hidden**  Now look for the folder called .desklets  double click it, then double click the folder goodnewsfeeder* look for the file named **newsfeed.py** double click in and select run.  Ok, it is now running,  what you can't see it? ??  ?? Where is it?  It isn't running - Where did it go?  Ok, you can't see it yet, but yes it is running.  

Again in the terminal we are going to type```
adesklets --nautilus
``` Ahhhh, now you can see it!!  It should pop up on the screen.  Be patient as it may take a second to get the verse.  

Ok, now you want this to pop up everytime you start your wonderfull Ubuntu CE, ok, here we go.  In you panel select System - Prefrences - Sessions.  Click on the Startup Programs tab.  Now click on add and paste this into the window that pops up. ```
adesklets -d 25 --nautilus
```  The 'd' will delay it from starting for 25 seconds, this is to ensure that it starts up, without the delay, it doesn't start.  You can modify the time if you like to another number other than 25 it is in seconds.  

That is it, you have a verse of the day on the screen!

Enjoy!

Shane

---

### Post by shane2peru on 2006-12-28
> **ubuntu27 said:**
> Good job Shane. :)

Thanks!
Shane

---

### Post by doobit on 2006-12-28
It really looks very nice on the desktop! I like that even better than the Bible verse toolbar in Firefox.

---

### Post by aggiemarine07 on 2007-03-27
Howdy!

Im still fairly new to linux and i followed your desklet how to get the goodnewsfeed working and it doesnt want to work for me. I was able to successfully load two other adesklets but not two others I downloaded (goodnews being one of them). I am running Xgl on my system. Would that make a difference? Is there any other info that I need to give you? Thanks!

GregW

---

### Post by shane2peru on 2007-03-27
> **aggiemarine07 said:**
> Howdy!

Im still fairly new to linux and i followed your desklet how to get the goodnewsfeed working and it doesnt want to work for me. I was able to successfully load two other adesklets but not two others I downloaded (goodnews being one of them). I am running Xgl on my system. Would that make a difference? Is there any other info that I need to give you? Thanks!

GregW

Greg,

Welcome to the communtiy and Linux!  I'm not sure about Xgl.  What other adesklets did you add?  I'm currently not on my Linux computer, and won't be for about a week. My computer with linux has been in for repairs for 1 month, and my new computer will not be put together till Friday, all I have access to is Windows computers.  If you give me a little more information about what you did to install it (what steps you ran through) and if you get any errors, and what adesklets you have installed that may help my pin point the problem.  I hope I can be of help without a Linux computer, we will have to test my memory :) .

Shane

---

### Post by shane2peru on 2007-04-01
> **aggiemarine07 said:**
> Howdy!

Im still fairly new to linux and i followed your desklet how to get the goodnewsfeed working and it doesnt want to work for me. I was able to successfully load two other adesklets but not two others I downloaded (goodnews being one of them). I am running Xgl on my system. Would that make a difference? Is there any other info that I need to give you? Thanks!

GregW

Greg,

Ok, I got my computer and had to re-setup my adesklets thing.  It was good for me to review the process again.  Here is what I need you to do.  If you followed my guide to install the goodnewsfeed, then I need you to open the terminal **Applications --> Accesories --> Terminal**  Now ```
cd *to the directory where you have goodnewsfeed* 
``` 
Then type ```
ls
```  this will show you the contents of that directory.  There should be a file called **newsfeed.py**  Next in the terminal type:```
python newsfeed.py
```when it asks if you want to register or test it just test it.  Copy and paste any errors you get from that.  If your screen flickers and the the terminal doesn't give you a return prompt then that part does work.  Just close everything and let me know and we will go from there.

Shane

---

### Post by glenn69 on 2007-04-06
Just to share.  I am running Mint Linux (ubuntu based) and this did not work immediately for me either.

My solution was to add the package python feedparser.  Apparently it was not included in the distro, but all works fine after that addition.

Hope it helps someone.  Thanks for a nice little desklet.

---

### Post by shane2peru on 2007-04-06
> **glenn69 said:**
> Just to share.  I am running Mint Linux (ubuntu based) and this did not work immediately for me either.

My solution was to add the package python feedparser.  Apparently it was not included in the distro, but all works fine after that addition.

Hope it helps someone.  Thanks for a nice little desklet.

Yeah, That is what I was shooting for.  It originally was included, but apparently they have updated it and the new one needs to be added to it. Glad you figured that out glenn!  Glad to hear you like it too!

[COLOR="Red"]**Ok, the link has been updated and you shouldn't have this problem any longer.  Everything should work great.**[/COLOR]

Shane

---

### Post by accludetuner on 2007-04-09
Thank you for this!  Works great in CE and in 64!

does anyone know how to edit the title using config.txt?  I know I could alter XML to change it but I was wondering if there's a way to do it without altering the RSS feed?

---

### Post by shane2peru on 2007-04-09
> **accludetuner said:**
> Thank you for this!  Works great in CE and in 64!

does anyone know how to edit the title using config.txt?  I know I could alter XML to change it but I was wondering if there's a way to do it without altering the RSS feed?

Thanks.  

I just checked both files and it appears that the title comes from the actual feed.  It was setup to be a newsfeed originally, and I hacked it to display the Bible verse.  So apparently the title is actually from the feed, and not in the config files or python script.

Shane

---

