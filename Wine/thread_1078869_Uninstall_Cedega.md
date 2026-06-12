---
title: "Uninstall Cedega?"
date: 2009-02-23
forum: Wine
---

### Post by Konsolkongen on 2009-02-23
Hey, i downloaded the Cedega demo yesterday and i don't wan't it anymore :) How do i remove it from my system?

Sorry if this has been asked before.

---

### Post by Firestem4 on 2009-02-23
please double check or someone else correct me on this before you do it. But I had downloaded the EVE Online version of cedega (obviously to run EVE) However I had to end up removing it because it wuoldn't work on my laptop. But cedega didn't remove.

What i ended up doing was after I found out using a nifty program called Filelight, i found where the cedega was. So I performed the following:

```
cd ~/Desktop/.cedega
sudo rm /.cedega -R 
```

FYI **rm** is Remove, so **be careful** with its use. (If you already know, I just wanted to state so you wouldn't make a mistake if you didn't). I believe the cedega files were written to desktop/.

---

### Post by Firestem4 on 2009-02-23
p.s. That does not completely remove all of Cedega, but it will remove atleast 95%. Some files are written to other locations in the HDD. I used Kleansweep to help me find a few of them.

---

### Post by Konsolkongen on 2009-02-24
Hey i removed the folder /home/konsolkongen/.cedega That is the one you where thinking of right? There is nothing in the Desktop folder.

Still the Cedega launcher is in my Games folder and when i run that Cedega starts but asks about account and password.

Maybe i should try Kleensweep?

---

### Post by Iukie on 2009-02-24
I too had difficulty with this. I went the hard way and rm'd the directories and then rm'd the files scattered all about. Ubuntu's search feature was actually pretty helpful here.

---

### Post by Konsolkongen on 2009-02-26
I forgot all about the search function already built into Ubuntu. I removed all files and directories that contained the name Cedega. Seems that solved my problem :)

---

### Post by ..::Ryan::.. on 2009-09-05
> **Konsolkongen said:**
> Hey, i downloaded the Cedega demo yesterday and i don't wan't it anymore :) How do i remove it from my system?

Sorry if this has been asked before.
Why not just
```
sudo apt-get remove cedega
```

---

### Post by RabidWeezle on 2009-09-06
on newer ubuntu builds (9.04) you can't even install cedega from deb since it requires a weird version of python. You have to manually install the tgz deb, just to find out it doesn't work that well and you are better off just using wine.

---

