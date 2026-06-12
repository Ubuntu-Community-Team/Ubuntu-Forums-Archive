---
title: "Ubuntu newbie (well, getting there)"
date: 2005-11-11
forum: The Cafe
---

### Post by Bartender on 2005-11-11
Good day -
I'm awaiting the promised 5 CD's, and trying to do a little pre-planning.  I get the impression that I'll need to be able to get online for assorted updates.  I'm using an older version of Juno (Juno 5).  Juno 5 uses proprietary software to get e-mail, and that software only works with Windows.  When going to the web, Juno only communicates with IE.  I don't think (it would be great if someone tells me I'm wrong!) that a Linux box will be able to connect at our house.

So, today's question is, can I use a Windows machine and a USB flash drive to bring data over to the Linux machine?

I can get ahold of surplus Pentium III 500 to 600 MHz computers.  Not sure of the RAM - 256 minimum, sometimes 512.  As you know, PC100/133 memory is ridiculously expensive compared to 184-pin DDR, so I need to know if Linux benefits greatly from having at least 512.  It's just not cost-effective to buy OEM copies of Windows for these old machines, but it'd be great to give them a new lease on life by installing Linux.

---

### Post by Kyral on 2005-11-11
As with everything, more RAM will increase performance. HOWEVER Linux has been known to run very well with 256 MB RAM

---

### Post by cstudent on 2005-11-11
I don't know if it would be practical to try transferrring program updates via a flash drive. You would have to download the .deb files and any dependencies. Is this Windows machine in the same house? Is so, you should be able to network the Windows and Ubuntu machines together and share the internet connection through the Windows machine. 


Bill

---

### Post by Bartender on 2005-11-11
Ooooh, network them together; I never thought of that.  Yeah, they would be in close proximity.  My present Windows box is a home-built machine running W2K.  I've never tried networking two Windows machines together, much less two computers speaking different languages.  
Wow, too many questions come to mind to even start asking.  You guys know any place on the web that lines out what I'd need to do?  

I've got another question for you...what are people doing with their digital cameras?  I don't imagine that Canon or Olympus or anyone else includes software that runs on Linux.  I understand that Linux has a viewer built into it somewhere, but what about some basic editing or manipulation or slideshows?

---

### Post by Pathogenix on 2005-11-11
Gimp will do editing, I think it's installed by default : applications > graphics > gimp image editor.

Slideshows I couldn't speak for.

Networking Windows machines is a piece of cake, you'll want Samba. There should be plenty of info on the forums, but I've subscribed to this thread, so post back if you get any major problems.

I use the Samba client on a laptop downstairs and the Samba server on the desktop upstairs. The nice thing is that it doesn't matter whether the (dual-boot) desktop is running XP or Linux, I can access my files in exactly the same way.

I don't know how internet connection sharing works, but again, I'm sure there is info on the forums, let me know how you get on, because I'm always willing to learn a new trick.

---

### Post by majikstreet on 2005-11-11
Since you seem to be on dial-up, I don't think that networking will be really practical. You could network them, but espically with wireless, the speed slows down. (Just my $0.02- probably not worth even that much)

The other topic, RAM, I can speak for. I used to have 256mb RAM. I quit using gnome because of the slowness. Just a thought.... I started XFCE, then went to fluxbox. Never went back.... Now, I have 512mb RAM, and I was away from gnome so long that I can't get used to it again, but it's not as slow..... Still on fluxbox.

Good luck,
majikstreet

---

### Post by cstudent on 2005-11-11
I shared a dial-up internet connection for quite a while with two Window machines networked together before I finally got DSL. One machine had XP and the other 98. Setting up internet connection sharing was pretty simple, just make a new network connection and run a wizard to walk you through it. The final step would make a floppy that you put on the 98 machine to get it connected. I also used those 3com phone line pci network cards because neither computer had a ethernet card and I could use the existing phone lines in the house to wire my machines together. It worked great. It won't be fast, but it should work. I'm not sure of the procedure to activate ICS on Win2k. I have a couple of machines at work I could try to see if I could figure it out on, but searching the MS knowledge base should surely give you some info on that. I now have 5 machines networked at home. 2 XP, 2 Ubuntu and 1 wireless dual booting both. Samba would be necessary on the Ubuntu machines for Windows to access Ubuntu files, but I don't think you would need it for the ICS. I'm not positive, but I would think that the Ubuntu machine should find it's way outside.


Bill

---

### Post by xequence on 2005-11-11
I have 192 MB RAM and gone runs fine, unless I open firefox, azureus, or limewire. Its slow then. You will probably get a great increase of performance from 512 MB over 256. Linux tends to use RAM very well and will use some of the unused RAM to make your system go extra fast.

I switch around WMs alot, and I am currently liking blackbox.

---

