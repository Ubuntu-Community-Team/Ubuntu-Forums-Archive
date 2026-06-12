---
title: "QjackCtl works after I open Audacity"
date: 2012-09-03
forum: Ubuntu Studio
---

### Post by Rulius on 2012-09-03
Hi,

I have pluged my guitar in the mic jack of my laptop and trying to simply produce sound.

I start QjackCtl, make the connection (just system to system), but I have no sound. Then I open Audacity, close it (or even leave it open), start QjackCtl, make the same connection and now I have sound.  ](*,)

I have rebooted and tried it several times and nothing changes: I need to first run Audacity in order for QjackCtl to produce sound. 

Can anyone explain this and give my some advise so that I don't have to run Audacity before using the QjackCtl?

Thanks

---

### Post by sgx on 2012-09-04
Hi, audacity and qjackctl have their own preferences settings,
and it is odd to behave that way. On qjackctl Setup page on the right side

Input Device >
Output Device >

click the  > to see a dropdown list of your sound devices.
Compare what is there, to what is shown for options in audacity device preferences.

arecord -l  and  aplay -l

should show your soundcard i/o in brackets. The  > list
should have an entry similar to what is in rackets, or type it in yourself, instead of 'default' or hw:xyz etc
omitting the brackets. Restart qjackctl for change to take effect.

Cheers

---

### Post by Rulius on 2012-09-06
Thanks for the reply!

The input output device is set correctly in Qjackctl - both hw:0 HDA intel - (its the same arecord and aplay give). Besides, I tried all the possible combinations and it doesn't work. Only when I open audacity do I have sound from qjackctl.

It doesn't make sense to me either, but that is what is happening.
The settings in Qjackctl are the same before and after I open audacity - at least the ones shown in setup.

The devices in audacity were set to default for playback and default: mic:0 for capture.
I also noticed in Audacity was more specific giving me 3 options for recording that were relevant with my card:

HDA Intel:ALC861 Analog (hw:0,0): Mic:0
HDA Intel:ALC861 Analog (hw:0,0): Line:0
HDA Intel:ALC861 Analog (hw:0,0): CD:0

from which only Mic:0 worked.

Then I changed the input device in Qjackctl to either "HDA Intel:ALC861 Analog (hw:0,0): Mic:0" or "hw:0,0 Mic:0" or  "hw:0,0:Mic:0" or "(hw:0,0) Mic:0" but it didn't accept them (wouldn't start or gave an error).

Anyway, for the time being I'll settle with opening audacity and I'll keep looking.

:guitar:

---

### Post by sgx on 2012-09-07
If you can, the Fender Mustang1 usb modeling amp $110 list,
is a great guitar interface for linux, and has great sound,
and a full linux editor is available. The usb input shows
up and works fine in qjackctl. Quite a few used Mustang1 out there,
as people often upgrade to the larger models. 24 sounds you can
edit and create, and select from the main dial. I am astonished at
the quality of the 12 modeled Fender amps, and also the nice fx,
embellished by linux fx, as desired.

[http://www.youtube.com/watch?v=Wl2Q8SNVnPU](http://www.youtube.com/watch?v=Wl2Q8SNVnPU)

[http://www.linuxjournal.com/content/plug-and-fender-mustang](http://www.linuxjournal.com/content/plug-and-fender-mustang)

[http://piorekf.org/plug/](http://piorekf.org/plug/)

Cheers

---

### Post by lupopa on 2013-02-04
it's a HOT Tip from User sgx :)

I'll use it too ...

---

