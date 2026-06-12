---
title: "How do I stop those password requests"
date: 2009-12-28
forum: Security
---

### Post by sparky2 on 2009-12-28
I've just installed 9.10 and it's working quite well. One of the reasons I'm experimenting with Ubuntu is to [hopefully] get away from the security interruptions and overheads imposed by Windows XP to "help" me stay "secure".

When I boot / login to Ubuntu I am subsequently asked for the admin password to get other services I would expect to have at my fingertips. For example, to connect to the wireless network, or  open the other logical disk drive through "Places" ...

(note this happens even though I have ticked "autoconnect" for the wireless network)

Is there some way in can skip these [kinda annoying] requests for the password?

thanks

---

### Post by CharlesA on 2009-12-28
> **sparky2 said:**
> I've just installed 9.10 and it's working quite well. One of the reasons I'm experimenting with Ubuntu is to [hopefully] get away from the security interruptions and overheads imposed by Windows XP to "help" me stay "secure".

Windows XP never had anything like that, as long as you were an administrator. UAC started with Vista.

> When I boot / login to Ubuntu I am subsequently asked for the admin password to get other services I would expect to have at my fingertips. For example, to connect to the wireless network, or  open the other logical disk drive through "Places" ...

(note this happens even though I have ticked "autoconnect" for the wireless network)

Is there some way in can skip these [kinda annoying] requests for the password?

thanks

it's probably because it requires a higher level of rights then you currently have, even if you are an admin. That's how Linux is designed, only a normal user can do certain things, and if they need to run maintenance, they are prompted for the password to elevate those rights.

---

### Post by MartyBuntu on 2009-12-28
> **sparky2 said:**
> ...or  open the other logical disk drive through "Places" ...


You can set permissions and details of mounting drives at boot by installing **pysdm**.

---

### Post by sparky2 on 2009-12-28
thanks for the clue MartyBuntu. How do I install psydm ?

Is there a similar resolution for password requests for connecting to my wireless network ?

---

### Post by SecretCode on 2009-12-28
To install psydm, open a terminal and type
```
sudo aptitude install psydm
```
[SIZE="1"]You'll have to enter your password :)[/SIZE]

You might be able to allow wireless connections via Users and Groups > 'click to make changes' > select user name > Properties > User Privileges tab > and tick 'Connect to wireless and ethernet networks'.

But my wireless connects automatically at login and I don't have this privilege enabled.

---

### Post by cariboo on 2009-12-28
Right click on Network-Manager in the top panel and select edit. Highlight your network device and click edit. Make sure **Available for all users** is enabled. Click apply and your done.

---

### Post by mc4man on 2009-12-28
If you are the admin user and if you have other partitions that you don't want to automount at boot then removing the need to authenticate when  mounting them is quite simple.
The behaviour in karmic in this regard has been addressed in lucid, but not yet  in karmic.

method [here]("http://ubuntuforums.org/showthread.php?p=8542850#post8542850")

---

### Post by MartyBuntu on 2009-12-28
> **SecretCode said:**
> To install psydm, open a terminal and type
```
sudo aptitude install psydm
```
[SIZE="1"]You'll have to enter your password :)[/SIZE]



Also, a menu entry isn't automatically created, so you'll either have to make one yourself, or start **pysdm** through the terminal.

---

### Post by sparky2 on 2009-12-28
OK looking good, 1 down, 1 to go.

With all your help and the tutorial "GUI Fstab Editing with PySDM" I now have my other partition mounting automatically at login. Many thanks 

(and I could feel you all nodding wisely when there was a hiccup at one point and I had to reinstate the fstab backup I had made !)

But so far no luck with wireless connection - at login I am  auto-prompted for keyring password, but that's the step i want to automate. 
I have ticked the box per **SecretCode**'s suggestion, but no change. 
**cariboo907** please excuse my noviceness but I could not see / find  "...Network-Manager in the top panel...". I do have a Wireless Network Connection icon (bunch of increasing height bars) and I  previously ticked the "connect automatially" option therein. That did reduce number of password requests by 1, but I still have 1 left to automate.

---

### Post by sparky2 on 2009-12-28
maybe a full screenshot will help - attached. 
This shows the password request dialogue box, and my top panel

---

### Post by sparky2 on 2009-12-28
actually 0 step forward, 1 backwards... :(

turns out my other partition is only mounting read-only, and when I untick read-only (in System>Admin>SDM) it always re-ticks it :confused: 

I tried to follow this (from the tutorial)  "An ntfs partition fstab entry should work with a simple 'ntfs-3g defaults' entry." but no luck .... so far.

---

### Post by SecretCode on 2009-12-29
I'm not sure about that keyring password prompt. I don't see it ... maybe my passwords are insecure ... *paranoid*

My ntfs entries are like this: 
```
/dev/sda6	/media/sda6	ntfs-3g	rw,users,umask=0000,auto	0	0
```
Afaik you need the 'rw' and some umask (umask=0000 is as permissive as you can get and not really recommended). And 'users' allows everyone to mount it.

---

### Post by sparky2 on 2009-12-29
hah - one man's nirvana is another's paranoia :)

well I tried to make my options match ***SecretCode***'s but I get mount errors. I've attached screenshots of the SDM page and resulting error message. 

To be honest, given my limited linux exposure this is way out of my league and further educated clues would be real good ](*,)

---

### Post by cariboo on 2009-12-29
> **sparky2 said:**
> maybe a full screenshot will help - attached. 
This shows the password request dialogue box, and my top panel

I'm not sure whether that icon of a termianl with bars in it is your network-manager icon, but if you right-click on it you should see a context menu with a choice to edit your connection. Then follow my instruction from my previous post.

---

### Post by SecretCode on 2009-12-30
You should take my suggested fstab entries with a pinch of salt, because I've sometimes got that "Unable to mount... " error when I click on certain entries in the nautilus menu. The drive's already mounted though, so it's just something odd with Nautilus treating internal drives as removable drives.

---

### Post by Lori700698 on 2009-12-30
I think I can help with the wireless/keyring, seems to be a glitch, I had the same issue with my son's computer. Run all your updates then go to keyrings and delete the wireless one that is currently stored.  Connect and it will ask you for everything again, check the little box for all users and save.  That was the last time I had to run around and do the password for wireless.  Now as for it asking you for password for other things, that's kind of Ubuntu's way of protecting you.  If your system asks you for a password and your technically not doing anything you have a problem.  and for the fstab here is the newest addition to mine, new 1TB external hard drive for Christmas.  I named the folder it is mounted to XTB.  Haven't had to remount after reboots and I can read and write from any user...and by the way I use Webmin with my headless server and it added this line to the fstab, I couldn't make it work on my own.

/dev/sdb1  /home/XTB  ntfs  user,gid=100  0  0

Hope it helps!!
Lori

---

### Post by sparky2 on 2010-01-04
Wireless password login - resolved :) (thanks all)

Other partition login - not yet resolved ... :(

Lori700698 your example for connecting your new 1TB drive may help, but can you explain how you

(1) named the folder it is mounted to XTB. :confused:
(2) used Webmin with my headless :shock: server ??? 

(note I'm trying to autoconnect my windows partition on same drive, not a separate drive) 

thank you

---

### Post by Jive Turkey on 2010-01-04
mounting that partition in /etc/fstab should clear up the problem.  Forget about that other app you were using.  
Step1 get the UUID for the volume you want automounted, in a terminal run:
```
 sudo vol_id /dev/sda1 | grep UUID=
```
The output should look like this:
```
ID_FS_UUID=E678C64378C611EB
```

step2
open fstab and add an entry similar to this:
```
# /DATA is existing folder in / 
UUID=E678C64378C611EB /DATA ntfs defaults,nls=utf8,umask=007,gid=46  0       1

```
of course replace the UUID with the one you got above, and /DATA with your desired mountpoint.

then type ```
sudo mount -a
``` to test, if this works then it will mount automatically at boot time.

If the folder you want the partition's contents in has not been created before mounting, mount will fail. Use ```
sudo mkdir /DATA
``` if you want it there.  The folder needn't be in / necessarily, you could put it to any **empty** folder you like.

---

### Post by sparky2 on 2010-01-05
Well ***Jive Turkey*** I followed your instructions as best I could, but failed at  step 1, since "sudo vol_id ... " did not recognise vol_id as a command. I tried replacing vol_id with "sda1" and then "DATA" (drive name) but no go. So i couldn't get the UUID. Not sure what's going on here...

But all is not lost, I did the rest of your suggestions using PySDM, then "sudo mount -a" in terminal and bingo... it works!

So now when I boot I get network connection and other partitions mounted and writeable without password requests... excellent. Thanks to ***Jive Turkey***

Only residual is now in Evolution Mail, when I hit "send/receive" it now asks for keyring password. It wasn't doing this before latest changes. 

Any suggestions to eliminate this one last password request??

---

