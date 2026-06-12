---
title: "Installing Kdenlive 0.7 Beta1"
date: 2008-10-11
forum: Ubuntu Studio
---

### Post by lexen on 2008-10-11
Hey guys.  I have really been looking forward to the new release of Kdenlive and it just came out but I can't install it.

   You can get the program [_here_]("http://www.kdenlive.org/node/19") and they have a tutorial [_here_]("http://www.kdenlive.org/compile"), but I am still having a hard time.

   Here is how far I got:

 - I downloaded this [_package_]("http://sourceforge.net/project/downloading.php?group_id=46786&use_mirror=internap&filename=kdenlive-0.7beta1.tar.bz2&42043528") and extracted it to my home folder (/home/dell).
 - Then, I went to the folder in terminal ```
cd '/home/dell/kdenlive-0.7beta1'
```
 - Then I installed a program called Cmake 
```
sudo apt-get install cmake
```
 - I used Cmake 
```
cmake '/home/dell/kdenlive-0.7beta1/CMakeLists.txt'
```

   Everything went fine until that point, but then they ask me to do the "make" command I get this error:
```
make: *** No targets specified and no makefile found.  Stop.
```

   Can anyone tell me what I am doing wrong?



Thanks,
Lexen

---

### Post by TVMA on 2008-10-14
This worked fine for me:

1) Add a repo to your sources.list

    *

      echo deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main | sudo tee -a /etc/apt/sources.list 

2) Get a load of extra packages

    *

      sudo apt-get update && sudo apt-get install gtk-qt-engine-kde4 bzip2 kdebase kommander subversion g++ cmake pkg-config kdelibs5-dev libsdl1.2-dev libxml2-dev 

3) Make a new directory

    *

      mkdir kdenlive 

4) Move into the new directory

    *

      cd kdenlive 

5) Download the script

    *

      wget [http://www.kde-apps.org/CONTENT/content-files/85826-kdenlive_builder_wizard.kmdr.bz2](http://www.kde-apps.org/CONTENT/content-files/85826-kdenlive_builder_wizard.kmdr.bz2) 

6) Extract, rename and make executable the script

    *

      `bunzip2 85826-kdenlive_builder_wizard.kmdr.bz2 && mv 85826-kdenlive_builder_wizard.kmdr kdenlive_builder_wizard.kmdr && chmod +x kdenlive_builder_wizard.kmdr 

7) Sort out a path by typing:

    *

      export PATH=$PATH:/usr/lib/kde4/bin 

8) Run the script

    *

      kmdr-executor kdenlive_builder_wizard.kmdr 

9) follow the instructions on-screen. Press "Cancel" after success.

10) In file browser (nautilus) navigate to the /kdenlive directory which you created in step 3

11) click "kdenlive_start" and you are in business.

12) Use alacarte (sudo apt-get install alacarte) to add ~/yourpath/kdenlive/kdenlive_start to your menu.

---

### Post by lexen on 2008-10-16
Thanks TVMA, you got me a lot farther then I could have gotten on my own.  I'm afraid that I couldn't get it all the way working, it hangs on "building ffmpeg" and it won't move past it.  I think I am going to have to bring that up with the kdenlive people.

     I have made a .sh file that automates the steps you lined out.  All you have to do is type y when it asks you a question and it can get you to the gui installer.  Take a look.



Thanks a ton TVMA,
Lexen

---

### Post by nowardev on 2008-10-16
hey guys someone can help me ? 

i would like know if kdenlive_render 0.0.7  is changed... so i need to see a script and wesley file

 you could put 2 images and a transition effect among these 2 photos and then
export time line---> create a script

then of couse post here the script **and the file .wesley** (it has the same name of the script but with wesley extension)

thank you

---

