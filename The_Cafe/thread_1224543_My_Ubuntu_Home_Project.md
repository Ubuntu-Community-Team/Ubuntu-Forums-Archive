---
title: "My Ubuntu Home Project"
date: 2009-07-27
forum: The Cafe
---

### Post by Maheriano on 2009-07-27
I was going to wait until I had everything done to spring it but I figured people might like a build thread. Plus I'm kind of excited about it myself!

[SIZE="5"]**_X10_**[/SIZE]
- swap all light switches/outlets in my house to X10 modules [COLOR="Red"][75%][/COLOR]
- hook up CM11A unit to transmit commands through house wiring [COLOR="Lime"][DONE][/COLOR]
- use CM17A to transmit wireless signals on separate circuits [COLOR="Lime"][DONE][/COLOR]
- buy projector screen, automate down/up motions
- mount projector to ceiling in line with screen [COLOR="Lime"][DONE][/COLOR]
- desktop computer will be running Ubuntu 10.04 desktop edition on wireless internet [COLOR="Lime"][DONE][/COLOR]
- laptop to run Ubuntu 10.04 Desktop edition with NXClient and SSH access to desktop mentioned above. [COLOR="Lime"][DONE][/COLOR]
- install Heyu to access X10 devices and control appliances/lights from anywhere in the house [COLOR="Lime"][DONE][/COLOR]
- Install MisterHouse to control X10 modules via voice recognition [COLOR="Blue"][NEW][/COLOR]
- Install Heyu web GUI to control X10 units remotely via the web [COLOR="Blue"][NEW][/COLOR]

[SIZE="5"]**_MEDIA - BASEMENT_**[/SIZE]
- same desktop used for X10 to be hooked to projector via DVI cable providing up to 1080i resolution. [COLOR="Lime"][DONE][/COLOR]
- motorized projector screen run by X10
- projector mounted to ceiling with custom mount [COLOR="Lime"][DONE][/COLOR]
- speaker wire run under floor or behind baseboards [COLOR="Lime"][DONE][/COLOR]
- 6.1 surround sound connected to SPEAKER A on receiver [COLOR="red"][BROKEN][/COLOR] (Upgrading to 9.1 killed my AC3 somehow.
- B SPEAKER on receiver connected to wall jack which feeds to living room speakers upstairs [COLOR="Lime"][DONE][/COLOR]
- BluRay ROM to play DVD
- Moovida used for media centre [COLOR="Blue"][CHANGED][/COLOR]
- 64 bit Boxee beta to replace Moovida [COLOR="Lime"][DONE][/COLOR]
- 8 inch touchscreen on the wall connected to secondary monitor port of computer. Will be used to browse media and play movies/music on projector. (Looking at using a pad for this now, like an iPad, Crunchpad or HP Slate)
- iPod Touch to remotely control everything via SSH [COLOR="Blue"][CHANGED][/COLOR]
- Install Gmote on my new Google Android phone to control everything via SSH [COLOR="Lime"][DONE][/COLOR]
- Write an Android application to control all the units via a GUI over Wi-Fi, HSPA or bluetooth, sell it and get filthy rich [COLOR="Red"][0%][/COLOR]

[SIZE="5"]**_MEDIA - LIVING ROOM_**[/SIZE]
- Media PC running Ubuntu 9.04 Desktop edition and Moovida [COLOR="lime"][DONE][/COLOR]
- My roommate wanted cable and I don't want to pay for it. So I set up Vuze to monitor RSS feeds for weekly television shows. Once a show is aired and added to the RSS feed as available, it downloads it from the torrent link in the RSS feed and placs it into its related folder on the computer. Moovida automatically scans these folders for new content and adds them to the shows lists. You don't have to do anything but click your show and watch. [COLOR="lime"][DONE][/COLOR]
- PC will be headless except for the television but will never need the desktop to be used, only Moovida.
- Wiimote as mouse to eliminate need for mouse/keyboard [COLOR="lime"][DONE][/COLOR]
- This was completely scrapped since my roommate took her television out of the living room. I no longer have anything to watch media on in my living room.

[SIZE="5"]**_CAR_**[/SIZE]
- pull out OEM stereo and replace with computer in the trunk and touchscreen in the dash [COLOR="lime"][DONE][/COLOR]
- USB GPS receiver to give turn by turn directions [COLOR="lime"][DONE][/COLOR]
- will run Ubuntu 10.04 Desktop edition and nGhost2 as a media front end [COLOR="Red"][0%][/COLOR]
- webcam constantly recording out front windshield and saving to 30 minute files [COLOR="Blue"][CHANGED][/COLOR]
- changed webcam application to RRCam which is more stable and works with more cameras.

[SIZE="5"]**_SECURITY_**[/SIZE]
- scheduled lighting and event triggers run by X10 to email me when windows/doors are opened or motion is detected
- multiple wireless IP pan/tilt cameras inside/outside home
- Ubuntu 10.04 Server edition and Zoneminder [COLOR="Red"][0%][/COLOR]

That's all I can think of for now, I'll add more as I remember some of the ideas I had planned. And once my camcorder comes in the mail, I'll make some videos of the stuff in action. What do you think? Any suggestions?

---

### Post by The Toxic Mite on 2009-07-28
That seems VERY ambitious! And I like people with it's-impossible-but-it's-possible ambitions.

Good luck! :D

---

### Post by Barrucadu on 2009-07-28
Nice :)

When I get a house in the future I plan to have DMX-controlled lighting throughout and have a lighting server connected to some dimmers. Nothing like being able to adjust the colour of the light in a room to suit your mood.
I also want ceiling speakers in every room. Each room should be able to suit the desire of the person/people currently occupying it.

I've got a big list somewhere :p

---

### Post by philcamlin on 2009-07-28
man that would be one intense house :P

i like it:popcorn:

---

### Post by Bachstelze on 2009-07-28
You should talk to the person who made [that thread]("http://ubuntuforums.org/showthread.php?t=1224388"). ;)

---

### Post by The Toxic Mite on 2009-07-28
When I move into my own house, I plan to have a media server with Mythbuntu installed on it, then hook up a PC to my living room telly and connect it to the server. That would also have Mythbuntu installed on it.

I also plan to have a web server.

---

### Post by Maheriano on 2009-07-28
> **Barrucadu said:**
> I also want ceiling speakers in every room.

We live in a townhouse complex and the house joined to us on one side has speakers in every room with control switches on the walls for them. I am extremely jealous, ours for some reason doesn't have them. I guess the builder decides which houses get certain packages or the people that bought the house before it was built decided they didn't want to pay extra for it. Who knows but I'm a little upset ours don't have it. However I can take solace in the fact that ours has hardwood floors up and down as well as oak cabinets and ceramic tiling!

I got a lot of this puzzle done do I'll create an update post when I'm not at work with all the things I have done so far and the functionality I currently have achieved.

As a quick list, I got my car computer installed and working, just pulled it back out to upgrade some components. X10 is working, just got to figure out a solution to the dimmer switch controlling the ceiling fan, it's causing the motor to hum with the strain. I've got Ubuntu installed on the media server and Vuze is configured to auto download my roommate's favourite shows....Ugly Betty, Bachelorette and other gayness. I just have to check it when I get home to see if it actually downloaded the finale of Bachelorette last night to see if it actually works.

Updates to follow!

---

### Post by Maheriano on 2009-07-29
So here's what I have done so far:

X10
I've hooked up the CM11A and CM17A (controllers) to the computer and to the house wiring. I replaced a light switch in the basement and 1 in my bedroom. I also installed Heyu on my desktop machine which both controllers are attached to via serial ports. I got the PCI serial card for free off a guy who told me, "It's cheaper for us to give this older stuff away instead of wasting our accountants' time trying to write down all the serial numbers and sell it." This desktop is my main machine with a terabyte drive and all the originals of my digital documents. When I refer to my computer, I'm usually talking about this one. It's plugged in in my basement.
I've got the projector plugged into it via DVI and a GeForce 8400 GS video card with hardware decoding so it should handle the maximum 1080i resolution of the projector fine. The desktop is running Ubuntu 9.04 and I also installed SSH and NXClient. I've got NXClient installed on my Dell Studio 15 laptop as well and can access the desktop from anywhere in the house through a session with this application or with SSH for command line stuff like Heyu.
Heyu is a command line application built for Linux which controls X10 controllers. The CM11A controller is wired and plugs into the wall. It will attach commands to the zero bit in your regular 120 volt house wiring which will be picked up by various outlets light switches around the house to turn on/off. This currently works fine for the light switch I replaced int he basement but will not work for the lights on the top floor which seem to be on a separate circuit. I got around this by using the CM17A controller which is wireless. It sends the signal out wirelessy (RF) and it's picked up by a X10 transceiver unit that I plugged in upstairs. This unit then rebroadcasts the signal through the 120 AC wiring to the bedroom switch on that circuit. The switch I used is a dimmer though and I need to swap it for a simple on/off because the dimmer wreaks havoc on the ceiling fan motor and causes it to hum. It keeps me from sleeping at night plus it sounds like it could cause a fire.

CM11A:

[IMG]http://cache1.smarthome.com/images/1140.jpg[/IMG]

CM17A (Firecracker):

[IMG]http://www.arduino.cc/playground/uploads/X10/CM17A.png[/IMG]

I've also been having trouble in my garage, the switch for the lights is at the front but I only have 1 garage door opener and it's in my car. Plus my roommate's bedroom is right above the garage and don't want to wake her every time I open/close the garage. So I enter the garage at the back via the door and have to feel my way around after shutting the door behind me to get into my car. I've fixed this by changing the lightswitch in the garage with an X10 switch and I use a credit card remote to turn the light on/off at will. I'm thinking of going motion detection with this one though.

Credit card remote:

[IMG]http://improvingtomorrow.com/catalog/images/remote_cc.jpg[/IMG]

My plans for the coming weeks are to swap all the light switches in the house and some of the outlets. And to investigate the switch for the central air and see if the X10 switches will handle the current for that. Be nice to turn the air on/off from anywhere in the house. Or out of the house!

---

### Post by DeadSuperHero on 2009-07-29
Definitely some great ideas. I find the modern home to be lacking most of the time, a complete lack of gadgetry.

I'd hate to prove all those old Popular Mechanics Magazine articles about what the future would be like wrong. If I had the funds, I'd probably do this too.

---

### Post by Maheriano on 2009-07-29
MEDIA - LIVING ROOM

My work was dumping a bunch of old stuff to recycling and let me dig through it before it left. I yanked one of those small Dell office machines and decided to use it as a media server, works perfect. I installed Ubuntu 9.04 on it as well as Moovida and Vuze. Then I installed a Vuze plugin called RSS Feeder to monitor RSS feeds of newly televised shows I have set up on a list. When one of those shows is added to the feed, Vuze accesses a link in the feed to download the torrent and automatically add it to the list of shows in the media player. This way I don't need to do anything except sit back and watch my shows once they're downloaded.

---

### Post by Maheriano on 2009-07-31
A little update for my few followers. I picked up a wireless PCI card for this machine last night, got it off a guy for $10. I brought it home and plugged it into my little Dell box......hmmmmmm.........the metal plate at the end is way too tall to fit in the machine. So I bent it back and forth a bunch of times until it snapped off and put it into the machine, closing the case.

I assumed I would have to download some proprietary drivers and do some fandangling to get this card to work right but all I did was literally boot the machine, click the wireless icon, click connect and I was online! Wow, this is why I love Ubuntu, I didn't have to do anything. So now I'm online and I downloaded Vuze, just have to install the RSS Feeder plugin, set up the shows I want to watch (last time I set it up was on my laptop to test it) and I'm in business. I should have this thing running media to the television by the end of the long weekend......yes, we have Monday off here.....suckers!

---

### Post by shingalated on 2009-07-31
> **Maheriano said:**
> MEDIA - LIVING ROOM

My work was dumping a bunch of old stuff to recycling and let me dig through it before it left. I yanked one of those small Dell office machines and decided to use it as a media server, works perfect. I installed Ubuntu 9.04 on it as well as Moovida and Vuze. Then I installed a Vuze plugin called RSS Feeder to monitor RSS feeds of newly televised shows I have set up on a list. When one of those shows is added to the feed, Vuze accesses a link in the feed to download the torrent and automatically add it to the list of shows in the media player. This way I don't need to do anything except sit back and watch my shows once they're downloaded.


I've been using Boxee as my media center application.  It is finally stable enough that I don't need to leave a mouse and keyboard plugged in at all times to restart it when it crashes.

---

### Post by Maheriano on 2009-07-31
Thanks, I just checked out the Boxee website and it seems it's only for 32 bit machines so I can't give it a test drive on my laptop. The media machine I built is 32 bit though so I'll put it on that when I get back at it. I'm done for the night, I just configured the entire thing to realize I created the partition too small for the / partition and ran out of space. Since it's only a 13 gig drive I decided I should swap that out for a 60 gig I have here so I just installed 9.04 on that one and configured that while putting together some furniture for the room. So now I have reinstalled Ubuntu, redownloaded all the applications, reconfigured Vuze to auto download via RSS torrents and still have to install the custom applications like Moovida and Boxee. I also have to set up the Wiimote as a mouse.

---

### Post by Maheriano on 2009-08-03
It was a holiday here today so I started swapping out more switches.
I was having issues in the morning getting into my car in the garage because it's an attached garage but there's no entry from inside, only outside. There's the garage door on the front and a normal door on the back. I always go in through the back door but the lightswitch is at the front, too far for me to reach. So I swapped all the switches in the garage out for X10 switches and plugged in a transceiver so I'd be able to use the little credit card remote to control the lights. It works perfect! I hang the remote by the door, turn on the lights when I get inside and turn them off again as I'm driving away from the garage.

I also swapped out the switches for the lights on the front and back porches, I'm hoping to get to all the other lights within the next 30 days.

---

### Post by Maheriano on 2009-08-05
Monday was a holiday here so I spent the long weekend doing some more work on my house.

So far for X10 modules I have installed:
- master bedroom (light)
- master bedroom (lamp)
- master bathroom (light)
- basement (light)
- front porch (light)
- back porch (light)
- garage (light)

They all work like butter, it's great. I even got transceivers plugged in in the garage and master bedroom so they can both be controlled via remote control. I had to remove the switch from the guest bedroom though since there's a fan in there and these switches can't hold the current required by the motor in the fan. I had to swap back a regular switch which isn't so bad.

I also finished up the install on the media box for the living room. I installed Vuze, got that working correctly with the RSS feed monitor and set up my Wiimote as a bluetooth mouse so now when I point my Wiimote at the screen, the mouse pointer moves around with it. I had an issue with batteries dying in the Wiimote so I decided to use the power button on the Wiimote to turn it off when not in use. This created a problem that you needed to run a connection command to get it connected to bluetooth every time. I got around that by installing an application called BlueProximity which constantly monitors bluetooth devices and when it detects one that you have set up, it runs a corresponding command. So as soon as I turn my Wiimote on, it runs the command to connect it and I'm in business.

My problem came when I tried to hook the computer to the television. The only video output on the computer is VGA and the inputs on the LCD television are HDMI, component, S-video and composite. I have a VGA-component cable but that didn't seem to work, does anyone know how to hook the 2 together?

---

### Post by gletob on 2009-08-05
> **Maheriano said:**
> 
My problem came when I tried to hook the computer to the television. The only video output on the computer is VGA and the inputs on the LCD television are HDMI, component, S-video and composite. I have a VGA-component cable but that didn't seem to work, does anyone know how to hook the 2 together?

You could buy a VGA to HDMI or VGA to component converter, but it would be cheaper to buy a well supported card that outputs in HDMI.  What type of card interfaces does the PC in question have? E.G. Pci, AGP, Pci Express

---

### Post by Maheriano on 2009-08-05
The computer is one of those small Dell office machines and has PCI and AGP. I guess I'll have to get an AGP donation from someone, shouldn't be more than $5 - $10 for a generic card.

I still don't know why the VGA-component cable doesn't work though.

---

### Post by gletob on 2009-08-05
> **Maheriano said:**
> The computer is one of those small Dell office machines and has PCI and AGP. I guess I'll have to get an AGP donation from someone, shouldn't be more than $5 - $10 for a generic card.

I still don't know why the VGA-component cable doesn't work though.

I know it sounds goofy but VGA to Component cables aren't meant for computers

---

### Post by Maheriano on 2009-08-06
Got a lead on a low profile AGP card with television out which should work for now. 480i should be plenty for a 36 inch LCD to watch shows on. It's likely stored to file in 640x480 anyway.

I also went to Rona last night and picked up batteries for the credit card X10 remote, my master bedroom is now finito for X10. Unfortunately it's not my room, it's my roommate's but I get the entire basement in lieu....yay! I also got a pile of switch plates because my house looks like the ghetto with no switch plates after swapping in all the X10 switches and taking out the sissy old time flip switches. I'm getting there....slowly.

I also sold my power supply (M1-ATX) and motherboard (Via Epia M10000) from the car and upgraded to a nice Mini-ITX Intel board and a M2-ATX power supply. I have the board and ordered the power supply 2 days ago. I'm expecting it to be here in a week or so and then I can put this computer back into my car. My plan is to hook one of the auxiliary outputs from my Compustar alarm to the motherboard, allowing me to turn on the computer with my keyfob from the house. I can then pick up the shared folder from the hard drive once it boots and copy songs to it from the comfort of my own home without leaving my computer chair. And since I have a 2 way pager remote, I get feedback from the car once it is turned on. That way I don't sit there pressing the button over and over wondering if it's on or not.

---

### Post by sydbat on 2009-08-06
> **Maheriano said:**
> Got a lead on a low profile AGP card with television out which should work for now. 480i should be plenty for a 36 inch LCD to watch shows on. It's likely stored to file in 640x480 anyway.

I also went to Rona last night and picked up batteries for the credit card X10 remote, my master bedroom is now finito for X10. Unfortunately it's not my room, it's my roommate's but I get the entire basement in lieu....yay! I also got a pile of switch plates because my house looks like the ghetto with no switch plates after swapping in all the X10 switches and taking out the sissy old time flip switches. I'm getting there....slowly.

I also sold my power supply (M1-ATX) and motherboard (Via Epia M10000) from the car and upgraded to a nice Mini-ITX Intel board and a M2-ATX power supply. I have the board and ordered the power supply 2 days ago. I'm expecting it to be here in a week or so and then I can put this computer back into my car. My plan is to hook one of the auxiliary outputs from my Compustar alarm to the motherboard, allowing me to turn on the computer with my keyfob from the house. I can then pick up the shared folder from the hard drive once it boots and copy songs to it from the comfort of my own home without leaving my computer chair. And since I have a 2 way pager remote, I get feedback from the car once it is turned on. That way I don't sit there pressing the button over and over wondering if it's on or not.Check Memory Express. They still sell a few AGP cards for a reasonable price.

Also, because we live in the same city, can you come over and set up my place too?? I can pay you in Alexander Kieth's...:P

---

### Post by Maheriano on 2009-08-06
> **sydbat said:**
> Check Memory Express. They still sell a few AGP cards for a reasonable price.

Also, because we live in the same city, can you come over and set up my place too?? I can pay you in Alexander Kieth's...:P

Kieth's! I lived in Nova Scotia for 5 years so I got a soft spot for the stuff, I have a case of Kieth's White in my fridge right now!

Memory Express probably wouldn't have anything in my price range of $5-$10 but I'll take a look. But for that price I'm afraid I can only swap out 1 light switch, sorry. :( Maybe I can offer my services on layaway?

---

### Post by sydbat on 2009-08-06
> **Maheriano said:**
> Kieth's! I lived in Nova Scotia for 5 years so I got a soft spot for the stuff, I have a case of Kieth's White in my fridge right now!

Memory Express probably wouldn't have anything in my price range of $5-$10 but I'll take a look. But for that price I'm afraid I can only swap out 1 light switch, sorry. :( Maybe I can offer my services on layaway?Let's see...you already have the Kieth's AND you are willing to work on the project at my house...win-win (for me...hehehe)...

I don't think Memory Express has anything less than $50. I, however, have found a 32MB AGP Rage Pro in my closet (and a 32MB PCI 3dfx card!!)! You can have it (them) if you like.

---

### Post by Maheriano on 2009-08-06
Sweet! Local pickup is win, are either of them low profile? Television out?

---

### Post by sydbat on 2009-08-06
> **Maheriano said:**
> Sweet! Local pickup is win, are either of them low profile? Television out?Nope. Sorry. But there are adaptors, aren't there??

[http://www.amazon.com/CablesToBuy-Perform-Converter-S-Video-Adapter/dp/B0010WGZQK](http://www.amazon.com/CablesToBuy-Perform-Converter-S-Video-Adapter/dp/B0010WGZQK)

[http://cgi.ebay.ca/VGA-to-S-Video-RCA-TV-Adapter-Converter-cable_W0QQitemZ200367934327QQcmdZViewItemQQimsxZ20090729?IMSfp=TL090729143001r4164](http://cgi.ebay.ca/VGA-to-S-Video-RCA-TV-Adapter-Converter-cable_W0QQitemZ200367934327QQcmdZViewItemQQimsxZ20090729?IMSfp=TL090729143001r4164)

Also, I think London Drugs or The Source (shudder) or Memory Express or a few others in town might have these for cheap. I'm sure I have seen them places, I just can't find anything online.

---

### Post by Maheriano on 2009-08-07
There are adapters but in order to use them you'll need an actual converter for the signal, not just an adapter. I already have a VGA-component cable and it doesn't work. And those converters would cost even more than a card.

---

### Post by gletob on 2009-08-07
> **Maheriano said:**
> There are adapters but in order to use them you'll need an actual converter for the signal, not just an adapter. I already have a VGA-component cable and it doesn't work. And those converters would cost even more than a card.

+1

And in my oppinion you need a card that will output in DVI or HDMI because anything less would look horrible on a tv.

---

### Post by northwestuntu on 2009-08-07
im gonna have to try some of this :P

---

### Post by Maheriano on 2009-08-07
> **gletob said:**
> +1

And in my oppinion you need a card that will output in DVI or HDMI because anything less would look horrible on a tv.
It depends on the file you're playing. Most television shows that are downloaded are recorded though basic cable which is 480i or 640x480. So whether you play that file with a RCA cable or HDMI cable, it's going to look exactly the same because it's sending only those 480 lines of resolution through the line into the television for processing. The only time it would matter is when I'm cruising around the desktop which is something I'm not going to be doing, the media center will constantly be running and will be the sole purpose of this machine.

---

### Post by sydbat on 2009-08-10
Sorry the cards I found won't work for you.

I do have a question though - can you post some type of cost for your project...like what you thought you'd spend (budget) and what you end up spending (under / over budget)? Also, where to find the products you are using and what their individual costs are?

---

### Post by Maheriano on 2009-08-10
> **sydbat said:**
> Sorry the cards I found won't work for you.

I do have a question though - can you post some type of cost for your project...like what you thought you'd spend (budget) and what you end up spending (under / over budget)? Also, where to find the products you are using and what their individual costs are?
Wow, this is going to be a long post! Breathe iiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiiin.........[SIZE="1"]here we go[/SIZE].....

For my media center all it required was:
- 3 computers
- cabling
- home theater system
- television
- projector
- screen
- 2 extra speakers

That's all it was. So the main computer running the music in the basement and hooked to the home theater / projector is my main desktop. Everyone has a desktop machine so this didn't cost me anything, I already had it. And it's hooked to my projector which I bought about 2.5 years ago. I had budgeted $2000 for a nice plasma or LCD television and when I started shopping around I realized the projectors give a much bigger picture and it's just about the same quality picture as well. So I ended up buying the projector....so that didn't cost me anything as I already had that as well. And the home theater system my dad bought for me for Christmas a few years ago so I already had that, that didn't cost me anything. So that's my media center in my basement, didn't cost me a dime.
Moving up to my living room, I've got 2 more speakers, 2 more computers and a LCD television. Well the television is my roommate's so that didn't cost me anything and one of the computers is my laptop which I already had (and most people do) so that didn't cost me anything extra. And I was at work one day 2 months ago and they were throwing out a pile of old computers but let me dig through it all first. So I took one of them home for my living room media center and that's what I'm using now, so I got that for free, that's the third and final computer.
So lastly, I was on a forum last month and had posted that I was looking to buy some speaker stands for $10. When I went to pick them up at the guy's house, he was in the middle of moving out and said, "Hey, do you want this 6 disc Sony CD changer and JVC receiver for free?" So as I'm trying to (very wobbly) navigate my way out the door, I'm stepping over a Kenwood speaker set and he says, "Hey, you want some Kenwood speakers for free too?" So that's how I got all the audio equipment for my living room, it was all free. So far I've spent nothing on that except $10 for some speaker wire. So that's the living room and the basement media centers.

Now my X10 project. I've been looking at this stuff for years, and just drooling every time I research it. I could never afford all the stuff as you need the sender unit (CM11A, CM15A or CM17A) and you also need to replace all your light switches and outlets that you want to control. Plus the list goes on with thermostats, wireless cameras and a pile of other addons. I could never afford it but I would always talk with other geeks about it, usually it was even over their heads and I ended up looking like a super geek. So I was at work and the same guy that let me pick through the computers he was throwing out was talking to me about home automation and I mentioned to him how I wanted some X10 stuff but couldn't afford it. He says to me, "Well, I got boxes of the stuff at home, I don't use it. I'll bring it in for you one day." It was about 5 months later he finally remembered and brought it in, he told me to make an offer but it was about $500 worth of stuff there, it was enough to do an entire house. I completely lowballed him and offered $70, he said, "Well, how about you give me $50, that way I won't feel bad if something doesn't work anymore." So I got an entire house full of X10 stuff for $50, it was an incredible deal. Here's pictures of everything I got from him:

[IMG]http://www.danmaher.com/gallery/d/14033-2/1.JPG[/IMG]

[IMG]http://www.danmaher.com/gallery/d/14037-2/2.JPG[/IMG]

[IMG]http://www.danmaher.com/gallery/d/14040-2/3.JPG[/IMG]

[IMG]http://www.danmaher.com/gallery/d/14043-2/4.JPG[/IMG]

[IMG]http://www.danmaher.com/gallery/d/14046-2/5.JPG[/IMG]

---

### Post by Maheriano on 2009-08-10
And for reference, here's some pictures and pricing of what you see in the pile. These are the 2 interfaces I received which actually send the commands out to my devices to turn them on/off.

CM11A
[IMG]http://cache1.smarthome.com/images/1140.jpg[/IMG]
Price: Not available anymore
This plugs into the wall and sends the commands through the house AC wiring

CM17A
[IMG]http://www.aartech.ca/images/cache/71c63142d92a706ab45b4c7b8da1f50f.jpg[/IMG]
Price: $20 CAD
This sends the commands out wirelessly but needs a receiver module to receive the wireless commands.

And these are the receivers I use:

WS12A
[IMG]http://www.aartech.ca/images/cache/cd9f26d415da3335d2bdc3cb605ad784.jpg[/IMG]
Price: $16 CAD
This replaces your light switch so you need to buy one for every switch you need to replace.

WS14A
[IMG]http://www.aartech.ca/images/cache/5ae2eada75baa6f1a7f2f4c163673004.jpg[/IMG]
Price: $12
This is a 3-way companion switch. If you want to replace a switch which is one of a pair controlling a single light then you need to use one WS12A and one WS14A.

RR501
[IMG]http://www.aartech.ca/images/cache/22b9dd0dd09cce510dd9956e1fc09280.jpg[/IMG]
Price: $17 CAD
This receives wireless commands either from the computer or from a remote control and transmits them to any receivers through the house AC wiring.

And these are remote controls that I have to control everything wirelessly:

HR12A
[IMG]http://www.aartech.ca/images/cache/760e3daea3d7c252765bbb437e913eec.jpg[/IMG]
Price: $10 CAD
This is a control pad you mount by the door to turn everything on/off.

KR22A
[IMG]http://www.aartech.ca/images/cache/70edfff7ceee61aa1485cd8585c4ff82.jpg[/IMG]
Price: $10 CAD
This one's my favourite, it's a credit card sized thin remote that controls up to 4 devices. I have one in the garage and one in the master bedroom for the lighting systems.

UR74A
[IMG]http://www.aartech.ca/images/cache/2cd727008020422d35693b009f4cdcdc.jpg[/IMG]
Price: $20 CAD
An all-in-one remote control for your complete media center plus it controls your X10 devices. Great for starting a DVD and changing the lighting from the same remote.

So basically I got a pile of X10 stuff, and I got it for less than 1/10 of the retail price.

Lastly is my car setup, this is the only one I actually made a budget for and didn't just pick up parts as I went along. I had initially thought I would do this project with old desktop parts for no more than $200 total. Since then I have spent about $2300 on the carputer, it consists of a Xenarc 700TSV touchscreen 7 inch monitor in the dash ($400 CAD), an Intel MiniITX motherboard with Atom 330 processor ($85 CAD), M2-ATX DC-DC 160 watt power supply with startup controller ($100 CAD), Ampie MiniITX case ($80 CAD) and your miscellaneous RAM, hard drive and cabling. This project is almost 4 years in the making though so that budget is really spread out.

EDIT - Some of the products can be found time to time at XSCargo, some of them are Radio Shack so they might be at The Source, and the rest can be ordered from a Canadian company called AARTech ([www.aartech.ca](www.aartech.ca)).

---

### Post by sydbat on 2009-08-12
Thanks.

So let me see if I understand all this...

You get stuff for free and stuff for virtually nothing. You are like my in-laws...they go to garage sales and get stuff that is really cool (and often high end) for free or virtually nothing.

Can I go shopping with you??:P

---

### Post by Maheriano on 2009-08-12
haha ya, I'm a cheap guy!
Just last week I was looking at $60 tanks for my tarantula but just knew I could get it for cheaper. Eventually I found a pet store that was going out of business and they had similar $60 tanks on sale for $15. I took the display model because it was missing some parts and the guy gave it to me for $10. And when I opened it I found $2 inside so I actually got it for $8!

This one's the best though, last year my roommate gave me her Dell D600 laptop because she had broken the screen off the base. It still worked, the screen was only attached by the wire and nothing else so it was kind of useless. I posted on a local forum asking if anyone had a D600 case, a guy gave one to me for free so I swapped all the parts into it and now it works like new! When my roommate came home and saw I was using my fully functional D600 laptop she was......a little upset! I ended up loading Ubuntu on it and giving it to my brother last Christmas.

And my X10 stuff works off my serial port except my desktop didn't have serial. I had to go pick up a PCI serial card and a guy gave it to me for free (same guy as the D600 case). He said it was cheaper to give it away rather than sell it because it meant his accounting department wouldn't have to write down all the information and track the sale, wasting time they could spend doing other things.

I don't like spending money.

---

### Post by Maheriano on 2009-08-18
Well, the weekend brought me back to it again.

I've had my Intel [Intel D945GCLF]("http://www.intel.com/Products/Desktop/Motherboards/D945GCLF/D945GCLF-overview.htm") for a few months but had to wait on my DC-DC power supply so I could put it into the car. Well Friday I got my [M2-ATX-HV]("http://www.mini-box.com/M2-ATX-HV-140w-Intelligent-Automotive-DC-DC-Power-Supply_2?sc=8&category=981") via UPS from [www.mp3car.com](www.mp3car.com) in Baltimore, Maryland. When I opened it up I realized it only has a single LP4 (molex) connector and I need 2.....1 to power my screen and 1 to power my IDE hard drive. I contemplated looking for a splitter but when I hooked everything up on the bench I quickly realized my new architecture wouldn't allow my hard drive to boot since my old motherboard (Via Epia M10000) was 32 bit. So even if I did get a splitter I was going to have to reinstall the whole system anyway, why not get a SATA drive? So Sunday night I ended up finding a used 80 gig SATA drive for $15 and installed Windows XP onto it. I got all the drivers loaded and updates installed, the next step is to completely strip it of all the stuff I don't need like networking components and default applications. Enlarge the font for the touchscreen, remove memory hogging themes, you get the idea.

So this week I'm hoping to get it all configured and get the front end installed so I can get it into the car. And after work today I hope to pick up the final cable I need to install it, a male-male P4 connector to go from the PSU to the motherboard. For some reason it didn't come with it, not sure why.

Back on the grind!

---

### Post by Maheriano on 2009-08-18
Another little quick update.
I forwarded port 22 on my router to the internal IP of the system controlling all my X10 modules so that I can SSH into it from outside my network. So now while I'm at work I can run commands to see which lights in the house are on and I can send commands to turn any of them on/off.

And to add to that, I downloaded an application to my Blackberry 8330 called midpSSH that allows me to connect to computers via SSH so now I can actually run my entire X10 system in my house from my Blackberry. No more getting up to get my laptop and remote in. Pretty sweet!

---

### Post by whiskeylover on 2010-04-09
Awesome. Please keep updating this thread.

Mods: I know its an old thread. But please don't lock it.

---

### Post by Maheriano on 2010-04-09
I guess I'll update this though I haven't changed much since I last updated. I had planned on a huge upgrade over the summer but started a business and simply don't have any time. I'm swamped with work.

I did end up replacing almost every light switch in my home with the WS12A/WS14A switches which work on X10. A few of them are low power LED lights which simply don't work with this type of switch, I need to get one specifically for them.

I also plan on getting one for my fireplace but again can't use the switches I have because it has to be a non-dimming switch and all the switches I have use dimming capabilities.

And lastly, I'm looking at a UM506 unit to control the opening/closing of my garage door. I looked into this and the way the unit works is you pull out the 2 wires which get connected by using the switch and put them into the unit. Then when the unit gets a signal from X10, it closes the contact and presto....door opens. The problem with this is this specific unit requires a 120 volt input and there are zero outlets around the switch. Plus I don't want this awful looking thing on the wall. So instead I've decided to get up at the ceiling, pull apart the door opener unit and put it in there. There's a plug right above the opener on the ceiling.

All of this should cost me about $60 shipped from [www.aartech.ca](www.aartech.ca) which is a Canadian company.

Also, since last update I've bought a HTC Hero smartphone running Google Android and installed a very slick SSH program to send command line applications to my desktop server to control all the units. I also had to reconfigure all the port forwarding when I updated to a wireless N router. Oh, and I ditched the Wiimote as a remote control in favour of an application on my phone called Gmote. It acts as a wireless touchpad for my mouse using the entire face of the touchscreen of my phone. There's also a button to bring up the on screen (on phone) keyboard to type something in. I posted a video of it here on the forums somewhere.

---

### Post by whiskeylover on 2010-04-09
Awesome. I'll be "smartizing" my home soon, and will be bugging you with questions, if you don't mind : )

---

### Post by Maheriano on 2010-04-12
Don't mind at all, I love technology. I might actually annoy you with wanting to see pictures of the install and asking how you did things!

I found some pretty cheap X10 stuff on Ebay last night for $7 each so I might be getting to this sooner than expected.

---

### Post by Maheriano on 2010-04-30
Well, I've been doing more research which seems like all I can do right now until I get some extra cash. I don't know if I mentioned this already but I'm going to get a UM506:

[IMG]http://www.aartech.ca/images/cache/a195d217d47a8cc1c28c074b904b3478.jpg[/IMG]

This will connect to the input line on the motor to my garage door and let me open/close the garage via X10 on my phone. Or I can set it to automatically open based no my phone entering the GPS coordinates of my house but that could get quite annoying. I can also use one of these to activate the fireplace I think.

I'm also getting some DS10A for the windows/doors:

[IMG]http://www.aartech.ca/images/cache/31125a12fb2d1c8ffd2bce1317f8e357.jpg[/IMG]

That will tell me when the windows/doors have been opened while I'm away so I can view the cameras on my phone to see what's going on.

I also came across some software to run on my home server that a guy made called Domus.Link. Check it out [here]("http://domus.link.co.pt/screenshots/iphone-theme/"). It's a web based front end for the command line control system I'm running right now and simply runs on an Apache install which I already have running. The iPhone theme right now comes up only when you access the site from an iPhone but I plan on hacking the configuration file to display it for my Android as well. It's just web based anyway so it should work.

---

### Post by GreyWolf903 on 2010-05-12
Hey guy, nice job on the Home Automation Project.  Especially like your approach to the media Center/Home Theater.   Glad to see you've updated this thread recently and keeping it alive.

Been working  on my Home Automation system for a couple years now and use it daily still..  When I initially setup my system I chose a commercial Windows based application with Voice Recognition support  While I enjoy my HA system, I have grown increasing  tired of Microsloft Windblows and have been looking at altenative solutions, so I'm new to Ubuntu and Linus but really like what I see.  In my search for alternative HA solutions I came across your posts.  It sounds as if the Mister Housea and HeyU are working well for you.  I'll definitely be checking them out!  My biggest concern will be the availability  of code to interface with some of my existing devices.

One question, were you able to get the projector screen to raise and lower automatically  and if so were you able to use X10 to do this or did you have to go with an IR transmitter?

---

### Post by Maheriano on 2010-05-13
> **GreyWolf903 said:**
> One question, were you able to get the projector screen to raise and lower automatically  and if so were you able to use X10 to do this or did you have to go with an IR transmitter?
I ordered the screen from Tiger Direct but they screwed me over on a video camera so I canceled all my orders including the screen. My plan was to use a simple motor like [this]("http://www.smarthome.com/3142/Motorized-Drape-Controller/p.aspx") which is motorizing your drapes. It would still work, I just haven't gotten to it yet.

I did however, order 2 UM506 from Ebay for $20 to automate my fireplace and garage door as I had put on my list. Should be here any day.

---

### Post by tmette on 2010-06-02
It's nice to see this thread being updated continually.  I would love to do this to my house, but I'm still living with parents.  Once I buy a house of my own I plan to do this.  I do like your idea with the computer in the car and touch screen.

---

### Post by Maheriano on 2010-06-03
> **tmette said:**
> It's nice to see this thread being updated continually.  I would love to do this to my house, but I'm still living with parents.  Once I buy a house of my own I plan to do this.  I do like your idea with the computer in the car and touch screen.

Computer in the car is done, I can post pictures if anyone wants to see. I'll be ripping it out sometime soon to install Windows 7 on it, it has XP on it now. Need something more updated. I bought Windows 7 for $50 last year but haven't used it for anything yet as I have Ubuntu on all my machines. I'll finally put it to use.

Still haven't installed the UM506 modules for the garage door, haven't had any time. All my time at home is taken up doing a power window conversion on my car. No more rolly windows.

---

### Post by pwnst*r on 2010-06-03
Unless I missed it, pics of your car install please.

---

### Post by earthpigg on 2010-06-03
> **pwnst*r said:**
> unless i missed it, pics of your car install please.

+1

---

### Post by Maheriano on 2010-06-04
Coming up when I get time. Either Friday night or Saturday.

---

### Post by Maheriano on 2010-06-05
As promised. Now I did use Microsoft Windows in this specific case because of its compatibility with a lot of my peripherals and also the user friendliness of the skins and navigation applications available for Windows which aren't available with Linux. Navit is simply not as easy to use as iGuidance and until it is, I can't switch over to Ubuntu.....or Linux Ice which is the project name for the Ubuntu in car distribution.....sorry Kevin.

So here's my Windows in car computer system. Keep in mind I'm currently pulling it all out to install Windows 7 over the current XP install and also upgrade a few other things.

On the floor installing Windows and getting all drivers installed. It's a Via Epia M10000 Mini-ITX motherboard with half gig of RAM and a regular 80 gig 2.5 inch laptop drive. The power comes from a M1-ATX DC-DC automative power supply with startup controller. It senses a signal when you turn the key and turns on the computer automatically so you don't have to push the button every time. Then when you turn off your car it puts the computer into hibernate for a quicker resume.

[IMG]http://www.danmaher.com/pictures/d/16829-1/Computer.jpg[/IMG]

Then I put everything into a tiny little case - the blue one. And hooked up the speaker output to a 4 channel amplifier - the black one.

[IMG]http://www.danmaher.com/pictures/d/16835-1/Computer_And_Amp_2.jpg[/IMG]

I pulled out my fan shroud and routed a tiny little USB GPS receiver into there.

[IMG]http://www.danmaher.com/pictures/d/16852-1/GPS_Receiver_1.jpg[/IMG]

Test fit the touchscreen.

[IMG]http://www.danmaher.com/pictures/d/16888-1/Screen_3.jpg[/IMG]

I didn't want to try and navigate Windows while driving the car so I installed a front end called Road Runner and a skin called eLite Lite.

[http://vimeo.com/6670660](http://vimeo.com/6670660)

Since then I've changed most of the hardware, I upgraded the motherboard to an Intel D945GCLF which is a lot faster and also a M2-ATX PSU because of the extra power demand on the board. And that's pretty much how it sits right now with GPS, 2000 songs, music videos and whatever else.

---

### Post by Maheriano on 2010-10-28
There were some issues with not being home very much over the summer but I just got back into my place and I'll be getting back to this install full on pretty soon. I've already got a 7 inch Xenarc touchscreen to put on the wall by the front door, it'll replace the crappy monochrome ADT panel that's currently there and use the existing mounting points. Plus I still have the units to automate the garage door and fireplace that I picked up earlier this year during a X10 sale they had online.

---

### Post by Maheriano on 2011-05-06
Small update.

I finally opened up the 2 UM506 modules that I bought last year and put one to use.

The objective - To be able to remotely control the on/off functionality of my natural gas fireplace in my living room.

So what I did was cut the power to my house at the main breaker in the basement and tried the switch on the wall to turn on the fireplace. The fireplace still came on which meant it wasn't using power from the 120 line of the house, it was using some sort of low power ignition control which is perfect for the UM506 module. 120 house wiring however, is definitely not suitable for controlling a fireplace with X10.

So once I made sure of that, I took the switch out of the wall and hooked the 2 wires to the UM506, plugged it into the wall as is required and gave it an address. I remoted into my computer via SSH, ran the on script and bingo bango, the fireplace came on! I didn't like the idea of not having a manual override so what I did was wire the switch in series with the UM506 so it'll only work if the switch is in the on position. At any time, for emergencies or vacation, I can put the switch to off and X10 won't accidentally turn on the fire.

So to sum it up, what I did was this:
1. unhook 2 fireplace wires from switch in wall
2. hook 1 wire back to switch and put 1 on UM506.
3. run another wire from UM506 on other side, back to switch so they're both wired in series
4. plug in UM506 as is required
5. give it a X10 address

Done!

Next up: garage door.

---

### Post by Throne777 on 2011-05-06
Reminds me of the episode of The Big Bang Theory when they set up all the light switches to be controlled via the internet (so people in China could turn their lights on & off, for novelties sake).

---

### Post by Maheriano on 2011-05-07
> **Throne777 said:**
> Reminds me of the episode of The Big Bang Theory when they set up all the light switches to be controlled via the internet (so people in China could turn their lights on & off, for novelties sake).

X10, same technology. Except I don't know why they forwarded their port externally, they could have just connected internally on the network. For television I guess.

Here's the video before I wired in the switch.

[http://www.youtube.com/watch?v=fBUJsjlUbiY](http://www.youtube.com/watch?v=fBUJsjlUbiY)

---

### Post by Maheriano on 2011-05-17
I upgraded my desktop to a quad core with 8 gigs of RAM so I reinstalled Ubuntu to reflect a larger SWAP partition and a cleaner environment. Because of that I had to set up Apache again and decided it was time to add [Zoneminder]("http://www.zoneminder.com/") to the mix as well. I only tested it with a crappy webcam but I actually got it working and it's pretty sweet. I can access the cameras through any browser by using my IP and I can pan/tilt them as well (if I had that kind of camera).

Zoneminder also has X10 integration so I can run any X10 command I want when the camera is triggered.

Now that I got it working I'll be going out this week to pick up a high definition webcam to set up with motion detection and secure my house.

Thanks for being awesome, Ubuntu!

---

### Post by Maheriano on 2011-05-18
I almost forgot. I also installed an Android application on my phone called [URemoteDroid]("http://www.guatedroid.com/") and ran the server on my desktop so now I can use my phone as a remote control to run Banshee on my desktop. I use a projector instead of a normal monitor so I don't have the patience to wait 30 seconds for the projector to warm up before being able to turn the music on so now I can just whip out my phone, connect to the server and click PLAY to get the music going. It also has capability to change the track and also the volume. Perfect when you're going from room to room.

---

### Post by williammanda on 2011-11-24
I've read through your posts and would like to know the steps to installing Misterhouse. Also any feedback with the use as well.
Thanks

---

