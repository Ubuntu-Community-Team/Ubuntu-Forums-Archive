---
title: "A new approach to handling encryption"
date: 2011-07-17
forum: The Cafe
---

### Post by TimeDistort12 on 2011-07-17
There is currently a problem with the way modern web browsers presents security and I strongly feel that this needs to change.

If I create a self-signed certificate for my server and someone comes to my website, most browsers warn the client that the site is "insecure". This is NOT TRUE!
Whilst my website would not be authenticated by a CA against a man-in-the-middle attack, the connection between my server and the client is encrypted, THEREFORE, there is the presents of security!

An encrypted connection and a trusted certificate are two different things. Right now, common browsers are treating HTTPS as if there is no trusted certificate then all fails! and this is wrong!

What needs to be introduced is something different, perhaps like this:

Encryption icon:
World - not secure
Gold padlock - secure

Certificate icon:
(something) - no verification
Red certificate - invalid certificate
Orange certificate - self signed certificate
Green certificate - trusted certificate

This way, people don't have to folk out cash if they want to supply a secure website, without browsers vomiting up a screen saying "wowoww watch out!!!"

I will be delivering this suggestion to Google, Microsoft, Mozilla, ad Opera in regards to their browsers.
Hopefully, we can all participate in my idea and have a new standard of browser security presentation.

... all input on my idea is welcome.

---

### Post by haqking on 2011-07-17
wont happen.

And you saying your certificate is secure because you say it is does not make it so.

If people who know you personally accept the certificate then fine, but for people who dont know you they may not.

This is why we have trusted cert authorities.

---

### Post by PartisanEntity on 2011-07-17
No way that is going to happen.

As per your idea, an orange flag means that all is well. This would create many problems of phishing attacks and could confuse normal end users who are not technically versed.

Many people would become victims of fraud because they would assume that all they have to watch out for is the red flag.

The current solution, while it may be semantically confusing, is better because it makes it harder to obtain a green flag in terms of certificate signing and authentication.

Your idea would reduce the obstacles needed to get authentication and certification even thought it makes sense semantically, it's not a good way to go IMO.

---

### Post by TimeDistort12 on 2011-07-17
> **haqking said:**
> wont happen.wont happen.

Only if people continue to think like this.


> **haqking said:**
> And you saying your certificate is secure because you say it is does not make it so.

Yes. I would only trust a self-signed certificates if the webmaster physically handed it over to me on storage medium.


> **PartisanEntity said:**
> No way that is going to happen.

If people continue to say this, then it may not.


> **PartisanEntity said:**
> As per your idea, an orange flag means that all is well. This would create many problems of phishing attacks and could confuse normal end users who are not technically versed.

Many people would become victims of fraud because they would assume that all they have to watch out for is the red flag.

I understand where you are coming from in regards to end-users not being technicall versed, but I do not think that security should suffer because the end-users does not understand computers well.

Bluntly, if people cannot grasp computers, I'm sorry but too bad. Computer enthusiasts should not have to suffer in their own world because of them.


> **PartisanEntity said:**
> The current solution, while it may be semantically confusing, is better because it makes it harder to obtain a green flag in terms of certificate signing and authentication.

My idea does not get rid of CA's, but it means browsers will treat an encrypted connection and certificate as two security entities.. ridding the current model where if the certificate is not trusted, the browser pops up a message saying the website is unsafe - ignoring the encrypted connection.
This way, people don't have to folk out cash if they want to supply a secure website, without browsers vomiting up a screen saying "wowoww watch out!!!"

---

### Post by ssam on 2011-07-17
why do you want encryption? i guess so that when alice logs on to the site from a public wifi point, eve can snoop in and see the data being transmitted.

now if eve has can control the access point, or pretend to be the access point, or trick you into using her DNS server, then she can sever alice a website that looks just like yours. if this fake site has a self signed certificate then it is by your definition encrypted and safe.

so with an untrusted certificate, you have no idea who can read the data while in transit, which is not much better than no encryption at all.

---

### Post by Bandit on 2011-07-17
> **TimeDistort12 said:**
> There is currently a problem with the way modern web browsers presents security and I strongly feel that this needs to change.

If I create a self-signed certificate for my server and someone comes to my website, most browsers warn the client that the site is "insecure". This is NOT TRUE!
Whilst my website would not be authenticated by a CA against a man-in-the-middle attack, the connection between my server and the client is encrypted, THEREFORE, there is the presents of security!

An encrypted connection and a trusted certificate are two different things. Right now, common browsers are treating HTTPS as if there is no trusted certificate then all fails! and this is wrong!

What needs to be introduced is something different, perhaps like this:

Encryption icon:
World - not secure
Gold padlock - secure

Certificate icon:
(something) - no verification
Red certificate - invalid certificate
Orange certificate - self signed certificate
Green certificate - trusted certificate

This way, people don't have to folk out cash if they want to supply a secure website, without browsers vomiting up a screen saying "wowoww watch out!!!"

I will be delivering this suggestion to Google, Microsoft, Mozilla, ad Opera in regards to their browsers.
Hopefully, we can all participate in my idea and have a new standard of browser security presentation.

... all input on my idea is welcome.

Since I am still really sleepy this morning. I am going to point you [HERE]("http://en.wikipedia.org/wiki/HTTP_Secure") and let you reevaluate what you mentioned above.

---

### Post by v8YKxgHe on 2011-07-17
TimeDistort12, it really would never happen because what you're suggesting implies a false sense of security and is very dangerous.

"security" is not one thing, it's a layer of things and by doing this you're removing one important layer. Sure, the client-server connection may very well be technically "secure", however what the server then does with the data I've just given it could very well not be secure and of malicious intent.

Lets say with your suggestion I setup a self-signed certificate for a common name of a well known bank here in the UK, on top of that I then manage to poison the DNS of my intended victims. With your suggestion, they would be able to visit this incredibly insecure website where they are about to enter in the bank account details - with the only warning being a little orange icon, of which a total of zero people will notice. However with the current model, the users browser will scream and shout that something is not right here.

Your suggestion is flawed and reduces security. SSL/TLS certificates are not that expensive, hop onto [http://www.trustico.co.uk/](http://www.trustico.co.uk/) and you can get a GeoTrust from £34.99, a Thawte from £69.00 and many more.

---

### Post by Bachstelze on 2011-07-17
> **TimeDistort12 said:**
> 
If I create a self-signed certificate for my server and someone comes to my website, most browsers warn the client that the site is "insecure". This is NOT TRUE!

I don't know about other browsers, but Firefox 5 warns that the connection is "untrusted". This is perfectly correct. If you trust the connection, you add the certificate to the list of trusted CAs, and the message will not appear.

Unsuccessful troll is unsuccessful, but thanks for trying.

---

### Post by juancarlospaco on 2011-07-17
HTML5 got its own KEYGEN tag, very interesting...  :)

---

### Post by dirtrider1 on 2011-07-18
I actually tend to agree with the OP, as a self signed certificate is just as unreadable and encrypted from point to point as any cert from a "trusted" certificate authentication service and most browsers incorrectly state that it is not. While with large well known sites verification by third party may be needed to an extent for protection against scam's, most web browsing is still somewhat an act of faith. A trusted certificate in no way guarantees that you are 100% percent secure. A signed certificate mean's a third party verifies who you say you are but if no one know's who you are or who your business is what difference does it make? That's where user feedback comes in with add ons like WOT. Verification now a day's is a very easy process with many so called Authority's and with very little actual authentication.

---

### Post by jhonan on 2011-07-18
There are two main things the certificate attests to;

1) You have established an encrypted connection to a website
AND
2) The website in question is 'trusted' and verified by a 3rd party

Sure, you can tell the end-user they've got a secure connection to your website, but not everyone should be able to tell them 'you can trust me, honest!' - Otherwise every phisher in the universe would be generating a 'self-signed' certificate as step one, rendering certificates useless.

---

### Post by Grenage on 2011-07-18
As above; such a system would both lower security and increase end-user confusion, whist offering nothing positive.  About the only time this is a problem is when an individual or company doesn't want to shell out a little money on an (admittedly overpriced) certificate.

---

### Post by uRock on 2011-07-18
> **TimeDistort12 said:**
> This way, people don't have to fo**r**k out cash if they want to supply a secure website, without browsers vomiting up a screen saying "wowoww watch out!!!"

ftfy

I think the reasoning against this has already been covered well enough in the posts above.

---

### Post by undecim on 2011-07-18
1: End users don't give a damn about certificates. They want to know if their connection is secure or not. They don't want five different measures of security, then want a boolean answer to "Is this site secure?"

2: If you don't have a certificate, then your connection is not secure. There is nothing stopping me from having people on my network (or any network I have gained unauthorized access to) connect to my server instead of yours. That's what a certificate does. Without it, I can just forward them to your server while reading the plaintext information.

Saying that a self-signed certificate is a presence of security is like saying your house is secure because you put a lock on your door, while leaving your window open. If I want in your house, I'm going to ignore the lock and go through your window

---

### Post by uRock on 2011-07-18
> **undecim said:**
> 
Saying that a self-signed certificate is a presence of security is like saying your house is secure because you put a lock on your door, while leaving your window open. If I want in your house, I'm going to ignore the lock and go through your window

And get chomped on by my four legged alarm system, lol. 

Seriously, I agree with your whole post. I wanna see VeriSign or one of the other major providers, when I go to log into a site.

---

### Post by DoubleClicker on 2011-07-18
A better solution would be a free, community supported signing authority.

---

### Post by Grenage on 2011-07-18
> **DoubleClicker said:**
> A better solution would be a free, community supported signing authority.

The reality is, that companies might not actually trust it unless it was paid for.

---

### Post by DoubleClicker on 2011-07-18
> **Grenage said:**
> The reality is, that companies might not actually trust it unless it was paid for.

Why is that an issue?  Those companies can buy certificates from Verisign.

---

### Post by undecim on 2011-07-18
> **Grenage said:**
> The reality is, that companies might not actually trust it unless it was paid for.

I would gladly receive payment for creating certificates for people.

Something like a web of trust would be a good idea, at least for those who can't afford VeriSign

---

### Post by Npl on 2011-07-18
> **DoubleClicker said:**
> A better solution would be a free, community supported signing authority.whats "community supported authority"?
Either one entity is giving out certificates (for free or paid) or there is really no sense in doing it.

And if certificates are just given out to anyone, this will defeat the purpose aswell. with payment you have atleast some kind of information who you are dealing with, also if you need further verification then having the funds to do so helps. Otherwise, what would stop me to get certs for the whole Simpson family?

Btw, Opera already works kinda like the OP requests - you get a lock for a "secure connection", and if the site got a proveable valid certificate its green. You can click on the symbol to get additional information. Unless I misunderstood something and he meant it should be "green" for just about ANY certificate...

---

### Post by Bachstelze on 2011-07-18
> **undecim said:**
> 
Saying that a self-signed certificate is a presence of security is like saying your house is secure because you put a lock on your door, while leaving your window open. If I want in your house, I'm going to ignore the lock and go through your window

Very bad analogy. A better one would be: saying a self-signed certificate is secure is like giving everyone the key to your lock and still saying it's secure. (Still not perfect, but better.)

---

### Post by undecim on 2011-07-18
> **Bachstelze said:**
> Very bad analogy. A better one would be: saying a self-signed certificate is secure is like giving everyone the key to your lock and still saying it's secure. (Still not perfect, but better.)

Mechanics of it don't matter. The point was that if you neglect one part of your security, the rest don't matter.

---

