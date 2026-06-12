---
title: "Ubuntu 12.04 client to OS X 10.6 OpenDirectory"
date: 2012-04-11
forum: Server Platforms
---

### Post by newbie-user on 2012-04-11
I'm having trouble getting an Ubuntu 12.04 client to authenticate against OpenDirectory hosted on a 10.6 OS X server. I've followed the instructions at [http://techblog.glendaleacademy.org/?p=7](http://techblog.glendaleacademy.org/?p=7) and [http://techblog.glendaleacademy.org/?p=27](http://techblog.glendaleacademy.org/?p=27) and it worked well for 10.04 and 11.10. However, 12.04 doesn't seem to work if I follow those same instructions. 

Log files on the OS X server indicate that the user has successfully authenticated but the Ubuntu client auth.log gives this message:

lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=user

I can su as the user in the terminal, but can't log in as the user in the GUI. The screen just goes black and stays that way.

Any help would be greatly appreciated.

---

### Post by godber on 2012-06-28
> **newbie-user said:**
> I'm having trouble getting an Ubuntu 12.04 client to authenticate against OpenDirectory hosted on a 10.6 OS X server. I've followed the instructions at [http://techblog.glendaleacademy.org/?p=7](http://techblog.glendaleacademy.org/?p=7) and [http://techblog.glendaleacademy.org/?p=27](http://techblog.glendaleacademy.org/?p=27) and it worked well for 10.04 and 11.10. However, 12.04 doesn't seem to work if I follow those same instructions. 

Log files on the OS X server indicate that the user has successfully authenticated but the Ubuntu client auth.log gives this message:

lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=user

I can su as the user in the terminal, but can't log in as the user in the GUI. The screen just goes black and stays that way.

Any help would be greatly appreciated.

You have any luck figuring this out?  I am trying to decide if I want to use Lion Server to authenticate my Ubuntu servers and websites and whatnot.

Austin

---

### Post by newbie-user on 2012-11-10
So I finally got back around to figuring this out and it turns out that I just needed to install nscd, as someone mentioned in a bug report that I can't seem to find the link to right now. All other installation steps were the same.

---

### Post by iLikeStrongJava on 2013-01-06
> **newbie-user said:**
> I'm having trouble getting an Ubuntu 12.04 client to authenticate against OpenDirectory hosted on a 10.6 OS X server. I've followed the instructions at [http://techblog.glendaleacademy.org/?p=7](http://techblog.glendaleacademy.org/?p=7) and [http://techblog.glendaleacademy.org/?p=27](http://techblog.glendaleacademy.org/?p=27) and it worked well for 10.04 and 11.10. However, 12.04 doesn't seem to work if I follow those same instructions. 

Log files on the OS X server indicate that the user has successfully authenticated but the Ubuntu client auth.log gives this message:

lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=user

I can su as the user in the terminal, but can't log in as the user in the GUI. The screen just goes black and stays that way.

Any help would be greatly appreciated.
I know I should be able to figure this out, but I'm getting beat.  Which log on OS X Server reported your successful authentication?  If it is the ApplePasswordServer.Server.log, I'm finding my testuser for getpolicy lines but no auth2.  

I'm getting ready to work on a more detailed post for the forums, but wanted to do some searching here first.

Tim

---

