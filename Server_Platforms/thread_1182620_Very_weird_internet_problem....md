---
title: "Very weird internet problem..."
date: 2009-06-09
forum: Server Platforms
---

### Post by the_sLiDe on 2009-06-09
Ok so here is the gist of the problem.

I set up my server a few months ago, with everything working fine.  Internet, etc... everything perfect.

Now, I left for Italy last week and I checked before I left that ssh was working etc etc.. no problems there.

Here is the weird part.

A few days ago I started being unable to connect to my server via ssh.  At all.

I started thinking maybe this is a problem with ssh etc etc...?  But I asked my family to hook up a monitor and keyboard to my server (was running headless) and check to see if anything was wrong.  This is very painful because I will be in Italy for the rest of the year and so I have to rely on my family to get the job done... and they don't know anything about Linux.

So, when the computer boots up I see a message that something has failed ( I don't know what, can someone point me in the right direction as to which log to check?).

I then say ok I don't know what it is but I'll make sure everything is ok, run apt-get update etc..

Turns out my computer is not even connected to the internet even though the cable is connected to the ethernet port, which in turn is connected to my router and then to my modem.  Keep in mind this was working fine until a few days ago... this kind of boggles my mind.

So what can I check to determine the problem? I am running Ubuntu Server 8.10.

Thank you in advance for your help!

---

### Post by macooper on 2009-06-09
The first thing is to get details of the error.  When Linux boots up, it keeps a log of everything that happens.  That log can be accessed using the dmesg command.  So if you get someone to login via ssh and run the command :
 
sudo dmesg | more
 
I'm not sure you need the sudo, but don't have a ubuntu server here to check, if you get them to page through that, it will likely allow you to identify the error.  If you can post the details of the error message here, it will help a lot in identifying the problem.
 
However, before you do, you might want them to do a full reset on your cable modem.  From time to time, cable modems do crash for no obvious reason.  Get them to shutdown your linux server and power down the cable modem.  Then start up the modem and wait for 5 mins (to give it time to startup properly) then boot the linux box and see if that brings it back online. 
 
Also, while they are checking the server, get them to check that the light on the back of the network card is flashing.  Although unlikely, it's always possible that it's a hardware failure.
 
Hope that helps.

---

### Post by the_sLiDe on 2009-06-09
Hey thank you for the quick response, I will try to skype over and give some more details!

---

### Post by the_sLiDe on 2009-06-10
Ok so the lights are on on the ethernet, so it is not hardware failure.  How do you scroll through once you have done sudo dmesg etc...?

Ok so the lights are on on the ethernet, so it is not hardware failure.  How do you scroll through once you have done sudo dmesg etc...?  By the way on my router it says the server is connected to it.

Ok so the lights are on on the ethernet, so it is not hardware failure.  How do you scroll through once you have done sudo dmesg etc...?

---

### Post by the_sLiDe on 2009-06-10
And I have been told they have seen the light flashing as of yesterday, this morning it was solid with no flashing though..?  This is so weird, anyways I'll post up whatever I find eventually..

---

### Post by ghen on 2009-06-10
the more command can be scrolled through with the enter key, if you use "less" instead of "more" you can use up and down arrows. 


when you want to exit the command, hit q. (might have to hit enter to get a prompt back)

both more and less are commands that help you with output that would normally go longer than your screen size. They both stop displaying the output from a previous command at the bottom of the screen and wait for the user to say its time to advance with the output.

so when you do 
sudo dmesg | less

you're running the dmesg command and then giving the output to the less command. (thats what the | does) the less command receives that output and allows you to browse through it with the arrow keys. (similar with more, but with the enter key)

---

### Post by the_sLiDe on 2009-06-13
Ok so when I try to connect on the LAN using 192.168.0.100 it says connection interrupted...?  Is it possible that it has somehow blocked some ports or something?  Or maybe the ISp?

---

### Post by the_sLiDe on 2009-06-13
Ok so I did dmesg | less and some things that jumped out were

acpi: pci interrupt irq.. 

upnp: bios pnp disabled (or something like that)

iomem error

I don't have the exact messages unfortunately, I had written them down but I don't know where they are..

---

### Post by E_K on 2009-06-14
what is the output of

ifconfig

and


ping [www.google.com](www.google.com)

(ctrl + c to stop)

---

### Post by the_sLiDe on 2009-06-14
there is no eth0, and ping don't work..

---

### Post by the_sLiDe on 2009-06-15
bump

---

### Post by the_sLiDe on 2009-06-16
bump

---

