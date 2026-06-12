---
title: "Will Wubiever be able to do a normal install or a normal install for a Linux newbie?"
date: 2008-09-01
forum: Ubuntu Brainstorm
---

### Post by NonStop on 2008-09-01
Basically, will Wubi ever be able to fully install Ubuntu (not within Windows)?

Or, could there be an option at the installation section which says for Windows users?

The reason why I ask is because the UI in Wubi when installing for a Windows user/Linux newbie makes things a lot easier when installing to an already existing partition. I know there are guides out there, but that isn't the issue. I think that is something Ubuntu should really work on, having features that pull in Windows users, but are easy to use for them too (installing is one of the most important), because lets face it, that's the majority of the market.

PS I swear in the older version of the Wubi official site, it said it was in the planning stages, or somehting like that.

---

### Post by aysiu on 2008-09-02
How would this work, exactly?

If you don't want to install it within Windows, you *have* to know something about partitioning. Otherwise, there's too much of a risk of accidentally deleting or corrupting your Windows partition.

---

### Post by Oldsoldier2003 on 2008-09-02
> **aysiu said:**
> How would this work, exactly?

If you don't want to install it within Windows, you *have* to know something about partitioning. Otherwise, there's too much of a risk of accidentally deleting or corrupting your Windows partition.

IMHO wubi is just a gimmick for grabbing new users. At the risk of being called a grumpy oldtimer, I think its pretty useless and the hassles outweigh the benefits. Use a live cd to evaluate and test your hardware compatibility, then do a real install in a separate partition. In the end there is less work...

---

### Post by NonStop on 2008-09-02
I mean an installation guide with Windows language. For example, if I wanted to install to my partition that I have already made (E), it would use the drive letters like in Windows.

---

### Post by NonStop on 2008-09-03
Nope, no considers this important?

---

### Post by aysiu on 2008-09-03
> **NonStop said:**
> Nope, no considers this important?
The way it appears you've proposed it? No, not really.

---

### Post by olskar on 2008-09-03
What would perhaps be good is a way to transform your wubi-installation into a real installation, I think I read somewhere that this was being worked upon?

Then again I think its easier to simply reinstall if you are tired with wubi..

---

### Post by NonStop on 2008-09-04
> **olskar said:**
> What would perhaps be good is a way to transform your wubi-installation into a real installation, I think I read somewhere that this was being worked upon?

Then again I think its easier to simply reinstall if you are tired with wubi..

That is what I mean. Sorry if I have not done a good job explaining myself, but that's what I mean, a real installation through Wubi, which is easy for a Windows user. 

Do you see what I mean aysiu?

---

### Post by mc4100 on 2008-09-04
> **NonStop said:**
> That is what I mean. Sorry if I have not done a good job explaining myself, but that's what I mean, a real installation through Wubi, which is easy for a Windows user. 

Do you see what I mean aysiu?

Do you mean installing Ubuntu as though the installer from the LiveCD was running, not from a "Live" Ubuntu system which has boot from a CD, but from inside windows itself -- like the typical installation of a program: only this one isn't copied to Directory, but to a Partition?

---

### Post by NonStop on 2008-09-05
> **mc4100 said:**
> Do you mean installing Ubuntu as though the installer from the LiveCD was running, not from a "Live" Ubuntu system which has boot from a CD, but from inside windows itself -- like the typical installation of a program: only this one isn't copied to Directory, but to a Partition?

No, just a normal install, but with an installation like Wubi; using Windows language.

---

### Post by mc4100 on 2008-09-05
> **NonStop said:**
> No, just a normal install, but with an installation like Wubi; using Windows language.
OK, I think I get it (should have read the first post better)...
You mean having the Ubuntu "installer", which *is* running in an Live Ubuntu system that has boot from CD, look more like the Wubi UI (which is more suitable for windows users).

---

### Post by aysiu on 2008-09-05
This won't fly. Windows users aren't the only ones who install Ubuntu.

---

### Post by NonStop on 2008-09-07
Basically an install option for Windows users,in windows language.

Why wouldn't it fly aysiu? It would be only an option, like a normal install, but a button for a normal install for Windows users.

---

### Post by Merk42 on 2008-09-07
> **NonStop said:**
> Basically an install option for Windows users,in windows language.

Why wouldn't it fly aysiu? It would be only an option, like a normal install, but a button for a normal install for Windows users.

Because then you're adding another button.  When the idea of the installer is to make it as simple as possible.  Ideally make it do everything by itself once you click install (unless you chose advanced).

---

### Post by kdorf on 2008-09-07
> **NonStop said:**
> Basically an install option for Windows users,in windows language.

Why wouldn't it fly aysiu? It would be only an option, like a normal install, but a button for a normal install for Windows users.

It won't fly because Linux is not Windows. If you want "Windows language" stick to Windows. That's all there is to it.

If I'm understanding you right, you want to be able to do something like install Linux to your E: drive(/partition).

Linux doesn't use drive letters, and it doesn't natively install to FAT32 or NTFS and it thus would not make sense to install that way.

The lesson here is that Linux is not Windows, and you should not expect it to act as such.

---

### Post by NonStop on 2008-09-08
> **kdorf said:**
> It won't fly because Linux is not Windows. If you want "Windows language" stick to Windows. That's all there is to it.

If I'm understanding you right, you want to be able to do something like install Linux to your E: drive(/partition).

Linux doesn't use drive letters, and it doesn't natively install to FAT32 or NTFS and it thus would not make sense to install that way.

The lesson here is that Linux is not Windows, and you should not expect it to act as such.

I'm not saying you should. But having say, drive letters underneath how Linux describes it would make things a lot, lot easier.

---

### Post by inportb on 2008-09-09
Of course, keep in mind that partitions that are not mounted in Windows do not receive drive letters. This includes partitions that cannot be mounted, such as Ext3 and empty space. And since the user can change drive letters, the best way would be to query the Windows setup for them.

So this leaves a few problems.
1) If it's NTFS/FAT, it gets a drive letter, so it could be presented as such, but it needs to be (should be) re-initialized with a different filesystem.
2) When a filesystem is reinitialized, it becomes a different partition, so its drive letter does not have to stay the same. Widows does not "know" abut the change, and so cannot assign a drive letter.
3) People going back for a reinstall would have no way to map a non-Windows partition to a Windows drive letter.
4) If these people depended on the drive-letter mapping the first time around, they'd be thoroughly disoriented when they encounter an interface that does _not_ present drive letters.

---

### Post by NonStop on 2008-09-12
> **inportb said:**
> Of course, keep in mind that partitions that are not mounted in Windows do not receive drive letters. This includes partitions that cannot be mounted, such as Ext3 and empty space. And since the user can change drive letters, the best way would be to query the Windows setup for them.

So this leaves a few problems.
1) If it's NTFS/FAT, it gets a drive letter, so it could be presented as such, but it needs to be (should be) re-initialized with a different filesystem.
2) When a filesystem is reinitialized, it becomes a different partition, so its drive letter does not have to stay the same. Widows does not "know" abut the change, and so cannot assign a drive letter.
3) People going back for a reinstall would have no way to map a non-Windows partition to a Windows drive letter.
4) If these people depended on the drive-letter mapping the first time around, they'd be thoroughly disoriented when they encounter an interface that does _not_ present drive letters.

Unfortunately, I'm not as tech-savvy as you, but could these problems be fixed?

---

