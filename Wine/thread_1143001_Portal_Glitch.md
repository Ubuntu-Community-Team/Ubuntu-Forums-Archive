---
title: "Portal Glitch?"
date: 2009-04-29
forum: Wine
---

### Post by tmun52 on 2009-04-29
So I got the Orange Box and installed it without errors with Wine. All the games work flawlessly, with the exception of a weird glitch in Portal.
    When the main menu loads up, I see a box on the bottom left hand corner of the screen that shows everything that's on the screen upside-down. It stays there when I'm actually playing the game, too. It doesn't much of a problem to the game-play, but when I updated to 9.04, I now see two boxes- one on the bottom left, and one on the top left.
I located this bug on the Wine Database and found a solution, which was to change the registry, but the bug is still prevalent. I think I might not have made the correct changes to the registry, or maybe the solution didn't work at all. I was hoping someone could help me on this.
Thanks.

---

### Post by cogadh on 2009-04-30
It might help if you actually told us what changes you made to the registry, perhaps providing a screenshot of it.

---

### Post by u235sentinel on 2009-04-30
> **tmun52 said:**
> So I got the Orange Box and installed it without errors with Wine. All the games work flawlessly, with the exception of a weird glitch in Portal.
    When the main menu loads up, I see a box on the bottom left hand corner of the screen that shows everything that's on the screen upside-down. It stays there when I'm actually playing the game, too. It doesn't much of a problem to the game-play, but when I updated to 9.04, I now see two boxes- one on the bottom left, and one on the top left.
I located this bug on the Wine Database and found a solution, which was to change the registry, but the bug is still prevalent. I think I might not have made the correct changes to the registry, or maybe the solution didn't work at all. I was hoping someone could help me on this.
Thanks.

Perhaps going through the changes with us would help... :-)

also check out their recommendations on winehq.  They have a few things you could do but personally the only changes I made were enabling direct3d and stuff like that.  I'm guessing this is what you are referring to?

---

### Post by tmun52 on 2009-04-30
Hehe, sorry for the lack of info. I totally forgot. Anyway, I took a few screenshots of Portal and the changes I made to the registry.

---

### Post by cogadh on 2009-04-30
Your registry screenshot explains the problem. You created your new registry entries with their intended value data in the value name. For example, the first string should have the value name "DirectDrawRenderer" with the value data of "OpenGL", not have the value name "DirectDrawRenderer OpenGL" with no value data. You will need to right-click on each entry and select "Modify" to change the value data, then right click on it again and select "Rename" to correct the value name. 

Also, that "UseGLSL" string should not have a space between "Use" and "GLSL".

See attached screenshot for what it should look like.

---

### Post by tmun52 on 2009-05-02
Well, I fixed my registry as per your directions, but the boxes were still present on the screen, so I went and checked back at wineHQ and added "OffscreenRenderingMode"="fbo", too, as it said on the solution I found on the bug I had. Amazingly, adding that worked!
Thanks a lot for your help, guys, I really appreciate it. 

I attached a photo of my new registry. If there is a problem with it, please let me know.

---

