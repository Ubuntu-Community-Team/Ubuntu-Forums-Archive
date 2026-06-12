---
title: "What the..."
date: 2009-09-19
forum: Server Platforms
---

### Post by baudday on 2009-09-19
Something incredibly strange, or at least strange to me, is going on. I just wrote a new php script that I wanted to try out in my Music folder. So I have a symbolic link in /var/www/ to my Music folder which sits at /media/disk/. When I tried to paste the index.php file into /media/disk/Music/ it just said it couldn't. No access denied, no nothing. I just "couldn't." I then did an ls command in the terminal on the Music folder and it listed all the files, among them an index.php file. When I tried to edit this file, it said I was editing a new file. So then I went back to my file browser (Dolphin) and checked and there was no index.php file showing up. I thought maybe it's hidden somehow even though there's no . in front of the filename. Showing the hidden files did nothing as it still didn't show up. I then tried deleting the file and it said the file didn't exist. Yet everytime I do ls /media/disk/Music/ it comes up with an index.php in there. Finally I tried to change the permissions of Music and all of its contents. It changed what it could but returned the following 3 errors. One of which is on the supposed index.php file.

chmod: cannot access `/media/disk/Music/index.php': No such file or directory
chmod: cannot access `/media/disk/Music/images': No such file or directory
chmod: cannot access `/media/disk/Music/upload.php': No such file or directory

Seems all 3 of these files are in the same boat as index.php. I don't know what the heck is going on here, and I would really appreciate any advice on how to fix this.

Thanks!

---

### Post by talsemgeest on 2009-09-19
Please remember to use a descriptive topic title, I couldnt make heads or tails of your one. :)

---

