---
title: "Feature request: improved albums/files management!"
date: 2005-02-10
forum: The Cafe
---

### Post by kiddo on 2005-02-10
Hi,
     - please move this topic to the correct location if needed
     - I decided to post here since I never got the hand of bugzilla and ubuntulinux.org is actually confusing me a bit
     
 I don't know if this should be posted in the forums, added somewhere in the giant ubuntulinux.org wiki, or sent to gnome, or if my ideas are just plain dumb :)
     
 I would really like to see an app/integration into nautilus that allows us "smart renaming". There are lots of ways to do this, I'm not really imaginative, whatever.
 

[list]
[*]Either improve the current album softwares (like digikam, which, I believe, is still a bit better than gtkam) so that it allows the user to BATCH RENAME files, or better, that's what I'd like to see, have all newly added content in specific folders be automatically renamed (for example, presetfilenamestring-PHOTONUMBER.jpg)
[/list]
[list]
[*]Make digital still camera importing SMART! But all this should not be applied only to cameras, it should be for everything you want! My problem comes from the following (so that non-camera users can get what I'm talking about):     
  
 When I take pictures, the camera names them, for example, DSCF0034.jpg, DSCF0035.jpg, etc. The problem is that if I want to avoid making a new folder everytime I import photos (that's at least once every 2 days for me!), I have to add the pictures to the same folder. Yeah. But with DSCFwhatever, the pictures which have the same numbers will try to overwrite, and that causes a serious problem. I believe it's within the linux community's grasp to make a kick-arse album/media/files management system with this simple concept (if it hasn't been said before). That's a shame I'm no programmer, just a designer :)
[/list]
[list]
[*]  Have a folder option that allows new added content to follow certain rules (that, however, would not really be standart)
[/list]Anyways, have a look at the log below, I'm kinda poor at explaining. Ideas?
     > * Now talking on #ubuntu
 * Topic for #ubuntu is: Ubuntu Help | FAQ: [http://www.ubuntulinux.org/support/documentation/faq/](http://www.ubuntulinux.org/support/documentation/faq/) | Wiki: [http://www.ubuntulinux.org/wiki/](http://www.ubuntulinux.org/wiki/) | Lists: [http://lists.ubuntu.com/](http://lists.ubuntu.com/) | Forum: [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/) | Guide: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) || Array 4 is released: [http://cdimage.ubuntu.com/releases/hoary/array-4/](http://cdimage.ubuntu.com/releases/hoary/array-4/)
 * Topic for #ubuntu set by mdz at Fri Feb  4 19:43:12 2005
 
 Nekohayo question: I'm a frequent photographer, is there a way / software which would automatically rename my files so that they do not overwrite in gnome? (some kind of auto album manager would be interesting)... asking this since I haven't seen one yet
 sladen: there's lots of renaming you could do, can you give examples of before and afterwards.  I tend to just move photographs to a directory called 20050211-0250 so that each directory has a unique name
 Nekohayo: that makes a lots of dirs! I kinda like to have a maximum of 5 dirs per year (ex.: 2005-misc1, 2005-misc2, etc, each one holding more than 200 pics at least.. why make tons of dirs elseway? :P)
 Nekohayo: in fact if I could solve this problem, I'd be using one directory per year maybe.. what would be cool is an app that allows you to "apply a filename template" to what you move in a specific dir
 sladen: so, anything dropped in would get a unique new number, completely deleting the name it had before?
 Nekohayo: yes, why would I care for a DSCF03498273598723493.jpg :)?
 Nekohayo: it would have a fixed string, then the number
 sladen: urm.  So what /would/ you care for?
 Nekohayo: well in fact the only important thing is to not have the files overwrite (since the camera goes back to zero when data is deleted)... for example, the files could be named Ilovechocolate-$FILEID.jpg
 sladen: I know many ways to do it, all on the command line!
 sladen: see if you can find something related on the wiki and recode your idea.  But very click exactly what should happen if you drag.  Exactly what the new name should be...
 Nekohayo: hmm, I'm a gui lover, I would be much more efficient if I could do that with nautilus/an album app
 Nekohayo: what do you mean about the wiki? that I should post this as a feature request?
 sladen: if you have an idea, yes
 Nekohayo: should it be posted in the ubuntuforums? in some ubuntulinux.org wiki page? (I tend to be lost in these a bit) mailed to the gnome guys?
 

---

### Post by Rule on 2005-02-10
[IMG]http://www3.telus.net/ra11le/smilies/werd.gif[/IMG]  but making a new folder everytime does kinda keep them a lil more organized haha

---

### Post by kiddo on 2005-02-10
That is my current /home/jeff/Desktop/photographie folder listing:
  
"2003 - chloe - divers
  2003 photos SCD86 samsung
  2004 album groupe 54
  2004 - amar - heritage festival new york
  2004 apres bal
  2004 divers 1
  2004 divers 2
  2004 divers 3
  2004 divers 4
  2004 - etienne - summer
  2004 gala meritas
  2004 kirika airduct patch
  2004 kirika installation d'un support clavier
  2004 - tammy - chemin de compostelle
  2004 - tammy - souper des pélerins
  2005 01 11 tournage
  2005 divers 1
  2005 divers 2
  2005 divers 3
  Macro-photographie
  panoramique
  special"
  
  
 And I find it already too much cluttered! I *don't* need more than one "2005 divers" folder (divers == miscellaneous) per year. Inside, I just have to browse with my thumbnails happily. And if I find there are too much pics, well let's just make a folder #2! 
  
 However, I don't want to make... let's do a quick calculation... 150 folders per year, or have to rename everything manually, that's kinda horrible.

---

### Post by CowPie on 2005-02-11
[QUOTE=kiddo]Hi,
     - please move this topic to the correct location if needed
     - I decided to post here since I never got the hand of bugzilla and ubuntulinux.org is actually confusing me a bit
     
 I don't know if this should be posted in the forums, added somewhere in the giant ubuntulinux.org wiki, or sent to gnome, or if my ideas are just plain dumb :)
     
 I would really like to see an app/integration into nautilus that allows us "smart renaming". There are lots of ways to do this, I'm not really imaginative, whatever.
 

[list]
[*]Either improve the current album softwares (like digikam, which, I believe, is still a bit better than gtkam) so that it allows the user to BATCH RENAME files, or better, that's what I'd like to see, have all newly added content in specific folders be automatically renamed (for example, presetfilenamestring-PHOTONUMBER.jpg)
[/list]
[list]
[*]Make digital still camera importing SMART! But all this should not be applied only to cameras, it should be for everything you want! My problem comes from the following (so that non-camera users can get what I'm talking about):     
  
 When I take pictures, the camera names them, for example, DSCF0034.jpg, DSCF0035.jpg, etc. The problem is that if I want to avoid making a new folder everytime I import photos (that's at least once every 2 days for me!), I have to add the pictures to the same folder. Yeah. But with DSCFwhatever, the pictures which have the same numbers will try to overwrite, and that causes a serious problem. I believe it's within the linux community's grasp to make a kick-arse album/media/files management system with this simple concept (if it hasn't been said before). That's a shame I'm no programmer, just a designer :)
[/list]
[list]
[*]  Have a folder option that allows new added content to follow certain rules (that, however, would not really be standart)
[/list]Anyways, have a look at the log below, I'm kinda poor at explaining. Ideas?[/QUOTE]
 I agreee, here is my Ubuntu bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6005](https://bugzilla.ubuntu.com/show_bug.cgi?id=6005)

but no replies. 
Batch rename would be a nice feature in nautilus; select all the parts that are in common.

---

### Post by CowPie on 2005-02-11
[QUOTE=CowPie]I agreee, here is my Ubuntu bug:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6005](https://bugzilla.ubuntu.com/show_bug.cgi?id=6005)

but no replies. 
Batch rename would be a nice feature in nautilus; select all the parts that are in common.[/QUOTE]
 PS: Windows XP has this "integration", hvae you looked at it as well?

---

### Post by ups on 2005-02-11
A batch rename techinique is present in gthumb - you might wanna have a look at it too.
gthumb -> Tools -> Rename Series

I find it quite useful, and it operates in the current directory.

---

### Post by kiddo on 2005-02-11
OMG. Now THAT'S something I didn't know!
 Thank you **so much**! I'm having a whole different look at gThumbs now o_o
 
 However, it would still be nice to have that functionnality within nautilus. (And yes, I did use the winXP feature: select all, rename one, and the rest is automatically renamed after.. not very flexible, but works)

---

### Post by jzke on 2005-06-28
I agree, has someone posted a bug report for nautilus... for a batch rename function? I'm NEED one... I have waaay too many images that are all from the same event, but have all different names, which is why I now use gThumb, but what about all my other files?

---

### Post by sonny on 2005-06-28
[QUOTE=kiddo]Hi,
     - please move this topic to the correct location if needed
     - I decided to post here since I never got the hand of bugzilla and ubuntulinux.org is actually confusing me a bit
     
 I don't know if this should be posted in the forums, added somewhere in the giant ubuntulinux.org wiki, or sent to gnome, or if my ideas are just plain dumb :)
     
 I would really like to see an app/integration into nautilus that allows us "smart renaming". There are lots of ways to do this, I'm not really imaginative, whatever.
 

[list]
[*]Either improve the current album softwares (like digikam, which, I believe, is still a bit better than gtkam) so that it allows the user to BATCH RENAME files, or better, that's what I'd like to see, have all newly added content in specific folders be automatically renamed (for example, presetfilenamestring-PHOTONUMBER.jpg)
[/list]
[list]
[*]Make digital still camera importing SMART! But all this should not be applied only to cameras, it should be for everything you want! My problem comes from the following (so that non-camera users can get what I'm talking about):     
  
 When I take pictures, the camera names them, for example, DSCF0034.jpg, DSCF0035.jpg, etc. The problem is that if I want to avoid making a new folder everytime I import photos (that's at least once every 2 days for me!), I have to add the pictures to the same folder. Yeah. But with DSCFwhatever, the pictures which have the same numbers will try to overwrite, and that causes a serious problem. I believe it's within the linux community's grasp to make a kick-arse album/media/files management system with this simple concept (if it hasn't been said before). That's a shame I'm no programmer, just a designer :)
[/list]
[list]
[*]  Have a folder option that allows new added content to follow certain rules (that, however, would not really be standart)
[/list]Anyways, have a look at the log below, I'm kinda poor at explaining. Ideas?[/QUOTE]
I found this very useful, I think it would be great to have somelike this in nautilus, or konqueror for the matter.

---

### Post by el3ktro on 2006-01-26
[QUOTE=ups]A batch rename techinique is present in gthumb - you might wanna have a look at it too.
gthumb -> Tools -> Rename Series

I find it quite useful, and it operates in the current directory.[/QUOTE]

Hi, I also really need this function, but in gThumb 2.7.1 I don't find this functon! Which version are you using?

Tom

---

