---
title: "Can I clone...."
date: 2010-12-30
forum: The Cafe
---

### Post by piquat on 2010-12-30
my windows install and then use that clone to lay it back down if ever needed AND not have to reactivate?
 
I reinstall a lot.  I think I spend more time screwing around with the way the computer operates than I do actually operating it.  Probably a common theme for many here.  I don't want to have to reactivate every time (it's OEM, I can see them balking at some point) so I'm thinking I could set it up like I like, update it, activate it and THEN clone it with something like clonezilla.
 
If it matters it's OEM Win7 Home Premium.
 
And I stuck this here because it weren't for screwing with linux, and my lack of knowledge doing it, I probably wouldn't need this precaution.
 
 
Thanks.

---

### Post by Paqman on 2010-12-30
If it's an OEM licence it's tied to that particular machine, so if you change the hardware too much then you're breaking the licence. I'm not too gripped up on Win7 but on previous versions the OS would keep an eye on the hardware and if too much changed it would require reactivation.

However, if you're not changing the hardware then I don't see why you'd have a problem. Providing an image to restore from is what the OEMs do instead of providing disks these days anyway, you're just doing something similar to that.

---

### Post by piquat on 2010-12-30
And that's exactly what I'm after.  Like you said, they lay images down on the drives anyway at the manufacturer...
 
I'm aware of the hardware changing thing.  There might be a storage drive or two added in the future but I think that's OK.  You can usually call in and explain the situation and get it reactivated if it doesn't like a hardware change, at least that's what I've heard.
 
Not looking to bootleg anything, just want to make reinstalling easier.
 
 
Thanks for the reply.):P

---

### Post by aysiu on 2010-12-30
Yes, CloneZilla will make an exact clone of your Windows installation so you can restore it without needing to reactivate it.

This is a good idea regardless of whether you're messing around with Linux or not. Backups are always a good idea.

If you're worried, though, you can set up a dual-boot with Windows using [Wubi](http://www.psychocats.net/ubuntu/wubi) to avoid replacing the Windows boot loader and to avoid repartitioning your hard drive. If you decide you don't like Ubuntu, you can uninstall it the same as you would any Windows program.

---

### Post by juancarlospaco on 2010-12-30
ReDo Live

---

### Post by 3Miro on 2010-12-30
I did something like that couple of times with Linux. I completely moved a Linux install from one HDD onto another. In the case of Linux, all you have to do is copy/paste all the files on the drives, edit fstab, reinstall grub.

Under Windows, you need to check whether or not his is legal and then use some 3d party software., but it should be doable.

---

### Post by piquat on 2010-12-30
> **aysiu said:**
> Yes, CloneZilla will make an exact clone of your Windows installation so you can restore it without needing to reactivate it.
 
 This is a good idea regardless of whether you're messing around with Linux or not. Backups are always a good idea.
 
 If you're worried, though, you can set up a dual-boot with Windows using [Wubi]("http://www.psychocats.net/ubuntu/wubi") to avoid replacing the Windows boot loader and to avoid repartitioning your hard drive. If you decide you don't like Ubuntu, you can uninstall it the same as you would any Windows program.
 
 No, I'm passed being scared of dual boot looong ago.  I've tried some version of Linux about every 2-3 years or so since 2000.  It's just always been such a struggle to get things running that I never wanted to mess up a system by playing with it.   THIS time around though, I'm really loving it!  It will definitely stay, as it is already full time on my two laptops.  Thanks for the CloneZilla confirmation, that's exactly what I was looking for.


> **juancarlospaco said:**
> ReDo Live

Ahhhhh, now THAT'S what I'm talking about.  Thanks!!!!  :p


> **3Miro said:**
> I did something like that couple of times with Linux. I completely moved a Linux install from one HDD onto another. In the case of Linux, all you have to do is copy/paste all the files on the drives, edit fstab, reinstall grub.

Under Windows, you need to check whether or not his is legal and then use some 3d party software., but it should be doable.

Nah, thanks, but I'm not moving from one drive to another.  I don't know if I'd get away with that considering it's an OEM license.  I just want to lay it down again, all "licensed up", haha, when/if I mess it up.


Thanks for the replies.  I'm going to try Redo first.  That looks kind of neat.  I'll probably try with clonezilla too.  Space is cheap, if one fails I'll have a totally different method to try...  :)


Thanks again!

---

### Post by 3Miro on 2010-12-30
> **piquat said:**
> 
Thanks for the replies.  I'm going to try Redo first.  That looks kind of neat.  I'll probably try with clonezilla too.  Space is cheap, if one fails I'll have a totally different method to try...  :)


I had to take my point one step further. You take the windows partition and put it on an external drive (or another internal one). Then later one, when things mess up, you copy it back overwriting everything. This works for Linux, I don't know if it will work for Windows. Also, it may be OK legally since you cannot use windows on an external HDD and you will return it to the original one (but again, I am not sure).

---

### Post by coffeecat on 2010-12-30
@piquat, you need to make an image. If clonezilla or ReDo live don't suit you, have a look at Macrium Reflect. I've used it, it works and it's free:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

This is the bit I like:

> Linux based Rescue CD with Network access and full GUI.                        Only 6.5MB in size!

---

### Post by sudoer541 on 2010-12-30
I use Acronis true Image Home 2010.
Its not free but it does a great job. Its fast, stable and easy to use.

---

### Post by piquat on 2011-01-12
So I thought I'd update this in case some other newb finds this and wonders what worked for me... one newb to another.  :)

I used Redo for the windows partition.  And yes, I just got done trying it out.  If you don't test the backup, it's worthless IMO.  

Not only was Redo easy to figure out, it found the network which allowed me to restore from an image stored on another Ubuntu machine on my network.  Pretty slick!  In addition to that, it didn't mess with the Ubuntu or Mint installs currently presiding on the disc.  I'm betting if I had modified the boot structure/order/added/subtracted os's it would have mangled the mbr, as looking in the restore data itself there is a blahblahblah.**mbr** flie.  Since I left everything alone I didn't have to touch a thing, same grub menu and everything.

Remastersys I like for the linux installs.  It's live, simple, familiar and useful for far more than just redoing an install.

Macrum and Clonezilla I'll have to play with on the 250G I have in the machine but not plugged in, perfect candidate for that.  It's a seagate and they all die early for me so beating the crap out of it installing won't really matter, it's doooomed in my house anyway. :P

Thanks for the help people!

---

