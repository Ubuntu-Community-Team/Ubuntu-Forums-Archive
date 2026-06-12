---
title: "Program to delte private data"
date: 2006-10-26
forum: Server Platforms
---

### Post by Oki on 2006-10-26
Hi

I just (almost) left Windows for Ubuntu(Dapper Drake). So far I loving it. 

When using Windows I had some programs that could delete your «private data», so the next person that used the pc cant see everything you have done/been. I am thinking about recently used documents, browser historikk (Opera, FF), trash can and so on. The programs are called Ccleaner and Privacy Guardian. It is not needed to delete the data for good &#8211; just so it is not that easy for others to look. 

So my question; are there programs like this for Linux? I know you could make a script, but I cant do that. 

Thanks for your help(and sorry my poor English)

---

### Post by madmetal on 2006-10-26
in firefox there is an option to delete historic cookies etc..
in places >> recent documents there is an option to delete recent documents..
i dont know if there is a program..

---

### Post by lloyd_b on 2006-10-26
> When using Windows I had some programs that could delete your «private data», so the next person that used the pc cant see everything you have done/been. I am thinking about recently used documents, browser historikk (Opera, FF), trash can and so on. The programs are called Ccleaner and Privacy Guardian. It is not needed to delete the data for good – just so it is not that easy for others to look.

Provided that the next person logs in as a different user, then all you need to do is change the permissions on your home directory.  With permissions on "/home/myuser" set to 700, nobody without root access (via "sudo") is going to be able to see what's in that directory.  All of your "private data" (browser history, recent documents, etc) is stored within your home directory....

Lloyd B.

---

### Post by Oki on 2006-10-26
Thanks for your answers:) 

I know how to manually delte those savings, Opera has this option to. You can also download an extension for FF called Panic button he he I have also thought about making a «guest» profile &#8211; but was more hoping to hear that there was a program that could fix it:-k Let say I have guest; then I would say "wait, I most change the profile"... Sorry for my bad English!

---

### Post by madmetal on 2006-10-26
if you have a guest switch user! why not?
if privacy is your priority then its an easy way to have it!

---

