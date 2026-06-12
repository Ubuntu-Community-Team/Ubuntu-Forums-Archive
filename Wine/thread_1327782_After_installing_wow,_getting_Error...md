---
title: "After installing wow, getting Error.."
date: 2009-11-15
forum: Wine
---

### Post by Travatan on 2009-11-15
I'm a first time Ubuntu user and Ive tried looking everywhere for a similiar error and cannot. After installing Wine, doing the online download and install of WoW, I try to run the program and I get the following error message:

"Details: Failed to change to directory '/home/chris/.wine/dosdevices/c:/World of Warcraft/' (Permission denied)"

I'm not sure where to go from here. If needed I can post a screenshot. Thanks in advance!

---

### Post by randallsquared on 2009-11-15
> **Travatan said:**
> I'm a first time Ubuntu user and Ive tried looking everywhere for a similiar error and cannot. After installing Wine, doing the online download and install of WoW, I try to run the program and I get the following error message:

"Details: Failed to change to directory '/home/chris/.wine/dosdevices/c:/World of Warcraft/' (Permission denied)"

I'm not sure where to go from here. If needed I can post a screenshot. Thanks in advance!

After recent downloaded patches, WoW (on my system, at least) spontaneously changes the permissions of its folder so you can't look in it.  Since you own it, it's not difficult to change it back.  If you know how to use the terminal, you can just do
```
chmod 755 "/home/chris/.wine/dosdevices/c:/World of Warcraft/"
```and then try to start it again.  This assumes you copied the error exactly, but if not, just replace the folder path above with whatever yours really is.

I'm sure there's a way to do this without using the command line, but I don't know enough about Ubuntu to know what it is, yet.

---

### Post by Travatan on 2009-11-15
Thanks for the response. I did copy that that error message directly and I had noticed the permisions changing. When i typed the code into the terminal I get the following error:

chris@chris-laptop:~$ chmod 755 /home/chris/.wine/dosdevices/c:World of Warcraft/
chmod: cannot access `/home/chris/.wine/dosdevices/c:World': No such file or directory
chmod: cannot access `of': No such file or directory
chmod: cannot access `Warcraft/': No such file or directory

What next? :p

---

### Post by bwisdom on 2009-11-15
I actually use a script for this. I got it off this forum actually, if I find the post I will edit it in. The reason for the script is so I dont have to do that over and over. Anywho, this is what is in it.

#!/bin/bash
clear
wine "/home/<user>/.wine/drive_c/Program Files/World of Warcraft/wow.exe";
chmod 755 "/home/<user>/.wine/drive_c/Program Files/World of Warcraft/" -R 

change where is says <user> to your login name and it should work. Oh and for what he typed I believe it goes

chmod 755 /home/chris/.wine/dosdevices/c:/World\ of\ Warcraft/

The reason for the back (or forward?) slashes is because you cant just have a space in a command line so to fix this you type the space character which is '\ '. If that doesnt work you need to put 'Program\ Files' inbetween c: and World of Warcraft. Or another way to go around it is to put double quotes around it like there is in my script above.

EDIT: The forum I found the info on was here
[http://ubuntuforums.org/showthread.php?p=8322730](http://ubuntuforums.org/showthread.php?p=8322730)

---

### Post by randallsquared on 2009-11-15
Yeah, like bwisdom said, use quotes.  Sorry.  My only excuse is that I use tab-completion so much that the shell always adds the backslashes to cover spaces for me. :D

---

### Post by Travatan on 2009-11-16
Well that certainly fixed it, now it just gives the 132 Error, which is a whole nuther bag o *&#(@.  Thanks alot tho. Now I know how to get WoW to work "Currently"

---

### Post by bwisdom on 2009-11-16
That is where I am stuck at too. Ive put a post up about it if ya want to check it out, I have yet to get any replies thought as of this posting

[http://ubuntuforums.org/showthread.php?t=1327627](http://ubuntuforums.org/showthread.php?t=1327627)

---

