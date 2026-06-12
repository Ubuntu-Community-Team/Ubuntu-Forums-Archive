---
title: "I Can't Get Audio From YouTube With Firefox In UbuntuStudio"
date: 2016-01-02
forum: Ubuntu Studio
---

### Post by Rocky_Bennett on 2016-01-02
Hello All,
I installed my Ubuntu Studio 14.04.3 a couple of weeks ago, and I have been having fun setting it up and tweaking it and just generally playing with various aspects of it, but I can not get my Firefox to put out any audio. I do use Firefox in my Linux Mint 17.3 dual-boot, and it works perfectly there, but in Ubuntu there is audio. I use Audacious as a sound player in both Ubuntu and Linux Mint, and the Audacious in Ubuntu works perfectly, there is exactly the sound I want with no problems. I need help to get sound out of my web browser.

Thank you,
Rocky Bennett

---

### Post by Dreamer Fithp Apprentice on 2016-01-02
See if this changes things:```
sudo apt-get install browser-plugin-vlc
```

---

### Post by gdesilva on 2016-01-02
I recall having an issue with audio in firefox when jackd is running or when another audio app starting jackd. Check if jackd is running and if so disable it and try firefox again.

---

### Post by Rocky_Bennett on 2016-01-03
Thanks guys. This is what I have done since my first post, I installed Chromium, no audio. I used the command to allow browser plugin mentioned by Dreamer Fithp above, still no audio. I really would like to get audio from my browsers, any other ideas.

Thank you.

---

### Post by Dreamer Fithp Apprentice on 2016-01-03
Have you looked at
```
about:preferences#applications
```
?
You paste that in the url field like it was a web address (or you can get there through edit).
There are settings there that might possibly help.

If not, maybe pavucontrol can help. It might can tell you if firefox is generating audio and what output device it is sending it to.

=========
Looks like some good mod fixed my ommission of code tags. Thanks, whoever.

---

### Post by Rocky_Bennett on 2016-01-04
Yes, I have messed with the preferences in Firefox, but as my last post indicated this problem effects all web browsers. Because of that, I think that I am missing a plug-in or a library or something. I am very new to Ubuntu, so I do not know what the problem is.

---

### Post by Dreamer Fithp Apprentice on 2016-01-04
OK, how about trying this:

Go someplace you know there should be sound and bookmark it. Close all other tabs. Close firefox.

Now open a terminal. Type in```
firefox > ff-problems.txt
```and press enter. Leave the terminal alone. If firefox doesn't start up in the tab you bookmarked, use the barkmark to go there. Give it long enough to be sure the problem is being manifested (as opposed to, for example, the video is slow to start), then close firefox. Soon the terminal should return a prompt. Now read ff-problems.txt. You may find something obvious to you. If not, post the content of that file. If that doesn't provide a sufficient clue we can try it again routing stderr to the file as well, but I doubt that would help. Another thing to try is to see if you can get any local (on your hard drive in other words) files with audio to play. Try a variety of different file types. If your firefox menu bar isn't showing, you can right click on the tab  bar and check "Menu Bar". You can open a local file with File - "open file".

---

### Post by Rocky_Bennett on 2016-01-06
Thank you for those directions. After doing that, this is what I got in the terminal, how do I fix it?

(firefox:2573): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(firefox:2573): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(firefox:2573): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(firefox:2573): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised

---

### Post by Rocky_Bennett on 2016-01-08
I completely uninstalled my Ubuntu Studio and installed Ubuntu 15.10 instead. So if I have any issues or questions with this, I will create a new thread. Thanks guys for trying to help me.

---

