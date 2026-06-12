---
title: "Securing the privacy of email relays with different providers (protonmail and gmail)"
date: 2023-08-10
forum: Security
---

### Post by Drone4four on 2023-08-10
I’m trying to secure the privacy of an email address and email relay network. I’m using protonmail as my service provider and I have a custom domain. It’s purpose is to be the point of contact for the one and only site admin for a rudimentary Django blog CMS for some boring academic philosophy content. The project is in the testing stage currently. Only once the project goes into production will the custom email address be published publicly. I am anticipating very low traffic. I don’t plan on logging into my protonmail account to check for messages regularly. So if I set up a relay, so that all protonmail messages are forwarded to a different email (say a less secure common gmail account that I do check several times a day), how easy would it be for a bad actor to be able to track the relay from a protonmail-based account to a regular gmail account? 

I don’t have adversaries and I can’t imagine ever being the target of an attack. So there isn’t much risk. But hypothetically speaking, for a bad actor as highly sophisticated as, say, an advanced professional pen-tester, how realistic would it be for them to identify the destination gmail address based on emails coming from the originating protonmail account?

---

### Post by TheFu on 2023-08-11
SMTP is like a postcard, by design.  The email headers are added, none are removed, so the sending machine and all intermediate SMTP servers tack on their part of the SMTP route between the source and the destination.  There's no hiding that.

If you care about privacy, don't use gmail and be very careful about which systems email transfers through in the world AND be certain that you are using SMTPS, not just SMTP.  I don't think SMTPS is mandated, so if either side of the connection refuses, then it won't be send in a TLS encrypted way.

Look at the headers in some test emails. Full headers.

BTW, I think you aren't running Linux on a PS/2 computer.

---

### Post by DuckHook on 2023-08-12
> **Drone4four said:**
> I don’t have adversaries and I can’t imagine ever being the target of an attack.
No one ever imagines being a target and therein lies the problem. The bad guys are indiscriminate and go after everyone they can. Your value to them is far more than you think and, in any case, not a material consideration to their twisted minds.

At an absolute minimum, the malicious sort will value your computing resources for a bot farm, or a crypto farm, or a malware relay. You have inherent worth to them if only in this way. But these days, the far larger and more insidious problem is the data harvesting that so&#8209;called "legitimate" corporations use to manipulate and exploit you. There's a reason that Microsoft, Google, Facebook and Apple (to say nothing of the dozens of only slightly smaller data slurpers) are multi&#8209;trillion dollar companies. They get your data for free, yet its market worth is what allows them to be godzillas.

> …hypothetically speaking, for a bad actor as highly sophisticated as, say, an advanced professional pen-tester, how realistic would it be for them to identify the destination gmail address based on emails coming from the originating protonmail account?
It's not my intent to offend you, but the way you've phrased the above question tells me that you are focusing on the lesser of the two evils. G-mail is actually somewhat secure against outside criminals. Google's encryption is pretty robust. This does not extend to your headers and routing history as TheFu points out, but the actual contents of your e&#8209;mail are protected to some extent. The real problem is Google itself. Who you send to, from where, and how often are significant pieces of metadata to them. They can construct a frighteningly good profile of you from such metadata alone, and they do. Without hesitation. It's how Google defines itself.

I raise this topic only because you use Protonmail. People who use Protonmail are primarily interested in privacy. Guarding against crims is a distant secondary concern. I use Protonmail too, but it's reserved for really sensitive stuff like medical records, financial docs, etc. If you are using Protonmail, then the best way to send stuff is to encrypt it with self&#8209;destruct.
> I’m trying to secure the privacy of an email address and email relay network.
If you are planning to forward Protonmail to a regular G-mail, then IMO you're defeating the very point and purpose of using Protonmail. Protonmail is about preserving privacy. G-mail is about surrendering privacy for all of the "conveniences" that Google offers. They are diametrically opposite and conflicting goals. If you are intent on creating an email relay network, then save yourself the trouble and complexity and just use G-mail. You may even risk compromising Protonmail with your strategy.

---

