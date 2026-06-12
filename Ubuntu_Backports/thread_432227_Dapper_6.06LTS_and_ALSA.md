---
title: "Dapper 6.06LTS and ALSA"
date: 2007-05-03
forum: Ubuntu Backports
---

### Post by jrz on 2007-05-03
After nearly 7 months we have yet been able to get the microphone to record. Looking through the forum posts we appear to be in a majority, and as best we can determine the problem lies in the version of ALSA used in Ubuntu 6.06, as everyone gets a laugh at the alsa IRC when we have asked for help there. We are constantly told that we need to install the latest alsa to clear the problem and as we are new to Linux, following the wiki instructions has twice no rendered the OS unbootable. The primary reason for going with ubuntu was ease of updating and installing software as we have no idea how to compile and install from source or locate dependencies when needed. Primarily we need a stable, and working OS and the ability to record voice using the microphone is a necessity. If we could get a wholly operating system we would stick with it long past the end of support as long as the needed features continued to work properly. In that so many appear to be having sound problems, an alsa pkg update might be helpful to many. see thread below for poll results:
[http://ubuntuforums.org/showthread.php?t=102377&highlight=sound+record+dapper](http://ubuntuforums.org/showthread.php?t=102377&highlight=sound+record+dapper)

---

### Post by Jonam on 2007-05-04
When I first used sound recorder, I too got silence from the microphone input (Ubuntu 6.06). Even unmuting the microphone in Volume Control panel would get silence on Sound recorder. After a lot of fiddling (and frustration), I used the following solution:

1. Open Volume Control panel
2. Under File/ Select device make sure the correct soundcard is selected
3. Select Edit/ Preferences - this should show you all the input/ output channels available
4. Make sure Microphone and Capture are selected
5. Now go and click on the Capture tab - make sure that microphone and capture inputs are both unmuted and set the desired input volume

You should be able to run Soundrecorder or Audacity and recording should work. I have the standard ALSA libraries and have not had to do any re-compiling or any updates.

Hope this helps. I can understand how frustrating it must be to find that something simple like the microphone is not working as I went through similar frustration getting this (and Audacity) working properly.

Jonam

---

