---
title: "Hardening default security and other power user features"
date: 2008-10-27
forum: Ubuntu Brainstorm
---

### Post by OpenSourceFuture on 2008-10-27
This is basically a list of feature requests relating to security.

I know its possible (I have done it thanks to information on this forum) but users should have more control, more user friendly at least, over the type of password hashes used, and the salt length added to the hashes. Unless I'm mistaken salt is not a configurable option yet. This would be useful for the security minded. Even low salts are vulnerable to rainbow tables, and SHA-512 takes about 4 times as much CPU power to generate than MD5 which is the current standard. So stronger default salts and stronger default hashes would be a good feature. Maybe a configurable option during password setting as well to control the level of security, as well as making secure options the default choice so it is newbie friendly.

In addition to this I think the GRSecurity kernel patches should be an installable/selectable package just like any other standard kernel, and should be more compatible with full drive crypt (I had problems). Features of GRSecurity that significantly reduce vulnerability without compromising security should be integrated into mainstream ubuntu.

Also maybe ubuntu could have a default server or paranoid mode where all essential files and programs are checked against a strong salted hash file at start up. This would be purely optional as it would impact some computers performance, although many of these security suggestions are optional, most modern machines can handle them with extreme ease.

On top of this full drive encryption should have the option of multiple keys like truecrypt (Example: Serpent 256, on top of AES 256, on top of Twofish 256) , as well as keyfile on boot support.

These are all just suggestions of course, but they would not be bad ideas.

Comments, feedback, and suggestions are welcome.

---

### Post by hyper_ch on 2008-10-28
> **OpenSourceFuture said:**
> over the type of password hashes used, and the salt length added to the hashes. Unless I'm mistaken salt is not a configurable option yet. 
What passwords/salts are you speaking of?

> **OpenSourceFuture said:**
> In addition to this I think the GRSecurity kernel patches should be an installable/selectable package just like any other standard kernel, and should be more compatible with full drive crypt (I had problems). Features of GRSecurity that significantly reduce vulnerability without compromising security should be integrated into mainstream ubuntu.
What does it do?

> **OpenSourceFuture said:**
> Also maybe ubuntu could have a default server or paranoid mode where all essential files and programs are checked against a strong salted hash file at start up. This would be purely optional as it would impact some computers performance, although many of these security suggestions are optional, most modern machines can handle them with extreme ease.
You mean at boot up first firing up network and then checking the binaries against checksums?

> **OpenSourceFuture said:**
> On top of this full drive encryption should have the option of multiple keys like truecrypt (Example: Serpent 256, on top of AES 256, on top of Twofish 256) , as well as keyfile on boot support.
What's the use of those chained encryption algorithms? Keyfile on boot is not that difficult, however most people will not use alternate install cd anyway for installation. Those who do will, IMHO, also find out how to accomplish that - although it would be easier if integrated...

---

### Post by cdenley on 2008-10-28
> **OpenSourceFuture said:**
> 
I know its possible (I have done it thanks to information on this forum) but users should have more control, more user friendly at least, over the type of password hashes used, and the salt length added to the hashes. Unless I'm mistaken salt is not a configurable option yet. This would be useful for the security minded. Even low salts are vulnerable to rainbow tables, and SHA-512 takes about 4 times as much CPU power to generate than MD5 which is the current standard. So stronger default salts and stronger default hashes would be a good feature. Maybe a configurable option during password setting as well to control the level of security, as well as making secure options the default choice so it is newbie friendly.

In hardy, you can only use MD5 or DES hashes in shadow, unless you install a replacement pam_unix module. In intrepid, sha512 is used by default, so there is no need to change it.

---

### Post by OpenSourceFuture on 2008-10-28
> **hyper_ch said:**
> What passwords/salts are you speaking of?

Your password is stored as a hash file:

[http://en.wikipedia.org/wiki/Hash_function](http://en.wikipedia.org/wiki/Hash_function)

Hash files (mostly unsalted although salted is still possible on low levels of salt) are vulnerable to rainbow tables.

[http://en.wikipedia.org/wiki/Rainbow_tables](http://en.wikipedia.org/wiki/Rainbow_tables)

> **hyper_ch said:**
> 
What does it do?


[http://en.wikipedia.org/wiki/Grsecurity](http://en.wikipedia.org/wiki/Grsecurity)

> **hyper_ch said:**
> 
You mean at boot up first firing up network and then checking the binaries against checksums?


Maybe locally, but essentially yes.

> **hyper_ch said:**
> 
What's the use of those chained encryption algorithms? Keyfile on boot is not that difficult, however most people will not use alternate install cd anyway for installation. Those who do will, IMHO, also find out how to accomplish that - although it would be easier if integrated...

More powerful encryption provides better privacy, and although the password is the most likely thing to be attacked, having chained keys adds security exponentially. If it were a standard feature (all ready implemented in true crypt) then the user could decide wither or not they use it, so if you think its pointless, don't use it. Plain and simple.

---

### Post by OpenSourceFuture on 2008-10-28
> **cdenley said:**
> In hardy, you can only use MD5 or DES hashes in shadow, unless you install a replacement pam_unix module. In intrepid, sha512 is used by default, so there is no need to change it.

I already changed mine to sha512, but sha512 is still vulnerable to rainbow tables, and so is small salt lengths. I'm just requesting more hash options, whirlpool, ripemd160, hell in theory you could also add WPA-PSK hashing, which is a very hard hash to compute, and salted it would be nearly uncrackable. Either way control of hash type, and control of salt length, would be quite useful for the security minded.

Edit: WPA-PSK you would have to tell the hash you have an SSID but you can just make it compute that based on your user name, it is still fully feasible, and would be a very functional and strong hashing algorithm for passwords.

---

### Post by cdenley on 2008-10-28
> **OpenSourceFuture said:**
> I already changed mine to sha512, but sha512 is still vulnerable to rainbow tables, and so is small salt lengths. I'm just requesting more hash options, whirlpool, ripemd160, hell in theory you could also add WPA-PSK hashing, which is a very hard hash to compute, and salted it would be nearly uncrackable. Either way control of hash type, and control of salt length, would be quite useful for the security minded.

Edit: WPA-PSK you would have to tell the hash you have an SSID but you can just make it compute that based on your user name, it is still fully feasible, and would be a very functional and strong hashing algorithm for passwords.

I don't think it would be possible to use any of those alogirithms with PAM, let alone create a configuration utility to make it easier.

SHA512 is vulnerable to rainbow tables? Can you provide an example or proof of concept?

Off the top of my head, I think it uses a 16 character salt, with 64 possible characters.
a-z A-Z 0-9 / .
That means each password has 64^16 possible salts.
Each sha512 hash is 86 characters long. That means for each password in your sha512 rainbow tables, you need 6051711999279104 petabytes to store the hashes.
86 * 64^16 = 6051711999279104 * 1024^5
Are my calculations correct? Even if you have a weak password, and it is one of 10,000 in a password dictionary:
6051711999279104 * 10,000
Are you really worried that someone with 60517119992791040000 PETABYTES of storage space is going to use rainbow tables to crack your passwords?

> Even for older Unix passwords, which used a 12-bit salt, this would be improbable.
Try reading your own link!

---

### Post by OpenSourceFuture on 2008-10-28
> **cdenley said:**
> I don't think it would be possible to use any of those alogirithms with PAM, let alone create a configuration utility to make it easier.

SHA512 is vulnerable to rainbow tables? Can you provide an example or proof of concept?


Most any multithreaded rtgen can generate SHA-512. Now that these can be run on graphics cards attacks like these are probable. 

> **cdenley said:**
> 
Off the top of my head, I think it uses a 16 character salt, with 64 possible characters.
a-z A-Z 0-9 / .
That means each password has 64^16 possible salts.
Each sha512 hash is 86 characters long. That means for each password in your sha512 rainbow tables, you need 6051711999279104 petabytes to store the hashes.
86 * 64^16 = 6051711999279104 * 1024^5
Are my calculations correct? Even if you have a weak password, and it is one of 10,000 in a password dictionary:
6051711999279104 * 10,000
Are you really worried that someone with 60517119992791040000 PETABYTES of storage space is going to use rainbow tables to crack your passwords?


First of all weak passwords can easily be brute forces on the fly, computational power has come a long way and this is not only probable, but the first step to any attack would be a dictionary attack.

Lets look at a much more practical scenario. 1-8 lowercase alpha numeric SHA-512 tables with 95.83% success rate would be 29.8 gigs. Chain length: 4800, chain count 100000000, number of tables 20. The total space requirements is a mere 29.8 gigs!

Luckily no one as access to that type of technology!

Although it could take a long time to generate on a standard single core processor, and the above example doesn't include salts, table generation on graphics cards makes this WAY faster and WAY cheaper. I could do that math if you'd like but it is really not worth the effort to make a point. 

You can increase the chain length of rainbow tables to increase the amount of passwords they can crack WITHOUT increasing file size, so really your example is utterly useless. The trade off is it increases analysis time when using the tables, but depending on how fast it was to begin with doubling, or even quadrupling the table chain lengths without increasing the chain count would allow for many more passwords to be checked without a significant decrease in speed, while at the same time decreasing file size by quite a bit. The above example changes as follows when the chain length size is doubled: 14.9 gigs total space, 10 tables, 95.32% success rate.

14.9 gigs too impractical for you?

Basic tables that check most possible user passwords are very feasible, and hard drive space is cheap (1.5TB internal SATA 180USD last time I checked) and computational power is relatively cheap (look at NVIDIA graphics cards). Even with the current salt size, a table of probable passwords, as the one calculated against WPA-PSK hashes (Each passphrase is hashed 4096 times with SHA-1 and 256 bits of the output is the resulting hash, much longer to calculate than SHA-512 by the way.) is possible, as well as tables of lower password lengths with salt, it is just less practical.
 
Not to mention now attackers now have access to distributed rainbow table generation, and distributed hash checking, although SHA-512 isn't on the priority lists of these organizations, MD5 is already done for, DES is already done for, and as people upgrade, so will the people trying to crack them.



> **cdenley said:**
> 
Try reading your own link!

I have but I will read everything twice just for you ;)

To reiterate you don't need to check every possible hash, or even every possible salted hash, I'm just saying longer salts would be a good thing, not a bad thing, and more user control of this is what I am requesting, not to mention the other improvements.

---

### Post by nubdora on 2008-10-28
> **cdenley said:**
> 
Are you really worried that someone with 60517119992791040000 PETABYTES of storage space is going to use rainbow tables to crack your passwords?


He should be. I have 60517119992791040001 petabytes worth of networked storage.

---

### Post by cdenley on 2008-10-28
> **OpenSourceFuture said:**
> First of all weak passwords can easily be brute forces on the fly, computational power has come a long way and this is not only probable, but the first step to any attack would be a dictionary attack.

Of course, but this would be true of any hash algorithm.
> **OpenSourceFuture said:**
> 
Lets look at a much more practical scenario. 1-8 lowercase alpha numeric SHA-512 tables with 95.83% success rate would be 29.8 gigs. Chain length: 4800, chain count 100000000, number of tables 20. The total space requirements is a mere 29.8 gigs!

How did you come up with those numbers? Is that for the SHA-512 alogorithm uses by pam_unix?
> **OpenSourceFuture said:**
> 
Although it could take a long time to generate on a standard single core processor, and the above example doesn't include salts, table generation on graphics cards makes this WAY faster and WAY cheaper.

Wouldn't not including salts would make your tables rather useless?
> **OpenSourceFuture said:**
> 
Basic tables that check most possible user passwords are very feasible, and hard drive space is cheap (1.5TB internal SATA 180USD last time I checked) and computational power is relatively cheap (look at NVIDIA graphics cards). Even with the current salt size, a table of probable passwords, as the one calculated against WPA-PSK hashes (Each passphrase is hashed 4096 times with SHA-1 and 256 bits of the output is the resulting hash, much longer to calculate than SHA-512 by the way.) is possible, as well as tables of lower password lengths with salt, it is just less practical.

I think SHA-512 uses 1000 rounds of hashing, but I'm not sure. I'm not sure which would be more expensive, 4096 rounds of SHA-1 or 1000 rounds of SHA-512.
> **OpenSourceFuture said:**
> 
To reiterate you don't need to check every possible hash, or even every possible salted hash, I'm just saying longer salts would be a good thing, not a bad thing, and more user control of this is what I am requesting, not to mention the other improvements.
Do you want more crypt functions to be added to linux? They just added SHA-512, and I'm satisfied with that. Better user control of pam modules wouldn't be a bad thing, but a little unnecessary since it defaults to the most secure possible with the version of PAM being used.

---

### Post by OpenSourceFuture on 2008-10-28
I came up with those numbers using winrtgetn v2.8 which states table size before generation if you run a benchmark on the proposed hash and table size. 

The *example* table would be useless against salted hashes, but tables can be generated with salt, and I was just showing how small the tables really were, I'm not quite sure how you got the table size you did, but I know for a rainbow table within a practical password length it is not nearly as large, and they can be generated with salt. If fact they would be exponentially smaller. The table I showed was just an example for the sake of showing just how small they are, and it uses the one and only SHA512 algorithm, the same one you use, the only difference is salt.

I can tell you right now from experience WPA-PSK is more expensive on CPU power than SHA-512, significantly more. Not to mention I really don't think Sha512 is the most secure hashing algorithm, as SHA0 was proven completely insecure, SHA1 has had a successful attack on it, so in theory the same principles will apply to the SHA2 family of hashes (which includes SHA512) and SHA512 will eventually be broken, but of course it is all open to debate and time will tell. If it was perfectly secure as is, and secure for the immediate future, I would think SHA3 would not now be in development as there would be no need for it. Of course with hash options I can only choose between the extremely broken DES, the very broken MD5, and the *currently* secure SHA512. All this being said SHA512 is a significant improvement of MD5 which is garbage in respect to password hashing, but at least its not LM.

This aside I was just asking for hash options, and the option to set higher Salt values, not to mention the GRSecurity patch options.

---

### Post by OpenSourceFuture on 2008-10-28
> **nubdora said:**
> He should be. I have 60517119992791040001 petabytes worth of networked storage.

It is people like you we need to look out for ;)

---

### Post by OpenSourceFuture on 2008-10-28
SHA-512 uses 80 rounds of hashing by the way, I'm not quite sure where you are pulling these numbers from. SHA-0 SHA-1 both use 80 rounds, SHA-2 uses 64 rounds for SHA-256, and 80 for SHA-512. SHA-2 has more operations, a bigger initial state size, and SHA-512 has a higher max word size, but they are algorithmically similar to SHA-1, which may have mathematical weaknesses, hence why alternatives are being developed. 

In the meantime it would be prudent to use something else, and although there is nothing worth cracking my password for to obtain on my computer since I just use it as a normal desktop, some people rely on Linux for more important tasks. For the sake of those people there should be hash options and salt options, that is why I was suggesting it.

---

### Post by cdenley on 2008-10-29
> **OpenSourceFuture said:**
> SHA-512 uses 80 rounds of hashing by the way, I'm not quite sure where you are pulling these numbers from. SHA-0 SHA-1 both use 80 rounds, SHA-2 uses 64 rounds for SHA-256, and 80 for SHA-512. SHA-2 has more operations, a bigger initial state size, and SHA-512 has a higher max word size, but they are algorithmically similar to SHA-1, which may have mathematical weaknesses, hence why alternatives are being developed. 

In the meantime it would be prudent to use something else, and although there is nothing worth cracking my password for to obtain on my computer since I just use it as a normal desktop, some people rely on Linux for more important tasks. For the sake of those people there should be hash options and salt options, that is why I was suggesting it.

[http://en.wikipedia.org/wiki/Crypt_(Unix](http://en.wikipedia.org/wiki/Crypt_(Unix))
Maybe I was confusing rounds with iterations. The MD5 algorithm actually created the password hash by hashing the password 1,000 times. The SHA based scheme is supposed to be similar to the MD5 scheme, so I assumed it also goes through 1,000 iterations.

SHA-512 hashes are not the same thing as the SHA-512 scheme used for password hashes in intrepid. Same with MD5. I'm pretty sure winrtgen does NOT create rainbow tables which can be used against linux. In fact, your link says the MD5 scheme used in linux is NOT vulnerable to rainbow tables, so I would assume SHA-512 is even safer (it has a larger salt).
> 
The MD5-crypt and bcrypt methods--used in Linux, BSD Unixes, and Solaris--have salts of 48 and 128 bits, respectively.[2] These larger salt values make precomputation attacks for almost any length of password impossible against these systems for the foreseeable future.


I think there was more to rainbow tables than I initially realized. My numbers were for all precomputed hashes for a given password dictionary, but apparently rainbow tables are a little more efficient. I still doubt you can crack SHA-512 linux passwords with rainbow tables (especially a 29.8 GB one). I'll have to read more about rainbow tables.

---

