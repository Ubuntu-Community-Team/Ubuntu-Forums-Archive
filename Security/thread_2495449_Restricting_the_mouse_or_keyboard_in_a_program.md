---
title: "Restricting the mouse or keyboard in a program?"
date: 2024-02-19
forum: Security
---

### Post by Tigera on 2024-02-19
Is there a way to restrict access to the keyboard in a specific program?  For example, if I wanted to run a web page in "slideshow mode" on a desktop, such that this program and only this program cannot change the URL or click anything (just open it or close it), is there a way to do it?

I've tried firejail to do it with the following profile:

```

private-dev
blacklist /dev/input
blacklist /dev/usb

```

The program still seems to recognize the mouse and keyboard inputs, though.  I have looked at AppArmor also, but I can't figure out whether you can restrict devices there or not...

---

### Post by TheFu on 2024-02-19
The easy solution would be to keep the keyboard and mouse locked up and only have the display viewable.  This is done around the world on all those displays we see in stores, at sports events, and in hotel/business lobbies.

But it seems you want to do things the hard way. ;)

Check out **feh** for slideshows. it is a slideshow program and doesn't have any obvious controls on screen.  It has customizable keyboard controls, so you can noop all of them.  To prevent events from getting to it, you could strip down the desktop to not have any DE or any window manager. I think feh doesn't even need X11/Wayland to work.
I use feh to set my root window background. Once set, there's no input to it that isn't for other programs.  Nothing says you can't do that on a timer for a slideshow.  feh has lots of options.  To set the root windows background, I use
```
feh --bg-max "/full/path/to/image/file.jpg"
```

If course, if you run it with all keyboard controls disabled and looping indefinitely, you'll want to set a timeout so it gets killed ... or have your script look for a specific file to make it kill itself.  You'd need to ssh into the system and create that file and code of the test for existence. Not hard. You could count the number of images and kill after 100 or 500 are shown.

There is a way to setup a system in kiosk mode with a web browser.  If you disable DNS, you can limit where that browswer can get.  Or you could setup firewall rules to block the system from internet access in general.  There are "application firewalls" that take training, but you can play with those too.  I can't remember the name of the F/LOSS one, but it is mirrored after a popular MacOS application firewall .... opensnitch or freesnitch?  Something like that.  I always found the training of it too be too much trouble.

Doubt this is helpful, but options might get you thinking different.

---

### Post by Tigera on 2024-02-23
That's a good idea.  Unfortunately, it's not quite what I want.  I'm trying to do a multi-seat setup where each mouse is constrained to its own window.  I've got the output working (via kwin_wayland), now I just need to get the input working.  If I can find a way to "reject" the input from specified mice/keyboards, I should have what I need.

---

### Post by TheFu on 2024-02-24
There are multi-seat distros. They are per X/Server, not per Window, however.

---

### Post by dragonfly41 on 2024-02-25
In last few days I have used Input Remapper (in repo) to disable mouse clickthrough on mouse scroll button. From what I see in GUI it can be applied to keyboard and mouse functions and other devices. I found it in a thread of discussion.

---

