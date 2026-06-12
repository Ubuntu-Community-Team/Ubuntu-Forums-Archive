---
title: "VirtualBox Seamless Windows"
date: 2007-10-16
forum: The Cafe
---

### Post by PartisanEntity on 2007-10-16
This new feature in VirtualBox is extremely cool. I still have to find out whether I can get rid of the Windows taskbar, but being able to run Windows applications in Ubuntu seamlessly (or vice versa) is very impressive IMO.

---

### Post by FFighter on 2007-10-16
Freaking Awesome! If the level of integration is good enough (like drag and drop, taskbar, etc) this would make a very good alternative to wine (of course you would have the whole operating system running but at least you wouldn't have the quirks and bugs of wine - with all the respect to wine developers, of course).

This is the same feature that Parallels for Mac has! I just wish VMWare Workstation had this (I currently use VMWare Wokstation 6...).

Is VirtualBox Open Source?

---

### Post by GSF1200S on 2007-10-16
Yes and no. They have 2 versions: one is totally open source, and the other is free to use, with non-free elements not free to modification. Check their website for more details.

---

### Post by n3tfury on 2007-10-16
old, but cool

---

### Post by Frak on 2007-10-16
> **FFighter said:**
> Is VirtualBox Open Source?

One from the repos is, the one from the site is not.

---

### Post by -grubby on 2007-10-16
that's impressive!!

---

### Post by n3tfury on 2007-10-17
mmmmm

---

### Post by PartisanEntity on 2007-10-17
Is it possible to hide the taskbar somehow?

---

### Post by n3tfury on 2007-10-17
yeah, you can set to auto hide.  not sure if you can completely get rid of it.

---

### Post by Sam on 2007-10-17
When I do that, the Windows bar is behind the Gnome one. How did you manage to get the Windows bar above the Gnome bar ??

---

### Post by n3tfury on 2007-10-17
i don't use a bottom panel in Ubuntu ;)  but you can move the windows task bar to the top if you need to.

---

### Post by popch on 2007-10-17
> **n3tfury said:**
> i don't use a bottom panel in Ubuntu ;)  but you can move the windows task bar to the top if you need to.

It should be possible to move the task bar to any of the four sides of the screen. It 'should' also be possible to hide the task bar until you move your mose on it. I said 'should' because ATM I can not test it.

---

### Post by n3tfury on 2007-10-17
well, if it works like windows is supposed to work, you can do all of that.

---

### Post by FFighter on 2007-10-17
> yeah, you can set to auto hide. not sure if you can completely get rid of it.

Yeah, I don't think I would want my linux desktop with a Windows taskbar around :)

---

### Post by EnigmaX on 2007-10-17
So I'm assuming running Win games on a Linux box is possible with this software?  That is the only downfall I've found so far is the game compatibility of the OS :(

---

### Post by Sam on 2007-10-17
> **EnigmaX said:**
> So I'm assuming running Win games on a Linux box is possible with this software?  That is the only downfall I've found so far is the game compatibility of the OS :(

You won't get all the performances as a native Windows installation. This should works with non-recent game which doesn't eat too much cpu.

---

### Post by n3tfury on 2007-10-17
> **FFighter said:**
> Yeah, I don't think I would want my linux desktop with a Windows taskbar around :)

then don't go seamless and run it in a window like normal.

---

### Post by popch on 2007-10-17
I am now at home and have performed a few simple tests.

(1) Seamless mode does indeed work. The effect is, however, only noticeable if you have an application window open. 

(2) You can move the task bar to each of the four sides of the screen.

(3) To can adjust the windows task bar to hide itself when the cursor is not on it. It will do so and reappear again when you place the cursor on the collapsed task bar. However

(4) Once the task bar has been collapsed and there is an (seamlessly) open application window, the task bar will not reappear as long as the application is open (vs closed or minimized)

(5) Minimizing or closing a seamless windows application will produce some rather strange effects on the desk top. It will show multiple copies of the window you want closed, several copies of the task bar and so on. No harm is done, all works well once you have puzzled out how to recover.

---

### Post by 71CH on 2007-10-17
is there a way to have one workspace totally dedicated to virtualbox?

---

### Post by PartisanEntity on 2007-10-17
Thanks very much **popch** for the research!

---

### Post by Nano Geek on 2007-10-17
> **71CH said:**
> is there a way to have one workspace totally dedicated to virtualbox?Just put it fullscreen on one desktop and switch between them.

---

### Post by n3tfury on 2007-10-17
> **71CH said:**
> is there a way to have one workspace totally dedicated to virtualbox?

if you're going to do that, no sense in using seamless mode.  just open virtualbox to fullscreen in whichever workspace you choose.

---

### Post by 71CH on 2007-10-17
i think i tried that once only to have ugly black borders along the sides of windows
is there a way to make the whole screen windows

---

### Post by n3tfury on 2007-10-17
> **71CH said:**
> i think i tried that once only to have ugly black borders along the sides of windows


along the sides of windows within the vm environment or the window outside of the environment?

---

### Post by 71CH on 2007-10-17
when i put it in fullscreen i see windows xp desktop only and then a thick black border along all four sides

---

### Post by n3tfury on 2007-10-17
maybe someone here can check that.  i'll have to wait till i'm back on my ubuntu box at home, sorry.

---

### Post by 71CH on 2007-10-17
thanks for trying
could it be my video card?
I would very much like to use virtualbox (I tried vmware and didn't much like it) but I was hoping to use it in fullscreen so that it's "seamless" in the sense that I can leave it in one workspace and switch back and forth from ubuntu and xp

---

### Post by n3tfury on 2007-10-17
ill be home in the next few hours, so if nobody's tried it, i'll take a look.  i don't recall what you describe though.  maybe you're not using enough graphics RAM in virtualbox?

---

### Post by epimer on 2007-10-17
> **71CH said:**
> thanks for trying
could it be my video card?
I would very much like to use virtualbox (I tried vmware and didn't much like it) but I was hoping to use it in fullscreen so that it's "seamless" in the sense that I can leave it in one workspace and switch back and forth from ubuntu and xp

You need to install the guest additions. The big black borders are because your XP desktop resolution is set lower than your actual desktop resolution, if you see what I mean. Install the guest additions, then set the resolution to match your native one.

---

### Post by 71CH on 2007-10-17
could you explain what you mean by installing guest additions
thanks

---

### Post by PartisanEntity on 2007-10-17
Anyone know how I can copy files from Ubuntu to the VritualBox OS? I saw something called Shared Folders, tried to set up my /home/Desktop as shared folder but I can't see it in VB-Win XP ?

---

### Post by Nano Geek on 2007-10-17
> **PartisanEntity said:**
> Anyone know how I can copy files from Ubuntu to the VritualBox OS? I saw something called Shared Folders, tried to set up my /home/Desktop as shared folder but I can't see it in VB-Win XP ?It's in the manual on their site.
You have to run a command in DOS (yuck) to mount the folder.

---

### Post by reza81 on 2007-10-17
lol just installed it ... It's like doing MS in de b*t & it feels nice!

seamless ownZ

---

### Post by popch on 2007-10-17
> **PartisanEntity said:**
> Anyone know how I can copy files from Ubuntu to the VritualBox OS? I saw something called Shared Folders, tried to set up my /home/Desktop as shared folder but I can't see it in VB-Win XP ?

(1) The 'guest extensions' have to be installed. Once the VM is running select Geräte/Gasterweiterungen installieren (presumably 'devices/install guest extensions')

(2) Create a folder anywhere in the host system. Why not on the desktop.

(3) shut down the guest machine. you can not attach a shared folder to a machine while it is running. You also can not do so when the machine is 'frozen'. It must be shut down.

(4) In the configuration details of the virtual machine ('Details') click on 'Gemeinsame Ordner' (shared folders, I suppose)

(5) Click on the greenish icon (right top) and locate the folder you want to share.

(6) Start your virtual machine again

(7) In the VM (I use win2k) open the Netzwerkumgebung (my Network?), select 'see all of the network' (Ganzes Netzwerk), locate 'Virtual Box Shared Folders'. Open that and you will find your shared folder. 

Sorry for the gibberish; I am using the German language version of VMBox. Should not pose insurmountable problems for you, I trust.

Edit: Instead of step (7) you can also open a 'terminal' (a command window) and use the ***net use ***command as described in the virtualBox doc (mentioned elsewhere in this thread). I did at first not dare mentioning that way because then someone would think Windows was not ready for the desktop because you need to type commands to do things

---

### Post by thisllub on 2007-10-17
It is easier to create a Samba share.

---

### Post by popch on 2007-10-17
> **thisllub said:**
> It is easier to create a Samba share.

As far as the guest is concerned, it ***is*** a Samba share (or rather, an SMB share), I think

---

### Post by PartisanEntity on 2007-10-17
> **popch said:**
> (7) In the VM (I use win2k) open the Netzwerkumgebung (my Network?), select 'see all of the network' (Ganzes Netzwerk), locate 'Virtual Box Shared Folders'. Open that and you will find your shared folder. 

I can't seem to find it in Network Places.

edit: I had to use 'net use' and it worked. Very cool, again thank you popch.

---

### Post by thisllub on 2007-10-17
> **popch said:**
> As far as the guest is concerned, it ***is*** a Samba share (or rather, an SMB share), I think

The reason I use Samba is that I have multiple VMs on multiple computers.

---

### Post by popch on 2007-10-17
> **PartisanEntity said:**
> I can't seem to find it in Network Places.

First, please check to see if the virtual guest indeed has the shared folder attached. In Innotek VirtualBox select your guest machine, display the details, look under the heading shared folders. You should see some entry like 'shared folders nn' (where nn is the number of shared folders attached, preferably >0). Actually, it says 'none' when zero.

I then open in succession (in win2k)

Desktop->Netzwerkumgebung(network places?)->Gesamtes Netzwerk(all of the network) 

which leaves me with an empty window. Click on 'display all of the content' ('ganzes Netzwerk anzeigen'). Now Windows should display (at least) two Icons made up of pipes and joints. The one which interests us is labelled 'Virtual Box Shared Folders'.

I think I left out one of those steps in my last description.

---

### Post by PartisanEntity on 2007-10-17
Danke popch funktioniert jetzt :)

---

### Post by popch on 2007-10-17
> **PartisanEntity said:**
> Danke popch funktioniert jetzt :)

Good show, PartisanEntity.

To be truthful, it's possibly simpler just to use the commands.

Oh - it appears that you ***can*** attach a shared folder to a machine while it is running. You do not use the 'Details' window in the virtualBox console but the 'devices' menu of the guest machine.

---

### Post by reza81 on 2007-10-17
Finaly ... one program suite i missed was macromedia studio stuite

flash & fireworks :guitar:

---

### Post by PartisanEntity on 2007-10-17
> **popch said:**
> Oh - it appears that you ***can*** attach a shared folder to a machine while it is running. You do not use the 'Details' window in the virtualBox console but the 'devices' menu of the guest machine.

I tried that but it did not seem to work for me, the instructions you posted did work in combination with 'net use'.

---

### Post by original_jamingrit on 2007-10-18
> **n3tfury said:**
> mmmmm

Man, that looks so crazy.

---

### Post by Depressed Man on 2007-10-18
Hmm I'm thinking about trying this on my laptop..though somehow I don't think video Skype would work (since the webcam is having issues in Gutsy so I would assume it'd be the same for a a virtual XP? But there are drivers for XP..so interesting)..

And Messenger Live. Hmm..anyone tried these yet?

---

### Post by popch on 2007-10-18
> **PartisanEntity said:**
>  the instructions you posted did work in combination with 'net use'.

Thanks for the feedback. I will try and find out what really works and what doesn't. Don't hold your breath, though, since I don't know when I find the time.

---

### Post by epimer on 2007-10-18
> **71CH said:**
> could you explain what you mean by installing guest additions
thanks

I don't have Virtualbox installed at the moment, but it's somewhere in the toolbar when you have the virtual machine running. The entry is along the lines of "Install Guest Additions..." or similar.

---

### Post by n3tfury on 2007-10-18
> **Depressed Man said:**
> Hmm I'm thinking about trying this on my laptop..though somehow I don't think video Skype would work (since the webcam is having issues in Gutsy so I would assume it'd be the same for a a virtual XP? But there are drivers for XP..so interesting)..

And Messenger Live. Hmm..anyone tried these yet?

i'm not sure about the cam, but live messenger does work.  any app for windows will work.  this is how i still use foobar and some random apps i can't live without.

---

### Post by Depressed Man on 2007-10-18
Camera doesn't work (not sure if that's because I didn't install the driver yet or it's because it doesn't work in Gutsy). And I can't seem to get it into seamless mode.

It's nice though..just gotta figure out what I'd want to do with this.. so far I just threw Live Messenger and whatever AOL AIM on there. So I can let my friends and family use that when they need to use my laptop.

---

### Post by mustang on 2007-10-18
Very cool. I believe Parallels already has something like this. Virtual machines are truly amazing pieces of software.

---

### Post by Frak on 2007-10-18
> **mustang said:**
> Very cool. I believe Parallels already has something like this. Virtual machines are truly amazing pieces of software.
Coherence, then VMware stole the concept and called it Unity (though Unity is better than Coherence), then VirtualBox went along with the crowd (which is not a bad thing IMHO)

---

### Post by DarkDancer on 2007-10-18
Why are you guys' all in German?

---

### Post by vexorian on 2007-10-18
> **71CH said:**
> is there a way to have one workspace totally dedicated to virtualbox?
Yes, and this is the answer for the taskbar as well, just move the vritual box "button" in the taskbar to another workspace, dunno about how it would work in compiz though.

VirtualBox is frigging awesome! One of the things I use this computer for is to develop and test windows apps and it is a BLESSING I can do it without unbooting ubuntu.

---

### Post by m0eman on 2007-10-18
> **vexorian said:**
> dunno about how it would work in compiz though.

It doesn't.

Edit: Seamless mode, I mean.

---

### Post by n3tfury on 2007-10-19
yes it does.

---

### Post by PartisanEntity on 2007-10-19
> **vexorian said:**
> Yes, and this is the answer for the taskbar as well, just move the vritual box "button" in the taskbar to another workspace, dunno about how it would work in compiz though.

VirtualBox is frigging awesome! One of the things I use this computer for is to develop and test windows apps and it is a BLESSING I can do it without unbooting ubuntu.

I am not sure I understood, which 'button'?

Thanks

---

### Post by arnold.pietersen on 2007-10-19
How can one set up a Windows shared folder in feisty?

I have Feisty as the host and Windows XP as the guest.  In Windows XP I can see my /home/arnold folder.  However, in Feisty I would like to access the Windows shared folder.

Any help

---

### Post by vexorian on 2007-10-21
> **arnold.pietersen said:**
> How can one set up a Windows shared folder in feisty?

I have Feisty as the host and Windows XP as the guest.  In Windows XP I can see my /home/arnold folder.  However, in Feisty I would like to access the Windows shared folder.

Any help
You can access /home/arnold/ in windows? That's new.

I tell virtual box to set up a share folder, and you then have to set up the share folder as a "shared drive" in windows using the net command.

The virtualBox user manual tells you the command to use from windows.

Can you write to /home/arnold from windows? if so you don't need to do more, right? You can just tell windows to write there and then you can access windows' stuff from feisty?

> 
I am not sure I understood, which 'button'?


Even in seamless mode, you would get to see a button belonging to the virtual machine in your taskbar, you can right click that button to send virtualbox to another workspace and that's the only place it will have the start menu + windows taskbar and apps.

---

### Post by DARKGuy on 2007-10-29
> **n3tfury said:**
> yes it does.

Please, tell me how? I've been dying to make it work with compiz!

---

### Post by hamster_billy on 2007-10-29
I've tried to set up seamless mode, but although the VBox window now behaves like a normal window in terms of z rather than being always on top, I still have a visible desktop.

I upgraded from VBox 1.4.? to 1.5.2, and upgraded guest additions from 1.4.0 to 1.5.0. When I <rctrl>+L I get the message about seamless mode starting, but I can still see the desktop icons and background picture. Is there something else I need to do to get it to work?

---

### Post by popch on 2007-10-29
> **hamster_billy said:**
> I've tried to set up seamless mode, but although the VBox window now behaves like a normal window in terms of z rather than being always on top, I still have a visible desktop.

I upgraded from VBox 1.4.? to 1.5.2, and upgraded guest additions from 1.4.0 to 1.5.0. When I <rctrl>+L I get the message about seamless mode starting, but I can still see the desktop icons and background picture. Is there something else I need to do to get it to work?

The seamless mode works only if you have an ***application window open***. I.e., if you open Notepad (to mention a really important case) and enter seamless mode, you will see on your display:
- your normal Gnome or KDE or whatever desktop
- the task bar withe the start button at its normal place (presumably at the bottom edge of your desktop)
- Notepad in a window of its own.

If you do not have an application open, you will see your Windows desktop, as you say you are seeing.

---

### Post by hamster_billy on 2007-10-29
Makes no difference for me. Just tried it with a few different applications, but the Windows desktop is always still visible. An extremely useful thing has come out of it - that I can have a Linux window on top of the fullscreen vbox. I'm happy with that, and have decided I don't care that much about seamless.

---

### Post by boast on 2007-10-29
that looks sick! Has anyone tried playing games? (like old dx7/dx8 games?)

---

### Post by BDNiner on 2007-10-29
Seamless didn't work they way i thought it would. I don't care for the windows desktop. I even went in the registry and created an key to turn the windows desktop off. so that way i only had the windows taskbar. Seamless only works if you have at least one application open. otherwise linux and windows will battle for the desktop.

---

### Post by vexorian on 2007-10-31
> **BDNiner said:**
> Seamless didn't work they way i thought it would. I don't care for the windows desktop. I even went in the registry and created an key to turn the windows desktop off. so that way i only had the windows taskbar. Seamless only works if you have at least one application open. otherwise linux and windows will battle for the desktop.
Could you please ellaborate? All windows does when seamless mode is enabled is show the start menu, the windows desktop is not there. Could this be a compiz fusion issue instead?

---

### Post by Frak on 2007-10-31
> **vexorian said:**
> Could you please ellaborate? All windows does when seamless mode is enabled is show the start menu, the windows desktop is not there. Could this be a compiz fusion issue instead?
It's supposed to do that.

---

### Post by vexorian on 2007-10-31
> **popch said:**
> The seamless mode works only if you have an ***application window open***. I.e., if you open Notepad (to mention a really important case) and enter seamless mode, you will see on your display:
- your normal Gnome or KDE or whatever desktop
- the task bar withe the start button at its normal place (presumably at the bottom edge of your desktop)
- Notepad in a window of its own.

If you do not have an application open, you will see your Windows desktop, as you say you are seeing.
No, no no, with no applications open I only see the windows taskbar, this is the correct behavior, if you see the windows desktop it is a bug.

---

### Post by Tichondrius on 2007-12-29
Yo, peeps, I have seamless mode WORKING for a Ubuntu guest running inside a VirtualBox VM on a Windows-XP host !!!!!

Not only that, but it is true seamless mode, that is only the applications I choose on the guest will appear in an independent window in the host. And each such window looks and behaves just like a regular host system (windows-xp) window.

How did I do that (despite the fact that VirtualBox doesn't even support it) ?  Easy!
Did I hack the VirtualBox open source code to achieve that ? Heck no !

Here's the secret (keep it between us, ok ?) :   
First install CygWin on your windows-xp host. Start up the CygWin X-server. 
Now in your Ubuntu guest, set the env variable DISPLAY to the address of the windows host (you can check that under Window's network connections).
Now any app you start from the shell where you set the DISPLAY env variable will display its window as a CygWin/X floating window in the Win-XP desktop.

Voila !  Easy-peasy 1-2-3 !!

It's cool to be playing "Crysis" on my high-performance windows machine, and also having Ubuntu run inside VirtualBox. Normally I use the Ubuntu guest as my development environment (for web applications in ruby/rails or python/pylons), which gives me the advantage of being able to test them from a windows browser (like they will be accessed the real world). And now it's even more cool to be able to run Ubuntu's apps like synaptic in a window on the host (XP) !!!!!!

---

### Post by process91 on 2008-03-25
First off, I believe the post above is referring to an opposite configuration, that is a Windows host with an Ubuntu guest.

Secondly, I would like to address the issue of Ubuntu/Windows fighting for total desktop coverage.

**How it should work**
Seamless mode should only display the windows task bar and any applications started in windows.
*This is the way it works with the Metacity Window Manager*

**How it works with Compiz Window Manager**
Windows start bar displays at the bottom of the screen correctly upon initial launch of "Seamless mode".
After switching to an Ubuntu application however, the desktop turns black. It's as if Windows is "fighting" for the background.
When switching back to the Windows virtual machine, the taskbar does not appear but if you click where the start button is you will see the Start menu appear.
At this point it appears to work correctly, only the taskbar and the start menu are showing over the Ubuntu applications in the background,
If you start an application, it will run but getting back to Ubuntu after starting an application is a difficult process of clicking on the Applications menu or using Alt-Tab switching (if you have a program open).

This still allows the "Seamless mode" to be effective, but it's not nearly as nice.

**Possible reasons why**
Compiz uses a lot of application jpegs (i.e. Scale plugin, Window Preview plugin) which need to display the entire image of the application. Opacity is another aspect which could be playing a role here, particularly if Opacity is set to dim applications without focus.

---

### Post by ODF on 2008-03-25
Since you have to run always at least one program non-minimized some people run a clock under the start bar.

What is your trick ? I'm not running anything, I just keep msn messenger open.

---

### Post by process91 on 2008-03-31
> **vexorian said:**
> No, no no, with no applications open I only see the windows taskbar, this is the correct behavior, if you see the windows desktop it is a bug.

This behavior seems to be fixed in a recent update. At least it's working for me (Ubuntu 8.04 Host with Windows XP Guest).

---

### Post by BDNiner on 2008-03-31
I need to have one window open for seemless mode to work properly. I wanted to have windows take one desktop on my compiz cube which works great until you want to switch the desktop back to one of the ubuntu ones. then windows and ubuntu battle for the desktop. For example i was running some updates in ubuntu while working on outlook in windows. As soon as ubuntu is done downloading the updates and starts installing them, the window is set to jump to the top of the active screen. Since i was working in outlook at the time the virutal machine crashed and i was unable to click back onto the windows desktop. I waited until ubuntu was done installing updates to see if when that window disappeared i would be given control of the windows desktop again so that i could close it. I was forced to do a hard reset, thank goodness the ubuntu updates worked if one of them had broken because of what i was doing i would have tossed the whole computer in the ocean.

---

### Post by pkkid on 2008-05-19
I have similar experiances running seamless mode w/ CompizFusion.

* Seamless Mode works great if at least one window is open.
* Putting a little analog clock above the task bar fixes it pretty well.
* Using VB in Full Screen mode is a little shady when switching desktops, Gnome and WinXP fight.

---

### Post by Gathalimay on 2008-05-20
Question:
Why exactly does guest additions not work for me anymore? I have windows as a guest (for Flash CS3) but I don't want to have it in window form every time. I go to devices -> Install Guest additions but nothing happens at all. It did this in a previous installation as well, so I'm not sure what the problem is. There is no reaction at all when I click on it. 

Thanks in advance.

---

### Post by jrusso2 on 2008-05-20
How do you get this seamless mode to work?  I have the guest additions installed but how to enable the sameless mode?

---

### Post by popch on 2008-05-20
> **Gathalimay said:**
> Question:
Why exactly does guest additions not work for me anymore? I have windows as a guest (for Flash CS3) but I don't want to have it in window form every time. I go to devices -> Install Guest additions but nothing happens at all. It did this in a previous installation as well, so I'm not sure what the problem is. There is no reaction at all when I click on it. 

Thanks in advance.

I am not near my installation ATM; I seem to remember that clicking on 'install guest additions' just mounts a virtual CD which contains the installation material. If you have no virtual CD attached to your machine or if your Windows is set not to autorun mounted CDs, that would explain vBox not installing the additions.

On the other hand, I had the installation fail at some time because vBox did not have the proper CD image. It then suggested to download the CD image from the vendor's site, which I did. The addition then installed itself correctly.

---

### Post by popch on 2008-05-20
> **jrusso2 said:**
> How do you get this seamless mode to work?  I have the guest additions installed but how to enable the sameless mode?

It's an entry in one of the menus of the window containing your virtual machine, and I think it's visible only while the machine is actually running.

---

### Post by jrusso2 on 2008-05-20
> **popch said:**
> It's an entry in one of the menus of the window containing your virtual machine, and I think it's visible only while the machine is actually running.

Yes I found that but it does not seem to do anything?  Is there some other change that has to be made?

---

### Post by popch on 2008-05-20
> **jrusso2 said:**
> Yes I found that but it does not seem to do anything?  Is there some other change that has to be made?

As I said before, I am not near my installation ATM. I seem to remember that the seamless mode only has any effect if there's an application window open. Otherwise, you'll just see the Windows desktop. I suggest you open an application (solitaire will do) and enable then the seamless mode.

---

### Post by aaaantoine on 2008-05-20
> **jrusso2 said:**
> How do you get this seamless mode to work?  I have the guest additions installed but how to enable the sameless mode?

The Host key (Right Ctrl by default) and L.

So, RCtrl+L.

---

### Post by jrusso2 on 2008-05-20
Got it thanks.

---

### Post by backupdevice on 2008-05-20
New version of VMware Workstation will also have it. This function is already available in Fusion.

---

### Post by endar98 on 2008-05-24
Hello,

I created a little .net application for a Windows VM to force an "invisible window" in your virtual machine to stop VirtualBox from having it's drawing issues when there aren't any windows open.

It creates a borderless, unmovable window which will position itself in the upper left hand corner of the screen, with 1 pixel actually on the screen, which is enough to satisfy the seamless virtualbox extensions.  It also does not include any kind of taskbar anything, with the only way to kill it off is through the task manager.

I added it to the startup folder of my user in my VM, therefore I can work peacefully without having to be concerned with accidentally closing anything.

I included the full source code (C#) with the application along with the binaries in the bin folder, it is public domain.

You can get it at: [http://www.acqusys.com/VBoxWorkaround.zip](http://www.acqusys.com/VBoxWorkaround.zip)

Please let me know if there are any issues with it, it has worked for me so far with VirutalBox 1.6 in Ubuntu 8.04 64bit, with Windows 2003 for a seamless desktop.


Does anyone know, is there an easy way to force the region of the seamless desktop space to force maximized VM windows to not overtake the menu bar that is part of gnome?  I would assume it would either be through custom settings for virtualbox and seamless desktop, or else in the VM itself.


Thanks,
Rick Fleming

---

### Post by Nakarian on 2008-06-13
Heh, I know it's only one pixel, but if that one pixel drives you as crazy as it did me (I tried having another beer - I still see it glaring at me), then try using ShellEnhancer to make that pixel invisible.  I already use ShellEnhancer to allow me to move and resize windows with Alt+Mouse, so it was just a matter of adding a new rule in the settings.

If interested, here's exactly what to do.

Install ShellEnhancer from [here]("http://www.nuonsoft.net/shellenhancer/downloads.php") and install it in the Windows guest OS.
Then right click on the icon in the system tray and click Settings->Settings.
Click on the "Auto Managed Windows" tab.
Click on the red plus to add a rule.
For application name, enter "VBoxWorkaround.exe".
Click "Next" twice.
Set both transparency options to 100.
Then just click "Next" until you can click "Finish".
After that's done, make sure to Apply the settings and if you already have the VBoxWorkaround.exe process running, end it in the Task Manager, then start it up again.

I hope that helps someone!  And a big thanks to endar98 for the workaround!  However, it seems that the one pixel window takes up 8 MB of memory on my system.  Is there some way to slim that down?  Even the Windows Calculator takes up less than half of that.

---

### Post by stinkinrich88 on 2008-07-13
best way to stop the seamless windows bug is this:

right click the start bar, go to "toolbars" then "new toolbar". Point the toolbar to some folder, doesn't matter what, now make it as small as you can right in the corner, I can't even see a pixel on my screen. Fiddle around until you get it perfect! There! no pixel, no start bar icon, nothing! bug workaround!

---

### Post by CheeseEatingBulldog on 2008-07-15
> **endar98 said:**
> Hello,

I created a little .net application for a Windows VM to force an "invisible window" in your virtual machine to stop VirtualBox from having it's drawing issues when there aren't any windows open.

It creates a borderless, unmovable window which will position itself in the upper left hand corner of the screen, with 1 pixel actually on the screen, which is enough to satisfy the seamless virtualbox extensions.  It also does not include any kind of taskbar anything, with the only way to kill it off is through the task manager.

I added it to the startup folder of my user in my VM, therefore I can work peacefully without having to be concerned with accidentally closing anything.

I included the full source code (C#) with the application along with the binaries in the bin folder, it is public domain.

You can get it at: [http://www.acqusys.com/VBoxWorkaround.zip](http://www.acqusys.com/VBoxWorkaround.zip)

Please let me know if there are any issues with it, it has worked for me so far with VirutalBox 1.6 in Ubuntu 8.04 64bit, with Windows 2003 for a seamless desktop.


Does anyone know, is there an easy way to force the region of the seamless desktop space to force maximized VM windows to not overtake the menu bar that is part of gnome?  I would assume it would either be through custom settings for virtualbox and seamless desktop, or else in the VM itself.


Thanks,
Rick Fleming

How do I run the .net files? I have tried all of the exe in the bin dir but they all give an error and are prompted to stop.

---

### Post by bforbes on 2008-10-15
Is there any way to have both the KDE and Windows taskbars displayed permanently? Whenever I activate a KDE app, the Windows taskbar disappears.

---

### Post by bforbes on 2008-10-15
If I could tweak KDE so that its windows never cover the top ~150 pixels of the screen, I could place the windows taskbar up there and it would always be visible. Is it possible to tell KDE that it can't use that space? That seems vaguely familiar to me, being able to restrict that.

---

### Post by master5o1 on 2008-10-15
> **71CH said:**
> is there a way to have one workspace totally dedicated to virtualbox?

Set the virtual window size to full screen ('home'+F or right-ctrl+F).

Keeping that in one workspace (e.g., no. 4) effectively keeps it as dedicated.

---

### Post by turbozmike on 2008-12-24
I cant believe no one has figured out how to fix this issue with windows desktop trying to take over ubuntu's if nothing in the windows guest is open.

I have been fighting with this stupid issue for a few days, I just discovered that I could do this seamless business and can finally use linux as my daily OS.  I have work programs that flat out wont run on linux so this is great.

I simply made an additional taskbar and put it on the right side, made it small as possible and told it to autohide.  It serves its purpose and is only a little bit noticeable because it unhides when you close an application.

---

### Post by Cope57 on 2008-12-24
**[sarcasm]** I love seeing dead threads come back to life for no apparent reason, thank you for sharing... **[/sarcasm]**

---

### Post by speedwell68 on 2008-12-25
> **turbozmike said:**
> I cant believe no one has figured out how to fix this issue with windows desktop trying to take over ubuntu's if nothing in the windows guest is open.

I have been fighting with this stupid issue for a few days, I just discovered that I could do this seamless business and can finally use linux as my daily OS.  I have work programs that flat out wont run on linux so this is great.

I simply made an additional taskbar and put it on the right side, made it small as possible and told it to autohide.  It serves its purpose and is only a little bit noticeable because it unhides when you close an application.

I only use XP in VirtualBox because I need to use Sony SonicStage for my mindisc player.  The wife uses it for Photoshop Elements, she is doing a college course that requires the minimum of Photoshop Elements.  If you require USB support use the release from Sun's website and not the repo version.

---

### Post by Giant Speck on 2008-12-25
Now that this thread is back in the limelight, I must ask:  Has anyone tried to use Windows 7 in VirtualBox with seamless mode on?

I'd be delighted to see some screenshots.  :)

---

### Post by dannytatom on 2008-12-25
I might give it a shot tomorrow, been considering it.

---

### Post by Frak on 2008-12-25
> **Giant Speck said:**
> Now that this thread is back in the limelight, I must ask:  Has anyone tried to use Windows 7 in VirtualBox with seamless mode on?

I'd be delighted to see some screenshots.  :)
Works, no screenshots though.

It just uses the Vista additions, so seamless is the same as Vista.

---

### Post by FirstByté on 2009-10-09
Good day y'all,

I have quite a bit of issue with my seamlessness so I discovered this thread.

**I must seek pardon ahead if my question is off the topic/core of this thread.** I've read through this thread a bit and saw no one having/addressing similar issue. Plus, I guess it's a rather more recent issue.

I run Windows XP guest on my Ubuntu Jackalope host with no qualms. However, since I have an Intel GPU, which had issues with Jackalope, Compiz effect was blacklisted (at /usr/bin/compiz) for me during upgrade--Due to Intel's change in core architecture et al...Since it worked for me in Ubuntu Intrepid, I decided to 'un'blacklist it and got my Compiz effect back and better... In such a way that my friends get their eyes stunned by the effects of Compiz. :popcorn: thanks Compiz guys u give us stuff to brag about. :P

However, enabling Compiz came at a cost. **I couldn't resume from hibernation, sleep mode to name a free GDM issues.** While I suspect the sleep/Hibernation seems to have been resolved, (I can't tell 'cause I disabled sleep/hibernation completely) **each time an application switches to fullscreen on my Windows XP guest, The top panel and lower panels of Ubunt disappears!** Though they are still there, and show whenever I click on the void/see-through space left. They become visible and respond to clicks. 


Pardon me if I'm posting this in a wrong thread. I know it has a lot to do with Intel's new thingy but any advice would help. I guess I might just be fine with Jaunty for a while though, so Kuala option might wait a bit :D

**What should be fixed?**

Thanks in advance!

---

### Post by -grubby on 2009-10-09
You should start a new thread for that. In the right sub-forum.

---

### Post by ternanta on 2009-10-09
think about it    ......   you could unlock the taskbar   ... easy to do   .... drag the top of the bar to the bottom of the window (it'll be just a thick line, now) .... lock it ... VIOLA ...presto chango :)

---

