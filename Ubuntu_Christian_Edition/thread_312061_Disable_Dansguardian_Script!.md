---
title: "Disable Dansguardian Script!"
date: 2006-12-03
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2006-12-03
[COLOR=Red][COLOR=Black][B]This thread is deprecated. The latest release of Ubuntu CE now includes the feature by default.
[http://www.mirror.christianubuntu.com](http://www.mirror.christianubuntu.com)
[/B][I]
Edit: I have attached a .deb package that will update your Dansguardian GUI to include the ability to disable/enable dansguardian. This will definitely be added in the next release of Ubuntu CE.[/I]
[/COLOR][/COLOR]
You can also use the attached script if you prefer. See below:

There have been many requests for a way to easily disable dansguardian. I do not want to make this too easy. However, I have decided to release a script that will allow users to easily disable/enable dansguardian. It will of course require root access. This script may eventually make it into the Dansguardian GUI. It will depend on the results from user experience with the script.

This script was tested on a fresh install of Ubuntu CE v2.0 (Edgy) only. It should also work on Ubuntu CE v1.5.1 (Dapper). If you have made any changes to the default dansguardian setup that ships with Ubuntu CE then results may vary.

[COLOR=Red]**PLEASE USE AT YOUR OWN RISK!**[COLOR=Black]

1. Download the attached archive.
2. Close Firefox.
3. Extract the archive.
4. Open the folder 'disable_dansguardian'.
5. Double Click the 'disable_dansguardian' file.
6. Choose 'Run In Terminal'.
7. Enter your root password.
8. Wait for the prompt.
9. Click 'Ok'.
10. That's it!

If you decide you want to enable dansguardian at a later date simply use the directions above on the 'enable_dansguardian' file.

I hope this will help those who are having trouble.

Thanks, Jereme
[/COLOR][/COLOR]

---

### Post by Darrious on 2006-12-03
Thanks.

I will try this and tell you how it goes. I hope everything works okay.

---

### Post by doobit on 2006-12-04
I think the problem I was having was partially related to the way I installed Dansguardian to begin with. I'll try it again tonight. I would really like to have the parental controls panel working under administrator mode so I can recommend it to parents the way it was intended. It shouldn't be too easy to disable.

---

### Post by mhancoc7 on 2006-12-04
> **doobit said:**
> I think the problem I was having was partially related to the way I installed Dansguardian to begin with. I'll try it again tonight. I would really like to have the parental controls panel working under administrator mode so I can recommend it to parents the way it was intended. It shouldn't be too easy to disable.

Let us know how it goes. I think the addition of the Enable/Disable buttons on the attached .deb is going to be nice. It will still require root access so it should not make it any easier to disable.

Jereme

---

### Post by HareBall on 2006-12-04
> **mhancoc7 said:**
> Let us know how it goes. I think the addition of the Enable/Disable buttons on the attached .deb is going to be nice. It will still require root access so it should not make it any easier to disable.

Jereme

Seems to work fine on my puter. I just got through installing it. I want to be able to lock certain people out of some things when they come to visit, but not have it bothering me when I am the only one using it.
Thanx.

---

### Post by Darrious on 2006-12-04
Do you think you might want to update the tutorial here.

---

### Post by Darrious on 2006-12-04
It works very well and it is good I do not have to go through the two scripts.

---

### Post by doobit on 2006-12-04
OK! I found out the whole set of minor problems in the convert_me script when trying to convert Xubuntu Edgy was due to not having zenity. I used Synaptic to download and install zenity, then used sudo su to run the convert_me script in the terminal (./convert_me) and it installed properly this time.
Then I ran the new GUI .deb (dpkg -i dansguardian-gui-ubuntu_1.3_all.deb ) and it installed just fine. Everything is good now.
Thank you Jereme!

---

### Post by Darrious on 2006-12-04
That is very good that you have figured out this problem.

---

### Post by mhancoc7 on 2006-12-04
> **Darrious said:**
> It works very well and it is good I do not have to go through the two scripts.

Glad to hear it. :)

> **doobit said:**
> OK! I found out the whole set of minor problems in the convert_me script when trying to convert Xubuntu Edgy was due to not having zenity. I used Synaptic to download and install zenity, then used sudo su to run the convert_me script in the terminal (./convert_me) and it installed properly this time.
Then I ran the new GUI .deb (dpkg -i dansguardian-gui-ubuntu_1.3_all.deb ) and it installed just fine. Everything is good now.
Thank you Jereme!

I am glad that you have got it working. I did not realize you were installing on Xubuntu.

Jereme

---

### Post by doobit on 2006-12-05
> **mhancoc7 said:**
> Glad to hear it. :)



I am glad that you have got it working. I did not realize you were installing on Xubuntu.

Jereme

Xubuntu requires a slightly different procedure to install because there is no terminal access in the right click properties menus. You need to open the terminal, navigate to the file's path and use sudo or sudo su and then run the file. 
The enable and disalbe buttons work great. I have not yet gotten the buttons for the whitelist scripts to open anything. I'll work on that more later when I get a chance.

---

### Post by mikexgough on 2006-12-06
I was glad to get rid of Dansguardian, too restrictive, love the Christian Edition other than this, I have uninstalled completely

---

### Post by doobit on 2006-12-06
The idea with dansguadian is that you should be able to adjust the restrictions based on blacklists and whitelists in the parental controls panel. Jereme also added enable and disable. We use Trend Micro's Office Scan where I work and it does the same thing, but is much more expensive.

---

### Post by Darrious on 2006-12-06
When I first started to use DansGuardian I got upset with it because I did not know how to use it. It just stopped me from downloading anything ect. 

Then I actually had to learn to use it and I can figure out how to control it now. But still, that enable/disable button does work good.

---

### Post by mikexgough on 2006-12-14
well I am best off without it thanks, other than that the Christian Edition is a great idea, should have an option not to install dansguardian though

---

### Post by doobit on 2006-12-14
> **mikexgough said:**
> well I am best off without it thanks, other than that the Christian Edition is a great idea, should have an option not to install dansguardian though

DansGuardian makes it possible to control what other people do on the computer. With the new GUI and scripts that Jereme created you can disable and enable it at will, as the computer's administrator.
It's really a great feature to have on a local machine, considering it was originally designed as a control on a network level.

---

### Post by C-A on 2007-01-24
First, I love the Christian Edition. Thanks to all who have worked on it. I just “ converted” to it and appreciate the additions.

When I “converted” I was aware that dansguarian was installed. However, I did not realize that it was running. Later, I installed D4X and then flashgot. Suddenly, I was aware that dansguardian was installed. I tried to download an .iso file but was stopped by dansguardian. I went to the black list and commented out the .iso file extension ( I assumed this was the correct way to edit the list) but still could not download the .iso file. 

 I then came upon this thread I tried to download the script but once again dansguardian stopped my download. Luckily, I was able to install the .deb file and then disable dansguardian.

I am not sure if my problem was due to a user error or related to D4X or flashgot. Anyway, I hope to enable dansguardian in the future, so I will be curious to hear about other peoples' experiences.

---

### Post by C-A on 2007-01-29
See me post above.  I have since installed opera. I tried downloading a file in opera but was stopped by dansguardian! :confused: I guess I will un-install it for now and maybe give it a try in the future.

---

### Post by dakotadare2b on 2007-01-29
I have had no issues with downloading files, after I figured out what things needed to be commented out and where...mostly by trial and error. :) I use Firefox exclusively, but have tried Opera; both after converting to CE w/Dansguardian.

I would imagine that you are downloading the .iso file as a zipped file. If so, you will not only have to comment out the .iso file type but also the type of zip file format that you are downloading (.zip, .rar, .gz, .tar, etc.). You will need to do this in two places within Dansguardian, if a .zip or .gzip file: 1) Blocked File Extensions and 2) Blocked MIME Types.

If you have tried this already, I'm sorry I couldn't be of more help; but if not, it is worth a shot.

Randy

---

### Post by C-A on 2007-02-01
Thanks for the reply. It was a .zip file that I tried to downloaded but I had already commented out the file type and disabled dansgaurdian. Firefox works with no problem since disabling dansgaurdian but for some reason when I installed opera, dansgaurdian blocks downloads  when using opera.

---

### Post by mhancoc7 on 2007-02-01
> **C-A said:**
> Thanks for the reply. It was a .zip file that I tried to downloaded but I had already commented out the file type and disabled dansgaurdian. Firefox works with no problem since disabling dansgaurdian but for some reason when I installed opera, dansgaurdian blocks downloads  when using opera.

Yes, the Dansguardian GUI only disables Dansguardian for firefox. If you install another browser it will still be filtered.

This is going to be fixed when Ubuntu CE v2.1 comes out. The Disable button will completely disable dansguardian system wide.

Jereme

---

### Post by mrdav1e on 2007-02-05
Please include an option to install / not install dansguardian when updating to ce.
Thanks!

---

### Post by mhancoc7 on 2007-02-05
> **mrdav1e said:**
> Please include an option to install / not install dansguardian when updating to ce.
Thanks!

This has been requested once before. I understand that many would not like to have the filtering or just don't need it. However, the parental filtering is really the biggest feature of Ubuntu CE. The next release, which I am finishing up as I type, will have an enhanced Dansguardian GUI which will easily allow the root user to completely disable dansguardian system wide.

Jereme

---

