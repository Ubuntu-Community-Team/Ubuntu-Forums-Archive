---
title: "Post your favorite Splashy themes for Gutsy"
date: 2007-10-28
forum: The Cafe
---

### Post by RAV TUX on 2007-10-28
reference:

[http://splashy.alioth.debian.org/wiki/themes](http://splashy.alioth.debian.org/wiki/themes)

---

### Post by RAV TUX on 2007-10-28
> **RAV TUX said:**
> reference:

[http://splashy.alioth.debian.org/wiki/themes](http://splashy.alioth.debian.org/wiki/themes)

I found fingerprint to be the coolest!

I just have to figure out how to install it...

reference:
[http://splashy.alioth.debian.org/wiki/themes/contrib](http://splashy.alioth.debian.org/wiki/themes/contrib)

---

### Post by tbroderick on 2007-10-28
I turn off all bootsplashes.

---

### Post by RAV TUX on 2007-10-28
So Splashy comes with the following themes by default:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=48099&d=1193555332[/IMG]

My question is how do I unpack the tarball so I can add the "fingerprint" splashy theme here to the other options?

---

### Post by FuturePilot on 2007-10-28
It seems to be broken 
```
sudo splashy test
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
```

---

### Post by RAV TUX on 2007-10-28
> **FuturePilot said:**
> It seems to be broken 
```
sudo splashy test
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
```
Did you install or extract any themes yet,...the test won't work if that hasn't been done.

The test comes up with an error because it hasn't been assigned a theme yet.

---

### Post by FuturePilot on 2007-10-28
> **RAV TUX said:**
> Did you install or extract any themes yet,...the test won't work if that hasn't been done.

The test comes up with an error because it hasn't been assigned a theme yet.

Yes, I have set a theme
```
sudo splashy_config --s ubuntusplashy
>Set theme as: ubuntusplashy          [ DONE ]

```

---

### Post by RAV TUX on 2007-10-28
Anyway check this Splashy theme out it so damn hot it has to work.

---

### Post by RAV TUX on 2007-10-28
> **FuturePilot said:**
> Yes, I have set a theme
```
sudo splashy_config --s ubuntusplashy
```maybe the ubuntusplashy theme is broken, have you tried the fingerprint splashy theme yet?

---

### Post by FuturePilot on 2007-10-28
> **RAV TUX said:**
> Anyway check this Splashy theme out it so damn hot it has to work.
Very nice!
> **RAV TUX said:**
> maybe the ubuntusplashy theme is broken, have you tried the fingerprint splashy theme yet?
```
sudo splashy_config --s default
>Set theme as: default          [ DONE ]
sudo splashy test
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
```
:(

---

### Post by RAV TUX on 2007-10-28
OK I set Debian-Cubism as the theme just to test it...

```
ravtux@CafeLinux:~$ sudo sudo splashy_config --s debian-cubism
>Set theme as: debian-cubism          [ DONE ]
ravtux@CafeLinux:~$
```

---

### Post by Frak on 2007-10-28
Here's mine

---

### Post by RAV TUX on 2007-10-28
> **FuturePilot said:**
> Yes, I have set a theme
```
sudo splashy_config --s ubuntusplashy
>Set theme as: ubuntusplashy          [ DONE ]

```
I get the same message, something is set up in Ubuntu that is blocking this...

I need to find a Debian HowTo to bypass this...

---

### Post by RAV TUX on 2007-10-28
> **Frak said:**
> Here's minewait you got it working...

Please post How...

starting with how do I unpack the tarball, every time I try to unpack it I get a message that says I don't have authorization. 

How do I run in root all the time so I don't get this whacky message.

---

### Post by Frak on 2007-10-28
I just unpacked as a folder in my home folder and ran
```
cd
cd ~/
sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
sudo update-alternatives --config usplash-artwork.so
sudo update-initramfs -u
```

Then I run the splashy_config commands.

---

### Post by RAV TUX on 2007-10-28
> **Frak said:**
> I just unpacked as a folder in my home folder and ran
```
cd
cd ~/
sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
sudo update-alternatives --config usplash-artwork.so
sudo update-initramfs -u
```Then I run the splashy_config commands.

OK this is what I got:
```

root@CafeLinux:/home/ravtux# cd
root@CafeLinux:~# cd ~/
root@CafeLinux:~# sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
cp: cannot stat `usplash-theme-fingerprint.so': No such file or directory
root@CafeLinux:~# sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
root@CafeLinux:~# sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-xubuntu.so). Nothing to configure.
root@CafeLinux:~# sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
root@CafeLinux:~# sudo splashy_config --s fingerprint
>Set theme as: fingerprint          [ FAIL ]
root@CafeLinux:~# sudo splashy_config --s usplash-theme-fingerprint.so
>Set theme as: usplash-theme-fingerprint.so          [ FAIL ]
root@CafeLinux:~#    
```

---

### Post by RAV TUX on 2007-10-28
wait is usplash and spalshy the same?

---

### Post by tbroderick on 2007-10-28
> **RAV TUX said:**
> wait is usplash and spalshy the same?

No. Ubuntu uses usplash by default. The fingerprint theme is here:

[http://u-fingerprint.sourceforge.net/](http://u-fingerprint.sourceforge.net/)

As for your error:

*cp: cannot stat `usplash-theme-fingerprint.so': **No such file or directory***

You need to specify the path. sudo cp /path/to/usplash-theme-fingerprint.so /usr/lib/usplash. Or cd to the folder where it's contained. Then the rest of the commands should work.

---

### Post by blueeyesmike on 2007-10-31
> **FuturePilot said:**
> It seems to be broken 
```
sudo splashy test
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
```

I have the same problem :( anyone have a way to fix this yet?

---

### Post by -grubby on 2007-10-31
> **RAV TUX said:**
> Anyway check this Splashy theme out it so damn hot it has to work.

Nice! I use that as my splash screen for KDE

---

### Post by blueeyesmike on 2007-10-31
Ok sorted out the problem for me. It was to do with no frame buffer modules being loaded at, I'm using Gutsy and this fixed it but i'm not sure if this is a problem for other releases. Anyway following the instructions at [http://ubuntuforums.org/showthread.php?p=3593262]("http://ubuntuforums.org/showthread.php?p=3593262") fixed the problem for me as well as fixing my virtual terminals. I also Used the version of splashy that is available at [http://splashy.alioth.debian.org/ubuntu/]("http://splashy.alioth.debian.org/ubuntu/")

hope this helps

---

### Post by applegrew on 2008-01-08
> **FuturePilot said:**
> It seems to be broken 
```
sudo splashy test
Splashy ERROR: Couldn't splashy_start_splashy(). Error -2
```
Well I too was getting this error but running splashy test as root, i.e. sudo splashy test worked!

But anyway I still see the default kubuntu splash screen, not the splashy one. I installed splashy and its themes from ubuntu's repo.

---

### Post by haarvik on 2009-01-20
I get the same thing.  I know it works because I can get the default Ubuntu splashy screen.  So why can't I set it to a different theme?

---

### Post by FuturePilot on 2009-01-20
> **haarvik said:**
> I get the same thing.  I know it works because I can get the default Ubuntu splashy screen.  So why can't I set it to a different theme?

The Ubuntu splash screen that you see is not Splashy but Usplash. Splashy gives this error if it can't find a framebuffer device to use. See this bug report.
[https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/92276]("https://bugs.launchpad.net/ubuntu/+source/splashy/+bug/92276")

---

