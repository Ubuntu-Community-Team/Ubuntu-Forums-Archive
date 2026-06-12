---
title: "Samba printer problems"
date: 2006-08-01
forum: Server Platforms
---

### Post by Flavian on 2006-08-01
Hi Folks
I am pretty new to the whole Linux-Server thing.
My printer I use is a HP PSC 1219 printer, the driver is supported in Linux.
I got it to work without a problem, just set up a Samba printer share and that's it.
I can print from my Ubuntu Laptop but when I want to use the printer in windows it says that the server can not provide the needed Printer drivers.
How do I set up a DRIVER REPOSITORY propperly?

I NEED to get the printer to work in windows as well, since my Dad and my brother both use windows.
I tried installing the driver in windows, but it does not show up in the drivers list, so I can't choose it...

Can someone help please?

Flo

---

### Post by daverx on 2006-08-02
i'm looking for a howto on setting up a samba print share... can you point me in the right direction?

---

### Post by Flavian on 2006-08-05
@daverx, just search on the board, I believe I have seen some around here.
Google should give you some good ones as well.

Does anyone know something about the problem I have!
It's really urgent!

Thanks in advance
Flo

---

### Post by chrisfay on 2006-08-05
Is the printer directly connected to the Windows machine or the Ubuntu?

I found it easiest to connect the printer to my Windows machine, then "share" the printer. Use samaba's printer add on option and go through the options it requires for finding your printer. Worked for me...

---

### Post by Flavian on 2006-08-06
Hi chrisfay
My printer is connected to my Linux machine, since my Linux machine is my server.
It should share the printer for ALL the clients in my network
1x Linux client
2x Windows clients

that was my idea.
Now, what do you mean with connecting it to your windows box and then...?
I couldn't understand what you meant.

Thanks for your help
Flo

---

### Post by chrisfay on 2006-08-06
I have two computers:

1.Windows (for whatever my wife needs to do that she can't in linux)

2.Ubuntu (Web,FTP,DNS,Samba,Mail server)

They are both connected behind a Linksys Wrt5g router with static ip's running on the same Workgroup. 

In order to have both these computers print to my HP PSC1510 I first connected it directly to my Windows machine to make sure it prints. Then, in Windows, I found my printer in the "printers" section and right clicked it. I found the option to "share this printer" and chose that.

Then, in Ubuntu, I went into the samba options where you can choose your shares. I chose the option to add a printer and followed the prompts. I can't remember exactly what it asked for but basically:

-The workgroup
-The IP the printer resides on (i'm pretty sure)
-It asked if I wanted to install my own drivers for the printer  which I chose no and let Ubuntu use the defaults. 
-It then asked me to choose my make and model of printer (I believe for driver default puposes)

That was it, I was able to access my printer from Ubuntu and print to it, while still being to print directly to it from my Windows machine. 

Like I said, I don't remember the exact options but you get the idea.

---

### Post by Flavian on 2006-08-06
Oh okay, so you have it all connected to your WINDOWS machine.
Seems like this printer doesn't work with a linux server, eh?
Dang it :/

---

### Post by chrisfay on 2006-08-06
Have you tried it the other way around just to see if your linux machine could see it?

---

### Post by Flavian on 2006-08-06
Yapp that works perfectly.
It is just that I had windows running on my old server and the funny thing was that windows decided out of the blue not to show the printer anymore.
Or the spooler just hung up and I had to reset the server, which is very very annoying!
So I decided to switch to Linux, now I encountered that sharing the printer is not that of an easy task to do :(

I hope someone has ideas how to set up the printer propperly to get it to work in Linux for windows

---

### Post by compunuts on 2006-08-08
Instead of using Samba for printing, you should use IPP (Internet Printing Protocol) since it's easier to set up and prints a lot faster.

Make sure you can locally print to your printer. Then in Windows, set it up to use Internet address and put in "http://<your.ip.addy.here>:631/printers/<your-printer-name> and that should so it. If you need detailed help, I can post it somewhere on the net for you when I have more time. LMK.

---

