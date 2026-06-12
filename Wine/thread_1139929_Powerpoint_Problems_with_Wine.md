---
title: "Powerpoint Problems with Wine"
date: 2009-04-27
forum: Wine
---

### Post by etheodos on 2009-04-27
Hello,

I do not know if this has been resolved, though I know for a fact that others have had this exact problem, so I apologize in advance for any redundancy. I have been trying to install Microsoft Office 2007 through wine and have been having particular difficulty with Powerpoint.  I started with wine 1.1.2, then completely reinstalled 1.1.15 according to a different post when I had troubles installing.  After this I updated back to 1.1.2 before realizing that Powerpoint did not work.  Since then I have uninstalled completely (even the .wine folder in home) and attempted it with other versions (1.1.13 through their development release), none of which worked.  Word and Excel work fine, but Powerpoint never loads, it just comes up with the initialization screen and then locks up.  I don't believe it is a hardware problem, though specifics can be given upon request.  My wine version as of right now is 1.1.2 and my OS is set at Windows XP.  Besides that I have made no changes to my wine settings, use nothing like winetricks and have refrained from installing any other programs so as to avoid conflict. And I have updated to 9.04 in the middle of these problems, but experienced the same problems in 8.10 as I am having now.

Any help would be greatly appreciated, and I am relatively new to linux, so please don't assume I would know something that may be an easy step for someone with superior experience.

Thanks in advance

---

### Post by iamkion132 on 2009-04-27
> **etheodos said:**
> Hello,

I do not know if this has been resolved, though I know for a fact that others have had this exact problem, so I apologize in advance for any redundancy. I have been trying to install Microsoft Office 2007 through wine and have been having particular difficulty with Powerpoint.  I started with wine 1.1.2, then completely reinstalled 1.1.15 according to a different post when I had troubles installing.  After this I updated back to 1.1.2 before realizing that Powerpoint did not work.  Since then I have uninstalled completely (even the .wine folder in home) and attempted it with other versions (1.1.13 through their development release), none of which worked.  Word and Excel work fine, but Powerpoint never loads, it just comes up with the initialization screen and then locks up.  I don't believe it is a hardware problem, though specifics can be given upon request.  My wine version as of right now is 1.1.2 and my OS is set at Windows XP.  Besides that I have made no changes to my wine settings, use nothing like winetricks and have refrained from installing any other programs so as to avoid conflict. And I have updated to 9.04 in the middle of these problems, but experienced the same problems in 8.10 as I am having now.

Any help would be greatly appreciated, and I am relatively new to linux, so please don't assume I would know something that may be an easy step for someone with superior experience.

Thanks in advance

Did you know that Ubuntu comes with an office style program called Open Office?  It can open/create/save Powerpoint presentations and is in fact a complete office suite like Microsoft Office 2000/2003/2007.  If you have a normal installation of Ubuntu, click on the applications menu, scroll down to office and in that menu click on openoffice.org presentation. 

Use it as you normally would with Power Point.  When it comes to saving however, you need to remember to do a couple of things.  If you just want to edit it on your computer, you can do a traditional save.  This will save it in the normal open office format.  

However, if you want to ever edit it on a different computer that only has Microsoft Office 2000/2003/2007, you need to do a save as.  In the save window, there will be a drop down box that has a list of options.  Scroll down a little bit and there will be an option to save as a Microsoft 97/2000/XP file.  There might be a warning that comes up that ask if you want to keep that format or save in ODF format.  You need to keep the current format to work on it in Microsoft Office.

You can open Microsoft office documents in Open Office 97-99.9% of the time without a problem. There is nothing special you need to do open it.  When you make changes to these documents and save them, you don't need to do a save as.  Just remember to keep format.  

I've never had any issues with the program when I used it under Windows and for the few days I've used Ubuntu, no problems either.  Except for certain complex macros, Open Office can handle most things created with Microsoft programs.  The only thing that you might run into problems is Publisher files as these aren't supported by OO.

OO is shorthand for OpenOffice if you ever get confused about that in the future.  Good luck with Linux and feel free to ask any other questions.

---

### Post by NightMKoder on 2009-04-28
[http://ubuntuforums.org/showthread.php?p=6936072](http://ubuntuforums.org/showthread.php?p=6936072)

Set riched20 to native in winecfg.

---

### Post by etheodos on 2009-04-28
Thank you very much for the advice both of you. The fix for Microsoft Office worked perfectly.

---

### Post by AlexanderDGreat on 2010-06-29
Wow! This actually works! Thank you so much.

@NightMKoder - is there any particular bug that I need to know of when using the Word, Excel, or Powerpoint in Office 2007?

For example, bullets don't work, letters showing in bold, etc... anything weird I need to anticipate?

How do you solve them? And where do you find information / bugs such as these?

I'm using Wine 1.1.42 and installed MS OFFICE ENTERPRISE 2007.

Thanks.

---

### Post by mrkazoodle on 2010-07-01
that solution was pretty standard, you need to learn to search the wine app database.
search for word 2007, powerpoint 2007,... on those pages you'll find a howto to fix the most basic problems

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

---

### Post by lunatico on 2010-08-09
I just found out today that I can't open more than one PowerPoint at the same time. They open, but the second one opens on top of the first one, I can see both down in the panel but they seem to be merged into one window. So only the second one shows and can not make the first one to show.

Anyone else seen this?

---

### Post by beew on 2010-08-09
Just use OpenOffice like the other guy says. I don't get it, why would some people go through a lot of troubles to install only 90% functioning microsoft stuffs in their systems with Wine while stubbornly refusing to use the native linux solution which is just as good for their purpose. I look at the Wine compatibility list. The only MS office suites that work perfectly with wine appear to be Office 9X and Office 2000 (2003?) Why would anyone switch to Linux just to use outdated windows programs?

Well I use wine for only one small program which I cannot find a native Linux solution and that's it. I find the concept of wine a lot more interesting than the softwares that it supposedly can run (mostly games, some Ms media utilities which I won't even use in windows, Office and maybe something a bit more interesting like Photoshop). I will keep my wine updated just to play around with it, not  for the purpose of installing  Windows softwares.

---

### Post by lunatico on 2010-08-09
> **beew said:**
> Just use OpenOffice like the other guy says. I don't get it, why would some people go through a lot of troubles to install only 90% functioning microsoft stuffs in their systems with Wine while stubbornly refusing to use the native linux solution which is just as good for their purpose. I look at the Wine compatibility list. The only MS office suites that work perfectly with wine appears to be Office 9X and Office 2000 (2003?) Why would anyone switch to Linux just to use outdated windows programs?

Because everyone else uses outdated windows programs. Don't get me wrong, I am 100% pro Ubuntu, linux, open source, open office, etc... but I use this for work also, and when interacting with companie's doc, xls and ppt documents open office always messes everything up. If it was for me I would only use Open Office, even though it lacks functionality compared to Office 2010.

---

### Post by beew on 2010-08-09
> **lunatico said:**
> Because everyone else uses outdated windows programs. Don't get me wrong, I am 100% pro Ubuntu, linux, open source, open office, etc... but I use this for work also, and when interacting with companie's doc, xls and ppt documents open office always messes everything up. If it was for me I would only use Open Office, even though it lacks functionality compared to Office 2010.

Well the only MS Office packages that got platinum or gold rating on the wine compatibility list are Office 9x and Office 2000 (perhaps, Office 2003 too, can't remember) They are hardly more compatible with Office2007 and Office2010 than OOO.

Unless you are a heavy duty gamer or need some odd softwares that only work in Windows (Photoshops? Though I am not sure if Photoshops with only a silver or bronze rating on the Wine list is so much better than gimp) I cannot really see the usefulness of Wine. Like I said, I find wine itself a lot more interesting than most Windows softwares that can run in wine with good results.

---

