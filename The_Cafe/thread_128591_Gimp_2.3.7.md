---
title: "Gimp 2.3.7"
date: 2006-02-11
forum: The Cafe
---

### Post by drfalkor on 2006-02-11
Here we go,.. I tryed to compile gimp 2.3.7 on my ubuntu breezy, but I could not compile. I need a new version of gtk( and maybe glib? ), Anyway.. could someone compile gimp 2.3.7 and make a .dep out of it ?

Download link: [ftp://ftp.gimp.org/pub/gimp/v2.3/gimp-2.3.7.tar.bz2](ftp://ftp.gimp.org/pub/gimp/v2.3/gimp-2.3.7.tar.bz2)

---

### Post by drfalkor on 2006-02-11
```
checking for GTK+ - version >= 2.8.8...
*** 'pkg-config --modversion gtk+-2.0' returned 2.8.9, but GTK+ (2.8.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GTK+. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: Test for GTK+ failed. See the file 'INSTALL' for help.

```

Weird, I compiled/installed gtk+-2.8.9 and did all that with pkg config, yeah.. I've tryed everything(not everything, but.. yeah)... any suggestions ?

EDIT: If I remove GTK+ (2.8.6), I'm screwed .

---

### Post by drfalkor on 2006-02-12
ooh yeah, I got It compiled and installed - hmm, If I only could make a .deb out of it :-k

---

### Post by kanem on 2006-02-12
[QUOTE=drfalkor]ooh yeah, I got It compiled and installed - hmm, If I only could make a .deb out of it :-k[/QUOTE]
[checkinstall](http://asic-linux.com.mx/~izto/checkinstall/) will make a deb out of it. It's in our repositories. When it's time to do 'make install' do 'checkinstall' instead.

---

### Post by drfalkor on 2006-02-12
Already did a 'make install',.. but I will 'make clean' and 'make' again, and then 'checkinstall', and upload the .deb to a mirror ( if I can find a mirror, anyone know about a mirror I can upload to ? ) 
By the way, where is the .deb saved after the checkinstall ?

EDIT:Ok, I have the .deb now - I only need a upload mirror now :)

---

### Post by kakashi on 2006-02-12
please for the love of god do not make the deb using check install. its a hack and a bad one at that ad can easily screw up your deb 

please make your deb with help of the debian new maintainer's guide. 
ps. i'll make it for you if you can tell me what things you installed (dev tools and others) to get it compiled. if your not in for the latest version then i compiled a deb for 2.3.6 and posted it somewhere in the forums (uploaded to rapidshare //or megaupload don't remeber) . use that.

---

### Post by Sheinar on 2006-02-12
Is it actually worth the hassle of compiling the latest gtk+ to get it working, or isn't there much difference from 2.3.6?

---

### Post by drfalkor on 2006-02-12
Well, I compiled gtk+-2.8.9 and pointed ld.so.conf to the lib files, then I ./configured gimp/compiled and installed,.. it's running very nice here, and I have been using the .deb file without any problems :)

---

### Post by drfalkor on 2006-02-12
[QUOTE=Sheinar]isn't there much difference from 2.3.6?[/QUOTE]

**Changes in GIMP 2.3.7**
=====================

- depend on GTK+ 2.8, use some of the new features
- removed workarounds for problems in GTK+ 2.6
- moved Align Visible Layers to the Image menu
- started to add a new vectors PDB API
- make it more obvious that docks can be rearranged by drag and drop
- modified the behaviour of the Tab key
- added --license command-line option
- improved dither matrix for RGB->Indexed conversion
- added PDB API to stroke with any paint method
- gave some plug-ins more sensible names
- keep settings of brush/pattern/font/... button popups across sessions
- reduced number of memory allocations by declaring some strings as static
- some improvements to the plug-in preview widgets
- added links to important topics in the user manual
- let the configure script display a summary of options
- bug fixes and code cleanup

:-D

---

### Post by spiritz on 2006-02-27
any deb available?

---

### Post by Totzo on 2006-03-01
I found a way that works well for me. (running dapper)

add the debian experimental repositories (src and deb)

Change your dist preference to experimental,

sudo apt-get -b source gimp

dpkg -i all the produced debs (choose one between gimp-wget & gimp-gnomevfs)

change your dist prefs back and off you go!

hope it works.:-D

---

### Post by Bandit on 2006-03-01
[QUOTE=kanem][checkinstall](http://asic-linux.com.mx/~izto/checkinstall/) will make a deb out of it. It's in our repositories. When it's time to do 'make install' do 'checkinstall' instead.[/QUOTE]
It isnt that bad. Its just not the proper way. But I have never ever seen it mess up any of my own or anyone elses systems. If you dont like it, thats fine. Just dont give out FUD.
Cheers,
Joey

---

### Post by Totzo on 2006-03-01
[QUOTE=Bandit]It isnt that bad. Its just not the proper way. But I have never ever seen it mess up any of my own or anyone elses systems. If you dont like it, thats fine. Just dont give out FUD.
Cheers,
Joey[/QUOTE]

I agree, I've used checkinstall and never had any problems, especially where single deb apps are concerned.

---

