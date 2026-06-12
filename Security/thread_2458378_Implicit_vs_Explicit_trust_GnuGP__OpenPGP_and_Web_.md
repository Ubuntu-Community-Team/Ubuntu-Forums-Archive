---
title: "Implicit vs Explicit trust GnuGP / OpenPGP and Web Of Trust (WoT)"
date: 2021-02-23
forum: Security
---

### Post by Drenriza on 2021-02-23
Hi all!

I have been trying to understand GnuPG (implementation of [OpenPGP)]("https://tools.ietf.org/html/rfc4880") in regards to implicit and explicit trust along with the WoT concept.
And depending on what you read and where you read it, there are terms used or not used or contradict eachother.[URL="https://tools.ietf.org/html/rfc4880"]

[/URL]_**Implicit trust**_
Something that is implicit is something that is "unsaid" or "goes without saying".

Question: In GnuPG and OpenPGP what is implicit trust if it even exists?
Question: Can you sign a key with a defined level of implicit trust?
Question: Is the signing process itself of a public key _the implicit trust_ even though the act than is explicit?
Question: Can i see keys in my keyring implicit trust value?

When you (in my test 20.04) import someone's key their trust level is [Unknown] (trust level 1?) and when you sign their key they become [Fully] (trust level 4?) trusted.
Is this the implicit trust of GnuPG? Unknown and Fully.

The questions above reflect my googling of trying to answer them myself (what is implicit trust in GnuPG / PGP), but based on where you read what you get a different answer or
different explanation.

_**Explicit trust**_
Something that is explicit is something that is "said" or "is made well aware of"

Explicit trust as far as i understand is something you give when
You edit someone's key and explicitly give them a different trust level from 1 to 4, and 5 is something you only should give yourself.

[U][B]The Web Of Trust (WoT)
[/B][/U]Are there any good resources that can explain how the WoT works in a practical sense?
I understand that based on fully and marginally trusted keys you can build trust to other keys you dont yet know.

But for example if i know 3 people that i all have marginally trust in knows a 4'th key, than i accordingly to WoT see the 4'th key as valid, but what trust is it given?

Again this seems to be explained overly complicated on the web, compare to what it probably is because alot of information on the web seems to contradict eachother in
their explanation.

There is an explanation [here]("https://www.gnupg.org/gph/en/manual/x334.html#WOT-EXAMPLES") with Alice, Blake and Dharma.
But the text (from example two) compared to the figure dont make sense when you read the two conditions that needs to be meet
before a key can considered valid...

_**Other question**_
When you create a GnuPG keypair, and you import someone's elses public key and dont sign it
can you than send encrypted data / messages to eachother? Or what is the minimum you need to do for example, import, sign and minimum trust of X, before you can send or receive encrypted data / messages??

Thanks in advance
Best regards

---

### Post by kevdog on 2021-02-23
Yea you can send GPG mail without signing the key although this is probably based on the requirements of the client and not the protocol.

---

### Post by Drenriza on 2021-03-01
> **kevdog said:**
> Yea you can send GPG mail without signing the key although this is probably based on the requirements of the client and not the protocol.

Thanks for the reply kevdog!

Any and all information is welcome

Best regards!

---

