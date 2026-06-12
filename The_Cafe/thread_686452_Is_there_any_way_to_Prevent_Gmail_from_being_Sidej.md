---
title: "Is there any way to Prevent Gmail from being Sidejacked?"
date: 2008-02-03
forum: The Cafe
---

### Post by kevdog on 2008-02-03
After all those stories came out a long time ago about gmail being able to be sidejacked using regular http wireless connections, I thought https would be secure, but now find that its not:
[http://erratasec.blogspot.com/2008/01/more-sidejacking.html](http://erratasec.blogspot.com/2008/01/more-sidejacking.html)

I suppose there isnt any extension out there for firefox or bettergmail that would force firefox or any google connection to use https and never default to http?

---

### Post by M$LOL on 2008-02-03
Would CustomizeGoogle work? [https://addons.mozilla.org/en-US/firefox/addon/743]("https://addons.mozilla.org/en-US/firefox/addon/743")

---

### Post by kevdog on 2008-02-03
That may force the https connection initially, however I don't know if that prevents fallbacks to http

---

### Post by crush304 on 2008-02-03
can you use imap through evolution with ssl?

---

### Post by kevdog on 2008-02-03
Hmm maybe I could.  But seems like there should be a better solution without having to resort to a different program -- a plugin perhaps.  With a different program I would have to resort to carrying around a USB stick to access gmail securely from different computers.

---

### Post by M$LOL on 2008-02-03
> **kevdog said:**
> That may force the https connection initially, however I don't know if that prevents fallbacks to http

There might be an option in there for it, I'll have to check.

---

### Post by XVII on 2008-02-03
This is what I do; use this [link]("https://mail.google.com/mail") to login.  It will stay https, it works for me in Opera.

---

### Post by kevdog on 2008-02-03
No, that link does not work.  If you read the article from the link I posted, even the [https://mail.google.com/mail](https://mail.google.com/mail) will fall back to http and release the session cookie if the ssl connection will not go through.  That is the entire problem.

---

### Post by ice60 on 2008-02-03
i didn't read the link, but i saw it mentions javascript, if you don't enable JS on gmail it will probably be OK, there are loads of examples of using java or JS to make a direct connection to get around security or privacy and disabling them normally fixes it. i'm not a security expert so i might be wrong lol

---

### Post by Crashmaxx on 2008-02-03
I know bettergmail has an option to force https, don't know if bettergmail2 has it yet.

---

### Post by Æniad on 2008-02-03
Do you really need to be **that **paranoid? I think using https would be suitable under most circumstances.

---

### Post by Pekkalainen on 2008-02-03
I just use [https://www.gmail.com](https://www.gmail.com) as my bookmark and the url bar stays yellow all the way through so I reckon it works?

---

### Post by kevdog on 2008-02-03
The entire point is that I think gmail falls back unknowingly to the user to http if https fails.  I have no idea if/when this is possible, however the article was pretty critical of the scheme nearly to the point of stating that gmail was insecure.  I'm no security expert, but when I read that, it seems like there is a problem.

---

### Post by DjBones on 2008-02-03
it seemed to make sense.. but his statement that the connection is secure and only in jeopardy in the situation (but how often or even plausible is it?) that ssl should fail.

> The JavaScript code uses an XMLHttpRequest object to make HTTP requests in the background. These are also SSL encrypted by default - but they become unencrypted if SSL fails.
but it does sound probable that if you found yourself in the unlikely situation where SSL for some god-forsaken reason did fail.. that you would be in trouble.

---

### Post by charding on 2008-02-04
Install greasemonkey.

There are https userscripts that will always keep you in https for gmail, google calendar, etc.

Search on userscripts.org to get one of these scripts.

---

### Post by michaelzap on 2008-02-04
If you don't use Gmail's web interface via an unencrypted wireless connection then I don't think there's any need to worry about sidejacking.

---

### Post by kevdog on 2008-02-04
> **DjBones said:**
> it seemed to make sense.. but his statement that the connection is secure and only in jeopardy in the situation (but how often or even plausible is it?) that ssl should fail.....

This is the part I don't know about -- how likely is it that ssl would fail?  
From the tone of the letter it sounded like it would not be an unrealistic possibility.

And yes this is most likely an issue with unencrypted wireless networks, however if using a WPA PSK at work or any any other venue where multiple users have the same key, you also open yourself up to this kind of attack.

---

### Post by michaelzap on 2008-02-04
I think that this is a real security problem, but it's nowhere near as grave as it's been hyped.

My understanding is that this sort of hack would really only be viable on a compromised/hostile network (such as a public unencrypted hotspot), since you would first need to make the SSL connection fail. You also need to have checked the Remember Me button, since otherwise there's no login cookie to intercept. So I really don't think the risk is very high if you always use the https URL, don't check Remember Me, and don't use unencrypted wireless connections.

I expect Google will patch this shortly (they've dealt with much worse before).

---

### Post by kevdog on 2008-02-04
I would have thought they would have fixed the problem after the original sidejacking problem was exposed at the BlackHat convention earlier last year.  Their response at that time was just to use https and everything will be all right.  It turns out later in Oct or Nov 2007, this supposed solution was actually exposed.   I suppose they will fix it in time, however its been over 4 months since the bug was exposed, so either they must not think it to be too serious, or they can't find a way around the bug and to a better secure solution.

Again as an end user I have no idea how frequently I would be exposed to this vulnerability.  It just annoys me that this is yet another potential security breach.

---

### Post by OrangeCrate on 2008-02-04
> **Crashmaxx said:**
> I know bettergmail has an option to force https, **don't know if bettergmail2 has it yet**.

It does.

---

### Post by aks44 on 2008-02-04
> **michaelzap said:**
> My understanding is that this sort of hack would really only be viable on a compromised/hostile network (such as a public unencrypted hotspot),
What people don't realize is that *any* wireless network is by definition a hostile network. Compromising a wireless connection is often a matter of no more than a few minutes.


> **michaelzap said:**
> you would first need to make the SSL connection fail.
Once an attacker has gained access to a network (even a wired one), making an SSL connection fail is as easy as sending a spoofed RST (*reset connection*) packet either to the victim's computer or to the server. Concerning gmail, *poof*, your AJAX requests are automagically reverted to plain HTTP.


> **michaelzap said:**
> You also need to have checked the Remember Me button, since otherwise there's no login cookie to intercept.
The attack doesn't target login cookies (which would be kinda hard to intercept since they're only sent once) but the *session* cookie that is sent with each and every request made to the server.


> **Pekkalainen said:**
> I just use [https://www.gmail.com](https://www.gmail.com) as my bookmark and the url bar stays yellow all the way through so I reckon it works?
The whole point of that attack is that it targets AJAX connections, which browsers usually don't consider when it comes to displaying the "secure connection" hints. So the victim really has no way to know if she's been hijacked (apart from noticing dubious activity on her account).


> **kevdog said:**
> Again as an end user I have no idea how frequently I would be exposed to this vulnerability.
As soon as you're using any kind of wireless connection, or that you allow someone on your wired network, you're a potential victim.



Granted there are ways to mitigate this attack (eg. MAC restrictions on private connections make it impractical enough, but if the attacker is specifically after *you* then you're basically screwed).
What is unclear to me is whether gmail can work with Javascript disabled (I don't have an account so I can't tell), but this would completely remove the attack vector.

---

### Post by kevdog on 2008-02-04
aks44

Great post, but I think the results of your information leads me to ask more questions than answers.

---

### Post by aks44 on 2008-02-04
> **kevdog said:**
> Great post, but I think the results of your information leads me to ask more questions than answers.

Feel free to ask then, as long as this stays within the rules of the forum. ;)

More on this topic (nothing new though, but the attack is explained in a more understandable / simplified fashion): [TheRegister]("http://www.theregister.co.uk/2008/02/01/google_ssl_sidejacking/")

This specific quote is a bit frightening:
> "If companies do SSL correctly, then you're safe," Graham says. "The problem with Gmail is it's not doing SSL correctly. In my experience just using Gmail normally, I've seen this happen accidentally."

---

