---
title: "How can i get ALSA to show up as I/O in the JACK Audio tab in the jack menu?"
date: 2014-07-29
forum: Ubuntu Studio
---

### Post by davstar on 2014-07-29
I've got all my equipment working somewhat satisfactory now but the last thing that i'm having trouble figuring out now is getting ALSA to show up in the Audio tab on jack .

heres how i got all my stuff configured

[IMG]

[IMG][[IMG]http://i1212.photobucket.com/albums/cc444/aktoninstinkt808/Screenshotfrom2014-07-25224517_zps8f1007d6.png[/IMG]]("http://s1212.photobucket.com/user/aktoninstinkt808/media/Screenshotfrom2014-07-25224517_zps8f1007d6.png.html")[/IMG]

i need ALSA to show up in this menu above to route sound from the internet and other sources ... i think

[IMG][[IMG]http://i1212.photobucket.com/albums/cc444/aktoninstinkt808/Screenshotfrom2014-07-25223452_zps4a031ab5.png[/IMG]]("http://s1212.photobucket.com/user/aktoninstinkt808/media/Screenshotfrom2014-07-25223452_zps4a031ab5.png.html")[/IMG]

---

### Post by jejeman on 2014-07-30
No, "ALSA" is already shown in AUDIO tab. That is your soundcard. (system)
What you want is to use JACK aware applications, in order to show up in AUDIO tab.
Or, if you can't use JACK aware applications, then ether patch through pulseaudio or set up ALSA environment to patch through non JACK aware applications. Both were discussed on this forum.

---

### Post by davstar on 2014-07-30
Thanks jejeman how would i route sound through JACK  from say from youtube? so i can record it ?

---

### Post by jejeman on 2014-07-31
When I said it was already discussed on this forum it means that you do the search. Respect our time.
One solution is here
[http://ubuntuforums.org/showthread.php?t=2157213&p=12705207#post12705207](http://ubuntuforums.org/showthread.php?t=2157213&p=12705207#post12705207)

Also, I've noticed that only 2 inputs are recognized, and as I recall, that USB card has four inputs.

---

