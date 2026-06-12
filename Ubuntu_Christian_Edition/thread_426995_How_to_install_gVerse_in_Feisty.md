---
title: "How to install gVerse in Feisty"
date: 2007-04-29
forum: Ubuntu Christian Edition
---

### Post by tak1150 on 2007-04-29
Well it is not very difficult at all, but I thought maybe 1 other person would benefit from this.

Those of us who are using Feisty (as of 04/28/07) do not have the CE version yet. So if you want to add gVerse to your Feisty, here it is:) 

*This is the how-to for clean-install Feisty

```
sudo apt-get install g++
```

Then in Synaptics, find "libgtk2.0-dev" and install it (along w/ a bunch of dependencies).

Then you can download gVerse source code from [here]("http://sourceforge.net/project/showfiles.php?group_id=179043").

cd to the directory and run

```
make
sudo make install
```

I'd add it to the "start-up" app list by "System" -> "Preference" -> "Sessions" -> "Startup Programs" and click "New"
That way, you see the daily Scripture every time you log in!

But we should not rely only on this program for getting fed from the Word :-)

---

