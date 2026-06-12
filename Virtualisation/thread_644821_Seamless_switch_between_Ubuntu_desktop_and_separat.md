---
title: "Seamless switch between Ubuntu desktop and separate vitual machine"
date: 2007-12-19
forum: Virtualisation
---

### Post by cronosxfiles on 2007-12-19
Hello, 

  I hope this, my first post on these forums, doesn't seem too obvius to be asked. 
  I've just removed my Windows XP and installed Ubuntu Server. I've also installed the desktop environment and VMWare server. As I should/want to keep using Windows on my PC, I'll have a couple of virtual machines running on VMWare. However, I would like to make one of those Windows available to someone else without requiring this user to log into Ubuntu and start a virtual Windows system. 
  I thought I could have the virtual machines on full screen and associated to Ubuntu terminals that could be switched simply by typing Alt+F1/Alt+F2/etc... Now I'm not so sure since I think there can be only one graphical environment on terminal 8/9 (Alt+F8/Alt+F9) - please correct me on this. This way, the user could just know which was it's terminal or searh for it trying with the keyboard.
  Thinking this idea wasn't feasible; I've thought about having each virtual machine running maximized on a desktop, but this way the second user would need to have access to my account or maybe to an second Ubuntu user account which would restrict simplicity to this process. Security is not a concern here, but sometimes you should be aware of what users with little knowledge could do just by clicking around. They just don't mind shutting down your system since they think is as safe as turning a calculator off. To end this second idea, it it possible to lock only one of several desktops under an open user account?
  Maybe if there was a way to have a virtual machine stuck to a user account desktop, limiting access to anything else on the environment: applications, terminal windows, etc...; and without the possibility that there could be a switch between the guest and the host OS.
  Have I made myself clear of what I whant with so many words? :( Are you still reading? :) Maybe no. 

  Thanks in advance for any help or hint on this. Feel free to do as many questions as you need to make myself a bit clear. 

  Regars, JM

---

### Post by cronosxfiles on 2007-12-21
No hint on this yet? Anyone? 

  I've found this on another post which appears on a message screen when installing ubuntu-desktop (GNOME):

[COLOR="Navy"][FONT="Courier New"]"(Multiple display managers can run simultaneously if they are configured to manage different servers; to achieve this, configure the display managers accordingly, edit each of their init scripts in /etc/init.d, and disable the check for a default display manager.)"[/FONT][/COLOR]

  Does this confirm that there can be only one desktop environment running on a single installation? :confused:
  Is it possible to have what I'm propossing on this post and also by somebody else on post [post=81773]_[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=81773[/COLOR]_[/post]?

  Thanks in advance for any help. 

  Regards, JM

---

### Post by Bq32 on 2007-12-22
> **cronosxfiles said:**
> 
  Maybe if there was a way to have a virtual machine stuck to a user account desktop, limiting access to anything else on the environment: applications, terminal windows, etc...; and without the possibility that there could be a switch between the guest and the host OS.


Do you want to switch it right away, or just use one(Ubuntu), and next time, use the other(Windows)?

---

### Post by HermanAB on 2007-12-23
Running a VM is exactly the same as running a separate machine.  Therefore, enable remote control in the Windows VM and let the other user log in via Windows  RDP or Linux rdesktop.

Cheers,

Herman

---

### Post by cronosxfiles on 2007-12-24
> **Bq32 said:**
> Do you want to switch it right away, or just use one(Ubuntu), and next time, use the other(Windows)?

  I would like something like switching between an Ubuntu session and a Windows virtual machine using (e.g.) Alt-F7/Alt-F8 

  So far I've created a second (basic) user account where the Windows user can open the Windows virtual machine or a remote desktop session to it. But the graphical user interface is not as comfortable (from what I've seen) as the one on Windows for switching between user accounts without the need to log them off. 
  Thanks for replying. 

  Cheers, JM

---

### Post by cronosxfiles on 2007-12-24
> **HermanAB said:**
> Running a VM is exactly the same as running a separate machine.  Therefore, enable remote control in the Windows VM and let the other user log in via Windows  RDP or Linux rdesktop.

Cheers,

Herman

  It seems the best option so far. But implies the user to get into a Linux session before having it's Window available. I suppose I could find how to run the remote desktop session right when the user logs in and the virtual machine could be started when Ubuntu starts as well. 
  Thanks for replying. 
  Cheers, JM

---

