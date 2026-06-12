---
title: "Wireless Rant"
date: 2006-10-31
forum: The Cafe
---

### Post by jml on 2006-10-31
I hope that this is the appropriate place to post this observation.  If I am in error, my sincere apologies.  I have been using Linux in one form or another since 1999.  While I can't call myself a newbie any more, I am far from an expert.  

Linux in general and Ubuntu in particular have come a long way in becoming user friendly, powerful and useful.  In my opinion,  the one thing that still holds most Linux distros back is wireless networking.  In the USA, this year was the first year that laptop sales outpaced desktop sales.  People who use laptops buy them in part for their portability.  A laptop without network connectivity, while useful, is not the ideal.  Images of people sitting on their deck, surfing the net, answering their e-mails wirelessly are responsible for a lot of laptop sales. 

This is one area, Linux developers really need give attention to, (I unfortunately am not a programmer, so I cannot contribute to this effort.)  Just a superficial review of all the discussion on wireless networking, the problems, the intricate solutions highlights what I am saying.  Until it is as easy to set up wireless networking in Linux as it is in Windows and Mac OS X, Linux will never gain a strong foot hold on the laptop market.  I realize wireless is a much more complicated problem to solve in Linux, ( propritary drivers, dozens of hardware options, hundreds of distros,) the mind boggles.  None the less, until a laptop user's experience can be improved, I fear that Linux will make little headway in this growing segment of the PC market.

Just my two cents worth.

Joe

---

### Post by IYY on 2006-10-31
I've never had any problems with wireless on my laptop, or either of my two desktops. But of course, I made sure I was buying a compatible card.

---

### Post by djsroknrol on 2006-10-31
I didn't have a problem with my wireless card either...It's a Linksys WMP54G, and all I had to do was enable it in:

System>Administration>Networking....

Simple as that....:p

---

### Post by aysiu on 2006-10-31
Buy a [System 76 laptop](http://www.system76.com).

---

### Post by prizrak on 2006-10-31
Few things to consider.
1) It is quite easy to wireless in Ubuntu, if network manager is installed it's so easy it's rediculous. You even get VPN connectivity through it. The only issue is that it is not default as of Edgy (perhaps Feisty?) and asks for a password on each reboot to connect to a secured network (it's not the passphrase but still annoying). The hardware has to be supported though, however as Centrino is really the best laptop platform it shouldn't be an issue.

2) OS X is a huge pain to set wireless up. Someone had written up their experience with trying to set up wireless with the built in utility with anything other than an airport router is close to impossible (esp since the error msg are not helpful). 

Windows built in utility is retarded, it connects to networks based on SSID so that when I'm at the laundromat (mine has wi-fi) that has an SSID "linksys" and connect to it. When I get home it connects to another network with the same SSID. Despite a really low signal strength, it also sees more than one "linksys" network when I'm at the laundry and has 1mbps and it hops to it from time to time instead of the closer one. The only way I solved it is by actually changing the SSID on the laundromat's router (yes they had a default pswd). Network manager on Ubuntu actually looks at signal strength in addition to the SSID so it automatically hopes on my home network after the laundry. 

3) Everything always works in a preinstalled computer. A System76 laptop will have 100% functional wireless out of the box. Try installing Windows on that and see how much pain hunting down the drivers will be if you don't have a restore CD. Linux won't make headway into laptops until Dell/HP start selling Linux laptops to regular people and organizations switch their desktops/laptops to it.

---

### Post by aprice2704 on 2006-10-31
I have to concur with JML. My own experiences with trying to get my Dell connected via wireless have been quite painful, though finally successful to some degree.

People who say "well you should just buy xxx" or "make sure your card is yyyy" are missing the point imo.

Wireless in linux is getting better but it's not remotely as polished as XP etc. out of the box. It needs to be.

I'm just describing outcomes.

:)

---

### Post by David Mulligan on 2006-10-31
> **aprice2704 said:**
> 
People who say "well you should just buy xxx" or "make sure your card is yyyy" are missing the point imo.

Wireless in linux is getting better but it's not remotely as polished as XP etc. out of the box. It needs to be.

You forget that you vote with your currency.  You buy a laptop made by a company that does not support linux and/or uses parts by like companies.  So when you buy equipment from a company that does not support linux you are telling them that linux support is not important.

If companies like broadcom, a very popular wifi chipset maker, would release specifications to linux developers then we would have had drivers years ago.  However Broadcom and many others will not release any information at all.  Nor do they release binary drivers themselves.  What can the linux development community do?

---

### Post by ZylGadis on 2006-10-31
> **jml said:**
> This is one area, Linux developers really need give attention to, (I unfortunately am not a programmer, so I cannot contribute to this effort.)

Completely wrong. This is a field GNU/Linux developers can do very little about, because of closed hardware specifications. If you want to help, do send a similar thing to your laptop manufacturer or, even better, to your wireless card manufacturer. Or you can indeed buy hardware with open specifications (and as a result is sure to have open-source drivers), thus supporting the respective manufacturer. I disapprove of phrases like "vote with your wallet" because such phrases are tightly coupled with the whole mentality of crass commercialism most of us have, but it works.

---

### Post by aysiu on 2006-10-31
> **aprice2704 said:**
> 
People who say "well you should just buy xxx" or "make sure your card is yyyy" are missing the point imo.

Wireless in linux is getting better but it's not remotely as polished as XP etc. out of the box. It needs to be.

I'm just describing outcomes.

:) You can't **get** those outcomes unless you tell manufacturers Linux support is essential to making money.

If you buy products from someone who doesn't support Linux and then tell them, "Can you support Linux?" do you think they'll care?

Buy from their competitors who do support Linux, and you'll get the outcomes you want soon enough. Money talks.

---

### Post by Skia_42 on 2006-10-31
Liux is not for anyone. And can understand where your rant is coming from. It took me a week to get my internal intel 345g card working, it was a simple matter of being patient. Now I am pleased that linux can handle nearly all wirelss cards EVEN THOUGH WIRELESS CARD MAKERS OFFER NO SUPPORT FOR THE LINUX SYSTEM. I find that pretty amazing...

---

### Post by prizrak on 2006-10-31
> **aprice2704 said:**
> I have to concur with JML. My own experiences with trying to get my Dell connected via wireless have been quite painful, though finally successful to some degree.

People who say "well you should just buy xxx" or "make sure your card is yyyy" are missing the point imo.

Wireless in linux is getting better but it's not remotely as polished as XP etc. out of the box. It needs to be.

I'm just describing outcomes.

:)

XP does not work with any wireless cards out of the box, it requires driver installation. Linux on the other hand has Orinoko, Atheros and Intel support (maybe others I don't know about) built right into the kernel. That means that as soon as you install Linux you only need to put your connection details in (depending on default application to manage it of course). In case your card does not work with Linux there is ndiswrapper that will allow you to install the Windows drivers. Can't see a whole lot of difference.

---

### Post by fuscia on 2006-10-31
there's a lot bigger difference between linux and windows than there is between one wireless and another. just get a wireless that works with linux.

---

### Post by Bezmotivnik on 2006-11-01
> **ZylGadis said:**
> Completely wrong. This is a field GNU/Linux developers can do very little about, because of closed hardware specifications. 
With respect, *baloney*.

Linux drivers have been out for most of these devices for **years**.  They have just been poorly integrated into Linux distributions by Linux developers.

---

### Post by prizrak on 2006-11-01
> **Bezmotivnik said:**
> With respect, *baloney*.

Linux drivers have been out for most of these devices for **years**.  They have just been poorly integrated into Linux distributions by Linux developers.

Well that really depends on the drivers, if their binary then unless it is done the same way nVidia does their drivers it would be illegal under the terms of GPL to integrate them.

---

### Post by jml on 2006-11-01
Thanks for all of your thoughts.  I can't disagree with anything written here.  It seems that everyone's "milage may vary".  The poster who suggested that we vote with our wallet is absolutely right.  I plan to buy a laptop from system 76 in the near future.  They sell laptops with Ubuntu installed and configured for use out of the box.  

My problem with wireless is really not only Linux's fault.  I require/want to use WPA-PSK encryption on my home network (WEP had been cracked by someone near me)  The fact that out of the box support for that is rare is a major part of my problem.  According to System 76 customer support, they set up WPA encryption as part of their configuration.

When I referred to ease of use in Windows XP and OS X, it was a bit of an unfair comparison.  I was referring to the fact that when you buy a laptop with either Windows XP or OS X installed nowadays, the computer already comes with a wireless card built in and configured to run with the OS.  My point was that compared to this ease of use, Linux is at a disadvantage.

Thanks for all of your comments.  And thanks for the absence of "flames"

Joe

---

### Post by spd106 on 2006-11-01
Does anyone know what progress is being made on incorporating Wifi Protected Setup into distros? I've read that linux is supported by Devicescape [http://www.linuxdevices.com/news/NS4665009721.html](http://www.linuxdevices.com/news/NS4665009721.html) But that was back in August, so what's the current state? 

I realise that we probably won't see products with this for a while yet and there will always be legacy devices out there, including all those laptops. WPS won't solve the driver problem completely but it should help most users configuration issues. Which is just as important since it shouldn't be necessary to need the level of knowledge that you do now.

In particular we can't really afford to fall too far behind Microsoft in implementing this new feature.

---

### Post by Bezmotivnik on 2006-11-01
> **prizrak said:**
> Well that really depends on the drivers, if their binary then unless it is done the same way nVidia does their drivers it would be illegal under the terms of GPL to integrate them.
They're out there, they're open to "the community," they're integrated into the kernels and distros, including Ubuntu -- but minimally, badly and with erratic results.

That's the problem.  None of the usual Linux excuses hold water here.

---

### Post by prizrak on 2006-11-01
> **Bezmotivnik said:**
> They're out there, they're open to "the community," they're integrated into the kernels and distros, including Ubuntu -- but minimally, badly and with erratic results.

That's the problem.  None of the usual Linux excuses hold water here.

The only possible excuse I can think of is not having the time/resources to test them. If they are obscure enough it would be hard to get hands on them. That's a guess of course.

---

### Post by jml on 2006-11-01
So far I have not found any distros that support WPS.  

The part that I find confusing is WPA support.  So far, I have found three distros that literally support WPA-PSK encryption out of the box and with user friendly front ends, SUSE 10.x, Mandriva 2006 (and I assume 2007) and Kanotix 2005-4.  If these three distros can do it, why not others?  Especially Ubuntu.  I really like Ubuntu and literally the only thing keeping me from using it on all of my laptops is easy WPA support.  (I must be slow, because I have never been able to get the solutions posted on the wireless forums and Wiki to work for me.)

Again, thanks for the insightful comments, I enjoy reading them.

Joe

---

### Post by prizrak on 2006-11-01
> **jml said:**
> So far I have not found any distros that support WPS.  

The part that I find confusing is WPA support.  So far, I have found three distros that literally support WPA-PSK encryption out of the box and with user friendly front ends, SUSE 10.x, Mandriva 2006 (and I assume 2007) and Kanotix 2005-4.  If these three distros can do it, why not others?  Especially Ubuntu.  I really like Ubuntu and literally the only thing keeping me from using it on all of my laptops is easy WPA support.  (I must be slow, because I have never been able to get the solutions posted on the wireless forums and Wiki to work for me.)

Again, thanks for the insightful comments, I enjoy reading them.

Joe

Install network-manager and look for guides on how to make it work. It's still a beta so some of the stuff is a bit hackish. WPA-PSK works just fine for me with it.

---

### Post by jml on 2006-11-03
thanks for the idea.

Joe

---

### Post by awakatanka on 2006-11-03
One tool work with wep the other one sometimes work with wpa but never had a tool that could do both.

I move a lot and need a tool that can easly access the network. Sometimes its wep the other time its wpa. I don't have time to edit config files. i just need something like wireless zero from ms. Click on the network broadcast and enter key. The tool just find out if it uses wep our wpa and there encryptiontypes.

My rt2500 is supported but i have to edit a lot to get it to work on different networks. in MS i just click and enter key. I need that and lot of laptop users need that. 

Networkmanager and kwlan look promissing but don't work for me.

---

### Post by wezlo on 2006-11-11
> **awakatanka said:**
> Networkmanager and kwlan look promissing but don't work for me.
It didnt' for me either - then I found a package for a newer version on the kde-applications site and it did work, very nicely, with my rt2500 wireless.  Here's the link to the kubuntu edgy package:

[Wlan for Kubuntu Edgy.]("http://kde-apps.org/content/download.php?content=37041&id=2&PHPSESSID=8c8ea9d5abedd342b8762528e80f3742")

I set up wpa_supplicant to use the wext driver and it worked fine.

---

