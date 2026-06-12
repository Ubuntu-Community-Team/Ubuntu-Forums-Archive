---
title: "Email accounts and passwords"
date: 2012-02-05
forum: The Cafe
---

### Post by hyperAura on 2012-02-05
Hi people,

I was thinking today about possible measures to safeguard my email accounts and I would like to ask other people if this could prove useful or really bad..

Imagine you have received a fraudulent email that went through your junk filter and as soon as you open it, it sends various emails to your contacts without you noticing. 

I was thinking that in cases like this it would be good if the client email program would ask you for a password in order to send the emails.. Well not in all cases, but lets say in case you are sending to more than 3 people at the same time or 3 different emails within a minute..

So what do you think about this?

---

### Post by haqking on 2012-02-05
> **hyperAura said:**
> Hi people,

I was thinking today about possible measures to safeguard my email accounts and I would like to ask other people if this could prove useful or really bad..

Imagine you have received a fraudulent email that went through your junk filter and as soon as you open it, it sends various emails to your contacts without you noticing. 

I was thinking that in cases like this it would be good if the client email program would ask you for a password in order to send the emails.. Well not in all cases, but lets say in case you are sending to more than 3 people at the same time or 3 different emails within a minute..

So what do you think about this?

disable your password for SMTP and then it will, in evolution for example under account settings choose account then under sending (SMTP) remove the tick from remember password

---

### Post by keithpeter on 2012-02-05
> **haqking said:**
> disable your password for SMTP and then it will, in evolution for example under account settings choose account then under sending (SMTP) remove the tick from remember password

Nice idea, but in the UK anyway, most ISPs don't require or provide SMTP authentication. They simply check that you are actually a subscriber to their service.

My solution is to use a shell account with a mail server, then to enable spam assassin at a suitably paranoid level. My fallback is to have a lot of mail boxes, basically one for each project.

---

### Post by haqking on 2012-02-05
> **keithpeter said:**
> Nice idea, but in the UK anyway, most ISPs don't require or provide SMTP authentication. They simply check that you are actually a subscriber to their service.

My solution is to use a shell account with a mail server, then to enable spam assassin at a suitably paranoid level. My fallback is to have a lot of mail boxes, basically one for each project.

I am in the UK, and i never use ISP email accounts. all my 10+ email accounts require SMTP auth.  It was just a generic solution for the password request issue really.

---

### Post by keithpeter on 2012-02-05
> **haqking said:**
> I am in the UK, and i never use ISP email accounts. all my 10+ email accounts require SMTP auth.  It was just a generic solution for the password request issue really.


Neither do I, but when I want to send e-mail from an e-mail client installed on my desktop, I just use smtp.orange.co.uk no authentication and it goes off into the interweb.

I've had to search hard to find a hosting company that provide an *authenticated* smtp as I want to send stuff off the phone, and for roaming wifi use.

---

### Post by SeijiSensei on 2012-02-05
I've used **thunderbird** for years and have never seen this problem.  I don't use SMTP authentication, either.

Maybe you should just leave those messages in your junk mail folder alone, or download them as text files before reading them locally with a text editor.

Does this happen when you're reading your mail with a web client?  If so, what kind of bozo mail provider enables a message to clone itself automatically without your permission?  Sounds like it's time for a new mail provider to me.

---

### Post by HermanAB on 2012-02-05
> as soon as you open it, it sends various emails to your contacts without you noticing
Simple - don't use MS Outlook on Windows 95...

---

