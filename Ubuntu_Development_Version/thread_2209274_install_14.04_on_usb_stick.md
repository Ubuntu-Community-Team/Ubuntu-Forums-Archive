---
title: "install 14.04 on usb stick"
date: 2014-03-04
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2014-03-04
need some help. been using linux for about 7 years but i am lost on how to do this. and i have been googling for a couple of days on how to do. i have a 32 gig flash drive and i want to install 14.04 on it. not a live cd version i can do this. but want to install a full blown verions on it. how do i proceed. there has got to be a way just cant figure it out, tks
unetbootin just gives me a live cd.

---

### Post by QDR06VV9 on 2014-03-04
> **rburkartjo said:**
> need some help. been using linux for about 7 years but i am lost on how to do this. and i have been googling for a couple of days on how to do. i have a 32 gig flash drive and i want to install 14.04 on it. not a live cd version i can do this. but want to install a full blown verions on it. how do i proceed. there has got to be a way just cant figure it out, tks
unetbootin just gives me a live cd.

You will probably get a few suggestions for this request.
But I will inflict you with my method.
Best if you have 2 usb sticks, But if you  do not then you will need 
a dvd to burn your install .iso to.
1.K3b is my favorite DVD or anything disc tool.(.iso)
2. Unetbootin is my favorite USB Tool
Your choice here.
After I have the install medium finished, (DVD) (USB)
Install just like you would a regular install,
Until you come to partitioning Choices, For this pick something else,
then look for your usb stick format accordingly install and enjoy.
[B][U]Strong Suggestion here, before you begin your install I undo, disconnect
my other harddrive(s):D[/U][/B]

---

### Post by varunendra on 2014-03-05
> **runrickus said:**
> 
Install just like you would a regular install,
Until you come to partioning Choices, For this pick something else,
then look for your usb stick format acordingly install and enjoy.
Exactly this ^^. One very important addition to above suggestion though (writing by memory of 12.04 installation) - On the partition selection screen, make sure the **target for Grub installation is your target USB drive**, not the local hard disk or source USB (in case you have booted from a 2nd USB). Otherwise the installation would be fine, but the boot manager would be installed on a wrong place.

So, assuming the system on which you would be doing this is booting in legacy (MBR) mode, not UEFI mode, this is the summary of installation -
[LIST=1]
[*]Boot from a live DVD/USB
[*]On partition selection stage, choose "Something Else.."
[*]Create/Select partition(s) on your target USB drive as mount point for root (/)
[*]Make sure the target for Grub is also the same USB drive, not a 'Partition' or another drive (e.g. **/dev/sdc** or **/dev/sdd** etc., NOT **/dev/sdc[COLOR="#FF0000"]1[/COLOR]** or **/dev/sdd[COLOR="#FF0000"]1[/COLOR]**..)
[*]Install normally and finish.
[/LIST]

**PS:**
A few things about **Live Persistent Vs. Full install** that everyone should be aware of : [http://ubuntuforums.org/showpost.php?p=12857885](http://ubuntuforums.org/showpost.php?p=12857885)

---

### Post by QDR06VV9 on 2014-03-05
> **varunendra said:**
> 
[LIST=1]
[*]_Make sure the target for Grub is also the same USB drive, not a 'Partition' or another drive (e.g. **/dev/sdc** or **/dev/sdd** etc., NOT **/dev/sdc[COLOR=#FF0000]1[/COLOR]** or **/dev/sdd[COLOR=#FF0000]1[/COLOR]**..)_ 
[*]Install normally and finish. 
[/LIST]

**PS:**
A few things about **Live Persistent Vs. Full install** that everyone should be aware of : [http://ubuntuforums.org/showpost.php?p=12857885](http://ubuntuforums.org/showpost.php?p=12857885)
Thats the whole reason for this.
```
Strong Sugjestion here, before you begin your install I undo, diconect
my other harddrive(s):grin:
```
But on the other hand the OP dose not seem to reply to his own requests.;)

---

### Post by varunendra on 2014-03-06
> **runrickus said:**
> Thats the whole reason for this.
```
Strong Sugjestion here, before you begin your install I undo, diconect
my other harddrive(s):grin:
```
You didn't tell them 'Why'. And what about the Source USB from which one might be booting?

I have NEVER seen Grub installed on Hard Disk when you are installing on a USB drive. The confusion that OFTEN happens is that it gets installed on the SOURCE USB instead of the target drive (internal OR external).

What I emphasized was what I have experienced - frequently, and what you suggested didn't cover it.

---

### Post by ventrical on 2014-03-06
That was covered pretty good here:

[http://www.youtube.com/watch?v=h8i67KksFlo&feature=youtu.be](http://www.youtube.com/watch?v=h8i67KksFlo&feature=youtu.be)

and here:

[http://ubuntuforums.org/showthread.php?t=2206472&p=12933663#post12933663](http://ubuntuforums.org/showthread.php?t=2206472&p=12933663#post12933663)

Regards..

---

### Post by QDR06VV9 on 2014-03-06
> **varunendra said:**
> You didn't tell them 'Why'. And what about the Source USB from which one might be booting?

I have NEVER seen Grub installed on Hard Disk when you are installing on a USB drive. The confusion that OFTEN happens is that it gets installed on the SOURCE USB instead of the target drive (internal OR external).

What I emphasized was what I have experienced - frequently, and what you suggested didn't cover it.
Fair enough. But the OP said "been using linux for about 7 years"
Yes I got lazy:P Thanks Vent for picking up my slack:) I was actually looking for the second link in your post to no avail on my first thread.
And this guy has not responded to a lot of his own threads???:confused:

---

### Post by rtalcott on 2014-03-06
I'll say Thank You because this was very useful to me.

---

### Post by ventrical on 2014-03-06
> **runrickus said:**
> Fair enough. But the OP said "been using linux for about 7 years"
Yes I got lazy:P Thanks Vent for picking up my slack:) I was actually looking for the second link in your post to no avail on my first thread.
And this guy has not responded to a lot of his own threads???:confused:

 You got it absolutely right!! (Your method). Take the hdd out !! No muss , no fuss with GRuB. When I first did this back during Maveric cycle I was dumbfounded!! I could stick my Lucid/Maveric USB into most any old tower/laptop and it would boot as if it were my own PC. The same still applies on my USB ver 3 with Trusty.. except faster ! :)lol

  I haven't noticed any regression on USB drives that I created well over 3 and 1/2 years ago.

Regards

edit:
 as for OP  :) .. who knows where he went ? :) lol

---

### Post by ventrical on 2014-03-06
> **rtalcott said:**
> I'll say Thank You because this was very useful to me.

 Ubiquity has this unique, built-in property to recognize a USB flash drive as if it were an actual hdd. It was (and still is) one of those hidden treasures built in to Ubuntu that kept me really interested (and still does)

  The other thing (a little off topic) is that now the  Ubiquity installer is trwice as fast as it used to be and it will take all of your home files and bookmarks .. etc. and carry them over to  your new re-install. The developers have streamlined these processes well beyond the edge, does not make Jack a dull boy and is saves tons of downtime.:)

Regards..

---

### Post by varunendra on 2014-03-06
> **runrickus said:**
> Fair enough. But the OP said "been using linux for about 7 years"
....
And this guy has not responded to a lot of his own threads???:confused:
I have seen many users who have been members since the beginning of this forum (2005), but they don't know even the basics we usually expect a regular Linux user should know. I don't see anything wrong with that. On the contrary, it proves the fact that one doesn't have to be a 'computer geek' to be able to use Ubuntu. It is as easy as any other popular OS for an average computer user.

Also, regardless of whether the OP remains active or not, I usually try to make my answers as complete and clear as possible. If the original question is clear, and so is the answer, it will be helpful to many, not just to OP.

> **ventrical said:**
> Take the hdd out !! No muss , no fuss with GRuB.
@ventrical, most of the 'normal users' would run away as soon as you tell them that they have to open their computer case just to be sure that the OS installs properly. The 'nerdy' ways should come later, when the 'standard' ways have failed and the poster is still interested. :)

---

### Post by ventrical on 2014-03-06
> **varunendra said:**
> I have seen many users who have been members since the beginning of this forum (2005), but they don't know even the basics we usually expect a regular Linux user should know. I don't see anything wrong with that. On the contrary, it proves the fact that one doesn't have to be a 'computer geek' to be able to use Ubuntu. It is as easy as any other popular OS for an average computer user.

Also, regardless of whether the OP remains active or not, I usually try to make my answers as complete and clear as possible. If the original question is clear, and so is the answer, it will be helpful to many, not just to OP.


@ventrical, most of the 'normal users' would run away as soon as you tell them that they have to open their computer case just to be sure that the OS installs properly. The 'nerdy' ways should come later, when the 'standard' ways have failed and the poster is still interested. :)


The majority of the standard ways do fail. That is why I basically cut to the chase on this one. However , there are certain cases , certain hardware that will allow for a successful install if an end_user is willing to share info about their PC. Also , nerd or no nerd , in 99 percent of all  cases dealing with an install to an USB it is most often required that an end_user have some basic knowledge of CMOS/BIOS and firmware. (Can't boot from a USB unless it is set in BIOS on across several different form factors - unless using the PLOP bootloader) so , if they  have a hard time disconnecting  their hdd they will probably have an equally difficult time navigating through thier BIOS that is , unless , there is  some kind ubuntuforums member that is willing to walk them through it.

  Also , remember, that we are in U+1 here. Sort of cutting edge stuff. At least we hear lots of banter about it.  I know it is not prerequisite for a U+1 participant to have a mindset to be on the cutting edge of things but to be able to achieve some of the more effervescent attributes that Ubuntu-linux offers to us , then we have to be willing to try some different things else then we can always embrace the mediocre methods of accomplishing these things and end up with an unsurrmountable downtime. As per getting topical again, installing 14.04 on a USB stick was a slice using the method I have  explained. I had also been able to perform this proceedure  without moving the harddrive but then there is BIOS and GRuB considerations .. etc.. so why not use Occam's razor in this case?

Regards..

---

### Post by varunendra on 2014-03-06
> **ventrical said:**
> The majority of the standard ways do fail.
That has never been, nor should ever be a reason to discard 'Standard' ways and promote the geeky ways.
If the user is not an advanced computer user, most probably they'd be scared to go "hardware mode" just to install an OS.
If the user IS and advance user, that is more a reason why they should know "What's and Why's".

Shortcuts are rarely a good option when they are far off from 'Standard' ways.

> **ventrical said:**
> nerd or no nerd , in 99 percent of all  cases dealing with an install to an USB it is most often required that an end_user have some basic knowledge of CMOS/BIOS and firmware.
'Basic' knowledge of BIOS (which is all that is required), is no reason to believe that a user would also be willing and comfortable with opening their case and fiddling with wires/ports. Especially when an additional two-line information (where to install GRUB, How and Why) is all they need to avoid that.

> if they  have a hard time disconnecting  their hdd they will probably have an equally difficult time navigating through thier BIOS that is
Sorry, can't agree with that. There is a reason why no official guide about booting from USB even mentions the word 'hardware'.
Finding and changing BIOS options is often trivial and safe. Fiddling with cables inside a cabinet is niether trivial nor safe.

> Also , remember, that we are in U+1 here. Sort of cutting edge stuff.
..<snip>..
installing 14.04 on a USB stick was a slice using the method I have  explained.
I don't need to mention how new users tend to think "latest is greatest" and thus end up with U+1 without a good understanding of even the OS, let alone BIOS or hardware. The OP is not a new user, but like I mentioned before, I like my answers to be complete and helpful for "Everyone" if possible.

And lastly, as also mentioned earlier, what about the Source USB which you are booting from? Disconnecting HDDs is not going to eliminate that possibility which is _almost always_ the case in "Grub misplaced" issues.

---

### Post by ventrical on 2014-03-06
> **varunendra said:**
>  <snip>

And lastly, as also mentioned earlier, what about the Source USB which you are booting from? Disconnecting HDDs is not going to eliminate that possibility which is _almost always_ the case in "Grub misplaced" issues.

 Never happened here for ... lemme see.. 4 years of doing this. Perhaps you have a case point ref but it hasn't happened here. I have learned to do what works for me. I like to experiement and I like to share the results of my experiments.  Others do what  works for them.  When I post here I do not expect end_users to do what I have done to accomplish  the same results. There are some here who do like working with hardware, like to experiement and know the risks. I am not offering shorcuts. I offered a solution that works. It may not work for you , but it may work for someone else. Just like your method does not jive with me , but it may jive with another end_user.

  Thats is why Ubuntu is so diverse. There are so many ways of doing things differently. There is so much to discover, if only one is willing to do so. Other commercial  OS testing expect endentured servitude to formalities and standards - here, we have some freedom to move around and try different things. I do not think that is a short cut of the way of doing things .. but to each their own I would venture to guess.

Regards..

---

### Post by mc4man on 2014-03-06
Installing to usb external media probably should have 2 or 3 main concerns - 
1. how to properly
2. should one even bother based on hardware being used
3. In the case of using this media on a UEFI or UEFI/Secure boot machine things to consider

Seems this thread is about 1
In that vein the suggestion to remove existing drives certainly shouldn't be at the  forefront (if mentioned at all, only thing I see possibly gained will be wiped out with the first update-grub command or grub upgrade with hard drive(s) returned.

It's pretty basic as mentioned - make sure to install the bootloader to the usb device your installing to, period

scr. 1 - first look at partitioning window, for me it always picks sda by default. If left like that huge mistake (sda here is where win7 boots from

scr.2 - after setting up a new install to usb device /dev/sdc,  (partition of /dev/sdc2), notice bootloader is still set to /dev/sda

scr3 - most of  my choices for bootloader - it this case only correct one is /dev/sdc 
(SSD2go Angelbird, the device I'm installing to, not a partition on that device which aren't in screenshot, ie. sdc1, sdc2

scr4 - picked /dev/sdc as bootloader, all ready to install

Pretty simple

---

### Post by monkeybrain20122 on 2014-03-06
The clearest, most explicit tutorial 
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Note: with trivial modifications for newer Ubuntu releases
Installing in usb works but it would be painfully slow, I suggest you use an external hd instead which will give you the same speed as an internal installation. The same steps apply.

---

### Post by mc4man on 2014-03-06
> **monkeybrain20122 said:**
> 
Installing in usb works but it would be painfully slow, I suggest you use an external hd instead which will give you the same speed as an internal installation. The same steps apply.

Atm I'm of opinion that if using usb3 (full rate or not) a real external ssd drive is the only way to go. But out of curiosity I did purchase what I'd think would be the **min **quality thumbdrive  for such  - a sandisk extreme.
Should be here tomorrow, I'll try though don't think thumb drives are really suitable for constant use but could be ok for occasional use on my  laptop .

---

### Post by ventrical on 2014-03-07
> **mc4man said:**
> Atm I'm of opinion that if using usb3 (full rate or not) a real external ssd drive is the only way to go. But out of curiosity I did purchase what I'd think would be the **min **quality thumbdrive  for such  - a sandisk extreme.
Should be here tomorrow, I'll try though don't think thumb drives are really suitable for constant use but could be ok for occasional use on my  laptop .

As I said, I have been using them here for over 4 years with no corruption. These USBs are for custom work for some, not everybody.  They are good to use , for instance, on commercial machines infected with malware with  AV program installed on the USB. Can also be done with live persistent - but this topic is not about live persisitent.

 
 " i want to install 14.04 on it. not a live cd version i can do this. but  want to install a full blown verions on it. how do i proceed. there has  got to be a way just cant figure it out, tks
unetbootin just gives me a live cd. 				"

 As for GRuB, it is assumed that the end_user is aware of this and will upgrade his USB install on a dumb terminal forgoing GRuB problems - so dependencies are upon circumstances, not for all , maybe for some ... I happen to have the arsenal of hardware available. Others do not. Therefore a softer method for them .. I agree.

Regards..

---

### Post by ventrical on 2014-03-07
> **monkeybrain20122 said:**
> The clearest, most explicit tutorial 
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Note: with trivial modifications for newer Ubuntu releases
Installing in usb works but it would be painfully slow, I suggest you use an external hd instead which will give you the same speed as an internal installation. The same steps apply.

  That is a one case scenario with one commercial brand of BIOS. For instance, that will not work with a DQ35J0E or DQ965GF Intel board. (or .. err even try that on a Toshiba Satalite) That information is extremely outdated. Anyways .. the OP hasn't offered up anything else as in like specifications of his system .. etc.. so I have nothing more to add at this stage.

Regards..

---

### Post by ventrical on 2014-03-07
> **varunendra said:**
> 


Sorry, can't agree with that. There is a reason why no official guide about booting from USB even mentions the word 'hardware'.
Finding and changing BIOS options is often trivial and safe. Fiddling with cables inside a cabinet is niether trivial nor safe.


You don't "fiddle" with them. You disconnect them. And it is very safe if you take  the time to learn how to do it. But then some play it safe and I respect that.

Regards..

---

### Post by varunendra on 2014-03-07
> **ventrical said:**
> You don't "fiddle" with them. You disconnect them. And it is very safe if you take  the time to learn how to do it...

I already gave in, no protests, I swear.... :p

---

### Post by ventrical on 2014-03-07
> **varunendra said:**
> 

Sorry, can't agree with that. There is a reason why no official guide about booting from USB even mentions the word 'hardware'.


there was just this one thing here :)

[http://askubuntu.com/questions/43174/installing-ubuntu-on-external-hard-disk](http://askubuntu.com/questions/43174/installing-ubuntu-on-external-hard-disk)

---

### Post by varunendra on 2014-03-07
Thanks! I'll try to figure out how and when AU became "Official Guide" for Ubuntu.

---

### Post by mc4man on 2014-03-07
> **ventrical said:**
> You don't "fiddle" with them. You disconnect them. And it is very safe if you take  the time to learn how to do it. But then some play it safe and I respect that.

Regards..
In the case of laptops where the back must be removed to access the hd  likely not something many users will want to do

---

### Post by formerub on 2014-03-07
> **varunendra said:**
> I have seen many users who have been members since the beginning of this forum (2005), but they don't know even the basics we usually expect a regular Linux user should know. I don't see anything wrong with that. On the contrary, it proves the fact that one doesn't have to be a 'computer geek' to be able to use Ubuntu. It is as easy as any other popular OS for an average computer user.  Also, regardless of whether the OP remains active or not, I usually try to make my answers as complete and clear as possible. If the original question is clear, and so is the answer, it will be helpful to many, not just to OP.   @ventrical, most of the 'normal users' would run away as soon as you tell them that they have to open their computer case just to be sure that the OS installs properly. The 'nerdy' ways should come later, when the 'standard' ways have failed and the poster is still interested. :) I like how you use slected verbage to convey your thoughts I had already fessed up to being lazy! No need to rub my nose in twice! The Mods here in U+1 often tell users that this testing not general help. Anyway deleted my account, way to much friction dilutes the community. Best of luck Regards runrickus GO ventrical Ill check in and say hey from time to time.

---

### Post by ventrical on 2014-03-07
> **mc4man said:**
> In the case of laptops where the back must be removed to access the hd  likely not something many users will want to do


Most laptops , only one screw - but I'm done here. You're right.

Thanks and regards..

---

### Post by rburkartjo on 2014-03-09
3rdalbum  gave me the answer i was looking for. i had to first put the iso on a usb stick then plug in another stick and try to install off the first. but kept getting this error message no root file system is defined. 
here is his response
You forgot to actually tell the installer where to put Ubuntu. Select the USB stick and choose "Edit Partition". Set the mount point to / and you can continue with the installation.

Installing the system onto a USB flash drive will put unusual wear and tear on the USB. Keep a backup of your data or use a hard disk instead of a flash drive.

works great for me now at least i can run and install any linux distro on a stick without having a iso burner. i just use unnetbootin to install on one stick and then follow the above advise. note i had to use boot repair disk when done. but works like a champ.

---

