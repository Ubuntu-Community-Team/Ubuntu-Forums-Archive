---
title: "virtualbox"
date: 2008-10-25
forum: Virtualisation
---

### Post by stonecoldjha on 2008-10-25
i have virtualbox installed in my PC running Hardy.i installed windows xp in the virtual box.but when i tried creating a folder to share between the host ubuntu and guest xp, i could not do so.whenever i start xp on the virtualbox,i get an error message as shown in the screenshot.how do i fix this problem?

---

### Post by stonecoldjha on 2008-10-25
i am unable to create a shared folder between ubuntu and xp.please help.

---

### Post by mikehmike on 2008-10-25
[http://forums.virtualbox.org/viewtopic.php?t=6364&sid=1cf343a0a81e668c7779246e5c2cd0d5](http://forums.virtualbox.org/viewtopic.php?t=6364&sid=1cf343a0a81e668c7779246e5c2cd0d5)

---

### Post by stonecoldjha on 2008-10-25
that doesn't solve my problem at all.even reinstalling the application doesn't help.

---

### Post by bodhi.zazen on 2008-10-25
Personally I am not a big fan of the "shared folders" option.

I prefer a network protocol, such as samba. Samba is, IMO, just as easy to configure and works out of the box for most people.

If you must there are tons of how-tos on this:

[http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/](http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/)

Can you give us more information on the configuration ? What version of Virtualbox are you using ? How did you configure the share ? How did you try to mount it? Did you get any error message ?

---

### Post by stonecoldjha on 2008-10-25
i installed virtualbox using a .deb file named "virtualbox-2.0_2.0.0-36488_Ubuntu_hardy_i386.deb.i did not get any error messages during installation,and i could successfully get xp running on it,and could also share a folder between ubuntu nad xp.but the xp installation got infected with some virus while i was working with it.so,i deleted the xp VM,and tried reinstalling xp.i could successfully do that.but,when i tried to create a shared folder through the virtualbox settings for xp,i could not,and whenever the xp starts i get that error message.

---

### Post by stonecoldjha on 2008-10-25
what should i do?

---

### Post by bodhi.zazen on 2008-10-26
Well, is networking on the host working ?

What is the content of 

/etc/hostname

Is you hostname listed in /etc/hosts ?

What is in /etc/resolv.conf ?

Did you reboot or restart virtualbox ?

---

### Post by stonecoldjha on 2008-10-26
yeah,networking works very well on host ubuntu,i am able to use the internet as well as the local area network,but virtualbox shows error in the very same.inside /etc/resolvconf i found a directory named "updatelibc.d" which itself contains some file called "avahi-daemon".

---

### Post by dunkar70 on 2008-10-26
stonecoldjha,

From the screenshot, it appears you only have 192MB of RAM allocated to your Windows XP vm. I'm surprised you can do anything with that small amount. Anyway, can you provide more details about how you have the networking setup? A screenshot of the network settings in the VirtualBox settings pane would be helpful.

While the file sharing is managed by the virtualbox application, it appears in the client as a shared network folder. Can you access the Internet from a browser inside of your vm?

---

### Post by stonecoldjha on 2008-10-27
no the network is not accessible from xp of virtualbox.yesterday i reinstalled ubuntu8.04.i then installed the .deb package for virtualbox,but i got the same error.i removed it completely,and then installed virtualbox ose.even that doesn't help.

---

### Post by stonecoldjha on 2008-10-28
sorry to say but the responses that are a bit too infrequent aren't working out,and are disappointing.please help me out.

---

### Post by Therion on 2008-10-28
The best solution, in my opinion, would be to re-create your XP virtual machine and do it correctly from the start.  You should have configured your shared folder when you first started creating your VM.

See this tutorial: [http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html) and follow the steps it outlines.

Or, you can skip to page 2, and try configuring a shared folder in your existing XP virtual machine; it MIGHT work for you.

---

### Post by stonecoldjha on 2008-10-28
i have done this many times.i even reinstalled ubuntu to see it working in the fresh installation.but it did not.

---

### Post by bodhi.zazen on 2008-10-28
I am sorry you are having so many problems.

I can not tell what the problem might be from your posts. You are stating you are having issues with shared forders, yet many of your posts are on networking.

At any rate, as I said before, I think your best solution is to:

1. Get networking going.

2. Use Samba. Samba works out of the box in the vast majority of cases. If not samba, ssh (winscp on windows).

---

### Post by stonecoldjha on 2008-10-28
the virtual machines of my virtualbox,viz xp and opensolaris do not connect to the internet.i am also unable to create a shared folder in xp,the screenshot that i attached in my first post describes the error.

---

### Post by bodhi.zazen on 2008-10-28
My guess it if you solve your networking problem shared folders would work (as would any other protocol).

I suggest you post on the virtualbox forums as this seems to be a problem with vbox and not the ubuntu host ;)

---

