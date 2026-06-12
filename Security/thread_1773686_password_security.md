---
title: "password security"
date: 2011-06-02
forum: Security
---

### Post by donsy on 2011-06-02
I try to maintain strong passwords and change them (somewhat) frequently. However, two entities I deal with, one a large financial institution and the other a government agency, will not allow a password that's been previously used a certain number of times. My question is this, for them to know a password has been previously used wouldn't they have to store raw passwords instead of, or in addition to, their hash values? And if so, isn't this poor security practice? What if they're hacked?

---

### Post by Lars Noodén on 2011-06-02
It's enough to store the hashes.  If the hash of a new password matches one of the stored hashes, then you know that the password is being re-used.

---

### Post by donsy on 2011-06-02
> **Lars Noodén said:**
> It's enough to store the hashes.  If the hash of a new password matches one of the stored hashes, then you know that the password is being re-used.

Thanks, I feel a little more at ease now. As a related question, one of the websites specifies rules for a password as at least one letter, one digit, and one of the special characters @!#$%^&*() and no mention of upper-case. I'm wondering out loud why such a restriction on the special characters and not just allow passwords to contain any of the 94 printable ASCII characters.

---

### Post by Lars Noodén on 2011-06-02
They probably have that to try to give the illusion of more [entropy](http://gcn.com/Articles/2005/08/10/How-strong-is-your-password-NIST-has-some-formulas.aspx)  Passwords are a science, not an art. ;)

---

### Post by donsy on 2011-06-02
> **Lars Noodén said:**
> They probably have that to try to give the illusion of more [entropy]("http://gcn.com/Articles/2005/08/10/How-strong-is-your-password-NIST-has-some-formulas.aspx")  Passwords are a science, not an art. ;)

I see your point Lars, but the point I'm making is that there's more entropy per character if chosen from a set of 94 possibilities, as opposed to restricting it to just 72.

---

### Post by Lars Noodén on 2011-06-02
You're correct, 94 > 72.  Their guidelines may be a little off.

---

### Post by bodhi.zazen on 2011-06-02
> **donsy said:**
> Thanks, I feel a little more at ease now. As a related question, one of the websites specifies rules for a password as at least one letter, one digit, and one of the special characters @!#$%^&*() and no mention of upper-case. I'm wondering out loud why such a restriction on the special characters and not just allow passwords to contain any of the 94 printable ASCII characters.

Because some of those special characters can be use to try to crack web servers (php or other other server side includes).

---

### Post by HermanAB on 2011-06-03
These things can be configured in PAM.  The default Ubuntu PAM settings are rather lax and will allow short passwords and re-use.  

The result is that many new Ubuntu users get their machines compromised as soon as they start to experiment with servers such as FTP or VNC and these forums are full of tales of woe.  To my mind, this is a really irresponsible oversight by the Ubuntu developers.

---

### Post by Lars Noodén on 2011-06-03
> **HermanAB said:**
> ...compromised as soon as they start to experiment with servers such as FTP ...

The source of the compromise there is from [FTP](http://en.wikibooks.org/wiki/OpenSSH/SSH_Protocols#Background_of_FTP) itself.  The machines could be kept more safely by using SFTP instead.  We need a re-write of a lot of documentation to steer new users to SFTP and away from FTP.

---

### Post by HermanAB on 2011-06-03
By default, Ubuntu allows 6 character passwords.  That is not good...

---

### Post by Lars Noodén on 2011-06-03
> **HermanAB said:**
> By default, Ubuntu allows 6 character passwords.  That is not good...

By default, Ubuntu has no external services activated either, so in some ways it doesn't matter how long or short the password is.  Those that will add external services will probably also know enough to improve the passwords.

---

### Post by tapi0n on 2011-06-03
> **bodhi.zazen said:**
> Because some of those special characters can be use to try to crack web servers (php or other other server side includes).

If they were to succeed in cracking it with use of special characters. Isn't that a really big flaw of the developer? 

For example, to prevent (just an example) injection in php it's enough to add a method which changes special characters to clear text right? And such method only takes like 3 lines to do so.

Or did I not understand what you ment?

---

### Post by spynappels on 2011-06-03
> **tapi0n said:**
> If they were to succeed in cracking it with use of special characters. Isn't that a really big flaw of the developer? 

For example, to prevent (just an example) injection in php it's enough to add a method which changes special characters to clear text right? And such method only takes like 3 lines to do so.

Or did I not understand what you ment?

You're right, but not all coders are good coders, so bad code does make it into production systems.

---

### Post by tapi0n on 2011-06-03
> **spynappels said:**
> You're right, but not all coders are good coders, so bad code does make it into production systems.

Well ye, but I think that when coding for a governement/financial institution you'de be able to escape some characters?

I'm actually interested as to what bodhi.zazen ment. Because the way I understand it is that even when escaping special characters, you're still able to get around it when using more then one special char?

---

### Post by bodhi.zazen on 2011-06-03
> **tapi0n said:**
> If they were to succeed in cracking it with use of special characters. Isn't that a really big flaw of the developer? 

Yes, but as there is not such ting as perfect code, it is far easier and far more secure to disable the special characters. In fact it is "standard practice" as you can see.

---

