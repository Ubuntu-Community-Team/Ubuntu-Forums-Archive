---
title: "Generating numeric Dictionary for Wpa"
date: 2010-07-18
forum: Security
---

### Post by mavericknik on 2010-07-18
Hey guys, so i just got a new internet connection from the local service provider. While installation, he insisted that i use my mobile number as the wpa password for the wifi. From what Ive heard, this is company policy. Im a little skeptical about this as ive read wpa is crackable using a dictionary if the password is in there. So i looked around and found the air-crack suite to test the security for my access point. As my password is only numeric, i couldn't find only a numeric dictionary to use with air-crack. 

So, i would like to create a dictionary that has only 10 digits, and the first two digit should be "05", because thats what mobile numbers here start from. I would be really grateful if anyone could point me to a way to do this easily. Thanks!

---

### Post by wacky_sung on 2010-07-18
Check out here below regarding WPA.

[http://en.wikipedia.org/wiki/WPA2#WPA2](http://en.wikipedia.org/wiki/WPA2#WPA2)
[http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access)
[http://arstechnica.com/security/news/2008/11/wpa-cracked.ars/](http://arstechnica.com/security/news/2008/11/wpa-cracked.ars/)

Test the strength of your password below.
[http://www.passwordmeter.com/](http://www.passwordmeter.com/)

Try to choose a password with 20 characters or more which make your wifi extreme difference to crack.Plus choose WPA2 over WPA due to encryption capability.

---

### Post by mavericknik on 2010-07-18
Thanks for the reply .I figured having only a numeric password isn't the brightest idea, and all that reading further added to my doubts. But what i really wanted to test is how easily a newbie like me would be able to get the password that (almost) everyone here is using, as most people don't bother to actually change their wifi password once its set up. One of my friends actually stupidly claimed that a 10 digit password is not brute-forceable(is that even a word?) and i just wanted to test how quickly i could get the password. So if someone could guide me in making that dictionary, i would be grateful.  Couldni i use a simple bash script or so?

---

### Post by OpSecShellshock on 2010-07-18
I don't imagine you'll find a whole lot of assistance in mounting a dictionary-based password cracking attack, even as a testing method. However, it should be trivial to find telephone numbers of people you know. I mean seriously? They insist that you use your telephone number? Also, who owns the access point, them or you? Do they have the option of just establishing a connection and letting you put your own AP (under your own full control) behind it?

---

### Post by rookcifer on 2010-07-18
Just brute-force it.  A 10 digit numerical password only has about 33 bits of entropy.  With a top-end GPU like the Radeon 5970, you can brute force a 10 digit WPA password in about 14 hours.  A core i7 920 CPU will take about two weeks.

Again a 10 character passphrase consisting only of numbers is ridiculously weak.  Whoever made this your company's password policy is an idiot.

---

### Post by mavericknik on 2010-07-18
> **OpSecShellshock said:**
> I don't imagine you'll find a whole lot of assistance in mounting a dictionary-based password cracking attack, even as a testing method. However, it should be trivial to find telephone numbers of people you know. I mean seriously? They insist that you use your telephone number? Also, who owns the access point, them or you? Do they have the option of just establishing a connection and letting you put your own AP (under your own full control) behind it?

Well, i dont really need assistance in mounting the attack, what i need is just a way to generate the said wordlist. That is the point, as i am a newbie, i dont want assistance, its just that this is the only place where i am stuck. I found a couple of full wordlists that i could use but that would just take more time, hence my need for the 10 digit numerical wordlist. Well, insist as in they do the setup that way the first time. I own the AP and i will obviously change the password, but most people just don't bother(well, i actually just got here, and my dad got the connection and the password has been numeric for 15 days, and he didn't bother)  

> **rookcifer said:**
> Just brute-force it.  A 10 digit numerical password only has about 33 bits of entropy.  With a top-end GPU like the Radeon 5970, you can brute force a 10 digit WPA password in about 14 hours.  A core i7 920 CPU will take about two weeks.

Again a 10 character passphrase consisting only of numbers is ridiculously weak.  Whoever made this your company's password policy is an idiot.

I actually want to try it offline, as in capturing the handshake and then trying a dictionary attack. It isnt my company, just the service provider here. Whats more surpising, is that the password is effectively 8 digits numeric, as the first 2 digits are same for phones here. I would still appreciate if i could know how to generate that dictionary. What i basically want is something like
0500000000
0500000001
to
0599999999 stored in a text file. though if im not supposed to ask here, ill gladly close the thread.

---

### Post by wacky_sung on 2010-07-18
Check it out using backtrack 4.

_**[COLOR="Red"]WPA2 Cracking with BackTrack 4 - 100.000 PWs in 6 Minutes (Dictionary Attack) [/COLOR]**_
[http://www.youtube.com/watch?v=udd_ymCyEnc](http://www.youtube.com/watch?v=udd_ymCyEnc)

---

### Post by mavericknik on 2010-07-18
> **wacky_sung said:**
> Check it out using backtrack 4.

_**[COLOR=Red]WPA2 Cracking with BackTrack 4 - 100.000 PWs in 6 Minutes (Dictionary Attack) [/COLOR]**_
[http://www.youtube.com/watch?v=udd_ymCyEnc](http://www.youtube.com/watch?v=udd_ymCyEnc)

Thanks mate, but i dont want help with the actual process. What i need is a way to make a numeric dictionary file.

---

### Post by wacky_sung on 2010-07-18
What you need is a password list / generator.

Probably you can search through the search engines

[http://www.google.com.sg/search?aq=f&sourceid=chrome&ie=UTF-8&q=password+list+generator](http://www.google.com.sg/search?aq=f&sourceid=chrome&ie=UTF-8&q=password+list+generator)

[http://www.google.com.sg/search?hl=en&q=password+list+txt&revid=875934661&sa=X&ei=8U9DTK2dLIfBcd6T8bkP&ved=0CFcQ1QIoAg](http://www.google.com.sg/search?hl=en&q=password+list+txt&revid=875934661&sa=X&ei=8U9DTK2dLIfBcd6T8bkP&ved=0CFcQ1QIoAg)

---

### Post by Agent ME on 2010-07-18
> **mavericknik said:**
> What i basically want is something like
0500000000
0500000001
to
0599999999 stored in a text file. though if im not supposed to ask here, ill gladly close the thread.
In a terminal
```
for ((i=500000000;i<600000000;i++)); do printf '%08d\n' "$i"; done > numbers.txt
```
will do the trick, but it will obviously have about 100 million entries in it and will take a while to run. It would be best if you could narrow it down; in my area for example, nearly all phone numbers start with a 2, 4, or 5, so I could run this to only get those numbers:
```
(
for ((i=520000000;i<530000000;i++)); do printf '%08d\n' "$i"; done 
for ((i=540000000;i<560000000;i++)); do printf '%08d\n' "$i"; done
) > numbers.txt
```

---

### Post by mavericknik on 2010-07-18
> **Agent ME said:**
> In a terminal
```
for ((i=500000000;i<600000000;i++)); do printf '%08d\n' "$i"; done > numbers.txt
```will do the trick, but it will obviously have about 100 million entries in it and will take a while to run. It would be best if you could narrow it down; in my area for example, nearly all phone numbers start with a 2, 4, or 5, so I could run this to only get those numbers:
```
(
for ((i=520000000;i<530000000;i++)); do printf '%08d\n' "$i"; done 
for ((i=540000000;i<560000000;i++)); do printf '%08d\n' "$i"; done
) > numbers.txt
```


thanks a lot . Im actualy talking about mobile numbers here so i cant really narrow it down. But your printf code will list numbers only as 
500000000
500000001...
right? Is there any way to append a 0 at the start of the code? This seems to be my biggest problem right now.

---

### Post by Agent ME on 2010-07-18
Whoops, I made it pad the numbers out to 8 digits, instead of 10 digits. Change the "printf '%08d\n'" part to "printf '%010d\n'".

---

### Post by WinstonChurchill on 2010-07-20
> **mavericknik said:**
> Hey guys, so i just got a new internet connection from the local service provider. While installation, he insisted that i use my mobile number as the wpa password for the wifi. From what Ive heard, this is company policy. Im a little skeptical about this as ive read wpa is crackable using a dictionary if the password is in there. So i looked around and found the air-crack suite to test the security for my access point. As my password is only numeric, i couldn't find only a numeric dictionary to use with air-crack. 

So, i would like to create a dictionary that has only 10 digits, and the first two digit should be "05", because thats what mobile numbers here start from. I would be really grateful if anyone could point me to a way to do this easily. Thanks!The likely explanation is that your ISP realized that they could fire 10 customer service reps if they eliminated all the calls about resetting WPA passwords, and some idiot had the brilliant idea that it should be phone numbers so customers wouldn't forget them. Of all computer businesses, you'd think ISP's would be the most with it, but sadly that never seems to be the case...

---

### Post by ldglance on 2011-04-03
for anyone still looking at numeric dictionaries and this comes up in google 

you may look at a few links here that answer this question 

crunch is a brute force that works extremely well 
[http://sourceforge.net/projects/crunch-wordlist/](http://sourceforge.net/projects/crunch-wordlist/)

if you pipe it in to pyrit (a GPU cracking program)

[https://code.google.com/p/pyrit/](https://code.google.com/p/pyrit/)

you can crack a 10 digit password extremely fast. 

if your just looking for a actual dictionary and not looking for creating the dictionary you can check out:

[http://www.torrenteen.com/torrent/2111522/WPA-word-list](http://www.torrenteen.com/torrent/2111522/WPA-word-list)

hope this helps future searchers. 

ldglance

---

### Post by spiky001 on 2011-04-03
See if this sed command helps [http://ubuntuforums.org/showpost.php?p=9960975&postcount=3](http://ubuntuforums.org/showpost.php?p=9960975&postcount=3)

---

