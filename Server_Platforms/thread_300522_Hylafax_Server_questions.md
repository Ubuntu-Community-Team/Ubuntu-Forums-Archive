---
title: "Hylafax Server questions"
date: 2006-11-15
forum: Server Platforms
---

### Post by profediego on 2006-11-15
Hi everyone, 

I managed to install a hylafax server, its up and running at the moment, but i have some questions about improvement or tweakin it.

Rigth know it has his own phone line, i mean is a dedicated line to send and receive faxes only.  
---------------------------------------------------
So my fisrt questions is:  Can a hylafax server become a telefax one.  I mean where i can program it to answer phone after 3 rings, and not rigth away when the phpne starts to ring??? And if a can answer the phone and the person in the otherside says he needs fax signal, can i do that?? How??

----------------------------------------------------

Second one:  My installation receives a fax and send the fax to my inbox (email), it took me a while to figure how but i managed to do it, But, there are 5 persons in the office so i want to program the server so it can figure it out to which email it has to send the fax.  Can i somehow know that, is there a variable or somthing i can refer to?? or a config file or i dont know something :P
---------------------------------------------------

Thanks in advance to every answer or guidance you can give me.

---

### Post by profediego on 2006-11-16
Hi, me again, 

I keep on readin and realize, with 'man faxrcvd', all the environment variable i need(answer to question 2), i guess, ill tell you later, how it went.  Thanks

Still looking for an answer of question one.  :-k

---

### Post by Adler on 2006-11-23
I've never been able to send / receive Faxes w/ Linux. I've been looking for the App that works right from my Desktop.

I'd always used all the WinFax versions, but need to send people faxes every once in the while. Since I've gone total Linux this one issue keeps coming back

Really -- this is the *Holy Grail* for me. Funny, huh?

I've asked this before *everywhere*.

HELP!

Adler

---

### Post by profediego on 2006-11-23
hey, hi.  More than pleased to help you man, ihave received a lot of help in this forum from many ppl.  Just tell me what you need and if i can, i will help you.

I know that oyur modem has to be linux friendly, thats the only big big problem i had, but once that is ready is just install hylafax (sudo apt-get install hylafax-server) then run faxsetup answer a few questions, and other just leave them by default.  then run faxaddmodem, and if everything is alrigth it will automatically detect your modem, and here i just use defaults in almost everything.

ok know that your fax-sever is setup. i just install gfax, sudo apt-get install gfax, conifgure and thats it.  you can fax everywhere.  Only thing is i can only fax pdf files.   

I know my english is really bad, so if i apologize, also know i am not good at writing guides, so if you have trouble with something and i can help you , well just ask.

---

### Post by Adler on 2006-11-23
profediego,

Your English is great.

Thanks for that reply. I'll try out what you suggested. Funny, how such a simple thing, becomes so complex.

Thanks again.

Adler

---

