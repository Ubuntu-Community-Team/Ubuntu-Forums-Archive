---
title: "Server Upgrade Questions (6.10 -&gt; 8.04, 7.04 -&gt; 8.04)"
date: 2008-04-25
forum: Server Platforms
---

### Post by MadHatHost on 2008-04-25
I need some good Ubuntu Advice ...

I recently started with a company that has 2 Ubuntu servers running, both at 6.10. I am faced with the daunting task of upgrading both of them to the latest LTS version of Ubuntu.

I started working on the development server last night and upgraded it from 6.10 to 7.04 with only a couple hunderd issues. ](*,) (Somehow, my first network card stopped working the way I thought is was supposed to, but that's neither here nor there) ...

Here are my questions:
 - Am I going about this the right way? 
 - Should I finish the dev server by going straight from 7.04 to 8.04, or should I go through 7.10 first?
 - When I choose to upgrade the production server, Is there a safe way to go from 6.10 straight to 8.04?

The person who setup these servers did things differently that I probably would have, but it seems to work. I have setup many linux servers, but am new to Ubuntu as of Sept. 2007. 

Any advice would be greatly appreciated ...

Thanks
Keith

---

### Post by Rohan Kapoor on 2008-04-25
Check out this link [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

However, you would have to bring both to 7.10 following the instructions above. going from 6.10 to 7.04 to 7.10 to 8.04.

---

### Post by XioNoX on 2008-04-25
2 ways : Update step by step or from scratch...

 step by step is normally harmless, but if there are exotic packages/configurations it can be dangerous. As soon as you have updated your server to the next version all others will be a lot easier.
I've done all updates on my home server since 6.06, and it is still working very well (and i've did bad things to it)

---

