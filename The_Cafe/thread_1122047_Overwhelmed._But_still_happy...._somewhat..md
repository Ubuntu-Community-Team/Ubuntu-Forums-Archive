---
title: "Overwhelmed. But still happy.... somewhat."
date: 2009-04-10
forum: The Cafe
---

### Post by tabarnackle on 2009-04-10
So i knew that linux was hard. 
But of course, anything has to run better then Vista, even if the learning curve and troubleshooting is university scholared hard.
Im not going to give up yet. However.....

below is a short list of the things i dont know how to use with ubuntu....
Number one is the SD Card reader... weather it has to be mounted or whatever I DONT KNOW, but i do know, its plugged in, and i dont know a single way to open it, out of what are possibbly thousands.... whatever. 

the second disheartening fact, is the fact that i dont understand how to get xp installed in virtual box. i give up to hell with it.

I have enough music to listen to on my zune from before, and the usb cable still charges it through ubuntu, however i cant "see" it anywhere. no biggie, long as it charges.

those are just a few things i could keep going but i wont, oh, the webcam doesnt work either. not that id have a clue on how to make it work anyway.

id really like to figure out how to upload images off my card into a file somewhere tho.... not that id know where that file should be located.
screw ubuntu.... im stuck with you now
thats better. thanks to anyone who has tried helping me out so far i learned a thing or mabye two that i wont forget.... but the rest is just so damn daunting even when you try and do a google search i just dont know how to word anything to get the right answer.... im thinking of buying the pocketguide once i get landed in ontario being as this is going to be only pastime all summer. ill probley learn it in that time too but my problem, being a windows kid, is being....microsofted. i just expect everything to be easy and i at the same time expect my computer to remain functional. i understand the tradeoff as far as linux systems go, it dont work if you dont let it. but you letting it is harder than youd think.... anyway. i suppose thats a good enough read to call a post.
-dumbfounded dave

---

### Post by Icehuck on 2009-04-10
> **tabarnackle said:**
> So i knew that linux was hard. 
But of course, anything has to run better then Vista, even if the learning curve and troubleshooting is university scholared hard.
Im not going to give up yet. However.....

below is a short list of the things i dont know how to use with ubuntu....
Number one is the SD Card reader... weather it has to be mounted or whatever I DONT KNOW, but i do know, its plugged in, and i dont know a single way to open it, out of what are possibbly thousands.... whatever. 

the second disheartening fact, is the fact that i dont understand how to get xp installed in virtual box. i give up to hell with it.

I have enough music to listen to on my zune from before, and the usb cable still charges it through ubuntu, however i cant "see" it anywhere. no biggie, long as it charges.

those are just a few things i could keep going but i wont, oh, the webcam doesnt work either. not that id have a clue on how to make it work anyway.

id really like to figure out how to upload images off my card into a file somewhere tho.... not that id know where that file should be located.
screw ubuntu.... im stuck with you now
thats better. thanks to anyone who has tried helping me out so far i learned a thing or mabye two that i wont forget.... but the rest is just so damn daunting even when you try and do a google search i just dont know how to word anything to get the right answer.... im thinking of buying the pocketguide once i get landed in ontario being as this is going to be only pastime all summer. ill probley learn it in that time too but my problem, being a windows kid, is being....microsofted. i just expect everything to be easy and i at the same time expect my computer to remain functional. i understand the tradeoff as far as linux systems go, it dont work if you dont let it. but you letting it is harder than youd think.... anyway. i suppose thats a good enough read to call a post.
-dumbfounded dave

When you are doing google searches, simply do something like "Mounting SD Card in Ubuntu".  Just type in what you are trying to do and Google takes care of the rest. It's the same thing you would do if you were trying to troubleshoot Windows issues.

Since you just switched its just going to take some time getting used to doing things a different way. Once you do get used to it you will be able to switch between Windows and Linux with no problems.

---

### Post by wolfen69 on 2009-04-10
download the manual for virtualbox. it's pretty easy actually.

---

### Post by Sealbhach on 2009-04-10
You might want to look up Virtualbox tutorials in Youtube - it might help. 

This sort of thing:

[http://www.youtube.com/watch?v=ch8X86R6d-g](http://www.youtube.com/watch?v=ch8X86R6d-g)

Also, the PDF manual from the Virtualbox site is nice and clear:

[http://download.virtualbox.org/virtualbox/2.2.0/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.2.0/UserManual.pdf)

Sometime when you're feeling more relaxed have another go at it. You'll get it sorted out eventually, it's not too bad. 

EDIT: make sure you install Virtualbox Guest Additions...



.

---

### Post by blastus on 2009-04-10
> **tabarnackle]So i knew that linux was hard.
But of course, anything has to run better then Vista, even if the learning curve and troubleshooting is university scholared hard.
Im not going to give up yet. However.....[/quote]

Determination pays off ):P 

In my case I only had dialup at the time and had to go through a lot of hoops to get my modem to work in Linux. But I pieced together the puzzle and got it working and it turned out not to be that difficult at all. I also had trouble when I got an LCD as I couldn't get it to run at its native resolution. But that didn't work in Windows either, and within a few days I got it working in Linux (I had to create my own X.Org ModeLine for that.) But I don't have to mess with that stuff anymore.  said:**
> below is a short list of the things i dont know how to use with ubuntu....
Number one is the SD Card reader... weather it has to be mounted or whatever I DONT KNOW, but i do know, its plugged in, and i dont know a single way to open it, out of what are possibbly thousands.... whatever.

I'm not sure about Ubuntu 8.10, but I have a laptop with Ubuntu 9.04 Beta and the CD Card Reader works. It's used just like a CD/DVD drive or USB key. 

[quote=tabarnackle]the second disheartening fact, is the fact that i dont understand how to get xp installed in virtual box. i give up to hell with it.[/quote]

To start make an ISO image of your Windows XP CD. You don't have to make an ISO image but it will enable you to install Windows XP much faster and you don't need the Windows XP CD. You can also use a Windows program called nLite to *slipstream* Windows XP and create a really lean ISO image that installs unattended and in less than 8 minutes. I've got my ISO image of Windows XP SP3 down to 180MB. To make an ISO image, put the Windows XP CD in the drive, then right-click on it on the desktop and select "Unmount" Then enter a command like this...

```
dd if=/dev/cdrom of=~/image.iso
```

...it will read your entire CD and create an ISO image from it called image.iso in your home directory. You can use that ISO image in Virtual Box by mounting the image file. All you have to do is create a virtual machine in Virtual Box and tell Virtual Box to mount the image file. Then when you start the VM you'll notice that it boots to the Windows XP installer. From there you can install Windows XP as you normally would except that it's running inside your VM. 

Spend some time and play around with Virtual Box, it's easy to use and quite fun also.

---

### Post by swoll1980 on 2009-04-10
You'll figure everything out soon enough. None of this stuff is hard, you just have to learn how, and you'll be fine.

---

