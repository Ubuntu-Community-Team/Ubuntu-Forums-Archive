---
title: "Configuring wine in POL 3.5"
date: 2009-05-27
forum: Wine
---

### Post by b@sh_n3rd on 2009-05-27
Hi, I'm using Jaunty Jackelope on my PC for the past couple of weeks. When I installed Jaunty, I partitioned my [COLOR="YellowGreen"]20GB HDD[/COLOR] as follows; [COLOR="SeaGreen"]100MiB /boot, 386MiB /swap, 6144MiB /home and 12416.4MiB /root[/COLOR]. At the time, I was unaware that if ever I use wine, all my programs would go in [COLOR="Green"]/home[/COLOR], and the main reason I made [COLOR="Green"]/home[/COLOR] so small was with the knowledge that I wouldn't have much files in it, except for Music, Videos and a few Downloads which take about 50-70% of my [COLOR="Green"]/home[/COLOR] directory's usage.

Currently, I'm testing a few games with POL on my PC. I install apps through POL using a prefix for each application and [COLOR="Navy"]drive C:[/COLOR] is located in my home folder as always [COLOR="DarkOrange"][eg: ~/.PlayOnLinux/wineprefix/*/dosdevices/c:][/COLOR]. I've created a separate directory, with user priviledges, on my [COLOR="Red"]/root[/COLOR] partition as the amount of space on my [COLOR="Green"]/home[/COLOR] dir is quite inadequate for several games which span at least a minimum of [COLOR="SeaGreen"]700MiB[/COLOR]. This I would like to configure as drive "D:" on wine so that I can use the free space on this partition (which is just a couple of GB's more than that of [COLOR="Green"]/home[/COLOR]). I *was* able to do this on wine directly, by selecting, "Configure Wine" under "Wine" in the "Applications" menu. However, I was still unable to do this on POL, since the individual configuration settings in Wine don't effect POL. When I try it on a certain prefix, it never stays that way and reports that drive "D:" does not exist when trying to install a program onto D: :(. Any help on this? I tried searching around without any success so far... My D: drive would be in, "[COLOR="DarkOrange"]./pol/dosdevices/d:[/COLOR]".

---

### Post by b@sh_n3rd on 2009-05-27
I noticed a few shortcuts to drives like "c:" and "d:" (/media/cdrom0) in ~/.PlayOnLinux/wineprefix/*/dosdevices. These shortcuts refer to their dedicated directories/mountpoints in Jaunty. Would it be possible to create a shortcut like this manually to direct wine to the folder I want?
Thanks...

---

