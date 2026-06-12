---
title: "Blue frog users: uninstall ASAP"
date: 2006-05-18
forum: Server Platforms
---

### Post by nocturn on 2006-05-18
[http://castlecops.com/modules.php?name=Forums&file=viewtopic&p=768501](http://castlecops.com/modules.php?name=Forums&file=viewtopic&p=768501)

With Blue security gone down, there is a chance that this client (maybe even the Linux port) may be turned malicious.

So, users are recommended to uninstall immediately.

---

### Post by louis_nichols on 2006-05-18
Quite regretable.

I wasn't using Blue Frog, but was considering it. It's quite a shame that, as the prolexic's site said, criminal spammers won.

---

### Post by nocturn on 2006-05-19
It may be a while, but there seem plans for an OSS version of it that is much more resilient against attacks.

It's supposed to use p2p tech instead of a central server.

---

### Post by wblancqu on 2006-05-20
That would be great news. I was wondering why they didn't do that in the first place. It's much harder for the spammers to attack a P2P system. It'll be many against many, and not many against one. They've won a battle, let's hope they don't win the war.

---

### Post by RavenOfOdin on 2006-06-07
Blue frog == Azureus?

:confused:

If so, I'm sure the RIAA is behind this somehow.

---

### Post by escape on 2006-06-15
Blue frog is not Azureus. Blue frog was anti-spam software created by an Israeli company, Blue Security. The software would log domains of spam email you got, send it to a central server, and if enough people sent in the domain, Blue Security would send a cease and desist letter. Failing that, Blue Security would orchestrate a massive DDOS on the domain via Blue Frog on the computer of each person who received spam from that domain. 

Needless to say, this made spammers extremely angry. Blue Security got DDOS'ed, and there is talk that if someone were to control the Blue Security IP, they could use the main server to direct every computer with Blue Frog to attack something, which would not be good.

---

### Post by RavenOfOdin on 2006-06-16
[QUOTE=escape]Blue frog is not Azureus. Blue frog was anti-spam software created by an Israeli company, Blue Security. The software would log domains of spam email you got, send it to a central server, and if enough people sent in the domain, Blue Security would send a cease and desist letter. Failing that, Blue Security would orchestrate a massive DDOS on the domain via Blue Frog on the computer of each person who received spam from that domain. 

Needless to say, this made spammers extremely angry. Blue Security got DDOS'ed, and there is talk that if someone were to control the Blue Security IP, they could use the main server to direct every computer with Blue Frog to attack something, which would not be good.[/QUOTE]

Oh. . .the "blue frog" and "p2p" thing kinda threw me there. Sorry. :p

---

### Post by Big_Rog on 2006-10-12
> **escape said:**
> Needless to say, this made spammers extremely angry. Blue Security got DDOS'ed, and there is talk that if someone were to control the Blue Security IP, they could use the main server to direct every computer with Blue Frog to attack something, which would not be good.

I thought that was the whole point of most trojans/worms: get access to a huge number of terminals, then aim them all at the location of the originator's choosing, and laugh, because it's "not the originator" doing the attack itself, and they claim innocence/immunity.  So what's the difference here?  If a police man or bounty hunter decided to take their weapons/car/dog/bomb squad etc. and run amok, it "would not be good" at all.    Same thing as a criminal taking control of said assets.  What we rely on in today's world to prevent that, is the integrity of those in control of such powers, and the ability of our society to reprimand/remove those who lack said integrity.

---

### Post by Big_Rog on 2006-10-12
...

---

### Post by GoBieN on 2006-12-13
> **Big_Rog said:**
> I thought that was the whole point of most trojans/worms: get access to a huge number of terminals, then aim them all at the location of the originator's choosing, and laugh, because it's "not the originator" doing the attack itself, and they claim innocence/immunity.  So what's the difference here?  If a police man or bounty hunter decided to take their weapons/car/dog/bomb squad etc. and run amok, it "would not be good" at all.    Same thing as a criminal taking control of said assets.  What we rely on in today's world to prevent that, is the integrity of those in control of such powers, and the ability of our society to reprimand/remove those who lack said integrity.

Because the explanation is not correct. Blue frog would indeed collect mail from spammers and then would bounce every spam mail back. So if the spammer send out 1000 spam mails to blue frog users around the world, he would get 1000 bounce mails back saying the address does not want to receive spam e-mail. This kind of resulted in the spammer being SPAMT himself thus not being able to use his mailbox anymore because of the 1000 mails.

Was a great plan, but the spammers were angry and that one russian guy DDOS's Blue Security into Oblivian. That just proofs it was working since the spammers got so angry.

---

### Post by Oceanwatcher on 2007-03-17
Actually, it proves nothing. Just that they got DDOS'ed.

No spam that I ever got had the right domain attached to it. And it became even more clear to me the day a spammer decided to use one of my domains as the sender address for several spam campaigns. I started getting replies from different spamfilters all over the world saying they did not accept spam. What an idiotic thing to do! If you send out a reply to a spam mail it will never reach the spammer. It will go to an innocent person that have no idea what this is about.

And yes, the mailserver I use has been secure from day one and is beeing kept up to date. It was not the server used to send the spam. The spammer just picked my domain and autogenerated the names.

I really believe in sending all spam directly to a blackhole. Never reply to it. Eventually, there has to be created systems that eliminate big parts of the spam. But until that happens, just delete it!

---

### Post by Brazen on 2007-03-23
Oceanwatcher, you are mistaken.  The BlueFrog system did not just reply to what was listed as the sender of the email.  It kept a database of who the actually spammers were and sent the emails to them.

---

### Post by Polygon on 2007-04-13
any news on the oss / more secure port of this program (well not port, similiar program)?

---

### Post by Luc1fer on 2007-06-10
Does anyone have the original blue frog code?

---

### Post by xurizaemon on 2008-01-07
Akismet is a lot similar, but works for blog posts. Large mail providers probably handle spam similarly too.

The beauty of something like Akismet is that it allows you to turn the "mass" aspect of spam against itself; the disadvantage is that someone else is reading all your posts.

For email, this probably wouldn't be acceptable. But a similar model might just work (somehow, dunno how ... yet).

---

