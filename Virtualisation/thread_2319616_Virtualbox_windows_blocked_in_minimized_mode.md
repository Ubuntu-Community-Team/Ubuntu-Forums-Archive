---
title: "Virtualbox windows blocked in minimized mode"
date: 2016-04-06
forum: Virtualisation
---

### Post by samuel_sayag on 2016-04-06
Hello,

New to Ubuntu, I search the forum and internet about this problem but couldn't find any thing that solves it. So decided to post...

_Hardware & Soft:_
Ubuntu Gnome 14.04 LTS 
Memory 19.5 GB
Intel® Core™ i7-2670QM CPU @ 2.20GHz × 8 
Intel® Sandybridge Mobile 
os 64-bit

I have installed virtualbox recently and experiments on 2-3 VMs. And my problem is very simple and could be hilarious if I wasn't really stucked.
My main virtualbox windows is _stucked all the time on minimize mode_. 
Alt+Tab gives me a way to try switching to the application but the window doesn't displays.

_What I have already tried:_ 
[LIST=1]
[*]right click on the minimized icon (on top left corner next to Activities) but it just proposed "Quit" which works but doesn't propose anything such as maximize 
[*]any shortcut possible related to maximizing a windows from Activities > Settings > Keyboard > Shortucut 
[*]some code in the terminal such as below that I have found in some blogs and forums 
[/LIST]

```

$ wmctrl -l
0x02200007 -1 machevi Oracle VM VirtualBox Manager
0x02600023  0 machevi Desktop Environments - Post New Thread - Firefox Developer Edition
0x030000e0  0 machevi Details
0x02a00009  0 machevi Pictures

$ wmctrl -a "Oracle VM VirtualBox Manager"
$ wmctrl -r "Oracle VM VirtualBox Manager" -b toggle,fullscreen

```

This code works well with windows such as the ones of a file manager for instance.

Another track was trying to understand the signification of the -1 in

```

$ wmctrl -l
0x02200007 **-1** machevi Oracle VM VirtualBox Manager

```

I learned that it means the windows is sticky and the fact that I can manipulate other windows without problem (the all bear 0 in the list of open windows) seems like a clue...but I lack knowledge in System to benefit from any information about this.

I somebody could be of anyhelp

Note: I currently double click on the VM main file (/home/samuel/VirtualBox VMs/Hortonworks Sandbox with HDP 2.4/Hortonworks Sandbox with HDP 2.4.vbox for instance) to start it so it give me access to currently installed VMs but it still not gives me access to the main virtualbox application and incidently prevent me from installing/de-installing new VMs.

Many thanks to you all

---

### Post by Bucky Ball on 2016-04-06
*Thread moved to **Virtualization**. *

---

### Post by MAFoElffen on 2016-04-06
With what version of VirtualBox (I didn't see that in your post)? And was it from the Ubuntu repo, from VirtualBox or from Oracle?

What screen resize issues are usually caused by, with a Linux host/VirtualBox combo, is that the guest additions or Extension pack (depending on what version of VirtualBox) is temp not synched during a user's recent kernel update. Try re-installing the Guest Additions or Extension Pack, depending on what version of VirtualBox you are using. (Different versions of VirtualBox use one or the other...)

That fix seems to solves about 80% of this. Other's are a video setting in the guest, where you setting where you set the "GUI/MaxGuestResolution" to "any".

---

### Post by samuel_sayag on 2016-04-06
Hello,

The version of virtualbox is
```

$ vboxmanage --version
4.3.36_Ubuntur105129

```

But the problem is not the windows of my VMs once launched (I put in my post that is working well when I double click on the .box file) but the windows of the main virtualbox application.
I already have installed guest addition and it is indeed working very well but it is simply not linked to my current problem.

(I don't understand why the moderator put the thread in this forum because the virtualization is working well.)

My problem is : I simply cannot reach the main application windows because it is stuck in minimize mode. 

I put an image of the windows that is stuck in minimized mode.

This is the windows I cannot have

Thanks

---

### Post by MAFoElffen on 2016-04-07
I've been using VirtualBox since VirtualBox OSE, 2007, running under OpenSolaris... and I have never run into that before. Most everything else under the Sun, but not that.  So, I did some digging into Oracles Bug Reports and the Version Change History since version 1.5.4.

You are on version 4.3.36. There has been 7 versions since then (most were maintenance releases, 2 were beta for release 5.0).

Version 5.10 was a maintenance release that had some GUI changes that fixed some problem with the VM Manager window.
> 
GUI: fixed another 3D overlay window reparenting issue when the VM is switched to fullscreen mode on X11 hosts
GUI: fixed state synchronization issue in the VM manager window when VM was paused from its runtime window

That was not exactly what you are describing, but there were improvements done to the VM Manager window in that later version... and further versions were done after that...

So with that, I can foresee if you reported a bug on that to Oracle resulting in them suggesting that you uninstall 4.3.36 and installing version 5.0.16 (current), to see if that corrects your problem. That just also happens to be what I would recommend.

Un-installing VirtualBox removes the program, but leaves the VM's. The VM's you can use with the new version of VirtualBox. You should also install the appropriate version Extension Pack onto your newly installed VirtualBox.

---

### Post by samuel_sayag on 2016-04-07
Thank you very much MAFoElffen for your answer.
I can try this if I have the insurance to keep my current VMs.

Could you be more explicit on the step to follow to change from my current version to the latest stable version ?

1 - How do I cleanly de-install the current version without touching my VMs ?
2 - How do I install manually the new one and make it aware of my VMs ?

Again many thanks for your support

---

### Post by Bucky Ball on 2016-04-07
I'd say before you do anything take a snapshot of your VM so you can restore it at any time to exactly how it is now.

---

### Post by samuel_sayag on 2016-04-07
Hello,

Thanks for answering.
I will do the snapshot no problem. Is it just a ```
tar cvzf 
``` of the directories of my VMs ?

Thank you

Still to answer:

> 
Could you be more explicit on the step to follow to change from my current version to the latest stable version ?

1 - How do I cleanly de-install the current version without touching my VMs ?
2 - How do I install manually the new one and make it aware of my VMs ?


Many thanks to you all

---

### Post by SeijiSensei on 2016-04-07
Visit the page [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions) and follow the instructions there to install support for the Oracle repository.  When you run "sudo apt-get install virtualbox-5.0" it will automatically remove the current virtualbox installation.  Then install the extension pack: [http://download.virtualbox.org/virtualbox/5.0.16/Oracle_VM_VirtualBox_Extension_Pack-5.0.16-105871.vbox-extpack](http://download.virtualbox.org/virtualbox/5.0.16/Oracle_VM_VirtualBox_Extension_Pack-5.0.16-105871.vbox-extpack)

The newly-installed version will usually detect all your VMs and present them in the manager just as before.  If that doesn't happen automatically, you can add them manually by running Machine > Add from the manager's menu.

---

### Post by samuel_sayag on 2016-04-07
Hello,

I am quite desperate now.
I have indeed a fresh installation of virtualbox 5.0 (I did a purge before the installation) but the window still does not want to appear. 

Thank to you I now know how to update my virtualbox to the last installation.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I did NOT solve my problem however

When I do a Ctrl + Tab I can switch to the icon of virtualbox and even by pressing Touch Down I can see that the window is launched but it refuse to make it appear...

So I returned to my first track: a problem of graphical desktop and found a shortcut to solve the problem but I am still a bit stuck.

As I wrote in my very first post when I start virtualbox it is stuck minimized. So I explore the command that gives information about windows on the desktop.

```

wmctrl -lG
0x02000008   0  0      105  1920 1014 machevi samuel@machevi: ~
0x02800023   0  0      105  1920 1014 machevi [UbuntuGnome] Virtualbox windows blocked in minimized mode - Reply to Topic - Firefox Developer Edition
0x00a00008   0  0      54   1920 1053 machevi Home
0x02400015  **-1**  448  218  1024 729  machevi Oracle VM VirtualBox Manager

```

The **-1** that is on my virtualbox is the GRAVITY from the man of wmctrl and it is immediatly put on -1. It means that the windows is always minimized. So I searched how to change the gravity:
And this did the job done.

```

wmctrl -r "Oracle VM VirtualBox Manager" -e '0,0,0,1024,729'

```

After that my window was accessible and when I changed some selection it stopped to be stucked...

So really I don't know the source of the problem but this may help somebody else sometime

Again many thanks to you all for suggestion and helping.

---

### Post by MAFoElffen on 2016-04-07
Just saw that also in a blog entry... LOL

For others: 
-r is select winodw by the long title.
-e is move and resize the selected window
Their suggestion for that command, was to enter the first field of the -e option as 1 (because 0 was too far up in the corner... Of those 5 fields:
1. Gravity
2. X coordinate of upper-left corner
3. Y coordinate of upper-left corner
4. Width in pixels
5. Height in pixels

What worked for them was another variant, like this:
```

wmctrl -r "Oracle VM VirtualBox Manager" -b toggle,shaded,maximized_horz

```
... where:
-b is change the state of the selected window.

---

