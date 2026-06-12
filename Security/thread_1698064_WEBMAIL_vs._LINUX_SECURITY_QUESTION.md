---
title: "WEBMAIL vs. LINUX SECURITY QUESTION"
date: 2011-03-01
forum: Security
---

### Post by flihi on 2011-03-01
Which is more secure, webmail email providers such as Yahoo or Linux desktop email clients such as Evolution?

---

### Post by HermanAB on 2011-03-02
Depends on the protocol. Normal mail protocols are plain text, but all have SSL equivalents.

You can run webmail over HTTPS and similarly use IMAPS, POPS, SMTPS etc with a mail client.

---

### Post by gerowen on 2011-03-02
I use Evolution, and generated a personal encryption key for myself and one for my wife so that if I want to send something sensitive to her, it gets encrypted using our own encryption keys.  I feel like this is a fairly secure solution regardless of who actually hosts your email service.

---

### Post by wacky_sung on 2011-03-02
> **gerowen said:**
> I use Evolution, and generated a personal encryption key for myself and one for my wife so that if I want to send something sensitive to her, it gets encrypted using our own encryption keys.  I feel like this is a fairly secure solution regardless of who actually hosts your email service.

This sound good but i do not like being a slave to email clients.I still prefer using browser to do everything securely through browser with SSL. That is just a personal preferences.

---

### Post by HermanAB on 2011-03-02
Note that the SSL protocols only provide security between your PC and the mail server.  So it is good for securing yourself a little in a coffee shop or airport, but it does nothing against a snoop in an ISP.  

Evolution encrypted email is secure end to end - nobody in the middle can read your email.

---

### Post by Irihapeti on 2011-03-02
Be aware that, no matter what kind of security you use, an email is only as secure as the person(s) you send it to. Emails can and do get forwarded to others, even when they shouldn't be.

It's happened a couple of times to me. It's made me more careful of what I put in emails.

---

### Post by flihi on 2011-03-02
> **Irihapeti said:**
> Be aware that, no matter what kind of security you use, an email is only as secure as the person(s) you send it to. Emails can and do get forwarded to others, even when they shouldn't be.

It's happened a couple of times to me. It's made me more careful of what I put in emails.
I buy merchandise from online stores such as Amazon. These online stores will always send a confirmation email with my account number and hopefully WITHOUT my credit card number. I do not like the idea of somebody sending computer code directly to my computer in this case being emails via Evolution. What I like better is accessing my emails from a third party in this case being webmail. But I question how secure my merchant account information is in cyberspace.

---

### Post by brian_p on 2011-03-02
> **flihi said:**
> I buy merchandise from online stores such as Amazon. These online stores will always send a confirmation email with my account number and hopefully WITHOUT my credit card number. I do not like the idea of somebody sending computer code directly to my computer in this case an email via Evolution. What I like better is accessing my emails from a third party in this case webmail.

The email does not do directly to your computer unless you are running a mail server. It goes to a third party which could be your ISP or webmail provider. With Evolution you can download it and read it. With a webmail client it is read on the provider's server. What's the problem? I'd rather have mail on my machine than someone elses.

> But I question how secure my merchant account information is in cyberspace.

This is a different issue. With reputable suppliers security is an important issue.

---

### Post by Irihapeti on 2011-03-02
Re unexpected forwarding, I was actually thinking of that "friend" who decides to forward your email to half the people in their address book.

One reason I get cheesed off with chain letter forwarders is because my email address ends up goodness only knows where. You only need one person with a dubious friend and...  

...SPAM ahoy!...

---

### Post by pafufta503 on 2011-03-02
> **Irihapeti said:**
> Re unexpected forwarding, I was actually thinking of that "friend" who decides to forward your email to half the people in their address book.

One reason I get cheesed off with chain letter forwarders is because my email address ends up goodness only knows where. You only need one person with a dubious friend and...  

...SPAM ahoy!...i can thank my mother and my grandparents for doing this to me.  they would send every chain letter to me they got, it became frustrating after a while.  each chain letter would have so many forwards that there were upwards of 100's and sometimes 1000's of e-mail addresses contained in each e-mail.  equally as annoying as my address being exposed was that the forwarding info text was around 20 pages or longer while the chain letters original text was generally less than a page long.

---

### Post by Rasputin69 on 2011-03-03
> **flihi said:**
> Which is more secure, webmail email providers such as Yahoo or Linux desktop email clients such as Evolution?

POP3 with digital certificate is best.

You can also use TrueCrypt to create a small container and use it for email as an attachment and pass the pass word by separate channel. 

Face to Face is the best way to pass a password.

---

### Post by flihi on 2011-03-03
> **Rasputin69 said:**
> POP3 with digital certificate is best.

You can also use TrueCrypt to create a small container and use it for email as an attachment and pass the pass word by separate channel. 

Face to Face is the best way to pass a password.
If I am not mistaken, one can use pop3 with a digital certificate with either a desktop email client or a webmail provider. Which do you recommend?

---

