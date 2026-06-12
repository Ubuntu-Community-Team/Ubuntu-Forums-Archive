---
title: "Black screen on initial login"
date: 2013-04-26
forum: System76 Support
---

### Post by volkerbradley on 2013-04-26
Just performed a fresh install of 13.04 on my 64-bit Serp6
My NVIDIA driver version is 304.88
On logging in, I see the launcher and the panel. The rest of the screen is black.
Is this normal behavior now?  Or should I be changing a specific setting?
If you would like to see what I am seeing, go to:
[http://www.youtube.com/watch?v=hLe_2v-Be_I&feature=youtu.be](http://www.youtube.com/watch?v=hLe_2v-Be_I&feature=youtu.be)

---

### Post by ssanders47 on 2013-04-26
I've got a bonp5 and am having a similar problem.  I've also noticed that the notifications tend to appear and not disappear.  Also, the top upper left hand corner which shows the name of the currently selected application but does not always change when the application terminates.

---

### Post by isantop on 2013-04-26
Try using the Driver version 310. It's the currently supported version.

Also, what happens if you open the Home Folder? Can you set a desktop background?

---

### Post by volkerbradley on 2013-04-26
I have updated the NVidia driver.  The main screen remains black except for the launcher and panel.
If I click on the Files icon in the Launcher and then choose Files, I am taken into the Home folder.  I can see things normally
If I click on System Settings -> Appearance ->  Look Tab, I can choose the background image.
However, the main screen remains black until I open the Tweak Tool and click on Desktop -> Have file manager handle the desktop -> ON
Interestingly, others are complaining of this behavior.

---

### Post by ssanders47 on 2013-04-27
Here's what I did that (eventually) worked for me :
 
1. Reinstall Ubuntu 13.04 cold - no luck.
2. Move my home directory out of the way, something like mv /home/sanders /home/sanders.orig
3. Delete and re-create my user account via user admin tool.
4. Move everything from /home/ssanders.orig to /home/ssanders EXCEPT the hidden files, i.e., files whose names start with a '.'
5. Profit

Apparently, there is a hidden configuration file that messes Unity (I'm guessing) up.  I haven't bothered to run it down more than that.

---

### Post by volkerbradley on 2013-04-28
This is very helpful.  It lets us know how to proceed.
Thank you very much.

---

### Post by volkerbradley on 2013-04-28
Did you encrypt your hard drive by chance?  Since not many people are seeing this problem, perhaps there is something that was done during the installation that caused this.

---

### Post by ssanders47 on 2013-04-28
I'm not using encryption on my drives. I can't think of anything I'm doing that isn't straight out of the Ubuntu repository other than the System76 stuff.

---

