---
title: "Unity/compiz = dunzo!"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by The_Autonomist on 2012-04-17
Okay, i don't know what i did wrong...but something went wrong. Majorly. I did a pretty big update through Update Manager and I also used UbuntuTweak's Janitor to clean my computer of unwanted files. Everything was running just fine...then I logged out. Then, when i went to log back into Ubuntu...all i have is my wallpaper. No panel...no launcher. Just my wallpaper. 

I can log into Gnome just fine, BUT, Gnome isn't what it once was. Instead of the new Gnome 3, it looks like the Gnome Classic...even though i didn't log into Gnome classic. 

Anyways, in Gnome, i tried running unity --reset and this is what i got: 

> ebonilm@ebonilm-HP-Pavilion-dv6-Notebook-PC:~$ unity --reset
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1800004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1a00003

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1a00014

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3000025

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3600058

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3a00004

Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
compiz (core) - Warn: unhandled ConfigureNotify on 0x3c00090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3c00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3c00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3c00099!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3c0009c!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x3c0009f!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.


what is going on?????

---

### Post by grahammechanical on 2012-04-17
You could use the software Centre to check if you still have Compiz, Unity, Gnome Shell, etc., still installed.

You could also do this through the Synaptic Package Manager but you will have to install it first.

clearly some stuff has been uninstalled. A quicker but more painful method would be to re-install without formatting the partition.

Regards.

---

### Post by The_Autonomist on 2012-04-17
Believe me, one of the first things i did was to check Synaptic to see if Unity, Compiz, gnome-shell were still installed. They are. How do i get back all of that stuff that terminal says i'm missing??

---

### Post by tehowe on 2012-04-17
If you're using NVIDIA you should look at this thread

[http://ubuntuforums.org/showthread.php?t=1959416](http://ubuntuforums.org/showthread.php?t=1959416)

---

### Post by The_Autonomist on 2012-04-17
i'm not using Nvidia...:/

---

### Post by effenberg0x0 on 2012-04-17
```
cd /usr/lib && ls -la *GL*
``` 
...should output a series of soft-links, such as:
ahsl@HOME-OFFICE:/usr/lib$ ls -la *GL*
```
lrwxrwxrwx 1 root root      16 Aug  4  2011 libGLEW.so.1.5 -> libGLEW.so.1.5.2
-rw-r--r-- 1 root root  337808 Aug  4  2011 libGLEW.so.1.5.2
-rw-r--r-- 1 root root     654 Apr 16 10:21 libGL.la
lrwxrwxrwx 1 root root      10 Apr 16 10:21 libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root      15 Apr 16 10:21 libGL.so.1 -> libGL.so.295.20
-rwxr-xr-x 1 root root 1052240 Apr 16 10:21 libGL.so.295.20
```

When you install a VGA driver, this soft-links change to point to the installed driver lib*.so file. So, my questions would be:
- Do you have /usr/lib/libGL.so.1
- What is it pointing to?
- Is it a broken link (pointing to a non-existing file)?

And about Compiz, if you cd /usr/lib/compiz && ls -la lib*.so do you see the plugins there? (libresize.so, 
libgrid.so. libwall.so. libmove.so, etc)? Cause, if not, you might have to:
```
sudo apt-get install --reinstall compiz-plugins
```

Regards,
Effenberg

---

### Post by ventrical on 2012-04-17
> **The_Autonomist said:**
> Okay, i don't know what i did wrong...but something went wrong. Majorly. I did a pretty big update through Update Manager and I also used UbuntuTweak's Janitor to clean my computer of unwanted files. Everything was running just fine...then I logged out. Then, when i went to log back into Ubuntu...all i have is my wallpaper. No panel...no launcher. Just my wallpaper. 

I can log into Gnome just fine, BUT, Gnome isn't what it once was. Instead of the new Gnome 3, it looks like the Gnome Classic...even though i didn't log into Gnome classic. 

Anyways, in Gnome, i tried running unity --reset and this is what i got: 



what is going on?????

  I used the Janitor about 6 months ago on an experimental install using Ocelot. I was trying to save some space because it kept telling me I was out of hdd space so I ran it and I could not get back in. Only speaking for myself,  I decided to do a fresh install.

---

### Post by The_Autonomist on 2012-04-18
> **effenberg0x0 said:**
> ```
cd /usr/lib && ls -la *GL*
``` 
...should output a series of soft-links, such as:
ahsl@HOME-OFFICE:/usr/lib$ ls -la *GL*
```
lrwxrwxrwx 1 root root      16 Aug  4  2011 libGLEW.so.1.5 -> libGLEW.so.1.5.2
-rw-r--r-- 1 root root  337808 Aug  4  2011 libGLEW.so.1.5.2
-rw-r--r-- 1 root root     654 Apr 16 10:21 libGL.la
lrwxrwxrwx 1 root root      10 Apr 16 10:21 libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root      15 Apr 16 10:21 libGL.so.1 -> libGL.so.295.20
-rwxr-xr-x 1 root root 1052240 Apr 16 10:21 libGL.so.295.20
```

When you install a VGA driver, this soft-links change to point to the installed driver lib*.so file. So, my questions would be:
- Do you have /usr/lib/libGL.so.1
- What is it pointing to?
- Is it a broken link (pointing to a non-existing file)?

And about Compiz, if you cd /usr/lib/compiz && ls -la lib*.so do you see the plugins there? (libresize.so, 
libgrid.so. libwall.so. libmove.so, etc)? Cause, if not, you might have to:
```
sudo apt-get install --reinstall compiz-plugins
```

Regards,
Effenberg

Okay, i'm a little confused here. What am i supposed to type in terminal? i did what you said and got this: 

```
ebonilm@ebonilm-HP-Pavilion-dv6-Notebook-PC:~$ cd /usr/lib
ebonilm@ebonilm-HP-Pavilion-dv6-Notebook-PC:/usr/lib$ ls -la *GL*
ls: cannot access *GL*: No such file or directory

```

And i also reinstalled compiz plugins via terminal, but i still don't think it's working. 

HELP???? i neeed my Unity back....

---

### Post by The_Autonomist on 2012-04-18
162 people have looked at this...and no one can help me? 

can someone please help me? i can't do anything in unity or unity 2d!! they won't load at all

---

### Post by ranch hand on 2012-04-18
> **The_Autonomist said:**
> 162 people have looked at this...and no one can help me? 

can someone please help me? i can't do anything in unity or unity 2d!! they won't load at all
There is little to say after someone uses dodgy tools like computer janitor.  That is like swatting flies on a glass table top with a sledge hammer.

Gluing it all back together will take some doing.

Did you reinstall the compiz plugins as eff suggested?  And run the rest of the things he suggested.  That is really the very best thing you can do to get started at attempting to fix this.

With out doing that there really is nothing more that can be said except the comment by 
ventrical in post #7.

There really is no fairy god mother on here.

---

### Post by The_Autonomist on 2012-04-18
yes i did what he said, i posted above what happened when i did. nothing happened. i didn't get the same output that he received in terminal. 

i have to do a fresh install? several other people on these forums have had this exact same issue and somehow got it resolved but no one will tell me HOW

---

### Post by effenberg0x0 on 2012-04-18
Well, this won't be a small answer. 

Basically you can think of OpenGL as sort of a standard for developing "hardware accelerated" graphics. Hardware accelerated graphics are faster and allow for more things than "software accelerated" graphics. Some VGA Cards support, among other of those "standards", OpenGL. Some do not. They can support different versions of it, correctly or incorrectly, completely or partially, with a good or poor performance. It all depends on the hardware, version and quality of the implementation. 

Compiz is a "compositing window manager". Think of it as something that makes the interface between the desktop core and your applications, but relying on OpenGL features (which is why Compiz has plugins, effects, etc).

Unity (the launcher, the dash, etc) is implemented as a Compiz plugin.

[LIST]
[*]In order to have Unity, you need Compiz. 
[*]In order to have Compiz, you need OpenGL. 
[*]In order to have OpenGL, you need to install proper drivers and the correct Kernel module for you VGA card. 
[*]You might also need Mesa. It is a package that contains files for the OpenGL implementation.[/LIST]
One thing is on top of the other.

- Having those set, you need to make sure that Compiz is properly installed, as well as it's plugins.

- On top of all that, you need to check if Unity packages and all of its dependencies are correctly installed.

- And, to conclude, some settings files stored in your home directory must exist, be correct and have the right ownership and permissions, so they can be read by Unity and Compiz. And, also in that line, we sometimes see situations in which ownership and permissions for other vital system folders or even the whole system are incorrect.

So, you see, it's not something easy to troubleshoot remotely. All that is done automatically when one installs and properly upgrades Ubuntu. We could go on debugging these thing but it could take a lot of time. On the other hand, inserting Ubuntu CD/DVD/USB and re-installing it will take minutes and most likely fix everything.

I think it's your best bet.

OBS: This explanation is deliberately wrong and incomplete, to avoid complexities. It's a simplification.

Regards,
Effenberg

> **The_Autonomist said:**
> Okay, i'm a little confused here. What am i supposed to type in terminal? i did what you said and got this: 

```
ebonilm@ebonilm-HP-Pavilion-dv6-Notebook-PC:~$ cd /usr/lib
ebonilm@ebonilm-HP-Pavilion-dv6-Notebook-PC:/usr/lib$ ls -la *GL*
ls: cannot access *GL*: No such file or directory

```

And i also reinstalled compiz plugins via terminal, but i still don't think it's working. 

HELP???? i neeed my Unity back....

---

### Post by effenberg0x0 on 2012-04-18
Question to all: How should we proceed to get Computer Janitor off Ubuntu repos? We see people having important stuff deleted for some cycles already. It does no good to have it there. No prob with the developer having it on a PPA anyway.

Regards,
Effenberg

---

### Post by The_Autonomist on 2012-04-18
i don't see why everyone is telling me to erase everything and start over when other people got this same issue resolved. 

is there a way to reinstall 12.04 without wiping all of my <stuff>

---

### Post by alphacrucis2 on 2012-04-18
> **effenberg0x0 said:**
> Question to all: How should we proceed to get Computer Janitor off Ubuntu repos? We see people having important stuff deleted for some cycles already. It does no good to have it there. No prob with the developer having it on a PPA anyway.

Regards,
Effenberg

Is the janitor function in Ubuntu-tweak the same thing as the old bug ridden "computer janitor" program? I didn't think it was. I read the OP as saying that the problem was caused by Ubuntu-tweak. If so then the issue should be raised with the ubuntu-tweak author.

---

### Post by effenberg0x0 on 2012-04-18
> **alphacrucis2 said:**
> Is the janitor function in Ubuntu-tweak the same thing as the old bug ridden "computer janitor" program? I didn't think it was. I read the OP as saying that the problem was caused by Ubuntu-tweak. If so then the issue should be raised with the ubuntu-tweak author.

Hi alphacrucis, I have no idea. I've seen people reporting problems about Computer Janitor, and always assumed they're talking about the computer-janitor package. This one is known to be harmful. But I have never used Ubuntu Tweak and can't say much about it.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-04-18
> **The_Autonomist said:**
> i don't see why everyone is telling me to erase everything and start over when other people got this same issue resolved. 

is there a way to reinstall 12.04 without wiping all of my butterflies?

Run the installer. I think Ubuntu will ask you if you want to keep your files. Your home content will be preserved, as well as programs settings. Programs will have to be reinstalled. But this is not like other OSs. A install of Ubuntu and programs doesn't take long.

Regards,
Effenberg

---

### Post by The_Autonomist on 2012-04-18
how do i run the installer? O_O

---

### Post by The_Autonomist on 2012-04-18
does anyone know how to reinstall 12.04 from inside of 12.04?????

---

### Post by The_Autonomist on 2012-04-18
I fixed it myself. Hours of googling, and typing hordes of random crap into terminal fixed the issue. apparently purging compiz core, unity, and then doing this: 

> ~$ sudo apt-get purge xorg-driver-fglrx
~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
~$ sudo dpkg-reconfigure xserver-xorg
~$ sudo apt-get install --reinstall xserver-xorg-core

did the trick. and i did NOT have to completely fresh install ubuntu. -__-

---

### Post by grahammechanical on 2012-04-19
> **The_Autonomist said:**
> I fixed it myself. Hours of googling, and typing hordes of random crap into terminal fixed the issue. apparently purging compiz core, unity, and then doing this: 

did the trick. and i did NOT have to completely fresh install ubuntu. -__-

Well done you! Now, you have learned a couple of things.

1) Only you can fix your system when you have done something to mess it up.

2) Not to expect other people to have a simple answer ready and waiting. Apparently it is often necessary to do just this:

> Hours of googling, and typing hordes of random crap into terminal fixed the issue.

3) Not to run an OS cleanup utility on a development branch because there are many libraries that need replacing but first the replacements have to be put in place. The cleanup utility took out those libraries but it was not capable of replacing them. Better to let Update Manager do it when it is ready to do it.

4) It is your choice to spend all those hours googling and typing random ****. Me? I would just install. It is a lot less painful and quicker.

---

### Post by The_Autonomist on 2012-04-19
In case you missed above, i was asking for HELP on HOW to install but no one replied. i was ignored. therefore, i had to do hours of googling. yeah, a "quick' install would have been painlessm but considering the fact that i have no cds and couldn't find an iso file for a usb, no one would help me when i asked how to do it from inside ubuntu. 

so no, it wasn't my choice to spend hours on google.

---

### Post by ventrical on 2012-04-19
I tired to share my own personal experience with this situation. I do not think people were ignoring you at all.

 My apologies if you feel you have been dissed. It was not meant in that spirit.

---

### Post by The_Autonomist on 2012-04-19
all's good. no need for an apology, ventrical! your response was appreciated. regardless of how, the issue has now been resolved.

---

### Post by balloons on 2012-04-19
> **effenberg0x0 said:**
> Question to all: How should we proceed to get Computer Janitor off Ubuntu repos? We see people having important stuff deleted for some cycles already. It does no good to have it there. No prob with the developer having it on a PPA anyway.

Regards,
Effenberg

Computer Janitor is gone as of 11.10:

[http://www.omgubuntu.co.uk/2011/05/app-changes-for-ubuntu-11-10-so-long-computer-janitor-hello-deja-dup/](http://www.omgubuntu.co.uk/2011/05/app-changes-for-ubuntu-11-10-so-long-computer-janitor-hello-deja-dup/)

Additionally, this sounds like someone used ubuntu-tweak which is also not on the default install. These tools can be dangerous to an unsuspecting user (not unlike similar tools on other OS's). I think removing computer janitor from the default cd was the right idea, but we can't do much about post-installation use besides filing bugs with those tool authors and asking for them to better safeguard/warn users if necessary.

---

### Post by ventrical on 2012-04-19
> **guitara said:**
> Computer Janitor is gone as of 11.10:

[http://www.omgubuntu.co.uk/2011/05/app-changes-for-ubuntu-11-10-so-long-computer-janitor-hello-deja-dup/](http://www.omgubuntu.co.uk/2011/05/app-changes-for-ubuntu-11-10-so-long-computer-janitor-hello-deja-dup/)

Additionally, this sounds like someone used ubuntu-tweak which is also not on the default install. These tools can be dangerous to an unsuspecting user (not unlike similar tools on other OS's). I think removing computer janitor from the default cd was the right idea, but we can't do much about post-installation use besides filing bugs with those tool authors and asking for them to better safeguard/warn users if necessary.


Thanks for this update guitara.. this is really helpful.

---

### Post by swright007 on 2012-04-20
I don't believe it was your cleanup utility.  This happened to me and I don't use a cleanup utility... It seems to occur during an update if you are using either (or both) Fallback mode or auto-login.  Just a pattern with the "nothing but desktop" thing going on.

---

