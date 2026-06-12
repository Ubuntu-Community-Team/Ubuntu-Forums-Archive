---
title: "ubuntuzilla 4.0.0: &quot;experimental&quot; version"
date: 2007-05-21
forum: Ubuntuzilla
---

### Post by nanotube on 2007-05-21
** EDIT: this version is now live on the project site.

hey everyone
so, i've been doing some thinking and some coding, and i have a new version of the scripts, all under one roof.
it is written in python, and can install firefox, thunderbird, and seamonkey (given appropriate command line options).
i call it "experimental" because it hasn't received as much testing as the shell scripts have, but i have tested it rather extensively myself, AND have used it to install ff, tb, and sm on my newly-installed feisty system, with nary a hitch.

so, i encourage you all to do some testing, and report any problems that may occur.

new features since the previous versions are as follows:
*) Ported to python 
*) Meld all scripts together into one (better ease of maintenance)
*) Allow multiple attempts at choosing a localization
*) Add shorter timeout for getting latest version, add message for latest version retrieval
*) Add command line option to bypass GPG key verification
*) Add command line option to set mozilla mirror
*) Add command line option to customize pgp keyserver list
*) Add command line option to set target directory for installation
*) Allow bypass if "apt-get update" fails, since that is possible due to third-party repositories being down, or missing GPG keys	

to use it to install thunderbird, e.g., the commandline to use it is
```
python ubuntuzilla.py -p thunderbird -a install
```

for more extensive help on the available commandline options, run it with '-h'. 

but please, be aware that it /may/ have problems, so here's the big old [SIZE="5"][COLOR="Red"]WARNING[/COLOR][/SIZE] about it being experimental. :)

it is attached in tar.gz format, because these forums for some reason have a really low filesize limit on .py scripts....

---

### Post by aysiu on 2007-06-01
Well, so far I've tried installing Firefox, and it worked (the download process seemed to take a really long time, though--about five minutes on a broadband connection). I'll work on uninstalling it as well and then looking at Thunderbird and Seamonkey, too.

---

### Post by aysiu on 2007-06-01
Came across the first glitch.

Installing Thunderbird worked, but it didn't symlink or copy ~/.mozilla-thunderbird to ~/.thunderbird, so when I launched the new Thunderbird, it gave me the first-start wizard (i.e., didn't already have all my email accounts set up).

By the way, I found a way around the slow download. If I put the downloaded .tar.gz in the /tmp folder manually before running the script, the script recognizes that the file is already there.

---

### Post by nanotube on 2007-06-01
> **aysiu said:**
> Came across the first glitch.

Installing Thunderbird worked, but it didn't symlink or copy ~/.mozilla-thunderbird to ~/.thunderbird, so when I launched the new Thunderbird, it gave me the first-start wizard (i.e., didn't already have all my email accounts set up).

By the way, I found a way around the slow download. If I put the downloaded .tar.gz in the /tmp folder manually before running the script, the script recognizes that the file is already there.

well, the slow download could be due to the whole world pulling ff2.0.0.4 off their servers. all it is doing is using good old wget as before, so... nothing i can do about the speed. :)

i will look into the thunderbird profile linking glitch...

---

### Post by nanotube on 2007-06-01
ok, it turns out i forgot that little piece of logic. it's there now, i attached the new version to the first message for further testing. :)

---

### Post by aysiu on 2007-06-01
Well, installing and removing Firefox worked (by the way, if you do ```
python ubuntuzilla.py
``` without any extra options, Firefox is installed by default--I like that little trick). Installing Thunderbird worked, but when I tried to remove it, I got this error: ```
**python ubuntuzilla.py -p thunderbird -a remove**
Traceback (most recent call last):
  File "ubuntuzilla.py", line 454, in <module>
    class ThunderbirdInstaller(MozillaInstaller):
  File "ubuntuzilla.py", line 490, in ThunderbirdInstaller
    if not self.options.test:
NameError: name 'self' is not defined
``` By the way, can you let people know that if they've already downloaded the .tar.gz, they should put it in the /tmp folder to save the extra download?

That could be a message the script displays at the beginning... or it could just be in the Wiki instructions. Which do you think is the best?

---

### Post by nanotube on 2007-06-03
> **aysiu said:**
> Well, installing and removing Firefox worked (by the way, if you do ```
python ubuntuzilla.py
``` without any extra options, Firefox is installed by default--I like that little trick).

yea, i figured that that is the most common action people would want to take, so set those as defaults. :)

> 
 Installing Thunderbird worked, but when I tried to remove it, I got this error: ```
**python ubuntuzilla.py -p thunderbird -a remove**
Traceback (most recent call last):
  File "ubuntuzilla.py", line 454, in <module>
    class ThunderbirdInstaller(MozillaInstaller):
  File "ubuntuzilla.py", line 490, in ThunderbirdInstaller
    if not self.options.test:
NameError: name 'self' is not defined
``` 


hmm, that's strange.. i noticed that that bit had different indentation (spaces instead of tabs), so, try the new fixed version. i gave it a testing (with the -t option, since i didn't actually want to remove my thunderbird :) ), and it didn't give me any problems. 

> 
By the way, can you let people know that if they've already downloaded the .tar.gz, they should put it in the /tmp folder to save the extra download?

That could be a message the script displays at the beginning... or it could just be in the Wiki instructions. Which do you think is the best?

yea, that's a good point. i don't even think twice of doing an extra download, but not everyone is on a fast connection. i think it would have a good home on the wiki instructions, so i will put that up there when i update the wiki for the new python version (which will be after our testing here is complete). what do you think?

---

### Post by aysiu on 2007-06-03
I'll try out the revised script.

The main thing about telling people to put it in the /tmp directory is that a lot of people have already downloaded the .tar.gz before they even know about the script (they're used to the setup.exe of Windows).

More after I've done some testing with the new script...

---

### Post by aysiu on 2007-06-03
Okay. The script worked flawlessly. I tried installing and removing Firefox, installing and removing Thunderbird, and installing and removing Seamonkey.

The only glitch I saw I *think* has to do more with Gnome than the script. After I removed Thunderbird, the Preferred Application for email suddenly became (stayed?) ```
/opt/thunderbird/thunderbird
``` instead of ```
mozilla-thunderbird %s
``` so my *launch email* keyboard shortcut gave me this error.

Again, nothing to do with the script itself, but it's just an adverse side effect Gnome users may encounter.

---

### Post by nanotube on 2007-06-03
> **aysiu said:**
> Okay. The script worked flawlessly. I tried installing and removing Firefox, installing and removing Thunderbird, and installing and removing Seamonkey.

The only glitch I saw I *think* has to do more with Gnome than the script. After I removed Thunderbird, the Preferred Application for email suddenly became (stayed?) ```
/opt/thunderbird/thunderbird
``` instead of ```
mozilla-thunderbird %s
``` so my *launch email* keyboard shortcut gave me this error.

Again, nothing to do with the script itself, but it's just an adverse side effect Gnome users may encounter.

aha, thanks for pointing that out! i looked into this, and it turns out that when the "new" thunderbird tells you to set itself as the default application, it ignores the symlinks, and sets it straight to /opt/thunderbird/thunderbird. that's why when it is removed, preferred app points to a nonexestent location.

i have added the functionality to the removal script to reset preferred applications back to the default "mozilla-thunderbird %s". please test to make sure that it works as expected.
if this goes through, since you say everything else works well, i suppose the script will be ready to go live? :)

edit: new version attached to first post, as before.

---

### Post by aysiu on 2007-06-03
It now works perfectly... including resetting the preferred application. Take it live!

---

### Post by nanotube on 2007-06-03
> **aysiu said:**
> It now works perfectly... including resetting the preferred application. Take it live!

excellent :). i will do that tomorrow, since before i push out the .py, i have to do some rather significant editing of the wiki instructions, and it's about 2 hours since i was ready to go to bed. :)

thanks for your thorough-as-usual testing. :)

---

### Post by nanotube on 2007-06-03
it is live! :)
i have updated the wiki and uploaded the release to the sf fileservers.
please check over the wiki page whenever you have a minute and see if i have made any glaring, or not so glaring, omissions.

---

### Post by aysiu on 2007-06-03
I'll do that probably in the next few days. Thanks for the update.

---

### Post by nanotube on 2007-06-03
> **aysiu said:**
> I'll do that probably in the next few days. Thanks for the update.

thanks :) no hurry, i did proof it myself a couple of times, so it shouldn't be that bad. 

by the way, i just tried updating firefox with the gksudo method, and chose 'restart firefox now', and the update failed. i had to do the "restart firefox manually" method in order for the update to go through... i'm thinking that maybe the double-manual sudo is a more surefire method? have you never had any similar problems?

---

### Post by aysiu on 2007-06-04
I've never experienced problems with it in the past, but I also haven't tried it recently (in a 2.0.0.3 to 2.0.0.4 update).

---

