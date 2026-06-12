---
title: "Which software can I use to develop a multiplayer game?"
date: 2013-02-02
forum: Ubuntu Application Development
---

### Post by clay7 on 2013-02-02
Hello. I would like to make a "Jeopardy!" style game which people can play by themselves or against other live online players. Actually, this will be an upgrade to a present game which lets players play by themselves but does not have online functionality. This game is in VB.net. I want to add online functionality so players can play against each other in real time if they so chose.

One of my biggest requirements is that the server side of this game must run on a Linux server, and I am most familiar with Ubuntu servers. **How do I develop the server side of this game in VB.net when it must run on an Ubuntu server? **

I have Visual Studio 2010 so converting the code another .net language is possible. I know PHP and MySQL as well. If you think a different development language/environment is better for what I'm trying to do, I am willing to learn since time is not the highest priority.

---

### Post by DominikST95 on 2013-02-02
This won't be possible, because VB.NET applications are Windows-Only. You could try to use Mono, which is an adaption of the .Net runtime environment, but be aware, that some functions are missing in Mono.

What can you do now? There is a language quite similar to VB, called Gambas. You could try to port your game to Gambas, the syntax is nearly the same. An other option would be, to develop the server-site of your game in a language, that runs on Ubuntu. Then you just have to program a communication between server and client and you are good to go :)

Hope, I could help you ;)

---

### Post by clay7 on 2013-02-02
Thanks for the reply. What language can I use to develop the server side that is similar to vb.net OR is relatively easy to learn for the purposes mentioned above? (My level of experience: I've been programming in vb.net and PHP for around 10 years).

---

### Post by AdjunctBlack on 2013-02-02
> **DominikST95 said:**
> This won't be possible, because VB.NET applications are Windows-Only. You could try to use Mono, which is an adaption of the .Net runtime environment, but be aware, that some functions are missing in Mono.

What can you do now? There is a language quite similar to VB, called Gambas. You could try to port your game to Gambas, the syntax is nearly the same. An other option would be, to develop the server-site of your game in a language, that runs on Ubuntu. Then you just have to program a communication between server and client and you are good to go :)

Hope, I could help you ;)

This is not exactly true.
VB.Net is a CLR language and therefore is supported by Mono and Mono-Develop(although it does not enjoy the same support as C# on the Mono platform).

If you are interested in building a game using Mono, you might want to take a look at MonoGame (free as in choice and beer) or something like Unity that makes use of .NET/Mono(not free as in beer)

---

### Post by _exn_ on 2013-02-03
hm, interesting. i've made a lot of games like this for web in the past, if you already have "server logic" on the paper and data -"questions,answers" database, i'd participate in development process. i'm suggesting using html5 (canvas) front-end developed using gwt , back-end - java or nodejs.. but java is much better

simple :
```

 F (HTML5)
      |
     (WS)
      |
 B (apache mina, netty, or so)
      |
 DB (Precached inmemory db, memcached..?)


```

---

### Post by solarghost on 2013-03-27
I would recommend Java EE in the back-end using an application server like Jboss, then you can easily do database interactions and web services using EJB/JPA.

---

### Post by mharv on 2013-03-30
If the client is browser based and performance is acceptable then converting to Mono will probably be the quickest/easiest solution.
> a different development language/environment is better for what I'm  trying to do, I am willing to learn since time is not the highest  priority
Writing in C will always be the best language/environment for someone who is competent with it so you may want to invest the time in learning it. It does take a significant amount
more time/effort than just reading an online tutorial and then jumping into code though.

---

