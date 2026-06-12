---
title: "Rough Edges"
date: 2012-12-19
forum: The Cafe
---

### Post by mike acker on 2012-12-19
I'm finishing my 2d month as a Linux refugee from w7

there are rough edges in Linux/U that need work:

1. home networking . it should be easy to make it work; to control access without running terminal lines in essoteric command line lingo

2. wireless : wireless interface needs to better report the condition of the wireless signal. wireless isn't either 'in' or 'out' -- we are concerned with signal quality, error rate and effective throughput.

3. sound : we should be able to direct the sound output application a=by application in the sound menu . if i'm listening to music i don't want another app dropping clunkers into the music

4. program associations : search/select app should work better

before you jump on my case here stop and think: how does Linux/U present to a Windows refugee ? are we not attempting to get Linux/U up as a mainstream alternative ?

---

### Post by wewantutopia on 2012-12-19
For home networking, after I installed samba, i just edited smb.conf in a text editor.

---

### Post by 3rdalbum on 2012-12-19
> **mike acker said:**
> I'm finishing my 2d month as a Linux refugee from w7

there are rough edges in Linux/U that need work:

1. home networking . it should be easy to make it work; to control access without running terminal lines in essoteric command line lingo

Not sure exactly what you're referring to by "home networking". If you mean running a shared drive with Samba, it's a common misconception that you need to delve into the smb.conf file in order to set up Samba. There are a number of easy setup utilities available in the repositories - I like system-config-samba, but other people use shares-admin or even Webmin. Printer sharing is trivial to set up. Internet connection sharing is also very easy. Other kinds of home networking, such as setting up DNLA shares, can be more troublesome but there are fewer ordinary users who want to do that.

> 2. wireless : wireless interface needs to better report the condition of the wireless signal. wireless isn't either 'in' or 'out' -- we are concerned with signal quality, error rate and effective throughput.

Who is concerned with signal quality, error rate and effective throughput? I'm not - as long as there is a signal, I can maintain a connection and am not waiting too long for files to transfer. I'd be willing to bet that most people don't really care about those figures. That's why the Network Manager doesn't make a habit of reporting it.

If you really want to know, then you can find out with the iwlist command. Geeky enough to want to know the exact signal quality? Geeky enough to use the terminal to find it.

> 3. sound : we should be able to direct the sound output application a=by application in the sound menu . if i'm listening to music i don't want another app dropping clunkers into the music

You can direct the sound output by application, but not with the default sound menu. You need padevchooser. I'll agree with you there - but once again, not many people use per-application volume settings on Windows or Linux. They probably don't really know it exists, as it was never in Windows XP.

> 4. program associations : search/select app should work better

Maybe, although I can't say I've had to manually choose an application since about 2008. You may be going about things in the least-efficient manner.

Rather than choose a file and right-click and then scroll through a list of programs to open the file; just drag the file to the Unity Launcher and it will fade out all the icons of programs that can't handle the file. You can drag the file onto one of the programs that's still lit up, to open it.

> before you jump on my case here stop and think: how does Linux/U present to a Windows refugee ? are we not attempting to get Linux/U up as a mainstream alternative ?

If these are the issues you consider to be rough spots, then we're doing very well. I'll concede that home networking is an unpolished spot, although not as rough as generally thought. The other things you mention are really quite nitpicky; I don't mind this as we really should be aiming for the highest quality throughout, but if these are the biggest issues facing you in your second month of Ubuntu then it seems that Ubuntu is very welcoming to Windows converts.

---

### Post by mbuell on 2012-12-20
> **3rdalbum said:**
> . . .If these are the issues you consider to be rough spots, then we're doing very well. I'll concede that home networking is an unpolished spot, although not as rough as generally thought. The other things you mention are really quite nitpicky; I don't mind this as we really should be aiming for the highest quality throughout, but if these are the biggest issues facing you in your second month of Ubuntu then it seems that Ubuntu is very welcoming to Windows converts.

Well, from my viewpoint, the comment above is a prime example of the community that keeps linux at less than 3% of the OS market. I'm more in tune with the OP on this. I don't think the OP is being "nitpicky" - but rather is expressing genuine needs. They will certainly smooth out as the OP gets up the learning curve - but the whole stated goal of Ubuntu back at the beginning was to find a way to get users past that learning curve painlessly, right? Somewhere along the way we have gotten lost in the linux userland weeds. 

Listen, we don't need more geekiness. We don't need to train other people to BE geeks to operate their desktop. Sorry.

To the OP, 3rdalbum is obviously knowledgable. What he said about sound apps is beyond me, and probably right. Home networking I can attest to. Samba works great, has a fairly small learning curve, and works "out of the box" with gui apps. There are a couple of the gui apps - one may work for you if the other doesn't. With samba you can "see" other computers in your file manager, and access their drives. All part of the functionality. If your local machines are all linux, as an alternative, you can use ssh, and sshfs, which gives you a more secure connection, and real functionality on your remote machine from your active keyboard. [Using ssh you can login to a remote computer and work on it! Pretty nifty, if you ask me, but it does take a little learning.]

Wireless - if you don't like the default Network Manager - and many people do not - try wicd. Network Manager has been known to be buggy, and I have witnessed that myself. It can also work magnificently well - but some times! You may eventually uninstall network manager to keep it from interfering. Both are gui - no need for the command line. (thank heaven!)

The program associations you mention, I'm not sure what you are talking about. Perhaps you are using Unity, and are disgusted with it's methods - needing to type in a program name to find it? I found Unity to be very good in some aspects, but ultimately I found it was much less useable than the more conservative menu-based desktops. If this is what you are talking about, check out xfce (xubuntu, or mint), or the Mint version of gnome2 (Mint MATE). Xfce has an interface that is perhaps the MOST immediately understandable for someone switching from Windows XP and 7, imho. It uses menus, and common menu submenu concepts and words. No new "paradigms". The Mint version of gnome 2 maintains the traditional gnome menu subdivisions - so is more familiar because of that. 

While these options all require a choice - and this means that a REAL newb will have difficulty - it isn't that big a jump in reality. If you find that the choices require too much learning for the time that you have to spend on it, check out a Mint MATE desktop liveCD, or an xubuntu live cd. Go with one of those. I prefer to keep Nautilus as my file manager (Thunar, the xfce default file manager, is almost, but not quite, as flexible and useful, but will still do the networking stuff you rate important). Imo, skip the lxde desktop, it is for confirmed geeks.

Btw - I am extremely ticked off, myself, about those rough edges. Here we are - several years after the launch of ubuntu - and we still have the  rough edges. If anything, recent releases have renewed the rough edges. This is disappointing to me, at the least. I am wondering if linux will always be just the "tinkering test bed" - the place where the tinkers, engineer geeks, and fanatic users test their concepts - so that Windows can watch them, and incorporate the functionality that works, and maintain their monopoly.

---

### Post by 3rdalbum on 2012-12-21
Nitpicky isn't bad. I said that I think we should be aiming for the highest quality and polish throughout.

Saying that 'Normal people wont convert to Linux until they can easily see the signal-to-noise ratio and latency of their wifi without the Terminal" is a bit of an exaggeration.

It is almost seven years exactly since I started using Ubuntu and things have come along drastically. 7 years ago we didn't have up-to-date Flash. Using one sound application would stop all other sound apps from working, sometimes until reboot. Video editing and video DVD burning were barely possible. Installing a Debian package required the terminal. Wifi required the terminal too.

In those days, Ubuntu was much more difficult to use. These were insurmountable problems for many that forced people back to Windows. But many more people managed with what they had. Nowadays, a quibble like "there is no preinstalled way of controlling the volume control of a single program" is so minor compared to "I can't run more that one sound-producing program at a time". It wont force anyone to leave Ubuntu when it is easily fixed.

---

### Post by mbuell on 2012-12-21
> **3rdalbum said:**
> Nitpicky isn't bad. I said that I think we should be aiming for the highest quality and polish throughout.

Saying that 'Normal people wont convert to Linux until they can easily see the signal-to-noise ratio and latency of their wifi without the Terminal" is a bit of an exaggeration.

It is almost seven years exactly since I started using Ubuntu and things have come along drastically. 7 years ago we didn't have up-to-date Flash. Using one sound application would stop all other sound apps from working, sometimes until reboot. Video editing and video DVD burning were barely possible. Installing a Debian package required the terminal. Wifi required the terminal too.

In those days, Ubuntu was much more difficult to use. These were insurmountable problems for many that forced people back to Windows. But many more people managed with what they had. Nowadays, a quibble like "there is no preinstalled way of controlling the volume control of a single program" is so minor compared to "I can't run more that one sound-producing program at a time". It wont force anyone to leave Ubuntu when it is easily fixed.

Ok, granted - the examples you point out are a little dramatic. Now set that aside for a second, because I have a question. 7 years, huh? So that was about from version 1.0, right? Ok, bump forward a couple years, in your memory, to version 4 or 5, and start your "rough edges" comparison from there. Do you still come up with the same answer? 

Now, back to the dramatic comments: perhaps I am underestimating the drama of each. I tend to listen, when a complaint or a comment of this type is put forth, not so much exactly to what is said, but to what the person is trying to express. In other words - what is that person seeing and experiencing that is causing them to make the comment. It usually isn't exactly what they are saying. This is rule one of "how to listen", whether you are working help desk, or mediating, or otherwise engaged in trying to help another person solve a problem. It's why asking for a "cat blabla | grep yakkety" cli request in response to a problem is frequently a GOOD answer. It helps the responder get to the root of the problem. In this case, we have a more generic complaint, not a specific problem. 

And, in this case, I tend to agree, and imho, ubuntu has lost the drive to make the interface as professional as possible. We are like the house painters who have done the wall, and not the trim, but are now rushing off to paint the next set of walls, because walls are exciting to us, and the trim we don't even see. I also tend to agree, in a fashion, with the OP's statement about the wifi. When I want to figure out what is going on after installing the latest version or getting a new box up to speed, I look for some sort of icon for the wifi to help me figure out a) if it is working, b) what networks are available, and c) how strong the signal is so I can connect. And you know what? It seems like about 50% of the time I'm missing the icon. Or the icon tells me nothing about why there is a problem. That's a rough spot. And that WILL turn new users away. Nor is it necessarily trivial to solve. I had a box a few months ago where Network Manager was inserting garbage into the essid for new wifi connections. The only way we figured it out was by a group of us at a linux meetup going over the situation. Ended up uninstalling network manager entirely to prevent it from messing things up. But, granted, it is not our biggest problem today. 

Still - I thought the whole point of Ubuntu was to offer a professional and polished desktop that would give us a reliable cd install that we could hand off to grandma, and not worry that she needed hand-holding to get it going. For a while, I thought we were doing a bang-up job at that. Enough so that I gave my sister a laptop so she could use email and Facebook to keep up with the family. She's at about the toaster level of geekiness. And will probably never be much higher than that. But I had to install the Ubuntu, just to make sure I worked through all those problems like we are talking about here. 

Anyway, thanks for the conv. And OP, I hope you have a little more insight now than before. Your comments have been aired. We have yet to see if they will be taken into consideration, but I think they will. 

BY THE WAY! You MIGHT want to use that cute little donation page that Ubuntu has started to VOTE on what you think Ubuntu should be working on!
 [http://www.ubuntu.com/download/desktop/questions]("http://www.ubuntu.com/download/desktop/questions") 
This, in my mind, is an EXCELLENT way to move forward. Ubuntu and linux have to have ways to make money so they can spend money to work! This way, I can give quickly and EASILY (!!!), a modest sum that I can afford at the moment, and get a VOTE on the direction I think Ubuntu should be working on! Nifty!

Speaking of drama, now I need to get back to work! If you'll excuse me, exit, stage left.

---

### Post by rrnbtter on 2012-12-21
Greetings, 
Regarding Post #3 by 3rdalbum.
 +1 on everything.
In my mind increasing Desktop share doesn't mean being like Windows.  Ubuntu is a great alternative that people will use if they like it.  The biggest room in the world is room for improvement and Ubuntu has come a long way since I started with Karmic a couple of years ago. I have been more amazed than disappointed. 
This being said, if you have a problem then ask for an answer. If you need to use a terminal however, well, thats just Linux.
[]("http://ubuntuforums.org/member.php?u=61044")

---

### Post by mike acker on 2012-12-21
thanks guys for the positive responses . i thought i'd just get jumped on and so I demurred and re-started on this post several times

It's the polish that counts

I started in IT back in 1967 on the IBM 1620 . and over the years i've dealt with a lot of software

the difference between keepers and throw-backs is the polish . professional software is feature rich and polished: the features all work

I have to give Linux 5 gold stars . It just runs good .


[LIST]
[*]my daughter and I had to use a thumb drive to share files during her math class because I still don't have home networking going . She should be able to log onto my Nix box and have immediate access to her areas there and also to the 'everyone' area I set up on drive 2 .
[*]my 802.11n reported 72Mb/sec . when I ran a speed test on it actual troughput was about 5Mb/sec -- where the Charter Cable provides us 30 to 40 Mb/sec . after chit-chatting on the wireless forum for several days and even installing another wireless card I discovered it was an antenna problem . problem: the wireless dialog does not provide connection information regarding signal quality . in|out might be OK on a cable connection but not on wireless . remember I also spent 30 years in the MIARNG Signal Corps -- working with wireless comm links .
[*]I had to hunt around on the net and then install some css decrypters before i could play a DVD . but the instruct i used was on an official (looking) Ubuntu dox page
[*]anyone who connects an AMP to their 'puter will want to control sound . i don't have speakers in my ASUS PA248 monitor so now i have to route everything thru the amp .  I want to get some small speakers for when i listen to a flash ( shudder ) video   which i would connect to the on-board audio on my M5A88 (mother board)  . i don't really like playing a flash video thru the main amp . that is for when I watch a Woodstock DVD -- and I want to pretend I'm listening to Bill Henley's sound system tee hee
[/LIST]
i think the future is very bright for Linux, particularly in controlling un-authorized programming -- which is the key to the hacking problem -- as well as the data-minining and privacy issues 



I use only Linux programs from the official library and so far have found an adequate substitute for the stuff i used in win7 .

---

### Post by lz1dsb on 2012-12-21
All of your points are valid. I'm just puzzled by the 802.11n issue. Throughput in wireless is a picky issue anyway. In general the fact it shows it's connected at 72Mbps doesn't even mean that you'll ever gonna get anything close to it. The best throughput you could get is about 50% less. And it's not a Linux thing... It's just how WiFi works. But 5Mpbs throughput... well that's quite low in this case anyway. But again it could be anything, driver, antenna, the AP itself... too many variables :p
My personal opinion... I've started using Linux about two years ago with Karmic. I could say that definitely the Linux desktop is going into the right direction as far as functionality and useabillity are concerned. But still the hardware compatibility issues with Linux are quite frustrating, and I guess this will not ever change until Linux becomes one of the major Desktop OS, which unfortunately isn't the case yet...

---

### Post by mike acker on 2012-12-21
> **lz1dsb said:**
> All of your points are valid. I'm just puzzled by the 802.11n issue. Throughput in wireless is a picky issue anyway. In general the fact it shows it's connected at 72Mbps doesn't even mean that you'll ever gonna get anything close to it. The best throughput you could get is about 50% less. And it's not a Linux thing... It's just how WiFi works. But 5Mpbs throughput... well that's quite low in this case anyway. But again it could be anything, driver, antenna, the AP itself... too many variables :p
My personal opinion... I've started using Linux about two years ago with Karmic. I could say that definitely the Linux desktop is going into the right direction as far as functionality and useabillity are concerned. But still the hardware compatibility issues with Linux are quite frustrating, and I guess this will not ever change until Linux becomes one of the major Desktop OS, which unfortunately isn't the case yet...
  it was the antenna type|location

the ASUS  PCE-N10 came with a little rabbit ear . i changed that for a 'witch's hat' antenna from another card and located it behind me . the rabbit ear was behind the computer case which probably obstructed the RF . as soon as i changed the antenna i had net tests between 30Mb/sec and 42Mb/sec

this is another classic case of a bad diagnostic putting me on the wrong track . i should have learned that lesson by now but i still get bit by it every once in a while . the system settings / network should have reported poor wireless signal .

I have to play with WireShark yet . one of the things that is critical to privacy -- which is a feature of Linux -- is in controlling what apps are allowed access to the network . this should start with Linux install and update .  after that user should need to grant access to each app .  data mining is facilitated by systems that allow every app to have unrestricted access to the net . not cool .

---

### Post by lz1dsb on 2012-12-22
> **mike acker said:**
> it was the antenna type|location

the ASUS  PCE-N10 came with a little rabbit ear . i changed that for a 'witch's hat' antenna from another card and located it behind me . the rabbit ear was behind the computer case which probably obstructed the RF . as soon as i changed the antenna i had net tests between 30Mb/sec and 42Mb/sec

this is another classic case of a bad diagnostic putting me on the wrong track . i should have learned that lesson by now but i still get bit by it every once in a while . the system settings / network should have reported poor wireless signal .

I have to play with WireShark yet . one of the things that is critical to privacy -- which is a feature of Linux -- is in controlling what apps are allowed access to the network . this should start with Linux install and update .  after that user should need to grant access to each app .  data mining is facilitated by systems that allow every app to have unrestricted access to the net . not cool .
I guess that's the idea of RSSI... It is strange though, that the Network Manager Applet doesn't provide any info about it, or in a way... it does, but giving this fuzzy icon...
I see your point. Well i guess the rationale here is that the standard user wouldn't ever need this...

---

### Post by oldos2er on 2012-12-22
> **mike acker said:**
> 4. program associations : search/select app should work better


Regarding the above, if you haven't tried KDE you might want to test it to see if it fits your needs.

---

### Post by mike acker on 2012-12-23
> **oldos2er said:**
> Regarding the above, if you haven't tried KDE you might want to test it to see if it fits your needs.

thanks all for the good notes

i'm a bit reluctant to switch distros as i've invested a lot in learning ubuntu, more particularly in selecting new software for my major activities:

[LIST]
[*]office
[*]photography
[*]music
[/LIST]
~~
it's easy to shake off a sign here and say 'most users don't need it' . but remember: when things don't work you are right of the edge of getting scrapped


historically Linux has been for geeks, and geeks don't mind fussing, digging up secrets


but ordinary users need things to work 'out of the box'


e.g. VLC media player


I wanted to play my Woodstock Video but I had to dig up the [ instructions for CSS ]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") to make it work


a little context sensitive assist would have been a good thing ...


same thing on the 802.11n antenna problem

we need a better camera import program: right now the best way I've found is to take the chip out of the camera and use that little adapter to access it as a USB device using Krusader. The reason: if you have 900 px in your camera you only want to import the last shoot. you don't want to wait while the software pulls thumbnails for every px in the camera . Canon DPP is beautiful. Gwenview comes close, lacking only a point or two -- while being up a point or two here and there as well  ( I like the upload to flickr feature in Gwenview; miss the focus point display option and download features of DPP ) . still Gwenview is plenty good that it's not worth thinking about wine.


I think the next year in particular offers a great opportunity for growth for Linux/Ubuntu . particularly if a couple of these pretty minor things could be addressed . initially maybe a little context sensitive help

---

### Post by blackbird34 on 2012-12-23
> **mike acker said:**
> I'm finishing my 2d month as a Linux refugee from w7

there are rough edges in Linux/U that need work:

1. home networking . it should be easy to make it work; to control access without running terminal lines in essoteric command line lingo

2. wireless : wireless interface needs to better report the condition of the wireless signal. wireless isn't either 'in' or 'out' -- we are concerned with signal quality, error rate and effective throughput. 

[Cinnamon]("http://www.webupd8.org/2012/02/alternative-cinnamon-ppa-for-ubuntu.html")'s Wifi applet gives you an idea of the signal quality, with a percentage (85% = good, 100 = very good obviously, my wifi tends to fail to connect properly below around 50%)

> 3. sound : we should be able to direct the sound output application a=by application in the sound menu . if i'm listening to music i don't want another app dropping clunkers into the musicDon't know about any of the rest of you but in both Cinnamon and Unity I can go to System Settings > Sound > Applications tab and configure the sound output allowed for any running program that can access the sound server (if it doesn't show up, launch the program and it should, your settings will be saved).

> 4. program associations : search/select app should work better

before you jump on my case here stop and think: how does Linux/U present to a Windows refugee ? are we not attempting to get Linux/U up as a mainstream alternative ?Not sure what this is...

And about what you were saying about CSS: when you install Ubuntu it offers you a tick box to download and install all the restricted= proprietary codecs for media and DVD playback (including libdvdcss). Maybe you didn't see it at the time...

---

