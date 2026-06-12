---
title: "firefox 3.5 64 bit"
date: 2009-08-07
forum: System76 Support
---

### Post by dreemreeper on 2009-08-07
Hi
i hope i'm not creating a redundant post here. 
after searching & searching i just cant figure out this firefox 3.5 i did also search this forum, no results returned. searching the whole ubuntu forums has proved more confusing.
[COLOR="Red"]i am on a gazelle ultra, 64 bit 9.04[/COLOR]
I had really good results, and successfully installed 3.5 using this link:
[http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox")
but the problem there was no flash. i tried re-installing restricted extras and iced tea. no-go. so i reverted back to 3.1
i am new to linux, and not proficient with the terminal yet.
i had found firefox 3.5 in repo and installed it but nothing ever changed. today in the update manager i was exited to see firefox 3.5 listed along with a flash and sys76 driver update. but after install, i was disappointed to still have 3.1.  i was going to try the instructions here: [http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/]("http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/") but saw in the comments the 64bit flash still seems to be a problem.
so i guess i am just fishing for any feedback from other system76'ers regarding this since i assume we mostly are all running 64 bit, and that seems to be the problem with the flash.
Won't there come a day when there will be the real firefox full supported 3.5 easily acquired from the update manager or the repository before karmic? I am new to ubuntu and love it and the whole concept of open source. i've even recently changed all my copyrights on my photo sites to creative commons. 
i am shocked though that something open source like firefox, is so damn tricky for a "noob" such as myself to simply to update to the latest version on the leading open source o.s. yet so simple and easy with a couple clicks for a windows user. you would think the open source OS would have the open source browser first and easiest to install?
maybe i'm missing something? does anyone here have a proper version 3.5 running installed correctly where security updates will be automatic and flash works? any solutions or feedback appreciated.

---

### Post by MorphWVUtuba on 2009-08-08
Adobe actually has a native 64bit client.  I didn't find this same link when I installed it, but if you google search Ubuntu 64 bit native flash there's tons of answers.  I know at least one of them worked for me.  :)

[http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/2008/11/install-native-64bit-flash-player-10-on-linux.html)

You could also just go to Adobe's website to install:

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)

-HTH :)


I don't have FF 3.5, I dunno how well this does or doesn't work with 3.5.  Sorry 'bout that.  :-\

---

### Post by gila_monster on 2009-08-08
If you installed 3.5 from the repos, it's there, but /usr/bin/firefox is a softlink that points to firefox-3.0. So when you type firefox at the terminal, or click on the Firefox shortcut that comes standard on the panel, you get 3.0.

Try typing firefox-3.5 in a terminal window and let us know what it does.

BTW, if you change the link to point to 3.5, the next update of 3.0 will reset it. That's bloody annoying.

---

### Post by gila_monster on 2009-08-08
> **MorphWVUtuba said:**
> 

I don't have FF 3.5, I dunno how well this does or doesn't work with 3.5.  Sorry 'bout that.  :-\

Hey, Morph. If it worked for 3.0, should work for 3.5. I have installed 64-bit flash by several means for both, results were identical.

Nice icon. I play tuba quite a bit myself.

---

### Post by dreemreeper on 2009-08-08
> **gila_monster said:**
> If you installed 3.5 from the repos, it's there, but /usr/bin/firefox is a softlink that points to firefox-3.0. So when you type firefox at the terminal, or click on the Firefox shortcut that comes standard on the panel, you get 3.0.

Try typing firefox-3.5 in a terminal window and let us know what it does.

BTW, if you change the link to point to 3.5, the next update of 3.0 will reset it. That's bloody annoying. 
thanks,that worked, it is the shiretoko branding version though. but flash did work also. and it seems this version will auto update through update manager? it's just ashame the whole process is so troublesome and awkward. so i guess to have 3.5 seamlessly and properly integrated into ubuntu we will have to wait for 9.10 karmic and just use these workarounds until then?   
maybe i could make a 2nd firefox shortcut in the menu pointing too 3.5

---

### Post by gila_monster on 2009-08-08
> **dreemreeper said:**
> thanks,that worked, it is the shiretoko branding version though. but flash did work also. and it seems this version will auto update through update manager? it's just ashame the whole process is so troublesome and awkward. so i guess to have 3.5 seamlessly and properly integrated into ubuntu we will have to wait for 9.10 karmic and just use these workarounds until then?   
maybe i could make a 2nd firefox shortcut in the menu pointing too 3.5

Yeah, pretty much. I have a second shortcut set up for now. And yes, Flash is more than a bit of a wart.

Annoying, but in the grand scheme, not that bad. I was a pallbearer for a friend this morning, and my father-in-law broke his hip yesterday and had some rather interesting surgery this morning. "It could be worse, it could be raining...."

---

### Post by nanotube on 2009-08-08
Hi

the ubuntuzilla website now has a section in the faq specifically about getting plugins running on 64bit ubuntu using the 32bit mozilla build of firefox. give it a look. :)

[https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F](https://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#.5BFirefox.5D_What_happened_with_Flash_and_all_my_other_plugins.3F)

---

