---
title: "What is securetty for?"
date: 2011-06-21
forum: Security
---

### Post by eddie3000 on 2011-06-21
First of all, I am an absolute newbie. And I hope what I say/ask makes sense. :D
I have been searching and all I have found is, basically, that the securetty file determines from which terminals root can login. Is that so? What terminals?  I deleted it and I can still do root operations from a terminal. 
How can I know what the contents of the file mean?
In what way can I make my computer more secure by deleting/renaming the file?
Hope I'm not too problematic. Thanks.

---

### Post by terrykiwi83 on 2011-06-21
am sorry I have no idea what your talking about? am assuming by securetty you possibly mean Security? Also what do you mean by security file, what is the name of this file and were is it located?

---

### Post by eddie3000 on 2011-06-21
Sorry, I meant the /etc/securetty file in Ubuntu (and probably other linux distos too).

---

### Post by spynappels on 2011-06-21
As you said, it determines on which TTY root can log in, but in Ubuntu root login is disabled by default, so removing it will not make any difference. 

You log in with your own username and use sudo or su when you need root privileges, you don't log in as root directly.

---

### Post by eddie3000 on 2011-06-21
Thank you. So why is it there then? I'm guessing that if you activate a root account in ubuntu it then stops ignoring the securetty file, and by the looks of the file, activating a root account without editing the secuetty file would open your computer to the world, right?

---

### Post by Thewhistlingwind on 2011-06-21
> **eddie3000 said:**
> Thank you. So why is it there then? I'm guessing that if you activate a root account in ubuntu it then stops ignoring the securetty file, and by the looks of the file, activating a root account without editing the secuetty file would open your computer to the world, right?

About opening your computer to the world. I don't know, probably not.

On the subject of root accounts in Ubuntu, theres far better reasons NOT to open a root account then anything having to do with tty.

---

### Post by eddie3000 on 2011-06-21
Thank you guys for your help. I will not create a root account under any circumstance. 
:guitar:

I intend to learn linux, slowly but surely. I like it very much. Could somebody point me in some direction where I can get step by step tutorials, documentation, courses, or whatever that will explain what the securetty file is for and what it's contents mean? And even this is offtopic, how about how to setup a secure server with remote access available via ssh?

---

### Post by spynappels on 2011-06-21
I would suggest you start by reading the security stickies at the top of this forum, they give a very good overview of keeping your systems secure. IMHO, it is a mistake to focus on one aspect, such as the /etc/securetty file, when a broader view is required to keep your systems secure, and reading the stickies will help you get the broader view.

Remember that there is no such thing as absolute security, but with Linux you are starting from a much better baseline than you might be used to. Read lots and ask lots of questions, and ignore most of the panic stories you will see about linux viruses, linux anti-virus etc as they are just that. Any real threats will be picked up on and fixed very quickly and will get publicity in places like these forums.

Enjoy Linux, it really is worth putting some time into.

---

### Post by eddie3000 on 2011-06-21
Ok, thanks. Good advice. I will read a lot and ask when I don't understand. I've already read through many stickies and security related stuff. But quite a lot sounds a bit like chinese to me still. I have a long way to go yet.
The reason I was interested in the /etc/securetty file is that I had an exam yesterday and I was asked "Can you login as root if the /etc/securetty file is deleted?". I hadn't the faintest idea. So I renamed and deleted the file, rebooted, and discovered I could do anything I wanted as root using sudo. I had three options: 1-Yes, 2-No, 3-Only graphical mode but not shell. I answered "1-Yes" but I still don't know the real answer. The course documentation doesn't even mention the matter. :confused:
Thank you very much for your replies.

---

