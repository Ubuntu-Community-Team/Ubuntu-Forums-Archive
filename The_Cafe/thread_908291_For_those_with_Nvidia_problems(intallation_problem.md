---
title: "For those with Nvidia problems(intallation problems/duel monitor)"
date: 2008-09-02
forum: The Cafe
---

### Post by bigtone on 2008-09-02
After installing **[COLOR="DarkRed"]Ununtu[/COLOR]** a few days ago I had huge problems installing my Nvidia video card.
Problem is no solved and I would like to **[COLOR="SeaGreen"]thank the forums[/COLOR]** they were a great help. I would like to put all the info I got together into a step by step guide so others don't have the problems I did.  you might recieve this message [B][I]You appear to be running an X server; please exit X before            
         installing.  For further details[/I][/B] or ***libc header files missing***

1.Go to The nvidia website and download your linux driver [http://www.Nvidia.com]("http://www.Nvidia.com")
Down load the package to your desktop.
for the sake of this post i will use the package name for the package I downloaded You must change this name to mack yours when installing.

2. most important you have got here print this document now or write down the codes you need from it (Don't say I didn't warn you)

3. type this code and follow commands **> *sudo apt-get install build-essential xorg-dev pkg-config linux-headers-$(uname -r)* **  ([COLOR="Red"]uname please put your user name)[/COLOR]

4.press Ctrl+Alt+f1 (bet you wish you wrote those codes down now)
on this screen tupe the following command(**case sensitive**).
> ***sudo /etc/init.d/gdm stop***

5. next command type > ***cd Desktop***  (case sensitive)

6.and now the following command (remember to change the package name for yours)  > ***sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run***

7. follow the on screen instructions.then type the following after installation   ***> sudo /etc/init.d/gdm restart***  This will restart your gdm.

8.now you might want to change your screen settings or ad a second monitor  but first you have to remove the old xconfig open terminal type ***> cd /etc/X11***  after that then type this next code
[B][I]> sudo rm -rf /etc/X11/xorg.conf.backup .
[/I][/B]
9. now you will be able to channge your settings but 1st to enter the control panel (keep dir the same as before) ***> cd /etc/X11***  after that then type this next code
***> gksudo nvidia-settings***  (dont forget to save)

10. Final time press Ctrl+Alt+f1  and ttype this next code
> ***sudo /ect/init.d/gdm restart*** 

Now you have installed your video card
The downside to this is if you update your system you wil have to go over this stage again to reinstall your card.:KS

---

### Post by freak42 on 2008-09-02
why not just go to 
System->Administration-> Hardware Drivers and enable (tick) the NVidia accelerated graphics driver
?

---

### Post by taavikko on 2008-09-02
> 3. type this code and follow commands
Quote:
sudo apt-get install build-essential xorg-dev pkg-config linux-headers-**$(uname )**
Is missing -r

Also, using envy, is easier method for beginners than compiling it yourself.
Recommended way, is using restricted drivers. "Hardware drivers"
or what it is called in english menus :)

---

### Post by philinux on 2008-09-02
Typo

9. now you will be able to channge your settings but 1st to enter the control panel (keep dir the same as before) [B][I] 	Quote:
 	 	 		 			 				cd /etc/X1 			 		
[/I][/B]should be X11

---

### Post by bigtone on 2008-09-02
> **philinux said:**
> Typo

9. now you will be able to channge your settings but 1st to enter the control panel (keep dir the same as before) [B][I] 	Quote:
 	 	 		 			 				cd /etc/X1 			 		
[/I][/B]should be X11

thanks typo now been edited

---

### Post by bigtone on 2008-09-02
> **freak42 said:**
> why not just go to 
System->Administration-> Hardware Drivers and enable (tick) the NVidia accelerated graphics driver
?

Installing 2 monitors that option did not work

---

### Post by taavikko on 2008-09-02
3. type this code and follow commands ****  ([COLOR="Red"]uname please put your user name)[/COLOR]

No! uname doesnt mean your username!
Type the command like it is. $(uname -r) or `uname -r`
not $(george -r)

---

### Post by taavikko on 2008-09-02
> **bigtone said:**
> Installing 2 monitors that option did not work

Dual monitors arent enabled by default, you have to use either 
nvidia-settings or manually editing xorg.conf

---

### Post by freak42 on 2008-09-02
Yes, I do have two monitors (laptop + external) that run successfully with the restricted drivers.

---

