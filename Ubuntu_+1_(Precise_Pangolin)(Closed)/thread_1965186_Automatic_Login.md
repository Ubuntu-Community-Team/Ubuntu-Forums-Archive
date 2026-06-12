---
title: "Automatic Login"
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Lokie538 on 2012-04-25
Hello,

Sorry about the repetitive question, I have been searching everywhere for an answer for a while now.

I am trying to get a user to automatically login, with a full updated 12.04 installation.

There is no automatic login slider in the user login section and I have tried adding lines into /etc/lightdm/lightdm.conf as followed:


```
autologin-user=myusername
autologin-user-timeout=0

```

Still no luck, I can't find any working solutions anywhere so I would love any more suggestions.

---

### Post by Cavsfan on 2012-04-25
> **Lokie538 said:**
> Hello,

Sorry about the repetitive question, I have been searching everywhere for an answer for a while now.

I am trying to get a user to automatically login, with a full updated 12.04 installation.

There is no automatic login slider in the user login section and I have tried adding lines into /etc/lightdm/lightdm.conf as followed:


```
autologin-user=myusername
autologin-user-timeout=0

```Still no luck, I can't find any working solutions anywhere so I would love any more suggestions.

It's not under System > Admin > Users and Groups?

---

### Post by Lokie538 on 2012-04-25
> **Cavsfan said:**
> It's not under System > Admin > Users and Groups?

I just realised I may be in the wrong sub-forum sorry. I'm running an updated 12.04 is that precise Pangolin?

If so not it's not there.

---

### Post by Cavsfan on 2012-04-25
> **Lokie538 said:**
> I just realised I may be in the wrong sub-forum sorry. I'm running an updated 12.04 is that precise Pangolin?

If so not it's not there.

You are in the right place, I probably am not. I do not know anything about 12.04. 
I didn't figure that much had changed. I thought that was where you would control user logins.

I guess I should not try to answer any more questions about 12.04.

---

### Post by Lokie538 on 2012-04-25
> **Cavsfan said:**
> You are in the right place, I probably am not. I do not know anything about 12.04. 
I didn't figure that much had changed. I thought that was where you would control user logins.

I guess I should not try to answer any more questions about 12.04.

Thanks anyways mate :)
It does seems strange because I believe that through my research it should be there in screen-shots I have seen.

---

### Post by sgage on 2012-04-25
Go to system settings (under the "gear" icon in the panel), and select User Accounts from the System section (you may have to scroll down - it's at the bottom). 

There you will find what you're looking for. You'll have to "unlock" it first with your password.

---

### Post by kansasnoob on 2012-04-25
> **Lokie538 said:**
> I just realised I may be in the wrong sub-forum sorry. I'm running an updated 12.04 is that precise Pangolin?

If so not it's not there.

That's odd, are you fully updated?

If so I suppose we need to see which "greeter" you're using, but I'm not quite sure how :(

---

### Post by grahammechanical on 2012-04-25
Can we p[lease have some clarification?

When I go to System Settings>User Accounts a dialogue opens and in the panel on the left there is a list of users on the system.

If I select a user then I get information about that user in the right panel.

As part of that information I get a slider that will change automatic log in for that user on or off.

To activate the slider I have to unlock the panel by clicking in the unlock button in the top right of the dialogue and then I have to enter my password as the administrator. When I am finished I lock the utility by clicking the button again.

Are you saying that none of this is available to you? This has been available to me on 12.04 for months.

Can you post a screen shot of this dialogue box?

Regards.

---

### Post by Cavsfan on 2012-04-25
> **Lokie538 said:**
> Thanks anyways mate :)
It does seems strange because I believe that through my research it should be there in screen-shots I have seen.

> **sgage said:**
> Go to system settings (under the "gear" icon in the panel), and select User Accounts from the System section (you may have to scroll down - it's at the bottom). 

There you will find what you're looking for. You'll have to "unlock" it first with your password.

You are welcome. I tried.
That is where it is on 10.04. Nice to know it is still there somewhere. I guess I will learn more about it when I jump to 12.04.
I like LTS versions but, I am going to wait a while longer before migrating.

---

### Post by kansasnoob on 2012-04-25
> **kansasnoob said:**
> That's odd, are you fully updated?

If so I suppose we need to see which "greeter" you're using, but I'm not quite sure how :(

Thinking about this further I wonder if you might have more than one display manager installed so try running:

```
sudo dpkg-reconfigure lightdm
```

If more than one dm is installed be sure to select lightdm and then see what happens.

---

### Post by Lokie538 on 2012-04-25
> **sgage said:**
> Go to system settings (under the "gear" icon in the panel), and select User Accounts from the System section (you may have to scroll down - it's at the bottom). 

There you will find what you're looking for. You'll have to "unlock" it first with your password.

I have tried unlocking previously, the option still does not show.

> **kansasnoob said:**
> That's odd, are you fully updated?

If so I suppose we need to see which "greeter" you're using, but I'm not quite sure how :(

I just installed today and opened up the update manager and updated everything. I'm wondering if I need to allow beta updates or simillar, I will look into this now.

> **grahammechanical said:**
> Can we p[lease have some clarification?

When I go to System Settings>User Accounts a dialogue opens and in the panel on the left there is a list of users on the system.

If I select a user then I get information about that user in the right panel.

As part of that information I get a slider that will change automatic log in for that user on or off.

To activate the slider I have to unlock the panel by clicking in the unlock button in the top right of the dialogue and then I have to enter my password as the administrator. When I am finished I lock the utility by clicking the button again.

Are you saying that none of this is available to you? This has been available to me on 12.04 for months.

Can you post a screen shot of this dialogue box?

Regards.

Attached is a screenshot of the unlocked panel. Not sure if Im just doing something stupid? I most likely am.

> Thinking about this further I wonder if you might have more than one display manager installed so try running:

Code:
sudo dpkg-reconfigure lightdm
If more than one dm is installed be sure to select lightdm and then see what happens.

I just tried that command, it gave no output, not sure if it had the desired affect.
My Ubuntu install should have mainly stock settings, I only installed today and have only installed a few software pieces and have not changed anything that should have affected display managers (as far as I am aware.)

---

### Post by kansasnoob on 2012-04-25
> **Lokie538 said:**
> I have tried unlocking previously, the option still does not show.



I just installed today and opened up the update manager and updated everything. I'm wondering if I need to allow beta updates or simillar, I will look into this now.



Attached is a screenshot of the unlocked panel. Not sure if Im just doing something stupid? I most likely am.

Please post the output of:

```
cat /var/log/installer/media-info
```

---

### Post by Lokie538 on 2012-04-25
> **kansasnoob said:**
> Please post the output of:

```
cat /var/log/installer/media-info
```

> Ubuntu 12.04 LTS "Precise Pangolin" - Beta amd64 (20120328)tigger@tigger-dedicated:~$

Thanks.

---

### Post by grahammechanical on 2012-04-25
There is a difference in look between your User Accounts and my User Accounts.

I just have simple + and - buttoms on the bottom but you have the words "Add user account" and "Remove user account." I also notice in your case the close and minimize buttons are on the right and not on the left.

Could this be the reason why this panel is not rendering correctly?

Regards.

---

### Post by sgage on 2012-04-25
> **Lokie538 said:**
> 

Attached is a screenshot of the unlocked panel. Not sure if Im just doing something stupid? I most likely am.


It looks like an older version of the user account settings panel. Are you sure you're up to date?

I think if I were you I'd simply back up my stuff and do a totally clean install with the final release version tomorrow.

---

### Post by Cavsfan on 2012-04-25
^^ Good idea **sgage**! +1

This is what the 10.04 User settings looks like FWTW.

[ATTACH]216559[/ATTACH]

---

### Post by kansasnoob on 2012-04-25
> **Lokie538 said:**
> Thanks.

I wish you'd used code tags instead of quote tags because I'm not sure what produces that brand of smiley, but what I can see is; 2012032smiley.

So 2012 is the year!

And 03 is the month (March)

So I don't really need to know the day of the month, I'd guess that was Beta 2. Regardless I haven't seen this happen but I'm right now installing a fresh 20120423 just to be sure it's not a bug.

---

### Post by Lokie538 on 2012-04-25
> **kansasnoob said:**
> I wish you'd used code tags instead of quite tags because I'm not sure what produces that brand of smiley, but what I can see is; 2012032smiley.

So 2012 is the year!

And 03 is the month (March)

So I don't really need to know the day of the month, I'd guess that was Beta 2. Regardless I haven't seen this happen but I'm right now installing a fresh 20120423 just to be sure it's not a bug.

```
Ubuntu 12.04 LTS "Precise Pangolin" - Beta amd64 (20120328)tigger@tigger-dedicated:/var/log/installer$

```

Sorry about that. Sorry if I've just made you check the bug over nothing.

---

### Post by kansasnoob on 2012-04-25
> **Lokie538 said:**
> ```
Ubuntu 12.04 LTS "Precise Pangolin" - Beta amd64 (20120328)tigger@tigger-dedicated:/var/log/installer$

```

Sorry about that. Sorry if I've just made you check the bug over nothing.

Don't be sorry. It's something that could have been overlooked.

What does the terminal show if you run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Lokie538 on 2012-04-25
> **kansasnoob said:**
> Don't be sorry. It's something that could have been overlooked.

What does the terminal show if you run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Just the usual hits. I have tried a variety of repo's, I thought the Australian one I was using might not have been the latest versions, but I just tried changing back to the main server.

```
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en
Fetched 71.1 kB in 10s (6,952 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Cavsfan on 2012-04-25
A fresh install sounds like a good idea. I would get the freshest daily build.

[[COLOR=blue]_http://cdimage.ubuntu.com/daily-live/current/_[/COLOR]]("http://cdimage.ubuntu.com/daily-live/current/")

---

### Post by Lokie538 on 2012-04-25
> **Cavsfan said:**
> A fresh install sounds like a good idea. I would get the freshest daily build.

[[COLOR=blue]_http://cdimage.ubuntu.com/daily-live/current/_[/COLOR]]("http://cdimage.ubuntu.com/daily-live/current/")

I think I will wait until final release, which will be tomorrow from what I understand from this thread? Thanks Cavsfan.

I am still happy to help if someone thinks it could possibly be a bug or anything, although it is nearly sleep time over here.

---

### Post by Cavsfan on 2012-04-25
> **Lokie538 said:**
> I think I will wait until final release, which will be tomorrow from what I understand from this thread? Thanks Cavsfan.

I am still happy to help if someone thinks it could possibly be a bug or anything, although it is nearly sleep time over here.

+1 on that idea!

I think I am going to wait until 12.04.1 comes out myself. I really like 10.04 :)

---

### Post by Lokie538 on 2012-04-25
> **Cavsfan said:**
> +1 on that idea!

I think I am going to wait until 12.04.1 comes out myself. I really like 10.04 :)

Haha so you've mentioned a few times :) 
I'm still still a Ubuntu / linux noob. I've only tinkered in Ubuntu before, so I thought I would finally install it on a server at home to give it a go properly and get some more experience. At work I only ever used Centos which I like, although I only install software, change software configuration and diagnose minor network issues, still in no way linux experienced.
I am looking forward to getting some experience in Ubuntu :)

---

### Post by kansasnoob on 2012-04-25
> **Lokie538 said:**
> I think I will wait until final release, which will be tomorrow from what I understand from this thread? Thanks Cavsfan.

I am still happy to help if someone thinks it could possibly be a bug or anything, although it is nearly sleep time over here.

Yes, all is well with my fresh install:

[ATTACH]216561[/ATTACH]

Please wait for the official release notice :)

BTW I needed this fresh install anyway, and I'll need to do many more over the next couple of weeks as I test and retest many things.

---

### Post by Lokie538 on 2012-04-25
> **kansasnoob said:**
> Yes, all is well with my fresh install:

[ATTACH]216561[/ATTACH]

Please wait for the official release notice :)

BTW I needed this fresh install anyway, and I'll need to do many more over the next couple of weeks as I test and retest many things.

So the diagnosis for my case is that It just isn't updated properly? I'm not sure why it isn't.....

Installed from this repo [http://mirror.aarnet.edu.au/pub/ubuntu/releases/12.04/ubuntu-12.04-beta2-desktop-amd64.iso](http://mirror.aarnet.edu.au/pub/ubuntu/releases/12.04/ubuntu-12.04-beta2-desktop-amd64.iso) 
and fully updated today... over 500mb of upgrades.....

Thanks for everyones help :)

---

### Post by Cavsfan on 2012-04-25
What is so great about this forum is that it is filled with knowledgeable people that are willing to help!
I have been involved with computers all my life, first electronic maintenance of mainframes and other computers, 
then programming them. I had some basic knowledge of Linux before installing (dual boot) Ubuntu.

You learn a lot of things over time and much of it will come from this forum.
Good Luck! :)

---

### Post by sgage on 2012-04-25
> **Lokie538 said:**
> So the diagnosis for my case is that It just isn't updated properly? I'm not sure why it isn't.....

Installed from this repo [http://mirror.aarnet.edu.au/pub/ubuntu/releases/12.04/ubuntu-12.04-beta2-desktop-amd64.iso](http://mirror.aarnet.edu.au/pub/ubuntu/releases/12.04/ubuntu-12.04-beta2-desktop-amd64.iso) 
and fully updated today... over 500mb of upgrades.....

Thanks for everyones help :)

Odd things sometimes happen during the development cycle. I've probably re-installed a dozen times since the first Alpha. It comes with the territory, and although sometimes you can sort out what's going on and fix it, sometimes it's easier and faster to simply reinstall and get a clean slate.

Deja-dup makes it quick and easy to save your personal settings and files and restore it all after a fresh install.

But tomorrow is the official release! I think Precise is going to be a great LTS release, whether you like Unity, Gnome Shell, Gnome Classic, or whatever.

---

### Post by Cavsfan on 2012-04-25
Is Gnome Classic pretty similar to Gnome 2 like on Lucid?

---

### Post by kansasnoob on 2012-04-25
> **Lokie538 said:**
> So the diagnosis for my case is that It just isn't updated properly? I'm not sure why it isn't.....

Installed from this repo [http://mirror.aarnet.edu.au/pub/ubuntu/releases/12.04/ubuntu-12.04-beta2-desktop-amd64.iso](http://mirror.aarnet.edu.au/pub/ubuntu/releases/12.04/ubuntu-12.04-beta2-desktop-amd64.iso) 
and fully updated today... over 500mb of upgrades.....

Thanks for everyones help :)

I don't understand it either, but I don't think that's a "trusted" download link.

---

### Post by sgage on 2012-04-25
> **Cavsfan said:**
> Is Gnome Classic pretty similar to Gnome 2 like on Lucid?

Yes, very similar. 2 panels, application and places menu in top panel, you can drag and drop programs from the menu to the panel for quick launchers, indicators and whatnot to the right. Window list and workspace switcher in bottom panel, etc.

A lot of what you would do with a right click in Lucid you do with an Alt-right click now.

Available in 2 flavors - Gnome Classic (using Compiz) and Gnome Classic No Effects (using straight-up Metacity).

If you want to try it in Precise, install gnome-fallback-session. Or install gnome-shell if you want to try it as well - it pulls in the gnome-fallback-session.

---

### Post by Cavsfan on 2012-04-25
> **sgage said:**
> Yes, very similar. 2 panels, application and places menu in top panel, you can drag and drop programs from the menu to the panel for quick launchers, indicators and whatnot to the right. Window list and workspace switcher in bottom panel, etc.

A lot of what you would do with a right click in Lucid you do with an Alt-right click now.

Available in 2 flavors - Gnome Classic (using Compiz) and Gnome Classic No Effects (using straight-up Metacity).

If you want to try it in Precise, install gnome-fallback-session. Or install gnome-shell if you want to try it as well - it pulls in the gnome-fallback-session.

Thanks for that info! :) 
Not sure I like the Alt-right click but, if that is the way it is, I'll get used to it.
I'm not changing for a while.

---

### Post by cryptotheslow on 2012-04-25
This is odd. When I look at User Accounts I also don't have the automatic login slider displayed for my account (the first account), however when I select another user in the list on the left the automatic login slider appears. :confused:

Could the difference be that my account has an encrypted home whereas the other doesn't?

---

### Post by Cavsfan on 2012-04-25
My screen is looking too cool to change in a hurry. I don't want to lose what I have!

[[IMG]http://ompldr.org/tZGlmNQ[/IMG]]("http://ompldr.org/vZGlmNQ")

I even have cairo-dock version 3.0.0 with impulse. Loving it!
Is all this possible in PP?

OK, I'm off topic. This is my last post.
Good Luck!

---

### Post by sgage on 2012-04-25
> **Cavsfan said:**
> My screen is looking too cool to change in a hurry. I don't want to lose what I have!

[[IMG]http://ompldr.org/tZGlmNQ[/IMG]]("http://ompldr.org/vZGlmNQ")

I even have cairo-dock version 3.0.0 with impulse. Loving it!
Is all this possible in PP?

OK, I'm off topic. This is my last post.
Good Luck!

I don't know, but strongly suspect that it is. But I am a minimalist in these matters - just a tasteful wallpaper and I'm content :KS

---

### Post by kansasnoob on 2012-04-25
> **Cavsfan said:**
> Is Gnome Classic pretty similar to Gnome 2 like on Lucid?

I'm workin' on it:

[http://ubuntuforums.org/showpost.php?p=11835822&postcount=389](http://ubuntuforums.org/showpost.php?p=11835822&postcount=389)

---

