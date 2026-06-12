---
title: "DreamWeaver in wine"
date: 2010-12-09
forum: Wine
---

### Post by cboxhero on 2010-12-09
I went to [http://frankscorner.org/index.php?p=dreamweaver8](http://frankscorner.org/index.php?p=dreamweaver8)
and it said "type wine dreamweaver-en.exe to install dreamweaver"

Where do I type this? Am I suppose to add more to it? How do I install dreamweaver on linux with wine?

---

### Post by Sugi on 2010-12-10
Hello cboxhero,
You actually only have to type 
> wine dreamweaver-en.exe
Accessories > Terminal
or
ALT+F2
or
Just makes you are in the directory of the exe.  On a side note, you can always right click on the exe and run it through wine.

But keep this in mind, everything depends on what version of dreamweaver you are going to install on what version of wine.  Here's a list of dreamweaver versions within wine, but some "test" are out dated and better versions of wine has come out since then.
[http://appdb.winehq.org/appview.php?appId=183]("http://appdb.winehq.org/appview.php?appId=183")

Sugi

---

### Post by Wtower on 2010-12-10
And of course you need to have wine installed:

```
sudo apt-get install wine
```

That or from the software centre.


Regards

---

### Post by cboxhero on 2010-12-11
I have wine, but ```
wine dreamweaver-en.exe
```
Won't work.
What do I have to do before that?

---

### Post by Sugi on 2010-12-11
Try installing wine.  You have opions to do so.  Installing from GUI.
Ubuntu Software Center > type 'wine' in the search bar
Now load up wine config
Next, launch the dreamweaver exe with wine.  Find the exe and right click on it, then launch with WINE

OR

You can use the terminal to install wine and install dreamweaver.
Applications > Accessories > Terminal
> sudo apt-get install wine

Next go over to winecfg
Terminal > type this
> winecfg

Now change directories to the location of the dreamweaver exe
cd ~/location/of/dreamweaver/exe
Terminal > type this
> wine dreamweaver-en.exe

Good luck,
Sugi

---

### Post by Wtower on 2010-12-13
Or you can use an alternative to dreamweaver, personally I find especially this particular piece of software to be mainly a matter of habit rather than providing unique features: [www.osalt.com]("http://ubuntuforums.org/www.osalt.com")

---

### Post by at100plus on 2010-12-13
What's the closest thing to Dreamweaver?  I recently made the switch to Ubuntu exclusively, I've adapted to everything I need except Dreamweaver, which I'll be more than happy do stop using Adobe garbage altogether once I find something that won't give me much of a learning curve.

---

### Post by Wtower on 2010-12-13
Sorry, my previous link is obviously wrong. Try: [http://www.osalt.com/dreamweaver](http://www.osalt.com/dreamweaver) . I don't know why eclipse ([http://www.eclipse.org/](http://www.eclipse.org/)) doesn't qualify on that page for a proper alternative, but inspite the fact that sometimes is a bit cumbersome, I rather prefer it for this kind of stuff.

---

### Post by at100plus on 2010-12-13
Thanks, I was wondering what's up with that link.  I'll check that out tomorrow.

---

### Post by Wtower on 2010-12-14
Great mate, please let us know your opinion after that.

---

### Post by at100plus on 2010-12-14
I installed Quanta from the download manager.  First thing it gave me errors saying it couldn't find Cervisa, Imagemap Editor and KXSLDbg.

I installed those, error still comes up for the first two.  

Either way I don't quite get it.  Poking around quickly I don't even see settings to connect to my webserver via FTP to download my site.  

Is the Quanta portion of this package supposed to resemble Dreamweaver CS3?

---

### Post by Wtower on 2010-12-14
I've never used Quanta, and I don't know if there are other packages with this kind of feature. What I have done regarding this matter is to use a small script based on scp or ftp commands to deploy or pull back web projects, which I had created myself. That was before I discovered bazaar, with which now I have used to keep a shared repository on the web server, to which I push/pull versions of the site.

Regards

---

### Post by at100plus on 2010-12-14
Scripts...Bazaar....you're losing me.

I just need a program like Dreamweaver without too much of a learning curve that I can FTP to my webserver and get the existing site and pick up editing where I left off.

I'm running Ubuntu now exclusively, done with Windows.  It's starting to look like I should install Dreamweaver on my Windows Virtual though.  I don't want to mess up this site, I maintain it for my buddy's business out of the kindness of my heart basically.

---

### Post by Wtower on 2010-12-14
In this case you're right. I'm afraid I can't suggest anything like that. It wouldn't harm trying eclipse though, it has got lots of plugins and possibly one for deploying a web project through ftp.

---

### Post by drdos2006 on 2010-12-14
I have just installed quanta on Ubuntu 10.4. Runs like a dream.
Try re-installing. 
Finally a program to compete with Dreamweaver, had no trouble connecting to my server, I can link, change, update on the server. 

However, there are differences between Dreamweaver coded pages and Quanta code. All the info is in the Dreamweaver html coded pages, but occasionally tags have to be added or removed in Quanta to see all the information.

 I certainly will NOT be going back to Dreamweaver.

regards

---

### Post by Yudin on 2010-12-17
There is problem with wine and dreamweaver 8: code view cutted by black lines, anyone solved this?

---

### Post by alaukikyo on 2010-12-17
> **at100plus said:**
> Scripts...Bazaar....you're losing me.


Try nvu

if not satisfied try some of the apps from [here]("http://alternativeto.net/software/adobe-dreamweaver/?profile=online?sort=likes&platform=linux&license=free")

---

### Post by at100plus on 2010-12-20
Nothing seems to really match up to what I'm used to and I'm only doing the site for a bit longer till they hire someone to do it using CMS and a database, so I got it going on a WinXP Virtual Machine and it seems to work fine that way.

---

