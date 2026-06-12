---
title: "HOW TO: Hide VLC videos on an iPhone"
date: 2011-02-25
forum: The Cafe
---

### Post by JohnElway on 2011-02-25
IMPORTANT NOTES: -This has nothing to do with Ubuntu. I've decided to  post it here since this is the only technical forum I visit consistently  and I figured I'd try to give back to the community.

-Your  iPhone must be jailbroken for this to work. I'm not sure what firmware  version would be required to follow this guide, but for what it's worth  my iPhone has version 4.2.1 firmware.

-Your iPhone must have the  following software installed: OpenSSH, some kind of ssh terminal client  (I'm using Touch Term), and VLC (I'm not sure if the version from the  App Store would work, I think you'll need one of the versions from  Cydia).

-This is a somewhat cumbersome way to hide videos on your iPhone, but it is also fairly discreet.


The  problem with most of the apps that protect your data is that they  include icons and other things that make them less incognito than I  would like. This method makes it so that your data will be inaccessible  unless someone ssh's into your device and starts snooping around the  file system. 

First, you need to ssh into your iPhone and create a  directory that you will use to hold your videos. Then you will need to  create the following two scripts and transfer them onto your iPhone  (make sure they are not in the directory you just created):

script1.sh
```
folder1="/var/root/hello/"
folder2="/var/mobile/Media/"
restoreifs=$IFS
IFS="
"

for filename in `ls $folder1`
do 
ln "$folder1$filename" "$folder2$filename"
done

IFS=$restoreifs
```
"/var/root/hello/" = the directory I created for my videos
"/var/mobile/Media/" = the directory my version of VLC uses for videos
This  first script reads the file name of each of my videos in  /var/root/hello/, creates a hard link for each of these videos and  places it in /var/mobile/Media/ where VLC can see it.

script2.sh
```
folder1="/var/root/hello/"
folder2="/var/mobile/Media/"
restoreifs=$IFS
IFS="
"

for filename in `ls $folder1`
do 
rm "$folder2$filename"
done

IFS=$restoreifs
```
This second script looks at each of my video files in /var/root/hello/ and removes any hard links of them in /var/mobile/Media/.

So  basically, whenever you want to watch your videos you will execute the  first script (from the ssh client on your iPhone) that will create hard  links that make them visible in VLC. When you want to make them hidden  again you will execute the second script which will remove the hard  links.

Optional: You can make the execution of the scripts even  easier by setting up a .bashrc file and adding aliases to it.  Information on that here:  [http://www.f-77.com/2011/01/07/add-bashrc-to-iphone/](http://www.f-77.com/2011/01/07/add-bashrc-to-iphone/)

I'm still  somewhat of a noob when it comes to ssh and bash scripting, so if  anybody has any comments or corrections to this guide, please reply.

---

### Post by Lucradia on 2011-02-25
> **JohnElway said:**
> -Your  iPhone must be jailbroken for this to work.

Why would anyone think of doing that besides reinstalling firmware, better apps, etc. I wouldn't, just like how I've sworn not to pirate applications, and report those who do to the companies. (Already done such with one friend and Adobe Flash CS5.)

I'm annoyed that people are shafted by jailbreaking users who think it's hilarious poking fun at do-gooders that can't get what they want (IE: Certain functions that require jailbreaking that would make your phone much, much better to use.)

---

### Post by JohnElway on 2011-02-25
> **Lucradia said:**
> Why would anyone think of doing that besides reinstalling firmware, better apps, etc. I wouldn't, just like how I've sworn not to pirate applications, and report those who do to the companies. (Already done such with one friend and Adobe Flash CS5.)

I'm annoyed that people are shafted by jailbreaking users who think it's hilarious poking fun at do-gooders that can't get what they want (IE: Certain functions that require jailbreaking that would make your phone much, much better to use.)
In what way does this have anything to do with my original post?

---

### Post by Dr. C on 2011-02-25
> **JohnElway said:**
> In what way does this have anything to do with my original post?

I was wondering the same thing myself

---

### Post by Lucradia on 2011-02-27
> **Dr. C said:**
> I was wondering the same thing myself

The requirement: "Your phone must be jailbroken."

it automatically makes my reply relevant.

---

### Post by upptown on 2011-02-27
> **Lucradia said:**
> The requirement: "Your phone must be jailbroken."

it automatically makes my reply relevant.

Don't have an iPhone so please excuse my ignorance....But, do iPhone users lease their phones or do they own the thing outright (pretty sure I know the answer).   How is j-breaking the phone "shafting" those who don't?  Does it allow people to steal apps?   Anyways, the entire argument is pretty much why I don't have a smart phone,  Only reason I use the carrier I have is cause the rest of the family is with the same provider so I don't have to hassle with the whole minutes crap.

As for pirating software/digital content....don't do it myself and when I have a friend who wants to I point them towards open source programs.  Made a lot of converts using by applying the old adage about honey and vinegar.

---

### Post by wewantutopia on 2011-02-27
@ [Lucradia]("http://ubuntuforums.org/member.php?u=1094376")

What is wrong with jailbreaking?  Don't know where you're from but in the US it is perfectly legal.

---

### Post by Spr0k3t on 2011-02-28
Just because someone is rooting their phone does not automatically make them a pirate.  It's like saying I'm a pirate because I use torrents to both download and upload files which happen to be ISOs of Linux distributions.  Those who abuse torrents to pirate software give people like me a bad name.  With that said, your repost Lucradia, is absolutely irrelavent to the thread.  There are features of rooting phones that people are normally not allowed to have access to.  Like on the Android phones, you can't take a screenshot unless you have rooted.

Reporting for piracy though, please keep it up.  Eventually this will be one area OpenSource will dominate for.

---

### Post by Lucradia on 2011-02-28
> **Spr0k3t said:**
> Just because someone is rooting their phone does not automatically make them a pirate.  It's like saying I'm a pirate because I use torrents to both download and upload files which happen to be ISOs of Linux distributions.  Those who abuse torrents to pirate software give people like me a bad name.  With that said, your repost Lucradia, is absolutely irrelavent to the thread.  There are features of rooting phones that people are normally not allowed to have access to.  Like on the Android phones, you can't take a screenshot unless you have rooted.

Reporting for piracy though, please keep it up.  Eventually this will be one area OpenSource will dominate for.

That's not the reason why I'm dissing jailbreaking. Jailbreaking for android is different than iPhone; and I really don't like iphone anyway. Since Android and iPhone both can get jailbroken, it should be considered an umbrella state of mind and/or opinion over all phones that can be jailbroken.

Jailbreaking is not a user-friendly-seeker's way of going about getting better features anyway.

---

### Post by upptown on 2011-02-28
> **Lucradia said:**
> That's not the reason why I'm dissing jailbreaking.....
Jailbreaking is not a user-friendly-seeker's way of going about getting better features anyway.


Still haven't answered two key questions:  

Why is it wrong, unethical, immoral, unwise to j-break your smart phone? 

How does j-breaking "shaft" users who haven't?:confused:

---

### Post by TheWeakSleep on 2011-02-28
I paid hundreds of dollars for my phone. If I want root access I'll take it, thank you. I'm not 'shafting' any user that CHOOSES not to and neither are any other individuals who CHOOSE to jailbreak or root THEIR devices.

As for the original post, that is a very resourceful solution :) thank you for sharing it :)

---

### Post by Muffinabus on 2011-02-28
Jeez, you definitely don't want to be that guys friend if you have a stolen and jail broken phone with a pirated copy of flash installed on it.

---

### Post by Grenage on 2011-02-28
If there was ever a troll post...

Do yourselves a favour and don't bite.

---

### Post by Sef on 2011-03-01
1) Jail breaking your iphone or other device is legal in the US.

2) If you do jail break your iphone or other device, then your warranty is voided.

---

### Post by Lucradia on 2011-03-02
> **Sef said:**
> 1) Jail breaking your iphone or other device is legal in the US.

2) If you do jail break your iphone or other device, then your warranty is voided.

It's also super annoying to even try to root / jailbreak the phone I have: [Droid X](http://www.droidxforums.com/forum/droid-x-hacks/1314-we-haz-rootz.html)

Can't even get past step one: Set up ADB, since I don't know how.

---

