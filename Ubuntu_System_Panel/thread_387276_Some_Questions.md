---
title: "Some Questions"
date: 2007-03-18
forum: Ubuntu System Panel
---

### Post by shiversc on 2007-03-18
Hello an sorry for my bad english.

1. In USP1 it was possible to add the "System Management" left in the "Side Pane". Can I add in USP2 the buttons too?

2. What's the name of the pane where I can choose  "GTK-Theme" and "Resolution"... etc? USP2 don´t have this by default.

3. After sometime using USP2 with the "Terminal-Plugin" in my taskmanager I have a lot of "bash". Why? And how can i get this away? Look at screenshot one. "Schläft" means sleep.

4. Sometimes a window is poping up an say's: "This problem report does not apply to a packaged program. (/usr/bin/usp)" Look at  Screenshot two. [[IMG]http://img175.imageshack.us/img175/4913/bashuz6.th.jpg[/IMG]](http://img175.imageshack.us/my.php?image=bashuz6.jpg)
[[IMG]http://img294.imageshack.us/img294/2555/probos8.th.jpg[/IMG]](http://img294.imageshack.us/my.php?image=probos8.jpg)

---

### Post by Malac on 2007-03-18
> **shiversc said:**
> Hello an sorry for my bad english.

1. In USP1 it was possible to add the "System Management" left in the "Side Pane". Can I add in USP2 the buttons too?

2. What's the name of the pane where I can choose  "GTK-Theme" and "Resolution"... etc? USP2 don´t have this by default.

3. After sometime using USP2 with the "Terminal-Plugin" in my taskmanager I have a lot of "bash". Why? And how can i get this away? Look at screenshot one. "Schläft" means sleep.

4. Sometimes a window is poping up an say's: "This problem report does not apply to a packaged program. (/usr/bin/usp)" Look at  Screenshot two. [[IMG]http://img175.imageshack.us/img175/4913/bashuz6.th.jpg[/IMG]]("http://img175.imageshack.us/my.php?image=bashuz6.jpg")
[[IMG]http://img294.imageshack.us/img294/2555/probos8.th.jpg[/IMG]]("http://img294.imageshack.us/my.php?image=probos8.jpg")

1. Create 4 shortcuts pointing to the System Management values:[ATTACH]27730[/ATTACH]
Then use "Compact List" to add these to the sidepane.[ATTACH]27731[/ATTACH]

2. The name is "computer" (without the quotes).

3. Unfortunately this is a bug in the terminal plugin which recreates a terminal session every time a reload is done. See Below.

4. On Feisty the crash report is _very_ sensitive to any bad output we are trying to track these down at the moment.

---

### Post by Malac on 2007-03-18
3. Terminal multiple bash bug now fixed . Download replacement files from post #2 of plugins thread.

---

### Post by shiversc on 2007-03-18
Thank you very much for your help. You're great.

After add "gnome-session-save --kill" to the compact list, there no no button for reboot, logout ... etc. what ist wrong?

---

### Post by Malac on 2007-03-18
> **shiversc said:**
> Thank you very much for your help. You're great.

After add "gnome-session-save --kill" to the compact list, there no no button for reboot, logout ... etc. what ist wrong?
Open gedit and paste this in to a new file:
```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Comment=Quit
Exec=gnome-session-save --kill
Icon=gnome-logout
Name=Quit
Terminal=false
```
Save it as Quit.desktop somewhere you can get it.
Add this file to the Compact List.

Do the same for each one replacing:
"Comment=" comment
"Exec=" command
"Icon=" icon
"Name=" name
with different values and save then as Lock.desktop, Install.desktop, etc.

---

### Post by shiversc on 2007-03-19
I'll give a try. Thank you very much.

Now my USP2 looks good. But a little thing...

After add "computer" to the list, I have no tab in the USP - Configuration tool. My "computer" pane ist alle liitle bit to small. Can i do something?

---

### Post by Malac on 2007-03-19
> **shiversc said:**
> I'll give a try. Thank you very much.

Now my USP2 looks good. But a little thing...

After add "computer" to the list, I have no tab in the USP - Configuration tool. My "computer" pane ist alle liitle bit to small. Can i do something?
It's titled "**Settings**" or "**Einstellungen**" :). Sorry for the confusion.

---

### Post by shiversc on 2007-03-19
Ohh, an german word. Great. 8-) 

In my settings tab is it not possible to change the width.

---

### Post by Malac on 2007-03-20
> **shiversc said:**
> Ohh, an german word. Great. 8-) 

In my settings tab is it not possible to change the width.
Sorry computer.py is a fixed width plugin.
Can you give a screenshot of what it looks like on your system and why it's too narrow.

---

### Post by shiversc on 2007-03-20
[[IMG]http://img513.imageshack.us/img513/2892/blubjc2.th.png[/IMG]](http://img513.imageshack.us/my.php?image=blubjc2.png)

---

### Post by Malac on 2007-03-20
Okay I have uploaded a new computer.glade and computer.py to the SVN(Revision 212) which allows choosing font size of information as well as main button title. Added changing width option to uspconfig/Preferences section.

Resolution is picked up from /desktop/gnome/screen/default/0/resolution in gconf-editor this sometimes doesn't get set automatically so you will have to do it yourself.
Here is a screenshot of my gconf section:[ATTACH]27917[/ATTACH]

Hope this helps.

---

### Post by shiversc on 2007-03-22
Pice for pice works better for me.

But, i've no "/desktop/gnome/**screen**/default/0/resolution" in gconf-editor! Why?

In the "Settings" tab i've add for "Control Center" "gnome-control-center". But i've no action, when ich klick in the "Settings" pane. Can you help me?

In my "places" pane there shortcuts to my webserver. In nautilus i can klick and all is allright. In USP pop an error up an says: "»/home/fawn/123456-78@www.xxxx.xxx:21/xxx« konnte nicht gefunden werden." "Bitte prüfen Sie die Rechtschreibung und versuchen Sie es noch einmal." It meens that USP can find the werbserver and I should ceck my spell!

I want to change the "distributor-logo". Where I've to place the new logo?

Sorry for my bad english.

---

### Post by Malac on 2007-03-22
.double post

---

### Post by Malac on 2007-03-22
> **shiversc said:**
> But, i've no "/desktop/gnome/**screen**/default/0/resolution" in gconf-editor! Why?Sorry I don't know but it is a known bug.
> **shiversc said:**
> In the "Settings" tab i've add for "Control Center" "gnome-control-center". But i've no action, when ich klick in the "Settings" pane. Can you help me?Have you clicked "Reload Plugins". This works on mine.
> **shiversc said:**
> In my "places" pane there shortcuts to my webserver. In nautilus i can klick and all is allright. In USP pop an error up an says: "»/home/fawn/123456-78@www.xxxx.xxx:21/xxx« konnte nicht gefunden werden." "Bitte prüfen Sie die Rechtschreibung und versuchen Sie es noch einmal." It meens that USP can find the werbserver and I should ceck my spell!Is this in bookmarks or is it a ssh pipe. Try making the command line [SIZE=4]**"**[/SIZE]/home/fawn/123456-78@www.xxxx.xxx:21/xxx[SIZE=4]**"**[/SIZE] and see if that helps. If not you may need to insert the program name in front of it e.g "firefox http://www.ubuntu.com". I'm not sure without seeing the shortcut itself.
> **shiversc said:**
>  I want to change the "distributor-logo". Where I've to place the new logo?/usr/share/icons/[COLOR=DimGray]*<name-of-theme>*[/COLOR]/scalable if .svg file or in the relevant /usr/share/icons/[COLOR=DimGray]*<name-of-theme>*[/COLOR]/[COLOR=DimGray]*00*[/COLOR]x[COLOR=DimGray]*00*[/COLOR]/apps folders

---

### Post by shiversc on 2007-03-22
I have the Problem with FTP and SSH Pipes.

---

