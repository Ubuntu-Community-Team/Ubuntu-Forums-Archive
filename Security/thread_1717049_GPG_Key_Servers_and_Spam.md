---
title: "GPG Key Servers and Spam"
date: 2011-03-29
forum: Security
---

### Post by NertSkull on 2011-03-29
So I've never uploaded a key of mine to a key-server before.  Mainly I've just been using it with one or two other people small scale and haven't had the need.  But that's slowly starting to change, so I have been thinking about using a key-server.

But I'm surprised to find what appears to be very little discussion out there on key-servers and spam.  I've read a few things that say bots do harvest emails from there, but there are also lots of people that try to claim its not an issue.

I'm surprised that its not more controlled.  I would have thought people who are concerned with privacy enough to use keys, would really want to do anything to combat that as well.

So I'm curious what everyone's thoughts are.  Is this a total non-issue?  If not, why is it not really talked about?

And in particular, should I be concerned that putting a key (with name and email address) out there be concerning to me? And, perhaps more important, is there anything I can do to protect my privacy more while putting a key on a server?

---

### Post by WinstonChurchill on 2011-03-29
> **NertSkull said:**
> So I've never uploaded a key of mine to a key-server before.  Mainly I've just been using it with one or two other people small scale and haven't had the need.  But that's slowly starting to change, so I have been thinking about using a key-server.

But I'm surprised to find what appears to be very little discussion out there on key-servers and spam.  I've read a few things that say bots do harvest emails from there, but there are also lots of people that try to claim its not an issue.

I'm surprised that its not more controlled.  I would have thought people who are concerned with privacy enough to use keys, would really want to do anything to combat that as well.

So I'm curious what everyone's thoughts are.  Is this a total non-issue?  If not, why is it not really talked about?

And in particular, should I be concerned that putting a key (with name and email address) out there be concerning to me? And, perhaps more important, is there anything I can do to protect my privacy more while putting a key on a server?
The entire point of a keyserver is to put your public key out where anybody can find it. If people who want to send you E-Mail can't find your key, they can't send you GPG-encrypted E-Mail. You could ostensibly just put your E-Mail on the key (eg use "Name Withheld" as the name), but if you don't associate the key with your E-Mail, it's kind of useless to have the key in the first place. 

If you only care about getting GPG-encrypted mail from a few people, you could just give them your public key directly (eg, E-Mail it to them), and not publish it on the keyserver. It makes GPG much, much less useful (nobody can verify your signatures easily), but if you're that paranoid, it would work for you.

FYI, I've had keys for both my E-Mails on all the major keyservers for at least 3 years (probably longer...), and the only spam I ever get is from the LKML.

---

### Post by NertSkull on 2011-03-29
Well thats good to know.  I don't think I would withold a name, thats not very useful like you said.

I guess I was curious more along the lines of do the servers tend to get farmed for email addresses or not, and if they do is there anything that can be done about it on a personal level.

But it sounds like in your case you have not had any issues with emails getting farmed off of a key-server.  

Which is a good thing to here.

Another quick question (maybe I need a different thread for this).  How do you know what keyservers are active.  I've been looking at ones I can find, and most seem to match up well and seem to sync.  But I've found one or two that are not up to date and is probably not syncing anymore with others.

How do you know what you are using is active/still currently being used?

---

### Post by NertSkull on 2011-03-31
Perhaps I'm the only one that finds this concept interesting here, but there is some interesting discussion [here]("http://www.mail-archive.com/gnupg-users@gnupg.org/msg13669.html") on it.

The part I find most interesting is this 
> 
2) This is not only about spam but about the protection of privacy. It is inacceptable that everyone can easily check who is in contact with whom via the clear text addresses and the web of trust. It was mentioned here that this can even be dangerous for people who get suppressed by their government.


I find it surprising that the world of encryption, where I would think people would be overly cautious about these types of things, do just put out this information easily accessible to anyone.

I'm sure I'll end up with my keys on a keyserver, and I may not get any increased spam from it.  But conceptually I still find myself surprised how much lack of privacy surrounds some of this.

--although, I'm beginning to wonder if I'm really just a lot more paranoid than I thought I was  :)

---

### Post by BkkBonanza on 2011-03-31
I did some tests on the MIT keyserver with my name. It seems if you know the name you can find the key. And if you know the email you can find the key. But it didn't show my email when I looked up by name. And it didn't find my key when looking up the key-id. So it seems the only way to see the email is if you search by email. I checked my key record in gpg and it has the email address in it. But on the MIT site it wasn't listed. I'm not sure if I removed it for the keyserver but I don't think I did (or could even). 

So it actually seems that to find emails this way you'd have to start with a big list of names. Anyway, I haven't had any problems with this after 10 years of being listed "out there". But then, I use gmail and spam very rarely ever gets to me anyway. I trash about a dozen a month maybe.

I would say if you're worried then create a separate email address for this, say on gmail, and forward it to your regular one. That way you can always cut it free someday. Then ideally you have to revoke the key too. Well, I have also a key from ten years ago that I lost the private key for and can't get rid of and it's got an old email address from a service that hasn't even existed in 3-4 years.

My guess is that there are a lot of keys out there that are dead anyway with old emails. How many people just played with this stuff and then lost their key...
[B]
Edit:[/B] Oh. I was just checking my name again and see it's a key from 1993 on there. Yikes. That would be me back then, I'm sure, but what's weird is this key server doesn't have my real recent key. Kinda useless then.

Looking at the Ubuntu key server does show my recent key and email address. Ah well. You have to know my name to get my email address but my name is my address anyway so no big leap there. It's been there for 2 years now.

---

### Post by NertSkull on 2011-03-31
> **BkkBonanza said:**
> I did some tests on the MIT keyserver with my name. It seems if you know the name you can find the key. And if you know the email you can find the key. But it didn't show my email when I looked up by name. And it didn't find my key when looking up the key-id. So it seems the only way to see the email is if you search by email. I checked my key record in gpg and it has the email address in it. But on the MIT site it wasn't listed. I'm not sure if I removed it for the keyserver but I don't think I did (or could even). 

So it actually seems that to find emails this way you'd have to start with a big list of names. 
So I'm not sure exactly what you are doing.  But I can definitely get addresses off of servers with just a name.  For example, if I go here

[http://keys.gnupg.net/](http://keys.gnupg.net/)

And then type in a random name (I chose John Adams)

Then I get 50+ names that list the key, comment and email very clear for me.  So you can get emails with a name off the server.

> Anyway, I haven't had any problems with this after 10 years of being listed "out there". But then, I use gmail and spam very rarely ever gets to me anyway. I trash about a dozen a month maybe.
That's good.  That seems to be the general consensus that people aren't getting increased spam from the servers.  And you're right, spam filters are pretty good.
> 

I would say if you're worried then create a separate email address for this, say on gmail, and forward it to your regular one. That way you can always cut it free someday. Then ideally you have to revoke the key too. Well, I have also a key from ten years ago that I lost the private key for and can't get rid of and it's got an old email address from a service that hasn't even existed in 3-4 years.

My guess is that there are a lot of keys out there that are dead anyway with old emails. How many people just played with this stuff and then lost their key...
[B]
Edit:[/B] Oh. I was just checking my name again and see it's a key from 1993 on there. Yikes. That would be me back then, I'm sure, but what's weird is this key server doesn't have my real recent key. Kinda useless then.

Looking at the Ubuntu key server does show my recent key and email address. Ah well. You have to know my name to get my email address but my name is my address anyway so no big leap there. It's been there for 2 years now.

This actually is a pretty important point to me as well.  I've been reading deep into some of the gnupg threads and it appears that some servers are not syncing right now.  The MIT server (pgp.mit.edu) has not been syncing to the others servers for something like 18 months now.  Which is a problem because its the first one that shows up on google searches often.

Also, the subkeys.pgp.net server is only having intermittent syncing also (from what I read they have three servers and only one appears to be working).  This problem was first noticed back in November, and appears to still not be working.

So right now it appears the best ones to use are like keys.gnupg.net or keyserver.ubuntu.com or similar ones.  But those other two I wouldn't use.

Again, it surprises me that these things aren't more of a concern to the GPG community.  But I guess its a small group as it is so not totally surprising that the servers can go un-noticed.

But still the whole emails out there on the servers is surprising to me.  And even more so being able to see who's signing who's keys does make it readily apparent who you are in communication with.

---

### Post by ThorX89 on 2012-09-18
I think that's a very good point you're making NertSkull. Regardless of whether or not keyservers are being used by spambots to collect e-mail lists, there's always the potential, given the current implementation.

If you are concerned about having your name associated with your e-mail address, you could always use a bogus name. Bogus e-mail addresses would probably not work without changes to the very core  of pgp/gpg.

What I think could be done is that keyservers could offer security optional policies so that uploaders could choose to withold certain kind of information from being subject to searches (e.g., you could choose to prevent people from searching you by name), and there could be an option to not return a key until the whole contents of a property item is provided (e.g., an uploader should be able to insist  that searches only be returned if the query contains the nothing more and nothing less than than the whole e-mail address ).

I also think it should be possible to link to a key on a keyserver from the web.

---

