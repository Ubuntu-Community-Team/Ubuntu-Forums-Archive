---
title: "How to assign read-only permission on Mass storage and CD-ROM"
date: 2010-01-07
forum: Security
---

### Post by pravindra.kumar on 2010-01-07
Dear All,
I have Ubuntu9.10 installed in my laptop, and I want to give read-only permission on mass storage device (USB flash & external HD) & CD-ROM.
please guide me how this is possible. It should be automatically.

It's necessary for security purpose.

Thanks !!!!

---

### Post by BkkBonanza on 2010-01-07
For cdrom there is no need as it's already read only.
For usb do a search here because I already answered this in a post about a week or two ago. It's easy to do manually but more involved for auto-mounting read only.

See last post here,
[http://ubuntuforums.org/showthread.php?t=1355737&highlight=usb+read](http://ubuntuforums.org/showthread.php?t=1355737&highlight=usb+read)

---

### Post by pravindra.kumar on 2010-01-08
Dear BkkBonaza,
you told in your thread that "create the needed script: /usr/local/bin/remounter and chmod +x as well.

**please guide how can create script for chmod +x.**

i don not have more knowledge about creating scripts.

thanks

---

### Post by BkkBonanza on 2010-01-08
You would use an editor like nano (or even gedit) to edit the file and paste the script into the file and save it.

Then you would use the chmod command or Nautilus properties to change the permissions of the file.

In Nautlius right click the file and choose Properties. Then select the Permissions tab and click the check mark for "Allow executing as a program". 

OR, in terminal,

sudo chmod +x /usr/local/bin/remounter

Actually, due to permission issues you're probably best doing it in terminal not nautilus. Likewise you should change the file ownership to root as well otherwise users can mess with it and bypass your restrictions.

sudo chown root:root /usr/local/bin/remounter

---

### Post by pravindra.kumar on 2010-01-08
Dear BkkBonaza,
Thanks a lot for USB it's fine and working.

but how can be applied on CD-RW/DVD-RW.

Thanks again for kind support.

---

### Post by BkkBonanza on 2010-01-08
You can add another line in the rule file to handle devices that match the cd-rw/dvd-rw names. I don't know off hand what they get named. I guess cdrom[0..9] because that's how mine gets mounted and it's likely the same. So the new rule could be,

KERNEL=="cdrom[0..9]", ACTION=="add", RUN+="/usr/local/bin/remounter /dev/%k"

I'm not actually sure this would work. Maybe cd writing software bypasses the normal mounting options but I haven't looked into that. Anyway, this is something you can try and see if it works.

Remember, when you change udev rules you need to reload them with,
sudo udevadm control --reload-rules

---

