---
title: "LibreOffice 5"
date: 2016-02-13
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2016-02-13
I installed 5.1 direct from libreoffice.org. It's working fine. One thing that had me worried for a while was what the devs refer to as "Use legacy cursor movement behavior when selecting". In version 5.0 and 5.1, I had to select this feature in *Tools > Options > LibreOffice Calc > General*; it wasn't on by default. IIRC, in version 4.x it was.

The other thing is that LibreOffice keeps including huge svg files. Here's an example:```
/usr/share/icons/hicolor/scalable/mimetypes $ ll
total 9712
-rw-r--r-- 1 root root    1324 Mar 11  2014 application-certificate-symbolic.svg
-rw-r--r-- 1 root root    1226 Mar 11  2014 application-rss+xml-symbolic.svg
-rw-r--r-- 1 root root    3698 Mar 11  2014 application-x-appliance-symbolic.svg
-rw-r--r-- 1 root root    1430 Mar 11  2014 audio-x-generic-symbolic.svg
-rw-r--r-- 1 root root  475172 Jan 27 15:19 libreoffice5.1-oasis-database.svg
-rw-r--r-- 1 root root  638337 Jan 27 15:19 libreoffice5.1-oasis-drawing.svg
-rw-r--r-- 1 root root  996789 Jan 27 15:19 libreoffice5.1-oasis-drawing-template.svg
-rw-r--r-- 1 root root  674687 Jan 27 15:19 libreoffice5.1-oasis-formula.svg
-rw-r--r-- 1 root root  517553 Jan 27 15:19 libreoffice5.1-oasis-master-document.svg
-rw-r--r-- 1 root root  562202 Jan 27 15:19 libreoffice5.1-oasis-presentation.svg
-rw-r--r-- 1 root root  894437 Jan 27 15:19 libreoffice5.1-oasis-presentation-template.svg
-rw-r--r-- 1 root root 1277590 Jan 27 15:19 libreoffice5.1-oasis-spreadsheet.svg
-rw-r--r-- 1 root root 1307010 Jan 27 15:19 libreoffice5.1-oasis-spreadsheet-template.svg
-rw-r--r-- 1 root root  545929 Jan 27 15:19 libreoffice5.1-oasis-text.svg
-rw-r--r-- 1 root root  784895 Jan 27 15:19 libreoffice5.1-oasis-text-template.svg
-rw-r--r-- 1 root root 1211242 Jan 27 15:19 libreoffice5.1-oasis-web-template.svg
-rw-r--r-- 1 root root    1475 Mar 11  2014 package-x-generic-symbolic.svg
-rw-r--r-- 1 root root    1136 Mar 11  2014 text-x-generic-symbolic.svg
-rw-r--r-- 1 root root    1545 Mar 11  2014 video-x-generic-symbolic.svg
-rw-r--r-- 1 root root    1366 Mar 11  2014 x-office-calendar-symbolic.svg

```

```
11:03 PM ~ $ locate libreoffice5.1-oasis-spreadsheet-template.svg
/usr/share/icons/gnome/scalable/mimetypes/libreoffice5.1-oasis-spreadsheet-template.svg
/usr/share/icons/hicolor/scalable/mimetypes/libreoffice5.1-oasis-spreadsheet-template.svg
11:03 PM ~ $ 

```Grrr...

---

### Post by monkeybrain20122 on 2016-02-13
I installed 5.1 from ppa. There is something wrong with the gtk3 theme package, scrolling on touchpad doesn't work with it installed [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=809363;msg=23](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=809363;msg=23) And it is really ugly too. Removed it and everything works.

---

### Post by mikodo on 2016-02-13
No specifics remembered. I have had problems with using the latest versions of Libreoffice, when trying from PPA's. I vowed I would stick to repos versions. Now, I wonder if even that is safe enough from problems and if it is worthwhile considering using older versions than the repos ones giving yet more time to have "the dust settle". I appreciate that LO is actively developed and "alive". I wonder if too much Alpha and Beta versions are being pushed out to stable too soon though.

---

### Post by vasa1 on 2016-02-13
> **monkeybrain20122 said:**
> I installed 5.1 from ppa. There is something wrong with the gtk3 theme package, scrolling on touchpad doesn't work with it installed [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=809363;msg=23](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=809363;msg=23) And it is really ugly too. Removed it and everything works.
The joys of gtk3.

Do you have a file like this: ~/.config/gtk-3.0/settings.ini?

Here's mine:```
[Settings] 
#gtk-theme-name=freebird
#gtk-theme-name=Numix
gtk-theme-name=Mymix
gtk-icon-theme-name=NoInherits
gtk-font-name=Ubuntu 12
gtk-cursor-theme-name=oxy-red-argentina
gtk-cursor-theme-size=18
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-toolbar-icon-size=GTK_ICON_SIZE_LARGE_TOOLBAR
gtk-button-images=0
gtk-menu-images=0
gtk-enable-event-sounds=1
gtk-enable-input-feedback-sounds=1
gtk-xft-antialias=1
gtk-xft-hinting=1
gtk-xft-hintstyle=hintslight
gtk-xft-rgba=rgb
gtk-primary-button-warps-slider=false
```The last line gives me old-fashioned gtk2 scrolling. But that apprently is not related to the bug you cited.

---

### Post by vasa1 on 2016-02-13
> **mikodo said:**
> No specifics remembered. I have had problems with using the latest versions of Libreoffice, when trying from PPA's. I vowed I would stick to repos versions. Now, I wonder if even that is safe enough from problems and if it is worthwhile considering using older versions than the repos ones giving yet more time to have "the dust settle". I appreciate that LO is actively developed and "alive". I wonder if too much Alpha and Beta versions are being pushed out to stable too soon though.
Well, I seem to be lucky in that I've not seen any deal-breaking issues, perhaps because I'm still on gtk2. Some keyboard shortcuts have been changed / rationalized / made intuitive but I'm patient.

---

### Post by vasa1 on 2016-03-25
LibreOffice had an issue (or feature) that whatever was in its clipboard would no longer exist if LibreOffice was closed. Apparently, the change to gtk3 will help allow the clipboard data to persist after closure:
[Bug 1240591 - Clipboard is cleared when LO is closed]("https://bugzilla.redhat.com/show_bug.cgi?id=1240591") 
Comment #1> Our current gtk2 impl doesn't use gtk for c-n-p, but uses the old direct X11 calls. The new gtk3 one does use the gtk apis, so at least in theory if we can find the right place to call gtk_clipboard_store somewhere during shutdown we should be able to finally support this.

Comment #2> can't do anything about f22. But for f23 onwards with libreoffice-gtk3 installed we can finally support thisI guess someone on 16.04 maybe able to check if the fix is for Ubuntu as well.

---

### Post by sudodus on 2016-03-25
I tried in the current Xenial beta 2, and can copy and paste while Libre Office is running, but not after shutting it down.

Edit: This is in a Xubuntu + Lubuntu desktop installed system.

---

### Post by vasa1 on 2016-03-25
> **sudodus said:**
> I tried in the current Xenial beta 2, and can copy and paste while Libre Office is running, but not after shutting it down.

Edit: This is in a Xubuntu + Lubuntu desktop installed system.
Thanks for checking. I don't think being on Xubu/Lubu might have anything to do with it. We may just have to wait for a later version of LibO.

---

