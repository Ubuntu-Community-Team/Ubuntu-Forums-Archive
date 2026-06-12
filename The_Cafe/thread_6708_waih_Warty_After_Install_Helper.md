---
title: "waih: Warty After Install Helper"
date: 2004-11-30
forum: The Cafe
---

### Post by Nis on 2004-11-30
New feature!  Mozilla Firefox can now be upgraded to 1.0 using the packages from the [Ubuntu Backports Project](http://ubuntu-bp.sourceforge.net/).
This script is designed to help new Ubuntu users perform some common tasks such as installing Java, Flash, and the Nvidia drivers.  You can either download the script [here](http://people.hsc.edu/students/morgand/waih).  The script has been well tested and so far nothing has been broken.

Some things to mention:
[list]
[*]The script is designed for new installs of Warty.  It should work on existing installs hopefully.
[*]This script so far only works on x86 machines.  Sorry ppc users. :(  I don't have a Mac and no one I know with one wants to try Ubuntu (they should though).
[*]The Nvidia install works great.  ATi install I'm not sure about.  I don't have an ATi card and I don't know anybody with one either.  Testing needed!
[*]The script is currently not very smart.  It doesn't even try to recover from errors.  I hope to make it smarter eventually.
[*]If anybody has any ideas for other tasks this script can do please let me know.
[/list] 

Finally I would like to thank everyone who's contributed to the Ubuntu Linux Wiki and the Ubuntu Forums HowTos.  This script mainly just automates the instructions provided by those HowTos.  You guys have done all the hard work. :)

---

### Post by oddabe19 on 2004-11-30
very nice, i didn't use it cause i use hoary, but when i get my test machine back from a friend i'll give it a shot.

Ummm one quick thing, it's probably nothing, but k7 is actually all current amd's (Duron, Athlon, AthlonXP, mobile athlon) not just durons like you have stated...

sorry... i'm a perfectionist :-(

---

### Post by Nis on 2004-11-30
[QUOTE=oddabe19]
Ummm one quick thing, it's probably nothing, but k7 is actually all current amd's (Duron, Athlon, AthlonXP, mobile athlon) not just durons like you have stated...
[/QUOTE]
Easy fix.  Any corrections are quite welcome.  :)

---

### Post by oddabe19 on 2004-11-30
one more thing, i really would like to see an output into terminal (or a command box or something) to see what exactly it is doing (downloading, installing, whatever) so i can see if there are hangups or something.

but that's just my opinion

---

### Post by Nis on 2004-11-30
[QUOTE=oddabe19]one more thing, i really would like to see an output into terminal (or a command box or something) to see what exactly it is doing (downloading, installing, whatever) so i can see if there are hangups or something.

but that's just my opinion[/QUOTE]
 Unfortunately it's not very easy to do with Zenity.  Right now all output is redirected towards Zenity so the progress dialogs know when to auto-close.  I'll look into it though. :)  Maybe a flag or something to use terminal output instead of Zenity.

---

### Post by Nis on 2004-12-03
New feature!  Mozilla Firefox can be upgraded to 1.0 (see above). :)

---

### Post by oddabe19 on 2004-12-03
it works well.... i tried the original version.... Java didn't work/ install though.

---

### Post by Nis on 2004-12-05
[QUOTE=oddabe19]it works well.... i tried the original version.... Java didn't work/ install though.[/QUOTE]
 Could you give me some information about what happened during the Java install?  Did the xterm open up with the EULA from Sun?

---

### Post by Géry Debongnie on 2004-12-05
That's a great idea. Keep it up.  It's nice to be able to set up a new box, then running your script, and voila : flash, java, multimedia and anything I (or my relatives) use is installed!  

Good job.

---

### Post by oddabe19 on 2004-12-06
[QUOTE=Nis]Could you give me some information about what happened during the Java install?  Did the xterm open up with the EULA from Sun?[/QUOTE]
not that i recall, it didn't....

---

### Post by Nis on 2004-12-06
[QUOTE=oddabe19]not that i recall, it didn't....[/QUOTE]
 Hmm... If you could try running the script again for Java while running the below in another terminal.
```

watch ls -l /tmp/*.bin /tmp/*.deb

```
You should see the bin file size steadily increase as it is being downloaded by wget.  The you should see the deb appear after answering two questions in an xterm that is opened by the script.  If you're not even seeing the xterm then I suspect the download might be failing.  The Java part has worried me even though this has been the only failing I've heard so far.  Thanks for your help. :)

---

### Post by mattyh on 2004-12-06
Awesome script.  Something like this could be REALLY useful for new installs, and *maybe* even something that could be included on the desktop or something with a default install at some point in a future release.  Do you think you could add a section for disabling ipv6 or is that not necessary once you upgrade to firefox 1.0?  I'll try to think of some other things that might be able to be automated as well.  All in all, very nice job.  =D>  =D>  =D>

---

### Post by saBrEwolf on 2004-12-06
Wow! Nis, this is a brilliant script!

Perhaps I could draw on those skills to help me out with something.

I had an idea of creating a script where you select a bunch of audio files (be they mp3s or oggs or anything else) and the script uses mpg321 or other tool to convert them to wav. These wavs are then put in an iso to be burned by nautilus. But I have no idea on how I could go about doing this.

Could you help me with this as this is the basic idea of G3b (a GNOME alternative to K3b I've been planning)

Any help would be greatly appreciated

---

### Post by ubuntu_demon on 2004-12-06
Nis,

would you like to join :

easy GUI based custom ubuntu cd creation tool
[http://www.ubuntuforums.org/showthread.php?t=5981&page=1](http://www.ubuntuforums.org/showthread.php?t=5981&page=1)

We are talking about a tool to create custom ubuntu cd's. 

One of our options is that the tool creates a series of flags for a script like yours that is run after the standard installation.

---

### Post by WW on 2004-12-06
saBrEwolf: You should go to the #ubuntu  IRC chat room and look for "ogra".  Ask him about "MrBurns".

---

### Post by Nis on 2004-12-06
[QUOTE=WW]saBrEwolf: You should go to the #ubuntu  IRC chat room and look for "ogra".  Ask him about "MrBurns".[/QUOTE]
I haven't had much luck getting MrBurns to work.  It looks promising though.  IMHO, however, audio CD burning should be were it belongs: in Rhythmbox.  But until that day something simple would be really nice.  Maybe I'll give MrBurns another try and it will do more than just look simple (no burning when I clicked on Write CD).   :-k

---

### Post by Nis on 2004-12-08
Some updates to the script to make it update Firefox through the [Ubuntu Backports Project](http://ubuntu-bp.sourceforge.net/).  I did notice that Mplayer can no longer be downloaded through Marillat; some dependencies aren't resolving.  If anybody has any info on this or an alternate Mplayer and mplayerplug-in repository let me know.  Thanks!

---

### Post by Nis on 2004-12-08
Urgent!  If you have used the most recent version of waih to install Firefox from the Ubuntu Backports Project you must reinstall Java using an updated version of waih.  Apparently the UBP Firefox has problems with Java 1.4.2.  The latest version of waih installs Java 1.5.0 which UBP Firefox apparently has no problems with.

---

### Post by jdong on 2004-12-08
[QUOTE=Nis]Some updates to the script to make it update Firefox through the [Ubuntu Backports Project](http://ubuntu-bp.sourceforge.net/).[/QUOTE]

Cool, cool cool :) :) :)

Does it add the UBP repository into sources.list, too?

---

### Post by Nis on 2004-12-08
[QUOTE=jdong]Does it add the UBP repository into sources.list, too?[/QUOTE]
Yes it does. :)  However, the Firefox build is having major problems with Java.  Java 1.4.2 does not work (Firefox won't even start with the plugin symlinked) and Java 1.5.0 has problems as well (Firefox crashes loading a page using Java.  Something about not being able to load the Java VM).

---

### Post by Nis on 2004-12-09
Some changes:
- Many of the Zenity progress dialogs have been replaced by gnome-terminal dialogs showing apt-get progress.  I think new users won't mind and it looks similar to Synaptic output.  It also makes it easier to see if things went wrong. :)
- Java is not installed using the Blackdown package released 23/11/2004.  It just seems better this way.

Some issues:
- Mplayer is still not installable.  The marillat repository changed something and dependencies cannot be resolved.  Looking into other repositories.
- Firefox 1.0 from Ubuntu Backports still does not work with Java.  Not sure why so you might want to wait on upgrading to Firefox 1.0 or hold off installing Java.

---

### Post by jdong on 2004-12-09
[QUOTE=Nis]- Firefox 1.0 from Ubuntu Backports still does not work with Java.  Not sure why so you might want to wait on upgrading to Firefox 1.0 or hold off installing Java.[/QUOTE]

Sorry, I'm investigating the situation... FF1.0 backport works fine with other binary plugins, just not any of the Java plugins....

---

### Post by jdong on 2004-12-09
Ok, I fixed that bug. Turns out that the version string was too long.

---

### Post by oddabe19 on 2004-12-09
Failed to run ./waih as user root:
 Child terminated with 1 status


:-(

gotta run it as sudo...
not sh... then enter password.

very nice, how about a feature to get the headers to your kernel?

---

### Post by Nis on 2004-12-09
[QUOTE=jdong]Ok, I fixed that bug. Turns out that the version string was too long.[/QUOTE]
I can verify that Java and Firefox 1.0 UBP works. :)  Thanks jdong on the quick response.

[QUOTE=oddabe19]very nice, how about a feature to get the headers to your kernel?[/QUOTE]
I'll look into it.  Maybe when the latest kernel is installed.  Maybe a new feature to install build-essentials and kernel-headers.  This might happen if I can't find a repository to replace the marillat one for mplayer.

---

### Post by jdong on 2004-12-09
[QUOTE=Nis]I can verify that Java and Firefox 1.0 UBP works. :)  Thanks jdong on the quick response.[/QUOTE]

Most certainly. Thank you guys for bringing this to my attention. :)

---

