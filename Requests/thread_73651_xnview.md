---
title: "xnview"
date: 2005-10-09
forum: Requests
---

### Post by yesplease on 2005-10-09
xnview is an excellent image viewer, it is very good in enlarging pics (zoom in with good quality) and I find it useful for cropping images (to 4:3) and basic lossless Jpeg transformations. I know Gimp can do this and much more, but xnview is quick and clean. I used it a lot on winXP.

I hope somebody finds the time to put xnview in a repository as I do not know how to do this. Thanks in advance.

Edit: an rpm package of xnview can be downloaded here [http://www.xnview.com/](http://www.xnview.com/)

---

### Post by billyhb123 on 2005-10-10
I was able to get it installed.  What version of Ubuntu do you have?  I find xnview very helpful, especially the feature that allows multiple images to be formatted automatically.  Did you get it installed?  If not, here are the install directions that I used:

Go to this url and download the rpm version (XnView v1.70 + NView/NConvert v4.51):
[http://perso.wanadoo.fr/pierre.g/xnview/endownloadlinux.html](http://perso.wanadoo.fr/pierre.g/xnview/endownloadlinux.html)

Then when you have that downloaded, make sure that you have alien installed on your machine: sudo apt-get install alien

When that is complete, you would go to your download location for xnview and type the following: sudo alien -d XnView-static.i386.rpm  This will format the rpm file to a debian file.

Then you would need to install Xnview.  Type in this: 
dpkg -i xnview_1.70-2_i386.deb

Thats it!  Your done.  Now go alt-f2 and type in xnview and you should be able to have the program.

At least it works for me.

---

### Post by yesplease on 2005-10-10
Thanks for your instructions Billyhb123, they seem very clear and simple to me. 

I use hoary hedgehog now and will upgrade to breezy in about a week (when it is stable).

When I have tried your method I will report back, though I still think it is worthwhile to put Xnview in the repositories.

Edit: It installed with your instructions. (alien is already present in hoary).  Alt-F2 showed xnview in the list of programs (but only after a restart). Run XnView did not work because "there is no default action for xnview".  

Edit: XnView did not work in hoary hedgehog, but **it works now after upgrading to Breezy**.

Note that this linux version does not have all the feauteres that the windows version has, the author intends to change that in the long term.

Thanks again for your help.

---

### Post by dbloom on 2005-10-17
i upgraded to breezy over the weekend and retried installing xnview with no luck.

when i try 'xnview' in the console, i get "Command not found". when i try it with sudo, i get "xnview: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory".

any thoughts?

---

### Post by yesplease on 2005-10-19
Did you also try Applications, Graphics, XnView?

---

### Post by Oceola on 2005-10-19
I'd also like to see it added along with some of the scientific astronomy packages.
I tried the Xnview rpm install but it was a little buggy and seemed to not work completely. It may be it didn't get completely installed. I removed it but would like it back. It's worthwhile for the repositories as it would sit nicely between EOG and Gimp in capabilities.

Not trolling here but I used it under Windows and it was handy. I switched to Hoary Hedgehog exclusively and removed Windows from my machine. I'm using Gimp under 5.04 and it's really nice, but sometimes it's a little more than needed and the Xnview is just right. There were some metric to inch translation issues also. Some times the image would be 29 inches large or more. :smile: 

As far as the astronomy packs I'd like to see something which is a local solar system mapper/planetarium format, timed to current local or universal time which has events and location of planets, stars and deep space objects which updates either animated or by time through an update button. I've been looking for something like this but haven't seen anything. I had Cybersky under windows and it could be used as a guide.
:smile:

---

### Post by [eXr] on 2005-11-17
To all who have problems :confused:  installing XnView ([http://www.xnview.com)](http://www.xnview.com)).
I made the .deb packages with alien:
```
sudo alien XnView-static.i386.rpm
```
that generates a .deb package, installed with dpkg:
```
sudo dpkg -i xnview_1.70-2_i386.deb
```

Then I found 3 problems with my Ubuntu Breezy running XnView:
[LIST=1]
[*]**xnview command isn't in the path**

I don't have in the $PATH the path: **/usr/X11R6/bin**. To apply to all the users I've edited the **/etc/profile** file and added **:/usr/X11R6/bin** at the end of the $PATH string.
```
sudo nano /etc/profile
```

[*]xnview: error while loading shared libraries: **libXp.so.6**: cannot open shared object file: No such file or directory

All you need is "aptitude" the **libxp6** library
```
sudo aptitude install libxp6
```

[*]xnview: error while loading shared libraries: **libstdc++-libc6.1-1.so.2**: cannot open shared object file: No such file or directory

All you need is the **libstdc++6** library and a "fake" :-\"  soft link to the unknown library
```
sudo aptitude install libstdc++6
sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++-libc6.1-1.so.2
```
[/LIST]

Now all is ready! Enjoy XnView!

---

### Post by BLTicklemonster on 2008-05-19
Just making the deb using alien works great in gutsy if anyone wonders...

---

### Post by needageek on 2008-11-15
> **billyhb123 said:**
> I was able to get it installed.  What version of Ubuntu do you have?  I find xnview very helpful, especially the feature that allows multiple images to be formatted automatically.  Did you get it installed?  If not, here are the install directions that I used:

Go to this url and download the rpm version (XnView v1.70 + NView/NConvert v4.51):
[http://perso.wanadoo.fr/pierre.g/xnview/endownloadlinux.html](http://perso.wanadoo.fr/pierre.g/xnview/endownloadlinux.html)

Then when you have that downloaded, make sure that you have alien installed on your machine: sudo apt-get install alien

When that is complete, you would go to your download location for xnview and type the following: sudo alien -d XnView-static.i386.rpm  This will format the rpm file to a debian file.

Then you would need to install Xnview.  Type in this: 
dpkg -i xnview_1.70-2_i386.deb

Thats it!  Your done.  Now go alt-f2 and type in xnview and you should be able to have the program.

At least it works for me.
Almost got this to work,  I was able to install 'alien'.  This worked fine,  I downloaded XnView 'rpm' from the link.  Good so far,  But then the wheels fell off.
I tried the command line "sudo alien -d XnView-static.i386.rpm" this did not work ?
Maybe I have this wrong too, so I tried..."sudo alien -d XnView-static-fc4.i386.rpm"
This din't work either, I get this message back ?
sudo: unable to resolve host Computer1
File "XnView-static.i386.rpm" not found.
Why ? Please help ...

---

### Post by BLTicklemonster on 2008-11-16
You cd to the directory the file is downloaded to, right? Like if you downloaded it to your desktop, 

cd /home/needageek/Desktop

then 

sudo alien -d XnView-static.i386.rpm

Or compile from source.

download the tar gz, open with whichever archiver you use, and put it in your /home/yourname directory.

The do this in the terminal:


cd /usr/lib/X11/
sudo mkdir /usr/lib/X11/app-defaults
cd /usr/lib/X11/app-defaults
sudo mkdir /usr/lib/X11/app-defaults/XnView
cd /home/yourname/XnView
sudo sh install


Then type xnview to run it.

---

### Post by Steistas on 2009-08-13
Great posts everyone, was very helpful. First I was really struggling with install of xnview and was desperate to convert a batch of around 500 photos. But with the help of this thread everything's sorted.:)

---

