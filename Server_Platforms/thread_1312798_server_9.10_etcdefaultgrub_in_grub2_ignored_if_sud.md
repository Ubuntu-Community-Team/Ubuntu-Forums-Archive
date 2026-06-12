---
title: "server 9.10: /etc/default/grub in grub2 ignored if sudo reboot not used"
date: 2009-11-03
forum: Server Platforms
---

### Post by Jason Heblack on 2009-11-03
Doesn't boot -server 9.10: /etc/default/grub in grub2 ignored if "sudo reboot" not used

Steps to reproduce
1. install ubuntu server 9.10 from the CD
2. remove CD
3. login
4. edit /etc/default/grub to put in a timeout (GRUB_TIMEOUT="0") 
5. at the command line, enter "sudo update-grub2"
6. at the command line, enter "sudo reboot"
7. observe that the timeout from Step 3 was used
8. remove the power cord to simulate a power failure

Actual results
The default grub menu screen is displayed at power up and does not go away no matter how many times the computer is rebooted. The timeout set in Step 4 is ignored. If a menu option is selected at that grub screen, then the server can finish starting up and a user can login. 

Expected results
User should not have to manually enter a menu option at power up to get server running.

Issue notes
After login, user can do "sudo reboot" to get the timeout from Step 4 to be used. The timeout was set so that if there was a power failure, then the server can get past the grub splash screen without a user being there or having a monitor connected.

---

### Post by DaBiTo on 2009-12-01
Im having the same issue, is there any workaround for this bug?

Edit: installed acpid module and so far on my tests, it solved the issue

---

### Post by Jason Heblack on 2009-12-01
There is an open ticket about this bug in the official bug tracking system that ubuntu has. I don't have the steps for how to log on to that system to read what is there about this bug. What I did to fix was downgrade from 9.10 to 8.04 LTS... Long term support (lts) is re-released every few years rather than twice a year and is less buggy supposedly.

You can try to find a similar ticket here - keyword 'grub2'
[http://bugs.launchpad.net/ubuntu/](http://bugs.launchpad.net/ubuntu/)

If you find the 'official' fix, maybe post it here. I had 'fixed' the problem by downgrading... Hope this helps.

---

### Post by Vegan on 2009-12-01
You should not be mucking with Grub, use....


sudo apt-get update
sudo apt-get update

and if anything is held back, name it directly.

Then no problems with anything.

---

### Post by bpollen on 2009-12-06
> **Vegan said:**
> You should not be mucking with Grub, use....


sudo apt-get update
sudo apt-get update

and if anything is held back, name it directly.

Then no problems with anything.

How does running "sudo apt-get update" twice fix grub?

---

### Post by martinrame on 2009-12-14
I think he wanted to write:

sudo apt-get update
sudo apt-get upgrade

Leonardo.

---

### Post by executivul on 2009-12-19
I confirm having the same issue
After a forced shutdown (power loss) Grub waits at the menu ignoring the timeout options, some sort of "do you want recovery or normal boot?"
Ubuntu 9.10 Karmic, installed via the network, no updates available yet.

Waiting for news.

---

### Post by dwp0980 on 2010-01-22
I just had this issue too.  Shows how often I turn the power off on my server!  I think the bug has been fixed, but it didn't do a full fresh install of grub following the update, so it doesn't actually fix it automatically.  After reading about the bug in launchpad, I did the following to fix. . .

```
sudo grub-install /dev/sda
```

Assuming /dev/sda is where you install grub normally.  Then. . .

```
sudo update-grub
```

Hope this helps someone.

---

