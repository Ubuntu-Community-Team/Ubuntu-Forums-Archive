---
title: "Why fork Gnome version also questions?"
date: 2012-12-03
forum: Ubuntu Development Version
---

### Post by kidx on 2012-12-03
I have 13.04 install how can I revert I am not liking the new gnome here is why.

The rectangle on minimizing.
Top bar is very empty why make 2 panels?
No hot spot.
Also this looks like a fork.

How do I revert to 12.10 with out the new Gnome cause its lame and boring just when I get used to the real gnome and like it it switch's to a wanna be mate version.

---

### Post by deadflowr on 2012-12-03
Gnome-what? Gnome-shell, Gnome-classic?

I far as I know, reverting back to 12.10 would require reinstalling 12.10 from scratch. 

As a note, the cinnamon desktop is in the raring repos.

For me personally, the only changes that annoy me are the ones for nautilus. I prefer an extra pane to an extra window or tab.

---

### Post by kidx on 2012-12-03
Looks like I wont be going above 12.10 then I guess this is where i am gona stay at since every thing is a Fork and not true Gnome.

---

### Post by Mr. Picklesworth on 2012-12-03
Sounds like you're using the GNOME Classic session. Might be that it's doing that on its own as a fallback, which it does if your graphics driver doesn't have the necessary support. (Happens a lot at this stage). If you open System Settings / Details, it will tell you about that in the Graphics page.

In 13.04, the fallback session will be going away, so it will just use GNOME Shell through llvmpipe. So, this will stop happening *on its own* soon enough, but chances are you just need to fiddle with your graphics drivers.

By the way, it's helpful to specify the shell you are using. GNOME is a suite of desktop applications, and then there are a bunch of shells that integrate nicely with it. GNOME Shell is the one that's a core part of GNOME, and there a bunch more like Unity and Cinnamon. I am assuming you're using GNOME Shell, of course, but as you can see it confuses people mightily and it doesn't make much sense to refer to the shell itself as "GNOME" ;)

---

### Post by screaminj3sus on 2012-12-03
13.04 uses unity 3d as the shell by default just like 12.10 does.

What desktop are you trying to use? gnome-shell? ubuntu doesn't include gnome-shell out of the box (and never has), you need to install it and select it from the login screen. The default session should be unity 3d.

It sounds like you may have logged into the fallback mode somehow.

13.04 is still extremely early in development, it doesn't come out until april. There's no way to downgrade, you'd need to download 12.10 and reinstall.

---

### Post by kidx on 2012-12-03
> **Mr. Picklesworth said:**
> Sounds like you're using the GNOME Classic session. Might be that it's doing that on its own as a fallback, which it does if your graphics driver doesn't have the necessary support. (Happens a lot at this stage). If you open System Settings / Details, it will tell you about that in the Graphics page.

In 13.04, the fallback session will be going away, so it will just use GNOME Shell through llvmpipe. So, this will stop happening *on its own* soon enough, but chances are you just need to fiddle with your graphics drivers.

By the way, it's helpful to specify the shell you are using. GNOME is a suite of desktop applications, and then there are a bunch of shells that integrate nicely with it. GNOME Shell is the one that's a core part of GNOME, and there a bunch more like Unity and Cinnamon. I am assuming you're using GNOME Shell, of course, but as you can see it confuses people mightily and it doesn't make much sense to refer to the shell itself as "GNOME" ;)

Let me say this I like Gnome 3 if there is a shell involved then yes I like it as well but Gnome3 is what i am used to calling it and thats what I like.But maybe I was in fall back mode so then I guess ill try again or wait till the fall back is gone casue it looks like mate version but in Gnome 3 if you know what i mean.

---

### Post by kidx on 2012-12-03
> **kidx said:**
> Let me say this I like Gnome 3 if there is a shell involved then yes I like it as well but Gnome3 is what i am used to calling it and thats what I like.But maybe I was in fall back mode so then I guess ill try again or wait till the fall back is gone casue it looks like mate version but in Gnome 3 if you know what i mean.

Fall back mode keeps enabling whats up with AMD drivers only when I install them whats a good driver for AMD HD5770 with 12.10?

---

### Post by deadflowr on 2012-12-03
When you login, in the box where your name/password is at the login screen click the Ubuntu logo in the rght corner and see if you can select a different desktop.
You can probably tell us what desktops are on your system, as this will help us understand what you're saying better.

My personal feeling though is that if you're having troubles identifying your desktop, then maybe you shouldn't be running the development branch.

---

### Post by kidx on 2012-12-03
> **deadflowr said:**
> When you login, in the box where your name/password is at the login screen click the Ubuntu logo in the rght corner and see if you can select a different desktop.
You can probably tell us what desktops are on your system, as this will help us understand what you're saying better.

My personal feeling though is that if you're having troubles identifying your desktop, then maybe you shouldn't be running the development branch.

I don't have trouble Gnome 3 is Gnome 3 and yes I see Gnome,Gnome classic,System default.

---

### Post by kuvanito on 2012-12-03
kidx i wish i knew what you are talking about but i can't make anything out of your topics.
i am running RR 13.04 and it is as Gnome as it could get and i see nothing of what you talk about
here are some pics for you,i myself don't like Unity and thats the first thing i remove when i install 13.04 but that's my choice.i can assure you that Gnome 3 works perfect with 13.04 so i have no idea of what your issue is.i wish i can help.

---

### Post by kidx on 2012-12-03
> **kuvanito said:**
> kidx i wish i knew what you are talking about but i can't make anything out of your topics.
i am running RR 13.04 and it is as Gnome as it could get and i see nothing of what you talk about
here are some pics for you,i myself don't like Unity and thats the first thing i remove when i install 13.04 but that's my choice.i can assure you that Gnome 3 works perfect with 13.04 so i have no idea of what your issue is.i wish i can help.

I am having a graphic driver issue it wont install my drivers keeps saying versa annoying any ideas how to get drivers installed? DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details

---

### Post by cariboo on 2012-12-03
There is a thread in this sub-forum concerning the installation of AMD/ATI drivers [here]("http://ubuntuforums.org/showthread.php?t=2074962").

I'd like to thank jfernyhough for his efforts in keeping us informed of what it takes to install the drivers.

---

### Post by kidx on 2012-12-03
> **cariboo907 said:**
> There is a thread in this sub-forum concerning the installation of AMD/ATI drivers [here]("http://ubuntuforums.org/showthread.php?t=2074962").

I'd like to thank jfernyhough for his efforts in keeping us informed of what it takes to install the drivers.

this ain't working at all wish it would but it keeps saying Versa drivers installed?

---

### Post by deadflowr on 2012-12-04
Can you run fglrxinfo?
If so, the fglrx drivers are installed.

Where is it telling you that the drivers are "versa".

Do you have the AMD catalyst control center?

---

### Post by kidx on 2012-12-04
> **deadflowr said:**
> Can you run fglrxinfo?
If so, the fglrx drivers are installed.

Where is it telling you that the drivers are "versa".

Do you have the AMD catalyst control center?

This is weird its showing i got beata installed I have the AMD testing only water mark but I get this on fglrxinfo also Fall back mode wont bug off.

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

---

### Post by kuvanito on 2012-12-04
> **kidx said:**
> How do I revert to 12.10 with out the new Gnome cause its lame and boring just when I get used to the real gnome and like it it switch's to a wanna be mate version.

best advise:
you should never upgrade
always do fresh installs

---

### Post by kidx on 2012-12-04
> **kuvanito said:**
> best advise:
you should never upgrade
always do fresh installs

Ok but I still have driver issues I think this is the only distro that I have this much issues with for drivers well this version when I go to details it shows Versa when I in fact have Catalyst installed also looks like I have to use the open source drivers I hope they are good for gaming.

---

### Post by Mr. Picklesworth on 2012-12-04
They aren't great for games, but neither is 13.04 (yet). The proprietary graphics drivers can be a moving target, so if you want them to be always working I suggest using 12.10 as your main driver for at least a few more months :)

---

### Post by kidx on 2012-12-05
> **Mr. Picklesworth said:**
> They aren't great for games, but neither is 13.04 (yet). The proprietary graphics drivers can be a moving target, so if you want them to be always working I suggest using 12.10 as your main driver for at least a few more months :)

Well 12.10 driver wont install right at all just lack of performance fall back mode keeps on enabling witch is annoying as hell.

---

### Post by sgage on 2012-12-05
> **kidx said:**
> Ok but I still have driver issues I think this is the only distro that I have this much issues with for drivers well this version when I go to details it shows Versa when I in fact have Catalyst installed also looks like I have to use the open source drivers I hope they are good for gaming.

Just a suggestion: Please consider using proper punctuation to indicate the end of sentences. Your posts are hard to read, and you are more likely to get help if you make things a bit easier. Thanks!

---

### Post by kidx on 2012-12-05
> **sgage said:**
> Just a suggestion: Please consider using proper punctuation to indicate the end of sentences. Your posts are hard to read, and you are more likely to get help if you make things a bit easier. Thanks!

Not to be rude but i am not pro at spelling on here so please don't judge thanks.Also I am having a driver issue looks like I gotta fix it on my own since my spelling is not pro and I don't meet your standards.

---

### Post by sgage on 2012-12-05
> **kidx said:**
> Not to be rude but i am not pro at spelling on here so please don't judge thanks.Also I am having a driver issue looks like I gotta fix it on my own since my spelling is not pro and I don't meet your standards.

Don't get so defensive. First, I wasn't judging - I was letting you know that it was hard to parse your writing. Second, I wasn't talking about spelling at all. Third, I didn't say anything about meeting standards - I was trying as politely as I could to explain that you would get more help if people could make sense of your writing more easily. A lot of people here are quite busy, and it helps to make things as clear as possible if you want good help. 

No need to be offended, or sarcastic.

---

### Post by ventrical on 2012-12-05
> **kidx said:**
> Not to be rude but i am not pro at spelling on here so please don't judge thanks.Also I am having a driver issue looks like I gotta fix it on my own since my spelling is not pro and I don't meet your standards.


Can you download the daily and  make a start up disk using StarupDiskCreator? If so, then try that, and then try to boot it and run in live mode and see what happens.

I have two machines with ATi graphics. They are not high performance but play games and compiz really good. I just use fglrx and ignore catalyst control center. it is a false/positve bug on older machines but I am not sure why it is a bug on your machine.

---

