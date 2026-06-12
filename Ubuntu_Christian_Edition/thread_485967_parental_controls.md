---
title: "parental controls"
date: 2007-06-27
forum: Ubuntu Christian Edition
---

### Post by grendelkhan on 2007-06-27
Has anyone been able to get a keystroke logger to work with a USB keyboard?  It's the one thing on my son's computer I'm missing from Windows.  I've been searching for a week now and can't find anything.

I'm using the firehol / tinyproxy / dansguardian solution to filter things, but we need to keep an eye on other things that my son is doing online.

---

### Post by HunkirDowne on 2007-07-01
> **grendelkhan said:**
> Has anyone been able to get a keystroke logger to work with a USB keyboard?  It's the one thing on my son's computer I'm missing from Windows.  I've been searching for a week now and can't find anything.

I'm using the firehol / tinyproxy / dansguardian solution to filter things, but we need to keep an eye on other things that my son is doing online.

You do know you can check the access logs don't you?  I've taken these to a spreadsheet and with some parsing turned it into HTML code so I could view sites I didn't recognize.

/var/log/dansguardian/access.log[.n] where "n" is the backup number.

---

### Post by grendelkhan on 2007-07-02
Yeah, that's easy, watching the email sex between him and some "girl" in texas, is much harder without a password.

---

### Post by HunkirDowne on 2007-07-02
Well, searching for "Linux Keylogger" (sans caps and quotes) in Google was a bit frustrating -- I'm sure you've been there.  I don't know if any of the few on there work with USB, though.

I'm pretty good with standalone computing in general.  Networking I'm rather new at.  But I wonder if it's possible to use a proxy of some kind that would record keystrokes as they pass through.  I guess if it were that easy...

/grasping at straws

---

### Post by mysticrider92 on 2007-07-02
I also Googled key loggers, and none specifically supported USB, but I am fairly sure (not positive) that with the way Linux is set up, any keyboard communication, whether USB or Mini-DIN, would all probably go through the same port. So if that guess is right, any keylogger should work with the USB, just because of the way the kernel is communicating with other applications and the keyboard. This is just a guess, I don't know if it will work, so correct me if i'm wrong.

---

### Post by grendelkhan on 2007-07-03
lkl and uberlogger all monitor the hardware keyboard port - which the computer my son is on (my laptop) doesn't have.

we've made the decision that we're going to have to go with a hardware logger, there's nothing out there that really does what we need.

---

### Post by mysticrider92 on 2007-07-03
I was saying that to Linux a keyboard connected to a USB port might be recognized the same as a PS/2 keyboard. I am not sure if this is true, but with the way some things work in Linux, it could well be.

The hardware logger would probably be easier anyway, although a bit more obvious.

---

### Post by dragonfyre13 on 2008-10-25
I worked on a project a while ago called pykeylogger. It's a python based keylogger, specifically windows based. I did the conversion on it to Linux, by using the python-xlib bindings, and capturing it at the xwindows layer instead of the hardware layer. If for some reason he's switching to a virtual terminal to browse the internet (I'll garantee he's not) it won't work, but otherwise it will capture everything.

I believe it's on sourceforge still.

---

