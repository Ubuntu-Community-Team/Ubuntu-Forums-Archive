---
title: "my experiences with ubuntu and a tablet"
date: 2012-01-03
forum: The Cafe
---

### Post by hogman500 on 2012-01-03
I decided to write this to discuss Ubuntu on tablets.

I received a 7" wintec filemate identity for Christmas and before Christmas I knew I would be getting it and I had already done a fair amount of research on android and using it. Having been a Ubuntu user since 7th grade (i am currentky a senior in highschool) u was very interested in having linux on my tablet Preferribly ubuntu  when i got it i used it for several days without any mods and was dissapointed by the abount of restrictions that android had on it. And being a linux user with complete controll over my system for so long i was annoyed witg them.

So i dcided to do some mods t completely allow me to do anything i wanted. So as any anandroid user knows the first step is rooting. Im lazy so instead of going througt the process of rooting i used the program superoneclick which allows you to connect your devise to the computor and click root to gain complete controll of you android. So i did all the basic rooted things overclocking, sdcard speed hacks, backing up. So the first thing u did was get titanium backup and batch backup my whole tablet to my sdcard having done that i was no longer scared to break it anymore because i had a backup. 

So now comes the part with linux. The first thing i found was an app called lil'debi which was supposed to be a one click debian/ubuntu installer. But it dident work it wuld start then you would click install and it would do nothing. I tried to force it  bt nothing. So i checked android market and i found linux installer an app that could install linux. So i statted it up and made a loop file image 1Gb in size and installed ubuntu 9.04 because i had used it ob the computor for mre than a year and it was very stable and no i am not still running it on that computor. So u installed the startup script linuxchroot and ran it on a terminal and i wasbsupprised it booted and worked.

So now i had a running linux distro on my tablet but no gui so my next step was to install a vnc server on it so i could use a vnc client on android and use it to access a gui. And ts is where i started to have problems  was missing a critical library for using apt-get libreadline and got huge strings of errors when i tried to  use it so i installed the library using dpkg --force-all -i and it installed and was functioning but now apt-get complained that the lib was too new so it fixed it by downgrading it and apt-get was fixed. Then while trying to install tightvnc i realized that many of my siurces in sources.list were broken so i manually installed tightvnc. But then i realized that i had no guu installe at all so i used apt-get to install xorg and tried to install xfce and gnome but those were somehow missing so i got some .deb files for icewm and installed that. And it worked but now apt-get complained about missing dependencies so many that it wanted to delete much of my system to fix it so i manually installed enough of them for apt-get to be able to fix it. Now i had a system wig a gui with no programs in it so i installed nautilus and synaptic and firefox and had a working system. But  i ran out of loop file space and resized it to 4.99 Gb.

Untill one day my tablet decided it was broken and would not boot so i had to reflash the rom and lost the root and the startup script so i rerooted using superoneclick and used titanium to restore and attemped to use linux installer to reinstall the script but it decided not to ket me so i reinstalled linux installer and reinstalled the script when i went on buntu i was supprised to find that my sources.list was working again and i tried to install gnash but i dident realize linux installer had replaced my sources.list  wiy a debian squeeze one so it tred to reinstall libudev and messed up dpkg apt-get and aptitude so pretty much everything important.

And thats where i am now a mostly working system. I can still download stuff and use it so i am ok since i have java and can run .jar files i am ok with it i should be able to fix it at some point.

Update:fixed apt reinstalled manually and all dependencies using dpkg-deb -X package.deb /

Thank you for reading.

---

### Post by cariboo on 2012-01-04
Why did you use an old unsupported version of Ubuntu?

---

### Post by kerry_s on 2012-01-04
lol, i'm still happy with Android, i don't think I'll try anything like that soon. 

i got a galaxy player 5.0, so far i only rooted, added adblock, tweaked the build.prop a bit for speed. the only thing i'm trying to figure out is how to remove the 4 tab limit on the stock browser, cause I'd rather use stock. i might try some memory tweaks, cause i do get the occasional hiccup when i'm downloading torrents. 
other than those things i'm very happy with Android,  don't think I'll ever go back to a PC.

---

### Post by hogman500 on 2012-01-04
Well the cool part is you dont lose android and ou can use it at the same time as ubuntu and i used an old version because i had used it before and had found it to be the most stable iv had to do many reinstalls of other vwrsions but not of 9.04 but i think i woukd have gone with a newer one if i had known how big a pain it would be lol i wdnt to try and upgrade buut amnot sure of the consequences of doing that

Want to do rom mods but there are none for my tablet lol

---

### Post by thatguruguy on 2012-01-04
> **cariboo907 said:**
> Why did you use an old unsupported version of Ubuntu?

This. Which happens to be the same point I raised in your other thread.  

For the record, you could have pretty easily installed Ubuntu 10.10 using the information contained [here]("http://forum.xda-developers.com/showthread.php?t=962023").

---

### Post by grahammechanical on 2012-01-04
And you enjoyed doing all that stuff? Wow! As we say where I live - it does me head in.

Have fun. I think that I will wait until I can buy a tablet with Ubuntu pre-installed and hopefully cheaper as well.

Regards.

---

