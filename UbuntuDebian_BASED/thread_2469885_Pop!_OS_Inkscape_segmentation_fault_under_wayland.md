---
title: "Pop! OS Inkscape segmentation fault under wayland"
date: 2021-12-12
forum: Ubuntu/Debian BASED
---

### Post by jubberwhacky on 2021-12-12
I'm running Pop! OS 21.04, but since the update to 20.10, Inkscape  is not running anymore under wayland. I'm running Inkscape v1.0.2  installed through apt. The curious thing is that Inkscape is working  under X, but under wayland I get
```
**  (org.inkscape.Inkscape:1068048): WARNING **: 18:33:08.156: Fonts dir  '/usr/share/inkscape/fonts' does not exist and will be ignored.
[1]    1068048 segmentation fault (core dumped)  inkscape
```
when running Inkscape in the terminal (the warning is not the cause, I also get it under X).
I tried reinstalling and deleting ~/.config/inkscape but this didn't help.

The  flatpak version of Inkscape is working under wayland, but due to  sandboxing it can't find my LaTeX installation (which is needed for  equation rendering in Inkscape and absolutely essential).

I guess  it's not a problem with Inkscape or Pop! OS per se, since I couldn't  find anyone else having the problem. I guess a proper clean-up und  reinstall of Inkscape might solve the problem, but I don't know where  other config files are stored.

I'd be happy to provide some debug logs, if someone could tell me what to run.

---

