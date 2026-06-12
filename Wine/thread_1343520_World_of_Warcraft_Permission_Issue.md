---
title: "World of Warcraft Permission Issue"
date: 2009-12-01
forum: Wine
---

### Post by fatum on 2009-12-01
Im trying to install WoW on my 9.10 64 bit desktop. I am using the downloader for the game client since that is always how I have installed it. I have downloaded and installed most of the patches for the game. Now I am to a point where the installer itself just upgraded and now I can no longer go any farther than the installer screen. 
I have done some checking and what it happening is the folder where everything is getting installed 

~/username/.wine/Program\ Files/World\ of\ Warcraft/ 

changes permissions every time I run the installer/updater to me not having access. I can change the permissions in the Terminal to make it so I have access and then run the installer/updater and the permissions change back and the program exits out. 

There is nothing in the log files to indicate anything that I can see wrong. Any help would be greatly appreciated. Thank you in advance.

---

### Post by PariahVayne on 2009-12-01
x

---

### Post by fatum on 2009-12-02
I have tried, for some reason it says that ~/.wine/ is not owned by me. But I can see from ls -al that I am the owner and that I have read/write access.

---

### Post by mnrapier on 2009-12-02
Same problem here. Just installed Ubuntu 9.10 and the latest Wine. After pressing 'play', the WoW loader screen just disappears and then the permissions are changed again. Unfortunately my craptastic Windows had it's final 'checkdsk not found' error yesterday so now I am forced to problem solve my way to Ubuntu ecstasy. However, this could be a good thing.

---

### Post by joeelmex on 2009-12-02
The updater for some reason is changing the permissions of the wow directory.  Just go to a terminal and type chmod 777 the path to the Wow game.  Once thats complete dont load the launcher, load wine wow.exe and it should work fine.  Thats how i been playing since 3 weeks ago when the updates started messing with the permissions.

---

### Post by mnrapier on 2009-12-02
Just got it working... for now anyways. I renamed the original 'World of Warcraft' folder to (random) 'blinky'  and then created a new folder named 'World of Warcraft' then copied all the files from 'blinky' to the new 'World of Warcraft'. I also renamed 'Wow.exe' to 'WOW.exe' per some other discussions of WoW loading problems. I am now downloading a kagillion bagillion bytes of patches.

---

### Post by mnrapier on 2009-12-02
Ah... the 'Failed to apply patch" problem now...

---

### Post by fatum on 2009-12-02
I deleted all the WoW folders and I am now trying to download the patches using the Wrath down-loader/uploader. The link I used to download the other installer gave me a Burning installer and I did not notice it right away. I am hoping that this changes it some.

Edit: 
Noticed that Package manager installed a new Beta for Wine. Uninstalled the Beta installed the working version of Wine and I am not having any more permissions issues so far. I am currently running the Blizzard Repair Utility and then I will see what happens.

---

### Post by mnrapier on 2009-12-02
K, copied all the files in the "World of Warcraft" folder from my other computer and pasted them into a folder in my Ubuntu PC. Played for a while, did the amphitheater of anguish then headed to Dalaran. Upon entering Dalaran WoW shut off and I haven't been able to start it yet.

So just using the copied files and Wine has gotten me much farther.

---

### Post by Alatar1 on 2009-12-02
Originally from [http://ubuntuforums.org/showthread.php?t=1330927](http://ubuntuforums.org/showthread.php?t=1330927)

>  Problem"Permission Denied" error when attempting to run the game. OR When the WoW Launcher comes up, the "play" button is greyed out and cant be used. (both are stemming from the same problem)

Solution The easiest and least technical way to fix this would be to first browse on over to /home/<yourusername>/.wine/drive_c/Program Files/World of Warcraft ,
There will more than likely be an X on the world of warcraft folder, simply right click on it,go to properties, click the "permissions" tab, right under where it says owner: username-group, change the drop down box to "create and delete files".
Now that that is set, In the World of Warcraft directory, Run the game via the "WoW.exe" file , NOT LAUNCHER.EXE (the launcher is whats causing it, it will lock you out everytime!!) once your on the title/login screen, UN-check the little box on the bottom left that says "show launcher".
***DO NOT USE THE LAUNCHER! it WILL lock you out again!!!*** this should fix this issue.

IF while working on the issue above, you cannot change file permissions due to it telling you the owner is "root"...
you will need to change the permissions as root,
the way i know how to do this is go to terminal and enter
Code:

sudo nautilus

or whatever file browser you use (nautilus is the default for ubuntu) this will allow you browse files as root,
BE VERY CAREFUL HOWEVER, Tinkering with files as root can have very bad consequences and compromise your machine possibly, that being said...
simply browse to the directy as stated above and change the permissions that way...there are also console commands to do it manually, but for the sake of the not so savvy, I've omitted those.

You should really try searching more, next time give it a try and refrain from just up and posting about something thats been covered..google is your friend.

---

### Post by hikaricore on 2009-12-03
I've tested this on my ex's comp and can confirm that not using the launcher resolves it.

---

### Post by fatum on 2009-12-03
> **Alatar1 said:**
> Originally from [http://ubuntuforums.org/showthread.php?t=1330927](http://ubuntuforums.org/showthread.php?t=1330927)



You should really try searching more, next time give it a try and refrain from just up and posting about something thats been covered..google is your friend.

And I would refrain from assuming that I did not search. Search engines will only get things for you based on the terminology that you use to search with. I probably (can almost guarantee) searched for different words than you did. Instead of being an *** about it why not just put that up to help someone out?

---

### Post by fatum on 2009-12-03
The information that Alatar1 posted helped once I was able to get to the login screen to un-check the box. Once the permission issue got straightened out another issue popped up. The game would begin to load I could hear the music but then I would get an error for memory allocation. Found a couple very useful websites

[WoWwiki]("http://www.wowwiki.com/Console_variables")
[BloghiHub]("http://www.blog.highub.com/linux/world-of-warcraft-configuration-configwtf-on-ubuntu/")
[Codeweavers]("http://www.codeweavers.com/compatibility/browse/name/?app_id=1185;tips=1")

Between the three of those websites with most coming from the Codeweavers website I created my own config.wtf file in the WTF folder of World of Warcraft. Once that was created I was able to get to the login screen for the game client. Since that point I have been running updates since many new patches have come out. So far no more issues. Just hope that the patches install correctly. Thank you all for your help I really appreciate it. I am marking as solved since the first issue of permissions has been fixed.

---

### Post by DedMoroz on 2009-12-07
> **mnrapier said:**
> Just got it working... for now anyways. I renamed the original 'World of Warcraft' folder to (random) 'blinky'  and then created a new folder named 'World of Warcraft' then copied all the files from 'blinky' to the new 'World of Warcraft'. I also renamed 'Wow.exe' to 'WOW.exe' per some other discussions of WoW loading problems. I am now downloading a kagillion bagillion bytes of patches.

This didnt work at all for me.

---

### Post by Heavy_Metal_Jedi on 2010-03-03
Easiest way to fix this:

goto terminal and type in:

sudo chown -R username:username /home/username/.wine/drive_c/Program \Files/World \Of \Warcraft

Then navigate to the "World of Warcraft" folder, right click, goto permissions tab and select the top drop down box in "Owner" and select "Create and Delete Files" then click below on "Apply Permissions to Enclosed Files" click close and start game as normal.

The first one changes the folder ownership from root to your user account, the second one give you read and write access. :popcorn:

---

### Post by Sparkfist on 2010-03-09
Hello all,

I've been having permission issues with WoW and wine too. I thought I had nailed most of it down.

I have changed ownership of everything under ~/.wine to myself. Changed permissions of the World of Warcraft folder, chmod 775. I can run repair and the launcher, but not start the game.

Just a few minutes I tried what everyone was saying worked, and that is just run the WoW.exe. Every time I do this my screen goes black, saying "No Analoge Signal". And I'm forced to restart my computer. This has happened every time. And when I checked the WoW folder after logging in this time it defaulted back to no permissions with the padlock on the folder.

Any ideas?

-Nick

P.S. I'm running 9.10 64-bit, Wine 1.1.31, and WoW was installed under wine using the download client.

---

