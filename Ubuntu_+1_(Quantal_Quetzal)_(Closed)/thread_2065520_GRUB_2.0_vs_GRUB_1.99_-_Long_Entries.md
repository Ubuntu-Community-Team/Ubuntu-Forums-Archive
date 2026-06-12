---
title: "GRUB 2.0 vs GRUB 1.99 - Long Entries"
date: 2012-10-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by amjjawad on 2012-10-02
Hi,

**[http://i46.tinypic.com/345fybs.jpg](http://i46.tinypic.com/345fybs.jpg)**

I'm aware that 12.10 will be shipped with GRUB version 2 but I'm still using GRUB 1.99 as shown in the above screenshot.

This is Asus F3F Laptop, Intel Core Duo T2350 @1.86GHz, 512MB RAM, Graphics is Intel 945GM/GMS and it is a multi-boot system with Lubuntu 12.04 as the main OS.

I was very surprised after I did the installation **[COLOR="Red"]of Lubuntu 12.10[/COLOR]** and updated GRUB from the main system that I have on that machine which is Lubuntu 12.04. Yes, GRUB 1.99 for Lubuntu 12.04 is installed in the MBR.

Why there are 3 entries instead of 2?
If I'm not mistaken:

[COLOR=#222222][FONT=arial][COLOR=#ff0000]Ubuntu' --class ubuntu  --class gun-linux  --class gnu  --class os  ....etc
[/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial][COLOR=#ff0000]
Ubuntu, with Linux 3.5.0-15-generic' --class ubuntu --class gnu-linux  --class gnu --class os ....etc
[/COLOR][/FONT][/COLOR][COLOR=#222222][FONT=arial]
Ubuntu, with Linux 3.5.0-15-generic (recovery mode )'  --class ubuntu --class gnu-linux  --class gnu --class os ....etc 
[/FONT][/COLOR]When I choose the first two in red, _**I guess**_ I get the same result. But again, why there are two? are they different or the same? 
Why the entries have very long names? is that a bug? some sort of compatibility issue between GRUB 1.99 and GRUB 2.0? what is going on?

Thanks!

P.S.
I have not installed GRUB 2.0 to the MBR yet and not planing to do so as of now.

---

### Post by grahammechanical on 2012-10-02
There are a couple of recent threads about Grub 2.0 which you may like to look through. Some of us have noticed things like this and a few are trying to work out why it is like that.

It is not clear if you have an install of 12.10. I guess that you must have.

I have found that Grub 2.0 has different designations for the kernels to that used by Grub 1.99. When running update-grub and putting Grub 2.0 into the MBR we get duplicate entries that are a combination of the new Grub 2.0 designations and the old Grub 1.99 designations. I am of the opinion that this is due to how update-grub works and not a bug with Grub 2.0 itself. But, hey, what do I know?

I have also found that Grub 1.99 on 12.04 will read the Grub 2.0 configurations files and create multiple entries.

Grub 2.0 allows for sub-menus. So, Recovery mode and older kernels are put into a sub-menu. So, you see 'Ubuntu' for the main 12.10 kernel and underneath 'Advance options for Ubuntu.' That is the sub-menu. There will be a similar sub-menu for every install of Ubuntu including 12.04.

But, Grub 1.99 cannot make use of sub-menus so it reads those Grub 2.0 configuration files and creates a long list of single entries in its menu.

Also, in each sub-menu there is first a link to the main kernel. So, that is a kind of duplication. We can load the main kernel by selecting its entry in the menu or from the Advanced Options list, without having to go backward a step.

My guess that in your menu "Ubuntu -class ubuntu" etc, refers to the main kernel which must be Linux 3.5.0-15. And "Ubuntu, with Linux 3.5.015" etc., is also referring to that same kernel but using the Grub 1.99 designation.

There is something I am curious about but that I cannot test.

What will someone with Ubuntu 12.04 get when they upgrade to 12.10? I know what will happen if they install 12.10 as a dual boot. But what kind of Grub menu will they see if they do a straight upgrade from 12.04 to 12.10? And what advice can we give to make the transition easier?

Regards.

---

### Post by jfernyhough on 2012-10-02
I have the same thing on my Mini311c; I'm running Ubuntu 12.04 as the main OS and Kubuntu 12.10 as a secondary installation. As such, grub 1.99 is installed to the MBR but the 12.10 grub config is grub 2.00.

I'd assumed that 1.99 doesn't know quite what to do with the 2.00 files so does the best it can, hence the extra stuff.

---

### Post by amjjawad on 2012-10-02
> **grahammechanical said:**
> There are a couple of recent threads about Grub 2.0 which you may like to look through. Some of us have noticed things like this and a few are trying to work out why it is like that.
Hi and thanks for posting. I have seen one thread and I'm sure there are more. I wanted to start my own thread to explain my own issue on my own test.

> It is not clear if you have an install of 12.10. I guess that you must have.
I have updated my post :)
Obviously, I have installed Lubuntu 12.10. If I understood you correctly, I think you were referring to that part.

> What will someone with Ubuntu 12.04 get when they upgrade to 12.10? I know what will happen if they install 12.10 as a dual boot. But what kind of Grub menu will they see if they do a straight upgrade from 12.04 to 12.10? And what advice can we give to make the transition easier?

They will have GRUB 2.0 because it will be a part of Lubuntu 12.10 packages.
The real question is, what kind of mess that will create? hopefully there will be NO mess but my first advise about that since things are not 100% clear will be: DO NOT upgrade, please do a clean install, which is always better IMHO.

---

### Post by grahammechanical on 2012-10-02
I have found out a little more since my last post.

Update-grub and update-grub2 do the same thing. They call an application x-executable called grub-mkconfig. That writes the grub.cfg file but it does not overwrite the MBR.

This is why when I run update-grub on my 12.10 installs the Grub of 12.04 remains in control.

I think, but I have not tested this that the command to save to MBR is grub-install.

A new installation must do more than run grub-mkconfig. It must also run grub-install because the new install over-writes what is already existing in the MBR.

I agree with your view that a new install will be best but unless Software Sources is set for LTS releases only, Update Manager will offer an upgrade to 12.10. What the resulting menu will look like I do not know. I do not have a separate hard disk to test this out.

Regards.

---

### Post by amjjawad on 2012-10-03
> **grahammechanical said:**
> Update-grub and update-grub2 do the same thing.
Yes. I thought you already know that :)
I think it is written somewhere on the Wiki? not 100% sure.

> They call an application x-executable called grub-mkconfig. That writes the grub.cfg file but it does not overwrite the MBR.
No overwrite UNTIL you install GRUB to the MBR. GRUB is too smart IMHO and it will not write itself by itself to the MBR.

> This is why when I run update-grub on my 12.10 installs the Grub of 12.04 remains in control.
Totally useless since GRUB of 12.04 is controlling the whole thing :)

> I think, but I have not tested this that the command to save to MBR is grub-install.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
This is a great source of information beside drs305 is one of the best guys who knows a lot about GRUB and he's one of the Forum Admins.

> A new installation must do more than run grub-mkconfig. It must also run grub-install because the new install over-writes what is already existing in the MBR.
New install, IMHO and AFAIK does:
Install GRUB then run update-grub before it finishes the installation.
As for installing to the MBR or not?
1- In case it is automatic install, it will be installed in the MBR.
2- If it is manual installation, then the user will decide where to install GRUB.

> I agree with your view that a new install will be best but unless Software Sources is set for LTS releases only, Update Manager will offer an upgrade to 12.10. What the resulting menu will look like I do not know. 
I don't like to upgrade and never upgraded an LTS release.

> I do not have a separate hard disk to test this out.
If you have a 4GB USB Drive, that would be more than enough ;)

---

### Post by Cavsfan on 2012-10-03
deleted

---

### Post by amjjawad on 2012-10-03
Aha, here is another guy who is obsessed about GRUB :D
Remember me? ;)

> **Cavsfan said:**
> I will throw this in: if you have re-installed any of your Ubuntus, you need to note the UUID of the one you are logged into via **sudo blkid**
Then edit fstab and correct the UUIDs **gksu gedit /etc/fstab**

It may have multiple UUIDs, the only one that should be there is the one that **sudo blkid** says should be in **fstab**.
There will most probably also be multiple entries for your swap file as well.
Just delete the old one(s) and save the file.

You will have to do this in each Ubuntu that you have re-installed.
And of course don't forget to enter **sudo update-grub** or **sudo update-grub2** (yes they both do the same thing).

Then when all of your fstab entries are correct, your boot menu should be correct.
Even when you delete a partition and reinstall the Ubuntu, somehow fstab remembers where the original UUIDs were. That is why I am saying you have to manually correct them.



Thanks for sharing your experience but that what I personally expected from GRUB version 2.
Ok, we both can do it but for new comers, I guess it is a bit of a problem for them.

With 1.99, we didn't have to do anything like that. Now, with 2.0, we do need to edit? this is not a good idea for many of users, I guess.

I don't have many systems there and I know what to choose but for those who have many systems, yes, they need to use GRUB Customizer which I have no idea how it will work with the new GRUB OR maybe your method :)

Thanks a lot :)

---

### Post by grahammechanical on 2012-10-03
Earlier I posted this:

> I think, but I have not tested this that the command to save to MBR is grub-install.

I can now confirm, through testing it myself, that this command

```
sudo grub-install /dev/sda
```

will save an updated Grub configuration into the MBR the first hard disc. In my case the only hard disk.

So, I now have a 12.10 Grub 2.0 menu in control, which is a bit neater than the mess that Grub 1.99 was making of the menu.

Regards.

---

### Post by amjjawad on 2012-10-03
> **grahammechanical said:**
> Earlier I posted this:



I can now confirm, through testing it myself, that this command

```
sudo grub-install /dev/sda
```

will save an updated Grub configuration into the MBR the first hard disc. In my case the only hard disk.

So, I now have a 12.10 Grub 2.0 menu in control, which is a bit neater than the mess that Grub 1.99 was making of the menu.

Regards.

The reason why I don't want to do that is: [http://ubuntuforums.org/showthread.php?t=2059108](http://ubuntuforums.org/showthread.php?t=2059108)

There are some bugs and GRUB 2.0 has the same long entries.

---

### Post by arpanaut on 2012-10-03
> There are some bugs and GRUB 2.0 has the same long entries.If you are using Grub 2.0  in the MBR of your booting disk this was corrected by Colin already with changes to the grub-prober script.

The issue with long entries has to do with Grub 1.99 being in your MBR of booting disk and Grub 2.0 being installed elsewhere.
the old grub-prober cannot parse the entries from Grub 2 correctly.
So if you have Grub 2 in charge of booting then there is not that issue. i.e. long entries.
Granted things have changed with what is presented in the menu but that is an easy adjustment.

---

### Post by amjjawad on 2012-10-03
> **arpanaut said:**
> If you are using Grub 2.0  in the MBR of your booting disk this was corrected by Colin already with changes to the grub-prober script.

Hi and thanks for posting!

That is good to know :)

> The issue with long entries has to do with Grub 1.99 being in your MBR of booting disk and Grub 2.0 being installed elsewhere.
Hope you don't mind my question but is that confirmed or it's your opinion? I'm so interesting to know, thanks :)

> the old grub-prober cannot parse the entries from Grub 2 correctly.

If that is so, then as I expected/thought, then it means 1.99 is not yet compatible with 2.0 and IMHO, that should be fixed as 12.04 which is LTS has GRUB 1.99 by default.

> So if you have Grub 2 in charge of booting then there is not that issue. i.e. long entries.
Granted things have changed with what is presented in the menu but that is an easy adjustment.

I guess the only way  that I can confirm this is by trying it myself. 
I need to follow one of these methods to re-install GRUB to the MBR: [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by Cavsfan on 2012-10-03
deleted

---

### Post by amjjawad on 2012-10-03
> **Cavsfan said:**
> **Amjjawad**, I posted a comment in that thread mentioning fstab and my tutorial/wiki.

There are no bugs in Grub 2.0 that I can see if you have correct fstab entries on each system and even better if you use my method of customizing the screen.
They have just decided to make sub-menu entries for when there are multiple kernels.
But, my custom grub2 screen does away with all of that and makes things simple.

I'm afraid you are missing my point :(
I'm not against your way and I'm not refusing to use it, my whole point is: why on the first place I/we need to do anything to correct that anyway?

As per the previous post, GRUB 2.0 will show normal short entries if installed in the MBR so I will try that :)

I have sometimes 10-12 systems installed and it will take some time to do that :)
However, the good news is, I no longer do that. It is just one P4 machine that sitting next to me with tons of systems installed and I'm not even using it for installation any more. I just use my ASUS Laptop these days.

Also, for new comers, IMHO, it may scare them a bit so we always should remember to give them the easiest solution and once they learn more about Linux in general and Ubuntu, it is time to give them more :D

Edit:
I forgot to add that I always delete and add partitions. Will your methods still effective?

---

### Post by dino99 on 2012-10-03
Reading your prose, that let me think yourself are not very sure about what to do or think; so stop doing the buzz here and read the other threads here about grub. Everything is already explained, so no need to add confusion. At first glance newbies are not there, except some of them.

):P

note: its a good idea to read the changelogs before spreading wrong info.

---

### Post by amjjawad on 2012-10-03
> **dino99 said:**
> Reading your prose, that let me think yourself are not very sure about what to do or think; so stop doing the buzz here and read the other threads here about grub. Everything is already explained, so no need to add confusion. At first glance newbies are not there, except some of them.

):P

note: its a good idea to read the changelogs before spreading wrong info.

What are you talking about? I don't know what you mean!

---

### Post by dino99 on 2012-10-03
> **amjjawad said:**
> What are you talking about? I don't know what you mean!

Really ?

[HTML]Hope you don't mind my question but is that confirmed or it's your opinion? I'm so interesting to know, thanks[/HTML]

---

### Post by amjjawad on 2012-10-03
> **dino99 said:**
> Really ?

[HTML]Hope you don't mind my question but is that confirmed or it's your opinion? I'm so interesting to know, thanks[/HTML]

That Q wasn't for you, I'm afraid :)

---

### Post by amjjawad on 2012-10-03
> **arpanaut said:**
> If you are using Grub 2.0  in the MBR of your booting disk this was corrected by Colin already with changes to the grub-prober script.

The issue with long entries has to do with Grub 1.99 being in your MBR of booting disk and Grub 2.0 being installed elsewhere.
the old grub-prober cannot parse the entries from Grub 2 correctly.
So if you have Grub 2 in charge of booting then there is not that issue. i.e. long entries.
Granted things have changed with what is presented in the menu but that is an easy adjustment.

```
sudo grub-install /dev/sda
```

```
sudo update-grub

```

Now, GRUB version 2 is controlling the whole thing.
But again, there is no way to tell what partition that installation has been installed at like GRUB 1.99 used to show.

---

### Post by arpanaut on 2012-10-03
> But again, there is no way to tell what partition that installation has been installed at like GRUB 1.99 used to show.

Yeah that is one of my gripes about the new grub, 
but you can highlight any entry and hit 'e' and the "set root=" entry there 
will show where the installation is.

Not a big deal for the average user who has only 1-2 installations.
And for people who have many multiple installations, it is just an extra step.
We have already complicated things for ourselves, so not a biggie.

---

### Post by amjjawad on 2012-10-03
> **arpanaut said:**
> Yeah that is one of my gripes about the new grub, 
but you can highlight any entry and hit 'e' and the "set root=" entry there 
will show where the installation is.

Not a big deal for the average user who has only 1-2 installations.
And for people who have many multiple installations, it is just an extra step.
We have already complicated things for ourselves, so not a biggie.

Yes, I'm aware of that of course ;)
And I agree with your point too :)


So, bottom line:
1- Is there away so far to tell without the extra step in case someone else is too lazy to do that?
2- Is there any way for GRUB 1.99 to have normal entries?

Edit:
Have you tested GRUB Customizer with the new GRUB?

---

### Post by grahammechanical on 2012-10-03
Regarding Grub Customizer

The latest version is 3.0.2. It has a new interface. I am trying it out on a 12.10 install. I think that it will be usable if we can get rid of those long file names.

You will need to run Grub Customizer with the command:

```
sudo grub-customizer
```

Actually grub-customizer will also work but you will then need to authenticate. 

Then you wait for at least 15 minutes for the user interface to appear. You get this message in the terminal:

> reading partition info...

And it takes about 15 minutes to do that. I do not know why. Perhaps it is because I have ten partitions and four Ubuntus.

It does recognise the submenus.

You can right click a menuentry and get a small menu. The Edit option will show what the boot parameters are for that entry.

Submenus are shown with a folder icon which a mouse click will expand to show what is in the submenu.

I suggest as a first step remove all old kernels (keep the latest two) from each install to avoid unnecessary entries.

Run update-grub from each install to, hopefully get a cleaner configuration file.

Do not run update-grub from 12.04 unless you have the latest grub customizer and are going to use 12.04 as your boot menu control.

If you want to use Grub 2.0 on 12.10 as the control, then run update-grub and then

```
sudo grub-install /dev/sda
``` to save grub to the MBR and run grub customizer from that install.

Do one edit at a time and test to see if things have improved. Make sure you do not remove from the grub customizer list those kernels that you want to keep.

Regards.

---

### Post by philinux on 2012-10-03
Amjjawad. Why not install grub 2 to the mbr of the disk from a live usb.

---

### Post by amjjawad on 2012-10-03
> **philinux said:**
> Amjjawad. Why not install grub 2 to the mbr of the disk from a live usb.

I installed it from Lubuntu 12.10 as per this: [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

GRUB 2.0 is now installed in the MBR of sda and it is working.

---

### Post by cariboo on 2012-10-03
Remove user deleted post

---

### Post by GeorgeVita on 2012-10-04
> **amjjawad said:**
>  ... GRUB 2.0 is now installed in the MBR of sda and it is working.
... but rest of your system still has previous versions of grub-associated programs. Check their versions:

```
update-grub -v
grub-install -v
```
When you boot the previous system (ex. 10,04, 12.04) which comes with grub 1.98 or 1.99, after any kernel update your grub configuration file will be changed using previous version (1.98 or 1.98[SIZE="1"] [/SIZE]) procedures. I don't know if this is "typical", possibly will work fine.

**General note: "playing" with GRUB will probably make your system not-bootable!**

---

### Post by philinux on 2012-10-04
amjjawad, just so folks can help run the bootinfoscript and post back the results.txt file.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by grahammechanical on 2012-10-04
Quote

> When you boot the previous system (ex. 10,04, 12.04) which comes with grub 1.98 or 1.99, after any kernel update your grub configuration file will be changed using previous version (1.98 or 1.98) procedures. I don't know if this is "typical", possibly will work fine.

Not necessarily. It happened to me the other day when my 12.04 had Grub itself updated. Grub 1.99 made a horrible mess of the menu.

But on my 3 x 12.10 installs when the kernel went from 3.5.0-15 to 3.5.0-16 the Grub configuration files were updated but the changes were not saved into the MBR. Grub 1.99 on 12.04 remained in control.

To get control back onto Grub 2.0 on a 12.10 install I had to run update-grub and grub-install /dev/sda. Having earlier removed all old kernels I now get a much neater but still not perfect Grub menu.

I do wonder what will happen when ordinary users upgrade from 12.04 to 12.10. Or, if sometime during the next five years Grub 2.0 is brought into 12.04. What kind of menu will they see?

I am used to having the Grub menu altered every time my installs get a kernel update. I simply put my non-testing install back in charge. This is part of the job description when doing ISO testing on a single hard disk machine.

I usually use Grub Customer. I shall test it out to see how well it copes with Grub 2 and its sub-menus.

Regards.

---

### Post by amjjawad on 2012-10-13
> **GeorgeVita said:**
> ... but rest of your system still has previous versions of grub-associated programs. Check their versions:

```
update-grub -v
grub-install -v
```
When you boot the previous system (ex. 10,04, 12.04) which comes with grub 1.98 or 1.99, after any kernel update your grub configuration file will be changed using previous version (1.98 or 1.98[SIZE="1"] [/SIZE]) procedures. I don't know if this is "typical", possibly will work fine.

**General note: "playing" with GRUB will probably make your system not-bootable!**

Hmm, I have no problem logging in to any other system. Well, at least as of now.

---

### Post by amjjawad on 2012-10-13
> **grahammechanical said:**
> I usually use Grub Customer. 

On my other test machine with 12 systems installed, GRUB Customizer is creating so much problems for me. It happened twice or three time so far.
Looks like it can't handle that much of systems.

---

