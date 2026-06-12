---
title: "[IDEA] -- generic loading screen for all programs"
date: 2007-11-07
forum: Ubuntu Brainstorm
---

### Post by altonbr on 2007-11-07
**Summary:**
Only a couple (major) programs in Ubuntu has splash/loading screens. Off the top of my head they are OpenOffice.org and GIMP.

I propose adding a simple, text and xpm/png based loading screen for ALL programs.

This is because I think users should always know when a program is loading or not because some novice users need visual reassurance right away.

**Scope and Use Cases:**
* Alida launches Firefox on a slower computer and it takes 20 seconds for it to load. She clicked the icon but nothing popped up, so she clicked it again and again and again, slowing down her computer by launching multiple Firefoxes.

* Ralph launches a heavy Wine application that takes 2 minutes and 30 seconds to load. He begins to think the program isn't working and reboots the computer.

**Implementation Plan:**
I've GIMPed a mockup for one of my games, GTA Vice City.

Right now it takes a 32x32 pixel xpm icon and stretches it to 96x96 (ew...) and then adds in the program name to the right. I think it would be easy to make a new splash screen but I hope this gives you the gist.

---

### Post by 23meg on 2007-11-07
It's overkill for all programs. Proper launch feedback from icons and task list entries would be preferable. Giving a somewhat unified look (and possible Ubuntu-branding, as in Gutsy's OO.o) to all splash screens in *applications that do have splash screens*, however, is a good idea.

---

### Post by Rinzwind on 2007-11-07
I would second this idea and would suggest even to include errormessages inside the splashscreen. Nothing's so annoying than clicking, seeing nothing, cursor going back into 'arrow-mode' and still seeing nothing only to find out you need to go to 'terminal', type it again, see the error-message, fix it and try again.

---

### Post by coolen on 2007-11-08
Seems to me this would still need to be implemented by the developer. Forcing it on all programs would get too cluttered, as even small programs that load in seconds may end up with splash screens. It'd be incredibly difficult to apply it to Wine programs, I'd imagine.
Very, very large scope. Perhaps including a splash screen for bigger applications would be a better idea. I remember back in Windows, Firefox had a splash screen.

---

### Post by teasum on 2007-11-08
> **23meg said:**
> It's overkill for all programs. Proper launch feedback from icons and task list entries would be preferable. Giving a somewhat unified look (and possible Ubuntu-branding, as in Gutsy's OO.o) to all splash screens in *applications that do have splash screens*, however, is a good idea.

I agree.  In fact, I like what firefox and evolution do--they show up in the window list as 'loading'.  Although I have had a problem similar to that described in the OP, where I click on firefox, nothing happens, then I click again, and eventually I end up with two or three windows, I would guess that if the window-list message did not appear, neither would a splash screen, were it enabled.

I also agree with the idea of fostering a unified look for splash screens already installed.  However, the Ubuntu-branded OOo screen was updated and changed to a blue splash screen some weeks back.  Is there perhaps an issue with uniformly branding splash screens?  I don't know why the change was made, and I thought I'd ask here as it is relevant to the idea being suggested.

---

