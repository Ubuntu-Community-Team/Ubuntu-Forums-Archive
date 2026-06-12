---
title: "Caffeine 0.3 out with major improvements!"
date: 2009-08-27
forum: The Cafe
---

### Post by Nevon on 2009-08-27
After little over a month of development, Caffeine 0.3 is now out!

If you don't know, or can't remember what it is; Caffeine is basically a little coffee cup that sits in your system tray - waiting for you to click it. Once you do, it instantly fills up with fresh coffee - keeping your computer from going asleep. In other words, it's a system applet that allows you to inhibit the screensaver and "sleep" power saving mode in an easy way. 

[img]http://blog.mahboy.com/wp-content/uploads/screenshot_029.png[/img]

Here's what we've been up to since the last time:
[LIST]
[*]Complete object-oriented rewrite.
[*]Support for xscreensaver
[*]Support for DPMS
[*]Full support for internationalization
[*]Command-line interface
[*]Simplification of packaging
[/LIST]
[URL="http://www.reddit.com/r/linux/comments/9eksu/caffeine_03_the_cute_and_easy_way_to_inhibit_your/"]
Full announcement with more information[/URL]

If you want to know more about the project, [check out our wiki]("http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page").

---

### Post by binbash on 2009-08-27
Any Karmic PPA?

---

### Post by Nevon on 2009-08-27
> **binbash said:**
> Any Karmic PPA?

Yup. [https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

---

### Post by binbash on 2009-08-27
Thanks, i am gonna review it soon.

---

### Post by joey-elijah on 2009-08-27
I don't even need this but i'm installing it because it's just such an awesome idea! Tack så mycket! ^_^

Blog post on it being written as i tippity-type, too!

---

### Post by Nevon on 2009-08-27
> **joey-elijah said:**
> I don't even need this but i'm installing it because it's just such an awesome idea! Tack så mycket! ^_^

Blog post on it being written as i tippity-type, too!

You know, I wasn't really sure I needed it before I started using it. Now I find myself using it all the time. For example when I'm watching flash video, when I'm downloading something and want to monitor the progress without being at the computer, or whenever I'm playing full-screen games (you'd me amazed at how many games don't inhibit the screensaver).

Be sure to send me a link to that blog post once it's done.

---

### Post by days_of_ruin on 2009-08-27
*bump*

---

### Post by sertse on 2009-08-27
> **Nevon said:**
> 
[LIST]
[*]Support for xscreensaver
[*]Support for DPMS
[/LIST]


Sexy, Been waiting for this. Will definitely try now.

---

### Post by Nevon on 2009-08-27
> **sertse said:**
> Sexy, Been waiting for this. Will definitely try now.
Go for it! I personally have only tried it in gnome, kde and xfce. But theoretically it should work on any system that uses gnome-screensaver, kscreensaver, xscreensaver or no screensaver and just DPMS - which to my knowledge are the only screensavers out there that are widely used.

---

### Post by RiceMonster on 2009-08-27
This will be handy on my F11 laptop since it locks the screen after a while. I'm going to give this a try when I get the chance.

---

### Post by binbash on 2009-08-27
Published a blog post about it : 

[http://www.ubuntu-inside.me/2009/08/caffeine-03-is-out-with-major.html](http://www.ubuntu-inside.me/2009/08/caffeine-03-is-out-with-major.html)

BTW it is very handy software and works great on Karmic

---

### Post by Nevon on 2009-08-28
> **binbash said:**
> BTW it is very handy software and works great on Karmic

Glad to hear it, and thanks for the post!

---

### Post by LookTJ on 2009-08-28
I want to use this on my system

which tar package would you suggest I use?

thanks

---

### Post by Nevon on 2009-08-28
> **LookTJ said:**
> I want to use this on my system

which tar package would you suggest I use?

thanks

If you are running Ubuntu you should add our ppa, by doing this:
```
sudo bash -c "echo 'deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu main' >>
/etc/apt/sources.list"
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 569113AE
sudo apt-get update && sudo apt-get install caffeine
```

You can also just download a deb from [here]("https://launchpad.net/caffeine/+download"). But if you do that, you won't get any subsequent updates.

If you're running some other distribution than Ubuntu, simply download this tar file, mark the file called caffeine inside the directory caffeine_0.3/bin/ as executable, and then run that file.

More information on downloading Caffeine is available [via the Wiki]("http://www.blastfromthepast.se/caffeine/index.php?title=Downloads").

---

### Post by LookTJ on 2009-08-28
> **Nevon said:**
> If you are running Ubuntu you should add our ppa, by doing this:
```
sudo bash -c "echo 'deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu main' >>
/etc/apt/sources.list"
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 569113AE
sudo apt-get update && sudo apt-get install caffeine
```You can also just download a deb from [here]("https://launchpad.net/caffeine/+download"). But if you do that, you won't get any subsequent updates.

If you're running some other distribution than Ubuntu, simply download this tar file, mark the file called caffeine inside the directory caffeine_0.3/bin/ as executable, and then run that file.

More information on downloading Caffeine is available [via the Wiki]("http://www.blastfromthepast.se/caffeine/index.php?title=Downloads").Thanks for the link to wiki, I am attempting to make a AUR PKGBUILD, so far no success,  Hopefully the Arch people can help over at the Arch forums. 

Good day :)

---

### Post by LookTJ on 2009-08-31
For all the Arch users,

I've uploaded caffeine into the AUR.

[http://aur.archlinux.org/packages.php?ID=29762](http://aur.archlinux.org/packages.php?ID=29762)

---

