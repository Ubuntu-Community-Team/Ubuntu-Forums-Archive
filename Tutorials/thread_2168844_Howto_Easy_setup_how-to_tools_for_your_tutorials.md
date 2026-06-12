---
title: "Howto: Easy setup how-to tools for your tutorials"
date: 2013-08-19
forum: Tutorials
---

### Post by hakermania on 2013-08-19
The Ubuntu Community has these Forums and AskUbuntu for support.

If you want to give decent answers and really help all the users (even the beginners), you should probably provide images and even files describing what you're talking about.

But, snapping a screenshot, editing it, uploading it to an image hoster are all time-consuming tasks.

In this tutorial I will talk about **how to install simple programs that will help you building your tutorials. This is NOT only for building your tutorials or answers, but also for sharing images and text quickly to everyone across the web. **

I am working under **Ubuntu 13.04** but this tutorial will also guide you on how to add these actions on keyboard shortcuts, in case you use some other environment. The right click shortcuts actions are only available on systems that run Unity.

How your setup will look like at the end of this tutorial:

[IMG]http://i.imgur.com/aDIG75L.png[/IMG]

[IMG]http://i.imgur.com/DMKhDxL.png[/IMG] 
The first 4 options on the dropdown menu will start Shutter which will immediately prompt you to select part of the screen. The first 2 of them will just take a simple screenshot while the last 2 will edit the image first with Shutter's editor. After you hit the 'Save' button on Shutter's editor then the image is uploaded to **imgur.com**. The word 'Delete' means that the image will be automatically removed from your hard drive once the image is successfully uploaded to imgur.com. The direct link to the image is pasted to your clipboard (and thus available anytime via Ctrl+V). If you don't delete your image, it will stay at ~/Pictures/ folder.

As for the 'Paste Online' option, it pastes your clipboard contents at paste.ubuntu.com and updates your clipboard with the corresponding direct link to paste.ubuntu.com.

Mention that this tutorial was built using the above setup.

So, first of all, install what you will need:
```

sudo apt-get install libnotify-bin xclip curl shutter pastebinit

```
libnotify-bin: For displaying notifications through bash scripts
xclip: For clipboard operations
curl: For imgur.com uploading
shutter: For screenshot capturing
pastebinit: For pasting to paste.ubuntu.com your text

Please after the installation of all the appropriate packages, run Shutter **at least once** to let it initialize/update its plugins.

[SIZE=3]**If you work with Unity (if you work with Unity but you prefer keyboard shortcuts please go to the next section):**
[/SIZE]
If you work with unity the best thing that you could do so as to have easy access to these actions is to create right click menu on a desktop launcher on the unity sidebar.

First of all, here is my **custom gnome-terminal.desktop** file:

[http://paste.ubuntu.com/6003743/](http://paste.ubuntu.com/6003743/)

Notice that adding these shortcuts to the gnome-terminal desktop file is NOT your only option. You may add these actions to any desktop file visible at your Unity sidebar.

Please save the above file as gnome-terminal.desktop and replace the string [COLOR=#000000]/home/alex with the corresponding user directory of yours (there are 5 occurrences) (e.g. /home/bongdacity). Move that file to /usr/share/applications/.

This requires root privileges. You can move the file either by terminal or by nautilus run by root. Place gnome-terminal.desktop to your home directory, open the terminal (Ctrl+Alt+T) and give

```
sudo mv gnome-terminal.desktop /usr/share/applications/
```

Fill in your password.

A more user friendly approach is running in a terminal

```
gksudo nautilus
```

and then manually moving gnome-terminal.desktop to /usr/share/applications/. Please be very careful when you run nautilus with root privileges, a drag and drop can destroy your system if you are not careful.
[/COLOR]
[SIZE=3]**If you don't work with Unity or you prefer using keyboard shortcuts:**
[/SIZE]
If you don't work with Unity the best thing to do in order to have access to these actions is to setup keyboard shortcuts that will launch each one of these actions[SIZE=2].
[/SIZE][SIZE=3]
[/SIZE]Almost every system has a way to setup your own keyboard shortcuts. For example, in Ubuntu this is under System Settings -> Keyboard -> Shortcuts -> Custom Shortcuts. There you can setup your own custom keyboard shortcuts. You can choose whatever shortcuts you like for each actions, but I would go with Ctrl+Shift+1 till 5. These are the commands that should be executed each time:
Take screenshot: /home/alex/Documents/Scripts/screenshot.sh js
Take screenshot (Delete): /home/alex/Documents/Scripts/screenshot.sh sd
Take screenshot (Edit): /home/alex/Documents/Scripts/screenshot.sh se
Take screenshot (Edit&Delete): /home/alex/Documents/Scripts/screenshot.sh sed

Please on the above commands **replace the word alex** with your own username.[SIZE=3]

**Wherever you work, continue reading:**[/SIZE]

Now, it is the time to create the directory that will contain the scripts that will be executed for the above actions.

First of all, create the directory ~/Documents/Scripts/

Inside this directory, place the following files and **give them the corresponding names**

screenshot.sh -> [http://paste.ubuntu.com/6003831/](http://paste.ubuntu.com/6003831/)
imgur.sh -> [http://paste.ubuntu.com/6003767/](http://paste.ubuntu.com/6003767/)
pastebin.sh -> [http://paste.ubuntu.com/6003783/](http://paste.ubuntu.com/6003783/)

screenshot.sh: It launches shutter using the appropriate command line arguments. Also, it edits shutter's configuration files to satisfy the Open with Build-in Editor option of Shutter or not, which doesn't have a command line option. Also, it calls imgur.sh for uploading the picture, xclip for saving the link to your clipboard. It removes the local picture if needed.

imgur.sh: A script that uses curl to upload a picture to imgur.com. It takes as an argument a local picture and returns an imgur.com link.

pastebin.sh: Reads your input from the clipboard, it pastes it to (ubuntu.)pastebin.com and then updates your clipboard with the remote link. These are done solely with the help of xlip and pastebinit.

DO NOT forget to give the above scripts the executable bit (select the above 3 files in nautilus -> right click -> properties -> permissions tab -> Click on the 'Allow executing file as program' twice so as to show the tick mark) so as to be executed through the unity or keyboard shortcuts that you have set up.

Now you should be good to go :)

---

### Post by vasa1 on 2013-08-19
Thanks for the tutorial. I have a couple of clarifications to ask of you:
[LIST]
[*]You have mentioned Ubuntu 13.04 but could you broaden it to include other official DEs such as Lubuntu, Xubuntu, etc? (I suppose KDE would be out of the picture.) I'm asking because you have specified "gnome-terminal" and your custom gnome-terminal.desktop has several "OnlyShowIn=Unity" lines.
[*]Is it necessary to move the custom gnome-terminal.desktop to `/usr/share/applications`? Why do you prefer that (system-wide) over `~/.local/share/applications`?
[/LIST]

---

### Post by hakermania on 2013-08-20
> **vasa1 said:**
> Thanks for the tutorial. I have a couple of clarifications to ask of you:
[LIST]
[*]You have mentioned Ubuntu 13.04 but could you broaden it to include other official DEs such as Lubuntu, Xubuntu, etc? (I suppose KDE would be out of the picture.) I'm asking because you have specified "gnome-terminal" and your custom gnome-terminal.desktop has several "OnlyShowIn=Unity" lines.
[*]Is it necessary to move the custom gnome-terminal.desktop to `/usr/share/applications`? Why do you prefer that (system-wide) over `~/.local/share/applications`?
[/LIST]


Well, the point is to have a quick right-click menu, easily accessible from somewhere. The only way to broaden this is to setup keyboard shortcuts to execute each command. This is a good idea, and I will add it to the tutorial, thanks.

The gnome-terminal desktop file has multiple OnlyShowIn=Unity entries because that is the official way to create static right click menus for the unity launcher for a specific desktop file (these actions are not visible in any other desktop environments, as far as I know).

As for moving the gnome-terminal.desktop to /usr/share/applications/ instead of the user directory ~/.local/share/applications, it is done in order to replace the old gnome-terminal file with the new one, so as to prevent any conflicts.

---

