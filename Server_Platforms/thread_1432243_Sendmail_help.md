---
title: "Sendmail help"
date: 2010-03-17
forum: Server Platforms
---

### Post by dado prso on 2010-03-17
Hello,

I'm a big server noob.

My boss just assigned me a project running ubuntu server 9.1

I've installed sendmail and now I have to:
1) configure it as a mail system that can accept mail from our internal network and
2) send messages to our exchange system. (we use microsoft exchange)

I've been trying to follow different guides for the past 3 hours and I've gotten no where.

The sendmail configuration file is really intimidating.

Thank you for your help,
Dado

---

### Post by KB1JWQ on 2010-03-17
You're absolutely right.  Sendmail is a scary beast, it's why I use Postfix for all of my mailing needs that don't involve UUCP.

Is this an option for you?

---

### Post by dado prso on 2010-03-17
Thanks for the suggestion, but I'm afraid it's not.

My boss wants me to learn sendmail because I'm an intern.

Dado

---

### Post by KB1JWQ on 2010-03-17
Ridiculous mindset; sendmail has a worse security track record, a horrible configuration mechanism, and effectively all of what it does that postfix doesn't do is ancient and outmoded.

I'd get the Bat Book from O'Reilly.

---

### Post by dado prso on 2010-03-17
Well I work for the State.....

---

### Post by dado prso on 2010-03-18
bump

---

### Post by KB1JWQ on 2010-03-18
At least one of us has a misconception here. :-)

Your boss wants you to do this as a learning experience.  Presumably he's going to provide support for you in some format. 

There's a lot of material out there on sendmail, there's #sendmail on freenode, there's a thousand tutorials.

It seems like you're asking "Do my job for me" rather than "I've started configuring sendmail, and don't understand X-- from my reading I see it's supposed to do Y, but I'm getting result Z.  Google hasn't been informative, and despite a fair bit of research I still can't see how to do this." 

The latter gets a half dozen people jumping in with advice and solutions for you; the former gets a dismissive shake of the head and people move on to other forums.

If you can forgive the condescending tone of the document, [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html) is a valuable resource on how to effectively ask for help in an online forum.

---

### Post by dado prso on 2010-03-18
Having a bad day?

---

### Post by jrssystemsnet on 2010-03-18
Well, the problem is that you want to use some pretty hideous software with a truly horrible security track record, which is ridiculously difficult to properly configure, for a task that much more modern, simple-to-configure, more secure, and for that matter typically higher-performance software would be thoroughly appropriate for.

Piled on top of that, you're (as KB1JWQ said) asking for a complete hand-holding through the whole process, rather than a tip on a particular point you're stuck on.

So basically, you're not too likely to get a helpful answer in a general-purpose Linux forum.  Note that I'm having a *good* day, and I ain't mad at'cha, but you'd probably be better off finding a Sendmail-specific (or at the very least, a mailserver-specific) forum or IRC chat or wiki or what have you, and trying to find your answers there - just because the odds of somebody who actually uses Sendmail on a regular basis and can easily answer your question off the top of his head is more likely to wander by and take pity on you. :)

---

### Post by jrssystemsnet on 2010-03-18
I will give you this much of a pointer, though - from what I can make out of your description in the opening post, the proper terminology for what you want to do sounds like "set up a sendmail server with a smarthost".

Googling **sendmail smarthost how-to** just might do you right.

---

### Post by dado prso on 2010-03-19
Thank you. I had no idea where to start.
Just wikipedia'd smarthost :)

---

