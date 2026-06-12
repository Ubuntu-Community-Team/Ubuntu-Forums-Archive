---
title: "Mute button disabled by default in Lucid Ardour"
date: 2010-05-17
forum: Ubuntu Studio
---

### Post by fritzm on 2010-05-17
I struggled (unsuccessfully)to get the mute button to work in Ardour on my new UbuntuStudio 10.4 installation. Since it's the first time that I'm using Ardour, I eventually decided that I must be doing something wrong and gave up. Shortly afterwards this bug report was filed on ubuntustudio-testers by Angus Kerr, which cheered me up - it's not just my ignorance, and there is a solution. I'm posting it here in case anyone else runs into the same problem.
..........................................................

I tried in vain to work out why the 'mute' button does not work in Ardour 2.8.6 packaged with Ubuntu Studio Lucid AM64. Help was
forthcoming from the Ardour forum:

It seems that mute has been disabled intentionally during, or after the installation of Ardour in Ubuntu Studio when the package was created.

The file 'ardour.rc' in .ardour2 directory in the home folder of the user, contains the following entries:

Option name="mute-affects-pre-fader" value="0"/>
Option name="mute-affects-post-fader" value="0"/>
Option name="mute-affects-control-outs" value="0"/>
Option name="mute-affects-main-outs" value="0"/>

The options should be set to 1, like this:

Option name="mute-affects-pre-fader" value="1"/>
Option name="mute-affects-post-fader" value="1"/>
Option name="mute-affects-control-outs" value="1"/>
Option name="mute-affects-main-outs" value="1"/>

..................................................

My thanks to Angus,

Fritz

---

### Post by GiveLove on 2010-05-20
Hello fritzm, :)

I ran into this exact same issue but using plain Ubuntu 9.10 and Ardour 2.8.2 from the repositories. 

Your posted fix did not work for me. Thankfully it turned out to be user error on my part. It seems Ardour changed how the mute button works since I last used it in Ubuntu 9.04. 

Here's the thread that helped me:
[http://ubuntuforums.org/showthread.php?t=1296863](http://ubuntuforums.org/showthread.php?t=1296863)

GiveLove

---

### Post by Scott L on 2010-05-30
Thanks to all the users who filed the bug and provided solutions to this problem.

Upstream (Paul Davis) has recognized the problem and I believe he is/has fixed the problem in Ardour 3.  Since I'm still using Ardour 2.8.6 I can not tell for sure.

A patch (120_mute.patch) has been applied to the package ardour-2.8.7 in both Debian and Ubuntu so this should prevent this occurrence going forward in the ardour-2.8.x series, which shouldn't be too much further I hope :) due to Ardour 3.

Therefore, ardour-2.8.7 is uploaded to Maverick so fresh installs of Ubuntu Studio starting with Maverick should not see this problem.  However, this does not include upgrading from an older version of Ubuntu Studio.

I believe this problem has been around for much of the 2.8.x series but really hasn't been as rampant because long time users were upgrading their system (probably from the ardour-2.7.2 era) which should not touch their home directories, which is where the ardour.rc file is located.  Therefore, it you upgrade your version of Ubuntu Studio to the next you will need to moderate your ~/.ardour2/ardour.rc as noted above.

So, to summarize:
Brand new installs of Ubuntu Studio staring with Maverick should not suffer this problem, not including upgrades.  If you upgrade your distro you will need to moderate ~/.ardour2/ardour.rc.

Right click the mute button and selecting the mute options enables mute FOR THAT TRACK ONLY.  Any new tracks in the same project will still suffer from disabled mute buttons.

Fixing the ~/.ardour2/ardour.rc file will not only enable the mute button for all new projects but will also enable the mute buttons for new tracks within existing projects.

Once again, many thanks to those involved to this point.  Without your efforts this bug would not have been addressed and users would continue to suffer.

ScottL

---

