---
title: "How can I share my Virtual Machine between users?"
date: 2009-02-10
forum: Virtualisation
---

### Post by jreyes33 on 2009-02-10
I have XP running on VirtualBox on my user, and I wnat to share that VM with other users in this computer so that I don't have to Install XP 2 or 3 times (which would be ridiculous).

Can anyone help me? I just want to share my VM among all (or some) users in this computer!

Thanks in advance

---

### Post by chronographer on 2009-02-10
Simple. Add other users to the Virtualbox group and make sure virtualbox on each install has a VM registered with it which points to the VDisk image.

You can then create a launcher on the desktop or in the menu to start only that VM so that the users double click the icon and get XP up in a minute or so.

I would also set up shared folders with each so that there is an easy way to get into the home directory (as a whole or per user) in the VM. This is all pretty easy to do! But post again for more specific advice.

---

### Post by jreyes33 on 2009-02-10
> **chronographer said:**
> Simple. Add other users to the Virtualbox group and make sure virtualbox on each install has a VM registered with it which points to the VDisk image.

You can then create a launcher on the desktop or in the menu to start only that VM so that the users double click the icon and get XP up in a minute or so.

I would also set up shared folders with each so that there is an easy way to get into the home directory (as a whole or per user) in the VM. This is all pretty easy to do! But post again for more specific advice.

Thanks!! that was quick!
I'd also like to know more about that shared folders set up :-k

---

### Post by chronographer on 2009-02-10
[http://ubuntuforums.org/showthread.php?t=627847](http://ubuntuforums.org/showthread.php?t=627847)

post no. 7 has the details: 
>  Re: virtualbox shared folders....?
here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out

---

### Post by HermanAB on 2009-02-10
However, XP is a single user system that only allows ONE user to use it at any one time.  Win2003 will allow three simultaneous users and it can be expanded with a licence upgrade.

Cheers,

Herman

---

### Post by chronographer on 2009-02-11
hmm. I didn't think of that. I would usually have only one person logged on and in a VM on my machine at home at once but if you were to have more than one this is very true!

---

