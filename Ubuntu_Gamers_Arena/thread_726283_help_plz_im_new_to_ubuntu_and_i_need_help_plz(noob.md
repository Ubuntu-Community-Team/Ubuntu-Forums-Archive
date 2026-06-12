---
title: "help plz im new to ubuntu and i need help plz(noob)"
date: 2008-03-16
forum: Ubuntu Gamers Arena
---

### Post by armory555 on 2008-03-16
ok  i downloaded armicas army for linux(armyops250linux.run) and it wont open off the desktop and when i try to open it it freezes my comp for a min or 2 so i try puting this command in the terminal >>>cd Desktop
                                                        >>>sh ./armyops250linux.run
and it work fine untill it says "please enter the installation path"
                                                   /usr/local/games/armyops/
                                                           <ok>          <cancel>
and just like any one else would most likely do i click enter which is the "ok"thing
but then it says             "Failed promissions"
                                                  <ok>
and i cant seem to get that to work plz help noob in dire need, and for sum reason and other things i try to do in the terminal it also says sumthing like that and i amthe only user on the comp which i think make me admin so why dose it sat that and help plz i need a solution i want to play that game plz plz plz help:(:mad::confused:

---

### Post by scragar on 2008-03-16
you may need root perms to install to /usr
```
sudo sh ./armyops250linux.run
```

---

### Post by k01 on 2008-03-21
Or
# su
Password: *****
# ./armyops250linux.run

---

### Post by imT on 2008-03-21
i'm don't think is a good idea to install a product developed by a government on your pc, but that's my n00b opinion, it's not necessarily a questionable thing.

---

### Post by scragar on 2008-03-21
> **k01 said:**
> Or
# su
Password: *****
# ./armyops250linux.run

not wise to enable the root accound, so I'd still say go for sudo.

and if need be long term sudo access can be done using ```
sudo -i
```

---

