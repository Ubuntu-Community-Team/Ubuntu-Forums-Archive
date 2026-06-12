---
title: "Every User Should Have This Feature for Their Ubuntu"
date: 2008-05-10
forum: The Cafe
---

### Post by SuperMike on 2008-05-10
Check [this article]("http://www.myfoxny.com/myfox/pages/Home/Detail;jsessionid=2C8EED15D33152238695035EA2C5A785?contentId=6506184&version=6&locale=EN-US&layoutCode=TSTY&pageId=1.1.1&sflg=1") out from Fox News New York.

So the mac user was able to find her stolen laptop by connecting remotely to it once it was connected to the Internet, and then snap a photo of the thieves.

Oh yeah! I want that for my Ubuntu laptop. I want to be able to connect remotely to it no matter where it is, and connect securely of course, as long as it's connected to the Internet again. Once there, I want to able to secretly activate the web cam and perhaps the microphone remotely.

And then it needs to be easy to use so that even newbies could use this control panel to activate this without much fuss.

---

### Post by swoll1980 on 2008-05-10
They never seen that coming

---

### Post by gn2 on 2008-05-10
Superb story serves them right the scumbags.

(should have formatted the drive)

---

### Post by MaindotC on 2008-05-10
Very interesting and I'm glad the thieves were caught but the fact that you can find your Mac ANYWHERE on the internet leads me to believe there's some sort of monitoring functionality that is probably at the government's fingertips.  How is this not a privacy concern?  If I set up my box for VNC at least only I know the IP address and VNC password.  Yeah, there are ways of scanning and seeing if the VNC service is being offered, but it seems to me that the Mac IT staff is LOGGING this information in a central location so it can be found.  Seems to be a rather hefty privacy concern.

---

### Post by Seti on 2008-05-10
the tools for this job are ssh and a good dynamic dns update client. First you install ssh, then get a domain from dyndns....they're free!
Once your dynamic dns client is properly set up, your computer should always properly identify itself on the internet when it connects.
That way, you can just ssh to it and do what you want...of course that depends on how cozy you feel working in a terminal.

---

### Post by MaindotC on 2008-05-10
K my fault for being newb - didn't know it was that easy.  I've heard of dydns but never took the time to google it.  So basically if you reboot the machine you should still be able to access it when it loads up, eh?  At least via SSH b/c you can't remote into a machine unless it has been logged into right?

---

### Post by barbedsaber on 2008-05-10
gold star for you:KS

---

### Post by spupy on 2008-05-10
You don't need SSH? You could just have the laptop take a picture when it connects to the internet and mail it to you. Why would you stay online at a console waiting a week for your stolen computer to get online.

But a clever thief would wipe the HD or at least copy it on an external one.

Still it is a good idea.

---

### Post by Tundro Walker on 2008-05-10
> **Seti said:**
> the tools for this job are ssh and a good dynamic dns update client. First you install ssh, then get a domain from dyndns....they're free!
Once your dynamic dns client is properly set up, your computer should always properly identify itself on the internet when it connects.
That way, you can just ssh to it and do what you want...of course that depends on how cozy you feel working in a terminal.

You post a video of your dear, sweet, old Grand-ma-ma doing this in Ubuntu, and I'll officially declare Ubuntu ready for the desktop.

---

### Post by the yawner on 2008-05-10
You have your *buntu laptops on auto-login?

---

### Post by roaldz on 2008-05-10
> **Tundro Walker said:**
> You post a video of your dear, sweet, old Grand-ma-ma doing this in Ubuntu, and I'll officially declare Ubuntu ready for the desktop.

Some functions don´t need to be accessible to every normal user. The terminal is for power users (at least you could be one if you´d use it). My grandma ain´t a poweruser.
Does your grandma take her laptop everywhere?

---

### Post by p_quarles on 2008-05-10
> **spupy said:**
> But a clever thief will wipe the HD or at least copy it on an external one.till it is a good idea.
A boot disk would allow a thief to get around any possible kind of software based countermeasure. This would really only be useful against thieves who were A) technically inept AND B) going to use the laptop themselves, rather than sell it. 

> **the yawner said:**
> You have your *buntu laptops on auto-login?
Many system users are activated prior to a human user's login, and one of these could be instructed to perform any operation you wanted it to.

---

### Post by SuperMike on 2008-05-10
> **spupy said:**
> You don't need SSH? You could just have the laptop take a picture when it connects to the internet and mail it to you. Why would you stay online at a console waiting a week for your stolen computer to get online.

But a clever thief will wipe the HD or at least copy it on an external one.

Still it is a good idea.

I like this approach a lot. Combine with one's favorite private website and some login authentication, and it could snap a photo of you like every 2 minutes and upload every 10 minutes. Still, if someone got ahold of my Ubuntu laptop, they would be very frustrated because they couldn't login no matter what they did unless they reinstalled or wiped the disk. (Well, some smart Linux guys would mount the partition and figure things out, I'm sure. However, the average thief is too stupid to know this technique.)

---

### Post by the8thstar on 2008-05-10
Try and catch thieves if your computer doesn't have a built-in webcam! That woman was savvy, sure, but damn lucky too.

Imagine if:

1. the thieves had reformatted the whole disk
2. there was no webcam
3. there was no internet connection
4. connection was through somebody else's bandwidth

She was LUCKY I say.

Ridiculous...

---

### Post by original_jamingrit on 2008-05-10
I remember a while ago, some people were able to achieve a similar effect using a benign trojan, which 'phoned home' and wrote to a log somewhere every time it was given a new IP address, and the time it was given, or something to that effect.

---

### Post by inportb on 2008-05-10
> **Seti said:**
> the tools for this job are ssh and a good dynamic dns update client. First you install ssh, then get a domain from dyndns....they're free!
Once your dynamic dns client is properly set up, your computer should always properly identify itself on the internet when it connects.
That way, you can just ssh to it and do what you want...of course that depends on how cozy you feel working in a terminal.

I'd think a reverse SSH tunnel would be helpful to guarantee connection even through NAT/firewall. This would require a constant machine to establish the connection to, which I imagine .mac  provides. You would then be able to set up a regular SSH tunnel to the "middleman" machine and receive data, even through NAT/firewall.

It doesn't matter how cozy you feel working in a terminal, because you can simply set up X forwarding or use NX.

---

### Post by klange on 2008-05-10
Automatic script is the best way, preferably one that checks the external IP address after a connection is made and if it isn't the one we're used to, phone home - include all connection data possible, IP, MAC of the router it's connected to, DNS servers assigned by the network, etc. That's how LowJack works - it records your external IP address and reports it to the LowJack service, which has a database of geolocations for IP ranges.

My machine doesn't have a web cam, and it's BIOS-password "protected", it also doesn't happily log on and connect to networks - you have to beat it into submission first. I guess, technically, I could remove the BIOS password, set the GRUB default to a mini-distro built specifically to log onto wireless networks and report location information, and set the timeout to something really short (I already have it on 3, but they might notice that...) Only I would know that I have to press and hold ESC while it boots to get the true boot menu.

You could also get an embedded GPS, if you want to always know where it is. That's one of the simplest solutions. And if you don't want to get one that always reports its location over a cell network or something like that, there's always the solution above, but with the current GPS location added to the report.

Also, some people have been throwing around the idea of computer thieves wiping hard drives - they wouldn't do this straight off, they'd boot it once to see how things run. Keep in mind, most people have some pretty useful information stored on their laptops - SSNs, credit card numbers, passwords (of course). That's your chance to screw them with a phone-home.

---

### Post by the8thstar on 2008-05-10
> **WindowsSucks said:**
> 

Also, some people have been throwing around the idea of computer thieves wiping hard drives - they wouldn't do this straight off, they'd boot it once to see how things run. Keep in mind, most people have some pretty useful information stored on their laptops - SSNs, credit card numbers, passwords (of course). That's your chance to screw them with a phone-home.

True, yet you don't need to be connected to any network to extract data. Plus, you can remove the hard disk from the PC and plug it somewhere else onto another rig. No one would ever know. How is it going to call home if the OS is not active?

Then you can copy data at will and the best thing is, you don't even need the original anymore. Of course, not every thief would do/know these tricks, I'll give you that. Most would just want to play games... or do a quick re-sell.

---

### Post by vrangforestillinger on 2008-05-10
The way my Ubuntu is set up now, this is easily done with
```
ssh -X -C myuser@mycomputer.no-ip.org
```
then
```
cheese
```

Cheese indeed. :lolflag:

(I have dynamic IP-update at no-ip.org)

---

### Post by CREEPING DEATH on 2008-05-10
[COLOR="Black"]Y'all keep bringing up thieves wiping the drives, most people smart enough to wipe a drive and re-install an OS are smart enough not to be thieves!  And the ones that are smart enough to do such things are looking at much larger scores than stolen laptops.

CD[/COLOR]

---

### Post by Incense on 2008-05-10
> **CREEPING DEATH said:**
> [COLOR="Black"]Y'all keep bringing up thieves wiping the drives, most people smart enough to wipe a drive and re-install an OS are smart enough not to be thieves!  And the ones that are smart enough to do such things are looking at much larger scores than stolen laptops.

CD[/COLOR]

+1. I'm thinking one look at the log in screen would get a "This isn't windows" response from the thief, and it would be off to the pawn shop, or Craig's list to make a little cash.

---

### Post by gn2 on 2008-05-10
> **CREEPING DEATH said:**
> [COLOR="Black"]Y'all keep bringing up thieves wiping the drives, most people smart enough to wipe a drive and re-install an OS are smart enough not to be thieves![/COLOR]

You're forgetting that the best thieves are the intelligent ones who know how to avoid being caught.
Unlike this pair of retards.

---

### Post by SuperMike on 2008-05-11
> **vrangforestillinger said:**
> 
```
cheese
```


```
# apt-get install cheese
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cheese
```

Would be a great little command to have, though.

---

### Post by inportb on 2008-05-11
No kidding. I would love to have cheese delivered to me when I want. Ever heard of the pizza_party program? Now put it on cron... =D

---

### Post by xtang on 2008-05-11
> **SuperMike said:**
> ```
# apt-get install cheese
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cheese
```

Would be a great little command to have, though.

[http://ubuntuforums.org/showthread.php?t=486722](http://ubuntuforums.org/showthread.php?t=486722)

---

### Post by SomeGuyDude on 2008-05-11
The ability to remotely connect to a computer anywhere and use its hardware from remote location?

Great! What could possibly go wrong?

---

### Post by the yawner on 2008-05-11
> **p_quarles said:**
> 
Many system users are activated prior to a human user's login, and one of these could be instructed to perform any operation you wanted it to.

Yes. But it's worthless to the thieves if they can't get into the system. So it's either they format the drive/ dispose of it, or if they're linux savvy, use a live CD.

---

### Post by klange on 2008-05-11
I just had the most brilliant of ideas:
Truth be told, they *will* boot the thing to make sure it works properly. If you have internal bluetooth and can get your hands on a mobile that can be slipped inside a PCMCIA slot, this is the ultimate solution.
1. Turn on phone, slip into slot.
2. Set boot menu to force a micro-distro after a very short interval (I'd say 1 second, hold ESC on boot to do normal operations)
3. Here's the setup for the micro-distro:
 - Load bluetooth drivers.
 - Connect to phone with bluetooth dialer.
 - Contact local police (should be a configuration option, controlled from your normal distro, so you can set it depending on where you are to the simplest form of 911, 999, etc.)
 - Send a very specific message to whoever answers (Wait for a response, this usually only takes a few seconds). This should be a prerecorded OGG that says something like "This is an automated message being sent from a stolen laptop, the property of [your name here] [your address here] [your phone number here]. Please trace this call. [Extra information here]." (loop message until call is disconnected.)
 - While sending the message, use the framebuffer to display a Windows boot screen (XP, Vista, something they'll think is for real).

Basically, the micro-distro should be so small and limited that it boots in a few seconds - it's not weighted down by anything, not even an X server, no Wireless drivers, etc., just a bluetooth module and a dialer program that can play OGGs through phones. This means that the time taken for the entire process should come down to just how long it takes to call the cops and play the message. If that message is long enough, they can trace the call by cell tower and get a very precise location. You can even combine this with a webcam, assuming your phone can send pictures and the dialer is equipped to handle them.

---

### Post by the8thstar on 2008-05-11
"*And where is the slot to put my 25 cents to play that jukebox?*" ;)

Seriously now, your idea is very good, but if they just take the hard disk out, you're screwed. Now you could put a bomb with a remote detonator inside the HDD of course... *KA-BOOOM*... (whistles)

Only McGyver and Indiana Jones would get out of that one.

Strong Data Encryption and regular disk backup are your safest protections IMO.

---

### Post by SuperMike on 2008-05-11
Giving this some serious thought, most people who steal your Ubuntu laptop are likely of the very dumb category, like these guys that stole that Mac OSX laptop. So, they'll open it up, see some funky operating system with a completely different login, and try to do a format/reinstall.

About the only thing that could stop them is to have a custom BIOS (like download one from the web) and customize it in C/C++, or put a password on your BIOS (which I think is harder to defeat in laptops).

I guess one prevention mechanism could be to edit the bitmap on your Ubuntu login screen such that it displays a "Guests, please use user:guest, pass:guest." message. When they login with this, you can set it up so that it's chrooted, and it takes their picture and their IP address and ships it up to your Flickr account secretly in the background. And if it's not connected to the Internet just then, it will try to resend every 5 minutes when finally connected until it does this successfully, and then reattempt to send every 30 minutes after that.

---

### Post by Ultra Magnus on 2008-05-11
Isn't this feature fairly redundant - I mean if your laptop is stolen and you have a good password then they'd have to format the hard disk and reinstall something on it so you wouldn't be able to log in - On the other hand if you purposely had a crap password so you could do this, then you'd lose all your data which would suck.

---

### Post by aysiu on 2008-05-11
If you know what you're doing (clearly these thieves did not), a password will not stop you if you have physical possession of the laptop.

In Mac OS X, for example, you can hold down Cmd-S during bootup to get a recovery console and then ```
cd /Users
ls
passwd *username*
reboot
``` to reset the user's password to one of your liking.

Ubuntu has a similar single-user log-in-as-root recovery mode in the Grub menu, and you can also boot a live CD and change the /etc/shadow file manually.

The real problem here was that the thieves were dumb. That woman was lucky.

---

### Post by the yawner on 2008-05-11
Haha... I totally forgot about the recovery mode. And while we're at it, I believe network is disabled when in recovery mode. I think.

---

### Post by p_quarles on 2008-05-11
> **the yawner said:**
> Haha... I totally forgot about the recovery mode. And while we're at it, I believe network is disabled when in recovery mode. I think.
Nope. "Recovery mode" is Ubuntu's term for what is better known as "single-user mode." Single-user mode = root mode. Booting into recovery mode gives you every possible privilege on that computer.

---

### Post by the yawner on 2008-05-11
Right. I forgot I was able to make that work. So that means you'll need to run possibly a script on certain conditions?

---

### Post by jnorth on 2008-05-12
> **WindowsSucks said:**
> I just had the most brilliant of ideas:
Truth be told, they *will* boot the thing to make sure it works properly. If you have internal bluetooth and can get your hands on a mobile that can be slipped inside a PCMCIA slot, this is the ultimate solution.
1. Turn on phone, slip into slot.
2. Set boot menu to force a micro-distro after a very short interval (I'd say 1 second, hold ESC on boot to do normal operations)
3. Here's the setup for the micro-distro:
 - Load bluetooth drivers.
 - Connect to phone with bluetooth dialer.
 - Contact local police (should be a configuration option, controlled from your normal distro, so you can set it depending on where you are to the simplest form of 911, 999, etc.)
 - Send a very specific message to whoever answers (Wait for a response, this usually only takes a few seconds). This should be a prerecorded OGG that says something like "This is an automated message being sent from a stolen laptop, the property of [your name here] [your address here] [your phone number here]. Please trace this call. [Extra information here]." (loop message until call is disconnected.)
 ...snip!

Dude that's not a bad idea at ALL!  The FCC now has regulations in place that _require_ all cellular phones to be able to call 911 - even without being activated.  So - if you can afford to buy the card, you won't need to pay for minutes on it if all you get it for is a custom "lojack" feature like this.

My $.02...

---

### Post by SuperMike on 2008-05-14
More news on this, at least for Macs, is this new piece of software:

[http://www.orbicule.com/undercover/](http://www.orbicule.com/undercover/)

So, for Ubuntu, it would be nice to have something comparable, even if a bit more minimal. And it would have to be very secure.

---

### Post by the8thstar on 2008-05-17
I guess the best and simplest solution is to not have your computer stolen in the first place.

---

