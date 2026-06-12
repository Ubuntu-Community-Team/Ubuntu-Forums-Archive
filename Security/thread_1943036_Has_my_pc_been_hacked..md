---
title: "Has my pc been hacked."
date: 2012-03-18
forum: Security
---

### Post by Janeleaper on 2012-03-18
Hi.  I have a slightly odd situation.  I'd just like to know what people think I should do, if anything.

 A few weeks ago, I found I could not access my gmail account.  The password was not recognised.  So, I answered the security question instead.  I was puzzled because I'd certainly not changed the password, which was a strong one.

Then the same day, I went to log into my bank account, and got a message warning me that someone had tried to access the account from a computer other than my own.  The person had got the password right, but not the security question that is asked if login is from an unauthorised computer.

So, I changed the password on my bank account too. 

No fraudulent activity seems to have taken place.  My friends haven't received emails asking for money or anything like that.

Today, I went to check my gmail, and found my password was not recognised again.

So, I've change the passwords on both my bank and gmail accounts for a second time, using strong passwords, and this time I've used Onboard, rather than the keyboard.

Is there anything else I should be doing?

---

### Post by OpSecShellshock on 2012-03-19
It's really hard to determine from the listed facts whether or not your computer specifically has been compromised in some way. Certainly it isn't necessary to compromise someone's computer in order to do the things that have been done with your accounts.

You can check in gmail to see when your account has been accessed from somewhere other than your own computer, I believe, although that won't tell you how. You can also go into the settings for gmail and check to see if any forwarding rules have been applied while this other person had access to the account.

My best guess: some site that you have signed up for using that gmail account has been breached, which led to your account name being exposed. If you use an easily guessed password, or used the same password for gmail that you used on the other site, then it would be easy to get into your mail account. If you also use that mail account to communicate with your bank, then anyone who can read old messages on that account would find out what your bank is and could possibly get your username on that site. Then they'd try using the same password as the mail account or would try to brute force it with a reasonably high possibility of getting in depending on the strength or uniqueness of the password. Or they could use the fact that they know both your email address and your bank to conduct a phish. Could be lots of things really.

Sorry this is happening. Hopefully we can help.

---

### Post by Janeleaper on 2012-03-19
Thanks for the reply.

My gmail password was strong and not used for any other site.  My bank password was also strong and not used for any other site.  Naturally, they have been replaced with equally strong and unique passwords.

It's that that puzzles me, really. The only way I can think that my password could have been revealed is by malware copying the keystrokes.  I'd been advised to use an onscreen keyboard, but because I use Linux, I did not think it would be necessary.

---

### Post by sidzen on 2012-03-19
As a suggestion --

Download, burn to CD, and learn how to use [**puppy linux**]("http://puppylinux.org/main/Download%20Latest%20Release.htm#lucidpuppy") from LiveCD to acess bank account, especially.  Dedicate your smallest USB stick to use with puppy to save your config files on it (encrypt them if you so desire) and take the stick out when done with puppy each time.

---

### Post by Ms. Daisy on 2012-03-19
Like OpSecShellshock said, it's hard to know how it happened based on what you said. 

Don't forget to consider the simple stuff. Is it possible that perhaps you mixed up the passwords on the accounts?  I've done that before, temporarily locking myself out of ubuntuforums when I was using a password for another site without realizing it.  If it happens again, find a way to confirm that you're using the correct password on the correct site.

Do you use any kind of browser security (blocking scripts, blocking ads)? Do you have the browser remember passwords? The browser is a popular attack surface & there are things you can do to increase your security there.  Take a look at the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity") and see if you're doing those things already.

If you're concerned about malicious stuff already on your computer, you can look at the "[Did I Just Get Owned]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned")" wiki to help you track down anything suspicious.

---

### Post by mr-woof on 2012-03-20
Do you use any other machines? Have you accessed the sites on any other machines?

---

### Post by Janeleaper on 2012-03-21
Thanks for the replies.

Yes, my browser remembers passwords. 

I'll try out all the suggestions.

No, I did not forget a password or use the wrong one.

---

### Post by Janeleaper on 2012-03-21
Mr Woof. I do use other machines occasionally, but when the security breach occurred, I'd not used another machine for weeks.  The message from my bank stated that another machine had tried to access my account, had the password, but did not get the security question right. The security question is asked only if access is from an unauthorised machine.  All my machines (desktop and notebooks) are authorised.

Also, although my browser does memorise passwords, it does not do so for my bank account.

---

### Post by OpSecShellshock on 2012-03-21
A period of weeks between the interception of credentials and their attempted use by others is not unusual. Usually one party will distribute malware, one will maintain the infrastructure for intercepted credentials to be delivered and stored, and will sell or give them to yet another party for actual use. It could honestly have been any of the computers that you had used in the three or four months prior to the unauthorized access attempts.

---

### Post by 0011235813 on 2012-03-22
I recommend you install KeePass2 or the Lastpass add-on to generate very secure passwords that only require you to remember the master password to use (try: iN$@nec0de$0feternity) . 

As for the keylogger idea, I would follow the requested ufw configuration wikis and block outgoing ports except http,https,smtp etc.
Checking your logs would be a good idea too. And the DidIJustGetOwned wiki + all the stickies in this category.

---

### Post by MasterGamerJK on 2012-03-22
Any password of 15 chars is good, no need to have more than that. 

Keep in mind "aaaaaaaaaaaaaaa" is more secure than "@sf5T7" when it comes to a brute force attack : p

---

### Post by 0011235813 on 2012-03-23
> **MasterGamerJK said:**
> Any password of 15 chars is good, no need to have more than that. 

Keep in mind "aaaaaaaaaaaaaaa" is more secure than "@sf5T7" when it comes to a brute force attack : p

Actually no...
Test it for yourself if you don't believe me: [http://www.passwordmeter.com/](http://www.passwordmeter.com/)

---

### Post by Brian0312 on 2012-03-23
Since you're using Gmail, I'd be tempted to turn on 2 factor authentication as well (assuming you have a smart phone).  That way, a person would need your password, username and access to your device to break into your account.

---

### Post by 0011235813 on 2012-03-23
> **Brian0312 said:**
> Since you're using Gmail, I'd be tempted to turn on 2 factor authentication as well (assuming you have a smart phone).  That way, a person would need your password, username and access to your device to break into your account.

Hmmm... Good idea. I use that, however, it does mistake me for someone else when I'm using Tor, so keep that it mind.

---

### Post by TheS0urce on 2012-03-24
> **sidzen said:**
> As a suggestion --

Download, burn to CD, and learn how to use [**puppy linux**]("http://puppylinux.org/main/Download%20Latest%20Release.htm#lucidpuppy") from LiveCD to acess bank account, especially.  Dedicate your smallest USB stick to use with puppy to save your config files on it (encrypt them if you so desire) and take the stick out when done with puppy each time.

That's a very good suggestion however if the system is infected it won't help.  Plus it doesn't stop hackers loading from the hard drive.

There is a solution if you have a router connected to the internet. 
All you need is Lightweight portable security.  There is no root nor there is mounting to storage devices can be done.  So there's no way on mounting and infecting the hard drive.  When you want to do secure transaction you should reboot and disable all the plugins like flash and java.


[http://www.spi.dod.mil/lipose.htm](http://www.spi.dod.mil/lipose.htm)

One thing I learned is not to use flash, unless I'm using a live cd.  It's so easy to get hacked with flash.

---

### Post by haqking on 2012-03-24
> **0011235813 said:**
> Actually no...
Test it for yourself if you don't believe me: [http://www.passwordmeter.com/](http://www.passwordmeter.com/)

actually that site sucks.

length is better than complexity in general for a brute force attack though both examples suck overall.

keyspace increases entropy

---

### Post by 0011235813 on 2012-03-25
> **haqking said:**
> actually that site sucks.

length is better than complexity in general for a brute force attack though both examples suck overall.

keyspace increases entropy

Search it on any password checker you wish, and they will ALL give you the same result.

I agree length is better than complexity, but "aaaaaaa"? Seriously? Not only is that hard to remember, but the fact that it uses the same letter over and over dramatically lowers security. If length is what we're talking about, try; thiswillneverbrokeninalloftime, but why not capitalize the first or second letter, maybe add a 0 instead of o, etc. etc.

---

### Post by angryfirelord on 2012-03-25
Have you ever logged onto your gmail account on a wireless network? It's a small possibility, but a sniffer might have snagged your login credentials.

---

### Post by haqking on 2012-03-26
> **0011235813 said:**
> Search it on any password checker you wish, and they will ALL give you the same result.

I agree length is better than complexity, but "aaaaaaa"? Seriously? Not only is that hard to remember, but the fact that it uses the same letter over and over dramatically lowers security. If length is what we're talking about, try; thiswillneverbrokeninalloftime, but why not capitalize the first or second letter, maybe add a 0 instead of o, etc. etc.

i dont need to search it and it wasnt "aaaaaaa" it was "aaaaaaaaaaaaaaa" which is exponentially longer in terms of keyspace.

he said a brute force attack.

everything else you said is about password security and how to increase it which i am well aware of the point was the 2 passwords he mentioned.

length is more important than complexity due to information entropy in this example.

both of them suck and i wasnt supporting either of them, but length is more important in that example.

however seeing as you think they will all give same results then here you go

[https://www.microsoft.com/security/pc-security/password-checker.aspx](https://www.microsoft.com/security/pc-security/password-checker.aspx)
[http://rumkin.com/tools/password/passchk.php](http://rumkin.com/tools/password/passchk.php)
[http://howsecureismypassword.net/](http://howsecureismypassword.net/)
[http://www.hammerofgod.com/passwordcheck.aspx](http://www.hammerofgod.com/passwordcheck.aspx)
[https://www.grc.com/haystack.htm](https://www.grc.com/haystack.htm)

These all agree.

And the passwordmeter test you quotes states it requires a minimum 8 character then still gives a report for "@sf5T7" which doesnt even meet its own requirements.

Anyways its all good, feel free to use short 6 characters over 15 if you wish ;-)

oh and never use a password strength tester for real passwords

the point is both of them are useless, but in terms of brute force and the tool you use to brute force it and whether it is online and offline and how much information you know about the password the overall security in general of these would be that 15 chrs is stronger, but it depends on what you know and tool you use.

See attached, i created 2 accounts on a old XP VM one account with the password "@sf5T7" and one with "aaaaaaaaaaaaaaa", using a popular and easy to use brute force tool cain & abel i dumped the local account hashes from the system and then set it to brute force them.

using all characters available in the predefined section and choosing 1 to 6 for the 6 and 1 to 15 for the 15 chr you can see the time taken to brute force is quite different for both.

like is said it depends what tool you use and what you know, in this example i assumed we didnt know the character composition so i chose to use all which is realistic, i chose the amount of characters simply because LM hashes for example are easily identifiable if below 7 characters which in this example it is as it is 6.

of course LM hashes are easier to crack than other types so the type of password also counts over the composition of it.

cheers

---

### Post by Ms. Daisy on 2012-03-26
That was very informative, haqking. Nice post.

---

### Post by haqking on 2012-03-26
> **Ms. Daisy said:**
> That was very informative, haqking. Nice post.

just to make it clear.

I am not saying either should be used or are any good.

I am talking specifically about a "brute force attack" and entropy.

if you dont know any of the construct pointing a brute forcer at a password that is 6 chrs and 15 chrs is quite different to using a dictionary attack and known words or known elements of the password etc.

---

### Post by Dangertux on 2012-03-26
aaaaaaaaaaaaaaa is a much stronger password in terms of entropy than @sf5T7.

Here I will explain why.

for the a password we have 15 characters, they are only lower case alpha characters so for a moment lets assume that is ALL that is allowed is lower case characters. That means there is a possible 26 values for each letter of the password or.

26^15 which is roughly 1.677 * 10^21 combinations.

Now lets look at the second, which assumes special characters, upper case lower case and numbers for approximately 72 values for each letter which is

72^8 or roughly 7.22 * 10^14 possible combinations, this is much lower (7 powers of 10) than the 15 character seemingly weak password.

Hope this helps.

---

### Post by haqking on 2012-03-26
> **Dangertux said:**
> aaaaaaaaaaaaaaa is a much stronger password in terms of entropy than @sf5T7.

Here I will explain why.

for the a password we have 15 characters, they are only lower case alpha characters so for a moment lets assume that is ALL that is allowed is lower case characters. That means there is a possible 26 values for each letter of the password or.

26^15 which is roughly 1.677 * 10^21 combinations.

Now lets look at the second, which assumes special characters, upper case lower case and numbers for approximately 72 values for each letter which is

72^8 or roughly 7.22 * 10^14 possible combinations, this is much lower (7 powers of 10) than the 15 character seemingly weak password.

Hope this helps.

+1

always nice to see common sense when it comes to town ;-)

and it would be 72^6 so 1.3 * 10^11

Entropy is key

peace

---

### Post by Ms. Daisy on 2012-03-26
> **haqking said:**
> just to make it clear.

I am not saying either should be used or are any good.

I am talking specifically about a "brute force attack" and entropy.

if you dont know any of the construct pointing a brute forcer at a password that is 6 chrs and 15 chrs is quite different to using a dictionary attack and known words or known elements of the password etc. Yes, that's why I liked the post, I don't know how you could have been any more clear about the sucky nature of those passwords.

and now I'm waiting for the dictionary attack & known words/elements demonstrations... 
;)

---

### Post by haqking on 2012-03-26
> **Ms. Daisy said:**
> Yes, that's why I liked the post, I don't know how you could have been any more clear about the sucky nature of those passwords.

and now I'm waiting for the dictionary attack & known words/elements demonstrations... 
;)

well thats simple, if its in the dictionary its game over, if its not then its brute force...or hybrid in the first place

demonstration:

open up a dictionary, pick a random page, find a word.....the end ;-)

---

### Post by 0011235813 on 2012-03-26
> i dont need to search it and it wasnt "aaaaaaa" it was "aaaaaaaaaaaaaaa" which is exponentially longer in terms of keyspace.
No need to be pedantic please, it was an honest mistake. 

> he said a brute force attack.

everything else you said is about password security and how to increase it which i am well aware of the point was the 2 passwords he mentioned.

length is more important than complexity due to information entropy in this example.
I understand what you're trying to say, but why did the poster have to use such an awful example?

> both of them suck and i wasnt supporting either of them, but length is more important in that example.

however seeing as you think they will all give same results then here you go

[https://www.microsoft.com/security/pc-security/password-checker.aspx](https://www.microsoft.com/security/pc-security/password-checker.aspx)
[http://rumkin.com/tools/password/passchk.php](http://rumkin.com/tools/password/passchk.php)
[http://howsecureismypassword.net/](http://howsecureismypassword.net/)
[http://www.hammerofgod.com/passwordcheck.aspx](http://www.hammerofgod.com/passwordcheck.aspx)
[https://www.grc.com/haystack.htm](https://www.grc.com/haystack.htm)

These all agree.

And the passwordmeter test you quotes states it requires a minimum 8 character then still gives a report for "@sf5T7" which doesnt even meet its own requirements.

I know it failed, the point is that it gave a different result to what the OP said. Oh and I'm not sure why Microsoft and grc is there.
> Anyways its all good, feel free to use short 6 characters over 15 if you wish ;-)
Hmmm yes, simple six character passwords can be broken by a GPU accelerated smart password cracker in about... Two hours?

> oh and never use a password strength tester for real passwords
Yeah, you never know who might be in the middle, or how reputable the site is. For all you know, the site might have been compromised.

> the point is both of them are useless, but in terms of brute force and the tool you use to brute force it and whether it is online and offline and how much information you know about the password the overall security in general of these would be that 15 chrs is stronger, but it depends on what you know and tool you use.
Of course, a dumb program would obviously struggle with really long passwords, but the sad truth is that modern day password breakers are smart and that is why a password like "maryannrose" (a.k.a the persons name) is fra more likely to be broken than $Ds27 as the hacker would obviously try the persons name. Pure bruteforce dumb programs are rare nowadays. 

> See attached, i created 2 accounts on a old XP VM one account with the password "@sf5T7" and one with "aaaaaaaaaaaaaaa", using a popular and easy to use brute force tool cain & abel i dumped the local account hashes from the system and then set it to brute force them.

using all characters available in the predefined section and choosing 1 to 6 for the 6 and 1 to 15 for the 15 chr you can see the time taken to brute force is quite different for both.

like is said it depends what tool you use and what you know, in this example i assumed we didnt know the character composition so i chose to use all which is realistic, i chose the amount of characters simply because LM hashes for example are easily identifiable if below 7 characters which in this example it is as it is 6.

of course LM hashes are easier to crack than other types so the type of password also counts over the composition of it.

cheers

In a real world scenario, names, 1234,password,personal details and repetitive passwords are easily broken by intelligent breaker programs. Your best bet is to choose something semi-random, unconnected to you that is fairly long (at least 14 characters, preferably in upwards of 20)
contains lower and upper-case letters, numbers and symbols. Prime numbers are better, by the way. 

In the end, it comes down to this; "aaaaaaaaaaaa" or "tB$13" is broken more easily depending on the type of attack. Dumber programs will struggle with longer passwords, while smart programs will break the long ones with ease, if it's something obvious.

In any case, it doesn't matter to the OP as both passwords are awful.

---

### Post by haqking on 2012-03-26
> **0011235813 said:**
> No need to be pedantic please, it was an honest mistake. 


I understand what you're trying to say, but why did the poster have to use such an awful example?


I know it failed, the point is that it gave a different result to what the OP said. Oh and I'm not sure why Microsoft and grc is there.

Hmmm yes, simple six character passwords can be broken by a GPU accelerated smart password cracker in about... Two hours?


Yeah, you never know who might be in the middle, or how reputable the site is. For all you know, the site might have been compromised.


Of course, a dumb program would obviously struggle with really long passwords, but the sad truth is that modern day password breakers are smart and that is why a password like "maryannrose" (a.k.a the persons name) is fra more likely to be broken than $Ds27 as the hacker would obviously try the persons name. Pure bruteforce dumb programs are rare nowadays. 


In a real world scenario, names, 1234,password,personal details and repetitive passwords are easily broken by intelligent breaker programs. Your best bet is to choose something semi-random, unconnected to you that is fairly long (at least 14 characters, preferably in upwards of 20)
contains lower and upper-case letters, numbers and symbols. Prime numbers are better, by the way. 

In the end, it comes down to this; "aaaaaaaaaaaa" or "tB$13" is broken more easily depending on the type of attack. Dumber programs will struggle with longer passwords, while smart programs will break the long ones with ease, if it's something obvious.

In any case, it doesn't matter to the OP as both passwords are awful.

I think they were just demonstrating simple security concepts.

and the point made was the longer "aaaaaaaaaaaaaaa" is stronger than "@sf5T7" which indeed it is in a brute force attack which was the point made as you argued that it wasnt that was all.

and i wasnt being pedantic, we were talking about keyspace and entropy and so there is a big difference between "aaaaaaa" and "aaaaaaaaaaaaaaa" i appreciate your mistake but there is big difference for the context of that debate.

And Microsoft and GRC are there as they use fairly reliable algorithms for testing password strengths which is not much different to any other site which provides the same thing, you asked me to go to any other testing site which i did.

Cheers

---

### Post by Dangertux on 2012-03-26
A 6 character password like that? With GPU cracking? 2 hours? Try about 12 seconds.

Now here's the caveat... You have to spend 3 1/2 months using that same GPU technology to generate terabytes of rainbow tables.

Just saying...

---

### Post by 0011235813 on 2012-03-27
> **Dangertux said:**
> A 6 character password like that? With GPU cracking? 2 hours? Try about 12 seconds.

Now here's the caveat... You have to spend 3 1/2 months using that same GPU technology to generate terabytes of rainbow tables.

Just saying...

I was being optimistic I know... But it does depend on the GPU though, something like an nVidia GeForce GT430 will break it much slower than the GTX580...

---

### Post by Dangertux on 2012-03-27
I think you fail to realize how GPU hash cracking actually works...

So... Basically how it works is this...

Let's say we have an MD5 hash we want to crack...

```

$1$QyM8v.68$8izeYQjjvPxcqFDAcV4w70

```Then we have a table full of hashes and their plain text equivalent

```

$1$QyM8v.68$8izeYQjjvPxcqFDAcV4w70 password
$1$AN4EtW8G$318eO4B6xx/aOQLoeH8Qs1 happytime
$1$8rh54/pp$4f0imF1M7VgnBdIW5rHcC0 001235813
$1$92Hf90MK$WXVuRW1tgMlF8RYJNKVER0 dangertux

```and so on... For hundreds of thousands of comon passwords right?... Okay..

So we now use our GPU's accelerated ability to perform time / memory tradeoff operations to run through the list of hashes and compare our hash to be cracked with each hash. When it matches we have our plain text password So...


We have
```

$1$QyM8v.68$8izeYQjjvPxcqFDAcV4w70

[COLOR=Red]
$1$QyM8v.68$8izeYQjjvPxcqFDAcV4w70[/COLOR] password
$1$AN4EtW8G$318eO4B6xx/aOQLoeH8Qs1 happytime
$1$8rh54/pp$4f0imF1M7VgnBdIW5rHcC0 001235813
$1$92Hf90MK$WXVuRW1tgMlF8RYJNKVER0 dangertux

```So our password is...password...

That is how GPU hash  cracking works, it is not a brute force method. It relies on having the password hash already. Rainbowtables, hashcat, etc are really more like "dictionary" attacks then brute force, but slightly different.

The point is, that list must be generated, it takes an extremely long time to generate a complete list. It also takes an extremely large amount of disk storage to store it.

The caveat here, is these hashes are salted. see the value between the second and third $. So there are ultimately more possibilities...

For instance both of these are also possible values for password
```

$1$LShwhBnI$9uKfTf5p3UUB6PxPibmy1.
$1$pMh0PIS7$fSxP6CZiFDWl5rvcXLcjS/

```If you'd like to test this theory you can simply use the following command to generate an md5 hash string for use in a shadow file

```

openssl passwd -1 "password_to_be_encrypted"

```You can also observe the difference if a static salt is used 
```

openssl passwd -salt "blahblah" -1 "password"

```So you're essentially doing an attack against the password and salt itself.

Likewise you can try the same with SHA512 based hashes (what Ubuntu and most modern distros use)

```

$6$zLucq/PDnn0nNgOw$OivM5oYhyLQjtwoE17zvatj69bxJOyXMx1UHuDUi.Odye3qxPQyqfwXv/lV9AUBvDvh5QDe/K/8DsYS9VjHNG.

```

However you will need to use the mkpasswd or grub-crypt command to generate one.


Hope this helps.

---

### Post by Ms. Daisy on 2012-03-27
Fascinating- thanks DT!

---

### Post by 0011235813 on 2012-03-28
> **Dangertux said:**
> I think you fail to realize how GPU hash cracking actually works...

So... Basically how it works is this...

Let's say we have an MD5 hash we want to crack...

```

$1$QyM8v.68$8izeYQjjvPxcqFDAcV4w70

```Then we have a table full of hashes and their plain text equivalent

```

$1$QyM8v.68$8izeYQjjvPxcqFDAcV4w70 password
$1$AN4EtW8G$318eO4B6xx/aOQLoeH8Qs1 happytime
$1$8rh54/pp$4f0imF1M7VgnBdIW5rHcC0 001235813
$1$92Hf90MK$WXVuRW1tgMlF8RYJNKVER0 dangertux

```and so on... For hundreds of thousands of comon passwords right?... Okay..

So we now use our GPU's accelerated ability to perform time / memory tradeoff operations to run through the list of hashes and compare our hash to be cracked with each hash. When it matches we have our plain text password So...


We have
```

$1$QyM8v.68$8izeYQjjvPxcqFDAcV4w70

[COLOR=Red]
$1$QyM8v.68$8izeYQjjvPxcqFDAcV4w70[/COLOR] password
$1$AN4EtW8G$318eO4B6xx/aOQLoeH8Qs1 happytime
$1$8rh54/pp$4f0imF1M7VgnBdIW5rHcC0 001235813
$1$92Hf90MK$WXVuRW1tgMlF8RYJNKVER0 dangertux

```So our password is...password...

That is how GPU hash  cracking works, it is not a brute force method. It relies on having the password hash already. Rainbowtables, hashcat, etc are really more like "dictionary" attacks then brute force, but slightly different.

The point is, that list must be generated, it takes an extremely long time to generate a complete list. It also takes an extremely large amount of disk storage to store it.

The caveat here, is these hashes are salted. see the value between the second and third $. So there are ultimately more possibilities...

For instance both of these are also possible values for password
```

$1$LShwhBnI$9uKfTf5p3UUB6PxPibmy1.
$1$pMh0PIS7$fSxP6CZiFDWl5rvcXLcjS/

```If you'd like to test this theory you can simply use the following command to generate an md5 hash string for use in a shadow file

```

openssl passwd -1 "password_to_be_encrypted"

```You can also observe the difference if a static salt is used 
```

openssl passwd -salt "blahblah" -1 "password"

```So you're essentially doing an attack against the password and salt itself.

Likewise you can try the same with SHA512 based hashes (what Ubuntu and most modern distros use)

```

$6$zLucq/PDnn0nNgOw$OivM5oYhyLQjtwoE17zvatj69bxJOyXMx1UHuDUi.Odye3qxPQyqfwXv/lV9AUBvDvh5QDe/K/8DsYS9VjHNG.

```

However you will need to use the mkpasswd or grub-crypt command to generate one.


Hope this helps.
That was an interesting post Dangertux, but I'm not sure how it applies to what I said. I admitted to putting a somewhat over-optimistic value, but I said that how long it takes ultimately depends on the GPU- or more specifically- FLOPS (i.e compute power) although granted other factors like GPU architecture and vectorisation units will affect the outcome. Obviously a low end HTPC card is going to take longer than a dual-GPU monster like the '580.

---

### Post by DanR01 on 2012-03-28
```
Hmmm... Good idea. I use that, however, it does mistake me for someone else when I'm using Tor, so keep that it mind.
```

Correct me if I'm wrong but isn't using Tor to access your email a security risk? Couldn't a rogue exit node could sniff your login details?

---

### Post by 0011235813 on 2012-03-28
> **DanR01 said:**
> ```
Hmmm... Good idea. I use that, however, it does mistake me for someone else when I'm using Tor, so keep that it mind.
```

Correct me if I'm wrong but isn't using Tor to access your email a security risk? Couldn't a rogue exit node could sniff your login details?

Well if tor is compromised, they could sniff out just about anything. That's probably why using a VPN is a better idea- if you can find one that works in Ubuntu, that is (tried it, and failed) .

But in response to your question; tor is pretty secure, it's unlikely you'd have to worry about it.

---

### Post by haqking on 2012-03-28
> **0011235813 said:**
> Well if tor is compromised, they could sniff out just about anything. That's probably why using a VPN is a better idea- if you can find one that works in Ubuntu, that is (tried it, and failed) .

But in response to your question; tor is pretty secure, it's unlikely you'd have to worry about it.
> 
Correct me if I'm wrong but isn't using Tor to access your email a security risk? Couldn't a rogue exit node could sniff your login details?

Tor is not about security, it is about anonymity which are not the same thing.

And online communications are always susceptible to sniffing, session hijacking, client/server side compromise etc as far as email login is concerned, using Tor is not a method to increase security for online secure transactions or logins.

VPN's can help yes and i have never come across one that doesnt work.

you can get a good list here [http://www.vpnreviews.com/](http://www.vpnreviews.com/)

obviously the password issue has been discussed and links to wikis on security posted to help take steps towards a more secure browsing experience, the most effective being user awareness, common sense and education



Peace

---

### Post by emiller12345 on 2012-03-28
The OP might consider verifying that the gmail login webpage is actually SSL encrypted by clicking on the blue 'google.com' logo near the part where it says [https://accounts.google.com](https://accounts.google.com).  If the login is secured with ssl, it should say so. if it doesn't, don't enter your information.

---

### Post by haqking on 2012-03-28
> **emiller12345 said:**
> The OP might consider verifying that the gmail login webpage is actually SSL encrypted by clicking on the blue 'google.com' logo near the part where it says [https://accounts.google.com](https://accounts.google.com).  If the login is secured with ssl, it should say so. if it doesn't, don't enter your information.

Just to be pedantic it would be TLS now and not SSL, just for clarty as it may confuse the OP when they dont see SSL ;-)

Cheers

---

### Post by Dangertux on 2012-03-28
> **0011235813 said:**
> That was an interesting post Dangertux, but I'm not sure how it applies to what I said. I admitted to putting a somewhat over-optimistic value, but I said that how long it takes ultimately depends on the GPU- or more specifically- FLOPS (i.e compute power) although granted other factors like GPU architecture and vectorisation units will affect the outcome. Obviously a low end HTPC card is going to take longer than a dual-GPU monster like the '580.

To add to the pedantic nature of the last few posts, yes I understand that. But you misunderstood my point. To clarify --

If your hash isnt in the table it doesn't matter how fast the card is, it won't find your password. To put it into perspective, a set of rainbow tables with all possible hash values for passwords length 1-9 containing mixed alpha numeric characters (that's [A-Za-Z0-9] ) it takes approximately 864 GB of storage space That's ONLY for MD5 hashes, not SHA-1/2 or NTLM.

So I assure you, it is highly unlikely that a 15 character password of ANY type is in a common set of rainbow tables.

Just a thought.

---

### Post by 0011235813 on 2012-03-29
> **haqking said:**
> Just to be pedantic it would be TLS now and not SSL, just for clarty as it may confuse the OP when they dont see SSL ;-)

Cheers

Yes, TSL is the newer protocol. It should be 256-bit as well if the browser supports it. Since Gmail forcibly uses https (that's **h**yper-**t**ext **t**ransfer **p**rotocol **s**ecure for those of you who don't know) if a site looks like Gmail but doesn't have https, then it is almost certainly a fake.

---

