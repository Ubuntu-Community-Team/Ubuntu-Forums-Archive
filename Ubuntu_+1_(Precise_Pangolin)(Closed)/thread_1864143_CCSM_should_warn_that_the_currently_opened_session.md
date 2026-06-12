---
title: "CCSM should warn that the currently opened session is 2D"
date: 2011-10-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-10-18
There are users cutting/pasting every command they can find on the forum in an attempt to make CCSM changes work. But they're using Ubuntu  2D.........

A little warning dialog in ccsm like: "Settings will only be applied when you start a 3D session. This is Ubuntu 2D." would help.



[ATTACH]204743[/ATTACH] 
[SIZE=3]It looks like you're trying to apply 90% 
transparency to Any & !(Any)? Good...[/SIZE]

---

### Post by ventrical on 2011-10-18
An example of that is the new little program called wallch (wallpaperchanger). It provides a notification each time a wallpaper has changed.

Something like that would be good to differentiate between 2D and 3D.

---

### Post by madjr on 2011-10-19
> **effenberg0x0 said:**
> There are users cutting/pasting every command they can find on the forum in an attempt to make CCSM changes work. But they're using Ubuntu  2D.........

A little warning dialog in ccsm like: "Settings will only be applied when you start a 3D session. This is Ubuntu 2D." would help.



[ATTACH]204743[/ATTACH] 
[SIZE=3]It looks like you're trying to apply 90% 
transparency to Any & !(Any)? Good...[/SIZE]

i think devs would agree too if its already reported

and here is a tool to change some options for unity 2d:
[http://www.omgubuntu.co.uk/2011/10/unity-2d-tweak-app-updated-for-11-10](http://www.omgubuntu.co.uk/2011/10/unity-2d-tweak-app-updated-for-11-10)

---

### Post by ventrical on 2011-10-20
I have the compiz Fusion icon enabled so everytime I log on to Unity 3D it's the first thing to pop-up and I know I am in Unity 3D (will not pop up in 2D. Now, changing some of the behaviour of the Icon might help !

:)
 :)

---

### Post by ventrical on 2011-10-20
For example .. on boot up or by pressing <ctrl>F11 the following will pop up.

*note* I just re-engineered it a bit for PP.

[http://www.youtube.com/watch?v=8pHDmEFg-UU](http://www.youtube.com/watch?v=8pHDmEFg-UU)


But perhaps a special icon can be intergrated for Unity 2D.

add-on .. this is achieved  by enabling the <splash> option in compiz.

---

### Post by jerrylamos on 2011-10-20
I'm typically running full screen applications (not games) so nothing that "Compiz" does churning away in the background using up processor cycles is ever visible, so why use it at all - I happily do Unity-2D.  Yep, my pc's are fast enough, that's for internet videos to use not for Compiz "eye candy".

I've had a black mark against Compiz ever since Intrepid when the Compiz launchpad bugs were legion.

Anyway, presumably Ubuntu is user configurable to a degree...

Jerry

---

### Post by ventrical on 2011-10-20
> **jerrylamos said:**
> I'm typically running full screen applications (not games) so nothing that "Compiz" does churning away in the background using up processor cycles is ever visible, so why use it at all - I happily do Unity-2D.  Yep, my pc's are fast enough, that's for internet videos to use not for Compiz "eye candy".

I've had a black mark against Compiz ever since Intrepid when the Compiz launchpad bugs were legion.

Anyway, presumably Ubuntu is user configurable to a degree...

Jerry


 I am not a gamer myself either but I think Compiz is a  great tool for graphical presentations. For example I have one of my PCs set up with rotating cubes and I was able to use a tool to put different wallpapers on each desktop.  Only thing is that the wallpapers were in the form of flash cards (for me) and so , with the flip of the mouse I can rotate to a memory peg - or I can schedule flash-cards for each different day. I look at is as a feat of assisitve technology rather that just eye-candy.( I am currently working on a design concept that will employ compiz as a 'scroll-o-dex' - where I can have all my notes, pics and tasks in a cue and be able to scroll through them like a roll-o-dex.)  :)

 Unity 2D is great also .. but I can't move aorund in it like I can with Unity 3D. So voila' , I proved to myself that I could reset compiz to tell me that I am using Unity 3D.!! And now I got an idea for Unity 2D.

 Ubuntu has thousands of tools, treasures even .. just out there .. :)

---

### Post by ventrical on 2011-10-20
Anyone want to help with this?

 I just need a tip on how to enable permissions so  I can save this file. I used the Gimp editor.

My assumption is that when the Unity  2D icon comes up in the launcher it will have the 2D stamped to it. This would be a real simple fix to "is it 2D or is it 3D.

:)

regards

ventrical

---

### Post by ronacc on 2011-10-20
> **ventrical said:**
> An example of that is the new little program called wallch (wallpaperchanger). It provides a notification each time a wallpaper has changed.

Something like that would be good to differentiate between 2D and 3D.

yeah thats about right a notification that tells you something very obvious has changed and none for information you need :lolflag:

---

### Post by effenberg0x0 on 2011-10-20
I just threw in a lame workaround. See screenshot. Of course it's not the best solution. /usr/bin/ccsm should be edited directly (Python). But, it gives an idea on how it could work.

When user is logged in to Ubuntu 2D:  $DESKTOP_SESSION is set to "ubuntu-2d". Otherwise it is set to "ubuntu". It just checks the env var and if/then/else/fi over it. I used Zenity, but could GTK+ directly via Python.

**EDIT:** Code to restart lightdm or directly switch to Ubuntu should be added, I'm really on a hurry here. Buttons are there just as a mockup.

[ATTACH]204933[/ATTACH]

```

$
$ sudo mv /usr/bin/ccsm /usr/bin/ccsm2
$ sudo nano /usr/bin/ccsm

#!/bin/sh
#
# Alvaro "Effenberg" Leal <https://launchpad.net/~effenberg0x0>, Oct. 2011
# Lame workaround: It will warn user if he's into a Ubuntu 2D session and trying to launch CCSM
# Otherwise do nothing, launch ccsm2.
# Replace /usr/bin/ccsm with this bash script. 
# /usr/bin/ccsm must be renamed to /usr/bin/ccsm2 
# 
# TODO: Add code to restart lightdm / Ubuntu 2D mode if user select this option on dialog
#       Check that $DESKTOP_SESSION is always correctly exported to environment. DO something if it is not.
#
#

DIALOG_TITLE"This is a Ubuntu 2D session"
DIALOG_TEXT="You\'re adjusting compiz settings and effects for a Ubuntu session,\\nbut this is a Ubuntu 2D Session.Your settings will only become\\nvisible once you start a Ubuntu session."
DIALOG_OK_TEXT="Restart in Ubuntu session mode"
DIALOG_CANCEL_TEXT="Ignore"


if [ $DESKTOP_SESSION == "ubuntu-2d" ]; then 
    /usr/bin/zenity --question --text="$DIALOG_TEXT" \
    --height=100 --width=300 --title="$DIALOG_TEXT" \
    --window-icon=INFO --ok-label="$DIALOG_OK_TEXT" \
    --cancel-label="$DIALOG_CANCEL_TEXT"
else
    /usr/bin/ccsm2 &
fi

$
$ sudo chown root:root /usr/bin/ccsm /usr/bin/ccsm2
$ sudo chmod 755 /usr/bin/ccsm /usr/bin/ccsm2
$

```
To revert:```

$ sudo mv /usr/bin/ccsm2 /usr/bin/ccsm

```

---

### Post by ventrical on 2011-10-20
Thanks for following up on your sugestion.

---

### Post by crdlb on 2011-10-20
The optimal way to do this would be to have ccsm use GDK to monitor the window manager name and insert a little gtk.InfoBar at the top of the window if it's not compiz. Or it could look for org.freedesktop.compiz on the session bus, but that requires compiz to have the dbus plugin loaded.

---

### Post by effenberg0x0 on 2011-10-20
> **crdlb said:**
> The optimal way to do this would be to have ccsm use GDK to monitor the window manager name and insert a little gtk.InfoBar at the top of the window if it's not compiz. Or it could look for org.freedesktop.compiz on the session bus, but that requires compiz to have the dbus plugin loaded.

They have opted to NOT set dbus plugin ON by default until now. Maybe there's some other issue with it? Probably... I was thinking about the $DESKTOP_SESSION environment variable because it is set by lightdm. See below:


> Overview of changes in lightdm 0.1.1

    * Change licence of libldmgreeter from GPL to LGPL
    * Write X server and session output to log files
   ** * Set PATH, DESKTOP_SESSION, GDMSESSION and USERNAME environment variables**
    * Run sessions through Xsession
    * Close all X servers on exit
    * Send SIGHUP to X server when returning to greeter (makes all clients quit)
    * Change authorization after a session ends so previous session does not get
      access
    * Make shutdown buttons work in GTK+ greeter
    * Make user manager configurable
    * Make GTK+ greeter show username entry if no user list
    * Hide C and POSIX languages in greeter
    * Load language and layout from .dmrc file
I'll propose it checks the environment variable and warn via standard GTK+ dialog, as the first condition. Now, I can't do python, really, and I wish every part of Ubuntu was done in C. But this works and gives them a general idea of what we're talking about, just as a mockup.

[ATTACH]204965[/ATTACH]

```

#!/usr/env/python

# If $DESKTOP_SESSION="ubuntu-2d", display a dialog warning user
# that changes will only have effect in a Ubuntu (not 2D) Session.

import os
import gtk, pygtk

def custom_dlg(dlg_type, dlg_title, dlg_text):
    dialog = gtk.MessageDialog(None,
                               gtk.DIALOG_MODAL,
                               type=dlg_type,
                               buttons=gtk.BUTTONS_OK)
    dialog.set_markup("<b>%s</b>" % dlg_title)
    dialog.format_secondary_markup(dlg_text)
    dialog.run()
    dialog.destroy()

def check_desktop_session():
  if os.environ["DESKTOP_SESSION"] == "ubuntu-2d":
    dlg_type = gtk.MESSAGE_INFO
    dlg_title = "This is a Ubuntu 2D Session"
    dlg_text = "You are trying to use Compiz Config\n" + \
             "Settings Manager at a Ubuntu 2D Session\n" + \
             "Your changes will only have effect once\n" + \
             "once you start a Ubuntu (not 2D) Session\n"
    custom_dlg(dlg_type, dlg_title, dlg_text)

check_desktop_session()

```

**EDIT: **Test case: export $DESKTOP_SESSION as "ubuntu-2d", run script.

---

### Post by ventrical on 2011-10-20
An easier way  (depending on user preference) is to just edit the launcher_bfb.png file  in usr/share/unity/4/


 I'm having a riot :) A person can do anything with Precise


 Cheers,

lol:)

---

### Post by ventrical on 2011-10-20
heahehaehah .. what a riot .. Unity 2D and Unity 3D both CALL the same launcher_icon from the same directory ..heheh :)

 too much..

the fun begins.. :)

---

### Post by crdlb on 2011-10-20
> **effenberg0x0 said:**
> I was thinking about the $DESKTOP_SESSION environment variable because it is set by lightdm.

```

import gtk

window = gtk.Window()
mainVbox = gtk.VBox()
window.add(mainVbox)

screen = gtk.gdk.screen_get_default()

if screen.get_window_manager_name() != "Compiz":
    info = gtk.InfoBar()
    info.get_content_area().add(gtk.Label("Compiz is not active. Your settings will not take effect in this session."))
    info.add_button(gtk.STOCK_OK, gtk.RESPONSE_OK)
    info.connect('response', lambda w, i: w.hide())
    mainVbox.pack_start(info, False, False)
    info.show()

window.show_all()

gtk.main()

```

That's basically how I'd do it. This way you're not putting unity-specific stuff in ccsm.

---

### Post by ventrical on 2011-10-20
Perhaps that way is better because I doubt that the devs would write in a new line of code and grab another launcher icon. It would  be alot more efficient if they did, That would be just one simple line of code:

ie;psuedo_code
if DE = unity2d then get <unity2D.png> else <unity3D.png>

end_if

 it's more 'precise'  having a tailored launcher icon for each desktop than larger pop-ups and warnings. It's an easy work-a-round.

regards,
ventrical

---

### Post by mc4man on 2011-10-21
Probably a good idea for a warning & possibly even then not let ccsm run in a unty-2d session.

Atm changes made in ccsm while not in unity(3d) are written to the "Default" profile which unity(3d) doesn't use, it uses the "Unity" profile by default.
 So changes made while in unity-2d will **not** take effect when logging back into the ubuntu session (unity3d

(com.canonical.Unity goes across both sessions

---

### Post by effenberg0x0 on 2011-10-21
> **mc4man said:**
> Probably a good idea for a warning & possibly even then not let ccsm run in a unty-2d session.

Atm changes made in ccsm while not in unity(3d) are written to the "Default" profile which unity(3d) doesn't use, it uses the "Unity" profile by default so changes made while in unity-2d will **not** take effect when logging back into the ubuntu session (unity3d

(com.canonical.Unity goes across both sessions

I didn't think of that! Totally forgot the profiles. You're right, if we're not in Ubuntu(3d), it should warn/info dialog and exit. That is much better advise for change in code.

---

### Post by mc4man on 2011-10-21
> **effenberg0x0 said:**
>  if we're not in Ubuntu(3d), it should warn/info dialog and exit. That is much better advise for change in code.
Well one other thing is that you don't want to prevent users from starting ccsm in the "Classic" session which can use compiz (this session uses the Default profile  - I think? - having 5 sessions potentially available can be a bit much to keep track of.

Though as it stands now preventing ccsm from running in unity-2d would be a positive, if not for anything else then preventing users from being advised to do so to fix unity-3d

---

### Post by effenberg0x0 on 2011-10-21
You're right, instead of looking at the desktop_session env var, one should explicitly look for Compiz. If compiz is running, ccsm should run normally. If not, then don't. It doesn't matter if the session supports compiz - user can have any other nondefault desktop running - only if compiz is actually running. Good advice, thanks.

---

### Post by ventrical on 2011-10-21
It's good to see that others are doing great work to solve this little problem.

  I found that there are , in fact, different calls to the Unity directory and the Unity2D directory which led me to this rough work-a-round I got going here. The file <background_sheen.png> is in the Unity2D/Places and is not called by Unity 3D... so then I was able to use that to impress Ubuntu 2D on the background leading to this:

[http://www.youtube.com/watch?v=FLxhPDr3r7g](http://www.youtube.com/watch?v=FLxhPDr3r7g)

I can do the same with Ubuntu3D without modifying the Dash icon .. and this makes it a lot easier without having to patch through (or worry about) compiz.

regards,
ventrical

---

### Post by PaulInBHC on 2011-10-21
> **mc4man said:**
> Well one other thing is that you don't want to prevent users from starting ccsm in the "Classic" session which can use compiz (this session uses the Default profile  - I think? - having 5 sessions potentially available can be a bit much to keep track of.

Though as it stands now preventing ccsm from running in unity-2d would be a positive, if not for anything else then preventing users from being advised to do so to fix unity-3d

That is how I fixed CCSM and Unity. Log in to 2D, check the Unity plug in box, log out and back in with Unity. How should have it been done?

---

### Post by mc4man on 2011-10-21
> **PaulInBHC said:**
> That is how I fixed CCSM and Unity. Log in to 2D, check the Unity plug in box, log out and back in with Unity. How should have it been done?

Myself have never seen that work. Give it a test
Log in to Ubuntu, disable the plugin, then log out/in to unity-2d. Enable the unity plugin & log out/in to Ubuntu again. 

If there still is no Unity running then you'd just start ccsm & enable
(ctrl+alt+t or one can always browse to /usr/share/applications

---

### Post by ventrical on 2011-10-21
> **PaulInBHC said:**
> That is how I fixed CCSM and Unity. Log in to 2D, check the Unity plug in box, log out and back in with Unity. How should have it been done?

Worked every time here .. especially during alpha./beta .. in fact that was the only way .  Tried the unity -reset etc .. but that never worked ,but ticking the Unity plugin in 2D did.

---

### Post by mc4man on 2011-10-21
> **ventrical said:**
> Worked every time here .. especially during alpha./beta .. in fact that was the only way .  ,but ticking the Unity plugin in 2D did.
I don't see it working  on a straight up install, that's why you see people making changes in ccsm & complaining the settings never take.
 > Tried the unity [COLOR="Blue"]-[/COLOR]-reset etc .. but that never worked
unity --reser will work, but you have to be using the 'unity' profile

All you need to do is what I said above, if you start ccsm from a terminal - 
In unity-2d
> $ ccsm
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     :[COLOR="Red"] default[/COLOR]

in a ubuntu login
> $ ccsm
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : [COLOR="Red"][COLOR="Red"]unity[/COLOR][/COLOR]

Changes to the default profile will not be applied to the unity profile

---

### Post by ventrical on 2011-10-21
ubuntu login:

dale@ubuntu:~$ ccsm
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
??

I don't see the 'unity' profile in 'ubuntu' login.  I got the cube and most of the features working here.

I tried 5 different installs on 2 different PCs and still no 'Unity'  showing up - but please do note that the compiz features I do have ticked off are all functioning properly.

I also know there were some earlier problems with 'preferences' as effenberg pointed out about 6 weeks ago with Ocelot testing.

  However .. I do see your point and you are correct. Unity Plugin is not set by default at a fresh install.

 and just a side note... you also said here:

[http://ubuntuforums.org/showpost.php?p=11265968&postcount=3](http://ubuntuforums.org/showpost.php?p=11265968&postcount=3)

but I think you meant Ubuntu 2D because there was just no way to use ubuntu (3d) because you couldn't get in .. to ccsm that way

---

### Post by mc4man on 2011-10-21
> **ventrical said:**
> 

  However .. I do see your point and you are correct. Unity Plugin is not set by default at a fresh install.

I not sure what you mean there
On a  new install that supports 3d the Unity plugin is enabled in the ubuntu session

> **ventrical said:**
> 
 and just a side note... you also said here:

[http://ubuntuforums.org/showpost.php?p=11265968&postcount=3](http://ubuntuforums.org/showpost.php?p=11265968&postcount=3)

but I think you meant Ubuntu 2D because there was just no way to use ubuntu (3d) because you couldn't get in .. to ccsm that way
Of course you can, there many ways to open ccsm in an ubuntu session when the unity plugin is disabled
2 simple ways -
ctrl+alt+t > ccsm
Browse to /usr/share/applications & d. click on terminal > ccsm
To browse there normally you'd see a menu on top left > click 'go'
Otherwise open a folder on the Desktop
If there isn't a folder on the Desktop then r. click > Create New Folder.
ect.

> **ventrical said:**
> I tried 5 different installs on 2 different PCs and still no 'Unity' showing up 
Well, then those installs, which may be fine, are not 'accurate' to the extent of what the vast majority using the 11.10 release or the upcoming 12.04, at least in this regard.

---

### Post by ventrical on 2011-10-21
> **mc4man said:**
> I not sure what you mean there
On a  new install that supports 3d the Unity plugin is enabled in the ubuntu session
.

???

     Quote:
                                                                      Originally Posted by **ventrical**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11375448#post11375448")                 
                 *Worked every time here .. especially  during alpha./beta .. in fact that was the only way .  ,but ticking the  Unity plugin in 2D did.*
                                 
{QUOTE=mc4man:]I don't see it working  on a straight up install, that's why you  see people making changes in ccsm & complaining the settings never  take.[/QUOTE]

??

Sorry mc4man. You lost me also. :)

Long day :)

EDIT:

Ahhh .. It came to me :)  The first thing I do after I installed Ocelot/Precise is set up the compiz. For me that would be enabling the CUBE. In alpha/beta this  (and a few other settings like wobbly windows) would knock out the UnityPlug-in .. then , loosing the Unity 3D desktop, I had to go into Unity 2D to reset the Unity Plugin. So I think we are on the same page here but just reading different paragraphs. :)

 however .. running ccsm on terminal still gives me = default and not = unity. Not sure why my installs would  then be so inaccurate. I'll check my Dell and do yet another fresh install using my USB IDE&SATA bridge.

---

### Post by ventrical on 2011-10-21
I know the problem here. I checked my Dell install and i had the =unity setting when I typed in ccsm in the terminal while in Unity 3D. I then went to >compiz>preferences>export and my system locked up . blew out all the compiz settings and then gave me the = default setting after reboot. I had to log on with Unity 2D to reset all my compiz settings and now I get:

madame@madame-ME051:~$ ccsm
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default


So that leads me to the question:

I do I get my Profile  setting back to =unity ?

---

### Post by effenberg0x0 on 2011-10-21
@mc4man and @ventrical, can you please check something for me?

I have $COMPIZ_CONFIG_PROFILE set to "ubuntu", but I don't have this profile in gconf. 

In fact, I only have one profile in compizconfig-1, which is "unity". I know that "unity" is the active one because I can use unset and disable plugins on the fly.

What do you have for these env vars when you're on Unity?
```
env | grep -i "^desktop_session" && env | grep -i "xdg_current_desktop" && env | grep -i "compiz"
```I have:
```
DESKTOP_SESSION=ubuntu
XDG_CURRENT_DESKTOP=Unity
COMPIZ_CONFIG_PROFILE=ubuntu **(I don't get this one)**
```

---

### Post by ventrical on 2011-10-21
dale@ubuntu:~$ env | grep -i "^desktop_session" && env | grep -i "xdg_current_desktop" && env | grep -i "compiz"
DESKTOP_SESSION=ubuntu
XDG_CURRENT_DESKTOP=Unity
COMPIZ_CONFIG_PROFILE=ubuntu
dale@ubuntu:~$

---

### Post by mc4man on 2011-10-21
> ~ "compiz"DESKTOP_SESSION=ubuntu
XDG_CURRENT_DESKTOP=Unity
COMPIZ_CONFIG_PROFILE=ubuntu

Anyway - the issue with whether one uses the 'unity' profile or the 'default' profile seems to be caused by going into ccsm > preferences

If it Totally crashes compiz & one does a forced log out then you start getting the 'default' profile which can be adjusted in unity-2d or even Classic/compiz

I don't know what the preferences > profile says by default because it always crashes the 1st time used on an install, sort of a catch-22
I suspect it would say 'Default', but that 'Default' is unity/ubuntu, until one crashes out compiz by opening preferences

I think most users never will open preferences but the current effect of doing so should be kept in mind
ccsm certainly needs some love..

Edit: 
if they would finally decide to provide a small unity or unity + a few other config tool default installed & visible then that would keep quite a number of users out of ccsm

---

### Post by ventrical on 2011-10-21
It won't crash on this install of Precise on my Intel Tower with nVidia

[http://www.youtube.com/watch?v=SAUA8uU6C3Y](http://www.youtube.com/watch?v=SAUA8uU6C3Y)

But it hammered my Dell!!

So when I choose <yes> I get this:

[decor]
s0_command = gtk-window-decorator --replace

[splash]
s0_background = /home/dale/Desktop/68a.jpg
s0_logo = /home/dale/Desktop/splash1_logo.png

[zoom]
s0_speed = 44.626202

[core]
s0_active_plugins = core;composite;opengl;decor;imgjpeg;firepaint;put;reflex;imgpng;resize;wobbly;place;compiztoolbox;cube;dbus;mousepoll;regex;move;text;splash;shift;td;rotate;cubeaddon;animation;expo;showmouse;scale;ring;animationaddon;ezoom;unityshell;bench;
s0_hsize = 6

[firepaint]
s0_num_particles = 2339
s0_fire_size = 2.818500
s0_fire_life = 0.287300
s0_fire_mystical = true
s0_bg_brightness = 20

[rotate]
s0_zoom = 0.622000
s0_rotate_flip_left_edge = 

[unityshell]
s0_icon_size = 41
s0_dash_blur_experimental = 0

[wallpaper]
s0_bg_image = ;/home/dale/Desktop/Screenshot at 2011-09-24 09:10:10.png;
s0_bg_image_pos = 0;0;
s0_bg_fill_type = 0;0;
s0_bg_color1 = #000000ff;#000000ff;
s0_bg_color2 = #000000ff;#000000ff;

[ring]
s0_prev_key = Disabled

[cube]
s0_skydome = true
s0_skydome_animated = true
s0_active_opacity = 85.714302
s0_inactive_opacity = 92.493896

[ezoom]
s0_zoom_in_key = <Super>v
s0_zoom_out_key = <Super>g


and when I choose no I get this:


```
staticswitcher]
s0_next_button = Disabled
s0_next_key = <Alt>Tab
s0_prev_button = Disabled
s0_prev_key = <Shift><Alt>Tab
s0_next_all_button = Disabled
s0_next_all_key = <Control><Alt>Tab
s0_prev_all_button = Disabled
s0_prev_all_key = <Shift><Control><Alt>Tab
s0_next_group_button = Disabled
s0_next_group_key = Disabled
s0_prev_group_button = Disabled
s0_prev_group_key = Disabled
s0_next_no_popup_button = Disabled
s0_next_no_popup_key = Disabled
s0_prev_no_popup_button = Disabled
s0_prev_no_popup_key = Disabled
s0_next_panel_button = Disabled
s0_next_panel_key = Disabled
s0_prev_panel_button = Disabled
s0_prev_panel_key = Disabled
s0_speed = 4.000000
s0_timestep = 1.200000
s0_window_match = Normal | Dialog | Toolbar | Utility | Unknown
s0_minimized = true
s0_auto_change_vp = true
s0_popup_delay = 0.200000
s0_mouse_select = true
s0_saturation = 100
s0_brightness = 100
s0_opacity = 100
s0_icon = true
s0_icon_only = false
s0_mipmap = false
s0_row_align = 1
s0_focus_on_switch = false
s0_bring_to_front = false
s0_highlight_mode = 0
s0_highlight_rect_hidden = 1
s0_highlight_color = #00000096
s0_highlight_border_color = #000000c8
s0_highlight_border_inlay_color = #c8c8c8c8

[gnomecompat]
s0_main_menu_key = <Alt>F1
s0_run_key = <Alt>F2
s0_command_screenshot = gnome-screenshot
s0_run_command_screenshot_key = Print
s0_command_window_screenshot = gnome-screenshot --window
s0_run_command_window_screenshot_key = <Alt>Print
s0_command_terminal = gnome-terminal
s0_run_command_terminal_key = <Control><Alt>T

[decor]
s0_shadow_radius = 15.000000
s0_shadow_opacity = 0.500000
s0_shadow_color = #00000000
s0_shadow_x_offset = 1
s0_shadow_y_offset = 5
s0_command = gtk-window-decorator --replace
s0_mipmap = false
s0_decoration_match = any
s0_shadow_match = any

[splash]
s0_initiate_key = <Control>F11
s0_firststart = true
s0_background = /home/dale/Desktop/68a.jpg
s0_logo = /home/dale/Desktop/splash1_logo.png
s0_fade_time = 1.000000
s0_display_time = 2.000000
s0_saturation = 50.000000
s0_brightness = 50.000000

[vpswitch]
s0_begin_key = Disabled
s0_switch_to_1_key = Disabled
s0_switch_to_2_key = Disabled
s0_switch_to_3_key = Disabled
s0_switch_to_4_key = Disabled
s0_switch_to_5_key = Disabled
s0_switch_to_6_key = Disabled
s0_switch_to_7_key = Disabled
s0_switch_to_8_key = Disabled
s0_switch_to_9_key = Disabled
s0_switch_to_10_key = Disabled
s0_switch_to_11_key = Disabled
s0_switch_to_12_key = Disabled
s0_left_button = Disabled
s0_right_button = Disabled
s0_up_button = Disabled
s0_down_button = Disabled
s0_next_button = Disabled
s0_prev_button = Disabled
s0_initiate_button = Button2
s0_init_plugin = rotate
s0_init_action = initiate_button

[mag]
s0_initiate = <Super>m
s0_zoom_in_button = <Shift><Super>Button4
s0_zoom_out_button = <Shift><Super>Button5
s0_mode = 0
s0_zoom_factor = 2.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_keep_screen = true
s0_box_width = 300
s0_box_height = 200
s0_border = 2
s0_box_color = #000000ff
s0_overlay = Gnome/overlay.png
s0_mask = Gnome/mask.png
s0_x_offset = 155
s0_y_offset = 155
s0_radius = 200

[composite]
s0_slow_animations_key = Disabled
s0_detect_refresh_rate = true
s0_refresh_rate = 50
s0_unredirect_fullscreen_windows = false
s0_force_independent_output_painting = false

[widget]
s0_toggle_key = F9
s0_toggle_button = Disabled
s0_toggle_edge = 
s0_match = 
s0_end_on_click = true
s0_fade_time = 0.500000
s0_bg_brightness = 50
s0_bg_saturation = 100

[resizeinfo]
s0_fade_time = 500
s0_always_show = false
s0_text_color = #000000ff
s0_gradient_1 = #cccce6cc
s0_gradient_2 = #f3f3f3cc
s0_gradient_3 = #d9d9d9cc

[group]
s0_select_button = Disabled
s0_select_single_key = <Super>s
s0_group_key = <Super>g
s0_ungroup_key = <Super>u
s0_remove_key = <Super>r
s0_close_key = <Super>c
s0_ignore_key = <Super>x
s0_tabmode_key = <Super>t
s0_change_tab_left_key = <Super>Left
s0_change_tab_right_key = <Super>Right
s0_change_color_key = Disabled
s0_move_all = true
s0_resize_all = false
s0_raise_all = true
s0_maximize_unmaximize_all = false
s0_minimize_all = true
s0_shade_all = false
s0_auto_group = false
s0_auto_ungroup = true
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_select_opacity = 80
s0_select_saturation = 20
s0_select_brightness = 70
s0_select_precision = 25
s0_fill_color = #00000055
s0_line_color = #000000ab
s0_mipmaps = false
s0_untab_on_close = false
s0_autotab_create = false
s0_autotab_windows = 
s0_tabbar_show_delay = 0.400000
s0_tabbing_speed = 1.200000
s0_tabbing_timestep = 1.500000
s0_fade_time = 0.200000
s0_pulse_time = 0.600000
s0_reflex_time = 0.500000
s0_fade_text_time = 0.250000
s0_visibility_time = 0.500000
s0_change_animation_time = 0.500000
s0_bar_animations = true
s0_thumb_size = 96
s0_thumb_space = 5
s0_border_radius = 10
s0_border_width = 1
s0_tab_base_color = #00000099
s0_tab_border_color = #000000ab
s0_tab_highlight_color = #ffffff99
s0_tab_style = 0
s0_tabbar_font_size = 12
s0_tabbar_font_color = #ffffffff
s0_dnd_ungroup_window = true
s0_drag_hover_time = 0.500000
s0_drag_spring_k = 8.000000
s0_drag_friction = 35.000000
s0_drag_y_distance = 400
s0_drag_speed_limit = 800
s0_glow = true
s0_glow_size = 64
s0_glow_type = 0

[extrawm]
s0_toggle_redirect_key = Disabled
s0_toggle_fullscreen_key = Disabled
s0_toggle_always_on_top_key = Disabled
s0_toggle_sticky_key = Disabled
s0_activate_demands_attention_key = Disabled

[scaleaddon]
s0_close_key = Disabled
s0_close_button = Button2
s0_pull_key = Disabled
s0_pull_button = Disabled
s0_zoom_key = Disabled
s0_zoom_button = Button3
s0_window_title = 1
s0_title_bold = false
s0_title_size = 13
s0_border_size = 3
s0_font_color = #ffffffff
s0_back_color = #00000099
s0_window_highlight = false
s0_highlight_color = #ffffff96
s0_layout_mode = 0
s0_natural_precision = 2.000000
s0_constrain_pull_to_screen = true
s0_exit_after_pull = false

[shift]
s0_initiate_key = <Shift><Super>s
s0_initiate_button = Disabled
s0_initiate_edge = 
s0_initiate_all_key = Disabled
s0_initiate_all_button = Disabled
s0_initiate_all_edge = 
s0_terminate_button = Button3
s0_next_key = <Super>Tab
s0_next_button = Disabled
s0_prev_key = <Shift><Super>Tab
s0_prev_button = Disabled
s0_next_all_key = <Alt><Super>Tab
s0_next_all_button = Disabled
s0_prev_all_key = <Shift><Alt><Super>Tab
s0_prev_all_button = Disabled
s0_next_group_key = Disabled
s0_next_group_button = Disabled
s0_prev_group_key = Disabled
s0_prev_group_button = Disabled
s0_speed = 1.500000
s0_shift_speed = 1.000000
s0_timestep = 1.200000
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_minimized = true
s0_mouse_speed = 10.000000
s0_click_duration = 500
s0_mode = 0
s0_size = 50
s0_background_intensity = 0.500000
s0_hide_all = false
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_intensity = 0.400000
s0_flip_rotation = 30
s0_cover_offset = 0.000000
s0_cover_angle = 60.000000
s0_cover_extra_space = 1.000000
s0_cover_max_visible_windows = 10
s0_overlay_icon = 1
s0_mipmaps = false
s0_multioutput_mode = 0
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 2

[kdecompat]
s0_plasma_thumbnails = true
s0_present_windows = true
s0_window_blur = true
s0_sliding_popups = true
s0_slide_in_duration = 250
s0_slide_out_duration = 250

[switcher]
s0_next_button = Disabled
s0_next_key = <Alt>Tab
s0_prev_button = Disabled
s0_prev_key = <Shift><Alt>Tab
s0_next_all_button = Disabled
s0_next_all_key = <Control><Alt>Tab
s0_prev_all_button = Disabled
s0_prev_all_key = <Shift><Control><Alt>Tab
s0_next_no_popup_button = Disabled
s0_next_no_popup_key = Disabled
s0_prev_no_popup_button = Disabled
s0_prev_no_popup_key = Disabled
s0_next_panel_button = Disabled
s0_next_panel_key = Disabled
s0_prev_panel_button = Disabled
s0_prev_panel_key = Disabled
s0_speed = 1.500000
s0_timestep = 1.200000
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_mipmap = true
s0_saturation = 100
s0_brightness = 65
s0_opacity = 40
s0_focus_on_switch = false
s0_bring_to_front = true
s0_zoom = 1.000000
s0_icon = true
s0_icon_only = false
s0_minimized = true
s0_auto_rotate = false

[zoom]
s0_initiate_button = <Super>Button3
s0_zoom_in_button = <Super>Button4
s0_zoom_out_button = <Super>Button5
s0_zoom_pan_button = <Super>Button2
s0_speed = 44.626202
s0_timestep = 1.200000
s0_zoom_factor = 2.000000
s0_filter_linear = false

[core]
s0_active_plugins = core;composite;opengl;decor;imgjpeg;firepaint;put;reflex;imgpng;resize;wobbly;place;compiztoolbox;cube;dbus;mousepoll;regex;move;text;splash;shift;td;rotate;cubeaddon;animation;expo;showmouse;scale;ring;animationaddon;ezoom;unityshell;bench;
s0_audible_bell = true
s0_ignore_hints_when_maximized = true
s0_hide_skip_taskbar_windows = true
s0_edge_delay = 0
s0_ping_delay = 5000
s0_default_icon = icon
s0_do_serialize = false
s0_overlapping_outputs = 0
s0_detect_outputs = true
s0_outputs = 640x480+0+0;
s0_click_to_focus = true
s0_raise_on_click = true
s0_autoraise = true
s0_autoraise_delay = 1000
s0_focus_prevention_level = 1
s0_focus_prevention_match = !(class=Polkit-gnome-authentication-agent-1)
s0_close_window_key = <Alt>F4
s0_close_window_button = Disabled
s0_raise_window_key = Disabled
s0_raise_window_button = <Control>Button6
s0_lower_window_key = Disabled
s0_lower_window_button = <Alt>Button6
s0_minimize_window_key = <Alt>F9
s0_minimize_window_button = Disabled
s0_maximize_window_key = <Alt>F10
s0_unmaximize_window_key = <Alt>F5
s0_maximize_window_horizontally_key = Disabled
s0_maximize_window_vertically_key = Disabled
s0_window_menu_key = <Alt>space
s0_window_menu_button = <Alt>Button3
s0_show_desktop_key = <Control><Alt>d
s0_show_desktop_edge = 
s0_toggle_window_maximized_key = Disabled
s0_toggle_window_maximized_button = Disabled
s0_toggle_window_maximized_horizontally_key = Disabled
s0_toggle_window_maximized_vertically_key = Disabled
s0_toggle_window_shaded_key = <Control><Alt>s
s0_hsize = 6
s0_vsize = 2
s0_number_of_desktops = 1

[bailer]
s0_fatal_fallback_mode = 2
s0_custom_fallback_window_manager = 
s0_custom_alternative_shell = 
s0_poor_performance_fallback = 0
s0_bad_performance_threshold = 50
s0_bad_plugins = 

[loginout]
s0_in_match = (iclass=^ksplash)
s0_in_time = 1.000000
s0_in_saturation = 0.000000
s0_in_brightness = 100.000000
s0_in_opacity = 100.000000
s0_out_match = (iclass=ksmserver & (role=logoutdialog | role=logouteffect)) | (class=Libssui-tool & type=Dialog)
s0_out_time = 1.000000
s0_out_saturation = 0.000000
s0_out_brightness = 100.000000
s0_out_opacity = 100.000000

[td]
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_min_cube_size = 60
s0_max_window_space = 10
s0_manual_only = true
s0_width = 0.300000
s0_bevel = 0
s0_width_color = #333333ff
s0_width_color_inactive = #333333ff
s0_bevel_topleft = true
s0_bevel_topright = true
s0_bevel_bottomleft = false
s0_bevel_bottomright = false

[trailfocus]
s0_window_match = (type=toolbar | type=utility | type=dialog | type=normal) & !(state=skiptaskbar | state=skippager)
s0_windows_count = 5
s0_windows_start = 2
s0_max_opacity = 100
s0_min_opacity = 70
s0_max_brightness = 100
s0_min_brightness = 100
s0_max_saturation = 100
s0_min_saturation = 100

[wall]
s0_show_switcher = true
s0_miniscreen = true
s0_preview_timeout = 0.200000
s0_preview_scale = 130
s0_edge_radius = 5
s0_border_width = 7
s0_outline_color = #ffffff32
s0_background_gradient_base_color = #00000064
s0_background_gradient_highlight_color = #00000064
s0_background_gradient_shadow_color = #00000064
s0_thumb_gradient_base_color = #55555532
s0_thumb_gradient_highlight_color = #55555532
s0_thumb_highlight_gradient_base_color = #ffffffff
s0_thumb_highlight_gradient_shadow_color = #dfdfdfff
s0_arrow_base_color = #e6e6e6d9
s0_arrow_shadow_color = #dcdcdcd9
s0_allow_wraparound = false
s0_slide_duration = 0.300000
s0_no_slide_match = type=Dock | type=Desktop | state=Sticky
s0_left_key = <Control><Alt>Left
s0_left_button = Disabled
s0_right_key = <Control><Alt>Right
s0_right_button = Disabled
s0_up_key = <Control><Alt>Up
s0_up_button = Disabled
s0_down_key = <Control><Alt>Down
s0_down_button = Disabled
s0_next_key = Disabled
s0_next_button = Disabled
s0_prev_key = Disabled
s0_prev_button = Disabled
s0_left_window_key = <Shift><Control><Alt>Left
s0_right_window_key = <Shift><Control><Alt>Right
s0_up_window_key = <Shift><Control><Alt>Up
s0_down_window_key = <Shift><Control><Alt>Down
s0_flip_left_edge = Left
s0_flip_right_edge = Right
s0_flip_up_edge = Top
s0_flip_down_edge = Bottom
s0_mmmode = 0
s0_edgeflip_pointer = false
s0_edgeflip_move = false
s0_edgeflip_dnd = false

[imgjpeg]
s0_quality = 80

[thumbnail]
s0_thumb_size = 200
s0_show_delay = 100
s0_border = 16
s0_thumb_color = #0000007f
s0_fade_speed = 0.500000
s0_current_viewport = true
s0_always_on_top = true
s0_window_like = true
s0_mipmap = false
s0_title_enabled = true
s0_font_bold = true
s0_font_size = 12
s0_font_color = #000000ff

[firepaint]
s0_initiate_key = Disabled
s0_initiate_button = <Shift><Super>Button1
s0_clear_key = <Shift><Super>c
s0_clear_button = Disabled
s0_num_particles = 2339
s0_fire_size = 2.818500
s0_fire_slowdown = 0.500000
s0_fire_life = 0.287300
s0_fire_color = #ff3305ff
s0_fire_mystical = true
s0_bg_brightness = 20

[put]
s0_put_viewport_1_key = Disabled
s0_put_viewport_2_key = Disabled
s0_put_viewport_3_key = Disabled
s0_put_viewport_4_key = Disabled
s0_put_viewport_5_key = Disabled
s0_put_viewport_6_key = Disabled
s0_put_viewport_7_key = Disabled
s0_put_viewport_8_key = Disabled
s0_put_viewport_9_key = Disabled
s0_put_viewport_10_key = Disabled
s0_put_viewport_11_key = Disabled
s0_put_viewport_12_key = Disabled
s0_put_viewport_left_key = Disabled
s0_put_viewport_right_key = Disabled
s0_put_viewport_up_key = Disabled
s0_put_viewport_down_key = Disabled
s0_put_center_key = <Super>KP_Begin
s0_put_center_button = Disabled
s0_put_left_key = <Super>KP_Left
s0_put_left_button = Disabled
s0_put_right_key = <Super>KP_Right
s0_put_right_button = Disabled
s0_put_top_key = <Super>KP_Up
s0_put_top_button = Disabled
s0_put_bottom_key = <Super>KP_Down
s0_put_bottom_button = Disabled
s0_put_topleft_key = <Super>KP_Home
s0_put_topleft_button = Disabled
s0_put_topright_key = <Super>KP_Prior
s0_put_topright_button = Disabled
s0_put_bottomleft_key = <Super>KP_End
s0_put_bottomleft_button = Disabled
s0_put_bottomright_key = <Super>KP_Next
s0_put_bottomright_button = Disabled
s0_put_empty_center_key = Disabled
s0_put_empty_center_button = Disabled
s0_put_empty_left_key = Disabled
s0_put_empty_left_button = Disabled
s0_put_empty_right_key = Disabled
s0_put_empty_right_button = Disabled
s0_put_empty_top_key = Disabled
s0_put_empty_top_button = Disabled
s0_put_empty_bottom_key = Disabled
s0_put_empty_bottom_button = Disabled
s0_put_empty_topleft_key = Disabled
s0_put_empty_topleft_button = Disabled
s0_put_empty_topright_key = Disabled
s0_put_empty_topright_button = Disabled
s0_put_empty_bottomleft_key = Disabled
s0_put_empty_bottomleft_button = Disabled
s0_put_empty_bottomright_key = Disabled
s0_put_empty_bottomright_button = Disabled
s0_put_restore_key = <Super>KP_Insert
s0_put_restore_button = Disabled
s0_put_pointer_key = <Super>z
s0_put_pointer_button = Disabled
s0_put_next_output_key = Disabled
s0_put_next_output_button = Disabled
s0_pad_left = 0
s0_pad_right = 0
s0_pad_top = 0
s0_pad_bottom = 0
s0_unfocus_window = false
s0_window_center = false
s0_avoid_offscreen = false
s0_speed = 2.500000
s0_timestep = 0.500000

[rotate]
s0_edge_flip_pointer = false
s0_edge_flip_window = true
s0_edge_flip_dnd = true
s0_raise_on_rotate = false
s0_invert_y = false
s0_snap_top = false
s0_snap_bottom = false
s0_zoom = 0.622000
s0_flip_time = 350
s0_sensitivity = 1.000000
s0_acceleration = 4.000000
s0_speed = 2.000000
s0_timestep = 1.000000
s0_initiate_button = <Control><Alt>Button1
s0_rotate_left_key = <Control><Alt>Left
s0_rotate_left_button = Disabled
s0_rotate_right_key = <Control><Alt>Right
s0_rotate_right_button = Disabled
s0_rotate_left_window_key = <Shift><Control><Alt>Left
s0_rotate_left_window_button = Disabled
s0_rotate_right_window_key = <Shift><Control><Alt>Right
s0_rotate_right_window_button = Disabled
s0_rotate_to_key = Disabled
s0_rotate_window_key = Disabled
s0_rotate_flip_left_edge = 
s0_rotate_flip_right_edge = Right
s0_rotate_to_1_key = Disabled
s0_rotate_to_2_key = Disabled
s0_rotate_to_3_key = Disabled
s0_rotate_to_4_key = Disabled
s0_rotate_to_5_key = Disabled
s0_rotate_to_6_key = Disabled
s0_rotate_to_7_key = Disabled
s0_rotate_to_8_key = Disabled
s0_rotate_to_9_key = Disabled
s0_rotate_to_10_key = Disabled
s0_rotate_to_11_key = Disabled
s0_rotate_to_12_key = Disabled
s0_rotate_to_1_window_key = Disabled
s0_rotate_to_2_window_key = Disabled
s0_rotate_to_3_window_key = Disabled
s0_rotate_to_4_window_key = Disabled
s0_rotate_to_5_window_key = Disabled
s0_rotate_to_6_window_key = Disabled
s0_rotate_to_7_window_key = Disabled
s0_rotate_to_8_window_key = Disabled
s0_rotate_to_9_window_key = Disabled
s0_rotate_to_10_window_key = Disabled
s0_rotate_to_11_window_key = Disabled
s0_rotate_to_12_window_key = Disabled

[cubeaddon]
s0_top_next_key = space
s0_top_next_button = Disabled
s0_top_prev_key = Disabled
s0_top_prev_button = Disabled
s0_bottom_next_key = Disabled
s0_bottom_next_button = Disabled
s0_bottom_prev_key = Disabled
s0_bottom_prev_button = Disabled
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_intensity = 0.400000
s0_auto_zoom = true
s0_zoom_manual_only = true
s0_mode = 0
s0_deformation = 1
s0_unfold_deformation = true
s0_cylinder_manual_only = false
s0_deform_caps = true
s0_sphere_aspect = 0.000000
s0_draw_top = true
s0_draw_bottom = true
s0_adjust_top = false
s0_adjust_bottom = false
s0_top_scale = true
s0_bottom_scale = true
s0_top_aspect = true
s0_bottom_aspect = true
s0_top_clamp = true
s0_bottom_clamp = true
s0_top_images = fusioncap.png;
s0_bottom_images = compizcap.png;

[showdesktop]
s0_speed = 1.200000
s0_timestep = 0.100000
s0_direction = 6
s0_window_match = type=toolbar | type=utility | type=dialog | type=normal
s0_window_opacity = 0.300000
s0_window_part_size = 20

[session]
s0_save_legacy = false
s0_ignore_match = 

[screenshot]
s0_initiate_button = <Super>Button1
s0_directory = 
s0_launch_app = 

[unityshell]
s0_launcher_reveal_edge = Left
s0_launcher_reveal_edge_timeout = 150
s0_launcher_hide_mode = 2
s0_show_launcher = <Super>
s0_keyboard_focus = <Alt>F1
s0_execute_command = <Alt>F2
s0_panel_first_menu = F10
s0_alt_tab_timeout = true
s0_alt_tab_bias_viewport = false
s0_alt_tab_forward = <Alt>Tab
s0_alt_tab_prev = <Shift><Alt>Tab
s0_alt_tab_right = <Alt>Right
s0_alt_tab_left = <Alt>Left
s0_alt_tab_detail_start = <Alt>Down
s0_alt_tab_detail_stop = <Alt>Up
s0_alt_tab_next_window = Disabled
s0_alt_tab_prev_window = Disabled
s0_show_minimized_windows = true
s0_backlight_mode = 0
s0_launch_animation = 1
s0_urgent_animation = 2
s0_panel_opacity = 1.000000
s0_launcher_opacity = 0.666700
s0_icon_size = 41
s0_autohide_animation = 3
s0_dash_blur_experimental = 0
s0_automaximize_value = 75
s0_devices_option = 1

[mblur]
s0_initiate_key = <Control>F12
s0_mode = 0
s0_strength = 20.000000
s0_on_transformed_screen = false

[crashhandler]
s0_enabled = true
s0_directory = /tmp
s0_start_wm = false
s0_wm_cmd = 

[bench]
s0_initiate_key = <Super>F12
s0_fps_limiter_mode = 0
s0_output_screen = true
s0_position_x = 0
s0_position_y = 0
s0_output_console = false
s0_console_update_time = 5

[annotate]
s0_initiate_free_draw_button = <Alt><Super>Button1
s0_initiate_line_button = <Alt><Super>Button2
s0_initiate_rectangle_button = <Shift><Alt><Super>Button1
s0_initiate_ellipse_button = <Shift><Alt><Super>Button2
s0_erase_button = <Alt><Super>Button3
s0_clear_key = <Alt><Super>k
s0_clear_button = Disabled
s0_draw_shapes_from_center = true
s0_fill_color = #ff000088
s0_stroke_color = #00ff00ff
s0_erase_width = 20.000000
s0_stroke_width = 3.000000

[workarounds]
s0_keep_minimized_windows = false
s0_legacy_fullscreen = false
s0_firefox_menu_fix = false
s0_ooo_menu_fix = true
s0_notification_daemon_fix = false
s0_java_fix = true
s0_java_taskbar_fix = true
s0_qt_fix = false
s0_convert_urgency = false
s0_aiglx_fragment_fix = true
s0_fglrx_xgl_fix = false
s0_force_glx_sync = false
s0_no_wait_for_video_sync = false
s0_force_swap_buffers = false
s0_sticky_alldesktops = false
s0_alldesktop_sticky_match = any

[reflex]
s0_file = reflection.png
s0_match = any
s0_window = false
s0_decoration = true
s0_threshold = 1
s0_moving = true

[scalefilter]
s0_timeout = 0
s0_filter_case_insensitive = true
s0_filter_display = true
s0_font_bold = true
s0_font_size = 24
s0_border_size = 5
s0_font_color = #ffffffff
s0_back_color = #00000099

[notification]
s0_timeout = -1
s0_max_log_level = 1

[unitymtgrabhandles]
s0_toggle_handles_key = Disabled
s0_show_handles_key = Disabled
s0_hide_handles_key = Disabled
s0_fade_duration = 150

[animation]
s0_open_effects = animation:Glide 2;animation:None;animation:Fade;
s0_open_durations = 120;80;80;
s0_open_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver);(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal);(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd);
s0_open_options = ;;;
s0_open_random_effects = 
s0_close_effects = animation:Glide 2;animation:Fade;animation:None;
s0_close_durations = 120;80;50;
s0_close_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver) & !(name=gnome-screenshot);(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal);(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd);
s0_close_options = ;;;
s0_close_random_effects = 
s0_minimize_effects = animation:Zoom;
s0_minimize_durations = 220;
s0_minimize_matches = (type=Normal | Dialog | ModalDialog | Unknown);
s0_minimize_options = ;
s0_minimize_random_effects = 
s0_shade_effects = animation:Roll Up;
s0_shade_durations = 300;
s0_shade_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown);
s0_shade_options = ;
s0_shade_random_effects = 
s0_focus_effects = animation:Fade;
s0_focus_durations = 150;
s0_focus_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown) & !(name=compiz);
s0_focus_options = ;
s0_all_random = false
s0_time_step = 16
s0_curved_fold_amp_mult = 1.000000
s0_curved_fold_zoom_to_taskbar = true
s0_dodge_mode = 1
s0_dodge_gap_ratio = 0.500000
s0_dream_zoom_to_taskbar = true
s0_glide1_away_position = 1.000000
s0_glide1_away_angle = 0.000000
s0_glide1_zoom_to_taskbar = false
s0_glide2_away_position = -0.100000
s0_glide2_away_angle = 0.000000
s0_glide2_zoom_to_taskbar = true
s0_horizontal_folds_amp_mult = 1.000000
s0_horizontal_folds_num_folds = 3
s0_horizontal_folds_zoom_to_taskbar = true
s0_magic_lamp_moving_end = true
s0_magic_lamp_grid_res = 100
s0_magic_lamp_open_start_width = 30
s0_magic_lamp_wavy_moving_end = true
s0_magic_lamp_wavy_grid_res = 100
s0_magic_lamp_wavy_max_waves = 3
s0_magic_lamp_wavy_amp_min = 200.000000
s0_magic_lamp_wavy_amp_max = 300.000000
s0_magic_lamp_wavy_open_start_width = 30
s0_rollup_fixed_interior = false
s0_sidekick_num_rotations = 0.500000
s0_sidekick_springiness = 0.000000
s0_sidekick_zoom_from_center = 0
s0_wave_width = 0.700000
s0_wave_amp_mult = 1.000000
s0_zoom_from_center = 0
s0_zoom_springiness = 0.080000

[neg]
s0_window_toggle_key = <Super>n
s0_screen_toggle_key = <Super>m
s0_neg_match = any
s0_exclude_match = type=Desktop
s0_neg_decorations = false

[resize]
s0_initiate_button = <Alt>Button2
s0_initiate_key = <Alt>F8
s0_mode = 2
s0_resize_from_center = false
s0_border_color = #fb8b009f
s0_fill_color = #fb8b0019
s0_normal_match = 
s0_outline_match = 
s0_rectangle_match = 
s0_stretch_match = 
s0_resize_from_center_match = 
s0_outline_modifier = 
s0_rectangle_modifier = 
s0_stretch_modifier = 
s0_centered_modifier = 0;

[blur]
s0_pulse = false
s0_blur_speed = 3.500000
s0_focus_blur_match = toolbar | menu | utility | normal | dialog | modaldialog
s0_focus_blur = false
s0_alpha_blur_match = 
s0_alpha_blur = true
s0_filter = 0
s0_gaussian_radius = 3
s0_gaussian_strength = 1.000000
s0_mipmap_lod = 2.500000
s0_saturation = 100
s0_occlusion = true
s0_independent_tex = false

[debugspew]
s0_spew_key = Disabled
s0_spew_on_fatal = true

[clone]
s0_initiate_button = <Shift><Super>Button1

[maximumize]
s0_ignore_sticky = true
s0_ignore_overlapping = false
s0_allow_shrink = true
s0_maximumize_left = true
s0_maximumize_right = true
s0_maximumize_up = true
s0_maximumize_down = true
s0_trigger_max_key = <Super>M
s0_trigger_max_left = Disabled
s0_trigger_max_right = Disabled
s0_trigger_max_up = Disabled
s0_trigger_max_down = Disabled
s0_trigger_max_horizontally = Disabled
s0_trigger_max_vertically = Disabled
s0_trigger_max_up_left = Disabled
s0_trigger_max_up_right = Disabled
s0_trigger_max_down_left = Disabled
s0_trigger_max_down_right = Disabled
s0_trigger_min_key = <Shift><Super>M
s0_trigger_min_left = Disabled
s0_trigger_min_right = Disabled
s0_trigger_min_up = Disabled
s0_trigger_min_down = Disabled
s0_trigger_min_horizontally = Disabled
s0_trigger_min_vertically = Disabled
s0_trigger_min_up_left = Disabled
s0_trigger_min_up_right = Disabled
s0_trigger_min_down_left = Disabled
s0_trigger_min_down_right = Disabled

[colorfilter]
s0_toggle_window_key = <Super>f
s0_toggle_screen_key = <Super>d
s0_switch_filter_key = <Control><Super>s
s0_filters = negative;negative-green;blueish-filter;sepia;grayscale;deuteranopia;protanopia;
s0_filter_decorations = false
s0_filter_match = any
s0_exclude_match = type=Desktop

[commands]
s0_command0 = 
s0_command1 = 
s0_command2 = 
s0_command3 = 
s0_command4 = 
s0_command5 = 
s0_command6 = 
s0_command7 = 
s0_command8 = 
s0_command9 = 
s0_command10 = 
s0_command11 = 
s0_command12 = 
s0_command13 = 
s0_command14 = 
s0_command15 = 
s0_command16 = 
s0_command17 = 
s0_command18 = 
s0_command19 = 
s0_command20 = 
s0_run_command0_key = Disabled
s0_run_command1_key = Disabled
s0_run_command2_key = Disabled
s0_run_command3_key = Disabled
s0_run_command4_key = Disabled
s0_run_command5_key = Disabled
s0_run_command6_key = Disabled
s0_run_command7_key = Disabled
s0_run_command8_key = Disabled
s0_run_command9_key = Disabled
s0_run_command10_key = Disabled
s0_run_command11_key = Disabled
s0_run_command12_key = Disabled
s0_run_command13_key = Disabled
s0_run_command14_key = Disabled
s0_run_command15_key = Disabled
s0_run_command16_key = Disabled
s0_run_command17_key = Disabled
s0_run_command18_key = Disabled
s0_run_command19_key = Disabled
s0_run_command20_key = Disabled
s0_run_command0_button = Disabled
s0_run_command1_button = Disabled
s0_run_command2_button = Disabled
s0_run_command3_button = Disabled
s0_run_command4_button = Disabled
s0_run_command5_button = Disabled
s0_run_command6_button = Disabled
s0_run_command7_button = Disabled
s0_run_command8_button = Disabled
s0_run_command9_button = Disabled
s0_run_command10_button = Disabled
s0_run_command11_button = Disabled
s0_run_command12_button = Disabled
s0_run_command13_button = Disabled
s0_run_command14_button = Disabled
s0_run_command15_button = Disabled
s0_run_command16_button = Disabled
s0_run_command17_button = Disabled
s0_run_command18_button = Disabled
s0_run_command19_button = Disabled
s0_run_command20_button = Disabled
s0_run_command0_edge = 
s0_run_command1_edge = 
s0_run_command2_edge = 
s0_run_command3_edge = 
s0_run_command4_edge = 
s0_run_command5_edge = 
s0_run_command6_edge = 
s0_run_command7_edge = 
s0_run_command8_edge = 
s0_run_command9_edge = 
s0_run_command10_edge = 
s0_run_command11_edge = 
s0_run_command12_edge = 
s0_run_command13_edge = 
s0_run_command14_edge = 
s0_run_command15_edge = 
s0_run_command16_edge = 
s0_run_command17_edge = 
s0_run_command18_edge = 
s0_run_command19_edge = 
s0_run_command20_edge = 

[wallpaper]
s0_bg_image = ;/home/dale/Desktop/Screenshot at 2011-09-24 09:10:10.png;
s0_bg_image_pos = 0;0;
s0_bg_fill_type = 0;0;
s0_bg_color1 = #000000ff;#000000ff;
s0_bg_color2 = #000000ff;#000000ff;
s0_cycle_wallpapers = false
s0_cycle_timeout = 10.000000
s0_fade_duration = 2.000000

[expo]
s0_expo_key = <Super>s
s0_expo_button = Disabled
s0_expo_edge = 
s0_double_click_time = 500
s0_dnd_button = Button1
s0_exit_button = Button3
s0_next_vp_button = Button5
s0_prev_vp_button = Button4
s0_zoom_time = 0.300000
s0_expo_immediate_move = false
s0_expo_animation = 0
s0_deform = 0
s0_x_offset = 64
s0_y_offset = 24
s0_distance = 0.005000
s0_vp_distance = 0.200000
s0_aspect_ratio = 1.000000
s0_curve = 0.500000
s0_hide_docks = false
s0_mipmaps = false
s0_multioutput_mode = 0
s0_vp_brightness = 40.000000
s0_vp_saturation = 40.000000
s0_selected_color = #fb8b00ff
s0_reflection = false
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_scale_factor = 1.000000

[showmouse]
s0_initiate = <Super>k
s0_initiate_button = Disabled
s0_initiate_edge = 
s0_num_particles = 500
s0_size = 10.000000
s0_slowdown = 1.000000
s0_life = 0.700000
s0_darken = 0.900000
s0_blend = true
s0_color = #ffdf3fff
s0_random = false
s0_rotation_speed = 0.500000
s0_radius = 100
s0_emiters = 3

[obs]
s0_opacity_increase_key = Disabled
s0_opacity_increase_button = <Alt>Button4
s0_opacity_decrease_key = Disabled
s0_opacity_decrease_button = <Alt>Button5
s0_opacity_step = 5
s0_opacity_matches = 
s0_opacity_values = 90;
s0_brightness_increase_key = Disabled
s0_brightness_increase_button = Disabled
s0_brightness_decrease_key = Disabled
s0_brightness_decrease_button = Disabled
s0_brightness_step = 5
s0_brightness_matches = 
s0_brightness_values = 90;
s0_saturation_increase_key = Disabled
s0_saturation_increase_button = Disabled
s0_saturation_decrease_key = Disabled
s0_saturation_decrease_button = Disabled
s0_saturation_step = 5
s0_saturation_matches = 
s0_saturation_values = 90;

[wobbly]
s0_snap_key = <Shift>
s0_snap_inverted = false
s0_shiver = false
s0_friction = 3.000000
s0_spring_k = 8.000000
s0_grid_resolution = 8
s0_min_grid_size = 8
s0_map_effect = 0
s0_focus_effect = 0
s0_map_window_match = Splash | DropdownMenu | PopupMenu | Tooltip | Notification | Combo | Dnd | Unknown
s0_focus_window_match = 
s0_grab_window_match = 
s0_move_window_match = Toolbar | Menu | Utility | Dialog | Normal | Unknown
s0_maximize_effect = true

[place]
s0_workarounds = true
s0_mode = 2
s0_multioutput_mode = 0
s0_force_placement_match = 
s0_position_matches = 
s0_position_x_values = 
s0_position_y_values = 
s0_position_constrain_workarea = 
s0_mode_matches = 
s0_mode_modes = 
s0_viewport_matches = 
s0_viewport_x_values = 
s0_viewport_y_values = 

[water]
s0_initiate_key = <Control><Super>
s0_toggle_rain_key = <Shift>F9
s0_toggle_wiper_key = <Shift>F8
s0_offset_scale = 1.000000
s0_rain_delay = 250
s0_title_wave = false

[scale]
s0_spacing = 68
s0_speed = 2.400000
s0_timestep = 0.100000
s0_darken_back = true
s0_opacity = 100
s0_overlay_icon = 0
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_hover_time = 750
s0_dnd_distance = 6
s0_multioutput_mode = 0
s0_key_bindings_toggle = true
s0_button_bindings_toggle = false
s0_initiate_edge = 
s0_initiate_key = <Shift><Alt>Up
s0_initiate_button = Disabled
s0_initiate_all_edge = 
s0_initiate_all_button = Disabled
s0_initiate_all_key = <Super>w
s0_initiate_group_edge = 
s0_initiate_group_button = Disabled
s0_initiate_group_key = Disabled
s0_initiate_output_edge = 
s0_initiate_output_button = Disabled
s0_initiate_output_key = Disabled
s0_show_desktop = false

[ring]
s0_next_key = <Super>Tab
s0_next_button = Disabled
s0_prev_key = Disabled
s0_prev_button = Disabled
s0_next_all_key = <Alt><Super>Tab
s0_next_all_button = Disabled
s0_prev_all_key = <Shift><Alt><Super>Tab
s0_prev_all_button = Disabled
s0_next_group_key = Disabled
s0_next_group_button = Disabled
s0_prev_group_key = Disabled
s0_prev_group_button = Disabled
s0_speed = 1.500000
s0_timestep = 1.200000
s0_inactive_opacity = 100
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_overlay_icon = 1
s0_darken_back = true
s0_minimized = true
s0_select_with_mouse = false
s0_ring_clockwise = false
s0_ring_width = 70
s0_ring_height = 60
s0_thumb_width = 350
s0_thumb_height = 250
s0_min_brightness = 0.500000
s0_min_scale = 0.400000
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 0

[detection]
s0_detect_bad_pci = true
s0_detect_bad_drivers = true

[grid]
s0_put_center_key = <Control><Alt>KP_5
s0_put_left_key = <Control><Alt>KP_4
s0_put_right_key = <Control><Alt>KP_6
s0_put_top_key = <Control><Alt>KP_8
s0_put_bottom_key = <Control><Alt>KP_2
s0_put_topleft_key = <Control><Alt>KP_7
s0_put_topright_key = <Control><Alt>KP_9
s0_put_bottomleft_key = <Control><Alt>KP_1
s0_put_bottomright_key = <Control><Alt>KP_3
s0_put_maximize_key = <Control><Alt>KP_0
s0_put_restore_key = <Control><Alt>r
s0_top_left_corner_action = 4
s0_top_edge_action = 10
s0_top_right_corner_action = 6
s0_left_edge_action = 4
s0_right_edge_action = 6
s0_bottom_left_corner_action = 4
s0_bottom_edge_action = 0
s0_bottom_right_corner_action = 6
s0_snapoff_maximized = false
s0_snapback_windows = true
s0_left_edge_threshold = 15
s0_right_edge_threshold = 15
s0_top_edge_threshold = 20
s0_bottom_edge_threshold = 5
s0_draw_indicator = true
s0_outline_color = #fb8b009f
s0_fill_color = #fb8b004f

[opacify]
s0_toggle_key = <Super>o
s0_toggle_reset = true
s0_timeout = 700
s0_init_toggle = true
s0_only_if_block = false
s0_focus_instant = false
s0_no_delay_change = false
s0_window_match = Normal | Dialog | ModalDialog | Utility | Toolbar | Fullscreen
s0_active_opacity = 100
s0_passive_opacity = 10

[winrules]
s0_skiptaskbar_match = 
s0_skippager_match = 
s0_above_match = 
s0_below_match = 
s0_sticky_match = 
s0_fullscreen_match = 
s0_maximize_match = 
s0_no_argb_match = 
s0_no_move_match = 
s0_no_resize_match = 
s0_no_minimize_match = 
s0_no_maximize_match = 
s0_no_close_match = 
s0_no_focus_match = 
s0_size_matches = 
s0_size_width_values = 
s0_size_height_values = 

[addhelper]
s0_toggle_key = <Super>p
s0_window_types = Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal
s0_ononinit = false
s0_brightness = 30
s0_saturation = 50
s0_opacity = 100

[shelf]
s0_trigger_key = <Super>l
s0_reset_key = Disabled
s0_triggerscreen_key = <Super>p
s0_dec_button = <Alt><Super>Button4
s0_inc_button = <Alt><Super>Button5
s0_animtime = 150
s0_interval = 0.900000

[cube]
s0_unfold_key = <Control><Alt>Down
s0_mipmap = true
s0_multioutput_mode = 0
s0_in = false
s0_acceleration = 4.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_top_color = #cdbe70ff
s0_bottom_color = #cdbe70ff
s0_skydome = true
s0_skydome_image = 
s0_skydome_animated = true
s0_skydome_gradient_start_color = #0db1fdff
s0_skydome_gradient_end_color = #feffc7ff
s0_active_opacity = 85.714302
s0_inactive_opacity = 92.493896
s0_transparent_manual_only = true

[mousepoll]
s0_mouse_poll_interval = 40

[animationaddon]
s0_time_step_intense = 30
s0_airplane_path_length = 1.000000
s0_airplane_fly_to_taskbar = true
s0_beam_size = 8.000000
s0_beam_spacing = 5
s0_beam_color = #7f7f7fff
s0_beam_slowdown = 1.000000
s0_beam_life = 0.700000
s0_fire_particles = 1000
s0_fire_size = 5.000000
s0_fire_slowdown = 0.500000
s0_fire_life = 0.700000
s0_fire_color = #ff3305ff
s0_fire_direction = 0
s0_fire_constant_speed = false
s0_fire_smoke = false
s0_fire_mystical = false
s0_domino_direction = 5
s0_explode_gridx = 13
s0_explode_gridy = 10
s0_explode_spokes = 2
s0_explode_tiers = 3
s0_explode_thickness = 15.000000
s0_explode_tessellation = 0
s0_fold_gridx = 3
s0_fold_gridy = 3
s0_fold_dir = 1
s0_glide3_away_position = -0.400000
s0_glide3_away_angle = 45.000000
s0_glide3_thickness = 0.000000
s0_razr_direction = 5
s0_skewer_direction = 8
s0_skewer_tessellation = 0
s0_skewer_gridx = 6
s0_skewer_gridy = 4
s0_skewer_thickness = 0.000000
s0_skewer_rotation = 0

[snap]
s0_avoid_snap = 0;
s0_snap_type = 0;
s0_edges_categories = 0;
s0_resistance_distance = 30
s0_attraction_distance = 20

[fadedesktop]
s0_fadetime = 500
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown

[opengl]
s0_texture_filter = 1
s0_lighting = false
s0_sync_to_vblank = true
s0_texture_compression = false

[ezoom]
s0_zoom_in_button = Disabled
s0_zoom_in_key = <Super>v
s0_zoom_out_button = Disabled
s0_zoom_out_key = <Super>g
s0_zoom_box_button = Disabled
s0_center_mouse_key = Disabled
s0_zoom_specific_1_key = Disabled
s0_zoom_spec1 = 1.000000
s0_zoom_specific_2_key = Disabled
s0_zoom_spec2 = 0.500000
s0_zoom_specific_3_key = Disabled
s0_zoom_spec3 = 0.200000
s0_spec_target_focus = true
s0_lock_zoom_key = Disabled
s0_pan_left_key = Disabled
s0_pan_right_key = Disabled
s0_pan_up_key = Disabled
s0_pan_down_key = Disabled
s0_fit_to_zoom_key = Disabled
s0_fit_to_window_key = Disabled
s0_zoom_factor = 1.150000
s0_minimum_zoom = 0.125000
s0_zoom_mode = 0
s0_scale_mouse = true
s0_scale_mouse_dynamic = true
s0_scale_mouse_static = 0.200000
s0_hide_original_mouse = true
s0_restrain_mouse = false
s0_restrain_margin = 5
s0_pan_factor = 0.100000
s0_follow_focus = true
s0_focus_fit_window = false
s0_autoscale_min = 0.250000
s0_always_focus_fit_window = false
s0_follow_focus_delay = 0
s0_speed = 25.000000
s0_timestep = 1.200000

[move]
s0_initiate_button = <Alt>Button1
s0_initiate_key = <Alt>F7
s0_opacity = 100
s0_constrain_y = true
s0_snapoff_maximized = true
s0_lazy_positioning = true

[fade]
s0_fade_mode = 0
s0_fade_speed = 5.000000
s0_fade_time = 100
s0_window_match = any & !(title=notify-osd)
s0_visual_bell = false
s0_fullscreen_visual_bell = false
s0_dim_unresponsive = true
s0_unresponsive_brightness = 65
s0_unresponsive_saturation = 0

```

edit:so if I try to import a saved file I get  =default and not = unity.

thanks all :)

---

### Post by effenberg0x0 on 2011-10-21
> **ventrical said:**
> It won't crash on this install of Precise on my Intel Tower with nVidia

[http://www.youtube.com/watch?v=SAUA8uU6C3Y](http://www.youtube.com/watch?v=SAUA8uU6C3Y)

But it hammered my Dell!!

So when I choose <yes> I get this:

[decor]
s0_command = gtk-window-decorator --replace

[/CODE]

gtk-window-decorator? Now I'm confused... what happened to compiz-decorator loading unity-window-decorator? :( Normally s0 whould be /usr/bin/compiz-decorator... yet, unityshell is activated there. I'm really lost, gotta sleep a little.....

---

### Post by mc4man on 2011-10-21
Here's the way it works here (dell if matters, don't think so

On a default install or newly created user the profile is 'unity'
Opening preferences always crashes & then the profile is switched to 'default'
While using the 'default' profile preferences doesn't crash

When setting the profile back to 'unity', opening preferences again crashes, profile is set back to 'default'

So here - preferences  will not work (crash) when the profile is 'unity', will when it's 'default'

To set profile back to unity go to
~/.config/compiz-1/compizconfig/config & set (add blue), log out/in
> [gnome_session]
profile = 

[general_ubuntu]
profile =[COLOR="Blue"] unity[/COLOR]

---

### Post by ventrical on 2011-10-21
> **mc4man said:**
> Here's the way it works here (dell if matters, don't think so

On a default install or newly created user the profile is 'unity'
Opening preferences always crashes & then the profile is switched to 'default'
While using the 'default' profile preferences doesn't crash

When setting the profile back to 'unity', opening preferences again crashes, profile is set back to 'default'

So here - preferences  will not work (crash) when the profile is 'unity', will when it's 'default'

To set profile back to unity go to
~/.config/compiz-1/compizconfig/config & set (add blue), log out/in

I just tried that in terminal  permision denied- as root permission denied

am I on the right track here mac.

?

---

### Post by ventrical on 2011-10-21
> **effenberg0x0 said:**
> gtk-window-decorator? Now I'm confused... what happened to compiz-decorator loading unity-window-decorator? :( Normally s0 whould be /usr/bin/compiz-decorator... yet, unityshell is activated there. I'm really lost, gotta sleep a little.....


that makes two of us :)

lots of work ahead lol

---

### Post by mc4man on 2011-10-21
> **ventrical said:**
> I just tried that in terminal  permision denied- as root permission denied

am I on the right track here mac.

?

tried what?
If opening that file there should be no permission issue

```
gedit ~/.config/compiz-1/compizconfig/config
```

On a newly created user that file is empty
The gnome session section is added by Gs or Classic, don't care
The general_Ubuntu section gets added after doing the preferences crash deal, assuming profile = <nothing> means 'default'

edit: It would also seem that when the unity plugin is disabled that unity --reset will re-enable, but you need to be using the 'unity' profile for that to happen

---

### Post by ventrical on 2011-10-22
> **mc4man said:**
> tried what?
If opening that file there should be no permission issue

```
gedit ~/.config/compiz-1/compizconfig/config
```On a newly created user that file is empty
The gnome session section is added by Gs or Classic, don't care
The general_Ubuntu section gets added after doing the preferences crash deal, assuming profile = <nothing> means 'default'

edit: It would also seem that when the unity plugin is disabled that unity --reset will re-enable, but you need to be using the 'unity' profile for that to happen

Yup .... that worked .. but it blew out all my compiz settings :)

  So now  I'll see if I can actually import those files that I exported ...

 wow .. it just keeps getting more interesting..

---

### Post by ventrical on 2011-10-22
Actually after I opened ccsm the PC just locked up ... so I just waited as I watched the led on the hardrive. after a minute it flicker.. then .. all settings are back to normal without an import ! :)

---

### Post by ventrical on 2011-10-22
I set the option 'crash-handler' i mcompiz and , sure enough, it crashed .. and spewed out this report:

```
Reading symbols from /usr/bin/compiz...(no debugging symbols found)...done.
Attaching to program: /usr/bin/compiz, process 1535
Reading symbols from /usr/lib/i386-linux-gnu/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libX11.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXrandr.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXinerama.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXext.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libICE.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libICE.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libSM.so.6
Reading symbols from /usr/lib/libgtk-3.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgtk-3.so.0
Reading symbols from /usr/lib/libglibmm-2.4.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglibmm-2.4.so.1
Reading symbols from /usr/lib/libsigc-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsigc-2.0.so.0
Reading symbols from /lib/i386-linux-gnu/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libglib-2.0.so.0
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /lib/i386-linux-gnu/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread 0xa891db70 (LWP 2018)]
[New Thread 0xb63ffb70 (LWP 1601)]
[New Thread 0xb6d87b70 (LWP 1600)]
Loaded symbols for /lib/i386-linux-gnu/libpthread.so.0
Reading symbols from /lib/i386-linux-gnu/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libdl.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libstdc++.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libstdc++.so.6
Reading symbols from /lib/i386-linux-gnu/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libgcc_s.so.1
Reading symbols from /lib/i386-linux-gnu/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libc.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libxcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libxcb.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXrender.so.1
Reading symbols from /lib/i386-linux-gnu/libuuid.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libuuid.so.1
Reading symbols from /usr/lib/libgdk-3.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk-3.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXfixes.so.3
Reading symbols from /usr/lib/i386-linux-gnu/libatk-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libatk-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libcairo-gobject.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libcairo-gobject.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libcairo.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libgio-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgio-2.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libpango-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libfontconfig.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0
Reading symbols from /lib/i386-linux-gnu/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libm.so.6
Reading symbols from /lib/i386-linux-gnu/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libpcre.so.3
Reading symbols from /lib/i386-linux-gnu/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/librt.so.1
Reading symbols from /usr/lib/libxcb-util.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-util.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libX11-xcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libX11-xcb.so.1
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXau.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXdmcp.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libXi.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXi.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXcursor.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXcomposite.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXdamage.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libfreetype.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libpixman-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libpixman-1.so.0
Reading symbols from /lib/i386-linux-gnu/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libpng12.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libxcb-shm.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libxcb-shm.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libxcb-render.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libxcb-render.so.0
Reading symbols from /lib/i386-linux-gnu/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libz.so.1
Reading symbols from /lib/i386-linux-gnu/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libselinux.so.1
Reading symbols from /lib/i386-linux-gnu/libresolv.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libresolv.so.2
Reading symbols from /lib/i386-linux-gnu/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libexpat.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libgthread-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgthread-2.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libffi.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libffi.so.6
Reading symbols from /usr/lib/liboverlay-scrollbar3-0.2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/liboverlay-scrollbar3-0.2.so.0
Reading symbols from /lib/i386-linux-gnu/libnss_compat.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnss_compat.so.2
Reading symbols from /lib/i386-linux-gnu/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnsl.so.1
Reading symbols from /lib/i386-linux-gnu/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnss_nis.so.2
Reading symbols from /lib/i386-linux-gnu/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnss_files.so.2
Reading symbols from /usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so
Reading symbols from /usr/lib/libcanberra-gtk3.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcanberra-gtk3.so.0
Reading symbols from /usr/lib/libcanberra.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcanberra.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libvorbisfile.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libvorbisfile.so.3
Reading symbols from /usr/lib/i386-linux-gnu/libtdb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libtdb.so.1
Reading symbols from /usr/lib/libltdl.so.7...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libltdl.so.7
Reading symbols from /usr/lib/i386-linux-gnu/libvorbis.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libvorbis.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libogg.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libogg.so.0
Reading symbols from /usr/lib/gio/modules/libgvfsdbus.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gio/modules/libgvfsdbus.so
Reading symbols from /usr/lib/gvfs/libgvfscommon.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gvfs/libgvfscommon.so
Reading symbols from /lib/i386-linux-gnu/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libdbus-1.so.3
Reading symbols from /lib/i386-linux-gnu/libudev.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libudev.so.0
Reading symbols from /usr/lib/gtk-3.0/3.0.0/theming-engines/libunico.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gtk-3.0/3.0.0/theming-engines/libunico.so
Reading symbols from /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
Reading symbols from /usr/lib/compiz/libccp.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libprotobuf.so.7...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libprotobuf.so.7
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2
Reading symbols from /usr/lib/compiz/libcomposite.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcomposite.so
Reading symbols from /usr/lib/compiz/libopengl.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libopengl.so
Reading symbols from /usr/lib/nvidia-current-updates/libGL.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/nvidia-current-updates/libGL.so.1
Reading symbols from /usr/lib/nvidia-current-updates/tls/libnvidia-tls.so.280.13...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/nvidia-current-updates/tls/libnvidia-tls.so.280.13
Reading symbols from /usr/lib/nvidia-current-updates/libnvidia-glcore.so.280.13...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/nvidia-current-updates/libnvidia-glcore.so.280.13
Reading symbols from /usr/lib/compiz/libdecor.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecor.so
Reading symbols from /usr/lib/libdecoration.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libvpswitch.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libimgpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgpng.so
Reading symbols from /usr/lib/compiz/libresize.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libcompiztoolbox.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcompiztoolbox.so
Reading symbols from /usr/lib/compiz/libgrid.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgrid.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libregex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libgnomecompat.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgnomecompat.so
Reading symbols from /usr/lib/compiz/libanimation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/i386-linux-gnu/libGLU.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libGLU.so.1
Reading symbols from /usr/lib/compiz/libwobbly.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/librotate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libexpo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libscale.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libunityshell.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libunityshell.so
Reading symbols from /usr/lib/libnux-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libnux-1.0.so.0
Reading symbols from /usr/lib/libnux-graphics-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libnux-graphics-1.0.so.0
Reading symbols from /usr/lib/libnux-image-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libnux-image-1.0.so.0
Reading symbols from /usr/lib/libGLEW.so.1.5...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLEW.so.1.5
Reading symbols from /usr/lib/libnux-core-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libnux-core-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libbamf3.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libbamf3.so.0
Reading symbols from /usr/lib/libdee-1.0.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdee-1.0.so.1
Reading symbols from /usr/lib/libdbusmenu-glib.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbusmenu-glib.so.4
Reading symbols from /usr/lib/libindicator3.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libindicator3.so.6
Reading symbols from /usr/lib/libunity-misc.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libunity-misc.so.4
Reading symbols from /usr/lib/libutouch-geis.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libutouch-geis.so.1
Reading symbols from /usr/lib/libjson-glib-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjson-glib-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libnotify.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libnotify.so.4
Reading symbols from /usr/lib/libgnome-desktop-3.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnome-desktop-3.so.2
Reading symbols from /usr/lib/libunity-core-4.0.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libunity-core-4.0.so.4
Reading symbols from /usr/lib/libGLEWmx.so.1.5...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLEWmx.so.1.5
Reading symbols from /usr/lib/i386-linux-gnu/libXxf86vm.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXxf86vm.so.1
Reading symbols from /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
Reading symbols from /usr/lib/gio/modules/libdconfsettings.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gio/modules/libdconfsettings.so
Reading symbols from /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
Reading symbols from /usr/lib/i386-linux-gnu/libjpeg.so.8...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libjpeg.so.8
Reading symbols from /usr/lib/gio/modules/libgioremote-volume-monitor.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gio/modules/libgioremote-volume-monitor.so
Reading symbols from /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
Reading symbols from /usr/lib/i386-linux-gnu/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/librsvg-2.so.2
Reading symbols from /usr/lib/libcroco-0.6.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
0x00932416 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 4 (Thread 0xb6d87b70 (LWP 1600)):
#0  0x00932416 in __kernel_vsyscall ()
#1  0x00a7440e in poll () from /lib/i386-linux-gnu/libc.so.6
#2  0x0016234b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x00153896 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x00153f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x03db3194 in ?? () from /usr/lib/gio/modules/libdconfsettings.so
#6  0x0017a5f4 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x003b9d31 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x00a830ce in clone () from /lib/i386-linux-gnu/libc.so.6
Backtrace stopped: Not enough registers or memory available to unwind further

Thread 3 (Thread 0xb63ffb70 (LWP 1601)):
#0  0x00932416 in __kernel_vsyscall ()
#1  0x00a7440e in poll () from /lib/i386-linux-gnu/libc.so.6
#2  0x0016234b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x00153896 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x00153f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x05ce1cea in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#6  0x0017a5f4 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x003b9d31 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x00a830ce in clone () from /lib/i386-linux-gnu/libc.so.6
Backtrace stopped: Not enough registers or memory available to unwind further

Thread 2 (Thread 0xa891db70 (LWP 2018)):
#0  0x00932416 in __kernel_vsyscall ()
#1  0x003bde04 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x005df021 in ?? () from /usr/lib/i386-linux-gnu/libgthread-2.0.so.0
#3  0x001253f0 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x00125dae in g_async_queue_timed_pop () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x0017c95b in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#6  0x0017a5f4 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x003b9d31 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x00a830ce in clone () from /lib/i386-linux-gnu/libc.so.6
Backtrace stopped: Not enough registers or memory available to unwind further

Thread 1 (Thread 0xb76f0880 (LWP 1535)):
#0  0x00932416 in __kernel_vsyscall ()
#1  0x00a4c06b in waitpid () from /lib/i386-linux-gnu/libc.so.6
#2  0x009ed6e3 in ?? () from /lib/i386-linux-gnu/libc.so.6
#3  0x009edb9a in system () from /lib/i386-linux-gnu/libc.so.6
#4  0x003c1ebb in system () from /lib/i386-linux-gnu/libpthread.so.0
#5  0x0132b8b5 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  <signal handler called>
#7  0x0159b572 in nux::Property<nux::color::Color>::Set(nux::color::Color const&) () from /usr/lib/compiz/libunityshell.so
#8  0x0159ae34 in unity::switcher::SwitcherController::OnBackgroundUpdate(_GVariant*, unity::switcher::SwitcherController*) () from /usr/lib/compiz/libunityshell.so
#9  0x015bb934 in ?? () from /usr/lib/compiz/libunityshell.so
#10 0x0014f110 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#11 0x0015325f in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
#12 0x00153990 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#13 0x00153f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#14 0x00446753 in Glib::MainLoop::run() () from /usr/lib/libglibmm-2.4.so.1
#15 0x08072497 in CompScreen::eventLoop() ()
#16 0x08065634 in main ()
(gdb) 
(gdb) 
(gdb) #0  0x00932416 in __kernel_vsyscall ()
#1  0x00a4c06b in waitpid () from /lib/i386-linux-gnu/libc.so.6
#2  0x009ed6e3 in ?? () from /lib/i386-linux-gnu/libc.so.6
#3  0x009edb9a in system () from /lib/i386-linux-gnu/libc.so.6
#4  0x003c1ebb in system () from /lib/i386-linux-gnu/libpthread.so.0
#5  0x0132b8b5 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  <signal handler called>
#7  0x0159b572 in nux::Property<nux::color::Color>::Set(nux::color::Color const&) () from /usr/lib/compiz/libunityshell.so
#8  0x0159ae34 in unity::switcher::SwitcherController::OnBackgroundUpdate(_GVariant*, unity::switcher::SwitcherController*) () from /usr/lib/compiz/libunityshell.so
#9  0x015bb934 in ?? () from /usr/lib/compiz/libunityshell.so
#10 0x0014f110 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#11 0x0015325f in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
#12 0x00153990 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#13 0x00153f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#14 0x00446753 in Glib::MainLoop::run() () from /usr/lib/libglibmm-2.4.so.1
#15 0x08072497 in CompScreen::eventLoop() ()
#16 0x08065634 in main ()
(gdb) A debugging session is active.

    Inferior 1 [process 1535] will be detached.

Quit anyway? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz, process 1535
```

I'm not familiar with what type of compiler they used to write ccsm but, from what I can tell ,  it looks like a buffer oveflow of somesort or that some handle or environ setting is not set large enough. So they actually wrote in code for compiz to reset itself  without user input, when is crashes.

---

### Post by PaulInBHC on 2011-10-22
Another discussion of CCSM and Preferences button

[http://ubuntuforums.org/showthread.php?t=1863905](http://ubuntuforums.org/showthread.php?t=1863905)

---

### Post by mc4man on 2011-10-22
The thing about pref's is sorta off the point of this thread though  - 
what's quite clear here is that if you open pref's while in the unity profile you're 'switched' to the default profile 

The first time the default profile is used it does not have the unity plugin enabled. If logging in to that state the user gets the screen with no launcher & indicators, just the left side menu

One can stay in the default profile & enable the unity plugin or just switch back to the unity profile, at least here, after switching only a log out/in is needed to restore panel & launcher, no unity --reset is needed

It actually makes perfect sense.

What may be of more interest is that there may be occurrences other than opening pref's than can switch users from the unity to default profile, this could account for the login to the no launcher & indicator screen & being able to adjust/affect unity-3d plugins from unity-2d/Classic

(the best way to ck. any of this is to set up a new user or 2

---

### Post by ventrical on 2011-10-22
> **mc4man said:**
> The thing about pref's is sorta off the point of this thread though  - 
what's quite clear here is that if you open pref's while in the unity profile you're 'switched' to the default profile 

The first time the default profile is used it does not have the unity plugin enabled. If logging in to that state the user gets the screen with no launcher & indicators, just the left side menu

One can stay in the default profile & enable the unity plugin or just switch back to the unity profile, at least here, after switching only a log out/in is needed to restore panel & launcher, no unity --reset is needed

It actually makes perfect sense.

What may be of more interest is that there may be occurrences other than opening pref's than can switch users from the unity to default profile, this could account for the login to the no launcher & indicator screen & being able to adjust/affect unity-3d plugins from unity-2d/Classic

(the best way to ck. any of this is to set up a new user or 2

 Yes .. I experimented with that process during beta. I'm not really worried  about the crashes. I can work through them . I was just trying to contribute to the topic - trying to find a way to weave through this tangled web - so that end_users can know if they are logging into  Unity 2D or Unity 3D. I already suggested a way which works for me and that is to edit the <desktop-dash-background,sci> for Unity 2D and <background-sheen.png>(for Unity 3D). So which ever desktop I log  into I am graphically alerted to which desktop I am in. I don't need compiz to cough out a warning to me. For the newer user though .. yes .. effenberg is on the right track.!

as for  'makes perfect sense'.... I don't agree with that.  The ccsm should work , and all the tools with it. Most of the options and features are not really well established as far as providng graphical user helps and dialogs - and <preferences> is one of them.  Ccsm should work, not  have these long resets, crashes and semi-borking of the desktop.  

 Hmmm.. maby I can compile a sort of <BORK-ALERT> for compiz :)

 thanks again mac.4man

---

### Post by ventrical on 2011-10-22
> **PaulInBHC said:**
> Another discussion of CCSM and Preferences button

[http://ubuntuforums.org/showthread.php?t=1863905](http://ubuntuforums.org/showthread.php?t=1863905)


Great article note !!

[http://ubuntuforums.org/showpost.php?p=11379441&postcount=12](http://ubuntuforums.org/showpost.php?p=11379441&postcount=12)

  But I don't see how they can mark it solved because it's not. It's just a patch.

So .. as we are all here  ready for Precise alpha/beta .. I'm sure that many would like to see this one pull up is socks so to speak.

Thanks Paulin BHC

---

### Post by mc4man on 2011-10-22
> **ventrical said:**
> 
as for  'makes perfect sense'.... I don't agree with that.  The ccsm should work , and all the tools with it.
It is working, makes 'sense',  took me a bit to catch on.

Ex. - new install or new user, same diff.
screen 1  - login - as is well, launcher, panel, using the default 'unity' profile, config file in ~/.config/compiz-1/compizconfig is empty

Screen 2 - Clicking on preferences Does Not crash compiz, it just starts switching the user to the default profile. Why? - because that's what's set in preferences, ie. Profile > Default
The screen shows it while in that process..

So waiting it out for a min. or so  results in screen 3, the 'default' profile has now been loaded.
unity is not enabled by default in the Default profile so no launcher, panel.
 Note that the config file has now been written to
At this point I could go into ccsm & enable the unity plugin, instead will just log out

screen 4 - doing  log in from the above   gives the  typical 'empty' desktop, only the top left menu. I'm using the default profile

One fix from this without opening ccsm or unity --reset, ect. -
 I just open nautilus, browse to ~/.config/compiz-1/compizconfig, open the config file & delete the contents. 
Then do a log out.
The next log in takes a while,  the unity profile is now  being loaded instead of the previous Default profile - screen 5 shows back to where it started, all fine, ect.


So ccsm > preferences is basically working, because it's set on 'Default' that is exactly what you get _as soon as you open it_ (whether that's correct behavior is debatable

---

### Post by ventrical on 2011-10-22
I totally agree and it is a bonus that the ccsm is not GLOBAL for other new_users .. and that was my point during beta test .... I can make 10 new_users and set them all differently as a new and fresh install. Lots of latitude here.  I just needed to be reminded. 

Thanks for the reminder notice !!! :) And user switiching is pretty fast - so this makes a versatile system overall, with or without compiz settings manager.

---

### Post by effenberg0x0 on 2011-10-22
There seems to be some sync error between the profiles, environment vars and ~/.config/compiz-1/compizconfig/config? 

If you change profile directly in ~/.config/compiz-1/compizconfig/config (considering it generally won't work through ccsm interface), the session will restart in the selected profile (considering it exists in the gconf tree). But environment vars won't change accordingly. As a result, you get a session with Compiz, but no plugin activated (no Unity, so no launcher/panel). 

Maybe this could be the source of the problem for those that can't manage to start a Unity session automatically (just manually with unity --replace &)?

All you have to do is have the wrong perms for .config/, .gconf/, or $HOME/, a wrong file or missing ~/.config/compiz-1/compizconfig/config, and, no matter how many times you restart lightdm and run unity --reset, you can't have a single plugin loaded at your session - even if you do have env vars pointing to the right profile exported by lightdm. Or at least this is what I am seeing here.

Regards,
Effenberg

---

### Post by mc4man on 2011-10-22
> If you change profile directly in ~/.config/compiz-1/compizconfig/config (considering it generally won't work through ccsm interface), the session will restart in the selected profile
It does to the extent that it can (& will) set the user to the Default profile.
> Maybe this could be the source of the problem for those that can't manage to start a Unity session automatically (just manually with unity --replace &)?

I think for for many(most?) users that boot/log into the no panel/no launcher screen are either using or have been switched to the Default profile, likely from some action in ccsm.
(& if it happens while in ccsm it appears to be a crash, but isn't - it takes up to 45 sec's here to have the profile switched & loaded  - I can image some people forcing a log out instead of waiting

By default the Default profile doesn't have the unity plugin enabled, though it can be after the fact thru ccsm , either in a ubuntu, unity-2d or classic session.

So if using the Default profile & the unity plugin has not yet been enabled For the Default profile then unity --reset will not work

What should always work is to remove in the config file this
> [general_ubuntu]
profile = 
And then log out/in -  this switches you back to the unity profile (where unity is enabled normally

There still may be a possibility that the unity plugin got unset but the profile wasn't changed. In that case either re-enabling or using unity --reset will work

---

### Post by ventrical on 2011-10-23
> **mc4man said:**
> It does to the extent that it can (& will) set the user to the Default profile.


I think for for many(most?) users that boot/log into the no panel/no launcher screen are either using or have been switched to the Default profile, likely from some action in ccsm.
(& if it happens while in ccsm it appears to be a crash, but isn't - it takes up to 45 sec's here to have the profile switched & loaded  - I can image some people forcing a log out instead of waiting


I am assuming that this is the major bug! It appears that the 'loading' process has some gum in the works. I am then assuming it is a memory handler problem... 

How do I get the source code? Is it written in C or Python?

thanks

---

### Post by mc4man on 2011-11-05
Having noticed that quite a number of users are ending up using the default profile in the Ubuntu session so filed a bug on the most likely cause - clicking on Preferences when in ccsm.

Actually think most have no real reason to go there, it's just sitting there in big letters & is a natural thing to do.

Not sure if there is anything to be done to prevent other than Pref's being initially set to the unity profile instead of Default  when using the Ubuntu session

As in ~/.config/compiz-1/compizconfig/config
[general_ubuntu]
profile = unity

[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/880679](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/880679)

---

### Post by ventrical on 2011-11-05
With compiz running under other versions of Ubuntu it is a novel tool to use the 'Wallpaper' Plugin because different wallpapers (and screenshots of data) can be splashed onto the cube making it  an excellent reference tool as oppossed to just eye candy. And so  then comes in preferences and profiles, scripts that can be loaded to compiz for several other purposes , education being the main one , and with Unity Plugin it is all but complelety muted.

  Don't get me wrong .. I like Unity a great deal . but the Compiz Unity Plugin nulls  a lot of features of ccsm. If Precise is going to be exactly that , 'precise' then the developers  really have to adress this problem. If not, then 12.04 will inherit useless data.  ya know ... it's like ... a stack ... well .. we will just keep burying the bug under another layer of dazzle ...

---

### Post by ventrical on 2011-11-05
> **mc4man said:**
> Having noticed that quite a number of users are ending up using the default profile in the Ubuntu session so filed a bug on the most likely cause - clicking on Preferences when in ccsm.

Actually think most have no real reason to go there, it's just sitting there in big letters & is a natural thing to do.

Not sure if there is anything to be done to prevent other than Pref's being initially set to the unity profile instead of Default  when using the Ubuntu session

As in ~/.config/compiz-1/compizconfig/config
[general_ubuntu]
profile = unity

[https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/880679](https://bugs.launchpad.net/ubuntu/+source/compizconfig-settings-manager/+bug/880679)


 I added my two cents worth :)

---

### Post by mc4man on 2011-11-05
Basically I think 2 slightly seperate things are wrong - 
The use of  profiles is somewhat borked, maybe not unexpected seeing how little work has been done to ccsm over the last year.

The other, more relevant to the bug, is that Preference > Profile doesn't reflect the current profile when being opened from a typical Ubuntu session (unity profile

If it did then nothing bad would occur when opening Preferences, at least not till one clicked on the Profile dropdown (back to the 1st. issue

So while it's currently not able to display "unity" in the Profile, it should be opening to it when ccsm is opened in the ubuntu session/unity profile.

Screen shows a new Ubuntu session user opening Pref's when the unity profile was 'preloaded', it doesn't say "unity" but it is - the launcher & panel are still there, no hang, ect.

---

### Post by ventrical on 2011-11-05
I agree on # 1. Apparently it appears that the devs of ccsm just more or less gave up - sort of 'lets hope it works ' :) I did have the experimental ppas for compiz and was able to  have preferences work quite satisfactory with the Beta test version of Ocelot. Of course , I haev since upgraded this current install to Precise kernel but I'm willing to check in on Compiz >preferences and see whats up . I was actually able to save and load a profile at one time. Something happened along the way with an update . Exactly what ?? I have no idea. I doubt it has anything to do with video drivers... lemme see here .....

 I'll be back!

---

### Post by ventrical on 2011-11-05
**warning** extreme patience required :)


Ok.. here is my 8 minute boring video of compiz >preferences.

[http://www.youtube.com/watch?v=AnOsm8V-ZWs](http://www.youtube.com/watch?v=AnOsm8V-ZWs)

There is some audio also.

 Mabey it may help somebody have a clue :)

 Luckily I forgot to turn off the crash-handler .. so I bet I'll have a nice fat compiz bug report. :)

---

### Post by ventrical on 2011-11-05
here is crash handler report  ... as usual  not enough memory for backtrace

```

Reading symbols from /usr/bin/compiz...(no debugging symbols found)...done.
Attaching to program: /usr/bin/compiz, process 1535
Reading symbols from /usr/lib/i386-linux-gnu/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libX11.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXrandr.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXinerama.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXext.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libICE.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libICE.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libSM.so.6
Reading symbols from /usr/lib/libgtk-3.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgtk-3.so.0
Reading symbols from /usr/lib/libglibmm-2.4.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglibmm-2.4.so.1
Reading symbols from /usr/lib/libsigc-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libsigc-2.0.so.0
Reading symbols from /lib/i386-linux-gnu/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libglib-2.0.so.0
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /lib/i386-linux-gnu/libpthread.so.0...(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread 0xa891db70 (LWP 2018)]
[New Thread 0xb63ffb70 (LWP 1601)]
[New Thread 0xb6d87b70 (LWP 1600)]
Loaded symbols for /lib/i386-linux-gnu/libpthread.so.0
Reading symbols from /lib/i386-linux-gnu/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libdl.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libstdc++.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libstdc++.so.6
Reading symbols from /lib/i386-linux-gnu/libgcc_s.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libgcc_s.so.1
Reading symbols from /lib/i386-linux-gnu/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libc.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libxcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libxcb.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXrender.so.1
Reading symbols from /lib/i386-linux-gnu/libuuid.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libuuid.so.1
Reading symbols from /usr/lib/libgdk-3.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk-3.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXfixes.so.3
Reading symbols from /usr/lib/i386-linux-gnu/libatk-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libatk-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libcairo-gobject.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libcairo-gobject.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libcairo.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libgio-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgio-2.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libpango-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libfontconfig.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0
Reading symbols from /lib/i386-linux-gnu/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libm.so.6
Reading symbols from /lib/i386-linux-gnu/libpcre.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libpcre.so.3
Reading symbols from /lib/i386-linux-gnu/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/librt.so.1
Reading symbols from /usr/lib/libxcb-util.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxcb-util.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libX11-xcb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libX11-xcb.so.1
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/i386-linux-gnu/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXau.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXdmcp.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libXi.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXi.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXcursor.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXcomposite.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXdamage.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libfreetype.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libfreetype.so.6
Reading symbols from /usr/lib/i386-linux-gnu/libpixman-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libpixman-1.so.0
Reading symbols from /lib/i386-linux-gnu/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libpng12.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libxcb-shm.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libxcb-shm.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libxcb-render.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libxcb-render.so.0
Reading symbols from /lib/i386-linux-gnu/libz.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libz.so.1
Reading symbols from /lib/i386-linux-gnu/libselinux.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libselinux.so.1
Reading symbols from /lib/i386-linux-gnu/libresolv.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libresolv.so.2
Reading symbols from /lib/i386-linux-gnu/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libexpat.so.1
Reading symbols from /usr/lib/i386-linux-gnu/libgthread-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libgthread-2.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libffi.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libffi.so.6
Reading symbols from /usr/lib/liboverlay-scrollbar3-0.2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/liboverlay-scrollbar3-0.2.so.0
Reading symbols from /lib/i386-linux-gnu/libnss_compat.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnss_compat.so.2
Reading symbols from /lib/i386-linux-gnu/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnsl.so.1
Reading symbols from /lib/i386-linux-gnu/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnss_nis.so.2
Reading symbols from /lib/i386-linux-gnu/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libnss_files.so.2
Reading symbols from /usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so
Reading symbols from /usr/lib/libcanberra-gtk3.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcanberra-gtk3.so.0
Reading symbols from /usr/lib/libcanberra.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcanberra.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libvorbisfile.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libvorbisfile.so.3
Reading symbols from /usr/lib/i386-linux-gnu/libtdb.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libtdb.so.1
Reading symbols from /usr/lib/libltdl.so.7...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libltdl.so.7
Reading symbols from /usr/lib/i386-linux-gnu/libvorbis.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libvorbis.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libogg.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libogg.so.0
Reading symbols from /usr/lib/gio/modules/libgvfsdbus.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gio/modules/libgvfsdbus.so
Reading symbols from /usr/lib/gvfs/libgvfscommon.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gvfs/libgvfscommon.so
Reading symbols from /lib/i386-linux-gnu/libdbus-1.so.3...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libdbus-1.so.3
Reading symbols from /lib/i386-linux-gnu/libudev.so.0...(no debugging symbols found)...done.
Loaded symbols for /lib/i386-linux-gnu/libudev.so.0
Reading symbols from /usr/lib/gtk-3.0/3.0.0/theming-engines/libunico.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gtk-3.0/3.0.0/theming-engines/libunico.so
Reading symbols from /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so
Reading symbols from /usr/lib/compiz/libccp.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libprotobuf.so.7...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libprotobuf.so.7
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libgconf-2.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libdbus-glib-1.so.2
Reading symbols from /usr/lib/compiz/libcomposite.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcomposite.so
Reading symbols from /usr/lib/compiz/libopengl.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libopengl.so
Reading symbols from /usr/lib/nvidia-current-updates/libGL.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/nvidia-current-updates/libGL.so.1
Reading symbols from /usr/lib/nvidia-current-updates/tls/libnvidia-tls.so.280.13...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/nvidia-current-updates/tls/libnvidia-tls.so.280.13
Reading symbols from /usr/lib/nvidia-current-updates/libnvidia-glcore.so.280.13...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/nvidia-current-updates/libnvidia-glcore.so.280.13
Reading symbols from /usr/lib/compiz/libdecor.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecor.so
Reading symbols from /usr/lib/libdecoration.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libvpswitch.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libimgpng.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgpng.so
Reading symbols from /usr/lib/compiz/libresize.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libcompiztoolbox.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcompiztoolbox.so
Reading symbols from /usr/lib/compiz/libgrid.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgrid.so
Reading symbols from /usr/lib/compiz/libmousepoll.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmousepoll.so
Reading symbols from /usr/lib/compiz/libregex.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libgnomecompat.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libgnomecompat.so
Reading symbols from /usr/lib/compiz/libanimation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/i386-linux-gnu/libGLU.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libGLU.so.1
Reading symbols from /usr/lib/compiz/libwobbly.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libwobbly.so
Reading symbols from /usr/lib/compiz/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcube.so
Reading symbols from /usr/lib/compiz/librotate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/librotate.so
Reading symbols from /usr/lib/compiz/libexpo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libexpo.so
Reading symbols from /usr/lib/compiz/libscale.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libscale.so
Reading symbols from /usr/lib/compiz/libunityshell.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libunityshell.so
Reading symbols from /usr/lib/libnux-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libnux-1.0.so.0
Reading symbols from /usr/lib/libnux-graphics-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libnux-graphics-1.0.so.0
Reading symbols from /usr/lib/libnux-image-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libnux-image-1.0.so.0
Reading symbols from /usr/lib/libGLEW.so.1.5...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLEW.so.1.5
Reading symbols from /usr/lib/libnux-core-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libnux-core-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libbamf3.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libbamf3.so.0
Reading symbols from /usr/lib/libdee-1.0.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdee-1.0.so.1
Reading symbols from /usr/lib/libdbusmenu-glib.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbusmenu-glib.so.4
Reading symbols from /usr/lib/libindicator3.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libindicator3.so.6
Reading symbols from /usr/lib/libunity-misc.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libunity-misc.so.4
Reading symbols from /usr/lib/libutouch-geis.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libutouch-geis.so.1
Reading symbols from /usr/lib/libjson-glib-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjson-glib-1.0.so.0
Reading symbols from /usr/lib/i386-linux-gnu/libnotify.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libnotify.so.4
Reading symbols from /usr/lib/libgnome-desktop-3.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgnome-desktop-3.so.2
Reading symbols from /usr/lib/libunity-core-4.0.so.4...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libunity-core-4.0.so.4
Reading symbols from /usr/lib/libGLEWmx.so.1.5...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLEWmx.so.1.5
Reading symbols from /usr/lib/i386-linux-gnu/libXxf86vm.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libXxf86vm.so.1
Reading symbols from /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
Reading symbols from /usr/lib/gio/modules/libdconfsettings.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gio/modules/libdconfsettings.so
Reading symbols from /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
Reading symbols from /usr/lib/i386-linux-gnu/libjpeg.so.8...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/libjpeg.so.8
Reading symbols from /usr/lib/gio/modules/libgioremote-volume-monitor.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/gio/modules/libgioremote-volume-monitor.so
Reading symbols from /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so
Reading symbols from /usr/lib/i386-linux-gnu/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/i386-linux-gnu/librsvg-2.so.2
Reading symbols from /usr/lib/libcroco-0.6.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
0x00932416 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 4 (Thread 0xb6d87b70 (LWP 1600)):
#0  0x00932416 in __kernel_vsyscall ()
#1  0x00a7440e in poll () from /lib/i386-linux-gnu/libc.so.6
#2  0x0016234b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x00153896 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x00153f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x03db3194 in ?? () from /usr/lib/gio/modules/libdconfsettings.so
#6  0x0017a5f4 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x003b9d31 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x00a830ce in clone () from /lib/i386-linux-gnu/libc.so.6
Backtrace stopped: Not enough registers or memory available to unwind further

Thread 3 (Thread 0xb63ffb70 (LWP 1601)):
#0  0x00932416 in __kernel_vsyscall ()
#1  0x00a7440e in poll () from /lib/i386-linux-gnu/libc.so.6
#2  0x0016234b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x00153896 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x00153f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x05ce1cea in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#6  0x0017a5f4 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x003b9d31 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x00a830ce in clone () from /lib/i386-linux-gnu/libc.so.6
Backtrace stopped: Not enough registers or memory available to unwind further

Thread 2 (Thread 0xa891db70 (LWP 2018)):
#0  0x00932416 in __kernel_vsyscall ()
#1  0x003bde04 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x005df021 in ?? () from /usr/lib/i386-linux-gnu/libgthread-2.0.so.0
#3  0x001253f0 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x00125dae in g_async_queue_timed_pop () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x0017c95b in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#6  0x0017a5f4 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x003b9d31 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x00a830ce in clone () from /lib/i386-linux-gnu/libc.so.6
Backtrace stopped: Not enough registers or memory available to unwind further

Thread 1 (Thread 0xb76f0880 (LWP 1535)):
#0  0x00932416 in __kernel_vsyscall ()
#1  0x00a4c06b in waitpid () from /lib/i386-linux-gnu/libc.so.6
#2  0x009ed6e3 in ?? () from /lib/i386-linux-gnu/libc.so.6
#3  0x009edb9a in system () from /lib/i386-linux-gnu/libc.so.6
#4  0x003c1ebb in system () from /lib/i386-linux-gnu/libpthread.so.0
#5  0x0132b8b5 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  <signal handler called>
#7  0x0159b572 in nux::Property<nux::color::Color>::Set(nux::color::Color const&) () from /usr/lib/compiz/libunityshell.so
#8  0x0159ae34 in unity::switcher::SwitcherController::OnBackgroundUpdate(_GVariant*, unity::switcher::SwitcherController*) () from /usr/lib/compiz/libunityshell.so
#9  0x015bb934 in ?? () from /usr/lib/compiz/libunityshell.so
#10 0x0014f110 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#11 0x0015325f in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
#12 0x00153990 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#13 0x00153f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#14 0x00446753 in Glib::MainLoop::run() () from /usr/lib/libglibmm-2.4.so.1
#15 0x08072497 in CompScreen::eventLoop() ()
#16 0x08065634 in main ()
(gdb) 
(gdb) 
(gdb) #0  0x00932416 in __kernel_vsyscall ()
#1  0x00a4c06b in waitpid () from /lib/i386-linux-gnu/libc.so.6
#2  0x009ed6e3 in ?? () from /lib/i386-linux-gnu/libc.so.6
#3  0x009edb9a in system () from /lib/i386-linux-gnu/libc.so.6
#4  0x003c1ebb in system () from /lib/i386-linux-gnu/libpthread.so.0
#5  0x0132b8b5 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  <signal handler called>
#7  0x0159b572 in nux::Property<nux::color::Color>::Set(nux::color::Color const&) () from /usr/lib/compiz/libunityshell.so
#8  0x0159ae34 in unity::switcher::SwitcherController::OnBackgroundUpdate(_GVariant*, unity::switcher::SwitcherController*) () from /usr/lib/compiz/libunityshell.so
#9  0x015bb934 in ?? () from /usr/lib/compiz/libunityshell.so
#10 0x0014f110 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#11 0x0015325f in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
#12 0x00153990 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#13 0x00153f9b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#14 0x00446753 in Glib::MainLoop::run() () from /usr/lib/libglibmm-2.4.so.1
#15 0x08072497 in CompScreen::eventLoop() ()
#16 0x08065634 in main ()
(gdb) A debugging session is active.

    Inferior 1 [process 1535] will be detached.

Quit anyway? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz, process 1535
```

---

### Post by ventrical on 2011-11-05
and here from syslog.

Nov  5 13:11:46 ubuntu kernel: [36933.977635] compiz[5028]: segfault at 24 ip 04988954 sp bf8de47c error 4 in libcomposite.so[497d000+16000]
Nov  5 13:11:46 ubuntu gnome-session[4951]: WARNING: Application 'compiz.desktop' killed by signal
Nov  5 13:11:46 ubuntu gnome-session[4951]: WARNING: App 'compiz.desktop' respawning too quickly
Nov  5 13:11:46 ubuntu gnome-session[4951]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov  5 13:12:52 ubuntu AptDaemon: INFO: Quitting due to inactivity
Nov  5 13:12:52 ubuntu AptDaemon: INFO: Quitting was requested
Nov  5 13:15:01 u

---

### Post by mc4man on 2011-11-10
The issue(s) with opening "Preferences" in ccsm has been fixed in both OO & PP with new compizconfig-python (0.9.5.94-0ubuntu3)

Available for both atm in the respective proposed repo, along with  bug fix compiz & nautilus packages

Edit; for any further tracking
[https://bugs.launchpad.net/compiz-compizconfig-python/+bug/874799](https://bugs.launchpad.net/compiz-compizconfig-python/+bug/874799)

---

### Post by effenberg0x0 on 2011-11-10
> **mc4man said:**
> The issue(s) with opening "Preferences" in ccsm has been fixed in both OO & PP with new compizconfig-python (0.9.5.94-0ubuntu3)

Available for both atm in the respective proposed repo, along with  bug fix compiz & nautilus packages

Edit; for any further tracking
[https://bugs.launchpad.net/compiz-compizconfig-python/+bug/874799](https://bugs.launchpad.net/compiz-compizconfig-python/+bug/874799)

That's just great, will help with other stuff I'm doing right now.

I really wish they fixed the dbus plugin, but that one is broken for a long time and it looks like will not be fixed so soon (not sure if its no longer supported by anyone).

Thanks for the notice :)

---

### Post by effenberg0x0 on 2011-11-10
I guess this also answers something else: A while ago I had asked if people here believed ccsm would still be in PP or if settings for plugins would be migrated to settings panel. Looks like ccsm will be alive in pp.

---

### Post by mc4man on 2011-11-10
Still wish they would create a config tool for unity* settings that's default installed & visible

( was just looking at what happens when someone inadvertently  hits Alt+F1 instead of Alt+F2 & doesn't know about Alt+F1 which is described in the unity plugin settings only. 
If they don't notice "Desktop" in upper l. panel disappearing there's no indication of the focus change.

All sorts of bad behavior start until one then uses the arrow key to select an icon and enter on keyboard to remove the launcher focus

---

### Post by ventrical on 2011-11-10
> **mc4man said:**
> Still wish they would create a config tool for unity* settings that's default installed & visible

( was just looking at what happens when someone inadvertently  hits Alt+F1 instead of Alt+F2 & doesn't know about Alt+F1 which is described in the unity plugin settings only. 
If they don't notice "Desktop" in upper l. panel disappearing there's no indication of the focus change.

All sorts of bad behavior start until one then uses the arrow key to select an icon and enter on keyboard to remove the launcher focus


Yep, it locks up until you hit <Esc>

---

