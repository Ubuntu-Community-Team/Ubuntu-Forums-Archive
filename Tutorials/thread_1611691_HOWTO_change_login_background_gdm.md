---
title: "HOWTO: change login background gdm"
date: 2010-11-02
forum: Tutorials
---

### Post by CristianCantoro on 2010-11-02
Hi everybody,

Many of you maybe are wondering how to change the login background image in gdm, i.e. the purple image which shows behind the login window in GDM, Ubuntu's Gnome Desktop Manager. The image is also the default background in a new Ubuntu installation.

I have surfed the net but have only found not-so-elegant solutions which seems more a "hack" than other.
Here there's a solution, using only the CLI (command line interface) or the GUI at your choice.

Please note that the login background is a different thing from the images you see at start-up, the former are called "spash screen". To change that, search for "plymouth themes" and how to change them.

First, you have to know that what you see when you log in is actually a desktop, precisely it exist a "gdm" user and what you see it's *its* desktop. When the system starts up simply some commands are executed, one of which pops the login window which let you select the user to log in.

So,what you have to do is to change the desktop background for user "gdm".

**Using the GUI**
*Please read all the instructions below before doing anything*

*== The easy way: Ubuntu Tweak ==*
Ubuntu Tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)) is a program to show/edit a lot configuration parameters (for various program) and for doing a bunch of useful things: it's like a (utterly nice ;-)) Ubuntu control panel.

You can easily change the login background going in the "Startup/Login Settings" section.

*== The not-so-easy way: gnome-appearance-properties for gdm ==*
First, open a terminal and type:
```
xhost +SI:localuser:gdm
```
This will give to the user "gdm" the possibility to launch a new  X session.

Second, change user with the command:
```
sudo su -lp gdm
```
this command starts a shell as another user (in this case the gdm user) providing "an environment similar to what the user would expect had the user logged in directly." and preserving environment variables.(see "man su" for more info).

Now you should see that your prompt has became:
```
gdm@yourhostname:~$ 
```
this means that you are now using the shell as the gdm user, this is confirmed launching the command whoami who tells you the current user name:
```
gdm@yourhostname:~$ whoami
gdm
```

Third, to change the background launch:
```
dbus-launch gnome-appearance-properties
```
ignore the warnings and browse to the "Background" tab and choose your favourite one, as you will do for your desktop :)


*== Third choice: exploit gdm's autostart ==*

You can also start gnome-appearance-properties when GDM starts:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```
You are now creating a symbolic link to the gnome-appearance-properties application in the autostart folder of gdm, which contains a list of programs which are automatically launched by gdm at startup (here included the login window itself).

Log out, you will see, other than the usual login window the "appearance" window, so make the changes in the background tab, close the window, log in as usual and remove it form GDM's autostart, with the folliwing code:
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

To see your brand new login background simply log out/change user and enjoy!

**Using the CLI**

Using the CLI is simpler (this is true most of the times ;-)).
```
sudo su -lp gdm
```

Your prompt becomes:
```
gdm@yourhostname:~$ 
```

Second, launch the following:
```
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/path/to/image.ext"
```

where "/path/to/image.ext" (with quotes) is the path to your chosen background image (e.g. "/usr/share/backgrounds/Morning_II_by_Tadas_N.jpg").

Please note that using the CLI method you need to reload the configuration before seeing the changes so you will see the changes on the next reboot _(if someone knows how to reload instantly the gnome configuration please tell us!)._

That's it, enjoy you new login background.

**Author's notes**
[LIST=1]
[*]*a question to X/Gtk experts* - I don't know why, to have the gui method working, I have to open a new X display. In theory I believe I should be able to do the second and third steps without openening a new X display. But here's what I get on my system:
```
cristian@cristian-asus:~$ sudo su -lp gdm
gdm@cristian-asus:~$ dbus-launch gnome-appearance-properties
No protocol specified
No protocol specified

(gnome-appearance-properties:8626): Gtk-WARNING **: cannot open display: :0.0
No protocol specified
Impossibile aprire il display: 
gdm@cristian-asus:~$
```
Please note that on a fresh installation (running in a virtual machine) I can do all that without open a new X display.
[/LIST]
This has been answered below and the HOWTO has been updated! Thanks to sisco311.

---

### Post by ubunterooster on 2010-11-02
Very nice. I do not like the default  login screen and find it as annoying as the green of mint. Now, you left out the hard part: what to choose for the new login screen... ;)

---

### Post by sisco311 on 2010-11-02
> **CristianCantoro said:**
> 
**Author's notes**
[LIST=1]
[*]*a question to X/Gtk experts* - I don't know why, to have the gui method working, I have to open a new X display. In theory I believe I should be able to do the second and third steps without openening a new X display. But here's what I get on my system:
```
cristian@cristian-asus:~$ sudo su -lp gdm
gdm@cristian-asus:~$ dbus-launch gnome-appearance-properties
No protocol specified
No protocol specified

(gnome-appearance-properties:8626): Gtk-WARNING **: cannot open display: :0.0
No protocol specified
Impossibile aprire il display: 
gdm@cristian-asus:~$
```
Please note that on a fresh installation (running in a virtual machine) I can do all that without open a new X display.
[/LIST]

I think you have to add gdm to the list of users allowed to make connection to the X server:
```
xhost +SI:localuser:gdm
```

You can also start gnome-appearance-properties when GDM starts:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```
Log out, make the changes, close the window, log in as usual and remove it form GDM's autostart:
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by karmila on 2010-11-02
I usually use ubuntu-tweak to change gdm background.

---

### Post by CristianCantoro on 2010-11-02
> **sisco311 said:**
> I think you have to add gdm to the list of users allowed to make connection to the X server:
```
xhost +SI:localuser:gdm
```

You are right! I will update the HOWTO, thank you.


> **sisco311 said:**
> 
You can also start gnome-appearance-properties when GDM starts:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```
Log out, make the changes, close the window, log in as usual and remove it form GDM's autostart:
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

This was the not-so-elegant solution that I found on the web: I don't like it and furthermore I needed to change the background without the possibility to logout (I had a chrooted subsystem... long story ;-) )

---

### Post by CristianCantoro on 2010-11-02
> **karmila said:**
> I usually use ubuntu-tweak to change gdm background.

I have Ubuntu-tweak installed on my main system and I think it is a really cool piece of software, so I recommend it (and thank you for the pointer), but I primarily needed a way to change the background using the CLI only. I will update the HOWTO in any case. :popcorn:

---

### Post by sisco311 on 2010-11-02
I do not like neither gdm2setup nor ubuntu-tweak. :(

(EDIT: chrooting is very cool :))

---

### Post by Jose Catre-Vandis on 2010-11-20
Doesn't work for Xubuntu:
```
dbus-launch gnome-appearance-properties
Couldn't exec gnome-appearance-properties: No such file or directory
```

Do you know how to do the same for Xubuntu?

[EDIT] It's alright - Ubuntu Tweak did it for me, but still can't figure out how to do it via the CLI

---

### Post by earlf on 2011-05-05
thanks ChristianCantoro and sisco311.:D

I've got this working on 10.10. Now its image time...

---

### Post by sisco311 on 2011-05-05
> **earlf said:**
> thanks ChristianCantoro and sisco311.:D


You're welcome!

> **earlf said:**
> 
Now its image time...

this traditionally been one of the more difficult steps... :)

---

### Post by twelve17 on 2011-08-05
Thanks for this tip!  In case you want to do this in a one-liner (assuming usage of bash shell):

```
xhost +SI:localuser:gdm && sudo su -lp gdm -c "dbus-launch gnome-appearance-properties"
```

---

### Post by hurtstotalktoyou on 2011-12-13
I used the second "not-so-easy" choice since it didn't require installing any new software, and it worked like a champ!  But there is one addendum which should be added...

After you change the display preferences in gdm, icons for "universal access preferences" will appear in the menu bar.  To remove this, run gnome-keyboard-properties and under the "accessibility" tab uncheck "accessibility features can be toggled with keyboard shortcuts."  That's it!

---

