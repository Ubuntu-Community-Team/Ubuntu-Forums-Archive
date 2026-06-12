---
title: "Steam, Left 4 Dead &amp; Left 4 Dead 2 Demo test results"
date: 2009-11-03
forum: Wine
---

### Post by lukeozade on 2009-11-03
Hey there.

All tests were done on unmodified wine versions with no additional programs installed on-top of it (i.e.: using winetricks to install fonts, ect..)

I am using the 190.42 version of the nvidia driver, availible from [http://www.nvidia.com/object/linux_display_ia32_190.42.html]("http://www.nvidia.com/object/linux_display_ia32_190.42.html") 

I am running Kubuntu 9.10 (Karmic Koala), desktop effects are turned off. Two gigs of DDR2 ram and Dual core amd athlon64 processor.

I decided to test Steam, Left 4 Dead and Left 4 Dead 2 Demo on a variety of wine versions to see which one came out top. Left 4 Dead and Left 4 Dead 2 demo are similar in a variety of ways, so testing them both seemed sensible. Steam is needed to run both these so i had to test this too.

I could not get the Left 4 Dead 2 Demo to work on any of them. Although before these tests i did manage to get to the level loading screen, where it would crash.

Left 4 Dead running on wine Wine 1.1.28 + will crash whilst viewing the crash course message of the day.

Does anyone know of a way to get the steam community in-game to work, it wouldn't work on any of the versions tested.

Finally, has anyone got the demo running successfully?

**_Some progress has been made:_**

[IMG]http://i33.tinypic.com/2vj1y1i.png[/IMG]
[IMG]http://i36.tinypic.com/28vso5k.jpg[/IMG]
[IMG]http://i38.tinypic.com/552v0w.png[/IMG]
[IMG]http://i37.tinypic.com/1p9i5z.png[/IMG]
[IMG]http://i35.tinypic.com/xcvmsj.png[/IMG]

Here are my results, starting from newest Wine version to oldest:

Wine 1.1.32 - L4D2 crashes on the loading screen. Program error.
Wine 1.1.32 - L4D playable, averaging 20fps. Leaves a zombie process of itself and comes up with the serious error message upon quitting it. Crashes viewing the motd (message of the day) on crash course.
Wine 1.1.32 - Steam loaded fine, can launch games.
Wine 1.1.31 - L4D2 crashes on the loading screen. Program error.
Wine 1.1.31 - L4D playable, averaging 18fps. Leaves a zombie process of itself and comes up with the serious error message upon quitting it. Crashes viewing the motd (message of the day) on crash course.
Wine 1.1.31 - Steam loaded fine, can launch games.
Wine 1.1.30 - L4D2 crashes xserver, forced to relogin.
Wine 1.1.30 - L4D playable, averaging 19fps. Leaves a zombie process of itself and comes up with the serious error message upon quitting it. Crashes viewing the motd (message of the day) on crash course.
Wine 1.1.30 - Steam loads fine, can launch games.
Wine 1.1.29 - L4D2 crashes xserver, forced to relogin.
Wine 1.1.29 - L4D playable, averaging 19fps. Leaves a zombie process of itself and comes up with the serious error message upon quitting it. Crashes viewing the motd (message of the day) on crash course.
Wine 1.1.29 - Steam loaded fine, can launch games.
Wine 1.1.28 - L4D2 freezes with a program error on the loading screen.
Wine 1.1.28 - L4D playable, averaging 18fps. Leaves a zombie process of itself and comes up with the serious error message upon quitting it. Crashes viewing the motd (message of the day) on crash course.
Wine 1.1.28 - Steam loaded fine, can launch games.
Wine 1.1.27 - L4D2 crashes xserver, forced to relogin.
Wine 1.1.27 - L4D playable, averaging 18fps. Serious error after quitting the game. Can play crash course and view the message of the day.
Wine 1.1.27 - Steam loaded fine, could launch games.
Wine 1.1.26 - L4D2 crashes xserver, forced to relogin.
Wine 1.1.26 - L4D playable, averaging 19fps. Upon quitting it says it encounted a serious error, but this doesn't affect game-play. Leaves a zombie (how convenient :D) process of itself which needs to be killed too.
Wine 1.1.26 - Steam loaded fine, could launch games.
Wine 1.1.25 - L4D2 wouldn't work as steam could not load.
Wine 1.1.25 - L4D wouldn't work as steam could not load.
Wine 1.1.25 - Steam encountered a serious problem, forced to kill the process.
Wine 1.1.24 - L4D2 wouldn't work as steam could not load.
Wine 1.1.24 - L4D wouldn't work as steam could not load.
Wine 1.1.24 - Steam encountered a serious problem, forced to kill the process.
Wine 1.1.23 - L4D2 wouldn't work as steam could not load.
Wine 1.1.23 - L4D wouldn't work as steam could not load.
Wine 1.1.23 - Steam encountered a serious problem, forced to kill the process.
Wine 1.1.22 - L4D2 wouldn't work as steam could not load.
Wine 1.1.22 - L4D wouldn't work as steam could not load.
Wine 1.1.22 - Steam encountered a serious problem, forced to kill the process.
Wine 1.1.21 - L4D2 wouldn't work as steam could not load.
Wine 1.1.21 - L4D wouldn't work as steam could not load.
Wine 1.1.21 - Steam encountered a serious problem, forced to kill the process.
Wine 1.1.20 - L4D2 Crashes at loading screen, program error.
Wine 1.1.20 - L4D playable, averaging 18fps.
WIne 1.1.19 - L4D2 crashes at loading screen, freezes.
Wine 1.1.19 - L4D playable, averaging 18fps.
Wine 1.1.18 - L4D2 crashes at loading screen, freezes.
Wine 1.1.18 - L4D playable, averaging 17fps.
Wine 1.1.17 - L4D2 crashes at valve video before loading screen, application bails out.
Wine 1.1.17 - L4D playable, averaging around 20fps.
Wine 1.1.16 - L4D2 crashed my xserver, forced to log back in.
Wine 1.1.16 - L4D playable, averaging 15fps
Wine 1.1.16 - Steam loaded fine, could launch games.
Wine 1.1.15 - L4D2 crashes after intro video, still crashes after passing the -novid parameter.
Wine 1.1.15 - L4D playable, averaging 17fps.
Wine 1.1.15 - Steam loaded fine and could launch games.
Wine 1.1.14 - L4D2 crashes after intro video, still crashes after passing the -novid parameter.
Wine 1.1.14 - L4D playable, averaging 17fps.
Wine 1.1.14 - Steam loaded fine and could launch games.
Wine 1.1.13 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.13 - L4D playable, averaging 18fps.
Wine 1.1.13 - Steam loaded fine and could launch games.
Wine 1.1.12 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.12 - L4D playable, averaging 16fps.
Wine 1.1.12 - Steam loaded fine and could launch games.
Wine 1.1.11 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.11 - L4D playable, averaging 17fps.
Wine 1.1.11 - Steam loaded fine and could launch games.
Wine 1.1.10 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.10 - L4D playable, averaging 17fps.
Wine 1.1.10 - Steam loaded fine and could launch games.
Wine 1.1.9 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.9 - L4D playable, averaging 17fps.
Wine 1.1.9 - Steam loaded fine and could launch games.
Wine 1.1.8 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.8 - L4D playable, averaging 15fps.
Wine 1.1.8 - Steam loaded fine and could launch games.
Wine 1.1.7 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.7 - L4D playable, averaging 18fps.
Wine 1.1.7 - Steam loaded fine and could launch games.
Wine 1.1.6 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.6 - L4D playable, averaging 17fps.
Wine 1.1.6 - Steam loaded fine and could launch games.
Wine 1.1.5 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.5 - L4D playable, averaging 16fps.
Wine 1.1.5 - Steam loaded fine and could launch games.
Wine 1.1.4 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.4 - L4D playable, averaging 16fps.
Wine 1.1.4 - Steam loaded fine and could launch games.
Wine 1.1.3 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.3 - L4D playable, averaging 15fps.
Wine 1.1.3 - Steam loaded fine and could launch games.
Wine 1.1.2 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.2 - L4D playable, averaging 17fps.
Wine 1.1.2 - Steam loaded fine and could launch games.
Wine 1.1.1 - L4D2 crashes after intro video, stilll crashes after passing the -novid parameter.
Wine 1.1.1 - L4D playable, averaging 16fps.
Wine 1.1.1 - Steam loaded fine and could launch games.
Wine 1.1.0 - L4D2 crashes after intro video, still crashes after passing the -novid parameter.
Wine 1.1.0 - L4D playable, averaging 15fps.
Wine 1.1.0 - Steam loaded fine and could launch games.
Wine 1.0.1 [STABLE RELEASE] L4D2 does not load.
Wine 1.0.1 [STABLE RELEASE] L4D playable, averaging around 16fps
Wine 1.0.1 [STABLE RELEASE] Steam loaded fine and could launch games.
Wine 1.0.0 - L4D2 does not load.
WIne 1.0.0 - L4D playable, averaging 15fps.
Wine 1.0.0 - Steam loaded fine and could launch games.
Wine 0.9.61 - left 4 Dead playable, averaging around 15fps.
Wine 0.9.60 - Left 4 Dead 2 demo does not load.
Wine 0.9.60 - Left 4 Dead playable, averaging 15fps.
Wine 0.9.60 - Steam loaded fine and could launch games.

I am currently using Wine 1.1.27 so that i can play L4D1 without the motd crashes. I got the demo to get as far as the game loading screen by running it from another partition and giving no access to writing files so nothing can be changed. I always have steam open at the same time. I beleive it crashes because of steam not picking it up as when it does crash it will open a steam windows complaining that the demo installation is incomplete (when it is not.)

For anyone that's interested here is the crash output from the konsole.

[Crash log]("http://pastebin.com/f2a9e6ede")

---

