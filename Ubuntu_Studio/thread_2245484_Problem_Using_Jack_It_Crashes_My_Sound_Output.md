---
title: "Problem Using Jack: It Crashes My Sound Output"
date: 2014-09-24
forum: Ubuntu Studio
---

### Post by daniel.jumper on 2014-09-24
Hi all,

I just installed ubuntu studio 14.04 (dual booting with windows) on my gateway NV570P V2.06 laptop and I'm having some sound output issues. My goal is to use an external midi keyboard to play music live using some sort of midi sequencer (I'm very new and still have to learn how set all that up, but that's a whole other story). The problem I'm having is that the second I open Jack my sound output stops working.

When I first boot up and log in, sound output works fine. my audio card is recognized and drivers work and everything out of the box. But as soon as I open QjackCtl, or Patchage to start setting up an audio workflow, sound output suddenly stops working and continues not working even after I close the program. In fact, i can "log off" and log back in and it still does not work. Only restarting the computer gets sound output working again.

Obviously something is wrong, and it could be very simple or very complex but I don't even know where to start troubleshooting. I'm super new to working with linux audio. Any help or tips for troubleshooting would be greatly appreciated!

UPDATE:

some clarification: It seems that the behavior I described above (sound output stopping immediately when i start jack) only happens when i open Patchage. When I open qjackctl now, sound keeps working, but i'm getting error messages now.

So, I'm not sure if I somehow missed it before, or if it's a new thing, but now when I start QjackCtl, I get these error messages:
>  [COLOR=#999999]01:00:02.915 Patchbay deactivated.[/COLOR]

 [COLOR=#999999]01:00:02.920 Statistics reset.[/COLOR]
 [COLOR=#cccc99]01:00:02.949 ALSA connection change.[/COLOR]
 [COLOR=#999999]01:00:03.233 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel

 jack server is not running or cannot be started
 [COLOR=#66cc99]01:00:03.240 ALSA connection graph change.[/COLOR]
 (qjackctl:2130): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:2130): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed


but my my sound output continues to work. Anyone make anything of that?

I've been using the command "aplay /usr/share/sounds/alsa/Front_Center.wav" to test my sound and to describe the behavior more specifically when it stops working, it does not produce sound output, but also the command hangs. My fallback test was to play a youtube video and when it stops working, I just don't hear sound output anymore.

Please let me know if anyone has thoughts. Thanks!

---

