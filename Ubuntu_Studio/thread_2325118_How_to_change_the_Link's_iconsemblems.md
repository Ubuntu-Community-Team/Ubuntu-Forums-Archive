---
title: "How to change the Link's icons/emblems?"
date: 2016-05-19
forum: Ubuntu Studio
---

### Post by javierdl on 2016-05-19
I thought I could just go to the Properties of the Link to click on its icon then choose an image file or another icon, as we can do with the classic Ubuntu (at least I used to do it in 14.04).
But apparently the only option is to choose one of the available "Emblems", only.

Any ideas?

JDL

---

### Post by vasa1 on 2016-05-19
Do you mean *folder* or *link*? What is the context?

---

### Post by javierdl on 2016-05-19
Link. I created this link from the context popup menu when right-clicking an app. and chose "Send to.../ Desktop (create link)". Now it would be nice if the generic emblem would represent the actual app it is for.

---

### Post by ajgreeny on 2016-05-19
Are you using the xfce4 DE as I believe Ubuntu-studio does by default?

I still do not know what you mean by a "link"; are you talking of launcher icons on the desktop that you have added or some other link?
More explanation is needed, please, or we are all stabbing in the dark.

---

### Post by javierdl on 2016-05-19
It's the equivalent to a Windows shortcut.
Yes, I think US is using XFCE4.

---

### Post by Dennis N on 2016-05-19
> **javierdl said:**
> I thought I could just go to the Properties of the Link to click on its icon then choose an image file or another icon, as we can do with the classic Ubuntu (at least I used to do it in 14.04). But apparently the only option is to choose one of the available "Emblems", only.
Any ideas?
JDL

Yes, it's possible. Files have an icon assigned by their mime type. But, you can change the icon for a mime type. For example, I once changed the file icon for .xml files to geany's icon just to learn how it was done. The key article was this one:

[http://unix.stackexchange.com/questions/23776/how-to-change-a-file-type-icon-in-xfce-thunar](http://unix.stackexchange.com/questions/23776/how-to-change-a-file-type-icon-in-xfce-thunar)

Symbolic links commonly show an icon matching the mime type of the target: text file, html file, and so on. One exception is image files, where Thunar can display a thumbnail of the target.

---

### Post by javierdl on 2016-05-21
Dennis N.,
That seems to be to change "icon types" to be applied generically to many files of one type, as far as I understand. I just want to be able to change the icon of one application file, with its own predefined and unique icon. 
Thanks for sharing though. This could come in handy later.

JDL

---

### Post by Dennis N on 2016-05-21
When you say link, I think symbolic link. If you create a link to a file as you mention in #3, it creates a symbolic link. The icon used for those comes from the type of file (mime type) you are linking to, and is not stored with the file itself. So, if you change it, it changes for all files of the same type.

If you want an application shortcut on the Desktop (to open a particular application instead of a file), that is done by creating a .desktop file on your Deskop (or wherever you might want it) which is a different thing.

---

### Post by javierdl on 2016-05-21
Oh! I see. Thanks for the explanation.
Then I need to learn about the latter one.

J

---

### Post by ajgreeny on 2016-05-23
To understand more about these shortcuts, ie, the **.desktop** files mentioned by **Dennis M**, have a look at [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles) where it is all explained in more detail.

You can probably right click on one of the shortcuts on your desktop and choose to open it with leafpad/mousepad or whatever text editor you have in U_Studio.  That will show you exactly what is in your own shortcuts.

---

