---
title: "Needed: Usplash for Ubuntu CE (Edgy)"
date: 2006-11-18
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2006-11-18
I am about 90% done with what will be Ubuntu CE v2.0 (Edgy). I also have to complete the convert_me script and of course the website.

I really would like to have a a simple modification to the default Edgy usplash. I have attached a mockup of what I would like. I of course want it to look nice a smooth like the rest of Edgy. I have tried to build one with the wiki How To. I have been unsuccessful so far. 

If there are any Edgy Usplash experts that could please consider putting one together for Ubuntu CE I would really appreciate it.

God Bless, Jereme

---

### Post by bruenig on 2006-11-18
Idea:

The splash instead of filling up that progress bar should have jesus slowly ressurecting. That would be really cool.

---

### Post by mhancoc7 on 2006-11-18
> **bruenig said:**
> Idea:

The splash instead of filling up that progress bar should have jesus slowly ressurecting. That would be really cool.

Well, I really just want to keep the default one with a simple "christian edtion" added.

God Bless, Jereme

---

### Post by mysticrider92 on 2006-11-18
> **bruenig said:**
> Idea:

The splash instead of filling up that progress bar should have jesus slowly ressurecting. That would be really cool.

The splash screen in Ubuntu has to be very simple (640x480 pixels, 16 colors), so that probably wouldn't work. It would be cool though.

---

### Post by thibeaz on 2006-11-19
thats for sure

---

### Post by Jimmy_r on 2006-11-23
Try this one: [ATTACH]19858[/ATTACH]

Here is how I made it:

Installed package build-essential

Did a
```
apt-get source usplash-theme-ubuntu
```

Extracted the package that was downloaded.

Opened the png files inside with gimp, 
cut-resized-pasted the "christian ubuntu" text from your mockup to each png.

Opened the make file in the same directory and did a search-and-replace of "usplash-theme-ubuntu.so" to "usplash-theme-ubuntu-ce.so"

opened a terminal, cd to inside the folder, did a
```
make
```
which created the "usplash-theme-ubuntu-ce.so" file.

Then I installed it with SUM(see signature)

To install it manually:
```
sudo cp usplash-theme-ubuntu-ce.so /usr/lib/usplash/usplash-theme-ubuntu-ce.so
sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu-ce.so /usr/lib/usplash/usplash-artwork.so
sudo update-initramfs -u
```

---

### Post by mhancoc7 on 2006-11-23
> **Jimmy_r said:**
> Try this one: [ATTACH]19858[/ATTACH]

Here is how I made it:

Installed package build-essential

Did a
```
apt-get source usplash-theme-ubuntu
```Extracted the package that was downloaded.

Opened the png files inside with gimp, 
cut-resized-pasted the "christian ubuntu" text from your mockup to each png.

Opened the make file in the same directory and did a search-and-replace of "usplash-theme-ubuntu.so" to "usplash-theme-ubuntu-ce.so"

opened a terminal, cd to inside the folder, did a
```
make
```which created the "usplash-theme-ubuntu-ce.so" file.

Then I installed it with SUM(see signature)

To install it manually:
```
sudo cp usplash-theme-ubuntu-ce.so /usr/lib/usplash/usplash-theme-ubuntu-ce.so
sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu-ce.so /usr/lib/usplash/usplash-artwork.so
sudo update-initramfs -u
```

Perfect! Perfect! Perfect!

Thank you so much. This is going to be the final touch. I just ironed out all of the known wrinkles with what will be the initial Ubuntu CE Edgy release.

Could I get you to do one more thing for me? Could you send me a copy of the new usplash as a .pcx (640X480) image. I need it for the LiveCD bootsplash. I like for it to be the same as the Usplash. Looks more consistent to me.

God Bless, Jereme

---

### Post by mhancoc7 on 2006-11-23
> **mhancoc7 said:**
> 
Could I get you to do one more thing for me? Could you send me a copy of the new usplash as a .pcx (640X480) image. I need it for the LiveCD bootsplash. I like for it to be the same as the Usplash. Looks more consistent to me.

Never mind. I was able to get the pcx image made by using a screenshot of the Usplash. I really appreciate your help with this. I was starting to think this was going to be the one thing that did not get finished before I was ready to release. 

God Bless, Jereme

---

### Post by mhancoc7 on 2006-11-23
Ok, I made a mistake with the mockup. It should say "christian edition" not "christian ubuntu".

Would you mind to terribly much if I asked you to do it again with the new attached image? :) Sorry!

God Bless, Jereme

---

### Post by Jimmy_r on 2006-11-23
New version attached :) 
Tell me if any other changes are needed.

---

### Post by mhancoc7 on 2006-11-24
> **Jimmy_r said:**
> New version attached :) 
Tell me if any other changes are needed.

Thank you so much. That is going to look really great!

God Bless, Jereme

---

### Post by Darrious on 2006-11-24
Hope that you get Ubuntu CE v.2.0 up soon :)

---

### Post by doobit on 2006-11-24
> **Darrious said:**
> Hope that you get Ubuntu CE v.2.0 up soon :)

It would be wonderful if you used the 2.6.18.2 kernel instead of the 2.6.17 Ubuntu kernel because it just works better.

---

### Post by mhancoc7 on 2006-11-24
> **Darrious said:**
> Hope that you get Ubuntu CE v.2.0 up soon :)

I am working on testing right now. I believe I have got the final release ready. Once I test the convert_me script then I should be ready to upload. I anticipate, barring any other issues, to have it released within a week.
> **doobit said:**
> It would be wonderful if you used the 2.6.18.2 kernel instead of the 2.6.17 Ubuntu kernel because it just works better.
You are probably right about the 2.6.18.2 kernel working better. I am going to leave that up to the end user for now though.

God Bless, Jereme

---

### Post by Darrious on 2006-11-25
One question, what is the difference between the 2.6.18.2 kernel and the 2.6.17 kernel?:confused:

---

### Post by thibeaz on 2006-11-25
well it is just a newer kernel and it's one that ubuntu did use yet. The diffeence between the 2 might be function wise or just a few other things I don't know

---

### Post by Darrious on 2006-11-25
I just hope that it fixes a kernel panic. I actually had to install an older version of kernel just to get it to run. Now it works but I would always like to upgrade to a newer kernel.

---

### Post by doobit on 2006-11-25
I compiled it for myself using instructions I found here on this forum. It seems to boot faster, run faster and so far I have had no - zero - problems with it. All of the new packages work very well with it.

[http://kernel.org](http://kernel.org)
[http://www.ubuntuforums.org/showthread.php?t=217657](http://www.ubuntuforums.org/showthread.php?t=217657)

---

### Post by Darrious on 2006-11-25
Thanks that helped. 

Although I really hope that Ubuntu CE v2.0 comes out soon. I've been really wanting it.

---

### Post by meth on 2006-11-30
I have a problem, im trying to make my own usplash for my ubuntu, but when i type make in the shell i get 
pngtousplash throbber_back.png > throbber_back.png.c
/bin/sh: pngtousplash: not found
make: *** [throbber_back.png.c] Error 127
rm throbber_back.png.c
Where can i find pngtousplash?
I have been looking for it and cant find

---

### Post by meth on 2006-11-30
I needed to install usplash-dev package.

---

### Post by doobit on 2006-12-01
What's your final upsplash look like?

---

### Post by Darrious on 2006-12-01
Why do you not just use the convert_me_script if you want the Ubuntu CE splash.

If you are using your own then never mind.

---

### Post by meth on 2006-12-04
I want to use my own usplash, but i cant do it run

---

### Post by Darrious on 2006-12-04
Well I found a couple of sites you might want to look at.

[http://www.ubuntuforums.org/showthread.php?t=295524](http://www.ubuntuforums.org/showthread.php?t=295524)

And

[http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html](http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html)

---

### Post by meth on 2006-12-06
Thanks

---

