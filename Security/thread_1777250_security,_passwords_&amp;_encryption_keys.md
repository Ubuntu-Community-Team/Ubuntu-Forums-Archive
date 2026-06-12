---
title: "security, passwords &amp; encryption keys?"
date: 2011-06-07
forum: Security
---

### Post by smcrossman on 2011-06-07
Today's project!  I am not very security minded...I'm aware of it, and always made sure I had up-to-date overall protection in Windows but firewalls, and the blasted passwords are largely a thorn in my side!

When I got my iPhone last year I suddenly discovered password managers & "wallets" to keep all that kind of information in and syncable across different devices. My life got so much easier. Of course now I need to figure out encryption keys, and how they work (I'm clueless). I also need to find a program or system that I can move my existing low-tech info (mailnly user name & passwords) that will also accomodate the increased needs of Ubuntu security and still be sync-able.  I started a little research weeks ago, but my current "wallet" only exports .csv so I quit since I'm going to have to do a lot of data entry whatever I go with.

So here goes:

1) what is the difference (bare bones) between using an encryption key (e.k.) vs. a standard user created password?  what situations are better suited for e.k.?
2) I have seahorse (default intall with Ubuntu I guess) but the only thing in it is Login under passwords which leads to a login keyring (?) and a drop-down list of about 6-10 of the gazillon passwords I use daily. The other tabs are for keys which I don't have any concept of.
3) I know FF also "remembers" user id & passwords as you choose to have it do so. Is that information transferable into seahorse or another program?
4)I'm also (today) getting ready to really set up my system for user names & security across my little home network. How can I integrate that into whichever program/app I go with to store my pwds and keys?
5) Can you give me links to fairly current documentation on this stuff?
6) Any program/app recommendations.  Pros/cons  uses, what they can & can't do or be used for, etc.....much appreciated.

---

### Post by uRock on 2011-06-07
Moved to ***Security Discussions***

---

### Post by kado1 on 2011-06-07
How do I post a message in the absolute beginner part?

---

### Post by smcrossman on 2011-06-07
Okay....I see I got transferred!  I searched through this forum before posting originally, but didn't really see anything quite along these lines. I've been working through the Samba setup slowly, running into issues with users and passwords....turned out I hadn't enabled (so the password would sync up) for the one user. 

I'm also looking at trying out a VM for the first time, but wanted to be sure I understood good security and have it set up before doing that. In my experience going back after a lot of things have been installed/set up means a lot more work.

I'm very willing to read through documentation, try it all out and then if I just can't get something figured out post with details as required. On this though, I'm uncertain what documentation to start with. There is so much and some of it doesn't seem to really apply to Natty or Win 7 or Samba or .... Trying to figure out what is relevant and not when I don't know much about basic protocols is making me feel really dumb. Hence the very basic questions leading up to requests for feedback on apps that are out there.

Thanks for your time and assistance!

---

### Post by smcrossman on 2011-06-07
> **kado1 said:**
> How do I post a message in the absolute beginner part?

The absolute beginner forum is above all the others on the main page. It works like all the others you sign in and can then reply to threads or start a new one.   They are generally quick to respond and patient with folks like me who have issues with the jargon or from years of windows use

---

### Post by Thewhistlingwind on 2011-06-08
Cryptography, well.

[http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)

That's probably simpler then I could really make it.

Really, you should just play around with gpg/etc and not publish your keys. 

man gpg

Also, remember, digital signatures are REAL signatures in many jurisdictions. (And all that implies.)

---

### Post by smcrossman on 2011-06-08
Thanks! Some interesting reading, considering my general lack of interest in the topic. I do understand and respect the importance of privacy and the need for it in general. I just would prefer to let someone else deal with the set up and monitoring.

I guess I will take some time to play with it, although I'm not sure how I would practically implement it into my life/system.

---

### Post by Thewhistlingwind on 2011-06-08
> **smcrossman said:**
> 

I guess I will take some time to play with it, although I'm not sure how I would practically implement it into my life/system.


That's part of the problem, to use encryption, your recipients have to know whats going on, or it's useless.

EDIT: That is, they need to be aware of what to do with what you send them. Most people won't see the point because they don't understand that they're packets hop 20+ servers to get to their destination/all the other problems with leaving your data sitting around on servers in however many different places.

---

### Post by CandidMan on 2011-06-08
Basically, the asymmetric key model is like a key and vault. It's extremely difficult to 'guess' correctly a file that's 4096 bytes large.
When you generate an encryption key, you're actually making a 'vault' and a 'key'. You send the 'vault' to everyone you know and they use that to secure anything they send to you.
And using the key part is self explanatory. It can also be used just to sign things when only integrity is a concern.

---

### Post by smcrossman on 2011-06-09
Before I started switching over to Ubuntu....I was looking at some online providers for medical records storage, etc.  I would still like to set up a cloud file with my records and current info (meds lists, insurance, recent labs, blood sugars, etc., etc.).  Since my family is so far away if anything ever happened they would need that kind of stuff, but they aren't very techie.  If it is encrypted and the key is on whatever password/key manager I am using on my network would they be able to access it from one of my pcs?  

Can different keys be set up for different levels of access?  Say if I have a particular provider who needs regular access to my blood sugars....can I give them a key (in their thinking a password likely) so they can access my bg records when I notify them there is an issue?

I currently use iDisk (which will be changing to a true cloud over the next 6 months) and know I can use different settings/passwords for different files, but the synchronization has always been a pain (since I used Windows).

As I get things set up here at home. I hope to eventually have a network HD for backups and to store active "shared" files on to access from any of my computers and possibly from the netbook when I'm not at home. I'm guessing that is where I truly will need to start seriously working on security and crypto.  But if my key is on the netbook (since I'm not likely to remember it!) Doesn't that defeat a good portion of the reason for encrypting?  I know that it will better ensure safety in case anyone else came in remotely and accessed my system....still really why would they? but.... folks do unimaginably strange things all the time.

Okay...so I guess I'm wanting to know what kind of password manager/key program am I should look for. How is it that things are really secure if the program is on your computer where anyone trying to get into your stuff can find it/use it...

Just because I don't like the whole concept and don't enjoy the process I am realistic enough to realize that no one today is really exempt from needing to protect information.  And I guess I'm just a bit too much..."if I'm going to do this then I'm damn well going to do it right" which just causes me way too much work. LOL

---

### Post by CandidMan on 2011-06-09
> **smcrossman said:**
> 
As I get things set up here at home. I hope to eventually have a network HD for backups and to store active "shared" files on to access from any of my computers and possibly from the netbook when I'm not at home. I'm guessing that is where I truly will need to start seriously working on security and crypto.  But if my key is on the netbook (since I'm not likely to remember it!) Doesn't that defeat a good portion of the reason for encrypting?  I know that it will better ensure safety in case anyone else came in remotely and accessed my system....still really why would they? but.... folks do unimaginably strange things all the time.
Assuming you mean the private key is on your netbook away from home.
Um, it all depends on what you want. The key model if usually for encryption between two people whereas something like Truecrypt can serve both purposes. Of course you can use your public 'key' to encrypt files that only be decrypted by your private 'key'.

And yes you have to look after your private key.
There's also the option of symmetric keys. That's one key that does both after entering the password.
If you have a lot of files or they're large and being edited often I'd use Truecrypt but I'm not sure how you'd use that remotely.
Or you could archive your files with tar and encrypt that.
EDIT:Truecrypt is probably easier for everyone if your family is not confident with computers plus you can use key files with it also.

I'm moving soon but plan on leaving an SSH server running on my brother's PC that will only accept SSH keys for connecting from a specific MAC address.

---

