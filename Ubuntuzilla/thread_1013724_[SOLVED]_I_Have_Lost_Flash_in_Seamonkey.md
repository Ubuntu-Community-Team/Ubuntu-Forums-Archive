---
title: "[SOLVED] I Have Lost Flash in Seamonkey"
date: 2008-12-17
forum: Ubuntuzilla
---

### Post by PierreDeKat on 2008-12-17
As stated in a previous thread, I had Seamonkey 1.1.12 installed via Intrepid's repositories, and I upgraded to 1.1.14 via Ubuntuzilla.

During the upgrade, I was posed the question:

```
If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
```

I answered "n" because I couldn't see why I would want to link my Seamonkey plugins to my Firefox install. Makes no sense to me. Having started out with Netscape, I hate the whole Firefox deal, anyway, but don't get me started on that mess.

Anyway, after the upgrade, I lost Flash. I've tried uninstalling and reinstalling both flashplugin-nonfree and adobe-flashplugin (from repositories and downloading the .deb), but no Flash in Seamonkey.

Okay, fine.

I do:

```
ubuntuzilla.py -a remove -p seamonkey
```

...go through the process. Then do:

```
ubuntuzilla.py -a install -p seamonkey
```

...go through the process, only this time when it asks if I want to link to the Firefox plugins, I choose "y".

That's when Terminal spits out:

```
If you have the repositories version of Firefox installed, you can choose to link all the Firefox plugins to your Seamonkey install. Would you like to do that? [y/n]? 
Please enter 'y' or 'n': y
sudo dpkg -L firefox-3.0 |grep 'firefox/plugins$'
Failed to determine plugin path. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1110, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 215, in start
    si.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 546, in install
    self.linkPlugins()
  File "/usr/local/bin/ubuntuzilla.py", line 925, in linkPlugins
    self.pluginPath = self.util.getSystemOutput(executionstring="sudo dpkg -L " + self.ffPackage + " |grep 'firefox/plugins$'", errormessage="Failed to determine plugin path. Exiting.")
  File "/usr/local/bin/ubuntuzilla.py", line 118, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, http://ubuntuzilla.sourceforge.net/
pierredekat@ubuntu:~$ 
```

The upgrade fails, and I've got no Seamonkey at all.

Do the install again, only this time I choose "n" on the plugins, just to get back to a usable Seamonkey 1.1.14.

So three things, I guess: 1) Maybe there needs to be some clarification as to why we would want to link Seamonkey plugins to a Firefox installation; 2) Why does it fail when I actually do try to do the link; and most importantly 3) How do I get Flash working in my Seamonkey 1.1.14 build?

TIA

---

### Post by PierreDeKat on 2008-12-17
Okay, got Flash working in Seamonkey 1.1.14.

I tried six or eight different ways to install and uninstall and reinstall flashplugin-nonfree, adobe-flashplugin, and Seamonkey 1.1.12 and 1.1.14. But no joy.

Then I discovered the [directions here]("http://plugindoc.mozdev.org/linux.html#Flash").

The first time I went to the [Adobe website]("http://get.adobe.com/flashplayer/") and downloaded and installed the .deb file for Ubuntu. Still no joy.

Then I went back and re-read the directions about getting libflashplayer.so into my /plugins folder. And that lead me to download the .tar.gz file from Adobe, which produces a usable libflashplayer.so file wherever it's extracted.

Then I used "gksudo nautilus" to copy libflashplayer.so to my /opt/seamonkey/plugins folder, and bingo, I have Flash again!

Just wanted to do a little documentation in case there's others in the same boat.

Next up: flashblock! ;)

---

### Post by PierreDeKat on 2008-12-17
FWIW, I'm starting to wonder if the old Flashblock plugin that I had installed in 1.1.12 might have been what was confusing my Flash plugin when I upgraded to 1.1.14.

I got Flash working with the method I documented above, and a lot of Flash animations were working for me, but there were still quite a few, particularly the more "complex" ones, for lack of a better description, that still weren't playing.

Then I installed Flashblock 1.3.10 in .xpi format from [here]("http://flashblock.mozdev.org/installation2.html"), and it pitched up some kind of error message related to "chrome". But oddly enough, after launching Seamonkey two times -- some kinda old bug -- everything works like it's supposed to.

All Flash animations, including the "complex" ones, are working flawlessly, and surprise, surprise, Flashblock is working, as well.

Again, just wanted to document what I've been doing, for whomever might be having similar problems.

Cheers.

---

### Post by nanotube on 2008-12-23
Hi
thanks for your posts!

it looks like there's a bug in the ubuntuzilla script in seamonkey's plugin detection.

i'll post a bugfix release in a bit and hopefully you can test it for me :)

---

### Post by nanotube on 2008-12-23
Hi
please test the attached ubuntuzilla to make sure it links seamonkey to firefox plugins correctly...

---

### Post by PierreDeKat on 2008-12-24
Wow, you rock, nanotube!

Okay, did the following:
1) Uninstalled Seamonkey 1.1.14 via old version of Ubuntuzilla
2) Verified that /opt/seamonkey (and old /opt/seamonkey/plugins folder) were gone
2) Uninstalled old version of Ubuntuzilla via Synaptic -- not sure if that was the best way, but it worked for me.
3) Installed new version of Ubuntuzilla (ubuntuzilla-4.5.9-0ubuntu1-i386.deb) by downloading, double-clicking on it, and installing.
4) Used Ubuntuzilla 4.5.9 to reinstall Seamonkey 1.1.14

This time, there were no errors, and the installation went through without a hitch.

And both Flash and Flashblock work perfectly. \\:D/

The only thing, and this is really minor, not something to rush to fix, but maybe something to make a note of for a future release.

During the installation, I got the message

```
Old Seamonkey preferences not found. Nothing to back up. Proceeding with installation.
```

Of course, it did apparently find my preferences, because everything looks and functions just like I had it set up before. But maybe the above message might cause unnecessary concerns.

Like I said, this is minor, since everything worked perfectly. Just something to consider for a future version of Ubuntuzilla. 

I'm happy to be an Ubuntuzilla tester, now and in the future. And as a tester, I will try to give my best assessment and make a note of my observations, just for what they're worth.

But thanks so much. Now, I've got two other computers to do this to.

---

### Post by nanotube on 2008-12-26
Hi,

glad it worked :)

about the preferences backup: when ubuntuzilla does the backup, it looks for seamonkey prefs in ~/.mozilla/default, if that's not found, it won't back up the preferences. could you look and see if that directory exists on your system?  if not, then tell me where your seamonkey stores the prefs? 

thanks :)

---

### Post by PierreDeKat on 2008-12-28
> **nanotube said:**
> Hi,

glad it worked :)

about the preferences backup: when ubuntuzilla does the backup, it looks for seamonkey prefs in ~/.mozilla/default, if that's not found, it won't back up the preferences. could you look and see if that directory exists on your system?  if not, then tell me where your seamonkey stores the prefs? 

thanks :)
Aaaahhh ... that would explain it. Yeah, I created special profiles for doing different things, and of course, neither is the original "default".

But it's no biggie, really. Ubuntuzilla seams to leave the old profiles intact and Seamonkey finds them with no problem, and that's all that really matters.

---

### Post by nanotube on 2008-12-29
Hi,
Aha, ok, makes sense. :)
Thanks again for your help and feedback. :)

---

### Post by nanotube on 2009-01-01
Hi,
Since you were so kind to volunteer :), please test the latest ubuntuzilla version. See the latest in the testing thread, here:
[http://ubuntuforums.org/showthread.php?p=6474686#post6474686](http://ubuntuforums.org/showthread.php?p=6474686#post6474686)

Thanks! :)

---

### Post by DonnaVieney on 2010-06-21
I just read this post. I hope I could get more updates about Seamonkey, I am in fact new with this app and I am trying to find more tutorials online.

---

### Post by matias13 on 2010-12-30
> **PierreDeKat said:**
> Okay, got Flash working in Seamonkey 1.1.14.

I tried six or eight different ways to install and uninstall and reinstall flashplugin-nonfree, adobe-flashplugin, and Seamonkey 1.1.12 and 1.1.14. But no joy.

Then I discovered the [directions here]("http://plugindoc.mozdev.org/linux.html#Flash").

The first time I went to the [Adobe website]("http://get.adobe.com/flashplayer/") and downloaded and installed the .deb file for Ubuntu. Still no joy.

Then I went back and re-read the directions about getting libflashplayer.so into my /plugins folder. And that lead me to download the .tar.gz file from Adobe, which produces a usable libflashplayer.so file wherever it's extracted.

Then I used "gksudo nautilus" to copy libflashplayer.so to my /opt/seamonkey/plugins folder, and bingo, I have Flash again!

Just wanted to do a little documentation in case there's others in the same boat.

Next up: flashblock! ;)
thx 4 the hlp, it worked perfectly.

---

