---
title: "Just a little happy post"
date: 2008-02-29
forum: Testimonials &amp; Experiences
---

### Post by rphil2008 on 2008-02-29
Not all posts here in the forums are about problems and frustrations only, right? Well, let me just share how glad I am today that the Edubuntu 7.1 CDs I requested from Canonical arrived, together with my order from Amazon the book, Ubuntu Linux Toolbox.

Thanks Canonical for the free CD deliveries! I started out with Linux only a month ago merely looking for alternative to Windows. But  now my curiosity is in full swing. I'm happy that Ubuntu is so popular, it has many reference materials at Amazon, making learninig Linux for me a bit organized.

This newbie has got a lot of reading and experimenting this weekend=)

Happy weekend to all!

---

### Post by Drakkor on 2008-02-29
Enjoy the linux revolution ! ,lol  :lolflag:

---

### Post by geekcliff on 2008-02-29
In the last year i've become a total fanatic, i think i'm suffering from distro feaver, i cant stop downloading different distro's, i'm driveing everyone mad, i try them all, but always end up back on ubuntu, to me they are the daddy.

---

### Post by CaptainCabinet on 2008-02-29
> **geekcliff said:**
> In the last year i've become a total fanatic, i think i'm suffering from distro feaver, i cant stop downloading different distro's, i'm driveing everyone mad, i try them all, but always end up back on ubuntu, to me they are the daddy.

I was exactly the same. I wasted about a dozen CD's trying different distros but kept coming back to Ubuntu. Now that I've ran out of CD's I can finally settle into Ubuntu. :D

---

### Post by geekcliff on 2008-02-29
I've just bought a new pack of 100.:lolflag:

---

### Post by CaptainCabinet on 2008-02-29
> **geekcliff said:**
> I've just bought a new pack of 100.:lolflag:

Your going to be kept busy trying distros with all them. :D

---

### Post by ukripper on 2008-02-29
> **rphil2008 said:**
> Not all posts here in the forums are about problems and frustrations only, right? Well, let me just share how glad I am today that the Edubuntu 7.1 CDs I requested from Canonical arrived, together with my order from Amazon the book, Ubuntu Linux Toolbox.

Thanks Canonical for the free CD deliveries! I started out with Linux only a month ago merely looking for alternative to Windows. But  now my curiosity is in full swing. I'm happy that Ubuntu is so popular, it has many reference materials at Amazon, making learninig Linux for me a bit organized.

This newbie has got a lot of reading and experimenting this weekend=)

Happy weekend to all!

Be another Einstein this weekend among million others !!

---

### Post by geekcliff on 2008-02-29
> **CaptainCabinet said:**
> Your going to be kept busy trying distros with all them. :D
I'll be busy when the next ubuntu comes out, cos there will be, ubuntu , kubuntu two versions, xubuntu, linux mint, and freespire.:confused:

---

### Post by steveneddy on 2008-02-29
Don't forget to visit[ this site]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") for instructions and help.

---

### Post by geekcliff on 2008-02-29
Thanks, i've bookmarked it.
This is a good one too [http://users.skynet.be/yvesvanbelle/DebianCommands.html](http://users.skynet.be/yvesvanbelle/DebianCommands.html)

---

### Post by hyper_ch on 2008-02-29
Btw, you know there are CD-RW out there ;) initally more expensive than a CD-R one but once you burnt a few distros for test driving you start saving money ;)

---

### Post by CaptainCabinet on 2008-02-29
> **hyper_ch said:**
> Btw, you know there are CD-RW out there ;) initally more expensive than a CD-R one but once you burnt a few distros for test driving you start saving money ;)

True. :)
But the cd-r's i were using were my Dads because I couldn't afford my own at the time. :lolflag:

---

### Post by Drakkor on 2008-02-29
Not to mention all the "coasters" in the landfills now,lol :)

---

### Post by MONODA on 2008-02-29
> In the last year i've become a total fanatic, i think i'm suffering from distro feaver, i cant stop downloading different distro's, i'm driveing everyone mad, i try them all, but always end up back on ubuntu, to me they are the daddy.
yeah im doing that now i cant stop downloading!!! but i always come back to ubuntu.
> I was exactly the same. I wasted about a dozen CD's trying different distros but kept coming back to Ubuntu. Now that I've ran out of CD's I can finally settle into Ubuntu.
i just got 5 re-writable ones and keep the iso on my computer :)

---

### Post by rphil2008 on 2008-03-02
Whoaa! Thanks for all the encouragement guys! I thought I was the only one downloading all these distros, installing them on my home pc only to return to Ubuntu afterwards. I was about to ask if hard disks would deteriorate after repeated formatting. Heheh.

Well, first order of business for me last weekend was to install the NVIDIA driver I downloaded, following the NVIdia instructions. Through trial and error I figured out how to enable this libc-something being asked by nvidia during the installation. So far so good. Then the installer asked to restart X. I did... then trouble!

The system cant find a compatible display manager. All I had was the command line login screen! Hmmm... Turning to the book Ubuntu toolbox, I was able to navigate to the xorg.conf and twiddle with it to no avail. Fortunately, nvidia backed up my previous xorg.conf and I was able to restore it. 

To some of you, restoring a failed xorg.conf update is chicken feed but not for me. It's a good thing that the book has clear instructions on how to get to that backed up xorg.conf from the command line. I changed directory to /etc/X11/ and typed this command:

rm xorg.conf ----- deletes the bad conf
cp xorg.conf.backup xorg.conf-----restores the old conf while retaining the backup

Back to my working screen, I pat myself on the back for a job well done, broke open a can of beer while I pondered what the heck happened! LOL! Kidding.

I will just post some more questions in the proper forums. Man, do I have a lot of questions! Thanks for your help folks!

---

### Post by geekcliff on 2008-03-03
[QUOTE=rphil2008;4442891]Whoaa! Thanks for all the encouragement guys! I thought I was the only one downloading all these distros, installing them on my home pc only to return to Ubuntu afterwards. I was about to ask if hard disks would deteriorate after repeated formatting. Heheh.

Well, first order of business for me last weekend was to install the NVIDIA driver I downloaded, following the NVIdia instructions. Through trial and error I figured out how to enable this libc-something being asked by nvidia during the installation. So far so good. Then the installer asked to restart X. I did... then trouble!

The system cant find a compatible display manager. All I had was the command line login screen! Hmmm... Turning to the book Ubuntu toolbox, I was able to navigate to the xorg.conf and twiddle with it to no avail. Fortunately, nvidia backed up my previous xorg.conf and I was able to restore it. 

To some of you, restoring a failed xorg.conf update is chicken feed but not for me. It's a good thing that the book has clear instructions on how to get to that backed up xorg.conf from the command line. I changed directory to /etc/X11/ and typed this command:

rm xorg.conf ----- deletes the bad conf
cp xorg.conf.backup xorg.conf-----restores the old conf while retaining the backup

Back to my working screen, I pat myself on the back for a job well done, broke open a can of beer while I pondered what the heck happened! LOL! Kidding.

I will just post some more questions in the proper forums. Man, do I have a lot of questions! Thanks for your help folks![/QUOTE

I realy need to learn more of this stuff, its become far too easy just to slap in the install disc and go again.
I was just the same when learnig windows.

Ps: looks like i just screwed that quote up.

---

### Post by CaptainCabinet on 2008-03-03
> **geekcliff said:**
> [QUOTE=rphil2008;4442891]Whoaa! Thanks for all the encouragement guys! I thought I was the only one downloading all these distros, installing them on my home pc only to return to Ubuntu afterwards. I was about to ask if hard disks would deteriorate after repeated formatting. Heheh.

Well, first order of business for me last weekend was to install the NVIDIA driver I downloaded, following the NVIdia instructions. Through trial and error I figured out how to enable this libc-something being asked by nvidia during the installation. So far so good. Then the installer asked to restart X. I did... then trouble!

The system cant find a compatible display manager. All I had was the command line login screen! Hmmm... Turning to the book Ubuntu toolbox, I was able to navigate to the xorg.conf and twiddle with it to no avail. Fortunately, nvidia backed up my previous xorg.conf and I was able to restore it. 

To some of you, restoring a failed xorg.conf update is chicken feed but not for me. It's a good thing that the book has clear instructions on how to get to that backed up xorg.conf from the command line. I changed directory to /etc/X11/ and typed this command:

rm xorg.conf ----- deletes the bad conf
cp xorg.conf.backup xorg.conf-----restores the old conf while retaining the backup

Back to my working screen, I pat myself on the back for a job well done, broke open a can of beer while I pondered what the heck happened! LOL! Kidding.

I will just post some more questions in the proper forums. Man, do I have a lot of questions! Thanks for your help folks![/QUOTE

I realy need to learn more of this stuff, its become far too easy just to slap in the install disc and go again.
I was just the same when learnig windows.

Ps: looks like i just screwed that quote up.

In the future if you want install the latest Nvidia or ATI driver easily you can use a program called Envy. It makes the job extremely simple as it does everything for you and I swear by it. :)

---

### Post by billgoldberg on 2008-03-03
> **geekcliff said:**
> In the last year i've become a total fanatic, i think i'm suffering from distro feaver, i cant stop downloading different distro's, i'm driveing everyone mad, i try them all, but always end up back on ubuntu, to me they are the daddy.

Same here.

---

### Post by geekcliff on 2008-03-04
> **CaptainCabinet said:**
> [QUOTE=geekcliff;4444328]

In the future if you want install the latest Nvidia or ATI driver easily you can use a program called Envy. It makes the job extremely simple as it does everything for you and I swear by it. :)

I have used envy on debian and yes it is good, but with ubuntu the fist thing that happens after a clean install is, the restricted driver box pops up,and its just as easy to click on that, envy does seem to do a lot more work though, maybe i try it on ubuntu on my next install, which wont be to far away cos i want to have a go with open suse next, ive just tried it live and it gives some very interesting refresh rates, the fastest ive seen on my machine and thats only live.

PS: The ole distro fever is still there.

---

### Post by geekcliff on 2008-03-04
> **billgoldberg said:**
> Same here.

There is no cure, once your hooked.

---

