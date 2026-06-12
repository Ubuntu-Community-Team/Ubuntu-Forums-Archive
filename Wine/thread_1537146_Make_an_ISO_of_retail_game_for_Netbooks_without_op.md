---
title: "Make an ISO of retail game for Netbooks without optical drive?"
date: 2010-07-23
forum: Wine
---

### Post by Nick_Jinn on 2010-07-23
I am talking about legally owned ISOs from retail copies that you own....I know you can download games from steam for netbooks, but once I buy a game for console and PC I feel stupid buying it a third time also for PC. I think I am entitled to make a backup for myself, which is legal.

       So how do you do it? Steps to creating the ISO? 

       Lets say you have the ISO. How do you mount the ISO and get it to play as if you had the disk in there, assuming you dont have an optical drive for your netbook or you are using your optical drive for a live session.

---

### Post by mdramige on 2010-07-23
I'm assuming you have another PC with a dvd/cd drive to make the ISO. Brasero, the default Ubuntu burner program, will make an ISO for you. Just choose "Disc copy" on the main menu and burn the disc to ISO.

On your netbook, follow the instructions at [http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html) to mount the ISO.

---

### Post by Nick_Jinn on 2010-07-23
Will that work for copyright protected games?

---

### Post by mdramige on 2010-07-23
Ah, good point. I think these are the wrong forums for talking about circumventing copy protection, however stupid it is.

---

### Post by Grenage on 2010-07-23
For a simple ISO mount:

```
sudo mount mygame.iso /media/iso -t iso9660 -o loop
```

---

### Post by Nick_Jinn on 2010-07-23
> **mdramige said:**
> Ah, good point. I think these are the wrong forums for talking about circumventing copy protection, however stupid it is.


I am talking only about legal backups in ISO format, not trying to  skirt the law.....in this case I must have bought the game 4 times already.....twice for PC, oce for 360 and once as a gift. I am not going to buy it again from steam. People are allowed to make backups according to the law, though developers are free to make this difficult it is not illegal as long as you purchased a valid copy at some point.

Now if you got the ISO from a place other than your own disk then it might be illegal even if you originally owned it.



I am talking about legally finding a way to play my games on a netbook though.

---

### Post by cogadh on 2010-07-23
However, because of the screwed up laws currently covering copy protection (in many countries), the act of circumventing the copy protection in order to make and use your perfectly legal copy is actually illegal. So in order to do something completely legal, you have to break the law. Not to mention, this is public forum, its not like whatever you get told about copying your games can't be used by someone else to do something criminally illegal. Lets not even get into the fact that many games have single instance licenses, meaning you can make a legal backup, but you can still only use the game on a single machine, so you technically can't install it on your netbook if you already have it installed somewhere else. There are way too many legal ambiguities here, hence the discussion of such things is not allowed on these forums, for both your protection and the protection of the forum owners. Best to not push the issue; you have already been told how to create and mount the ISO, that should be enough to get you going, Google can take you the rest of the way.

---

### Post by Nick_Jinn on 2010-07-23
Sorry. Ill ask about it elsewhere. If anyone wants to help me out then maybe PM me instead.

---

### Post by asdfoo on 2010-07-23
your thread has nothing to do with wine.

---

### Post by Nick_Jinn on 2010-07-23
It might. Fallout 3 only plays in wine, which is the game I wanted to mount from ISO. I would be executing the game with WINE.

---

