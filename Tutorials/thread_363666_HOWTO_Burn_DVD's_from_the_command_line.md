---
title: "HOWTO: Burn DVD's from the command line"
date: 2007-02-17
forum: Tutorials
---

### Post by GrammatonCleric on 2007-02-17
Why would you do this?  Say like me you have a server that you have remote ssh access to.  Or you do not want to install GUI on a system but have need to burn a DVD backup.

_**Step 1: Install dvd+rw-tools**_

```

   
sudo apt-get install dvd+rw-tools


```[U][B]

Step 2: To find where your DVD Burner is [/B][/U]

```

less /etc/fstab

```Look for a line that is simular to:

```

/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0

```[U][B]

Step 3: Buring your DVD.[/B][/U]

_*Burning a content of a directory:*_

```
    
growisofs -dvd-compat -input-charset=ISO-8859-1 -Z /dev/hdd -R -J -pad "/path/to/some/data"

``` If you are unsure of the charter set leave blank and your default system charter set will be used.

When finished eject the DVD by issuing the command:

```
    
eject

```[U][I]
Burning data from multiple directories:[/I][/U]

Ok now if you want to burn data from directories /path/to/foo and /path/to/chu (given you have enough space on the DVD for it) and you want to put the data into directories "foo"  and "chu" on the DVD.

```

growisofs -dvd-compat -input-charset=ISO-8859-1 -Z /dev/hdd -R -J -pad -graft-points "/foo=/path/to/foo" "/chu=/path/to/chu"

```_*Burning to DVD-RW:*_

If you are using a DVD-RW, you need to format your DVD-RW before you can burn to it. 

```
    
dvd+rw-format -force /dev/hdd

```Now you are ready to burn to your DVD-RW.
  
_*Appending Data to DVD-RW:*_

If you would like to add data to your DVD-RW from a previous burn you can append data by using the -M switch:

```

growisofs -dvd-compat -input-charset=ISO-8859-1 -M /dev/hdd -R -J -pad -graft-points "/foo=/path/to/additonal/data"

```_*Burning an iso:*_

If you used "dd" to created an ISO or made a backup of another DVD you've created.  To burn that ISO use the following command.

```

growisofs -dvd-compat -Z /dev/hdd**=**/path/to/image.iso

```


-GC

---

### Post by duister on 2008-05-04
Thanks man. Was usefull to me.

---

### Post by swordphsh on 2008-07-18
EDIT: nevermind, dvd-compat option does it



Question: In nero for windows, it gives an option for book-type which is usually set to automatic. Then when burning starts, it says "settingn book type to dvd-rom."

Is there a way to set this in Linux?

I tried using the DVD+RW-booktype tool, but I keep getting an error that my drive is not supported. My drive should be supported (it's a Lite-on) and nero will set this bit at the time of burning regardless of the drive type.

---

### Post by GeekPapa on 2010-02-02
Nice job.  Simple and a great reference for people who are memory challenged like me.  My wife needed something burned when I was out of town.  I had her put the disc into my server and I burned it remotely.  Much appreciate your post!

---

### Post by mankand007 on 2012-02-04
Thanks a lot!

---

### Post by ramsforums on 2012-06-14
thanks good tutorial

---

