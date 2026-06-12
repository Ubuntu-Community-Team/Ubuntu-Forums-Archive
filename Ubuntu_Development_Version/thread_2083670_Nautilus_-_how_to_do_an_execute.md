---
title: "Nautilus - how to do an execute?"
date: 2012-11-13
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2012-11-13
Used to be, double click on a #!/bin/bash execute script had the choices:
execute  display  cancel  ...
Now double click on an execute script does not start it but just does display.

I don't see anything under any of the choices I've found.

How under Nautilus do I start an execute?

Is this a bug or I fear a new "feeture"?

Thanks, Jerry

---

### Post by ercherramon on 2012-11-13
you have tried to copy the executable in the home or on the desktop?

---

### Post by Abhinav Kumar on 2012-11-13
> **jerrylamos said:**
> Used to be, double click on a #!/bin/bash execute script had the choices:
execute  display  cancel  ...
Now double click on an execute script does not start it but just does display.

I don't see anything under any of the choices I've found.

How under Nautilus do I start an execute?

Is this a bug or I fear a new "feeture"?

Thanks, Jerry
Hi,

You can execute by opening the terminal and then ```

cd folder
./fileName
```
replace folder by the folde in which executable is located.
replace fileName.sh by the script file you want to execute.

Note that file needs to have permissions to be executable.
:)

Regards
Abhinav

---

### Post by mc4man on 2012-11-13
> **jerrylamos said:**
> Used to be ....

Is this a bug or I fear a new "feeture"?

Thanks, Jerry
Neither, simply the default 'preference' has been set to display. You can change it back if desired

---

### Post by jerrylamos on 2012-11-13
mc4man, the "Files Preferences" looks like what I want.
My question is, where did you find that drop down menu?
I don't see Files Preferences on the file display panels
I don't see Files Preferences on Systems Settings
?
Thanks, Jerry

Hey, finally found the drop down under Home Folder way up at the top left of the screen.

I'm still not used to having some controls on the window of an application and some controls on the top panel of the screen.  For example sometimes edit is way up there at the top left, sometimes it's in the application window.

I set the Files Preferences to ask each time and got the same behavior as on quantal, precise, narwhal, meerkat, ...

The developers change preferences for various basic things like keyboard and it takes me a while to dig out what changed and how to set it back.

---

### Post by pkadeel on 2012-11-13
> **jerrylamos said:**
> mc4man, the "Files Preferences" looks like what I want.
My question is, where did you find that drop down menu?
I don't see Files Preferences on the file display panels
I don't see Files Preferences on Systems Settings
?
Thanks, Jerry
That should be in the Nautilus menus. Not using Nautilus right now but it should be under Edit > Prefrences or Options > Preferences

---

### Post by mc4man on 2012-11-13
> **jerrylamos said:**
> 

Hey, finally found the drop down under Home Folder way up at the top left of the screen.

I'm still not used to having some controls on the window of an application and some controls on the top panel of the screen.  
It's a bit different but for the most part don't mind the 4 menus.
App menu - in panel
Selection menu - the gear icon
View menu - the down arrow
Context menu
 Also in most cases each menu item is direct accessible instead of thru a tree

So things are missing but not that big a deal - to me the most obvious is the missing "New Document" in the context menu - will come back if you place a file in ~/Templates
(there is a fix in 3.7.1 that removes the dupe if you place an empty text file in ~/Templates, maybe they will backport it to 3.6.+

---

### Post by EowynCarter on 2013-05-01
> **mc4man said:**
> Neither, simply the default 'preference' has been set to display. You can change it back if desired

Tanks !!
I was getting crazy tying to get Intellij to start without resorting to Command line!

---

