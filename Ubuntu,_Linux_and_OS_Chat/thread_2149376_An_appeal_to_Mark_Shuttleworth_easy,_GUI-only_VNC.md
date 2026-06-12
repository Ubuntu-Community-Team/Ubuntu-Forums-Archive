---
title: "An appeal to Mark Shuttleworth: easy, GUI-only VNC"
date: 2013-05-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Bill Tetzeli on 2013-05-28
Last summer I made the full switch to Ubuntu Linux, and this year I retired my Windows partition for good.  Canonical has taken the fear out of switching for people like me, who would rather spend time using a computer than configuring it.  And yet after the Windows 8 debacle, I'm wary of putting all my eggs into one digital basket, even a basket as large as the Ubuntu distro family.  Although currently I've been able to set up x11vnc to run before login and connect to it with an SSH public/private key pair over Remmina, regardless of which Ubuntu-based distro I'm using, I don't know what the future holds as Ubuntu replaces lightdm with Mir and the rest of the Ubuntu flock start using Wayland (currently my VNC setup is lightdm-dependent; e.g., I wasn't able to get it working in Mint until I installed lightdm and set it as the default display manager).  Even now I'm unable to get vino-server to start in Ubuntu 13.04 [the way I was up till Ubuntu 12.10]("http://jakeyoon.com/2008/11/19/enable-vino-vnc-server-for-login-manager-gdm-in-ubuntu/").  And while I'm comfortable with some distros outside the Ubuntu fold, e.g. OpenSUSE and Fedora, I've lost untold nights of sleep and practically gone blind googling ways to set up a VNC that works on them.  Ergo, my appeal to Mark Shuttleworth is as follows:

1. You and Canonical have set out on a strategy to create what is inarguably the most user-friendly version of Linux ever, as a means or "loss leader" for selling related services and devices.  It seems to be working.  I've already bought a System 76 Pangolin Performance and am taking a hard look at the new Asus thin device (since you're advertising it on your homepage, I presume (and hope) this is something you're actually making money off of, not just Asus).  Congratulations and, especially, thank you!

2. This success is presumably contingent on continuing the progress on usability (here defined as "the less command line and googling necessary to make something work, the better").

Therefore

3. I would appeal to you and Canonical to make VNC networking as easy as you've made wireless networking, peripherals (mouse, speakers, etc.), printer support.  In my mind that would entail the following:

- a VNC server that can be set up to run before login via a GUI interface, and would work across all display managers and desktop environments (at least the major ones)
- OpenSSH with public/private key capability that's as easy to set up as it currently is in Remmina.  Personally, I think the current method of generating key pairs in Linux via the command line is actually easier than the Putty method in Windows (every rule has its exception), but if you want to take a stab at making that GUI have at it. [edit]Actually, since Remmina's already got that covered, I suppose the only thing that needs work is the server end.[/edit]


You and Canonical have already done a miraculous job of making Linux accessible to everyone.  There's so much that just works without fanfare that is a major PITA in other distros that don't have out of the box touchpad support, wireless, printer or just plain won't install in the first place because it locks trying to unmount partitions that aren't mounted in the first place (Bhodi, anyone? Hey, Bhodi - love the look of your distro in Live CD mode.  I'd install it if I could!).  Anyway, as I said, you've made all these things I don't even have to think about. VNC, however, has yet to achieve that ease of use.  What will encourage me to continue with Ubuntu in the future, and hell yeah buy computers from you if you should ever start manufacturing them, is if I can be confident that ten years from now networking from one computer to another via VNC or similar method will be as easy or easier than it is now.  It's how I connect to my stereo computer at home and how I connect to my home computer (I never have personal information on my travel netbook - of any sort) when I travel, so it's an essential capability.

Thank you for all the hard work you've done in making Linux an OS I can use, and for considering my proposal for making it easier still.


Your humble, grateful, non-geek supplicant,

Bill Tetzeli

---

### Post by lykwydchykyn on 2013-05-28
You might want to email mark, I doubt he participates in these forums.

---

### Post by Bill Tetzeli on 2013-05-28
> **lykwydchykyn said:**
> You might want to email mark, I doubt he participates in these forums.

Thanks, I just might do that.  I suppose the reason I posted here first was because I'm hoping the user community could tell me if 1) my fears that setting up VNC in the future will become more of a hacking nightmare than it already is are totally groundless or 2) if my hope, as expressed in the appeal, is either reasonable or desirable.  I don't have to edit any system files to use my mouse, wireless, etc.  It'd be nice if I didn't have to do that for VNC either.  Right now Ubuntu's my favorite linux distro, first among equals with Ubuntu Studio and Xubuntu (both of which use the xubuntu enviro, which I use in official Ubuntu), then Mint, Pear, Zorin, Kubuntu, in that order.  After weeks of fretting I've decided to simply be content with the fact that everything's working right now in all the Ubuntu-based distros, and figure that either Canonical won't go off the rez and pull a Win 8 turn on us in the future or, if they do, there are enough Ubuntu derivatives/forks/what-have-you that will supply the ease and forgo the cheese.  One way or another things will work out.  I wish I knew of an easy, distro-agnostic way to set up VNC so if I ever needed to ditch all Ubuntu distros I could.  I also wish I'd built a shelter in case an asteroid lands on my house.

I figure the two are equally likely. :)

---

### Post by Cheesehead on 2013-05-28
This seems like a [set of] bug report[s] about your VNC applications. The developers generally intend their applications to be able to start and to work. When they don't work, a bug report is the best way to let the developer(s) know so they can reproduce the issue, isolate the problem(s), and fix them.

For example, Remmina should not require LightDM - it's not a listed dependency. If Remmina requires LightDM to work, that's a bug.
There are *lots* of VNC servers and clients to try, if Remmina is not working for you. Personally, I have used xtightvncviewer for my client for the past five years. Flawless and fast.

Mark, to my knowledge, has no involvement with any VNC-related applications - he seems like quite the wrong person to tell your problems to.

---

### Post by Bill Tetzeli on 2013-05-28
My problem isn't the client but the server.  I'm sure there's a zillion different ways to set up a zillion different servers, but it took a lot of searching to figure out a way to do that with x11vnc that worked, and it involved setting up an x11vnc.conf file in /etc/init/ that references lightdm:

[TABLE="class: lista, width: 100%"]
[TR]
[TD="class: last10, align: left"][TABLE="class: lista, width: 100%"]
[TR]
[TD]start on login-session-start
script
/usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /home/your user name goes here/.vnc/passwd -shared -forever -bg -rfbport 5900 -o /var/log/x11vnc.log
end script[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

Although I'm sure there are other ways to do it, most of my searching leads back to Ubuntu.  And although I'm sure I could find out other ways if I spent yet another ten or twelve nights staying up till four in the morning to figure this out - I'm just tired of staying up till four in the morning. :-(

Remmina's a piece of cake - no problems with that whatsoever.

---

### Post by cariboo on 2013-05-28
You may have better luck, posting your problem on the [ubuntu-devel-discuss]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss") mailing list. At least you'll bring ther problerm to the attention of the developers,and they should be able to point you in the right direction

---

### Post by Cheesehead on 2013-05-28
Hmmm. Are you trying to connect to an existing session, or is your SSH triggering a new session?

The latter seems like a use case for [X Forwarding]("http://unix.stackexchange.com/questions/12755/how-to-forward-x-over-ssh-from-ubuntu-machine") rather than VNC. Triggering a remote X session that you can then VNC into is an old chicken-and-egg problem that most people get around by using SSH instead.

The Upstart/LightDM relationship may change soon, and that change may break your script. LightDM will no longer launch an X session directly, but will instead launch a user-level upstart session, which will control all the X and other user-level session.

---

### Post by Bill Tetzeli on 2013-05-29
> **Cheesehead said:**
> Hmmm. Are you trying to connect to an existing session, or is your SSH triggering a new session?

The latter seems like a use case for [X Forwarding]("http://unix.stackexchange.com/questions/12755/how-to-forward-x-over-ssh-from-ubuntu-machine") rather than VNC. Triggering a remote X session that you can then VNC into is an old chicken-and-egg problem that most people get around by using SSH instead.

The Upstart/LightDM relationship may change soon, and that change may break your script. LightDM will no longer launch an X session directly, but will instead launch a user-level upstart session, which will control all the X and other user-level session.

Wow! That looks like what I might be looking for.  A quick test using a fresh install of Fedora 18 and Remmina as a client on my guinea pig netbook shows I am able to SSH to my Ubuntu 13.04 laptop, so it looks like it could be distro-agnostic - a huge plus.  Would you mind helping guide a poor, tender noob on how to do this X forwarding business, though?  Some of my questions:

- I see ssh_config and sshd_config in my /etc/ssh folder, but I don't see the "config" file in my ~/ssh folder.  I also don't see it mention on [this page]("http://narnia.cs.ttu.edu/drupal/node/132"), which seems to have a fuller explanation of the setup.  Is there really a need for the ~/ssh/config file on the client side as the page you link to indicates, or is that superfluous?

- Also, is this something I could set up in Remmina?  Will a public/private key pair work in it, so I can have strengthened encryption, and an additional password layer (so that my ssh password and user login password aren't the same)?

- Maybe, could you tell me specifically how you set your X forwarding up, as closely as possible without revealing any compromising information?


Thanks even if you say no - this already seems to be starting me off in a good direction!

---

### Post by HermanAB on 2013-05-29
VNC is mostly a Windows thing.  If your local machine is Linux, then you already have a proper X based desktop system, so overlaying it with a remote desktop system using VNC is mostly pointless.

It is more efficient to simply log in to the remote system via SSH and then launch the remote application that you need and it will run transparently on your local desktop:
$ ssh -C -X -c blowfish user@server "gedit filename" &

If you need to run multiple remote apps, simply do that multiple times.

---

### Post by Bill Tetzeli on 2013-05-29
Thanks, Herman, I appreciate the suggestion.  I think, though, I'm going to try the X forwarding route.  Even though I've left Windows I'm still a GUI guy at heart - if I have to access every remote program and file by command line, I'd go loony toons and *gulp* "get a Mac"! lol

On the good news side, I managed to get SSH running on boot before login on my Fedora computer, even though it didn't install that way by default.  That's putting me well on the way to the distro-agnostic solution I'm looking for (I think/hope/pray/bribe).  In the meantime, I'm hitting the sack.  I remember the reason I started learning Linux last year was so I wouldn't have to take a crash course when my Windows 7 Home Edition support ends 2 years from now.  I made the switch slowly and stress-free. Right now my VNC through public/private key SSH tunnel via Remmina > X11vnc works fine over most of the Ubuntu distro family.  Given that I can always fall back on Ubuntu 12.04 LTS, which is supported for another four years, I have a much longer time window to learn this new (to me) method and should just

r    e       e          e                     e                              l                                             a                                                              a                                                   x


In other words - it's time to SLEEP!


(a bit easier thanks to the help I've gotten from you all - thanks again!)


Bill

---

