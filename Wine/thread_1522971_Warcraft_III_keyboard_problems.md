---
title: "Warcraft III keyboard problems"
date: 2010-07-02
forum: Wine
---

### Post by necrosymbiont on 2010-07-02
Hello all,

I have a machine running Ubuntu 8.10 w/ Wine 1.1.42.

Until about a month ago, this machine ran Warcraft III more or less without any difficulties. I say "more or less" because there were minor rendering issues that I was willing to tolerate - I believe they are unrelated to the present issue.

Recently, I began encountering the same problem as described in these old threads:

[http://ubuntuforums.org/showthread.php?t=409674](http://ubuntuforums.org/showthread.php?t=409674)
[http://ubuntuforums.org/showthread.php?t=552712](http://ubuntuforums.org/showthread.php?t=552712)
[http://ubuntuforums.org/showthread.php?t=557773](http://ubuntuforums.org/showthread.php?t=557773)

To summarise, the problem is that Warcraft III has stopped capturing keyboard input; all keyboard input goes to the terminal. This prevents me from making new profiles in the main menu, and also prevents the use of hotkeys within the game. The latter problem is very crippling; the game is more or less unplayable if you cannot assign numbers to groups of units.

Now, I see that all those previous threads just died out without any successful resolution being posted, and I would appreciate any help in continuing to deal with the issue described.

What I have tried:
[LIST]
[*]apt-get upgrade
[*]reinstalling warcraft
[*]trying reinstalled warcraft both with and without the latest blizzard patch
[*]running warcraft with the "-opengl" command line argument
[*]altering different settings in the wine config, such as whether or not directx apps should prevent the mouse leaving the window.
[/LIST]

It just seems weird to me that everything was working perfectly (or near enough to it), and then all of a sudden this debilitating keyboard problem suddenly appeared for no apparent reason. Note that as mentioned in the original threads, windowed mode does work, while fullscreen does not. (But I have no intention of playing in windowed mode!)

Oh, and I've attached a couple of files containing the output that obtains from running Warcraft III in both windowed and fullscreen modes. I can't see any significant differences in the outputs aside from the single line:

```
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
```

Edit: Of course you can see this for yourselves, but this line of code appears in windowed mode, but not in fullscreen mode.

---

