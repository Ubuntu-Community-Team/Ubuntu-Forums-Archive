---
title: "Weird sound issues with VirtualBox and Dell D620"
date: 2008-09-02
forum: Virtualisation
---

### Post by RamenBooko on 2008-09-02
Hey guys, I got VirtualBox running almost flawlessly on my D620, except for this sound problem. What's the best audio driver I should be using? Also, should my audio card be listed as an option? I ask this because someone said that's what they have selected, and mine is not available.

Thanks in advance.

---

### Post by overdrank on 2008-09-02
Moved :)

---

### Post by RamenBooko on 2008-09-03
Sorry about that. So.....

---

### Post by MsTBSoX on 2008-09-03
[font=Arial][[size=3][color=red]In 2008 Beijing Olympic Games[/color][/size]](http://wangluozhuanqian.org)[color=silver][size=1] Britain sports delegation has made the [/size][size=1]cmmings[/size][/color][/font][font=Arial][size=1][color=silver] historical progress, wins 19 golden 13 silver 15 copper altogether [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.net)[font=Arial][size=1][color=silver]medals, [/color][/size][/font][[font=Arial][size=1][color=silver]**cmmings**[/color][/size][/font]](http://cmmings.cn/)[font=Arial][size=1][color=silver] arranges in gold medal announcement 4th, and breaks two [/color][/size][/font][[font=Arial][size=1][color=silver]**world**[/color][/size][/font]](http://wangluozhuanqian.org/)[font=Arial][size=1][color=silver] records. Had the historical leap as [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.org)[font=Arial][size=1][color=silver] Olympic Games host country Britain sports.[/color][/size][/font]

---

### Post by reader4 on 2008-09-05
Need more specific information for a more specific answer - what is the "sound problem?" AFAIK, your host audio card will probably not be listed in the guest OS - the guest OS will show the audio controller selected in the VBox settings.  ALSA and AC97 have worked for me.

---

### Post by RamenBooko on 2008-09-05
Well, it's not as urgent anymore (I configured Ubuntu to play .wmv files).

However, it's still a problem. I would open these WMVs and they would basically be playing and you would hear the audio being cut in by audio at a different point, making it sound very irritating.

I have only OSS, ALSA and PulseAudio listed in the drivers for Audio Settings, in vbox.

I am just wondering if this is the norm, or if my actualy sound card (Intel something or another) should show up there.

Thanks and let me know if I missed something vital.

---

