---
title: "can someone eplain more in depth what these stpes mean"
date: 2011-03-06
forum: Wine
---

### Post by Metul Burr on 2011-03-06
[LIST=1]
[*]Make sure you have the following packages installed before you start:
# aptitude install libgl1-mesa-dev x11proto-gl-dev libasound2-dev
At least these were the packages I had to install in Hardy to get Wine  to compile with OpenGL and ALSA support (crucial if you want to get the  game to run at all and with sound as well).
[*]Grab the latest Wine source (1.1.4, at the time of writing) from [the official download site]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449")
[*]Extract the source tarball to its own directory, *cd* to that directory
[*]Download [this patch to the Wine source]("http://bugs.winehq.org/attachment.cgi?id=15883") and rename it to *spore.patch*
[*]*cd* into the *wine-x.x.x* subfolder with the actual source
[*]Apply the patch by issuing the following command:
$ patch -p1 < ../spore.patch
[*]If the patching was successful, compile and install Wine with the following command:
$ tools/wineinstall
Make yourself a sandwich and some coffee, because the compiling may take  a while depending on how fast your CPU is (it took roughly 20 minutes  on my 2.5 GHz Core 2 Duo). When Wine asked me if I wanted to install the  compiled version to my system, I answered “yes” and consequently had to  enter my root password before the installation stage. If you do not  want to install the patched version permanently, answer “no”.
[*]Install *Spore* with the installer from the CD  and cancel the DirectX install popup. The install should finish  normally. If Wine hangs a bit, leave it to do its thing for a  few minutes.
[*]Crack *Spore*’s [stupid DRM]("http://arstechnica.com/news.ars/post/20080908-gamers-fight-back-against-lackluster-spore-gameplay-bad-drm.html") (see disclaimer up top!).
[*]Start the game with the provided Wine launcher or by going to the game’s *Sporebin* directory and typing $ wine SporeApp.exe in the terminal. Enjoy!
[/LIST]

---

