---
title: "Good bye Ubuntu, see you next release"
date: 2007-05-10
forum: Testimonials &amp; Experiences
---

### Post by thommango on 2007-05-10
Well, I give up...again.  I tried Ubuntu Dapper a while back and found that I just couldn't get the wireless thing going on.  When Feisty came out, I thought I'd try it again - but this time on a desktop to avoid the wireless problem.  I thought it was a fairly vanilla machine.  Alas, I found a whole new set of issues.  The machine (Dell SX260) doesn't come with dedicated video ram, and that, it turns out, made for mayhem.   Ubuntu wouldn't get out of  640x480 display.  

Oh there's lots of advice on the issue.  I tried reconfiguring this and changing that.  But none of it worked.  So, it's back to XP for this machine.  I'll keep Ubuntu on my daughter's laptop Thinkpad x600 and tryit again with  whatever computer I'm using when the next release comes out.   

So long, and thanks for all the fish.

---

### Post by rich.bradshaw on 2007-05-10
I had this - easy fix as well.


When you boot, go into your bios setup. Change the video memory to 8MB. Restart. It will work.

I have same computer.

---

### Post by drowner on 2007-05-10
Seeya!

---

### Post by Cypher on 2007-05-10
I've always been a little weary of Dell's shared RAM thing. It's a very sly way of saying they're giving you 1G or something, but take away a little for the video RAM. Very sneaky. Hopefully, now that Dell has decided to start including Linux as an option on their PC's, they'll stop all these tactics and start selling machines that behave just as well in Linux as Windows.

---

### Post by Blofeld on 2007-05-10
1.  try out a live system before installing
2.  laptops are notoriously difficult to install to:  as evidenced by the current massive problems with laptops and Windows Vista

---

### Post by Blofeld on 2007-05-10
3.  have you tried reconfiguring the X.org X window server by running [FONT="Courier New"]sudo dpkg-reconfigure xserver-xorg[/FONT] ?

---

### Post by 3rdalbum on 2007-05-11
My computer doesn't have dedicated VRAM, yet it is currently at 1152x864.

I don't know what sort of card is in your computer, but it's probably running off the open-source drivers. Those generally don't allow very good resolutions. Either use the vesa driver, or install some proprietry drivers.

---

### Post by Jhongy on 2007-05-11
> **Cypher said:**
> I've always been a little weary of Dell's shared RAM thing. It's a very sly way of saying they're giving you 1G or something, but take away a little for the video RAM. Very sneaky. Hopefully, now that Dell has decided to start including Linux as an option on their PC's, they'll stop all these tactics and start selling machines that behave just as well in Linux as Windows.

All on-board 3D graphics use shared RAM... nothing peculiar to Dell. 

Of course, Ubuntu should have no problem with it.

---

### Post by stanjam on 2007-05-11
It amazes me that people are so willing to give up BEFORE they reach out to ask if there is a solution to their problem, yet they arte willing to post about why they are leaving.

---

### Post by thommango on 2007-05-11
> **rich.bradshaw said:**
> I had this - easy fix as well.


When you boot, go into your bios setup. Change the video memory to 8MB. Restart. It will work.

I have same computer.

Yeah, I tried that and about 6 other pieces of great advice that work for other people/computers with varying success rates.  

Someone mentioned trying out the live version first.  I agree with the advice, but it wouldn't really make it possible to try some of the tips that I did try, because you need to change the xconf files or try a different driver, and I don't think you can really try these things from the live CD.  

Someone else thought I gave up too soon.  Well, I did try three different machines, four different install CDs and about 5 different suggestions for fixing the problem.  I think that's more than enough attempts and far more than enough if Ubuntu is going to actually make serious in-roads into the millions of people who just want their computer to work without a lot of fussing about.  

Thanks for the feedback.

---

### Post by stchman on 2007-05-11
> **thommango said:**
> Well, I give up...again.  I tried Ubuntu Dapper a while back and found that I just couldn't get the wireless thing going on.  When Feisty came out, I thought I'd try it again - but this time on a desktop to avoid the wireless problem.  I thought it was a fairly vanilla machine.  Alas, I found a whole new set of issues.  The machine (Dell SX260) doesn't come with dedicated video ram, and that, it turns out, made for mayhem.   Ubuntu wouldn't get out of  640x480 display.  

Oh there's lots of advice on the issue.  I tried reconfiguring this and changing that.  But none of it worked.  So, it's back to XP for this machine.  I'll keep Ubuntu on my daughter's laptop Thinkpad x600 and tryit again with  whatever computer I'm using when the next release comes out.   

So long, and thanks for all the fish.

My ATI equipped laptop has shared memory for the video card and no problems.  The BIOS takes care of allocating memory for the video card from system RAM.  I have 1G of RAM and the video card can take up to 128MB of RAM.  I have approx 870 MB RAM left.  No problem.  I had a time getting the madwifi drivers to work but on my desktop it runs extremely well.

You could also buy a better video card.  GeForce FX video cards are very cheap and then just disable the onboard video.

---

### Post by thommango on 2007-05-14
> **stchman said:**
> 

You could also buy a better video card.  GeForce FX video cards are very cheap and then just disable the onboard video.

Actually, I can't do that.  This particular machine is a small form factor Dell machine with no expansion slots.  (Dell SX260)

---

### Post by Enverex on 2007-05-14
> **Blofeld said:**
> 2.  laptops are notoriously difficult to install to:  as evidenced by the current massive problems with laptops and Windows Vista

This isn't really true, it entirely depends on the laptop and unless there is something dodgy or very very new about the laptop then it should be fine.

---

### Post by knadoor on 2007-05-14
> **thommango said:**
> Well, I give up...again.  I tried Ubuntu Dapper a while back and found that I just couldn't get the wireless thing going on.  When Feisty came out, I thought I'd try it again - but this time on a desktop to avoid the wireless problem.  I thought it was a fairly vanilla machine.  Alas, I found a whole new set of issues.  The machine (Dell SX260) doesn't come with dedicated video ram, and that, it turns out, made for mayhem.   Ubuntu wouldn't get out of  640x480 display.  

Oh there's lots of advice on the issue.  I tried reconfiguring this and changing that.  But none of it worked.  So, it's back to XP for this machine.  I'll keep Ubuntu on my daughter's laptop Thinkpad x600 and tryit again with  whatever computer I'm using when the next release comes out.   

So long, and thanks for all the fish.
Dude I too had the problem of Ubuntu running at 640x480 maximum, it was just a matter of modifying xorg.conf and saving some display settings via terminal. Not big of a deal really. :) Now I run Ubuntu at 1280x1024 resolution with 3D capabilities. ;)

---

### Post by newlinux on 2007-05-14
We hope you do come back. If you want to get around the install headaches you can buy your next machine with specs better suited to easy ubuntu installation your could be ubuntu pre-installed.

Good luck!

---

### Post by thommango on 2007-05-14
> **knadoor said:**
> Dude I too had the problem of Ubuntu running at 640x480 maximum, it was just a matter of modifying xorg.conf and saving some display settings via terminal. Not big of a deal really. :) Now I run Ubuntu at 1280x1024 resolution with 3D capabilities. ;)

 Thanks for the advice.  Like I said at the beginning of the thread, I tried many great pieces of advice (inlcuing your tip) without success.  I guess the problems are not exactly identical, despite the fact that the symptoms are.  At this point, someone would have to tell me that they have it running successfully on an identical machine (Dell SX260) before I'd consider re-installing.    

Cheers

---

### Post by thommango on 2007-05-25
Just tried Xandros on the same Dell SX260.  It installed perfectly.  3d effects work, printer found, etc.  Smoothest install I ever experienced (including windoze).  Looking back on the time to configure and remove, it seems well worth the $40.

---

### Post by lazyart on 2007-05-25
Congrats on finding a distro that works for you. :)

---

