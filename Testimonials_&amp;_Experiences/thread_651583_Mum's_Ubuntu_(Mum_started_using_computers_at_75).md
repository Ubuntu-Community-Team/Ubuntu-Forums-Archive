---
title: "Mum's Ubuntu (Mum started using computers at 75)"
date: 2007-12-27
forum: Testimonials &amp; Experiences
---

### Post by TimGS on 2007-12-27
In summer, prior to entering the Ubuntu world, I set up my 75yr old Mum's then new PC  - which came with Windows Vista. It is a 512MB machine, but I was encouraged by the number of apparently independent claims on the net that Vista works fine with 512MB :roll: 

It ought to have been incredibly high spec for my Mum's requirements but it (then) appeared the cheapest way of getting a large screen as her eyesight isn't the best. I didn't get a secondhand machine plus brand new large monitor as I then took the point of view that it would be unreliable and it's probable Windows installation would be old, slow (mainly due to Windows programs arguing with each other), and possibly not up to running up to date software. As tech support (me) doesn't live close by this had to work well and be reliable.

Vista was slow, took ages to boot, and required Zone Alarm and AVG. This mean't frequent phone calls were received at Tech Support (me) asking what she should do because something called AVG was asking for updates or Zone Alarm was asking her to allow or disallow a quite incomprehensible (to her) program name. Then there is the Vista 'feature' that checks if you really want to run such-and-such a program.Then Windows started falling out with (from what I could tell over the phone) the NVIDIA graphics card. Then Windows said it was completely broken and needed fixing. Occassionally the computer would switch itself off half way through boot up, presumably having decided enough was enough. By mid December it was 'taking an hour' to get as far as checking email. ](*,)

Christmas is of course the time for visiting family. Also, enter Ubuntu which I had installed on my own machine in October. Time to switch Mum to Ubuntu. :idea:

There were some problems to be fair. The Live CD froze twice - once after having (successfully) shrunk the Vista partition and once during linux installation (at some point after ext3 formatting but before the GRUB installation) 

There are problems with Power management - I had to set this to 'Never' because otherwise the computer went to sleep but wouldn't wake up to the power button - had to pull the plug! Similarly the 'sleep' key on the keyboard puts the computer to sleep - but it refuses to wake up again. Presumably these two problems are down to the same thing. 
There were problems with multiple users logged on - occasionally computer would crash while logging one user out or switching users with a blank white screen display. Not a big deal though normally in this situation. I only found it as I oscillated between my own admin session and 'Mum's' session.

Irritatingly I found that users must be able to 'use scanners' (Admin -> Users and Groups) to access the HP Deskjet D2360 with HPLIP. I'd only allowed what appeared necessary on my Mum's account and as she didn't have a scanner I didn't initially tick that box.

Flash installation was problematical as documented elsewhere. Installing the tar.gz package from my own administrator ID did not result in Epiphany or Firefox on my Mum's ID recognising its presence. Temporarily making my Mum administrator and using sudo apt-get to purge the initial installation and then re-install did work. 

[Please please please make non-free features (Flash, DVD playing....) more easily accessible. I am a techie person - I can deal with it and will keep trying various suggested solutions that can be found on the forums and know that in the end it will be worthwhile as linux I feel is a more robust system - but others will not or cannot and may not see the point in persevering with Ubuntu. Please please please improve on this (I say this because I don't want to spend life living in a Windows dominated desktop world).]

I set it up so she has access to only the features she uses, and I got rid as much as possible of menu items that would not be used. The only applications now that she can get to are Epiphany, Google Earth, and Abiword. Preferences only gives Access to HPLIP. Auto login is enabled and Epiphany starts up automatically and logs in to her gmail account without asking for a password.

My mum now has a system which won't pop up confusing dialogue boxes that she doesn't understand. It boots quickly and is quite responsive. It doesn't argue with the hardware and doesn't tell her she needs to fix it. It would also be quite difficult (touch wood) for her to mess up any settings as I've been able to block access to them.

British Telecom will get less revenue now, but I now will have a quiter and easier life. Thank you Ubuntu developers everywhere. =D>

-- Tim.

---

### Post by zero244 on 2007-12-28
She will be far better off using Ubuntu on the specs of her computer. Im surprised they even sent the computer onto the shelves with so little ram. Ive noticed lately most computers who ship with Vista start out with 2gigs of ram.
I have a feeling that even MS realizes that Vista is overpriced junk.
When they finally have to admit it.........thats when you see Balmer take a hike.
I bet your mum likes Ubuntu better too.
Good luck.

---

### Post by Bungo Pony on 2007-12-29
My 512M RAM PC also shipped with Vista. It was also slow as hell. But I knew when I got it I'd be wiping it and dual-booting Win2k and Ubuntu.

Sounds like you may have had a few problems due to how new the PC is. That's what my problem was when I initially tried to install Ubuntu. Now that the developers have caught up with my hardware, it runs a lot better than it did last year.

---

