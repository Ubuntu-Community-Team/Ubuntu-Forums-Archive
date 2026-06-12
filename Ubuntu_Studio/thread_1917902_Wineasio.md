---
title: "Wineasio"
date: 2012-01-30
forum: Ubuntu Studio
---

### Post by 0p7 0u7 on 2012-01-30
Hello, I've installed wineasio but when I choose it as an option in either Reaper or Ableton it gives me an error and doesn't show any inputs or outputs. I was wondering if this was a common problem and if so what the fix would be. Thx :)

---

### Post by sgx on 2012-01-30
Hi, you must run a command after installation of wineasio. Sounds like this was done, but worth doing again.

regsvr32 wineasio.dll

Start jackd/qjackctl, start reaper, and when wineasio is chosen as the asio device in reaper, there is nothing more to do on the linux side.
At that point, reaper is 'running in windows',
and you insert tracks, plugins or media files normally.

You should see reaper auto-connected in qjackctl, and be able
to route its output to any other jackd recognized hardware or software.

If the problem persists, mention the error, wine version,
wineasio version, OS, and basic hardware involved.
Cheers

---

### Post by 0p7 0u7 on 2012-01-30
The problem appears to be that jackbridge isn't running. I installed jackbridge but have no idea how to start it! Help! thx :_(

---

### Post by 0p7 0u7 on 2012-01-30
1.2.2-0ubuntu6 (wine)
0.3-x-1 (wineasio)
Ubuntu Studio 11.04
HP laptop

---

### Post by 0p7 0u7 on 2012-01-30
I did some more research and it looks like my wineasio was just out of date, so I removed it and compiled wineasio .90. Compiled and appeared to install fine but it didn't create a wineasio.dll, just a wineasio.ddl.so.. Therefore I'm not able to load the regsvr32 command.  Reaper loads just fine and allows me to select wineasio but it shows no devices, and then when you exit the preferences it says Audio Device Error, everything works fine through wavemapper, but wavemapper = no asio and no routing. Any ideas? Thx

[FONT=Courier New]> a3n05m41@a3n05m41:~/Desktop/wineasio$ make
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o main.o main.c
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o regsvr.o regsvr.c
winegcc -shared -m32 wineasio.dll.spec -mnocygwin -L/usr/lib32/wine -L/usr/lib32 -o wineasio.dll.so asio.o main.o regsvr.o     -ljack  -lodbc32 -lole32 -lwinmm -luuid
a3n05m41@a3n05m41:~/Desktop/wineasio$ sudo make install
[sudo] password for a3n05m41: 
if [ -d /usr/lib32/wine ]; then cp wineasio.dll.so /usr/lib32/wine; else cp wineasio.dll.so /usr/lib/wine; fi
a3n05m41@a3n05m41:~/Desktop/wineasio$ regsvr32 wineasio.dll
Failed to load DLL wineasio.dll
[/FONT]

---

### Post by 0p7 0u7 on 2012-01-30
At this point it just appears that the driver is failing to register, any idea what would cause this? wineasio.dll.so is located in /usr/lib32/wine/ Thx

---

### Post by 0p7 0u7 on 2012-01-31
I also tried from another post this ---> 
[FONT=Courier New]
> a3n05m41@a3n05m41:/usr/lib/wine$ sudo apt-get install wineasioReading package lists... Done
Building dependency tree       
Reading state information... Done
wineasio is already the newest version.
The following packages were automatically installed and are no longer required:
  gnome-js-common gir1.2-gstreamer-0.10 libseed0 libdesktop-agnostic-fdo-glib
  libboost-date-time1.42.0 fortune-mod libdesktop-agnostic-vfs-gio
  gir1.2-json-glib-1.0 libdesktop-agnostic-cfg-gconf librecode0 gnash-common
  libclutter-1.0-common libclutter-1.0-0 libsamplerate0-dev libffado-dev
  libconfuse0 fortunes-min gir1.2-clutter-1.0 epiphany-browser-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
a3n05m41@a3n05m41:/usr/lib/wine$ sudo ln -s /usr/lib32/wine/wineasio.dll.so /usr/lib/wine/wineasio.dll.so
ln: creating symbolic link `/usr/lib/wine/wineasio.dll.so': File exists
a3n05m41@a3n05m41:/usr/lib/wine$ regsvr32 wineasio.dll
Failed to load DLL wineasio.dll
[/FONT]

---

### Post by sgx on 2012-01-31
In winecfg, make sure alsa is chosen for sound. (jackd support is
likely dead in future mainstream wine releases)

You can uninstall or delete wineasio.dll. and replace it with several versions which are on the web, .rpm versions can be converted with
alien -d name-of.deb

one .deb is here in the attachement link post #1
[http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187)

mine is in /usr/lib/wine  you can copy it there to test.

Other audio distros with live media can be run, and the .dll
cherrypicked from them, but it may be luckier to mate
a wine version with a wineasio from the same repository, and install
them both from synaptic or manually with dpkg -i

It is a pretty simple app, several versions from multiple
distros from V3 on up work here, without compiling anything.
Wine changes so fast, and iscentered on office/gaming apps,
so I stick with a V1.2xxx because it works. Also, the command

a2jmidid -j default

should place a midi port in the midi tab of qjackctl.

Cheers

---

### Post by 0p7 0u7 on 2012-01-31
So I was frustrated enough to do a clean install of ubuntu studio 11.10.  Installed wine 1.2.2. Installed Wineasio .09 from the kxstudio debs. 

Did this
sudo ln -s /usr/lib32/wine/wineasio.dll.so /usr/lib/wine/wineasio.dll.so

And then
a3n05m41@a3n05m41:/usr/lib/wine$ regsvr32 wineasio.dll
Failed to load DLL wineasio.dll

Also tried the .7.5 deb installed with the same result. I'm sure I'm missing something small here but I know I'm not going to be able to get this running until I get that to register.  Please Help! Thx :_/

---

### Post by sgx on 2012-02-01
I would manually copy the .dll instead of linking it.
Then try to regsvr32 wineasio.dll 

if /home was not reformatted, check for a hidden
.wine folder, or wineasio text config that could persist
an error. delete, and run winecfg, choose alsa for sound

There are distros where all this is configured ahead of time.
avlinux 5.02 is a good one, I tested on a usbstick
unetbootin install.

[http://www.bandshed.net/Packages.html](http://www.bandshed.net/Packages.html) for download the iso

[http://www.bandshed.net/custom/](http://www.bandshed.net/custom/)   is the av package list itself,
you could use synaptic to manually delete all wine and .wine folders/files, and just install the wine files here, as a team

Puppy Studio is 380 meg, with wine/wineasio/reaper by default,
runs live in ram, prompts for save file on first shutdown

[http://www.murga-linux.com/puppy/viewtopic.php?t=72402](http://www.murga-linux.com/puppy/viewtopic.php?t=72402)


[https://launchpad.net/~falk-t-j/+archive/festige/+packages](https://launchpad.net/~falk-t-j/+archive/festige/+packages)

falks wine packages, these should work with the 7.5
or 0.9 wineasio

just in case, winecfg and regsvr32 should not ne run as sudo.

Cheers

---

### Post by 0p7 0u7 on 2012-02-01
Just wanted to report back, I did get wineasio to register, it needed to be in /usr/local/lib/wine/ as opposed to /usr/lib/wine/.. Thx :)

---

### Post by 0p7 0u7 on 2012-02-01
Ok so Wineasio registered, jack starts and runs, but the jack driver is not showing up as an option in the wine configuration.. any ideas would be greatly appreciated. Thx.

---

### Post by sgx on 2012-02-01
> **0p7 0u7 said:**
> Ok so Wineasio registered, jack starts and runs, but the jack driver is not showing up as an option in the wine configuration.. any ideas would be greatly appreciated. Thx.

You want to choose alsa in the winecfg audio panel. It seems odd,I know.
Install reaper in your /home/username folder,

wine name-of-insaller.exe

and when you start reaper,

wine /home/username/REAPER/reaper.exe

choose options-->preferences and to choose
 asio device, wineasio should be the option. If you have plugins, create these last two folders

/home/username/.wine/drive_c/Program Files/Steinberg/VstPlugins

copy plugins there, and use reaper VST preferences to choose that
location. Start jackd and qjackctl, Restart reaper, and the plugin location will be scanned, as well as reapers included plugins.

Reaper should X   cross connect in and out in qjackctl.

Also install Festige, an unrelated gui to use the wine/wineasio
engine, written by Falk, that will load many vsts. Nothing supports
dongled vsts, nor likely ever will, but most others will
work in reaper, and very many in Festige.
Cheers

---

