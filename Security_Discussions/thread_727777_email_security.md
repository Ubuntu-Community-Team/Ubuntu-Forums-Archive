---
title: "email security"
date: 2008-03-18
forum: Security Discussions
---

### Post by whitefort on 2008-03-18
Hi,

This isn't a specifically ubuntu (or Linux) question, but I only became aware of the issue because Linux has encouraged me to learn more about my computer.

For a few years, I've had my own domain name, and used it to host my website and to give family members email addresses that match the name of our house, (Which we all thought was very cool).

It's all hosted by Lycos.

Now that I'm learning a bit about security, I'm very concerned that all these emails are going out unencrypted (and am I right in thinking that this means even the passwords are going across the internet in unencrypted plaintext?)

I checked my Thunderbird settings, and found that there was neither SSL or TLS set up.  I contacted Lycos, and the only answer I got from them was that no, I couldn't use these with POP email.

So, my question:  Am I being over-cautious, or is this a Very Bad Thing? And if I can't use SSL or TLS, is there something else  I should know about?

I'm a newbie to all this, and would appreciate any advice/comments.

Thanks!

---

### Post by hyper_ch on 2008-03-18
question 1:
How "important" is your email account password to you? Does it really need to be secured?

question 2:
Even if you encrypt the connection between your computer and lycos mailserver the meails still get send unencrypted from mailserver to mailserver.. do you need to encrypt the whole email itself?

---

### Post by whitefort on 2008-03-18
I've got that awful sinking feeling that all I'm doing is reveal my ignorance about all this stuff...

To answer your question, I'm really not bothered by the idea that somebody, somewhere, might be reading our family emails.  If such a person was THAT seriously in need of a life, I'm happy to entertain them in any way I can!  And on the rare occasions when I send something more personal, I just encrypt the email body with enigmail and OpenPGP.

No, what worried me more is the idea that every time I send an email, the hypothetical snooper could get both my email address AND my password.  In which case they could presumably start sending emails as me - and I really would be bothered by that.

If I'm mistaken in this assumption (that my password could be grabbed and used if the email is sent without SSL or TLS), then I apologise for posting such a dumb question - but at least I'll have learned something!

Thanks!

---

### Post by hyper_ch on 2008-03-18
well, if you're worried about being hijacked with your email/password the you will need some secure transport... 

without ssl/tls it is sent in plaintext... however I think grabbing the password in a package nowadays is quite hard to do... I don't think it just won't happen by accident. Somebody would have to target you or lycos - and in that case I think you are facing a lot of other problems...

it's not a dumb question ;)

---

### Post by HermanAB on 2008-03-18
Yup, you seem to be wisening up nicely.  This is one reason why I run my own mail, chat, IM and bulletin board server and connect to it using HTTPS.  The only way to control the security of your system is to do it yourself and the solution is probably Citadel.

---

### Post by FakeOutdoorsman on 2008-03-18
You should try running Wireshark (as root) to see what it looks like to "sniff packets" (such a funny term).  It's available in the Ubuntu Universe repository.  Open Wireshark and then choose "List the available capture interfaces...".  Choose your interface (eth0 for me) to analyze by hitting the start button.  You will now be watching the packets and other network data.  You can click on each one and sometimes can make out unencrypted web site addresses, usernames, etc.  A good tool.  I used it recently to confirm that Tor was working.

---

### Post by whitefort on 2008-03-18
Hi,

Yeah, actually it was playing around with wireshark that started to get me worried.  I discovered that I could read the text of every unencrypted email (which I kinda expected), but also that the password was clearly visible (which I didn't!)

I also used wireshark to demonstrate to some family and friends that running an unsecured wireless network was a really bad idea!

---

