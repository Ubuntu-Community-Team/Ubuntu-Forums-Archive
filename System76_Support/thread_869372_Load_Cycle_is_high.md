---
title: "Load Cycle is high"
date: 2008-07-24
forum: System76 Support
---

### Post by ajlewis2 on 2008-07-24
I have a Darter, I think it is a DARU1.  In early June I checked the load cycles and it came out to about 50 per day which I understand is good.  Since then I have upgraded to Hardy.  I'm not getting about 350 per day.  Any thoughts on why that would be and what I can do about it?

Thanks,
Anita

---

### Post by thomasaaron on 2008-07-25
Here's a bug report with a number of workaround options...

[http://wiki.ubuntu.com/DanielHahler/Bug59695](http://wiki.ubuntu.com/DanielHahler/Bug59695)


Here's what I did:
1. Create a text file with this in it...
```
#!/bin/sh
hdparm -B 254 /dev/sda #Or whatever your hard drive designation is
```

2. Save it as 99-fix-park.sh *on your Desktop*

3. Then run these commands one at a time:

chmod a+x ~/Desktop/99-fix-park.sh
sudo cp ~/Desktop/99-fix-park.sh /etc/acpi/resume.d
sudo cp ~/Desktop/99-fix-park.sh /etc/acpi/start.d
sudo reboot now

---

### Post by ajlewis2 on 2008-07-25
Thanks, Thomas.  I've done that.  I'll wait a couple days to see how it does.

Anita

---

### Post by ajlewis2 on 2008-07-27
Thomas, that worked for me.  It's giving me about 6 per day now.    Thanks.

Anita

---

