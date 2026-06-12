---
title: "Ubuntu hasn't felt geeky for years- ASCII X Server?"
date: 2010-09-17
forum: The Cafe
---

### Post by murderslastcrow on 2010-09-17
I haven't felt geeky since I started using Linux with 8.10. Like, seriously, the geekiest thing I've ever done is install encrypted DVD playback, or download a PGP key. Other than that it's all simple as all get out. I hate how productive I am- it's WRONG!

Therefore, I'm wondering if there's any way to get X to run in ASCII mode. Kinda' like how mplayer has an ASCII mode you can run from a terminal to watch videos, I'd like something like that for the whole desktop, even if it requires a super-high resolution to be somewhat readable. I don't care, I don't need words to run my music player, I just want to look geeky for a day. T3T just once, without the need for Gentoo, please.

*hopes, as Google hasn't found him anything*

---

### Post by v1ad on 2010-09-17
pianobar -- for pandora  [http://ubuntuforums.org/showthread.php?t=1533357](http://ubuntuforums.org/showthread.php?t=1533357)
web browsers -- lynx, w3m, links, elinks
conky -- if you really wan't to feel geeky,and configure it to your liking.

also do cntrl f1, and do some of this stuff in console :] you can minimize and maximize using screen. screen is a great program, allows you do drop shell programs into the background.

---

### Post by cj.surrusco on 2010-09-17
Maybe you could try spending an entire day using just the command line? That might be fun and it sure would reduce your productivity! ;)

Try elinks for a web browser.

---

### Post by NCLI on 2010-09-17
I don't think there is an "ASCII X server", since the entire point of the X server is to render a graphical work environment. Just install a few CLI apps and press ctrl+alt+F1.

---

### Post by murderslastcrow on 2010-09-17
Ah yes, there was one day where I just used the command line for everything. It was kind of hilarious.

I mean something that renders the GUI into ASCII, though, which would be far more inefficient than a terminal. But lol, okay, I'll get lynx again, anyway. XD

Um, is Pithos just a frontend for pianobar? Either way, totally doing that, too. Maybe I should get a terminal on my EVO as well.

---

### Post by v1ad on 2010-09-17
reason i use pianobar for pandora is because it does not require flash, and no adds. a lot less cpu usage. and yes it is just a front end.

---

### Post by tgalati4 on 2010-09-17
For playing music:

sudo apt-get install moc
mocp

For anything else ascii:

apt-cache search ascii

Some interesting items from that list:

aa3d - ASCII art stereogram generator
aajm - ascii art version of jugglemaster

aview - A high quality ASCII art image viewer and video player

(And that is just the "a"'s)

That will keep you busy for a while.

Use screen to get multiple ascii windows.  No real need for an X server in ascii.

---

### Post by AlphaLexman on 2010-09-17
I enjoy 'fbi' when I need to feel geeky, you can look at jpg's from a real terminal!

---

### Post by tgm4883 on 2010-09-17
Start developing. That can be geeky

---

### Post by Bachstelze on 2010-09-17
> **murderslastcrow said:**
> I haven't felt geeky since I started using Linux with 8.10. Like, seriously, the geekiest thing I've ever done is install encrypted DVD playback, or download a PGP key. Other than that it's all simple as all get out. I hate how productive I am- it's WRONG!


Ubuntu is not an epenis enlargement product. Go do something meaningful, like coding work.

---

### Post by Dustin2128 on 2010-09-17
> **Bachstelze said:**
> Ubuntu is not an epenis enlargement product. Go do something meaningful, like coding work.
Ubuntu forums is not 4chan. There's nothing wrong with experimenting around in the terminal, or learning more about it. Go do something meaningful, like trolling another site.

Anyway, you could test out awesome wm or ratpoison. Both have high levels of terminal integration while still being more awesome than the a plain terminal (in terms of geek cred too!), having used all 3.

---

### Post by nerdopolis on 2010-09-17
it seems mplayer can render video in ASCII
[http://joesteiger.com/2010/06/17/watch-video-in-the-terminal-ubuntu-10-04/](http://joesteiger.com/2010/06/17/watch-video-in-the-terminal-ubuntu-10-04/)

I don't know if the same can be done to an xserver
It probably wont be easy...

---

### Post by cammin on 2010-09-17
[http://www.meow.org.uk/stan/xserver/](http://www.meow.org.uk/stan/xserver/)

---

### Post by DemonBob on 2010-09-17
> **Dustin2128 said:**
> Ubuntu forums is not 4chan. There's nothing wrong with experimenting around in the terminal, or learning more about it. Go do something meaningful, like trolling another site.

Anyway, you could test out awesome wm or ratpoison. Both have high levels of terminal integration while still being more awesome than the a plain terminal (in terms of geek cred too!), having used all 3.

Second on the awesome wm. I just started using it a few weeks ago. I LOVE IT.

---

### Post by tgalati4 on 2010-09-17
Did anyone notice that the ascii X server was running on a Libretto?  Now that's both retro and cool.

---

### Post by andrew.46 on 2010-09-18
Hi nerdopolis,

> **nerdopolis said:**
> it seems mplayer can render video in ASCII...

Pick up a more recent version and try *-vo matrixview* :)

Andrew

---

### Post by Spice Weasel on 2010-09-18
**Step 1.** Install elinks, centerim, irssi and any other program you need (Music players, etc.)
**Step 2.** apt-get remove xorg gdm. You won't need the sudo, I'm sure, because you'll be using the [root account]("http://www.garyshood.com/root/").
**Step 3.** [Textmode Quake]("http://webpages.mr.net/bobz/ttyquake/").
**Step 4.** Watch [ASCII Star Wars]("http://geekswithblogs.net/btinkler/archive/2005/03/21/26915.aspx") through telnet.
**Step 5.** Sit back and rejoice in your awesomeness and manlyness.
**Step 6. **If you really need X11, try installing ratpoison or wm2. Don't forget to remove GDM and edit the xinitrc to open the WM of your choice.

---

### Post by Dustin2128 on 2010-09-19
> **Spice Weasel said:**
> 
**Step 4.** Watch [ASCII Star Wars]("http://geekswithblogs.net/btinkler/archive/2005/03/21/26915.aspx") through telnet.

Han shot first.

---

### Post by murderslastcrow on 2010-09-20
Lol, even after restating what I was looking for people just kept talking about viewing jpegs and videos in the terminal. But yeah, I guess that would mean rendering the entire desktop in ASCII doesn't exist (yet). And, as I do code, perhaps I should code that? XD

Thanks for your contributions, but I think you guys just reminded me of how geeky I can be sometimes. In the field of multimedia design, it's nice to get inside once in a while, lol.

---

### Post by Windows Nerd on 2010-09-20
> **DemonBob said:**
> Second on the awesome wm. I just started using it a few weeks ago. I LOVE IT.
<thread hijack>Don't want to start a new thread for this- I have been looking at a tiling window manager for some time now (from my current minimalist openbox desktop). Do you feel like awesome organizes your windows very well? Does it do it in a logical way? Unfortunately I know little about tiling window managers (having never used one other than the default TWM from Xorg for, like 20 seconds when I was testing if X was working on my Arch install). 
</thread hijack>

---

### Post by bwhite82 on 2010-09-20
Give straight-razor shaving a try.

[http://artofmanliness.com/2009/10/06/how-to-straight-razor-shave/](http://artofmanliness.com/2009/10/06/how-to-straight-razor-shave/)

Edit: random? yes.

---

### Post by DemonBob on 2010-09-20
> **Windows Nerd said:**
> <thread hijack>Don't want to start a new thread for this- I have been looking at a tiling window manager for some time now (from my current minimalist openbox desktop). Do you feel like awesome organizes your windows very well? Does it do it in a logical way? Unfortunately I know little about tiling window managers (having never used one other than the default TWM from Xorg for, like 20 seconds when I was testing if X was working on my Arch install). 
</thread hijack>

With awesomewm you have a config file called rc.lua. This file allows you to configure the tiling layout (9 to chose from) across 9 different tags. You can also tie certain programs to certain tags, and layouts to tags. Tiling window managers are heavily keyboard based. The only time i use a mouse now is browsing the internet. Other then that, i can do everything with the keyboard. It's helped my productivity alot.

If you want to know more, start a new thread, or PM me so we don't hijack anymore.

---

### Post by mamamia88 on 2010-09-20
That's what I love about ubuntu. It is super easy to use and I really don't have to think when using my computer.  But when I feel like it I can get down and dirty because it's base is still linux

---

