---
title: "Digging deeper into GPG Encryption"
date: 2010-10-17
forum: Security
---

### Post by NertSkull on 2010-10-17
So I've been using GPG keys for about a year now to send encrypted emails to family.  But now I want to try and understand more, mainly on signing keys.  I've read a ton of stuff, but not fully grasping the concept.  So I thought I'd check my understanding people here.  Please let me know if I'm wrong on something.

Point 1

Signing keys seems to be just signing someone else's public key with my private(public??) key.  Does that mean I don't sign my own keys?  Or should I?

Point 2

There seem to be lots of keyservers out there, mainly I keep hearing about the MIT one and the ubuntu keyserver.  Does it matter where I upload my public key?  Somewhere I read that once you upload it once, it will slowly make its way to other servers.  How is that possible.  If someone signs my key on one server, will that also get pushed to other servers?

Point 3

Trust levels seem to be the opposite direction of signing.  I sign someone elses key (or they sign mine) to say to the world I trust this key is legit.  But trust levels seem to be only on my own computer, telling me that I trust that person fully or not so much.  But the trust level I set doesn't get seen by anyone else.  Is that right?

Point 4

The Ubuntu gpg howto page lists biglumber.com as a good place to find someone to sign your key.  Is that the best place to look?

Point 5

I don't really understand the web of trust on a broader level.  I get the idea of having lots of keys signed by many people to expand it out.  But I don't see how that works exactly.  If one person signs my key, does that mean that by extension everyone that has signed his key has also signed my key?  

Point 6

Kind of along those lines, how do I expand my key's web of trust.  Do I have to meet with someone everytime I want to add another signer?

Point 7

I don't fully get the difference between signing your gpg key and signing an email.  for example, thunderbirds enigmail add-on lets me sign and encrypt messages.  I've always just been encrypting them only.  Do I need to sign them?  Is this a totally different concept or is it related to gpg-signing?  


Allright, thats it for now.  I have more, but those are top on my mind.  I'm trying to get a solid grasp on this stuff but I'm finding a lot of the documentation is written for people who already understand a lot of it.  But I'm still trying to get the basics.  Sorry for the long post, but I appreciate any help/ideas people have.

---

### Post by rookcifer on 2010-10-17
> **NertSkull said:**
> Point 1

Signing keys seems to be just signing someone else's public key with my private(public??) key.  Does that mean I don't sign my own keys?  Or should I?

Your own key is automatically signed when it is created, so no need to worry about that.  When you sign other people's keys you are signing their public key with your private key.  Then you must send their public key back to them.

> Point 2

There seem to be lots of keyservers out there, mainly I keep hearing about the MIT one and the ubuntu keyserver.  Does it matter where I upload my public key?  Somewhere I read that once you upload it once, it will slowly make its way to other servers.  How is that possible.  If someone signs my key on one server, will that also get pushed to other servers?

Most of the keyservers sync with each other.  When you sign someone else's key, it is best to send the key directly to them in email rather than uploading it to the keyserver for them (considered bad ettiquete).

> Point 3

Trust levels seem to be the opposite direction of signing.  I sign someone elses key (or they sign mine) to say to the world I trust this key is legit.  But trust levels seem to be only on my own computer, telling me that I trust that person fully or not so much.  But the trust level I set doesn't get seen by anyone else.  Is that right?

You should never sign a key that you aren't 100% sure belongs to the person who claims it.  This is typically verified by meeting the person in real life and having them bring their key fingerprint with them along with at least one picture ID.  There is a lot of info on the Internet about "key signing parties" and how to conduct one properly.

> Point 4

The Ubuntu gpg howto page lists biglumber.com as a good place to find someone to sign your key.  Is that the best place to look?

Probably, but sadly there are only a few cities listed.

> Point 5

I don't really understand the web of trust on a broader level.  I get the idea of having lots of keys signed by many people to expand it out.  But I don't see how that works exactly.  If one person signs my key, does that mean that by extension everyone that has signed his key has also signed my key?  

Not really.  It works in degrees of separation in a sense.  Alice has signed Bob's key and Bob has signed Mallory's key.  This doesn't mean that Alice trusts Mallory or vice versa.  But it does mean that if Alice and Mallory wanted to sign each other's keys, they would have an easier time with it since they both can get Bob to vouch for the other.  Typically a person with a lot of signatures on their key can be trusted more than an unknown.  Google "Web of Trust."  Wikipedia has a page on it.

> Point 6

Kind of along those lines, how do I expand my key's web of trust.  Do I have to meet with someone everytime I want to add another signer?

Personally I would, yes.  You kind of hurt the WOT if you go around signing people's keys you haven't met.

> Point 7

I don't fully get the difference between signing your gpg key and signing an email.  for example, thunderbirds enigmail add-on lets me sign and encrypt messages.  I've always just been encrypting them only.  Do I need to sign them?  Is this a totally different concept or is it related to gpg-signing?  

Signing a key is just saying that you (Bob) have vouched for Jane.  This helps other people in your WOT decide whether they can at least marginally trust Jane.

Signing an e-mail (or any file really) is different than key signing even though the concept is the same.  When you sign an e-mail you are putting a hash on the email signed by your private key.  This way, anyone with your public key can verify that it was your private key that is responsible for signing the e-mail.  This alleviates the issue of someone sending out (unencrypted) e-mails under your name.

---

### Post by Agent ME on 2010-10-18
The point of signing a key is to say "This key really does belong to the person" to others.

If Alice wants to send an encrypted message to Charlie, she needs Charlie's public key key. She could check the keyservers, but anyone could put up their own key saying it belongs to Charlie. Alice wants to know which key really belongs to Charlie. If she sees one key that is signed by Bob's key (and she knows from checking in-person that that really is Bob's key), then she knows that Bob has personally checked Charlie's key. If she trusts Bob's word then she can reason that that key belongs to Charlie.

---

### Post by NertSkull on 2010-10-18
Those were both actually pretty helpful to me in getting things more solidified.

Just a few more clarifications

#1

So if I get my key signed by someone else, and they give it to back to me.  Should I try to upload it to many different keyservers?  Or just load it to one?  Should I choose a "main" keyserver for me?  How else would they sync?  Because I could, in theory, put two different versions w/ different signatures on two servers.  So is it best to just rely on one server?

#2

If so, how do I pick a server?  Does it not matter, are some more "synced up" than others?

#3

If I back up my keys (i.e. I reinstall my system) do the signatures get backed up as well?  Are the signatures stored in the same file so I don't lose them?  So that I can treat my local copy of the key as my "master".

#4 

along those lines, is there a way to list all the signatures (I still need to google this one, so don't yell at me if its ridiculously simple)


Allright, thanks everyone.  That was really helpful, I think I'm slowly getting the hang of this.  And luckily my city has a few people listed that can help start me in on the web of trust.

---

### Post by rookcifer on 2010-10-19
> **NertSkull said:**
> Those were both actually pretty helpful to me in getting things more solidified.

Just a few more clarifications

#1

So if I get my key signed by someone else, and they give it to back to me.  Should I try to upload it to many different keyservers?  Or just load it to one?  Should I choose a "main" keyserver for me?  How else would they sync?  Because I could, in theory, put two different versions w/ different signatures on two servers.  So is it best to just rely on one server?

Yeah, you can upload it to pgp.mit.edu (or any of the other ones) and they will all sync together within a day or two.  Then you will see your key on most of the other servers automatically without having to do anything extra.  

When someone signs your key (or you make a change to your key) you will have to resend it to the server.  (Also note that you can never delete a key from a server, but you can revoke it).

> #2

If so, how do I pick a server?  Does it not matter, are some more "synced up" than others?

Shouldn't matter.  Just use the default ubuntu server or the MIT server.

> #3

If I back up my keys (i.e. I reinstall my system) do the signatures get backed up as well?  Are the signatures stored in the same file so I don't lose them?  So that I can treat my local copy of the key as my "master".

Yeah, if you back up your ~/.gnupg directory, everything you need will be there.  If you ever need to reinstall the OS, just simply copy that directory from your backup and replace the default .gnupg directory with your backed up one.

> #4 

along those lines, is there a way to list all the signatures (I still need to google this one, so don't yell at me if its ridiculously simple)

```
gpg --list-sigs
```

Also found a nice [tutorial here]("http://www.spywarewarrior.com/uiuc/gpg/gpg-com-4.htm#4-1a") that you might want to read.

---

### Post by NertSkull on 2010-10-21
Thanks all.  That all helped a lot in understanding.  

Now I just need to meet more people to use encryption with.

Thanks again.

---

### Post by rookcifer on 2010-10-22
> **NertSkull said:**
> 
Now I just need to meet more people to use encryption with.

Thanks again.

That's the hard part.  Most people either don't know or care about encryption.

---

