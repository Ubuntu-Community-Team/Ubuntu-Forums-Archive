---
title: "Using DynDNS to recover stolen laptop"
date: 2007-05-26
forum: Server Platforms
---

### Post by PurplePenguin on 2007-05-26
I came across an [interesting article/tutorial]("http://www.arsgeek.com/?p=1612") this morning and thought I'd share it.  It's amazing how people can take one tool and use it to do something that nobody had originally intended.

Basically, the idea is that if you have a free DynDNS account and install ddclient to keep it updating its address, you can ping and traceroute your way to your computer if it's ever stolen and used on another network (and hasn't had its drive removed or formatted).

Even if that doesn't work out for you, you could always use this method to ssh into your computer and delete important information and documents.

It's very, very far from perfect, but I thought I'd share it anyway. :D  I had a rough time trying to figure out which subforum this should be in, so if the mods want to toss it somewhere else, go for it!

---

### Post by etcpool on 2007-05-26
Ummmm...

---

### Post by MJN on 2007-05-26
I've done this as you've not really got anything to lose. Furthermore, given my laptop has WiFi which automatically connects there is a chance a thief might well inadvertently connect. Of course, it's far from foolproof and carries no guarantees given the multitude of options a thief has but I can't see any downsides. My machine runs Kubuntu and Vista so I've put dynamic clients on them both.

Rather than me sitting around querying the DNS to see of the laptop 'turns up' I wrote a small script to check it every few seconds - it compares the result with the last known address and, if it changes, sends me an SMS text to alert me of the fact (it uses mercurySMS for this bit).

Mathew

---

### Post by PurplePenguin on 2007-05-26
> **etcpool said:**
> Ummmm...

Yes? :)

---

### Post by PurplePenguin on 2007-05-26
> **MJN said:**
> I've done this as you've not really got anything to lose. Furthermore, given my laptop has WiFi which automatically connects there is a chance a thief might well inadvertently connect. Of course, it's far from foolproof and carries no guarantees given the multitude of options a thief has but I can't see any downsides. My machine runs Kubuntu and Vista so I've put dynamic clients on them both.

Rather than me sitting around querying the DNS to see of the laptop 'turns up' I wrote a small script to check it every few seconds - it compares the result with the last known address and, if it changes, sends me an SMS text to alert me of the fact (it uses mercurySMS for this bit).

Mathew

That's a fantastic idea!  I'm sure that thieves would catch on to this sooner or later (and just sacrifice the hard drives before booting even once), but as long as it saves a few laptops, it'd be worth it.

I was thinking of this script idea right after posting my comment, but disregarded it since I don't have any experience making scripts like this.  Is there any chance that you'd share your script (that is, minus your personalized info)?  A lot of people might enjoy modifying it for themselves.

---

### Post by Cows on 2007-05-26
Very smart idea MjN. I haven't used DynDNS alot since I used NoIP on windows and a bit on linux. But just for this I might switch to DynDNS for when I get a laptop :).

---

### Post by MrHorus on 2007-05-27
> **PurplePenguin said:**
> That's a fantastic idea!  I'm sure that thieves would catch on to this sooner or later (and just sacrifice the hard drives before booting even once), but as long as it saves a few laptops, it'd be worth it.

Dunno likes.

It's always struck me that the kinda of people that would snatch and grab a laptop from a coffee shop would be oppertunist thieves i.e. homeless, drug addicts etc etc and the person who eventually ends up with the laptop after buying it from someone in a pub or a car boot sale or whatever, might not actually be the thief (handling stolen goods is a different gig entirely).

The other problem would be proving ownership of your laptop and then actually explaining to a police officer and a judge/sheriff exactly what an IP address is and how and why they should serve a warrant on the ISP for the customer details - I suspect that would be your greatest problem somehow :)

---

### Post by MJN on 2007-05-27
Sure, there are many many reasons why it would be of no use whatsoever (particularly with regards to what you do once you have an IP address![1]) however given there aren't any drawbacks to implementing it, yet a slight possibility of it coming up trumps, then why not? I'd much rather find that it either works or doesn't by putting it into practice than pondering the theory. It's not like I'm implementing this strategy at the expense of any other security.

> **PurplePenguin said:**
> Is there any chance that you'd share your script (that is, minus your personalized info)?  A lot of people might enjoy modifying it for themselves.

Sure, here it is:

```

#!/bin/sh
# Script to monitor the DNS for the laptop (and any other devices) for changes due to the
# dynamically updated DNS. Intended to be run if the laptop gets stolen in the hope that
# it will be connected to the Internet whereupon the dynamic update client will trigger
# and record the new IP address in the DNS. This IP can then hopefully be used to track the
# location of the laptop. Also provides reverse DNS and tracepath(route) outputs to aid
# initial location identification.
# Written by Mathew Newton
# v0.2 08/04/07

# Global variables
host_to_monitor="your laptop FQDN"
existing_laptop_ip=`host -t A -W 10 $host_to_monitor | grep "has address" |cut -f4 -d" "`
huntlaptop_log=./huntlaptop_log

echo "Checking every 60s to see if $host_to_monitor points to somewhere other than $existing_laptop_ip ..." | tee -a $huntlaptop_log
echo "Output recorded in $huntlaptop_log" | tee -a $huntlaptop_log

while [ -d / ]; do
      latest_ip=`host -t A -W 10 $host_to_monitor | grep "has address" | cut -f4 -d" "`

      echo "At `date` $host_to_monitor pointed to $latest_ip" |tee -a $huntlaptop_log

      #insert error checking for non-IP results?

      if [ "$latest_ip" != $existing_laptop_ip ] ; then
         echo -e "\nALERT! IP ADDRESS OF $host_to_monitor HAS CHANGED !!!" |tee -a $huntlaptop_log
         echo "IP ADDRESS OF $host_to_monitor IS NOW $latest_ip" |tee -a $huntlaptop_log
         echo "REVERSE PTR of $latest_ip is `host -t PTR -W 10 $latest_ip | cut -f5 -d" "`" |tee -a $huntlaptop_log
         echo -e "PATH TO $host_to_monitor IS: \n`tracepath $latest_ip`\n" |tee -a $huntlapop_log
         # Send SMS alert (optional)
         # ./mercurysms <mercury config stripped> -m="IP address of $host_to_monitor has changed to $latest_ip!"
      fi

      existing_laptop_ip=$latest_ip
sleep 5s
done

```So, it starts by checking the current (existing) IP address last known to be assigned to the laptop and outputs it to screen and the log. It then performs a DNS lookup for the laptop and compares the result with the existing address - if no change it reports as such. This loops every 5 seconds. If the address does change this is output and alerted to me via SMS.

Mathew

[1] In addition to the more conventional avenues that one might explore once an IP is known (e.g. persuing the ISP, involving the police etc) there are some other options available... For example, whilst many laptops no doubt simply get exchanged locally I bet there's a whole load that end up on eBay. If you spotted a similar machine to your own on eBay you could get into an innocent conversation with the seller, preferably by e-mail, and try and marry up the IP addresses. If you've got a match, well, you're sorted as you'd easily be able to get the seller's address and/or any other useful information. Aternatively perhaps you could search high-and-low on the web (or Usenet etc) for the address and seek contact that way. Of course, lots of 'ifs' but then if I lost my laptop I'd just go out and buy a new one and treat this 'hunt' as merely an exercise in some lateral thinking...

---

### Post by leexgx on 2007-05-27
As the user who stole it properly did not know that Linux was on it the first thing he would of properly of done after failing to logon put an XP disk in and install windows

that option above that users have posted is most likey have an result of nothing as by the time the user plugs the laptop in it have windows installed 

This tactic properly more useful for windows users, but the same result mite happen any way (format and reinstall) unless its not passworded theen maybe not probly work very well

other options (more likey to work)

Built in GPS with 15 min call back of last known location then the police not needed just 15 or more friends (and some paint) to Retrive the laptop 
you could allso have an mobile phone with GPS running java to SMS the location of it self when not been prodded (press an button) after 30 mins

or

&#8220;Laptop has Hardware base security is on this laptop if stolen it will be useless please drop this laptop to the local police station&#8221;

Have that stuck onto laptop or the laptop Bag it self

---

### Post by PurplePenguin on 2007-05-27
Well, DynDNS can be used with Windows, as well as linux.  :)  Hmm... come to think of it, maybe Mac laptop users will get the most benefit from this kind of thing...

As has been said before, it can't hurt to try, right?  And as long as the guy tries booting the computer once (and is near a wireless connection to the net), a script like the one posted might just give the laptop's owner a clue of the general area that the laptop is in.  Especially if he gets distracted by the unfamiliar, yet incredibly intuitive new OS he's staring at. :D

Maybe we might be converting a few thieves from Windows to Ubuntu after they try using their stolen laptops... ;) (/jk)

---

### Post by ninocass on 2007-05-27
With a BIOS and Hardrive password theyre not gonna turn my laptop on, oh and full disk encryption theyre not going to use the harddrive in anything else either :)

A very nice idea none the less, it would be cool if a company was set up that had a relationship with the ISP's in that they could discolse the geographic location of the stolen laptopand maybe pass this information to the police

---

### Post by MJN on 2007-05-27
> **leexgx said:**
> As the user who stole it properly did not know that Linux was on it the first thing he would of properly of done after failing to logon put an XP disk in and install windows

That script is for running on my server - the laptop merely has a standard dynamic DNS update client running. In this case, as a dual boot laptop, it's Zoneclient on Kubuntu and zedyn on Vista (which, dare I say it, is the default boot!). You can probably guess that ZoneEdit is my DNS provider.

> that option above that users have posted is most likey have an result of nothing as by the time the user plugs the laptop in it have windows installed 'Most likely' is not 'definite' and hence that chance is still remaining, and that's what I'm aiming for here (although as above it's also working in Windows which, as you say, has an arguably better chance of working). Either way, why not? I must say if my laptop does ever get nicked part of me will actually be quite excited waiting to see if it calls home!

> other options (more likey to work)

Built in GPS with 15 min call back of last known location then the police not needed just 15 or more friends (and some paint) to Retrive the laptop 
you could allso have an mobile phone with GPS running java to SMS the location of it self when not been prodded (press an button) after 30 mins

or

&#8220;Laptop has Hardware base security is on this laptop if stolen it will be useless please drop this laptop to the local police station&#8221;

Have that stuck onto laptop or the laptop Bag it selfYeah, all valid ideas (apart from perhaps the last one for recovery - it'll still get nicked). But then they all cost and given my laptop has a brand-new value of only £250 it's really not worth it... for me at least. I've probably spent more time discussing it here than it took to implement! ;)

Mathew

P.S. I'm intrigued as to what the '*and some paint*' bit meant!

---

### Post by PurplePenguin on 2007-05-28
> **MJN said:**
> I must say if my laptop does ever get nicked part of me will actually be quite excited waiting to see if it calls home!

:biggrin:  Funny... in a way, I guess that's sort of true.  You can find a silver lining for anything!

---

