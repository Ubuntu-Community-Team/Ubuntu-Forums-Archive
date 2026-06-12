---
title: "windows user needs help"
date: 2008-08-01
forum: Server Platforms
---

### Post by NeoAnima83 on 2008-08-01
Im sure this has been posted a billion times. Im a network admin testing out vmware. I run WINDOWS servers. i installed on my xp desktop- a virtual ubuntu server 8.04 or something. I follow a couple of suggestions when i browsed the forums. i installed gnome, and firefox. but when i do the startx it comes up - Fatal server error: could not open default font 'fixed'. also, when i do /etc/init.d/gdm start it comes up with *Starting GNOME Display Manager... [fail]

i installed samba, but have no idea what to do.

is this a bad install, whats going on? i may be a little SLOW on the linux side, but im trying. any help is appreciated.

---

### Post by freebeer on 2008-08-01
I don't know if I can be of much help (I've never tried to run it in a vm on Windows), but here goes:

First off, Samba's not your issue.  Samba is about sharing files between clients.

Your first error seems to imply that it can't find a specific font.  I'm not really sure why that would prevent it from loading, though.  I'm wondering if X doesn't have the right video hardware information from Windows?  At any rate, I think that's the area for you to focus on.

---

### Post by yeaitsdark on 2008-08-01
Have you tried ```
sudo dpkg-reconfigure xserver-xorg
```. Aside from that my thinking is something to do with the virtual video card provided by M$

But yea I presume this is an issue Windows side. First, because it's far easier to blame M$ for all our problems. Second, "fail" isn't that much information to go on. But do try to reconfigure X and see if perhaps that helps a bit. 

Also, I've been to lazy to actually delve into the server kernel, but perhaps it hasn't been compiled with your "virtual" video card in mind... but I really kinda doubt that, as I'm sure it's a most generic device.

---

### Post by cariboo on 2008-08-01
The idea behind the linux server is that you administer it remotely, you don't have have a monitor and keyboard hooked up to it. Most of us just use the command line to do administration. Seeing as you are new to this you can install a full desktop from the command line. At the prompt type:

```
sudo apt-get install ubuntu-desktop
```

This is a meta package that will install all the programs needed for a full gui. The above command will ask for your password, when you enter it, it won't echo back anything. This is to prevent shoulder surfers from getting your password.

Jim

---

### Post by NeoAnima83 on 2008-08-01
i was just stating i didnt know how to start samba, or use it for that matter. how would i even check the video information provided by microsoft. i thought my only problem with virtualization was that you are "supposed" to need a cpu that supports it intel-v or amd-v, and most commonly they werent able to run virtual windows servers without the v-processor, but linux/unix should have no problems-- although i am already running a v-server2003 on my xp box. i did the reconfigure xorg but i didnt notice anything wrong. like i said, i am as new as they get to this. and YES i understand the reasoning behind a linux server - well, the reason i chose ubuntu was because it kinda meets halfway (or at least the desktop is). Graphical (I can operate ANYTHING with a gui), somewhat user friendly. if something doesnt work then u can always try the cli. im young as **** and i grew up on windows not DOS or the like kind. give me a break. at least im giving it a shot.

---

### Post by freebeer on 2008-08-01
Hi again!

No need for "give me a break"... no-one said anything hostile as far as I can tell... they are trying to help you.

Did you install the desktop like cariboo907 suggested?

---

### Post by windependence on 2008-08-01
> **NeoAnima83 said:**
> (I can operate ANYTHING with a gui).

So can most of the breathing people on the planet. This probably isn't going to impress anyone here.

Now, as for your question, if all you need to do is have a platform for virtualization, you don't even need all this. VMware has just released their ESXi hypervisor for free, which is it's own OS. It has just a 32mb footprint, and does NOT need special hardware or processors.

[http://www.vmware.com/products/esxi/#c62293](http://www.vmware.com/products/esxi/#c62293)

Seriously, you should do some research on virtualization, because you are just scraping the surface here and to really plan for what direction you want to go, you need to be better informed. Should you need any help, I will gladly do what I can.

-Tim

---

### Post by NeoAnima83 on 2008-08-01
im definitely not trying to impress anyone other than my boss's. idk about the ESXi, i am running vmware server 1.0 on my xp desktop (just as test environment) with a server2003 and ubuntu. really my goal was to create SERVER space to hold windows files, by just going around the windows licensing. my main management program (TAM) will only work on windows, and the only way to get it to run on linux is by pushing the app via Citrix. I have an older version of citrix (not PS4) and dont know if i really want to make this move. the only reason to do that is to make sure i dont have to install vista on any new machines. im not super interested in server consolidation or linux, im just trying to get this setup to work, to have options.

---

### Post by windependence on 2008-08-01
If all you need is a file server for Windoze, then Linux with SAMBA is the way to go, and run it headless. If you REALLY have to have a GUI, run a remote web config like WebMin, or SWAT from another machine. You can just create your shares and all the windows machines just see them as network shares, Windoze doesn't know the difference.

When you say get around the license cost, if you could explain a little more what you are doing (what TAM does, etc) I may be able to give you some better advice. You may not even need Linux. Correct me if I'm wrong, you already have one Windoze license?

-Tim

---

### Post by Mumbly on 2008-08-02
First off, VMware workstation on Windows has had problems configuring the correct card many times. Check the xorg.conf file, and look for what driver the card is using. First off, let's backup your existing xorg.conf in case things go bad.
```

cp /etc/x11/xorg.conf /

```
Now open it for editing.
```

sudo vi /etc/X11/xorg.conf

```
Look for the Driver listing under "Section Device"
Try changing it to something like vga instead of what it is.

Once it is changed, type :wq! to exit and save.

If that doesn't work try the following:

```

sudo apt-get clean
sudo apt-get update
sudo apt-get xfonts-base xfonts-100dpi xfonts-scalable 

```

If it says you already have them installed, use dpkg-reconfigure as yeaitsdark stated above except use it with the fonts package.

Hope it helps!

---

### Post by NeoAnima83 on 2008-08-02
TAM is my main management system developed by AppliedSystems Inc wwww.appliedsystems.com Yes i have windows licenses, my Entire environtment is windows.  As my company grows and does acquisitions ( i believe i will have two more remote offices at the end of the year) i will need more machines. if i could use linux instead of windows and save on their licenses, that would be great. as for the server share, my current server has all 8 SAS drive slots in use and i dont have much room. i was thinking of hosting all of my mail (.pst) files on the v-server and having backup exec or ultra bac or acronis back it up to an LTO4 drive. I guess i could setup a v-server to use instead of exchange, would be nice, but i would have to invest in a little better box than my decent 2.6Ghz dual core with 2GB DDR2. so many options. i could vpn into work and do some of that code but ive been there all week, im waiting until monday. thanks for all the advice, i will post what happens. thanks

---

### Post by windependence on 2008-08-02
Ah, OK you are in the Insurance biz?

I was in the biz for 15 years and owned an Agency. Yeah, most of those agency management systems are highly Windoze centric, but there are some things you could move to linux, file storage, you could dump exchange for something like Zimbra, etc. If you let us know what you want to accomplish, I am sure we could help you here.

-Tim

---

### Post by NeoAnima83 on 2008-08-02
yes indeed insurance. i got the xbase-fonts and that seemed to work. i screwed up editing the xorg.conf file, and even though i had copied it, had no idea how to paste it, but i was able to download and overwrite that file, so no big deal. now i have a graphical desktop, and can surf the net, and a few things. somethings are still giving me errors. i need to just keep this setup and work with it. i downloaded a couple of .tar.gz files and have no idea how to install them. i am going to try and get beryl next. im thinking of testing out other flavors too, maybe knoppix, or gentoo. idk. its wierd, the ubuntu server has many problems, but the ubuntu desktop is running fine. i downloaded the cisco vpn client but i cant install it. thanks for the help.

---

### Post by windependence on 2008-08-02
Well the sever version doesn't <really> have problems as you are not supposed to be loading a GUI. Things like beryl were never intended to be run on server. The CLI is a completely different paradigm, and at first it is daunting and then later on you just "get it" and it all falls in place but you have to force yourself NOT to use the GUI or a web interface crutch. I know. I've been there.

-Tim

---

