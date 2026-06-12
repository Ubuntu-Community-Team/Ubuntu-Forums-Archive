---
title: "Display Overscan on 64-bit with nVidia"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ewangr on 2012-04-12
Went ahead and installed on my second machine downstairs which is attached to a 42 inch Samsung LCD TV via HDMI. Everything is running well except that there is an "overscan" issue that has half of the Left-hand panel with the icons cut off, and the entire top menu isn't showing.

On Windows the nVidia control panel has an option to correct for this. Is there anything similar for Ubuntu?

---

### Post by papibe on 2012-04-12
Hi ewangr.

Yes, there is an option, but I would start trying to solve the problem on the TV side:

Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV (sometimes the option is not easy to see). Check your manual or research about it on the Internet.

If none of that works, 'Nvidia X Server Settings' has an option to correct overscan manually. Check [this]("http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/") tutorial on how to do it.

I hope that helps, and tell us how it goes.
Regards.

EDIT: it seems the tutorial link is dead. The option in 'Nvidia X Server Settings' is:
```
Click on 'DFP-1 (Samsumg)' (or similar) under GPU-0 in the left menu.
In the right side there's an option called: 'Overscan Compensation'
```

---

### Post by cariboo on 2012-04-12
I've got an older (4 years) Samsung 32" LCD TV, in the picture settings menu on the TV, I've found that the ***Just Scan*** setting works the best with both a VGA and HDMI connection.

---

### Post by ewangr on 2012-04-13
Appreciate the suggestions. Yes, the TV has a menu option I can set that makes it work perfectly. The problem is that any time I turn it off, it resets. Not sure why it won't save the picture setting in between, but since this is a family TV my pointing out that it is a small sacrifice to be able to watch smooth 1080 isn't going over so well.

I will try the nvidia change suggested above when I get home tonight.

Thanks!

---

### Post by ewangr on 2012-04-14
Made the change in the nVidia panel as suggested, and it has worked fine so far. I want to see how it affects some of my video programs (am a little concerned this might be requiring some extra work by the GPU), but at least I can see everything now!

---

### Post by ewangr on 2012-04-15
As expected (unfortunately), turning on this option fixes the UI, but impacts GPU performance. 720p video is still smooth, but 1080 is now jerky at best. Since the GPU has to do the resizing as well as the frame by frame decoding I'm not too surprised but this. It does help make sure that the subtitles don't get clipped on the sides, so there is that advantage as well.

I don't suppose there is a settings toggle panel or app that I could put on the desktop that would let me turn that on and off?

---

### Post by papibe on 2012-04-15
Take a look at the tips on post #4 of this [thread]("http://ubuntuforums.org/showthread.php?t=1683875&highlight=nvidia+tearing"), to see if they help you with the jerkiness.

Regards.

---

