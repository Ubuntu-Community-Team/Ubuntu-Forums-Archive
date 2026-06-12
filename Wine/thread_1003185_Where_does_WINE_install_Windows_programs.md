---
title: "Where does WINE install Windows programs"
date: 2008-12-05
forum: Wine
---

### Post by thadacto on 2008-12-05
Hi Wine sippers -
I am running Windows XP as my C drive and Ubuntu 8.04.
If I install a program that I have in XP will WINE overwrite it or does it install to somewhere in the UBUNTU directories? I don't want to upset my Windows programs before I know they will work in WINE.


Just one more glass, please!

---

### Post by Patrick793 on 2008-12-05
Wine installs the program in ~/.wine/drive_c/Program Files
It doesn't touch your Windows XP installation.

---

### Post by thadacto on 2008-12-05
Cheers - Many thanks
I can install without worries.[http://ubuntuforums.org/images/smilies/smiley-faces-80.gif](http://ubuntuforums.org/images/smilies/smiley-faces-80.gif)

---

### Post by Kellemora on 2008-12-05
Hi thadacto

Since it wasn't mentioned.

.wine is a hidden folder in your /home/user directory.

You can hit CTRL-h or go up to VIEW and select show hidden files, in order to be able to see those hidden files.

Took me 2 whole days to find the .wine folder because I didn't know it was hidden!  That's why I chimed in, just in case you didn't know this.

But most people have more Schmartz than I do with these confounded computin' contraptions, hi hi.........

TTUL
Gary

---

### Post by thadacto on 2008-12-05
Hi Kellemora,
Thanks - I was searching for the winecfg file because I couldn't find it. The search eventually got it but then it doesn't tell you exactly where it is in the file system - just that it's there, its size and when last modified. Even the properties box didn't really help.
To be honest, I am a computer user - I enjoy playing around with the programs, like driving a car - I don't care what's under the bonnet (hood -  for those in the US!) as long as it goes. With Linux, you've got to know something about what's under the bonnet. It's two weeks now and I'm still not up and running smoothly, yet.

---

### Post by jacksaff on 2008-12-05
Well you're trying to run programs for one operating system on another, completely different os. This is not basic computing so you would expect to need to know a little. Do you think you would have been able to get unix software running on your windows installation within your first two weeks?

---

