---
title: "[HOWTO] Configure Unity 2D to Simulate Unity 3D"
date: 2011-05-03
forum: Tutorials
---

### Post by Entyrion on 2011-05-03
**For computers that cannot run Unity 3D, but ARE capable of running Compiz (yes, they exist! [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/758747](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/758747))**

Stuck with an older or less powerful machine that can't run Unity 3D with your newly upgraded 11.04 machine? Don't worry, you can still experience Unity and replicate most of the eye candy of the fancy 3D version! I'm a Linux and Ubuntu noob and I started from scratch when trying to customize my new UI. After sifting through LOTS of forums and websites and teaching myself a little bit about CompizConfig Settings Manager (and a couple other tools) along the way, I was able to get my Unity 2D interface to look just like its 3D big brother!

Because it involved a lot of trouble for me (as a complete noob), I figured I'd create my first "how to" guide to make it easier for other not-so-experienced Ubuntu users to customize their own Natty Narwhal machines. Please feel free to post new ideas, tips, questions, corrections, or problems regarding my guide or any additional customizations! I'll also keep this thread up to date with additional tips for other features I add in the future.

One note on my approach to compiling this guide -- I'm a noob, so I like GUIs. Manually editing config files is not my thing. Whenever possible, I will include instructions for using available GUI-based configuration tools in favor of going through and editing config files line by line. Yes, it will entail a few extra steps and yes I'm sure much more experienced and technically adept Linux pros can open up gconf-editor or some other not-so-noob-friendly tool and achieve these things more efficiently. Like I said, I want to make this as friendly as possible to new and inexperienced users (like me!) who still want to get the most out of their Unity 2D experience. I've also tried to include links to the other sources I used or the forum threads I created to discuss each specific issue so you can read more on your own if you want!

*As a heads-up, if changes you apply using these steps don't seem to be immediate, first try logging out and back in and/or restarting your computer. Then double-check to see if the settings have taken effect. If they have not, make sure that the setting changes have been saved.

*Also, before you get into heavy-duty CompizConfig editing, I would recommend backing up the default config profile and remember to save the changes you make to your custom config file frequently so you can come back to it if you tweak something and it doesn't work. The details of how to do this are part of step 7, in the guide provided via the link there.

*A quick note on my notation. When I type something like: "enter the value "title=unity-2d-panel" into window xyz"
I mean type the value exactly as it appears WITHIN the quotes; the quotes themselves should be omitted :)

**IT IS IMPORTANT TO NOTE THAT THIS HOWTO IS ONLY APPLICABLE TO A SPECIFIC DEMOGRAPHIC OF COMPUTER USERS! THIS GUIDE IS SPECIFICALLY TAILORED FOR USERS WITH A COMPUTER THAT IS CABABLE OF RUNNING COMPIZ, BUT DOES NOT QUITE MEET THE REQUIREMENTS FOR UNITY 3D! If you have OpenGL 1.4+ and meet all the other requirements (see step 1 below), then you can simply use the 3D version of Unity. If your computer is not capable of running Compiz, then you can still install Unity 2D (see steps 1-3), but you will not be able to use Compiz to modify any of the effects or appearance options. I DO know this user demographic exists because I fall into it (along with other ATI Radeon RV250 users)... I can run Compiz, but I only have OpenGL 1.3, so Unity 3D cannot run. There have also been at least a few bug reports of this as noted at [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/758747](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/758747) so for those that fall into this small club, I hope this can help!

I customized my Compiz and Unity 2D interface with the following features, which I'll do my best to walk through:
	- toggle launcher auto-hide
	- enable transparent menus
	- enable wobbly windows
	- enable cube desktop
	- dodge focus window setting
	- open/close/max/min windows effects
	- unity launcher transparency
	- remove "workspaces" icon from launcher

1. Verify Unity 3D compatibility. 
([http://ubuntuforums.org/showthread.php?t=1747367#7](http://ubuntuforums.org/showthread.php?t=1747367#7))
Open the terminal and type in: ```
/usr/lib/nux/unity_support_test -p
``` If the output says "Unity supported: no" then you'll need to use Unity 2D if you want Unity at all. If it says "yes," then enjoy using Unity 3D! This guide is not for you =P

2. Install Unity 2D. 
([http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html](http://www.webupd8.org/2011/01/unity-2d-qt-now-available-in-ppa-for.html))
For 11.04 machines, all you need to do is open a terminal and type in ```
sudo apt-get install unity-2d-default-settings
``` If you use 10.10 the process is slightly more complicated; you can find the 10.10 procedure at the link above. After you install Unity 2D, you will probably want to restart your computer. When you log back in, the "Ubuntu" session should now default to Unity 2D. If for some reason it does not, simply relog and select "Unity 2D" from the session menu.

3. Install "2D-Desktop Settings" -- a bare-bones GUI for configuring Unity 2D. 
([http://marianochavero.wordpress.com/2011/04/20/a-simple-gui-for-unity-2d-settings-ubuntu-11-04/](http://marianochavero.wordpress.com/2011/04/20/a-simple-gui-for-unity-2d-settings-ubuntu-11-04/))
This GUI is very simple. You can install it from the link above, or by searching "2d desktop settings" in the Ubuntu Software Center. Once it is installed, make sure that the bottom 3 check boxes are enabled and set the Launcher Preferences to the setting you prefer (I chose Auto-Hide). Make sure the behavior you just toggled is working. If not, relog and double-check.
	[x] toggle launcher auto-hide

4. Create a desktop launcher to manually enable Compiz in your Unity 2D session.
([http://ubuntuforums.org/showthread.php?p=10764332#post10764332](http://ubuntuforums.org/showthread.php?p=10764332#post10764332))
Right-click anywhere on your desktop and select "Create Launcher..." "Type" should be "Application" and "Command" should read "compiz --replace" you can name it whatever you want and include a comment if you like.

Now, every time you boot into Ubuntu, Unity 2D should be enabled and Compiz should be disabled. Whenever you want to enable Compiz features, double-click this launcher. Your UI should go blank and reload with the Compiz features up and running. Make sure that Compiz is enabled before going on (and if you relog at any point, make sure you turn it back on before you start customizing again).

5. (optional) Install CompizConfig Settings Manager (aka "ccsm"). 
This can be done by searching "ccsm" in the USC. Make sure you install the one named "Advanced Desktop Settings Manager (ccsm)" -- the Simple version is broken in 11.04 at the moment. When you install Ubuntu Tweak (below), there should be an option for Tweak to install this automatically for you, but if not, you can always follow this process to do it manually.

6. Install and run Ubuntu Tweak.
([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/))
Either install from the link above, or search for "ubuntu tweak" and install "Ubuntu Configuration Tool" in USC. Once it is installed, run the program and click on the "Compiz Settings" menu under "Desktop" on the left-hand side of the Ubuntu Tweak window. Check the boxes for "Enable wobbly windows" (this will automatically disable the snapping windows feature) and "Enable transparent menus." I also have the "Make the launcher hide automatically after some time inactive" box checked for good measure, but this setting should have no effect either way (since Unity 2D is not a Compiz plugin). Once these two things are checked off, quit Ubuntu Tweak and make sure they work. Relog if you have to (remember to use that Compiz launcher when you get back) and check again.
	[x] enable transparent menus
	[x] enable wobbly windows

7. Enable desktop cube by modifying the CCSM config file.
([http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/))
This guide is quick and easy to follow. Yes, it involves modifying a config file, but at the moment its the only way I found. Fortunately it isn't too diffucult. Simply follow the instructions listed on that omgubuntu link. While following these instructions, take special care to follow their recommended process for backing up the default config file and creating a new one for you to edit (this saved my butt several times)!

One piece of advice. If you're having trouble finding or modifying the hsize and vsize values in the config file in that guide, you can use the GUI to modify those values. Preferably before you modify the active_plugins values (though I'm not sure if it matters... I changed the workspace layout in the GUI before I ran across the guide), just run CCSM and go to General > General Options > Desktop Size and use the sliders there to change the horizontal slider to 4 and vertical to 1. After this is done, follow the omgubuntu instructions and omit the part where you edit the hsize and vsize vaules in the config file.
	[x] enable desktop cube

8. Use CCSM to enable and modify window animations.
([http://ubuntuforums.org/showthread.php?t=1745039](http://ubuntuforums.org/showthread.php?t=1745039))
Run CCSM and go to Effects > Animations (make sure this box is checked). There will be tabs for each window scenario (open, close, minimize, focus, etc). The top line in each of these should include "type=Normal" this is what you want to edit for the general behavior of generic windows. Double-clicking on this "type=Normal" line for each window scenario you want to edit will let you pick specific animations to use or select "Random" and the check boxes below the list will let you determine exactly what random effects Compiz can choose from. I set open, close, and minimize to "Random" and focus to "Dodge" and left Shade alone. This is a matter of personal taste, but I would also recommend increasing the duration to about 300 or so; it seems to make the animations look smoother and nicer IMO.
	[x] dodge focus window setting
	[x] open/close/max/min windows effects

9. Use CCSM to selectively edit the opacity of Unity 2D panel, places, and launcher.
([http://ubuntuforums.org/showthread.php?t=1746381](http://ubuntuforums.org/showthread.php?t=1746381))
Run CCSM and go to Accessibility > Opacity, Brightness, and Saturation (this box should already be checked if you used Ubuntu Tweak to enable transparent menus, if not, turn it on) > Opacity tab. In the "Window specific settings" list, there should already be one item (assuming you enabled transparent menus with Ubuntu Tweak), if you want to make your menus more or less transparent, you can always change the percentage value here, otherwise, leave this line alone. To modify the opacity of each of the 3 Unity 2D elements independently, we'll need to add 3 new items to that list. Click "New" and type in "title=unity-2d-panel" This will be for the top bar in Unity. Set the opacity to whatever you like. You can edit this value at any time by double-clicking on the item in the list. Use the "New" button twice more, adding "title=unity-2d-launcher" (the sidebar on the left-hand side with all your icons) and "title=unity-2d-places" (the window that pops up with your list of applications and stuff when you hit the Ubuntu/Windows/Super button). Add opacity values to these as you're creating them. There you go! You can edit each of these 3 opacity values at any time by double-clicking on them in the list. Tweak them until you have them just right :)
	[x] unity launcher transparency

10. Remove the unused/broken "workspaces" icon from the launcher.
([http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html](http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html))
For me, the workspaces icon on the launcher seemed to break, I'm guessing when I changed the workspace layout to 4x1 instead of 2x2. In any case, I didn't use it anyways and I though it took up too much space and added clutter to the launcher. If you'd like to remove that (or any other permanent icons) or tweak them, I would recommend following the procedure listed on the ubunturoot link above. Unfortunately, it does require some config file editing, but it isn't too in-depth. EDIT: Note that whenever your Update Manager updates Unity 2D, it will replace the Launcher.qml file you edit to do this, restoring the broken Workspaces icon in the process. If you want to eliminate that pesky icon, you'll need to repeat this process after each Unity 2D update is applied.
	[x] remove "workspaces" icon from launcher

After you've gotten everything to look the way you want, make sure to save your settings to your modified config file (as mentioned in step 7) and reboot your machine. After you log into Unity 2D and activate your Compiz launcher, you should be all set with a brand new pro interface and plenty of eye candy!

If you were interested in tweaking other minor things with the launcher, the ubunturoot link in step 10 also includes other steps for things like changing the launcher icon size and background image, etc. I haven't done any of them myself, but if might be a great place to start if you're interested in additional customization. I hope my guide might be helpful to at least a few people out there who find themselves in the same situation I'm in: a computer decent enough to run Compiz, but not quite good enough to meet the Unity 3D requirements! Good luck customizing and let me know what you think!

---

### Post by Entyrion on 2011-05-09
Update:
([http://ubuntuforums.org/showthread.php?t=1744455](http://ubuntuforums.org/showthread.php?t=1744455))

I recently found a thread at the link above that allowed me to eliminate the manual Compiz launcher I created in step 4 of this guide. I like a clean desktop, so I prefer not to have any icons cluttering it up whenever possible. If you also prefer a minimalist look I would recommend it. However, if you prefer the flexibility of enabling Compiz manually, you might want to keep the launcher. It might also be helpful to use the launcher as outlined in step 4 above during the setup and troubleshooting process and only delete the launcher and use the script after everything is set up and working smoothly. That said, here is the new procedure:

1. Navigate to your Home folder, or any sub-folder you prefer and create the script below by right-clicking > Create Document > Empty File. (I have a folder within Home called "Stuff" for random junk, I just put it in there for example.) Name it something like "Enable Compiz" or whatever you like, then open it in gedit (gedit will be the default program). Insert the script below and save the file.

```
#!/bin/bash

sleep 15
compiz --replace
```

2. Right-click the script file and go to Properties > Permissions tab. Make sure "Allow executing file as a program" is checked. Then close the window.

3. Open the Startup Applications program (in Unity 2D just hit the Ubuntu/Windows/Super button and search for "startup").

4. Click "Add" and name it whatever you like (something like "auto-enable compiz"). Under "Command" click "Browse..." and find the file path to the script you just created. Add a comment if you want for future reference.

5. Once the script is added to the startup list, make sure it is checked and close the Startup Applications window. You can now delete the manual launcher if you like. Restart your computer and Compiz should automatically run 15 seconds after startup!

If Compiz boots too soon, it can cause the UI to look funny. If your machine takes more than 15 seconds to boot up, you can edit the script to "sleep X" where X is the number of seconds you want Compiz to wait (I personally set it to sleep 20 because my computer boots up a bit slow).

There you have it! I hope this is helpful :)

As an additional addendum, I would also recommend visiting the link at the bottom of the thread linked above ([http://jaket.is-a-geek.com/blog/linux/remove-titlebar-on-maximized-windows-with-compiz](http://jaket.is-a-geek.com/blog/linux/remove-titlebar-on-maximized-windows-with-compiz)). There are instructions here to get rid of the duplicate titlebar on maximized windows when running Compiz (this will restore the appearance back to Unity default).

---

### Post by Rubi1200 on 2011-05-09
Thank you Entyrion for creating this guide. I am sure there are many users who will find this useful.

Nice job :-)

---

### Post by geazzy on 2011-05-09
very nice guide.... :D

---

### Post by hadobac on 2011-07-14
Tho apparently, my shitty Latitude d620 is still able to run Unity 3d, the 2d version is real epic. The lens opens incredibly fast, the effect of the dock with composition looks even better than its laggy equivalent.

If only Unity 2d had its dock resized a bit less and alway shown, I would stick with it, w/o any hesitation.

---

### Post by Trespasser on 2011-08-20
Nice guide. I applaud your effort. One request...please update this thread when you discover new info.

Thanks again.

Later...

---

### Post by Neodarkness on 2011-09-23
Awesome guide and awesome updates!
Note: this is useful to people that can run Unity 3D too, as Unity-2D + compiz is faster.

---

### Post by pme 72 on 2011-09-24
Entyrion, thank you. This morning I installed VirtualBox and Natty in my Lucid installation and found Unity was not an option. With Unity 2D now it is. Thank you again.

3D Unity works for me from a Live CD. If I upgrade to or install Natty it might work just fine.

---

### Post by suryateja.sun on 2011-10-01
Thanks for the wonderful guide.

I found now that from step 1, I can use unity 3D. I am using unity 2D. How to rollback to Unity 3D? What packages need to be installed to get full version? I am using ubuntu 11.04.

---

