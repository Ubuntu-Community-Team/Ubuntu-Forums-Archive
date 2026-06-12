---
title: "Tascam US-2000"
date: 2013-07-02
forum: Ubuntu Studio
---

### Post by MrBalloonHands on 2013-07-02
My band and I are trying to use the Tascam US-2000 to do some recording. When I Started up Jacks it only detected Capture 1 and Capture 2. Is this normal? I can't imagine it would be considering it can record up to 16 tracks at the same time. Am I missing something? Is there a driver? I'm new to all this so any help would greatly be appreciated. Thanks ahead of time.

---

### Post by cub on 2013-07-03
Could you provide a screen shot?

---

### Post by su:bhatta on 2013-07-03
[ATTACH=CONFIG]244350[/ATTACH][ATTACH=CONFIG]244351[/ATTACH]
This is how it looks like I suppose... After tweaking with LinuxBand the same has happened to me... n there r no system sounds that r being played.

Also, I had configured Jack Port to be the fallback from my sound settings earlier, but now under Output Devices, JackPort is not being shown anymore....

Both screenshots attached..

But the thing is, I can connect LinuxBand and Qsynth to play midi. Only when I play songs from the Music folder then am not getting any sound and no sysytem sound too...

---

### Post by cub on 2013-07-03
I was more thinking of the Settings in Qjackctl.
[ATTACH=CONFIG]244353[/ATTACH]

---

### Post by su:bhatta on 2013-07-03
Really sorry, i misunderstood... am attaching again...
But this is how mine looks like... i hav no intention of hijacking the thread...:D

[ATTACH=CONFIG]244356[/ATTACH][ATTACH=CONFIG]244357[/ATTACH]

Also, i might add here that, once i am stopping jack, n selecting from 'playback' under soundsettings the 'generic analog device' i am getting sounds back on VLC, Youtube and all... but with Jack on there is no playback from these devices...

As i said before, Under SoundSettings, there is no Jack Port... but earlier I had selected JackPort to be the fallback... Giving u a shot of error  msg from Jack If i am playing Audacious n starting Jack after that... if that helps...[ATTACH=CONFIG]244361[/ATTACH]

---

### Post by su:bhatta on 2013-07-03
MrBalloonHands, Try this.. it works... did work for me :)

run the following command on terminal after starting jack:
     

     
```
pactl load-module module-jack-sink channels=2; pactl load-module module-jack-source channels=2;pacmd set-default-sink jack_out 
```

i found it here [http://trac.jackaudio.org/wiki/WalkT...er/PulseOnJack]("http://trac.jackaudio.org/wiki/WalkThrough/User/PulseOnJack") (bottom of the page)

PS: This post describes how to make the changes permanent so as not to run the command on terminal every time u start Jack...
[http://http://ubuntuforums.org/showthread.php?t=843012](http://http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by cub on 2013-07-03
> **bhattabhishek said:**
> MrBalloonHands, Try this.. it works... did work for me :)

run the following command on terminal after starting jack:
     

     
```
pactl load-module module-jack-sink channels=2; pactl load-module module-jack-source channels=2;pacmd set-default-sink jack_out 
```

i found it here [http://trac.jackaudio.org/wiki/WalkT...er/PulseOnJack]("http://trac.jackaudio.org/wiki/WalkThrough/User/PulseOnJack") (bottom of the page)

PS: This post describes how to make the changes permanent so as not to run the command on terminal every time u start Jack...
[http://http://ubuntuforums.org/showthread.php?t=843012](http://http://ubuntuforums.org/showthread.php?t=843012)
I'm not sure running PulseAudio is the solution here, or even recommended. To record 16 channels I would stay away from PulseAudio and run ALSA.

As the page says:
> Running PulseAudio on top of JACK

If you intend to use consumer applications like Flash or media players in your JACK setup, one possible solution is to use PulseAudio as an intermediate layer for all these non-JACKified programs. Basically, it boils down to the following:

1. Redirect all ALSA output to PulseAudio
2. Redirect PulseAudio to JACK

Which to my understanding is not what MrBalloonHands was asking about.

---

### Post by su:bhatta on 2013-07-03
Ok.. this is then new territory for me...

Forgive my idiocy... &

MrBalloonHands.. Please neglect my posts....

Cub: How do I delete my posts from this thread before it causes MrBalloonHands any harm.. cant find a 'delete post'

---

### Post by cub on 2013-07-03
> **bhattabhishek said:**
> Ok.. this is then new territory for me...

Forgive my idiocy... &

MrBalloonHands.. Please neglect my posts....

Cub: How do I delete my posts from this thread before it causes MrBalloonHands any harm.. cant find a 'delete post'
I don't think you can delete posts. But no worries, let's wait for MrBalloonHands reply to receive more information on the issue. You never know which post might be useful.

---

### Post by Iowan on 2013-07-03
> **bhattabhishek said:**
> 
Cub: How do I delete my posts from this thread before it causes MrBalloonHands any harm.. cant find a 'delete post'Lower left corner of each post has a "Report Post" button that can be used to request staff action - move, remove, edit, etc.

---

### Post by su:bhatta on 2013-07-04
Iowan, Thank you for letting that come to light.. I never tried Report Post in fear if that link directly reports a post and creates a spot of trouble...

As of now , i will take Cub's  path and leave the posts to see if any comes in handy for MrrBalloonHands...

---

