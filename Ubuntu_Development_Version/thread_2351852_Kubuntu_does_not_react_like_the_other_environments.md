---
title: "Kubuntu does not react like the other environments at all!"
date: 2017-02-07
forum: Ubuntu Development Version
---

### Post by oui on 2017-02-07
I use Kubuntu 17.04.

I did install it as «netinstall» in language «Korean» adding at the step taksel «Kubuntu full».

As it was not possible for me to write Korean Hangul characters after the first start of the new installation (no Dialog «adequate Input Method for that language needing? [Y/N]», I did add more and more other environments growing to an really impressing big installation).

I did install in Korean only because I will write in Hangul chars only to learn that language I actually absolutely not know... So I need other languages. I did especially add British English, French, and German, as I am French and live in Germany since years). And I write usually using the Ubuntu keyboard map «us intl» as it permit to write the most West European languages and pinyin very correctly.

My problems with Kubuntu:

- no way to make that the clear information «us intl» can be selected AND appears after that in the settings...
- it seems that the keyboard selector in Kubuntu reduces the choices from 4 to only 3 languages (I really need 4 including Korean)
- it is not clear how to select ibus without disturb in the Kubuntu settings
- Kubuntu refuses to take the CLI command «setxkbmap us intl» in consideration

---

### Post by SeijiSensei on 2017-02-07
You do realize you're running a cutting-edge version of Kubuntu that is still a couple months away from release, right?  And even when it is released, 17.04 will have just a nine-month lifetime?

Have you tried the long-term support versions, 16.04 or 14.04?  Did you have the same problems on those?

I've run Kubuntu for years and never had to run a "tasksel kubuntu full" command.

---

### Post by zika on 2017-02-08
> **oui said:**
> - Kubuntu refuses to take the CLI command ```
setxkbmap us intl
``` in consideration```
setxkbmap us -variant intl
```

---

### Post by oui on 2017-02-10
> **zika said:**
> ```
setxkbmap us -variant intl
```

Thank you! I also use this code

setxkbmap -layout us -variant intl

for other languages, but it does not solve the problem, sorry.

---

### Post by oui on 2017-02-12
Changing the language did bring messages to appear being more expressive for me. The German version did explain me at setting time, that, really, the ibus input method can disturb the usual keyboard setting.

after the installation of LXQT over the Kubuntu full installation, I  have in LXQT a more easy access to the commands and I did experiment that it is possible, but terribly bad integrated, to commute ibus on and off. doing that, it is possible to have access to all signs under heavy difficulties (perhaps/probably is KDE not the optimal environment for ibus?). But one step stay (actually for me) impossible: reactivate the dead key writing so that both sign are to see, but not the one under the other :mad: 

an idea how to find a more user friendly way

(the best way would probably don't to use the commutations icons but to open a console and activate step by step all that in commando line interpreter... after that and the adequate experience, it would probably possible to make it more easy with a script!)

my problem: I don't know and don't find the adequate CLI commands.

how is knowing them?

---

