---
title: "Getting error while using make command"
date: 2017-07-09
forum: Server Platforms
---

### Post by aaressinfomedia on 2017-07-09
[COLOR=#000000]Hello Community Members,[/COLOR]

[COLOR=#000000]I am sujit from India, I am trying to clone litecoin on my linux ubuntu server, I am completing all steps as per instructions but getting error while trying to use make command as follow;[/COLOR]

[COLOR=#000000]$ make -f makefile.unix USE_UPNP=-[/COLOR]

[COLOR=#000000]Error I am getting is [/COLOR]

[COLOR=#000000]make: *** No rule to make target `makefile.unix'. Stop.[/COLOR]

[COLOR=#000000]please help I am stuck at this point.[/COLOR]

---

### Post by steeldriver on 2017-07-09
The error means that there isn't a file called 'makefile.unix' in the directory where you are running the command

Perhaps you are in the wrong directory

Or perhaps a previous step (such as an autogen command) failed to create the file due to earlier errors or missing dependencies

---

