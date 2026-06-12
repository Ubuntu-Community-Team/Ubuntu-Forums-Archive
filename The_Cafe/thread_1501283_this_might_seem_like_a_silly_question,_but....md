---
title: "this might seem like a silly question, but..."
date: 2010-06-04
forum: The Cafe
---

### Post by spezticle on 2010-06-04
when running a webhost, why bother ever using :80
why not base a standard around consistent https connections all the time?
would a apache2 server setup that disregards all port 80 requests even work?

just curious, really.

---

### Post by Diluted on 2010-06-04
Just to clarify, are you asking why web hosts aren't using HTTPS for everything?

If so, that's because HTTPS increases the server load.

---

### Post by spezticle on 2010-06-04
that's kind of what i figured, but with the direction and momentum of technology, it's seeming like using that as an excuse not to explicitly use https would be the same as saying we're NOT going to use  steel for car frames but reinforced plastic because it would decrease the load of the engine.

of course i know this is a drastic comparison, i just am disappointed by the availability of encryption and security.

i have gmail set up with encryption keys and all that but it doesn't do me any good at all because nobody i email has anything to decrypt the email installed. everything is so... open except logins, banking and that sort of thing...
i don't even have a choice for popular methods of social networking, facebook for example. chat.facebook.com for jabber communication doesn't allow ssh connections. authentication for gmail via pop3 or imap only allows plain.

why aren't we building a standard of security?

intel can make a 50 core cpu and we can cluster computers around the world for a virtual private network and cluster super computer. we lock our car doors when we go into the grocery stores and we don't send letters via mail in transparent envelopes. Many parents get super edgy when someone they don't know even just  talks to their children in a public place.... we maintain our security... but not online. it just doesn't make sense to me why we aren't designing our systems to handle the increased load for phasing out non encrypted connections and data transmission.

---

### Post by Johnsie on 2010-06-04
When I have a conversation with a friend in the bar we don't encrypt what we are saying, we are just careful about what we say. If we want to say something really private, that is when we might go somewhere else or 'whisper'. People would think we're a little weird and paranoid if we whispered all the time though.

Most internet traffic is non-sensitive and doesn't need to be encrypted. It's a waste of time, money and environmental resources.

---

### Post by Diluted on 2010-06-04
> **spezticle said:**
> that's kind of what i figured, but with the direction and momentum of technology, it's seeming like using that as an excuse not to explicitly use https would be the same as saying we're NOT going to use  steel for car frames but reinforced plastic because it would decrease the load of the engine.

of course i know this is a drastic comparison, i just am disappointed by the availability of encryption and security.
Bear in mind that if web hosts start mandating HTTPS on all websites, server load would increase and the people they can pack into a server would decrease. Thus, web hosting would be more expensive than it is now. I think some people would not appreciate being forced to use HTTPS for something simple like blogs. Don't forget you need to pay extra for a certificate as well.

> **spezticle said:**
> i have gmail set up with encryption keys and all that but it doesn't do me any good at all because nobody i email has anything to decrypt the email installed.
I think that's a problem of encrypted technologies being more complicated than unencrypted ones. Besides, not everyone is aware of e-mail being insecure.

> **spezticle said:**
> i don't even have a choice for popular methods of social networking, facebook for example. chat.facebook.com for jabber communication doesn't allow ssh connections. authentication for gmail via pop3 or imap only allows plain.
Well, that's up to the service providers to decide. Switch providers if you're not satisfied with the security? Or tunnel everything through SSH.

> **spezticle said:**
> intel can make a 50 core cpu and we can cluster computers around the world for a virtual private network and cluster super computer. we lock our car doors when we go into the grocery stores and we don't send letters via mail in transparent envelopes. Many parents get super edgy when someone they don't know even just  talks to their children in a public place.... we maintain our security... but not online. it just doesn't make sense to me why we aren't designing our systems to handle the increased load for phasing out non encrypted connections and data transmission.
Increased load means increased costs. I think you'll find website owners preferring to encrypt important information only in order to save costs.

---

### Post by spezticle on 2010-06-04
> **Johnsie said:**
> When I have a conversation with a friend in the bar we don't encrypt what we are saying, we are just careful about what we say. If we want to say something really private, that is when we might go somewhere else or 'whisper'. People would think we're a little weird and paranoid if we whispered all the time though.

Most internet traffic is non-sensitive and doesn't need to be encrypted. It's a waste of time, money and environmental resources.

yeah, i suppose you're right.

---

### Post by spezticle on 2010-06-04
> **Diluted said:**
> Besides, not everyone is aware of e-mail being insecure.

it would be nice to know that all my email really was secure.
if i send "jane" an email to her gmail, for example, and jane's friend jamie knows her password, jamie can quite easily breach my privacy beyond my control, but if jamie didn't have the key, despite she knew the password, it would still be private.

can you imagine the amount of drama that could be avoided if email was strongly encrypted lol

---

### Post by koenn on 2010-06-04
> **spezticle said:**
> when running a webhost, why bother ever using :80
why not base a standard around consistent https connections all the time?
would a apache2 server setup that disregards all port 80 requests even work?

just curious, really.

web servers, mostly, are a form of broadcast: they're 1-to-many communications. You publish something on a web server and want anyone with a http client (a browser, ...) to read/see/hear it. 
There's absolutely no point in adding authentication and encryption to content that you are making available to the general public. 


When you start using web for other use cases than that one, eg web mail, it begins to make sense to  use https for these specific applications. Even more so if you want one or both sides to authenticate before disclosing information. 

But the default use case is to publish content to the world. So Apache defaults to port 80.

---

### Post by koenn on 2010-06-04
> **spezticle said:**
> it would be nice to know that all my email really was secure.
if i send "jane" an email to her gmail, for example, and jane's friend jamie knows her password, jamie can quite easily breach my privacy beyond my control, but if jamie didn't have the key, despite she knew the password, it would still be private.

can you imagine the amount of drama that could be avoided if email was strongly encrypted lol

bad example. Even witout all the password stuff, if jane accidentally or on purpose forwards that mail, or plainly tells jamie what you wrote, your privacy is down the drain as well, completely beyound your control. (And woman tell each other a lot  :) )

---

### Post by spezticle on 2010-06-04
> **koenn said:**
> bad example. Even witout all the password stuff, if jane accidentally or on purpose forwards that mail, or plainly tells jamie what you wrote, your privacy is down the drain as well, completely beyound your control. (And woman tell each other a lot  :) )

haha! true indeed.

i guess the moral of the thread is that we can only be as secure as the weakest link in the security. which really isn't even that profound of an idea lol.

---

