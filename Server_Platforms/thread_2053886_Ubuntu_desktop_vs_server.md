---
title: "Ubuntu desktop vs server"
date: 2012-09-06
forum: Server Platforms
---

### Post by AgentZ86 on 2012-09-06
Hi

I currently run an SME server and understand most basic topics for setup and domain records but feel that I would like to install more packages that I would not be able to do on SME due to their templating methods of the server design.

I believe ubuntu server may be a better choice at this time.

Is there any reason to load the server version vs the desktop version ?
I mean can I install all the features of the server version from the desktop software center ? 

I know performance will be slightly lower this way but I only have minimum users and probably also use as a minecraft server too.

Will be installing on a supermicro server with (2X) Xeon E5320 64bit quad core processors = 8 cores/4GB/80GB sata

Please advise
Thanks

---

### Post by Bachstelze on 2012-09-06
> **AgentZ86 said:**
> 
I mean can I install all the features of the server version from the desktop software center ? 



Yes, the only difference between the "server" and "desktop" versions are the packages installed by default. Once the system is installed, you can install any package you wnt (so you can install "server" packages on a "desktop" Ubuntu, and vice versa).

A lot of people consider it a taboo to install any "desktop" package on a "server". They are wrong, of course, use what you are most comfortable with (but please avoid Webmin).

---

### Post by The Cog on 2012-09-06
I believe that the server version has task scheduler settings tweaked more for server loads than desktop loads, but I think the difference is slight. 

By default the server install doesn't include a GUI, but all the same packages are available for install if you want them.

---

### Post by Cheesemill on 2012-09-06
> **The Cog said:**
> I believe that the server version has task scheduler settings tweaked more for server loads than desktop loads, but I think the difference is slight. 

It used to but not any more, the Desktop and Server versions now use an identical kernel.

---

### Post by AgentZ86 on 2012-09-07
> **Cheesemill said:**
> It used to but not any more, the Desktop and Server versions now use an identical kernel.

Do they use the same repos too ? 

Basically I install the Desktop version on the rack mount server just to test the server for now, but which packages should I install to make it a complete server / desktop combo ? 

Is there something in the repos I should install to get this fixed up as a server too ? 

Thanks

---

### Post by arrrghhh on 2012-09-07
> **AgentZ86 said:**
> Do they use the same repos too ? 

Basically I install the Desktop version on the rack mount server just to test the server for now, but which packages should I install to make it a complete server / desktop combo ? 

Is there something in the repos I should install to get this fixed up as a server too ? 

Thanks

Same repo's.  The server version has A LOT less gunk installed - obviously, as there's no GUI.

So just think of Ubuntu Server as a really stripped, lean and mean version of Ubuntu Desktop - optimized to run on servers (as in, no UI)

---

### Post by darkod on 2012-09-07
> **AgentZ86 said:**
>  but which packages should I install to make it a complete server / desktop combo ? 


The packages to install depend on the roles you want it to have. There is no particular set of packages to "make" it a combo.

---

### Post by Wim Sturkenboom on 2012-09-07
Install the server and add a graphical environment. That way, you will not install stuff that you don't need.

---

### Post by arrrghhh on 2012-09-07
> **Wim Sturkenboom said:**
> Install the server and add a graphical environment. That way, you will not install stuff that you don't need.

This is potentially dangerous advice, as some people would misconstrue this as "apt-get install ubuntu-desktop" which is NOT right.

I found at first I wanted the GUI as a crutch/fallback, but found that with the overhead, headache of upgrades, and general insecurity from a GUI made me want to go CLI full time.  I haven't looked back, love every bit of it.

---

### Post by Bachstelze on 2012-09-07
> **AgentZ86 said:**
> Do they use the same repos too ? 

Yes.

> Basically I install the Desktop version on the rack mount server just to test the server for now, but which packages should I install to make it a complete server / desktop combo ? 

There is no rule as to what a "complete server" (or a "complete desktop") is. Install what you need.

---

### Post by cariboo on 2012-09-08
My suggestion would be to install a desktop, whether it be ubuntu, kubuntu. lubuntu or xubuntu, but don't install and of the desktop managers, gdm, lightdm, kdm etc, that way the desktop isn't started automatically when the system is booted. When you need to do something that needs a gui, just type:

```
startx
```

at the prompt to run the desktop, then when you're done just log out, and you're back at the prompt.

If you administer the system remotely, just install the gui applications you need and run them remotely via ssh:

```
ssh -X user@server
```

then just type the name of the app you want to run at the prompt.

---

### Post by AgentZ86 on 2012-09-30
thanks all

---

### Post by sysko on 2012-10-18
I found this post insightful.

Thanks 

:KS

---

### Post by Z.K. on 2012-10-19
> **Bachstelze said:**
> Yes, the only difference between the "server" and "desktop" versions are the packages installed by default. Once the system is installed, you can install any package you wnt (so you can install "server" packages on a "desktop" Ubuntu, and vice versa).

A lot of people consider it a taboo to install any "desktop" package on a "server". They are wrong, of course, use what you are most comfortable with (but please avoid Webmin).

Why don't you recommend webmin?  I have been using it for a number of years and have had no problems.  I don't use it often, but sometimes it comes in handy.  Mostly I just ssh into the server.

---

### Post by donniezazen on 2012-10-21
> **Bachstelze said:**
> A lot of people consider it a taboo to install any "desktop" package on a "server". They are wrong, of course, use what you are most comfortable with (but please avoid Webmin).

Can you please elaborate on why to avoid Webmin? Is there a better alternative? Or is command line recommended over webmin?

---

### Post by AgentZ86 on 2013-01-26
Old post reactivated
Thanks to everyone
.....

OK, I'm confused
I need some help with a few things

I installed the default ubuntu desktop, java update and now running it as a minecraft server
But the unity 3d effects are hogging everything up

What do I need to install the server stuff and just make it boot as a server?  And just startx as needed sometimes
Does webmin come with the server stuff by default ?

Will the desktop package that came with the default desktop be running and still bogging things down ? or will booting to the server mode / console solve that ? 

Thanks again

---

### Post by Cheesemill on 2013-01-26
To configure your machine to always boot in text mode just type the following command...
```
echo  "manual" | sudo tee -a /etc/init/lightdm.override
```Then whenever you want to use the GUI you can start it with the command...
```
startx
```

>  Will the desktop package that came with the default desktop be running  and still bogging things down ? or will booting to the server mode /  console solve that ?
No. None of the desktop packages will be running.
All they will do is take up room an the hard drive.

---

