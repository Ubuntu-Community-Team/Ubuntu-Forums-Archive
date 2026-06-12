---
title: "Windows Server Alternative?"
date: 2007-08-24
forum: Server Platforms
---

### Post by towerofpower256 on 2007-08-24
Hello all,
I know that this question has possibly been asked a million times and just so you know, I did search the forums for my answer. Well, here goes...

I'm looking for an alternative to Windows Server 2003. More specifically, the ability to make users and groups, allow those users to login at the startup screen from any client, have the users rights/policies modifiable from the server (and having the clients automatically update them) and have the 'home folder' capability from Windows (e.g. how J:\ was always the users home folder).

I would suspect that this is a combination of packages and some tweaking here 'n there.

Unfortunately, the only answer I could pull up was 'a mixture of OpenLDAP and Samba' yet I failed to see how that would influence the login capabilities of a workstation. Accessing remote devices/locations once you are logged in, yes, but not the logging in process itself.

If it's any help, something like NetWare.

I'm sorry about my poor linguistic skills, I'm a little unclear on how to present a clear picture of what I'm after. If anyone can correct me on any of my misunderstandings, please do. I hope that anyone can give me a hand in this area. Even if you can only assist in a single aspect, it would be greatly appreciated.

Thanks,
towerofpower256

---

### Post by NewbieNik on 2007-08-24
Hi thepowerof256,

Don´t worry, you are not alone I am also trying to use Ubuntu as a replacement for windows server.
This is what I have found so far.
Server 6.04 LTS is probably your best bet. I have installed this in the LAMP configuration so Apache and MySQL is preconfigured.
I then followed the guide [http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html) This took me through installing SSH, OpenLDAP (Which is causing me some issues, but I working on it) DHCP, DNS and others.
Samba is also included in the gudie and this can map drives to certain users even Windows users.
There is a wealth of help here in the forums, but because there is so much, it can take some time to find what you want. Do persever, it IS worth it....

---

### Post by rickyjones on 2007-08-24
With some work you can get users/computers authenticating against your Linux server. You can create scripts and use Samba to mount home drives. But you will not have anything for group policy - this is one of the biggest things that causes me to keep a Windows domain controller with Linux fileservers.

I hope this helps.

-Richard

---

### Post by towerofpower256 on 2007-08-24
Hmmmm..... sounds like Windows Server is still the best choice. Bugger.

Maybe, just maybe, there is another way around it. I was after a means to disable *all* menus and bars and everything on the desktop. All I was after was the desktop, a few shortcuts and thats it, but only for the basic users. So far I haven't found a way to do that *and* disable the users from modifying the settings.

It's for a small gaming network I have at my school. Windows Server did the trick but lately, Ubuntu has peaked my interests. What other OS ships with such cool screensavers :p 
Windows? I think not!

Ah well, I'm sure the Linux community will fill this hole sooner or later. From what I can tell, you are all a very talented bunch ;)

---

### Post by rickyjones on 2007-08-25
> **towerofpower256 said:**
> Hmmmm..... sounds like Windows Server is still the best choice. Bugger.

Maybe, just maybe, there is another way around it. I was after a means to disable *all* menus and bars and everything on the desktop. All I was after was the desktop, a few shortcuts and thats it, but only for the basic users. So far I haven't found a way to do that *and* disable the users from modifying the settings.

It's for a small gaming network I have at my school. Windows Server did the trick but lately, Ubuntu has peaked my interests. What other OS ships with such cool screensavers :p 
Windows? I think not!

Ah well, I'm sure the Linux community will fill this hole sooner or later. From what I can tell, you are all a very talented bunch ;)

Well, you could use Ubuntu for central authentication without issue. Then, on the desktops, use the local group policy object editor to edit the local GPO to make the changes you want. Then create a profile for the general user account and make it a mandatory profile (also make them limited users if possible).

That might work if you only have a few users and it'd take some initial overhead.

Hope that helps!

-Richard

---

### Post by towerofpower256 on 2007-08-26
Yea, that thought hit me as well (make all the necessary changes locally with a common master account and make a common user account which the customers use) and just construct some SSH scripts that can be run when minor 'adjustments' need to be made. 

> Well, you could use Ubuntu for central authentication without issue. Then, on the desktops, use the local group policy object editor to edit the local GPO to make the changes you want. Then create a profile for the general user account and make it a mandatory profile (also make them limited users if possible)
Hmmm... I think you think that Windows will be on the clients. Close, but I'm trying to convert the whole room into a Linux facility.

As for the no-desktop theory, I found out that the Kiosk feature within KDE should do the trick; can't do anything but open shortcuts and logoff. I believe I have what I need to do the trick.

One final trivial question I am still unclear about; what is it called when you put what's on your screen on many computers? My teachers use it to teach us but I don't know the proper term for it. I know it's a little off topic but it would help if I knew.

---

### Post by Dark Star on 2007-08-26
Ubuntu has Server Edition too :D But I bet it would surpass WIndows in terms of performance as Linux is always better than Windows in terms of everything ;)

---

### Post by towerofpower256 on 2007-08-26
Oh I have no doubt of that. I say that because my server just crashed (blue screen of death) and I'm going to turn it into a Linux box. Dam thing was fragmented to Antarctica and back. I hope I can get my website out of it :(

---

