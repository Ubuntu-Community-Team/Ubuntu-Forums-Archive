---
title: "Auto run tasks on system start with rc.local not working"
date: 2011-03-30
forum: Server Platforms
---

### Post by monsterkiller on 2011-03-30
Hello.

I am currently running a VPS with Ubuntu Server 10.10. I have been trying for a few days now to get some programs to run when the system starts, but with no luck. I am trying to use rc.local to do this, there is an:
/etc/init.d/rc.local - [http://paste.monsterprojects.org/mpbjhwhbjzhbjrr](http://paste.monsterprojects.org/mpbjhwhbjzhbjrr) (Was already on the system, I have not edited this)
and:
/etc/rc.local - [http://paste.monsterprojects.org/mpbjhwhbkkkhwez](http://paste.monsterprojects.org/mpbjhwhbkkkhwez)

If i run the /etc/rc.local script manually all the programs start fine, and if i run /etc/init.d/rc.local start, all the programs start fine. But for some reason they just don't seem to be starting when the system boots. If anyone can help i will be much appreciative. 

Thanks.

---

### Post by BkkBonanza on 2011-03-30
Those programs you put in /etc/rc.local already have their own init scripts. You don't need to, and shouldn't, start them via rc.local.

They should have been configured for autostart with the default install. Nowadays this usually uses the new Upstart system rather than the older SysV init.d system (though the two methods are still present, the older init.d now redirects into Upstart).

It would seem that some changes have been made to default and normal behavior and I expect whatever was done is now preventing /etc/rc.local from running. The new mode Upstart init configs are in /etc/init. The correct way to enable/disable autostart in the older system was using update-rc.d (see man page). I don't know whether that tool still works and has been patched to support Upstart though.

You may want to read through the [Ubuntu Bootup HowTo]("https://help.ubuntu.com/community/UbuntuBootupHowto").

---

### Post by monsterkiller on 2011-03-31
Thank you [[COLOR=#d40000]**BkkBonanza**[/COLOR]]("http://ubuntuforums.org/member.php?u=550406"). I will look into this.

---

### Post by monsterkiller on 2011-03-31
I tried it and it works perfectly. Thank you so much, have been trying to do this for days and day now.

---

