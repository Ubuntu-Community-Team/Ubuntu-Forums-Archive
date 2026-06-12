---
title: "Can encryption beat a man in the middle?"
date: 2009-11-17
forum: Security
---

### Post by Ulysses_ on 2009-11-17
If I could get physical access to a server and store a few GB of really random text on the server, or somehow store it when there is NO man in the middle, I could then program a special proxy in the server whereby the link between me and the proxy would be encrypted with the one-time pad method, ie by simply XORing the random text with the data.  Then it is impossible to break the encryption, but it is also impossible for the man in the middle to harm me by directing me to another server of theirs, because that other server does not have a copy of the secret random text so there can be no communication.  1. Can the same be achieved by conventional encryption schemes like SSL or PGP when I do NOT have physical access to a server that provides an encrypted proxy service?  2. Can a conventional authentication take place somewhere where there is no man in the middle, at a cafe or something, and then continue my access at a place where I know there is a man in the middle to any access to the internet?

---

### Post by Zhwazi on 2009-11-18
> **Ulysses_ said:**
> If I could get physical access to a server and store a few GB of really random text on the server, or somehow store it when there is NO man in the middle, I could then program a special proxy in the server whereby the link between me and the proxy would be encrypted with the one-time pad method, ie by simply XORing the random text with the data.  Then it is impossible to break the encryption, but it is also impossible for the man in the middle to harm me by directing me to another server of theirs, because that other server does not have a copy of the secret random text so there can be no communication.  1. Can the same be achieved by conventional encryption schemes like SSL or PGP when I do NOT have physical access to a server that provides an encrypted proxy service?  2. Can a conventional authentication take place somewhere where there is no man in the middle, at a cafe or something, and then continue my access at a place where I know there is a man in the middle to any access to the internet?

SSL and PGP have key signing and certificates. And what you're talking about is pre-sharing the key, so there's no way for a man to get into the middle, and if someone tries to use a different key it's detected, and that's built into to any encryption implementation I've worked with, including SSL and PGP, and that does defeat man-in-the-middle attacks. The simple way around man in the middle is don't use keys unless you're certain where they came from.

---

### Post by osjak on 2009-11-20
Ulysses_, secure communication between servers is a very old problem in computing. Your idea of pre-shared key has a good base, but there are more advanced ways to communicate safely now. I'm not sure if you set up your link by hand, or writing a script, but in any case you can use the SSH to connect you to your server using keys as your authentication method (don't use passwords!). It will establish a secure link to your server and no man in the middle can read your data. This is a very secure and well tested method. You set it up once and then can use from any location.

---

### Post by Agent ME on 2009-11-20
Public key cryptography can beat any eavesdropper. (However, a real man-in-the-middle who knows what you're doing and can change messages between you and another person can mess things up a bit, but any changes made are obvious if you double-check the keys through another channel.)

Here's a post I recently made somewhere else describing the ideas to public key cryptography, hopefully you'll find it interesting: [http://www.reddit.com/r/AskReddit/comments/a5rxl/what_is_a_concept_that_has_been_explained_to_you/c0fzocm](http://www.reddit.com/r/AskReddit/comments/a5rxl/what_is_a_concept_that_has_been_explained_to_you/c0fzocm)

SSH is one of the most common and powerful tools to use to securely connect to a server or another computer. (I often SSH into my home computer to grab files or run commands.)

Other tools: If you want to set up a general use web server with a secure connection, look into HTTPS. If you want to encrypt specific files, look at GPG. If you want to encrypt a specific folder of files on your hard drive (such as personal data and configuration settings), look into EcryptFS. If you want to encrypt an entire hard drive, look into Ubuntu's Alternate Installer's Encrypted LVM option.

---

### Post by Ulysses_ on 2009-11-21
> **osjak said:**
> you can use the SSH to connect you to your server using keys as your authentication method (don't use passwords!). It will establish a secure link to your server and no man in the middle can read your data. This is a very secure and well tested method. You set it up once and then can use from any location.

Could you explain this please, what am I supposed to do.  Other people tell me:

"SSH and others are susceptible to man-in-the-middle attack during the initial connection. Certificates were supposed to take care of that possibility."

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
>  "SSH and others are susceptible to man-in-the-middle attack during the initial connection. SSHv1 was. But these days everything is SSHv2.

Are you still trying to spread panic? :D

---

### Post by Ulysses_ on 2009-11-21
What I want to do is access the internet through a SOCKS proxy that I connect to via an encrypted connection (as if I had a VPN between me and the proxy).

I have seriously considered physically mailing DVDs of truly random data to a provider of a free unix account, if I find one that allows me to do that.  Then there would be no concerns about MITM attacks during the initial connection that SSL suffers from, my key would be physically pre-shared, and no computing power would be able to break my one-time-pad encryption.

---

### Post by Ulysses_ on 2009-11-21
> **scorp123 said:**
> SSHv1 was. But these days everything is SSHv2.

Why do you believe he says afterwards "certificates were supposed to take care of that".  Not taking care of it very well perhaps? ;)

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
> Why do you believe he says afterwards "certificates were supposed to take care of that".  Not taking care of it very well perhaps? ;)

Getting a succesful MITM attack against SSHv2 to work is several times more complex than against SSHv1. The real problem are things like the certificates themselves and potentially weak passphrases. There was a really stupid bug recently in all Debian-based distributions that had a severe impact on the complexity of SSL and SSH keys ... rendering them by far less complex than they should be. So if anyone used such a certificate that was created on a buggy system then an intruder might get lucky and be able to "guess" things because the complexity is drastically reduced.

But on a healthy + patched system I'd have my doubts that such an attack would be succesful.

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
>  Then there would be no concerns about MITM attacks during the initial connection that SSL suffers from, my key would be physically pre-shared, and no computing power would be able to break my one-time-pad encryption. And what's wrong with SSHv2 and passphrases? Or OpenVPN? IPsec?

What's next on your plan? Invent something that turns carbon-based matter into hot gas and then call it "fire"? Invent a rotary transport mechanism and then call it "wheel" ... ? Those things have already been invented, you know? :D

---

### Post by Ulysses_ on 2009-11-21
Well if you feel I have presented pre-sharing of keys and the one-time-pad as something brand new, clearly your reading comprehension is not at its best today and I suggest getting some sleep or something, cause it gets tiresome.

---

### Post by scorp123 on 2009-11-21
Edit:

You really need to take it easier ... :D

---

### Post by Ulysses_ on 2009-11-21
Sleep-deprived indeed.

---

### Post by Ulysses_ on 2009-11-21
Hey! Don't delete what you write! :)

---

### Post by Ulysses_ on 2009-11-21
(Here's what you deleted):

> [quote]Well if you feel I have presented pre-sharing of keys and the one-time-pad as something brand new"Brand-new"?? LOL :D :D :D

[http://www.rsa.com/node.aspx?id=1156](http://www.rsa.com/node.aspx?id=1156)

[http://www.cryptocard.com/](http://www.cryptocard.com/)


Quod erat demonstrandum.[/quote]

---

### Post by sgosnell on 2009-11-21
No, he's not saying those are brand-new.  He's saying that you're trying to re-invent the wheel and fire.  They've already been invented, and solutions for what you're worried about have also already been found, so you're really wasting your time.

---

### Post by scorp123 on 2009-11-21
> **sgosnell said:**
> No, he's not saying those are brand-new.  He's saying that you're trying to re-invent the wheel and fire.  They've already been invented, and solutions for what you're worried about have also already been found, so you're really wasting your time.

Thank you. So it seems I am speaking English well enough to be understood? Hah. 

:D

---

### Post by Ulysses_ on 2009-11-21
> **sgosnell said:**
> No, he's not saying those are brand-new.

He feels I am PRESENTING them as my brand-new inventions (therefore gives advise about re-inventing the wheel, "don't do that") when obviously nothing I said was brand new, neither did I present it so  So comments about re-inventing are not relevant.  

I have the right to question the effectiveness of the state of the art of LEGALLY ALLOWED security, or not?  Why is there a law against stronger encryption than AES-256 in SSL, and they are not allowed to use anything stronger in services they sell? ;)

---

### Post by sgosnell on 2009-11-21
It depends on where you are.  The legality of cryptography software varies by country.  Why do you need stronger encryption than AES-256?

---

### Post by scorp123 on 2009-11-21
> **Ulysses_ said:**
> Why is there a law against stronger encryption than AES-256 in SSL, and they are not allowed to use anything stronger in services they sell? ;)

As I said ... you need to take it easier. And I wrote before: Why not IPSec or --the part that I deleted because I felt it would be useless to mention but OK you mentioned it anyway-- secure ID tokens or other known-to-be-super-strong solutions??

And last time I checked AES-256 was regarded as being super-strong and super-hard to crack. I fail to see the need for SSL supporting anything "stronger". It would just add overhead and slow down the transmission of the actual payload. AES-256 is already so strong that it would take several millennia to decode a transmission with a well-chosen passphrase. Any further levels of encryption are redundant. Whether it takes 25'000'000 years to decypher a transmission or 45'000'000 years ... what's the difference? It won't be in our lifetimes anyway.

And sending out DVD's with random data and such ... Oh dear. If you have so many doubts about SSHv2 and anything else that already exists ... how come you trust the mail delivery service not to copy the DVD? Or how come you trust the recipient not to copy the DVD to other parties?

What's the next thread you will open? How to create self-destructing DVD's that destroy themselves after they have been used once for a SSH over SOCKS session?

Really. Take it easier.

There is nothing wrong in being interested in security but then again: this is a support forum. You don't seem to have any technical Linux problems at all and maybe you would be better served to take this discussion to some dark sinister IRC channel where the real black hats hang around? Because it seems nothing we write or say can satisfy you??

---

### Post by Ulysses_ on 2009-11-21
> **sgosnell said:**
> Why do you need stronger encryption than AES-256?

I don't need it.  Just making the point that security should be under scrutiny, not trust it and talk about it like a parrot, but adapt and play the game like a hacker would.

So do you understand the problem with certificates mentioned above, that I copied from someone else at linuxforums?  I really want to know what the problem with certificates is.

---

### Post by Ulysses_ on 2009-11-21
To scorp123 I am not going to reply any more, he's getting extremely personal, and trying to ridicule the topic and my person instead of doing what this forum is for.

---

### Post by sgosnell on 2009-11-21
Again, why are you so worried?  What data are you trying to transfer that is so vital?  You can't do anything about what you pass to and from secure sites like banks, paypal, etc, so either stop worrying or stop using them.

---

### Post by scorp123 on 2009-11-21
> **sgosnell said:**
> Again, why are you so worried?  What data are you trying to transfer that is so vital?  You can't do anything about what you pass to and from secure sites like banks, paypal, etc, so either stop worrying or stop using them. My thoughts exactly. :D

---

### Post by Ulysses_ on 2009-11-21
[quote=sgosnell]What data are you trying to transfer that is so vital?[quote]

For example today I got two messages from paypal that yahoo detected as "SPOOFED".  If I went to their links, I might end up... buying a stranger a big gift.  If I just went to paypal, I might already have a MITM going on using poisoned DNS.  A secure proxy beats all these possibilites, as long as you find the way to pre-share the keys.  Maybe at a cafe or something.  

So things can be done, and this forum is for support on such questions.  If you know, please contribute.  If not, do the decent thing.

---

### Post by Ulysses_ on 2009-11-21
> **sgosnell said:**
> What data are you trying to transfer that is so vital?

For example today I got two messages from paypal that yahoo detected as "SPOOFED".  If I went to their links, I might end up... buying a stranger a big gift.  If I just went to paypal, I might already have a MITM going on using poisoned DNS.  A secure proxy beats all these possibilities, as long as you find the way to pre-share the keys.  Maybe at a cafe or something.  

So things can be done, and this forum is for support on such questions.  If you know, please contribute.  If not, do the decent thing.

---

### Post by osjak on 2009-11-21
> **Ulysses_ said:**
> Could you explain this please, what am I supposed to do.
Just use the SSH as it is intended, nothing extra special is required. Here is a couple of links to help:
[OpenSSH Public Key Authentication]("http://sial.org/howto/openssh/publickey-auth/")
[OpenSSH key management]("http://www.ibm.com/developerworks/library/l-keyc.html")

> **Ulysses_ said:**
> 
  Other people tell me:

"SSH and others are susceptible to man-in-the-middle attack during the initial connection. Certificates were supposed to take care of that possibility."
It's hard to get into other person's head by reading a taken out of context quote. This is how SSH combats spoofing the name service:
> **3.10.2. Name Service and IP Spoofing**
If an attacker subverts your naming service (DNS, NIS, etc.), network-related programs may be coerced to connect to the wrong machine. Similarly, an attacker can impersonate a host by stealing use of its IP address(es). In either case, you're in trouble: your client program can connect to a false server that steals your password when you supply it. SSH guards against this attack by cryptographically verifying the server host identity. When setting up a session, the SSH client validates the server's host key against a local list associating server names and addresses with their keys. If the supplied host key doesn't match the one on the list, SSH complains. This feature may be disabled in less security-conscious settings if the warning messages get annoying. [Section 7.4.3.1, "Strict host key checking"] The SSH-2 protocol allows for including PKI certificates along with keys. In the future, we hope that implementation of this feature in SSH products along with more common deployment of PKI will ease the burden of key management and reduce the need for this particular security trade-off. 
[http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_10.htm](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_10.htm)

So if you ever used SSH before, you remember that when you connect to a server for the very first time, it will issue a statement saying that it cannot verify the server. After you agree to connect, SSH creates the host key, and from that time forward you can always be sure to connect to the right machine. I'm assuming the person you quoted was talking about this first connection. And there are two ways to solve that problem:
1. Make the very first connection from a safe network, OR
2. Verify the server identity via an SSL certificate, issued by a reputable authority.
You can do your research why SSL certificates usually work fine, but are not perfect (and they aren't), but that technology has nothing to do with SSH. So as long as you can make the first connection safely using either one of the above methods, you then can use SSH as a secure way of communication.

---

### Post by Ulysses_ on 2009-11-22
> **osjak said:**
> It's hard to get into other person's head by reading a taken out of context quote.

His context is exactly the same as here, he's responding to the same OP.  In a duplicate of this topic.

> This is how SSH combats spoofing the nae service:

[http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_10.htm](http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch03_10.htm)

> when you connect to a server for the very first time, it will issue a statement saying that it cannot verify the server.Then that's confirming what the quote is saying in its first sentence.  I therefore should go to a cafe or somewhere safe and use a brand new virtual machine to connect to all secure servers of interest just once.  

On the subject of option 2: certificates, I'm not going to physically go to any certificate issuing authority but I'll have to connect to that authority, and that connection can be MITM'ed, therefore we go back to the same need for a safe connection to get started with.  That's what he probably means by "certificates were SUPPOSED to fix that".

If I "Clear Private Data" in firefox, presumably any keys and other information I got in the first visit to a secure server is kept.  

Or is it not kept, but only certificates are kept?  

Either way, where is that information kept?

---

### Post by osjak on 2009-11-22
> **Ulysses_ said:**
> On the subject of option 2: certificates, I'm not going to physically go to any certificate issuing authority but I'll have to connect to that authority, and that connection can be MITM'ed, therefore we go back to the same need for a safe connection to get started with.  That's what he probably means by "certificates were SUPPOSED to fix that".
This is not how SSL works. You don't connect to any CA's directly. You ask the server you are trying to connect to for a certificate, it gives it to you, and then you verify it has been signed by a known authority using its key. The set of known keys comes with your SSL client by default. Browsers, as SSL clients, come with keys for well known CA's. So does any other SSL client.

---

### Post by Ulysses_ on 2009-11-24
In short, with certificates you still need a safe connection the first time, the only difference is that the first time is for good.  Stored in your computer until you... format it, right?

I'd like to know what is going on with firefox when you "Clear Private Data".  Any certificates should survive this, right?  

How do I know which certificates I have?

Is it possible that no certificates are being used for a given SSL server?  I'm only interested in two types of secure service, emails and anonymous proxy.

---

### Post by Agent ME on 2009-11-24
> **Ulysses_ said:**
> In short, with certificates you still need a safe connection the first time, the only difference is that the first time is for good.  Stored in your computer until you... format it, right?
No, that's how SSH (and non-certified SSL keys) work.

Certificates signed b a CA (certificate authority) get around the first connection problem. When you connect to the server, the the certificate it gives you has a signature from a CA (that can't be faked) which proves that the certificate was approved by the CA, and you're safe from any man-in-the-middle.

---

### Post by BkkBonanza on 2009-11-25
It's a basic principle of cryptography that unless you really know what you're doing and have a lot of genuine experience it's better not to create your own security systems. The reason is that beginners rarely see the flaws that experts find quickly. Generally, thinking that you can outsmart hackers more than security experts with years of background is not a good bet to take.

It sounds like you're looking for a way to use a secure proxy in a situation where you can't trust local traffic like in a cafe with wifi or an untrusted LAN.

The easiest and safest approach for this is to have access to a server account somewhere "safe" and use an SSL SOCKS proxy through that server. You can do this with a single SSH command on your notebook (or whatever local computer you are using). 

ssh -D 8080 user@server

Will create a SOCKS proxy on your machine (port 8080) and connect to the server machine and relay all connections to the world through that server. The connection between you and that proxy (which SSH creates for you as well) uses SSL. It is very simple and secure and for Ubuntu there is a useful little GUI app called gSTM for managing such a ssh proxies. I use them regularly and they work very well. (It even proxies p2p traffic well). 

You can also add a key to the server so that your connection is key based rather than passphrase. Also when you initially connect to the server you can verify it's authenticity and copy the server's key to your local machine so that any later connection will check the server key is correct. Any security method depends on some initial level of trust. In the case of a DVD by mail you are depending on the trustworthiness of the system admin not copying or otherwise forwarding the DVD contents. It would be smarter to have that admin send you the server key by DVD (or maybe encrypted email) so that you can verify your first connection to the server.

There are a few companies offering linux shell accounts and various proxy server accounts. Any linux shell account or VPS server account will typically be able to use ssh to create a secure SOCKS proxy, though some may disable that use if they are trying to prevent abuse. I use my web server VPS account when I need a secure connection out to a data center connected to a backbone. This is good at securing open wifi traffic or any traffic in an apartment building where you don't trust who may be listening in.

There has been a recent bug in the SSL protocol that could affect people under some conditions. That bug is being fixed right now and apparently a recent version of openssl already has a workaround in place.

BTW one of the nice things about the SSH proxy is that all traffic goes through the single connection to the server. In cases where local routers are not so capable and you are using P2P which opens hundreds of connections this is brilliant. For example, at my local cafe if I start P2P traffic with 200 connections then it bogs right down as the router can't cope. But with the SSH proxy only one connection is open and on the remote server all the P2P connections get opened - the local router doesn't bog down and I get good data rates.

---

### Post by Ulysses_ on 2009-11-25
Good post, BkkBonanza.  I was also considering using an anonymity service where you connect to their proxy over a secure connection.  They probably have a certificate.  In some other case I found someone offering a secure connection with a "self-signed certificate", ie one they made themselves without paying the certificate authority.  Presumably that is not safe for their customers, but why can't a proper certificate be faked?

---

### Post by Ulysses_ on 2009-11-25
Also, anyone can offer an anonymity service and even pay some money to a certificate authority, but still have a malicious intent.

---

### Post by BkkBonanza on 2009-11-25
Certificates can be faked if you aren't observant or careful.

What stops fakes from working for most web sites is that your browser ships with a set of certificates built in that are **trusted**. When you visit a site the browser gets a certificate from that site and looks in your trusted certificate store for the authority certificate that created that site's certificate. Then it checks that the certificate has been correctly signed by the authority expected using the embedded public key (in the certificate) from the authority. When the authority isn't in the browsers store then it warns you by telling you it doesn't recognize who issued it. Hence, it's telling you it doesn't trust the certificate the site provided. 

The same process is used for any SSL connection whether your browser or otherwise. Ubuntu ships with a set of trusted certificates just like a browser. Well, openssl does really. Look in /etc/ssl/certs and you'll see the certificates trusted by Ubuntu (openssl). You can add a certificate authority (CA) to your trusted store and then any certificates signed by this CA will be trusted.

If a user gets a warning by the browser that it doesn't trust the certificate and the user skips the warning (tells it to add an exception in Firefox) then the user is saying "just go ahead anyway". Well, if the site is spoofing the real site then yes, you just told your browser to communicate with the spoofed site using the fake certificate. A MITM attack would be a case where this is done via trickery or some hidden way. There are several "user engineering" approaches to trick users into accepting a bad certificate. 

I'm not expert enough to know about any hacks/technical tricks to do this at the ssl protocol level. This recent SSL bug was using something called re-negotiation that occurs after some time during an established SSL session. From what I've read the workaround was to disable re-negotiation until a real fix gets properly tested and distributed.

Using a self-signed certificate means you are using a certificate created by a CA that is not trusted (in the local store). You can tell your browser or other app to trust it anyway and if you know the issuer to be good then it's not inherently bad for the single certificate in question. I would not add a self signed CA to your trusted CA store for any random certificate unless you really, really trust that any certificate issued by this signor is universally valid. If *you* signed it and you are using it then fine. But joe blow at xyz corp could be signing all sorts of fake certificates without you knowing. If one happens to be for paypal and you added his CA then I think it's a serious breach. Don't add CA to your trusted store willy nilly. Firefox allows you to add specific exceptions for a site. Using the Prefs, Advanced, Security options you can also add certificates as CA too. Probably dangerous.

Anyway there is lots you can dig into in dealing with certificates. If you need a free one for your own use that is trusted by most browsers then I'd suggest StartCom at startssl.com. They are in most browser's trusted stores and offer free ssl certificates and client/email certificates. Also CaCert issues certificates but they aren't trusted in browsers. I've used them for my own stuff but really they are about as good as signing your own.

For SSH you use keys which are much the same as certificates but handled differently in different formats (as I recall anyway). To my knowledge the security handling and level of security is similar.

---

### Post by BkkBonanza on 2009-11-25
There was a story roughly a year ago about a reseller of Comodo (trusted) that was issuing certificates without properly verifying the buyer. The guy who runs StartCom went there and bought a certificate for mozilla.com. This was a serious breach and I believe that Comodo suspended the reseller and revoked the certificate. This doesn't seem to be a common occurence that I've heard but certainly there could be unknown things like this happening that represent risks. One wants to ask the question how that reseller was even able to sign a certificate on behalf of Comodo.

A CA is supposed to verify the buyer of a certiciate. The process they have in place for this is supposedly what has been audited and the reason why they have gained the trust to be included in most trusted CA stores (like IE, Firefox etc). How well that is done is certainly open to question but you would think that banks and online stores like amazon etc would have a great interest in making sure the CA that people use are in fact trustworthy. 

If you want to see which CAs you trust in Firefox you can select Prefs, Advanced, Encryption, Certificates, Authorities and view the list there. Quite a few really, the main ones being Verisign, Geotrust, Comodo, etc.

A CA usually has a few trust levels as well. You can buy a certificate for a domain name only if you own/control that domain. The CA will send confirmation email to the domain's registered email address only to check. If you spend more money then you can get a higher level by sending in corp docs and providing details to verify you really are the domain owner in question. This is what big name sites would do and those certificates have more detail indicating they are not just the correct site but also the verified corporation/person in question. When you look at any certificate indetail it tells you just how much has been verified when it was issued.

BTW the math behind certificates is public key cryptography. The owner of the certificate keeps the private key safe (we hope!) on their server and data vault. They send a CSR (cert signing request) to the CA to get a certificate issued. The CA never gets the private key and hence can't divulge it to others. The CA issues the certicate, which is the public key portion only, signed with the CA pricate key and can be sent to anyone. You trust it because you have the CA public key and can verify that it was signed by them on behalf of the certificate owner. It's pretty nice and has a track record going back many years as working despite the odd problem that comes up now and then. Without having some serious crypto chops the chances of figuring out a better system is slim.

Here's two interesting links - one on basic crypto and why you shouldn't roll your own and the other listing articles this well known "expert" has written. 

[http://www.schneier.com/essay-037.html](http://www.schneier.com/essay-037.html)

[http://www.schneier.com/essays-infosec.html](http://www.schneier.com/essays-infosec.html)

---

### Post by BkkBonanza on 2009-11-25
Regarding using a proxy service... 

You are always forced into trusting whoever runs that proxy. I have always used my own server for proxying for this reason. You can get a VPS (root access linux account) for $8/mo. (Seattle, WA) and up. I believe that is better than some of these other services because you have more control over the account and checking it thoroughly if you need to. 

On your own vps you can build SSH from scratch if you want. You can check and configure to suit your needs. You can run your own proxy software (though SSH has that built in) if you like and you can browse and check the source code if you want. SSH is used universally all over the web for secure server communications by almost every system admin / developer everywhere so it's pretty trusted and has been put through years of testing.

When you use a third party proxy (even if it's based on SSH) you are trusting they have not modified the code for the proxy to carry out data filtering/extraction. You are trusting them not to insert some malicious code that does who knows what. 

In theory they shouldn't be able to tamper with the SSL session data as it is encrypted in your browser and can only be decrypted by the server (using the private key) but there is certainly more potential for other forms of attack. If your DNS queries route through the proxy then they could be poisoned and you could be routed to a fake site and given fake certificates. You take that chance though it is likely slim. For example, I don't think I'd use proxies hosted in untrusted countries (Russia, Rommania etc) for secure banking traffic.

If you manage your own VPS server account hosted in a data center in Texas (as I do for $10/mo.) then I think you have a higher level of trust that the software on that server is trustworthy. After all, you can login and check it, you can build from source if you like, or you can at least use apt to verify the packages against known distribution keys. Once you know that the version of SSH installed is verified original you should be able to trust it.

---

### Post by Ulysses_ on 2009-11-25
What virtualization is a $10/mo VPS likely using, or do you recommend?  I am very familiar with vmware workstation, but VPS's based on that cost far more, don't they.

---

### Post by Ulysses_ on 2009-11-25
On second thought, a VPS of my own would be a little more vulnerable to hackers keen to penetrate it.  

How do those free services of anonymity fare in terms of defences against hackers breaking into?

By the way, does google provide anything like an anonymity service, free or paid-for?

---

### Post by BkkBonanza on 2009-11-25
The lowest price VPSs typically use OpenVPS. This is the open source version of Virtuozzo. Both are well suited for running many VM at the same time in server farm type applications as they have very little overhead. It is used by millions of web sites / servers around the world. 

The answer to your question about vulnerabilities is unknowable. Certainly no server admin is going to publish details about whether or how they got hacked. To be frank, there is a point where paranoia becomes debilitating and you have simply not use the net. You can never know for sure that you are 100% secure. Just about every network device, router, and server on the web today (based on Linux or BSD) uses ssh for secure access and admin. And I'm pretty sure that Google is no more perfect than the rest - even less so since they are very clearly a desirable target whereas people like you or me are not even known as targets, and Google too uses ssh for server management. If you take a reasonable level of care in managing a server you are very unlikely to have any problem with being hacked. There are lots of tutorials around about server hardening and mostly it's fairly easy stuff. If that's not good enough then you shouldn't be using the web because your security is apparently too important for a public place.

I'm not aware of any google product offering proxies, anonymous or not. They do offer various web applications that are all secured by SSL.

---

### Post by Ulysses_ on 2009-11-26
> **BkkBonaza said:**
> there is a point where paranoia becomes debilitating and you have simply not use the net.

You cannot know if I am up against the same threats that you are.  You got yourself a VPS, I'm not going to call you paranoid because I cannot know the real reasons why you got it, let alone evaluate if they're paranoid or not.  For us here, it's only 

"is A more secure than B?", 

"is C more secure than A?", 

and so on.  

And we take one aspect of security at a time, ie: 

- how do you beat MITM attacks?  

- how do you beat a running keylogger?

- how do you stop Google invading privacy?

So if I say I found a way to beat a MITM attack, by sending DVDs of one-time-pad keys to my own proxy (or having the provider of the unix account send me a DVD of his key as you suggested), the claim is only limited to the MITM attack, the claim is not "I found 100% security".

> If you take a reasonable level of care in managing a server you are very unlikely to have any problem with being hacked. There are lots of tutorials around about server hardening and mostly it's fairly easy stuff.

I'd be a beginner mechanically following instructions that I'd probably not fully understand the ramifications of, let alone judge whether they are sufficient.  

Whereas someone who has a lot of experience in hacking would know much better what is sufficient and what isn't.

But where do I find an experienced hacker who also provides a VPS service?

---

### Post by Agent ME on 2009-11-26
> **Ulysses_ said:**
> For us here, it's only 

"is A more secure than B?", 

"is C more secure than A?", 

and so on.
There is a point where more security doesn't add anything, but takes away. Say choice A of security would take 100,000 years to crack theoretically, and is pretty simple to use and understand. Choice B of security would take 1,000,000 years to crack theoretically, but is hard to use, not well-known, and prone to user mistakes (that can compromise security, to the point of being easily crackable).

SSH is similar to choice A.
Your one time pad setup is more similar to choice B. There isn't too much of a bonus to choice B, and it would be difficult to setup, and one mistake could cost you all the security. Maybe if you knew the ins and outs of cryptography completely, this could be a viable choice, but it probably would still be a waste of time when choice A is practically just as good. Maybe choice B would be a fun programming exercise, but choice A is the simple and good answer to the question "How do I set up a secure proxy?".

> **Ulysses_ said:**
> So if I say I found a way to beat a MITM attack, by sending DVDs of one-time-pad keys to my own proxy (or having the provider of the unix account send me a DVD of his key as you suggested), the claim is only limited to the MITM attack, the claim is not "I found 100% security".
Tools that beat MITM attacks already exist, and they're much simpler than the method you're describing. With SSH, you only have to be able to securely send a small public key to the server. With your method, you have to send probably gigabytes worth of randomness securely to the server.


> **Ulysses_ said:**
> I'd be a beginner mechanically following instructions that I'd probably not fully understand the ramifications of, let alone judge whether they are sufficient.  

Whereas someone who has a lot of experience in hacking would know much better what is sufficient and what isn't.
The alternative to following directions that are probably correct and secure, is to make up on your own system without understanding the ramifications and hope it's secure.

---

### Post by Ulysses_ on 2009-11-26
> **Agent ME said:**
> Tools that beat MITM attacks already exist, and they're much simpler than the method you're describing. (SSH)

You've noticed?  After several pages of people describing SSH beating MITM attacks, you think I consider the one-time-pad scheme the only method that exists to beat MITM attacks. Clearly helpdesk jobs are not suitable for you.

> The alternative to following directions that are probably correct and secure, is to make up on your own system without understanding the ramifications and hope it's secure.

I never said sending DVDs for a one-time-pad scheme is 100% secure.  I said it gives the MITM attack no chance.  You can't deny that.  And since you can't deny that, distorting people's words is your only chance.

---

### Post by Agent ME on 2009-11-26
> **Ulysses_ said:**
> I never said sending DVDs etc is 100% secure.  I said it gives the MITM attack no chance.  You can't deny that.  And since you can't deny that, distorting people's words is your only chance.
Done correctly, it gives MITM no chance. But if you're developing your own tool, as opposed to using something standard and well-reviewed like SSH, there's a greater chance it will be done incorrectly.

Your DVD one time pad method has the plus of being theoretically more secure (but as long as both choices outlive our lifetimes and maybe even human society's lifetime, this is a moot point), but you have to program it yourself and not only mail one DVD full random data, but another DVD each time you use the DVD's worth of bandwidth.
SSH is already programmed and ready to use, well reviewed, and only requires you to get your tiny public key to the server.

---

### Post by Ulysses_ on 2009-11-26
> **Agent ME said:**
> Done correctly, it gives MITM no chance. But if you're developing your own tool, as opposed to using something standard and well-reviewed like SSH, there's a greater chance it will be done incorrectly.Incorrect implementations are a likely problem with complex schemes like public key cryptography.  But XORing files against data is so simple, that even cgiproxy might be able to do it with a few more lines of code, I wouldn't design a proxy from scratch but modify an existing proxy.

> Your DVD one time pad method has the plus of being theoretically more secureActually it's less secure, it's only with stronger encryption and safer against the internet MITM but less secure because the server has to be my own and therefore hackable.

> both choices outlive our lifetimes and maybe even human society's lifetimeThat's for a casual hacker with limited resources.  Not for those who made it illegal to use encryption stronger than AES-256.  In fact my scheme would be illegal.

---

### Post by Beverly Roberts on 2009-11-29
I prefer OpenVPN. It's alot simpler than IPSec, you don't need to recompile the kernel with OpenVPN. 

Beverly Roberts

---

