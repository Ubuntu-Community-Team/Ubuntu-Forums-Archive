---
title: "Security issue: Locked computer and Virtualbox"
date: 2012-01-16
forum: Security
---

### Post by LordVeovis on 2012-01-16
How to reproduce: 
Virtualbox running an OS that does not support keyboard and mouse integration that currently has captured the keyboard and mouse.  Wait for your time out to have the screen locked.

Effect: You come back into the computer not being prompted for a password and will continue to not be prompted for a password until your focus changes away from Virtualbox, at which point you will immediately be prompted for a password.

This poses HUGE security problems as someone has complete access to your VM without needing to know your user information.

---

### Post by Dangertux on 2012-01-16
I'm not sure how I understand that this is a security issue, if you attempt to do something on the guest system you are not prompted for a password, however if you attempt to move into the host you will be?

You can not expect a desktop environment to protect a virtualized OS, it doesn't work that way.

I might be misunderstanding you though. Also I can't reproduce what you're doing.

---

### Post by Azdour on 2012-01-16
Hi,

I think what the OP is saying and I have seen this too, but rarely in Ubuntu 10.04, is the following:

Lets say the screen-saver is set up to kick in after 20 minutes of inactivity and to lock the machine. 

I am running VirtualBox and after 20 minutes of inactivity the screen-saver does not kick in until the VirtualBox window looses focus.

This means the computer never locks and people can use your VirtualBox on your machine. If they try and do anything else with Ubuntu then the screen-saver and lock kicks in. It's as if it had been waiting because it was somehow blocked by an in-focus VirtualBox window (not that I think this is the what the issue is, just coming at it from a developers angle).

That being the case, it has been said on many occassions on this forum that having direct access to a machine is always a security vulnerability.

---

### Post by Dangertux on 2012-01-16
> **Azdour said:**
> Hi,

I think what the OP is saying and I have seen this too, but rarely in Ubuntu 10.04, is the following:

Lets say the screen-saver is set up to kick in after 20 minutes of inactivity and to lock the machine. 

I am running VirtualBox and after 20 minutes of inactivity the screen-saver does not kick in until the VirtualBox window looses focus.

This means the computer never locks and people can use your VirtualBox on your machine. If they try and do anything else with Ubuntu then the screen-saver and lock kicks in. It's as if it had been waiting because it was somehow blocked by an in-focus VirtualBox window (not that I think this is the what the issue is, just coming at it from a developers angle).

That being the case, it has been said on many occassions on this forum that having direct access to a machine is always a security vulnerability.

That makes sense though, if the mouse/keyboard are captured. I don't know. I am not a Ubuntu Developer so I'm not sure if this is "working as intended" or not, I just don't see how else it would work since Vbox captures your mouse/key input.

---

### Post by Habitual on 2012-01-16
> **dangertux said:**
> ...you can not expect a desktop environment to protect a virtualized os, it doesn't work that way.

+1

---

### Post by CharlesA on 2012-01-16
I would think that it would be easier/better to just lock the machine when you walk away. *shrug*

---

### Post by LordVeovis on 2012-01-16
> **Dangertux said:**
> You can not expect a desktop environment to protect a virtualized OS, it doesn't work that way.

Not expecting a host system to protect the guest, I am expecting the host system that is set to lock the system after a given period of time to actually lock the system.


> **Azdour said:**
> Hi,

I think what the OP is saying and I have seen this too, but rarely in Ubuntu 10.04, is the following:

Lets say the screen-saver is set up to kick in after 20 minutes of inactivity and to lock the machine. 

I am running VirtualBox and after 20 minutes of inactivity the screen-saver does not kick in until the VirtualBox window looses focus.

This means the computer never locks and people can use your VirtualBox on your machine. If they try and do anything else with Ubuntu then the screen-saver and lock kicks in. It's as if it had been waiting because it was somehow blocked by an in-focus VirtualBox window (not that I think this is the what the issue is, just coming at it from a developers angle).

That being the case, it has been said on many occassions on this forum that having direct access to a machine is always a security vulnerability.

Yes that is basically what I am saying.  The 'screen saver' (which I have none set, just set to lock the system) DOES kick in, aka screen fades to black as it would when it locks, however you are not prompted for a PW until you lose focus on the VM.

Also on the note of direct access I am fully aware that direct access will bypass 99.9% of security on the system.  I have luks encryption on it as well which add least places some barriers in the way.  Aside from that there is a significant amount of time involved (in terms of my situation) with getting access to the system.  There is a difference in someone coming in the room and moving the mouse and seeing what you are doing and sitting down at the computer with full access trying to get at your data.  I am more concerned with the former.

---

### Post by LordVeovis on 2012-01-16
> **CharlesA said:**
> I would think that it would be easier/better to just lock the machine when you walk away. *shrug*

You are right, it is safer to do so, but not always practical as I then have to leave the guest session to manually lock the system as you cannot lock it while your guest has focus.

---

### Post by Ms. Daisy on 2012-01-16
Why don't you just set the OS inside of the VM to require a password upon wake up?  That way everything requires a password no matter where the mouse is captured.

---

### Post by georgemc on 2012-01-16
Not sure if this is a bug or just normal behavior.  Ran across this awhile back and dismissed it as a quirk in Gnome2 or X11.
 

 It can be easily reproduced by just clicking on a pull down menu and letting the cursor sit there (see the enclosed picture).  This is not just limited to VM s.
 

 The good thing is that when you click the cursor any where else the screen saver and locking mechanism do kick in.   
 

 The security exposure would be that the screen remains visible and appears to be unsecured, until someone clicks anywhere else.  For example: if you go to the pull down menu to lock the screen and just leave the cursor over &#8220;Lock Screen&#8221; and OOPS do not click on the item, then this will happen too.
 

 I am using 10.04.3LTS Ubuntu with the standard Gnome2.
 
Q:    	 	 	 	 	 	   Can this be reproduced in the other DE s like KDE, Gnome3, Unity, XFCE?
  
 Interesting
 

 George

---

### Post by LordVeovis on 2012-01-16
> **georgemc said:**
> Not sure if this is a bug or just normal behavior.  Ran across this awhile back and dismissed it as a quirk in Gnome2 or X11.
 

 It can be easily reproduced by just clicking on a pull down menu and letting the cursor sit there (see the enclosed picture).  This is not just limited to VM s.
 

 The good thing is that when you click the cursor any where else the screen saver and locking mechanism do kick in.   
 

 The security exposure would be that the screen remains visible and appears to be unsecured, until someone clicks anywhere else.  For example: if you go to the pull down menu to lock the screen and just leave the cursor over “Lock Screen” and OOPS do not click on the item, then this will happen too.
 

 I am using 10.04.3LTS Ubuntu with the standard Gnome2.
 
Q:    	 	 	 	 	 	   Can this be reproduced in the other DE s like KDE, Gnome3, Unity, XFCE?
  
 Interesting
 

 George

That's right, I forgot you could get it to show that way as well.  I don't think this should be regarded as 'normal behavior'.  It does pose an extra level vulnerability.

---

### Post by LordVeovis on 2012-01-16
Should this be submitted as a bug to launchpad?  Any thoughts on this?

---

### Post by LordVeovis on 2012-01-16
> **Ms. Daisy said:**
> Why don't you just set the OS inside of the VM to require a password upon wake up?  That way everything requires a password no matter where the mouse is captured.

That can be done, but then there is the annoyance of leaving the VM and again having to enter a password while actively at the computer.  That is not a good solution, but it is a temporary work around.

It also doesn't address the fact that any open applications on the host, other than the VM, would remain completely visible without the need for a password, even if they cannot leave focus of the VM.

---

### Post by imachavel on 2012-01-16
> **Azdour said:**
> Hi,

I think what the OP is saying and I have seen this too, but rarely in Ubuntu 10.04, is the following:

Lets say the screen-saver is set up to kick in after 20 minutes of inactivity and to lock the machine. 

I am running VirtualBox and after 20 minutes of inactivity the screen-saver does not kick in until the VirtualBox window looses focus.

This means the computer never locks and people can use your VirtualBox on your machine. If they try and do anything else with Ubuntu then the screen-saver and lock kicks in. It's as if it had been waiting because it was somehow blocked by an in-focus VirtualBox window (not that I think this is the what the issue is, just coming at it from a developers angle).

That being the case, it has been said on many occassions on this forum that having direct access to a machine is always a security vulnerability.

I agree with that, easy enough to hack something through a network, why not directly on the machine? you can back up whatever you want to an hdd of course, unless the pc is locked. But on the development side, would it be ubuntu's fault or virtualbox fault that the whole computer isn't locked when you are inside virtualbox and the screen saver is supposed to kick in after 20 minutes?

Would you say windows has over come this issue? If so let me know:popcorn:

---

### Post by Rebelli0us on 2012-01-16
It's a gnome problem not a virtualbox bug.

But, you have to be logged in to use the VM, so the VM is as secure as your desktop, right? For this reason I set all my VM's to auto-login, I think of the VM as just another app. Can you buy that?

---

### Post by LordVeovis on 2012-01-17
> **Rebelli0us said:**
> It's a gnome problem not a virtualbox bug.

But, you have to be logged in to use the VM, so the VM is as secure as your desktop, right? For this reason I set all my VM's to auto-login, I think of the VM as just another app. Can you buy that?

Yes and no.  I think of the VM as an app to which is why this particularly bugs me.  Being in ANY app should not cause the locking feature to not work.  A user should not have to log out to secure his computer, nor should I have to lock my screen myself (which requires me to leave the vm) in order for gnome to lock properly.

You do have to log in to start the VM, but after it is started, if you are in it, the vm is as secure as any app running on a computer that is not and will not lock.

---

### Post by LordVeovis on 2012-01-18
So where should I go / post to get this fixed, or at least start a discussion about having it fixed?

---

### Post by CharlesA on 2012-01-19
> **LordVeovis said:**
> So where should I go / post to get this fixed, or at least start a discussion about having it fixed?
Try launchpad.

---

### Post by Rebelli0us on 2012-01-21
> **LordVeovis said:**
> Yes and no.  I think of the VM as an app to which is why this particularly bugs me.  Being in ANY app should not cause the locking feature to not work.  A user should not have to log out to secure his computer, nor should I have to lock my screen myself (which requires me to leave the vm) in order for gnome to lock properly.

You do have to log in to start the VM, but after it is started, if you are in it, the vm is as secure as any app running on a computer that is not and will not lock.

Screensaver is an anachronism. Have you tried setting the host to Suspend S3 after x minutes of inactivity?

---

### Post by FuturePilot on 2012-01-23
> **georgemc said:**
> Not sure if this is a bug or just normal behavior.  Ran across this awhile back and dismissed it as a quirk in Gnome2 or X11.
 

 It can be easily reproduced by just clicking on a pull down menu and letting the cursor sit there (see the enclosed picture).  This is not just limited to VM s.
 

 The good thing is that when you click the cursor any where else the screen saver and locking mechanism do kick in.   
 

 The security exposure would be that the screen remains visible and appears to be unsecured, until someone clicks anywhere else.  For example: if you go to the pull down menu to lock the screen and just leave the cursor over “Lock Screen” and OOPS do not click on the item, then this will happen too.
 

 I am using 10.04.3LTS Ubuntu with the standard Gnome2.
 
Q:    	 	 	 	 	 	   Can this be reproduced in the other DE s like KDE, Gnome3, Unity, XFCE?
  
 Interesting
 

 George

Well not quite the same, but the result is pretty much the same. That issue is because of how Xorg works. When you have a menu open, it grabs all input meaning nothing can grab the screen. Try having a menu open and adjusting the volume with the keyboard. It doesn't work. However, I would have to say the these two problems are somehow related to input grabbing.

---

### Post by LordVeovis on 2012-01-23
> **Rebelli0us said:**
> Screensaver is an anachronism. Have you tried setting the host to Suspend S3 after x minutes of inactivity?

I'm not sure what you mean

---

### Post by Rebelli0us on 2012-01-23
> **LordVeovis said:**
> I'm not sure what you mean

Set auto-suspend in power preferences, that also locks the machine.

---

### Post by LordVeovis on 2012-01-23
> **Rebelli0us said:**
> Set auto-suspend in power preferences, that also locks the machine.

Auto suspending my machine would not be something I wish to do as I want my machine to still be online and the host and guest to still be processing.

---

### Post by dbarreth on 2012-02-09
I have the exact same problem at my workstation.
My setting is to turn of monitor and lock the screen after 20 min.

If my last focus was on my windows VM in virtualbox when i come back, i don't need the password (but the screen is off and turns on during mouse/keyboard activity). As soon as i set focus on the Ubuntu host machine the screen locks and forces the password. This means anyone can see whats on the monitor and have full control on my VM as the logged in user there.

Don't know exactly when this started, but I am quite sure this worked as intended in earlier versions of Ubuntu, as 9.04/9.10. Don't know if VirtualBox or ubuntu is to blame though. Seems like an Ubuntu problem. But I'm not a developer so what do I know.

Seems like a bug report is the right way to go. But don't sure if we should submit it to Ubuntu or Virtualbox. The problem seems easy to replicate though

---

### Post by Rebelli0us on 2012-02-09
> **dbarreth said:**
> I have the exact same problem at my workstation.
My setting is to turn of monitor and lock the screen after 20 min.

If my last focus was on my windows VM in virtualbox when i come back, i don't need the password (but the screen is off and turns on during mouse/keyboard activity). As soon as i set focus on the Ubuntu host machine the screen locks and forces the password. This means anyone can see whats on the monitor and have full control on my VM as the logged in user there.

Don't know exactly when this started, but I am quite sure this worked as intended in earlier versions of Ubuntu, as 9.04/9.10. Don't know if VirtualBox or ubuntu is to blame though. Seems like an Ubuntu problem. But I'm not a developer so what do I know.

Seems like a bug report is the right way to go. But don't sure if we should submit it to Ubuntu or Virtualbox. The problem seems easy to replicate though


What happens if you tap the Host key just before you walk away?

---

### Post by dbarreth on 2012-05-08
> **Rebelli0us said:**
> What happens if you tap the Host key just before you walk away?

Sorry for late respons

If i tap the Host key before leaving, everything works as expected. Same result as manually changing focus from the VM by clicking on a "linux window" before leaving.

---

