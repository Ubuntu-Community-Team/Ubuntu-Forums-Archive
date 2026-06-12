---
title: "e-Sword and Kubuntu: Quite easy under dual boot."
date: 2007-09-10
forum: Ubuntu Christian Edition
---

### Post by RJQ on 2007-09-10
For the last five months I was using e-Sword in Ubuntu Dapper under Wine, It was stable but I remember I had some trouble to get it running, but now I am using Feisty and it was quiet easy, the installation was smooth but the most important is that now every basic thing works just perfect, ( I am not sure if every single thing works fine since I do not use ALL the features available) Now my machine has three System Boot, Windows-Ubuntu-Kubuntu, (in practice is just like Dual Boot just more organized), and this are the steps in case some one may find them usable, the thing here is that there is nothing but installing and cutting and paste, thats all.

At this moment I am using the Wine version 0.9.33-0ubuntu1 (I am on may way to test the latest version available for Feisty 0.9.44-0ubuntu2~feisty1)

I installed Wine and its dependency through Adept Manager, then I copy from may windows partition the following files from System32 to Wine's System32:
riched20.dll, oleaut32.dll, riched32.dll y msls31.dll. (remembering to overwriting the the ones that are already in the folder)
After copying the files I installed e-Sword then in Wine Configuration (under Kubuntu located in the desktop menu) I select e-sword.exe under the “applications” tab, once highlighted I turn the tab to “libraries”, then select riched20 and oleaut32 adding them to the “Existing Overrides Box”, next is select them in that box and click on “edit” button then select the option “native (Windows)” this are actually some of the files we just copy from the windows partitions.
What I did then is totally optional, I select the “Desktop Integration” tab and then I installed the “Luna” theme from the windows partition, it is located in your_computer_path/WINDOWS/Resources/Themes/Luna/luna.msstyles
And now I have windows XP theme in e-sword and even better in Kubuntu you can configure Wine under “System Settings” and there select the KDE colors so your e-sword will look quite nice.
Now in my Windows System I have the latest e-Sword version and also all my settings and modules, I just went to the program folder and copy all the files in the e-Sword folder then in Wine's program folder in the e-Sword I just paste every single thing. The result is a perfect clone of e-Sword, actually in Kubuntu works quite faster than in windows and this time every gadget including the graphic window work just great. I hope some one may find it useful, I believe it is nothing new but for the newbies like me this may be the way to follow, I not even used the terminal this time. Enjoy.

---

### Post by Matthew Wiebelhaus on 2007-09-12
Thanks for the contribution of your time.

---

