---
title: "Run command when logout is initiated"
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-03-23
i had a script running when lightdm's session exits, but as of raring the script runs too late to get the job done
i need it to run "gmusicbrowser -cmd Quit" as soon as i click shutdown/logout

this is what i was using, it ran as root from lightdm's session cleanup script
```
pid="`pgrep -f gmusicbrowser | head -1`"
if [ "0$pid" -gt "0" ]; then
    user=$(ps aux | awk '{print $1" "$2}' | grep $pid | awk '{print $1}')
    sudo -u $user gmusicbrowser -cmd Quit
fi
```

---

### Post by dino99 on 2013-03-24
i does not know how to do that, but you need to set a priority to your script, or teach it about the logout process (kind of while !=logout)

---

### Post by pqwoerituytrueiwoq on 2013-03-24
[IMG]http://images.wikia.com/uncyclopedia/images/2/2f/Facepalm_emote_gif.gif[/IMG]
it is closing properly, i thought is was not cause it opened with a error at login, but really it was starting before pulse-audio which made it give a error
i edited my startup entry to this
```
sh -c 'volume delay;gmusicbrowser -play'
```
volume script: [http://pastebin.com/cxahpsh5](http://pastebin.com/cxahpsh5)
note lines 5 - 7
the script can tell you your audio device my using the dump option, it needs to have that output before it becomes detectable

---

