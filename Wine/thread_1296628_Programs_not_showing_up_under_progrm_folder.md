---
title: "Programs not showing up under progrm folder"
date: 2009-10-20
forum: Wine
---

### Post by chisle on 2009-10-20
Like the  title says programs that i install are not showing up in the programs folder. i can access them by going to the c drive and clicking on the .exe file from there but for convenience i would like to be able to just click on the program from the drop down menu. any suggestions on fixing this. an extension for wine i need to download or something?

---

### Post by pedro_orange on 2009-10-21
You can add things to the menu by right clicking and editing it (I think - If not there's something under System). Or you can do something like:

(Find a nice graphic for the menu bar)
```
sudo mv my_img.svg /usr/share/pixmaps/
```

```
gksudo gedit /usr/share/applications/myapp.desktop
```

In the new file type:

```
[Desktop Entry]
Encoding=UTF-8
Name=My Application
Exec=wine /home/<username>/.wine/drive_c/Program\ Files/Vendor/MyApp/MyApp.exe
Icon=my_img.svg
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=false
```

```
Categories=Application;Game;
```

This line tells the menu where it's going to live.
Make sure you're case sensitive. 

But you can do all this from the GUI if you're not happy with the command line.

---

