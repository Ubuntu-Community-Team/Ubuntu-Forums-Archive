---
title: "How to: Make CDs &amp; DVDs you can Check for Defects at any time. Includes Fast Aliases!"
date: 2009-01-15
forum: Ubuntu Studio
---

### Post by OzzyFrank on 2009-01-15
Want to be able to check your discs after you've burned them, and at any time in the future? Read this tutorial to find out how! You can do this using a **terminal** and **your favourite burning app** like Gnomebaker... but for movie DVDs you'll need **[COLOR="Indigo"]K3B[/COLOR]**.

First off, because these terminal commands are sort of hard to remember, you'll need to copy and paste them into a text file for later use. _Better still_: **add them to your command aliases file**! I'll include info on how to do this too, so you won't even need to copy and paste the commands to the terminal, just type easy-to-remember names like **make5** (to generate the checksums), **5** (check a folder with a checksum file) and **cd5** (check a disc in your drive that contains a checksum). (If you don't want to do this, just ignore the steps and use the commands outlined.)

Secondly, you need to make sure you have the ability to do 2 things: **open a terminal in the current folder you're in** (you'll be doing quite a bit of this), and to **see hidden files** in any folder you're in (to edit the command aliases file). If you right-click an empty area of a folder, you should see the option **Open In Terminal** - if you don't, open Synaptic and install **[COLOR="#4b0082"]nautilus-open-terminal[/COLOR]** and then you'll be able to do so. From then on, when I say "open a terminal in the current folder", you'll be able to do so with a right-click. Now, to show hidden files, open any folder in **Nautilus** ("File Browser"), go to **Edit > Preferences > Views** and make sure **Show hidden and backup files** is checked.

Now go to your home folder and look for a text file called **[COLOR="Indigo"].bash_aliases[/COLOR]** and open it. For your convenience, I've included the relevent bits from my own one, so you just need to copy and paste this into yours:

[B][COLOR="DarkRed"]alias cd5='cd /media/cdrom0 && md5sum -c md5sum.txt'
alias 5='md5sum -c md5sum.txt'
alias make5='find -type f -exec md5sum "{}" \; > md5sum.txt'
[/COLOR][/B]
For those who don't want to add these aliases (though I have no idea why you wouldn't want to make things easier for yourself!), just copy and paste the commands directly into a terminal when needed. Just use my guide to what each alias means to find the command you need.

One last thing before we proceed is a command for **finding out exactly how much space the project will take up** before you burn it: **[COLOR="Indigo"]du -m[/COLOR]**. I've made this easier for myself by making a single-character alias - **[COLOR="#4b0082"]?[/COLOR]** - for this task; if you want to do so too (once again, why wouldn't you??), add this line to **[COLOR="Indigo"].bash_aliases[/COLOR]** under the others:

**[COLOR="DarkRed"]alias ?='du -m'[/COLOR]**

Now, for the main part of this tutorial, I'll be using my aliases, so if you didn't bother making them, use the commands themselves. One thing I won't bother mentioning is using **?** (or **du -m**), since it should be obvious that you'll need to keep an eye on how much space the project is taking up. To do so, just type **?** into a terminal and it will display the size (including all sub-folders) in megabytes. For a DVD, you won't want to exceed 4486 Mb (4488 Mb is actually the limit of most, but some brands hold slightly less, so I've found 4486 Mb to be the safest maximum).

OK, now to generate a checksum (or should I say an **md5sum.txt** file full of checksums for all files to be burned), open a terminal in the current folder and type the alias **make5**. This can even be done with movie DVD projects; just do it in the root of the folder that contains your VIDEO_TS folder.

Now, a checksum will also be generated for md5sum.txt, even though it is still being created. In other words, when that file is checked, it is sure to fail, so once md5sum.txt has finished being created, open it and delete the line that has md5sum.txt to avoid this. If the file contains thousands of entries, simply **Ctrl+F** and type **md5** to search for it, then delete it.

If you're paranoid like me, you'll want to check the folder before burning it, so use the alias **5** to make sure all checksums were created without errors (it doesn't hurt to do this, especially if you had a bunch of tasks churning away in the background).

Now burn all files and folders with your favourite burning app. **To make a playable movie DVD, use K3b** (at the bottom of the Quickstart tab choose **Further actions...** and then **New Video DVD Project**, and simply drag the **VIDEO_TS** folder and **md5sum.txt** file to the project and burn it. You can specify the title label in **Filesystem** before committing to it).

Once your disc has been burned, pop it back in (if it was ejected), open a terminal (Applications > Accessories > Terminal) and type the alias **cd5** to check it! It's that simple!

I hope this has been of use to someone. (If you'd like to thank me, remember you can do so with the little icon/button below this post, hehe!). Cheers. OzzyFrank.

---

