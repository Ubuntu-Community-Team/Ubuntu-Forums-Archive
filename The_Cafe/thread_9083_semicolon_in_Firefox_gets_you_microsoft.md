---
title: "semicolon in Firefox gets you microsoft?"
date: 2004-12-23
forum: The Cafe
---

### Post by chz on 2004-12-23
i dont know if this is the appropriate place to start a thread on this, but, moderators please redirect if so.

anyways, an interesting thing caught my attention earlier today while surfing the net. normally when i type in an address to the addy bar in firefox i type the entire [http://www.yadayada.com](http://www.yadayada.com). well, this one time, i typed the url to my webserver and all of a sudden microsoft.com, came up. I FREAKED, and was quick to judge my host, and started to get angry. i tried typing it in again, but then this time no problem. I tried to google to see if anybody else had this problem, but fortunately not, so i thought maybe my network sumhow got a hit from sumbody elses query (maybe the router was poisoned and it was sending packets to everybody and it was getting mixed...who knows). This all happened maybe a few months ago. 
 
i now am in california visiting family. a few minutes ago, im on my laptop showing my brother the wonders of ubuntu, how it works, the cleanliness and ease of use, etc. when he asks me to check out a site he is curious to see on firefox in linux. so i type away. and then all of a sudden, ITS BACK. went straight to microsoft.com. but how. he was shocked as was I, but he was more laughing as i was ticked. just to double check he hopped on his computer to see if the site was still up correctly and sure enough it was. i retyped the entire address and as i started the http entry i noticed the very top with a semicolon instead of the colon. so i typed in a random address not dealin with microsoft with the semicolon in place....and sure enough it went to microsoft.com. i told him to try it on his winXP mahcine with firefox and that too did the same thing. straight to microsoft.com. I'm assuming this is some kind of bug but have no idea where to go to inform the developers of this.

Has anybody else experienced this as well? also, does anybody know why this might be? i know to be careful, so its not a HUGE issue, but something for people to be aware of i gess.

---

### Post by CowPie on 2004-12-23
Do an I'm Feeling Lucky search for ";" on google, make the connection ! ;)

---

### Post by Quest-Master on 2004-12-23
That's one of the weirdest things I've seen in a while. o_O

---

### Post by jakeslife on 2004-12-23
There is a traitor at Mozilla.....burn the witches!

---

### Post by ubuntu_demon on 2004-12-24
Maybe your provider always redirects certain IP's to [www.microsoft.com](www.microsoft.com) ?

What kind of setup do you have ? 

Do you connect directly to the internet ? Do other people sharing the same provider have the same problem ?

That sort of things. Info needed :)

---

### Post by nocturn on 2004-12-24
[QUOTE=demon666_nl]Maybe your provider always redirects certain IP's to [www.microsoft.com](www.microsoft.com) ?

What kind of setup do you have ? 

Do you connect directly to the internet ? Do other people sharing the same provider have the same problem ?

That sort of things. Info needed :)[/QUOTE]


The cause is this (briefly mentioned in a post before).

FireFox passes the unknown url to your local google.
For some reasons, these queries in some google mirrors turn up microsoft.com as the first link.
So FireFox takes you there...

---

### Post by ubuntu_demon on 2004-12-24
[QUOTE=nocturn]The cause is this (briefly mentioned in a post before).

FireFox passes the unknown url to your local google.
For some reasons, these queries in some google mirrors turn up microsoft.com as the first link.
So FireFox takes you there...[/QUOTE]
 you said that already.
But did you check other people using the same provider ?

---

### Post by nocturn on 2004-12-24
[QUOTE=demon666_nl]you said that already.
But did you check other people using the same provider ?[/QUOTE]


Actually, CowPie said it, but...
There were stories about this on The Register and The Inquirer.

---

### Post by eBopBob on 2004-12-24
Wow... never knew that.
In Opera when you type http;//www.site.com say by accident, it redirects you to: [http://www.http.com/;//www.site.com](http://www.http.com/;//www.site.com)

Guess you'll have to be more careful next time. ;)

---

### Post by chz on 2004-12-24
[QUOTE=CowPie]Do an I'm Feeling Lucky search for ";" on google, make the connection ! ;)[/QUOTE]
 i tried doing the "im feeling lucky" search, didnt do the same thing as typing in a semicolon into the address bar. for instance, my webserver jadecell.com...if u type http;// (thats with a semicolon) jadecell.com itll take u directly to microsoft. but if u do the same thing in google's search with an I'm feeling lucky, it takes u straight to some sport site.

---

### Post by chz on 2004-12-24
[QUOTE=demon666_nl]Maybe your provider always redirects certain IP's to [www.microsoft.com](www.microsoft.com) ?

What kind of setup do you have ? 

Do you connect directly to the internet ? Do other people sharing the same provider have the same problem ?

That sort of things. Info needed :)[/QUOTE]
 sorry to double post, but i figure i answer ur questions.
its just a basic setup. when it first happened was on my school network connecting to the internet. when it happened earlier, it was on broadband dsl. i don't think the two are in any way related. its wierd for two totally different ISP's to do the exact same thing, UNLESS they maybe running IIS servers, and theres sum connection there....BUT, i think its not the ISP, its totally firefox, i had sum friends try it too across the US, and they too got the same thing.

---

### Post by ubuntu_demon on 2004-12-24
[QUOTE=chz]sorry to double post, but i figure i answer ur questions.
its just a basic setup. when it first happened was on my school network connecting to the internet. when it happened earlier, it was on broadband dsl. i don't think the two are in any way related. its wierd for two totally different ISP's to do the exact same thing, UNLESS they maybe running IIS servers, and theres sum connection there....BUT, i think its not the ISP, its totally firefox, i had sum friends try it too across the US, and they too got the same thing.[/QUOTE]
 It wasn't clear to me. I thought maybe your school is also your provider or something.

But it's strange.

---

### Post by eBopBob on 2004-12-24
> BUT, i think its not the ISP, its totally Firefox, i had sum friends try it too across the US, and they too got the same thing.
I'd have to agree - It's probably Firefox and not the ISP. The same thing happened to me, and for fun I told some friends and the same thing happy to them. I'm on Tiscali, one is on AOL and the others are on a mixture of Club Internet and Wanadoo.

---

### Post by matt on 2004-12-25
It's definitely not the ISP - I'm in Japan and get the same Microsoft redirect if I enter a semi-colon. Weird.

---

### Post by ubuntu_demon on 2004-12-25
[QUOTE=matt]It's definitely not the ISP - I'm in Japan and get the same Microsoft redirect if I enter a semi-colon. Weird.[/QUOTE]
 (offtopic in the christmas spirit) 

Japan has a lot of cool things!
I like anime (and sometimes I play go) :D

---

