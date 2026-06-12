---
title: "Ubuntu and the Wiimote"
date: 2011-11-23
forum: Tutorials
---

### Post by nickleboyblue on 2011-11-23
I've always wanted to have a controller for my favorite games that used accelerometers to control movement.  The problem has always been that all of the solutions out there were never customizable enough to meet my needs as a Linux gamer.

Recently, I discovered Wiican, a project that aims at making the best wiimote software for Linux that you'll find anywhere.  Here's the scoop:  They've actually got a great gui that works like a charm (except that it seems to have problems in 11.10 64-bit, though I'm not 100% certain about that).  It allows you to write custom maps for different applications, it allows you to easily connect the controller to your computer through bluetooth, and once connected, it actually makes the wiimote recognizable to the system as a gamepad, making it possible to use other programs to finalize the mapping of controls and get your ultimate interface for your favorite game.

Hardware you will need:
1-Bluetooth adapter
2-Wiimote
3-(optional) Nunchuck
4-(optional) Sensor bar

So, here's how to do it:  First off, I wouldn't download wiican through the repositories.  It may be available from playdeb, but you should probably install the tar file instead.  Download it [here]("http://fontanon.org/wiican/") and run the following command:

```
tar -xzvf <filename>.tar.gz
```

That will get you a brand new file that you should navigate your terminal into and run this next command:

```
cat INSTALL
```

This file has a list of dependencies, so you should read through them and make sure your system as them installed.  Some of them, like PLY, have a completely different name in the Ubuntu repositories (in this case, python-ply).  Once finished with that task, follow the instructions in the INSTALL file and execute the following command:

```
sudo python setup.py install
```

Enter your password, let it copy/paste files for a couple of seconds, and voila! You've installed wiican.

I suggest at this point that you head on over to playdeb and install qjoypad.  It's the most advanced gamepad mapper I've found yet for Linux, and it's amazing.  It supports multiple devices, multiple profiles, and easy input mapping.  Once you have qjoypad installed, you are ready to work on the maps in wiican.

Open wiican (sudo wiican or just wiican from the command line, though sudo may be necessary depending on your setup).  It will show you a window that has a bunch of configurations.  Select the ones you want to have visible in the appindicator menu, and create a couple of your own.  I suggest you don't make up any key bindings on your own, as these configuration files are rather picky about syntax.  Just browse the other configurations and mix and match the different buttons from the control to the different button slots available in the pre-made configurations.

Once you've gotten a configuration that meets your needs (or two or three...), connect your wiimote to your machine.  This is done by clicking on the menu item for the profile you want to activate in the wiican menu.  It will prompt you to put the wiimote in discovery mode, which you do by pushing the "1" and "2" buttons at the same time (on my controller, lights blink to tell me that it's trying to connect).  Once connected, your controller should work fine with most programs that allow you to define the inputs.

At this point, open qjoypad and set up your final key mapping.  Create a profile for each game or application you wish to use the wiimote for, and save them all (this may require starting your games multiple times to get the settings just right).

If you change profiles while qjoypad is up, it will look like your wiimote is not connected.  No worries! Simply ask qjoypad to refresh it's data on joysticks.

(side note:  qjoypad doesn't like Unity so much, so launch it with "qjoypad --notray", which will open a tiny window at some random place on your desktop.  This window gives you all of the functionality of the traditional system tray menu of qjoypad).

Optional: Get a sensor bar (not too expensive) or make one yourself by placing two infrared lights a short distance from each other on top or your television set or whatever screen your computer uses.  This allows you to use the wiimote as a much more precise mouse on your screen, which is fun if you're running mythubuntu.

I have not yet found a way to get wiican to automatically pick a profile and scan for connections on boot.  This would be especially nice if you run Mythubuntu (as I do) and wanted to use the wiimote as a RE-mote and control myth tv, boxee, and hulu from one device without getting up from the couch (we're getting lazier every day...).

A couple of good games to use the wiimote with:

Neverball (good with a profile that lets you use the accelerometers to balance the platforms.  You'll have to make that profile yourself).

Tee Worlds (if you can get the mouse working with the joystick of a nunchuck, you can totally rock on this game using the wiimote-nunchuck combination).

Red Eclipse (great FPS.  Xbox styled controllers work best for this game, but I am aware that some people may use the wiimote so much that they get better at it than anybody else could ever hope to become).

SuperTuxKart (Great open source racer, very similar to a funny game starring a plumber, some monkies, a princess, a couple of dinosaurs, ... you get the point).

Virtually any racing game (with wiimote addons like the steering wheel, this would be great!)

Frets On Fire (again, with wiimote addons, this one could rock as much as the commercial games with the same themes)

Plus, it's pretty cool to just point it at the screen and watch the pointer move around.

Hope this helps someone out there.  If anyone reading this has any further tips to make this setup even better, PLEASE let us know.  This is one of those things we can all rub in our friends' faces as yet another reason why Linux gaming is so much fun.

Oh, and one last thing.  The wiimote is capable of working well as a head-tracking interface.  with a couple of them connected to the computer, you could create one of the most amazing 3d interfaces possible with today's tech.  Check out youtube for a video on how other people have accomplished this.  And if you're a developer, headtracking interfaces using this system could be super cool.

Have a nice day, and keep up the hacking!

---

### Post by neu5eeCh on 2011-12-26
//**Side Note:**  qjoypad doesn't like Unity  so much, so launch it with "qjoypad --notray", which will open a tiny  window at some random place on your desktop.  This window gives you all  of the functionality of the traditional system tray menu of qjoypad.//

**And about that side note:** I've been using qjoypad with Edubuntu 11.10. It also seems to have trouble applying settings from one session to another. In other words, if one creates a profile for a given game (and though the profile is registered after a restart or reboot) one still has to recreate it every time one wants to play a given game. At this point, I probably wouldn't recommend Unity for serious gaming, at least not where gamepad/keymapping is concerned. Go back to pre-Unity Ubuntu or use Windows.

---

### Post by nickleboyblue on 2012-01-01
QJoypad's bugs, outside of not having an appindicator applet, are probably not related in any way to Unity.  Unity is a great interface with loads of potential, and I am happy with how it has matured so far, especially considering how much it has increased my efficiency as a programmer.

I do agree that Windows is head and shoulders above Ubuntu when it comes to gaming, but I have a life outside of gaming, which means that I have little to no time to spend on games except once in a while when I need to wind down.  Linux's gaming capacities are perfect for my needs.  I would never tell anyone to use Windows for any reason unless their needs cannot be satisfactorily met by alternatives such as Ubuntu.

As for Unity, I think it is a superior desktop, though it still has some maturing to do.  I stick to it because it has doubled my efficiency as a programmer and because it's easy enough to use that I don't have to worry about getting lost anywhere.  Also, the potential Unity has for greatness goes beyond simple desktop usage.  Even my wife likes it better than anything else she's used before, which says a lot of the stagnation of Windows and Apple user interfaces.

---

### Post by neu5eeCh on 2012-01-22
//I would never tell anyone to use Windows for any reason unless their  needs cannot be satisfactorily met by alternatives such as Ubuntu.//

Like when you have children who want a functioning gamepad. Whether or not it's related[COLOR=Black] to [/COLOR][COLOR=Black]Unity is irrelevant. If anyone has kids who want a functioning [/COLOR][COLOR=Black]Gamepad, I recommend [/COLOR][COLOR=Black]Windows.  If you don't like that, then volunteer your time at Canonical so that Edubuntu is something kids *will want to use their gamepads with*[/COLOR][COLOR=Black]. Other than that, my advice remains unchanged.[/COLOR]

---

