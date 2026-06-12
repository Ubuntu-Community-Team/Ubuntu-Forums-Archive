---
title: "Muine plugin bug?"
date: 2005-07-07
forum: Ubuntu Backports
---

### Post by kaput on 2005-07-07
I'm having a problem with the current backported Muine/Icon Tray Plugin packages (0.8.3-3ubuntu1~5.04ubp1). If I install the plugin, attempting to play the current playlist or add songs/albums results in a segfault. Removing the plugin allows me to use Muine without any segfaults, but it obvioulsy eliminates the plugin's capabilities. ;-)  

I'm currently running Hoary on x86 and am willing to provide any other needed info or testing results.

---

### Post by Majlo on 2005-07-07
Hi..
Have you installed Audioscrobbler plugin ? When i install audioscrobbler plugin then always segfault..Icon Tray Plugin work for me great

---

### Post by kaput on 2005-07-07
[QUOTE=Majlo]Hi..
Have you installed Audioscrobbler plugin ? When i install audioscrobbler plugin then always segfault..Icon Tray Plugin work for me great[/QUOTE]

Nope, no Audioscrobbler plugin installed. It's on a fresh install and the version from Hoary's universe repo works perfectly.

---

### Post by TheSavage on 2005-07-07
Got the same problem over here :neutral:

---

### Post by kaput on 2005-07-08
Thanks for the confirmation. Hopefully this will bring the problem to the attention of a maintainer and we can get it fixed.

---

### Post by Majlo on 2005-07-08
Interesting .In Breezy i have problem with muine-plugin-trayicon .When i installed it then always Segmantation Fault .But in Hoary i dont have this problem with backport Muine 0.8.3-4 ..I write this bug into Launchpad [https://launchpad.ubuntu.com/malone/bugs/1304](https://launchpad.ubuntu.com/malone/bugs/1304)

---

### Post by kaput on 2005-07-08
The way I understood it, backported packages are not entirely official, so bugs should be reported to the backport forums, which I did, instead of posting bug reports with Ubuntu devs via ubuntu.com.

Am I missing something or is this the prescribed method for getting a backported package fixed?

---

### Post by Majlo on 2005-07-08
[QUOTE=kaput]The way I understood it, backported packages are not entirely official, so bugs should be reported to the backport forums, which I did, instead of posting bug reports with Ubuntu devs via ubuntu.com.

Am I missing something or is this the prescribed method for getting a backported package fixed?[/QUOTE]

I report bug for Breezy package not for Hoary .For me muine-plugin-trayicon from Backport work fine .In Breezy not .

---

### Post by jdong on 2005-07-09
That makes me think it might be an upstream issue...

---

### Post by Wolki on 2005-07-11
[QUOTE=kaput]I'm having a problem with the current backported Muine/Icon Tray Plugin packages (0.8.3-3ubuntu1~5.04ubp1). If I install the plugin, attempting to play the current playlist or add songs/albums results in a segfault. Removing the plugin allows me to use Muine without any segfaults, but it obvioulsy eliminates the plugin's capabilities. ;-)  

I'm currently running Hoary on x86 and am willing to provide any other needed info or testing results.[/QUOTE]

I had the same problems with the Cuckoo and Ruffle plugins (not available as packages, but really easy to install from source). In that case it was a problem with the new Mono version, downgrading allowed the Cuckoo plugin to work again. Ruffle needs Muine 0.8.3 :-/

Last time I tried, the Tray Icon plugin seemed to work though. Had to reinstall my system after the harddisk failed and didn't upgrade to backports on the new system yet.

---

### Post by Xterminator on 2005-08-07
I'm solving this problem creating a simple file...

```
sudo nano /usr/lib/muine/plugins/TrayIcon.dll.config
```

it writes the text

```
<configuration>
  <dllmap dll="gdk-x11-2.0" target="libgdk-x11-2.0.so.0"/>
  <dllmap dll="libX11" target="libX11.so.6"/>
</configuration>

```

and install libx11-6-dev

```
sudo apt-get install libx11-6-dev
```

run ```
sudo ldconfig
```
and enjoy :-)

it would be interesting to rebuild the package, including this file and adding the dependence for libx11-6-dev.

---

### Post by theraginasian on 2005-08-26
[QUOTE=Xterminator]I'm solving this problem creating a simple file...

```
sudo nano /usr/lib/muine/plugins/TrayIcon.dll.config
```

it writes the text

```
<configuration>
  <dllmap dll="gdk-x11-2.0" target="libgdk-x11-2.0.so.0"/>
  <dllmap dll="libX11" target="libX11.so.6"/>
</configuration>

```

and install libx11-6-dev

```
sudo apt-get install libx11-6-dev
```

run ```
sudo ldconfig
```
and enjoy :-)

it would be interesting to rebuild the package, including this file and adding the dependence for libx11-6-dev.[/QUOTE]
 thanks for the attempt but my tray icon still doesnt work! AHHHH!!

---

### Post by mginou on 2005-09-11
After upgrading from Hoary to Breezy, muine wouldn't run due to a segfault in the Ruffle plugin. Downloading the source, compiling and installing fixed up the problem:

```
tar zxf ruffle-0.3.0b2.tar.gz
cd ruffle-0.3.0b2
make
cp RufflePlugin.dll $HOME/.gnome2/muine/plugins
```

Hope that works for you too.

---

### Post by jdong on 2005-09-11
Please file a bug report for stuff as serious as that!

---

