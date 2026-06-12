---
title: "encrypted email web portal server"
date: 2018-02-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Paul_Sueno on 2018-02-02
Hi all.

I want an open-source solution I've been digging for these past few months. I need to deploy a system whereby an email and attachment is sent securely through all steps. I know I can set up a Postfix-Dovecot with TLS system. However, I don't think there is a current way to ensure every downstream server also encrypts the email and attachment by TLS. 

I have been using a proprietary system through 4securemail.com. I can add a token string in my subject (e.g., encrypt or secure), and their proprietary system will make my recipient log into a secure web portal to access the encrypted email and attachment. I would like to deploy a similar system in house and incorporate it into my Postfix-Dovecot box.

I have come across two systems that may work: ciphermail and open-xchange. Both of these allow for email to be read by recipients by a secure web portal. However, it seems both of these require proprietary front-ends to use the email system. I need something that can be integrated with any modern email front-end a user wants to use (e.g., Outlook, Thunderbird, Android, iPhone, etc), without having to download proprietary apps. I would like users to use any program that can utilize standard encrypted IMAP/SMTP ports without having to download/install certificates or keys.

Is there something like this that can integrate into a Postfix-Dovecot with TLS box I already have?

See screenshots below of what I'm talking about.

Somebody else posted on this forum a while ago, but the thread was closed. Nobody responded. Hopefully, more people out there know of something that is hidden under all the Google and Bing search noise. [https://ubuntuforums.org/showthread.php?t=2345942](https://ubuntuforums.org/showthread.php?t=2345942)

Thanks!
Paul

[ATTACH=CONFIG]278419[/ATTACH][ATTACH=CONFIG]278420[/ATTACH][ATTACH=CONFIG]278421[/ATTACH]

---

### Post by TheFu on 2018-02-03
gpg is the only solution I know for this. Lots of moving parts depending on the clients used.  
I use Thunderbird + pineentry + enigmail + Zimbra on my stack.

---

### Post by mastablasta on 2018-02-05
you say you want something without using/installing certificates. but how would you encrypt without the key and lock, which is what the certificates basically are?

a thunderbird plughin will encrypt mail before sending it as well as decrypt it locally when receiving it.

---

