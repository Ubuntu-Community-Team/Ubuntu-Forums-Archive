---
title: "Problems with Graphics"
date: 2012-08-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Krabby.Linux on 2012-08-28
I accidently switched to Ubuntu 12.10. I got an E-Mail from the Mailing List saying that there is a new Ubuntu Version (Later i figured out it was 12.04.1) and i upgraded to 12.10 cause i thought its stable :-) <-- Idiot.

So I have 1 Major Problem I need to fix as soon as possible. I have Problems with my Graphics Card drivers ... Catalyst C. Center tells me that there are no drivers installed (I installed the new Catalyst drivers twice). The next point is, that i cant access the System Config. If i am running gnome-control-center in Terminal I get this error message:

```

(gnome-control-center:6192): Gdk-ERROR **: The program 'gnome-control-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 145 error_code 1 request_code 153 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I know its my fault, that i upgraded to 12.10 but is there a way to fix that Problem?

Thanks!


[B]Switched from 12.04 to 12.10 [Ubuntu]
ATI Radeon HD 6950 Graphics Card[/B]

---

### Post by effenberg0x0 on 2012-08-28
> **Krabby.Linux said:**
> I accidently switched to Ubuntu 12.10. I got an E-Mail from the Mailing List saying that there is a new Ubuntu Version (Later i figured out it was 12.04.1) and i upgraded to 12.10 cause i thought its stable :-) <-- Idiot.

So I have 1 Major Problem I need to fix as soon as possible. I have Problems with my Graphics Card drivers ... Catalyst C. Center tells me that there are no drivers installed (I installed the new Catalyst drivers twice). The next point is, that i cant access the System Config. If i am running gnome-control-center in Terminal I get this error message:

```

(gnome-control-center:6192): Gdk-ERROR **: The program 'gnome-control-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 145 error_code 1 request_code 153 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I know its my fault, that i upgraded to 12.10 but is there a way to fix that Problem?

Thanks!


[B]Switched from 12.04 to 12.10 [Ubuntu]
ATI Radeon HD 6950 Graphics Card[/B]

I'm not sure that specific g-c-c problem would be caused by VGA. I'm no ATI specialist, other guys here can offer better advice. 

IMO, g-c-c usually crashes for other reasons, such as wrong modes/permissions in specific files/folders, wrong/conflicting libs, even problems with themes and locale. If you'll keep 12.10, make sure you have proper Quantal repositories inside /etc/apt/sources.list and also check your PPAs in /etc/apt/sources.list.d (ppa-purge stuff you're not sure). If you're comfortable with sources and PPAs, make sure QQ is fully upgraded (sudo apt-get update && sudo apt-get upgrade) before you start playing with drivers and stuff. 

A possible way to debug this g-c-c problem would be to strace it, like this:

```
strace -t -f -e open gnome-control-center
```

If g-c-c is crashing consistently, strace will exit when g-c-c crashes and you can then scroll up at the terminal to understand at which point that happened. We're filtering "open" calls because I have a guess you'll come back with a "open <somelib>" line as the culprit here. But that's just my guess. You can also not filter "open" and just look at the entire trace, like this:

```
strace -t -f gnome-control-center
```

Regards,
Effenberg

---

### Post by Krabby.Linux on 2012-08-28
Thanks a lot for your Help. I dont fully understand everything you said but i tried to use strace and it has shown that there is a massive amount of "(No such file or directory)" errors. 

I have switched from English Language to Spanish languag in 12.04. Since lots of the errors are on Spanish Language Files... Can this be the Problem? Do i have to switch back to english? How can i do that without open the System Config?

EDIT: I managed to change the language to en_US using the terminal. Errors are still there after reboot :(

---

### Post by effenberg0x0 on 2012-08-28
> **Krabby.Linux said:**
> Thanks a lot for your Help. I dont fully understand everything you said but i tried to use strace and it has shown that there is a massive amount of "(No such file or directory)" errors. 

I have switched from English Language to Spanish languag in 12.04. Since lots of the errors are on Spanish Language Files... Can this be the Problem? Do i have to switch back to english? How can i do that without open the System Config?

EDIT: I managed to change the language to en_US using the terminal. Errors are still there after reboot :(


Keep in mind I'm still guessing, because we have seen no specific error message/log. I've seen people reporting g-c-c crashes due to locale problems / language files. In this case, I think I'd probably try this:

Display the locales available in my system
```
locale -a 
```
Check what locale is set in environment variables:
```
env | grep -i lang
```
Depending on the results, I'd probably try:
```
sudo apt-get install --reinstall language-pack-es language-pack-es-base 
```
(and I'd probably do the same for the English packs just in case)
And just to be extra-sure:
```
sudo dpkg-reconfigure locales
```

Then restart the session. By the way, we know of a bug in which we have Ubuntu crashing right after install/update exactly when it is installing languages. If that's the case, you might even try to see if you have stuff waiting to be installed properly with:
```
sudo apt-get install -f
```

One other thing, you can see f it works when you set the environment variables to other locale temporarily, just to launch gnome-control-center. Like this:

```
LANGUAGE=pt_BR.UTF-8 LANG=pt_BR.UTF-8 gnome-control-center
```
(This is for Brazilian Portuguese. You will get the language codes you have available from running locale -a)

Regards,
Effenberg

---

### Post by Krabby.Linux on 2012-08-29
It didnt worked but first i just want to thank you so much for your nice help!!!

I tried everything you said. I changed Language to en_US just to be sure. Its still the same error:
```
(gnome-control-center:8307): Gdk-ERROR **: The program 'gnome-control-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 146 error_code 1 request_code 153 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)

```

I googled but it seems that there is noone having the same Problem :-(

---

### Post by effenberg0x0 on 2012-08-29
> **Krabby.Linux said:**
> It didnt worked but first i just want to thank you so much for your nice help!!!

I tried everything you said. I changed Language to en_US just to be sure. Its still the same error:
```
(gnome-control-center:8307): Gdk-ERROR **: The program 'gnome-control-center' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 146 error_code 1 request_code 153 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap (core dumped)

```

Hi, 

Yeah, to tell you the truth I Googled your situation and error message for quite a while last night and although I found some similar bugs, nothing is really conclusive. The error message is too generic.

I think there's another possibility to work around this problem. If this issue is caused by user-specific settings (not global/system wide settings), you might consider creating a new user.

If you'd like to try it, run this on console:
```
sudo adduser anynewusername

```

Then reboot and login using this new username. The new user settings will be defaults. Desktop settings, etc, will look different. Try to use gnome-control-center with this new user and report back. If you still have the same problem, we can discard user-specific settings and focus only on global/system wide settings.

Regards,
Effenberg

---

### Post by jfernyhough on 2012-08-30
IIRC I had this problem when the system was using the fglrx kernel module built for an old kernel; X will load the driver but it won't work correctly throwing all sorts of errors like those above, normally when loading programs that try to use accelerated graphics.

When you're installing the AMD driver it's not actually installing; the installer runs but the driver module isn't being built. But, because of the old version, it appears as though things should work. But they won't!

You need to purge fglrx and use the open-source drivers for now (until xserver 1.13 is supported, unless you can handle downgrading to 1.12 manually), something along the lines of:

$ sudo apt-get purge fglrx fglrx-updates
$ sudo mv /etc/X11/xorg.conf /etx/X11/xorg.conf.amdbackup

and reboot.

---

### Post by Krabby.Linux on 2012-08-30
> **jfernyhough said:**
> IIRC I had this problem when the system was using the fglrx kernel module built for an old kernel; X will load the driver but it won't work correctly throwing all sorts of errors like those above, normally when loading programs that try to use accelerated graphics.

When you're installing the AMD driver it's not actually installing; the installer runs but the driver module isn't being built. But, because of the old version, it appears as though things should work. But they won't!

You need to purge fglrx and use the open-source drivers for now (until xserver 1.13 is supported, unless you can handle downgrading to 1.12 manually), something along the lines of:

$ sudo apt-get purge fglrx fglrx-updates
$ sudo mv /etc/X11/xorg.conf /etx/X11/xorg.conf.amdbackup

and reboot.

hey, thanks for your help.

Were can i get the open source drivers?

thanks

---

### Post by jfernyhough on 2012-08-30
The open-source drivers are installed by default. They're already on your system.

---

### Post by Krabby.Linux on 2012-09-01
> **jfernyhough said:**
> IIRC I had this problem when the system was using the fglrx kernel module built for an old kernel; X will load the driver but it won't work correctly throwing all sorts of errors like those above, normally when loading programs that try to use accelerated graphics.

When you're installing the AMD driver it's not actually installing; the installer runs but the driver module isn't being built. But, because of the old version, it appears as though things should work. But they won't!

You need to purge fglrx and use the open-source drivers for now (until xserver 1.13 is supported, unless you can handle downgrading to 1.12 manually), something along the lines of:

$ sudo apt-get purge fglrx fglrx-updates
$ sudo mv /etc/X11/xorg.conf /etx/X11/xorg.conf.amdbackup

and reboot.


This does not work. It says: 


Package 'fglrx' is not installed, so not removed
Package 'fglrx-updates' is not installed, so not removed

Adding a new username does not work and results in the same errors.

---

