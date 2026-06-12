---
title: "How to autostart virtualbox's virtual machine"
date: 2008-04-18
forum: Virtualisation
---

### Post by randomAccess on 2008-04-18
Is it possible to autostart virtual OS installed thru virtualbox? FOr example, Windows XP installed thru Virtualbox.

If this is possible, how can I make it autostart in full mode or seamless mode?

---

### Post by kerry_s on 2008-04-18
go to the virtual site and read the pdf manual, i think i saw command line options for something like that. good luck

---

### Post by phrostbyte on 2008-04-18
yes, make a session in System -> Perfs -> Session for: vboxsdl -vm "Name of your VM" -fullscreen.

Cheers

---

### Post by randomAccess on 2008-04-19
Hm this doesn't work for non-OSE edition (USB didn't work with OSE edition) and also I cannot find the manual you mentioned. 

While waiting for more ideas, I'll check for the manual onoline. ;)

---

### Post by randomAccess on 2008-04-19
Found it :D

VBoxMange startvm [vm name]

---

### Post by xwisdom on 2008-05-01
You might also want t check out this script:

[http://farfewertoes.com/stories/2008-03-09-start-virtualbox-virtual-machines-on-boot/](http://farfewertoes.com/stories/2008-03-09-start-virtualbox-virtual-machines-on-boot/)

Let me know if this works for you

---

### Post by jtb_90 on 2009-03-18
Hey guys I want to do the same thing kinda, I have an XP VM machine, and I would like it to startup in seamless mode everytime I log on.

Anybody know if that's possible? Some sort of script to start the VM and then some sort of script to press right CTRL and L?

Cheers!

---

### Post by terabyte1 on 2009-03-18
What's wrong with Gnome? I Love it - it's more straight-forward than KDE, though KDE seems to have more scientific projects  than Gnome - maybe i'm not loooking in the right place though :D the KDE 4.1 is superb though under Kubuntu :D

:P

non sibi sed omnibus (Not for oneself but for all)

terabyte

---

### Post by charon79m on 2009-05-21
I use Ubuntu as my main desktop, but I have two apps that require a MS box (proprietary VPN client, and .NET 3.5 app).

To do this, I setup VirtualBox and start a headless XP VM by autoruning this command:

VBoxManage startvm {XP VM} --type vrdp

I then RDP to this machine as needed to do my Windows stuff.

It works quite well for me.

---

### Post by markba on 2009-05-21
> **charon79m said:**
> I use Ubuntu as my main desktop, but I have two apps that require a MS box (proprietary VPN client, and .NET 3.5 app).

To do this, I setup VirtualBox and start a headless XP VM by autoruning this command:

VBoxManage startvm {XP VM} --type vrdp

I then RDP to this machine as needed to do my Windows stuff.

It works quite well for me.


If this is exactly want you want, maybe it's a good idea to use vboxcontrol (mentioned above) or vboxtool (see my sig). Both can start a session in the background (vrdp-mode), but what's more important, both save all running sessions on shutdown. This is important because if sessions are not properly saved on shutdown, they become in an aborted state, which could result in data loss or (eventually) in a session crash.

---

### Post by jimerman on 2012-04-12
OK, so to be absolutely clear.  I am using Ubuntu Desktop (for the Gnome GUI) 12.04 as the Host machine.  I created an executable script file in my home folder, I called it "personal-startup" (give it Execute permissions).  In this script file, I put:

VBoxManage startvm {my-machine-name} --type gui

Then, I go to the Applications menu > System Tools > System Settings, scroll down to User Accounts, and made my admin user "Automatic Login=ON".

Finally, Applications > System Tools > Preferences > Startup Applications, and add my personal-startup script.

Reboot.  

Life is good! :-)

---

