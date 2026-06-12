---
title: "Uninterrupbtible Power Supply (UPS) for Ubuntu Server"
date: 2009-11-15
forum: Server Platforms
---

### Post by garfonzo on 2009-11-15
As we roll into the winter weather, my area has a lot of rain/wind/thunder storms (thankfully little to zero snow!). We've already had two power outages in the past two weeks and I believe this will be a common occurence (my neighbourhood isn't in a great power supply area).

When the power fails, the only saving factor at thie time are the surge protectors I have everything plugged in to. However, I want a better solution for the server.

Enter a UPS.

I'm looking at the APC products becuase they seem to get a lot of praise for their quality and ability to switch to battery without a hitch and power the system down. However, I'm not sure about their Linux support. I would need the UPS to tell the computer to turn off when there is a power failure. 

My server is a simple desktop computer (newer specs) and is headless, running Ubuntu server edition in the garage. I have a few HDDs dangled off of in USB cases, but they can stay on a surge protector. It's the proper shutdown of the Server that I want. 

What have you done for a UPS solution specific to Ubuntu Server edition? Do you use the "NUT" package or some other software? Is APC the way to go, or some other brand?

Thanks!

---

### Post by windependence on 2009-11-15
[http://www.refurbups.com/](http://www.refurbups.com/)

Almost all of them come with a disk with software for Unix/Linux. If not there are some programs out there to do it. Not sure of the names though.

-Tim

---

### Post by gordintoronto on 2009-11-15
APCUPSD is in the repositories.

---

### Post by garfonzo on 2009-11-15
> **gordintoronto said:**
> APCUPSD is in the repositories.

Anyone have experience with the APCUPSD package? Which APC UPS do you have?

---

### Post by AMuze on 2009-11-15
hi,

i'm using an APC ES 750 with USB connection. It works well and is easy to setup with apcupsd. The only really hidden thingie is that you have to set ISCONFIGURED=yes in /etc/default/apcupsd. Do that after you configure the settings (cable type etc) in /etc/apcupsd/apcupsd.conf.

It worked pretty easily for me. I don't run a web server so I did not install the cgi files, if you want a GUI install gapcmon, it's pretty nice.

--A

---

### Post by garfonzo on 2009-11-15
> **AMuze said:**
> hi,

i'm using an APC ES 750 with USB connection. It works well and is easy to setup with apcupsd. The only really hidden thingie is that you have to set ISCONFIGURED=yes in /etc/default/apcupsd. Do that after you configure the settings (cable type etc) in /etc/apcupsd/apcupsd.conf.

It worked pretty easily for me. I don't run a web server so I did not install the cgi files, if you want a GUI install gapcmon, it's pretty nice.

--A

Awesome! Thanks for the tips. I just got home from purchasing the same model. It is currently charging and I hope to set everything up tomorrow. I'm leaving the server unplugged until this unit is ready. 

Thanks for the help!

---

### Post by AMuze on 2009-11-15
these are my config files, if you see an error please let me know. I had to ad .txt to end of file to get it to attach in this forum. And don't forget to attach the battery wires, they come disconnected, just an FYI.

Oh, and if you know how to get LVM on RAID1 working correctly on 9.10 please ping me, I can't get it to work after I reboot my system.

--Amuze

---

### Post by Noah0504 on 2009-11-15
I have an APC 550.  Works perfectly with my Ubuntu server and keeps it running when, or at lease allows it to shut down properly whenever the power goes out.  Love APC.

---

### Post by BulletTootg on 2009-11-16
> **Noah0504 said:**
> I have an APC 550.  Works perfectly with my Ubuntu server and keeps it running when, or at lease allows it to shut down properly whenever the power goes out.  Love APC.


Our servers run on two [APC Smart-UPS 1500]("http://excessups.com/smartups-1500-sua1500-p-38.html")'s. We get good power filtering, avr boost/drop, sinewave output and we get 16-20 minutes per UPS. We used to use the smaller CS series but they were too small once we upgraded, plus the simulated sine wave didn't agree with the power supplies.

Love APC

---

