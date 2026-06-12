---
title: "kpovmodeler acting up in Interpid. KDE4 issue?"
date: 2008-11-02
forum: Ubuntu Studio
---

### Post by Oswald1 on 2008-11-02
Cheers all,

Any ideas what's going on? Yesterday I upgraded to Interpid Ibex and afterwards my Kpovmodeler looks like this:

[img]http://alku.org/images/kpm1.png[/img]

when it's supposed to look something like this:

[img]http://alku.org/images/kpm2.png[/img]


The biggest problem is that the black screens showing different wirefreame views of the model are and stay just blanl, but the whole layout of the thing is messed up too and I cannot even properly use some of the stuff popping up under the icons' menus.

Does this have something to do with the KDE3->KDE4 transition. Kpovmodeler has a transitional kde4 package which I installed, to no avail.

Thanks for any help!

p.s. I'm using Ubuntu and not Kubuntu if that's of any help.

---

### Post by sablobsimus on 2009-03-31
I'm looking for help with the same issue.

---

### Post by BCtom on 2009-04-01
Oh BOO! This does look like an issue with Intrepid and KDE4. Everything was working find last night until I closed KpovMoldeler, and that's when it quit working properly. 

Symptoms: When I open the GUI, the window covers the entire screen rendering my desktop useless. Also, it seems to kill X, not even Ctrl+Alt+F1 gets me out, only a complete reboot. 

I guess I'm going to try and revert back to KDE3. I really like KpovModeler because of the GUI, but I also like Intrepid too. Oh well, I'll keep on searching for PovRay Utopia.

---

### Post by BCtom on 2009-04-04
Well, I still need help with KpovModeler.

Here's what I've done so far....

At first when I had KPovModeler-KDE4 loaded from the repositories, I could create a scene, but once I saved it and then reopened it, the window would disappear and Kpov would cover the entire screen. Same problem that I mentioned before. So I decided to go into ".KDE/Share/config/kpovmodelrrc" and erase it. That made opening the previous file work semi-normal.

My ongoing issue is that I cannot save the image once I render it. I keep getting the error, "Unknown Image Format. Please Enter a Valid Suffix." I've tried all of the image options to save the render but none work.

I Uninstalled KpovModeler -KDE4 and just left the Ubuntu Approved KpovModeler from the repositories, but that doesn't seem to help. However, the window doesn't freeze up on my screen any more. 

Has anyone else experienced this, and some how fixed this problem?

Also, where can I get a copy of the Older version of Kpov? I've look at the old repositories and it seems to have been expunged from everything. At least that version worked.

---

### Post by cnewswanger on 2009-04-11
I have seen the same issues.  The menues can be streched and moved around to get them the way you want them.  Saving from the render window comes up with an error:

Unknown image format.
Please enter a valid suffix.

I never saw the missing wireframe issue.

I am running Ubuntu Studio 8.10 on a Dell inspiron 1420. (Intel core duo) with nvidia graphics

I have been using Kpovmodeller for years due to its simplicity and direct modelling using the pov primitives rather than meshes.  

Hope this gets figured out.

---

### Post by Oswald1 on 2009-04-21
Cheers all.

It seems that the missing wire frame issue is display driver related. Another problem with my system kinda helps me. Namely, I need to run nvidia-settings after log in to load the settings I have there. However if I don't load the settings, I do get the wire frames. Otherwise I need to log out/in. Must be some more specific setting there, but I haven't had time to investigate this in more depth.

Coming to the image saving problem. I made a quick and dirty patch in the source to circumvent this problem. For some reason the file extensions don't get recognized in qt. I implemented a simple string to string comparison, which only accepts png and jpg. Well, this IS quick and dirty, but at least I can now save the renders.

Also there is a bug I fixed, that prevents you from using for example previously defined textures as prototypes (the OK button doesn't get enabled). I informed the developer of KPM of the issue, but like he states on his homepage, he doesn't sadly have the time to upkeep the app and is looking for a new maintainer.

Anyhow, if someone is interested in my patches, drop me a pm or whatnot.

---

### Post by BCtom on 2009-04-21
Hey Oswald1,

> **Oswald1 said:**
> Cheers all.

Coming to the image saving problem. I made a quick and dirty patch in the source to circumvent this problem. For some reason the file extensions don't get recognized in qt. I implemented a simple string to string comparison, which only accepts png and jpg. Well, this IS quick and dirty, but at least I can now save the renders.


Anyhow, if someone is interested in my patches, drop me a pm or whatnot.

I would be very interested in your patch for the image file extension problem. This is my main key issue with Kpovmodeler at the moment. Could you post it here, or a link to it--maybe a how-to, also? 

Tom

---

### Post by Oswald1 on 2009-04-21
Well here it is. Didn't occur to me to attach it here :roll: Had to rename the .diff to .txt for uploading, but that shouldn't matter...

Both of my fixes are included. The other one (realted to prototype selection) is a pretty obvious bug and fix, so shouldn't hurt anyone to apply it.

(For anyone reading and not familiar with compiling stuff: This patch needs to be applied to the source code and kpm needs to be compiled afterwards. :) )

e: It is pretty straight forward to add different accepted image-formats to the patch, but please note that you have to make sure qt supports them.

---

### Post by BCtom on 2009-04-29
Hey Oswald,

> **Oswald1 said:**
> (For anyone reading and not familiar with compiling stuff: This patch needs to be applied to the source code and kpm needs to be compiled afterwards. :) )

e: It is pretty straight forward to add different accepted image-formats to the patch, but please note that you have to make sure qt supports them.

I tried, but to no avail could I get Kpovmodeler to accept your patch and fix the image format problem. I compiled it, but nothing came up--not even any warnings. Maybe if you could make a step by step procedure of what you did to get your patch to work that would be a great help? 

Also, could it be possible to just insert it somewhere in the root directory so that Kpovmodeler can use it instead without the need to recompile?

In the mean time I'm using Kpovmodeler to create scenes, export it to a povray script, then using the commandline scripts to render it into the proper image formats I want. I'm actully ready to move away from KDE for a while till they fix all their bugs. But things are working, but not the way I would like them to, but at least I can create PovRay scenes notheless.

---

### Post by Oswald1 on 2009-04-30
Hi BCtom,

I have no idea how to apply to this patch without recompling. Perhaps making an .deb of my own or something, but I have no experience with that.

Here's the steps to make it work though:



To get the latest svn snapshot create some working directory (e.g. ~/src and cd in there):
```
svn checkout svn://anonsvn.kde.org/home/kde/trunk/extragear/graphics/kpovmodeler
```

Alternatively you can get the latest source package from kpovmodeler's homepage, but I don't know how many changes there are in the svn.

Next copy my patch there (in the working directory src/ and not src/kpovmodeler/) and apply it with
```
patch -p0 < kpm_patch.txt
```

Next you run cmake, to check for what is needed by
```

cd kpovmodeler
cmake .
```
After this command you get a long list of tests and if something vital is missing install it (via synaptic for example).

When you have completed cmake with no critical errors, compile everything with
```
make -j4
```
(-j4 makes use of multiple cores if you have such hence speeding up the process).

Finally use (uninstall kpm if you have it installed through synaptic or what not)
```
sudo make install
```
to get everything in place.

Writing
```
kpovmodeler
```
should run your new patched thing now.

Hopefully there weren't too many missteps there:) Good luck!

---

### Post by MrGump on 2009-06-23
> **Oswald1 said:**
> 
When you have completed cmake with no critical errors, compile everything with
```
make -j4
```(-j4 makes use of multiple cores if you have such hence speeding up the process).

  When I get to this point my computer tells me that it cannot find the make file.

---

### Post by Oswald1 on 2009-06-23
Just shooting air here, but I would suspect that cmake found some problem like a missing package and didn't finish during the previous step.

---

### Post by gmt2027 on 2009-09-07
I got the wireframe views by running kpovmodeler in fluxbox rather than kde4 but for some strange reason it failed to work the next time I tried.

---

### Post by HaakonME on 2009-12-01
I use Kubuntu 9.10 Netbook remix. I installed all three kdevelop packages, qt4opengl-dev and subversion using KPackageKit. Use sudo apt-get install kdevelop* qt4opengl-dev subversion from the command line if you prefer. Either way, the package manager will automatically add all dependencies for you. I then followed Oswald1's instructions and everything went well. I tried to do the same in kdevelop, adding the kpovmodeler directory as a project, _removing_ the auto-suggested "build" subdirectory from the cmake settings so that kdevelop could find the makefile in the kpovmodeler directory, and it went well. Time permitting, I'll write step-by-step instructions at [http://far.no/fram/index.php?title=Kpovmodeler](http://far.no/fram/index.php?title=Kpovmodeler)

Cheers,
Haakon

---

