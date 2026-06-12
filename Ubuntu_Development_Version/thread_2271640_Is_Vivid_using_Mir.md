---
title: "Is Vivid using Mir?"
date: 2015-03-31
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-03-31
I tried to open Dconf-editor through lightdm.```
** (dconf-editor:2527): WARNING **: Could not open X display
No protocol specified
gdk_mir_display_open
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(dconf-editor:2527): Gtk-WARNING **: cannot open display: :0
```

I was trying to get the dotted grid disabled the way I did it in Trusty, but cannot do that in Vivid this way.

---

### Post by Frogs Hair on 2015-03-31
No, but Unity8/Mir is available for testing. There is a check box in the dconf editor under unity>unity greeter>draw grid.

---

### Post by Chanath on 2015-03-31
> **Frogs Hair said:**
> No, but Unity8/Mir is available for testing. There is a check box in the dconf editor under unity>unity greeter>draw grid.

That doesn't work.

Anyway, please notice the part;
```
gdk_mir_display_open
``` 

and, ```
Failed to connect to Mir
```
I wasn't trying to connect to mir, but lightdm was.

Also:
```
$ ps afx | grep unity-system-compositor
 2266 pts/1    S+     0:00                  \_ grep --color=auto unity-system-compositor
```

which most probably means that Vivid is running Mir.

Checked with Synaptic. It shows there is a package ** mir-client-platform-mesa2** installed.

---

### Post by Frogs Hair on 2015-03-31
The setting failed for me as well. When I run the top command to it appears that Xorg and Compiz are running with no sign of Mir  however synaptic indicates some Mir libs installed. Maybe some one can clarify this.

Edit: I was able to disable the grid via Ubuntu Tweak, but not via the grid check box in dconf editor. ???

---

### Post by Chanath on 2015-03-31
> **Frogs Hair said:**
> The setting failed for me as well. When I run the top command to it appears that Xorg and Compiz are running with no sign of Mir  however synaptic indicates some Mir libs installed. Maybe some one can clarify this.

I had additionally installed Gnome-Flashback. I find everything works faster in Flashback than in Unity. I have also installed the old Slingshot Launcher, so I have a Dash-like menu with categories. One panel is kept and it is auto hidden, so I have full screen for me. I am debating with myself, whether to keep Unity or completely uninstall it. And, I am using Flashback-Compiz.

---

### Post by Mateusz Stachowski on 2015-03-31
Vivid isn't running Mir. You only have Mir by default in Ubuntu Desktop Next image the regular image is still using Unity 7 and X server.

Besides the command that you list isn't for checking if Mir is running. That command was for checking XMir back in the days that Ubuntu devs wanted to switch to XMir as default (it was planned for 13.10).

This [question on AskUbuntu]("http://askubuntu.com/questions/330862/how-do-i-find-out-if-my-system-is-using-mir") has some good answers especially by Jorge Castro and Stephen M. Webb (both are Ubuntu developers). Stephen starts his answer from stating that Mir is just a set of libraries and that's what you see installed in Vivid. A set of Mir libraries which on their own don't get you to running Mir. There are also binaries but those definitely aren't installed in Vivid by default.

---

### Post by Chanath on 2015-03-31
> **Frogs Hair said:**
> Edit: I was able to disable the grid via Ubuntu Tweak, but not via the grid check box in dconf editor. ???

Yes, it got rid of the grid. It also got rid of the pinkish background colour. 
Unity: I'd keep it until the final release day, and if it won't be faster than Flashback-Compiz, I'd uninstall it. The idea is to find the apps and start them quickly. Slingshot is doing it quicker. If there is app like the Whisker menu, I'd happily use it on Ubuntu.

PS: Thanks Mateusz_[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1040945")_

---

### Post by grahammechanical on 2015-03-31
From what I have heard Unity 8 is Unity 7 re-written to run on Mir. If Ubuntu had already switched to Mir then we would be running Unity 8 and Unity 8 is not yet ready for desktop use. As any install of Unity8 Desktop Next will prove.

I saw systemd libraries long before the switch was made from upstart to systemd. I see nothing wrong with getting Mir libraries in advance especially as it has been stated that 16.04 will have the option to load with either unity 7 or 8. There will have to be some co-existence. Also with Wayland stuff. If it is open source and if it is useful, then why not use it?

---

### Post by Frogs Hair on 2015-03-31
> Mir is just a set of libraries and that's what you see installed in  Vivid. A set of Mir libraries which on their own don't get you to  running Mir. Thanks , that's what I suspected.

---

### Post by Hazzabin on 2015-03-31
> **Chanath said:**
> Yes, it got rid of the grid. It also got rid of the pinkish background colour. 
Unity: I'd keep it until the final release day, and if it won't be faster than Flashback-Compiz, I'd uninstall it. The idea is to find the apps and start them quickly. Slingshot is doing it quicker. If there is app like the Whisker menu, I'd happily use it on Ubuntu.

PS: Thanks Mateusz

I have found 'Flashback-Compiz' works beautifully in Unity setup and maybe even just a tad better than flashback-compiz does in Gnome, just my opinion is all :)

---

