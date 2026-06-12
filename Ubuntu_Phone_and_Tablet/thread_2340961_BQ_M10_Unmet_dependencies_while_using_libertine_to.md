---
title: "BQ M10 Unmet dependencies while using libertine to install krita"
date: 2016-10-23
forum: Ubuntu Phone and Tablet
---

### Post by 243750496 on 2016-10-23
after the breaked installation of krita on tablet all app can't install correctly , all shows up apt-get -f install,when i tried sudo apt-get -f install nothing happened 
so how to slove the[B] Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
[/B]is there some similar commond like apt-get -f install in libertine???thx!

```
phablet@ubuntu-phablet:~$ libertine-container-manager install-package -i myapps -p krita
Reading package lists... Done
Building dependency tree       
Reading state information... Done
krita is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 calligraplan : Depends: calligra-libs (= 1:2.9.2-0ubuntu2) but it is not going to be installed
 krita : Depends: calligra-libs (= 1:2.9.2-0ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
phablet@ubuntu-phablet:~$ 


```
```
phablet@ubuntu-phablet:~$ libertine-container-manager install-package -i myapps -p blender
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 blender : Depends: blender-data (= 2.72.b+dfsg0-3build1) but it is not going to be installed
           Depends: fonts-droid but it is not going to be installed
           Depends: libjs-jquery-ui but it is not going to be installed
           Depends: libavcodec56 (>= 6:11~beta1) but it is not going to be installed or
                    libavcodec-extra-56 (>= 6:11.2) but it is not going to be installed
           Depends: libavdevice55 (>= 6:11~beta1) but it is not going to be installed
           Depends: libavformat56 (>= 6:11~beta1) but it is not going to be installed
           Depends: libavutil54 (>= 6:11~beta1) but it is not going to be installed
           Depends: libboost-locale1.55.0 but it is not going to be installed
           Depends: libglew1.10 (>= 1.10.0) but it is not going to be installed
           Depends: libopenal1 (>= 1.14) but it is not going to be installed
           Depends: libopencolorio1 but it is not going to be installed
           Depends: libopenimageio1.4 but it is not going to be installed
           Depends: libpython3.4 (>= 3.4.2) but it is not going to be installed
           Depends: libsdl1.2debian (>= 1.2.11) but it is not going to be installed
           Depends: libswscale3 (>= 6:11~beta1) but it is not going to be installed
 calligraplan : Depends: calligra-libs (= 1:2.9.2-0ubuntu2) but it is not going to be installed
 krita : Depends: calligra-libs (= 1:2.9.2-0ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
phablet@ubuntu-phablet:~$ 


```

```
phablet@ubuntu-phablet:~$ sudo apt-get -f install
[sudo] password for phablet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
phablet@ubuntu-phablet:~$ 


```


 By the way how to add ppa to my  tablet  by using some function in  libertine  to get latest dailybuild version of software

---

