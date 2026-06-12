---
title: "Antivirus for Wine apps?"
date: 2010-04-07
forum: The Cafe
---

### Post by arnab_das on 2010-04-07
Well, since Wine is running all my windows programs which does sometimes connect to the internet to download patches and updates, i would like to know if there's a way to check programs in wine for presence of viruses (i hate to use that term! linux is such a peace of mind thing!)


any antivirus for wine apps?

---

### Post by Psumi on 2010-04-07
Use AVG Free Edition for Windows?

Seriously, use Windows antivirus on wine, it'll work. Oh and,

remove Z: drive that maps your entire filesystem for wine. Otherwise your antivirus may do some damage to your linux portion.

The Z: drive mapping / is only for the ease of use... removing it disallows wine to execute windows apps anywhere but .wine/drive_c

---

### Post by arnab_das on 2010-04-07
> **Psumi said:**
> Use AVG Free Edition for Windows?

Seriously, use Windows antivirus on wine, it'll work. Oh and,

remove Z: drive that maps your entire filesystem for wine. Otherwise your antivirus may do some damage to your linux portion.

The Z: drive mapping / is only for the ease of use... removing it disallows wine to execute windows apps anywhere but .wine/drive_c

thanks. :)

if i remove z mapping i wouldnt be able to open say a .exe file after i downloaded something right? i would have to move it to the Z: folder and then run it, isnt it?

btw avg has a 'live' thing right? where it would run in the system area. would that also work in linux?

---

### Post by Psumi on 2010-04-07
> **arnab_das said:**
> thanks. :)

if i remove z mapping i wouldnt be able to open say a .exe file after i downloaded something right? i would have to move it to the Z: folder and then run it, isnt it?

No, you have to move the exe into .wine/drive_c then run it there by using the wine command from terminal.

> btw avg has a 'live' thing right? where it would run in the system area. would that also work in linux?

Don't know if WINE forwards its systray to linux's systray.

---

### Post by tom66 on 2010-04-07
[http://www.linux.com/archive/feed/42031](http://www.linux.com/archive/feed/42031)

---

### Post by arnab_das on 2010-04-07
also one more question (bear with me), can a windows virus damage my linux filesystem? i use ext4, so i guess windows viruses wont be able to do any damage to it right?

@Psumi, do u use antivirus for wine apps?

---

### Post by Psumi on 2010-04-07
> **tom66 said:**
> [http://www.linux.com/archive/feed/42031](http://www.linux.com/archive/feed/42031)

Those are only a handful of hundreds of thousands of viruses/malware.

> **arnab_das said:**
> also one more question (bear with me), can a windows virus damage my linux filesystem? i use ext4, so i guess windows viruses wont be able to do any damage to it right?

Yes, they can, if granted appropriate access.

> @Psumi, do u use antivirus for wine apps?

No, I don't use wine at the moment. I don't use wine for IM programs or web browsers, so I'm safe pretty much.

---

### Post by Chronon on 2010-04-07
You could use ClamAV too.  Its main purpose is to detect Windows viruses.

---

### Post by J V on 2010-04-07
> **Psumi said:**
> No, you have to move the exe into .wine/drive_c then run it there by using the wine command from terminal.
Don't know if WINE forwards its systray to linux's systray.
You CAN run it from outside a wineprefix but you have to set the prefix first (I believe along the lines of env WINEPREFIX="dir/to/wine/prefix" wine "appname.exe")

I woulden't run a windows virus afk, just kill the wineserver when you're done with it, scan it occasionally with clam, and run the antivirus if you need something fixed. Windows AV is notorious for its bigger-than-a-bunch-of-gnome-logos footprint ;)

Btw, please post these things in the help forums people, I'm missing out on beans!

---

### Post by arnab_das on 2010-04-07
> **Chronon said:**
> You could use ClamAV too.  Its main purpose is to detect Windows viruses.

thanks for that. erm i have found this page: 

[http://www.clamav.net/lang/en/download/](http://www.clamav.net/lang/en/download/)

now which do i download? the linux one or the windows one? since i want to detect windows viruses mainly.

---

### Post by Chronon on 2010-04-07
It's in the repositories too.  You can get the Linux version.  Both of them scan for Windows viruses.

---

### Post by Hero of the Day on 2010-04-07
> **Chronon said:**
> It's in the repositories too. You can get the Linux version. Both of them scan for Windows viruses.
 
Are you serious? Since when? you are awesome, I read all your posts this morning.

---

### Post by J V on 2010-04-07
ClamAV comes in a windows version? :shock:

---

### Post by Psumi on 2010-04-07
> **J V said:**
> ClamAV comes in a windows version? :shock:

Yes, it has had a windows version for quite some time.

---

### Post by arnab_das on 2010-04-08
btw the one in the repos is outdated. one has to download the antivirus from the clamav site. however still not sure if this will indeed detect windows viruses.

---

### Post by Frogs Hair on 2010-04-08
I use Clam in a way that I don't store the virus data base on my computer . I open Clam, select virus browser and wait for the current definitions to download and than 
scan. Remember Clam doesn't provide real time protection and you will need to use AVG or Avast for that purpose. The Clam data base gives the names of the viruses
and exploits that it protects against.

---

### Post by Psumi on 2010-04-08
> **Frogs Hair said:**
> I use Clam in a way that I don't store the virus data base on my computer . I open Clam, select virus browser and wait for the current definitions to download and than 
scan. Remember Clam doesn't provide real time protection and you will need to use AVG or Avast for that purpose. The Clam data base gives the names of the viruses
and exploits that it protects against.

You'd have to use AVG's Windows version in wine though. The Linux version ([found here](http://free.avg.com/ww-en/download)) does not boast real-time protection.

---

### Post by dragos240 on 2010-04-08
Meh. I really don't think that it's too much of a problem on Linux. If you only use programs that you know aren't viruses, then it's not a problem.

---

