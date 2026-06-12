---
title: "Rockbox on my sansa fuze :)"
date: 2009-06-07
forum: The Cafe
---

### Post by dragos240 on 2009-06-07
Okay so I finally got a rockbox on my sanas fuze, although, I got the bootloader working, the firmware is another story, but I'm installing that now, and if it doesn't work, I found out that all my previous songs and even the sansa OS itself is still there and working. This is really neat.

---

### Post by dragos240 on 2009-06-07
UPDATE: It is working!!!! I now have rockbox on my fuze. Testing it now. It is NOT available yet other than compiling everything from source.

---

### Post by Jackelope on 2009-06-07
Wow, seriously? I didn't know that was possible yet. If you get a chance after testing the stability of it, could you post some step-by-step instructions?

---

### Post by andrewabc on 2009-06-07
Good news.

[http://www.rockbox.org/twiki/bin/view/Main/SansaFuze](http://www.rockbox.org/twiki/bin/view/Main/SansaFuze)

---

### Post by Vostrocity on 2009-06-07
Very nice, but it's not out officially yet. I may upgrade my e200 once it is. I'd be pretty impressed if they got RockBox to work on a Clip though.

---

### Post by Dharmachakra on 2009-06-07
That's pretty nifty. I might have to try that out sometime soon... though I am happy with my stock Fuze.

---

### Post by dragos240 on 2009-06-08
Yes, it's not released yet, but I do have a few guides that I followed to get it on my fuze running 9.04.
First open up a terminal and download the source via subversion:[FONT=monospace]
[/FONT]svn co svn://svn.rockbox.org/rockbox/trunk rockbox

get into your rockbox directory now, and create a new folder for your built files.
ex: mkdir build.

now go back to the main directory and go to tools. From here run rockboxdev.sh, you may have to make it an executable by:
chmod +x rockboxdev.sh.

and follow the onscreen instructions.

Now there is something you need to add to the .bashrc and logout and in, but I don't know where or what it is right now. If you find it out, the navigate to your build directory and enter:
../tools/configure and choose n for normal,

now make. This may take a bit.

And now configure again in the build directory, but this time, choose b for bootloader. When all of this is done, navigate to the main directory and choose rbutil and mkamsboot.

Make this. And then copy the bootloader and the original firmware (which can be found [here]("http://forums.sandisk.com/sansa/?category.id=devices")) to the mkamsboot directory. And now do this:
./mkamsboot [original firmware] [bootloader] output.bin now go to your build directory and:
build zip, extract this directory to the root sansa directory. And then copy the output.bin to the root directory, and rename it to your original firmware name. And enjoi!

---

