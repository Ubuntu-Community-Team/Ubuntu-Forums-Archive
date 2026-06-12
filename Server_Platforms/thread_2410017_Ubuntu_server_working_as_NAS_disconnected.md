---
title: "Ubuntu server working as NAS disconnected"
date: 2019-01-10
forum: Server Platforms
---

### Post by szlapy on 2019-01-10
Hi, 

Several years ago I set-up an Ubuntu-server with few hard drives connected to my home network. Only local access was configured.

Everything was fine since February 2014 when I set it up. I didn't do anything just used it. I know I could make updates, but I didn't assuming that if it's working the way I want there is no need to fix anything. 

Yesterday I saved some files on the NAS, did something else and when returned to my windows 7 laptop I got a message that an error occured while reconnecting to the disks. When I try to ping the server the message read "Destination Host Unreachable".

The server runs of an USB stick and I thought that after almost 5 years the stick gave up. I had an image of the USB stick and clonned this to a new one hoping that this will solve the problem. (Tested the image back in 2014 and each USB that I clonned with this image run nicely as expected.) Unfortunately this time round it didn't.

I thought this may be my home router, so I checked the static IP address that had been allocated to the server - nothing changed there. I rebooted the router, still nothing.

I'm now lost.

Any suggestions? How can I get it back working again?

Cheers, Piotr

PS I don't even know (remember) which version of the Ubuntu server I installed. But it must have been one LTS version current in Jan / Feb 2014.

---

### Post by mastablasta on 2019-01-10
if the image is good you can use it to restore the settings. /etc, /home /var will be the needed folders.

then it is time for a fresh install.

after initial setup, you can look at the old settings and some things can be just moved to the newly setup OS. some commands may need to be copied into files (e.g. if config files changed a lot).

then setup unnatended updates.

I have a similar setup.

I use Ajenti for administering and setting up the server (much nicer text editor than nano or others), ssh (for sFTP connection and data transfer to server), owncloud (hope to replace with nextcloud soon), fail2ban and unnatended updates.

also, you didn't say what was not working upon image restore. you might need to attach a monitor to be able to see what is actually happening on server and be able to troubleshoot.

---

### Post by darkod on 2019-01-11
Before starting anything else you should confirm what actually is the problem. Why creating new sticks or images or restore of settings if that is not the issue?

I don't see anywhere in your post mentioned whether you tried to attach a monitor and keyboard to the server and see what is going on. Did you do that? Any helpful messages on screen?

---

### Post by szlapy on 2019-01-12
Hi,
As suspected by darkod the problem was elsewhere - one of the switches in the daisychain. The leds on the switch showed all connected ports as working. I restarted the switch more than once but it didn't help - the switch appeared to be working fine, but there was no connection to the server. Then I tried using backup sticks and it didn't help either. I thought that before I drag a screen + keyboard to the server I replace the switches one by one with a spare one I had. This seemed easier to do considering location of the server. Bang! this was the problem. Replaced it and now all is back to normal.

---

