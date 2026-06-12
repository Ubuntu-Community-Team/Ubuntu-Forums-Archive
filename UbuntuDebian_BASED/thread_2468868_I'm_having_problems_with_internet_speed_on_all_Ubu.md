---
title: "I'm having problems with internet speed on all Ubuntu Based Distros"
date: 2021-11-12
forum: Ubuntu/Debian BASED
---

### Post by renatenho on 2021-11-12
I'm trying to migrate to linux and I tried several distributions my favorite were Zorin OS and Manjaro, but in manjaro I had problems with drivers and left it aside, I tried Kubuntu, Ubuntu , Zorin and Pop!_OS in versions, 20.04.3 LTS and version 21.10, right now I have an installation of Zorin OS, in all of them I disabled ipv6, because I researched and in my research I saw that this could be it, but I still have the same problem, what makes me strange is that it is only through the terminal, when I do the speed measurement through the browser or when I try to download something through the browser the speed is normal mbps 500, but I tried to download python through apt and well... "Fetched 1766 kB in 10min 20s (2,848 B/ s)", with and without the ipv6 the speed through the terminal is about 3 b/s

---

### Post by praseodym on 2021-11-12
Please run the wireless script from the sticky thread and show the outputs

---

### Post by renatenho on 2021-11-13
If i do this with pastebin informations are masked?

---

### Post by DuckHook on 2021-11-13
[list=1]
[*]It is fine to post your results of the WIFI script in public. Sensitive identification info is either masked or not gathered to start with. However, please post results either as attachment (preferred), or post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.
[*]In a typical setup, it is unlikely that you have different download speeds through your browser versus your command line. Unless you have some sort of convoluted proxy setup, your browser is using exactly the same network infrastructure and protocols as your command line.
[*]The only example of slow CLI download speeds that you give is your apt update process. This could be due to your use of a slow mirror. Changing to a faster mirror may be all you need to solve this.
[*]To test CLI DL speed vs browser, install then run speedtest-cli and compare to browser speedtest.net results. ```
sudo apt install speedtest-cli && speedtest-cli
``` This will give you an accurate speed comparison. For reasons given in (3) above, looking at apt download speed is not accurate.
[/list]

---

### Post by rsteinmetz70112 on 2021-11-14
I find the repository mirrors are frequently slow.

---

