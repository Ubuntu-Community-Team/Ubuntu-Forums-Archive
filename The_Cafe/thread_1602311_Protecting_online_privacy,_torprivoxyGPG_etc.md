---
title: "Protecting online privacy, tor/privoxy/GPG etc"
date: 2010-10-21
forum: The Cafe
---

### Post by slackthumbz on 2010-10-21
So the UK Government is looking at reviving its interception modernisation program (Dear mods, please don't kill this thread as there is a valid tech angle here). The point of the program is to keep records of _all_ of our online activity. What web sites we visit, who we email, what we buy online etc. 

Personally I feel that no-one has the right to spy on me and I sure as hell aren't going to take this lying down. So I've installed tor and privoxy and configured all my applications to proxy through them. I've also set up my machine as a relay to further obfuscate the traffic running through it. Next I'm going to start GPG encrypting all my mail. 

My point is I'm interested in what other measures are available to us who want privacy online, all politics aside.

---

### Post by Oxwivi on 2010-10-21
I use the VPN solution, [proXPN]("http://proxpn.com/"). Though there's no official instruction for Ubuntu or Linux, I was able to connect using the nm-applet.

---

### Post by Spice Weasel on 2010-10-21
Tor and Scroogle are excellent for this.

---

### Post by slackthumbz on 2010-10-21
> **Spice Weasel said:**
> Tor and Scroogle are excellent for this.

I'd forgotten about scroogle, think I'll configure chromium and firefox to use it as their default search.

---

### Post by Cuddles McKitten on 2010-10-21
For what it's worth, there's this too: [https://secure.wikimedia.org/wikipedia/en/wiki/](https://secure.wikimedia.org/wikipedia/en/wiki/)

I'd also remind you (probably unnecessary) that rubber hose cryptanalysis is perfectly legal in the UK.

---

### Post by Velnias on 2010-10-21
Tor can protect against clueless neighbor, not goverment. What you need is FreeNet

[http://freenetproject.org/](http://freenetproject.org/)

---

### Post by slackthumbz on 2010-10-21
> **Velnias said:**
> Tor can protect against clueless neighbor, not goverment. What you need is FreeNet

[http://freenetproject.org/](http://freenetproject.org/)

Awesome, was not aware of this project. Thanks for the heads up :)

---

### Post by ljhffmn on 2010-10-31
Due to my installation being so new I'm not worried about having any private data on my machine and thus installed freenet. 

However, before I leave it on here too much longer can anyone verify that this project is ligit? The key wasn't valid...

---

### Post by cariboo on 2010-11-01
This really isn't the place for a thread about security, a better place would be the [security discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") sub-forum.

---

### Post by Robbyx on 2011-05-14
> **Oxwivi said:**
> I use the VPN solution, [proXPN]("http://proxpn.com/"). Though there's no official instruction for Ubuntu or Linux, I was able to connect using the nm-applet.

Would you mind spelling out what you did to use proxpn?

---

### Post by jerenept on 2011-05-14
Try TrueCrypt.
Also, GMail with [https://,](https://,) or GPG (supported in evolution email)

---

### Post by Robbyx on 2011-05-14
> **jerenept said:**
> Try TrueCrypt.
Also, GMail with [https://,](https://,) or GPG (supported in evolution email)

 I was referring to the comment about proxpn and wondered how he got it to work via linux?

---

### Post by jerenept on 2011-05-14
> **Robbyx said:**
> I was referring to the comment about proxpn and wondered how he got it to work via linux?

Oh. 'Network Manager applet> VPN Connections> Configure VPN' I assume.

---

### Post by Dustin2128 on 2011-05-14
I use duck duck go for searches- it's pretty awesome. Its search algorithms aren't bad and feature wise it's definitely a step up from google.

---

### Post by jerenept on 2011-05-14
> **Dustin2128 said:**
> I use duck duck go for searches- it's pretty awesome. Its search algorithms aren't bad and feature wise it's definitely a step up from google.

I second this.... you can even use it over SSL.

aother thing to consider using is NoScript, which I use with privoxy.... NS+privoxy=no crap.

---

### Post by rjbl on 2011-05-15
> **Cuddles McKitten said:**
> For what it's worth, there's this too: [https://secure.wikimedia.org/wikipedia/en/wiki/](https://secure.wikimedia.org/wikipedia/en/wiki/)

I'd also remind you (probably unnecessary) that rubber hose cryptanalysis is perfectly legal in the UK.

Yes'n'no.

Certainly the investigator authorised by a RIPA warrant can demand either the decryption key or, alternatively, a decrypted copy of any encrypted material on a suspects computer. **But** it is a sufficient defence that the suspect no longer possesses the key; the suspect only has to show, on the balance of probabilities, that he no longer has it to escape conviction. He does *not *have to prove his defence beyond reasonable doubt.

The snag with RIPA is that it is a criminal offence ever to reveal the very existence of a RIPA warrant, hence it is quite difficult prove admissible in Court. There have only be two cases where the right to demand decryption keys has been tried. Most forensic decryptions depend upon the suspect having written down his password somewhere findable; or using a guessable password; or by using an unreliable encryption application like PKzip(old versions) or Microsoft EFS

rjbl

---

