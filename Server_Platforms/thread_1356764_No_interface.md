---
title: "No interface?"
date: 2009-12-16
forum: Server Platforms
---

### Post by twin-08 on 2009-12-16
Hey guys my server came so I went to put ubuntu server 9.10 on it and to my shock its all a command based os.

Im really a noob to linux so I thought that the server edition was the same as ubuntu desktop edition.

Also is there a command to let me log in like the ubuntu desktop edition.

Thanks, twin-08 sorry for asking noob questions however I am a noob to linux

---

### Post by howefield on 2009-12-16
It is normal to have a command line only on a server, but that doesn't stop you installing the desktop environment of your choice.

eg, sudo apt-get install ubuntu-desktop would install gnome.

But... it would also install all the stuff that comes with it, like open office ect.

I'm sure there is a way to get just the desktop but I can't remember how, someone will come along and tell you, or use a search engine, it certainly isn't the first time this question has been asked ;)

---

### Post by kewlrichie on 2009-12-16
It is best practice that you don't install a full desktop because your basically adding more probabilities for security holes and there alot of other reasons not to also, there is a sticky or post someone explaining the drawbacks from installing a full gnome desktop on server edition on ubuntu. Im sure someone will post it. Also from what i remember the server kernel is optimized for non graphical use and doesn't have everything thats in the desktop edition. I would highly suggest learning the command line or using something like Webmin and if you NEED a desktop install a lightweight desktop like XFCE or LXDE. Thats just my two cents

After reading ServerGUI link again i realize i didnt add in eBox or ISPconfig those are both very good options also. For ISPConfig you can follow great write up by falko over at how to forge for "The Perfect Server - Ubuntu 9.10 [ISPConfig 3]" [http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3)

here are some server FAQ that will come in very handy with any further questions you might have [https://help.ubuntu.com/community/ServerFaq#What%27s%20the%20difference%20between%20desktop%20and%20server?]("https://help.ubuntu.com/community/ServerFaq#What%27s%20the%20difference%20between%20desktop%20and%20server?")

and also definitely read this "Arguments Against a GUI"
[https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

btw: what are you using the server for?

---

### Post by doas777 on 2009-12-16
if this server is internal only, then I would either install the ubuntu-desktop package on it, or just reinstall with the desktop ed, and install your services.

if it is externally facing, then follow kewlrichie's advice re webmin or another lightweight frontend.

---

### Post by twin-08 on 2009-12-16
Ok, its just that I can work with an interface better, I was thinking of switching the server to windows home server, but I want to learn linux and for me using a command line isn't learning well its not learning for me.

And the server is only being used as a storage server for my network not for hosting etc.

---

### Post by craigp84 on 2009-12-16
Windows Home Server's maybe the right choice?

In general the power of Linux comes from the command line interface, learn it and you'll never be satisfied with anything less again, but that's also a curse!!!

---

### Post by doas777 on 2009-12-16
I'd just follow [howefield]("http://ubuntuforums.org/member.php?u=186490")'s advice then and install gnome. beware however, at some point you will have to touch the cli, and it's better to have gotten comfortable with it before you need it to dig you out of a problem/

additionally you will find that most linux support focuses on the cli, because while everyones desktop is differant, the cli is the same. also asking volenteers to capture, crop and upload images, will really reduce the number of people that are willing to take the time to assist.  it would take me an half hour to put together the screen shots to walk you through installing ubuntu-desktop via symantic or the add/remove, but it takes me 20 secs to type

run:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by twin-08 on 2009-12-16
Yes but I'll be removing the stuff that I don't need and keeping it the core desktop.

As I don't need it for speed as its only hosting files, also that the pc will be stand alone so I would like something to remote it by eg say teamviewer for windows a program like that which I forget the name off the linux one.

However it was a shocked when taking xp off to find a command line I was gutted as im a noob a linux with the commands as I only know the basics.

Thanks for the help, and see the way you were talking about the guide, would you mind making it for future in case someone hits the same brick wall as I did.

---

### Post by kewlrichie on 2009-12-16
> **twin-08 said:**
> And the server is only being used as a storage server for my network not for hosting etc.

If its going to be for storage only and being that you said windows server I am assuming you have windows boxes that will need to access this data then you will probably be using Samba and you will only need to know a small amount of command line stuff plus the basic which is golden to know just in cause you come across another linux machine or even if you have trouble with your server and cant get to the graphical interface. Anyways if its just storage you can look into the options like FreeNAS which has a very nice web interface or if you still want to stick with Ubuntu Server Webmin would be all you need to configure simple samba shares and you wouldn't need any of the overhead of the GUI Desktop. See i like to go with no gui to save systm resources and use it for server related things but if your going to be doing other heavy server related things then your only slow down would be the network and not so much the machine. So its up to you but i still feel that learning the command line just a little bit like knowing how to edit a config files with nano or vi and learning how to restart services and checking log files will benefit you so much more in the linux world then any interface would.

btw i use mostly command line interface but i always keep Webmin installed just for a backup and when some things are very new to me i'll take a look in there and see whats available etc..

---

### Post by twin-08 on 2009-12-16
See I tried getting ubuntu desktop via commands that most said however it gives me an error saying it cant find the files, so im going to burn ubuntu deskop and install it and just install Samba.

---

### Post by kewlrichie on 2009-12-16
> **twin-08 said:**
> See I tried getting ubuntu desktop via commands that most said however it gives me an error saying it cant find the files, so im going to burn ubuntu deskop and install it and just install Samba.


did you follow the commands from here? [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by doas777 on 2009-12-16
> **twin-08 said:**
> See I tried getting ubuntu desktop via commands that most said however it gives me an error saying it cant find the files, so im going to burn ubuntu deskop and install it and just install Samba.

thats what i do for my internal server (it's also the bedroom TV/media box, so needs a desktop). 
good luck

---

### Post by twin-08 on 2009-12-16
Thanks guys for the help.

Also can you install a web-based admin tool which I can remote desktop etc and edit the server?

---

### Post by doas777 on 2009-12-16
> **twin-08 said:**
> Thanks guys for the help.

Also can you install a web-based admin tool which I can remote desktop etc and edit the server?

I use freenx, but the ubuntu desktop uses vino for VNC based sharing by default. you can find it under system->preferences->remote desktop. freenx is somewhat superior for my usecase. there is no reason you could not install webmin as well/

---

### Post by twin-08 on 2009-12-16
Ok thanks for the help im installing it now tho I think 9.04 messed up as it went to a black screen =[

---

### Post by Krupski on 2009-12-16
> **twin-08 said:**
> Hey guys my server came so I went to put ubuntu server 9.10 on it and to my shock its all a command based os.

Im really a noob to linux so I thought that the server edition was the same as ubuntu desktop edition.

Also is there a command to let me log in like the ubuntu desktop edition.

Thanks, twin-08 sorry for asking noob questions however I am a noob to linux

Server is optimized to be a... server. Both internally and externally (i.e. no GUI because a server doesn't need one).

Adding GNOME or other GUI to server will work, but you will run into intermittent, strange little glitches here and there caused by missing files (that WOULD have been installed with a real desktop install).

One would think that adding a GUI with apt would resolve all the dependencies, but I have found that it doesn't find all of them.

Your BEST bet is to start again with an Ubuntu DESKTOP install disk and do it right.

---

### Post by Iowan on 2009-12-16
[eBox]("https://help.ubuntu.com/9.04/serverguide/C/ebox.html")?

---

### Post by windependence on 2009-12-16
Stay with Windows, you are probably better off.

-Tim

---

### Post by Thocrun on 2009-12-16
If what you are running allows it maybe try Sun Virtual Box?

---

