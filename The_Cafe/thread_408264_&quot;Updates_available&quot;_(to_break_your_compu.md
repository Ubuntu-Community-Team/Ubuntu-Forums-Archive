---
title: "&quot;Updates available&quot; (to break your computer)"
date: 2007-04-13
forum: The Cafe
---

### Post by Praill on 2007-04-13
I'm getting really sick of this.
Everytime I "update" it breaks something.
The new updates had entries for the kernel-source and kernel-headers, so I KNEW it was going to give me special issues... needless to say, I was not dissapointed.

After "updating" my sound no longer worked, and my wireless became painfully slow.
To fix this I had to make uninstall, ./configure, make, and make install my alsa drivers again. The wireless issues still remains unsolved as I did not compile the driver myself (it worked out of the box) so I dont even know what driver it uses. I've read a bit and think I'm using an ipwxxx driver, so I'll have to mess with it later.

Seriously though.. what was wrong with my installation before these "updates"? Why did I need them? Its seriously ticking me off as this isnt the first time this has happened.

---

### Post by B3Nji on 2007-04-13
> **Praill said:**
> I'm getting really sick of this.
Everytime I "update" it breaks something.
The new updates had entries for the kernel-source and kernel-headers, so I KNEW it was going to give me special issues... needless to say, I was not dissapointed.

After "updating" my sound no longer worked, and my wireless became painfully slow.
To fix this I had to make uninstall, ./configure, make, and make install my alsa drivers again. The wireless issues still remains unsolved as I did not compile the driver myself (it worked out of the box) so I dont even know what driver it uses. I've read a bit and think I'm using an ipwxxx driver, so I'll have to mess with it later.

Seriously though.. what was wrong with my installation before these "updates"? Why did I need them? Its seriously ticking me off as this isnt the first time this has happened.

I totally agree. My last updates have now given me an option to  boot into the new kernel it installed as well as the old one on boot up! My ubuntu system seems to have really slowed down, to the point where if im opening automatix my mouse lags like a bitch! hows that working out! Its not right... it was running really fast before. now I have "updated" its all gone Pete tong!

---

### Post by STREETURCHINE on 2007-04-13
```
I'm getting really sick of this.
Everytime I "update" it breaks something.
The new updates had entries for the kernel-source and kernel-headers, so I KNEW it was going to give me special issues... needless to say, I was not dissapointed.

After "updating" my sound no longer worked, and my wireless became painfully slow.
To fix this I had to make uninstall, ./configure, make, and make install my alsa drivers again. The wireless issues still remains unsolved as I did not compile the driver myself (it worked out of the box) so I dont even know what driver it uses. I've read a bit and think I'm using an ipwxxx driver, so I'll have to mess with it later.

Seriously though.. what was wrong with my installation before these "updates"? Why did I need them? Its seriously ticking me off as this isnt the first time this has happened.

```

yep thats why i now hang on to the updates for a week to wait and see if any of them are breaking the system.

```
I totally agree. My last updates have now given me an option to boot into the new kernel it installed as well as the old one on boot up! My ubuntu system seems to have really slowed down, to the point where if im opening automatix my mouse lags like a bitch! hows that working out! Its not right... it was running really fast before. now I have "updated" its all gone Pete tong!
```

should not have mentioned automatix it will get the blame for the breakage.

---

### Post by Adamant1988 on 2007-04-13
Which version are you guys running?

---

### Post by anaconda on 2007-04-13
The only updates that break the system is kernel updates. By breaking I mean the  need to reconfiguring some things.. like VMWare, and NVIDIA.

But usually there isn't any real advantage in updating to each new kernel as soon as it is published.

I have decided NOT to update kernels more often than once in 1-2 months.

---

### Post by InuyashaDuelist on 2007-04-13
I couldn't even get the most recent kernel updates. It said "STOPED BEXUZ IT LL BRAEK SUMTING" or something along those lines.

---

### Post by ssam on 2007-04-13
if you make custom changes to your system, and then update to something with out the change then things might break.

i dont use any unofficial drivers (i use the opensource radeon driver, and my wifi drivers are in the kernel) i have never had a problem like this for a update to a stable release.

maybe now that things like easy driver installation is done within the official ubuntu project things should get better.

---

### Post by salsafyren on 2007-04-13
Are you using edgy or dapper?

I never had a problem with those.

---

### Post by prizrak on 2007-04-13
I'm on Feisty and I don't have update problems. Well cept that I can't install the latest batch of updates cuz it's not letting me download anything for some reason.

---

### Post by smoothone on 2007-04-13
HP dv 2025, update for feisty broke my sound. Sound came back after doing nothing. Now is gone again after latest updates.

---

### Post by Fascination on 2007-04-13
[quote="ubuntu geek"]Don't use Feisty as your primary desktop/OS. Feisty is Ubuntu in development. It's not ready for the general public! If you want new stuff you can use backports instead of Feisty.

Feisty should only be used if you want to help testing bugs. Important stuff can and will get broken. Probably X is going to break this means that during that time (maybe even for weeks) you can't easily log into X anymore.

If you want to help testing you are welcome to try Feisty. You should backup your stuff such as personal files and data. Also install Feisty on a different partition than Dapper/Edgy and use a different username if you use the same /home partition. [/quote]

In short; dont whine about updates 'breaking' things if you're using the beta. ;)
Be constructive and discuss them in the development section, or log them. :)

[http://ubuntuforums.org/announcement.php?f=179]("http://ubuntuforums.org/announcement.php?f=179")

---

### Post by prizrak on 2007-04-13
> **smoothone said:**
> HP dv 2025, update for feisty broke my sound. Sound came back after doing nothing. Now is gone again after latest updates.

I can't even get the latest updates I get a 403 error from the repos for some reason :(

---

### Post by smoothone on 2007-04-13
If i'm not mistaken the first three that posted are edgy users so they have the right to rant and complain. But yes Feisty is for testing as of now!

---

### Post by prizrak on 2007-04-13
> **smoothone said:**
> If i'm not mistaken the first three that posted are edgy users so they have the right to rant and complain. But yes Feisty is for testing as of now!
Edgy isn't very good and have been suffering problems since the beginning. This was communicated quite clearly. Hell it's was a 4 months release, people have been warned. Now if that was an issue on Dapper I would agree that it's a problem.

---

### Post by smoothone on 2007-04-13
> **prizrak said:**
> I can't even get the latest updates I get a 403 error from the repos for some reason :(


I've had the same error on several occasions.

---

### Post by eentonig on 2007-04-13
If they are on Edgy, they have the right to complain. If Edgy was released (even with a 4 months release cycle) it should be stable. Otherwise, Ubuntu should have been smart and hold it off.

If they're running on Feisty, they should smack their face again the wall and stop complaining. If you want to use béta software (and certainly béta soft with a short release cycle as ubuntu release have), you have to accept the fact that there will be lots of changes. And that a high % of these changes introduce more or less annoyance.

---

### Post by Fascination on 2007-04-13
> **smoothone said:**
> If i'm not mistaken the first three that posted are edgy users so they have the right to rant and complain. But yes Feisty is for testing as of now!

Going by the first user's post on another thread, Im guessing hes feisty.. and using Feisty. ;)

---

### Post by frodon on 2007-04-13
About feisty there's some movement on the kernel these days and you are more likely to have problems with some kernel versions because devs are fixing the bugs these days, so just use your old kernel before that the fixes got commited.
Like some already said using an unstable release like feisty fawn you know that things like that happen so it's just normal for an unstable release.

---

### Post by Mateo on 2007-04-13
they need to figure out a way where you don't have to reconfigure your video card and tv card, etc every time a new kernel comes out.

---

### Post by frodon on 2007-04-13
> **Mateo said:**
> they need to figure out a way where you don't have to reconfigure your video card and tv card, etc every time a new kernel comes out.:confused:  You don't have to, obviously if you use software from the ubuntu official repositories.

---

### Post by Mateo on 2007-04-13
> **frodon said:**
> :confused:  You don't have to, obviously if you use software from the ubuntu official repositories.

yeah you do.  you have to do sudo depmod -a for sure for the video card.  you also have to run some stuff on my tv card.

---

### Post by FuturePilot on 2007-04-13
Everything is fine here. On 2 computers Dapper and Edgy all working fine. Although I don't understand what the point of that latest kernel update was? It was the same version that I already have installed. Anyone know what that was about?

Never mind, it was the last number that changed, had to look in the Synaptic history for that.

---

### Post by happy-and-lost on 2007-04-13
I enjoy fixing what updates broke. Keeps me on my toes and my Linux problem solving skills sharp and fresh :)

---

### Post by frodon on 2007-04-13
> **Mateo said:**
> yeah you do.  you have to do sudo depmod -a for sure for the video card.  you also have to run some stuff on my tv card.I think you are in a special case because i have a video card and a tv card as well and after 2 years of ubuntu use i nerver have to do such thing.
However each tweak you do on your kernel (like running the official nvidia installer to get the latest drivers) have to be performed again on each kernel release and AFAIK there's no solution for this, it is how linux works, own kernel tweaks have to be repeated on each kernel release.

---

### Post by Mateo on 2007-04-13
> **frodon said:**
> I think you are in a special case because i have a video card and a tv card as well and after 2 years of ubuntu use i nerver have to do such thing.
However each tweak you do on your kernel (like running the official nvidia installer to get the latest drivers) have to be performed again on each kernel release and AFAIK there's no solution for this, it is how linux works, own kernel tweaks have to be repeated on each kernel release.

probably depends on your hardware.  with ATI cards, you have to run depmod -a every time. it's in the wiki if you don't believe me ;)

---

### Post by Saxitoxin1 on 2007-04-13
I comply with all the frustrating comments.  The last update screwed up my wireless connection.  It is no longer detected.  I had to painstakingly do a manual installation with ndiswrapper to get my Broadcom 4306 wireless working and now it's apparently all gone.  Does any of you know how to reactivate detection of my wireless?

---

### Post by atihimself on 2007-04-13
I have 3 feisty ubuntu machines at home, none have had any problems after updates, plus all the computers are made by different campanies, Dell, ibm and ordi (last one uses asus barebone I think)

---

### Post by macogw on 2007-04-13
> **ssam said:**
> if you make custom changes to your system, and then update to something with out the change then things might break.

i dont use any unofficial drivers (i use the opensource radeon driver, and my wifi drivers are in the kernel) i have never had a problem like this for a update to a stable release.

maybe now that things like easy driver installation is done within the official ubuntu project things should get better.

Exactly.  If you compile in a driver from god-knows-where,  you've compiled it *into* that kernel, and it won't be there with the new one.  Only what's there by default is supported.  If you make your own customizations, that's your own d*** fault.  

Sometimes, linux-restricted-modules takes a few hours longer to populate to all of the servers than the kernel does, so the new restricted/proprietary drivers won't be there with the new kernel.  Just don't do kernel updates without the new restricted modules show up.  When all you guys complained about your video disappearing and having no X and having to use the CLI in August, well, I was sitting there going "Dapper update killed X?  What are they talking about?  It works fine!"

Example of a customization:
> I comply with all the frustrating comments. The last update screwed up my wireless connection. It is no longer detected. I had to painstakingly do a manual installation with ndiswrapper to get my Broadcom 4306 wireless working and now it's apparently all gone. Does any of you know how to reactivate detection of my wireless?
reason: you had to do it to make it work with one kernel and you'll have to do it to make it work with every kernel, and that's just. the. way. it. is.



The only updates that broke things for me were during Feisty's alpha testing (though I just discovered one of them yesterday, I know the update was old).

---

