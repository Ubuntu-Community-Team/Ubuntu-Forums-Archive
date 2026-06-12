---
title: "Open Spotify URIs from Firefox"
date: 2009-10-31
forum: Wine
---

### Post by hekone on 2009-10-31
I've followed all tutorials I found on Google and it still doesn't work. Does anyone know how to do it??

I have Ubuntu 9.10 and I'm using wine to run spotify.

Thanks

---

### Post by ukblacknight on 2009-11-14
Yup.  The guide on the spotify website is wrong, although I'm positive it worked for me once, then stopped.

In the terminal, copy & paste each line:

```
echo '#!/bin/sh' > ~/.browser2spotify
echo 'exec wine "C:\Program Files\Spotify\spotify.exe" /uri "$1"' >> ~/.browser2spotify
chmod 755 ~/.browser2spotify
```

Note: On the spotify website, it passes $@ - that's wrong!

If you've done all the other stuff, like go into about:config, then you need to get rid of them:

[LIST=1]
[*]In the address bar in Firefox, type about:config
[*]Search for Spotify
[*]Reset the two items that the website told you to add (if they don't exist, ignore this step)
[*]Restart firefox
[*]Go into Edit->Preferences->Applications
[*]Search for Spotify
[*]*Change* the handler to other, using .browser2spotify in your home directory
[/LIST]

This should now work.

---

### Post by hekone on 2009-12-03
Thanks!

Sorry but I wasn't able to response earlier.
:D

---

### Post by Shwan.c on 2010-03-06
> **ukblacknight said:**
> Yup.  The guide on the spotify website is wrong, although I'm positive it worked for me once, then stopped.

In the terminal, copy & paste each line:

```
echo '#!/bin/sh' > ~/.browser2spotify
echo 'exec wine "C:\Program Files\Spotify\spotify.exe" /uri "$1"' >> ~/.browser2spotify
chmod 755 ~/.browser2spotify
```

Note: On the spotify website, it passes $@ - that's wrong!

If you've done all the other stuff, like go into about:config, then you need to get rid of them:

[LIST=1]
[*]In the address bar in Firefox, type about:config
[*]Search for Spotify
[*]Reset the two items that the website told you to add (if they don't exist, ignore this step)
[*]Restart firefox
[*]Go into Edit->Preferences->Applications
[*]Search for Spotify
[*]*Change* the handler to other, using .browser2spotify in your home directory
[/LIST]

This should now work.

it's not working for me as FF 3.6 ubuntu karmic, FF ignores handlers in the about:config 
from here [http://kb.mozillazine.org/Register_protocol](http://kb.mozillazine.org/Register_protocol)  I got this 
```

[CODE]gconftool-2 -s /desktop/gnome/url-handlers/foo/command '/path/to/app %s' --type String
gconftool-2 -s /desktop/gnome/url-handlers/foo/enabled --type Boolean true
```

Replace foo on both lines with the protocol you want to register and /path/to/app with the path to the application you want to run. [/CODE]

---

