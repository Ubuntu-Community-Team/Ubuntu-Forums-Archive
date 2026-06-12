---
title: "Flash 9 final and full release!"
date: 2007-01-17
forum: The Cafe
---

### Post by TheRingmaster on 2007-01-17
[Penguin.SWF: Flash Player 9 For Linux (x86)]("http://blogs.adobe.com/penguin.swf/2007/01/flash_player_9_for_linux_x86.html")

this is it guys. 

I am sure this is not the first thread, so please combine them if needed.

---

### Post by EdThaSlayer on 2007-01-17
Taken from SlashDot! 

"Schlaegel writes "The official Adobe Linux Flash blog has announced that Flash player for x86 Linux is now final and no longer beta. Every x86 Linux user, at least those willing to load binary software, can rejoice and no longer feel like a second rate citizen. Distribution packages are also available, for example the Macromedia Fedora repository already has the flash player marked for update.""

Hope I'm not being redundant here! (If I'm mods, delete this topic :) )

Here is the blog:
[http://blogs.adobe.com/penguin.swf/2007/01/flash_player_9_for_linux_x86.html]("http://blogs.adobe.com/penguin.swf/2007/01/flash_player_9_for_linux_x86.html")


Here is the link to the download :-D 
[URL="http://www.adobe.com/go/getflashplayer/"]http://www.adobe.com/go/getflashplayer/
[/URL]

EDIT:I just found out someone else made a topic like this 11 hours ago ](*,)

---

### Post by rowanparker on 2007-01-17
Will it hit the repos any time soon because I'm feeling lazy and can't be bothered installing it?

---

### Post by Johnsie on 2007-01-17
It's not hard to install... you just drop the .so file into your browsers plugins folder

---

### Post by Brunellus on 2007-01-17
> **Johnsie said:**
> It's not hard to install... you just drop the .so file into your browsers plugins folder
I should note here that I prophesied that the final release of Flash 9 for linux was a sign of the End Times.  

Now all we're wating for are Duke Nukem Forever and Kernel 3

---

### Post by prizrak on 2007-01-17
It's in Feisty already, well in the repos.

---

### Post by rowanparker on 2007-01-17
> **prizrak said:**
> It's in Feisty already, well in the repos.
Have I got any luck with it being in the Dapper repos?

And I might just install it, it sounds easy.

---

### Post by ThrobbingBrain66 on 2007-01-17
> **Johnsie said:**
> It's not hard to install... you just drop the .so file into your browsers plugins folder

The .so file also has to be placed in ```
/usr/lib/flashplugin-nonfree/
```
otherwise the version number in about: plugins doesn't change

---

### Post by EdThaSlayer on 2007-01-17
There should be this file included in there(flashplayer-installer) where all you have to do is click on it and press "run in terminal" and it will ask you all the essentials(aka-yes or no questions) and copy everything for you...

---

### Post by Brunellus on 2007-01-17
> **EdThaSlayer said:**
> There should be this file included in there(flashplayer-installer) where all you have to do is click on it and press "run in terminal" and it will ask you all the essentials(aka-yes or no questions) and copy everything for you...
you'd have to run that script with the necessary permissions if it's going to write in /usr

---

### Post by StarsAndBars14 on 2007-01-17
This is weird.

I downloaded the file from the Adobe site in .rpm format and then did:

sudo alien flash-plugin-blahblahblahyaddayadda.rpm

then I installed with dpkg and when I went back into Firefox it didn't show as installed.  I got the "click here to download plugin" box with the puzzle piece on a Flash animation.  So I clicked it and it brought me to Adobe Flash player, then it downloaded and installed normally. 

I'm guessing I don't need the flash-plugin package proper now.

---

### Post by daynah on 2007-01-17
I took the rpm, used alien to change it to deb, had deb magic done and poof! For everyone else's benefit (because I know I hate thinking also), this is exactly what I typed.

1. Download the rpm to your desktop.

2. sudo apt-get install alien

3. cd desktop

4. sudo alien flash-plugin-9.0.31.0-release.i386.rpm -d

5. sudo dpkg -i flash-plugin_9.0.31.0-1_i386.deb
        (yay! now you have flash 9 installed in /usr/lib/flash-plugin/)
6. sudo cp libflashplayer.so /usr/lib/flashplugin-nonfree -f
        (this makes your browser, or at least makes opera, use flash 9)
7. Now check that it's [Adobe Approved!]("http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_15507") And ignore the chart in the bottom. It's obviously wrong, because Linux has version 9 now! Yay!

---

### Post by Engnome on 2007-01-17
Still bugs with Opera, when I close a tab with flash in it all flash windows disappear. :mad:

---

### Post by daynah on 2007-01-17
Engome, my Opera doesn't do that (9.10). What URL does it do it on? Different sites or have you only tried just one Flash 9 site? (I can... only think of one, but I'd been very eager to use it!)

---

### Post by pipin on 2007-01-17
Flash player is not in main or rescrictive repos . Will we get 9 via Ubuntu upates? Or do we have to manually install it?

---

### Post by rowanparker on 2007-01-17
I already have 9, I didn't do anything to update.
It's just there.

---

### Post by prizrak on 2007-01-18
> **rowanparker said:**
> Have I got any luck with it being in the Dapper repos?

And I might just install it, it sounds easy.

No idea, it might get backported since it doesn't really impact the system I suggest checking the backports project (is it still alive?)

---

