---
title: "How to create custom file associations on Gnome 3"
date: 2011-09-26
forum: Tutorials
---

### Post by kalaka on 2011-09-26
So you installed Gnome Shell and you want to open a specific type of file with your favorite application but when you select 'Open With' from the Nautilus menu, your application is not on the list? The good old Gnome 2.X had an option to open with a 'custom command', missing it already? I agree, its a design flaw.

So... here's how you do it.


[SIZE="2"]**1. Add your Application**[/SIZE]
First, you have to add your application so that Gnome Shell can find it. This can be done by creating a .desktop file. Run this command where **myapp** is the name you want to give your app.
```
sudo gedit /usr/share/applications/**myapp**.desktop
```

Now create the file with the following format:
```
Exec=/path/to/your/app %U
Version=1.0
Name=My First App
GenericName=MyApp
X-GNOME-FullName=My First Application
Comment=This app will do this and this
Icon=myapp-icon
StartupNotify=true
Terminal=false
Type=Application

```
The Icon value sets an icon to your application found in /usr/share/app-install/icons/
If you don't like any of the exiting icons, you can add your own! It's just a small .png image.


[SIZE="2"]**2. Find out what file type you want to associate**[/SIZE]
Right click your file, select Properties and look under Type, it should be something like *application/x-type*. Here's a screenshot! 

[[img]http://s4.postimage.org/266dgkuck/Screenshot.jpg[/img]](http://postimage.org/image/266dgkuck/)


[SIZE="2"]**3. Associate the file type with your application**[/SIZE]
Run the following command
```
sudo gedit /usr/share/applications/defaults.list 
```
Now add your file type (preferably in an alphabetically correct place) and link it to your application.
Example:
```
application/x-type=myapp.desktop
```


[SIZE="2"]**4. Logout and Login again**[/SIZE]
I think this is necessary (its not enough to just restart the Gnome-shell).

[SIZE="2"]**5. Done!**[/SIZE]
Enjoy just having to double-click your files to open with your favorite application.

---

### Post by MSwal2846 on 2011-11-01
Thanks, Kalaka!

This isn't working for me, though.

I need to invoke a wine application (MS Project 2003 for *.mpp files), so I generated my "desktop" file as follows:

[PHP]Exec=env WINEPREFIX="/home/mswallow/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\WINPROJ.EXE" %U
Version=1.0
Name=msproject2003
GenericName=msproject2003
X-GNOME-FullName=msproject2003
Comment=This app will open up the wine version of MS Project 2003
Icon=projectl.png
StartupNotify=true
Terminal=false
Type=Application[/PHP]

I notice that in the applications directory, it's the entry that has the ".desktop" fully qualified on it.  Also, I wonder if I'm specifying the "Exec" correctly.  Can you take a look?

I did make the change to the defaults.list file:  audio/x-musepack=msproject2003.desktop

Appreciate any help!

---

### Post by mc4man on 2011-11-01
There are several ways to do an Exec= for wine in a custom .desktop
If you are going to use a env of WINEPREFIX then don't "" your wine command.
Also the %U may not be good to have - *an anomaly of gnome 3 is that any .desktop tat doesn't have have an %<some letter> on the Exec= line will not show up in the r. click > properties > open with list, so you can try with it included or remove if need be, doesn't matter that much

So you could try this Exec= instead, if no go then try without the %U
```
Exec=env WINEPREFIX="/home/mswallow/.wine" wine C:\\\\Program\\ Files\\\\Microsoft\\ Office\\\\OFFICE11\\\\WINPROJ.EXE %U 
```
Or Try something like this, again with or without the %U

```
Exec=wine "C:\Program Files\Microsoft Office\OFFICE11\WINPROJ.EXE" %U
```

(Not a big fan of using defaults.list to set a new default, think it's better to do locally in ~/.local/share/applications/mimeapps.list for both Added & Default

You could also add a line to your .desktop that may provide some benefit
```
MimeType=audio/x-musepack;
```

Edit: if still having difficulty with either of the above you could try adding this to the .desktop, though shouldn't matter.
```
Path=/home/mswallow/.wine/dosdevices/c:/Program Files/Microsoft Office/OFFICE11
```

---

### Post by MSwal2846 on 2011-11-01
Thanks, mc4man,

Well, I've tried various incantations without success.  I think there's something more fundamental wrong.  When I compare properties for my entry against those already there, I get major differences:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206075&stc=1&d=1320176999[/IMG]

The one on the left is "standard" and the one on the right is mine.  

See what I mean?

---

### Post by mc4man on 2011-11-01
Your .desktop is missing a key line (at least as posted
The very 1st line needs to be
```
[Desktop Entry]
```

Here's an example of one I have for ImgBurn, note that I've not set any Mimetype= or Category= for this, no need for my use case (I just open ImgBurn, then do as I intend
```
[Desktop Entry]
Name=ImgBurn
Exec=env WINEPREFIX="/home/doug/.wine" wine C:\\\\Program\\ Files\\\\ImgBurn\\\\ImgBurn.exe 
Type=Application
StartupNotify=true
Path=/home/doug/.wine/dosdevices/c:/Program Files/ImgBurn
Icon=8074_ImgBurn.0

```

---

### Post by MSwal2846 on 2011-11-01
Thanks, again .... so I've updated the file to be

[PHP][Desktop Entry]
Name=msproject2003
Exec=env WINEPREFIX="/home/mswallow/.wine" wine C:/Program Files/Microsoft Office/OFFICE11/WINPROJ.EXE %U
Path=/home/mswallow/.wine/dosdevices/c:/Program Files/Microsoft Office/OFFICE11
GenericName=msproject2003
X-GNOME-FullName=msproject2003
Comment=This app will open up the wine version of MS Project 2003
Icon=projectl.png
StartupNotify=true
Terminal=false
Type=Application  
MimeType=audio/x-musepack[/PHP]

It's still not working and I still see a big difference in properties: 
 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=206089&stc=1&d=1320192737[/IMG]

Any other ideas?

---

### Post by mc4man on 2011-11-01
Try this - 
delete that file you've created  in /usr/applications

Open a terminal & go
```
gedit ~/.local/share/applications/msproject2003.desktop
```

Use this inside, save & exit gedit (copy & paste
```
[Desktop Entry]
Version=1.0
Type=Application
Exec=Exec=env WINEPREFIX="/home/mswallow/.wine" wine C:\\\\Program\\ Files\\\\Microsoft\\ Office\\\\OFFICE11\\\\WINPROJ.EXE 
Name=msproject2003
Icon=projectl.png
Comment=This app will open up the wine version of MS Project 2003
Path=/home/mswallow/.wine/dosdevices/c:/Program Files/Microsoft Office/OFFICE11
MimeType=audio/x-musepack; 
```

Then in same terminal
```
chmod u+x ~/.local/share/applications/msproject2003.desktop
```

Now browse to ~/.local/share/applications & d. click on the icon, see if it starts your app.

If that goes well then see what happens if you d. click on a .mpp
(it's possible your prog will open but not load the file - if so that can likely be fixed
If your prog doesn't open then that can also be fixed..

Edit: - in the future if you post a .desktop put it in a code box, not PHP

---

### Post by MSwal2846 on 2011-11-02
mc4man,

Excellent!  All works!

(Sorry for the php...)

---

### Post by mc4man on 2011-11-02
> **MSwal2846 said:**
> mc4man,

Excellent!  All works!

(Sorry for the php...)

There is a possible variation to your Exec= that you might try at some point.
It would only be needed if you were using unity, added the .desktop to the launcher & wanted to use Drag & Drop of .mpp files on to the icon.

If so & _they didn't open loaded_ in your prog then try adding this to the end of the Exec= line, **using a space after** .EXE
 ```
Z:%f
```

(For some reason when I tried copying your posted .desktop's from the php box they'd always produce a bad .desktop until I replaced all the lines, can't quite figure that one out...

---

### Post by MSwal2846 on 2011-11-02
Ok, got it ... I'll give that a try...

---

### Post by mrinvader on 2011-12-15
Any way to just re-enable the button/menu option? 

thanks!:confused:

---

### Post by Carambakaracho on 2012-02-14
First, thank you so much, mc4man. I must open my movies with avidemux and it turned out not to be in the list of suggested software for video/x-msvideo files. Moreover, the button to simply add it there has obviously disappeared.

[QUOTE=mrinvader]Any way to just re-enable the button/menu option?[/QUOTE]
This were too easy then. Apparently Gnome3 devs and Ubuntu with them take a way where you either go back to editing text files as Linux users did back then or you capitulate because it became too complicated (in contrast to being so simple previously)

I do not understand this decision at all

---

### Post by MSwal2846 on 2012-02-14
I completely agree.  They've made this way too cumbersome.  It's ridiculous.  Usability, guys, usability!

---

### Post by ami7878 on 2012-03-04
First, I would like to thank you on this post. It was very helpful.

> **kalaka said:**
> 
[SIZE="2"]**4. Logout and Login again**[/SIZE]
I think this is necessary (its not enough to just restart the Gnome-shell).


I think that you don't need to logout and login again. What worked for me is right click the file and select properties. Then, in the "Open With" tab, I pressed the Reset button and that did the trick :)

---

### Post by alfem on 2012-09-25
I have cooked this little script to allow our users to open a file with a program of their choice (in Gnome3)

[https://github.com/gecos-team/openwith](https://github.com/gecos-team/openwith)

---

