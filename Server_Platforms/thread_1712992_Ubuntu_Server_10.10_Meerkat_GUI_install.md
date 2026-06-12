---
title: "Ubuntu Server 10.10 Meerkat GUI install"
date: 2011-03-23
forum: Server Platforms
---

### Post by Doeydude on 2011-03-23
Hi There

As I'm sure you are sick of hearing, I'm a noobee to Ubuntu Server. I have used desktop on and off over the past decade and find it relatively easy to get around. However I have to use a GUI. I prefer Gnome but KDE is just fine. I am not comfortable at all when using Terminal.

Anyway. I have installed 10.10 server, a number of times, on to a machine. I thought that it was some option that I was over looking, during setup, that wasn't loading Gnome for me. I eventually realised that it was not supposed to install during the server setup, but had to be added later.

So I have come across many sites that explain how to do this. But I keep getting the same error. Let me explain.

I enter the following after logging in and it asks me to put the install disk into the drive.

*sudo apt-get update  * 

After a few seconds I am able to enter

*sudo apt-get install ubuntu-desktop*

However, I get the following error

*E: unable to locate package ubuntu-desktop*

From this I am gathering that it is looking for the Gnome desktop from the disk. Even though I read that it needs to be downloaded from the internet. I have also tested for a broadband connection by pinging a website and I am getting correct results.

Is there a way to force it to look for the files online (if that's what I'm supposed to be doing) or is there another disk I can download and use?

Doey

---

### Post by arrrghhh on 2011-03-23
Just install Ubuntu Desktop.

There's no point in running the server distro if you're just going to put a full GUI on top of it - you can run _all_ of the same services on Desktop as you can on Server... So if you need/want a GUI, stick to the desktop edition.  Server edition is made to be lean and mean, with minimal packages installed so updates are easier - you obviously don't want that, so there's no point for you to run the Server edition.  Thanks.

---

### Post by iconoclast hero on 2011-03-23
I hear you on just using desktop, unfortunately, I don't have enough RAM so I opted for server (desktop just hangs with the wallpaper and top bar after booting).  I am trying to do the same thing (get GUI on top of server) because I would really like to set this up to sit in a corner and play music into my stereo from a network location and occasionally go in via VNC to change things up.

As in the initial post, I am getting E: Unable to locate package ubuntu-desktop and I can ping google.

---

### Post by arrrghhh on 2011-03-23
> **iconoclast hero said:**
> I hear you on just using desktop, unfortunately, I don't have enough RAM so I opted for server (desktop just hangs with the wallpaper and top bar after booting).  I am trying to do the same thing (get GUI on top of server) because I would really like to set this up to sit in a corner and play music into my stereo from a network location and occasionally go in via VNC to change things up.

As in the initial post, I am getting E: Unable to locate package ubuntu-desktop and I can ping google.

My server plays music just fine with no GUI - MPD :D.

If you don't have enough RAM, that seems like a really good reason to not have/use a GUI...

Especially if the desktop version hangs, installing the ubuntu-desktop package is just asking for trouble.

---

### Post by iconoclast hero on 2011-03-23
Ok, so how do I download and install MPD?  If I am getting the error that it can't locate the ubuntu-desktop package, why would I expect anything different with MPD?

---

### Post by arrrghhh on 2011-03-23
> **iconoclast hero said:**
> Ok, so how do I download and install MPD?  If I am getting the error that it can't locate the ubuntu-desktop package, why would I expect anything different with MPD?

mpd is music player daemon - I was just saying you don't need a GUI to play music, there's CLI-based methods/applications that play music...

---

### Post by cariboo on 2011-03-23
If you don't have the ram to run the ubuntu-desktop on your server, trying to add it later will still run into problems, as the system will use all the ram to run the gui, and probably run into swap if you try to run something else. If you really need a desktop gui, have a look at something lighter weight like the lubuntu desktop, or the gnome-desktop-environment. They are both in the repositories.

---

### Post by Doeydude on 2011-03-23
> **cariboo907 said:**
> If you don't have the ram to run the ubuntu-desktop on your server, trying to add it later will still run into problems, as the system will use all the ram to run the gui, and probably run into swap if you try to run something else. If you really need a desktop gui, have a look at something lighter weight like the lubuntu desktop, or the gnome-desktop-environment. They are both in the repositories.

I would gladly try either of these GUI's but it brings me back to my question. How do I get them to install. I am getting an error as stated earlier even after following all the recommended instructions.

---

### Post by arrrghhh on 2011-03-23
> **Doeydude said:**
> I would gladly try either of these GUI's but it brings me back to my question. How do I get them to install. I am getting an error as stated earlier even after following all the recommended instructions.

Please see my post.

Don't try to fit a square peg into a round hole - if you want a GUI, install/use Ubuntu Desktop - don't install Server and then put the ubuntu-desktop package on top of it, that defeats the entire purpose of the server distro - and is literally pointless, as you'd get all the same packages as if you just started with Ubuntu Desktop in the first place ;).

---

### Post by cariboo on 2011-03-24
> **Doeydude said:**
> I would gladly try either of these GUI's but it brings me back to my question. How do I get them to install. I am getting an error as stated earlier even after following all the recommended instructions.

Make sure there aren't any repositories commented out in /etc/apt/sources.list, then run:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

then try to install lubuntu-desktop

---

### Post by arrrghhh on 2011-03-24
> **cariboo907 said:**
> Make sure there aren't any repositories commented out in /etc/apt/sources.list, then run:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

then try to install lubuntu-desktop

Remember, aptitude isn't installed by default anymore so that might fail for him... Assuming it's a fresh install of 10.10, which it would seem like it is...

---

### Post by cariboo on 2011-03-24
It is only on the desktop install that aptitude isn't installed by default, if you use the server iso or the alternate install iso, aptitude gets installed by default.

---

### Post by arrrghhh on 2011-03-24
> **cariboo907 said:**
> It is only on the desktop install that aptitude isn't installed by default, if you use the server iso or the alternate install iso, aptitude gets installed by default.

Ah, my apologies.  I don't remember if I tested that on my vm testing of the server edition...  Thanks!

---

