---
title: "Need some advice on a home server setup."
date: 2012-12-10
forum: Server Platforms
---

### Post by AdamTherio on 2012-12-10
**What I want: **A file server (RAID 1), Mumble/Teamspeak/Ventrillo server and it to have a GUI for me to remote connect to and needed as this may become a media PC for my TV. Security is of NO concern.

**What I have:** A 16gb i7 board with 1 120gb SSD and 2x 1TB drives. Its my old gaming box.

**My issue this far:** It seems im working against the flow here, The server image had no GUI and im assuming its going to be alot of work to install one. So I went with a desktop version but now it wont boot without a monitor.

**My question is**, Is there something better i should be doing here? How do i boot without a monitor? I googled a answer but it dosent work post v10.

---

### Post by drdos2006 on 2012-12-10
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb

Install with :
sudo dpkg -i webmin_1.590_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Remotely edit files, create shares, startup daemons etc..

regards

---

### Post by AdamTherio on 2012-12-10
Thanks, reading now... Also i had no idea there was a program for a web interface. Very cool.

---

### Post by tgalati4 on 2012-12-10
If your server is running 24/7, you won't be booting that often, so you could run the desktop version and use the TV as a monitor, either through vga port or hdmi.  You just need to make sure the TV is on when you boot.  The advantage of using the desktop version is you get all of the media goodies that you will need for a media PC, plus it can run all of the file, print, and web services that you need.

To get a full remote desktop, use ssh:

ssh -2 -Y username@machinename
gnome-panel

You may have to change the gnome-panel command to whatever desktop environment you are running.

If your throw-away, old, gaming box is a 16GB i7 machine, what is your new and shiny gaming machine?

---

### Post by mastablasta on 2012-12-11
> **AdamTherio said:**
> Thanks, reading now... Also i had no idea there was a program for a web interface. Very cool.
 
 
there are plenty web interfaces. there are also distributions that come with their own GUI web interfaces such as for example Openmediavault (dedicated to media server), Zentyal (small business server), ClearOS (small business server)... and many others. 
 
actually to install a desktop to server it is really simple. it's a one short command. for example to install ubuntu desktop you would type:
sudo apt-get install ubuntu-desktop
 
tpye in you user password and it will install it.

---

### Post by Elfy on 2012-12-11
*Thread moved to **Server Platforms**.*

---

### Post by AdamTherio on 2012-12-11
> **tgalati4 said:**
> If your server is running 24/7, you won't be booting that often, so you could run the desktop version and use the TV as a monitor, either through vga port or hdmi.  You just need to make sure the TV is on when you boot.  The advantage of using the desktop version is you get all of the media goodies that you will need for a media PC, plus it can run all of the file, print, and web services that you need.

To get a full remote desktop, use ssh:

ssh -2 -Y username@machinename
gnome-panel

You may have to change the gnome-panel command to whatever desktop environment you are running.

If your throw-away, old, gaming box is a 16GB i7 machine, what is your new and shiny gaming machine?

Thats what im planning in doing I think, but i dont have much time for tv anymore. That ssh command is typed in the terminal of another linux box? Im just using putty on windows as linux is very hard to game on.

That brings me to why a i7 16gb isnt good enough. I moved from 12 EvE Online accounts to 20 using isboxer. 20 MMO's at low settings requires 25 some gb of ram. Im SLI'ing 2 680 atm with 32 gb and a overclocked i7-3770s @ 4.1 ghz (H60 cooler), 3x raid 0'ed intel 240gb drives, sadly tho its all out of commission as i have to special order a PSU for it and the monitor mounts.

> **mastablasta said:**
> there are plenty web interfaces. there are also distributions that come with their own GUI web interfaces such as for example Openmediavault (dedicated to media server), Zentyal (small business server), ClearOS (small business server)... and many others. 
 
actually to install a desktop to server it is really simple. it's a one short command. for example to install ubuntu desktop you would type:
sudo apt-get install ubuntu-desktop
 
tpye in you user password and it will install it.

Thanks! So if I install the desktop it automatically boot into the GUI or do I need to startx every time?

> **Elfy said:**
> *Thread moved to **Server Platforms**.*


My bad.

Edit: was gunna take a pic of my "battle station" but them the wife whent full retard about privacy.

---

### Post by mythic97 on 2012-12-11
Just a point a home server cost a heck of alot in electrical bills so be warned it will cost you alot

---

### Post by CharlesA on 2012-12-11
> **mythic97 said:**
> Just a point a home server cost a heck of alot in electrical bills so be warned it will cost you alot
Depends on what you using it for and what hardware is used.

The i7 I am running hasn't really increased the electric bill for me. The air conditioning in the summer killed it more than the server.

---

### Post by chadk5utc on 2012-12-11
+1
> **CharlesA said:**
> Depends on what you using it for and what hardware is used.

The i7 I am running hasn't really increased the electric bill for me. The air conditioning in the summer killed it more than the server.

I agree with the heat/air

heres a good ref: [http://www.willsmith.org/climatechange/domestic.html](http://www.willsmith.org/climatechange/domestic.html)

---

### Post by tgalati4 on 2012-12-11
Wow, so playing ~20 instances of MMO's requires 25GB of RAM?  I guess 2nd Life wasn't good enough.  Now we are into 3rd Life.  There's a YouTube video that shows 6 TB of SSD's strung together that gives you the equivalent speed of 6 TB of RAM.  At some point we will reach the singularity that unbalances the master equation.

---

### Post by AdamTherio on 2012-12-11
My house is mostly solar/wind powered, except the 3 phase welder. Thanks for your concern tho sir!

> **tgalati4 said:**
> Wow, so playing ~20 instances of MMO's requires  25GB of RAM?  I guess 2nd Life wasn't good enough.  Now we are into 3rd  Life.  There's a YouTube video that shows 6 TB of SSD's strung together  that gives you the equivalent speed of 6 TB of RAM.  At some point we  will reach the singularity that unbalances the master equation.


Actually there where "ram drives" that i experimented with before I got the first SSDs. The downside was that it had to stay on.

---

