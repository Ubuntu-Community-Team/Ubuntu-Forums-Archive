---
title: "Self erase after entering wrong password a number ot imes"
date: 2014-12-27
forum: Security
---

### Post by kal2 on 2014-12-27
Hello,

I'm a newbie to ubuntu and linux in general. 

I am looking for a way to do at leas one of the following:

1- To have the the entire disk or the home folder erased after entering the wrong password a specific number of times.


2- Have my luks encrypted disk/usb self erase after entering the incorrect password a specific number ot imes.

I basically can not risk having the information accessed by a dermined agency/person and though I use a very strong password I would still be more comfortable having the data erased in it's encrypted form so that it is not in any wahy recoverable.


Doable?


Thanks

Kal

---

### Post by open2reason on 2014-12-27
Kal2,
Have you considered the physical safety of your machine? Are you the only one with access 24*7*365? if not then a determined agency/person may well have enough to ply their evil trades at the detriment of both your machine and your data.
An encrypted home folder with super secret data held upon a  luks encrypted usb might be worth considering as a "three goes then erase" could not be used by some to destroy your data just for fun or even triggered by you on a bad day.

I am sure others will be along with offerings of scripts to do just as you wish but at least consider keeping data on a usb memory and then only mounted when required.

---

### Post by Bucky Ball on 2014-12-27
Welcome. Use a ridiculously long and involoved alpha/numeric password that would be impossible to guess or crack. What I can't figure is, if they try three times and get it wrong, then they can't access your data anyhow. 

Before trying anything, backup your data. To get into your machine, let alone your data, the infiltrator will need to have (or fluke) your password in the first place.

I suppose one option would be to have your /home on a separate partition on an external drive which you can simply unplug and plug in only when you want to access the data. Encryption might be the best option, though, as suggested.

---

### Post by buzzingrobot on 2014-12-27
As Bucky said, anyone who fails to provide the correct password doesn't have access, so why wipe the drive at that point?

In any case, it could be done. Remember, though, that running rm recursively over a filesystem is not an instant process. 

That would not remove data from the drive. To try to reduce the ability of someone to recover that data, those areas of the drive need to be overwritten with something, like zeros. That can take a substantial amount of time.

A machine that is not on the network is safe from attack over the network. Access to a machine someone has physically acquired is wide open, limited only by their skills and resources.

---

### Post by HermanAB on 2014-12-28
Self erase is a good description of the problem. As your data is encrypted, all you need to do is hit yourself upside the head with a brick to forget the password.

---

### Post by bashiergui on 2014-12-28
Pretty sure this is what you're really asking for
[http://hackaday.com/2008/09/16/how-to-thermite-based-hard-drive-anti-forensic-destruction/](http://hackaday.com/2008/09/16/how-to-thermite-based-hard-drive-anti-forensic-destruction/)

---

### Post by kal2 on 2014-12-28
> **bashiergui said:**
> Pretty sure this is what you're really asking for
[http://hackaday.com/2008/09/16/how-to-thermite-based-hard-drive-anti-forensic-destruction/](http://hackaday.com/2008/09/16/how-to-thermite-based-hard-drive-anti-forensic-destruction/)

After a bit of research it looks like this is exactly what I need! 


The idea is that if my laptop or pc is stolen for the purpose of getting to the information on it they perpetrators would do everything possible to crack the password and though I have a VERY strong password I would rather just have the whole drive erased (actually destroyed) to riskiing the password getting cracked.
But now I'm aware that erasing a disk means rewriting the whole thing which could take hours. I also read something that I don't quite understand. Someone who's trying to extract infromatin from the disk would not try to enter the password but would take an image of the disk and then try cracking that. So in reality "bashiergui" solution is the only one satisfactory!

Out of curiousity, if I have a password of say 50 characters that include everything psossible in it, what would it take to crack it?

---

### Post by kal2 on 2014-12-28
I also thought of something like truecrypt or veracrypt where the decoy system would start while erasing the hidden partition. But again that would work with amateurs not so with pros.

---

### Post by Balzy on 2014-12-28
**How secure a 50 characters passphrase is? **
With even a shorter password, given computational power available today even to big corporations or governments, a brute force attack would probably produce results after our Sun has died. Of course computational power grows exponentially at passing of time but even considering this fact your data would still be secure.

* _Note that:_ You are still vulnerable to social engineering, keyloggers, court orders, torture... etceter*a.


** About wiping your hard-drive:**
A professional analyst would never put your drive in a computer and type a password he believe to decrypt data on it. He would first of all make a backup copy of the drive and then scan it or decrypt it with some appropriate tools. He would never use your patched "password checker" that wipes anything after 3rd failed attempt. This is also why having a nuke password with LUKS header (a second password that erase LUKS header instead of decrypting data) is useless unless you can trigger such a function before your drive is backupped.

Example: You have your laptop in your suitcase containing informations more valuable than your own life. You are threatened to unlock it. You simply write the nuke password and wipe out encryption keys making data recovery even harder. Encryption won't stop a bullet and save your a**, but data will be "safer".

Anyway forget those "secret agent" scenarios, if that was the case you wouldn't be seeking advice here ;)


I read tons of topics/question around the Internet saying "What if NSA steals my laptop..." "Is ### algorithm strong enough to protect me against..."
Understanding encryption limits and how strongly sensible data can be protected is a good thing. But please keep in mind you're out in the real world, not in a crypto nerd world and people won't ask gently for a password if you are suspected of terrorism (just an example).

[IMG]http://imgs.xkcd.com/comics/security.png[/IMG]

Hope I've given you a better understanding of cryptography limits. Don't think it's useless, a strong encryption algorithm and a strong key are always needed to protect data, but there's more than that. Don't get stuck on it more than necessary.

If anybody else wants to say something more or correct me, feel free to reply, I'd like to discuss about this topic.

---

### Post by bashiergui on 2014-12-28
> The idea is that if my laptop or pc is stolen for the purpose of getting to the information on it they perpetrators would do everything possible to crack the password...Really? Is that realistic? What you have on your computer is so valuable or incriminating that "They" would try cracking it until the death of the universe. *Really*? 

Or is it more likely that information you encrypt with a reasonable algorithm (say aes256, LUKS) using a reasonably strong passphrase will be useless 1s and 0s for anyone that might care about your data.

I encourage you to educate yourself about encryption, how it works, and how/if it gets cracked. Don't waste your time defending against an imaginary threat, especially if you aren't defending against low-level, boring, basic threats.

---

### Post by kal2 on 2014-12-29
Thanks for the poor effort to reply to my questions. A weird thing about every single discussion forum on the entire Web is that it attracts losers. Next time just answer the questions instead of trying to read people's minds.

The woods are lovely dark and deep but I have promises to keep.

---

### Post by Elfy on 2014-12-29
and .... 

that's just about enough of that, next time you go to the woods have a thought about what people are actually telling you

if you are that concerned about data being found by others I'll have to assume you've hundreds of accounts asking the same question on hundreds of forum's - see if they'll put up with the snarky attitude.

Closing this - don't start new threads for the same issue - they'll be closed

---

