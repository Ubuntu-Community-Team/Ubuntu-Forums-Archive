---
title: "Gnome horror story"
date: 2012-01-20
forum: Testimonials &amp; Experiences
---

### Post by fallofshadows on 2012-01-20
I'm writing this for two reasons. One, because I need to rant to people who understand just how painful this process was. Two, because I want everyone to NOT make the same mistake I did.

I recently updated to Ubuntu 11.10. Everything was working fine, I had all my previous settings/files. It was perfect. If you're like me, you prefer the Gnome Shell over Unity. One plus side to this is the extensions to the Shell you can get over the gnome shell website.

I was trying to work with my extensions, and the site was telling me I didn't have the most recent version of Gnome. Since there's no easy way to determine this, I took their word for it, and set out in search of the most recent version. I found a script a guy suggested, ran it, and everything went downhill.

Long story short, I had to delete my linux partition. I tried restoring the system image I had made about a week ago, but clonezilla didn't show the option to restore an image. I also couldn't boot my computer, it was saying there was no file found.

Desperate, I searched the internet from my phone. I found the exact error I was seeing: It was because my computer was trying to boot from Linux, but there wasn't any. It's an easy fix: just install a version of linux, and Grub comes with it. Well, that saved me from wiping everything (including windows, which I use occasionally for video editing.)

I installed Debian, figuring I could at least get the most up to date version of Gnome. Turns out it was running 2.xx, so I dumped it. I downloaded the Ubuntu 11.10 iso file, burned a disk, and managed to install it. Let me tell you, I've learned more about partitions over the course of the day than I ever knew before.

Finally, on my second attempt (didn't use Gparted the first time, had to burn a disk of that, too) I managed to install Ubuntu 11.10. I got it up and running, downloaded ~300Mb of updates/data/gnome shell, and got to work getting my settings back up. I downloaded Chrome, my new favorite web browser, and set off to the Gnome Shell Extensions website. Same message. "Your gnome shell is not up to date. click here to read more about this problem." Desperate, I clicked there.

Turns out the error wasn't my gnome shell. Ever. It was the fact that the website is in the alpha stage of testing, and only works under firefox. Which I had used, up until about 2 or 3 days ago.

I went through an entire day of stressing out, fearing I had lost my computer. All because I was using the wrong browser and didn't read closely enough that the site doesn't work under Chromium (or in my case, Chrome.)

Moral of the story: when it says "click here for more info," get all the info you can. Use multiple browsers. Don't be stupid, like I was. Tomorrow I'm going to spend most of my day bringing back all my pictures, videos, and documents from my external drive. What a way to spend my last few days of winter break...

---

### Post by nothingspecial on 2012-01-20
Not a support request.

Moved to Testimonials.

---

### Post by tommpogg on 2012-01-20
> **fallofshadows said:**
> 
I was trying to work with my extensions, and the site was telling me I didn't have the most recent version of Gnome. Since there's no easy way to determine this, I took their word for it, and set out in search of the most recent version. I found a script a guy suggested, ran it, and everything went downhill.


Thank you for sharing your story.
I believe the moral is never run a script if you are not 100% sure of what it is going to do.

---

### Post by craig10x on 2012-01-20
The reason the gnome shell extensions site told you you appear to not have the proper version of shell is because you went to the site on the chrome browser...if you had used firefox to go to the site you would not have gotten that message...and could have added whatever extension(s) you wanted...

I use and prefer Chrome myself (all the time in fact) but currently the gnome 3 extension site is not compatible with the chrome browser, and that is why you got that strange message...they really should mention it on their website because i would imagine it creates a lot of confusion for sure...

---

### Post by Juan Largo on 2012-01-20
I'm sorry to hear about your misfortune, and it's a real shame that Clonezilla let you down (underscoring the need to test your back ups).  Others could learn some good lessons from your troubles.  Thanks for sharing.

---

