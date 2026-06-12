---
title: "ubuntu studio"
date: 2009-01-31
forum: System76 Support
---

### Post by bbrace on 2009-01-31
Has anyone else had experience installing/running Ubuntu Studio on Pangolin laptops? Problems?
Does installing it replace all of the regular Ubuntu applications?

thanks  /:brad

---

### Post by thomasaaron on 2009-02-01
There were at least two responses on this thread. Not sure where they went!

---

### Post by MorphWVUtuba on 2009-02-01
ACK!  Yes there were.  If I go to this thread from my User CP, they're all still there:

```

Old 2 Days Ago 	  #2
thomasaaron
Iced Blended Vanilla Crème Ubuntu
 
thomasaaron's Avatar
 
Join Date: Sep 2006
Posts: 2,809
	
Re: installing ubuntu studio on pangolin system76 laptop
I spoke to this gentleman on the phone and explained to him that we do not install Ubuntu Studio.

Are there any 76ers out there who have given Studio a spin? If so, what is involved with getting it up and running?

Also, we image with a separate home partition that can be shrunk to create a new partition for Studio. I can walk you through that process when you're ready. It's very simple.
__________________
HELP ME HELP YOU:
1. What version of Ubuntu are you using? (Ubuntu, Kbuntu, Xubuntu | 32-bit, 64-bit)
2. What is your System 76 Model Number?
3. What have you already tried?
thomasaaron is offline Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message
thomasaaron
View Public Profile
Send a private message to thomasaaron
Find More Posts by thomasaaron
Add thomasaaron to Your Contacts
Old 2 Days Ago 	  #3
MorphWVUtuba
A Carafe of Ubuntu
 
MorphWVUtuba's Avatar
 
Join Date: Apr 2006
Location: Fairmont, WV
Posts: 85
Send a message via AIM to MorphWVUtuba
	
Re: installing ubuntu studio on pangolin system76 laptop
I've never had ANY trouble with adding UbuntuStudio on ANY Ubuntu machine, S76 or otherwise. I think all the way back to the previous LTS 6.06, it's been included in the official Ubuntu repos.

SO. On to the steak & taters:

Code:

sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

( Pulled from https://help.ubuntu.com/community/Ub...adingFromHardy )

If you don't want something, like the video apps, just remove "ubuntustudio-video" from the command.

The linux-rt loads the low-latency, real-time kernel to your computer. This allows for better performance in audio/video capturing/processing.

You have to reboot & select this at the GRUB menu to utilize, and you may want to change the amount of time GRUB is displayed. Since my machine is a dual-boot with Windows, I have "timeout 60" to give me a minute to change the option. Change it to whatever # of seconds you wish, but I have a tendency to wander off & miss it before it boots into whatever the default option is. Anywayz...

THAT. IS. IT.

ENJOY!!!
MorphWVUtuba is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
MorphWVUtuba
View Public Profile
Send a private message to MorphWVUtuba
Send email to MorphWVUtuba
Find More Posts by MorphWVUtuba
Add MorphWVUtuba to Your Contacts
Old 2 Days Ago 	  #4
bbrace
First Cup of Ubuntu
 
Join Date: Jan 2009
Posts: 5
	
Re: installing ubuntu studio on pangolin system76 laptop
ok thanks; it may be possible to install but...
do all the ubuntu studio applications function correctly?

/:b


Quote:
Originally Posted by MorphWVUtuba View Post
I've never had ANY trouble with adding UbuntuStudio on ANY Ubuntu machine, S76 or otherwise. I think all the way back to the previous LTS 6.06, it's been included in the official Ubuntu repos.

SO. On to the steak & taters:

Code:

sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

( Pulled from https://help.ubuntu.com/community/Ub...adingFromHardy )

If you don't want something, like the video apps, just remove "ubuntustudio-video" from the command.

The linux-rt loads the low-latency, real-time kernel to your computer. This allows for better performance in audio/video capturing/processing.

You have to reboot & select this at the GRUB menu to utilize, and you may want to change the amount of time GRUB is displayed. Since my machine is a dual-boot with Windows, I have "timeout 60" to give me a minute to change the option. Change it to whatever # of seconds you wish, but I have a tendency to wander off & miss it before it boots into whatever the default option is. Anywayz...

THAT. IS. IT.

ENJOY!!!
bbrace is offline Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message
bbrace
View Public Profile
Send a private message to bbrace
Find More Posts by bbrace
Add bbrace to Your Contacts
Old 1 Day Ago 	  #5
MorphWVUtuba
A Carafe of Ubuntu
 
MorphWVUtuba's Avatar
 
Join Date: Apr 2006
Location: Fairmont, WV
Posts: 85
Send a message via AIM to MorphWVUtuba
	
Re: installing ubuntu studio on pangolin system76 laptop
I haven't used the JACK applications, because I'm too much of a n00b to know how to set it up. But I do know everything else works. I think at one time the rt kernel didn't allow me to connect to wireless, but if I remember correctly that's not the case anymore.

<strike>Have you purchased a machine already or is this just part of your evaluation? Cuz if you've got one, you could always try a livecd.</strike> If there's something specific you'd like to know about, I'd be happy to test it for you on my Serval Pro.
Last edited by MorphWVUtuba; 1 Day Ago at 11:55 AM.. Reason: sorry, I guess it helps to read the original post
MorphWVUtuba is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
MorphWVUtuba
View Public Profile
Send a private message to MorphWVUtuba
Send email to MorphWVUtuba
Find More Posts by MorphWVUtuba
Add MorphWVUtuba to Your Contacts
Old 1 Day Ago 	  #6
bbrace
First Cup of Ubuntu
 
Join Date: Jan 2009
Posts: 5
	
Re: installing ubuntu studio on pangolin system76 laptop
Quote:
Originally Posted by MorphWVUtuba View Post
I haven't used the JACK applications, because I'm too much of a n00b to know how to set it up. But I do know everything else works. I think at one time the rt kernel didn't allow me to connect to wireless, but if I remember correctly that's not the case anymore.

<strike>Have you purchased a machine already or is this just part of your evaluation? Cuz if you've got one, you could always try a livecd.</strike> If there's something specific you'd like to know about, I'd be happy to test it for you on my Serval Pro.
thanks very much! this is reassuring
I'm ready to buy the Pangolin -- hopefully it will behave like your Serval
does installing studio replace all of ubuntu?
(would it make sense to keep both on partions?)

/:brad
bbrace is offline Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message
bbrace
View Public Profile
Send a private message to bbrace
Find More Posts by bbrace
Add bbrace to Your Contacts
Old 1 Day Ago 	  #7
MorphWVUtuba
A Carafe of Ubuntu
 
MorphWVUtuba's Avatar
 
Join Date: Apr 2006
Location: Fairmont, WV
Posts: 85
Send a message via AIM to MorphWVUtuba
	
Re: installing ubuntu studio on pangolin system76 laptop
Quote:
Originally Posted by bbrace View Post
thanks very much! this is reassuring
I'm ready to buy the Pangolin -- hopefully it will behave like your Serval
does installing studio replace all of ubuntu?
(would it make sense to keep both on partions?)

/:brad
This is what I love about package managers in Linux & Ubuntu specifically. You can install this on a separate partition using a livecd, replace the default ubuntu desktop, or just pick & choose which elements you want from synaptic!

I just have the audio & video packages installed, (see screenshot). I did install the graphics applications, but I removed all mono-based apps to keep at least my Ubuntu partition ms-free.
Attached Thumbnails
Click image for larger version Name: ubuntustudio_synaptic_search.png Views: 4 Size: 98.6 KB ID: 101705  
MorphWVUtuba is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
MorphWVUtuba
View Public Profile
Send a private message to MorphWVUtuba
Send email to MorphWVUtuba
Find More Posts by MorphWVUtuba
Add MorphWVUtuba to Your Contacts
New Reply 
```

---

### Post by darkknight045 on 2009-02-02
I believe a moderator moved the responses to another thread.

[Found here.]("http://ubuntuforums.org/showthread.php?t=1055121")

---

### Post by thomasaaron on 2009-02-02
An honest mistake. But it does pertain to System76 in this instance.

---

