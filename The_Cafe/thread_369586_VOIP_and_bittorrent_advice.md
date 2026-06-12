---
title: "VOIP and bittorrent advice"
date: 2007-02-24
forum: The Cafe
---

### Post by Solicitous on 2007-02-24
Hi All,

I'm just seeking some advice from fellow forum members.  My situation is this;
I'm going to put in a headless box for my file backups and bittorrent downloads.  I'm thinking of using Dapper and not Edgy only for the LTS.  I was thinking that while I was at it I would also attach my usb voip phone.

So my questions are;

What do you think would be a good torrent client?  I'm thinking more along the lines of being able to administer it via a browser to save logging in with vnc or ssh, perhaps also with the ability to schedule start and stop times for the client (so it will download automatically overnight say) but then again cron can fix this if it's not an option.

And secondly, I'm currently trying out VOIP at home to see if it is a viable option for home use.  The usb phone I have is a fairly standard I believe, uses the yealink driver (or perhaps that is the chipset in it, unsure :) ), and I currently use XtenSoftPhone on my laptop for making the calls.  Only issue I have with the software/phone working together is the hangup button on the phone actually enables/disables the mute function.  Under Windows it works flawlessly but using that solution isn't a preferred option.  So what other options would you suggest I try for using my voip phone?  Just remember, it will be a headless box.

I am also aware of the adapter to attach to ordinary phones and then into the broadband, but they cost around the $120AUS and I'm trying to avoid spending that kind of money at the moment because I'm still testing the viability of voip for here at home.

Any tips/advice would be greatly appreciated.

TIA

Solicitous

EDIT:  I must also mention, I am requiring with the voip the 'voip to phone' ability.  And yes, I do currently have a provider and setup.

---

### Post by cowlip on 2007-02-24
You can probably run the utorrent webui beta in WINE for very low resource usage.  Or the memory hog Azureus has tons of plugins as well as a webui

If you have DD-WRT for the Linksys wrt54g (v4 or earlier off ebay or the wrt54gl) or some other routers, you can specify QoS times in your router.

[http://www.dd-wrt.com/wiki/index.php/Supported_Devices](http://www.dd-wrt.com/wiki/index.php/Supported_Devices)
[http://en.wikipedia.org/wiki/Wrt54g](http://en.wikipedia.org/wiki/Wrt54g)

---

### Post by Solicitous on 2007-02-25
I think I will try out Azureus with a webui plugin.  Thanks for pointing that out to me.

With the VOIP, I'm looking more for suggestions of softphones that I could try out.  I currently have a usb phone but am having a few little issues with the buttons not doing specifically what they're meant to do eg; Hangup actually enables/disables the mute function on my current softphone.

---

