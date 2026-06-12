---
title: "Is my router dying or something?"
date: 2007-04-08
forum: The Cafe
---

### Post by TravisNewman on 2007-04-08
I don't get this. Recently some sites have been crapping out on me, that haven't before. This happens on all the PC's on our home network.

I was just testing sites at random here.
linuxforclinics.org throws back a bunch of mysql warnings
modfree.org doesn't load at all (shows sql errors)
any SMF forum with reverse DNS lookup enabled takes at least 30 seconds to load any page.
some things on the Angry Nintendo Nerd website will not load properly.

BUT

At work, all these sites work properly (haven't tested all of them at work)
If I connect through a proxy (i.e. myspaceproxy.com) or Tor they work fine.
If I connect the cable modem directly to my computer (bypass the router entirely) all the sites work fine.

One thing I did notice, my WAN ip is entirely different when connected directly to the cable modem and when connecting through the router (in my testing, it gave me the exact same IP each time I was using the router, and a different IP from the router when I used the cable modem). 

So here are my two guesses:
My router is messed up.
Something at the ISP is messed up, maybe for the random IP they've assigned me that I keep getting when I connect with the router.

Can anyone share some expertise here? I'm stumped.

EDIT: I should have mentioned, I've restored the factory settings on the router.

---

### Post by futz on 2007-04-09
If there's ever any question about your router or your modem, just reboot them by power-cycling them. Unplug the power, wait 20 seconds or so, plug back in, wait for them to reboot and get going again.

Most routers have a reset button too, which you can push with a pen or other small pointy implement. That will do the trick without unplugging power.

Can't hurt to try it.

Firmware updates for routers can sometimes solve problems.

> One thing I did notice, my WAN ip is entirely different when connected directly to the cable modem and when connecting through the router (in my testing, it gave me the exact same IP each time I was using the router, and a different IP from the router when I used the cable modem).
When you're plugged directly to the modem, you get an IP served to you by the ISP's DHCP server.

When you plug into the router, you get an IP served to you by the router's DHCP. The router gets the one from your ISP.

---

### Post by TravisNewman on 2007-04-09
> **futz said:**
> If there's ever any question about your router or your modem, just reboot them by power-cycling them. Unplug the power, wait 20 seconds or so, plug back in, wait for them to reboot and get going again.
Did all that

> Most routers have a reset button too, which you can push with a pen or other small pointy implement. That will do the trick without unplugging power.

Can't hurt to try it.
Yeah, the reset button is a factory settings reset button, which I've done.

> Firmware updates for routers can sometimes solve problems.
Done that too :)


> When you're plugged directly to the modem, you get an IP served to you by the ISP's DHCP server.

When you plug into the router, you get an IP served to you by the router's DHCP. The router gets the one from your ISP.
I know, I was referring to the IP address that the router got, not the one that my PC got. I know my way around networking, but this one is stumping me.

---

### Post by LookTJ on 2007-04-09
What kind of router you got?

---

### Post by TravisNewman on 2007-04-09
Network Everywhere nr041

Piece of crap but it's served me well for a few years.

EDIT: I just tried DOWNGRADING the firmware, because... why not? That didn't help either.

---

### Post by futz on 2007-04-09
> **panickedthumb said:**
> I know, I was referring to the IP address that the router got, not the one that my PC got. I know my way around networking, but this one is stumping me.
Just getting the basics out of the way, in case you were a newb. So you get a different IP depending on which device asks for it? Router gets one range and computer gets a different range? That's odd, isn't it?

---

### Post by TravisNewman on 2007-04-09
> **futz said:**
> Just getting the basics out of the way, in case you were a newb. So you get a different IP depending on which device asks for it? Router gets one range and computer gets a different range? That's odd, isn't it?
Not only a different range, a different specific IP. For example, every time I connected with the router the IP was 1.1.1.1, every time I connected straight to the cable modem it was 2.2.2.2

Obviously not the same IP's as I was getting, but it was significantly different. Not even near the same subnet, or even the same network. The first octet was different by 10.

And yes, that is very odd.

---

### Post by LookTJ on 2007-04-09
Have you tried viewing the page on a different pc?

---

### Post by TravisNewman on 2007-04-09
> **Taylor said:**
> Have you tried viewing the page on a different pc?
yes, as I said in the first post, it's the same no matter which PC on the network I use.

---

### Post by LookTJ on 2007-04-09
I'm thinking it's a dns problem that router has setup to...

hmm... try making your router use opendns's dns servers

if that fails...

---

### Post by TravisNewman on 2007-04-09
Yep, I've tried that too :)

---

### Post by LookTJ on 2007-04-09
Question....Does it show wrong on both Linux and Windows?

---

### Post by TravisNewman on 2007-04-09
yep.

---

### Post by LookTJ on 2007-04-09
Question 2: Did you call both your router's manufacture and your ISP about the problem?

---

### Post by TravisNewman on 2007-04-09
No, I haven't yet. My ISP's tech support has never impressed me one bit. At work I'm on the phone with equipment manufacturers and software companies for about 3 hours a day, I've lost faith in them to an extent ;)

---

### Post by LookTJ on 2007-04-09
I hope you don't mind...I have added you on my jabber because ubuntuforums is running majorly slow...

---

### Post by TravisNewman on 2007-04-09
that's fine, I won't be getting on for a while though.

---

### Post by LookTJ on 2007-04-09
I have narrowed down all the possibilities I could think...try accessing the sites by their ip if possible also.

---

### Post by TravisNewman on 2007-04-09
At this point I'm thinking of buying a new router... I would like to have wireless, and one port on this one's built in switch is fubar anyway.

So if any of you have any ideas about how to fix this, now's the time to share :)

---

### Post by Big Dave on 2007-04-09
> **panickedthumb said:**
> I was just testing sites at random here.
linuxforclinics.org throws back a bunch of mysql warnings
modfree.org doesn't load at all (shows sql errors)

The fact those two sites aren't working is very odd. (I'm an administrator on both sites, by the way.)

They are both hosted on the same server, so there may be a server problem. If you encounter the error again, could you please PM me any details of the problems you might be having? Also, on the linuxforclinics.org site, is it the forum that isn't working, or the whole site? The rest of the site is powered by Joomla, but the forums are SMF.

I'll get in touch with the owner of the server and see if there could be a problem there.

Thanks.

---

### Post by TravisNewman on 2007-04-09
It's not a server problem, it's happening on my own webserver too. But only when I'm using the router, connecting directly works fine. 

And it's not just those sites, there are many, many more.

---

### Post by charlie85254 on 2007-04-09
> **panickedthumb said:**
> It's not a server problem, it's happening on my own webserver too. But only when I'm using the router, connecting directly works fine. 

And it's not just those sites, there are many, many more.I'm sorry your having a problem...but thank God it's not the server!  I was quite worried there for a few minutes.

---

### Post by OffHand on 2007-04-09
If it works properly without your router I can only come to one conclusion... get rid of it.

---

### Post by altaaa on 2007-04-09
If your router supports MAC spoofing, you could try enter your PC's MAC address in the router. See if your router then gets the IP address you would get on your PC.

---

### Post by TravisNewman on 2007-04-09
> **altaaa said:**
> If your router supports MAC spoofing, you could try enter your PC's MAC address in the router. See if your router then gets the IP address you would get on your PC.
Hmm. Well my only question there, I have to register the mac address of the cable modem with the ISP. Spoofing the mac of the router wouldn't cause that to mess up would it?

---

### Post by altaaa on 2007-04-09
If your setup is like this:

CABLE MODEM ---- ROUTER ---- PC

then no, you wouldn't.  Since you have said earlier that you can also connect your computer directly, I'm assuming this is the setup you're using.

In this case you can safely modify such a setting in your router, the only thing it does is to make it look for your ISP like this:

CABLE MODEM ---- PC

I'd rethink it if your cable modem and router are one device, though...

---

### Post by TravisNewman on 2007-04-09
No, you're right, they are two separate devices. I'll give that a go this evening.

If that works, would you suggest just changing the router's mac address and see if that fixes things somehow?

---

### Post by altaaa on 2007-04-09
If that works, my guess is that the lease in your ISP's DHCP server is somehow messed up. That would explain why your router gets a completely different IP that your PC. 

If it should work, just leave it like that. Once the lease that is registered to the MAC of your router expires (could take up to a week), you can have a second go at using the original MAC of your router.

But, not all routers support MAC Address Cloning. If your router doesn't you should call your ISP and ask them to release your router's WAN IP... Maybe that helps.

---

### Post by TravisNewman on 2007-04-09
I'm pretty sure it does support that. I'll give it a go and let you all know. Hopefully I won't have to buy another router (but I was kinda looking forward to some wireless :P)

---

### Post by TravisNewman on 2007-04-09
> **altaaa said:**
> If that works, my guess is that the lease in your ISP's DHCP server is somehow messed up. That would explain why your router gets a completely different IP that your PC. 

If it should work, just leave it like that. Once the lease that is registered to the MAC of your router expires (could take up to a week), you can have a second go at using the original MAC of your router.

But, not all routers support MAC Address Cloning. If your router doesn't you should call your ISP and ask them to release your router's WAN IP... Maybe that helps.

/me gives you a gold star

That's freakin' weird. But it works now. Woo!

---

### Post by TravisNewman on 2007-04-09
The funny thing is, I joined three other forums to ask for help. All of them popular, all of them network related, and this is the only forum I got any replies on :)

---

### Post by altaaa on 2007-04-09
That's good! Thanks for the gold star! :)

---

### Post by altaaa on 2007-04-09
> **panickedthumb said:**
> The funny thing is, I joined three other forums to ask for help. All of them popular, all of them network related, and this is the only forum I got any replies on :)

I think this is one of the best forums around. Must be the 'Ubuntu' mindset :)

---

### Post by TravisNewman on 2007-04-09
Hey! I think I've now figured out the problem! 

I posted this question at Broadband Help, and I *did* get one reply. 
[http://www.dslreports.com/forum/remark,18139726?r=36#18143346](http://www.dslreports.com/forum/remark,18139726?r=36#18143346)
I didn't sign up for an account, and in that case it shows your domain.  If you notice, it says charter.com for the first post, and the post that I sent back to say that all was working, it says suddenlink.net

Well, the charter location in the area was bought out by suddenlink recently. I guess something got messed up in their merger or something. Either way I don't care, it works now. :)

---

### Post by matthew on 2007-04-09
> **panickedthumb said:**
> /me gives you a gold star/me makes it official... :KS

---

### Post by altaaa on 2007-04-10
That would explain the different IP range. Try in a week or two to remove the MAC cloning, so you can use the router's MAC address once again. Or just keep it as it is, at least it's working :)

---

