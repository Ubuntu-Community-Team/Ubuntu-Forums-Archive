---
title: "An updated WINE possible?"
date: 2010-01-10
forum: Wine
---

### Post by josepaul on 2010-01-10
Hi, I'm pretty new to all this Linux and stuff (max 1/2 year knowledge), in the WINE program, whenever I run a windows program, it goes to a '98 style interface, am I being naive or can this be changed to a more current vista or win7 style one? Just a suggestion, unless you can already do this?, I don't know, what do you think?

---

### Post by gsmanners on 2010-01-10
WINE does have theme support. I guess you could do a search for "msstyles" and see what turns up.

> 1. Download a Windows XP theme. Be sure it contains a .msstyles file.

2. Create a set of new directories in your fake Windows drive: $ mkdir -p ~/.wine/drive_c/windows/Resources/themes/name-of-your-theme

3. Move the .msstyles to that new name-of-your-theme directory.

4. Use the Desktop Integration tab of winecfg to select the new theme.

See: [http://www.winehq.org/docs/wineusr-guide/config-wine-main#AEN309](http://www.winehq.org/docs/wineusr-guide/config-wine-main#AEN309)

---

### Post by Soulcage on 2010-01-11
In winecfg's graphics tab did you turn off: allow the window manager to decorate the windows?

---

