---
title: "Install problem with corrupt 'Make'"
date: 2010-02-15
forum: Server Platforms
---

### Post by katiwhompas on 2010-02-15
Greetings,  Okay, I spent several hours with my wacky ex-marine,Vietnam War Veteran friend as he was babysitting his equally wacky grandson. (Trust me, it was not pretty), trying to download 9.10 server which I need VERY BADLY as I am way behind in a project. Why am I telling you this? Because I have to drive over 2 hours as I live next to or almost on top of the continental devide. I use a cellular internet connection, he has a 7MBs DSL line as he lives in the city a couple hours away. This will make sense eventually...  His setup or &quot;computer&quot; is a old HP notebook with 128 megs of ram running windows 2000 pro.  So, I used a downloader that pulls from up to 10 threads and reassembles at the end.  This is where I get to the point.  Upon reassembly things I suppose went awry, once back in the middle of no-where I start loading this server software and I get: Warning: file:///cdrom/pool/main/m/make-dfsg/make_3.81-6i386.deb was corrupt. The damn check sum is not adding up. Yet it was good to go according to the old gimpy notebook.  Okay, fine. I can get to the point of installing when my monitor is saying manual package whatever instead of getting the LAMP setup at the get-go. I can then get to &quot;landscape&quot;, so...    My question is can anyone tell me how I can get 'make_3.81-6 etc. using landscape, or whatever it is called, or in some other perhaps more arcane pathway so I can go forward making my LAMP? Or do I have to drive another 2 hours to do it all again AND I would have to drag my rig along so as to avoid using the gimpy notebook? I am used to apt-get and the BSD package manager... But how do I get make so I can get my work done? Thank you in advance for even getting this far in my rant...

---

### Post by Satoru-san on 2010-02-15
If one package on the CD is corrupt, there are bound to be more, is there any way that you can redownload the ISO, and then reburn it to a different CD? I totally hear you about your problem, however this particalar part of the forum is dead around this time in the afternoon. Most americans are sleeping.
I don't really have any other way to help you other than that, You might want to ask in a more popular forum like general help. You will get WAY more responses.
I hope everything goes well, I probably wont be here when you respond to this post, so I hope everything goes well.
Sorry to hear about your problem.
Welcome to the forums :KS

Shitsurei shimasu~

P.S. ~ I read the whole thing almost twice to make sure I understood.

---

### Post by katiwhompas on 2010-02-15
Hi

I tried to get this note out shortly after getting the message, but something went awry with the site or my browser... This is my 4th try to get a message back. Odd really, I kept getting the error that I needed at least 1 character. I had more than that... so, I gave up. I will try again...

Okay, I was able to install the base package. I was not able to install using the LAMP option. Since the only reason I reason got this package was to save me the time and aggravation associated with building intranet LAMPs' for internal site testing of commercial websites. 

So, I comprimised and called another friend and will use their connection as it will only take 6 hours instead of the 20 or so mine would. But I gotta say, there is nothing like pulling 7 Mbs to make you feel like you are getting something done... I am just spoiled I guess...

Thanks for responding Satoru-san,

---

### Post by Satoru-san on 2010-02-16
So you were able to get it installed? Or you are trying to download it again? I am so sorry once again to hear about your problem, no one is meant to have to handle these problems, yet I help people with them every day. We figure it out eventually and can help others. The problem is in this case I don't know 100% for sure. I am just speculating. I hope you fix your problem, I will see if I can get some other people to look at your problem.

---

### Post by katiwhompas on 2010-02-16
Well, it has gotten stranger... I did get another download and the very same thing or error with make came up! I used a different provider and computer to download and used a different (Mac) box to burn the iso. I am at a complete loss for what to do.
 
I now have 3 server install discs. I now can not get even the base system installed. 
I also kept getting an error from this server that I had nothing written, yet I had. Now I am using IE instead of firefox and that seems to be working. 
 
I put my problem into the general area, but no one is reading it... I really have no clue why except it may be the way I started off. Anyway, I realized that my problems really started after I had installed NetBSD. The odd thing is I can install Wndows XP Pro with no problems yet I get all kids of errors with both the server and desktop versions of ubuntu. I even tried the ubuntu desktop I had before all this started; 9.04.
 
My last try at installing ubuntu gave me this error:initramfs) stdin: i/o error
mount: mounting /dev/loop0 on //filesystem.squashfs failed: no such device
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
 
Now even NetBSD install disc gives me an I/O error?!?  my sleen aches with the memory of frustration. And yet I can install windows XP Pro. 
 
I am going to wander the internet to see if I can find some answers to this. Thanks for trying!

---

### Post by Satoru-san on 2010-02-16
Hrm, seeing as you burned it on a different computer, it IS possible that you are burning on a cd-r and its a cd+r drive, however modern cd drives aren't effected by this, but some drives cant read burned cd's at all. This may be the case, it may not be. You could try ordering a cd from Ubuntu. I dont think they can send you server, but it is almost the same you just need to apt get the right files.

---

### Post by katiwhompas on 2010-02-17
The Nightmare continues...

I finally solved the install problem. There is a problem between the computer I want to install on and server 9.10

After a lot of banging my head (figuratively) againsed the box I did get 9.04 desktop to load. I swapped part after part until it worked.

Now a bigger problem popped up. I tested the 9.10 desktop - Try before you install- option and while it would not run on the machine I wanted it on, it did work on my workstation. However when I shut down Ubuntu 9.10 mt workstation was destroyed! Well, my video would no longer work. It has taken 2 days and a lot of strees to resolve. I had to re-install my entire Operating System. I am so screwed. I was tying to get a LAMP to get this very important work done and instead I have angered all the clients and may loose the job. This is a terrible distro they never should have put 9.10 on the site as it is so full of bugs that it just has made me want nothing to do with Ubuntu again. I used to install it on all my friends boxes, but never again. I still do not know if my main work station works!

---

