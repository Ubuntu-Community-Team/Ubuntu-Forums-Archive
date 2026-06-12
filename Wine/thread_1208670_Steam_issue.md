---
title: "Steam issue"
date: 2009-07-09
forum: Wine
---

### Post by Mayan2012 on 2009-07-09
Hello, I'm new here, and the reason I registered is that when I install steam with wine and all that stuff (It's working) the STEAM FRIENDS INTERFACE is really disordered and the text looks destroyed and very, VERY hard to read.

Yes, I have tahoma installed.

Can anyone help me please? Btw, I'm running on Jaunty.

- MOVE THIS THREAD TO THE RIGHT SECTION IF THIS IS NOT THE ONE -

---

### Post by Mayan2012 on 2009-07-10
Bump

---

### Post by TalkHero on 2009-07-13
> **Mayan2012 said:**
> Hello, I'm new here, and the reason I registered is that when I install steam with wine and all that stuff (It's working) the STEAM FRIENDS INTERFACE is really disordered and the text looks destroyed and very, VERY hard to read.

Yes, I have tahoma installed.

Can anyone help me please? Btw, I'm running on Jaunty.

- MOVE THIS THREAD TO THE RIGHT SECTION IF THIS IS NOT THE ONE -

Have you installed the MS font pack?

```
sudo aptitude install msttcorefonts
```

That might help, it might not.

---

### Post by 8Kuula on 2009-07-13
If memory works, you need tahoma.ttf, marlett.ttf and Lucida Console fonts in your ~/.wine/drive_c/windows/fonts directory.

msttcorefonts package wont install fonts to your home directory, so need copy them to that same directory.

---

### Post by diggedy on 2009-07-14
Ive just fixed this myself. you need to install winetricks and then install all the corefonts, tahoma only fixes some of the ingame fonts.

---

### Post by nowhereman00 on 2009-07-15
well does anyone have the issue of steam closing inexplicably after it starts and if so a fix?

can has fix?

would really like a fix T_T

---

### Post by nowhereman00 on 2009-07-15
> **nowhereman00 said:**
> well does anyone have the issue of steam closing inexplicably after it starts and if so a fix?

can has fix?

would really like a fix T_T

nvm i fixed it installed corefonts under ubuntu and not just wine

---

### Post by Hgisle on 2009-07-27
> nvm i fixed it installed corefonts under ubuntu and not just wine 	

i got the same problem. But im new to ubuntu so i dont know how to do thins? got the newes version of corefonts:

sudo apt-get msttcorefonts.

is there anyting else i can do?:)

---

