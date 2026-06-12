---
title: "Typewriter Server"
date: 2013-10-26
forum: Server Platforms
---

### Post by gabrielfcampbell on 2013-10-26
Hello Everyone,

I have installed Ubuntu Server on an old laptop of mine to turn it into an electronic typewriter. Basically it can just do text editing in nano and then save my files on the cloud in dropbox. I followed this tutorial:

[http://www.pcworld.com/article/259236/how_to_turn_your_laptop_into_a_typewriter.html](http://www.pcworld.com/article/259236/how_to_turn_your_laptop_into_a_typewriter.html)

I have finished the tutorial but there are a few nagging issues.

First, in nano:

I would like to be able to use smooth scrolling to scroll one line at a time while editing my writing, but instead it scrolls by paragraph. The -S in the command line prompt while opening the file (nano -S file.txt) does not seem to work
Also, the files I import from dropbox and read and edit in nano replace all the single and double quotes with white boxes. Can I fix this (other than by going through and replacing them all)?
Also, I would like to narrow the columns in the file while viewing it. Each line is currently 180 character wide (from edge to edge of the monitor) but I would like it to be about half that or even less (-r90, or any other number, does not seem to do anything).

Second, for my wireless:

I connected to my WPA network during installation, and it shows it on the networking interfaces file, and it works, but only after a LONG wait. I have to wait about 1 or 2 hours after having turned the computer on before it decides to actually connect to the internet. It just happens suddenly. It will be disconnected for hours and then, all of the sudden, the wifi light will turn on and my other computer (desktop) with my dropbox open will say that new files from the old laptop have been uploaded. Any idea how to fix this?
Also, I would like to know how to setup up the laptop so that it can connect to the internet in multiple places. Can i simply change the ssid and psk values in the /etc/network/interfaces file to the new network? 

Thanks for any help you can provide.

Also, sorry if this is the wrong sub-forum, but I am using the server OS (32 bit 12.04).

The network interfaces file looks like this:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

iface wlan0 inet6 auto
        wpa-ssid MYNETWORKSSID
        wpa-psk MYPASSWORD

---

### Post by TheFu on 2013-10-27
Can't help with the wifi, but I think an explanation of the other issue.

nano is a minimal editor. It doesn't know about lines on the screen, just where the end-of-line characters are. If that/those characters are beyond whatever width is set for the terminal, then i guess nano will "wrap" the line for you. I don't know, since removing nano is the very first command I run on any new Linux system.  I can't say which character or characters are used for end-of-line - MS-Dos uses CRLF and most UNIX-like systems are just LF.  An "editor" should always honor that split - it is a word processor that will behave more like expected.

Or I could be misunderstanding the question completely.

Anyway, best to ask 1 question per thread so the replies are focused.

---

### Post by SeijiSensei on 2013-10-28
Nano is a good editor for beginners, but as TheFu suggests, it has its limitations.  (It was originally designed as the mail composition program for the Pine mail client, now available as "alpine.")

I learned [emacs]("http://www.gnu.org/software/emacs/") syntax a long time ago and continue to use an emacs clone called **[jed](http://www.jedsoft.org)** which is in the Ubuntu repositories.  It also includes menus, though once you start remembering the Control-key sequences, you won't use the menus very much.  Unlike nano, it is not line oriented.  Texts stream endlessly until you type a return.  You can wrap lines as well, of course.

I've never liked vi/vim.

Here's another option you might consider.  If you were to install a lightweight desktop environment on the server like xubuntu-desktop, you could use a graphical editor like gedit.  That would also let you use the server remotely.  If you run openssh-server, you can connect to it from other machines with "ssh -X", then run gedit on the server and have the window appear on your remote desktop.  [XRDP]("http://www.xrdp.org/") sessions are another option.

I'd hook up a dot-matrix printer while you're at it! :D

---

### Post by coldraven on 2013-10-28
> i'd hook up a dot-matrix printer while you're at it! :grin:
lol

---

### Post by Lars Noodén on 2013-10-29
If you want to go to the other end of the spectrum from nano, you could use LaTeX and do your own typesetting.  I've never used it but have known quite a few people that did their dissertations and subsequent scholarly publishing using LaTeX or a variant.  I suppose you could use LaTeX in either nano or Emacs.  But if you use Emacs you could get distracted with mail and dozens of other things.

---

### Post by gabrielfcampbell on 2013-10-29
Hi again,

Thanks for the replies. I fixed the problems with nano mostly, but the wireless still takes a long time to connect and I'm not sure how to connect it to routers other than the one I installed it on.

---

