---
title: "Neighbor says &quot;I can see what's in your computer&quot;"
date: 2007-01-16
forum: The Cafe
---

### Post by xyz on 2007-01-16
Hi,

Actually a friend told me that yesterday. I went to his house and installed Ubuntu dual boot with XP Home. That's the good news! Yeah...one more in the community!

I had very little to offer him as an answer/explanation and solution as I'm not one to pry into someone's computer, one way or another, even if I knew their user's names/passwords.

I guess the neigbor's stealing my friend's Internet connection; WIFI!!

Now will that also happen now that my friend will be using Ubuntu to surf?

Thanks for reading.

---

### Post by Dragonfly_X on 2007-01-16
Your friend will have to setup some encryption on his wifi router (asuming it's a router). You could use a WEP shared key or/and setup the router firewall's MAC addressing (a computer's hardware address).

This should prevent any unwanted computers from connecting to your friend's network.

---

### Post by speedwell68 on 2007-01-16
If you go out with a wireless laptop you will find the number of unencrypted wifi connections out there mind boggling.  With one bloke I could see his peer to peer windows network, I could have printed on his networked printer if I wanted to.  This really worries me that there are literally hundreds of unprotected people out there literally givng the world access to there personal stuff.

---

### Post by slimdog360 on 2007-01-16
depending on where the access point is he may be able to lower the power output of the signal just enough to get around his house. Thats what I do with mine. Plus all of the MAC filtering, WPA stuff etc.

Either that or he can get a baseball bat and have some fun on his neighbors computer.

---

### Post by xyz on 2007-01-16
> Either that or he can get a baseball bat and have some fun on his neighbors computer. LOL!!
That sure is what I would do!!
I don't use WIFI; don't know the 1st thing about it except that its...wireless!

Now you all gave me good advice even though I don't understand how exactly I should go about installing these filter, WPA and so on.

Would [T H I S]("http://ubuntuforums.org/showthread.php?t=185174") be a good place to start learning how to protect my friend's computer from this damn invasive neighbor?


Also lowering the power output of the signal seems to be something I'd be capable of doing for him. But would it be enough?

---

### Post by RandomJoe on 2007-01-16
> **xyz said:**
> Now will that also happen now that my friend will be using Ubuntu to surf?
When he's running Ubuntu, not by default.  If he enables sharing, opens ports and such, then sure it's possible but by default Ubuntu is nicely closed up - certainly it isn't sharing the hard drive via SMB which is what most people mean when they say they can "see your computer".

I haven't run Windows in a while, so I'm not sure what's enabled by default, but perhaps the neighbor found the default share for the hard drive and was looking at that?  So when he boots to Windows he may still have isses, although most commonly people share their drive to "Everyone" without a password because it's easier to move stuff between their own computers.  It doesn't occur to them when they add the wireless AP that anyone in range can now do the same thing...

Depending on the technical competence of the neighbor, the simplest solution is usually just to enable encryption on the access point - most people won't go to the trouble of breaking it (or even know how).  If this neighbor is capable and willing, then you'll have to go further.

The MAC filtering is just something you set up in the access point, usually through its web-based interface.  The encryption (WPA, preferably) is also set up there, although you also have to set it up on the other end at each computer using wireless cards.

---

### Post by prizrak on 2007-01-16
> **Dragonfly_X said:**
> Your friend will have to setup some encryption on his wifi router (asuming it's a router). You could use a WEP shared key or/and setup the router firewall's MAC addressing (a computer's hardware address).

This should prevent any unwanted computers from connecting to your friend's network.

Why would you recommend WEP? It's 2007 not 2001 we got WPA (even WPA2 but not as many cards support it). WEP is utterly useless and should never be used for anything, WPA is the encryption to setup.

---

### Post by irish_flu on 2007-01-16
Your friend should definitely set up Wifi encryption (preferably WPA) and MAC-address filtering.  Whatever kind of Wireless Router it is, look in the manual or check out that manufacturer's website; there should be instructions for your friend's particular model.

Then your friend should remind the neighbor that webcams are everywhere, and his curtains are not opaque. :-D

If you want to post the make and the model number of your friend's router, we might be able to point you to instructions....

---

### Post by apunc1 on 2007-01-16
he could also change the SSID (name of the router, i.e linksys, netgear) and disable SSID broadcast so that the SSID doesn't come up when someone goes looking for wifi connections
the other suggestion about WPA encryption is encouraged as well
have your friend change the administrator password of the router also, so the neighbor can't log in to the router and change all the before mentioned settings that your friend will set up.

---

### Post by AlanRogers on 2007-01-16
> **prizrak said:**
> WEP is utterly useless and should never be used for anything, WPA is the encryption to setup.Three points spring to mind here:[LIST=1]
[*]There is apparently no encryption at all at present so WEP is a definite improvement. Sure, MAC address filtering and WPA encryption are better than WEP but the former is inflexible and the latter is more difficult to set-up.
[*]The primary issue is that the neighbour can apparently see the default admin share on the C: drive, which is easily addressed without even touching the router - just set a password on the login profile!
[*]We're giving advice to someone who self-confessedly doesn't know much about WiFi who is then going to try and support the friend. Surely the friend should just be pointed in the direction of real assistance ... and a baseball bat for the nosey neighbour
[/LIST]A quick win is all that's required here and all that requires is to become more difficult to look at than any one else in range. WEP, and a profile password, will deal adequately with this. 

EDIT: I overlooked changing the default password and SSID on the router, as suggested below but the underlying sentiment of KISS (Keep It Simple Stupid) still applies - don't try to run before you can walk and, above all else, don't break your mate's connection!

---

### Post by apunc1 on 2007-01-16
> **AlanRogers said:**
> 

EDIT: I overlooked changing the default password and SSID on the router, as suggested below but the underlying sentiment of KISS (Keep It Simple Stupid) still applies - don't try to run before you can walk and, above all else, don't break your mate's connection!

disabling SSID broadcast and changing the SSID are easier than enabling WPA encryption and will in no way disrupt the wifi connection. :) 
one of the first things you should do when setting up a wireless router after making sure your router and modem and computer all talk to each other is change the administrator password. otherwise, anyone who finds the connection can log into it using 192.168.1.1, enter admin as the password, and totally hack your connection :(

---

### Post by AlanRogers on 2007-01-16
> **apunc1 said:**
> disabling SSID broadcast and changing the SSID are easier than enabling WPA encryption and will in no way disrupt the wifi connectionI totally agree with everything you've said and totally endorse the advice. However, the starting comment on the thread was "I can see your computer", not "I can see your router". Therefore, whilst these steps should indeed be taken anyway and as soon as possible, they won't deal with the network security issue.

Ubuntu, indeed Linux, asks you to set a user password in setup by default. Windows does not and then shares the root of all hard drives by default! Therein is the root cause of this problem I think. The router is ancilliary to the problem, not the cause.

---

### Post by apunc1 on 2007-01-16
> **AlanRogers said:**
> I totally agree with everything you've said and totally endorse the advice. However, the starting comment on the thread was "I can see your computer", not "I can see your router". Therefore, whilst these steps should indeed be taken anyway and as soon as possible, they won't deal with the network security issue.

Ubuntu, indeed Linux, asks you to set a user password in setup by default. Windows does not and then shares the root of all hard drives by default! Therein is the root cause of this problem I think. The router is ancilliary to the problem, not the cause.

but the reason the neighbor can see the computer is because of the wireless connection, so setting up security on that is key to solving this particular problem. 
i was talking about the admin password of the router, not the computer os, just so we're on the same page!

you're right about os security too. but the open ports on the windows os are a whole other issue :)

---

### Post by AlanRogers on 2007-01-16
> **apunc1 said:**
> You're right about os security too. but the open ports on the windows os are a whole other issue :)We're definitely on the same page and, FWIW, Windows / Wireless Security is a nice little money earner. I have absolutely no issue letting that cat out of the bag because there's way more work than I can cope with! :cool: 

When I moved two years ago, I was connected to the internet long before our broadband was enabled, courtesy of the wireless network in the school behind! You'd think that they'd know better. ](*,)

I didn't try to hack their network though, just stole their bandwidth for a few days. [-(

---

### Post by dca on 2007-01-16
Everyone here is correct, find the IP of the wireless router and access it through his web browser:
 
(1)  Disable broadcast of SSID
(2)  Enable WEP (WPA is somewhat better but more of a pain to set-up, ie:  wpasupplicant)
(3)  Apply MAC address filters on wireless router

Everything mentioned above and by everyone else is done on the router end...

---

### Post by viper on 2007-01-16
> **dca said:**
> Everyone here is correct, find the IP of the wireless router and access it through his web browser:
 
(1)  Disable broadcast of SSID
(2)  Enable WEP (WPA is somewhat better but more of a pain to set-up, ie:  wpasupplicant)
(3)  Apply MAC address filters on wireless router

Everything mentioned above and by everyone else is done on the router end...

Exactly  correct...............and as slimdog360 mentioned in his earlier reply go over with the baseball bat :twisted:  that should deter the bugger!!!!

---

### Post by daynah on 2007-01-16
> **speedwell68 said:**
> If you go out with a wireless laptop you will find the number of unencrypted wifi connections out there mind boggling.  With one bloke I could see his peer to peer windows network, I could have printed on his networked printer if I wanted to.  This really worries me that there are literally hundreds of unprotected people out there literally givng the world access to there personal stuff.

What worries me more is people are talking about having your washing machine and other appliances hooked up to your computer network. Just imagine the literal physical damage one could do to a house if all of your appliances where hooked up to a computer and thus accessed by anyone?

---

### Post by Bezmotivnik on 2007-01-16
> **prizrak said:**
> Why would you recommend WEP? It's 2007 not 2001 we got WPA (even WPA2 but not as many cards support it). WEP is utterly useless and should never be used for anything, WPA is the encryption to setup.
Completely correct, but anything else is such a nosebleed to set up in Linux that most people are relieved to even have the obsolete and almost worthless WEP.

Someone nearby has 3M WiFi DSL on a carefully secured box, but with the connect open for neighborhood use, which is nice.  I'm on it now and run a repeater off it to extend range, along with someone else's repeater operating somewhere else.  Otherwise, I wouldn't be using Linux online as I could never get WPA2 to work in Ubuntu or any other Linux when I had my own *highly-secure* WiFi.

While I had a very secure wireless net, I'm not as sure about my security on my own computers now that I'm accessing an open DSL WiFi connect. :-k

---

### Post by Bezmotivnik on 2007-01-16
> **viper said:**
> as slimdog360 mentioned in his earlier reply go over with the baseball bat :twisted:  that should deter the bugger!!!!
Baloney.

Unsecured, open WiFi is presumptively public.

---

### Post by migla on 2007-01-16
Before you use the baseball bat, consider if maybe the neighbor was doing your friend a favor by pointing out that some shared stuff was visible to anyone.

---

### Post by prizrak on 2007-01-16
> **AlanRogers said:**
> Three points spring to mind here:[LIST=1]
[*]There is apparently no encryption at all at present so WEP is a definite improvement. Sure, MAC address filtering and WPA encryption are better than WEP but the former is inflexible and the latter is more difficult to set-up.
[*]The primary issue is that the neighbour can apparently see the default admin share on the C: drive, which is easily addressed without even touching the router - just set a password on the login profile!
[*]We're giving advice to someone who self-confessedly doesn't know much about WiFi who is then going to try and support the friend. Surely the friend should just be pointed in the direction of real assistance ... and a baseball bat for the nosey neighbour
[/LIST]A quick win is all that's required here and all that requires is to become more difficult to look at than any one else in range. WEP, and a profile password, will deal adequately with this. 

EDIT: I overlooked changing the default password and SSID on the router, as suggested below but the underlying sentiment of KISS (Keep It Simple Stupid) still applies - don't try to run before you can walk and, above all else, don't break your mate's connection!
WEP can be broken in less than an hour with any decent laptop it's not an improvement. WPA is no harder to set up than WEP (in fact with Windows and newer Linksys routers there is a one button setup that takes care of it for you). MAC blocking is unnecessary on a WPA secured AP simply because you can't connect w/o the WPA key.

---

### Post by G Morgan on 2007-01-16
My network will only allow devices on via registration but I still use WEP on top of that. I may well change that over time. All static machines are wired in properly of course and I turn off wireless altogether if I won't need if for a few days.

---

### Post by G Morgan on 2007-01-16
> **prizrak said:**
> WEP can be broken in less than an hour with any decent laptop it's not an improvement. WPA is no harder to set up than WEP (in fact with Windows and newer Linksys routers there is a one button setup that takes care of it for you). MAC blocking is unnecessary on a WPA secured AP simply because you can't connect w/o the WPA key.

How many people are capable of it. Encryption is there to stop grandma next door from stealing your bandwidth, if somebody was serious then WPA can be cracked as well, especially if people use WPA-PSK.

If somebody is really determined to stand outside my home for an hour risking me cracking something heavy across their head then God encryption may not be enough.

---

### Post by Bezmotivnik on 2007-01-16
> **G Morgan said:**
> How many people are capable of it. 

Any scriptkiddie can bust WEP in as little as five minutes with readily available online guides and freeware.

All WEP means is that the owner does not *intentionally* wish to share bandwidth.

> Encryption is there to stop grandma next door from stealing your bandwidth, if somebody was serious then WPA can be cracked as well, especially if people use WPA-PSK.
Not so.  The only thing that currently works against WPA2/AES is dictionary attacks, and that's simply not happening if you set up with a 63-character random ASCII PSK, which are [instantly generated from a number of sites]("https://www.grc.com/passwords.htm").

AES is simply more cryptologically robust, and using the inherently greater security features of WPA2 you can make your WiFi **extremely** difficult to access -- impossible for all practical purposes.

---

### Post by prizrak on 2007-01-16
> **Bezmotivnik said:**
> Any scriptkiddie can bust WEP in as little as five minutes with readily available online guides and freeware.

All WEP means is that the owner does not *intentionally* wish to share bandwidth.


Not so.  The only thing that currently works against WPA2/AES is dictionary attacks, and that's simply not happening if you set up with a 63-character random ASCII PSK, which are [instantly generated from a number of sites]("https://www.grc.com/passwords.htm").

AES is simply more cryptologically robust, and using the inherently greater security features of WPA2 you can make your WiFi **extremely** difficult to access -- impossible for all practical purposes.

Just to add to that, anyone who uses a password database program (just about everyone should be by now) can generate huge random passphrases in their programs (also helps letting friends on). 

Even WPA-PSK is difficult enough to break to be considered inpenetrable from a home user's perspective.

---

### Post by Bezmotivnik on 2007-01-16
> **prizrak said:**
> 
Even WPA-PSK is difficult enough to break to be considered inpenetrable from a home user's perspective.
Some WPA-PSK implementations can use AES, which makes them essentially the same as WPA2.  WPA features seem to vary a bit in the wireless devices I've encountered.

---

### Post by G Morgan on 2007-01-16
> **Bezmotivnik said:**
> Any scriptkiddie can bust WEP in as little as five minutes with readily available online guides and freeware.

All WEP means is that the owner does not *intentionally* wish to share bandwidth.

Again how many script kiddies exist out there. In all likelihood there is 1 for every 1000 people, living within range of one is very unlikely. I'm not saying it is impossible but if this was a serious problem you'd see more people using encryption, the sheer lack of noise about it generally suggests it's not as big a problem as it technically should be

Anyway no one can actively use my network without MAC address registration though I suppose they could intercept packets being passed back and forth. They would not be able to make requests and steal bandwidth even if I used a totally unencrypted network. I prefer a white listing system in any case since it can be left alone, the WEP is just there for an extra layer of protection. I find it a much simpler solution than WPA though I will be adding WPA on top of this in future.

Also the best solution of all is RJ45 wherever possible and being selective with your wireless. Further than that don't be lazy and check your server logs and password any network shares.

---

### Post by Bezmotivnik on 2007-01-16
> **G Morgan said:**
> Again how many script kiddies exist out there. In all likelihood there is 1 for every 1000 people, living within range of one is very unlikely. 
In Wales, maybe.  Here, where I live -- in Northern California's Hi-Tech Triangle -- there are kids hacking the systems in my immediate vicinity, purely for sport.  I was astonished at the number of wireless nets and that they are being doinked with.

> Anyway no one can actively use my network without MAC address registration though I suppose they could intercept packets being passed back and forth.

They can crack MAC listing as quickly as WEP cracking, with the same "how-to" pages all over the net.

> Also the best solution of all is RJ45 wherever possible and being selective with your wireless. 
Yes, the best way to have your wireless net secure is to not have it wireless...

The main ways to *really* secure your WiFi are to turn off the AP when not in use, limit signal strength and coverage to areas actually needed, and use WPA2/AES with long, random-ASCII PSKs.

Any of the other measures, like WEP, are trivially beaten -- though of course they should be used anyway on the "security-in-depth" principle; can't hurt, might help.

---

### Post by macogw on 2007-01-17
> **prizrak said:**
> Why would you recommend WEP? It's 2007 not 2001 we got WPA (even WPA2 but not as many cards support it). WEP is utterly useless and should never be used for anything, WPA is the encryption to setup.
Well, from what I understand there were some really bad backdoors in Linksys routers that made hacking their WEP a task of a few minutes.  A hacker I know says that one of his hacker-buddies now works for Linksys and told them about them, so then they fixed them.  Now you actually have to sit there and gather a huge crapload of packets and the easiest way is to kick them off so many times that they have to reauthenticate over and over and over, but it takes like a half hour.  My hacker-buddy claims he can get into WPA in 4 packets.  IF he was getting whole (not partially fragmented) packets during a login, then I'd believe it.  I think he's exaggerating.  He did say "only if it's regular WPA though.  WPA2? I can't do it"  So basically, WPA2 is the grand-daddy of it all and WEP on Linksys isn't as bad as it used to be (which says nothing for NetGear et al).

To G Morgan: wrong.  MAC Address Filtering is an easy easy spoof.  Heck, Ubuntu in a VM will automatically spoof the MAC.

---

### Post by xyz on 2007-01-17
THANK YOU all for the replies! I don't have the time to go through the thread right now but I sure will as soon as I can.

I'll also get more informations,specs and so on.

Just a thought: wouldn't doing this help as a first step:

System > Admin > Login Window > Remote/security tabs and then disable in there?

---

### Post by apunc1 on 2007-01-17
> **xyz said:**
> THANK YOU all for the replies! I don't have the time to go through the thread right now but I sure will as soon as I can.

I'll also get more informations,specs and so on.

Just a thought: wouldn't doing this help as a first step:

System > Admin > Login Window > Remote/security tabs and then disable in there?

i'm not sure exactly what that does, as i'm not at my ubuntu machine now, but the steps everyone gave you are done through the router admin page.
the router documentation should list the ip to login to the router (i.e. 192.168.1.1 or 192.168.0.1, it should say on the router's website if your friend can't find the documentation)
the documentation (or website) should also tell you the username/password to access the admin page of the router.
from there, there are a set of tabs such as basic setup, wireless, then under that wireless security. you should be able to change your SSID, disable SSID broadcast, and also set up any encryption (WEP, WPA, WPA2) or MAC filtering if you wish.
also, be sure to change the admin password of the router, as it's usually set to "admin" or something widely known and easily found.
i hope that is more clear.:D

---

### Post by xyz on 2007-01-17
Yes it is a bit clearer now Thx! Next step is to go over to my friend's when I get the chance to - things will no doubt become clearer when I'm in front of his box even though I have NO experience in this....and he turned on his 1st computer ever...2 days ago!
Will keep you informed! Thx again everyone!

---

### Post by esaym on 2007-01-17
> **slimdog360 said:**
> depending on where the access point is he may be able to lower the power output of the signal just enough to get around his house. 


Thats what everyone should do.  Who wants brain [cancer]("http://www.google.com/search?hl=en&q=wireless+cancer&btnG=Google+Search"):mrgreen: 

Mine works fine for me set at 1mw

---

### Post by macogw on 2007-01-17
> **xyz said:**
> THANK YOU all for the replies! I don't have the time to go through the thread right now but I sure will as soon as I can.

I'll also get more informations,specs and so on.

Just a thought: wouldn't doing this help as a first step:

System > Admin > Login Window > Remote/security tabs and then disable in there?

He has remote desktop enabled?  Well that makes it considerably easier for people to get inside your computer.  It's an open door.

---

### Post by MrHorus on 2007-01-17
> **apunc1 said:**
> but the reason the neighbor can see the computer is because of the wireless connection, so setting up security on that is key to solving this particular problem. 


That's simply not true - the reason the neighbour can see the open shares is because the Windows machine is not locked down and secured and THAT is the problem.

The wireless is just the medium for the attack and if you were on a shared cable modem infrastructure you would still be able to browse the shares since the problem lies with the Windows machine.

Locking down the AP is a start and it's a good one but the Windows machine should be secured too otherwise all you are doing is hiding the problem until someone comes along and cracks the encryption.

---

### Post by apunc1 on 2007-01-17
> **MrHorus said:**
> That's simply not true - the reason the neighbour can see the open shares is because the Windows machine is not locked down and secured and THAT is the problem.


i think i misread the original post and you and alanrogers are correct about the windows open shares, but i haven't used windows in a long time so i'm not sure how to close that.
maybe someone here could help the OP with locking down windows once he gets the wireless figured out as the windows holes seem to be a crucial issue as well :)

---

### Post by Biggus on 2007-01-17
Tell your neighbour that you're running a honeypot in conjuction with local law officials in order to try and locate a notorious wireless cracker who's been operating in your area.

Should put them off from ever trying to crack it.

---

### Post by AlanRogers on 2007-01-20
> **apunc1 said:**
> maybe someone here could help the OP with locking down windows once he gets the wireless figured out as the windows holes seem to be a crucial issue as wellIn Control Panel, under User Accounts, for each user:[LIST=1]
[*]Create Password
[*]Make Files Private (which is a step in the above process)
[*]Change My Account Type to Limited (removes Administrator privileges)
[/LIST]
Remember that one user needs to be an Administrator but it doesn't have to be the user you usually use! Without an Administrator log-in, you can't install updates or new software.

Once you've done all of this, boot to Safe Mode (usually F8 after POST) to access the Admin login and make sure that there is a password set on that as well.

Then he shouldn't be able to see anything. If he says he can, ask him to show you, so you know what you're looking for. You'll also then know where he lives! I like the idea about the sting operation though.=D>

---

### Post by apunc1 on 2007-01-20
alanrogers, thank you
xyz, i think with alanroger's suggestions for securing windows and the wireless router security measures offered by myself and others, your friend should have a secure computer with windows and ubuntu :D

---

