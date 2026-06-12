---
title: "Need help with ffmpeg installation"
date: 2009-09-22
forum: Ubuntu Studio
---

### Post by zelalem on 2009-09-22
Hi all, I am using Ubuntu Hardy. After I installed all the dependencies and ffmpeg, I got a problem of running. Initially the error was "ffmpeg: error while loading shared libraries: libavformat.so.52: cannot open shared object file: No such file or directory." After following the thread at [http://ubuntuforums.org/showthread.php?t=903103](http://ubuntuforums.org/showthread.php?t=903103), I solved the problem using the follwoing command
           export LD_LIBRARY_PATH=/usr/local/lib/
           
 But it is not long lasting solution. Each time i close my terminal and open again the problem comes. There is also another lasting solution (the last comment by verysimple) on the same thread but then I got the following error:
 "ffmpeg: symbol lookup error: ffmpeg: undefined symbol: sws_getContext"

But again the above export command still solves the problem. So, what shall I do to fix this problem.

Thank you,.

Zelalem

---

### Post by stumbleUpon on 2009-09-22
I have never had this problem with ffmpeg.

Anyway just put

```
 export LD_LIBRARY_PATH=/usr/local/lib/ 
```

at the end of your .bashrc file (located in your home folder). You can open the .bashrc file with any text editor. Save the file and close it after adding the above line, and then do

```
source ~/.bashrc 
```

This will make sure that the LD_LIBRARY_PATH variables is set to /usr/local/lib/.

---

### Post by zelalem on 2009-09-22
Hi StumbleUpOn, yes it has solved my problem. 

Thank you very much.

Best regards,

Zelalem

---

### Post by FakeOutdoorsman on 2009-09-22
I recommend the following guide when installing FFmpeg on Ubuntu.  It is well tested and kept up to date.  Admittedly, I am tooting my own horn here.

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by zelalem on 2009-09-23
Hi FakeOutdoorsman, thank you for the great work. It is a very nice guide.

Best regards,

Zelalem

---

### Post by hellocatfood on 2009-12-22
Thanks guys, the solution at the top worked well for me!

---

