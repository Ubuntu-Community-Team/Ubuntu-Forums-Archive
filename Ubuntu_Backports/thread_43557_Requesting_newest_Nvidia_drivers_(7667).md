---
title: "Requesting newest Nvidia drivers (7667)"
date: 2005-06-22
forum: Ubuntu Backports
---

### Post by meldroc on 2005-06-22
Could we get a port of the freshest and mintiest Nvidia drivers.  7667 has quite a few new features, such as OpenGL 2.0 (mmmm, pixel shaders), as well as many bug fixes.

---

### Post by Lunde on 2005-06-22
[QUOTE=meldroc]Could we get a port of the freshest and mintiest Nvidia drivers.  7667 has quite a few new features, such as OpenGL 2.0 (mmmm, pixel shaders), as well as many bug fixes.[/QUOTE]

It has also many bugs. It crashed my system and I had to roll back the driver. There are also a lot of others who have problems. Have you checked your framerate with the glxgears after about 5min after boot, a lot of people have drasticly dropped framerates.

I wish this driver worked for me, it worked excellent for about 2min.. but when I did a reboot, I couldnt start X

---

### Post by kleeman on 2005-06-22
Yeah not only that but the 7664 driver caused a whole bunch of kernel errors on my standard hoary system and then (shudder) file corruption. I did not enjoy the reinstall much .... As I recall it the devs checked this driver out on this forum quite carefully before the hoary release. From my experience this sounds very sensible.....

---

### Post by jdong on 2005-06-22
Someone already asked about a week or so back. Kernel driver backports are some of the HARDEST to maintain and do, because they get so deep inside the system.

From my initial tests, unless you need the OpenGL2 features, there's no difference between the Hoary release and this one...

---

### Post by FLeiXiuS on 2005-06-22
I agree, the 7667 aren't quite ready.  I heard they're patching it this coming week or so. 

Something to look forward too!

---

### Post by TheRealEdwin on 2005-06-22
Battlefield 2 requires the latest Nvidia drivers. ;(

---

### Post by jdong on 2005-06-22
For those who really want 7667... compile it yourself. If you want to use bleeding-edge software, you need to know how to deal with it when it breaks.... And how the heck do you think you can fix it if you can't even install a working copy to begin with? ;)


Install linux-headers and blast off :)

---

### Post by Kyral on 2005-06-22
BF2 supports Linux?! Please tell me you are serious!

---

### Post by McQuaid on 2005-06-22
Can hoary actually update nvidia binaries safely?

On a fresh install I grabbed the headers and tried to install any nvidia binary and I could not get X to boot at all.  I tried removing the hoary deb packages first of course, but just could not get any nvidia binary to install.  I've never had this problem before with other distros, usually as long as you have the headers your good to go.  I've since compiled my own kernel and have installed any version of the nvidia binaries without issue.  I have not however grabbed the latest as I didn't have any real motivation to go to the latest with my card gf4ti 4200 as it does not suport opengl 2.0.  

Just curious if other people have been able to install other nvidia versions with the stock hoary kernel and it's headers.  I certainly couldn't.

---

### Post by jdong on 2005-06-22
[QUOTE=McQuaid]Can hoary actually update nvidia binaries safely?

On a fresh install I grabbed the headers and tried to install any nvidia binary and I could not get X to boot at all.  I tried removing the hoary deb packages first of course, but just could not get any nvidia binary to install.  I've never had this problem before with other distros, usually as long as you have the headers your good to go.  I've since compiled my own kernel and have installed any version of the nvidia binaries without issue.  I have not however grabbed the latest as I didn't have any real motivation to go to the latest with my card gf4ti 4200 as it does not suport opengl 2.0.  

Just curious if other people have been able to install other nvidia versions with the stock hoary kernel and it's headers.  I certainly couldn't.[/QUOTE]

You must remove the nvidia-glx package. After that, it works as advertised for me :)

---

### Post by McQuaid on 2005-06-22
Hmm, maybe I missed the nvidia-glx package but I can't recall now.  I could go through synaptic history to see what I removed but no big deal.  I'd rather hear it was me than an issue with hoary's headers or something.

---

### Post by TheRealEdwin on 2005-06-22
[QUOTE=Kyral]BF2 supports Linux?! Please tell me you are serious![/QUOTE]
 Not natively, but Cedega should soon.

---

### Post by Stephen-I-M on 2005-06-26
One issue is that the version prior to 7667 had issues with flatpanels at 1600x1200. I'm running now with 7667 and the monitor works.

Should changing the version line to:

   VERSION="1.0.7667"

be enough to get the script in /etc/init.d/nvidia-glx to work?

Stephen

---

### Post by skoal on 2005-06-27
766**[size=4]7[/size]**? Sweet...I'm still on 7664.  I'm still contemplating whether or not to go ahead and make the upgrade.  Just 3 points though for a revision? What did they do? Finally run a spell checker on their README?

\\//_

---

### Post by tristan on 2005-06-27
[QUOTE=skoal]766**[size=4]7[/size]**? Sweet...I'm still on 7664.  I'm still contemplating whether or not to go ahead and make the upgrade.  Just 3 points though for a revision? What did they do? Finally run a spell checker on their README?
\\//_[/QUOTE]

LOL! I think the main thing is support for the new 7000 series cards. I installed 7667 and noticed nothing revolutionary (a 200% speedup for instance).

---

### Post by skoal on 2005-06-27
You know what, I seriously thought all you guys were pulling a joke on the rest of us.  I kept seeing the 7667 and couldn't quit figure out why everyone seemed to be repeating that version, when I only could see 7664 as the latest on Nvidia's website.

* Apparently, how you check for the latest Nvidia driver on their website is important (and will give you 2 different results):

Go to Nvidia's website, click "download drivers".  Now, you're faced with 2 different paths here...

1. use the form box and click "graphics drivers" > "GeForce and TNT2" > "LinuxIA32".  Hmmm...what version do you see as the latest? 766[SIZE=4]4[/SIZE]

-or-

2. click the "Linux, FreeBSD, and Solaris Drivers" link just above the form box.  Hmmm....now what version do you see? 766[SIZE=4]7[/SIZE]

What's the dealio?? Has it alwyas been that inconsistent?

To all you nvidia web developers, you're lucky I'm not Donald Trump.  Otherwise, "you're fired!"

\\//_

---

### Post by kassetra on 2005-06-27
[QUOTE=tristan]LOL! I think the main thing is support for the new 7000 series cards. I installed 7667 and noticed nothing revolutionary (a 200% speedup for instance).[/QUOTE]

Correct. I have the 7800, and not a single driver works with it except the 7667. If you have the 7800 or better, this is the driver you have to use.  Other than that, almost no need to upgrade.

---

### Post by Jet2k5 on 2005-07-11
[QUOTE=kassetra]Correct. I have the 7800, and not a single driver works with it except the 7667. If you have the 7800 or better, this is the driver you have to use.  Other than that, almost no need to upgrade.[/QUOTE]

That's not good to hear.  I'm going to be getting that card in about a months time, and probably installing Hoary since Breezer won't be out by then.  Will I be able to install the system?  Or will it not work.  Seems like the drivers don't work if you are trying to get the 3d working.  I just want to be able to install the system get the basics running and then downlod the 7667 to get 3d working.

BTW those of you that want to play BF2 , you have to wait for 1.4 pixel shaders from Cedega.  They are working hard on it, but It's going to take a while.  Also like they said, you need the newest nvidia drivers.  

Note:  Ubuntu is a stable distro.  Not per-say the most bleeding edge.  But those that stay on the Bleeding-Edge also deal with non working systems :).  So either " Go big, or go home "  Want the latest use Mandriva, which actually i think uses the latests.  But they are snappy on those things.

Anyhow tell me how this is going to work when I install Ubuntu.

---

### Post by senectus on 2005-08-06
I need the latest drivers for smoother play of guildwars under cedega :-(
Anyone know of a "safe howto" for manual driver install?

---

### Post by oneybm on 2005-08-15
I was wondering the same thing as I too want the driver for play with GuildWars.  I've looked for awhile and have seen no how to.  I've also tried what was suggested in the FAQ and the forums with no luck.  Oh well, I still have *sigh* my XP partition for games.

---

### Post by senectus on 2005-08-15
[QUOTE=oneybm]I was wondering the same thing as I too want the driver for play with GuildWars.  I've looked for awhile and have seen no how to.  I've also tried what was suggested in the FAQ and the forums with no luck.  Oh well, I still have *sigh* my XP partition for games.[/QUOTE]

It's worth doing the upgrade manually.. It made GuildWars stable and slick.. and I now have a pretty good character :-)

---

