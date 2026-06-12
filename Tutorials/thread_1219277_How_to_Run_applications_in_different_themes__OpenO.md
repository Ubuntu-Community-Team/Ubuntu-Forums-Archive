---
title: "How to: Run applications in different themes / OpenOffice dark theme fix"
date: 2009-07-21
forum: Tutorials
---

### Post by kogger on 2009-07-21
I seem to be somewhat addicted to the SlicknesS-black theme, but one common problem with dark themes is that they often render certain programs virtually unusable (or at the very least, much more difficult to use), OpenOffice Writer being what prompted me to discover the fix for this as under the SlicknesS-black theme it is impossible to change the color of the text.

One fix was posted on the gnome-look website, but several comments were posted that it didn't work (which I can confirm; it really didn't work, not on my computer at least). I give that fix credit for pointing me in the correct direction, but ultimately a different technique was needed.

This howto isn't just for people having issues with dark themes, though. If you've ever wanted to run one application using a different theme than the rest of your system (or hell, choose a different theme for each application. Why not?), it's actually very easy.

The basic idea is to create an executable shell script that will override the program's launching script in order to call that script using the env command. For this howto I'll demonstrate how I used this technique to run OpenOffice using the SlicknessX theme (although any theme with a locatable gtkrc file will work).

Here we go.

**1)** First, find the exact location of the executable that calls the program that you want to theme. This can be done using the 'which' command. To find OpenOffice, you would type into the terminal: 'which ooffice'. This gave me the result '/usr/bin/ooffice'. So far so good.

**2)** Second, check on your PATH variable. For this to work you need to settle on using a directory that's higher up on the search path than the one where the executable currently resides (in this case, '/usr/bin'). You can see your current value for path by typing 'echo $PATH' into a terminal. To be higher up on the search path, the directory you want to use should be to the left of the one that contains the script's executable. I highly recommend creating a bin folder in your home directory and setting that as the top folder in the search path exactly for situations like these. To do that:

```
$ mkdir ~/bin
```

Close the terminal and open it again, then check on PATH by typing 'echo $PATH' again. If the first value isn't /home/YOUR_USERNAME/bin (my terminal automatically added my home bin folder to the path), you'll need to put it there manually by opening up .bashrc ...

```
$ gedit ~/.bashrc
```

... going down to the bottom of the page, and entering in this line:

```
export PATH=~/bin:${PATH}
```

Again, you can use any directory as long as it's higher up the search path than the program's executable, but the rest of this howto will assume that ~/bin is being used.

**3)** Okay, now we'll create the script that will override the program. To override OpenOffice's executable (/usr/bin/ooffice), create a file called 'ooffice' in ~/bin:

```
$ gedit ~/bin/ooffice
```

The actual script we'll put into this file is very simple, but we need some information first. Namely, decide on a theme to use, and then locate that theme's gtkrc file. Themes are usually installed in /usr/share/themes or ~/.themes. Open up the folder for the one you want, open up the 'gtk-2.0' folder, and make sure that a file called 'gtkrc' is in that directory. If it isn't, choose a different theme; if it is, remember its absolute path (in my case it's '/usr/share/themes/SlicknessX/gtk-2.0/gtkrc'). In addition to that you'll need the absolute path to your program's executable ('/usr/bin/ooffice'). Once you have that, put this in the 'ooffice' file we created:

```
#!/bin/bash
env GTK2_RC_FILES=/usr/share/themes/SlicknessX/gtk-2.0/gtkrc /usr/bin/ooffice "$@"
```

Since this technique can be used for any program, here's the basic format. Remember, the filename *must* be the same as the program's executable script (what you would type into the terminal to open it):

```
#!/bin/bash
env GTK2_RC_FILES=**PATH_TO_GTKRC** **PATH_TO_EXECUTABLE** "$@"
```

**4)** Last step: make our newly created script executable. To do that, simply type this into a terminal:

```
$ chmod +x ~/bin/ooffice
```

This step is extremely important, since without it our newly created script would be unable to execute.

Now every time you open OpenOffice (or whichever program you desire to theme), it will open in the chosen theme. If you want to undo this it's as simple as removing the script (rm ~/bin/ooffice).

Feedback is welcome. :)

---

### Post by Fancycakes on 2009-10-15
Your walk-through was clear and concise, but for some reason, OO isn't responding to the script. I am using the themes SlicknesS-black and Overglossed, which were made by the same person and have the same OO problems. I followed your instructions to the letter, however OO still doesn't have buttons, but text where the buttons should be.

I run the script and OO does come up, but in a rather basic mode. There are no toolbars open, nor can I enter any text. Knock on wood, there aren't any icons either.

I actually just tried SlicknesS and the buttons are working fine on that, but it always seems to be a problem with themes that have a black background.

If there's anything you might suggest, it'd be welcome.

---

### Post by undecim on 2009-10-16
I did this, but put mine in /usr/local/bin/instead of a folder in my home directory.

Using clearlooks, however, left my toolbars with the dark theme. Switching it to ThinIce fixed that though.

---

### Post by Hagar Delest on 2010-02-06
See that one (especially the end), it even brings back the default gray shading: [[Solved] OOO_FORCE_DESKTOP for dark themes]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=27216").

---

### Post by thaitang on 2013-03-10
> **kogger said:**
> I seem to be somewhat addicted to the SlicknesS-black theme,...Feedback is welcome. :)

I am not sure if there is another more mainstream fix for this problem since this post, but 3 years later and this fix worked like a charm for me. I am using Xfce-dusk on xubu. Thanks for the clear and easy-to-follow instructions.

---

