---
title: "Unistalling Wine Application [Clean]"
date: 2009-11-20
forum: Wine
---

### Post by kristine12 on 2009-11-20
I installed orbit downloader on my Ubuntu and uninstall it after several crashes. When I uninstalled it my system says that Orbit Downloader is successfully removed from my system. But when I look at Wine -> Programs, Orbit Folder is still there. How can I removed it and does this have an impact on my computer?

---

### Post by Xog on 2009-11-20
> **kristine12 said:**
> I installed orbit downloader on my Ubuntu and uninstall it after several crashes. When I uninstalled it my system says that Orbit Downloader is successfully removed from my system. But when I look at Wine -> Programs, Orbit Folder is still there. How can I removed it and does this have an impact on my computer?

```
gksu nautilus
```

That will give you a root file manager, and at the top of the file manager window you need to click on View then check the box for Show Hidden Files. PLEASE BE CAREFUL, you are acting as root, which means you could bork your system if you do something you shouldn't have.


you can find all the junk that won't remove hiding out in these four places...

home/username/.config/menus/applications-merged/wine
home/username/.local/share/applications/wine
home/username/.local/share/desktop-directories/wine
home/username/.local/share/icons/

---

### Post by beastrace91 on 2009-11-20
> **Xog said:**
> ```
gksu nautilus
```

That will give you a root file manager, and at the top of the file manager window you need to click on View then check the box for Show Hidden Files. PLEASE BE CAREFUL, you are acting as root, which means you could bork your system if you do something you shouldn't have.


you can find all the junk that won't remove hiding out in these four places...

home/username/.config/menus/applications-merged/wine
home/username/.local/share/applications/wine
home/username/.local/share/desktop-directories/wine
home/username/.local/share/icons/

Since all of these directories are located in your **~/** (home) folder you do not need a root file viewer to edit/remove them. Just browse to your home folder from your **Places** menu and press **ctrl+h** (toggles hidden files on/off) when you have the file viewer selected to see the above listed directories.

~Jeff

---

### Post by Xog on 2009-11-20
> **beastrace91 said:**
> Since all of these directories are located in your **~/** (home) folder you do not need a root file viewer to edit/remove them. Just browse to your home folder from your **Places** menu and press **ctrl+h** (toggles hidden files on/off) when you have the file viewer selected to see the above listed directories.

~Jeff

I've seen wine make a file only accessible by root quite a few times, this why i mentioned to run that command.

---

### Post by kristine12 on 2009-11-21
My problem is solved! Thank you for the advice! I have successfully deleted the orbit folder using nautilus @ "/home/username/.local/share/applications/wine/"

---

