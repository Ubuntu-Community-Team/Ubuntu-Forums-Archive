---
title: "[SOLVED] I can't figure this out!!!"
date: 2007-06-30
forum: Ubuntuzilla
---

### Post by RogerDavis on 2007-06-30
I was really glad to find a script and a simple procedure to update SeaMonkey.  However, it either is working and I can't see anything happening, or there isn't enough detail for me to know how to  proceed.
1) I try to download the script compressed? file, apparently not possible.  
2) I try to download the individual files, says downloading, but I can't see it happening.  
3) It says 0 downloads.  
4) I can't find it on the disk by search.

I need more information, more detail, something...   Thanks!

---

### Post by PaulFr on 2007-06-30
By download link for SeaMonkey, are you referring to **[http://download.mozilla.org/?product=seamonkey-1.1.2&os=linux&lang=en-US](http://download.mozilla.org/?product=seamonkey-1.1.2&os=linux&lang=en-US)** ? Well,

1. I did not have any problem downloading this in Firefox (this put it in my Desktop),
2. Created a ~/seamonkey directory and moved this downloaded file file from my Desktop to ~/seamonkey.
4. **tar zxvf sea*tar.gz** gave me the installer in ~/seamonkey-installer, which I ran to install everything in ~/seamonkey-install directory. Running ~/seamonkey-install/seamonkey brings up the software properly.

Cannot see any issue. As far as upgrade goes, the installer indicates that the installaiton directory should either be empty, OR have a previous installation. Presumably, the installer will upgrade the previous installation to version 1.1.2 properly (cannot be sure since I do not have a previous version).

---

### Post by nanotube on 2007-06-30
> **RogerDavis said:**
> I was really glad to find a script and a simple procedure to update SeaMonkey.  However, it either is working and I can't see anything happening, or there isn't enough detail for me to know how to  proceed.
1) I try to download the script compressed? file, apparently not possible.  
2) I try to download the individual files, says downloading, but I can't see it happening.  
3) It says 0 downloads.  
4) I can't find it on the disk by search.

I need more information, more detail, something...   Thanks!

the script is not a compressed file, it is a plain-text python script.
please follow download instructions on the main ubuntuzilla website:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)
and then let me know if you have any problems. :)

---

### Post by PaulFr on 2007-06-30
Thx nanotube for the info.

---

### Post by RogerDavis on 2007-07-01
I'm still having problems.  Here's what happens.

1) Attempt Download
- I get "Downloading ...
Thank you for downloading Simple Python Keylogger for Windows.
Your download should begin shortly. If you are experiencing problems with the download please use this direct link. 
- Nothing visible happens.  No download manager, nothing...
2) Attempt "direct link"
- "ba72e66aec2aa81b9ff0414e0718a3f7  ubuntuzilla_4.1.1.py" appears on screen, no other activity.
3) Attempt different site
- Get choice of keylogger or Ubuntuzilla
- Choose Ubuntuzilla
- Same as 1)
4) Choose San Jose
- No result
5) Attempt "direct link"
- Get 
"from optparse import OptionParser
import re
import os, os.path
import sys
import stat
import time
#todo: skipbackup even in attended mode? really only need for tbird, and it already asks anyway?
etc...
(By ANY chance, can I simply copy this and paste it into the terminal?)
6) Loop to line 1)...
7) Self taught lesson in creative language...
8) Beg for help again...

I just must lack some kind of basic info.  I have downloaded in Ubuntu with SeaMonkey before, it goes pretty normally, no problems, just like in Windoze.

---

### Post by PaulFr on 2007-07-01
This I can answer - when you get to the direct link, right click on the link, and use "Save Link As" and select the location as your home directory.

---

### Post by nanotube on 2007-07-01
> **RogerDavis said:**
> I'm still having problems.  Here's what happens.

1) Attempt Download
- I get "Downloading ...
Thank you for downloading Simple Python Keylogger for Windows.
Your download should begin shortly. If you are experiencing problems with the download please use this direct link. 
- Nothing visible happens.  No download manager, nothing...
2) Attempt "direct link"
- "ba72e66aec2aa81b9ff0414e0718a3f7  ubuntuzilla_4.1.1.py" appears on screen, no other activity.
3) Attempt different site
- Get choice of keylogger or Ubuntuzilla
- Choose Ubuntuzilla
- Same as 1)
4) Choose San Jose
- No result
5) Attempt "direct link"
- Get 
"from optparse import OptionParser
import re
import os, os.path
import sys
import stat
import time
#todo: skipbackup even in attended mode? really only need for tbird, and it already asks anyway?
etc...
(By ANY chance, can I simply copy this and paste it into the terminal?)
6) Loop to line 1)...
7) Self taught lesson in creative language...
8) Beg for help again...

I just must lack some kind of basic info.  I have downloaded in Ubuntu with SeaMonkey before, it goes pretty normally, no problems, just like in Windoze.

that first content you got' "ba72e66aec2aa81b9ff0414e0718a3f7  ubuntuzilla_4.1.1.py" must be the md5sum, not the script itself. 
when you get that second page, with "from optparse..."
just go file -> save page as, and save that as ubuntuzilla.py in your home dir. :)

---

### Post by RogerDavis on 2007-07-01
OK, I got a few steps forward.

1) Got main file from direct link method, saved - OK
2) Can't get text file - continually either no result at all, or if I select direct link, get ba72e66aec2aa81b9ff0414e0718a3f7  ubuntuzilla_4.1.1.py every time, never get download or  actual file (unless this is it?!?)
3) I want SeaMonkey as a two-user program, I currently have it installed in File System/usr/local/seamonkey, and both she and I can access it.  Where will the script put it?  If not as mentioned, I presume I can do a search and replace to change the installation point?  Or will it place Seamonkey in a better location and remove the old one?

Thanks!

---

### Post by nanotube on 2007-07-01
> **RogerDavis said:**
> OK, I got a few steps forward.

1) Got main file from direct link method, saved - OK
2) Can't get text file - continually either no result at all, or if I select direct link, get ba72e66aec2aa81b9ff0414e0718a3f7  ubuntuzilla_4.1.1.py every time, never get download or  actual file (unless this is it?!?)
3) I want SeaMonkey as a two-user program, I currently have it installed in File System/usr/local/seamonkey, and both she and I can access it.  Where will the script put it?  If not as mentioned, I presume I can do a search and replace to change the installation point?  Or will it place Seamonkey in a better location and remove the old one?

Thanks!

ok, just to be clear again, here's a direct link to the .py file:
[http://superb-west.dl.sourceforge.net/sourceforge/pykeylogger/ubuntuzilla_4.1.1.py](http://superb-west.dl.sourceforge.net/sourceforge/pykeylogger/ubuntuzilla_4.1.1.py)
right click on that, say save as, and save it to your home dir as ubuntuzilla.py

you don't need any other file, just follow the instructions on the website for running the script. for seamonkey, the command line would be
```
python ~/ubuntuzilla.py -a install -p seamonkey
```

follow the prompts, and seamonkey will be installed.

the installation directory is /opt/seamonkey, this is where everything will go. it will also create an applications menu item for seamonkey, so you can use that to launch.

so go run the script, and let us know how it goes. :)

---

### Post by RogerDavis on 2007-07-01
I now have the Ubuntuzilla file on hand.  (Will it run from any location?)

I can see that the installation directory is different from where I put the first SeaMonkey.  

If I don't want to leave trash around, or worse yet, have SeaMonkey stuff in two or more locations, will the script remove the old one but save the bookmarks, or should I delete it first and save the bookmarks separately?

Thanks!

---

### Post by nanotube on 2007-07-01
> **RogerDavis said:**
> I now have the Ubuntuzilla file on hand.  (Will it run from any location?)

I can see that the installation directory is different from where I put the first SeaMonkey.  

If I don't want to leave trash around, or worse yet, have SeaMonkey stuff in two or more locations, will the script remove the old one but save the bookmarks, or should I delete it first and save the bookmarks separately?

Thanks!

it will run from any location - but for the automatic update checker it should be in your home directory. so i'd recommend that you put it straight into your home directory.

your bookmarks, etc. are stored in a .mozilla directory in your home dir - and will be taken up by the new install without any problems. your settings/profile is completely separate from where you put your executable (/usr/local/seamonkey), so you should basically feel free to delete /usr/local/seamonkey after ubuntuzilla finishes its work. all your personal settings and bookmarks should remain unaffected (but of course, run the new seamonkey first, and make sure everything is there, before deleting the old one).

also note that ubuntuzilla will automatically make a backup of your .mozilla folder, so you will have a backup of your bookmarks etc. just in case. :)

---

### Post by RogerDavis on 2007-07-01
Getting closer...

There are two home directories, one "Home", the other "file system/home", which then contains the user directories.  I tried the "Home" one, and got :

"root@Roger-Ubuntu-desktop:/home/roger# python ~/ubuntuzilla.py -a install -p seamonkey
python: can't open file '/root/ubuntuzilla.py': [Errno 2] No such file or directory
root@Roger-Ubuntu-desktop:/home/roger# "

Which is the correct one?

Or do I need to set the terminal to root, and if so, how?

Thanks!

---

### Post by nanotube on 2007-07-01
> **RogerDavis said:**
> Getting closer...

There are two home directories, one "Home", the other "file system/home", which then contains the user directories.  I tried the "Home" one, and got :

"root@Roger-Ubuntu-desktop:/home/roger# python ~/ubuntuzilla.py -a install -p seamonkey
python: can't open file '/root/ubuntuzilla.py': [Errno 2] No such file or directory
root@Roger-Ubuntu-desktop:/home/roger# "

Which is the correct one?

Or do I need to set the terminal to root, and if so, how?

Thanks!

you need to put it into your user's home directory. so, that would be **/home/roger** (as i can see from looking at your prompt there). 

and no, you don't need to run the script as root. it will ask you for your root password at some point to do some things as root, but don't run the script itself as root. run it as your regular user (it this case, roger, it seems).

try that. ;)

---

### Post by RogerDavis on 2007-07-02
OK, done, working. 

Now, trying to delete the /usr/local/seamonkey.  File Manager says not mine (root), so can't do it.  How do I log in as root, or tell file manager to let me do it?

Thanks!

---

### Post by nanotube on 2007-07-02
> **RogerDavis said:**
> OK, done, working. 

Now, trying to delete the /usr/local/seamonkey.  File Manager says not mine (root), so can't do it.  How do I log in as root, or tell file manager to let me do it?

Thanks!

sounds good! :)

to remove that folder, 
enter command
```
sudo rm -rf /usr/local/seamonkey
```
and it will ask you for your password, and then remove the stuff.
in general, if you want to learn more about privilege separation on linux and how to work with root and sudo (and trust me, you do want to learn more :) ), read this page:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by RogerDavis on 2007-07-03
OK, all done.

I suggest you take all my questions and combine them (answers) with your instructions.

The script itself worked very well!

---

### Post by nanotube on 2007-07-03
hm, you're right, the instructions on the site could be a bit clearer. i suppose i'll update them. :)

---

### Post by RogerDavis on 2007-07-07
Another thing - I never did get the instructions downloaded, never could make the download work, had to indirectly get the script, though I obviously got that - no idea of why the difficulty.

Thanks!

---

