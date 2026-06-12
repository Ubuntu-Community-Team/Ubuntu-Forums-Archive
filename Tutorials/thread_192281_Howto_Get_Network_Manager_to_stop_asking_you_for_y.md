---
title: "Howto: Get Network Manager to stop asking you for your keyring password (pam_keyring)"
date: 2006-06-08
forum: Tutorials
---

### Post by Kawayanan on 2006-06-08
Howto: Get Network Manager to stop asking you for your keyring password


I am by no means an expert on PAM (Pluggable Authentication Module) or pam_keyring so I wanted to start by acknowleging where I got my info:

Mike Petullo - first wrote the pam_keyring module
Jonathan Nettleton - current maintainer of pam_keyring and added code to allow this module to work with the older PAM included with Ubuntu
s31523 and Buell (from these forums) - for posting the [topic]("http://www.ubuntuforums.org/showthread.php?t=187874") and [comment]("http://www.ubuntuforums.org/showpost.php?p=1090142&postcount=4") that helped me get this working.

After I got my wireless working in 6.06 using Network Manager I was very happy, but it would be nice not to have to enter the keyring password after logging in.  Luckily, there is a PAM module pam_keyring that will automatically unlock your gnome keyring when you login.  You can find pam_keyring and more info [here]("http://www.hekanetworks.com/pam_keyring/").  Pam_keyring is not currently an available package for Ubuntu, but you can get it installed pretty easily on 6.06. **For this to work, your login password and your keyring password must be the same**.  If the two passwords are not the same, there are a few possibilities. (See below)**

Pam_keyring requires the following packages (I think they are installed by default in 6.06):
gnome-keyring >= 0.4.8
gnome-session >= 2.10
pam >= 0.77

Since you will need to compile pam_keyring from source, you will also need some development packages.  Here are the additional packages that I needed to install (were not installed by default in 6.06):

build-essential
libtool
libglib2.0-dev
libgnome-keyring-dev
libpam0g-dev

You can install these packages using Synaptic.  Then download [pam_keyring-0.0.8.tar.gz]("http://www.hekanetworks.com/opensource/pam_keyring/pam_keyring-0.0.8.tar.gz").  Open a terminal window, find the downloaded tarball and do the following at the command line:

```
tar -xvvzf pam_keyring-0.0.8.tar.gz
```

```
cd pam_keyring-0.0.8
```

```
./configure --prefix=/usr --libdir=/lib
``` - hopefully you get no errors here.  If you do, most likely you are missing a needed package.

```
make
```

```
sudo make install
``` - this should ask you for your password

Now, you will need to edit one file.  I use vi, but if you are more comfortable with a graphical editor you can enter the following:

```
sudo gedit /etc/pam.d/gdm
```

add the following two lines to the end of the file:

```
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
```

Now you can reboot and it should not ask you for your keyring password to log onto your encrypted wireless network. :)

Hope this works for everyone.

Kawayanan


** If your login password and your keyring password are not the same, you have to fix this and there are a couple of possible ways.  Unfortuantely, there isn't a good way to change your keyring password, and you will need to work around this.  

1)  Change you login password to match your keyring password

2)  You may be able to remove the keyring entirely and create a new one.  See [this page]("http://www.linuxquestions.org/questions/showthread.php?t=410266") for info.  I haven't tried this, but howfully the next time Network Manager tries to logon to your encrypted wireless network it would ask you for the encryption key again and create a new keyring (use your logon password this time).  Someone should post if they do whis to confirm this works.

3)  If you are feeling really brave, Jonathan Nettleton (who maintains pam_keyring) has submitted a patch to the gnome-keyring that allows you to change the keyring password.  It has not been excepted yet, but he has provided patched cvs downloads that people can test.  He has more info and the downloads [here]("http://www.hekanetworks.com/pam_keyring/").  Hopefull in the future, we will all be able to easily change our keyring passwords. :) Thanks Jonathan Nettleton.

---

### Post by KillerKiwi on 2006-06-08
A "checkinstall" might be better than "sudo make install", im trying this as soon as I get home.

---

### Post by Chrissss on 2006-06-08
Ah, thanks! NOW you actually can work with gnome-keyring ;)

---

### Post by kleeman on 2006-06-09
Did not work for me. I had to delete my old keyring using keyring manager in order to get passwords to match so maybe this is the issue

---

### Post by ????? on 2006-06-09
It works! Thanks for the howto.

---

### Post by yopnono on 2006-06-27
Made a .DEB for those that are little lazy ;) But you still need to add this to the GDM file.

cd /etc/pam.d
sudo gedit gdm

```

## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password. 
auth optional pam_keyring.so try_first_pass 
session optional pam_keyring.so
```

---

### Post by horace on 2006-06-27
Thanks for the .deb (and the howto) - installed and working for me too. That's another little annoyance crossed off the list (on my wife's laptop, so it needs to be kept simple ....)

---

### Post by rmjb on 2006-07-31
Okay I tried this hoping nautilus wouldn't ask me for the keyring password when accessing my samba shares, but that didn't work, how do I uninstall pam_keyring?

- rmjb

---

### Post by rmjb on 2006-07-31
Okay, I was lazy and I didn't reboot to test this initially, now that I've rebooted it works.

- rmjb

---

### Post by mrojas73 on 2006-08-01
Kawayanan; Thank you very much. This worked like a charm for me on my Presario V2000, it's nice not having to enter the password everytime I reboot.

Good work!

---

### Post by Ares Drake on 2006-08-01
cool, thanks a lot!! 8)

---

### Post by rmjb on 2006-08-01
Okay, is this a security risk? Even if it is I'm keeping it, I'm aware about the trade off between security & convenience.

But if it's not how can we get the Ubuntu devs to include this out of the box?

- rmjb

---

### Post by n00blar on 2006-08-02
Excellent HOWTO....took me exactly 4 minutes to get the whole thing fixed!! ;)

I love the Ubuntu community, way to go!!

---

### Post by Ares Drake on 2006-08-02
Unfortunately it only works for me when I manually log in with gdm. If I set to login the user automatically after a given time, it doesn't work. Any way to fix this?

---

### Post by Flavian on 2006-08-06
Since my last update the work around doesn't seem to work anymore.
I tried redoing everything in here but it did not work.
Has anyone got a solution?
Thanks
Flo

---

### Post by plutoprime on 2006-08-06
> **Flavian said:**
> Since my last update the work around doesn't seem to work anymore.
I tried redoing everything in here but it did not work.
Has anyone got a solution?
Thanks
Flo

Same problem here

---

### Post by mr2nr on 2006-08-24
Yeah it no longer works for me too.

---

### Post by kpkeerthi on 2006-08-24
Same here.. LOL!

---

### Post by kleeman on 2006-08-26
The new NetworkManager (0.7?) circumvents this problem nicely. Instructions for installation are here:
[http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)

---

### Post by superm1 on 2006-08-31
> **kleeman said:**
> The new NetworkManager (0.7?) circumvents this problem nicely. Instructions for installation are here:
[http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)
What exactly is different in the new NM that circumvents the problem?  Does it store passwords in a different fashion?

---

### Post by kleeman on 2006-08-31
Yes it does not use the gnome keyring anymore. Much less annoying. Store the wpa key once and that is it.

---

### Post by superm1 on 2006-08-31
That sounds awesome.  Has it been pushed into edgy yet?  I can grab edgy sources and build a dapper package for it easily if so.

---

### Post by kleeman on 2006-08-31
No not yet. You have to use the manual guide here:

[http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)

---

### Post by Flavian on 2006-09-01
> **kleeman said:**
> No not yet. You have to use the manual guide here:

[http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)

Sorry, I don't get it. What part of the manual do I have to do?
Networkmanager works on my laptop it's just the annyoing Keyring thing that I want to get rid of. So do I have to follow ALL the steps in the howto, or is it just possible to upgrade network manager alone?

---

### Post by Paul133 on 2006-09-01
Actually, I kind of like the fact that you need to enter a password. More of a deterrent if somone's trying to get into your profile. OK, the real reason I'm saying this is because when I first installed this, I wanted to make the password the same as my login, but I hit CAPS LOCK! : ( All well, like I said, I've grown to like the extra security.

---

### Post by kleeman on 2006-09-01
You just need to update networkmanager i.e. below this line:

"The second strategy is to update to the latest NetworkManager, beginning with some of its important dependencies."

It probably wouldn't hurt to update your wireless driver as well while you are at it. There are constant improvements going on.

Bear in mind though that you will be installing experimental cvs software and there may be bugs. Mine worked fine but maybe I was lucky....

Tschuess ;)

---

### Post by thepizzaking on 2006-09-01
I updated my network manager using that guide and it worked fine.  The only problem is that it still asks me for my keyring password.  Did I do something wrong?

---

### Post by eg-maverick on 2006-09-05
Ah,
Nice to see I'm not alone in losing my mind. My last update caused the keyring problem to return. I'll try upgrading again to v.7 of NM.
Thanks (for sharing in the pain).

---

### Post by eg-maverick on 2006-09-06
[PHP]The new NetworkManager (0.7?) circumvents this problem nicely. Instructions for installation are here:
http://www.ubuntuforums.org/showthread.php?t=125150
Reply With Quote[/PHP]
I went to the NetworkManager website [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) and it seems they only go up to v.6 (which is what I have). I also went to the thread you suggested but it seems rather ominous for a newbie like me. Is there an easier and working solution?

---

### Post by kleeman on 2006-09-06
> **eg-maverick said:**
> [PHP]The new NetworkManager (0.7?) circumvents this problem nicely. Instructions for installation are here:
http://www.ubuntuforums.org/showthread.php?t=125150
Reply With Quote[/PHP]
I went to the NetworkManager website [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) and it seems they only go up to v.6 (which is what I have). I also went to the thread you suggested but it seems rather ominous for a newbie like me. Is there an easier and working solution?
The howto I quote installs the cvs not stable version of NetworkManager. I would not recommend it for newbies. Wait for the stable release of 0.7. BTW distrowatch has a nice feature on the left handside of the page which tracks the latest releases of a whole range of FOSS software. Keep an eye on this.

---

### Post by eg-maverick on 2006-09-07
> **kleeman said:**
> The howto I quote installs the cvs not stable version of NetworkManager. I would not recommend it for newbies. Wait for the stable release of 0.7. BTW distrowatch has a nice feature on the left handside of the page which tracks the latest releases of a whole range of FOSS software. Keep an eye on this.

Rant on
I guess I will (reluctantly) wait. I'm disappointed in this flaw with Ubuntu. It essentially makes Ubuntu unusable as a mobile (WIFI) option when the user (my son and a student) does not have admin privelege. I would have thought a user profile like this qualifies as a target for "Linux for humans". 
Rant off
Thanks for the info. Craig

---

### Post by chrismyers on 2006-10-26
Just a note to say that this also works with Edgy Eft.

Cheers.   :mrgreen:

---

### Post by mark_g on 2006-11-16
Yep, works great indeed. Thanks a lot.

---

### Post by dentaku65 on 2006-11-17
Thank you so much, it works perfect on Edgy

---

### Post by cwhisperer on 2006-11-19
It simply works ;) great job !!

---

### Post by n3Cre0 on 2006-11-19
Yep worked here flawless aswell 6.10 thnx

---

### Post by eg-maverick on 2006-11-25
is there some configuration I need to do to get it to stop asking for the keyring password? I upgraded to 6.10 and it still asks every time I turn the machine on or switch wifi networks.
Craig

---

### Post by Moe-loves-ayumi on 2006-11-25
> **Kawayanan said:**
> Pam_keyring requires the following packages (I think they are installed by default in 6.06):
gnome-keyring >= 0.4.8
gnome-session >= 2.10
pam >= 0.77pam doesn't exist in Synaptic. I didn't install it. May it be the reason why nm-applet ask me to type my password each time I'm logging automatically into GNOME ? I've installed pam_keyring with the .deb.

Thanks.

Edit : with manual logging nm-applet doesn't ask a password and turn on the connection. How can we enable automatic login with gdm and an automatic connection with NetworkManager ?

---

### Post by stacktracer on 2006-11-26
> How can we enable automatic login with gdm and an automatic connection with NetworkManager ?

Try appending to **/etc/pam.d/gdm-autologin** the same couple of lines you appended to /etc/pam.d/gdm.

I haven't tried it myself, but it seems like it ought to work. *However*, if you do this, be aware that you're taking another step down the convenience-vs.-security spectrum.

---

### Post by Moe-loves-ayumi on 2006-11-27
I used [wpa_supplicant](http://ubuntuforums.org/showthread.php?t=263136&highlight=wpa) instead of Network Manager and it worked perfectly. Thanks anyway.

---

### Post by eg-maverick on 2006-11-28
> **dentaku65 said:**
> Thank you so much, it works perfect on Edgy

When you say it works, what exactly works? I upgraded to 6.10 and every time I try and attach to a WEP keyed wifi network, it asks for my keyring password (twice). 
Thanks,
Craig

---

### Post by atlas95 on 2006-12-04
Hello!
I have had pam bluetooth and so, I must enter my password yet in nm-applet.
I hope you understand my problem and you can help me.
Thanks

Here my /etc/pam.d/gdm
```

#%PAM-1.0
auth	requisite	pam_nologin.so
auth	required	pam_env.so
auth    sufficient      pam_blue.so debug  ##I have add this for pam bluetooth


@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password

## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so

```

---

### Post by hornett on 2006-12-06
This has stopped working on my system recently. Not sure if it was an update or some other change. :(

Is everybody else still OK?

---

### Post by skirkpatrick on 2006-12-06
It depends.  It works reliably on my Acer laptop with Edgy but doesn't work most of the time on my HP laptop with Dapper.

---

### Post by plouj on 2006-12-08
Thanks a lot. This works perfectly on my Ubuntu 6.10. The user is only asked to enter his password once, at the gdb login screen. After that, the NetworkManager is able to connect to my WPA router without any additional prompts.
By the way, I didn't have to reboot for the pam settings to take effect. A log-off was enough. Of course I tested that it works after a reboot as well.

---

### Post by CoolHand on 2006-12-10
I found another solution in another thread.  I would credit the author if I could find that post again.  In any case it is not me so thanks to the real finder of this fix.

You can use the .deb file from earlier in this thread and make it all work on Edgy etc. without having to build anything from source.  I run Xubuntu and it was driving me nuts to have to re-enter my password multiple times.  This fix solved it and your login and keyring pass do not (and should not) be the same with this fix and it supposedly works with auto-login though I have not tried that.  However it makes your keyring insecure so don't use it if that bothers you.

Here's how it works.  Install pam keyring and edit the gdm file as stated earlier in this thread.  Then create a script with the following contents:
```
#!/bin/bash
PATH=$PATH:$HOME/(scriptdir)
echo (ringpass) | /usr/libexec/pam-keyring-tool -u -s
```
Replace scriptdir with the directory where your script is and ringpass with your keyring password.  Both without the () brackets, of course.  Make the script executable and then through the gui you use (gnome, kde, xfce) call the script first thing from your session startup options.  In XFCE it is under settings/autostarted applications.  Not sure for you gnome/kde users but I know you can do it.  The script will unlock the keyring and avoid the need for the password.  The PATH statement isn't really needed but that is how it was posted when I found it and it doesn't hurt so I included it.  Worked for me.  Good luck.

---

### Post by Pobega on 2007-01-03
In the autostarted applications, do I put it at

/home/$USER/script
 -or-
./home/$USER/script

**Edit:** No matter what I do I can't get the keyring to not ask me for a password. I have both pam-keyring installed and edited the gdm file as the OP suggested, and I have this script running on startup. But no matter what it asks for the password.

---

### Post by puccaso on 2007-01-04
```
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.12.6)
checking for gnome-keyring-1... yes
checking GNOME_KEYRING_CFLAGS... -I/usr/include/gnome-keyring-1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking GNOME_KEYRING_LIBS... -lgnome-keyring -lglib-2.0  
checking for gnome_keyring_unlock in -lgnome-keyring... yes
checking security/pam_modules.h usability... no
checking security/pam_modules.h presence... no
checking for security/pam_modules.h... no
configure: error: You are missing security/pam_modules.h
```



why am i getting this error?

---

### Post by CoolHand on 2007-01-04
> **Pobega said:**
> In the autostarted applications, do I put it at

/home/$USER/script
 -or-
./home/$USER/script

**Edit:** No matter what I do I can't get the keyring to not ask me for a password. I have both pam-keyring installed and edited the gdm file as the OP suggested, and I have this script running on startup. But no matter what it asks for the password.

Without the . would be correct.  The dot tells the system to start from the current working directory so if your working directory is /home/$USER/ you are essentially telling it to look in /home/$USER/home/$USER/ if you use the dot.  Also make sure that this script is the first thing that you call to start.  In my case it works but if Network Manager tries to start before the script unlocks the keyring it will not work so it needs to be called as soon as possible upon login.

---

### Post by Alz on 2007-01-20
Are there any methods for this to work with autologin?

---

### Post by Floppyjoe on 2007-01-25
The method at the beginning of this thread worked for me in Ubuntu 6.10 Edgy.
My problem is that i have a script that starts my Firestarter GUI that starts before the keyring applet and so the firewall gui always fails to turn on after it loads up because the network interface hasn't  finished connecting to the network yet. Is there a way to change the order in the sessions dialog?

---

### Post by SnowPunk98 on 2007-02-06
Thanks, worked perfectly on 6.10

---

### Post by SnowPunk98 on 2007-02-06
Actually it doesn't seem to work anymore for some reason. I have tried to do it again but when I reboot it comes up again. If I do it and just restart X it works but not when I reboot, can anyone help this is really annoying.

---

### Post by usererror on 2007-02-11
> **SnowPunk98 said:**
> Actually it doesn't seem to work anymore for some reason. I have tried to do it again but when I reboot it comes up again. If I do it and just restart X it works but not when I reboot, can anyone help this is really annoying.

What errors did you receive?  What version of Ubuntu are you using?

To the original poster:

I had to add this additional package that I was missing during the make step of the compile:

```
sudo apt-get install libgnome-keyring0
```

but it is working for me on my wireless profile for my home network.  hopefully it'll work also when I connect to the wireless network at my workplace tomorrow!

---

### Post by Fitzcarraldo on 2007-03-08
> **Kawayanan said:**
> 
2)  You may be able to remove the keyring entirely and create a new one.  See [this page]("http://www.linuxquestions.org/questions/showthread.php?t=410266") for info.  I haven't tried this, but howfully the next time Network Manager tries to logon to your encrypted wireless network it would ask you for the encryption key again and create a new keyring (use your logon password this time).  Someone should post if they do whis to confirm this works.


I did not need to kill the Gnome Keyring daemon to do it, but I can confirm that deleting the file default.keyring in ~/.gnome2/keyrings will result in you being prompted at next boot to define a new password for the default keyring. So it is quite straightforward to change the default keyring's password to make it the same as your ubuntu log-in password if you want.

Either of the following will achieve the desired effect:

```
rm ~/.gnome2/keyrings/default.keyring
```

```
mv ~/.gnome2/keyrings/default.keyring ~/Desktop/default.keyring.bak
```

By the way, I found that doing the following is of no use, presumably because Gnome Keyring Manager just finds the default keyring password in the file keyring.bak instead. It seems you need to make sure the folder ~/.gnome2/keyrings is empty.

```
mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.bak
```

---

### Post by geckorock69 on 2007-03-11
Thank you - worked perfectly!

---

### Post by Kobalt on 2007-03-11
Pam_keyring is now in the Feisty repos : I had installed it and couldn't figure out why it wasn't working since I still was asked my password to start my network. Then I came across your post, and tried to simply paste the following lines at the end of /etc/pam.d/gdm : 
> auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
And it worked ! 

So thanks a lot for the advice ;)

---

### Post by mshlin on 2007-03-11
Brilliant tip. Worked like a dream! :) 

Many thanks.

---

### Post by lotus49 on 2007-03-17
Thanks (especially to kawayanan and yopnono) for this great tip.  I used the deb on Edgy Eft and it worked perfectly.

This was the only annoying thing left about my Ubuntu installation so I am chuffed to get this fixed.

---

### Post by superm1 on 2007-03-17
Just a note for feisty people:

to install on feisty:
```
sudo apt-get install libpam-keyring
```
to enable it:
1) edit /etc/pam.d/gdm
```
gksudo gedit /etc/pam.d/gdm
```
2) Add this line to the end
```
@include common-pamkeyring
```

---

### Post by FishRCynic on 2007-03-21
this works great - without beryl - when beryl loads the password is required again.
i have set up auto login which works as advertised with the pam keyring working well when
beryl is disabled.  When beryl is enabled, the logon proceeds correctly the gdm call 
does not request a password but as soon as beryl loads the nm-applet must get refreshed
and the keyring password is required.  I have tried to enable a pam keyring configuration file
for nm-applet and/or for beryl but so far i have not been successful. If anyone can point me in the right direction it would be most appreciated.

---

### Post by Pausanias on 2007-03-25
Tested this on feisty and it works great. Thanks!

> **superm1 said:**
> Just a note for feisty people:

to install on feisty:
```
sudo apt-get install libpam-keyring
```
to enable it:
1) edit /etc/pam.d/gdm
```
gksudo gedit /etc/pam.d/gdm
```
2) Add this line to the end
```
@include common-pamkeyring
```

---

### Post by Durden on 2007-04-08
This works great for when my laptop starts up (using Feisty) but when I hibernate and come back I have to enter my passphrase again. Anyone have a solution? This is the last annoying thing in my Ubuntu setup.

---

### Post by craigmac on 2007-04-08
I'm with Durden on this one. When my lappie comes back from suspend or hibernate, I need to enter the keyring password.

Anybody have a solution for this one?

---

### Post by Thomaseov on 2007-04-09
I'm with Durden and craigmac...I never had any trouble with wifi until feisty...it always just worked on my laptop at home, and I used the console to connect elsewhere with iwlist, iwconfig and dhclient.  Now it is painfully slow and even with pamkeyring I still have to renter my password on waking from suspend after a 15 second wait...   anyone?

---

### Post by TomFumb on 2007-04-22
ok this is not good, I did everything in this howto, to the letter, and now gdm won't work anymore

I can log in to the system in text mode with no problems, and I removed the 'x' from my username in /etc/passwd, but I still can't log in with gdm

does anyone know how to fix this problem? I already tried reinstalling gdm, and my /etc/pam.d/gdm file is back to how it was before I started with network manager. 

I'd really hate to have to reinstall because of this

 thanks

---

### Post by h6w on 2007-04-24
> **stacktracer said:**
> Try appending to **/etc/pam.d/gdm-autologin** the same couple of lines you appended to /etc/pam.d/gdm.

I haven't tried it myself, but it seems like it ought to work. *However*, if you do this, be aware that you're taking another step down the convenience-vs.-security spectrum.

Not quite.  It will work, however, during the login process it will pop up a big text box saying "Automatic login password" with a field in plaintext (not password cloaked)!

---

### Post by ngolian on 2007-04-24
Several people have asked how to get this to work with autologin. Making the same change to /etc/pam.d/gdm-autologin as to /etc/pam.d/gdm described at the start of the thread sort of works, but you do get asked for a password at login, so it isn't really automatic any more.

Instead I wrote this script:

#!/bin/sh
exec echo -n "MyKeyringPassword" | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

and added it to the session Startup Programs. Obviously it relies on being run after gnome-keyring-daemon starts but before nm-applet, but that seems to happen automagically for me.

So I don't need to enter a password at all any more! I know, I know, very lax security. But people who don't use gdm autologin might also find this method useful, because it means you can use separate passwords for logging in and for the keyring. And the script could probably be refined so as not to reveal the password in plain text.

You still need the libpam-keyring package for pam-keyring-tool. And I had to look at the source to find out how to use it. There's probably a way of doing the same thing using the dbus interface so you don't need libpam-keyring.

---

### Post by Mr Squiddy on 2007-04-24
Apologies if anyone has asked this one before but is there an equivalent change which can be done on Kubuntu to achieve the same end?  I tried doing the same modification to /etc/pam.d/kdm as one would do for /etc/pam.d/gdm but it doesn't work.

---

### Post by depp on 2007-04-26
you can simply disable kwallet

---

### Post by Blueshift on 2007-04-27
On Feisty its a lot easier to get it working. Here is what I did:

Added the following two lines (here marked as red) in the /etc/pam.d/gdm file:

```
#%PAM-1.0
[COLOR="Red"]auth	optional	pam_keyring.so try_first_pass
session	optional	pam_keyring.so[/COLOR]
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password
```

Then go to: [COLOR="Red"]System --> Administration --> Synaptec Packagemanager[/COLOR] and search for: [COLOR="Red"]pam_key[/COLOR]

Install the first module you see and voila, you don't have to enter the keyring password after each login :)

---

### Post by depp on 2007-04-28
> **Blueshift said:**
> On Feisty its a lot easier to get it working. Here is what I did:

Added the following two lines (here marked as red) in the /etc/pam.d/gdm file:

```
#%PAM-1.0
[COLOR="Red"]auth	optional	pam_keyring.so try_first_pass
session	optional	pam_keyring.so[/COLOR]
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password
```

Then go to: [COLOR="Red"]System --> Administration --> Synaptec Packagemanager[/COLOR] and search for: [COLOR="Red"]pam_key[/COLOR]

Install the first module you see and voila, you don't have to enter the keyring password after each login :)

or just simply ```
@include common-pamkering
```

---

### Post by lcohen999 on 2007-04-29
I am trying to use this with Feisty..

I have auto-login setup so the regular fix does not work.

As per the older email, this seems to fix that problem (with edgy):

#!/bin/bash
#PATH=$PATH:$HOME)
echo XXX | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

with feisty I get:
echo XXX | /usr/lib/libpam-keyring/pam-keyring-tool -u -s --keyring=default
pam-keyring-tool: error unlocking the default keyring

any thoughts?

---

### Post by ngolian on 2007-04-29
The first way works for me with Feisty. It could be that your script runs before gnome-keyring-daemon. ISTR getting a vague error like that when I was using ROX-Session and needed to start the keyring daemon manually. You could try removing the daemon from the session manager's control (easier said than done) and amending your script:

gnome-keyring-daemon &
sleep 1
echo XXX | /usr/lib/libpam-keyring/pam-keyring-tool -u -s --keyring=default

The sleep does seem to be necessary, but it's a bad bodge. If you make the delay too long it may cause network manager to start up before the keyring is unlocked. AIUI the keyring stuff is all done by dbus, so you'd expect that trying to use it should automatically cause the service to start. Maybe one day I'll investigate its dbus interface and try to come up with a less bodgy solution.

---

### Post by lcohen999 on 2007-04-29
> **ngolian said:**
> The first way works for me with Feisty. It could be that your script runs before gnome-keyring-daemon. ISTR getting a vague error like that when I was using ROX-Session and needed to start the keyring daemon manually. You could try removing the daemon from the session manager's control (easier said than done) and amending your script:

gnome-keyring-daemon &
sleep 1
echo XXX | /usr/lib/libpam-keyring/pam-keyring-tool -u -s --keyring=default

The sleep does seem to be necessary, but it's a bad bodge. If you make the delay too long it may cause network manager to start up before the keyring is unlocked. AIUI the keyring stuff is all done by dbus, so you'd expect that trying to use it should automatically cause the service to start. Maybe one day I'll investigate its dbus interface and try to come up with a less bodgy solution.

....so you know what question comes next...where do I disable the gnome-keyring-daemon :)

---

### Post by lcohen999 on 2007-04-29
actually more that I think about it, it can't even be that, I get this error if I run the script manually after everything is booted..

---

### Post by lcohen999 on 2007-04-29
you can disregard, from a command line it didn't work..on bootup in session manager, it works fine :)  thanks for the help!

---

### Post by Villainous on 2007-04-30
I did a search for pam_key and I get nothing.  Is there another repo that I need to setup first?  I admit that I haven't read through all of this thread and will go back and do so.  However, in the meantime, I would like to get this working, especially because I have never had to do this in any other OS....

---

### Post by superm1 on 2007-04-30
Read the thread backwards.  There is a post from me and someone else both explaining methods for feisty.

---

### Post by strumluff on 2007-05-05
Thank you superm1 for your Feisty solution, so much easier to do than previous ubuntu versions and works a treat :)

---

### Post by Tautvydas on 2007-05-21
Edited:
Now it works and for me. Thanks for good info :)

---

### Post by michwill on 2007-06-05
Ok, I'm about to lose it.  I've done everything suggested in this forum. . .twice.  And I've done everything besides, except sacrifice chickens.  I've got my system set to auto-login and I've basically duplicated the "gdm" into the "gdm-autologin". . .all to no avail.

Please humor me, and list *explicitly*, once again, the steps required to get this to work with auto-login.

Thanks

NOTE: using Feisty

---

### Post by vanadium on 2007-06-05
There was another approach listed in this thread that involved creating a small script that echoes the password into network manager. This is not quite safe, but since you are using auto login, the security is not a big issue. That approach should work for you.

---

### Post by michwill on 2007-06-05
> **vanadium said:**
> There was another approach listed in this thread that involved creating a small script that echoes the password into network manager. This is not quite safe, but since you are using auto login, the security is not a big issue. That approach should work for you.



Thank you, but there couple of issues here:

1)  That solution doesn't help me in the event of a network disconnect/reconnect issue.  That solution seems to only work on boot.  I need an end all "never ask me again" solution to this problem.  Obviously I could just open up my network and eliminate the need, but that's not an option.

2) I requested "Please humor me, and list *explicitly*, once again, the steps required to get this to work with auto-login."   . . .whether that means re-listing or copying and pasting.  There are several solutions and I'm looking for a direct answer to the question posed.

Regards.

---

### Post by ngolian on 2007-06-05
I described how to use a script to avoid a password prompt with auto-login in post #68. Using that method you should **not** alter /etc/pam.d/gdm-autologin. You're unlocking the gnome keyring, not just network-manager, so it should stay unlocked in the event of a disconnection. It sounds like your network manager isn't saving its password in the keyring for some reason.

---

### Post by michwill on 2007-06-05
> **ngolian said:**
> I described how to use a script to avoid a password prompt with auto-login in post #68. Using that method you should **not** alter /etc/pam.d/gdm-autologin. You're unlocking the gnome keyring, not just network-manager, so it should stay unlocked in the event of a disconnection. It sounds like your network manager isn't saving its password in the keyring for some reason.

I'm really not sure what's going on, or what I'm missing, but this solution is still no better.  I get a small box during login asking me for a password to access the script.  Once it's booted it doesn't ask me for anything, but the whole point is to avoid *EVER* having to type a password.  I've restarted 4 times and each time I get the dialog asking me for a password to access the script.

FYI, I put the script in /usr/bin

---

### Post by ngolian on 2007-06-06
> **michwill said:**
> I'm really not sure what's going on, or what I'm missing, but this solution is still no better.  I get a small box during login asking me for a password to access the script.  Once it's booted it doesn't ask me for anything, but the whole point is to avoid *EVER* having to type a password.  I've restarted 4 times and each time I get the dialog asking me for a password to access the script.
It sounds like you previously tried the other method of altering /etc/pam.d/gdm-autologin and you haven't reversed that change. Make sure that file doesn't contain the extra lines described further up the thread.
> FYI, I put the script in /usr/bin
That's OK, but as it isn't part of the distro it should really go in /usr/local/bin or in a bin directory in your home directory (in which case you'll have to enter the full path in Gnome session manager). Did you also remember to make it executable? I wasn't sure what level of newbie would be reading so I neglected those sorts of details.

---

### Post by michwill on 2007-06-09
You're right, and I fixed that.  Now it will stop asking for the password upon login, but it will not reconnect.  I've traced this to the fact that, upon disconnect, for whatever reason it wants to connect to one of two other networks (one open, one closed) in the neighborhood.  Since it's on "roam" (as suggested), it gets to pick and choose like that.  This then leaves me at a password prompt for one of the other networks. . .


. . .That in turn lead me to simply enter the SSID and password information manually and take it off "roam".  This, of course, is spotty and reconnects pretty much *NEVER* occur.  Why is this such a problem?!?!  ](*,)

---

### Post by Shaktipwr on 2007-06-30
Sorry for the dupe post from system76.com but i am desperate!
 was trying to stop having to type the keyring password everytime i logged in.  I was following the instructions on: 

[http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring](http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring)

After the fact I realized that was for ubuntu 6.06 not Feisty.  It seemed to fail when doing the make install and after this point I can no longer log into x.  I get a dialog box that reads "authentication failed" with any user name and password that i have.  If i enter a wrong user name and psswd, I get the standard message of "incorrect username or password".  My geek husband was able to login to the console when not going through X however he doesn't know much about pam.d and can't figure out how to enable x logins (his words).  Can someone ****please**** help!!!!

I am a total newbie and I was trying to teach myself something and totally screwed up, my computer geek husband can't even fix this one!!!

My system is
Gazelle model S62FM
I'm running Feisty Fawn, not sure which version but the kernel is 2.6.20-16.
The system is only a couple weeks old so it might be the latest from System76.

And, I did find what Superm1 had posted about Feisty and added the line" @include common-pamkeyring.
It worked once then never again so i am back to square one.

---

### Post by woyzeckswoe on 2007-07-17
> **ngolian said:**
> Several people have asked how to get this to work with autologin. Making the same change to /etc/pam.d/gdm-autologin as to /etc/pam.d/gdm described at the start of the thread sort of works, but you do get asked for a password at login, so it isn't really automatic any more.

Instead I wrote this script:

#!/bin/sh
exec echo -n "MyKeyringPassword" | /usr/lib/libpam-keyring/pam-keyring-tool -u -s

and added it to the session Startup Programs. Obviously it relies on being run after gnome-keyring-daemon starts but before nm-applet, but that seems to happen automagically for me.

So I don't need to enter a password at all any more! I know, I know, very lax security. But people who don't use gdm autologin might also find this method useful, because it means you can use separate passwords for logging in and for the keyring. And the script could probably be refined so as not to reveal the password in plain text.

You still need the libpam-keyring package for pam-keyring-tool. And I had to look at the source to find out how to use it. There's probably a way of doing the same thing using the dbus interface so you don't need libpam-keyring.

it finally worked for me too, after crushing my head on the wall for several nights i followed the above posts and deleted the @blablabla entry in gdm autologin and then make my script executable and now i'm really happy and reaching for welll earned beer in the fridge

thankyou all people! (especially ngolian)

ww

---

### Post by houms on 2007-08-08
This may not be the desired approach for some but, from my experience with Ubuntu(feisty), setting the interface statically did the trick. Did not do anything else mentioned. I first established a connection and was prompted to setup default keyring password. Once I got connected, just modifying the /etc/network/interfaces file did it.

---

### Post by stuffer007 on 2007-09-18
Thank you so much. You are freaking awesome.

---

### Post by houms on 2007-09-18
Glad it was helpful. Let me know if you have any other issues. I'm here to help and learn.

---

### Post by CaptainCool on 2007-09-27
> **houms said:**
> This may not be the desired approach for some but, from my experience with Ubuntu(feisty), setting the interface statically did the trick. Did not do anything else mentioned. I first established a connection and was prompted to setup default keyring password. Once I got connected, just modifying the /etc/network/interfaces file did it.

could you please go into more detail as to what you changed in the interfaces file?

---

### Post by houms on 2007-09-27
> could you please go into more detail as to what you changed in the interfaces file? 

all you have to do is edit your interface config file. You will have to know which interface is your wireless... for example mine is eth1, a simple iwconfig will show you which interface corresponds with your wireless.

if on gnome 
sudo gedit /etc/network/interfaces

if kde
sudo kate /etc/network/interfaces

Once in that file look for your interface(e.g eth1)
what you have to do is give it a static ip for example mine interface file looked like this for the wireless interface. Now I had other entries such as eth0 and wlan0 but they look similar to whats below

auto eth1
iface eth1 inet dhcp
 This means your wireless is set to dhcp. Now change it to look like this below
auto eth1
iface eth1 inet [COLOR="Red"]static[/COLOR]
address 10.0.0.7
netmask 255.255.255.0
gateway 10.0.0.1
wpa-driver wext
wpa-ssid yourssidhere
wpa-ap-scan 2 (this was donw because my ssid broadcasting is disabled)
wpa-proto RSN (this is for wpa2)
wpa-pairwise CCMP (this is for AES as opposed to tkip)
wpa-group CCMP     (this is for AES as opposed to tkip)
wpa-key-mgmt WPA-PSK
wpa-psk yourwirelesshexkey (if you need help on how to get this let me know)
post-up iface down
post-up iface up

Now there is a great howto here :[http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa2](http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa2)
on these particular setting so you can set it for your network.  If you need help with this let me know.....
the two post-up command at the end is because everytime I started my computer and logged in, I was not able to get the wireless to work until i did
sudo ifdown eth1
then
sudo ifup eth1
so adding those 2 commands to the config file brings up the interface automagically...once your done restart the computer and from now on you should be conntected to your network.. no prompt for keyring or anything just straight connection.. Again if something is unclear or you need help let me know. I'm here to learn and help.

---

### Post by markp1989 on 2007-10-24
i cannot get this to work with xubuntu 7.10 any one know why?

---

### Post by Pausanias on 2007-10-24
This shouldn't be needed in Gutsy. There's a checkbox that lets you do this on the defaul install when you first enter the password.

---

### Post by lcohen999 on 2007-10-24
Where is that checkbox?  (post install)

---

### Post by Pausanias on 2007-10-24
1) Connect to a new network. Enter the specs.
2) Log out.
3) Log back in. It will ask you to re-enter this password. In that same dialog box, you should see the check box that say something like "Don't ask again."

---

### Post by misterbeetz on 2007-10-25
> **Pausanias said:**
> 1) Connect to a new network. Enter the specs.
2) Log out.
3) Log back in. It will ask you to re-enter this password. In that same dialog box, you should see the check box that say something like "Don't ask again."

When network manager triggers an "unlock keyring" prompt upon every boot up for me I am afraid I see no such option in Gutsy.

EDIT:  Looks like I found a way to fix this (in Gutsy):  Apparently network manager will keep asking for the keyring password if it is in roaming mode.  Essentially you need to go into network manager's manual configuration, turn off roaming mode for your wifi radio (card), and manually enter the connection specs for your private wifi network.  After that, the keyring stopped popping up after reboots.  I got this tip from the following post:

> **joshzam said:**
> I'd like to share what took me a few hours to figure out on my own. Maybe it'll spare someone else the hair-pulling that I've suffered.

I've got a clean Gutsy install on my laptop. I didn't want to have to enter my login or keyring passwords at startup. Auto login for Ubuntu worked fine but I kept getting asked for my keyring password to connect to my WiFi router. I searched the forums and followed about a dozen different suggestions involving:
- install Pam
- install Wicd
- edit the /etc/pam.d/gdm file
- configure the Keyring manager
- etc. etc.

Then I found this thread and i thought that my prayers were answered. What a fool I was for not noticing the checkbox at the bottom of the keyring prompt to log in automatically! I rebooted and... there was no checkbox!!

search... search... search... answer :)

The default network configuration for my wireless modem was set to 'roaming' (as indicated by the WiFi strength meter as the network icon). I removed the roaming option and configured my network manually (the network icon changed to the double LCD monitors). After the next reboot, I wasn't asked for either my Ubuntu login or my keyring password. It just worked.

I hope this helps others with the same problem.

From the following thread: [http://ubuntuforums.org/showthread.php?t=577641&highlight=keyring&page=2](http://ubuntuforums.org/showthread.php?t=577641&highlight=keyring&page=2)

Everything works for me like it should until I reboot however.  After which firefox seems unable to connect to the internet until I go back into network manager's manual config and re-enter the password for my wifi network.  The problem is that i have to do this every time I reboot.  (Shouldn't Network manager remember my network password?  Especially when using manual config?)  Hopefully this is just some issue with my personal network though. 

- misterbeetz

---

### Post by jackobean on 2007-10-29
has anyone had any luck with the autologin in gusty? there is a bug report on launchpad (sorry cant remember the link) for the gnome-libpam-keyring package which seems to be the problem.

---

### Post by CoolHand on 2007-12-22
I had this all working previously but to be honest I gave up on it.  Network Manager is only half functional even when you fix these anoying problems.  I removed it completely.  Installed Wifi Radar and life is good.  Good luck to those that insist on trying to make it work but I wish Ubuntu would follow the trend and start including Wifi Radar instead of NM.

---

### Post by superm1 on 2007-12-22
> **CoolHand said:**
> I had this all working previously but to be honest I gave up on it.  Network Manager is only half functional even when you fix these anoying problems.  I removed it completely.  Installed Wifi Radar and life is good.  Good luck to those that insist on trying to make it work but I wish Ubuntu would follow the trend and start including Wifi Radar instead of NM.
Trend?

What other distro is using Wifi Radar by default?

---

### Post by John Wiersba on 2008-01-23
libpam-keyring seems to be a feisty-only solution.  Anything for gutsy?

---

### Post by doorknob60 on 2008-01-24
It doesn't work with autologin...any solutions/alternatives?

---

### Post by krisztian_andre on 2008-03-04
Two new things that I havent seen on the forums and that solved my hibernate problems are:

1. kill wpa_supplicant before hibernating by putting these two lines as the first commands in /etc/acpi/hibernate.sh:

killall wpa_supplicant
sleep 5

2. with gconf-editor under apps/gnome-power-manager/lock  uncheck gnome_keyring_hibernate

---

### Post by yngens on 2008-03-23
This worked perfectly for me:

[http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04](http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04)

---

### Post by blackhole82 on 2008-03-30
I tried this using Xubuntu 7.10 and I still get asked for two passwords when connecting to my wireless network at start up.  I don't remember what I had to do, but I got rid of the password annoyance on another Ubuntu machine.  Hopefully I'll get this one fixed too eventually....

---

### Post by haz2a on 2008-04-06
[COLOR=black]blackhole82 - did you remember how you fixed this yet? Please let us know if you did.

This drives me nuts!
[/COLOR]

---

### Post by ignorabimus on 2008-04-24
> **yngens said:**
> This worked perfectly for me:

[http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04](http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04)

Only took me three days of searching for this but finally!
Thanks yngens and Ulan Melisbek, this is a good workaround for this problem, and don't worry Wicd rocks! This the text from this link:

"Network Manager problem in Ubuntu 8.04 Hardy Heron(works on 7.10 also)

Submitted by Ulan Melisbek on Sat, 2008-03-22 10:50.

Just have installed Ubuntu 8.04 Beta and since I did not like the way it starts up, turned on auto-login. Unfortunately, every time you start Ubuntu after this the Network Manager keeps asking you for your keyring password. Which is very much annoying. So I followed these steps to solve the issue:

1. Go to Administration > Synaptic Package Manager > Settings > Repositories > Third Party Software > Add...

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

(replace 'hardy' with 'dapper', 'edgy', 'feisty' or 'gutsy' according to your system's name).

2. Click Reload and wait while the package lists are downloaded, Search for "Wicd" and install it. The system will warn about that in order to install Wicd you have to uninstall NetworkManager. Response positively and just go ahead and finish the installation.

Don't worry about the message "The NetworkManager applet could not find some required resources. It cannot continue", just close it for now.

3. Go to Applications > Internet > Wicd.

Attention! If Wicd does not run at this stage, then have these instructions copied in some place on your Desktop or Home folder, because you will now need to restart your computer, and after the system loads back you will not have immediate Internet connection to get to these page online!

- Select your wireless network, make sure to put check mark for "Automatically connect to this network".

- Then click to "Advanced Settings", mark up "Use Encryption" and put your WPA or WEP password in the field just below it. If you use MAC filter wireless security, then just omit this step.

- Press "Connect".

4. Go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "Add" button. Give it some name ("Wireless Manager" or "Wicd"). In the command field enter "/opt/wicd/tray.py".

5. Go to System > Administration > Login Window > Security and enable "Automatic Login", close and rock and roll!"

---

### Post by whomever21 on 2008-04-25
has anyone tried this?

---

### Post by lawhorne on 2008-05-19
I just followed the steps listed on 
[http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04]("http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04")

It worked perfectly.  I was trying to avoid having to enter a password after autologon (desktop computer).  This solved my problem.  
Thanks

---

### Post by cutOff on 2008-05-21
> **ignorabimus said:**
> Only took me three days of searching for this but finally!
Thanks yngens and Ulan Melisbek, this is a good workaround for this problem, and don't worry Wicd rocks! This the text from this link:

"Network Manager problem in Ubuntu 8.04 Hardy Heron(works on 7.10 also)

Submitted by Ulan Melisbek on Sat, 2008-03-22 10:50.

Just have installed Ubuntu 8.04 Beta and since I did not like the way it starts up, turned on auto-login. Unfortunately, every time you start Ubuntu after this the Network Manager keeps asking you for your keyring password. Which is very much annoying. So I followed these steps to solve the issue:

1. Go to Administration > Synaptic Package Manager > Settings > Repositories > Third Party Software > Add...

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

(replace 'hardy' with 'dapper', 'edgy', 'feisty' or 'gutsy' according to your system's name).

2. Click Reload and wait while the package lists are downloaded, Search for "Wicd" and install it. The system will warn about that in order to install Wicd you have to uninstall NetworkManager. Response positively and just go ahead and finish the installation.

Don't worry about the message "The NetworkManager applet could not find some required resources. It cannot continue", just close it for now.

3. Go to Applications > Internet > Wicd.

Attention! If Wicd does not run at this stage, then have these instructions copied in some place on your Desktop or Home folder, because you will now need to restart your computer, and after the system loads back you will not have immediate Internet connection to get to these page online!

- Select your wireless network, make sure to put check mark for "Automatically connect to this network".

- Then click to "Advanced Settings", mark up "Use Encryption" and put your WPA or WEP password in the field just below it. If you use MAC filter wireless security, then just omit this step.

- Press "Connect".

4. Go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "Add" button. Give it some name ("Wireless Manager" or "Wicd"). In the command field enter "/opt/wicd/tray.py".

5. Go to System > Administration > Login Window > Security and enable "Automatic Login", close and rock and roll!"

Thanks a lot. Works like a charm.

---

### Post by DJ_Peng on 2008-07-31
I saw that, but I'm not sure if it's what I need since I don't have a wireless network. I simply want to stop Evolution from asking for my password on my computer with autologin. (I'm the only one who uses this box so I don't need the added security of entering my password on boot.) Can someone tell me if this would work for me before I go through the hassle of installing something that may do nothing to resolve my issue?

---

### Post by Grolmania on 2008-11-05
This may be a bit too simple, but I'd just like to mention it for completeness.  My computer did not start asking for the keyring password until I enabled my first password keyring item named "default."  By simply removing this item, "default" form the keyring item list, the annoying screen stopped appearing at computer start-up.  Then if keyrings are required to be stored, I simply do not give a password to be used.  The "default" keyring item is still created once again; but, no screen ever pops up at start-up asking for a password.  Obviously there is no password protection if you use this method.

---

### Post by tekknokrat on 2008-11-06
If you use another dm like slim, it suffices to copy the gdm entry in /etc/pam.d dir to slim.

```
cd /etc/pam.d
cp gdm slim
```

After restart you also wont be asked for keyring-password anymore.
Works at least in intrepid.

---

### Post by rjg_1966 on 2008-11-15
Far easier solution is to reset your password to blank (on Intrepid 8.10):

Do a search (Places / search) for Seahorse (on file system)
Start up Seahorse
Select Edit/Preferences
Select default and select change unlock password
after entering your odl password, for new password just hit line return twice
there will be a warning message that security is low, but this will allow you to connect to Wifi without problem at boot (without being asked!).

Just dont save your other passwords on this keyring if you dont want anyone to access eg your emails!

:)

---

### Post by dwieeb on 2008-11-20
Hi I'm getting an error when I try to configure --prefix blah blah

I've installed all the needed packages but I keep getting this error:

> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
configure: error: cannot run /bin/bash ./config.sub


Anyone know whats going on?

---

### Post by Dec0594 on 2009-02-07
Ok so i follow the code all the way and right when i type in the code i get this:

.......@.......-desktop:~/pam_keyring-0.0.8$ ./configure --prefix=/usr --libdir=/lib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
[COLOR="Red"]configure: error: cannot run /bin/bash ./config.sub[/COLOR]
.......@......-desktop:~/pam_keyring-0.0.8$ 



what an i doing wrong??   ssoooo frustrating:(

---

### Post by surre_sprett on 2009-02-28
Hi, don't know whether this is solved or not, but your problem is that the symbolic links pointing to config.guess, config.sub, and ltmain.sh are broken.. 

I just moved these files to a new folder, and in a terminal typed in:

```
/pam_keyring-0.0.8$ ln -s /usr/share/libtool/config/ltmain.sh
/pam_keyring-0.0.8$ ln -s /usr/share/libtool/config/config.guess
/pam_keyring-0.0.8$ ln -s /usr/share/libtool/config/config.sub
```

---

### Post by danmarycap on 2009-03-12
> **rjg_1966 said:**
> Far easier solution is to reset your password to blank (on Intrepid 8.10):

Do a search (Places / search) for Seahorse (on file system)
Start up Seahorse
Select Edit/Preferences
Select default and select change unlock password
after entering your odl password, for new password just hit line return twice
there will be a warning message that security is low, but this will allow you to connect to Wifi without problem at boot (without being asked!).

Just dont save your other passwords on this keyring if you dont want anyone to access eg your emails!

:)


Thanks for this simple solution -- it works!  Now I just need to get Ubuntu to stop asking for a password on resume from suspend and all will be golden.

-Dan

---

### Post by psavva on 2009-04-10
Here is probably the best solution to this problem

```

http://www.it-labcy.com/Forum/viewtopic.php?f=6&t=3

```

This is not an actual problem with PAM or with Network Manager.

If you have a password specified for seahorse better known as "Passwords and Encryption Keys", it will ask you for the password.

Don't specify a password and it won't ask you for one :)
That easy!!!

---

### Post by psycoticfrenzy on 2009-05-01
I might have had another problem as the rest of you, but all i had to do is check one box to fix this problem.   This is what i did.  Also, i have 9.04. 

Menu > Preferences> Network Connections.

Then i clicked on my Wireless that i have connect automatically when i boot up.  Clicked on Edit.  And at the very bottom it has a box to make the connection available to all users. Check that box.  


That fixed it for me. No codes or terminal or anything.

---

### Post by konza on 2009-05-10
After a couple of days putzing around trying to eliminate the need to enter passwords (as do many judging from the quarries ) i came across a quick and simple click, click, click that works in Intrepid for sure.  It is from the site of a gentleman named Damien. Hope it makes life a bit easier for you too!
[http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)

---

### Post by DJ_Peng on 2009-05-11
Unfortunately that doesn't work from what I see in Jaunty. I went through the tutorial and couldn't find a matching set of info to be able to make the change. But thanks for posting that link so Intrepid users can have it.

---

### Post by djchandler on 2009-05-12
Changed my login password, only to find I need to change it in two places. I had Evolution bugging me for access to the keyring in Jaunty. The fix was to change the password  for login in seahorse.

I wonder why that does not happen automatically, or at least give you a warning if seahorse is installed.

Anyway, thanks to all above who discussed seahorse.

To change the login password in seahorse that is packaged with jaunty, open **seahorse** (2.26.1) at the command line, either by pressing alt-F2 or in the terminal, and typing in **seahorse**. Go to the ***Passwords*** tab (the far right), and right-click on ***Passwords login***. Select **change passwords**, type in your old login password, then enter the new login password twice. 

Problem solved.

---

### Post by Carl H on 2009-05-29
> **psycoticfrenzy said:**
> I might have had another problem as the rest of you, but all i had to do is check one box to fix this problem.   This is what i did.  Also, i have 9.04. 

Menu > Preferences> Network Connections.

Then i clicked on my Wireless that i have connect automatically when i boot up.  Clicked on Edit.  And at the very bottom it has a box to make the connection available to all users. Check that box.  


That fixed it for me. No codes or terminal or anything.

That worked for me. Thanks! :D

---

### Post by ArdeXxX on 2009-11-17
> **psycoticfrenzy said:**
> I might have had another problem as the rest of you, but all i had to do is check one box to fix this problem.   This is what i did.  Also, i have 9.04. 

Menu > Preferences> Network Connections.

Then i clicked on my Wireless that i have connect automatically when i boot up.  Clicked on Edit.  And at the very bottom it has a box to make the connection available to all users. Check that box.  


That fixed it for me. No codes or terminal or anything.

Awesome! That's all it took to make it work without any problems :D

Cheers, mate!

---

### Post by Pancho Pistolas on 2010-01-11
go here:

[http://ubuntuforums.org/showthread.php?t=1378648](http://ubuntuforums.org/showthread.php?t=1378648)

---

### Post by Pancho Pistolas on 2010-01-11
> **ArdeXxX said:**
> Awesome! That's all it took to make it work without any problems :D

Cheers, mate!

sry, didn't read that.

---

### Post by libssd on 2010-05-15
This had been a minor annoyance since a re-install of 9.04. I had never noticed that little "available to all users" checkbox before. Very simple and clean solution. I use a bios password to control access to my machine, so I have autologin defined for both Windows and Ubuntu partitions. Getting rid of the keyring password is one less annoyance to deal with.

---

### Post by calande on 2010-10-03
I followed the how-to but the keyring keeps asking for my password (I'm trying to access a Windows share). How can I nuke the damn thing? :evil:](*,)
Thanks.

---

### Post by JBud on 2010-11-04
Hello,

I followed your guide completely, after over an hour of errors, I finally installed pam keyring, however, while even though my passwords match my login password, it continues to ask me for my keyring passwords on login.



I am running Ubuntu 10.10 Desktop 32-bit on my Acer Aspire 5740 with:
Intel Core i5 430m
4GB Ram
(let me know if you need more information from me.)

---

### Post by cracker89 on 2010-11-04
simplest solution - clean install, and dont change ur password from the one you put in the install. 
Hey, i can bet it'll work!

---

### Post by calande on 2011-05-06
This tutorial still won't work in natty :(

---

### Post by Pithikos on 2011-06-02
The "connection available to all users" fixed my issue too on Crunchbang. Though pay attention that you even have to add the connection's password on the second tab or else the marking of the option will roll back to unchecked.

---

### Post by cirobr on 2011-10-02
It works on Lucid. Thanks.

> **djchandler said:**
> Changed my login password, only to find I need to change it in two places. I had Evolution bugging me for access to the keyring in Jaunty. The fix was to change the password  for login in seahorse.

I wonder why that does not happen automatically, or at least give you a warning if seahorse is installed.

Anyway, thanks to all above who discussed seahorse.

To change the login password in seahorse that is packaged with jaunty, open **seahorse** (2.26.1) at the command line, either by pressing alt-F2 or in the terminal, and typing in **seahorse**. Go to the ***Passwords*** tab (the far right), and right-click on ***Passwords login***. Select **change passwords**, type in your old login password, then enter the new login password twice. 

Problem solved.

---

