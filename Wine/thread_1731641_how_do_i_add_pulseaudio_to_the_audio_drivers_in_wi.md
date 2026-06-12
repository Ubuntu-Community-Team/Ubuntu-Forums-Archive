---
title: "how do i add pulseaudio to the audio drivers in wine?"
date: 2011-04-17
forum: Wine
---

### Post by Zeezj on 2011-04-17
i am trying to play the halo demo(or trial if you want to be specific about the os) bu the sound doesn't work so i went to winecfg and apparently i need to get it to use pulseaudio as a driver, but i don't know how...

---

### Post by marin123 on 2011-04-17
you can use alsa and skip one step :)

you will have better latency with alsa.

---

### Post by Zeezj on 2011-04-17
> **marin123 said:**
> you can use alsa and skip one step :)

you will have better latency with alsa.

yeah but alsa isn't working i need to use pulseAudio

---

### Post by dino99 on 2011-04-17
have you seen this topic:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720)

---

### Post by Zeezj on 2011-04-17
> **dino99 said:**
> have you seen this topic:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720)

when i did that, the sound started working for like half a second and then stopped again.

---

### Post by pazuzuthewise on 2011-05-04
It isn't necessary to select directly pulseaudio from winecfg.
You can reroute the output of wine (with the alsa driver selected) to pulseaudio.
You can test if this works for you by running the command:

[INDENT]padsp winecfg[/INDENT]

and testing the sound under the Audio tab with only the Alsa driver selected.
If you can hear the test sound, then run your game with the command

[INDENT]padsp wine *game_executable_name*[/INDENT]

Tested this under with Diablo 2, under Natty and wine 1.2.2. Previously, I had sound only in the menu for a few seconds, when launching the game.

Now it works.:popcorn: It should work also for your game.

---

### Post by cogadh on 2011-05-04
> **pazuzuthewise said:**
> It isn't necessary to select directly pulseaudio from winecfg.
You can reroute the output of wine (with the alsa driver selected) to pulseaudio.
You can test if this works for you by running the command:

[INDENT]padsp winecfg[/INDENT]

and testing the sound under the Audio tab with only the Alsa driver selected.
If you can hear the test sound, then run your game with the command

[INDENT]padsp wine *game_executable_name*[/INDENT]

Tested this under with Diablo 2, under Natty and wine 1.2.2. Previously, I had sound only in the menu for a few seconds, when launching the game.

Now it works.:popcorn: It should work also for your game.

^^This, it's the best/easiest way to get audio working acceptably. Besides, you can't just "add" PA support to Wine, that support simply does not exist in the current version (and it may never exist officially). There is an unofficial and not fully developed addition to Wine called WinePulse that will add limited PA support, but it requires you to custom compile it in Wine... or you can try one of the precompiled versions for Ubuntu found here: [https://launchpad.net/~c-korn/+archive/ppa](https://launchpad.net/~c-korn/+archive/ppa)

---

### Post by cwwilson721 on 2011-05-05
Actually, to clarify the point:

*UBUNTU* doesn't enable pulse audio support in wine when they compile it for the official repos (not the wine devs). Pulse audio IS in the compile options, but due to other issues, it is not enabled in the versions compiled and put on the official repos.

I've gone all three ways: The padsp workaround, the self-compiled wine install, and Korn's repo. All of them work. However, the padsp workaround just makes my shoulderblades itch with the comparison of duct taping the bumper onto your car. It works, but...(To be fair, I feel that way about any workaround)

The self compiled version works wonderful, *if* you know what you are doing concerning the options during compiling. BUT you have to recompile everytime you want to upgrade wine. That's a bit time consuming for me, personally.

So now I stick with the Korn repos. The packages are solid, they work very well, and are updated fairly closely to the official repos (might be a day or two behind, but that's okay with me).

So, take your choice, and do what you wish. That's why I've been using Linux for MANY years. The choice.

---

