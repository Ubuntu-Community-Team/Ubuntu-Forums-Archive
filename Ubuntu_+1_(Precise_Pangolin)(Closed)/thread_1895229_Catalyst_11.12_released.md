---
title: "Catalyst 11.12 released"
date: 2011-12-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jfernyhough on 2011-12-14
New fglrx released. Builds and installs fine.

As always, I use --buildpkg so I have the .debs:

$ wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-12-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-12-x86.x86_64.run)
$ chmod +x ati-driver-installer-11-12-x86.x86_64.run
$ ./ati-driver-installer-11-12-x86.x86_64.run --buildpkg Ubuntu/precise
$ sudo dpkg -i *.deb

---

### Post by kaldor on 2011-12-14
How's the performance/quality on Unity?

---

### Post by Harry33 on 2011-12-14
For those, that want to install the deb-file (fglrx-installer) for Precise, go get it from xorg-edgers PPA.

Here:
[https://launchpad.net/~xorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=precise")

---

### Post by jfernyhough on 2011-12-14
> **kaldor said:**
> How's the performance/quality on Unity?I'm sure there's an issue with Unity (and gnome-shell) and VBLANK with fglrx.

Running Unity moving windows is slowww. Running gnome-session-fallback with Compiz window movements are smooth, but slow after a while. 

Running gnome-shell with $ CLUTTER_VBLANK=none gnome-shell --replace then mutter is also very smooth (though I haven't found a way of getting it to work with an environment variable).

---

### Post by Dlambert on 2011-12-14
> **jfernyhough said:**
> New fglrx released. Looks to build fine.

As always, I use --buildpkg so I have the .debs:

$ wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-12-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-12-x86.x86_64.run)
$ chmod +x ati-driver-installer-11-12-x86.x86_64.run
$ ./ati-driver-installer-11-12-x86.x86_64.run --buildpkg Ubuntu/precise
$ sudo dpkg -i *.deb

Good news, but not if performance is bad :(

---

### Post by kaldor on 2011-12-15
> **jfernyhough said:**
> Running Unity moving windows is slowww. Running gnome-session-fallback with Compiz window movements are smooth, but slow after a while.

I use the open source driver and have this exact issue.

---

### Post by ncholson on 2011-12-15
still not work on my ATi Radeon 6470M ,,  ....

when open the CCC, 

"theres no ati driver installed, please install ati driver or reconfigure with aticonfig". 

can somebody help me???
Spek : HP Pavilion 431, Pros i5 Sandy Bridge, VGA ATI Radon 6470M ..

NB : My hardware temp alway show 80C , this really make me confused >,<

---

### Post by jfernyhough on 2011-12-16
If you install using the AMD installer (e.g. from the first post) or install fglrx directly (e.g. with apt-get) you may need to run

$ sudo aticonfig --initial

and reboot for fglrx to be loaded.

If you use Jockey (Additional Drivers) everything "should" be done for you if you click "Activate".

If things still don't seem to be working run glxinfo in a terminal. If it errors reinstall fglrx so it rebuilds (there's probably a more direct way with DKMS but this is easy), e.g. with $ sudo apt-get install --reinstall fglrx

---

