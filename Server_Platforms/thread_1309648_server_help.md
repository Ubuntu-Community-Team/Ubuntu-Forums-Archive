---
title: "server help"
date: 2009-11-01
forum: Server Platforms
---

### Post by themoddingden on 2009-11-01
Hi;
I'm setting up a server for my website.
I could use some help.
I live in Quebec is there anyone around that could ,
be a guide for me /help me .
I have it up for working on it at times.
I have ksplice in.
I can't mount flash drive anymore(it's seen but can't mount it).
 i would like to be able to ftp into the www dir and edit files.
I have ssh in and working and freenx.
It's headless.
I may want top setup my mail server as well.
this is for a mid to small site serving html and css pages,
I choose not to do cms thing .
I symlinked the www to my account home dir.
I will when it's setup the way I want it will change my account to a limited account with just read /write to that dir.
any help would be great

---

### Post by HermanAB on 2009-11-01
Howdy, I'm 2 hours west. 

What problems do you have?  Since you have SSH up, it seems like you are pretty much going already.

Regarding USB drives, the automounter may be confused.  Delete the two hidden files in /media to fix it.

You can of course mount USB drives manually:
$ dmesg
will tell you what you plugged in, then do:
$ sudo mkdir /mnt/usb
$ sudo mount /dev/sdxx /mnt/usb

---

### Post by themoddingden on 2009-11-02
Hi;
Ok heres what I want to do.
I want to be able to ftp right into my www dir.
when i install vsftp or pro it makes a new dir outside the home dir in ubuntu(not what i want at all).
This is to help me upload webpages files etc.
I want to be able to mount my www in my webmasters account as well.
and let him upload content and edit.
He lives 4 hours away so you can see how this would help.
ssh was freaking easy to setup and once i found the guide to symlink the www dir to my home dir that was great.
the other thing is email is a b but i have gmail(for the site) for that so why even do it .
the only other thing would be putting my domain name in.
while using dd-client.

---

