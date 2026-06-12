---
title: "Ubuntu Studio in Wubi?"
date: 2012-07-13
forum: Ubuntu Studio
---

### Post by cwfullerton21043 on 2012-07-13
How hard would it be to include Ubuntu Studio in the Drop down button in WUBI and have it install?  

I've searched this topic and found a number of posts asking about this in earlier versions..  I don't understand why it's not included,  I would have thought it would be a no brainer...

I'm not sure how much would be involved to add a way to include an iso that's already downloaded to install, but that would be nice...  

I would really like to run this next two Win7 and wubi is the easiest way to do this...

HELP please??

---

### Post by Cheesemill on 2012-07-14
You could always just install Ubuntu using Wubi and then install the Ubuntu Studio packages afterwards.

---

### Post by cwfullerton21043 on 2012-07-14
is there an easy way to get all the packages for Studio?  How hard is it to configure it the way Ubuntu Studio is set up?

---

### Post by Cheesemill on 2012-07-14
```
sudo apt-get install plymouth-theme-ubuntustudio ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-controls ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-font meta ubuntustudio-generation ubuntustudio-graphics ubuntustudio-icon-theme ubuntustudio-lightdm-theme ubuntustudio-live-settings ubuntustudio-look ubuntustudio-menu ubuntustudio-recording ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-video ubuntustudio-wallpapers
```

Will give you the exact Ubuntu Studio setup.

---

### Post by cwfullerton21043 on 2012-07-14
Ok.. I installed Ubuntu using Wubi.. I then ran that piece of code and got the following output... (also found what looked to be a typo.. corrected that and still had a problem)

*****
charlie@ubuntu:~$ sudo apt-get install plymouth-theme-ubuntustudio ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-controls ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-font meta ubuntustudio-generation ubuntustudio-graphics ubuntustudio-icon-theme ubuntustudio-lightdm-theme ubuntustudio-live-settings ubuntustudio-look ubuntustudio-menu ubuntustudio-recording ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-video ubuntustudio-wallpapers  
 [sudo] password for charlie:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 E: Unable to locate package ubuntustudio-font  
 E: Unable to locate package meta  
 charlie@ubuntu:~$ sudo apt-get install plymouth-theme-ubuntustudio ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-controls ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-font-meta ubuntustudio-generation ubuntustudio-graphics ubuntustudio-icon-theme ubuntustudio-lightdm-theme ubuntustudio-live-settings ubuntustudio-look ubuntustudio-menu ubuntustudio-recording ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-video ubuntustudio-wallpapers  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Some packages could not be installed. This may mean that you have  
 requested an impossible situation or if you are using the unstable  
 distribution that some required packages have not yet been created  
 or been moved out of Incoming.  
 The following information may help to resolve the situation:  
 

 The following packages have unmet dependencies:  
  ubuntustudio-default-settings : Conflicts: ubuntustudio-menu but 0.15 is to be installed  
 E: Unable to correct problems, you have held broken packages.  
 charlie@ubuntu:~$  
 *****

I really appreciate the help.. Could you tell me how to fix this?  Should I remove the menu from the list and install that separately after??  How to proceed??

---

### Post by cfhowlett on 2012-07-28
According to its developer, Wubi is a TESTING tool, it is NOT intended to be a long-term installation solution.  I strongly suggest you consider dual booting.

---

### Post by Frogs Hair on 2012-07-30
I agree with the previous post. The ubuntu-studio-desktop is in the repository, but the real time or low latency kernel won't be installed with it and you also end up a mix of applications. 12.04 has 5 year support so the time is right to dual boot if your interested in US.

Attempt to repair broken packages. ```
sudo apt-get -f install 
```  

If you want to get back where you started try reversing the command instead get install I inserted get remove. 

```
sudo apt-get remove plymouth-theme-ubuntustudio ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-controls ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-font meta ubuntustudio-generation ubuntustudio-graphics ubuntustudio-icon-theme ubuntustudio-lightdm-theme ubuntustudio-live-settings ubuntustudio-look ubuntustudio-menu ubuntustudio-recording ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-video ubuntustudio-wallpapers
```

---

