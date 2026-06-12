---
title: "Which should I download ?"
date: 2011-08-13
forum: Server Platforms
---

### Post by FMS.SouL on 2011-08-13
Hello I'm new of this forum,I think I post correct section.:)
Straight to the point of my question.
First of all,I tell my PC operating system information,I'm using window 7 starter 32bits and now I planning to download ubuntu system.
As I know,1 PC can install 2 type of windows,so I wanna download thing from ubuntu is remote desktop.Of course I do not mean team viewer,a live remote desktop.
What I wanted is remote desktop called virtual private server,that can make my application running online 24/7 even I offline.
I found many type of download link,I'm afraid I downloaded wrong or something bad happen during I install it.:p
Thank you for checking my thread.:KS

---

### Post by FMS.SouL on 2011-08-13
Bump~
Any moderators or someone else can asnwer my question ? :(

---

### Post by allwimb on 2011-08-13
Do you want to install and configure a VPS ?

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by volkswagner on 2011-08-13
You should wait 24 hours before bumping a thread.

Your question is not clear.

A virtual private server is typically located at a data center that you can subscribe to.

Remote desktop requires the server to have a GUI, which is not included by default on Ubuntu server.

I'm going out on a limb to guess you may be interested to install Ubuntu as a guest Virtual machine.

Please clarify.

---

### Post by FMS.SouL on 2011-08-13
First of all,sorry for bump thread.
I just wanted a Linux/Ubuntu server,which can make my application running 24/7 even I shut down the PC:)

---

### Post by arrrghhh on 2011-08-13
> **FMS.SouL said:**
> First of all,sorry for bump thread.
I just wanted a Linux/Ubuntu server,which can make my application running 24/7 even I shut down the PC:)

Well you would need to buy some hosted services.  It's not possible to keep services running when the PC is shutdown.

You can run a virtual machine, which would run Linux inside of Windows.  You could dual-boot, where when you turn on the PC you can choose Linux or Windows.  But nothing exists that would give you the ability to continue to have services running when the PC is shut down - short of paying a monthly fee for a VPS, a hosted server, what-have-you.  Not sure what your needs are...  The more information the better (usually ;))

---

### Post by FMS.SouL on 2011-08-13
> **arrrghhh said:**
> Well you would need to buy some hosted services.  It's not possible to keep services running when the PC is shutdown.

You can run a virtual machine, which would run Linux inside of Windows.  You could dual-boot, where when you turn on the PC you can choose Linux or Windows.  But nothing exists that would give you the ability to continue to have services running when the PC is shut down - short of paying a monthly fee for a VPS, a hosted server, what-have-you.  Not sure what your needs are...  The more information the better (usually ;))
I saw at Ubuntu server download page there wrote :
**Why use Ubuntu for servers?**

 		 			[URL="http://www.ubuntu.com/business/server/reduce-costs"] 				**Reduce costs ›**

 				Free to use and redistribute without charge, no licence restrictions mean you can expand your IT systems without the expense.
[/URL][URL="http://www.ubuntu.com/business/server/reduce-costs"]

[/URL]It's free,isn't ?

---

### Post by arrrghhh on 2011-08-13
> **FMS.SouL said:**
> I saw at Ubuntu server download page there wrote :
**Why use Ubuntu for servers?**

 		 			[URL="http://www.ubuntu.com/business/server/reduce-costs"] 				**Reduce costs ›**

 				Free to use and redistribute without charge, no licence restrictions mean you can expand your IT systems without the expense.
[/URL][URL="http://www.ubuntu.com/business/server/reduce-costs"]

[/URL]It's free,isn't ?

Oh yes, Ubuntu itself is completely free and open source.  No licensing restrictions, it's pretty much all GPL.

But what you were asking was ludicrous, you wanted to be able to shut down your PC and still have services run, like a website.  That's not possible :p.

---

### Post by FMS.SouL on 2011-08-13
> **arrrghhh said:**
> Oh yes, Ubuntu itself is completely free and open source.  No licensing restrictions, it's pretty much all GPL.

But what you were asking was ludicrous, you wanted to be able to shut down your PC and still have services run, like a website.  That's not possible :p.

Well,not hosting website,just running application 24/7.For example running maple story client,Mozilla firefox and online game etc.:D

---

### Post by arrrghhh on 2011-08-13
> **FMS.SouL said:**
> Well,not hosting website,just running application 24/7.For example running maple story client,Mozilla firefox and online game etc.:D

Sounds like you want Ubuntu Desktop edition.  The server edition has no GUI (point-and-click interface).  So grab the Desktop Edition, **not** the Server edition.  Most people administer their servers remotely, and GUI interfaces are just unnecessary.

I also don't see why you need Firefox or whatever the heck Maple Story is 24/7...

---

### Post by dFlyer on 2011-08-13
My advice is download ubuntu 11.04 live desktop and test your system to make sure your hardware can run linux before you do anything. If 11.04 doesn't work than try 10.04 or 10.10 live desktops.

---

### Post by FMS.SouL on 2011-08-13
> **arrrghhh said:**
> Sounds like you want Ubuntu Desktop edition.  The server edition has no GUI (point-and-click interface).  So grab the Desktop Edition, **not** the Server edition.  Most people administer their servers remotely, and GUI interfaces are just unnecessary.

I also don't see why you need Firefox or whatever the heck Maple Story is 24/7...

I just give an example for let you get my point. :)
@dFlyer,the desktop edition can running the application even I shut down my PC ?

---

### Post by arrrghhh on 2011-08-13
> **FMS.SouL said:**
> I just give an example for let you get my point. :)
Btw,the desktop edition can running the application even I shut down my PC ?

Dude... Like I said before, no application/service/whatever can run if you shut down your PC.  Desktop Edition, Server Edition, I don't care edition.  You can't run a service on a machine that is powered off...

The Desktop Edition can run all the same services the Server Edition has.  If you want to run Firefox, you're going to want the Desktop Edition.  Heed the advice in the previous post, grab 11.04 Desktop Edition and try it 'live' - you can boot off the CD or DVD or even USB key and not make any modifications to your PC - make sure hardware works correctly.

---

### Post by 1serveyou on 2011-08-15
Is the PC and the server the same machine? Or are they two different machines?

---

