---
title: "Need help, seeing same issues of window virus since switching to ubuntu"
date: 2011-05-01
forum: Security
---

### Post by Ubun2help on 2011-05-01
Now I know that some of you are going to say, this is just a simple pop up and that I have nothing to worry about, that I have to choose to run a program etc etc etc.... Well this is the start of the same virus as the windows security center virus, I know because in the last week or two I had that virus and for that very reason decided it was time to make the complete jump to ubuntu, now as of this morning, while surfing I have had this happen a couple times, specifically so far while looking through pics on google image search. I click on a picture to go to the page for said picture and instead this comes up... This is how windows security root kit started when I had it, Now that im seeing a couple of pages this morning redirected to this it is worrying me just a bit.... Im not sure if I have a virus, what I do know is this is how the other started and I have no idea how its redirecting web pages on me if I dont...... any light that can be shed on this would be very very appreciated.

---

### Post by collisionystm on 2011-05-01
Look at your address bar.... your Firefox had its search provider changed with a cookie or somekind of popup you clicked. You need to run Firefox in safe mode and reset it.

Perhaps you frequent bad sites? Just because its linux does not change the fact that you are using Firefox ( also available in windows). Stay off bad sites and don't click stupid toolbars and popups. Oh and watch where you are installing software from. You can't trust ppa's and repo's just because they say they have ubuntu software.

---

### Post by Ubun2help on 2011-05-01
I havent clicked on a popup, or installed anything that wasnt on ubuntu software center.... any useful advice?

---

### Post by bodhi.zazen on 2011-05-01
> **Ubun2help said:**
> I havent clicked on a popup, or installed anything that wasnt on ubuntu software center.... any useful advice?

1. Linux is not windows and there are no known active linux viruses.

2. Not every problem you might have in Windows is a virus.

3. Use Noscirpt.

---

### Post by chris0161 on 2011-05-01
If this is the first screen you see when you open Firefox then something has changed you Home Screen setting and the message you get is from a malicious site and has nothing to do with Mozilla.

Do not click on the okay button as it may trigger a script and try and install a virus on your machine.

Go into Edit > Preferences in Firefox and in the Home Page box type [http://www.google.co.uk/](http://www.google.co.uk/) and save.

When you restart Firefox it should take you to Google home page. If not something nasty has installed itself on your machine and is messing with the Firefox configuration files.

Its possible you have a file with a hidden payload (maybe a pdf or image file which you brought over to Ubuntu form Windows.

For example while running Windows you received an image file in an email or downloaded it. When you clicked on it to see the image a hidden script executed and infected Firefox. When you installed Ubuntu you copied your personal files across as the image will display on both operating systems. When you viewed the file in Ubuntu the hidden script also executed and as Firefox has common configuration files for Windows and Ubuntu you got the same problem.

If this is the case I would reinstall Ubuntu and try running Firefox before you import any personal files.

Good Luck

---

### Post by Ubun2help on 2011-05-01
Thanks for some of the info guys, Ive never clicked on it, In windows id have to end firefox's process and then start it again in safe mode, in ubuntu ive been able to click the back button and get away, I dont get prompted with that "are you sure you want to leave this page message"...It hasnt happened since I cleared my cookies earlier, hopefully that deals with it. Going to add no scipt now.

---

### Post by EGamerHDK on 2011-05-02
Please update this when you get an answer because I'm just curious to how this turns out. I have a feeling you might just be getting redirected to some website that is showing that message. I mean the address bar tells it all. You are going to some website that ends up giving you that message.

---

