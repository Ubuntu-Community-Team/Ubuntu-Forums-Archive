---
title: "Can't get back to Ubuntu Desktop"
date: 2008-03-06
forum: System76 Support
---

### Post by yuri06 on 2008-03-06
Linux beginner. Changed resolution, shutdown. Now when turn computer on - only getting terminal/shell command prompts? (not sure what correct terminology is). Can't get back to Ubuntu Desktop. What command(s) will get me back?

---

### Post by criskat777 on 2008-03-06
In terminal :

sudo nano /etc/X11/xorg.conf

then scroll down until u see your res and change it to what you want it 

then Ctrl+x then yes  

if that does not work you can reconfigure x from terminal no problem

and let me know if you have a video card so i can give you specifics on what to do

---

### Post by thomasaaron on 2008-03-07
Which System76 computer model you have? This will tell us what graphics card you are using, and we can give you model-specific instructions.

---

### Post by yuri06 on 2008-03-07
I haven't tried anything yet to fix this. It's the System 76 Pangolin Value model with Intel GMA x3100 graphics. Ubuntu G.Gibbon, 32 bit. 

When I turn the computer on, instead of loading to the Ubuntu desktop, I get the terminal (I think that's what it's called) that reads: [    11.586536] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3 then it reads "Loading, please wait....Kinit:  name_to_dev_t (then more info) then Kinit: trying to resume from (lists more numbers) then kinit:  No resume image, doing normal boot...then Ubuntu 7.10 ubuntu tty1 then ubuntu login:

Sorry, I'm very green. Not sure what info. will help the most.

---

### Post by thomasaaron on 2008-03-10
The "Resource Allocation" message has been there for years. We've never been able to determine that it actually affects anything.

From the terminal you end up in, run this command:
sudo dpkg-reconfigure xserver-xorg

In the resulting utility, choose ALL default options EXCEPT:
for the driver, select "intel"
for resolutions, select ALL of them (space bar selects, down-arrow moves down)
Choose "Advanced" when presented with that option and continue to select defaults.

When the utility is finished:
sudo reboot now

---

