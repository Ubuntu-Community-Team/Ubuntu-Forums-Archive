---
title: "Installing ubuntu on a small server."
date: 2005-11-12
forum: Server Platforms
---

### Post by Vegettex on 2005-11-12
Hi there :)

I am quite new here, and I already have a question :( Well my situation is like this. I have been using Ubuntu (first 5.04 and upgraded to 5.10) for about 3 months now and I must admit that I definetly like it! So I was planning to install it on my server aswel, previously there was running Win2k3 on it but I thought "Hey lets switch to ubuntu as wel :D". So I formatted the thing and tried to install ubuntu on it. But that failed because the installer says that I don't have enough disk space. Well I could understand that because it is only 4.3 gig totally. But i thought that it would be enough to install ubuntu on it. I am not the expert yet so that I can live without the whole Gnome gui. I have also tried to install it with making my whole partition as ext3 and no swap space but the result was the same.

So my question is pretty simple... does anybody have an idea or thought on how to fix it?

Thanks in advance!

 - Vegettex

---

### Post by Juippisi on 2005-11-12
Make a server-install and install the X and some light WM, like fluxbox, afterwards. Server-install takes something like 500 MB of disk space, so it should work.

---

### Post by Vegettex on 2005-11-12
Thanks for the reply :) Been here, done that...I installed only the server-version so I only have a nice black terminal look-a-like. But how do I install Gnome on it now? Can I run that from the cd or should I apt-get 'something' ?

Greetz!

 - Vegettex

---

### Post by Juippisi on 2005-11-12
Try "apt-get install gnome" - that should install a bunch of packages. But I recommend you trying some lighter WM / DE on the server... like fluxbox or PekWM. But it's your decide and Gnome is good...

---

### Post by tikal26 on 2005-11-12
I use xfce and it seems to work fine for me if you are just going to use it a a server noneed for all fancy stuff.

---

### Post by Vegettex on 2005-11-13
[QUOTE=Juippisi]Try "apt-get install gnome" - that should install a bunch of packages. But I recommend you trying some lighter WM / DE on the server... like fluxbox or PekWM. But it's your decide and Gnome is good...[/QUOTE]

Hmm well I tried the 'apt-get install gnome' but then I get the following [quote="My Server"]The package gnome is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: The package gnome has no installation candidate[/quote]

Yeah, well I wanted to install gnome first, because since I am not really an expert yet and I am used to gnome (the only one I tried yet ;)) but later on I will try another one but for now I wanted to stick with gnome...

Any idea what I am doing wrong?

---

### Post by skirkpatrick on 2005-11-13
I believe you want "sudo apt-get install gnome-desktop".

---

### Post by Vegettex on 2005-11-13
After doing that I get the following error:

[quote="Another error from my server"]GDM: Xserver not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth
/var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM.[/quote]

Bah, hoped it would work :(

Thanks for the idea anyway :) You also have an idea on how to fix this? Or any other idea's?

---

### Post by skirkpatrick on 2005-11-13
I know I've seen this on the forums somewhere.

---

### Post by Sutto on 2005-11-14
try
apt-get install gdm

and then once that has finished user either -
apt-get install gnome-desktop OR
if you would prefer something a little faster,
apt-get install xubuntu-desktop

Then restart, select sessions (I think thats it) and choose whichever desktop you installed.

HTH,
-Sutto

---

### Post by LordHunter317 on 2005-11-14
You need to install an X server: x-window-system-core.

---

### Post by Vegettex on 2005-11-15
[QUOTE=LordHunter317]You need to install an X server: x-window-system-core.[/QUOTE]
Well I formatted it, so I would have a clean install again. So just the server installation with ```
sudo apt-get install x-window-system-core
``` what should I do next? "apt-get install" gdm / gnome-desktop / gnome ? Wich one?

:) Hope this time it is working.

Thanks for all tries guys :cool:

---

