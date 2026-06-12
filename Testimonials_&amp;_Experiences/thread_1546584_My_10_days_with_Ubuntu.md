---
title: "My 10 days with Ubuntu"
date: 2010-08-05
forum: Testimonials &amp; Experiences
---

### Post by Cycledoc on 2010-08-05
I'm a reasonable bright 69 year old, with moderate at best computer skills.

I spent the last week or so trying to use Ubuntu 10.04 on my old Dell Inspiron 2650 laptop (Pentium 4 Mobile 1.7Gh 512 Ram).  It had Home XP on it so I checked the various permutations of Ubuntu and decided to download the WUBI version which theoretically operated within the XP environs.  Simple?  No!

I am recalling this after the fact and grant that some of events may not be in order, but I can assure you that the problems did occur.

On first booting all went well until I was asked to type in the password and found that the keyboard didn’t work.  I used the on-screen keyboard to sign in.  The keyboard still didn’t work but somehow during the session I clicked OK once to many times and some update, I think of the grub loader, occurred.

On rebooting I found a blank screen when trying to load either MS home or Ubuntu.  After several hours, yes hours of research I stumbled on the fix of holding the shift while grub started to boot--after choosing to boot Ubuntu.  This allowed me an opportunity to edit the boot by choosing again the Ubuntu system and hitting e which allowed me to add to the boot list or whatever it’s called the notation acpi=off (this apparently is a problem with these older Dells)

The screen appeared to work as did the keyboard and I could enter Ubuntu.  However, when I tried to go into MS Home I was greeted with a blank screen (the system apparently booting in the background).

Because I didn’t want to go through the above manipulations each time I opened Ubuntu, I tried to edit the grub boot file.   In Grub2 this is in the etc file.  After saving my edit I  used the update order in the terminal.  I added the “acpi=off” to the line with “splash.”  It didn’t work and when I tried to boot I got the “grub > “ screen and had no way of getting into Ubuntu.  I couldn’t find my way out of this again after several hours of research.  The MS side continued with the blank screen.

I tried reloading Ubuntu using the live CD and erasing Home XP but failed and simply got the “grub>” terminal on booting the computer.

After several tries at erasing the MBR I succeeded in loading Ubuntu and had an almost workable situation except for the above noted issues on log in--use shift while booting, hit e after highlighting Ubuntu and adding acpi=off to the script).  Not an acceptable solution.

Adding insult to injury while trying to use Ubuntu I  may have loaded some malware I think while downloading the adblocker for Firefox--not from the Firefox site, I don’t recommend doing this.  The result was that when I selected a web site from search, or manually wrote in the URL more often than not I was taken to a Yahoo corporate advertising site.  

In the end I gave up.  I’m back to MS Home.  I would suggest caution for those with older computers who want to try Ubuntu.  It would have been cheaper (If I paid myself $10/hour) simply buy a new computer with Ubuntu, or for that matter a newer used computer that might work better than my almost 8 year old antique.   

In the end I enjoyed the challenge but there came a time for to ditch this ill fitting system (for my computer).

---

### Post by Zulu-Zeffir on 2010-08-05
Having struggled with many problems (some similar to what you have described except on an old IBM thinkpad) in many different flavors of Linux and with not ever reaching a viable solution in some cases; I have always walked away with a new found bit of knowledge then I did before ;)  There is going to be a learning curve no matter what new or different OS you choose to use be it M$, Mac, or Linux.  It may not be for the faint of hart but for some that's where the enjoyment is found.

---

### Post by QIII on 2010-08-05
I empathize.  I'm sorry your experience was frustrating.

There is a learning curve associated with learning a foreign language, and this is just the same.

I have had some difficulty installing Ubuntu on older machines due to  input devices not functioning properly.  This is often due to the fact  that the I/O devices internal to the machine will not work with the more recent versions of the X  server system (which controls I/O).

Before you throw up your hands entirely, it might be worth trying 8.04  LTS to see if some of your problems are solved.  I can't speak with any  authority on how well WUBI works, since I have never used it.  It is  intended to be used for just what you were using it for -- to kick the  tires and give it a try.  Unfortunately, you weren't able to do that.  A  pity.

It appears that in your last thread a finger was pointed at the machine.  Could be.  Maybe not.  Hard to say.

By the way, my 76 year young Dad uses Ubuntu.  But he's been a geek since he was in  High School in the late 40s.  I still ask him for technical support!

---

### Post by Cycledoc on 2010-08-05
QIII it had to be the computer, after all I know it wasn't me!?

---

### Post by Iowan on 2010-08-05
Moved to Ubuntu Testimonials & Experiences

---

### Post by simosx on 2010-08-05
Thanks for the testimonial, it's really useful.

My first comment would be that I believe the source of your Linux problem was the 'bad' BIOS. The BIOS includes information about the computer that the operating system can use for powersaving; it's the 'acpi=off' option you had to add because the BIOS was probably unusable by Linux.
If you are inclined, you can read more about the BIOS and the 'DSDT' information at [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

What I recommend for you, should you wish to dive again, is to search the Dell website for a BIOS update, and install it.

Then, if you face issues, you can ask here or on IRC ([http://www.ubuntu.com/support/community/chat](http://www.ubuntu.com/support/community/chat)) for immediate help.

---

### Post by MooPi on 2010-08-05
More or less your situations seems to have been an exasperating and almost endless hardware issue. I noticed that you only have the two posts to the forum. Maybe you should have visited us earlier. We like to help people just like yourself through those tough installs. Would you like to start again with the help of the forum ?  I imagine that may sound like a silly idea after all you have been through but have faith in the best online support forum. We may surprise you .

---

### Post by QIII on 2010-08-05
> **Cycledoc said:**
> QIII it had to be the computer, after all I know it wasn't me!?

I always say when my software doesn't work, its the user!  And typos in what I write are the fault of the keyboard!  ;)

Really, though.  I think what you have run into is some difficulty with hardware and maybe its interplay with WUBI -- not you.

---

### Post by nothingspecial on 2010-08-05
> **Cycledoc said:**
> In the end I gave up. 

Don`t blame you one little bit.

I am not being sarcastic when I say this.

I have tried windows a few times, and always give up because I don`t know what I`m doing.

I started with linux.

---

### Post by mastablasta on 2010-08-06
Ok - as some already mentioned there is alot of help available on forums as well as IRC channels (in case you need it faster).
 
Secondly there is special subforum for Dell computers.
 
Besides all this you should know that Wubi is not really linux. It's more like running a system within a system. it would be better to try a dual boot. it's very easy to do if you follow the procedure and experience could be better.
 
next just as there is dell subforum there is also a "Dell" compatible version of Ubuntu in existance. check those forums, because i think guys there compile a version that supports dell better than others.

---

### Post by Cycledoc on 2010-08-09
Many thanks for all the responses.  

Like the Schmoos in Lil Abner I keep bouncing back and have reinstalled, this time with success.  Nice double boot.  Working on configuring wireless now.

Regards

---

