---
title: "Finally a Linux Desktop for the Layperson"
date: 2007-04-26
forum: Testimonials &amp; Experiences
---

### Post by Brian Levy on 2007-04-26
Well, yesterday downloaded the new release and burnt a DVD.  First tried it live on my Compaq N610C and everything went smoothly.  Then the big hassle; getting it to work with the WiFi card.  I have a D-Link DWL-650+ that seems to be a workhorse but on loading Linux usually have to give it to Junior to find and get the card working, even with 6.06.  I am really backwards in things I do.  The Compaq is a business machine that is bullet proof so I use it at home for nonbusiness things and have a home unit, a Toshiba Satellite PC60 (or something) that would be a great home media machine working in the office with a really nice 17" screen.

The Compaq has been running in XP Home and most of the time I use it for e-mail and download and listen to old time radio programs and watch old time movies or tv shows.  I never could get them to work with 6.06 but with this version MoviePlayer needed a plug-in or so, immediately found them, downloaded and everything worked 1st time. No hitches, dropouts or anything.  I use OOo daily in my business and used to used to Mozilla so everything seems so familiar and easy.  Only challenges seem to be the need to add Java for LogMeIn that I use to access my office system when offsite and then to see if I can somehow get my UTC 6700 PPC that uses MW 5.0 to somehow sync and transfer files (just bought it and that was a mistake - stay with a Palm based unit).

Bottom line is that for the first time Linux is almost there as a layperson's practical desktop operating system.  The system seems to install smoothly, everything ran without having to do prompt level commands.  The wireless card setup was even easier than I find doing the Windows setup.

---

### Post by mrvertigo on 2007-04-26
congrats! welcome to easy street AKA ubuntu

---

### Post by rggavubt on 2007-04-27
Release 7.04 has java package already built in....you should not have to add it??  I had to install it when I used 6.06LTS but not for 7.04

---

### Post by RedBeard3 on 2007-05-03
I also use LogMeIn to access several Windows OS PCs for various business and personal reasons, and while Java is included with Fiesty Fawn (AKA 7.0.4) you need to load Sun's JRE and set the alternatives so FireFox uses the right version of Java (I hear this step is also necessary for folks who need to fun Sun's JRE for a host of reasons, like P2P).

I used the steps found at this URL - [http://users.piuha.net/martti/comp/ubuntu/install.htm](http://users.piuha.net/martti/comp/ubuntu/install.htm) - to perform a number of tasks including installing codecs that might help you with the video viewing problem you mentioned (it helped me out there as well).  

The Java specific steps are as follows:

# sudo apt-get install sun-java5-jre sun-java5-fonts sun-java5-plugin
# sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

I simply updated them to 6 by replacing the 5 in all instances, and low and behold it worked.  If memory serves you'll need to reboot to make the setting affective, and may also have to check the "enable java" box on the content tab of FireFox preferences.

good luck,
Harry

---

### Post by aysiu on 2007-05-03
I've moved this to our Testimonials and Experiences section.

---

