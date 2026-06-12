---
title: "A (Thorough) Guide To GnuPG"
date: 2012-05-08
forum: Security
---

### Post by rookcifer on 2012-05-08
**[CENTER][SIZE="3"]Introduction[/SIZE][/CENTER]**

I see quite a few posts on this forum where people inquire about things like package signing, verifying packages, and making GPG keys for their own personal use. There is a lot of confusion as to how the whole system works and I would like to use this post to clarify that a bit. This post will provide all the information that a layman will need to know about cryptographic software (at least as it applies to tools like GnuPG) and how to effectively use it on his Linux box. I will cover topics like creating a GnuPG key-pair and how to use the key-pair for secure e-mail. I will cover package signing and verification and will touch on SSL/TLS briefly. I will use plain English and give walkthroughs.  There are many other good introductory references out there on the Internet and I will provide links within this post as necessary.  This post is focused on teaching the reader about how to *use* public-key cryptography effectively on Linux.

This post will not contain any number theory, discrete mathematics or talk about factoring large primes or solving the discrete logarithm problem. I wont mention Elliptic Curves or the finer points of any mathematics behind the whole system (except in passing). You will just have to trust that those things are well understood by mathematicians and that they "just work." In short, this post is aimed at Joe Average computer user and is not meant to be some self-study on cryptography. I will provide a section at the end for the real geeks who want to dive into the math and I will mention a few important books that any aspiring crypto-developer might want to read before he fails (and you *will fail* if you don't have the background, no matter how good of a programmer you are). 

This posts may end up being a series of posts, but for now this post will be outlined as follows:

[LIST]
[*]A history of crypto in general
[*]The breakthrough of public-key crypto (important to read)
[*]Some problems with public-key crypto and how they are solved (really important to read)
[*]Some definitions for the reader (for clarification)
[/LIST]

If you are someone who is familiar with cryptography (specifically public-key cryptography), then you can skip past the history.  *If you do not have a clue about any of this, then you should take a few minutes and read the history.*  So with that out of the way, let me get started.  

[SIZE="3"][CENTER]
**What is cryptography?**[/CENTER][/SIZE]

[Cryptography]("https://en.wikipedia.org/wiki/Cryptography") is the art (and science) of making and breaking secret codes. It has been around for thousands of years and has seen many developments over the centuries.  The ancient Egyptians had secret writing that many consider cryptography today.  Julius Caesar used it to send messages to his generals on the battlefield.  Thomas Jefferson [invented]("https://en.wikipedia.org/wiki/Jefferson_disk") his own brilliant system based on a wheel that randomly transformed the plaintext into the ciphertext (this basic idea was even used during WWII with the rotor machines).  Jefferson's design was similar to some ancient Greek designs.  Many other cultures throughout history have had some hand in cryptography.  However, most of those systems are what are known as [transposition]("https://en.wikipedia.org/wiki/Transposition_cipher") or [substitution]("https://en.wikipedia.org/wiki/Substitution_cipher") ciphers and are easily broken today due to the fact that modern cryptographers have many techniques to easily defeat them.  The modern science of cryptography uses the hard logic of mathematics in analyzing and breaking the systems -- something the ancients didn't really bother with.  However, some of their systems were ingenious and laid the basic groundwork for us today.

[CENTER]**[SIZE="1"]A Short History[/SIZE]**[/CENTER]

Entire volumes could be written on the history of cryptography, so I will refrain from going too far into detail.  But I feel it is worthy of devoting a few paragraphs to it.  What we are concerned with here is modern cryptography which began (roughly) at the end of the 19th century and really began picking up in the 20th century due to the two world wars (war has a way of quickly advancing technology).  The field really started picking up in complexity and design during World War II as communications systems (radio, telephones, etc.) became more advanced and allowed easier communications.  An example of a WWII era crypto-system is the infamous German [Enigma machine]("https://en.wikipedia.org/wiki/Enigma_machine") which was eventually cracked (in secret) by the allies.  Many historians think this breakthrough by the allies (actually the Polish did it first, then the Brits did it later after the Germans changed the machines) shortened the war by several years.  

As you can see it was at this point that cryptography began being dominated (even more than it was already) by the military.  Militaries of the world had an intense interest in the field, for obvious reasons, and most of the work from WWII onward was highly classified by most any government that had an interest in it.  In the USA, for instance, most of the work was just as highly classified as the nuclear program, and the field was treated with similar amounts of secrecy in Britain and the Soviet Union.

Shortly after WWII, the [NSA]("https://en.wikipedia.org/wiki/Nsa") was formed to explicitly take over (and specialize) in the field of signals intelligence (SIGINT) for the United States military.  Prior to that time the responsibility was scattered amongst the various military services (which wasn't very efficient).  The NSA sought to consolidate the responsibility into one agency that specialized in the field and dispensed what it learned to the appropriate leaders.  NSA was probably the most classified of all of the intelligence agencies (even more so than the CIA); it's mere existence was unknown to the public for years.  Britain has [the GCHQ]("https://en.wikipedia.org/wiki/GCHQ") (Government Communications Headquarters) which has essentially the same function and the same amount of secrecy behind it.  

So as I touched on above, the field of cryptography at this point was solely the expertise of the NSA and other intelligence agencies around the world.  The NSA snatched up as many mathematicians as it could to carry out research.  Some of these people were well known professors at various universities who secretly published work for NSA on the side.  More often than not, most of the work was done by people (who's names we still don't know) that were directly on the payroll for NSA.  

In any case, NSA had almost a complete monopoly on the research.  Laws were enacted to stop publication of what little research was out in the open from being exported outside of the USA (cryptography was considered the same as a weapon or munition and the law carried the same penalty).  There were a number of cases where patents were denied to people inventing crypto-machines and where the government snatched up open research and classified it.  One must remember that this transformation happened during the Cold War, so information was perhaps the single most important weapon in learning what exactly the Soviets were up to regarding nuclear weapons.  It is also why cryptography was such a well guarded secret.  If the methods of SIGINT and COMSEC the NSA was using fell into the Soviet's hands, it could mean disaster.  The NSA didn't want the Soviets to know what codes it could and could not break and the Soviets had the same concerns.  Naturally, this meant NSA didn't want academics in the open world doing research that could leak to the Soviets which would make NSA's job of gathering intelligence more difficult.

The field of cryptography remained almost exclusively the sole domain of the NSA until roughly the early 70's when the computer age began taking off in the commercial, non-classified world.  It was at this point that people realized that securing data on machines was pretty important, especially considering the new phenomenon of electronic banking transactions.  So, the National Bureau of Standards in the USA (a non-classified government standards and research body) called out for help from industry.  They wanted the open academic world to submit to them a group of encryption algorithms as part of a "contest."  Each algorithm would be studied by the NBS, and the other academics involved, until a winner would be chosen to become the new standard.  

Several ciphers were submitted, but most of them were flawed and were immediately disqualified.  However, one well designed submission did appear and that was a cipher named ["Lucifer"]("https://en.wikipedia.org/wiki/Lucifer_%28cipher%29") submitted by IBM.  NSA immediately got involved and began tampering with the algorithm, making changes to the S-boxes, and shortened the key length.  Many academics involved were highly suspicious of what exactly NSA's motives were.  Eventually, there was so much uproar around the whole NSA issue that hearings were held by the U.S. Congress (they concluded that NSA was only trying to help).  After it was all said and done, the cipher was finalized and was dubbed "DES" or Data Encryption Standard.  It would be used all the way up until the late 1990's when it became obvious that its 56 bit key length was far too short for general use due to the steady increase of the computational power of modern computers.  (Incidentally, 20 years after DES was standardized, the academic community discovered via cryptanalysis that the NSA actually had strengthened the DES with their changes.  NSA couldn't explain the changes at the time due to national security concerns.  IBM came forward later and said they knew why NSA was making the changes but were sworn to secrecy).  DES to this day has not been successfully broken outside of "brute force."

DES is what we call a symmetric cipher which means that the key to encrypt and decrypt is the same.  As a result, this means that it is virtually worthless for sending and receiving messages unless one has already exchanged the key with one's contact before hand.  This presents problems when one's contact is on the other side of the country and where secure key exchange might not be possible. This is exactly the problem that had confounded cryptographers for many years -- how to make key exchange feasible without having to do it through an outside channel.  

This was exactly why no one used [one-time-pads]("https://en.wikipedia.org/wiki/One-time_pad") for anything that required any significant amount of data to be transferred.  The one-time-pad (when properly implemented) has been proven mathematically to be unbreakable, which seems great on the face of it.  One might think that the science of cryptography should just end there. But in reality, the OTP is next to useless in the real world because the key has to be the same length as the message.  So, if you want to send gigabytes of data to a contact, the contact must have gigabytes of key.  Not only that, but you must find a way to securely transmit that gigabyte of key to him securely through an outside channel.  With large amounts of data, such large keys simply become unwieldy and have a great chance of being stolen or compromised. This is why the OTP is rarely used today outside of extremely covert spy operations where short instructional messages are acceptable.  If someone tries to tell you to encrypt your hard drive with a one-time-pad, you can just laugh at him.  For each hard drive you encrypt, you need another hard drive just to store the key.  This obviously makes the OTP worthless for any real work.

**[CENTER][SIZE="2"]The Breakthrough of Public Key Cryptography[/SIZE][/CENTER]**

Enter a man named [Whitfield Diffie.]("https://en.wikipedia.org/wiki/Whitfield_Diffie")  He discovered a way, during the 1970's, to solve the problem of exchanging keys.  He wasn't the very first to propose the idea (a man named Ralph Merkle had proposed it in a paper in graduate school but was told by his professor it was a dumb idea.  Also cryptographers at Britain's GCHQ had already discovered it but had classified it as TOP SECRET at the time). At any rate, Diffie discovered a way that two parties could securely exchange keys even when the communication channel was being monitored.  Diffie got in touch with a colleague named Martin Hellman who helped him refine the idea and eventually this method became what we call [Diffie-Hellman]("https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange") today (Merkle should also be recognized).  It was so revolutionary that some people consider it the greatest breakthrough in cryptography since the renaissance. For an excellent lecture by Whitfield Diffie regarding his discovery and how it all came about, see [this link from YouTube.]("https://www.youtube.com/watch?v=1BJuuUxCaaY")

A few years later, other researchers at MIT and elsewhere, picked up on the idea and took it a bit further.  These people invented what we call ["RSA"]("https://en.wikipedia.org/wiki/RSA_%28algorithm%29") today (Rivest, Shamir, Adleman).  Essentially all of these guys discovered that one could have a public key and a private key that were mathematically related in such a way as to make it impossible to derive one from the other unless the attacker knew what both were (the attacker would not be able to derive the private key by merely seeing the public key).  RSA used the "hardness" of factoring large composites into primes whereas Diffie-Hellman was primarily based on the discrete logarithm problem.  The security of both systems relies on these problems being computationally infeasible to solve in any reasonable amount of time.  Most e-mail encryption systems today, including GnuPG, use the RSA method as it uses static keys that can be used for as long as one chooses.  Diffie-Hellman's design was more based on ephemeral session keys (and is better suited in SSL connections where it doesn't matter if the key changes often).  The [ElGamal]("https://en.wikipedia.org/wiki/ElGamal_encryption") method was another public-key system that was invented in the 1980's that is very similar to Diffie-Hellman and, like RSA, allows one to create a static public/private key-pair that can be used repeatedly.  There are a number of other public-key schemes but most of them haven't been as well studied as the aforementioned three.  GnuPG uses RSA and ElGamal (DSA can be used for signatures only).

Not only do these schemes allow for secure key exchange over an insecure channel, but they also allow for authentication.  This is just as important as the encryption itself.  Without being able to authenticate who one is talking to, there is not much point in continuing the conversation.  One does this with the public/private keys.  Here's how it works:  Two people exchange public keys, but keep their private keys secret (very important).  Let's call these two people Alice and Bob (as is the convention).  When Alice gets ready to send Bob a message, she takes Bob's public key and then encrypts the message with that key.  When Bob receives it, he decrypts it with his private key.  So far so good.  But how does Bob know the message really came from Alice?  Well, before she sends the message to Bob, she signs the message with her private key.  Since Bob has her public key, he is able to check the signature made by her private key against her public key.  This allows him to both decrypt the message itself and prove it came from Alice.  As you can see, the work of Merkle, Diffie, Hellman and others solved this very difficult problem of secure key exchange and authentication for us.

[CENTER]**The Problem of Trust**[/CENTER]

So I have explained how the problem of secure key exchange over insecure channels can be achieved.  I have also explained how one can authenticate that the message actually did come from the person one thinks it did.  But we're not done -- there is still the problem of trust.  Trust is primarily a human issue and not a technological one.  Although Diffie and Hellman and others helped us tremendously with the technology to achieve this, there are still human issues involved.  

To illustrate this, let me give an example.  One question that comes up a lot on the forums is packing signing.  Package signing is when a developer uses his private key to sign a package before he distributes it.  People with his public key can verify the package's authenticity by checking the signature.  This is very nice in theory, but it ultimately relies on trust.  Why?  Because anyone can generate a key and attach any name they want to the key.  For instance, I can generate a key and put the name "Linus Torvalds" on it.  I can then send the key to some random Linux developer hoping to trick him into believing I am actually Linus himself.  If he falls for it, then I can send him a malicious piece of code hoping he inserts it into the Linux kernel.  He can even check the signature on the package and see that it came from "Linus Torvalds" when in fact it came from me, the impostor.  In essence, he was socially engineered.  Of course, I seriously doubt any kernel developer would fall for that, but a lot of less savvy (and paranoid) people in the world certainly will (and do every day).

There is no technological way to solve this problem.  The public-key methods I have outlined above all rely on the assumption that the human users have verified the owners of the keys in some outside channel. It becomes obvious then that the solution is to verify identities in some physical way.  That is, meet the person and check his ID.  If you know him already, then call him on the phone and have him read the key fingerprint to you.  But wouldn't that sort of make the whole public-key idea useless, you ask?  If we have to do some sort of offline verification anyway, then what makes it better than the old fashioned symmetric ciphers?  Isn't it just a matter of "kicking the can down the road," as they say? Well, in case you haven't figured it out, let me give you a few reasons why public-keys are better than using symmetric keys alone:

[LIST]
[*]You can create *one* public key and have everyone use that one key to send you encrypted messages.  It is akin to having a mailbox that is there for the world to see -- anyone can drop letters in it, but only you can retrieve them.

[*]Building on the above, if you were to use symmetric keys for every contact, then the number of keys you need grows based on the number of contacts you have. If you have 20 regular contacts, you need to manage 20 separate secret keys.  This is obviously impratical.  Public-key crypto solves this problem by allowing every person to only have to manage one key no matter how many contacts.

[*]Public-keys allow you to secure your key by something you have (the private-key) and something you know (the password).  If you were to use symmetric keys only, you would have to remember the symmetric key itself, which is just a string of random numbers.  Good luck memorizing a 128 bit random value, especially when you have 20 of them to memorize!  (Sure you could save them all to an encrypted file, but it would still be a major hassle to keep up with what key goes to what contact, etc.)[/list]

Hopefully it is now clear why public-keys are better than symmetric keys for communicating with many contacts where secure key exchange is not possible beforehand.  But, as I said above, there is still the problem of trust.  In an attempt to help alleviate this issue, PGP/GPG has proposed what is known as the "Web of Trust," which I will now describe.

[CENTER]**The Web Of Trust**[/CENTER]

The Web of Trust is a method of allowing a user to verify a key identity without having to go out and meet this contact in person.  Basically it works like this:  Let's say you have a friend named Alice who you want to communicate with privately via e-mail.  You and she both exchange public keys in person and both have verified 100% that the keys are legit.  You would then sign Alice's key with your signature and she would sign yours.  Now anyone who has access to your key would notice that Alice trusts that your key really belongs to you.  Likewise, Alice's key will show that you (Bob) trust that the key belongs to her.  

Now let's say Alice has a friend, Charlie, that lives on the other side of the country and whom you have never met or seen.  Let's say Charlie would like to communicate with you privately for some reason. The first step, obviously, is for him to send you his public-key.  He can do that via e-mail or his website or any other public means -- it doesn't really matter how he does it as we have already covered that public keys are perfectly OK to send insecurely.  The problem is you have no way of knowing whether this person really is Charlie or some clever impostor.  But all hope is not lost as there's a way to check without having to meet him in person.  You look at the key he sent you and you notice that Alice has signed his key (you verify it really is Alice's signature by checking that her digital fingerprint matches the digital fingerprint she left on your key).  Since you trust Alice, then you can trust that this person really is Charlie.  Of course, the WOT can go as far down the line as you want (you can trust that Charlie has verified the signatures on his own key and then make friends with his contacts without having to meet them).  And you can do the same for those people's friends.  It all depends on how far down the line you are willing to trust that people have actually verified the keys of other people.  This is basically how the Web of Trust works.  You essentially trust other people you know to verify identities for you.  Large webs of trust can be tricky and if all of your contacts are not thorough in verifying identity, it is possible for impostors to sneak in.

Another method of solving this is to have large centralized organizations identify everyone.  This is known as PKI [(Public Key infrastructure)]("https://en.wikipedia.org/wiki/Public_key_infrastructure") and is the method SSL uses.  PKI on its face seems to make this problem much simpler -- a big certificate authority (CA) has everyone submit ID to them and they in return sign your key.  The problem with this is that there are over 600 of these organizations around the world and anyone who somehow steals *any* one of their keys is able to forge signatures on bogus keys (and then impersonate most any site on the Internet).  This has happened a number of times already with some of the CA's [(Comodo, for example).]("http://www.wired.com/threatlevel/2011/03/comodo_hack/")  So it comes down to trusting a CA to do the right thing.  History has shown us that some of them are very sketchy and don't do proper checking of identities and do not secure their keys very well.  Basically, if you use SSL and rely on your browser to check the certs, there is no way you can be 100% sure you are not being spied upon by a third party even if the browser says the cert is valid.  SSL is broken and needs to be fixed, but that's beyond the scope here.  For a good talk about SSL and it's problems, I highly recommend Moxie Marlinspike's talk that you can [watch here.]("https://www.youtube.com/watch?v=Z7Wl2FW2TcA")  I also recommend you install his Firefox add-on.

**[CENTER][SIZE="3"]Putting Together What We've Learned[/SIZE][/CENTER]**

Hopefully the above sections have provided the reader with a decent (if not admittedly incomplete) basic history of how cryptography evolved and why.  We have covered both symmetric and asymmetric ciphers as well as what the Web of Trust is.  Let us define a few terms below for completeness:

1) Symmetric cipher -- A cipher that uses the same key to encrypt and decrypt (AES, DES, Twofish, etc.).

2) Asymmetric cipher -- A cipher that uses one key to encrypt and a different, but related, key to decrypt (RSA, ElGamal, Diffie-Hellman).

3) Hash Function -- Also known as a message digest.  A hash function takes an arbitrary block of data of any length and returns a fixed size unique string. (MD5, SHA-1, RIPEMD-160, etc.)

4) Hybrid cryptosystem -- A system that utilizes both asymmetric and symmetric techniques.

5) Web of Trust -- A distributed method of having people you trust verify keys of people you don't know.

The above terms are crucial for one's understanding in order to use GnuPG (and public-key crypto in general) effectively. It should be mentioned at this point that public-key crypto schemes (due to their mathematical properties) require much larger keys to obtain the same amount of security as a symmetric cipher.  It is estimated that a 1024 bit RSA key is equivalent in strength to an 80 bit AES key.  A 2048 bit RSA key is believed to be about of equal strength to a 112 bit key. To achieve full 128 bit security you need roughly a 3072 bit key.  Asymmetric ciphers are also much slower.  As a result of this, most modern systems are what we call hybrid-cryptosystems.  GnuPG is such a hybrid system.  When you encrypt a message to a contact, the symmetric cipher (AES, CAST5, etc.) is used to do the bulk encryption of the message itself.  Since symmetric ciphers use the same key for encryption and decryption, you encrypt that key with your asymmetric algorithm.  Your contact then gets the message, decrypts the symmetric key, and then uses that key to decrypt the actual message. So, once again, the only thing the asymmetric algorithm is used for is encrypting the key of the symmetric algorithm (like AES).  GnuPG does this all automatically for you, of course.  So, the next time someone confuses RSA for AES, you can explain to them the difference.

Hash functions are very important in cryptography, but I will not spend much time on them here.  Basically a hash function takes any arbitrary block of data and returns a fixed length string (usually much shorter than the original).  Hash functions are designed not to be reversible -- that is they are one-way functions.  So in this regard, they are similar to ciphers. You can hash down anything.  If you have a novel you are writing and it's 300 pages, you can hash it down to a single 128 bit string that identifies it as unique.  It's the same for any data -- all of it can be hashed down to a 128 bit string (or 160 bit or 256 bit or whatever the size of the hash is).  When you verify that a message has not changed in transit, you are actually checking its hash (the sender actually signs the hash of the message before he sends it.  When you receive it, you check that the hash you see matches the hash of the message that he signed).  When you hear the word "fingerprint" this usually means a hash.  Hashes can also be used for things like for protecting passwords, but that doesn't really matter here.  The only thing you need to know about hashes, for our purposes, is that MD5 is broken and should be avoided at all costs.  SHA-1 is still (mostly) OK, but it is recommended to move to SHA-256 or better.  The GnuPG defaults do not use MD5, so you should be OK there.

**[SIZE="2"][CENTER]To Be Continued[/CENTER][/SIZE]**

I will continue this post very soon.  In Part II I will outline how to use GPG.  But first, it is crucial that anyone interested in understanding how it works, understands the concepts posted here.

---

### Post by ottosykora on 2012-05-09
fine work!
thanks

---

### Post by donsy on 2012-05-09
Very well written, looking forward to the next installment.

---

### Post by rookcifer on 2012-05-10
[SIZE="3"]**[CENTER]Part II: How To Use GnuPG[/CENTER]**[/SIZE]

In Part I, I explained what public-key cryptography is and how it solved the problem of key exchange over insecure channels, as well as how it solved the very pernicious problem of symmetric key management.  If you do not understand how public-key crypto works, I highly recommend you read part I above.

What I will explain here is how to use GnuPG.  GPG is primarily used for secure e-mail exchange, but it also has other uses of which I will also cover.  In the next section I will show how to generate a key.  

**[CENTER][SIZE="2"]GnuPG Key Generation[/SIZE][/CENTER]**

For key generation the reader will need the terminal.  Seahorse can generate keys graphically, but Seahorse has many problems, so I prefer to use the terminal.  I will assume here that the reader has a basic understanding of elementary terminal commands.  For every command I present, I will show a screenshot of my own machine performing the command so that the reader can follow along visually.

**[CENTER]Step 1[/CENTER]**

Open a terminal and type the following:

```
gpg --gen-key
```

The first choice you have to make is what type of key you want to make.  GnuPG gives good defaults and you should probably stick with them.  If you are an advanced user, you can run the above command with the --expert flag for more options.  But I do *not* recommend that unless you really know what you are doing and have a good reason why.
[B]
So here, you should choose "1" and go with RSA/RSA. [/B] 

[IMG]http://s18.postimage.org/4i6uik0vd/gen_key.png[/IMG]

**[CENTER]Step 2[/CENTER]**

The next question will be how long of a key you want.  It is *highly* recommended to go with at least 2048 bits (which is the default).  This should be fine for most people.  However, most people will want a key with a long life, and since we have no idea how much factoring technology will increase in the future, I recommend going with at least 3072 bits.  3072 bits gives you roughly the same strength as AES-128, so I think it is the right choice for a long life key.  You could also go with 4096, which is the maximum.  Either choice is fine. 

I went with 3072 bits in my example.  (You will have to enter the keylength twice, as GPG creates two keys here).

After you enter the keylength, it will ask you how long you want the key's life to be.  I recommend not setting any limit.  So, select 0 here.

[IMG]http://i48.tinypic.com/10sd8gi.png[/IMG]


[CENTER]**Step 3**[/CENTER]

Now you must enter the identity you want attached to the key.  This could be either your real name or an alias.  If you want to get into a web of trust with your friends, I recommend putting your real name here so that other people can verify your identity in real life.  It is kind of hard to verify a key named "1337hackerman" because there is simply no way to tell who "1337hackerman" is.  Don't misunderstand, there is nothing wrong with using aliases.  Indeed I have two separate keys, one under my Internet alias and one under my real name.  I just realize that no one will ever accept my alias into a web of trust and I am fine with that.  I have a key under my real name for that.  

Again, if you want to use the key for any real work (i.e. you want people to trust the key), *you will need to enter your real name. *

After you enter the name, then enter the e-mail address you want associated with that key.  I used "John Doe" in the example here and "JohnDoe@xyz.com" as the example e-mail address.


**[CENTER]Step 4[/CENTER]**

Now it will ask you for your passphrase.  I recommend you enter a passphrase of at least 13 or so characters with upper and lowercase letters and some numbers and special characters thrown in.  ***The longer the passphrase the better!***  Do NOT forget this passphrase and do not write it down on some sticky note somewhere.  You may have to spend a little time with selecting a good passphrase that you can remember, so I recommend doing it right.  This passphrase is what protects your private key, and if you will recall in Part I, the private key is what you must take great care to protect.

[IMG]http://i49.tinypic.com/2dul406.jpg[/IMG]

**[CENTER]Step 5[/CENTER]**

After you enter the passphrase, you will notice that GPG is needing to collect entropy.  Entropy, in cryptography, is essentially what a pseudo-random number generator (PRNG) will use as a seed.  Since computer PRNG algorithms cannot create true random numbers, they must rely on outside input to help.  What GnuPG does is rely on /dev/random, which collects "entropy" from user mouse movements, keyboard presses, disk drive operations and a few other things that are thought to be sufficiently unpredictable to an attacker.  GnuPG then takes these unpredictable seeds and feeds them through a PRNG so the output looks random.  If you want to read more on how one can generate secure random numbers on a computer, there are a number of resources out there.  Just type into google the phrase "Cryptographically secure pseudo-random number generator" or "CSPRNG."  It is an interesting topic unto itself.

The technique GnuPG uses is secure, but it assumes the attacker does not have access to your box when the keys are being generated.  Keep that in mind!

So at this stage, you should move your mouse around on your screen as unpredictably as possible.  When entropy collection is finished, GnuPG will create your key.  You should now see a screen that looks like this:

[IMG]http://i47.tinypic.com/145ljl.png[/IMG]


Your key is now created.  You will see the key ID and the fingerprint on your screen.  One thing to keep in mind here is that what GnuPG did was actually create **two** key-pairs.  You can see this by running:

```
gpg --list-keys
```

And finding your key.  

You will notice it lists two different key ID's.  One is your master key and the other is a sub-key.  Both of these keys have a public and private component.  When you send someone your public key, you are actually sending them both of these public keys.  The sub-key is used for actually encrypting messages to you and the main key ID is used by your contacts to check your signature.  (Your sub-key is actually signed by your master key.)  I know this sounds confusing, but just think of the sub-key as being used to encrypt to you and the master key being used to check your signature.  When you sign a message you are actually signing it with your master key's private key.  Again, both of these keys each have a public/private component for a total of four keys.

**[CENTER]Step 6: Create a revocation certificate[/CENTER]**

One thing you need to do now is create a key revocation certificate.  Why is this important?  Consider the possibility that you lose your private key or forget it's password.  In that case you will need a way of proving to your contacts that you really lost it.  So you must create a certificate that you would send them that proves this, and you must do this *before* your key is lost!  With this certificate your contacts can verify that indeed it is your certificate and that you really did lose your key.  

Still don't understand why this matters?  Well, consider the following scenario.  Let's say one day one of your contacts receives an e-mail from someone pretending to be you.  The e-mail is as follows:

> "Hello, I am John Doe.  Please do not send e-mail to my old e-mail address (JohnDoe@xyz.com).  Instead use this new address (JohnDoe@abc.com).  I have lost my key!  My new key is attached to this e-mail. Please send future e-mail to this new e-mail address with this new key."  

Of course most people will be suspicious when he says not only did he lose his key but he also changed his e-mail address.  Even in that case, it is possible an attacker somehow hacked your e-mail address and has control of it too.  So in that case all he would need to do is convince them to use his new fake key.

As you can see, this person could be anyone.  And unless your contact asks for a revocation cert, he could easily be fooled into actually communicating with this person thinking he is you!  This type of thing could easily happen in a business situation with someone trying to steal trade secrets or some other type of high-value target.  Again, if your contact is smart, he/she will ask this person for a revocation certificate.  Since this impostor will not be able to provide one, it proves he is a fake.  (Of course, this also depends on your contacts being vigilant and actually checking for a revocation cert, but that's another issue).

So this is why it is important that you create a revocation certificate *now* in the case your key is lost in the future. Because if your contacts are vigilant and want you to prove you lost your key, you are out of luck (unless you know them personally and can call them, etc.  But this is not possible with some contacts you may not know as well.  And even if it were, this means making a lot of phone calls and wasting a lot of time trying to convince people you really lost your key.)  Avoid this hassle by creating a revocation cert *now*.

Open a terminal and type the following.  (Note, I will use the example key I created.  Substitute your own key's information accordingly):

```

gpg --output revoke.asc --gen-revoke JohnDoe@xyz.com
```

It will then ask you to specify a reason.  You can leave it blank.  It will then ask for a comment.  I like to put something there like "I am generating this certificate in advance in case my key is lost or stolen."  It will then ask for your password.  Enter it and then the revocation cert is generated.

At this point you should move this certificate to a safe place.  A backup CD or USB drive is a good place to store it.  Even better is put that CD or thumb drive in a safe place, like a locked safe or in your bank's safety deposit box.  It is probably a good idea to also print out a physical copy and place it there as well (CD's can wear out if they sit for a long period of time). Just remember to put it somewhere that an attacker cannot get it!


**[CENTER][SIZE="2"]Final Step: Upload your Key[/SIZE][/CENTER]**

One final thing you might want to do is upload your key to a key server so that anyone on the Internet can easily find it.  This is a personal preference.  If you only want to use the key to communicate with a few close friends, then you could just send the key to them individually.  If you want to be open for anyone on the Internet to send you secure e-mail, you will probably want to put it on a key server.  I will show you now how to do that now.

Open a terminal and type:

```
gpg --keyserver pgp.mit.edu --send-keys <YourKeyID>
```

The key ID will be the 8 digit ID of your public key.  You can see that by running:

```
gpg --list-keys
```

and finding your public-key ID (it will be the one on the top, not the key on the bottom).

**[SIZE="3"][CENTER]Conclusion[/CENTER][/SIZE]**

In this tutorial, I have demonstrated how to create a key-pair, how to create a revocation certificate, and how to upload the key to a key server so that anyone in the world can get it and send you secure e-mail.  In future installments I will talk about how to easily setup Thunderbird to utilize your key.  I will also comment on key-signing and a little bit more on how to utilize the Web of Trust.

Until next time..

---

### Post by ottosykora on 2012-05-11
again many thanks for that. It looks like this will become a sticky tutorial thread as most people have hard times to read all that rather technical original manual.

---

### Post by Shadius on 2012-05-11
Great stuff! Have you thought about doing a series about this on Full Circle Magazine?

---

### Post by donsy on 2012-05-11
> **rookcifer said:**
> 
...
You will notice it lists two different key ID's.  One is your master key  and the other is a sub-key.  Both of these keys have a public and  private component.  When you send someone your public key, you are  actually sending them both of these public keys.  The sub-key is used  for actually encrypting messages to you and the main key ID is used by  your contacts to check your signature.  (Your sub-key is actually signed  by your master key.)  I know this sounds confusing, but just think of  the sub-key as being used to encrypt to you and the master key being  used to check your signature.  When you sign a message you are actually  signing it with your master key's private key.  Again, both of these  keys each have a public/private component for a total of four keys. 
...


Finally a concise explanation in plain language. Great job!

---

