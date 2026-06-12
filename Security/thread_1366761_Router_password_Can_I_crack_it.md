---
title: "Router password: Can I crack it?"
date: 2009-12-28
forum: Security
---

### Post by mailman1175 on 2009-12-28
All right, so I'm a dummy, and I'm hard-headed. I forgot the password I created to log into my router. Yeah, it's easy to do a hard reset of the router, but it was a pain in the rear to get my ISP settings right the first time (it took me and my sister's now-ex-boyfriend about 3 hours to get it right). I really, really, REALLY don't want to have to do that again.

I know there are a lot of password-cracking programs out there, for lots of different platforms. I'm not really interested in WEP/WPA cracking, though. I just want to turn my machine loose to try to brute-force crack my router's login password while I sleep.

I have a few questions, though:
[LIST=1]
[*]Am I crazy? That is, is there even a FOSS program that can do what I want it to do? [I can use something for OS X or Ubuntu, though I'd prefer OS X, just because I've got better hardware behind that platform.]
[*]The password is somewhere in the vicinity of 10 characters, including numbers, upper- and lower-case letters, and special characters, but is basically a l33t-speak twist on an actual word. [I'd intended to make it easier to remember, but difficult to guess…] Is it realistic to think that up-to-date hardware (say, a new MacBook) could crack that password overnight?
[*]Assuming there's a program that does what I want, and assuming it's not going to be ridiculously time-consuming to do it, how do I go about *implementing* the crack?
[*]Or do I just need to bite the bullet, reset the router, and move on?
[/LIST]

So, hit me with it. And thanks.

---

### Post by whoop on 2009-12-28
I'm not exactly sure if this is the proper forum to post questions like this, but:

To help you I would at least needs the exact make and model of your router...

The only solution that could work for any make and model would be brute force...

---

### Post by mailman1175 on 2009-12-28
> **whoop said:**
> I'm not exactly sure if this is the proper forum to post questions like this, but:

To help you I would at least needs the exact make and model of your router...

The only solution that could work for any make and model would be brute force...
If I'm in the wrong forum, I apologize. Moderators are free to move the topic, obviously, if necessary.

Does the method/program varies according to router specification? I knew it would have to be brute force. I'm just a little wary of exposing more information than I absolutely have to&#8230;

---

### Post by __p1n__ on 2009-12-28
> **mailman1175 said:**
> I'm not really interested in WEP/WPA cracking, though. I just want to turn my machine loose to try to brute-force crack my router's login password while I sleep.
 
You don't even know if it uses WEP or WPA?  Are you sure that it's your router?  All that will do in any event is allow your wifi client to connect to the AP; you'll still need the admin password to configure it.  This latter will need to be cracked if you can't exploit a vuln on the router.

You really should just reset it; setting up the DHCP and gateway information from your ISP is trivial.

---

### Post by mailman1175 on 2009-12-28
> **__p1n__ said:**
> You don't even know if it uses WEP or WPA?  Are you sure that it's your router?  All that will do in any event is allow your wifi client to connect to the AP; you'll still need the admin password to configure it.  This latter will need to be cracked if you can't exploit a vuln on the router.

You really should just reset it; setting up the DHCP and gateway information from your ISP is trivial.
It's my network, and it's unsecured. I don't use either WEP or WPA for login. My house is a quarter mile from my neighbors, and 25 miles from any place of any significance. Anyone trying to scam my wifi's going to have my attention when they pull into the driveway.

I suppose it's inevitable that responders to these kinds of threads are going to assume I'm a script kiddie trying to get into my neighbor's network so I can surf pr0n&#8230;

It's the admin password I've forgotten. And, as I said in the OP, setting up the router/ISP is not trivial (for me). I've only done it once, and it took me and one other guy half a day of trial-and-error to get it right. My ISP won't give any kind of support to customers setting up wireless routers, so they're no help.

---

### Post by whoop on 2009-12-28
> **mailman1175 said:**
> 
Does the method/program varies according to router specification? I knew it would have to be brute force.

Some router's are exploitable (the firmware actually), so methods may vary.
Some router's even have a functionality to just reset the password...

---

### Post by mailman1175 on 2009-12-28
> **whoop said:**
> Some router's are exploitable (the firmware actually), so methods may vary.
Some router's even have a functionality to just reset the password...
I've done some more research, and it looks like it could take a very long time for any machine to brute force crack my router. I talked to my ISP, and they've at least made it sound easy to get reconnected, so I'm just going to reset the router.

---

### Post by echoreply on 2009-12-28
some tools in backtrack or OSWA assistant (for wireless) might come in handy.

---

### Post by DGortze380 on 2009-12-29
> **mailman1175 said:**
> 
[*]The password is somewhere in the vicinity of 10 characters, including numbers, upper- and lower-case letters, and special characters, but is basically a l33t-speak twist on an actual word. [I'd intended to make it easier to remember, but difficult to guess…] Is it realistic to think that up-to-date hardware (say, a new MacBook) could crack that password overnight?

No, it's not. You've describe a 'strong' password. It will likely take an exceptionally long time to brute-force.

A modified dictionary attack would be quicker, still too long to make it practical IMO.

Just do a hard reset. Network settings from your ISP shouldn't be that difficult to restore.

---

### Post by insane_alien on 2009-12-29
mm, hard reset, reconfigure it(it shouldn't take three hours as some things will come back to you) and once you have it running again, backup the configuration. that way next time you will be able to just tell the router to look a tthat file and everything will be dandy again.

---

### Post by Project PWNED on 2009-12-29
Reset the router. "3 hours of reconfiguring" beats 3 days of searching online for the solution.

---

### Post by HH60Gunner on 2010-02-02
if setting up isp settings is more than trivial for you then cracking a password is going to be way beyond your capabilities.  I'm not trying to be a jerk, but just being honest.

---

### Post by bodhi.zazen on 2010-02-02
> **HH60Gunner said:**
> if setting up isp settings is more than trivial for you then cracking a password is going to be way beyond your capabilities.  I'm not trying to be a jerk, but just being honest.

And with that I am closing this thread.

It is over a month old and we really do not support cracking passwords here.

---

