---
title: "Multimedia server questions"
date: 2012-04-14
forum: Server Platforms
---

### Post by slammed87d21 on 2012-04-14
Ok, I've got Ubuntu 10.04 server installed, with VNC server and the Gnome core components. Trying to use GTK VNC Viewer to connect to the server, but not sure how to do the setup of the viewer. Any suggestions on how to connect to the server to see the desktop? Sorry for the noob questions but I'm lost and Google isn't helpful since I'm using Linux Mint instead of Windows.

---

### Post by Jonathan L on 2012-04-15
Hi Slammed

>  Ubuntu 10.04 server installed, with VNC server and the Gnome core components ... Any suggestions on how to connect to the server to see the desktop?

My guess is you have the Gnome pieces installed but not running.

It is far, far, more usual to have no desktop on the server, and connect to it by ssh.  Have you tried that?

Kind regards,
Jonathan.

---

### Post by slammed87d21 on 2012-04-16
Jonathan, thanks for your reply. You're very correct that ssh is more common, and FTP also, but maybe explaining what and why might help in understanding this situation. 

Ok, I'm working with a base of a Dell Optiplex GX270 for a small form factor and since I found it at the dump. Lol. It's got a 2.5 GHz P4, and 2.5 gigs of DDR ram. I've had home network based servers before using FTP before. But here's the catch. I don't mind the geek work for using a server, but my gf isn't like me with computers. She wants a GUI. So, the server will be used for storing movie and music backups (despise using discs unless I have to) and pictures and be used for streaming to our PS3 since it upconverts the video. Using it to stream to the PS3 I can handle, but the GUI for her is what has me confused. I've never done anything like this before so it has me a bit confused.


Thanks soooo much,
Andrea

---

### Post by Jonathan L on 2012-04-16
Hi Andrea

Nothing like recovering perfectly good machines if you can!  I've used those Dells for all kinds of things and have had really good success with them. 

If you want the server to be friendly to use for your gf, my suggestion would be install Ubuntu *desktop* and leave it on.  Install sshd/nfs/samba/apache or whatever "serverish" things you need.  Ie, don't get a server and add desktop software, get a desktop machine and add server software.

Getting desktop processes to work and feel "natural" has a lot of dependencies, and the work has already been done as the desktop release.  I wouldn't worry overly about the extra "fat", and the desktop release is certainly good enough for doing what you're describing.

Just a thought.

Kind regards,
Jonathan.

---

### Post by slammed87d21 on 2012-04-16
This isn't the first computer I've saved before. Gateway Solo 2500 running Puppy, a Dell laptop (can't think of the model), the desktop, and my laptop I'm on now, a Toshiba Satellite M115. :)

I had thought about doing the desktop version, but I honestly want to keep the OS space on the HD's to a minimum. It only has a 160 gig HD inside it and I'll be using a 500 gig externally. The server won't have a monitor or keyboard, and is going to be shoved behind the entertainment center so it's easily accessible when needed. When I got the idea for this type of setup I found it by a Google search. What it was showing was using a VNC viewer to take control and stuff of the server for use of it. 

I think I need to go crash since my sleep med is kicking in so hopefully that made sense. If not, I'll post a link to what I was trying to do. 

Thanks so much for all your help. :)
Andrea

---

### Post by SeijiSensei on 2012-04-16
Maybe you and your girlfriend would be better served with something like [MythPC]("http://www.mythbuntu.org/") or [XBMC]("http://wiki.xbmc.org/index.php?title=XBMCbuntu") as the interface?

You might want to take a look at [this forum]("http://www.avsforum.com/avs-vb/forumdisplay.php?f=76") as well.

---

### Post by mcordell on 2012-04-16
> **slammed87d21 said:**
> 
the server will be used for storing movie and music backups (despise using discs unless I have to) and pictures and be used for streaming to our PS3 since it upconverts the video. Using it to stream to the PS3 I can handle, but the GUI for her is what has me confused. 

I'd say that xmbc or myth would work if they were going to run a video card and hook the computer up to a tv. 

But if I read this correctly, this is being used as primarily a file server. Rather than trying to solve this GUI problem, I think it would make more sense to just have the OP mount the filesystem as a network share on the computers that do have a head. OP could just use SAMBA  or NFS and not even screw with FTP.

Andrea, you said that you just want to do backups, and transfer media? If so go with the network share option. Also if you're on a mac or other BSD system, just use rsync to do your backups.

Finally, it should be noted that you might be better served with a network storage solution where you connect the usb drive to a router. Would save on the energy bill

---

### Post by SeijiSensei on 2012-04-17
Software like Myth and XBMC use databases that can help substantially with organizing the files. They also have well-crafted GUI interfaces that the OP's girlfriend might find more friendly than simply a file share.  Here, for instance, is a [sample]("http://wiki.xbmc.org/index.php?title=File:Library.videos.tvshowwide.WSCR.jpg") of program thumbnails from XBMC.

---

