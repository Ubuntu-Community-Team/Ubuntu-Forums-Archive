---
title: "Magic Dvd Copier dvd not seen in ubuntu"
date: 2011-01-07
forum: Wine
---

### Post by electroken on 2011-01-07
I have a legal copy of Magic Dvd Copier which will run under windows xp and I want to run it under Ubuntu/wine.
I managed to install the program and put in the registration codes ok etc and the program said it was running ok. 
When I copied in my dvd it made a copy of it as normal but then could not burn the copy to a new dvd. It will not see any dvd or burner on my computer. The program reports an error: DDE failure

This is not an ordinary dvd copier program but one which will convert a video_rm to a video_ts which is the normal format for a video disk. If you use a standalone burner to copy tv programs such as TCM or any of the movie channels you will find that the burner will only make you a vr mode dvd and not the normal dvd video. You will find further that it is impossible to make a copy of that disk by any other means other than Magic Dvd Copier, as far as I know.

So I need this to make copies of my vr mode videos. The program does not see the dvd drive on the computer although I am easily able to burn a dvd using brasero.

---

### Post by electroken on 2011-01-14
I guess I am not getting much help with this issue. It may not apply ONLY to using this program but maybe to almost any other Microsoft program which would need a driver for the MS program to be able to see the dvd drive. I would also expect this to be somewhat a problem if you were trying to use an MS program such as Nero.

---

### Post by cogadh on 2011-01-14
Did you configure the DVD drive in Wine? By default, I believe all CD/DVD drives are simply defined as CD drives unless you configure them otherwise.

---

### Post by electroken on 2011-01-15
I think that I did do that but not sure I did it all correctly. The drive does show up in the configuration folder, but I am not certain it is really working ok. 
I am sure that Magic Dvd Copier does not see a drive which is a burner but it can see the disk I put in the drive to try to make the copy. In other words it can seem to write the disk to a folder but not be able to copy it out to another disk as a video disk. It simply will not see a drive I can use to write the files. I know I have had this same kind of issue with a regular windows machine but it was due mainly to trouble with some kind of virus or nero making my drive useless for copying since it had probable confirmed I was using an invalid copy of the nero program. etc
It acts like wine is not seeing the correct drivers for the dvd burner or needs codecs or some other thing. Similar to when I see the yellow question mark in the device driver menu in windows. I think I need to put in a better driver so wine can work but I am not certain how to do it. 
It is sooo bad to be a newbie!

---

### Post by electroken on 2011-03-01
You do state that the drive shows up in the Wine configuration as a cd rom and as you say: "By default, I believe all CD/DVD drives are simply defined as CD drives unless you configure them otherwise"
so how do I configure it otherwise to make this all work?
I think I will first try to install nero in Wine to see if it will do the job

---

### Post by Automat2 on 2012-03-16
> **electroken said:**
> You do state that the drive shows up in the Wine configuration as a cd rom and as you say: "By default, I believe all CD/DVD drives are simply defined as CD drives unless you configure them otherwise"
so how do I configure it otherwise to make this all work?
I think I will first try to install nero in Wine to see if it will do the job

In my case, I had to map my CD/DVD drives to be *seen *and mounted by Wine. They mounted well on Ubuntu though, but Wine never mounted them until I found this solution in the forums, that basically maps the drives on Wine.

Open a terminal and type:
```
ln -s /mnt/cdrom ~/.wine/dosdevices/d: 
ln -s /mnt/cdrom1 ~/.wine/dosdevices/e:
```I have two drives, so one code and letter for each.

However, I don't think that this is your problem. To be honest, since I started using Ubuntu, I have never burnt any DVD using a Windows native app but Linux, not even Nerolinux. I found these quite complicated to use and lacked of features.

Having used Nero in Windows before, I thought that Nerolinux fell very short of being the poor Cinderella of Nero. Since there are native Linux apps like Brasero (Deb) and k3B and K9 (KDE), who needs any other?

---

### Post by DGINSD on 2012-11-17
I solved my issues with wine recognizing cd drives by listing them in the /etc/stab file and then mapping them in wine. I added this line to my fstab file, but your may vary.
```
# built in CDrom
/dev/sr0	/media/cdrom/	auto	ro,noauto,user,exec	0 0

```

then in a terminal do

```
sudo mount -a
```

then in the configure wine application select the drives tab and click the auto configure button.

[IMG]http://s19.postimage.org/ht93hdjdf/winecfg_drives.png[/IMG]

---

