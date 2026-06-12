---
title: "I finally will stick with it"
date: 2009-05-12
forum: Testimonials &amp; Experiences
---

### Post by patrickalexson on 2009-05-12
Ive tried Ubuntu since the 7.x days

I am very happy with the newest 9.x version of Ubuntu for a few reasons:

1. Performance wise, it seems much faster than previous versions
2. Driver support seems to have increased
3. I believe its been out long enough to have EXTENSIVE support options

Here are my complaints, those of which CANNOT really be aimed toward Ubuntu:

1. That dam AMD Unsupported Hardware watermark which totally prevents me from seeing the minimap in Warzone 2100 and other applications
2. CPU scaling which makes almost every application I run become 'laggy' for lack of a better term

* I know how to change it but whenever my system restarts, it reverts back and Ive been too lazy to go in depth in how to keep it changed
3. I think that, sambia? I do believe thats the service that allows me to connect to shares on Windows based PCs should be installed by default. I would assume it would be used more often than not

With that being said I want to give a hats of to the team and a 7.62mm bullet to AMD for that precious watermark.

If someone feels helpful enough and wants to help a noob, message me here or at my email, [email]compelx@gmail.com[/email] with possible solutions to that AMD watermark deal.

Thanks!!

---

### Post by Peter09 on 2009-05-13
removed

---

### Post by 3rdalbum on 2009-05-13
> **patrickalexson said:**
> 
3. I think that, sambia? I do believe thats the service that allows me to connect to shares on Windows based PCs should be installed by default.

Er.... it is.

If you want to set up a Samba server, that's an extra download - it's Ubuntu policy to not have open ports by default, and let's face it if you're on a network you're very likely to have internet access. But connecting to existing shares is available out-of-the-box on Ubuntu.

---

### Post by patrickalexson on 2009-05-13
Well everything works except for my graphics card driver...it seems way to unstable. It will frequently blur text and cause applications running in full screen mode to refresh at odd intervals and to minimize randomly.

I know its not the card cause Im able to boot into my Windows partition and the card runs fine with all the other applications.

I used the restricted drivers that came with the CD and they appear to be the latest available but no luck still.

I have a support thread open and am awaiting a response from the community.

Besides that, im loving it.

---

### Post by stchman on 2009-05-13
> **patrickalexson said:**
> Ive tried Ubuntu since the 7.x days

I am very happy with the newest 9.x version of Ubuntu for a few reasons:

1. Performance wise, it seems much faster than previous versions
2. Driver support seems to have increased
3. I believe its been out long enough to have EXTENSIVE support options

Here are my complaints, those of which CANNOT really be aimed toward Ubuntu:

1. That dam AMD Unsupported Hardware watermark which totally prevents me from seeing the minimap in Warzone 2100 and other applications
2. CPU scaling which makes almost every application I run become 'laggy' for lack of a better term

* I know how to change it but whenever my system restarts, it reverts back and Ive been too lazy to go in depth in how to keep it changed
3. I think that, sambia? I do believe thats the service that allows me to connect to shares on Windows based PCs should be installed by default. I would assume it would be used more often than not

With that being said I want to give a hats of to the team and a 7.62mm bullet to AMD for that precious watermark.

If someone feels helpful enough and wants to help a noob, message me here or at my email, [email]compelx@gmail.com[/email] with possible solutions to that AMD watermark deal.

Thanks!!

Samba is intended for Windows machines to connect to Linux machines.  I have found that Linux machines have great difficulty IMO connecting to a Windows machine.  Since I run all Linux at home I use NFS.

---

### Post by patrickalexson on 2009-05-13
Ok that would make sense cause It was much easier to attempt to connect to the linux machine from a windows based laptop than the other way around

I know im being repetative but I jacked up my machine, could someone give me an idea how to (by using the shell from safe mode) uninstall all graphics drivers?

---

### Post by HappyFeet on 2009-05-13
```
sudo apt-get remove xorg-driver-fglrx 
```

---

### Post by patrickalexson on 2009-05-14
Finally! Thanks Happy. Ill give her a shot tomorrow.

---

### Post by moster on 2009-05-14
> **patrickalexson said:**
> ...
2. CPU scaling which makes almost every application I run become 'laggy' for lack of a better term

* I know how to change it but whenever my system restarts, it reverts back and Ive been too lazy to go in depth in how to keep it changed

Thanks!!

Just go into BIOS and disable that CPU scaling. It must be somewhere there. I have do it and it feel more responsive.

---

### Post by patrickalexson on 2009-05-14
I do not have any custom settings for powersave or scaling in the BIOS. My Windows OS keeps my clock at its highest. Its something in Ubuntu. I like the idea of not wasting resources but in this case, Im not running it on a laptop to conserve power, and applications are very laggy until I bump it to 'performance' mode in the CPU notification dock bar item (whatever).

I gotta find a way to KEEP IT on performance mode.

---

### Post by moster on 2009-05-15
> **patrickalexson said:**
> I do not have any custom settings for powersave or scaling in the BIOS. My Windows OS keeps my clock at its highest. Its something in Ubuntu. I like the idea of not wasting resources but in this case, Im not running it on a laptop to conserve power, and applications are very laggy until I bump it to 'performance' mode in the CPU notification dock bar item (whatever).

I gotta find a way to KEEP IT on performance mode.

Ok, you are no alone in that problem, here is your answer

[http://ubuntuforums.org/archive/index.php/t-1111609.html]("http://ubuntuforums.org/archive/index.php/t-1111609.html")

But, I never see BIOS without that option. AMD call CPU scaling "Cool 'n' quiet" if you have that in your bios, that is your problem :)

---

