---
title: "wine-1.0-rc1 .. not updating!"
date: 2009-11-19
forum: Wine
---

### Post by Xog on 2009-11-19
Okay, I wanted to update wine to the newest version. Being the windows blockhead I am, I think to myself "okay so I have to uninstall the current version."

So, I go over to my Ubuntu Software Manager and search "wine" and click "Remove"

Now, I want to completely remove it, so I follow the instructions here:
[http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391](http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391)

and enter these commands:
```
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm


```
to completely get rid of it.

So now, I go to [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) and follow the instructions to the tee.

Now I'm at the end of it. And I see this:
Click close to finish, and then reload the package information when prompted. If you have Wine installed, the system's update manager will now inform you of the latest Wine beta release and prompt you to upgrade. If you haven't installed Wine yet, go to Applications->Add/Remove and search for Wine or just click _this link._
So I clicked Close, and then Reload, and I see a bunch of stuff updating. Cool. But then, I see the "If you haven't installed Wine yet, go to blahblahblah or click here" so being the lazybum I am, I click the "Click here".
I click Open, and I'm presented with the lovely message:
```
Could not apply changes!
Fix broken packages first.

```
GREAT! : - \

So I go to Ubuntu Software Center and search "wine" and click Install.. where I'm now presented with:
```
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```
So, I click Details and it says:
wine


So now I see below wine is the Beta Release in the software center, so I install that. Cool cool. It's working. To be on the safe side, I check the version..

[IMG]http://img34.imageshack.us/img34/5650/wineversion.png[/IMG]

What the heck!

Now here's the REAL DOOZIE.

I uninstall wine again, and remove the .wine directory as I did before.

Then I do wine --version again, and it still says wine-1.0rc-1 !!!
Has wine become a ghost?? Is it haunting my hard drive!? How do I perform an exorcism on this program!

---

### Post by Xog on 2009-11-19
okay :-| It's freaking me out now. My screen just flashed black for a split second while viewing the forums.

---

### Post by Xog on 2009-11-19
solved it by pure luck from another person's post that didn't even regard this.

Solved by:

Opening Synaptic Package Manager
search "wine"
right clicked on the green boxes, and marked for COMPLETE REMOVAL.

Then installed wine :-D as I should.. unfortunately when I try
```
wine --version
```
I get this: 
bash: /usr/local/bin/wine: No such file or directory

What's up?

---

### Post by Alatar1 on 2009-11-19
This could be a karmic issue im not sure...
you CAN try ```
sudo apt-get remove --purge wine
```
WARNING this can be dangerous using this command
then delete the files and try reinstalling via the instructions on winehq
Don't use the option to install it built in to ubuntu, if you do that it will install 1.0 everytime

---

### Post by Xog on 2009-11-19
using the method i explained in my previous post i removed the way way outdated wine version and currently have the newest version. im installing WoW at the moment. is it possible you could upload your /usr/local/bin/wine to ubuntu one for me to d/l? :D

---

