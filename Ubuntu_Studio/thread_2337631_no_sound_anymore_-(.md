---
title: "no sound anymore :-("
date: 2016-09-20
forum: Ubuntu Studio
---

### Post by anakine78 on 2016-09-20
hello,

my saffire pro 24 dont work very well with ffado, so searched on forums and tried things..

then I wrote the following line in /etc/modprobe.d/blacklist-firewire.conf:
install snd_dice /bin/false

and now i dont have sound.

tried the inverse : install snd_dice /bin/true

but won't work.. deleted the line also but same. no sound.

can you help me to repair it ?

---

### Post by CrocoDuck on 2016-09-20
You will need to either remove or comment (better practice) that line by placing a # in front of it:
```

#install snd_dice /bin/false

```

What you are doing with that line is to force the system to not load the snd_dice kernel module not even if required by other modules. Changing /bin/false to /bin/true will not change much I am afraid, as these are just binaries that return a status code and then exit, thus allowing module load failure (type man true and man false in the console for more info). Just to clarify: the install keyword makes /bin/true or /bin/false (or whatever you put there) to run in place of module insertion. Beware that this will produce also the load failure of all the other modules that depend on it (see [here]("https://wiki.archlinux.org/index.php/Kernel_modules#Blacklisting") for more info). Probably this is preventing some module that you need for audio to load.

In order to resolve possible conflicts with hardware drivers handling your device, you are better trying something like [this]("https://wiki.archlinux.org/index.php/JACK_Audio_Connection_Kit#Firewire") (additional info [here]("https://wiki.archlinux.org/index.php/Professional_audio#FireWire")). The blacklist keyword prevents module loading unless required by a dependency (you can see all keywords by typing man modprobe.d in your terminal). As such, it is better to have a go with it first.

Hope it helps and, please, _do not mess with conf files without documenting yourself on what you are doing_. You need to know what you are doing in order to:


[LIST]
[*]Be successful 
[*]Be able to roll back something bad should happen 
[*]Avoid potential destructive actions 
[/LIST]

I really advise you to have a good read at the pages I linked and to often refer to man pages. Linux installations come with plenty of help.

---

