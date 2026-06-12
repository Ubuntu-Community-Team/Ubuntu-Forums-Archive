---
title: "Root login"
date: 2008-11-18
forum: Security
---

### Post by adityabankar on 2008-11-18
Hi All,

I noticed that if on grub loader we choose the options to start ubuntu in recovery mode then it gives options like repair X, root terminal, etc (not sure of exact names).
If we choose root terminal we get a root terminal without being asked for any password. If I do same thing on Debian then the root password is set by me and I get a login prompt if I go to recovery mode. But in ubuntu it directly logs in as root.
This way any person can login to my computer as root delete all my necessary files and take over my computer.

I tried this on my ubuntu 8.04 system not sure if this is fixed in ubuntu 8.10.

Thanks,
Aditya

---

### Post by hyper_ch on 2008-11-18
anyone who gets physical access to your computer and copy/delete/change all your files....

--> Boot your computer with a live cd and you have full access...


..... unless you protect yourself against it with encryption. Then they could only delete the harddisk.

---

### Post by Sarmacid on 2008-11-18
I haven't tested it, but I think if you set a root password, you'll get asked for it on the recovery mode.

---

### Post by bodhi.zazen on 2008-11-18
> **adityabankar said:**
> Hi All,

I noticed that if on grub loader we choose the options to start ubuntu in recovery mode then it gives options like repair X, root terminal, etc (not sure of exact names).
If we choose root terminal we get a root terminal without being asked for any password. If I do same thing on Debian then the root password is set by me and I get a login prompt if I go to recovery mode. But in ubuntu it directly logs in as root.
This way any person can login to my computer as root delete all my necessary files and take over my computer.

I tried this on my ubuntu 8.04 system not sure if this is fixed in ubuntu 8.10.

Thanks,
Aditya

I agree with hyper_ch, the problem is not root access without a password, the problem is physical access.

I also agree the only "defense" is encryption.

Sarmacid is correct, if you set a root password you will be asked for a password when you boot to recovery mode, but keep in mind Ubuntu is not Debian and there is a down side to setting a root password :)

---

### Post by cariboo on 2008-11-18
You could always set a password on grub if you are that worried. The easiest way to do it is to use StartUp-Manager. It is available in the repositories, search for startupmanager.

Jim

---

### Post by adityabankar on 2008-11-19
I too tend agree that setting a root password would be better.

And it should be done like this: "sudo passwd", never tried this.

This is something that other distros do during installation, even debian.

I think live CD won't let other user get access to my files as there is a live user created how won't be allowed to access other users' files.

I will try setting up a root password but believe that this should be done during installation.

Thanks,
Aditya

---

### Post by hyper_ch on 2008-11-19
> **adityabankar said:**
> I too tend agree that setting a root password would be better.

[...]

This is something that other distros do during installation, even debian.

I think live CD won't let other user get access to my files as there is a live user created how won't be allowed to access other users' files.

I will try setting up a root password but believe that this should be done during installation.

Thanks,
Aditya

(1) it is against forum policies to tell how to enable root:
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

(2) Other distro use a root account - but they don't make use of the sudo option - this goes namely for debian. Have again a read here: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

(3) If you don't encrypt the files then anyone being able to get physical access to your harddisk can get all the data. Linux permissions won't protect you against this and neither will a "root password login".

(4) Enabling root has also other implications (e.g. bots that try to guess login data will know what the "root" account is and hence there is one less hurdle on gaining remote access).

(5) Again I point to this here: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by liquid.silver on 2008-11-19
I'm not sure if this is 100% relevant, but anyways...

What i do is i set a root password, a grub password for the recovery mode option, and i also have a main grub password. Then i set the boot sequence in the bios so that it boot off the hard drive first, and skips the cd. then i set a password for the bios.

I am well aware that you can reset the bios password or remove the hard drive with physical access, but seen as i have a laptop, that would take someone quite some time and i would usually be able to stop them.

Of course none of these security settings have ever actually been needed and my pc would probably never have been compromised with a password of "123", but i'm kinda paranoid... besides, it's fun to setup :)

---

### Post by hyper_ch on 2008-11-19
@liquid.silver
someone just need to get hold of the harddisk and they can extract all data at home without you interfering.

---

### Post by cariboo on 2008-11-19
Unless you have security type screws on the cover over the hard drive, you can remove the hard drive from a laptop quicker then you can from a desktop computer.

See this page here:

[http://www.brycefastener.com/](http://www.brycefastener.com/)

for the type of screw I mean.

Jim

---

### Post by mflint on 2008-11-19
> **adityabankar said:**
> I noticed that if on grub loader ... If we choose root terminal we get a root terminal without being asked for any password.
True. But for that to happen, an attacker will need *physical* access to your Ubuntu box. And to get such physical access, they've probably broken into your apartment.

To be honest, if someone's broken into your apartment, then the security of your Ubuntu box should be the least of your worries. Me, I'd be more concerned about the potential for identity theft, violation of my privacy, and the thought of someone rifling through my underwear drawer looking for jewellery. *shudder*

If this concerns you, install better locks or get yourself more trustworthy housemates.

M

---

### Post by hyper_ch on 2008-11-20
> **mflint said:**
> To be honest, if someone's broken into your apartment, then the security of your Ubuntu box should be the least of your worries.

depends on wha you have on your box.

---

### Post by liquid.silver on 2008-11-20
I guess, but it's a fine balance between my laziness and my paranoia. It's so easy to just type, taking out a screw driver is effort. :)

---

### Post by adityabankar on 2008-11-21
Hi,

When I posted on this for first time, I didn't have following in mind:
1) Enabling root account
2) Someone accessing my ubuntu box without my permission
3) Someone breaking into my house to steal data from my ubuntu box instead of stealing the box forever (I don't work for intelligence department).

What I had in mind is:
1) I employ an accountant and give him a laptop with ubuntu by setting up an account for him on which browsing internet is disabled. I know for sure that he cannot steal my laptop. But he shouldn't be able to (at least not easily) be able to change permissions for his account.
2) I have a desktop and my younger sister sees movies in my absence even is she has a examination tomorrow. So on her account I can disable video.

In both the cases it would be simple to change permissions if they log in to system as root. Which can be done by choosing recovery option on grub.

In all cases I don't want to disallow people from accessing my computer but I want to restrict their access.

Think that you are a parent having children in their early adolescence and you are worried about the kind of data they access. Instead ask the OS to curb their access rights and make sure that no one can override these permission settings in any way.

-Aditya

---

