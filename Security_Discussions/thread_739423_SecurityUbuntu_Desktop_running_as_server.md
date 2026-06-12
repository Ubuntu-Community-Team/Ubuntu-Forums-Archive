---
title: "Security:Ubuntu Desktop running as server"
date: 2008-03-29
forum: Security Discussions
---

### Post by saj0577 on 2008-03-29
I know obviously more programs means more possible vulnerabilities, but if i have a server install with just an x server installed as well and i secure the x server, their should not be anything that makes my machine any more insecure then just a ubuntu server without an X-server should their as they both have the same security updates?

Saj

---

### Post by Joeb454 on 2008-03-29
Why not post this in the server or security section of the forums where you'll likely get a far better and more informed response :)

---

### Post by p_quarles on 2008-03-29
Moved to Security Discussions. 

The more applications you are running on a public server, the more potential vulnerabilities it will acquire. The best practice is to install what you need and nothing more.

---

### Post by saj0577 on 2008-03-29
But as long as i secure the X server much like you would with any desktop edition then it will be secure yeah?

Saj

---

### Post by p_quarles on 2008-03-29
> **saj0577 said:**
> But as long as i secure the X server much like you would with any desktop edition then it will be secure yeah?

Saj
"Secure" it how? Please don't take this as anything other than friendly advice: if you don't know how to answer that question, you might want to research the subject more before going any further.

---

### Post by Joeb454 on 2008-03-29
Can I just ask as to why you want to install X Server on a server? They're pretty easy to set up and manage anyway.

Sure it involves learning a little of the CLI, but still, it's really not that hard in my opinion :)

---

### Post by saj0577 on 2008-03-29
Just sometimes i get problems with things on my sever which i cant fix in terminal no matter how hard i try.

CUPS
NFS
etc..

I treid posting but i need a guide not the principal of how.

Saj

---

### Post by saj0577 on 2008-03-29
> **p_quarles said:**
> "Secure" it how? Please don't take this as anything other than friendly advice: if you don't know how to answer that question, you might want to research the subject more before going any further.

Like make sure their no remote desktop etc running. Just basics.

Saj

---

### Post by p_quarles on 2008-03-29
> **saj0577 said:**
> Just sometimes i get problems with things on my sever which i cant fix in terminal no matter how hard i try.

CUPS
NFS
etc..

I treid posting but i need a guide not the principal of how.

Saj
That strikes me as perfectly reasonable, but you can largely avoid potential security issues by running X on an as-needed basis. Make sure that the default session does *not* run X, and start it up when you need to fix something.

For my money, though, the CUPS web interface is on par with any of the X interfaces available.

---

### Post by saj0577 on 2008-03-29
Okay, so you think my idea is resonable just shut down the X when not needed yeah?

Saj

---

### Post by HermanAB on 2008-03-30
A real 'server' is usually a scary headless machine installed in a dank corner of a dark data centre where there are no screens, keyboards or rodents and hence no need for X servers.

Hard core geeks manage these remote servers using SSH.  SSH has a X client  built-in and allows the remote control of a server with nice graphical utilities, using the X server on the local desktop machine used to log into the remote server. Consequently a server doesn't need X if the local controlling machine has it, which is usually the case.

However, if you are running a desktop machine as a cheap skate server, with all the trimmings attached, then you certainly can run X.  It is easy to switch the console schtuff on/off, using 'init 3' and 'init 5' to save some memory and file handles if you are really paranoid. Nowadays however, any half decent machine has an obscene amount of RAM and therefore the memory savings from turning X off is really not worth the trouble and the security issues that X used to have twenty years ago have long since been fixed.

I believe that most people on these forums should not install the Ubuntu Server Edition, since they don't have dank, dark data centres and headless servers, but should rather install a regular Linux, eg, Xubuntu or Ubuntu for their server functions.

Cheers,

Herman

---

### Post by Dr Small on 2008-03-30
> **HermanAB said:**
> A real 'server' is usually a scary headless machine installed in a dank corner of a dark data centre where there are no screens, keyboards or rodents and hence no need for X servers.

Hard core geeks manage these remote servers using SSH.  SSH has a X client  built-in and allows the remote control of a server with nice graphical utilities, using the X server on the local desktop machine used to log into the remote server. Consequently a server doesn't need X if the local controlling machine has it, which is usually the case.

However, if you are running a desktop machine as a cheap skate server, with all the trimmings attached, then you certainly can run X.  It is easy to switch the console schtuff on/off, using 'init 3' and 'init 5' to save some memory and file handles if you are really paranoid. Nowadays however, any half decent machine has an obscene amount of RAM and therefore the memory savings from turning X off is really not worth the trouble and the security issues that X used to have twenty years ago have long since been fixed.

I believe that most people on these forums should not install the Ubuntu Server Edition, since they don't have dank, dark data centres and headless servers, but should rather install a regular Linux, eg, Xubuntu or Ubuntu for their server functions.

Cheers,

Herman
If I had the dark, dank data centre, that is where my server would be.
Unfortuantly, mine is beside my desk, but still headless and controled via SSH :)

---

### Post by saj0577 on 2008-03-30
So how i get it to work with an x server through SSh from another computer please (as the server computer when its set up will be thrown in the attic not to be seen again for a few years. )

Saj

---

### Post by HermanAB on 2008-03-30
First install the ssh server package.  (Ubuntu is the only schtooopiddttt Linux system in the whole world that doesn't install SSH server by default - my pet peeve...)

Then from your desktop do something like:
$ ssh -X [email]user@server.ip.add.ress[/email] "gedit /etc/fstab"

Cheers,

Herman

---

### Post by Dr Small on 2008-03-30
> **HermanAB said:**
> First install the ssh server package.  (Ubuntu is the only schtooopiddttt Linux system in the whole world that doesn't install SSH server by default - my pet peeve...)

Then from your desktop do something like:
$ ssh -X [email]user@server.ip.add.ress[/email] "gedit /etc/fstab"

Cheers,

Herman
Or, my favorite:
```
ssh -XC -c blowfish user@host
```

If you want to launch a Window Manager on the remote system, open a new X session (or use [Xephyr]("http://ubuntuforums.org/showthread.php?t=620003")) and run:
```
ssh -XC -c blowfish user@host *icewm-session*
```

It ports the Window Manager over into your Xsession and makes you feel right at home :)

Dr Small

---

### Post by saj0577 on 2008-03-30
Cheers both of you and this willl look just like gnome yeah?

Saj

---

### Post by Dr Small on 2008-03-30
Looking like Gnome is your choice.
You could have it look any window manager you want!

But assuming you want to see the gnome desktop (insinuating that it has already been installed), start a new Xsession and run:
```
ssh -XC -c blowfish user@host gnome-session
```

Dr Small

---

### Post by saj0577 on 2008-03-31
You say installed.On Server or client?

If server what commands i need to install it?

Saj

---

### Post by p_quarles on 2008-03-31
> **HermanAB said:**
> I believe that most people on these forums should not install the Ubuntu Server Edition, since they don't have dank, dark data centres and headless servers, but should rather install a regular Linux, eg, Xubuntu or Ubuntu for their server functions.
That's not completely accurate. That Xorg update in January that broke Java applications? The intent was to fix a privilege escalation exploit. 

Whether or not X is any *more* likely to be vulnerable than something else (there was also a similar kernel exploit found in February) isn't really the point. The fewer applications you are running, the fewer potential exploits your system will be exposed to.

---

### Post by Dr Small on 2008-03-31
> **saj0577 said:**
> You say installed.On Server or client?

If server what commands i need to install it?

Saj
It would need to be installed on the server to be able to be viewed remotely from a client. To install the Ubuntu Desktop:
```
sudo apt-get install ubuntu-desktop
```

But personally to me, that is alot of bloat. I prefer:
```
sudo apt-get install xorg icewm
```

Dr Small

---

### Post by saj0577 on 2008-03-31
So you believe use server with minimal  x server use yeah?untill can use without any x server?

Saj

---

### Post by saj0577 on 2008-03-31
> **Dr Small said:**
> It would need to be installed on the server to be able to be viewed remotely from a client. To install the Ubuntu Desktop:
```
sudo apt-get install ubuntu-desktop
```

But personally to me, that is alot of bloat. I prefer:
```
sudo apt-get install xorg icewm
```

Dr Small

```
sudo apt-get install ubuntu-desktop
```
would install all the other programs too not just the gnome though woudl it not?

```
sudo apt-get install xorg icewm
```
icewm I will look into this thanks

Saj

---

### Post by Dr Small on 2008-03-31
> **saj0577 said:**
> So you believe use server with minimal  x server use yeah?untill can use without any x server?

Saj
I believe that if it is a server, Xorg is not necessary, and neither is Ubuntu Desktop due to being overly large and hogs system resources.

---

### Post by saj0577 on 2008-03-31
> **Dr Small said:**
> I believe that if it is a server, Xorg is not necessary, and neither is Ubuntu Desktop due to being overly large and hogs system resources.

Okay thanks i will look into the window manager you suggested.

Thanks
Saj

I will get back to you with my opinion on it.

---

### Post by saj0577 on 2008-03-31
It appears ixewm is more like kde with the layout then ubuntu yeah?

Saj

---

### Post by Dr Small on 2008-03-31
IceWM is a lightweight window manager that has some look and feel of Windows, (per say) but is highly customizable:

[https://help.ubuntu.com/community/IceWM](https://help.ubuntu.com/community/IceWM)

---

### Post by saj0577 on 2008-03-31
Cheers you have been a great hand.

Saj

---

### Post by saj0577 on 2008-03-31
From that wiki

> If you want a desktop with IceWM, you can do so in several ways. The best is to get ROX-Filer.

What does it mean by desktop? Sorry for asking so many question but i love you like being helpful hehe.

Saj

---

### Post by The Cog on 2008-03-31
Personally, I suggest you install whichever desktop you use on your normal desktop machine. Frinstance, I use Ubuntu (as opposed to kbuntu, xubuntu etc), so I would install ubuntu-desktop. Then I would disable the desktop manager by removing the file /etc/rc2.d/gdm. This means you have all your familiar configuration utilities installed, but no desktop on your non-existent screen.

Now connect in with
**ssh -XC servername**
and you will find that if you run the utilities from the command line (e.g. **gksudo synaptic**) the windows appear on your own display. Magic! You just have to know the program names to launch them with, and you can find these by right-clicking and editing your own menu and looking at the menu item properties.

---

### Post by saj0577 on 2008-03-31
But installing ubuntu-desktop installs all the other programs as well yes?

Saj

---

### Post by The Cog on 2008-03-31
True. You get quite a few megabytes of things like OpenOffice that you won't ever want. Is your server that desperately short of disk space?

---

### Post by saj0577 on 2008-03-31
No, not at all just why have it if not need it?

No way to just install the gnome panels and so forth without programs?

Saj

---

### Post by Dr Small on 2008-03-31
> **saj0577 said:**
> From that wiki



What does it mean by desktop? Sorry for asking so many question but i love you like being helpful hehe.

Saj
A desktop, as it a place where you can "stick" icons.
But you could simply try installing gnome-session and see how well that would work (if at all?)

Dr Small

---

### Post by saj0577 on 2008-04-01
Okay i dont want a desktop just curious.

Thanks
Saj

---

### Post by The Cog on 2008-04-01
The package gnome-desktop has no actual contents itself, but has a very long list of dependencies which get summoned when you install it. Itis basically a shopping list of all the default-install desktop applications. 

If you are really short of disk space, you can just pick and choose to install the individual GUI apps you want like the user manager, network manager and so on. Just work through the menus picking the applications you might want and then try to work out what package name each one is in. I don't know how much space you would save. Personally, I would rather save my time by installing the one super-package.

---

### Post by saj0577 on 2008-04-02
Anyone got a list of every application on the System part of the menu, (so non of the ones from the games,internet,office,multimedia menus etc??) 


Thanks in advance
Saj

---

### Post by saj0577 on 2008-04-02
I know its not the best way of doing it but im going to do a ubuntu 7.10 desktop edition install then remove ALL programs apart from the ones on the System menu, then disable the gdm and then setup the server, by doing this if i get a problem through terminal such as setting up CUPS i can enable the X, set the printer sharing up then disable the X again. I think this is the easiet way to suit my needs. 

When I have finised the set up i will post some screenshots, and some discription of exactly what my server has on it so that if anyone has similar needs (a server but they dont know the terminal quite well enough to be dependant on it) then they can use the same set up as mine. Maybe create a .iso from my computer when done for others to use?

Saj

---

### Post by saj0577 on 2008-04-02
Just finished the install got rid of everything that is uneeded that can delete (a few apps had to be left otherwise it deletes ubuntu-desktop too.) More information coming soon.


Saj

UPDATE: Working on a list of packages to install to a ubuntu-server for the perfect system

---

### Post by netlogic on 2008-04-02
> **p_quarles said:**
> The fewer applications you are running, the fewer potential exploits your system will be exposed to.

Oh, I agree... It is so hard to explain this people. It is also less codes to examine.

---

