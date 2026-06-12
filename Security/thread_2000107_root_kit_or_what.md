---
title: "root kit or what?"
date: 2012-06-09
forum: Security
---

### Post by CongoJim on 2012-06-09
Computer running XP wouldn't boot properly. I pulled out my trusty USB with a live install of 12.04 (remastersys copy with avast and clam on it) to boot it up. Put in username as normal and no password as usual and got incorrect password. I know I didn't add a password. Tried it in another computer and it didn't work, stuck in the startup. Did a new install on USB using the original iso of 12.04 i386 and it booted to the page would I like to try it or install? I clicked try it and it went to the signin page again and I got wrong password there as well. None of the installs go to the grub screen either so I can't do a no password boot. I tried copies of 11.10 and 11.04 same thing. What is on this computer and how to get rid of it. As I write this I am downloading the 400.vps for avast and have pulled the hard drive to be scanned on another computer.

---

### Post by Ms. Daisy on 2012-06-09
I'm not seeing anything that would lead me to conclude you've got a root kit, not sure what it is you're seeing that led you there.  

When you install Ubuntu you set up a user account, and that user has a password.  I don't *think* you can leave the password blank.  So it appears that you have forgotten or didn't realize you had a password on the live USB.  To reset it, use this 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

As for the XP computer not booting properly, perhaps you've got bad sectors on your hard drive?  You can use the Ubuntu Live USB to look for those.

---

### Post by CharlesA on 2012-06-09
I thought the default password was "ubuntu" ?

Or some such thing. I haven't tried booting a remastersys install before but as far as I know remastersys just packages a current install into an ISO you can burn. Any passwords that are set remain unchanged.

See here:
[http://serverfault.com/questions/26185/whats-the-default-username-and-password-for-an-ubuntu-live-cd](http://serverfault.com/questions/26185/whats-the-default-username-and-password-for-an-ubuntu-live-cd)

---

### Post by CongoJim on 2012-06-12
When you make a remastersys iso and install on the USB there is no password, I've done this dozens of times. I'm the Pied Piper of Ubuntu in my part of the Congo. Something is changing the user name or adding a password during the boot and that is beyond my skills and I'm hoping someone knows what could do that. It doesn't matter what version I use nor even a clean version freshly downloaded. With the clean version I could get into install but it fails on grub install.

---

### Post by bodhi.zazen on 2012-06-12
> **CongoJim said:**
> When you make a remastersys iso and install on the USB there is no password, I've done this dozens of times. I'm the Pied Piper of Ubuntu in my part of the Congo. Something is changing the user name or adding a password during the boot and that is beyond my skills and I'm hoping someone knows what could do that. It doesn't matter what version I use nor even a clean version freshly downloaded. With the clean version I could get into install but it fails on grub install.

If you want to make custom live ISO, done right, learn to use the live scripts

[http://live.debian.net/](http://live.debian.net/)

To change the default user name and password you have to edit the casper scripts

See also 

[http://uck.sourceforge.net/](http://uck.sourceforge.net/)

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

