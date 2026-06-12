---
title: "no password required for encrypted emails..."
date: 2011-04-25
forum: Security
---

### Post by onlycuteusernames on 2011-04-25
I'm running Thunderbird with Enigmail, and I have this very annoying problem. When I open an encrypted email for the first time, it asks me for my key password. It then remembers my password. This is fine for a few minutes, since I don't want to enter the password every time if I look at seven emails in five minutes. However, I WOULD like it to EVENTUALLY forget. At the moment, it doesn't even forget if I shut off Thunderbird. I have to restart my computer, in fact.

The preferences for Enigmail don't help. I've configured it to remember the password for 0 minutes, for example. I don't know how to edit the preferences for gpg-agent or anything else like that.

All help is appreciated, but please bear in my mind that I'm a huge newb!

---

### Post by rookcifer on 2011-04-25
Post the output of your:

```
~/.gnupg/gpg.conf 
```

---

### Post by dacoolio on 2011-04-25
That sounds like a configuration issue with GnuPG. Like rookcifer said, you should post what's in your gpg configuration file. Since you said you're a "huge newb", here are the steps to get the output:

First, open the terminal by going to Applications>Accessories>Terminal

In the terminal, type:

```
cat ~/.gnupg/gpg.conf
```

Then just post what the output is.

---

