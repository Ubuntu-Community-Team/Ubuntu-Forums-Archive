---
title: "Recommend an email server installation..."
date: 2012-02-07
forum: Server Platforms
---

### Post by jamesp81 on 2012-02-07
that will actually work if I follow the instructions on how to set it up.

This is for personal use.  Running Ubuntu 11.04.  It needs to be robust and secure, and I don't want something that the publisher is going to use read my email so they can send me junk mail constantly.

I do not have good feelings about linux in general, but it's supposedly more secure than Windows.  However, I've ran mailtraq pretty extensively on a Windows box with good success, and I'm sorely tempted to go with that.  However, I don't trust non open source software to not spy on me for marketing purposes.

What do you all recommend?

---

### Post by restorator on 2012-02-07
> I do not have good feelings about linux in general, but it's supposedly more secure than Windows. However, I've ran mailtraq pretty extensively on a Windows box with good success, and I'm sorely tempted to go with that. However, I don't trust non open source software to not spy on me for marketing purposes.

What do you all recommend? 

I recommend that if you "don't trust open source" Then stick with what you do. But I would also recommend that if you are really that fearful, you spend the time to thoroughly research this issue a little more in depth than asking a forum question. 

When you look more in into it you should find that open source software is many times MORE likely to be free from hidden programs or "spying" as you fear. Generally the reason is that the more people that can see the code, the more likely they are to find anything bad and if they do they quickly speak out against it. You can contrast this with closed source software that only a few select people know what it contains and they may be bound by a non-disclosure agreement. It has happened in the past where programs were hidden inside reputable programs made by top vendors of closed source programs. Personally I would trust open source to be much more likely to NOT spy on me.



EDIT**  OOPS! , I re-read that and found that i missed the "non" in your original post and found you were in agreement with my statements. Please disregard....

---

### Post by jamesp81 on 2012-02-07
> **restorator said:**
> I recommend that if you "don't trust open source" Then stick with what you do. But I would also recommend that if you are really that fearful, you spend the time to thoroughly research this issue a little more in depth than asking a forum question. 

When you look more in into it you should find that open source software is many times MORE likely to be free from hidden programs or "spying" as you fear. Generally the reason is that the more people that can see the code, the more likely they are to find anything bad and if they do they quickly speak out against it. You can contrast this with closed source software that only a few select people know what it contains and they may be bound by a non-disclosure agreement. It has happened in the past where programs were hidden inside reputable programs made by top vendors of closed source programs. Personally I would trust open source to be much more likely to NOT spy on me.

You misunderstand.  I distrust **non** open source software.

The reason I'm looking into linux is because I would prefer to run open source if possible.  But, again, that involves finding mail server software that, as I said, will actually work when I follow the directions:)

---

### Post by druhboruch on 2012-02-08
The Ubuntu repository contains mail-stack-delivery package that performs a complete install and secure configuration of Postfix and Dovecot (pop3, imap and sieve) with SASL authentication TLS support and maildir style mailboxes.
It contains everything you need to set up an internet facing mail server.
After the installation you may want to change the user authentication mehtod and use postfix-admin and mysql, ldap or samba4...

---

### Post by HermanAB on 2012-02-08
Howdy,

The easiest mail system to set up is Citadel.  Go to citadel.org and run the Easy Install script.  It takes about 20 minutes, provided that you have your DNS configured already of course.  

I have been running Citadel with numerous small business users for more than 10 years.  It works - nuf sed.

---

### Post by Cheesemill on 2012-02-08
I've been using the tutorials at [[COLOR=black]http://workaround.org/ispmail[/COLOR]]("http://workaround.org/ispmail") for years successfully.

They're based on Debian instead of Ubuntu, but I prefer this for my mail servers as Debian stable tends to break less often than Ubuntu (for me anyway).

The tutorial is very long but does explain in detail not only what steps to take but why you are doing them, so you actually learn how your email system works rather than just blindly following instructions.

All in all a 5:KS tutorial.

---

