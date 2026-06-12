---
title: "TamTam mini on Ubuntu possible?"
date: 2009-04-28
forum: Ubuntu Studio
---

### Post by jahst on 2009-04-28
First - Hopefully this is the correct forum..sorry if it's not.
Second - Is it possible to install TAMTAM from the Sugar XO on Ubuntu

** Edit - should be the TAMTAM suite.. I guess there are 4 programs. TAMTAM mini, jam, edit, and synth. **


I found this file 
[http://activities.sugarlabs.org/en-US/sugar/addon/4061]("http://activities.sugarlabs.org/en-US/sugar/addon/4061")

And many more
[http://activities.sugarlabs.org/en-US/sugar/browse/type:all/cat:101?sort=popular]("http://activities.sugarlabs.org/en-US/sugar/browse/type:all/cat:101?sort=popular")

I've searched the forums and the web for a long time and only found an old (2007) read-only post by someone asking the same question.. but it never got answered. Seeing how this is 2009, I was hoping someone else might be interested, working on, or better yet solved this.

As a workaround I've ran XO in Qemu.. but it's not the same.

Why do I want this?
Because TamTam is perfect for teaching introductory level music to students that have no experience with music at all.

I've tried hydrogen, muse, etc.. and they all involve mime and the jack server. I've never been able to get it to work properly.. and yes it's probably me. I just need something simple for my students... and myself. haha

So.. is this possible?
Or is there any similar Ubuntu compatible program that is as simple as TamTam?

Thanks,
Jahst

---

### Post by Stochastic on 2009-04-28
It looks like the entire Sugar software installs as one package in ubuntu according to their documentation: [http://wiki.sugarlabs.org/go/Community/Distributions/Ubuntu](http://wiki.sugarlabs.org/go/Community/Distributions/Ubuntu)  Then you'll probably just install your addons as you please.

---

### Post by jahst on 2009-05-02
Thanks for replying. I've tried installing the sugar-emulator and ran into problems.

1st - I was really wondering if just the TAMTAM programs could be run from the gnome desktop without having to worry about introducing students to the sugar desktop. 


2nd- the menu link does nothing. Do I need to be root? lets try.


3rd - as root sugar-emulator starts but I get a black screen. Terminal output shows a something about not being able to take over xorg due to security policies. see code pasted below.


4th - does "sugar-emulator" really mean it's being emulated? How would I go about connecting to network shares in sugar... I'm not sure it can handle that yet.


Here's the error message I get on Ubuntu 9.04
But again, I'd like to run the programs without the sugar desktop if possible.

sudo sugar-emulator
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.423" is not allowed to own the service "org.x.config.display100" due to security policies in the configuration file)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
(EE) XKB: No components provided for device Virtual core keyboard
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.423" is not allowed to own the service "org.x.config.display100" due to security policies in the configuration file)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
matchbox: keyboard does not appear to have a <alt> key.
matchbox: ignoring key shortcut <Alt>return=fullscreen

/usr/lib/python2.6/dist-packages/jarabe/desktop/meshbox.py:19: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
/usr/lib/python2.6/dist-packages/jarabe/desktop/keydialog.py:17: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5

---

### Post by Stochastic on 2009-05-02
From what I understand (not a sugar user myself), you can run sugar as your normal window manager (in a non-emulation way) if you setup a GDM session to do so.  This way at login, you can choose either the regular Gnome session or the sugar session.  I really don't know much more than that.

---

### Post by jahst on 2009-05-10
Well, thanks for your time.
I'll keep looking into it whenever I get a chance.
I'll post back if I do learn something or figure it out.

---

### Post by aureliusm on 2009-07-05
I was fiddling with TamTam Suite on Ubuntu for last couple of days.
I installed Sugar packages as a desktop manager and that part works fine.
Installing activities from web browser activity didn't work.
To install the TamTam packages I had to download them manually and install them from terminal using:

sugar-install-bundle </path/name_of_the_package.xo>

After installation the new activities appeared in the 'frame'.
When tried to run them - they appeared in the 'ring' but after a minute or so they exited without further messages.

I then tried running them from terminal using:

python TamTamMini.py

And then received error messages about libcsound.so.5.1

I then installed csound package using:

apt-get install csound

The error still persisted - it turned out that csound that was installed was 64 bit version for some reason and only libcsound64.so.5.1 was present in /usr/lib
I've created a symbolic link 

ln -s libcsound64.so.5.1 libcsound.so.5.1 

and run a ldconfig

After that the TamTam applications were starting fine in sugar desktop - but there is still no sound

Any suggestions are welcome

---

### Post by jahst on 2009-10-29
aureliusm,

thanks for posting your efforts.
I'm back in school this year, and will continue to mess with this when I have time. I find it hard to believe this is so difficult... you would think there would be a way to simply apt-get install the tamtam packages directly into Ubuntu and skip the whole Sugar emulator route.

Does anyone know why it only works on Sugar?
If it's all Linux shouldn't it just be a dependency thing?

---

### Post by Stochastic on 2009-10-29
For ore information on sugar and possibly porting TamTam out of the sugar desktop environment to another linux-based desktop environment I'd take a look at this page: [http://en.flossmanuals.net/Sugar/Overview](http://en.flossmanuals.net/Sugar/Overview)

I would also casually consult with any programmer friends you might know and run this idea by them.  Most likely they'll smack you upside the head and tell you to just run either the sugar emulator environment (which you've already tried) or run sugar natively (which aureliusm has reported modest success with).  That is of course unless they really enjoy a challenge.

Essentially, you're right it is just a dependency thing, the dependency is sugar.

I realize I'm getting quite curt with you, and for that I apologize.  I do hope you're able to get this up and running as I know a few other people that might be interested in sugar applications.

---

### Post by nadian on 2009-11-13
I'm also interested in getting Tam Tam working in ubuntu, but also some of the other bundled software in sugar, does anyone know if there are any plans to port the educational software package out of sugar wrapping and onto linux / ubuntu?

---

### Post by jahst on 2009-12-01
So after an update to Karmic Koala, I installed sugar and am able to start it up and use it. The e-toys works.. from what I can tell.. as well as writer. But browser didnt work, so I couldnt browse to download the TamTamMini.xo

To install it on Karmic I followed these directions.

[http://wiki.sugarlabs.org/go/Community/Distributions/Ubuntu](http://wiki.sugarlabs.org/go/Community/Distributions/Ubuntu)

To use Sucrose-0.86 on 9.10(Karmic)

sudo sh -c 'echo deb [http://ppa.launchpad.net/sugarteam/0.86/ubuntu](http://ppa.launchpad.net/sugarteam/0.86/ubuntu) karmic main >> /etc/apt/sources.list'
sudo apt-get update
sudo apt-get install sugar-platform


I then logged out and started the Sugar session... and it started up.

I'm behind a proxy at work so I had to open a terminal and

export http_proxy=ip : port

I thought this might fix the browser... but still no browser.
So used wget in a terminal...which did work.

wget [http://wiki.laptop.org/images/f/f6/Tamtammini-51.xo](http://wiki.laptop.org/images/f/f6/Tamtammini-51.xo)

which is the download link to one of the projects found here

[http://wiki.laptop.org/go/Activities](http://wiki.laptop.org/go/Activities)

I then followed aureliusm's post about installing the package.

sugar-install-bundle </path/name_of_the_package.xo>

"sugar-install-bundle Tamtammini-51.xo" in my case

Looks like everything installs? At least everything is extracted.

So now, how do I go about starting the program?

I used "ls" in a terminal and followed this path...

cd Activities

cd TamTamMini.activity

ls now shows setup.py and TamTamMini.py

I tried "python TamTamMini.py" and it just went back to terminal prompt.
"python setup.py" gives an error ---

unlink: cannot unlink 'common': Is a directory and some other stuff I dont have time to copy down right now.

So I try them both as sudo.

setup still gives unlink problem but now the TamTamMini.py also posts some errors...

Traceback 

import common.Util.Instruments
import common.Config as Config
Tam_Tam_ROOT = get_bundle_path()
return os.environ['SUGAR_BUNDLE_PATH'}
raise KeyError(key)

KeyError: 'SUGAR_BUNDLE_PATH'

----------------------------------------

I logged back into a gnome session and repeated the commands in a gnome-terminal.
It posted the same errors.

I have no idea how to use the SUGAR OS, but can't imagine installing and running a program should be this difficult on the actual XO machine.

It's like the terminal commands in the sugar session are not getting applied to the sugar session ?? since they returned the same errors in the gnome session.

So I must be doing something wrong with the install.

What am I missing / doing wrong... that I cant even install it.

I even found a /usr/share/sugar/activities folder that I moved everything to, and it still won't start or show up on the Sugar start Menu thingy. 

I'll keep looking into this...

I also found Sugar-on-a-Stick.iso

I'll try this later and post back as well.

---

### Post by freakalad on 2012-01-30
I've installed a fresh OS, based on Ubuntu, via Trisquel 5.

Unfortunately this problem persists, with no solution in sight.

Seems a problem related to CSound, and I just don't know how to resolve the issue

---

