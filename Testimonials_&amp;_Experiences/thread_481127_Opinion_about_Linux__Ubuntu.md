---
title: "Opinion about Linux / Ubuntu"
date: 2007-06-22
forum: Testimonials &amp; Experiences
---

### Post by Chronos6 on 2007-06-22
Hy there!
In brief i'm a Hungarian guy, studying programming at Debrecen University.
I was using m$ products from a long time, probably becouse everybody surrounding me was using them. I heard of Linux, Unix, MacOS and stuff like that, i tried Suse, but it was a kinda unsimphatic. I tried later 2 DVD Sarge Debian, and 5.time it was working:P it was too big bit for me, but i enjoyed it pretty well. In that time i read an article about Linux philosophy, and stuff like that, and i really got ambitous. After that i downloaded Fedora, i loved it, but as i didnt had internet i was screwed. And i have the opinion that Linux cant work without internet connection. Can it?! Than i gave up Fedora, and now i have an internet connection at home, so i was looking for distibutions, the first was Fedora(i really liked that), and Ubuntu was what i read all about in forums. So much users!?!:P And the third was Uhu, a Hungarian Debian based distro. I downloaded Ubuntu(only one CD?! WOW) and it worked soo charmingly smooth!!! I have an Ati 9600xt, and the Compiz was working at first boot, sound was installed, everything was set. It it amasing. 
And here comes why i'm writing this:D
I had several problems. I think i'm a powa user, so i can do whatever i want, i just need time, and stamina. True, but shall we proceed, we will come back to this later. 
I wanted to make my girlfriend like Linux, so i asked her what is she using most of the time. She said three things: MSN(voice conference), internet radio, and working with pictures. 
So i started to look for msn clones. I found mercury(couldnt get work), aMSN, and Trillian. Trillian worked with Cedega(:P) aMSN was good after tweaing a bit, and installing a few plugins. But there is no voice conference option. Thats bad. So if we wanted to speak with people we had to go back to xp. I've installed Skype, what was easy, and the vioce was not fluent, sometimes we coulndt here nothing, just chunks. So as who we called. So we had to go back to xp:( I've givin up trying(jabber). 
Listening to internet radio was easy with Amarok, it's a cool player, and GStream is a good thing:D
Working with pictures was kind a headache. When i click browse, i couldnt see the files thumbnails(Gnome?) and its kind a backforce. Using Gimp and Gwenview is unfamiliar, but can get used to. 2 out of 3. Not bad, but not good either. 
I tried to make ntfs partition writable(i could read it from the first boot WOW!) I had problems with that, i still have problems with Krusader, it always want to mount the partition, what is already mounted. And i coulndt read a few DVD/CDs what is readable in xp. Irritating. Writing disks is easy with Nero(:P) sometimes i couldt get out my dvd-s from the drives (my god what a disapponting thing...) i have to use Nero to get it out. I tried to find a solution, couldt get it work. And i couldnt get ISO files mounted. Not all, but the most important ones(good ol' Murphy:P) And i couldt get files extracted as well. Had to go back to xp(how many time now?:|) 
Tried to make games work(Q3, and Nexuiz). In quake i dont have a pointer, but mouse buttons work. In Nexuiz after trying to change resolution it freezes Xorg(?) and i have to go to console, and go reboot. It must be something to do with beryl(:P) 
I have a printer (Canon ip1500) and it worked fine after installing driver, what has limited possabilities. 
I couldt get my phone communicate with Linux(Smartphone).
Couldnt get my keyboard special keys assigned.

I dont want to hurt Linux, it has a great potencial, but it is not perfect as it could be. 
I can handle the problems. Can an ordenary user? Definitely no. Not even in xp. There are many noobs, who are not thinking, just want to watch a movie or listen to internet radio, or use some funcions what is easy. Linux is not that, but close. Is xp? i'm not sure, probably not. Is vista? (LOL not:D).

I think what Ubuntu(or Linux?)is really missing is just a big main philosophy. In self Ubuntu has that. It is working, stable easy, fast, pretty(love berly:D:D:D). But Gnome, aMSN, opengl support, printer support, beryl, krusader etc need more time to "bake". I wont leave Linux world, i love to be free, and innovate, and i will help the community where i can, even help develop programs when i have the knoweledge. Just the world is too materialistic, needs a change. I dont know what should be the last word...maybe Don't let life kill your dreams. Or dont let m$ eat every bit of the cake:P

Waiting for your oppinion. Regards, Chronos
PS: sorry for mistyping words, hope my english is understandable enaugh:P

---

### Post by 3rdalbum on 2007-06-22
Gizmo Project is a VOIP program which recently has started supporting MSN chat. I think they're claiming to have voice support on MSN too, check it out! [www.gizmoproject.com](www.gizmoproject.com)

I'm not sure I quite understand the problem you're having with the pictures - is this the thumbnails in Nautilus (the Gnome file manager) that aren't working? Have you checked under "Edit > Preferences > Preview" that you don't have restrictions on the file sizes to get previews from?

Making an NTFS partition writable has worked fine for me. At the moment I don't think any automounters support NTFS-3G (you've got to put the partition in the fstab), but this problem is being worked on as we speak. The only real problem I've had with NTFS-3G is actually because Windows won't read colons in the filenames, even though the NTFS specification actually supports them. I sent two bug reports: One to the NTFS-3G team, one to Microsoft. The NTFS-3G team responded with an explanation. Microsoft are yet to get back to me.

It's really not appropriate to run Beryl while trying to do gaming, so that's probably the cause of your problems. Windows Vista turns off its own composited interface when you run fullscreen games, so it's not a problem specific to Beryl.

Some of your other problems are caused by lack of third-party support and Microsoft's vendor lock-in, so they don't really apply as Linux criticisms. You're absolutely right when you say that ordinary users can't handle the problems in Windows XP, but I find that the problems in Linux only come out when you're doing advanced, bleeding-edge things. XP's problems can occur for everyday tasks.

Your English is very good, and thank you for your post.

---

### Post by Jimbo2184 on 2007-06-22
> Listening to internet radio was easy with Amarok, it's a cool player, and GStream is a good thing

Have you tried StreamTuner as well? Its pretty nice, lightweight and launches the XMMS player to play back the streaming music, and you can also record the stream as you listen to it from the StreamTuner interface. I agree - Amarok is an excellent player.

> Tried to make games work(Q3, and Nexuiz). In quake i dont have a pointer, but mouse buttons work. In Nexuiz after trying to change resolution it freezes Xorg(?) and i have to go to console, and go reboot. It must be something to do with beryl(:P)

Ah yep the composited interface will freeze up games or cause flickering sometimes. Had the same problem with Neverball and Nexuiz in fullscreen modes. Try this.

Right click Beryl Manager > Select Window Manager > Metacity (GNOME Window Manager)

This will use the basic 2D GNOME Window Manager, and it works with Neverball and Nexuiz really well with no artifacts. You can always turn it back on later with the Beryl Manager icon again:


Right click Beryl Manager > Select Window Manager > Beryl

As for the keyboard special keys what make and model of keyboard do you have? I may be able to help you set up xorg to recognise the special keys.

As for the DVD writing have you tried K3B yet? Installing it is easy through Synaptic or:

```
sudo apt-get install k3b
```

in an xterm window.

Hope it helps.

---

