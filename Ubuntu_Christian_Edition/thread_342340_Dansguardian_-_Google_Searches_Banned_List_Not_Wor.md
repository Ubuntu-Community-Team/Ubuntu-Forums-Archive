---
title: "Dansguardian - Google Searches Banned List Not Working"
date: 2007-01-19
forum: Ubuntu Christian Edition
---

### Post by Ennead on 2007-01-19
I'm running Ubuntu 6.06, and it is working well.  I installed Dansguardian, and except for losing my LAN communication, it seems to be working fine.  I first tried to install DG from the command line, which didn't work, so I installed it using Synaptic. 

To figure out how to configure DG, I've been putting inocuous words (brick, tree, mountain) into the banned and weighted lists, and I'm beginning to see how things work.

One item that particularly stumps me is the /phraselists/googlesearches/banned list.  I put it into the bannedphraselist file using the GUI, but it doesn't do a blessed thing.  I can add words to be banned, and they do get banned, so I know it's reading the file, but none of the existing content that purports to restrict searches works at all.  Also, the /phraselists/pornography/banned file appears to disallow all image searches with safesearch off, but it doesn't work either.  As mentioned earlier, I can insert words to be banned in this file and get them to work.  The existing content seems useless.

How does one get this filter to work?  Does it sound like I've messed something up?

---

### Post by mhancoc7 on 2007-01-19
Did you install dansguardian using one of the scripts on the Ubuntu CE page?

Jereme

---

### Post by Ennead on 2007-01-20
Yes, I used the "Web Content Filtering Only" script.  When I ran the script, it seemed to run just fine, but I didn't have the GUI for configuring DG under Admin.  So, I downloaded and ran the script again.  I didn't uninstall DG before reloading, thinking it hadn't worked and there was nothing to uninstall.  Same results.  So then I went to Synaptic, added all the repositories, and installed DG from there.  At that point, I had the GUI and I started trying to figure out the configuration.  And that's when things started getting interesting ...

---

### Post by mhancoc7 on 2007-01-20
Are you using the GUI to edit the config files? The GUI will reconfigure dansguardian when you click "Save & Exit". So things should be working. If you are still having trouble I would suggest running the script again just to be sure that all the components are installed properly.

Jereme

---

### Post by Ennead on 2007-01-22
Thanks!  Rerunning the script did the trick.  I'm a bit confused as to why it didn't work the other times I did that, and I'm a little embarrassed that I had to bother you about something so elementary, but it's working now, and I thank you very much!!!

Joe

---

### Post by mhancoc7 on 2007-01-22
No problem! Great to hear you got it working.

Sometimes if the internet connection times out it will not get everything installed. Running the script again normally fixes it.

Jereme

---

