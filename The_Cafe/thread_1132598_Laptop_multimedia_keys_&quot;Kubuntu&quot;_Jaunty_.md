---
title: "Laptop multimedia keys &quot;Kubuntu&quot; Jaunty (9.04)"
date: 2009-04-22
forum: The Cafe
---

### Post by kpkeerthi on 2009-04-22
Can someone running Kubuntu Jaunty pls. confirm if your laptop multimedia keys work? 

I have KDE4.2 running on Arch. I have all but one multimedia key not working. When I press the 'Mute" button, the OSD simply shows up displaying the current volume level but it won't mute the channel (I have master selected as the main channel in Kmix). Does it work in Jaunty (Kubuntu)?

I can test with a live CD but I'm on a limited bandwidth.

---

### Post by kpkeerthi on 2009-04-23
bump

---

### Post by jaimedavila on 2009-04-24
On my IBM/Lenovo Thinkpad X40, the keys do control the volume, but I am not getting any visual feedback of the fact that they have been pressed on the screen, or on the kmix tray icon.

---

### Post by der_joachim on 2009-04-25
No laptop multimedia keys whatsoever. It could be Amarok 2 though...

---

### Post by snova on 2009-04-25
> **kpkeerthi said:**
> Can someone running Kubuntu Jaunty pls. confirm if your laptop multimedia keys work?

They do.

> I have KDE4.2 running on Arch. I have all but one multimedia key not working. When I press the 'Mute" button, the OSD simply shows up displaying the current volume level but it won't mute the channel (I have master selected as the main channel in Kmix). Does it work in Jaunty (Kubuntu)?

I had to fix Kmix, but also the global shortcuts (make them target Master instead of PCM). I don't know why KDE so consistently (Intrepid did it as well) picks the wrong one. :)

---

### Post by Namtabmai on 2009-04-25
This is probably better off in one of the support forums but;

Run xev from a terminal, focus on the window that is produced and press your mute button. The terminal should show something like;

```
state 0x10, keycode 121 (keysym 0x1008ff12, XF86AudioMute), same_screen YES,
```

The XF86AudioMute, is the important part. If you get this your system recognises the button a mute button and KDE isn't picking this up. If you don't see this, then the system as a whole doesn't think the button is a mute button.

---

### Post by jaimedavila on 2009-04-25
I don't get anything from xev, but the hardware does treat the keys as mute, volume up, volume down, etc, as evidenced by the fact that the volume does mute, and go up, and go down. In my case it's just that I get no screen confirmation that the key was pressed, or on the systray kmix icon.

---

### Post by kpkeerthi on 2009-04-27
> **snova said:**
> 
I had to fix Kmix, but also the global shortcuts (make them target Master instead of PCM).

Can you elaborate?

---

### Post by snova on 2009-04-27
> **kpkeerthi said:**
> Can you elaborate?

System Settings -> Keyboard & Mouse -> Global Keyboard Shortcuts

KDE Component: Kmix

The keys were bound to generic actions, "Decrease Volume", etc. I moved each of them to the one with "Master" in them.

---

### Post by jaimedavila on 2009-04-27
Those system settings are probably useful. In my entries the "master" setting is blank. 

Now, does anyone know what to do if, when I try to map the master mute to the mute button, I press the mute button and it doesn't register in the input box? Notice that, when I tried pressing the mute button inside the box created by xev, I got nothing. 

Thanks,

Jaime

---

### Post by Firestem4 on 2009-04-27
Kubuntu 9.04 works with Volume Up/Down and Mute. I have not tested the rest. Running on a Dell XPS M1210. 

Amarok sometimes has to be configured against the default KDE Global or Program hotkeys. For instance my HP Pavillion Dv9600 has a lot of multimedia keys and so far I've only gotten the volume to work globally. Play/Pause only works when Amarok is my active window. (Running Arch w/ KDEmod on my HP laptop)

My previous dell laptop (Inspiron). The keys would work globally but Pause would restart the song from the beginning.

---

### Post by der_joachim on 2009-04-28
I did some testing, and it was amarok2 after all. The amarok 1.4 shortcuts were overwritten. As somebody wrote earlier in this thread, the volume keys are configured for kmix, and for some reason amarok2 does not use kmix. I am still looking for a way to get them to play together.

---

### Post by SLA_leandrin on 2009-05-10
> **snova said:**
> System Settings -> Keyboard & Mouse -> Global Keyboard Shortcuts

KDE Component: Kmix

The keys were bound to generic actions, "Decrease Volume", etc. I moved each of them to the one with "Master" in them.

Hi.

This worked fine for me, BUT now there's no graphic display of the volume percentage when turning volume up or down... does anyone knows how to fix that??

Cheers.

---

### Post by nikolardo on 2009-05-24
> **SLA_leandrin said:**
> Hi.

This worked fine for me, BUT now there's no graphic display of the volume percentage when turning volume up or down... does anyone knows how to fix that??

Cheers.

ditto for me.  I had a graphical display but no mute functionality when the keys were linked to the PCM volume, when linked to the master everything seems happier and mute works, but no display.

I seem to have fixed this for me.  It should work for everyone.  Right-click the Kmix icon on the panel, click "Select Master Channel..." and set "Master" instead of "PCM" as the master channel.  Then go into "Keyboard Shortcuts,"  and set the hotkeys not the simple "increase volume" "decrease volume" and "mute", not the ones with "Master" in the title.  Having the simple settings brings the graphical volume display back, and having "Master" as the Master Channel makes it so that the shortcuts apply to master.

---

### Post by Rythan on 2009-06-24
> **nikolardo said:**
> ditto for me.  I had a graphical display but no mute functionality when the keys were linked to the PCM volume, when linked to the master everything seems happier and mute works, but no display.

I seem to have fixed this for me.  It should work for everyone.  Right-click the Kmix icon on the panel, click "Select Master Channel..." and set "Master" instead of "PCM" as the master channel.  Then go into "Keyboard Shortcuts,"  and set the hotkeys not the simple "increase volume" "decrease volume" and "mute", not the ones with "Master" in the title.  Having the simple settings brings the graphical volume display back, and having "Master" as the Master Channel makes it so that the shortcuts apply to master.
Ah, that is the correct solution thanks

---

