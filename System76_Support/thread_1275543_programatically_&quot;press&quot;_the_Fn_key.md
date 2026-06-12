---
title: "programatically &quot;press&quot; the Fn key"
date: 2009-09-25
forum: System76 Support
---

### Post by slide_o_mix on 2009-09-25
Is there a way to programatically "press" the Fn key? I've opened up xev and tried to see if there was a key code associated with the key, but nothing came up. I am trying to write a little shell script or something that will enable the bluetooth on boot on my wife's Pongolin (that she loves) so that her bluetooth mouse will work without her having to remember to turn it on every time.

---

### Post by perce on 2009-09-26
Sometime hotkeys don't returne a keycode, but an acpi event. You can check that with acpi_listen

---

