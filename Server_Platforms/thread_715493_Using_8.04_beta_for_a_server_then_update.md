---
title: "Using 8.04 beta for a server then update?"
date: 2008-03-04
forum: Server Platforms
---

### Post by Sir Jake on 2008-03-04
Pretty much what the title says, I am wondering if I could install the beta for 8.04 then install gui, then once it's out of beta is it just an update to the full thing? Or what? I have a week befor I bring my server to a colocation and right now have fedora 8 on it... It sucks, I much rather use this. Anyhelp would be great. :)
Thanks in advance.

---

### Post by tubezninja on 2008-03-04
If it's going to be a production server, you'll probably want to stick with 7.10 for now.  You should be able to upgrade to 8.04 when it officially gets released, from 7.10.

---

### Post by nickjqw on 2008-03-05
What is it in 8.04 that you need?  If the answer is nothing, then stick with 7.10.  I use 6.04 all the time, gotta love the 5 years of support.  I'm going to be really happy when 8.04 is out, though, there are some great things I've been waiting for, like resizing ext3 volumes on the fly... it's about time!

---

### Post by igknighted on 2008-03-05
If you are doing this as a home server, I think that's a great plan.  In actuality, there is no "upgrade" to do, just keep up with the daily updates and you will be using the final release when it comes out (actually a little sooner).  This would be easier and less of a hassle than using 7,10 and upgrading, or even 6.06.2 and upgrading.

For a business, you may want to either go with a more stable release like 6.06.2 or even Debian Etch or CentOS... or delay bringing the server online until 8.04 is out or very close.  You could upgrade (in theory) to 8.04 from 6.06.2, but I am skeptical that the upgrade would succeed from versions that far apart, so you would likely be looking at a full reinstall if you choose to go to 8.04 in april no matter what you choose now (aside from just rolling the dice and using 8.04)

---

### Post by Sir Jake on 2008-03-05
Okay, well right now I have my server on Fedora Core 8.. I hate the support on their forums and so on. I think my home is here with ubuntu.
So I guess I'll install 7.10 on it, the server is going to be run in a colocation for my Gaming clan. I need it up very soon, will installing ubuntu 7.10 server give me the same raid setup options as I got with the alternate install cd?  As I need to setup raid 1 :)
Once again thanks for your help and quick replys.

---

### Post by tubezninja on 2008-03-05
Is this a software RAID 1 that you're setting up?  If so, there's a tutorial on setting up a RAID  with 7.10 server here:

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

---

### Post by Sir Jake on 2008-03-06
Yes it would be software raid, my onboard card does not support linux. :(
Server is taking me a bit longer to setup now, my harddrive just died on my main computer with most of my info on it.  What is a good program for me to download for my server to reduce my chances of getting hacked as my server is going to be located in a colocation.
The raid setup worked great by the way thanks. :)

---

