---
title: "Bug in xmodmap?"
date: 2013-10-17
forum: Ubuntu Development Version
---

### Post by effenberg0x0 on 2013-10-17
It's been a while. 
Can anyone using SS help me confirm a bug before I post it on Launchpad (question mark). Yes, I don't have a question mark right now.

**1)** Open a terminal window;
**2)** Press any letter. Let's test with '**A**'. You press '**A**' and you obviously get '**A**'. OK :)
**3)** Now lets map '**A'** to something else. Lets say '**X**':
```
xmodmap -e "keycode 38 = x X
```
**4)** Press '**A**': You probably see "**X**" now. Good. xmodmap works so far.
**5)** Now click anywhere else on your desktop. Anywhere: Your wallpaper, the launcher, the dash, you choose.
**6)** Go back to that terminal. Press '**A**'. 

**Do you see 'A' or 'X' **(question mark)
If you see '**A**', something is in fact wrong with xmodmap.

- Up to the previous version, anyone could customize a keyboard by modifying ~/.Xmodmap (Example: when you buy an imported laptop).
- It looks like xmodmap settings are lost when the user switches from Terminal to Desktop and back to Terminal.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2013-10-17
I have apparently fixed it here with:
```
sudo apt-get remove indicator-keyboard
sudo kill -s KILL $(ps ax | grep -i indicator-keyboard-service | awk 'BEGIN {FS=" "} {print $1}')
```
Then I remapped with xmodmap like in the previous post and changes are now kept when I alternate between windows.

Regards,
Effenberg

[EDIT]: Yep, I believe it's the new language indicator indeed. It seems to refresh keyboard mappings every time the user switches between windows. [/EDIT]
[EDIT 2]: It's a dup anyway: [https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1215826](https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1215826) [/EDIT]

---

### Post by grahammechanical on 2013-10-17
I cannot believe my eyes! It is nice to see your ugly mug again. :) I wish you well.

Have you been following developments? Ventrical has led the charge in practical testing of Ubuntu on btrfs. I trotted along after him. I did manage to work out how to modify the Recovery mode scripts to produce a snapshot manager menu. It actually worked.

It is late here in England. Time to go. 

Best regards.

---

### Post by OGpmpdog on 2013-10-17
> **effenberg0x0 said:**
> I have apparently fixed it here with:
```
sudo apt-get remove indicator-keyboard
sudo kill -s KILL $(ps ax | grep -i indicator-keyboard-service | awk 'BEGIN {FS=" "} {print $1}')
```
Then I remapped with xmodmap like in the previous post and changes are now kept when I alternate between windows.

Regards,
Effenberg

[EDIT]: Yep, I believe it's the new language indicator indeed. It seems to refresh keyboard mappings every time the user switches between windows. [/EDIT]
[EDIT 2]: It's a dup anyway: [https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1215826](https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1215826) [/EDIT]

My eyes deceive me!! An Effenberg sighting?? 

Dude, Planet Earth welcomes you back to the Saucy Side...

---

### Post by effenberg0x0 on 2013-10-18
> **grahammechanical said:**
> I cannot believe my eyes! It is nice to see your ugly mug again. :) I wish you well.
Ventrical has led the charge in practical testing of Ubuntu on btrfs. I trotted along after him. I did manage to work out how to modify the Recovery mode scripts to produce a snapshot manager menu. It actually worked.
It is late here in England. Time to go. 
Best regards.

> **OGpmpdog said:**
> My eyes deceive me!! An Effenberg sighting?? 
Dude, Planet Earth welcomes you back to the Saucy Side...

Hey :) I had to step out of these last two cycles, for personal reasons. And I really missed it.
I've been reading some of the topics here once every two weeks or so, since October 16 2012. But I'm not really up-to-date on everything that went on. 
There are more emails in my Ubuntu-related folder than I can possibly read. I'm glad to see everyone is still here. I'll be on IRC, let's catch up.  

Regards,
Effenberg

---

