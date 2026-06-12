---
title: "HP Proliant DL140 Server Drivers"
date: 2011-04-17
forum: Server Platforms
---

### Post by RadiusD on 2011-04-17
I'm pretty much an ubuntu noob and I got a HP Proliant Dl140 server machine that I just put Ubuntu Server on. Where can I find and how do I update drivers for this server? I have never messed with drivers before with ubuntu. Any help would be appreciated. Thank You.

---

### Post by spynappels on 2011-04-18
Is any of the hardware not working correctly? On these machines, I've never had to do anything with the drivers as they are all loaded correctly on start up.

If you can tell us what hardware is not working as you expect it to, we can have a better stab at fixing it, your question needs a little elaborating so we can help you better.

---

### Post by RadiusD on 2011-04-18
Well at first glance everything looks like its working. But the video is very choppy. Like when I moves windows around or open menus everything is choppy. So I assumed video drivers need to be updated.

Also my network card works and I have internet but when I do update or download software it works fine for about 20 seconds and then get very slow. That might not be a driver problem but I thought it would be worth a shot.

---

### Post by spynappels on 2011-04-18
Ok, can I just check a few things first.

Ubuntu Server does not come with a GUI, did you install server edition and then install a GUI, or did you install Desktop Version?

Just from my personal experience, the HP on board video has worked fine for me in both Server and Desktop installs, I'm wondering if the way the GUI was installed is causing a problem.

WRT the networking, it does not sound like a driver issue but I'll dig up the commands needed to check this when I get home later.

---

### Post by elico on 2011-04-18
this server has most likely nvidia card on it.
are you using a desktop environment such as gnome on the server? or shell?
the network speed can be tested using wget.
you can try to download a file from a local mirror of files or updates.
to get a closer mirror you can try to look at:
[http://www.mozilla.org/community/mirrors.html](http://www.mozilla.org/community/mirrors.html)
find a http server that is very close to you and download the file using wget.
for me i took the file
wget "http://mirror.isoc.org.il/pub/mozilla/firefox/releases/4.0/win32/en-US/Firefox%20Setup%204.0.exe"
and it's very fast speed.
when i was using aria2 (aria2c)
it worked much faster cause it's using 8 parallel connections.
by the way maybe you ISP is resposible on the speed problem.

---

### Post by kimda on 2011-04-18
[http://www.ubuntu.com/certification/hardware/200712-183](http://www.ubuntu.com/certification/hardware/200712-183) 
This server is certified with Ubuntu 10.10 and 10.04 LTS so it should work out of the box. Have you installed gnome as a desktop?

---

### Post by RadiusD on 2011-04-18
I have installed the desktop on it. Using this command
>> sudo apt-get install ubuntu-desktop

I will try and run some speed tests and also the graphics card on this server is an ATI Rage XL

---

### Post by usatonycuba on 2011-04-19
@RadiusD

There Are Several recommendations why not to use Desktop environment on a Server .. But if you decide to do so anyway .. I do recommend you Better make install Ubuntu Desktop, And Then LAMP .. (ie. If Its mandatory That You want a graphical interface to run your server)

---

### Post by arrrghhh on 2011-04-19
> **usatonycuba said:**
> @RadiusD

There Are Several recommendations why not to use Desktop environment on a Server .. But if you decide to do so anyway .. I do recommend you Better make install Ubuntu Desktop, And Then LAMP .. (ie. If Its mandatory That You want a graphical interface to run your server)

I will mirror these comments.

DO NOT install the server edition, and then do 'apt-get install ubuntu-desktop'.

That is a complete and utter waste - if you want a GUI, use Ubuntu Desktop.  If you want to run a lean&mean server and have no need for a GUI (hence the lean&mean) then run Ubuntu Server.  Please, don't try to mix them.  Thanks!

---

### Post by tlan on 2011-04-20
HP DL140 will use the most generic ATI video chipset, a couple options will be to check HP's website for a generic linux video driver or download the smartstart CD for linux which i believe defaults to redhat and suse and boot it, once it ask for the OS CD attempt to install UBuntu instead. it might work, never tried it

and the DL140 is low end workgroup server. i would use it as a server only no window desktop manager should be installed.

if you must use that hardware i would go out and buy a inexpensive nvidia card and install it. that server should have two full length PCI-X or PCI-E slots.

Hope that helps

---

### Post by jcer93705 on 2011-08-03
> **RadiusD said:**
> I'm pretty much an ubuntu noob and I got a HP Proliant Dl140 server machine that I just put Ubuntu Server on. Where can I find and how do I update drivers for this server? I have never messed with drivers before with ubuntu. Any help would be appreciated. Thank You.

Hello, the cdrom is it connected by ide cord onnector?
Did you had any issue installing ubuntu? Did you installed
How did you installed ubuntu? I'm thinking of buying one.

---

