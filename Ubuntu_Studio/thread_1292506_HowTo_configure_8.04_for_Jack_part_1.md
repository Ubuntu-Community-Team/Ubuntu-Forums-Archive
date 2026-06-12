---
title: "HowTo configure 8.04 for Jack part 1"
date: 2009-10-15
forum: Ubuntu Studio
---

### Post by llwdtp on 2009-10-15
This is the story of a successful configuration of Ubuntu Studio 8.04 to get jack to run. It was a long road, but I have *mostly* arrived. I think.

The main guide is done by [Studio Dave]("http://www.linuxjournal.com/content/judgement-day-studio-dave-tests-ubuntu-studio-904"). That guide was for Ubuntu Studio 9.04. This description is for 8.04. I am going to try to detail the steps I used even though they are in Studio Dave's guide.

The first issue is pulseaudio. Pulseaudio does not get along well with Jack. Some folks reference a module that lets pulseaudio and jack play with each other. But I did not find that module.  I used the instruction given by idyllic in this [Howto]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/"). As far as I know there is nothing wrong with pulseaudio. THe problem is I did not know how to make it work with Jack, Qsynth and Rosegarden.

[SIZE=5]**Audio Group**[/SIZE]
First, the audio group also needs to be added. Go to* [SIZE=2]**System>administration>users and groups**[/SIZE]* and click on Unlock
[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_4g64mzdgb_b[/IMG][/LEFT]

Then put in the administrators password and click Authenticate
[IMG]http://docs.google.com/File?id=dhjrjpnc_5gpdkbsdm_b[/IMG]

Now Click on Manage Groups

[IMG]http://docs.google.com/File?id=dhjrjpnc_6hkgvs7gc_b[/IMG]

Now add the audio group by clicking on "Add Group"

[LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_7gm476xf3_b[/IMG][/LEFT]

and put in the name "audio" and click on all of the users that you want to be part of the audio group
[IMG]http://docs.google.com/File?id=dhjrjpnc_8d5w5mkct_b[/IMG]

Close out of these dialogs.


[SIZE=5]**Enable Real time Memory**[/SIZE]
 [SIZE=2]Click on[/SIZE]*[SIZE=2]** System>administration>Ubuntu Studio Controls **[/SIZE]*[SIZE=2]and enter the administrator password.
[/SIZE][I][SIZE=2][B][LEFT][IMG]http://docs.google.com/File?id=dhjrjpnc_9hmjxfsgj_b[/IMG][/LEFT]

[/B][/SIZE][/I][SIZE=2]Select the amount of memory to dedicate to the real time memory and click ***Enable Memlock. ***Make sure and click ***apply*** before clicking ***OK***.  I think you need to restart the computer at this point to make the memory changes take hold.

Please continue by reading
***HowTo configure 8.04 for Jack part 1***
[/SIZE]

---

