---
title: "Wine Programs Cannot Access Internet plz help"
date: 2009-11-02
forum: Wine
---

### Post by tanush on 2009-11-02
Guyz Im a newbie as you can see and im having a serious problem
which is :

[B][SIZE=6][COLOR=Black]Wine Programs Cannot Access Internet[/COLOR][/SIZE]



[FONT=Tahoma]same thing happens when i use cross over...

Im using ubuntu 32 bit wine and cross over are totally updated.

plz help..


this is the last thing i need before i make a total which to linux
[/FONT]


waitng for ur help eagerly


[/B]

---

### Post by beastrace91 on 2009-11-02
Just so we are clear your native Linux applications can get on the net but Wined programs can not? By totally updated this means your Wine version is 1.1.32 and Crossover is running at the latest version of 8? Also if the issue is occurring within Crossover before to file a support ticket with them - they are very good about getting back to you.

~Jeff

---

### Post by pedro_orange on 2009-11-03
Run the applications from the terminal and whack up the debug level. 
I would imagine it's nothing to do with wine itself, but you never know. Post the terminal output here please.

---

### Post by tanush on 2009-11-03
> **pedro_orange said:**
> Run the applications from the terminal and whack up the debug level. 
I would imagine it's nothing to do with wine itself, but you never know. Post the terminal output here please.
i told you im a newbie...

tell me how to do it


i can open console and run from there
 but how can i debug ?

---

### Post by tanush on 2009-11-03
> **beastrace91 said:**
> Just so we are clear your native Linux applications can get on the net but Wined programs can not? By totally updated this means your Wine version is 1.1.32 and Crossover is running at the latest version of 8? Also if the issue is occurring within Crossover before to file a support ticket with them - they are very good about getting back to you.

~Jeff



ya i installed wine tomorrow only and cross over too....


im trying to run ultrasurf and IDM but they are not able to connect to internet

---

### Post by pedro_orange on 2009-11-03
> **tanush said:**
> i told you im a newbie...

tell me how to do it


i can open console and run from there
 but how can i debug ?

Terminal:

```
WINEDEBUG=+all wine program
```

Prepare for some serious spam. But have a good read. It might help.

---

### Post by tanush on 2009-11-03
After a lot of searching i think i need lib32nss-mdns

but whenever i install it,using:
apt-get install lib32nss-mdns

It says 
Couldn't find package lib32nss-mdns
 plz help i need a 32 bit version of this

---

### Post by soluphobe on 2009-11-03
I notice you are trying to run programs that are really mods for Windows programs.  Don't expect that running a wine'd ultrasurf will help your ubuntu firefox.

If and when you get these to work, remember you need a wine'd version of firefox/chrome/opera/whatever to take advantage of them.

---

### Post by tanush on 2009-11-04
> **pedro_orange said:**
> Terminal:

```
WINEDEBUG=+all wine program
```Prepare for some serious spam. But have a good read. It might help.

> **soluphobe said:**
> I notice you are trying to run programs that are really mods for Windows programs.  Don't expect that running a wine'd ultrasurf will help your ubuntu firefox.

If and when you get these to work, remember you need a wine'd version of firefox/chrome/opera/whatever to take advantage of them.


 i know it thru a blog i read to make ultrasurf work.

that will be no worries but i just need to install that file..
 you know any way ?

---

