---
title: "FireGPG Replacement"
date: 2012-05-24
forum: Security
---

### Post by yeehi on 2012-05-24
FireGPG was unfortunately discontinued.
Is there a replacement plugin for Firefox?

What about an equivalent plugin for Chrome? Is there something out there?

Thank you!

---

### Post by Ms. Daisy on 2012-05-24
Sounds like that may not have been a bad thing

[https://tails.boum.org/doc/encryption_and_privacy/FireGPG_susceptible_to_devastating_attacks/index.en.html](https://tails.boum.org/doc/encryption_and_privacy/FireGPG_susceptible_to_devastating_attacks/index.en.html)

I don't use the add-on, but a google search found these alternatives:
[http://support.mozilla.org/en-US/questions/831463](http://support.mozilla.org/en-US/questions/831463)

---

### Post by ottosykora on 2012-05-25
> **yeehi said:**
> FireGPG was unfortunately discontinued.
Is there a replacement plugin for Firefox?

What about an equivalent plugin for Chrome? Is there something out there?

Thank you!

this whole encryption in those webmail things was always a big problem and rather insecure anyway, from many points of view, no point in creating other program which is just an other security problem. Doubt that something liek that will come again.

Unfortunately the native encryption of text in the gedit is gone with gnome2 and we have no idea if it will come back or not.
Encryption in nautilus does not work really any more, decryption somehow, but it is too buggy.

For the time being I use portable pgp, which is a java application and work nice with current versions of ubuntu.

I created a launcher and have an icon also on the panel.
You can do all basic tasks with it, encrypt/decrypt text and files, basic key management too.

[http://ppgp.sourceforge.net/](http://ppgp.sourceforge.net/)

---

### Post by kevdog on 2012-05-25
I use WebPG for a chrome extension. Definitely not as good as the old firegpg, but as of right now, its about the only thing out there I can find that will work with a browser client.

---

### Post by jon zendatta on 2012-05-25
I'm a Gmail client and use Gedit & Terminal.

As an alternate method you can read the message from the terminal. Copy and paste the message from "-----BEGIN PGP MESSAGE-----" till "-----END PGP MESSAGE-----" including those two lines in a text file. From the terminal run "gpg -d opgpm.txt" excluding the quotes where "opgpm" is the name you gave the text file. You will be asked to enter your passphrase and you get the decrypted message.:KS

---

