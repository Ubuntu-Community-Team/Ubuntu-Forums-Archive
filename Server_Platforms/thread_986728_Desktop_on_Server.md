---
title: "Desktop on Server"
date: 2008-11-18
forum: Server Platforms
---

### Post by daboroe on 2008-11-18
I was wondering if there would be any security risk of running Desktop as a GUI interface on server? I am contemplating doing this but want to know if there would be any security risks involved in this.

---

### Post by Philio on 2008-11-18
There really isnt any advantage to having a gui on your server. It uses more resources and can potentially be a security risk.

---

### Post by iponeverything on 2008-11-18
It will just consume extra resources. no real security risk.

---

### Post by daboroe on 2008-11-18
so there is **NO**security risk or there is a **SMALL**security risk?

---

### Post by mike010 on 2008-11-18
none that i know but i would just install ith gui on the server 
then add the extra software on to that but if you need a server
and that is it the basic server without the gui would do and will not be as hard on system requirements but if you would like to install both i do not thank it would hurt.

to install the gui on the server here is the command this will give you the
gnome desktop.

sudo apt-get install ubuntu-desktop


friends dont let friends use windows...

---

### Post by y@w on 2008-11-18
If someone says that there is "no security risk" they are lying. It's perfectly fine to run X on your server. The reason most people don't is to avoid the additional resources needed to have X running when most serious server admins are just going to use SSH to control their servers anyway. I will say it this way: there's no added security risk that would stop me from running X on a server except it's completely unnecessary for me.

---

### Post by iponeverything on 2008-11-19
> **y@w said:**
> If someone says that there is "no security risk" they are lying. It's perfectly fine to run X on your server. The reason most people don't is to avoid the additional resources needed to have X running when most serious server admins are just going to use SSH to control their servers anyway. I will say it this way: there's no added security risk that would stop me from running X on a server except it's completely unnecessary for me.

Enlighten me please. How does running a X server make your server less secure?

---

### Post by Philio on 2008-11-19
> **iponeverything said:**
> Enlighten me please. How does running a X server make your server less secure?

Although I don't know of specific examples it's the principle of more software installed, more ports open to the outside world, more potential for security bugs/holes. Chances are it wouldn't nescessarily be a security risk, BUT why do you need a gui on a server, it doesn't compliment it in any way whatsoever.

---

### Post by iponeverything on 2008-11-19
> **Philio said:**
> Although I don't know of specific examples it's the principle of more software installed, more ports open to the outside world, more potential for security bugs/holes. Chances are it wouldn't nescessarily be a security risk, BUT why do you need a gui on a server, it doesn't compliment it in any way whatsoever.

I assume he has a good reason for wanting X on his server. All my servers are headless, so I know I would not need X.

This is not rocket science. A simple nmap port scan well tell what ports your listening on. The default X configuration on Ubuntu has X being started with the -nolisten option.  It has been that way for a while.

At some level everything is a security risk, but far and away the biggest security risk is ignorance. That goes for your own physical security just as it does for computer security. Folks put blind faith ahead common sense, I have seen companies shell out a boat load of money for a fancy PIX firewall, only to punch more holes in it than a fishing net.

A little knowledge goes a long way.

---

### Post by daboroe on 2008-11-19
> **iponeverything said:**
> I assume he has a good reason for wanting X on his server. All my servers are headless, so I know I would not need X.

This is not rocket science. A simple nmap port scan well tell what ports your listening on. The default X configuration on Ubuntu has X being started with the -nolisten option.  It has been that way for a while.

At some level everything is a security risk, but far and away the biggest security risk is ignorance. That goes for your own physical security just as it does for computer security. Folks put blind faith ahead common sense, I have seen companies shell out a boat load of money for a fancy PIX firewall, only to punch more holes in it than a fishing net.

A little knowledge goes a long way.

and from not doing updates with the following two commaands

```

sudo apt-get update

```

```

sudo apt-get upgrade

```

---

### Post by y@w on 2008-11-19
> **iponeverything said:**
> Enlighten me please. How does running a X server make your server less secure?

[http://www.google.com/search?q=X11+vulnerabilities&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=X11+vulnerabilities&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Do a little homework before making snide comments, please. Having more services and software installed means more patching and more vulnerabilities. I'm not saying that X is a major security hole. If you read my comment you'd know that. I'm saying it's more software to manage that has its own set of vulnerabilities that can affect the rest of the system.

---

### Post by daboroe on 2008-11-19
> **y@w said:**
> [http://www.google.com/search?q=X11+vulnerabilities&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=X11+vulnerabilities&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Do a little homework before making snide comments, please. Having more services and software installed means more patching and more vulnerabilities. I'm not saying that X is a major security hole. If you read my comment you'd know that. I'm saying it's more software to manage that has its own set of vulnerabilities that can affect the rest of the system.
thank you for your response  y@w. What is the link you posted?

---

### Post by iponeverything on 2008-11-19
> **y@w said:**
> [http://www.google.com/search?q=X11+vulnerabilities&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=X11+vulnerabilities&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

I'm saying it's more software to manage that has its own set of vulnerabilities that can affect the rest of the system.

Thanks y@w :)

---

### Post by mitchroberts on 2008-11-20
> **iponeverything said:**
> Thanks y@w :)

Do a little homework before making snide comments linux buy far has 1 bad vulnerability that has not had a patch yet i know i tryed it on 8.04 yes linux is better and i am a big fan but to say its bad or has more vulnerability with a gui it dont the other software has that it's more software to manage but if you cant manage it you don't need to have it...yes it's more software to manage that has its own set of vulnerabilities that "can" affect the rest of the system key word being "can" but most people do not have a lot of time to do it that way.I use a gui so i will have a desktop on my lts build and it works great by far a lot better then the other way...

---

### Post by iponeverything on 2008-11-21
> **mitchroberts said:**
> Do a little homework before making snide comments linux buy far has 1 bad vulnerability that has not had a patch yet i know i tryed it on 8.04 yes linux is better and i am a big fan but to say its bad or has more vulnerability with a gui it dont the other software has that it's more software to manage but if you cant manage it you don't need to have it...yes it's more software to manage that has its own set of vulnerabilities that "can" affect the rest of the system key word being "can" but most people do not have a lot of time to do it that way.I use a gui so i will have a desktop on my lts build and it works great by far a lot better then the other way...

what are you talking about? 

Or are just trying to get me to be more polite. It thats the case, then thanks.

If its to tell me that running an x server on server is bad idea, indeed it is -- if the person running server has it on public IP address and has no business running a server on a public address in the first place.

Did you bother to look at google search results?

---

### Post by y@w on 2008-11-21
> **iponeverything said:**
> what are you talking about? 

Or are just trying to get me to be more polite. It thats the case, then thanks.

If its to tell me that running an x server on server is bad idea, indeed it is -- if the person running server has it on public IP address and has no business running a server on a public address in the first place.

Did you bother to look at google search results?

Haha.. we might be running into a language barrier here.. 

Anyway, to the OP: the answer is more of a general security model answer than specifically about X11. In general, you want to run as little software as possible to make as small of a target for potential attackers as possible. Of course, if there's a need to run X, then go for it (after all, you need it). Just be aware that, from a high level, there's always added risk in installing more software whether X11 is specifically vulnerable right now or not. Of course, "security" is a moving target anyway :)

---

### Post by mitchroberts on 2008-11-21
> **iponeverything said:**
> what are you talking about? 

Or are just trying to get me to be more polite. It thats the case, then thanks.

If its to tell me that running an x server on server is bad idea, indeed it is -- if the person running server has it on public IP address and has no business running a server on a public address in the first place.

Did you bother to look at google x server?

I am not trying to piss you off or make you mad but running an x server on server is not a bad idea if it is then why???If i was trying to do something to a linux box the last place i would go looking is the x server or anywere near there i would look to the boot loader.how hard would it be to get in from there just try it and you will see what i am talking about.I did look at the google and no one is going to hack a server from stuff you get off there
i am sorry if i pissed you or made you mad but if i was going to do something 
like that then i would look were i could do the most damage and going in that
way would not do it.Run a update,patch it encrypt it or whatever but bottom line is if there trying hard to do it your not going to stop them anyway.All you can do is damage control and catch them.

---

### Post by iponeverything on 2008-11-21
> **mitchroberts said:**
> I am not trying to piss you off or make you mad but running an x server on server is not a bad idea if it is then why???If i was trying to do something to a linux box the last place i would go looking is the x server or anywere near there i would look to the boot loader.how hard would it be to get in from there just try it and you will see what i am talking about.I did look at the google and no one is going to hack a server from stuff you get off there
i am sorry if i pissed you or made you mad but if i was going to do something 
like that then i would look were i could do the most damage and going in that
way would not do it.Run a update,patch it encrypt it or whatever but bottom line is if there trying hard to do it your not going to stop them anyway.All you can do is damage control and catch them.

I am not mad.. just very confused. Believe it not -- we are on the same page. 

It reminds me of a time in Chennai when I ask a question to a group of six guys and from the answers I got -- not one of them heard the same question and not one of them understood the question that I ask. And from the ensuing confusion afterward, I realized that they really didn't understand each other either. I suppose its on one of the drawbacks of India having so many official languages.

Running X on a server is not bad, except in the case where a local escalation makes it that much easier for a black hat to have a safe platform to attack another box.  I have lost count of the number of times that I have been on the phone with someone that had no idea that their server was owned or how to fix it.  I don't think anyone wants a couple of black suited feds walking into their home or office and walking off with their box -- because it was used to cover someone's tracks in in an attack on a bank's server or worse.

---

### Post by mitchroberts on 2008-11-21
> **iponeverything said:**
> I am not mad.. just very confused. Believe it not -- we are on the same page. 

It reminds me of a time in Chennai when I ask a question to a group of six guys and from the answers I got -- not one of them heard the same question and not one of them understood the question that I ask. And from the ensuing confusion afterward, I realized that they really didn't understand each other either. I suppose its on one of the drawbacks of India having so many official languages.

Running X on a server is not bad, except in the case where a local escalation makes it that much easier for a black hat to have a safe platform to attack another box.  I have lost count of the number of times that I have been on the phone with someone that had no idea that their server was owned or how to fix it.  I don't think anyone wants a couple of black suited feds walking into their home or office and walking off with their box -- because it was used to cover someone's tracks in in an attack on a bank's server or worse.


most people dont need to run X on a server is not bad but if they don't know how to lock it down then your right it can be
i run it but i need a desktop on the clients of my terminal server i have it locked down real good.

good talking with you

Mitch

---

