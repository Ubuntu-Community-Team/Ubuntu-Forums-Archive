---
title: "[SOLVED] Mounted USB-&amp;amp;amp;gt;MicroSD adapter won't let me write anything."
date: 2008-09-30
forum: Security
---

### Post by amishphysicist on 2008-09-30
Heya,

I'm trying to be able to copy files over to a USB->microSD adapter.  I've finally got the thing mounting fine thanks to the fellers over in  
[this original Thread]("http://ubuntuforums.org/showthread.php?t=934563"), but can't seem to actually write anything to the disk.

I can ls and chmod without any errors, but touching or copying a file to the mounted dir isn't happening:

```

sudo mount /dev/sdb1 ~/usbdrive
:~/usbdrive/$ touch sadf
touch: cannot touch `sadf': Permission denied
```

Any ideas?

thanks!

---

### Post by cariboo on 2008-09-30
Use:

```
sudo touch sadf
```

You have a permission issue with your device. Try

```
sudo chmod 777 ~/usbdrive
```

Even though the drive is mounted in your home directory, by using sudo to mount the drive root owns it.

Jim

---

### Post by cdenley on 2008-10-01
```

man mount

```
Look at the uid and gid options in the "fat" section. When you mount as root, it defaults to root's uid, and uses the default umask of 022, which wouldn't allow non-root users to write anything.

---

### Post by amishphysicist on 2008-10-02
> **cdenley said:**
> ```

man mount

```
Look at the uid and gid options in the "fat" section. When you mount as root, it defaults to root's uid, and uses the default umask of 022, which wouldn't allow non-root users to write anything.

Man pages read like stereo instructions. :/

---

### Post by amishphysicist on 2008-10-02
Well, it magically started being recognized by my system today, so I guess that's good.  Still not sure why it was barfin gin the first place.  Automount wins!

---

### Post by cdenley on 2008-10-02
> **amishphysicist said:**
> Man pages read like stereo instructions. :/

I never tried reading stereo instructions, but I find many such as "man mount" to be an excellent reference. It simply explains every single option available for the command.

---

### Post by amishphysicist on 2008-10-27
Hey all,

Same issue as before, but with a different drive.  It's still not clear how I can mount a drive with sudo, and then give permissions for all users.   

I tired this, but evidently it doesn't share the way I think it should: 
sudo mount --make-rshared /home/mountdir

chmod/own don't seem to work either.  Is there an arg to pass to mount to make the drive read/writable for all users?

Just to be absolutely clear, here is what I'm doing to mount, currently:

```

sudo mount -t vfat /dev/sdb1 ~/mountee
sudo mount --make-shared /home/nlieby/mountee/
sudo chmod -R a+w /home/nlieby/mountee/

```

thanks!

-nate

---

### Post by cdenley on 2008-10-27
> **amishphysicist said:**
> Hey all,

Same issue as before, but with a different drive.  It's still not clear how I can mount a drive with sudo, and then give permissions for all users.   

I tired this, but evidently it doesn't share the way I think it should: 
sudo mount --make-rshared /home/mountdir

chmod/own don't seem to work either.  Is there an arg to pass to mount to make the drive read/writable for all users?

Just to be absolutely clear, here is what I'm doing to mount, currently:

```

sudo mount -t vfat /dev/sdb1 ~/mountee
sudo mount --make-shared /home/nlieby/mountee/
sudo chmod -R a+w /home/nlieby/mountee/

```

thanks!

-nate

```

sudo mount -t vfat -o umask=000 /dev/sdb1 ~/mountee

```

---

### Post by 080801jk on 2008-10-30
&#22768;&#35759;&#30005;&#35805;&#24405;&#38899;&#31995;&#32479;&#21151;&#33021;: 1.&#22768;&#35759;&#30005;&#35805;&#24405;&#38899;&#22312;&#32447;&#24405;&#38899;&#30417;&#35270;&#21151;&#33021;&#65306; [**&#30005;&#35805;&#24405;&#38899;&#35774;&#22791;**](http://www.googlejk.cn/dhlysb.htm)&#19968;&#26086;&#29992;&#25143;&#24320;&#22987;&#36890;&#35805;&#65292;&#31995;&#32479;&#33258;&#21160;&#21551;&#21160;&#22768;&#35759;&#30005;&#35805;&#24405;&#38899;&#21151;&#33021;&#65292;[**&#25968;&#30721;&#24405;&#38899;&#30005;&#35805;**](http://www.googlejk.cn/smlydh.htm)&#26174;&#31034;&#35813;&#36890;&#36947;&#30340;&#21462;&#26426;&#26102;&#38388;&#12289;[**&#30005;&#35805;&#35821;&#38899;&#21345;**](http://www.googlejk.cn/dhyyk.htm)&#25346;&#26426;&#26102;&#38388;&#31561;&#20449;&#24687;&#12290;&#36890;&#35805;&#32467;&#26463;&#21518;&#65292;[**&#30005;&#35805;&#24405;&#38899;&#31995;&#32479;**](http://www.googlejk.cn/dhlyxt.htm)&#31995;&#32479;&#33258;&#21160;&#23558;&#24405;&#38899;&#20869;&#23481;&#21450;&#26085;&#26399;&#26102;&#38388;&#23384;&#20837;&#30828;&#30424;&#30456;&#24212;&#30340;&#36335;&#24452;&#65292;&#20197;&#22791;&#26597;&#35810;&#12290; 2.&#22768;&#35759;&#30005;&#35805;&#24405;&#38899;&#35821;&#38899;&#36164;&#26009;&#26597;&#35810;&#21151;&#33021;/&#25773;&#25918;&#21151;&#33021;&#65306;&#31995;&#32479;&#25805;&#20316;&#21592;&#21487;&#26681;&#25454;&#38656;&#35201;&#65292;&#38543;&#26102;&#26597;&#35810;&#24405;&#38899;&#20869;&#23481;&#12290;&#31995;&#32479;&#21487;&#20197;&#25353;&#26085;&#26399;&#12289;&#36890;&#36947;&#12289;&#26102;&#38388;&#32034;&#24341;&#65292;[**&#21628;&#21483;&#20013;&#24515;**](http://www.googlejk.cn/hjzx.htm)&#24182;&#21487;&#21306;&#20998;&#20027;&#21483;&#26041;&#12289;&#34987;&#21483;&#26041;&#12290;&#23545;&#38656;&#35201;&#30340;&#20869;&#23481;&#21487;&#20197;&#25773;&#25918;&#30417;&#21548;&#65292;&#23545;&#26080;&#20445;&#23384;&#20215;&#20540;&#30340;&#24405;&#38899;&#20869;&#23481;&#21487;&#20197;&#36827;&#34892;&#21024;&#38500;

---

