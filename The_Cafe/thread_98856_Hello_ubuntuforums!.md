---
title: "Hello ubuntuforums!"
date: 2005-12-04
forum: The Cafe
---

### Post by qiet72 on 2005-12-04
Just saying hello as a new member.

Installed ubuntu on two different laptops - worked pretty well out of the box.

The only issues to note:

If you have an ATI Mobility Radeon M6 LY card which is installed in laptops like the Dell c610 Latitude, then remember to switch the driver in xorg.conf from "ati" to "radeon" otherwise 3D accelleration will not work.  The 3D accelleration also requires quite a bit of video memory so you may have to switch your color depth from 24 bit to 16 bit in xorg.conf.  The solution took me 3 days to figure that out.  The solution is so simple that it seemed ridiculous.

Don't try the fglrx driver - very unstable and it will not work with the ATI Mobility Radeon M6 LY card!!!

Other issues:  I noticed a lot of people having problems with programs that use the OpenAL api for sound like Chromium.  This is because OpenAL uses /dev/dsp directly which conflicts with the Enlightenment Sound Daemon (esd) which also uses /dev/dsp.  The most elegant solution I have found is to create a file called ~/.openalrc and paste the following line into the file:

(define devices '(alsa esd native))

Save the file and it should work immediately without reboot or logout.
The line tells OpenAL to try and use alsa, then esd, then /dev/dsp for sound output.  Reference to this information is here: 

[http://ggo.sourceforge.net/manual/ar01s09.html](http://ggo.sourceforge.net/manual/ar01s09.html)

On to the rest of my hardware setup!  Still trying to get Infrared to work.  I will post if I find a solution.

2005-12-4 Update: Pingus doesn't seem to give sound.  The following makes the sound work but is not elegant:

As root type: echo "pingus 0 0 direct" >/proc/asound/card0/pcm0p/oss

If anybody else knows a more elegant way than this, post.

Quinn

---

### Post by bwog on 2005-12-04
Welcome.

You seem very capable of finding the solutions you need. The installation and upgrade section could use a visit now and then from somebody with your capabilities. It seems like many laptopusers turn away with disgust from that section when they finally solved their problems :) If you have no time for that kind of thing you are equally welcome ofcourse.

---

### Post by sapo on 2005-12-04
My only wish is that everybody that tries ubuntu try finding the solution for the problems as you did, instead of coming here complaining when they find the first problem.

Gratz, and welcome :D

---

### Post by bwog on 2005-12-05
@sapo: it would be nice if everybody was capable of that. Some installation problems are daunting for beginners. It would already help to show them how to search for solutions. Friendly suggestions of what the new user can try, helps them to persevere. Anyway, I do not see many angry or whining questions.

---

### Post by sapo on 2005-12-05
You didnt understand exactly what i mean.. 

They dont even try to solve their problems, they come here to say:

"my XYZ card didnt work out of the box, this ubuntu stuff sux help me or die!"

I just hate this kind of people, who dont want to find a solution, they just think that ubuntu MUST work with they stupid hardware, so if it doesnt work, its all ubuntu fault, not theirs or the hardware manufacturer that didnt make linux drivers.

---

### Post by bwog on 2005-12-05
I know what you mean. I also can imagine how it works: they have been trying to install again and again, and perhaps tried some different options. Then they post as a last resort, without mentioning what they did or what their hardware is, just because they are tired (or even angry). I am not saying this is the right thing to do, but it is  eh... human :)

Nobody is obliged to answer such posts, but when you give some suggestions, they may persevere with the installation.

---

