---
title: "GTA III &quot;Insert disk 2&quot; problem"
date: 2009-04-19
forum: Wine
---

### Post by cristian.palmas on 2009-04-19
Hi,

I successfully installed GTAIII on my laptop with Kubuntu 8.10 and Wine 1.1.17, installed via a [multiple wine versions installer]("http://ubuntuforums.org/showthread.php?t=942269").

The installation worked and the game ran smoothly after have modified the menu shortcut in order to make the 1.1.17 version of wine run.

After that I configured the application with winecfg and I patched the game to upgrade it to 1.1 version.

The problem is that, when I start the game it always ask to insert the disk 2 even if it is already inserted.
So I had to press "Esc" to exit the game and I noticed that the disk was unmounted.

Then I manually mounted the play disk (disk 2) by Dolphin and afterwards I ran the game. Same problem: "Please, insert disk 2".
I again exited the game and noticed that the disk was unmounted again.

So I thought that, for some reason, wine unmount the disk when the game starts. Is that possible? Did anybody have the same problem? Does anyone know the solution?
Thanks in advance.

Cristian Palmas

---

### Post by cogadh on 2009-04-19
Put the disk in, either let it automount or manually mount it, start winecfg then go to the drives tab, tell it to autodetect your drives, save the changes, then quit out of winecfg. Try running the game again and see what happens.

---

### Post by asdfoo on 2009-04-19
might be a copy protection issue also... in which case you'll need to use a crack

---

### Post by cogadh on 2009-04-20
A crack is not required for GTA 3 or Vice City (not sure about the others), their copy protection scheme is fully supported, provided Wine is configured correctly.

---

### Post by cristian.palmas on 2009-04-20
> **cogadh said:**
> A crack is not required for GTA 3 or Vice City (not sure about the others), their copy protection scheme is fully supported, provided Wine is configured correctly.

Hi,

does it means that it's all about a weak setting in winecfg?
Well I didn't take too much care about the config because I set the game to work as if on Win XP and that's it.

I didn't tweak anything else, such as drivers or hardware acceleration, leaving everything to the default settings.
Maybe you can provide some tweak to avoid the "insert disk" problem?
Thanks in advance.

Cristian Palmas

---

### Post by cogadh on 2009-04-21
I did, see my first post.

---

### Post by cristian.palmas on 2009-04-21
> **cogadh said:**
> I did, see my first post.

It works for me as you said above in your first post.

My combination is
- GTA III version 1.1 (patched)
- wine 1.1.17

It runs very slowly but it is a different problem from the one dealing with this thread and I read that someone has just wrote about it.

Thanks.

---

### Post by ornages on 2010-07-22
I have a similar problem so I decided to put it into this thread as well.
I am trying to install simcity 4 and I have the game on cd. During installation using wine the game asks me for cd2. now I have followed the instructions given in post 2, but the setup still keeps asking for cd2. For cd1 it was easy, I just right clicked on setup and launched it with wine.. but cd2 doesnt have a setup, its just needed to validate or read some files.. What should I do?

Also when I go to Drives tab in winecfg and I click on autodetect, I get one additional drive by doing so. But when I apply changes, close cfg and then open it again, the additional drive is gone.

//Edit: Solved! I had to unmount cd1, which still remained in file browser although I replaced it in my drive with cd2. After unmounting cd1, the setup continued!

---

