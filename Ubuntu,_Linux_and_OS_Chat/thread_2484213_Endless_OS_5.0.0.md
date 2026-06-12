---
title: "Endless OS 5.0.0"
date: 2023-02-20
forum: Ubuntu, Linux and OS Chat
---

### Post by kagashe on 2023-02-20
Endless OS was running with gnome 3.38 for a long time. Now it is updated to Endless OS 5.0.0 with gnome 41.3 on Wayland. For the first time it has multiple work spaces and gesture support like swipe left right with 3 fingers to switch between work spaces, 2 finger scrolling. I am delighted to run this new version of Endless OS.
[IMG]https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEghuWHdtsMANj_lZkEMxWd201C_zSlDkAt2z1wwrUxwpAs5JFGKWcvfNWVbuglPZ-xEnLtkowfZuEQVgid863cd9AEnkVQHlXQ479b6rEhbXQUqBbisAtKHIzQo8XSMb7pzDrkMZREQjCe6btU9DHQsrMzu_HiaiQ-jJbyoPKcGpMLsazweOq0/s1366/Screenshot%20from%202023-02-18%2019-29-23.png[/IMG]

---

### Post by poorguy on 2023-07-01
I'm using Easy OS 5.4.5 kirkstone64 as it comes OOTB.

Easy OS has a learning curve and has a good how to guide.

---

### Post by kagashe on 2023-07-01
> **poorguy said:**
> I'm using Easy OS 5.4.5 kirkstone64 as it comes OOTB.

Easy OS has a learning curve and has a good how to guide.
I It seems this OS is like Puppy Linux. Can I have frugal install of Easy OS like I have fossapup_64?

---

### Post by poorguy on 2023-07-01
> **kagashe said:**
> I It seems this OS is like Puppy Linux. Can I have frugal install of Easy OS like I have fossapup_64?

Yes it can be installed as a frugal.

[https://easyos.org/](https://easyos.org/)


***Wow I feel stupid. ***#-o[I]

**How embarrassing. **[/I]:oops: [I]

**You are posting about Endless OS 5.0.0 OS and for some reason I read it as Easy OS.**

**My apologies and I best have my eyes tested for glasses.**
[/I]

---

### Post by kagashe on 2023-07-02
> Wow I feel stupid.

    How embarrassing.

    You are posting about Endless OS 5.0.0 OS and for some reason I read it as Easy OS.

    My apologies and I best have my eyes tested for glasses.

Never mind. I was happy to receive a reply to my Endless OS thread and I am a fan of Puppy Linux and Barry too, Didn't know about this current venture of Barry and thanks for that.

---

### Post by poorguy on 2023-07-02
Cool Thanks.

I've heard of Endless OS however have never tried it guess I should give it a look.

I like Debian and Gnome DE however my computers are old and low powered by today's standard so Gnome DE can be a bit demanding on the old hardware.

---

### Post by kagashe on 2023-07-02
Running frugal install of Easy OS.

 Recently I came to know about Easy OS, a Linux distribution developed by Barry Kauler who developed Puppy Linux and gave it to community. I downloaded the .img file of easy 5.4.5 from this page and checked md5sum.

I created a folder EasyOS on root of the Ubuntu Linux I was running, mounted the .img file and copied its content (easy.sfs, initrd, vmlinuz) to EasyOS folder.

I added the following menu entry in /etc/grub.d/40_custom

menuentry 'Easy OS 5.4.5' {
search --no-floppy --fs-uuid --set 1e364a7e-9e6d-468a-99a2-404936a14d59
linux /EasyOS/vmlinuz rw wkg_uuid=1e364a7e-9e6d-468a-99a2-404936a14d59 wkg_dir=EasyOS
initrd /EasyOS/initrd
}

and updated grub.

I could boot into Easy OS Desktop.

I opened Package Manager (pkg) and clicked on Flapi.

I added Gnucash in Flapi by clicking on Customize button.
[IMG]https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhdTnBRFTY-xc25jQ-PYwcH8V4e4FPuOmYr0gXI1zmh4kFiEyGvOZaw7ZEcTZJCu8QtT4dSp4XryBC2wHeEuUWG9dU5pJeSG-ee-IVmHAYbFT7z2Vs45oYVOsgZfAmRq-FzdOlhD9cWk8VXTjj5y5i1yEc_gaM-bbSt0b-sYKIO9t3JlKKUlV5vcA/s362/Screenshotpart.png[/IMG]

and clicked on Add. It opened GnuCash page on flathub and asked me to confirm that it was the right application. After confirmation it downloaded the flatpak package and installed it.

Easy OS rocks!

---

### Post by poorguy on 2023-07-02
I agree Easy OS rocks.

I have not tried any of the Flatpaks / Flapi yet.

I'm using Appimages at the moment just more familiar with them.

I'm finding Easy OS to live up to it's name.

[COLOR=#000000]Barry Kauler gave the Linux community another good one imo.[/COLOR]

[COLOR=#000000]I like being able to lock down everything to ram and completely isolating and removing the hard drive(s) from the session if the user chooses to do so.

I check the news part of Easy OS website on a regular bases so I can stay up with the fixes and updates.

I haven't experience any issues  so far but then I'm mostly a web surfer.[/COLOR]

---

