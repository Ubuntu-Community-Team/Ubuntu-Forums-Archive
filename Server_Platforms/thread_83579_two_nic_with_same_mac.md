---
title: "two nic with same mac"
date: 2005-10-29
forum: Server Platforms
---

### Post by diebels on 2005-10-29
Lets say I configure two machines nic's with the same mac and ip, and put them on a switch.

Then i connect a third machine with different mac and ip, and ping the ip of the two other machines.

Do I get two replies?

Can I do this to clone a server for redundantcy?

---

### Post by adwait on 2005-10-29
I am no expert with networking.......but aren't two machines NOT allowed to have the same IP?

---

### Post by LordHunter317 on 2005-10-29
You will see terribly bad and more or less undefined behavior from this.  If it were just the same IPs, the boxen would go into a phase where they attempt to compensate, usually by screaming messages on the console and refusing to do any more networking.

But with the same MAC, I think you're goign to see totally random and unpredictable results.

---

### Post by lexor on 2005-10-29
On the MAC side of things, is it possible to give 2 cards the same MAC? Is the MAC not set by the hardware of the device and there is no way of changeing it?

The first 6 digits are the Manufacturers Code and the last 6 digits are the Model Code.

On the IP side you have 2 IPs shouting out..yes hello here I am that would cancel each other out would it not, even if the machine you ping from indeed even gets to any on of the 2.

---

### Post by LordHunter317 on 2005-10-29
[QUOTE=lexor]On the MAC side of things, is it possible to give 2 cards the same MAC?[/quote]Yes.

>  Is the MAC not set by the hardware of the device and there is no way of changeing it?Many cards support changing it.  Nearly all 802.11b devices do, for example.

Hell, some cards come from the manufacturer with the same MAC, they're not globally unique.

> On the IP side you have 2 IPs shouting out..yes hello here I am that would cancel each other out would it not,Nope.  Genearlly, both machines will attempt to respond until they become aware of each other, at which point they run an "evasion" procedure to correct for the problem, which usually consists of the steps I mentioned above.

---

### Post by lexor on 2005-10-29
Thanks for the info on that.

I had this problem a while ago with a cable modem from NTL a ISP in the UK. The way it was setup was that it only would accept to recgonise 1 MAC I was told it was 3 but the time it took to reboot the modem to get it to take another MAC into memory took hours sometimes even days.

So if I was wanting to put another machine on the modem, I would just take the NIC card out the machine it recgonised and put it in the other machine.

If I could change the MAC then I would have just done that. How would you go about changing a MAC if indeed your device supported it?

---

### Post by adwait on 2005-10-29
[http://en.wikipedia.org/wiki/MAC_address#Linux](http://en.wikipedia.org/wiki/MAC_address#Linux)

---

### Post by lexor on 2005-10-30
thanks that saves a lot of messing about.

---

### Post by diebels on 2005-11-02
Maybe something like this is a better idea:[http://www.cisco.com/univercd/cc/td/doc/product/iaabu/pix/pix_v3/failover.htm]("http://www.cisco.com/univercd/cc/td/doc/product/iaabu/pix/pix_v3/failover.htm")
If I have 2 nic's(or ip alaising) on each server, and configure an active and standby mode. Where in standby mode all connections to the shared ip network is dropped by iptables, or maybe just ifdown. Let the standby server monitor the active over a seperate network, and switch to active mode on the shared ip network if the currently active server goes down.

I want to do something like this on a ssh/web/mail/mysql server, so I need to clone data with rsync or something.

---

### Post by owdeuk on 2005-11-04
" Is the MAC not set by the hardware of the device and there is no way of changeing it?"

Yes it is. It carries a burned in address that part of it relates to an OUI code from the manufacturer, all unique. (This is how M$ ban people on xbox live for using a modded xbox).

All's this relates to is "spoofing" the MAC, ie changing it at OS level. So if you flatten your PC, the MAC will revert back to the orignal burned in address.

---

### Post by LordHunter317 on 2005-11-04
[QUOTE=owdeuk]Yes it is. It carries a burned in address that part of it relates to an OUI code from the manufacturer, all unique.[/quote]No, they're not.  I have two NICs on the shelf with matching MACs that prove you wrong.

They're *supposed* to be.  That's not reality, though.

---

### Post by owdeuk on 2005-11-07
"No, they're not. I have two NICs on the shelf with matching MACs that prove you wrong.

They're supposed to be. That's not reality, though."

[B]*Removed errenously negative post* 
Stay on target, Stay on target...Luke..Luke!!!!.....your targeting computer is off. KB[/B]

---

### Post by LordHunter317 on 2005-11-07
Well, I'm sorry you can't accept the fact you're parading around a common misconception.  Run a big enough network or see enough NICs, and you will see an eventual duplicated MAC.

---

### Post by owdeuk on 2005-11-07
I love know it all's like you.....Sarcastic, arrogant and completly obnoxious. Glad I don't come across idiots like you in my life. Funny how you just manage to come across idiot's like you on the net. Never face to face.

I've never seen a duped MAC on our corporate network and I'm talking about 1,000 clients all in all. (Not saying they don't exist). But if you looked at my post it said the OUI was unique.

As I said before....

"Go back to school and learn some manners"

and please never reply to my posts in this way!

---

### Post by FLeiXiuS on 2005-11-07
[QUOTE=owdeuk]I love know it all's like you.....Sarcastic, arrogant and completly obnoxious. Glad I don't come across idiots like you in my life. Funny how you just manage to come across idiot's like you on the net. Never face to face.

I've never seen a duped MAC on our corporate network and I'm talking about 1,000 clients all in all. (Not saying they don't exist). But if you looked at my post it said the OUI was unique.

As I said before....

"Go back to school and learn some manners"

and please never reply to my posts in this way![/QUOTE]
It's always possible to have a duplicate MAC on a network.  It's not a problem unless your doing a lot of switching.  Users easily become aware that you can change your whole MAC in general, including the OUI.  I work for the Government and not one and I mean one of our machines are defaulted to the original MAC.  Simple because the OUI is an IEEE standard meaning you can see exactly who makes that specific product.  This is not my ideal of security.  

This goes to show that USERS are not IDIOTS we are mearly different in experience. 

And for the record they don't BAN you by our MAC address on XBOX.  Take a look at the EEPROM.  The EEPROM carries a unique character ID which will be used to determine each Xbox.  This is also the mechanism that LOCK'S / UNLOCKS the hard drive.  If your an xbox guru, then you would have flashed he EEPROM or removed it to disable the hard drive locks throughout the life of your xbox and to remove your unique ID.

---

### Post by LordHunter317 on 2005-11-07
[QUOTE=owdeuk]Sarcastic, arrogant and completly obnoxious.[/quote]I was none of the above to you.

> . But if you looked at my post it said the OUI was unique.No, it's ambigious to which portion of the subject that the modifying phrase, "all unique," refers to.

> "Go back to school and learn some manners":rolleyes: Go back to school and learn some English, and some manners.

If the post had really referred to the OUI, as you had said, why didn't you post, "Well, I was talking about the OUI," **originally**, instead of attacking my person?  Had you done so, I would replied, "You're right, I misunderstood what you wrote," and that would have been the end of that.

Instead, you willingly chose to make an attack on me for correcting your vauge and quite possibly incorrect statement.  So who's the one without any manners?

> and please never reply to my posts in this way!And you in turn.  You'll be shocked to find you have no moral standing from which to make your attack on me.  By doing as you have done, any statment of this nature loses it's weight.

---

### Post by owdeuk on 2005-11-07
"And for the record they don't BAN you by our MAC address on XBOX. Take a look at the EEPROM. The EEPROM carries a unique character ID which will be used to determine each Xbox. This is also the mechanism that LOCK'S / UNLOCKS the hard drive. If your an xbox guru, then you would have flashed he EEPROM or removed it to disable the hard drive locks throughout the life of your xbox and to remove your unique ID."

Never knew that. I used slayers install disk so I suppose that did all the EEPROM flashing for me.

LordHunter317. 

Quotes like "I have two NICs on the shelf with matching MACs that prove you wrong." I'm sorry but comments directed that way really do my head in. Specially PROVE YOU WRONG, Jeeze.

Just think twice before you type and I'll do the same.

---

### Post by LordHunter317 on 2005-11-07
:rolleyes:  You're the one who started this mess, not me.  Trying being civil and reasonably intelligent (meaning, willing to engage in a dialogoue without assuming a correction of something you said means I think you're stupid or any other such nonsense) with me and you'll find I'm quite civil.  Don't act civil and well, you see the result.

---

### Post by owdeuk on 2005-11-07
You just don't know when to give it a rest do you?

Ah well flame away....and for the record you are anything but civil. I find you most arrogant with comments like "I have two NICs on the shelf with matching MACs that prove you wrong.". 

Why not think, and answer things another way.

---

### Post by LordHunter317 on 2005-11-07
Well, how else do you want me to point out the fact I have a pair of NICs on my  shelf that have matching MACs?

Once again, your post is accusing me of the fault, when you're the one who started the personal attacks, not I.

---

### Post by owdeuk on 2005-11-07
Just think it could of been worded better. Probably best to use smilies as it's get's the point across better and saves any offence. When someone comes out with a comment to "prove you wrong", it's does appear to be very confrontational. ;)

---

