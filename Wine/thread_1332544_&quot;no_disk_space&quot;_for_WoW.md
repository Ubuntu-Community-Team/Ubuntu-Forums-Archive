---
title: "&quot;no disk space&quot; for WoW"
date: 2009-11-20
forum: Wine
---

### Post by id10twork on 2009-11-20
I got the first part installed, now I am trying to download The Burning Crusades and I am getting an error that I have 0 disk space available (which is not true); is this a common error? Can someone please tell me how to fix this?

---

### Post by Xog on 2009-11-20
You upgraded from jaunty, i've seen several posts on the issue. I'll browse around for you and see if I can find a fix. I know there's one on here somewhere..

edit:
This may or may not work, but if there's files that aren't needed anymore it'll get rid of them (like outdated programs & packages you have installed updates for already)
```
sudo apt-get clean
sudo apt-get autoremove
```

-- 
I'd also like you to run this command and tell me your results,

```
# df -h
```

---

### Post by id10twork on 2009-11-20
thanks, I ran the cleanup and I'll try again. When I typed in that last command I got nothing, it just went to the next line.

Update to this... It still tells me I have 0 space

---

### Post by beastrace91 on 2009-11-20
You should check out [this thread](http://ubuntuforums.org/showthread.php?t=1330927). It lists a fix for the issue you are having.

Cheers,
~Jeff

---

### Post by id10twork on 2009-11-20
> **beastrace91 said:**
> You should check out [this thread](http://ubuntuforums.org/showthread.php?t=1330927). It lists a fix for the issue you are having.

Cheers,
~Jeff

Thanks, but that does not have my problem listed.

---

### Post by Xog on 2009-11-20
can you copy and paste the error you're receiving, it's easier for us to identify a problem with the exact words of the error.

1. I said earlier to run
```
# df -h
```
my mistake, don't include the "#"

2. Empty your trash.

3. Do you have another OS installed?

4. How large is your hard drive, and how much does it actually say is free & used?

---

### Post by id10twork on 2009-11-20
> **Xog said:**
> can you copy and paste the error you're receiving, it's easier for us to identify a problem with the exact words of the error.

1. I said earlier to run
```
# df -h
```
my mistake, don't include the "#"

2. Empty your trash.

3. Do you have another OS installed?

4. How large is your hard drive, and how much does it actually say is free & used?
I don't know how to check what is free. The size is 120g.

---

### Post by Xog on 2009-11-20
> **id10twork said:**
> I don't know how to check what is free. The size is 120g.

You check what is free by typing this in terminal:
```

df -h

```

---

### Post by id10twork on 2009-11-20
> **Xog said:**
> You check what is free by typing this in terminal:
```

df -h

```
O I'm sorry I didn't know that's what that did. Give me a few hours, I'll go home and try it and report back.

---

### Post by Xog on 2009-11-20
> **id10twork said:**
> O I'm sorry I didn't know that's what that did. Give me a few hours, I'll go home and try it and report back.

I won't be home for another 10 hours or so, it's friday night and I'm going out with the wife. Here's what to do:

1. if your available disk space is small, then you need to get another hard drive or delete files you don't use or need. With updates from WoW, you're goung to need about 18 GB of free space.

That's about 15% of your hard drive.

2. if your available disk space has sufficient space to install world of warcraft (it states 10GB or more for original install) then you have another problem that needs to be addressed.

The problem if you reach 2 is, your computer has enough space to install a program but it is stating you do not have enough space. This needs to be edited in to your original post if it occurs and someone else will have to help you out.

A way you can determine if #2 is the problem is by pasting the results of both of these commands:

```
df /home
```
```
df -h
```

An experienced user will understand the problem and be able to help you out when they see these two results.

---

### Post by id10twork on 2009-11-20
thank you. understood. have a good time tonight.

---

### Post by beastrace91 on 2009-11-20
You can also easily check your used disc space by installing gparted ```
sudo apt-get install gparted
``` And then accessing it from **System->Administration->Partition  Editor**

The issue in the above linked to thread I was referring to is the "permissions" error for your WoW folder - check to see if there is a lock icon on the folder (meaning your default user cannot write to it) which can in some cases cause a Wine program to read as 0 space left because it does not understand Unix file system permissions. I'd be willing to bet this is your issue if you indeed have enough space to install the game in your **~/.wine** folder.

Regards,
~Jeff

---

### Post by Xog on 2009-11-20
> **beastrace91 said:**
> You can also easily check your used disc space by installing gparted ```
sudo apt-get install gparted
``` And then accessing it from **System->Administration->Partition  Editor**

The issue in the above linked to thread I was referring to is the "permissions" error for your WoW folder - check to see if there is a lock icon on the folder (meaning your default user cannot write to it) which can in some cases cause a Wine program to read as 0 space left because it does not understand Unix file system permissions. I'd be willing to bet this is your issue if you indeed have enough space to install the game in your **~/.wine** folder.

Regards,
~Jeff


I specifically told him to do this in his other thread,
[http://ubuntuforums.org/showpost.php?p=8354268&postcount=62](http://ubuntuforums.org/showpost.php?p=8354268&postcount=62)

It's possible he wasn't listening ;)

---

### Post by id10twork on 2009-11-20
thanks guys. If any of you posted anything on my other threads I didn't see it. I'm using my phone more than half the time. I'll try your suggestions when I can and report back.

---

### Post by Alatar1 on 2009-11-21
Thing is, you are more than likely having one of the issues i listed, it's probably telling you that you don't have space because you dont have permission...

---

