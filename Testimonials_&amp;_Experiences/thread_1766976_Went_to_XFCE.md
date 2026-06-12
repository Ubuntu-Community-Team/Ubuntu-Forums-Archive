---
title: "Went to XFCE"
date: 2011-05-25
forum: Testimonials &amp; Experiences
---

### Post by and1bskbl72 on 2011-05-25
I am having a problem accepting Unity. The main issue for me is the loss of time navigating without the standard menu so I installed XFCE for about 80 megs of space and like it. It suits me for now we will see what happens when 11.04 comes out. 

I am really waiting on the ability to move the taskbar. The left side stationary was getting annoying.

---

### Post by Bucky Ball on 2011-05-25
I love Xfce on 10.10 (or any release!). Lots of custom shortcut keys, easy and fast. I generally install Ubuntu then Xfce (or the other way around) and have packages from both. It's about how you like to compute. Great thing about Linux is you have lots of options to try til you get it 'just nice'. Enjoy!

---

### Post by Nyromith on 2011-05-25
I'm glad that more and more people discover this wonderful project. Maybe Unity isn't that bad after all :)

---

### Post by 3Miro on 2011-05-25
> **Bucky Ball said:**
> I love Xfce on 10.10 (or any release!). Lots of custom shortcut keys, easy and fast. I generally install Ubuntu then Xfce (or the other way around) and have packages from both. It's about how you like to compute. Great thing about Linux is you have lots of options to try til you get it 'just nice'. Enjoy!

10.10 comes with xfce 4.6, 11.04 comes with 4.8. The new 4.8 is much better, you should give it a try.

---

### Post by 3rdalbum on 2011-05-25
> **and1bskbl72 said:**
> I am having a problem accepting Unity. The main issue for me is the loss of time navigating without the standard menu so I installed XFCE for about 80 megs of space and like it. It suits me for now we will see what happens when 11.04 comes out. 

I am really waiting on the ability to move the taskbar. The left side stationary was getting annoying.

You can make it "intellihide", so it's hidden whenever any program would overlap it, and then you can show it by slamming your mouse against the left of the screen or by pushing it into the top-left corner.

---

### Post by mastablasta on 2011-05-25
how is the file sharing setup? is it easy? all working out of the box?
 
KDE had a required package missing on default install. took me a while to find this out, since there was no error it just didn't show anything else on the net. :-)

---

### Post by Morbius1 on 2011-05-25
> **mastablasta said:**
> how is the file sharing setup? is it easy? all working out of the box?
On the Server end something is missing. Once upon a time there was a package called "thunar-shares-plugin" that allowed you to do in thunar what nautilus-share does for Nautilus - right click a folder > share this thing ( I paraphrased :wink: ). That package is now gone. I don't know where it went or why it doesn't work any longer so you need to create shares the classic way using "system-config-samba".

On the Client side you can go to Thunar > Network to see the remote shares.

---

### Post by Bucky Ball on 2011-05-25
That is a problem. I connect with the other machines using SSH and static IPs which is easy in Gnome. Places>Connect to Server>Input the IP and wap, I can see the whole machine and start swapping or dropping files.

Not so easy with Xubuntu and I haven't figured a way to do that yet. Not that I've tried for hours to nut it out but I have had a peek. Nothing obvious. Filezilla seems to work from memory but not as simple as Gnome. Bit like elephant gun to kill a fly.

Samba? Haven't bothered with it since Windows days (apart from a few hours early on before I discovered there were more straightforward ways of doing what I wanted to do). ;)

---

### Post by Morbius1 on 2011-05-26
> **Bucky Ball said:**
> That is a problem. I connect with the other machines using SSH and static IPs which is easy in Gnome. Places>Connect to Server>Input the IP and wap, I can see the whole machine and start swapping or dropping files.

Not so easy with Xubuntu and I haven't figured a way to do that yet. Not that I've tried for hours to nut it out but I have had a peek. Nothing obvious. Filezilla seems to work from memory but not as simple as Gnome. Bit like elephant gun to kill a fly.  

That's why the gods gave us Gigolo. Here's a mini-howto: 

Install gigolo and fuse:
```
sudo apt-get install gigolo
sudo apt-get install fuse
```When you first bring it up make a change in the preferences:
[B]Edit > Preferences > Interface>
Select "Show Side Panel"[/B]
**Select "Start minimized in the Notification Area"**
**Disable "Show auto-connect error messages"**

Now open gigolo > Connect > SSH > fill in the blanks > Select Connect.

Now comes the best part. On the right panel of gigolo you will see the connected folder. Right click that and select: **Create Bookmark**

* Change the name of the bookmark if you want.
* And select: **Auto-Connect**

Now add Gigolo to your autostart programs in "Settings and Startup". The next time you boot the remote folder will connect automatically. If the remote machine is not up at the time you boot, gigolo will probe the network at user defined intervals and connect when the remote machine is available.

---

### Post by Bucky Ball on 2011-05-26
Thanks for that info, Morbius1. Will have a play with Gigolo later and let you know. ;)

---

