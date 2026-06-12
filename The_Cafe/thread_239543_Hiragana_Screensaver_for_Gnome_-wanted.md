---
title: "Hiragana Screensaver for Gnome -wanted"
date: 2006-08-19
forum: The Cafe
---

### Post by welders4linux on 2006-08-19
Has anybody found a Hiragana Screensaver for Gnome,
Ive located a few for KDE, but I use Gnome. :-k 
thanks for your time
w4l

---

### Post by tiris on 2006-08-24
Really, what screensavers did you find for kde that are hirigana related?

---

### Post by tiris on 2006-08-24
Oh, I did find something related...kanjisaver...it is not a hiragana screensaver but it is related to Learning Japanese.

I still haven't figured out how to integrate it into the system and use it as a default screensaver but you can bring it up from the command line.

If you know or find out how to integrate the kanjisaver into the system let me know -- I have one dapper machine and one breezy machine.

---

### Post by RichLouth on 2006-09-16
Hello,

Wanted this myself. The solution:

I'm assuming you've got xscreensaver running rather than the gnome screensaver. See this post:
[http://www.ubuntuforums.org/showthread.php?t=195557&highlight=xscreensaver+default]("http://www.ubuntuforums.org/showthread.php?t=195557&highlight=xscreensaver+default")
Once that's done the rest of this should work fine:)

Make sure you have the language pack installed.
> sudo apt-get install language-pack-gnome-ja

Install the screensaver packages.
> sudo apt-get install kanjisaver
sudo apt-get install kannasaver

Go to your home directory.
> cd

Open the xscreensaver config file.
> gedit .xscreensaver

Add the following two lines under the "programs:" section.

> -				kanjisaver.kss --root			    \n\
-				kannasaver.kss --root			    \n\

When you open up xscreensaver they should now appear in the list. Although the preview window in xscreensaver doesn't work it will work when you press the preview button.

You won't be able to edit the settings using xscreensaver. You'll have to do it through the command line:

> kanjisaver.kss --setup
kannasaver.kss --setup

And a window will open where you can adjust the settings.

Enjoy:)

---

