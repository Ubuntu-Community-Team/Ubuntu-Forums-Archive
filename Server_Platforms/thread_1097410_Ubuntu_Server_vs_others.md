---
title: "Ubuntu Server vs others"
date: 2009-03-15
forum: Server Platforms
---

### Post by Xeoncross on 2009-03-15
I know that topic title probably makes some people sick - so sorry for bring it back to life. 

Anyway, I love using Ubuntu Desktop as it make it so easy for someone with a M$ background like me to get into the swing of things. However, after speeding a whole week learning as much as I could I had to drop the system because I was spending all my time learning and no time actually getting things done. That was about 2 months ago.

I'm back, but this time I need to learn how to manage a server with a linux distro. No GUI. So this brings up the question as to whether Ubuntu server is as good as the other distros like Fedora. I know Ubuntu rocks on the desktop - but what about servers?

So to answer that I figured that I would ask two questions that should let me know.

Is the number of documentation articles (and quality) as good as another more business styled linux when it comes to webservers?
[COLOR="Silver"](I have a lot to learn!)[/COLOR]

Is the package count as high as the other distros? I remember reading some distros have as many as 20,000 packages supported?
[COLOR="Silver"](I can't be held back by missing packages)[/COLOR]

[COLOR="Silver"]
P.S. Whether I use Ubuntu for the server or not- it's still my desktop choice. ;)[/COLOR]

---

### Post by askreet on 2009-03-16
First of all, if you're going with command-line linux distros, I wouldn't even consider Fedora.  Realistic choices are (IMPO, of course):  Ubuntu Server,  CentOS,  RHEL ($) and Gentoo (Time)

As far as documentation goes:
- Google.  How-tos are your friend.  I've learned everything I know from starting here.  If someone else has done it, you can learn a lot from them.  Chances are anything you're trying to do has been done by someone using any of the OSes above.

- Man pages.  These are the same on any (decent) Linux distro.

I work for a company that uses a mix of CentOS and Ubuntu Server.  I have my complaints and praises about both, but at the end of the day it's all minor stuff.

Hope this helps!

---

### Post by askreet on 2009-03-16
Also, as far as package count goes.  Yes, it's very high.  Most everything is available for Debian, so almost all packagers will re-pack an Ubuntu package too, since it's based on the same stuff =)

---

### Post by mrsteveman1 on 2009-03-16
I manage a few servers day to day for a mid size commercial website, we have hosted it on CentOS in the past but I didn't like managing it at all, so we switched a few months ago to Ubuntu and i much prefer it. For one thing, Apt is the best packaging system i've ever used on any of them, and that helps sometimes. Also a lot of the desktop support applies to the server, they are nearly identical save for the kernel package.

---

### Post by bodhi.zazen on 2009-03-16
To be honest, under the hood, once you get to the command line, a server is a server.

I suggest you start by learning basic commands, how to use the man pages, and how to use an editor (vim ftw !!!).

Also take a look at ssh + screen.

There are several web interfaces as well, such as webmin.

Last I suggest you plan the transition. Yes you will have a lot of learning in the few 3-6 months and that needs to be "built - in" to your transition plan.

See also :

[https://help.ubuntu.com/8.04/switching/index.html](https://help.ubuntu.com/8.04/switching/index.html)

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by buldozerceto on 2009-03-16
My suggestion for servers is: Centos, Rhel, Debian.

---

### Post by mrsteveman1 on 2009-03-16
A lot of things are similar, but you will run into differences sooner or later, and sometimes those differences get in the way. These distros all keep some files in different places for some reason, almost all of them use different structure for apaches configuration files, some of them use a different log format.

For one of the most annoying examples, a few years ago when i was using VMware server on Gentoo, the installer refused to complete because it wanted to know where the rc0.d-rc6.d directories were, and Gentoo didn't have any. There was an ebuild at some point but not then.

---

### Post by Xeoncross on 2009-03-16
Thank you for all the feed back. First, I keep hearing about CentOS so that might be something to look into. Second, I guess that bodhi is mostly right - a server is a server. I love the Ubuntu system so as long as you guys don't think I am shooting myself in the foot - I might as well use it on my server too! :D

Oh, and if anyone has time:

How do I change the cmd line to a white background and black text. From a typography stand point - that white text on a black background is awful. I'd probably be wearing glasses in a few months after looking at that thing. I messed around with the .bash_profile but I can't do more than change the text color.

Oh, and how do you use commands in vim? Like ":q" is supposed to quit - but sadly, I just can't figure out how to make it work. do you have to type something else before it or hold down a certain key while you type?

---

### Post by bodhi.zazen on 2009-03-16
Just search on colorizing bash :twisted:

[http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html#AEN341](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html#AEN341)

Although there are better sites.

---

### Post by schettj on 2009-03-16
> **Xeoncross said:**
> Thank you for all the feed back. First, I keep hearing about CentOS so that might be something to look into. Second, I guess that bodhi is mostly right - a server is a server. I love the Ubuntu system so as long as you guys don't think I am shooting myself in the foot - I might as well use it on my server too! :D

I use CentOS on headless servers. It's RHEL w/o RedHat support. If you *must* be more current then that, then Ubuntu server is fine.
> 
Oh, and how do you use commands in vim? Like ":q" is supposed to quit - but sadly, I just can't figure out how to make it work. do you have to type something else before it or hold down a certain key while you type?

Basic VI
press i key to go into insert mode. Press escape key to exit insert mode. press : key to enter command mode

So, if you were in insert mode, you would need to press esc, then press :,. then q, then the return key.
The typical I am done editing this file mojo is 
esc:wq<ret> 
esc - get out of insert mode
: - HEY VI, I have a command for you!
w - write the file
q - quit
<ret> - please do all those commands now, thanks ;)

Welcome to 1971. Enjoy the CLI.

PS: when you start to do everything and even think in emacs, then you'll know you've hit rock bottom.

---

### Post by MrWES on 2009-03-16
so it's really :q = quit :)

---

### Post by bodhi.zazen on 2009-03-16
Also, for vi, you might prefer vim

```
sudo apt-get install vim-full
```

---

### Post by HermanAB on 2009-03-17
If you want a point-and-click server similar to Windows 2003, then you should use Mandriva or Suse.  These two distributions are very mature and their wizards can do absolutely anything with a few mouse clicks.  

I like Mandriva best since it allows you to use a wizard to set things up and still edit the resulting configuration files without screwing things up - so you can actually learn from the wizards.  Suse doesn't allows a user to edit the files by hand - well it does, but it will overwrite any user changes the next time you run the wizard which I find rather annoying.

If you are wondering, I use Mandriva for work and Ubuntu for fun.

Cheers,

Herman

---

### Post by askreet on 2009-03-17
I use nano, and get made fun of for it constantly at work.  You might like it too.  It's installed in Ubuntu by default.

Also, don't mess with the colors of the bash profile, etc.  You'll probably be connecting to your server via SSH anyway, just change the colors of the terminal application you're using =)

- askreet.

---

### Post by Xeoncross on 2009-03-17
> **schettj said:**
> Basic VI - press i key to go into insert mode. Press escape key to exit insert mode. press : key to enter command mode

Welcome to 1971. Enjoy the CLI.

Why couldn't all the pages I read just say that?! I must have looked over 10 articles that listed the commands for everything - but no instructions on the whole "there are three modes in the editor". Thanks so much, I have just been using nano because I couldn't figure it out (and nano gives the commands at the bottom which is helpful).

Still this whole "different modes" think could really be handy...

Thanks for the link again bodhi, however, I am having a hard time digesting some of that. That was actually one of the pages I looked at when I was trying to figure this thing out. I have the SSH prompt changed over to a better font and a white background with black text - but the bash_profile or whatever on the server is still causing the actual text returned to be white on a black background.

Herman, thanks for the info on Mandriva & Suse. However, I won't be using any sort of GUI for this system - which is one of the reasons I was questioning Ubuntu (i.e. Ubuntu has a great GUI but can it perform as well.) as I will just run a webserver on a VPS.

---

### Post by HermanAB on 2009-03-17
BTW, SSH can do X forwarding, meaning that you don't need X on the server, only on the client.  So you can use any X editor on the server (once you installed it anyway!).  Try this:
$ sudo ssh user@server "gedit /etc/fstab"

You can install all of Gnome on the server (but leave the server in runlevel 3 with no X) and do this:
$ ssh user@server gnome-panel

and go click happy!
(drag the distant tool bars to the sides of the screen to keep your wits together about it.)

Cheers,

Herman

---

### Post by Xeoncross on 2009-03-18
> **HermanAB said:**
> BTW, SSH can do X forwarding, meaning that you don't need X on the server, only on the client.

Hmmm.... So does that mean I can setup a client editor on Ubuntu Deaktop or Windows that will receive and send text files over SSH instead of having to use the small terminal with vim or nano on the server? Like how you can set textmate to edit files on the mac?

My favorite editor is SciTE as it has the best PHP highlighting of any editor - next is eclipse for larger projects...

---

