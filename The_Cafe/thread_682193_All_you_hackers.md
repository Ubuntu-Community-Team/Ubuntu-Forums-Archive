---
title: "All you hackers"
date: 2008-01-29
forum: The Cafe
---

### Post by cartisdm on 2008-01-29
Ok so while at work today I was making fun of a co-worker by using the "Windings" font and typing stuff like "I'm gay, I should be doing my work" so that he would paste it into word and see what it said after changing the font etc.

Anywho, he's one of the developers/programmers and decided he'd get smart with me and emailed me this:

> If you can break this encrypted message, I’ll give you $5:

&#9618;Ä&#9508;&#945;&#9556;Çƒò&#8801;ú&#9572;&#9580;&#9576;ç&#9488;&#945;&#9555;&#9554;ôï&#8801;&#9571;&#9600;&#9554;éô&#9569;¼&#9555;ü

Important hints:

XOR encryption algorithm

Key is only 6 characters in length.  The upper four bits of the first byte in the sequence = 1111.

I tried googling how to crack XOR but I didn't get anywhere lol.  He told me I have till Friday, any help?

---

### Post by ~LoKe on 2008-01-29
Don't even try.  You can't crack XOR.

---

### Post by hhhhhx on 2008-01-29
sorry, but you don't have a chance cracking XOR. :(

---

### Post by Joeb454 on 2008-01-29
If it works like gpg does, then you'll need his public key to decrypt the message ;)

---

### Post by cartisdm on 2008-01-29
> **~LoKe said:**
> Don't even try.  You can't crack XOR.

Really? From what I could find with a little research it seemed like there's a technique/formula for it.  Of course, that's easy for me to say I have no idea how to even attempt at it lol

---

### Post by ~LoKe on 2008-01-29
> **cartisdm said:**
> Really? From what I could find with a little research it seemed like there's a technique/formula for it.  Of course, that's easy for me to say I have no idea how to even attempt at it lol

If there is, I'd like to know it.  As far as I know. XOR is more secure than md5 and sha1 combined.

---

### Post by xzero1 on 2008-01-30
If the key used to create the a true (simple) XOR encryption is sufficiently random and
of sufficient length then the only way to 'crack it' is by brute force. Even then one would get many plain text 'decryptions' and never know which was correct. Indeed, it has been proven impossible to crack. The only problem with XOR is if the key is used more than once and the encrypted text is known then it is trivial to crack -- by XOR ing the encrypted texts.

---

### Post by LaRoza on 2008-01-30
> **xzero1 said:**
> If the key used to create the XOR encryption is sufficiently random and
of sufficient length then the only way to 'crack it' is by brute force. Even then one would get many plain text 'decryptions' and never know which was correct. Indeed, it has been proven impossible to crack. The only problem with XOR is if the key is used more than once and the encrypted text is known then it is trivial to crack -- by XOR ing the encrypted texts.

@OP Tell whoever sent you this that you accidently deleted it, and ask for a new one to solve with the same key. Hopefully, you'll get a different message. Social engineering: It works.

---

### Post by meborc on 2008-01-30
> **LaRoza said:**
> @OP Tell whoever sent you this that you accidently deleted it, and ask for a new one to solve with the same key. Hopefully, you'll get a different message. Social engineering: It works.

thats good thinking :D

---

### Post by scorp123 on 2008-01-30
> **~LoKe said:**
> Don't even try.  You can't crack XOR. Huh? From which parallel universe are you? XOR is simple and stupid.

---

### Post by scorp123 on 2008-01-30
> **~LoKe said:**
>  XOR is more secure than md5 and sha1 combined. I am sorry to say but in that case I have to question your knowledge. Your claims are not true. Simple as that.

---

### Post by LaRoza on 2008-01-30
> **scorp123 said:**
> Huh? From which parallel universe are you? XOR is simple and stupid.

Yes, it is a weak way to encrypt and easy to decrypt. Easy is relative here.

I will work on it now, it is 0349 now.

---

### Post by scorp123 on 2008-01-30
> **cartisdm said:**
>  I tried googling how to crack XOR but I didn't get anywhere lol.  He told me I have till Friday, any help? He already gave you tons of hints there. And as for Googling ... I don't know what you entered as search argument but my first attempt came up with this:

[http://www.tech-faq.com/xor-encryption.shtml](http://www.tech-faq.com/xor-encryption.shtml)

Quote from there: "XOR encryption is trivially simple to implement and equally trivial to break. XOR encryption should not be utilized for any data which you would want to protect."

Read the example they give on that page. Your programmer there gave you an important hint: The first bits are = 1111 .... Look at the example, XOR isn't that hard. Most important is this: It's symmetric. Different than more sophisticated methods the same key that encrypted the message can also decrypt it again.

EDIT:

Wikipedia has a nice example of XOR decryption:
[http://en.wikipedia.org/wiki/Simple_XOR_cipher](http://en.wikipedia.org/wiki/Simple_XOR_cipher)

---

### Post by scorp123 on 2008-01-30
> **cartisdm said:**
> 
```
&#9618;Ä&#9508;&#945;&#9556;Ç&#402;ò&#8801;ú&#9572;&#9580;&#9576;ç&#9488;&#945;&#9555;&#9554;ôï&#8801;&#9571;&#9600;&#9554;éô&#9569;¼&#9555;ü
```

Important hints:
XOR encryption algorithm

Key is only 6 characters in length. The upper four bits of the first byte in the sequence = 1111.   Something is not entirely consistent here. Let's take the first character up there: ```
 &#9618; 
```

And now let's look at the codes for "Codepage 437", because guessing from the characters up there that's what's being used here, plain old 8-bit ASCII characters from the US character table:
[http://en.wikipedia.org/wiki/Code_page_437](http://en.wikipedia.org/wiki/Code_page_437)

According to that page this character has the decimal value of 177. In binary notation that's 10110001 ...

But we're talking XOR here. For details:
[http://en.wikipedia.org/wiki/Simple_XOR_cipher](http://en.wikipedia.org/wiki/Simple_XOR_cipher)

And your friend claims that the key only has 6 characters and that the first bits of the decrypted character are "1111...." ...  so the key should be something like 111000 (= six. characters length) ... But if we apply that to the encrypted character and follow the rules of XOR (1+0=1; 0+0=0; 1+1=0) we get: ```
 
1[COLOR="Red"]0[/COLOR]110001 <= Encrypted character
0[COLOR="Red"]0[/COLOR]111000 <= key (based on assumption; 6 bits length as suggested in the hints)
------------------
1[COLOR="Red"]0[/COLOR]001001 <= decrypted character ... 

... which can't match the pattern given in the hints ("first bits: 1111 ...")
``` See the characters I marked in red? Your friend said the first decrypted character would start with "1111....". And because both the first bit of the encrypted and decrypted character is 1, so the key underneath has to be 0 if we follow the XOR rules (XOR: 1+0=1). So far so good. But the next bit of the encrypted character is 0 ... but your friend said that the first bits of the decrypted character would be "1111" ... In order to get that the next bit of the key would have to be 1 now (XOR: 1+0=1! 0+0=0! 1+1=0!) But your friend also said the key is only six characters in length, which means something like "111000" which technically is the same as "00111000" (we just add leading zeros, the number, the value and its length remain the same). But with an encrypted character that starts with 10110001 and where the decrypted character is supposed to read "1111...."-something the key can't have two leading zeros, e.g. it can't be only six characters in length ("00 something"), the key must be longer in this case and start with "0100..." or else we won't get four 1's ("1111") in the decrypted character.

Either I understood something wrong here, or the hints your friend gave you aren't exactly precise :)

What we should get is this:```
 
[COLOR="Red"]1011[/COLOR]0001 <= Encrypted character
[COLOR="Red"]0100[/COLOR]???? <= unknown key
------------------
[COLOR="Red"]1111[/COLOR]???? <= decrypted character ... 
```

As I said ... something isn't entirely right here. Or someone please kick me in the head and tell me where my error is :)

---

### Post by quanumphaze on 2008-01-30
> **scorp123 said:**
> so the key should be something like 111000 (= six. characters length)

I think it would make more sense if you interpreted "six characters" as 6 ASCII characters ie: 6 bytes.

I assume the six byte key would be used byte by byte for the first 6 chars then repeats for the next 6 chars.

To try the first char

```
    10110001 <= Encrypted character
    1111???? <= Unknown 1st byte of key
=   0100????
```
Leaving a possibility of 16 chars. Some may be numbers or symbols and safe to exclude.

This key byte should be usable for every 6 chars of the message.

I could do more but it's 12:14p and I'm getting illiterate.

Happy hacking

---

### Post by cartisdm on 2008-01-30
I'm loving all the response I'm getting for this:)  I'll check back with it more when I have more time this afternoon

---

### Post by scorp123 on 2008-01-30
> **quanumphaze said:**
> I think it would make more sense if you interpreted "six characters" as 6 ASCII characters ie: 6 bytes. I thought of this too ... But remember: This is kind of a prank, a joke between colleagues. We're talking about a $5 competition (what's that? A coffee and a sandwich in the coffee shop around the corner?) and not a $50000 competition where you'd encounter some really nasty crypto stuff. So with this in mind I therefore thought he wouldn't really use a 6 byte long key ... that would be a 48-bit key, and the information that the first bits of the first decrypted character are "1111...." would then be kind of pointless.

Nope ... I am sure it's something simple. We're just not seeing it at the moment.

I once challenged one of my apprentices in a similar manner by taking text and inverting the byte order ... e.g. The letter "A" has the number 41hex in the ASCII table, and if you twist the numbers around you get "14" in hex. The letter "m" (D6) then becomes "Ö" (6D) and so on. Simple and stupid.

Having played such jokes myself I am sure it must be something similarly simple here :)

---

### Post by ~LoKe on 2008-01-30
Ah, that's my mistake.  I didn't read the entire post and didn't see the hints.  But good luck anyways...

---

### Post by Luggy on 2008-01-30
XOR is simple but you will probably have to do some brute forcing to figure the key out. I'll see if I can whip up a little hack to get'er done.

```

char crypt;
// assign crypt to some value
char key;
// guess what key may be
char awns = crypt^key;
// viola!

```

However, you wouldn't have to brute force all 30 characters, just the first 6 ( the size of the key ). What I would probably do us try and find a key that makes the first 6 characters make sense, once you have that it will probably crack the rest of the code.

---

### Post by popch on 2008-01-30
> **Luggy said:**
>  What I would probably do us try and find a key that makes the first 6 characters make sense, once you have that it will probably crack the rest of the code.

Since the decoding is so simple and the plaintext only 30 chars, I would decode all of the text at once. This give many more clues at the same time and greatly saves on user's time.

Don't forget that the first four bits of the key are known, anyway, and that with a bit of luck the key itself could be a short 'plaintext'.

---

### Post by cartisdm on 2008-01-30
I'm glad you all know what your doing because this went over my head about 10 posts ago haha.  It's pretty interesting though, keep it up:D

---

### Post by Lostincyberspace on 2008-01-30
Well there are only so many 6 letter words (about [SIZE=-1]19000 to give an estimate[/SIZE]) in the English language you could brute force it pretty quickly with a script. And taking the 19000 if One was tried each second it would take a about 5 hours to crack it. If I was better at scripting I would go ahead and even create the script for you but I don't know how to script well yet. and since it is so small it could probably be done in an hour on an above average (dual core  gig of ram). And XOR is really not that hard to crack.

I will get the list of words and put it up in a text just give me a second.

---

### Post by Lostincyberspace on 2008-01-30
Here is the list it is from the sowpods dictionary for scrabble it should have the pass key in here even though it is only about the eighth the size of the above mentioned number.

---

### Post by isparkes on 2008-01-30
I swore I wouldn't get involved in this, but...

"XOR encryption" is as simple or as hard as the thing the data is encrypted with. If you take a string, and XOR encrypt it with a number of truly random bytes (one byte of random data for each each byte of string), there is no way or recovering it, as all solutions are equally possible. This is the classic "one time pad", which gives you no attack points whatsoever.

Basically XOR is not an algorithm, it's a bit level operation that is at the heart of every encryption algorithm. It is special in that it is reversible.

Even with social engineering, (getting a second message) and XORing the two results together, you'll still have to perform analysis on the results to pick apart the two messages. He could use a different key, and in this case you are no nearer the result. Probably, the guy will send you the same message again, and XORing them together will give you a series if 0s.

If you break it, I'll give you $10... ;)

---

### Post by saulgoode on 2008-01-30
> **isparkes said:**
> If you break it, I'll give you $10... ;)

I broke it. Do I get $10? :)

---

### Post by popch on 2008-01-30
> **isparkes said:**
>  If you take a string, and XOR encrypt it with a number of truly random bytes (one byte of random data for each each byte of string), there is no way or recovering it, as all solutions are equally possible. 

In this case the key is only 6 bytes, hence 5 times repeated. One half of one byte of the key is already known, and one might speculate that the key is not any old random number but a string. Not in the same league as XORing with a one time pad.

---

### Post by aimran on 2008-01-30
You nerds!!!111

/tinfoilhat 

:)

---

### Post by cartisdm on 2008-01-30
> **aimran said:**
> You nerds!!!111
 

:)

Helpful....lol.  Anywho, my deadline has been shortened to Thursday because I won't be in the office on Friday:D

As for the trial/error method of using a script, how possible/likely would that be? (I can't script so I would need outside assistance:))

---

### Post by Fixman on 2008-01-30
You can brute force all 6 byte keys and check if all bytes of the result are alphanumeric. It will be like 10 mins to decrypt, but will be worth it.

---

### Post by cartisdm on 2008-01-30
> **Fixman said:**
> You can brute force all 6 byte keys and check if all bytes of the result are alphanumeric. It will be like 10 mins to decrypt, but will be worth it.

Anyone willing to help a brotha out?  I'd be happy to give them the $5 reward haha (via paypal) I only care about rubbing it in my friends face:KS

---

### Post by Kvark on 2008-01-30
With 6 lines of code I got good enough results to understand what the message says and after some manual adjustments I got the exact key and message. I'm half tempted to write a function that does the adjustments automatically by comparing the possible solutions to a spell check dictionary even though it's no longer needed.

The code is in code page 437 encoding so make sure you use that encoding. The plain text message contains only ASCII letters, space and punctuation so any keys that produce other characters need not be checked.

Should I post the solution or more hints?

---

### Post by Lostincyberspace on 2008-01-30
I would just post the script here in a txt file and let others decide if they want it.

---

### Post by saulgoode on 2008-01-30
> **cartisdm said:**
>  I only care about rubbing it in my friends face:KS

Send him the following reply:

&#9619;òñ&#945;&#9567;&#9556;äê&#9569;&#945;öò&#9604;&#9492;Ö&#945;&#9561;&#9524;&#8359;&#9492;&#9474;í&#9604;&#9568;&#9576;Ö&#9488;&#9569;&#9516;Ç¥Å&#9564;&#8712;èë

---

### Post by cartisdm on 2008-01-30
> **saulgoode said:**
> Send him the following reply:

&#9619;òñ&#945;&#9567;&#9556;äê&#9569;&#945;öò&#9604;&#9492;Ö&#945;&#9561;&#9524;&#8359;&#9492;&#9474;í&#9604;&#9568;&#9576;Ö&#9488;&#9569;&#9516;Ç¥Å&#9564;&#8712;èë


Haha, do I dare ask what is says?

---

### Post by cartisdm on 2008-01-30
> **Kvark said:**
> With 6 lines of code I got good enough results to understand what the message says and after some manual adjustments I got the exact key and message. I'm half tempted to write a function that does the adjustments automatically by comparing the possible solutions to a spell check dictionary even though it's no longer needed.

The code is in code page 437 encoding so make sure you use that encoding. The plain text message contains only ASCII letters, space and punctuation so any keys that produce other characters need not be checked.

Should I post the solution or more hints?

I'd love to see the script run if you have it available, can you post it?  How would I run the program?

---

### Post by Kvark on 2008-01-30
> **Lostincyberspace said:**
> I would just post the script here in a txt file and let others decide if they want it.
Okay here it is, read it for instructions, run it as an executable or with python to try it.

I added a way to get the correct message out of it by editing one line (the message = "guess" line) and trying again.

---

### Post by cartisdm on 2008-01-30
I wasn't quite sure how to run it correctly (even with the documentation lol sorry..) So I ran this in a terminal:

```
dan@dan:~$ cd /home/dan/Desktop
dan@dan:~/Desktop$ python crackxor.py

```

It printed out the message (with a few slight errors) how can I run it with the "?" corrections? I tried using "Open with" and using Python but I couldn't find that listed.  Obviously I got the hidden message:redface: but I'd like to see more of the script

---

### Post by Kvark on 2008-01-30
> **cartisdm said:**
> I wasn't quite sure how to run it correctly (even with the documentation lol sorry..) So I ran this in a terminal:

```
dan@dan:~$ cd /home/dan/Desktop
dan@dan:~/Desktop$ python crackxor.py

```

It printed out the message (with a few slight errors) how can I run it with the "?" corrections? I tried using "Open with" and using Python but I couldn't find that listed.  Obviously I got the hidden message:redface: but I'd like to see more of the script
Open it with your favourite text editor to read and edit it.

---

### Post by cartisdm on 2008-01-30
Got it thanks:D  I keep getting the list out of range error but I'm sure I'll figure it out

I'll be sure to post with what my friend says tomorrow

Edit:

It's still odd that no matter how many times I replace characters with different guesses I get that error.  And for the obvious letters that are wrong by replacing them all with "?" nothing of the message prints any different than the original.

---

### Post by scorp123 on 2008-01-30
> **Kvark said:**
> Okay here it is, read it for instructions, run it as an executable or with python to try it.

I added a way to get the correct message out of it by editing one line (the message = "guess" line) and trying again. Niiiiiiiice :)

---

### Post by Kvark on 2008-01-30
> **cartisdm said:**
> Got it thanks:D  I keep getting the list out of range error but I'm sure I'll figure it out

I'll be sure to post with what my friend says tomorrow

Edit:

It's still odd that no matter how many times I replace characters with different guesses I get that error.  And for the obvious letters that are wrong by replacing them all with "?" nothing of the message prints any different than the original.
Here is a version that tells you which characters it can't find any possible keys for, it should help with figuring out which part of your guess that is wrong.

---

### Post by macogw on 2008-01-30
> **scorp123 said:**
> But your friend also said the key is only six characters in length, which means something like "111000" which technically is the same as "00111000" (we just add leading zeros, the number, the value and its length remain the same). 
Not necessarily.  In 2s complement binary, negative numbers start with 1, so 00111000 is definitely NOT the same as 11111000.

00111000 = a positive number... 56
11111000 = a negative number... -8

---

### Post by popch on 2008-01-30
> **scorp123 said:**
> Or someone please kick me in the head and tell me where my error is :)

The key is 6 characters long. That's 6 Bytes, not 6 bits.

---

### Post by \Oo._.oO/ on 2008-01-30
> **Kvark said:**
> Here is a version that tells you which characters it can't find any possible keys for, it should help with figuring out which part of your guess that is wrong.

Nice script. Gives pretty accurate results just by guessing the 1st char from 0100????...

---

### Post by scorp123 on 2008-01-30
> **macogw said:**
> Not necessarily.  In 2s complement binary, negative numbers start with 1, so 00111000 is definitely NOT the same as 11111000. I definitely didn't say that! :)  All I am saying is that whether I write it "100" or "00100" or "000000100" ... it's always the same: 100. Leading zeros to fill up the "empty" space don't hurt. Let's not get each other wrong ... I was assuming (wrongly it seems) that this encryption thing is "simple", e.g. I assumed the key is only 6 bits .... and not 6 bytes long = 48 bit (major difference :)  )

> **macogw said:**
>  00111000 = a positive number... 56
11111000 = a negative number... -8  I am perfectly aware of that ;)

---

### Post by scorp123 on 2008-01-30
> **popch said:**
> The key is 6 characters long. That's 6 Bytes, not 6 bits. Yeap, I indeed misinterpreted the information that was given.

---

### Post by sefs on 2008-01-30
Well?

What was the message?

---

### Post by scorp123 on 2008-01-30
> **sefs said:**
>  What was the message? Something very impolite ... probably not appropriate for this forum. As you may remember, the thread starter had written a message saying "I'm gay, I should be doing my work" ... so the encrypted response he got is along those lines. It basically describes the function of vacuum cleaners (yes, the verb starts with "s....") and the related activity one might do to oneself if one were to immitate such a device :lolflag:

(I hope I described it polite enough and the admins here won't delete the posting? :) )

---

### Post by LaRoza on 2008-01-30
> **scorp123 said:**
> Something very impolite ... probably not appropriate for this forum. As you may remember, the thread starter had written a message saying "I'm gay, I should be doing my work" ... so the encrypted response he got is along those lines. It basically describes the function of vacuum cleaners (yes, the verb starts with "s....") and the related activity one might do to oneself if one were to immitate such a device

(I hope I described it polite enough and the admins here won't delete the posting? :) )

I am sure we get the message.

Now send your friend a bunch of gibberish (make it up) and tell him you'll give him a lot of money or something if he can figure out what it says. He'll spend hours.

---

### Post by scorp123 on 2008-01-30
> **LaRoza said:**
>  Now send your friend a bunch of gibberish (make it up) and tell him you'll give him a lot of money or something if he can figure out what it says.  ```
cat /dev/urandom > encrypted_message.txt
``` ... As soon as you think the message is big enough, hit Ctrl-C.

He will spend the next few trillions of years trying to "decrypt" this random nonsense :lolflag:

Oh and yeah .... The key: It's based on the number "Pi" (3.141592 ...). It's the 128'000th - 128'006th numbers after the comma ... :)  It will take him hours to calculate "Pi" and find those numbers. Of course it's all a lie. :)

But hey ... he doesn't need to know, right? :lolflag:

---

### Post by LaRoza on 2008-01-30
> **scorp123 said:**
> 
But hey ... he doesn't need to know, right? 

Of course not :)

---

### Post by macogw on 2008-01-31
> **scorp123 said:**
> I definitely didn't say that! :)  All I am saying is that whether I write it "100" or "00100" or "000000100" ... it's always the same: 100. Leading zeros to fill up the "empty" space don't hurt. Let's not get each other wrong ... I was assuming (wrongly it seems) that this encryption thing is "simple", e.g. I assumed the key is only 6 bits .... and not 6 bytes long = 48 bit (major difference :)  )

 I am perfectly aware of that ;)

But leading zeros *don't* fill up the space on the left in 2s complement (and 1s complement as well, I think--but 1s complement is yicky because it has two different ways to write zero) binary.  2s complement is the form of binary used in computers because it is very easy to implement in hardware.  If the front-most bit is a 1, you get leading 1s.  So then

1111111000
11111111111111000
1000

those three all mean the same thing.  Flip the bits to: <a bunch of zeros>0000111 then add 1 and you get <a bunch of zeros>0001000, which is 8, so it means that 1111111111111000 (no matter how many ones in the front) is negative 8.

Whatever the far left bit is is what fills in the rest on the left.  If you do a bit-shift (in C it's not uncommon to do a >> 4 which shifts 4 bits left, so divides by 16), the front gets filled in with whatever the left-most bit was.  If a zero was on the left, you get more zeros filling in the new spots on the left.  If a one was there, you get more ones.

---

### Post by ryanVickers on 2008-01-31
My basic logic is that any encryption can be inevitably hacked, but it may take almost an eternity in some cases :p

---

### Post by ryanVickers on 2008-01-31
> **scorp123 said:**
> Oh and yeah .... The key: It's based on the number "Pi" (3.141592 ...). It's the 128'000th - 128'006th numbers after the comma ... :)  It will take him hours to calculate "Pi" and find those numbers. Of course it's all a lie. :)

Your kidding right? I calculated 1 million digits in under 20 seconds... :lolflag:

---

### Post by DjBones on 2008-01-31
under ten over here :wink:

---

### Post by Lostincyberspace on 2008-01-31
[SIZE=-1]0.08 seconds here. if you can figure out how I did it I will give you a farthing for each of the numbers.
[/SIZE]

---

### Post by scorp123 on 2008-01-31
> **ryanVickers said:**
> Your kidding right? I calculated 1 million digits in under 20 seconds... :lolflag: Yeap, I missed a few zeros there. But hey, you understood what I meant. :)

And no matter how many or how few seconds it took him .... you can't "decrypt" the nonsense in the text file. One might as well claim "The key is Stacey's phone number ... You know Stacey, the cute blonde from 2nd floor ... Oh you don't? Oh well ... you will have to find out her phone number then ... "   <== if the other guy is a classic geek or a nerd (= not exactly the guy who "normal" ladies would want to give their phone numbers to ....) he's probably in trouble now ... :D  (note to thread starter: Don't forget to record that and put it on YouTube ... )  :D

---

### Post by cartisdm on 2008-01-31
Thanks for everyone's help that pitched in:)  It was worth the laughs around the office today haha.

Here's the key he used:
> 0xF0, 0xE0, 0xD0, 0xC0, 0xB0, 0xA0

---

### Post by ryanVickers on 2008-01-31
> **DjBones said:**
> under ten over here :wink:

I just timed it; 7.67 seconds to be precise, and that's including the delay of displaying it all ;)

---

### Post by Eth3real on 2008-02-04
I know this thread is dead, but I'm going to ask, anyway.
I have the hex value of a password written in XOR cipher. 
904EEEA756EABAE614C2D7823012F0197365
How can I run the hex value through that script?
I am really not that familiar with Python, so any help will be greatly appreciated.

Thanks!

---

### Post by cartisdm on 2008-02-05
I don't have a clue when it comes to this stuff but hopefully you'll get the same response I did when I posted it.  I was surprised everyone was able to get what they got

---

