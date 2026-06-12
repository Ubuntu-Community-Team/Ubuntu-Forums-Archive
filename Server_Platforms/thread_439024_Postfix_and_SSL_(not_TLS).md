---
title: "Postfix and SSL (not TLS)"
date: 2007-05-10
forum: Server Platforms
---

### Post by jtc on 2007-05-10
I would like to tell my Postfix to accept good old SSL-connections on a specific port, such as 465 for an example. Still, I can only find documention telling me how to let postfix listening on the default port and offering STARTTLS. In itself that probably is a nicer solution, but not one which satisfies what I need right now.

The reason I want to have a SSL-connection listening on a port diffrent from 25 is that my ISP is blocking that port outwards.

Any suggestions where to look? Or am I perhaps trying the wrong solution to my problem?

The postfix in questions runs on a VPS of mine. I want to be able to use it send mail from home, and other places, using SMTPAUTH. The auth-part is no problem by the way.

---

### Post by MJN on 2007-05-10
It sounds like you are indeed barking up the wrong tree.

Regardless how you are connecting *in* to your server, whether it be on port 25, 465, with/without SSL/TSL, if your ISP is blocking outbound port 25 then when it comes for your server to relay the message on (to the externel destination) then it won't be able to.

A solution would be to use the relayhost directive to relay outbound mail via your ISP's mail server, which they presumably allow you access to.

Edit: Ah... thinking a bit wider would I be right in thinking that your VPS isn't hosted by your ISP and hence not the machine subject to the blocked outbound port 25 issue? In which case, just add another smptd line to your master.cf file listening on a port of your choosing (e.g. 2525 inet  n       -       -       -       -       smtpd). Having never done this myself it might be prudent you researching any potential consequences that you may need to be aware of (I can't think of any but that means little!).

Mathew

---

### Post by jtc on 2007-05-10
> **MJN said:**
> 
Edit: Ah... thinking a bit wider would I be right in thinking that your VPS isn't hosted by your ISP and hence not subject to the blocked outbound port 25 issue?

Excatly

It is only my workstation/mail klient which is affected.

---

### Post by MJN on 2007-05-10
Okay, then just add the second daemon in master.cf as mentioned.

It was your '*and other places' *that threw me as you won't have any trouble connecting to your VPS on port 25 from elsewhere, well not unless 'elsewhere' also has outbound port 25 blocked!

Mathew

---

### Post by jtc on 2007-05-10
> **MJN said:**
> Okay, then just add the second daemon in master.cf as mentioned.
Look, there it is! All I had to do was to uncomment it :-)

Guess I should start learning my master.cf aswell, instead of just main.cf

Thanks for the help. I promise to phrases questions better in the future.

---

### Post by MJN on 2007-05-10
> **jtc said:**
> Thanks for the help. I promise to phrases questions better in the future.

Hah, they all say that! ;)

Glad it worked out.

Mathew

---

