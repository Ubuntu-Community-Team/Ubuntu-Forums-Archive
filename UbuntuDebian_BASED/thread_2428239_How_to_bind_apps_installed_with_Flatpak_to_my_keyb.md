---
title: "How to bind apps installed with Flatpak to my keyboard's favorite top keys?"
date: 2019-10-01
forum: Ubuntu/Debian BASED
---

### Post by javierdl on 2019-10-01
Deepin 15.11

I installed Gimp from Flatpak before. How do I find what is its location path to use it to make a costume shortcut?
And how about apps from the App Store? Where are they located?

This is where I go to add the costume shortcut:
All Settings/Keyboard & Language/Shortcuts/Add Costume Shortcut/

[IMG]https://www.linuxquestions.org/questions/attachment.php?attachmentid=31428&d=1569869453[/IMG]


Thanks

---

### Post by Frogs Hair on 2019-10-01
It maybe helpful to find the path if you open the file manager and select show hidden and search .desktop and see if gimp is located there. From what I've read flat-packs  should be listed there. I have used the same package on Deepin, but never tried to create a key binding .

---

### Post by vanadium on 2019-10-01
It can help to find the corresponding .desktop file of your application: it's "Exec=" line will show the command. If you note the title of the launcher you find in your menu system (e.g. "Applications overview" in standard Ubuntu), then this one liner lets you search for desktop files on your system that contain that string, e.g. "Libreoffice Writer":

```
find / -name '*.desktop' -exec grep -H 'LibreOffice Writer' {} \; 2>/dev/null  
```

Inspect the contents of the relevant .desktop file found by that command to see the "Exec=" line.

---

### Post by javierdl on 2019-10-02
> **Frogs Hair said:**
> It maybe helpful to find the path if you open the file manager and select show hidden and search .desktop and see if gimp is located there. From what I've read flat-packs  should be listed there. I have used the same package on Deepin, but never tried to create a key binding .

Only 2 items on the Desktop:
```
ls -a
.  ..  ASTRONEER.desktop  Blender.desktop



```

Same thing showed File Manager.

---

### Post by javierdl on 2019-10-02
> **vanadium said:**
> It can help to find the corresponding .desktop file of your application: it's "Exec=" line will show the command. If you note the title of the launcher you find in your menu system (e.g. "Applications overview" in standard Ubuntu), then this one liner lets you search for desktop files on your system that contain that string, e.g. "Libreoffice Writer":

```
find / -name '*.desktop' -exec grep -H 'LibreOffice Writer' {} \; 2>/dev/null  
```

Inspect the contents of the relevant .desktop file found by that command to see the "Exec=" line.


```
find / -name '*.desktop' -exec grep -H gimp {} \; 2>/dev/null
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:MimeType=image/bmp;image/g3fax;image/gif;image/x-fits;image/x-pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/x-gimp-gbr;image/x-gimp-pat;image/x-gimp-gih;image/tiff;image/jpeg;image/x-psp;application/postscript;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;application/pdf;image/x-wmf;image/jp2;image/jpeg2000;image/jpx;image/x-xcursor;



```

There were many more results. All started the same way: "/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/**timeshift**/"


Here are the all of them:

```


/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/home/nitro/.local/share/applications/krita_brush.desktop:MimeType=image/x-gimp-brush;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/usr/share/applications/krita_brush.desktop:MimeType=image/x-gimp-brush;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:X-AppInstall-Package=gimp
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:Exec=gimp-2.8 %U
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:TryExec=gimp-2.8
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:Icon=gimp
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:X-GNOME-Bugzilla-OtherBinaries=gimp-2.8
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:MimeType=image/bmp;image/g3fax;image/gif;image/x-fits;image/x-pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/x-gimp-gbr;image/x-gimp-pat;image/x-gimp-gih;image/tiff;image/jpeg;image/x-psp;application/postscript;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;application/pdf;image/x-wmf;image/jp2;image/jpeg2000;image/jpx;image/x-xcursor;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/exports/share/applications/org.gimp.GIMP.desktop:Exec=/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @@u %U @@
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/exports/share/applications/org.gimp.GIMP.desktop:Icon=org.gimp.GIMP
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/exports/share/applications/org.gimp.GIMP.desktop:X-GNOME-Bugzilla-OtherBinaries=gimp-2.10
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/exports/share/applications/org.gimp.GIMP.desktop:MimeType=image/bmp;image/g3fax;image/gif;image/x-fits;image/x-pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/x-gimp-gbr;image/x-gimp-pat;image/x-gimp-gih;image/tiff;image/jpeg;image/x-psp;application/postscript;image/png;image/x-icon;image/x-xpixmap;image/x-exr;image/x-webp;image/heif;image/heic;image/svg+xml;application/pdf;image/x-wmf;image/jp2;image/x-xcursor;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/exports/share/applications/org.gimp.GIMP.desktop:X-Flatpak-RenamedFrom=gimp.desktop;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/exports/share/applications/org.gimp.GIMP.desktop:X-Flatpak=org.gimp.GIMP
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/export/share/applications/org.gimp.GIMP.desktop:Exec=/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=gimp-2.10 --file-forwarding org.gimp.GIMP @@u %U @@
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/export/share/applications/org.gimp.GIMP.desktop:Icon=org.gimp.GIMP
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/export/share/applications/org.gimp.GIMP.desktop:X-GNOME-Bugzilla-OtherBinaries=gimp-2.10
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/export/share/applications/org.gimp.GIMP.desktop:MimeType=image/bmp;image/g3fax;image/gif;image/x-fits;image/x-pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/x-gimp-gbr;image/x-gimp-pat;image/x-gimp-gih;image/tiff;image/jpeg;image/x-psp;application/postscript;image/png;image/x-icon;image/x-xpixmap;image/x-exr;image/x-webp;image/heif;image/heic;image/svg+xml;application/pdf;image/x-wmf;image/jp2;image/x-xcursor;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/export/share/applications/org.gimp.GIMP.desktop:X-Flatpak-RenamedFrom=gimp.desktop;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/export/share/applications/org.gimp.GIMP.desktop:X-Flatpak=org.gimp.GIMP
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/files/share/applications/org.gimp.GIMP.desktop:Exec=gimp-2.10 %U
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/files/share/applications/org.gimp.GIMP.desktop:TryExec=gimp-2.10
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/files/share/applications/org.gimp.GIMP.desktop:Icon=org.gimp.GIMP
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/files/share/applications/org.gimp.GIMP.desktop:X-GNOME-Bugzilla-OtherBinaries=gimp-2.10
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/files/share/applications/org.gimp.GIMP.desktop:MimeType=image/bmp;image/g3fax;image/gif;image/x-fits;image/x-pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/x-gimp-gbr;image/x-gimp-pat;image/x-gimp-gih;image/tiff;image/jpeg;image/x-psp;application/postscript;image/png;image/x-icon;image/x-xpixmap;image/x-exr;image/x-webp;image/heif;image/heic;image/svg+xml;application/pdf;image/x-wmf;image/jp2;image/x-xcursor;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-24_15-00-01/localhost/var/lib/flatpak/app/org.gimp.GIMP/x86_64/stable/3fdfdf0963ba67629f287092229d9f5659bc9a2eeb1158c060b09d8a603acbcf/files/share/applications/org.gimp.GIMP.desktop:X-Flatpak-RenamedFrom=gimp.desktop;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-22_15-00-04/localhost/home/nitro/.local/share/applications/krita_brush.desktop:MimeType=image/x-gimp-brush;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-22_15-00-04/localhost/usr/share/applications/krita_brush.desktop:MimeType=image/x-gimp-brush;
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-22_15-00-04/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:X-AppInstall-Package=gimp
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-22_15-00-04/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:Exec=gimp-2.8 %U
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-22_15-00-04/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:TryExec=gimp-2.8
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-22_15-00-04/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:Icon=gimp
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-22_15-00-04/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:X-GNOME-Bugzilla-OtherBinaries=gimp-2.8
/media/drpeppercan/4902dea5-369a-4981-a4d3-41ff0e5dca42/timeshift/snapshots/2019-09-22_15-00-04/localhost/usr/share/app-install/desktop/gimp:gimp.desktop:MimeType=image/bmp;image/g3fax;image/gif;image/x-fits;image/x-pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/x-gimp-gbr;image/x-gimp-pat;image/x-gimp-gih;image/tiff;image/jpeg;image/x-psp;application/postscript;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;application/pdf;image/x-wmf;image/jp2;image/jpeg2000;image/jpx;image/x-xcursor;




```

---

