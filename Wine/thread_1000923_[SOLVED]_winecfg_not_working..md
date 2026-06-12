---
title: "[SOLVED] winecfg not working."
date: 2008-12-03
forum: Wine
---

### Post by Fahuadai on 2008-12-03
Hello.

I'm trying to get wine working under 8.10.

I've installed wine from apt (v1.0.1), and tried to run the config as instructed on [http://www.winehq.org/site/docs/wineusr-guide/config-wine-main](http://www.winehq.org/site/docs/wineusr-guide/config-wine-main)
I then updated to v1.1.9 using the repository and tried again, but no result either.

I get the following from console when trying to run winecfg:

```

mark@Pegasus:~$ winecfg
No protocol specified
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: Permission denied
No protocol specified
No protocol specified
No protocol specified
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114

```

Trying to run wine config from the application launcher also does nothing. (The application fails to run).

Any suggestions?

---

