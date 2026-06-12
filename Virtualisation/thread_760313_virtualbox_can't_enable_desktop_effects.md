---
title: "virtualbox can't enable desktop effects"
date: 2008-04-20
forum: Virtualisation
---

### Post by thunderwolf333 on 2008-04-20
I'm running Ubuntu in Virtual Box.
My primary system is xp.
I have a nvidia fx 5200 card.

I get the error "Desktop effects could not be enabled".

Any help would be appreciated but please be simple as I am still new to linux.

---

### Post by Antispaceman on 2008-04-20
Which version of Ubuntu are you using?

I am not entirely sure (seeing as its a virtualisation) but suggest that you may need restricted drivers

---

### Post by Tux Aubrey on 2008-04-20
VirtualBox is not using your graphics card - or any of your "real" hardware.  The virtual graphics card is very basic and will not run 3D effects.

While VB's are very useful for testing lots of stuff, they don't do glx graphix (yet).

---

### Post by thunderwolf333 on 2008-04-20
aw ok then I guess I will have to finally just install it as a partition. it's just easier to toggle with the virtual box but oh well.

thank you for your help. :D

---

### Post by olskar on 2008-04-20
You might find this interesting:

[http://forums.virtualbox.org/viewtopic.php?t=16](http://forums.virtualbox.org/viewtopic.php?t=16)

---

### Post by olskar on 2008-04-20
VMware apparently already have support for this:
[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)

---

### Post by taamir on 2009-06-24
Doe's Wubi support 3D effects ?

Edit : 
I now so some videos in youtube that are running 3D effects in VB...
Can any one please help me get it to work- it says that "Desktop effects can not be enabld "

Edit :
got it to work !

---

### Post by foxmajik on 2010-01-19
> **taamir said:**
> Doe's Wubi support 3D effects ?

Edit : 
I now so some videos in youtube that are running 3D effects in VB...
Can any one please help me get it to work- it says that "Desktop effects can not be enabld "

Edit :
got it to work !

Can you tell us how you got it to work?

---

### Post by KdotJ on 2010-05-06
Sorry to bump this, but could you (or anyone) tell us how to make this work?

---

### Post by foxmajik on 2010-05-06
> **KdotJ said:**
> Sorry to bump this, but could you (or anyone) tell us how to make this work?

Sorry for not keeping up with this thread.

As I understand it, the video drivers for Virtualbox guests do not support the required extensions for desktop effects.

Video drivers for Linux guests support only very basic OpenGL effects.

---

### Post by KdotJ on 2010-05-06
Ah ok, thanks for the quick response.
So I'm guessing that taamir was referring to getting the effects to work under Wubi rather than in VB...

---

### Post by foxmajik on 2010-05-06
> **KdotJ said:**
> Ah ok, thanks for the quick response.
So I'm guessing that taamir was referring to getting the effects to work under Wubi rather than in VB...

Wubi is an installer for Ubuntu that installs Ubuntu into a loopback filesystem inside a Windows partition.

Everyone person I've seen who has posted that they got desktop effects working in Virtualbox has become suddenly silent when asked how they did it.

---

### Post by KdotJ on 2010-05-06
> **foxmajik said:**
> 
Everyone person I've seen who has posted that they got desktop effects working in Virtualbox has become suddenly silent when asked how they did it.


lol go figure..

---

### Post by tilixibr on 2010-05-14
Did you install the guest additions? I got the effects working and no drivers had to be installed :)

Btw, to install the guest additions, go to the "Devices" Menu in the VM window, and select "Install Guest Additions". VBox will mount a disc on the VM. In my case, Ubuntu detected the disc to be a executable disk (or something like that), I allowed it to run and it did it all by itself in a few minutes. Then I restarted the VM and tried enabling desktop effects and it worked :)
I don't think the graphics card is an issue

I was the only one who managed to explain how I got Desktop Effects working on VBox :P

---

### Post by travelinman81 on 2010-06-21
I was also able to enable 3d effects in Virtual box using the same method. Also be sure that in the settings for your Virtual Machine you check the enable 3d effects tick box and then you probably want to dedicate 128 MB of Ram to video. I am running Centos as the host and I have an Ubuntu 10.04 VM with 1GB of Ram 128 MB for video and have 3d effects working. It is really no big deal you don't even have to RTFM. VBox has come a long way since I started using it several years ago.

---

### Post by carsonrose on 2010-07-07
> **KdotJ said:**
> lol go figure..


I am was successful enabling desktop effects in VB on a Win 7 host and a Fedora 12 host. Just enable the guest additions, reboot virtual box linux, then enable desktop effects..... bada bing!

---

### Post by roystreet on 2010-12-04
Hello,
    I was able to increase the screen resolution some...But I can't get it to increase very far.  

My host is Win7, 
Guest is ubuntu 10.10 32bit desktop.

I can't make the desktop effects run either.  (Althought I believe both are tied together
I do have a wubit install of ubuntu.  When I boot into that one, I have vbox installed w/winXP & I can totally resize XP & ubuntu works perfectly in the wubi...Including desktop effects, etc.

So, I know my system can run them, but when I'm running ubuntu as a guest on vbox, I can only stretch the screen so far & no effects will work..  Any ideas?

Thanks,
~roystreet

---

### Post by bprins on 2010-12-07
I don't know how some of you managed to get this working, but I am failing every try.

I have:
Ubuntu 10.10 64bit (host) and installed VirtualBox (3.2.12) on it.

I installed multiple guests (winXp, Mint, natty, ubuntu 10.10 i386)
**All guests have the 3D acceleration tickbox enabled.**

If I boot up e.g. Mint, or ubuntu10.10 i386 and in a shell I type:
glxinfo | grep rendering 
I get:
direct rendering: Yes

When I then try to enable desktop effects, after a while I see a messagebox stating that desktop effects can't be loaded.

Who can help me further?

Thanks.

Bas

---

### Post by liste on 2011-01-14
Hi everyone,

I don't know if there is anything in this or not, but I have not been able to get Compiz-Fusion and Desktop Effects enabled since Sun MicroSystems became a division of Oracle.  A long time ago I had Ubuntu 9.10 and the Desktop Effects enabled in VirtualBox.  Since then I upgraded to Ubuntu 10.04, still no problems.  Then Sun MicroSystems was bought out by Oracle and Oracle produced their first version of VirtualBox.  I have in my mind that was somewhere around version 3.2.0 or so, but I don't remember for sure.

Since I upgraded to Oracle VirtualBox I have no longer been able to get Desktop Effects enabled in my Ubuntu guest.  I have also had major troubles when saving my virtual machine.  I wish I could figure out what to do.  Sun Microsystems made VirtualBox work; Oracle broke it.  :(

---

### Post by liste on 2011-01-14
Sorry about the triple post.  :(

I posted the fix in the next post.  I have tried it in Ubuntu 10.10, 10.04, and XUbuntu 10.10, and the fix seems to work consistently.  If you have any questions, just post them!  :)

---

### Post by liste on 2011-01-14
OK.  Here is a link to a VirtualBox forum addressing the issue.  I'm attempting a fresh install of Ubuntu 10.10 on VirtualBox 3.2.12.  We'll see how it goes.
[http://forums.virtualbox.org/viewtopic.php?f=3&t=35218&sid=86ad6b311d4e6bad2542e5cd1f42608b&start=45](http://forums.virtualbox.org/viewtopic.php?f=3&t=35218&sid=86ad6b311d4e6bad2542e5cd1f42608b&start=45)

Finally this is what I did on my existing install, and it worked for me (copied from the link I pasted above):

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install dkms build-essential

reboot
install guest editions
reboot
turn on Desktop effects

If you experience the weird mouse moving windows in the wrong direction install compiz manager and turn off "Snapping Windows" and it goes away.

Hope that helps!

---

### Post by vol7ron on 2011-03-19
Host: Win7 64b Ultimate
Guest: Ubuntu 10.10
VM: VirtualBox 4.0.4

I didn't have to do any of the above, once installed I:
1) shut down the guest (Ubuntu) and went to VirtualBox
2) highlighted the VM and selected settings
3) went to display and beefed up the Virtual Memory (I'm planning to use the extra effects)
4) in the same display tab, check "Enable 3D Acceleration"


Before doing this I also installed the VirtualBox Guest Additions inside of Ubuntu ([http://ubuntuforums.org/showpost.php?p=8037797&postcount=13](http://ubuntuforums.org/showpost.php?p=8037797&postcount=13)), basically 1) add the CD to the devices and 2) run autorun.sh in terminal.

I'm going to see if installing these effects might work in VMWare Player as well (I doubt it, though).


**Update:** Not going to try it on VMWare - too much work to install a new OS, when I have things to do.  I wanted to note that I did perform some updates to Ubuntu, which must have replaced some drivers because the Extra Effects disappeared.  Installing the Guest Additions again got it to work.

---

