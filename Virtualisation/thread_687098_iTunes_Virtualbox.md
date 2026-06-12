---
title: "iTunes Virtualbox"
date: 2008-02-03
forum: Virtualisation
---

### Post by myusername on 2008-02-03
i am running gutsy with windows xp pro in virtual box for my ipod touch (because i like my album artwork) and i keep getting this error from itunes saying it could not connect to my iphone...and i don't know why its saying that because i have an ipod touch

so if there is anyway to get this to work or if i could use another way and still be able to have my album artwork and be able to transfer videos and music could you please tell me?? i really hate using windows


see pic for error

---

### Post by p_quarles on 2008-02-04
There are some steps you will need to take prior to using USB devices with Virtualbox machines:
[http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices](http://doc.gwos.org/doku.php/doc:office:virtualbox#enable_usb_devices)

---

### Post by myusername on 2008-02-04
thanks but I've already done both of those

EDIT: I have also tried using winamp for my iPod using mlpod and its like the windows vm isnt recognizing it... But virtual box says its connected

Any help?

---

### Post by ntetreau on 2008-02-04
If you only need iTunes so you can enjoy your album art, there is no need to go through all this trouble.  I use Amarok and gtkpod with my iphone and both give me album art.  

Check out and follow this wiki to set it up:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by myusername on 2008-02-05
i dont like doing that... it is too buggy

---

### Post by stanger192 on 2008-05-03
i had the same issue with a ipod shuffle

turning off usb 2.0 in the vm worked for me

---

### Post by Skol312000 on 2009-03-19
I just need a full way to work itunes on ubuntu 8.10 so i can sync/update my iphones OS... Evrrywhere i sesrch this doesnt clearnit up... What should i do?

---

### Post by SentientFluid on 2009-04-14
> **myusername said:**
> i am running gutsy with windows xp pro in virtual box for my ipod touch (because i like my album artwork) and i keep getting this error from itunes saying it could not connect to my iphone...and i don't know why its saying that because i have an ipod touch

Is your Touch connected directly to the computer or is it connecting through a USB hub? If a USB hub, does it work when directly conencted?  Does Gutsy mount the Touch? Do other iPods work?

Another thought, did you enable USB 2.0 (EHCI) in your VM?

---

### Post by jrd2 on 2009-04-19
This may or may not be of any help to anyone but I thought I'd give connecting my iPhone through Virtualbox ago. So far it looks like it's working. I'm as far as "backing up iPhone" in iTunes.

So I guess I'm just confirming that it can be done.

Some more details:

* I'm using Jaunty release candidate.
* I was using Virtualbox OSE but as this doesn't have USB support I removed. I then added the repository for the closed source version (v2.2.0) and installed that. Make sure you enable the USB.
* The guest OS is WinXP

Everything just worked. The backing up is a bit slow but from what I can remember it is pretty slow on a Mac too.

Also, check out Handbrake for converting video to the iPod format. I'm doing my first convert now so can't give confirmation just yet, but it's easy use and advertises iPhone/iPod support.

---

### Post by lex0429 on 2009-06-18
Just in case someone stumbles here. I can confirm that i have had the following setup working for a while now...

8.04 
vbox 2.2.4
xp
itunes
iphone 

one caveat, do not upgrade to 3.0 software with this setup, you will need to use a native install of XP. After the upgrade started and the iphone rebooted the system could no longer see it. i had to go into a normal XP, restore to factory defaults, apply the upgrade, then went back into my ubuntu/virtualbox xp and restored the backup it took right before the upgrade...long story it did work but not the best way to do it.

---

### Post by ogoforth on 2010-09-13
I am running Ubuntu 10.04 with VirtualBox v3.2.8 and a Microsoft XP Pro virtual machine.  On that XP Virtual machine I have the latest iTunes v10 installed and running without any problems.  It works 100%.  Can even sync Outlook information to the iTouch.

---

### Post by renebs on 2011-02-17
I am using:
Ubuntu 10.04
Itunes: 10.1.1.4
Virtualbox 3.2.12
ipod: touch 4g. 

Everything works in my setup. But it could not be any more slower, or more buggy. 

Things that make itunes crash, among many others: stop syncing in the middle, adding music folders to the library.

If you have a setup that works well can you reply with your configuration and tips?

---

### Post by nathan28 on 2011-04-23
Bump. Going to try this with an OSX virtual box. (b/c I want to upgrade my wife's phone w/out playing a bunch of dd nonsense).

Not really sure how to get OSX to 'see' the music on an ext4 external HDD, or even just in my /home partition in ext4. How do you get an virtual disk image to to see files on a true (well, logical) disk?

---

