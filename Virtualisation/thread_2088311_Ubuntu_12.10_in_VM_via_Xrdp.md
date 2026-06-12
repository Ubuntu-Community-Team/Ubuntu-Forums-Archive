---
title: "Ubuntu 12.10 in VM via Xrdp"
date: 2012-11-26
forum: Virtualisation
---

### Post by ozxpat on 2012-11-26
Gentlemen and Ladies, 

I'm trying to find out why my new installation of Ubuntu 12.10 via xrdp does not show any icons, 12.04 still runs well.

I have just installed an new release Ubuntu 12.10 64bit server (no problems). On this I run VirtualBox 4.2.4 with 3 OS's 1) Ubuntu 12.04 32bit, 2) Windows XP and 3) Ubuntu 12.10 32bit.
Both 12.04 and XP run without any problems however 12.10 is giving nothing but problems. During installation in VBox I get all the icons and everything seems too work fine. After I start it up as vboxheadless I get the background but no icons when I use sesman-Xvnc and console options. Options sesman-any, rdp-any and sesman-X11rdp give errors and hang. Only option vnc-any gave access to full desktop but once. After that nada. The only way out is to kill the rdp session or shutdown the VM.
I (attempt to) logon via rdp on Windows 7 and Vista. 

I realise the info is limited but with the right questions I should be able to supply more.

Thanks
Ron

---

### Post by coffeecat on 2012-11-26
Not a Forum Feedback & Help question. *Thread moved to **Virtualisation**.*

@ozxpat, I've moved this to the virtualisation forum as this seems most appropriate, but if you would prefer a different technical support forum, send a move request to the staff area by means of the the [img]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/img] button in your post. Don't worry that it says "report abuse". You can use it for any occasion where staff attention/action is needed.

---

### Post by ozxpat on 2012-11-27
> **coffeecat said:**
> Not a Forum Feedback & Help question. *Thread moved to **Virtualisation**.*

@ozxpat, I've moved this to the virtualisation forum as this seems most appropriate, but if you would prefer a different technical support forum, send a move request to the staff area by means of the the [img]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/img] button in your post. Don't worry that it says "report abuse". You can use it for any occasion where staff attention/action is needed.
Thanks Coffeecat, 
I don't mind where this goes as long as I get some tips as to the direction I should be looking.

As additional info I think it's in the 32 bit version of 12.10 (12.04 works fine) or in combination with the vbox headless (with in installation lens works fine). 

I hope someone has some ideas.

thanks
Ron

---

### Post by fcipriani on 2012-11-29
xrdp never really worked with Unity. Before 12.10 it could be configured with Unity 2d, but now Unity 2d has been removed: 

[https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/846407](https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/846407)

You can still make it work using the gnome fallback desktop interface:

[http://c-nergy.be/blog/?p=3518](http://c-nergy.be/blog/?p=3518)

---

### Post by ozxpat on 2012-12-01
Thanks [fcipriani]("http://ubuntuforums.org/member.php?u=1760712"),
 I had found this fix however it didn't work. I keep getting connection errors. I tried all the connection variations but again nada. I tried restalling it again, same result.
As soon as I get a chance I'll re-install from scratch and see if that's any better.
Will report regardless of result.

Ron

---

### Post by ozxpat on 2012-12-04
Have succeeded in doing a re-install of 12.10 32 bit desktop, xrdp and Gnome-fallback under the VirtualBox Manager . I can now do a remote logon however still have 2 (potential) problems.
1) the xterm box is black and I can't type into it. ie cant disconnect.
2) I get the folowing error message in the xsession-errorlog
  ** (gnome-session:6734): WARNING **: Caouldn't connect to accessibility bus: Failed to connect to socket / tmp/dbus-AK6p5l9uC2: Connection refused.
The latter could be because I killed the rdp box however now I can start it under VNC headless.

Ah well these things are meant to try us... and don't they ever.

---

### Post by ozxpat on 2012-12-04
Oops my mistake... forgot to remove the virtual installation disk.

Please close this issue

---

