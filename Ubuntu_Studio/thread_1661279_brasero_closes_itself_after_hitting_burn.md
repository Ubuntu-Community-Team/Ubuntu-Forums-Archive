---
title: "brasero closes itself after hitting burn"
date: 2011-01-06
forum: Ubuntu Studio
---

### Post by surfmonkee on 2011-01-06
just installed ubuntu studio and so far loving it.

two tests first, install vlc, perfect and love it.

burn a dvd from a avi file, disaster.

opened brasero,selected the dvd video option, added a typical 700mb avi movie file, when i hit the burn button the program just closes!

i didnt have a disc in the machine, i was trying to make a cue file but if i insert a blank verbatim dvd disc it does the same thing.

any help would be appreciated, is there a better tool to create dvd content from an avi file?  i can use ffmpeg command lines if you know the command to generate a bunch of vob files for a dvd ts file.

---

### Post by babarosa on 2011-01-07
You do not tell us which version of operating system you are using.
The version of brasero (cdrdao) coming with 10.04 is buggy. Get it from this ppa

[https://launchpad.net/~renbag/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~renbag/+archive/ppa?field.series_filter=lucid) for 10.04

Be sure also to update the "cdrdao" file!
If it fails, gnomebaker is a very good working alternative for burning CDs and DVDs.

Handbrake and DVDStyler are my tools for transcoding and generating MovieDVDs.
Latest 10.04 versions:
Handbrake snapshots ppa [https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)
DVDStyler ppa [https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid?field.series_filter=](https://launchpad.net/~ferramroberto/+archive/linuxfreedomlucid?field.series_filter=)

---

### Post by surfmonkee on 2011-01-07
sorry i should know better! on the laptop:

ubuntu 10.10 meerkat with brasero 2.32.0

and on the desktop:

ubuntu studio 10.10 and 2.32.0 brasero

both behave the same way


i did manage to make a reasonble dvd frfom avi using devede and brasero to burn the iso file.  i would rather have an all in one solution.


i am very new to ubuntu so i doubt i shall learn how to use ppa stuff this weekend let alone how to actually download it and i wouldnt know how to update cdrdao either, im finding the studio ubuntu quite challenging so that definately wont get updated anytime soon!

thanks for your reply, i shall read read read!

---

### Post by Pablo_F on 2011-01-07
Hi surfmonkee!

Whenever you encounter a weird issue with a program, try launching it from a terminal window. In this case, just type:

brasero

Hopefully, the terminal will tell what the flip is up.

cdrao is a program that brasero uses in the background. You don't need to know how to use cdrao, just install a more recent cdrao version (if this is the actual problem).

Adding a PPA to your software origins is easy and well explained in every PPA site. Once the PPA is added, you forget about downloading packages from the PPA through the web browser. What you do is use a program that manages the software packages. For you is just "install". For the package manager is download the desired packages and dependencies if any, install and configure. That is a mouse click or a command like "sudo apt-get install package". For a graphical interface you can use Synaptic.

Also, note that ubuntustudio is 99% ubuntu. 

EDIT: You have to check that the PPA has the packages for maverick. It is very important that the packages are compatible with your ubuntu version.  

Cheers, Pablo

---

### Post by surfmonkee on 2011-01-08
thanks for your reply, i have managed to use devede to make an image then im using brasero to burn.

i recall cdrao from my window days.

i have looked at using ppa's i shall investigate further.

i can launch brasero from the terminal, the only error it throws up is 'failed to load image' and makes reference to a png file.  no worries, im good with what i have for now using devede.

again, thanks for your time

---

### Post by Pablo_F on 2011-01-08
Cool

---

### Post by TrevorDuke on 2011-02-01
trevor@trevor-t410:~$ brasero

** (brasero:3970): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory


(brasero:3970): GLib-CRITICAL **: g_variant_builder_end: assertion `is_valid_builder (builder)' failed

(brasero:3970): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(brasero:3970): GLib-CRITICAL **: g_variant_type_is_array: assertion `g_variant_type_check (type)' failed

(brasero:3970): GLib-CRITICAL **: g_variant_get_type_string: assertion `value != NULL' failed

GLib-ERROR **: g_variant_new: expected array GVariantBuilder but the built value has type `(null)'
aborting...
Aborted



After operning brasero, i added a file and clicked burn . then brasero closed

---

### Post by DexterP17 on 2011-02-02
I was having the same issue but I found out the fix in the help and support section of Brasero! All you have to do is install this: DVDauthor in the Ubuntu Software Center or Synaptic and you can start burning DVDs. I hope this helps.

---

### Post by dc2045 on 2011-02-03
Same thing keeps happening to me too. No error or warning.

---

