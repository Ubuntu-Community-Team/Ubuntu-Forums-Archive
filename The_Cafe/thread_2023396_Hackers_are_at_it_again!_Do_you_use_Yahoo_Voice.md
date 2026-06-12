---
title: "Hackers are at it again! Do you use Yahoo Voice?"
date: 2012-07-12
forum: The Cafe
---

### Post by sharathpaps on 2012-07-12
[http://ibnlive.in.com/news/yahoo-hacked-45-lakh-passwords-reportedly-posted-online/270871-11.html](http://ibnlive.in.com/news/yahoo-hacked-45-lakh-passwords-reportedly-posted-online/270871-11.html)

---

### Post by irv on 2012-07-12
> The beleaguered Internet company Yahoo! has another crisis on its hands: 450,000 user email addresses and passwords stolen from its user-generated content service, Yahoo! Voices.

**[SIZE="3"][450,000 Yahoo Voice passwords stolen in data breach]("http://today.msnbc.msn.com/id/48160193/ns/technology_and_science-security/#.T_8NjuErrsc")[/SIZE]**

---

### Post by MG&amp;TL on 2012-07-12
Thanks for the heads-up. I just forwarded this to my mum, who does.

"Hackers are **added** again"?

---

### Post by Primefalcon on 2012-07-12
> **MG&TL said:**
> Thanks for the heads-up. I just forwarded this to my mum, who does.

"Hackers are **added** again"?
hmm and I am guessing one yahoo account to rule the yahoo services... if you use mail or anything at all.... change your password

---

### Post by Paqman on 2012-07-12
> **MG&TL said:**
> 
"Hackers are **added** again"?

Presumably: "Hackers are at it again".

---

### Post by Primefalcon on 2012-07-12
> **Paqman said:**
> Presumably: "Hackers are at it again".
That's what I assumed he meant......

---

### Post by irv on 2012-07-12
I also posted this on facebook because some of my family and friends have yahoo accounts. I don't. I try to keep my online accounts down. I don't have accounts all over the place. I do have some, so I try to keep an eye on them. I also check my online bank account everyday to make sure someone hasn't Hacked into it or got a hold of my cc number. (only one and one debit).

---

### Post by irv on 2012-07-12
> **Primefalcon said:**
> That's what I assumed he meant......

Yes that's what I meant. I had a brain freeze again. Hoping someone could fix this.

---

### Post by CharlesA on 2012-07-12
> **irv said:**
> Yes that's what I meant. I had a brain freeze again. Hoping someone could fix this.
Fixed :-)

I'll be changing my yahoo password and letting others know too.

Thanks!

---

### Post by irv on 2012-07-12
Another update. The count has gone up.
[SIZE="3"]**[Hackers expose 453,000 credentials allegedly taken from Yahoo service (Updated)]("http://arstechnica.com/security/2012/07/yahoo-service-hacked/")**[/SIZE]

EDIT: I would like to add this quote from the above link. It is important, please read.
> The dump, posted on a public website by a hacking collective known as D33Ds Company, said it penetrated the Yahoo subdomain using what's known as a union-based SQL injection. The hacking technique preys on poorly secured Web applications that don't properly scrutinize text entered into search boxes and other user input fields. By injecting powerful database commands into them, attackers can trick back-end servers into dumping huge amounts of sensitive information.

To support their claim, the hackers posted what they said were the plaintext credentials for 453,492 Yahoo accounts, more than 2,700 database table or column names, and 298 MySQL variables, all of which they claim to have obtained in the exploit.

"We hope that the parties responsible for managing the security of this subdomain will take this as a wake-up call, and not as a threat," a brief note at the end of the dump stated. "There have been many security holes exploited in webservers belonging to Yahoo! Inc. that have caused far greater damage than our disclosure. Please do not take them lightly. The subdomain and vulnerable parameters have not been posted to avoid further damage."

---

### Post by KiwiNZ on 2012-07-12
Its incredible that the scum who did this try to justify their criminal activity by asserting it was done for the public good.

---

### Post by Primefalcon on 2012-07-12
nothing new, look at the sony hack, how many times did they get hacked before they ended up fixing their systems...

---

### Post by irv on 2012-07-12
> **KiwiNZ said:**
> Its incredible that the scum who did this try to justify their criminal activity by asserting it was done for the public good.

Hope he's not a Linux user, it would give us Linux users a bad name.

---

### Post by CharlesA on 2012-07-12
> **KiwiNZ said:**
> Its incredible that the scum who did this try to justify their criminal activity by asserting it was done for the public good.
Indeed. Not sure if I am more annoyed with the haxxors or with Yahoo for not sanitizing their DB inputs and encrypting their passwords..

---

### Post by Primefalcon on 2012-07-12
> **CharlesA said:**
> Indeed. Not sure if I am more annoyed with the haxxors or with Yahoo for not sanitizing their DB inputs and encrypting their passwords..
Yahoo myself... since this isn't new for Yahoo... they should of learned by now

---

### Post by nec207 on 2012-07-12
> **irv said:**
> **[SIZE=3][450,000 Yahoo Voice passwords stolen in data breach]("http://today.msnbc.msn.com/id/48160193/ns/technology_and_science-security/#.T_8NjuErrsc")[/SIZE]**
 
How did this happan ? No way 2 or 5 hackers hacked 450,000 yahoo accounts .

---

### Post by Primefalcon on 2012-07-12
> **nec207 said:**
> How did this happan ? No way 2 or 5 hackers hacked 450,000 yahoo accounts .
sure they did, they spq injected, probally saved the output of the sql database in a plain text file which would only be something like 45 megs or less and bang 45k user and passwords ready to upload to forums and such

once they had the sql databse all they would of had to do was sumbit something along the lines of....

Select username, password FROM accounts

and it literally would of outputted all the data for the hackers to save..... and since it was all plain text and no encryption there was no bruteforcing hashes... or anything....

---

### Post by CharlesA on 2012-07-12
> **nec207 said:**
> How did this happan ? No way 2 or 5 hackers hacked 450,000 yahoo accounts .
The article mentions SQL injection.

---

### Post by nec207 on 2012-07-12
> **CharlesA said:**
> The article mentions SQL injection.
 
What is SQL or SQL injection .
 
 
That is why passwords need to be 6 to 12 characters long

---

### Post by MG&amp;TL on 2012-07-12
> **nec207 said:**
> What is SQL or SQL injection .
 
 
That is why passwords need to be 6 to 12 characters long

Wouldn't make a difference. SQL injection is where a user is able to use an input to directly query a database, resulting in a data dump of said database.

[http://en.wikipedia.org/wiki/SQL_injection](http://en.wikipedia.org/wiki/SQL_injection)

---

### Post by Primefalcon on 2012-07-12
> **nec207 said:**
> What is SQL or SQL injection .
 
 
That is why passwords need to be 6 to 12 characters long
it wouldn't of mattered what length the passwords were....

and SQL is a database, and it basically happened because yahoo wasn't sanitizing user input for malformed...

a user probably hacked the database via a form asking to register or even a search box...

---

### Post by Paqman on 2012-07-12
> **nec207 said:**
> How did this happan ? No way 2 or 5 hackers hacked 450,000 yahoo accounts .

They didn't hack 450,000 accounts, they hacked the database(s) that contained the account details.

---

### Post by CharlesA on 2012-07-12
> **Paqman said:**
> They didn't hack 450,000 accounts, they hacked the database(s) that contained the account details.
Yep. SQL dump via an SQL injection renders password length meaningless, especially if those passwords were stored in plain-text. :|

---

### Post by irv on 2012-07-12
This was easy to do because of the big hole in their system. Just tricked the database into giving them the information by submitting SQL commands in a user form and got the data. Simply put.

---

### Post by CharlesA on 2012-07-12
Mandatory XKCD:
[http://xkcd.com/327/](http://xkcd.com/327/)

---

### Post by nec207 on 2012-07-12
> **Primefalcon said:**
> it wouldn't of mattered what length the passwords were....
 
and SQL is a database, and it basically happened because yahoo wasn't sanitizing user input for malformed...
 
a user probably hacked the database via a form asking to register or even a search box...
 
But how would yahoo allow some thing like that hapen?  Why would the database allow requests.

---

### Post by irv on 2012-07-12
> **CharlesA said:**
> Mandatory XKCD:
[http://xkcd.com/327/](http://xkcd.com/327/)

Very good humor. :D

---

### Post by Paqman on 2012-07-12
> **nec207 said:**
> But how would yahoo allow some thing like that hapen?  Why would the database allow requests.

Perhaps they didn't intend it to work like that.

---

### Post by nec207 on 2012-07-12
Reading the link it was only voice-over-Internet-protocol, or VOIP  not the other yahoo service.
 
>  
 
The affected accounts appeared to belong to a voice-over-Internet-protocol, or VOIP, service called Yahoo Voices, which runs on Yahoo's instant messenger. The Voices service is powered by Jajah, a VOIP platform that was bought by Telefonica Europe BV in 2010. 


---

### Post by MG&amp;TL on 2012-07-12
> **nec207 said:**
> Reading the link it was only voice-over-Internet-protocol, or VOIP  not the other yahoo service.

Yes, but unless I'm mistaken, Yahoo! uses the same password for everything. So if you use their VOIP service, the rest of your account is compromised as well.

---

### Post by Primefalcon on 2012-07-12
> **MG&TL said:**
> Yes, but unless I'm mistaken, Yahoo! uses the same password for everything. So if you use their VOIP service, the rest of your account is compromised as well.
and if yo create a mail account you have an account for voice...... since its your yahoo account

---

### Post by MG&amp;TL on 2012-07-12
> **Primefalcon said:**
> and if yo create a mail account you have an account for voice...... since its your yahoo account

Since they only cracked the VoIP databases, my guess is that you have to use their VoIP service to have a record on there. They could use a separate database to, say, record the last conversation.

But I'm telling my brother to change his password too now. He doesn't use the VoIP service.

---

### Post by Primefalcon on 2012-07-12
> **MG&TL said:**
> Since they only cracked the VoIP databases, my guess is that you have to use their VoIP service to have a record on there. They could use a separate database to, say, record the last conversation.

But I'm telling my brother to change his password too now. He doesn't use the VoIP service.
it's possible that's the case, but I wouldn't risk it

---

### Post by skellat on 2012-07-12
Yahoo! has a service for VoIP?  I hadn't heard of it even existing before this!

---

### Post by lisati on 2012-07-12
"Yahoo" speaks volumes. These are people whose help pages and abuse reporting systems assume that you're using a Yahoo mail account to report spam that arrives at that particular email account, and which gives little to no help to people who use other email providers and who wish to report spam arriving from Yahoo.

*mutter mutter mutter*

---

### Post by Ubun2to on 2012-07-12
My flash drive: SHA512 encryption.
Yahoo: no encryption.
Kinda amazing how dumb they are.

---

### Post by nec207 on 2012-07-13
> **MG&TL said:**
> Yes, but unless I'm mistaken, Yahoo! uses the same password for everything. So if you use their VOIP service, the rest of your account is compromised as well.
 
Yes if you have yahoo account and use VOIP service all you account they have your password do to it is the same.
 
If you have yahoo account and do not use VOIP service you okay.
 
 
They must have hacked into yahoo computer and clicked on database that had no password to open the database program.Than some how copy the data too their computer.

---

### Post by CharlesA on 2012-07-13
In any case, it is better to change your password "just in case" instead of being hopefully that is is not compromised.

---

### Post by Primefalcon on 2012-07-13
> **CharlesA said:**
> In any case, it is better to change your password "just in case" instead of being hopefully that is is not compromised.
agreed, to help theres now a tool out there to check whether you've been hacked or not

[http://labs.sucuri.net/?yahooleak](http://labs.sucuri.net/?yahooleak)

---

### Post by MG&amp;TL on 2012-07-13
> **CharlesA said:**
> In any case, it is better to change your password "just in case" instead of being hopefully that is is not compromised.

Of course. I was merely speculating. The sensible thing to do is to change passwords regularly anyway, but especially so if you suspect the account has been compromised.

---

### Post by CharlesA on 2012-07-13
> **MG&TL said:**
> Of course. I was merely speculating. The sensible thing to do is to change passwords regularly anyway, but especially so if you suspect the account has been compromised.
Yep. :)

---

### Post by irv on 2012-07-14
[SIZE="3"]**[Five online services were breached this week]("http://securitywatch.pcmag.com/none/300262-breach-week-2-androidforum-yahoo-nvidia-formspring")**[/SIZE]
More then just Yahoo. Breach Week 2: AndroidForum, Yahoo, NVIDIA, Formspring
[ATTACH]221254[/ATTACH]

EDIT:  [Android Forums Now Back to Full Operation After Hacking Incident]("http://thedroidguy.com/2012/07/android-forums-now-back-to-full-operation-after-hacking-incident/")

---

### Post by CharlesA on 2012-07-14
Sheesh!

---

### Post by Irihapeti on 2012-07-14
And people want us to entrust everything to the cloud???

Sorry, won't be joining them.

---

### Post by Ubun2to on 2012-07-15
> **Irihapeti said:**
> And people want us to entrust everything to the cloud???

Sorry, won't be joining them.

I agree. Especially when you consider how pricey a good high speed connection is-that is what you need to take full advantage of the cloud. I don't have a good high speed connection ATM (too little competition where I live allows CenturyLink to charge whatever it wants), and I don't trust big companies security systems, either.

---

### Post by mr john on 2012-07-15
Bring back Geocities!!!

---

### Post by Lucradia on 2012-07-15
I have never used Yahoo Voice.

---

### Post by irv on 2012-07-16
I had to laugh when I saw this one. Sounds like some people I know.
[ATTACH]221337[/ATTACH]

---

