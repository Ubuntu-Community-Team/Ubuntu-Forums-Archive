---
title: "Can Dapper Do This?"
date: 2006-04-21
forum: The Cafe
---

### Post by Kernel Sanders on 2006-04-21
As a noob, who's played around with Ubuntu and Kubuntu, i'm finding the KDE desktop environment more user friendly at the moment.

The only thing that I couldnt get the hang of was installing.

I downloaded firefox 1.5.0.2 from the firefox website, and compleatly ballsed it up.

I unzipped it to the home directory, so I had a bunch of random files in a Firefox folder in my home directory, and then I was at a loss. People in the "absolute beginners" section tried to help, but I had still had no idea how/where to do what they were telling me.

So I was wondering (I saw a dapper screenshot that seemed like some kind of GUI install interface?) does dapper have some kind of automated install system for the idiotic noobs like myself? Something where I could just dump a .tar.gz (or whatever it was) file into it and click install? 

John :)

---

### Post by dabear on 2006-04-21
Why do you download from the fx website? Ubuntu come with Firefox preinstalled.

.tar.gz/.tgz files are most frequently used for **source code**, so you would have to go to a terminal and type ./configure , make and make install/checkinstall. However when I tried downloading the files directly from mozilla, they were supplied as a binary. After you've unwraped the compressed archive, it should only be a matter of pressing the file called «firefox» and choosing «run» (or something like that, running kde, not gnome atm).

Next time, if you don't find the package you want in synaptic, try to find a .deb package (resembles .exe-windows files), which can be installed(including dependencies) through the gdebi program

---

### Post by prizrak on 2006-04-21
Ubuntu comes with a very outdate version of FF. To install FF 1.5.02 you just decompress (unzip) the files into some folder (call it Firefox for instance). To run it you just double click on  the file named "firefox" if it prompts you whether you want to run it or view it hit run. 
Also you might wanna search the forums for "firefox install script" some people made easy to use scripts to install it for you as well as copy all your bookmarks and such.

---

### Post by dabear on 2006-04-21
[QUOTE=prizrak]Ubuntu comes with a very outdate version of FF. To install FF 1.5.02 you just decompress (unzip) the files into some folder (call it Firefox for instance). To run it you just double click on  the file named "firefox" if it prompts you whether you want to run it or view it hit run. 
Also you might wanna search the forums for "firefox install script" some people made easy to use scripts to install it for you as well as copy all your bookmarks and such.[/QUOTE]
The title of the thread said «can **Dapper** do this», so I assumed that the thread starter was running Dapper Drake. While breezy comes with an old version of firefox, Dapper don't

---

### Post by taurus on 2006-04-21
He already asked this same question in another area (Beginner) like 6 hours ago!!!  I guess he didn't like the answers there...  ](*,) 

[http://www.ubuntuforums.org/showthread.php?t=163783](http://www.ubuntuforums.org/showthread.php?t=163783)

---

### Post by Kernel Sanders on 2006-04-22
[QUOTE=taurus]He already asked this same question in another area (Beginner) like 6 hours ago!!!  I guess he didn't like the answers there...  ](*,) 

[http://www.ubuntuforums.org/showthread.php?t=163783](http://www.ubuntuforums.org/showthread.php?t=163783)[/QUOTE]

Not quite, I asked the question there, and was unable to understand how to put the answer into practice. :(

But that is not what this thread is about.

My question was about dapper and whether it had implimented some kind of GUI install? Because I saw a screenshot of something like that IIRC?

If they have it would be great for idiotic Kununtu noobs like me :oops:

Can anyone confirm whether this is true?

Thanks!

John :)

---

### Post by Hanj on 2006-04-22
If you are talking about a GUI installer for deb-packages (installer packages specific for ubuntu), then there's Synaptic which has been included in all releases of ubuntu (and will be included in dapper too of course). If you want a graphical installer for source packages, you can try [kompile]("http://www.kde-look.org/content/show.php?content=30223") for KDE.

---

### Post by curuxz on 2006-04-22
If he is talking about dap having a diffrent package system this could be SMART, i think Mark mentioned something about moving away from synaptic in DAP or DAP+1

---

### Post by WakkiTabakki on 2006-04-22
I think he's fishing for something like Automatix:
[http://ubuntuforums.org/showthread.php?t=138405]("http://ubuntuforums.org/showthread.php?t=138405")
[http://www.ubuntuforums.org/showthread.php?t=114251]("http://www.ubuntuforums.org/showthread.php?t=114251")
[http://www.tectonic.co.za/view.php?id=868]("http://www.tectonic.co.za/view.php?id=868")
But, I don't think it's ready for Dapper just yet, though...

/N

---

### Post by Kernel Sanders on 2006-04-22
[QUOTE=Hanj]If you are talking about a GUI installer for deb-packages (installer packages specific for ubuntu), then there's Synaptic which has been included in all releases of ubuntu (and will be included in dapper too of course). If you want a graphical installer for source packages, you can try [kompile]("http://www.kde-look.org/content/show.php?content=30223") for KDE.[/QUOTE]

Thats exactly what i'm looking for! :D

Tbh, I have been spoilt by Windows XP Pro SP2. I have only been used to installing by double clicking an exe, or by the menu autorunning when I insert a CD/DVD. Also, I am only used to to having a GUI to do anything.

So when I tried the Kubuntu Live CD I was like a rat trapped in a maze. I literally had no idea where anything was, or how to do anything?

So a program like Kompile would be great for totally lost noobs like me :oops:

---

### Post by imagine on 2006-04-22
Ubuntu, as every Debian based distribution, uses the DEB package-format.
There exist a bunch of servers for Ubuntu called repositories with all kind of software on them, and you use apt-get (or a graphical frontend like Synaptic/Adept) to download and install those software fully automatic.

So if you want to have Firefox you run *sudo apt-get install firefox* and that's it. To start Firefox either type *firefox* in a shell or select it from the KDE menu. That's ten times easier than everything Windows has to offer. Or if you don't like the command-line you can aswell start Adept, search for Firefox and install it from there.
However what you do not want to do is going to the website of Firefox or some other program and download it from there. That's only necessary when the program you want is not available from the Ubuntu repositories.



In your case you downloaded an archive with all the Firefox files in it. You can unpack it into a folder (ark is an archiving tool like errr... winzip) and then run the file called firefox from there. But I don't know of any reason why anyone would want to do that since Firefox is already available in the repositories.



To answer the question in the thread title: What Dapper can do and what Breezy couldn't is installing a DEB package with the help of a graphical user interface. Imagine you downloaded such a DEB package from somewhere or someone sent you one. In Breezy you would have to open a shell and run *dpkg --install /path/to/your/example.deb*. In Dapper you can simply doubleclick the package.
But there's no automatic way to install a bzip/gz/zip archive, since there's nothing to install. It's just some files packed together.

---

