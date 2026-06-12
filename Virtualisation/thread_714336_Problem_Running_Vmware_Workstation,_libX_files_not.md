---
title: "Problem Running Vmware Workstation, libX files not found"
date: 2008-03-03
forum: Virtualisation
---

### Post by woody22075 on 2008-03-03
I just installed the evaluation of Wmware Workstation on my Feisty 64 AMD.  When i run the install, i get a error saying that i cannot run Workstation until i get the following installed:

libX11.so.6
libXst.so.6
libXext.so.6
libXrender.so.1
libz.so.1

I cant find these on Synaptic.  How should i proceed?

Thank you for the assistance!

M

---

### Post by fjgaude on 2008-03-04
Did you install build-essential? This group might have these files in it.

```
sudo apt-get install build-essential
```

---

### Post by woody22075 on 2008-03-16
sorry for the delay in response.  i do have build-essential installed, still no dice.  any other recommendations?  i am really looking forwards to getting vmware up and running so i can dump windows, unfort VMware is not responding to my support emails.

---

### Post by fjgaude on 2008-03-16
I have these files on my computer, and I know I never intentionally installed them. They must come with some package, but can't say which.

Have you done anything unusual to your install of Feisty? Try Gutsy?

---

### Post by woody22075 on 2008-03-16
cant go gutsy (hardware thing), havent done anything "weird" with feisty.  can you maybe look up to what these files are a dependency?

thanks!

---

### Post by fjgaude on 2008-03-16
Well, the libX11 files has to go with anything to do with X11, like python, evolution, and most everything that has to do with the GUI. The rest are just like it, associated with just about every program on the system.

Try installing libX11 and libXrender and see what happens.

Strange that you are missing the .so and the like.

---

### Post by woody22075 on 2008-03-18
fjgaude, thanks for the input...will try that now.  is there an easy way to just install these dependencies?  i have trouble trying to find them in synaptic.  if they are so common, surely there is a way to d/l then. no?

Cheers,

Marshall

---

### Post by fjgaude on 2008-03-19
I believe they are a part of the general gnome desktop. You aren't running just the server Ubuntu, eh?

---

### Post by woody22075 on 2008-03-19
No, not running the server.  Im not sure how i am missing the files, but would really like to get them.

---

### Post by fjgaude on 2008-03-19
I don't have the time now but I will gather them up for you and put them as an attachment... then the issue will be to put them all in the correct directories. This will take time sorting this all out.

It all has something to do with that workstation package and the files contained within it. I'm at a loss to say what is going on.

---

### Post by fjgaude on 2008-03-19
I'm running Gutsy, 64-bit. Here's what I get from a locate for each of your missing files:
```

frank@sunshine:~$ locate libXrender.so.1
/home/frank/vmware-server-distrib/lib/lib/libXrender.so.1
/home/frank/vmware-server-distrib/lib/lib/libXrender.so.1/libXrender.so.1
/usr/lib32/libXrender.so.1.3.0
/usr/lib32/libXrender.so.1
/usr/lib/libXrender.so.1.3.0
/usr/lib/vmware/lib/libXrender.so.1
/usr/lib/vmware/lib/libXrender.so.1/libXrender.so.1
/usr/lib/libXrender.so.1
frank@sunshine:~$ locate libz.so.1
/usr/lib32/libz.so.1.2.3.3
/usr/lib32/libz.so.1
/usr/lib/libz.so.1.2.3.3
/usr/lib/libz.so.1
frank@sunshine:~$ locate libX11.so.6
/usr/lib32/libX11.so.6
/usr/lib32/libX11.so.6.2.0
/usr/lib/libX11.so.6
/usr/lib/libX11.so.6.2.0
frank@sunshine:~$ locate libXext.so.6
/usr/lib32/libXext.so.6.4.0
/usr/lib32/libXext.so.6
/usr/lib/libXext.so.6.4.0
/usr/lib/libXext.so.6

```

I don't have libXst.so.6 on my system.

When you do a google on anyone of them you see that these "shared objects" go with larger packages.

I could copy mine out and put them in attachments but I don't think it would work for you, running Feisty.

The libXrender.so.1 comes from my vmware-server distribution file after it was expanded.

Seems to me you have something other than a "standard" install of Ubuntu, or of Feisty. Maybe Workstation is not setup for Feisty?

---

### Post by woody22075 on 2008-03-19
fjgaude,

when you have the time I would really appreciate the files!  I havent been able to locate them (as i mentioned before) and vmware will not respond to my inquiries.

Best,

 Marshall

---

### Post by fjgaude on 2008-03-19
Okay here they are, the four I have as an attachment archive.

Good luck!

---

### Post by woody22075 on 2008-03-19
fjgaude,

thanks for the files!  one small question, how should i install them?  should i put them in the directories as per your gutsy install?

thanks again for the assistance,

marshall

---

### Post by fjgaude on 2008-03-20
I guess so... good luck!

You see those files had lots of links to them, mostly soft ones. I really think this is a bad idea to try to install them this way.

---

