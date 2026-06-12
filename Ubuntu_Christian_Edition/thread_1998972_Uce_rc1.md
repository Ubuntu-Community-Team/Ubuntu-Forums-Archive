---
title: "Uce rc1"
date: 2012-06-07
forum: Ubuntu Christian Edition
---

### Post by stlsaint on 2012-06-07
UCE RC1 :guitar::popcorn:

I say RC1 because this is a stable OS as it's built off Ubuntu 12.04 LTS.
Let it be known now that this is a stable OS and can as such be installed to hardware but i would prefer that this remain as a test stage until im able to release a OS at a standard befitting UCE!! The biggest bump right now is artwork to truly customize this into a Christian distro! Also once we orgainze the christian repository we will be able to add on many more third-party applications! Big plans for final release!!

Brief changelog:

The ISO is 1.4 GB and that is because it is fully up to date with all updates since the official 12.04 release plus applications!

Applications: 
DansGuardian + Privoxy for Web Content Filter
Xiphos*
Lyricue
OpenLP 
Bibletime
Bible Analyzer
Quelea
BleachBit
Remastersys
Terminator
gnome-tweak-tool
Pastebinit

Unity Lens:
Photo 
Video (to include youtube)
Files
Wikipedia
US Cities

Artwork:
Unity custom themes and Icons

Now what makes this a RC1 is that there is still work to be done as you will see below.

Artwork is still needed. Custom wallpapers, splash images, etc
Customizing ubiquity installer to fit UCE
Bring in Wine stable (some bugs being worked out now)
Provide installer for E-sword
**Clean up the UCE repository for addition of more third party applications**

For most consistent download use wget with -c switch

```
wget -c downloadlink.com 
```

The two listed download links are available now but the people.ubuntu.com link will be removed once the torrent is fully up and running. Please use torrent once its up. Again i stress this is NOT the final release! But it is stable if you want to use now.

First link: [http://db.tt/v3fviyZi](http://db.tt/v3fviyZi)  #This is via dropbox
Second link: [Ubuntu Christian Edition RC1 torrent]("http://linuxtracker.org/index.php?page=torrent-details&id=df73fb04a7a863e7e5d15489bfec695a97123024") #Currently having issues with torrent. DP link would be better!

---

### Post by stlsaint on 2012-06-07
Im going to take this slot to use for any release information or notes discussed or needed for UCE RC1.

Fist off: 
(NOTE: To enable DG, point your browser to manual proxy: 127.0.0.1 with port 8080) DG and privoxy should already be running!
If not than:
```
 sudo service privoxy start 
```
then
```
 sudo service dansguardian start 
```

Secondly: There is one custom theme plus many icons. Themes are simple to install as i have already added the ppa. Use y-ppa-manager and view the packages for the noobslab/themes ppa to see all themes.

Watch this thread as I will add more information as more testing brings them to light.

---

### Post by sffvba[e0rt on 2012-06-07
Congrats on the RC1.  I will test it out in VBox as soon as I am back home.


404

---

### Post by stlsaint on 2012-06-07
> **not found said:**
> Congrats on the RC1.  I will test it out in VBox as soon as I am back home.


404

Thanks. All contructive critique welcome!

---

### Post by KBD47 on 2012-06-09
Installed to a 4 gig usb stick with 1.5 gig persistence. I don't know if it was because I was in the live usb mode, but got a [fail] on trying to launch dansguardian using the commands in terminal you list above. Everything else functioning well, wireless connected, apps working, I launched Xiphos and installed some bibles without issue. Looks good so far, will be interested in seeing the final version :-)

edit/update: I suggested elsewhere that you should have a second edition for older hardware, but then I noticed you have installed gnome-panel to UCE, so really there would be no need for a second edition since gnome-panel will work well on older hardware just fine logged into classic with no effects. I would suggest adding Ubuntu Tweak, it gives the user a bit more control and would allow them to turn off HUD. Your selection of apps is excellent, even if I didn't want this for the Christian elements I'd still choose it over regular Ubuntu because it has the apps I would install right away like synaptic, gdebi, and chromium. I think a wiki telling users how to log into classic, and how to remove the overlay scrollbars, and global menu, and how to add the restricted extras, and how to make the launcher smaller and/or autohide, some very basic how-to info would be useful I think. That and add some nice Christian themed wallpaper, and maybe a screensaver with a Christian theme, definitely will be impressive.

---

### Post by KBD47 on 2012-06-09
stlsaint, I went ahead and did a full install to a 16 gig usb stick to give me more control and options with the OS. I notice you have Chromium set as the default browser, which is good, but Firefox is the browser in the launcher. I would suggest either going ahead and setting Firefox as the default browser, or removing it from the launcher and putting Chromium in there so the default browser is also the launcher browser. I think Gimp would be useful to add to the default apps, maybe Sunday School teachers or others would find it useful/necessary. Speaking of Gimp, if you wanted to stick with the overall Ubuntu feel for the default, someone handy with Gimp could take the default wallpaper and put a nice cross and some scripture verse on it. Other themes could be added for more choices, but the Ubuntu flavor could be just slightly tweaked on the default for a bit of Christianizing (is that a real word?) :lolflag:

---

### Post by stlsaint on 2012-06-09
> **KBD47 said:**
> stlsaint, I went ahead and did a full install to a 16 gig usb stick to give me more control and options with the OS. I notice you have Chromium set as the default browser, which is good, but Firefox is the browser in the launcher. I would suggest either going ahead and setting Firefox as the default browser, or removing it from the launcher and putting Chromium in there so the default browser is also the launcher browser. I think Gimp would be useful to add to the default apps, maybe Sunday School teachers or others would find it useful/necessary. Speaking of Gimp, if you wanted to stick with the overall Ubuntu feel for the default, someone handy with Gimp could take the default wallpaper and put a nice cross and some scripture verse on it. Other themes could be added for more choices, but the Ubuntu flavor could be just slightly tweaked on the default for a bit of Christianizing (is that a real word?) :lolflag:

I thank you for the feedback. Yes Chromium will be default browser and I will see on making chromium in launcher. Also i dont see a major issue with adding gimp. I will have to see how big it makes the ISO. Also i am not a gimp guru at all and am in constant search of someone who could polish up some walls i have for UCE final. Also i added a couple ppa's with alot of themes for installing. Will also look at iso size to include more themes. As for your first post of the live usb issue i would want to see some logs so i can pinpoint an issue. I will try it myself also. There also will be many more ce editions coming. Im honestly anxious to release UCE final so i can begin works on a debian edition with free reign to build from scratch. The selection of apps came with the thought in mind of users being able to see this as an everyday distro in all types of organizations, thanks for noticing. Also take a swing at the nautilus scripts included. :D Now as for the documentation work, I must be honest and say that those wiki's will have to take a back seat if im left to do them until after final release and proper configuration for current and future repositories for UCE. Just know the item is on the list....just towards bottom unless someone else wanted to take on the task. ;) Thanks again for feedback. Any more thoughts shoot them here or mailing list.

---

### Post by KBD47 on 2012-06-09
I used your instructions above and got Firefox working with dansguardian. I threw some foul words in the search engine and it blocked them. I don't think it is perfect security, but probably will provide some measure of filtering for the most offensive terms/subjects. 
  UCE right now feels as solid and stable as Ubuntu 12.04 should. I think once you tweak the final apps they way you like and get the wallpaper/themes on board, this one is ready to go.
   I wish I was good with Gimp, to me it is not very intuitive. But it's what we have in Linux. 
  I can help with some writing, but I really need more info about who started the project, why it was started, it's goals, who it is specifically targeted toward in the Christian community, e.g., to provide a safe OS for children, to give pastors/bible teachers/sunday school teachers tools for ministry, outreach, just Christians in general, or all of the above.
  The UCE web site appears to be gone, there is nothing on wikipedia about it, and distrowatch has it labelled dormant. It definitely needs an infusion of energy and support :-) We need to recruit that amjjawad (sp?) guy who is fired up about Lubuntu :-)
  I'm happy to help, just would like more info and some place to focus my writing effort. I will carve out space on my hard drive when you release the final, will review it on my blog, spend some time with it and help with documentation with my limited technical abilities :-)
Thanks again for your work on this. I think there is an audience, we just need to find them and point them in the right direction regarding the distro :-)

---

### Post by KBD47 on 2012-06-10
Keep in mind that I'm a novice with gimp. 
Here is a wallpaper I made:
[http://i1250.photobucket.com/albums/hh521/kbd47/4new_wallpaper_final_full_size02a.jpg](http://i1250.photobucket.com/albums/hh521/kbd47/4new_wallpaper_final_full_size02a.jpg)

Here is it set as my wallpaper:
[http://i1250.photobucket.com/albums/hh521/kbd47/Screenshotfrom2012-06-10004747.png](http://i1250.photobucket.com/albums/hh521/kbd47/Screenshotfrom2012-06-10004747.png)

---

### Post by KBD47 on 2012-06-10
2 more and I've probably stretched the limits of my artistic ability :-)

water:
[http://i1250.photobucket.com/albums/hh521/kbd47/6water.jpg](http://i1250.photobucket.com/albums/hh521/kbd47/6water.jpg)

bridge:
[http://i1250.photobucket.com/albums/hh521/kbd47/6bridge.jpg](http://i1250.photobucket.com/albums/hh521/kbd47/6bridge.jpg)

---

### Post by Megaptera on 2012-06-10
KBD47,
Those are great! Thanks for sharing.

---

### Post by KBD47 on 2012-06-10
You are welcome. Glad you like them :-)
The first one of course is regular Ubuntu wallpaper I added text to. The second two are my own photos taken near where I live. The one with the water was an accidental special effect with the blurred colors, just the way the light played on the camera lens. I love the red bridge, it is at a nearby park.

---

### Post by forrestcupp on 2012-06-10
I don't care which browser you use, but here's something applicable to this project to keep in mind. Firefox has a lot of good free antiporn addons, and I haven't been able to find any at all for Chrome. I know that you're focusing on Dansguardian being the solution for that, but I just thought I'd throw that out there. I really don't think Flash support is going to be an issue with using Firefox, if that is part of your reasoning.

---

### Post by stlsaint on 2012-06-10
> **forrestcupp said:**
> I don't care which browser you use, but here's something applicable to this project to keep in mind. Firefox has a lot of good free antiporn addons, and I haven't been able to find any at all for Chrome. I know that you're focusing on Dansguardian being the solution for that, but I just thought I'd throw that out there. I really don't think Flash support is going to be an issue with using Firefox, if that is part of your reasoning.

Thanks for the insight. I am not much a firefox user so i am not sure of all its addon's granted i do know there are boat loads. Flash was not a concern, it was more so resource usage between the two that lead me towards chromium since low hardware usage may be employed to put UCE on. I will definitely look at adding firefox addons.

---

### Post by Anastasis on 2012-07-03
> **stlsaint said:**
> UCE RC1 :guitar::popcorn:

I say RC1 because this is a stable OS as it's built off Ubuntu 12.04 LTS.
Let it be known now that this is a stable OS and can as such be installed to hardware but i would prefer that this remain as a test stage until im able to release a OS at a standard befitting UCE!! The biggest bump right now is artwork to truly customize this into a Christian distro! Also once we orgainze the christian repository we will be able to add on many more third-party applications! Big plans for final release!!

Brief changelog:

The ISO is 1.4 GB and that is because it is fully up to date with all updates since the official 12.04 release plus applications!

Applications: 
DansGuardian + Privoxy for Web Content Filter
Xiphos*
Lyricue
OpenLP 
Bibletime
Bible Analyzer
Quelea
BleachBit
Remastersys
Terminator
gnome-tweak-tool
Pastebinit

Unity Lens:
Photo 
Video (to include youtube)
Files
Wikipedia
US Cities

Artwork:
Unity custom themes and Icons

Now what makes this a RC1 is that there is still work to be done as you will see below.

Artwork is still needed. Custom wallpapers, splash images, etc
Customizing ubiquity installer to fit UCE
Bring in Wine stable (some bugs being worked out now)
Provide installer for E-sword
**Clean up the UCE repository for addition of more third party applications**

For most consistent download use wget with -c switch

```
wget -c downloadlink.com 
```The two listed download links are available now but the people.ubuntu.com link will be removed once the torrent is fully up and running. Please use torrent once its up. Again i stress this is NOT the final release! But it is stable if you want to use now.

First link: [http://db.tt/v3fviyZi](http://db.tt/v3fviyZi)  #This is via dropbox
Second link: [Ubuntu Christian Edition RC1 torrent]("http://linuxtracker.org/index.php?page=torrent-details&id=df73fb04a7a863e7e5d15489bfec695a97123024") #Currently having issues with torrent. DP link would be better!

Look like you guys have been doing a lot of good work during this spring and summer. I'm just getting back settled into a new apartment here in Asia for the next year, so I might be able to have some time to give the new effort a spin on my laptop.

Everything looks great. There's just one little problem. I can't download it. The dropbox link doesn't work and the torrent has no seeders. If I could just get a little iso file of it, that'd be great. Thanks. 

Blessings. ;)

---

### Post by bodhi.zazen on 2012-07-03
I think moving the iptables rules to ufw was a good move :twisted:

---

### Post by stlsaint on 2012-07-03
> **bodhi.zazen said:**
> I think moving the iptables rules to ufw was a good move :twisted:

Agreed, very nice move!

---

### Post by mikodo on 2012-08-04
Hello,

Could we install the Xubuntu-desktop metapackage on top of the Uce rc1 and boot into a make-shift Xubuntu Christian Edition?

```
sudo aptitude update && sudo aptitude safe-upgrade

sudo aptitude install xubuntu-desktop
```It would be a bit more cluttered Xfce-deskop menu of apps and such, than just Unity-desktop, but still an Xfce desktop.

Or, am I dreaming in technicolor?

Thank you, for the wonderful effort!

---

### Post by stlsaint on 2012-08-05
> **mikodo said:**
> Hello,

Could we install the Xubuntu-desktop metapackage on top of the Uce rc1 and boot into a make-shift Xubuntu Christian Edition?

```
sudo aptitude update

sudo aptitude install xubuntu-desktop
```It would be a bit more cluttered Xfce-deskop menu of apps and such, than just Unity-desktop, but still an Xfce desktop.

Or, am I dreaming in technicolor?

Thank you, for the wonderful effort!

That should be fine. I have not done it personally so in your case i would try it first maybe in a virtual machine with vbox and see how it works. But i see no major immediate issues but again don't try it on a production system just to be super safe.

---

### Post by mikodo on 2012-08-05
> **stlsaint said:**
> That should be fine. I have not done it personally so in your case i would try it first maybe in a virtual machine with vbox and see how it works. But i see no major immediate issues but again don't try it on a production system just to be super safe.
Thanks. Will do.

---

### Post by ubun2geek on 2012-08-17
Ok, it's nice to see someone firing the project back up again. Just wondering why the website isn't being updated. ;)
However, it looks like you are doing a fine job! I think I could make some wallpapers for you. One question, is this a Christian or a Catholic project? To me, this is important. Keep up the good work!
Nick

---

### Post by stlsaint on 2012-08-19
The project is not geared towards one non-denom or Catholic or any other. If is a project for those of Christ faith in general. There will never show preference for one variant or another.

---

### Post by ubun2geek on 2012-08-19
I guess I was just curious what denomination the project members are if you don't mind answering.

---

### Post by stlsaint on 2012-08-19
> **ubun2geek said:**
> I guess I was just curious what denomination the project members are if you don't mind answering.

Ah ok. There are two things to address with your question. 
1. Please try not to change threads towards another topic. IE: The thread starts with a RC of UCE so lets not change it to "what is your religion".

2. We have tried such threads before and it causes alot of conflict with starting to discuss various denominations and then it turns into who's denomination is better and why! :guitar:

So we refrain from starting such threads. Personally i have no issues with discussing my denomination but this is not the place for it! ):P

---

### Post by bodhi.zazen on 2012-08-21
> **stlsaint said:**
> ah ok. There are two things to address with your question. 
1. Please try not to change threads towards another topic. Ie: The thread starts with a rc of uce so lets not change it to "what is your religion".

2. We have tried such threads before and it causes alot of conflict with starting to discuss various denominations and then it turns into who's denomination is better and why! :guitar:

So we refrain from starting such threads. Personally i have no issues with discussing my denomination but this is not the place for it! ):p

+1

---

### Post by josephmills on 2012-08-29
I would love to help with this and sense you all are using 2d I def can. This is what I was thinking that I can help out with. 
Building and making a personalized unity2d for you all. Like have the pictures that are in the background be the dash background picture with a light opacity. 

I will Tell you what...

 I will start to make something. (and post picture's/videos)

Do you all have a branch on launchpad or a personal branch ? (will google after posting )

I will be free for the next 2 weeks so. I think that this could be cool.

---

### Post by stlsaint on 2012-08-30
> Do you all have a branch on launchpad or a personal branch ? (will google after posting )

Hey mills, we are on lp but for now a personal branch should be fine.

---

