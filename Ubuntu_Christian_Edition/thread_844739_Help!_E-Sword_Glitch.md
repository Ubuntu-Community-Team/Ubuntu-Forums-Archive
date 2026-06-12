---
title: "Help! E-Sword Glitch"
date: 2008-06-29
forum: Ubuntu Christian Edition
---

### Post by PCWatson1 on 2008-06-29
Hello. This is my first post here so greetings to you all. I have been interested in switching from Windows to Ubuntu mainly because of Vista. The one thing that is holding me back is not being able to use E-Sword to its full extent. I finally got it installed and working via WINE, but when I try to type in a reference and hit search the program closes. When I navigate to the reference through the list I have no problems and all of the other features seem to work fine. Does anyone have any recommendations to fix this problem?
Thanks in advance.

---

### Post by david_kt on 2008-06-29
> **PCWatson1 said:**
> Hello. This is my first post here so greetings to you all. I have been interested in switching from Windows to Ubuntu mainly because of Vista. The one thing that is holding me back is not being able to use E-Sword to its full extent. I finally got it installed and working via WINE, but when I try to type in a reference and hit search the program closes. When I navigate to the reference through the list I have no problems and all of the other features seem to work fine. Does anyone have any recommendations to fix this problem?
Thanks in advance.

Could you try to follow below instruction to install e-sword:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

---

### Post by PCWatson1 on 2008-06-29
That was basically what I did but I had to add a couple of other dlls to the cfg list in WINE.

---

### Post by david_kt on 2008-06-30
> **PCWatson1 said:**
> That was basically what I did but I had to add a couple of other dlls to the cfg list in WINE.

What are the other dlls you need to add and why?

DK

---

### Post by PCWatson1 on 2008-07-01
Well the help thread that I found had the oleaut32.dll and the riched32.dll in the list to add to the exceptions menu in WINE cfg so I did. Doing that got me farther than any of my other attempts to get e-Sword running on my machine. I did try the method that you have posted and didn't really have any luck but that could have been due to an error that I may have made in the process, (I am very new to this whole Ubuntu/Linux thing). I would be willing to try your method again but the last time I tried doing an uninstall to start fresh I could not totally get rid of what I had. To fix the problem  I just reinstalled Ubuntu because I don't have any important information  to worry about (I am using an older machine for testing purposes so that I don't have to experiment on a primary when/if I totally change over). Thanks

---

### Post by david_kt on 2008-07-01
> **PCWatson1 said:**
> Well the help thread that I found had the oleaut32.dll and the riched32.dll in the list to add to the exceptions menu in WINE cfg so I did. Doing that got me farther than any of my other attempts to get e-Sword running on my machine. I did try the method that you have posted and didn't really have any luck but that could have been due to an error that I may have made in the process, (I am very new to this whole Ubuntu/Linux thing). I would be willing to try your method again but the last time I tried doing an uninstall to start fresh I could not totally get rid of what I had. To fix the problem  I just reinstalled Ubuntu because I don't have any important information  to worry about (I am using an older machine for testing purposes so that I don't have to experiment on a primary when/if I totally change over). Thanks

Look like you follow the help for older version of wine. To start a fresh wine, just delete the .wine folder (hidden folder) in your home directory.

If you want to follow the instruction I give, you do not need to remove anything as it will make a special bottle just for e-sword. Imagine the bottle as a separate computer running MS Windows, you can create many bottle for each application so as not to interfere with each other.

DK

---

### Post by PCWatson1 on 2008-07-01
So will having e-Sword already installed make any difference in how the new install goes? Sorry if I don't seem to be catching on very quickly. I'm a Windows child what can I say?  :(

---

### Post by david_kt on 2008-07-01
> **PCWatson1 said:**
> So will having e-Sword already installed make any difference in how the new install goes? Sorry if I don't seem to be catching on very quickly. I'm a Windows child what can I say?  :(

There is no difference.

DK

---

### Post by PCWatson1 on 2008-07-04
Okay. I think I may have found the problem. I was using Wine version .9.5.9. Do you think that could be making the difference? I have looked all over to try to get Wine 1.0 but I can't find it in my repositories.

---

### Post by david_kt on 2008-07-04
> **PCWatson1 said:**
> Okay. I think I may have found the problem. I was using Wine version .9.5.9. Do you think that could be making the difference? I have looked all over to try to get Wine 1.0 but I can't find it in my repositories.

Is it 0.9.59? That would depend on how you install it. I think for 0.9.59 you could follow the instruction on the link I give. Please let me know the result.

Are you using hardy? If you are using hardy, you could follow below instruction to upgrade to latest wine:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Or you could download manually from this link:

[http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.0.0~winehq0~ubuntu~8.04-1_i386.deb)

DK

---

### Post by PCWatson1 on 2008-07-04
I finally got everything working smoothly. I guess it finally just clicked. Thank you very much for the help, I really appreciate it.

---

