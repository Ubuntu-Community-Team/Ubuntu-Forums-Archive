---
title: "How to Hack Unity 3d"
date: 2012-08-29
forum: Tutorials
---

### Post by josephmills on 2012-08-29
This is going to be a small tutorial on how I hack away at Unity 3d. 
Before reading this I must say that there are many ways to skin a cat. Meaning that I am sure that there are other ways of doing this but , that being said this is how I do it. 

Things that you are going to need 
some C++ 
Qt Creator 

This is the C++ /qt / Awesome IDE that I will be using for this tutorial. You can install it via sotware center or 
```
sudo apt-get install qtcreator
```

Next we are going to need all of Unity's and Nux's dependency's 
so 

```
sudo apt-get build-dep unity && sudo apt-get build-dep nux
```

It is imorant that I mention that I am going to be building this out of the directory 
```
~/Desktop
```
so 
```
cd ~/Desktop 
```

Next we need The source code for Unity its self there are a couple of ways of doing this. I just say gather with  apt
make sure you are still located at ~/Desktop
```
apt-get source unity
```

Once that is downloaded you should get a folder That is like this. 
```
unity-6.2.0+bzr2635ubuntu0+762
```


Now lets make are build dir so in terminal
```
mkdir ~/Desktop/unity-6.2.0+bzr2635ubuntu0+762[COLOR="Red"]-build[/COLOR]
```

make sure that it is the same name so if you source code of unity is 

```
unity-6.2.0+bzr26[COLOR="red"]22[/COLOR]ubuntu0+762

```
make sure that it is 

```
unity-6.2.0+bzr26[COLOR="red"]22[/COLOR]ubuntu0+762[COLOR="red"]-build[/COLOR]
```


Now it is time too open qtcreator 

Once qtcreator is open go to 

File-->Open FIle or Project

then open 

~/Desktop/unity-6.2.0+bzr2635ubuntu0+762/CMakeList.txt


[img]http://ubuntuforums.org/attachment.php?attachmentid=223363&stc=1&d=1346261476[/img]



You should get a screen that looks like this 


[img]http://ubuntuforums.org/attachment.php?attachmentid=223364&stc=1&d=1346261476[/img]



Make sure that you add the -build on at the end if it is not there already. Then press Next 

Next you will get the Cmake options for now sense we are going to be building to are unity-6.2.0+bzr2635ubuntu0+762-build. we do not have to add any arguments. So just press Run Cmake.
after cmake runs just press the Finish button.


[img]http://ubuntuforums.org/attachment.php?attachmentid=223365&stc=1&d=1346261476[/img]



If you are getting errors make sure that you ran the build-deps above.  
 

All right Now it is time to start Hacking away at unity. 
for purposes of this tutorial I am only going to get into changing a icon size at the bottom of the dash.(your lens icons)

to do this we go to dash-->LensBarIcon.cpp

Lines 33 and 34 might look like this. 
```

const int FOCUS_OVERLAY_HEIGHT = 44;
const int FOCUS_OVERLAY_WIDTH = 60;

```

Lets make them look like this 

```

const int FOCUS_OVERLAY_HEIGHT = 64;
const int FOCUS_OVERLAY_WIDTH = 64;

```

then go down to line 41 it should look like this 

```
 : IconTexture(icon_hint, 24)
```

Lets change that to 
```
 : IconTexture(icon_hint, 48)
```


[img]http://ubuntuforums.org/attachment.php?attachmentid=223366&stc=1&d=1346261476[/img]





Now lets save are work. (ctrl+s) or go to File->Save

Now this next part is only included with Unity 6.2 and up. 

we go to the thing that looks like a monitor that is above the green arrow then we set are running point to be 

Unity-Standalone



[img]http://ubuntuforums.org/attachment.php?attachmentid=223367&stc=1&d=1346261476[/img]





then we press the run button or press ctrl+r  and we wait for it to build. Once it is build it will launch Unity-Standalone

[img]http://imagebin.org/226348[/img]

Now that you have previewed your changes you can go back to qtcreator and stop it from Running 



[img]http://imagebin.org/226347[/img]



Once you like whatt you got and you want to replace the stock Unity with what you have just built 
remove old unity. 
```
sudo apt-get remove unity 
```
and back in qtcreator
Go to Build-->Run Cmake and this time in the option's add 
```
-DCMAKE_INSTALL_PREFIX:PATH=/usr
```
and Click Run Cmake. after that runs. It is now Build your unity .
press ctrl+b and it will build your unity. 
then in the terminal go to 
  
```
cd ~/Desktop/unity-6.2.0+bzr2635ubuntu0+762-build 
```
then run 
```
sudo make install
```


reboot and enjoy your new Unity. Hope you enjoyed reading this.

---

### Post by daslinkard on 2012-09-21
Good job! I enjoyed reading this and will be attempting it in the future!

---

### Post by tumutanzi.com on 2012-09-21
I do not use Unity any. Still using Gnome2.

---

### Post by MG&amp;TL on 2012-09-21
Two things: 

```
bzr branch lp:unity
```

will get the most up-to-date revision in the upstream source. 

You shouldn't have to "remove old unity" - simply overwriting the files should work great. :)

Other than, great. I'm looking forward to it.

---

### Post by vexorian on 2012-09-22
```
sudo checkinstall
```
Might be better, as you will be able to remove the package to uninstall it.

--
Howto needs before and after pics.

Actually, making those icons larger seems like a good idea. May try to follow this tutorial to make it a configurable option.

---

### Post by asuastrophysics on 2013-07-02
Is it possible to change the position of the unity dock through various edits in the QT editor?

---

### Post by asuastrophysics on 2013-07-03
It's okay if there isn't currently. I was just asking. Great tutorial, btw OP. If such fields don't exist in the code, I may have to add the methods and method calls in myself to accomplish this. Knowing the inner workings of Unity will help me to create a version of it that can be placed on the bottom of the screen again - like what was done back in Ubuntu 11.04 and 11.10. :p

---

### Post by asuastrophysics on 2013-07-13
Bump.

---

