---
title: "HOWTO: Get new linuxsampler (1.0) work"
date: 2009-10-29
forum: Ubuntu Studio
---

### Post by barisurum on 2009-10-29
Hey, rejoice ubuntu studio users!

I've been struggling to get linuxsampler - fantasia to work for some time. I tried many things from compiling to installing them under wine (yes a shame but I was curious ) and believe me it was a disaster!) and finally I found this ppa archive by David Konsumer:

[https://launchpad.net/~david-konsumer/+archive/konsumer](https://launchpad.net/~david-konsumer/+archive/konsumer)

Brand new linuxsampler, qsampler stuff there including amd64 builds! downloaded them all and first installed the libgig6 and liblscp packages from the ppa and then tried to install liblinuxsampler (1.0)

There were dependency problems with libjack in liblinuxsampler package and the name is libjack0 in our repos so I searched virtually all the web (just joking) and found this solution, guess where? Of course in our beloved ubuntu forums again:

[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

Using the second script I found there (use the script with gedit as the editor its easier) I was able to change the debian control file inside the liblinuxsampler deb and changed the [COLOR="Red"]libjack[/COLOR] dependency to [COLOR="Red"]libjack0[/COLOR] on the depends line. I also changed the [COLOR="Red"]libgig[/COLOR] (with version number) to [COLOR="Red"]libgig6[/COLOR] to look like: [COLOR="Blue"]libgig6 (>= 3.3.0)[/COLOR] and removed the other unneeded libgig6 entry. And after that liblinuxsampler installed no problem.

There was another depends problem with linuxsampler package (libgig problem) so I edited that with the script too to change [COLOR="Red"]libgig[/COLOR] to [COLOR="Red"]libgig6[/COLOR]. Installed it too without problems.

The rest is easy, just install fantasia from [here]("http://sourceforge.net/projects/jsampler/files/Fantasia/Fantasia%200.9/Fantasia-0.9.jar/download") and start rocking!

I would like to thank David Konsumer for his excellent (ok maybe not excellent but efficient enough) ppa archive, loevborg for this wonderful videbcontrol script and motin for modifying it to work with gedit.

Cheers

---

### Post by mickyching on 2009-10-30
Thanks a million Mr Barisurum. Very useful indeed. I've taken a quick look at the links and i think this could be quite an interesting path to follow. Once again thank you very much.

---

### Post by barisurum on 2009-11-10
The ppa builds by konsumer may get updated (I don't know) and fixed, so please try to install them first and then try to hack them with the above solution. and finally... do some great music! :)

---

