---
title: "Linux is amazing and blows my mind..."
date: 2009-01-21
forum: Testimonials &amp; Experiences
---

### Post by cacycleworks on 2009-01-21
Wow!

I will never cease to be amazed at what can be done in Linux / ubuntu / what-have-u. The attachment shows my latest silly trick: running graphical X programs from my server at the office on my laptop at home!

Setup:
kubuntu 8.04 laptop at home (where I made a id_dsa.pub file)
(home has cable modem)
(work has cable modem)
(router at work has port 22 routed to my server)
ubuntu 7.10 "headless" server at work (i call it bus) (with the id_dsa.pub from home pasted in to ~/.ssh/authorized_keys2 )

At home you can run a command like:
ssh -X bus xterm 

And viola, an xterm window from the work server pops up and I have a command prompt from that machine with secure access to the local network at the office.

Ok, so then I start thinking and on the work server, I do a minimum xfce4 install. I use aptitude to install programs so I see how many other apps it wants to install. It didn't look too crazy, so I went for it. And then I started playing! :D

So check it out: at the top of the desktop is a black looking taskbar. It is running from my server at work, so anything I run from its applications menu launches from work but is shown here! This is identical to how an x-terminal works, only I've got the full power of my "local" laptop and its desktop coupled with the usability of work access.

Interesting observations:
    * Some X apps just don't work remotely.
    * The xfce panel shows all applications running on the current screen, those from work and those local.
    * xfce4-panel has the "net" and "load" plugins towards the right (that what the colors are)
    * The Applications menu launches programs from the work server (or tries to...)
    * There is an interesting mixture of "desktop things" that do or do not work. I used the xfce window configurator to mess with the fonts and color schemes (the dark is from xfce-dusk) and some options said "Not allowed with current window manager: KWin". Trippy.
    * You can easily "alias" your work's IP address to a friendly name like "hell", work, armpit, ***, or whatever by editing your /etc/hosts file. 
    * You can also alias lots of different names to the same IP address. I use this for website development on my work server ... it has virtual hosts set up and run different www directories depending on what hostname I use.
    * Frequently, I will launch konqueror from a remote location to get access to that location's router so I can change configurations.
    * This is too cool.


SSH is amazing and powerful... 
    * anything done by ssh is encrypted.
    * you can just "ssh into" a host to get a command line.
    * you can "scp" files to/from a host.
    * you can use sshfs to mount a remote host's filesystem on your local computer, so you won't need to ftp files around anymore.
    * ssh has the id_dsa identity method which can allow for password-less signing on.
    * and ssh -X lets you run those X apps from a remote host.

I had all kinds of unix experience in college some 12+ years ago, but was a "power windows user" until about 2 years ago. Now I can't even imagine crippling myself in windows-land again! 

Hopefully, this little post can help others with their work flow -- or impress others with how awesome linux and ubuntu are.

:) Chris

---

### Post by Rocket2DMn on 2009-01-21
Moved to Ubuntu Testimonials & Experiences - glad you're still loving Ubuntu!

---

### Post by wolfen69 on 2009-01-21
that's awesome. linux really is amazing what you can do. keep up the good work.

---

### Post by Crafty Kisses on 2009-01-21
Good stuff my man, glad your liking it.

---

