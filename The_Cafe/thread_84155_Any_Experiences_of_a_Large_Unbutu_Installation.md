---
title: "Any Experiences of a Large Unbutu Installation"
date: 2005-10-30
forum: The Cafe
---

### Post by port7 on 2005-10-30
I *think* we are about to deploy approx 700-800 Breezy desktops, has anyone else done this sort of thing before? Any war stories, tips, etc?

Apreciate peoples thoughts...

---

### Post by stuporglue on 2005-10-30
For that big of a project, you might want to look at remastering the install CD with some preseed info on it. Preseed info lets you skip all the debconf questions. 

An option for CD-less installs might be to PXE boot them all off of a server. I've tried to set this up, but have always gotten stuck though, so I don't have any real advice about it. 

I would like to hear what you do though.Our Unix Users Group installs Linux on about 40 machines every 4 or 5 months, and a faster way (than one by one CD booting) would be nice.

---

### Post by xequence on 2005-10-30
[QUOTE=port7]I *think* we are about to deploy approx 700-800 Breezy desktops, has anyone else done this sort of thing before? Any war stories, tips, etc?

Apreciate peoples thoughts...[/QUOTE]

I have no experience, but that is just plain awesome =) Its great to know ubuntu is used like that :)

---

### Post by mustang on 2005-10-30
Wow, that looks like an ambitious task you got going there. Let us know how it goes and how you did it.

---

### Post by UbuWu on 2005-10-30
Use either preseeding or kickstart for automatic installations. Will save you a lot of time ;)

---

### Post by bionnaki on 2005-10-30
[QUOTE=port7]I *think* we are about to deploy approx 700-800 Breezy desktops, has anyone else done this sort of thing before? Any war stories, tips, etc?

Apreciate peoples thoughts...[/QUOTE]

wow - university? business?

---

### Post by port7 on 2005-10-31
[QUOTE=bionnaki]wow - university? business?[/QUOTE]

Business, we currently have 700-800 Debian Woody Desktops. We need to update them all for various reasons and so were going to go to Sarge but Ubuntu fitted our needs better so Ubuntu it is!

I would have liked to have waited for Dapper Drake beacuse of the 5 year support thing, but we need to do this upgrade by Jan 06 so we can't.

I shall post about it as we get more into it, though picking up on a few of the points earlier. As this is a business it's a very trimmed down image and so we have a custom CD install that we give the engineers to install, it needs minimal interaction from them (what is the location code). I do want to do FAI at some point in the future for PXE network installs, but thats something for the future.

---

### Post by ubuntu_demon on 2005-10-31
what kind of business ?
(just curious)

---

### Post by joaoeb on 2005-10-31
I installed ubuntu in 35 machines some time ago.
What I did was:

Choose a machine to be the "Install server"

Installed apt-cacher and apache in that machine.

Adapted the script in the Ubuntu Mini-Ram how-to to my needs: [http://www.ubuntuforums.org/showthread.php?t=42873](http://www.ubuntuforums.org/showthread.php?t=42873)

Remember to change your sources.list in the desktops soon after the first reboot.

But you is migrating. In this case I will give you a advice. Sometimes simply coping the /home folder don't work or give errors. In this case create a NEW user for the computer and copy only the necessary .something folders from his old home to the new one (.evolution for example).

Hope it helps.
P.S. Sorry abouth my english.

---

### Post by port7 on 2005-11-01
[QUOTE=ubuntu_demon]what kind of business ?
(just curious)[/QUOTE]

Toolhire ([www.speedyhire.co.uk)](www.speedyhire.co.uk)), we are a national toolhire company with about 320 branches all over the UK. So each branch has on average 3 PC's and they are all connected via a private DSL network. It's an easy image as all the users need is a telnet session (main business app), Openoffice.org and Firefox.

Cheers

---

### Post by .Danny on 2005-11-01
Sounds like a great project. Wish you all the best. ;)

---

### Post by linuxlady2714 on 2005-11-22
I used systemimager to configure 8 machines.  There were some little problems, I would like to find something better as well.

[http://www.systemimager.org/](http://www.systemimager.org/)

And a way to automate changes after the machines have been configured.

-Anne

---

