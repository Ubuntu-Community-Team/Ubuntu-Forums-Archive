---
title: "Why I enjoy Ubuntu?"
date: 2006-05-09
forum: Testimonials &amp; Experiences
---

### Post by harisund on 2006-05-09
There are a couple of reasons I enjoy Linux in general, and Ubuntu in particular. 

(1) The power of the command line. Enough said. 
Seriously, if you have written bash scripts that take the output of a command, pipe it into a sed edit, then use perl to manipulate it, and finally send the ouput to another command that in turns does.... you get the picture, right? 

(2) The ease of program installation. apt-get. More than enough said.
I hate using Synaptic since it's *so slow*. By the time it loads and shows me the massive listing, I could have just as well made some coffee. apt-cache search, aptitude search and dpkg --list are the best things that have happened to man kind after .. hmmm.... make install? 

(3) THE COMMUNITY. #ubuntu, #ubuntu-offtopic and [http://ubuntuforums.org](http://ubuntuforums.org). Much more than enough said. 
I have used a lot of other distros (ok not used, only tried to use) and absolutely nowhere have I seen a more friendlier gang. Testimony to that is my number of forum posts. Even though they may not be huge, you can rest assured that I am having no intention of stopping whatsoever. Did I mention the people are extremely friendly? All of my free time is spent on the IRC. I believe I have made more friends through these forums and the channels than I have in real life. 

(4) Customization. Everything is in text files. I often break my system trying out new stuff etc. I have a neat (albeit) big script that restores my machine the exact way it was before breaking it. I install Ubuntu again and I am shown with the default interface. I go to Ctrl Alt F1, execute and invoke-rc.d gdm stop, and run my script. Bam. When I reboot, everything is perfect. I have edited and backed up the following files (for example)
--/etc/gdm/gdm.conf -- include auto login with my user name
--/etc/dhcp3/dhclient.conf -- to send my machine name to the DHCP server 
--/etc/motd -- pretty obvious
--/etc/sources.list -- duh!
--/etc/xorg.conf -- you just have to change it,right? 
--/etc/fstab -- added the exec option to mount, so that binaries can be executed
--/etc/inittab -- isn't it lame to be running 6 gettys? 
--/etc/sudoers -- Username nopasswd:ALL (nopasswd) I hate passwords
--/etc/interfaces -- Static IP
--/etc/resolv.conf -- DNS information
--/etc/ssh -- I need to make sure my servers DSA/RSA keys remain the same. 

Now on a system reinstall, all I need to restore these files and the files in my $HOME directory, and I am back, productivity and all. 

Actually, you can do something similar with the Windows registry and write a .reg file that automatically manages and edits the registry keys. But come on, what are you trying to compare that with? 

(5) Geek factor. This might not help you in getting laid, but when someone walks by and sees something on your laptop, and goes "Hmmm... I didn't know you can do that to your computer" and I say "hahaha.. you have no ideas of my world domination." 
Have you tried compiling your Windows kernel, anyway? How much more geek factor do you really want? 

For some reason, most people seem to think doing anything on the command line is geeky. If I am really feeling bored, I will fire up my laptop, and do something like compiling Firefox or some such big software. As we all know, doing a ./configure itself lists out sooo many lines. So I just let it run and my geekiness factor jumps up by something like a 1000 points :)

(6) Power. Raw power over your machine. Your computer the way you want it. Your kernel the way you want it. Your hardware the way you want it. Can you do either of 'xset dpms force off' or 'hdparm -Y /dev/hda' to immediately put it to sleep on any other operating system? 

(7) You learn something new everyday. Fire up a terminal and hit tab key twice. Assuming you are running Bash with file name tab completion turned on, my terminal says "Display all 2336 possibilities?" Wow. How much does your terminal say?  I have made it a point to learn atleast one new command weekly. And by learn, I mean *learn* with all, or atleast as much as practically possible, switches. I didn't know grep -v existed! What a fool ... 

(8) Remote access. If you even attempt to compare Remote Desktop with SSH, you need to hang your head in shame. X does it so much better. 

(9) oh and did I mention command line?

---

### Post by Thoop on 2006-05-09
I can just say one thing: You're damn right!

---

### Post by johnc4510 on 2006-05-09
Well said, the only other things I might list are:security, savings, and not having to pay Billy Gates.

---

### Post by dralaroc on 2006-05-09
[QUOTE=harisund]There are a couple of reasons I enjoy Linux in general, and Ubuntu in particular. 

--/etc/inittab -- isn't it lame to be running 6 gettys? 

Should gettys 2 thru 6 be # out or deleted?  This /etc/inittab is a new one to me.  I agree with ya also, I  am spending crazy hours on my Dapper machine.  My wife calls my computer my mistress...I don't know if thats a good or bad thing :mrgreen:

---

### Post by harisund on 2006-05-09
Thoop: Thanks for your feedback. 

johnc4510, thanks for yours too. Somehow, the security option never crossed my mind. I guess the whole "no spyware malware adware" thing is so overblown that I considered it for granted. 
Savings, yes of course. Why didn't that come to my mind? 

I guess I was trying to list reasons that are not often repeated. 

dralaroc, I always comment them out. In fact any customization I do, it's always commenting out unwanted stuff and/or adding new stuff. This way I know I can always go back too. 

Yeah, I am addicted to my machine too. Good thing I live alone :)

---

### Post by dralaroc on 2006-05-09
Thanks man!! That post was packed with some good info...well for a rookie anyway.  Most of that stuff is greek to me ](*,)

---

