---
title: "VirtualBox and full screen mode"
date: 2014-04-17
forum: Virtualisation
---

### Post by Luft on 2014-04-17
I just downloaded Ubuntu 14.04 64 bit Desktop and donated money to the project (something I hope everyone does).  

I want to try it out in a VurtualBox session running on Ubuntu 13.10.  Everything installs fine but when I switch to full screen mode (Right-CNTL-F) the main window is expanded but the session running inside is still truncated.

This is fairly well documented [here]("http://askubuntu.com/questions/247629/how-do-i-display-the-whole-desktop-in-virtual-box-fullscreen-mode").  It seems that one must install the Guest Additions which is fairly well documented [here]("http://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-virtualbox").

When I did this I saw a message telling me that the kernel headers were not found and that if the install didn't work that may be the reason.  There were no errors but after the install full screen mode still was not working properly.

So I tried to install the headers which is documented [here]("http://askubuntu.com/questions/75709/how-do-i-install-kernel-header-files").

I saw a message telling me that the headers were already the newest headers.  I'm at a loss as to what to do next.  Help anyone? :p

---

### Post by ibjsb4 on 2014-04-18
Have you installed dkms and build-essential on the host?


```
sudo apt-get install dkms build-essential

```

---

### Post by QIII on 2014-04-18
Hello!

Install build-essential and dkms on the *guest, *since that is where the Guest Additions are installed.  But I don't recall that they are required.

You probably need to install linux-headers-*generic.*

```
sudo apt-get install linux-headers-generic
```

and then try to install the Guest Additions again.

---

### Post by Luft on 2014-04-19
> **ibjsb4 said:**
> Have you installed dkms and build-essential on the host?


```
sudo apt-get install dkms build-essential

```
Thank you!

I did install dkms but not the build-essential package.

I had to start with a fresh install of virtualbox on a fresh install of Ubuntu but it now works!

Thank you!

---

### Post by Luft on 2014-04-19
Thank you for your reply.  I got the same headers already the newest message.  But the issue is resolved .  I hadn't installed the build-essential package.  BTW I don't know how to mark this thread as resolved.:confused::confused:

---

### Post by vishal6 on 2014-07-31
[TABLE]
[TR]
[TD="class: votecell"]     down vote        
              [/TD]
                [TD="class: answercell"]                  If you have problem of Full screen  Just Install Virtualbox 4.3.8 It would be work 
  After hard-work of 3 days i uninstall Old or new virsion of virtualbox and installed 4.3.8
After installation, don't do anything just Click on Devices and then  cleck on install Guest Additions..and after some process then reboot and  finally  You will get what you want really....
  Don't forget to Reboot after process 
  Thnks
      
[/TD]
[/TR]
[/TABLE]

---

