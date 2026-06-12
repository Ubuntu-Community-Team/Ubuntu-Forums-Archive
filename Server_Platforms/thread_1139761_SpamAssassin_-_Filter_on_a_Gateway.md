---
title: "SpamAssassin - Filter on a Gateway"
date: 2009-04-27
forum: Server Platforms
---

### Post by Dogmatix86 on 2009-04-27
Hi There,
 
I've searching around the net for about 4 hours now and haven't found the answer I'm looking for.
 
My domain recieves an unbelievable amount of email spam. The server does not have any spam software installed. Yes I know...how the hell can you not have spam filters installed on your domain/email server!! The domain is being hosted for free in the US by a friend of mine who I do not wish to upset. I like the hosting because it costs a nice, round affordable of 0.00 :guitar:.
 
So, what I would like to know is this. In Untangle, you have the ability to setup SpamAssassin as a module which 'transparently intercepts' all mail passing through the gateway. So regardless of what domain the user utilising the gateway is requesting mail from, SpamAssassin intercepts the mail message and marks it as spam if thats what it is.
 
I have looked at PostFix and a few others, and they all seem to be full on mail servers which isn't what I want. 
 
Does anyone know how, where, what the requirements are to JUST filter mail passing through a gateway and nothing more?
 
Thanks in advance,
Dogmatix86

---

### Post by HermanAB on 2009-04-27
Howdy,

Get ASSP from Sourceforge:
[http://assp.sourceforge.net/](http://assp.sourceforge.net/)

It does what you want.

---

