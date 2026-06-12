---
title: "Mint - Installed streaming server Streamio and then deleted it, apt now calls it"
date: 2021-07-12
forum: Ubuntu/Debian BASED
---

### Post by Toast2120 on 2021-07-12
I installed the media server Stremio to test it out. I decided that I didn't like it and the instructions on the website to remove it were to just the delete the folders that it installed to. However now whenever I do an apt request it refers to the program. I even tried to purge it. 

```
 toast@strata:~/Downloads$ sudo apt purge stremio
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package stremio needs to be reinstalled, but I can't find an archive for it.
```

I tried doing a 
  ```
  sudo rm /var/lib/apt/lists/* -vf
    sudo apt-get update
```

But has the same result
```
toast@strata:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package stremio needs to be reinstalled, but I can't find an archive for it.
toast@strata:~$ 
```

I tried reinstalling the program but go this error. 
[ATTACH=CONFIG]288811[/ATTACH]

And trying the commands in that box has the same result:
```
 toast@strata:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package stremio needs to be reinstalled, but I can't find an archive for it.
toast@strata:~$ 
```

I also checked /etc/apt/sources.list but the file contains nothing. What can I try?

---

### Post by Toast2120 on 2021-07-12
Error also seen from Synaptic. Synaptic immediately closes after closing the dialog window.

[ATTACH=CONFIG]288812[/ATTACH]

---

### Post by monkeybrain20122 on 2021-07-12
So I found [this]("https://translate.google.com/translate?hl=en&sl=pt&u=https://ubuntuforum-br.org/index.php%3Ftopic%3D121535.0&prev=search&pto=aue"). Translate the page with google translate if you can't read Portuguese. Never heard of this program but a google search shows that a lot of people are having problems removing it including Windows and Mac, if not a Malware then it is very poorly packaged and documented.

---

