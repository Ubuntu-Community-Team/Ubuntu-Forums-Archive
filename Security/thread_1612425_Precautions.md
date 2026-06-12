---
title: "Precautions?"
date: 2010-11-03
forum: Security
---

### Post by Yezinki on 2010-11-03
What are the generally recommended safety precautions on a Ubuntu variants/ Linux distro machine...like firewalls, ports, malware etc?

Thanks.

---

### Post by CharlesA on 2010-11-03
It would depend on if you are running a regular desktop or a server.

---

### Post by HermanAB on 2010-11-03
Howdy,

The single most important Linux security measure is to use at least a 9 character (with complexity) or 12 character (without complexity) password for all user accounts.

---

### Post by Grenage on 2010-11-03
> **Yezinki said:**
> What are the generally recommended safety precautions on a Ubuntu variants/ Linux distro machine...like firewalls, ports, malware etc?

Thanks.

Generally:

A good password.
If using SSH, use keys or very good passwords.
If using a desktop, stop remote desktop access from autostarting (it's ridiculous that it does by default).
Don't install code from untrusted sources (ubuntu repos = good, bustyasians.com = bad).
Always use a firewall; if your router has one, perfect.  UPnP enabled only if you really need it.
Don't enable the root account, and don't use root rights unless required.
Don't install software you'll never use - simple is easier to secure than complicated.

---

### Post by msandoy on 2010-11-03
> **Grenage said:**
> Generally:

A good password.
If using SSH, use keys or very good passwords.
If using a desktop, stop remote desktop access from autostarting (it's ridiculous that it does by default).
Don't install code from untrusted sources (ubuntu repos = good, bustyasians.com = bad).
Always use a firewall; if your router has one, perfect.  UPnP enabled only if you really need it.
Don't enable the root account, and don't use root rights unless required.
Don't install software you'll never use - simple is easier to secure than complicated.

Good advice, maybe this could be an idea for a quick and easy sticky for the beginners section. :-)

---

### Post by CharlesA on 2010-11-03
> **msandoy said:**
> Good advice, maybe this could be an idea for a quick and easy sticky for the beginners section. :-)

There's already a [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") somewheres.

---

### Post by Megaptera on 2010-11-03
I particularly like  
> **Grenage said:**
> Generally:
Don't install code from untrusted sources (ubuntu repos = good, bustyasians.com = bad).
.

---

### Post by Yezinki on 2010-11-03
Thanks for your replies highly appreciated

I'm an old retired MD using a desktop.

1. Could yo care to post an example of a good password?

2. Whats SSH?

3. How do I enable a firewall?

4. Don't enable the root account, and don't use root rights unless required....how do I do that?

Best Regards!

---

### Post by CharlesA on 2010-11-03
> **Yezinki said:**
> Thanks for your replies highly appreciated

I'm an old retired MD using a desktop.

1. Could yo care to post an example of a good password?

2. Whats SSH?

3. How do I enable a firewall?

4. Don't enable the root account, and don't use root rights unless required....how do I do that?

Best Regards!

1. A good password 10-15 characters in length (or more) that have upper and lowercase letters, numbers, and symbols.

2. SSH = Secure SHell, you have to install it as it isn't installed by default on either the Desktop or Server edition.

3. You can enable the firewall by running this:

```
sudo ufw enable
```

4. The root account is disabled by default in Ubuntu, so you don't have to worry about it. You use sudo to do admin tasks.

---

### Post by Yezinki on 2010-11-03
Thanks CharlesA,

1. How do I install SSH?

2, 10-15 characters.........ppbb705634abc.........like this?

Best Regards!

---

### Post by CharlesA on 2010-11-03
> **Yezinki said:**
> Thanks CharlesA,

1. How do I install SSH?

2, 10-15 characters.........ppbb705634abc.........like this?

Best Regards!

1. If you want it installed, it's just an apt-get away:

```
sudo apt-get install ssh
```

Keep in mind that it'll be listening on port 22 by default. It's not really secured by default, so you'd have to secure it after installation - read the security sticky for more info.

2. Something like that. I use KeePassX to generate passwords.

---

### Post by Grenage on 2010-11-03
ssh is for connecting to the machine remotely.  If you have no need, don't install it.

---

### Post by Yezinki on 2010-11-03
Thanks Grenage & CharlesA,

Btw whats KeePassX?

Regards!

---

### Post by CharlesA on 2010-11-03
> **Yezinki said:**
> Thanks Grenage & CharlesA,

Btw whats KeePassX?

Regards!

Password manager. [www.keepassx.org/](www.keepassx.org/)

It might be in the repos, but I don't know.

---

### Post by Yezinki on 2010-11-03
How do i install it?

---

### Post by CharlesA on 2010-11-03
> **Yezinki said:**
> How do i install it?

Looks like you'd have to add their PPA.

Check [here]("http://www.keepassx.org/downloads/") and [here]("https://launchpad.net/~keepassx/+archive/ppa").

Basically you'd need to add it like so:

```
sudo add-apt--repository ppa:keepassx/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install keepassx
```

---

### Post by Soul-Sing on 2010-11-03
> **Yezinki said:**
> How do i install it?

maybe via a PPA: [https://launchpad.net/~keepassx/+archive/ppa](https://launchpad.net/~keepassx/+archive/ppa)

---

### Post by mainerror on 2010-11-03
> **HermanAB said:**
> Howdy,

The single most important Linux security measure is to use at least a 9 character (with complexity) or 12 character (without complexity) password for all user accounts.

12 characters without complexity is not as secure as 9 with complexity. Always use passwords with upper-case, lower-case, special characters and numbers.

---

### Post by CharlesA on 2010-11-03
> **mainerror said:**
> 12 characters without complexity is not as secure as 9 with complexity. Always use passwords with upper-case, lower-case, special characters and numbers.

As long as it's not a dictionary word, you can get away with a 12 character non complex password.

It's recommended to use numbers and symbols, but not necessary.

---

### Post by Megaptera on 2010-11-03
I carry a card produced from PasswordCard. No one should guess which string/combination I'm using and it helps me stop using qwerty all the time!!

[http://www.passwordcard.org/en](http://www.passwordcard.org/en)

---

### Post by brian_p on 2010-11-03
> **CharlesA said:**
> 

It's not really secured by default, so you'd have to secure it after installation . . . . . .

When something like that is said it gives the impression there is something not quite kosher about ssh and it is lacking. The implication is that that extra steps have to be taken to bring it up speed.

My sshd runs on port 22 (as is intended) and responds to the 16 character password I give it. I'd maintain it is as secure as anything else on this machine. Or the front door of my house for that matter.

---

### Post by CharlesA on 2010-11-03
> **brian_p said:**
> When something like that is said it gives the impression there is something not quite kosher about ssh and it is lacking. The implication is that that extra steps have to be taken to bring it up speed.

My sshd runs on port 22 (as is intended) and responds to the 16 character password I give it. I'd maintain it is as secure as anything else on this machine. Or the front door of my house for that matter.

If you use a strong password, like you are doing, it's fine out of the box.

If you use a weak password, and expose SSH to the internet, you'll likely have a compromised system.

---

### Post by brian_p on 2010-11-03
> **mainerror said:**
> 12 characters without complexity is not as secure as 9 with complexity. 

I'll not argue with that - the maths might be on your side.

> Always use passwords with upper-case, lower-case, special characters and numbers.

I'd argue with that. mypasswordwithoutuppercaseandspecialcharcters is an excellent (and easily remembered) password.

---

### Post by tgm4883 on 2010-11-03
> **brian_p said:**
> I'll not argue with that - the maths might be on your side.



I'd argue with that. mypasswordwithoutuppercaseandspecialcharcters is an excellent (and easily remembered) password.

According to [http://howsecureismypassword.net/](http://howsecureismypassword.net/), It would take About 8 octillion years for a desktop PC to crack your password

---

### Post by Yezinki on 2010-11-03
> **tgm4883 said:**
> According to [http://howsecureismypassword.net/](http://howsecureismypassword.net/), It would take About 8 octillion years for a desktop PC to crack your password

According to the link it would take 117 days for a desktop pc to crack my pw?

Regards!

---

### Post by Yezinki on 2010-11-03
> **Megaptera said:**
> I carry a card produced from PasswordCard. No one should guess which string/combination I'm using and it helps me stop using qwerty all the time!!

[http://www.passwordcard.org/en](http://www.passwordcard.org/en)


How do I use this..........password card #s, alphabets, symbols are so dim......has 8 passwords?

Thanks.

---

### Post by brian_p on 2010-11-03
> **tgm4883 said:**
> According to [http://howsecureismypassword.net/](http://howsecureismypassword.net/), It would take About 8 octillion years for a desktop PC to crack your password

That's quite an interesting site. At least it is upfront about its methodology, which is more than can be said about some of the others which advise on password strength.

I'd question some of the things there, 'braekfast' being a better password than 'breakfast' being one. In brute force terms there is no difference and this can be seen by testing both. As for changing a password frequently - I change mine at the same time I replace the five lever mortice locks on the doors of my home.

---

### Post by brian_p on 2010-11-03
> **Yezinki said:**
> According to the link it would take 117 days for a desktop pc to crack my pw?

You're using a total of 9 lower case/number characters. Add an upper case letter for 2,000 years! Should last you a lifetime.

---

### Post by Yezinki on 2010-11-03
Thanks brian_p for the hint.

Regards!

---

### Post by Megaptera on 2010-11-04
> **Yezinki said:**
> How do I use this..........password card #s, alphabets, symbols are so dim......has 8 passwords?

Thanks.

You can print off any number of unique cards.
You use the characters/letters in any combo eg l to r or r to l; up to down or diagonal. You can use 1 line or 1.5 lines.
Only you know what combo/direction/number of lines you've used.
You can use 6 digits or all 96 in any order that you can remember.

Pick a direction. You don't have to go from left to right to read your passwords, you can go from right to left, up or down, or even diagonally. It's probably a good idea to pick one direction though, even if you use your PasswordCard for multiple passwords.
Pick a password length. Eight is pretty secure and usually acceptable. Again, it's a good idea to pick one length.
Pick a colour and a symbol for each password. You can use one password for all your sites, but that still wouldn't be very safe. It's a good idea to at least have different passwords for very important sites, such as Internet banking sites.

Don't read along with your finger, or the smudge will tell a thief where your password is.
Keep your PasswordCard on your person, don't leave it lying around near your computer.
Clear your browser cache and history after printing this page.

---

### Post by linux18 on 2010-11-04
It would take
About 7,732,087,003 nonillion years
for a desktop PC to crack your password

w00t! I win

and its easy to type and remember:
!@#$%^&*()qwertyuiopQWERTYUIOP

now I lost :)

---

### Post by mainerror on 2010-11-04
> **tgm4883 said:**
> According to [http://howsecureismypassword.net/](http://howsecureismypassword.net/), It would take About 8 octillion years for a desktop PC to crack your password

This site is pretty much useless as it only tells how long it'd take to crack the given password using brute-force method. There are other methods like dictionary attacks which would get simple passwords with simple dictionary words and combinations of dictionary words in no-time.

---

### Post by tgm4883 on 2010-11-04
> **mainerror said:**
> This site is pretty much useless as it only tells how long it'd take to crack the given password using brute-force method. There are other methods like dictionary attacks which would get simple passwords with simple dictionary words and combinations of dictionary words in no-time.

Pretty much useless is a little strong don't you think? I mean, I would never type my password into a site like that for fear they were logging that sort of thing. And we should all know by now that dictionary words are very bad to have. But as an educational tool I believe it has value in that it can show you how much longer it takes to crack a password if you add a special character, or move from 8 to 10 characters. 

Worthless say you? I say educational.

---

