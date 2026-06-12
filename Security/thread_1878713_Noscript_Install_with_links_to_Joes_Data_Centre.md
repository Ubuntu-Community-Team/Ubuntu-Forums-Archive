---
title: "Noscript Install with links to Joes Data Centre"
date: 2011-11-10
forum: Security
---

### Post by SparTacux on 2011-11-10
I've just installed Noscript and now I get https links going to Joe's Data Centre ( IP 69.195.141.179 ) when I am using my browser. I'm not sure if this is normal or not and decided some of you guys who use Noscript will be familiar with this traffic.

---

### Post by vasa1 on 2011-11-10
> **SparTacux said:**
> I've just installed Noscript and now I get https links going to Joe's Data Centre ( IP 69.195.141.179 ) when I am using my browser. I'm not sure if this is normal or not and decided some of you guys who use Noscript will be familiar with this traffic.

Wow! I'm one of the few who don't use NoScript but have you looked at the whitelist? From what I remember, there are quite a few entries that can be removed for the better.

---

### Post by CharlesA on 2011-11-10
Is it any HTTPS site?

I just installed firefox and no script on a vm and went to a site that used https and didn't have any problems.

---

### Post by SparTacux on 2011-11-10
> **vasa1 said:**
> Wow! I'm one of the few who don't use NoScript but have you looked at the whitelist? From what I remember, there are quite a few entries that can be removed for the better.

I cleared the white list.

I need to do a bit more testing to find out if there is a regular pattern when the links go out. I'm used to seeing what traffic is normal and which ain't. This is new - I ain't seen it before.

---

### Post by SparTacux on 2011-11-10
> **CharlesA said:**
> Is it any HTTPS site?

I just installed firefox and no script on a vm and went to a site that used https and didn't have any problems.

 My homepage is [http://eu.ixquick.com](http://eu.ixquick.com) which uses https for privacy reasons.  As soon as I installed Noscript - I started getting extra https traffic to 69.195.141.179. It seems to have tailed off for the moment - I'll have to restart my browser a few times and see what gives.

---

### Post by SparTacux on 2011-11-10
First instance of the link was at 9.46 am this morning - just after I installed Noscript. The https links to 69.195.141.179 go out soon after I restart my browser.    Possibly Noscript or Mozzila add-ons phoning home? Dunno - maybe those who use Noscript may be more familiar.

---

### Post by SparTacux on 2011-11-10
> **CharlesA said:**
> Is it any HTTPS site?

I just installed firefox and no script on a vm and went to a site that used https and didn't have any problems.

I was using Seamonkey :-)

My other user account on this computer doesn't have Noscript installed on the browser and I don't get the same outgoing traffic. It certainly started happening after Noscript install in Seamonkey.

---

### Post by Lampi on 2011-11-10
It this is bothering you try unchecking NoScript Options|Advanced|ABE|WAN IP &#8712; LOCAL and you should be good to go

see: [http://www.wilderssecurity.com/archive/index.php/t-305394.html](http://www.wilderssecurity.com/archive/index.php/t-305394.html)

---

### Post by SparTacux on 2011-11-10
> **Lampi said:**
> It this is bothering you try unchecking NoScript Options|Advanced|ABE|WAN IP &#8712; LOCAL and you should be good to go

see: [http://www.wilderssecurity.com/archive/index.php/t-305394.html](http://www.wilderssecurity.com/archive/index.php/t-305394.html)

That did the job - Thanks a lot :-)

I found a link from that forum that explained the reason for the outgoing traffic.
It seems they are trying to protect your router amongst other things.

[https://addons.mozilla.org/en-US/firefox/addon/noscript/privacy/](https://addons.mozilla.org/en-US/firefox/addon/noscript/privacy/)

---

### Post by CharlesA on 2011-11-10
Glad it was documented somewhere.

---

### Post by OpSecShellshock on 2011-11-10
Seems like a decent trade-off to me: this traffic, according to the privacy link, is used as a mechanism to protect against [DNS rebinding attacks]("http://en.wikipedia.org/wiki/DNS_rebinding").

The only other real mechanism of protection would involve either sites respecting host: headers (most of them don't) or would involve you controlling the name servers and configuring them to not allow rebinding. In other words, NoScript's solution is one of a very few that can be implemented on the client side.

Just something to keep in mind.

---

### Post by SparTacux on 2011-11-10
> **OpSecShellshock said:**
> Seems like a decent trade-off to me: this traffic, according to the privacy link, is used as a mechanism to protect against [DNS rebinding attacks]("http://en.wikipedia.org/wiki/DNS_rebinding").

The only other real mechanism of protection would involve either sites respecting host: headers (most of them don't) or would involve you controlling the name servers and configuring them to not allow rebinding. In other words, NoScript's solution is one of a very few that can be implemented on the client side.

Just something to keep in mind.

So - you would allow the traffic then?

I've not quite got my head around what a rebinding attack does - I read the info on that link. It mentions something about your  web browser  being used to attack other computers on your private network. Couldn't you create a firewall rule to stop http 'traffic' going to your subnet such as DENY OUT TCP PORT 80 to 192.168.0.0/24 or something like that?

Just had another look on the info you gave - it seems a rebinding attack can do a number of things.

---

### Post by OpSecShellshock on 2011-11-10
> **SparTacux said:**
> So - you would allow the traffic then?

I've not quite got my head around what a rebinding attack does - I read the info on that link. It mentions something about your  web browser  being used to attack other computers on your private network. Couldn't you create a firewall rule to stop http 'traffic' going to your subnet such as DENY OUT TCP PORT 80 to 192.168.0.0/24 or something like that?

Just had another look on the info you gave - it seems a rebinding attack can do a number of things.

I think if you take the NoScript developers at their word that they are only doing it a couple times a day, and that they are not collecting information in excess of exactly what they need in order to prevent attacks, then yes. It seems harmless enough, and is probably helpful.

Oh, and if you stop all http traffic out to your entire private address space, you'll also be stopping it from getting to your router and points beyond, I think. In any rate, the purpose of the NoScript-related traffic is to obtain the public IP address information (which it otherwise wouldn't know) in order stop anything rebinding to that (at least that's what I'm taking from the privacy link).

---

### Post by hansdown on 2011-11-10
The IP address originates in Kansas City, Mo.

A phone number is provided.

---

### Post by OpSecShellshock on 2011-11-10
> **hansdown said:**
> The IP address originates in Kansas City, Mo.

A phone number is provided.

Just to put everyone at ease about the IP address (to whatever extent that can be done):

The IP resolves to secure.informaction.com, and that domain is registered to the developer of NoScript.

---

### Post by hansdown on 2011-11-10
> **OpSecShellshock said:**
> Just to put everyone at ease about the IP address (to whatever extent that can be done):

The IP resolves to secure.informaction.com, and that domain is registered to the developer of NoScript.

Thanks, OpSecShellshock.

---

### Post by SparTacux on 2011-11-11
Everyone's Happy Then :-)
Case Closed

---

