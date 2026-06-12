---
title: "Administrative Password"
date: 2009-09-02
forum: Security
---

### Post by Cormac Wyatt on 2009-09-02
Hi All,

I need some help.

I have a Dell Mini 10 Laptop with Ubuntu OS.

There are updates available for it but when i go to update its looking for my administrative password.

When i first set-up the computer i do not remember setting a password.

Can i get around this other than reloading Ubuntu.
 
Any help is greatly appreciated.

Regards
Cormac

---

### Post by jerrrys on 2009-09-02
[http://ubuntuforums.org/showthread.php?t=1146638&highlight=password](http://ubuntuforums.org/showthread.php?t=1146638&highlight=password)

should do the trick

---

### Post by lisati on 2009-09-02
In Ubuntu, when you are asked for your administrative password, it's usually OK to use the password with your Ubuntu user name (assuming you're using the user you set up as part of the installation process)

---

### Post by Cormac Wyatt on 2009-09-02
Thanks for the reply but because im using a netbook with a flash drive it has no boot menu (as far as i know).

Maybe i am wrong.

Please let me know otherwise.

Regards
Cormac

---

### Post by snowpine on 2009-09-02
Hi Cormac, it is impossible to install Ubuntu without a username and password. If you've fogotten yours, here are some good instructions: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

The only exception to this rule is if you haven't installed Ubuntu yet. If you are running it in "live" mode from a flash drive, then there is no password. Just press Enter if prompted. (If you are running in Live mode however, there is no reason to install the updates--they will vanish when you power down.)

---

### Post by Cormac Wyatt on 2009-09-02
Thanks for the reply.

I guessed it is impossible to install Ubuntu without a username and password.
How can i reset the password.

I use a Dell Netbook Mini 10. It runs on a flash drive. 

The tried what was mentioned on the link but it doesn't work.

Is this because my Ubunto OS is running from a flash drive and not a hard drive?

Regards
Cormac

---

### Post by snowpine on 2009-09-02
Can you be more specific than "it doesn't work"? Which step specifically of the instructions I linked to are you stuck at?

---

### Post by Cormac Wyatt on 2009-09-02
I am unable to reboot in recovery mode.

I have a single boot system. When i press escape during boot up it does not show any available options and just continues to boot up.

Regards
Cormac

---

### Post by snowpine on 2009-09-02
> **Cormac Wyatt said:**
> I am unable to reboot in recovery mode.

I have a single boot system. When i press escape during boot up it does not show any available options and just continues to boot up.

Regards
Cormac

The Dells have a very short "timeout" or window of opportunity to press the Esc key (maybe 1 second or less)... just keep hammering that Esc key until you get the timing right. :)

ps Once you're logged in, you can edit that timeout for future convenience by editing your /boot/grub/menu.lst... happy to explain once you get the other problem sorted out.

---

### Post by aysiu on 2009-09-02
> **Cormac Wyatt said:**
> I am unable to reboot in recovery mode.

I have a single boot system. When i press escape during boot up it does not show any available options and just continues to boot up.

Regards
Cormac
I don't know why Dell does this.

Apparently, there's a different way to do it with a Dell Mini:
[http://blogs.gnome.org/mneptok/2008/11/11/reset-your-password-with-recovery-mode-on-the-dell-mini-9-netbook/](http://blogs.gnome.org/mneptok/2008/11/11/reset-your-password-with-recovery-mode-on-the-dell-mini-9-netbook/)

---

### Post by QIII on 2009-09-02
You may not be able to get to the boot options if your timeout delay is set too short in menu.lst and you are just not getting the chance.  Either that or you are not pressing escape within the three second default by a fraction of a second.

I have heard unconfirmed horror stories about timeout delays being set by default to 0, although I don't know how that would happen.

I don't know for sure if either of those is your problem, but you might try backing up your 
menu.lst.  If you don't know how, let us know.  It is hard sometimes to know what a poster's experience level is.

Open menu.lst in a text editor of your choice from the terminal and find the line 

timeout X

where X is some whole number representing seconds.

Change X to something reasonable like 10.

---

### Post by Cormac Wyatt on 2009-09-02
Hi All,

I sorted out the problem.

Thank you for all your help!

Thanks aysiu for the link, it worked pretty much straight away (after a bit of annoyance trying to get the 'enter' and 'escape' buttons in the right time.

I cant believe i forgot the password i originally set.

Now another thing is i have heard/been told not to put the updates on my computer as there are problems with them. Is this true?

Regards
Cormac

---

