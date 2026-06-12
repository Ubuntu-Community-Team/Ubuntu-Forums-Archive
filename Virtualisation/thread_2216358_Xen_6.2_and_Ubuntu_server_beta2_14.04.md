---
title: "Xen 6.2 and Ubuntu server beta2 14.04"
date: 2014-04-11
forum: Virtualisation
---

### Post by drenda on 2014-04-11
Hello to all, 
I just installed Ubuntu Server 14.04 beta2 on Xen Server 6.2 on which I have other virtual machines ubuntu (12.04) installed. The installation procedure is successful as usual, but this time the virtual machine does not start because of this error: 

April 11, 2014 4:04:40 PM Error: Starting VM 'Development' - The bootloader for this VM returned an error - did the VM installation succeed? Unable to find partition containing kernel 

I state that Grub is installed on the MBR and I have tried either with a separate /boot ext3 partition that with unique /  ext4 partition. 

Does anyone have some idea of what could be the problem? 

thanks very much!

---

### Post by karnaugh2 on 2014-04-17
I see the same problem, have not gotten that far into why but did successfully deploy with HVM template. Not optimal though :/

---

### Post by japje2 on 2014-04-18
I managed to get Ubuntu 14.04 LTS 64bit working on xenserver 6.2.

I used the same method to get a new template as described [here]("http://invalidlogic.com/2012/05/01/deploying-ubuntu-12-04-on-xenserver-made-easy/"). But ofcourse used  "other-config:debian-release=Trusty" while setting the parameters.

So now with the new template start a new installation of Trusty. 

Create a /boot partition that is ext2.

[B]Do not install grub2!, instead drop to shell, chroot to /target, install grub, and run update-grub.

[/B]Then resume the installation, reboot. Install xentools from the iso and you should have a working  Ubuntu 14.04 LTS 64bit on xenserver 6.2 :)

---

### Post by todd5 on 2014-04-18
> **japje2 said:**
> [B]Do not install grub2!, instead drop to shell, chroot to /target, install grub, and run update-grub.

[/B]Then resume the installation



newb here.  how do you drop to a shell in the middle of an install, then how do you get back to the install?

---

### Post by japje2 on 2014-04-18
> **todd5 said:**
> newb here.  how do you drop to a shell in the middle of an install, then how do you get back to the install?


Select 'go back' at the screen where it requests to install grub. In the menu you get go down untill you see the execute shell option.

---

### Post by mindbender9 on 2014-04-20
> **japje2 said:**
> Select 'go back' at the screen where it requests to install grub. In the menu you get go down untill you see the execute shell option.

Sorry... another newb here. Can you explain how to manually install grub1? I can get to the Shell during the install, but there is no grub-install' app to run. 

Running: Xenserver v6.2 but trying to install Ubuntu v14.04 x64 via the iso. I have created the /boot dir in ext2 and the / folder in ext4 (used the steps found here: [https://gist.github.com/ypchen/3187714](https://gist.github.com/ypchen/3187714)), but the reboot fails immediately after the install with the following error:

> Apr 20, 2014 2:20:18 PM Error: Starting VM 'ubuntu' - The bootloader for this VM returned an error -- did the VM installation succeed?  Unable to find partition containing kernel

Can anyone help? I am amazed by the number of people running into this problem but yet there seems to be no easy solution.

Thank you for your help.

---

### Post by ipolit on 2014-04-22
There is no need of creating ext2 for boot, but it could be made.
When the installaion reaches the **grub2 installation point**, select **Go  back**. The install menu will appear. Scroll down to **execute shell** option. Execute the following 

 [FONT=courier new]chroot /target
apt-get install grub
grub-install /dev/xvda 
update-grub 
[/FONT] confirm generation of** menu.lst **

 [FONT=courier new]exit
exit
[/FONT] in the menu press **finish installation**. 
For me it works. Thanks to[**[COLOR=#000000] japje2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1917712")

---

### Post by japje2 on 2014-04-22
> **ipolit said:**
> There is no need of creating ext2 for boot, but it could be made.
When the installaion reaches the **grub2 installation point**, select **Go  back**. The install menu will appear. Scroll down to **execute shell** option. Execute the following 

 [FONT=courier new]chroot /target
apt-get install grub
grub-install /dev/xvda 
update-grub 
[/FONT] confirm generation of** menu.lst **

 [FONT=courier new]exit
exit
[/FONT] in the menu press **finish installation**. 
For me it works. Thanks to[**[COLOR=#000000] japje2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1917712")


These are the steps indeed :-) 

The cause of this (afaik) is the grub2 support in PyGrub. So dist-upgrading your 12.04 can work, if you change to grub (legacy). 
Untill PyGrub is 'fixed' in XenServer this is i think the only solution.

---

### Post by mindbender9 on 2014-04-23
> **ipolit said:**
> [FONT=courier new]
[/FONT] in the menu press **finish installation**. 
For me it works. Thanks to[**[COLOR=#000000] japje2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1917712")

First, thank you for posting the instructions. I really appreciate your help with this.

Unfortunately, I find that the v14.04 Server install fails right after I click on "Finish the Installation" in the menu. What I end up seeing is a blank screen with the solid cursor in the lower left corner. The CPU then runs at 100% constantly - this happened twice to me when I followed your instructions.

On my second attempt, I left the install running overnight and still had the same result in the morning. Rebooting the install causes the 14.04 server to boot partially due to it not completing.

Any suggestions?

---

### Post by bart6 on 2014-04-23
follow japje2 and ipolit suggestion and after exit exit do not choose finish installation from menu
instead choose don't install grub and then complete installation
Works on XenServer 6.2 (all updates installed) + ubuntu 14.04 server current official
hope this helps ::

---

### Post by mindbender9 on 2014-04-24
> **bart6 said:**
> follow japje2 and ipolit suggestion and after exit exit do not choose finish installation from menu
instead choose don't install grub and then complete installation

I wanted to thank everyone here for all of the help. I was able to get 14.04 working successfully on Xenserver v6.2.

I love it when the community comes to the aid of users such as myself. Thanks again everyone!

---

### Post by matt_fussell2 on 2014-04-25
subscribed - I may be trying this out next week.

---

### Post by Steve_McMaster on 2014-04-28
This worked for me without having to install legacy grub:

1) Modify /usr/lib/python2.4/site-packages/grub/GrubConf.py on the XenServer machine
2) Line 428, change:
> if arg.strip() == "${saved_entry}":
to
> if arg.strip() == "${saved_entry}" or arg.strip() == "${next_entry}":
3) Boot your new VM that won't start, or create a new VM.

I've only tested this once, but it worked for me. Hope that helps someone else too.

---

### Post by dave116 on 2014-04-29
> **Steve_McMaster said:**
> This worked for me without having to install legacy grub:

1) Modify /usr/lib/python2.4/site-packages/grub/GrubConf.py on the XenServer machine
2) Line 428, change:

to

3) Boot your new VM that won't start, or create a new VM.

I've only tested this once, but it worked for me. Hope that helps someone else too.


I can confirm this solution works... BUT

dont remove the line and then add the entire new line, that then gives a Syntax error regarding the block of code.

Rather append the following
```

[COLOR=#000000][I]or arg.strip() == "${next_entry}"
[/I][/COLOR]
```
[COLOR=#000000][I]
to the line 428
[/I][/COLOR]```
[COLOR=#000000][I]if arg.strip() == "${saved_entry}":
[/I][/COLOR]
```[COLOR=#000000][I]

to make it look like this:
[/I][/COLOR]```
[COLOR=#000000][I]if arg.strip() == "${saved_entry}" or arg.strip() == "${next_entry}":
[/I][/COLOR]
```[COLOR=#000000][I]


I have tested 4x 14.04 installations now, reboots, halts, etc and I can confirm the above fix works.[/I][/COLOR]

---

### Post by Zonique on 2014-04-30
> **Steve_McMaster said:**
> This worked for me without having to install legacy grub:

1) Modify /usr/lib/python2.4/site-packages/grub/GrubConf.py on the XenServer machine
2) Line 428, change:
```
if arg.strip() == "${saved_entry}":
```

to
```
if arg.strip() == "${saved_entry}" or arg.strip() == "${next_entry}":
```

3) Boot your new VM that won't start, or create a new VM.

I've only tested this once, but it worked for me. Hope that helps someone else too.

Noticed that this has been patched in the Xenserver code base approximately 10 months ago:
[https://github.com/xenserver/xen-4.3/commit/2196372e76456ce859230950a6e484343e990423](https://github.com/xenserver/xen-4.3/commit/2196372e76456ce859230950a6e484343e990423)

Would have expected it in the mainstream binaries (or patches) by now...

---

### Post by jsnlry on 2014-05-31
Hi! Thanks for all the information, it helped a lot. I added the ext2-/boot partition and now the server boots but I'm stuck with one final problem:

When I boot my VM I cannot see any output in XenCenter console tab. All I see is a black screen with a white cursor in the upper left corner.

Any idea what's the problem? I already tried to do this, but with no effects: [http://support.citrix.com/article/CTX128753](http://support.citrix.com/article/CTX128753)

---

### Post by jsnlry on 2014-05-31
Ok. Did the installation again, and now it works. The difference: First I installed it via *VM --> Start/Shut down --> Start in Recovery Mode* and did the Ubuntu installation as I do it on a normal server (using *Expert Mode*). Now I installed it using the installer that appeared after creating the VM.

So, looks like there's some magic happening when installing it *the direct way*, but I love the expert mode and use it almost every time. Since I'm new to XenServer I'd like to know what's the difference. Any idea?

---

### Post by nroussi on 2014-07-11
Thank you Steve_McMaster. That worked perfectly.

---

### Post by Barmynon on 2014-07-27
I found the above didn't work for me- but I had just applied the XS62ESP1006 patch release- not sure if that should have any bearing. After an hour of cutting, pasting and rewriting in an attempt to get the suggested solution working, I eventually had success with the following:

[https://github.com/xenserver/xen-4.3/commit/2196372e76456ce859230950a6e484343e990423](https://github.com/xenserver/xen-4.3/commit/2196372e76456ce859230950a6e484343e990423)

Which details the following
```
[SIZE=3]
	                 if self.commands[com] is not None:
	                     if arg.strip() == "${saved_entry}":
	                         arg = "0"
                             elif arg.strip() == "${next_entry}":
                                 arg = "0
                         setattr(self, self.commands[com], arg.strip()[/SIZE]

```

So in essence adding an elif rather than extending the existing command with an OR statement. I hope this helps some others.

---

### Post by Yong_Kam_Wah on 2014-08-02
[SIZE=2][FONT=arial]Yes, i manage to install Ubuntu 14.04 on my XenServer 6.2 SP1 Server successfully by [/FONT]

[COLOR=#000000][FONT=arial][I]Modify /usr/lib/python2.4/site-packages/grub/GrubConf.py on the XenServer machine
from 
[/I][/FONT][/COLOR][FONT=arial]“if arg.strip() == "${saved_entry}":”[/FONT]
[FONT=arial]to [/FONT]
**if arg.strip() == "${saved_entry}" or arg.strip() == "${next_entry}":**
[COLOR=#000000][FONT=arial][/FONT][/COLOR][FONT=arial]Load the xs-tools.iso 
sudo mount /dev/xvdd /media/cdrom 
[/FONT][FONT=arial]sudo dpkg -i /media/cdrom/Linux/xe-guest-utilities_6.2.0-1133_amd64.deb [/FONT]

[FONT=arial]Successfully booted my Ubuntu 14.04 with Xen Tool installed on XenServer 6.2 SP1 Server[/FONT]

[FONT=arial]Thanks everyone for helps. [/FONT]
[/SIZE][FONT=Courier New]
[/FONT]

---

### Post by volkswagner on 2014-08-02
> **Steve_McMaster said:**
> This worked for me without having to install legacy grub:

1) Modify /usr/lib/python2.4/site-packages/grub/GrubConf.py on the XenServer machine
2) Line 428, change:

to

3) Boot your new VM that won't start, or create a new VM.

I've only tested this once, but it worked for me. Hope that helps someone else too.

Thank you for posting this.  Worked for me when upgrade from 12.04 to 14.04 would not boot using XenServer 6.2

---

### Post by MisterIX on 2014-09-09
Hey there,

I hope I'm right in this thread, but i followed the instructions of japje and minbender9 to install ubuntu 14.04 on Xen 6.2. In my case Ubuntu starts, but in the Xen-Center Console the last shown entry is STOPPING SYSTEM V RUNLEVEL COMPATIBILITY and no login prompt shows up.

SSH is running fine though and there are no unusual mistakes, that would keep me from configuring Ubuntu. Only in case the SSH is going to fail, the server is going to be unreachable.

Any suggestions, what the problem might be?

Kindly, MisterIX.

):P


[h=2][/h]

---

### Post by tim68 on 2014-09-30
So, I just broke my VM on XenServer by upgrading from 12.04 to 14.04 (do-release-update). Of course, I didn't take a snapshot beforehand, nor did I bother to read anything regarding compatibility of XenServer 6.2 and Ubuntu 14.04. 

Having said that, am I able to repair this by booting into a live CD and doing the following which was suggested earlier in this thread?
[COLOR=#000000][FONT=courier new]
[/FONT][/COLOR]> 
chroot /target
apt-get install grub
grub-install /dev/xvda 
update-grub 


[COLOR=#000000][FONT=courier new]
Any other suggestions would be appreciated! If I can't repair this, I'm going to need to rebuild a new VM from scratch and hopefully recover the data from my non-bootable environment. 






[/FONT][/COLOR]

---

### Post by filipposd on 2014-10-03
> **volkswagner said:**
> Thank you for posting this.  Worked for me when upgrade from 12.04 to 14.04 would not boot using XenServer 6.2
Hi everyone,
I have Xen 6.2 and Ubuntu 14.04 and in that file I'm supposed to edit I don't have these lines at all... so there's nothing to edit. Should I insert it? I really don't want to mess the entire server...
As this is a clean VM that I have just started to install, does anyone know a guide for fresh installation that works?

---

### Post by tim68 on 2014-10-09
> **Steve_McMaster said:**
> This worked for me without having to install legacy grub:

1) Modify /usr/lib/python2.4/site-packages/grub/GrubConf.py on the XenServer machine
2) Line 428, change:

to

3) Boot your new VM that won't start, or create a new VM.

I've only tested this once, but it worked for me. Hope that helps someone else too.

This worked for me as well, thanks!

---

