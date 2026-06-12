---
title: "Weird question about a program called wine."
date: 2010-07-19
forum: Wine
---

### Post by IDontKnowWhatIAmDoing on 2010-07-19
Hey, can anyone help me with wine?  Anytime I try to use wine to open a windows program it says:


"The file '/home/christopher/Desktop/iTunes64Setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."


Any help would be greatly appreciated, and I am also pretty new to using anything linux... so any hints or clues to using linux would be helpful too.

Thanks,
Chris

---

### Post by jerenept on 2010-07-19
right click on the .exe file, then select "Properties" go to the tab that says "Permissions". Now check the box next to the sentence "Allow executing file as program"

iTunes typically does not work properly in Wine. it is more sensible to either dual-boot, use a Virtual Machine, or use Rhythmbox or GTKPod to use your iPod.
AFAIK

---

### Post by IDontKnowWhatIAmDoing on 2010-07-19
ok, Thank you!  I didn't really want to use iTunes though I find Rhythmbox much more effective.  I tried to use wine to run a game, and I got the same message.  So I figured that apple would be a "Trusted source" ya know? lol

---

### Post by howefield on 2010-07-19
jerenept is correct, running itunes in wine is not a good move.

You could try opening the installer via terminal, it may give you a clue in the output as to what is going wrong.

Open a terminal (Applications > Accessories > Terminal) and type

```
wine filename.exe
``` 

Substitute "filename.exe" with the name of the file you are executing.

---

### Post by IDontKnowWhatIAmDoing on 2010-07-19
When it comes to Terminal, Its pretty much like reading Japanese to me at this moment... this is what it says:


"err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)"

I have no clue what this means.

---

### Post by howefield on 2010-07-19
> **IDontKnowWhatIAmDoing said:**
> "err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)"

Yep, means nothing to me, but you could use the string and do a search on it, see if anything useful comes up. The error seems common to more than just getting itunes to work.

Also, I would post in the wine forum as you may get posters reading that may not visit the General Help forum.

And again, I have to say, running itunes in wine is not a good move.

---

### Post by ronnielsen1 on 2010-07-19
If you're trying to install windows software google software winehq

Example: Office 2007 winehq

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992\](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992\)

It will tell you if you need to do anything special and how well it works

---

### Post by 3Miro on 2010-07-19
> **ronnielsen1 said:**
> If you're trying to install windows software google software winehq

Example: Office 2007 winehq

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992\](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992\)

It will tell you if you need to do anything special and how well it works

I second that. Windows programs often require specific settings to properly work under wine (and yes, some games/software will not work at all). Go the winehq and search for the specific app there, they usually have detailed instructions.

---

### Post by etdsbastar on 2010-07-19
> **IDontKnowWhatIAmDoing said:**
> Hey, can anyone help me with wine?  Anytime I try to use wine to open a windows program it says:


"The file '/home/christopher/Desktop/iTunes64Setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."


Any help would be greatly appreciated, and I am also pretty new to using anything linux... so any hints or clues to using linux would be helpful too.

Thanks,
Chris

Why don't you use Virtual Box, Its much better, you can install mostly all the packages at your will and choice. More help from [www.virtualbox.org]("http://www.virtualbox.org")

Below is the screenshot.

---

### Post by Iowan on 2010-07-19
> **howefield said:**
> Also, I would post in the wine forum as you may get posters reading that may not visit the General Help forum.I can help with that part...
Moved to Wine.

---

### Post by asdfoo on 2010-07-20
You haven't specified which version of Wine you are using.  1.2 is the most recent, open a terminal and type 'wine --version'

---

