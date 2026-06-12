---
title: "Just Got My Nokia N810"
date: 2008-10-16
forum: The Cafe
---

### Post by bigbrovar on 2008-10-16
Actually i would be getting the it in less than 6 hours time . although i have been running ubuntu linux as my primary OS for more than a year. This would be my first experience with the Internet Tablet and i would appreciate those of you who have been using it can give me tips on some the best and stable 3rd party application to install. and also some few beta must have applications. here are some of the things i look forward to be able to do on the IT
Blog,Twit,Word processing,ssh,media,podcast,chat,IRC, etc
 while i would prefer a smooth install i am however not afraid to get my hands dirty hacking,cli stuff and hunting down dependencies if the situation warrants.

Also would like to know if its possible to flash/upgrade the IT's firmware on an Ubuntu desktop or do i need windows to do that?

---

### Post by kavon89 on 2008-10-16
I got mine this week. Here is how you flash the firmware to the latest:

[http://wiki.maemo.org/Updating_the_tablet_firmware](http://wiki.maemo.org/Updating_the_tablet_firmware)

Must have 3rd party apps: Pidgin, Numpty Physics (fun game), Xournal, openssh, easyroot (or one of the other packages that allows you to become root, i think i use easyroot and have sucess with it), I use the default media player for my music library... otherwise i'd use canola2, it has an excellent interface but it doesn't seem to support .m4a so I'm stuck with the default (which is not bad actually).

Also, make sure you get a MiniSD, not MicroSD (unless u find an adapter) to put music/movies/whatever on there. 

Oh and another thing, I would recommend converting 128MB of the internal memory card's memory into virtual memory, allows you to multi task more etc.

EDIT: also, you can't run ubuntu on it because it has an ARM processor, not the common x86 type ubuntu is primarily used for. Ubuntu MID edition supposedly will have an ARM version AFAIK.

---

### Post by DemonBob on 2008-10-16
I want one, but i'm waiting, the next series is suppose to have 3g. 


Right now it's a toss up between waiting or getting the Gigabyte m528 which is going to have 3g also.

---

### Post by bigbrovar on 2008-10-16
> 
Also, make sure you get a MiniSD, not MicroSD (unless u find an adapter) to put music/movies/whatever on there. 


Gee thanks .. i ordered an 8GB microsd card which would be delivered with the Nokia but am not sure the card would come with a minisd adapter (which shouldn't be hard to get anyway) 

> Oh and another thing, I would recommend converting 128MB of the internal memory card's memory into virtual memory, allows you to multi task more etc.



how should i do that .. is it supported if yes then i guess i would figure it out .. if i would have to hack then i would appreciate if you can give me pointers

---

### Post by Mr. Picklesworth on 2008-10-16
No need for easyroot. Install sudser (in extras repository) and the already existing sudo command will behave just like in Ubuntu. becomeroot is evil :P

As for Mini vs. Micro SD, I highly recommend you go with the adapter. MiniSD cards are tricky to find, and as I understand it Micro and Mini are identical in specs other than size. (Except MicroSD is reasonably inexpensive thanks to being very popular). With a MicroSD, you can get an adapter from that to practically anything else. Quite handy with those free digital cameras that always seem to take different card formats ;)

Must-have apps:
I am in love with Canola 2. It is the greatest media player on the face of the Earth. It is superior to all the ones on the desktop, too, which is why I am really excited for their final release which (don't quote me on this) will be open source and hopefully see a Linux desktop port in short order. The thing is fast, feature-packed and *slick*.

ScummVM. Get that and the Monkey Island games. Monkey Island 3 is particularly awesome on the tablet, although don't play that unless you've played the first two. I have the good fortune of having discovered Monkey Island 1 and 2 on my DS, playing them (and the similarly awesome talkie version of Rise Of The Tentacle) with the homebrew port of ScummVM... then the N810 came along, perfectly suited to Monkey Island 3. Don't know what I'll do with #4 except hope it's irrelevant.

FreeCiv. I believe a recent package of the SDL version is available in the extras (or at least extras-devel) repository. Runs quite nicely.

If you find you want Java or any of Debian's incredibly huge catalogue of software (and don't mind whether it fits in the tablet's own desktop environment), there is something called EasyDebian Chroot. I have a Debian install aboard a 1.5 GB partition on my (also 8 GB) MicroSD card. I can run Debian apps within the N810's Hildon environment, or launch an entire desktop session with its own window manager and all that jazz. Very cool.

The tablet doesn't have any PIM software by default (although I for one kind of like the contacts app, regardless of its lack of location information), but you can install Pimlico which is really quite well optimized for the thing. Alas, it is super painful to get it to synchronize with Evolution on a desktop right now, but hopefully in the future we'll have Pimlico sync or Conduit actually working well on the tablet.

For your Ubuntu desktop, download tablet-encode. You can just run the program from your home directory. It simplifies encoding videos to play well on the thing, since the device doesn't have a great video processor. (Which really hurts, because we actually have the same video chipset as the iPhone; just can't use it because of evil license restrictions from PowerVR. "Why hardware manufacturers are evil" reason of the day).
Err, anyway, tablet-encode is pretty nice. Run it like so from the terminal:
./tablet-encode --preset=best /my/video/1 /my/video/2 /my/video/3 /my/video/4 /videos/encoded/for/tablet/directory
(Or you can do one video at a time, with the first argument being your original video and the second argument being what you wish to save it as).
Tip of the day: Drag and drop files onto the terminal and their full path is automatically entered so you needn't spend all day typing. Indeed, you can select and drag / drop a group of files, too! :)

---

### Post by kavon89 on 2008-10-16
> **bigbrovar said:**
> how should i do that .. is it supported if yes then i guess i would figure it out .. if i would have to hack then i would appreciate if you can give me pointers

It's very easy, go to the control panel, choose Memory. Then goto Virtual, and then it gives you an option to use up to 128MB as virtual memory.

> **Mr. Picklesworth said:**
> No need for easyroot. Install sudser (in extras repository) and the already existing sudo command will behave just like in Ubuntu.

As for Mini vs. Micro SD, I highly recommend you go with the adapter. MiniSD cards are tricky to find, and as I understand it Micro and Mini are identical in specs other than size. (Except MicroSD is reasonably inexpensive thanks to being very popular). With a MicroSD, you can get an adapter from that to practically anything else. Quite handy with those free digital cameras that always seem to take different card formats ;)

I had trouble getting sudser to work for some reason. I found my 4GB MiniSD card on Amazon for 8 bucks, 6 dollar shipping.

I don't understand why my AdblockPlus plugin for the browser is ineffective, anyone else have trouble with it?

---

### Post by bigbrovar on 2008-10-16
> Mr. Picklesworth  	
Re: Just Got My Nokia N810
No need for easyroot. Install sudser (in extras repository) and the already existing sudo command will behave just like in Ubuntu.

As for Mini vs. Micro SD, I highly recommend you go with the adapter. MiniSD cards are tricky to find, and as I understand it Micro and Mini are identical in specs other than size. (Except MicroSD is reasonably inexpensive thanks to being very popular). With a MicroSD, you can get an adapter from that to practically anything else. Quite handy with those free digital cameras that always seem to take different card formats 
thanks i ordered it with an 8gb MicroSD. but am not sure if the package comes with a MiniSD adapter .. but i guess we would find out in 5 hours time.

---

### Post by bigbrovar on 2008-10-18
i tried download the latest firmware image using this link [http://tablets-dev.nokia.com/nokia_N810.php](http://tablets-dev.nokia.com/nokia_N810.php) but my internet is very slow and unsatble. it would take like 2:30 min for me to be able to download the image using my current connection which breaks a lot. and when it breaks i would have to restart the download. on 5 occasions i was at 90% before it failed. does anybody have the  the latest diablo image for linux ? can you help me upload it to an upload site that support resume download like mediafire or sendspace ? i would really appreciate if you can do this for me thanks.

---

### Post by bigbrovar on 2008-10-18
bump ! :(

---

### Post by raul_ on 2009-01-14
Hello!

Since you have a N810, could you upload the default wallpaper (Echo), please? I've been googling like crazy for it, and can't download it from anywhere!

---

### Post by Onyros on 2009-01-14
> **raul_ said:**
> Hello!

Since you have a N810, could you upload the default wallpaper (Echo), please? I've been googling like crazy for it, and can't download it from anywhere!Toma lá, Raul... não quero te falte nada :P

---

### Post by raul_ on 2009-01-14
> **Onyros said:**
> Toma lá, Raul... não quero te falte nada :P

LOL

Muito obrigado ;) 

(Thank you very much)

---

### Post by Mr. Picklesworth on 2009-01-14
Oh, while we're in N810 mode, I feel I should point people to this:
[http://www.internettablettalk.com/forums/showthread.php?t=25752](http://www.internettablettalk.com/forums/showthread.php?t=25752)

Tear is also a nice browser:
[http://www.internettablettalk.com/forums/showthread.php?t=24293](http://www.internettablettalk.com/forums/showthread.php?t=24293)

Both completely blow the default browser out of the water. They are using webkit, so are extremely fast and have EXCELLENT javascript performance. Embarassingly slow time to open the locally stored home page no more!
I'm using the former since it replaces the default browser smoothly, and it pretty much beats the iPhone browser by a few magnitudes.

---

### Post by raul_ on 2009-01-14
Oh, too bad that I can't convert it to svg :( I was eager to use it as my wallpaper. As is, I can't resize it without aliasing.

Does anyone have a 1200x800 version of that image, by any chance?

---

### Post by init1 on 2009-01-14
My Archos 5 came yesterday, it's a great device. I considered getting an n800, but I wanted a big hard drive.

---

### Post by xenoalien on 2009-01-14
What operating system do these devices use? What is it called?

---

### Post by raul_ on 2009-01-14
> **xenoalien said:**
> What operating system do these devices use? What is it called?

Maemo or OS2008 (It's the same thing)

---

### Post by wipeout140 on 2009-01-14
nokia n810 OS is based off debian aswell

---

