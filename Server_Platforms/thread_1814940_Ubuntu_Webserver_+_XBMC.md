---
title: "Ubuntu Webserver + XBMC"
date: 2011-07-30
forum: Server Platforms
---

### Post by donniezazen on 2011-07-30
I am having a little trouble running both Xbmc and Ubuntu-server on same machine.

I had a ubuntu-server running apache, subsonic, webmin, etc. I installed xbmc using their wiki. I have problem running both at same time. It boots directly to xbmc and would not run Ubuntu-server. If i close xbmc logon to server and then run xbmc, both works.

Do you run both xbmc and Ubuntu-server on same machine?

Since i can't keep server near Ethernet port i have to run wifi on it. I have to run wpa_supplicant command after each login and leave that screen on. Can it be automated?

My laptops screen doesn't work. And resolution is messed up on monitor. The maxmium i get is 1024x7xx but my dell monitor has a resolution of 2048x1152. I wrote a modeline for correct resolution using this thread [http://forum.xbmc.org/showthread.php?t=54685](http://forum.xbmc.org/showthread.php?t=54685) but it is not working. I have to keep screen because without it wifi won't work. It is little frustrating to go up to TV station and press fn+f8 so it switches to monitor. (i will probably buy a linux friendly usb network adapter and get rid of screen altogether).

Any help will be appreciated.

Thanks.

---

### Post by papibe on 2011-07-30
Could you explain a little more?
Did you install Ubuntu Server and XBMC on a laptop? Or,
Do you have a server and a laptop?

BTW, I'm using XBMC and I have a server, but they are installed on different machines though.

Regards.

---

### Post by donniezazen on 2011-07-30
> **papibe said:**
> Could you explain a little more?
Did you install Ubuntu Server and XBMC on a laptop? Or,
Do you have a server and a laptop?

BTW, I'm using XBMC and I have a server, but they are installed on different machines though.

Regards.

Sorry for not being clear.

I already had Ubuntu-server running apache, ssh, webmin, subsonic, samba, Transmission,etc on Dell Inspiron E1505. I thought why not install XBMC on it and hook it permanently to Dell SP2309W external monitor. Laptop's screen is broken but it is needed for wifi to work.

My question is  I want to run both XBMC and Ubuntu server on same machine. I do not need GUI for Ubuntu Server. I want to keep XBMC on and ubuntu server running in background. Do you think this should work in theory without any glitch?

I have now installed to Ubuntu Desktop to familiar myself with XBMC and then i would like to go back to command line server and XBMC GUI.

Is WPA_Supplicant the best way to manage wifi through command line? I had it working but i had to initiate it every time i reboot. It would be great if it works as a start job.

I was unable to get right resolution on my external monitor. I have now unhooked LCD cable keeping wifi connections, so, it should probably work this time.

Thanks.

---

