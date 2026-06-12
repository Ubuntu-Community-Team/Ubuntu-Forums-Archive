---
title: "NETFLIX, won't work without tru type fonts, can't install true type fonts"
date: 2014-03-11
forum: Ubuntu Studio
---

### Post by Ralph_Lam on 2014-03-11
I had used Ubuntu or awhile with no problem.  I was able to successfully install the Netflix desktop with the following comands in the terminal

```
sudo apt-add-repository ppa:ehoover/compholio
``` 
```
sudo apt-get update
```
```
sudo apt-get install netflix-desktop
```

However; I am now running Ubuntu studio, and thought it would be a simple matter to run those three commands and be off and runing with Netflix, but something else is happening this time.

I an find the red netflix icon in my applications list and when I click on it I get a window that pops p and says

> MS true type fonts are not properly installed, would you like to download and install them now? (requires an internet conection and sudo permissions)

answering yes brings up a license agreemtn for fonts from Web EULA

clicking the accpet box ad forward, a new window pops up saying

> It appears that you still have not installed the MS true type fonts.  You need to accept the license agreemtn and install these for Netflix Desktop to work properly

then the only choise "forward" closes the window....

Is there a way to install the true type fonts manually in the terminal?

---

### Post by bcschmerker on 2014-03-11
You'll need the Package **ttf-mscorefonts-installer**, in Miscellaneous - Graphical (multiverse), installable from APT-Get (Terminal) or Synaptic Package Manager.
```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by Ralph_Lam on 2014-03-12
Well, my first question was "what changed?" less the obvious answer is that "Ubuntu Studo" is not a similar to regular "Ubuntu" as I might suspect.

After running ```
sudo apt-get install ttf-mscorefonts-installer
```

I get

```
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

Still get the same feedback from the system; 
"you need the fonts, do you want the fonts" 

yes

" oops you didn't say you wanted the fonts, goodbye", 

etc

---

### Post by Pedro_Felipe on 2014-09-26
Perhaps the problem is the license? Try this:

apt-get install --reinstall ttf-mscorefonts-installer

And click 'ok' in the prompt. This worked for me.

---

### Post by Vladlenin5000 on 2014-09-28
When the EULA dialog appears you need to hit TAB then use the arrow keys and ENTER to select and confirm the options.

---

