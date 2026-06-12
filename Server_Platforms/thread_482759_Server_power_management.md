---
title: "Server power management"
date: 2007-06-24
forum: Server Platforms
---

### Post by Moonshine on 2007-06-24
I've got an Xubuntu File/Print server....

What I'd like to do is let the disks spin down after a certain period of inactivity....and possibly put it into a suspend/sleep type of mode if it could 'wake up' again when its needed.

I can't find any settings to achieve this.

I searched the forums, and my needs are similar to these, however this did not get a response.

Thanks!
> 
I also need to setup power management options as the server is allways running and doing nothing. I was thinking of getting the hdd's to spin down after a certain time, and using cool + quiet ( i have a AM2 X2) to slow down the cpu and fan. I might actually set it up to go into standby if it is robust, i.e. it WILL come on when needed for printing or accessing or FTP or web access (im guessing the latter will need it to allways be on).

---

### Post by Moonshine on 2007-06-26
I've continued my search but have been unable to find any more information....:(

---

### Post by Cache22 on 2007-06-27
Hey Moonshine,

I don't have any information about suspend or sleep mode for the whole system, but for the hard drives check out hdparm. There is some info here: [http://ubuntuforums.org/showthread.php?t=16360](http://ubuntuforums.org/showthread.php?t=16360) or just search around for **hdparm **... don't change any settings until you know what they do, but for a quick start look at the *spindown_time* setting in */etc/hdparm.conf*. There are a lot of settings, but in my case everything is ok with the defaults and I just wanted to specify the spindown time, here is a portion of my current hdparm.conf file:

```
/dev/sdd {
        spindown_time = 120
}
/dev/sde {
        spindown_time = 120
}
/dev/sdf {
        spindown_time = 120
}

```

You can also run hdparm from the command line to test various settings, the command line equivalent of the above for /dev/sdd is:

```
hdparm -S 120 /dev/sdd
```

The number (120 in this case) is a count of 5 second intervals, so I have the drive set to spin down after 10 minutes of being idle.

Hope that helped ... I'm not an expert on the subject, but those settings in /etc/hdparm.conf have worked well for me. The default conf file has a lot of comments, and you can also use "*info hdparm.conf*" and "*info hdparm*" to get info on the various options and command line switches.

Ben

---

