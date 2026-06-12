---
title: "HOWTO: Workaround ipw3945 freeze (cmd #07 failure)"
date: 2007-12-17
forum: System76 Support
---

### Post by DBO on 2007-12-17
NOTE: My laptop has been stable with this hack for two days thus far.  It seems to be a proper fix, but only time will tell as sometims this bug can lay dormant for several days.

the intel ipw3945 driver causes issues on some laptops that will result in freezing the driver all together.  This causes (in some way) your session to break (to launch an app, you must use --sm-disable) and to prevent sudo from working which makes fixing the issue somewhat difficult.  These two conditions make this a rather serious bug in my eyes, and a bug I experienced literally within 20 minutes of first turning my laptop on from System76 *evil glare*.

I have been able to work out a procedure to get the iwl3945 driver working as well as the ipw3945 driver, including suspending and resuming with it.  So if you are having issues with your wireless freezing up read on.

For those with some idea of what they are doing: (procedure in a nutshell)
- Blacklist ipw3945
- add iwl3945 to /etc/modules
- Make a script in /etc/acpi/resume.d/98-nm-restart.sh that does the following
--- /etc/dbus-1/event.d/25-NetworkManager restart
--- /etc/dbus-1/event.d/26-NetworkManagerDispatcher restart
- Reboot your computer (note your wireless LED may end up being a casualty of war here)

I will provide more detailed instructions in a day or two when I get home.  I just know I am not the only one who experiences this issue and wanted to get a fix out there.

p.s. - The following fixes to not work!

- Setting irqpoll as a boot option
- Setting the led=0 param for ipw3945 module
- Disabling NetworkManager
- Manually configuring the interface
- Several others I tried and can no longer remember

---

### Post by Trevor Bramble on 2007-12-20
Subscribed.  Thanks for documenting this.  I've had my Serval just under a week now and while I'm largely very happy with it, this behavior is driving me insane.

I'll give this a go and follow up with my results.

---

### Post by R. McC on 2007-12-25
Can you elaborate what you mean by 'wireless freezing up'?  Does it resemble what I describe [here](http://ubuntuforums.org/showthread.php?t=625916) by any chance?

---

### Post by DBO on 2007-12-25
Sorry R. McC, different issue.  Still I would give it a go, it might fix it anyway.

---

### Post by thomasaaron on 2007-12-26
DBO,

Please post the output of cat /var/log/messages immediately after a freeze.
Also, what System76 model do you have?

If it is a black Gazelle Value or a white Darter Ultra, the problem might be firmware related, and I have the fix for it.

---

### Post by DBO on 2008-01-07
> **thomasaaron said:**
> DBO,

Please post the output of cat /var/log/messages immediately after a freeze.
Also, what System76 model do you have?

If it is a black Gazelle Value or a white Darter Ultra, the problem might be firmware related, and I have the fix for it.

its a black and white gazp5 if that helps at all.  As for the message output, Ill post it next time it happens.  iwl3945 as it turns out has different, equally annoying issues...  I am not very happy with the wireless right now...

---

### Post by rumblered on 2008-01-07
I had this same issue on my gazv5, and also solved it by switching to iwl3945. Of course, being a bleeding-edge user, I'm on AMD64 hardy and here that driver works pretty well. You could grab Hardy's 2.6.24 kernel and use that, or compile a 2.6.22 kernel with the latest iwl3945 code patched in.

The first option, I must warn, has two issues to be aware of. First, the power manager will see two batteries instead of one. This is because HAL (even in Hardy) needs to be updated for a change in 2.6.24. Second, Bluetooth SCO (headset support) doesn't work right with the built-in Bluetooth module. The rest of Bluetooth is working, though.

---

### Post by hbb on 2008-01-07
DBO, I tried your workaround, but it seems not to work for me. I blacklisted ipw3945, added iwl3945 to the modules file, and created the script you mentioned.

Upon reboot, my wireless connection is indeed using iwl3945, but it simply doesn't find the network. If i switch things back, it obviously works just fine (otherwise it would be hard to post this;)), but I'm not really sure why your workaround didn't work for me. Hopefully you can at least point me in the right direction (sorry, I'm a tad clueless as I've never had wifi issues before)

For reference, I'm using a Serval laptop with Gutsy (I don't think the specific options I chose, such as 2 GB of RAM vs. 1 GB, are really relevant, so I won't rattle them off here).

Any help would be greatly appreciated. Thanks!

---

### Post by Hero of Time on 2008-01-14
I have a question about this too. I removed the restricted modules package and lost my wifi driver (obviously it's in there) and would like to load the iwl3945 driver, since the Hardy kernel also uses this driver. However, with the Hardy kernel, I can't get wpa_supplicant to work. It gives an error about using WEXT, the driver for wireless.

So, how to use iwl3945 with wpa_supplicant and hidden ssid?

---

### Post by Trevor Bramble on 2008-01-21
As a follow-up to my earlier post, this issue hasn't come up again for me but for one time about a week ago, and I was too busy to stop and troubleshoot.  I can say that it was during a heavy file transfer, but that's all.

I'm also using ethernet almost as often as wifi, so that has something to do with dodging the bullet, I'm sure. =^)

---

### Post by Squish on 2008-01-25
Well, I want to learn, so I gotsa ask questions:
- Blacklist ipw3945
- add iwl3945 to /etc/modules
- Make a script in that does the following
--- /etc/dbus-1/event.d/25-NetworkManager restart
--- /etc/dbus-1/event.d/26-NetworkManagerDispatcher restart
- Reboot your computer (note your wireless LED may end up being a casualty of war here)

What do you mean by blacklist?
By adding the module, just means pasting iwl3945 at the bottom, causing this to be a boot up item - is this correct?
The script leaves me clueless - how am I supposed to make one, and where...?

I have a serval performance. This is indeed a bug, but has it been reported?

---

### Post by thomasaaron on 2008-01-28
To blacklist a module, you add it to the /etc/modprope.d/blacklist file.
To add the iwl3945 module, you add it to the /etc/modules file.

You can do both from the command line by running these commands.

echo blacklist ipw3945 | sudo tee -a /etc/modprobe.d/blacklist
echo iwl3945 | sudo tee -a /etc/modules 

As for the script, run this command to see if it exists...
locate /etc/acpi/resume.d/98-nm-restart.sh

If it does exist, open it with:
sudo gedit /etc/acpi/resume.d/98-nm-restart.sh
...and add these lines to the bottom of it:
/etc/dbus-1/event.d/25-NetworkManager restart
/etc/dbus-1/event.d/26-NetworkManagerDispatcher restart

If it doesn't exist, create it with:
sudo touch /etc/acpi/resume.d/98-nm-restart.sh

Then open it with:
sudo gedit /etc/acpi/resume.d/98-nm-restart.sh
...and add these lines to it...
/etc/dbus-1/event.d/25-NetworkManager restart
/etc/dbus-1/event.d/26-NetworkManagerDispatcher restart

Then make it executable with:
sudo chmod a+x /etc/acpi/resume.d/98-nm-restart.sh

---

### Post by Squish on 2008-01-29
Thank you so much - heres to hoping it works!

---

### Post by thomasaaron on 2008-01-29
No problem. You'll need to restart your computer afterwards, btw. You probably knew that, but...

---

### Post by Squish on 2008-01-30
Well weird issue now


I can connect to my router wirelessly... but I cannot access the internet. I also seem to have an extra connection in my connection manager that wasnt there before... 2 ethernets, a modem, and now this weird Ipvwhatsit thing...
The manager is giving me 4 bars... but no internet access. its weird.
I dont mind doing a reinstall... Ive been thinking of beta testing hardy. I had fun beta testing before so it cool. Backing up files is no problem, I just need to find a way to keep my deluge torrent list in tact. I have over 100 torrents, and it took me like 7 hours to get all of em.
anyways, either or solution is fine.
This issue is so strange though... I wish I could understand just what is going on here...?

It stopped working after I restarted. My computer is a bit fickle though, so it doesnt surprise me. lol, it doesnt even give me a gdm anymore - straight to commandline. Funny that I actually prefer it that way:lolflag:

---

