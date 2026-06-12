---
title: "using ubuntu as a server with terminals running windows"
date: 2009-09-25
forum: Server Platforms
---

### Post by itachis.eyes on 2009-09-25
do i need to make any special "arrangements" to do this or will the linux server integrate with windows computers without any modifications?
and if i do need to do something special, what is it that i need to do? for example would i need to install BASH on the windows computers

---

### Post by abaden on 2009-09-25
What exactly are you trying to do? If you want to use Ubuntu like [ActiveDirectory]("http://en.wikipedia.org/wiki/Active_Directory") (delivering software, sharing folders, etc) you will find it to be a little more challenging to setup with Windows. There are third party apps for most of that, but you will have to do some searching. 

One example is Samba, which can be used to share folders on your ubuntu server that can be accessed by multiple windows machines, each with their own user account. Is this the kind of thing you are looking to do?


Alex

---

### Post by scorp123 on 2009-09-26
> **itachis.eyes said:**
>  or will the linux server integrate with windows computers without any modifications?Not even a Windows server would do that. So what exactly are you talking about? What is it that you want to achieve here??

> **itachis.eyes said:**
>  for example would i need to install BASH on the windows computers If you feel like using Bash to control your Windows PC's ... But most Windows users are already overwhelmed by the standard Windows "***cmd***" shell. If you want a powerful shell on Windows you might as well go for Microsoft's own ***PowerShell***.

But somehow I get the impression that's not what you wanted. What you seem to want is e.g. ***Putty*** ... a SSH client for Windows with which you could connect to a remote Linux system and thus control it. But if you have to ask *such* things I honestly think you're already way over your head. Sorry to say so, but that's the impression I get after reading your strange question up there.

---

### Post by itachis.eyes on 2009-09-26
> **abaden said:**
> What exactly are you trying to do? If you want to use Ubuntu like [ActiveDirectory]("http://en.wikipedia.org/wiki/Active_Directory") (delivering software, sharing folders, etc) you will find it to be a little more challenging to setup with Windows. There are third party apps for most of that, but you will have to do some searching. 

One example is Samba, which can be used to share folders on your ubuntu server that can be accessed by multiple windows machines, each with their own user account. Is this the kind of thing you are looking to do?


Alex

yes just a simple file sharing server (sorry, i probably should have mentioned that in my first post)

---

### Post by itachis.eyes on 2009-09-26
> **scorp123 said:**
> Not even a Windows server would do that. So what exactly are you talking about? What is it that you want to achieve here??

 If you feel like using Bash to control your Windows PC's ... But most Windows users are already overwhelmed by the standard Windows "***cmd***" shell. If you want a powerful shell on Windows you might as well go for Microsoft's own ***PowerShell***.

But somehow I get the impression that's not what you wanted. What you seem to want is e.g. ***Putty*** ... a SSH client for Windows with which you could connect to a remote Linux system and thus control it. But if you have to ask *such* things I honestly think you're already way over your head. Sorry to say so, but that's the impression I get after reading your strange question up there.

well just a file sharing server. 
a SSH client is...further down the list as far as educating myself about networking, which has always been one of my short comings.

---

### Post by lmlypfan on 2009-09-26
Here is a quick guide on [samba]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Filesharing")

---

### Post by scorp123 on 2009-09-26
> **itachis.eyes said:**
> well just a file sharing server. Well, you need to learn SAMBA then. The poster above me already gave you the link. Try that.

---

