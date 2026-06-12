---
title: "Python script (GUI) to easily set mouse acceleration"
date: 2014-07-15
forum: Ubuntu Application Development
---

### Post by michael171 on 2014-07-15
I wrote this simple python 3 script complete with GUI for users who have high dpi / gaming mice and find the current settings too fast but dont want to muck around at a terminal.  What it does is present you with two sliders and some spinbox controls to alow you to tweak settings that directly affect the speed and acceleration of your mouse.  The idea is not new and has been done before, at Patrick Nielsen's blog: [http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/) 
My python script runs under python 3 not python 2.x so you will need that installed to get it working.  When you run python3 main.py it will open the GUI where you can adjust the sliders and press Run to test the current settings.  After you are happy with it, simply close the program and it will save a script in the current directory called script.sh which you can chmod +x script.sh and add it to your startup programs via your preferred method.

To get this program, you can go to [bitbucket.org/backwardsbyte/mousespeed/downloads]("http://bitbucket.org/backwardsbyte/mousespeed/downloads") and click Download repository, or if you want to use the terminal you can with:

```
sudo apt-get install git
git clone https://bitbucket.org/backwardsbyte/mousespeed.git
```

I provide this script under the unlicence agreement, included in the download.  You are free to do what you want with this, I don't provide a warranty.

---

