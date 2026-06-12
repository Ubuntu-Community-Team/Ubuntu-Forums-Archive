---
title: "Are Password Managers Really Worth It?"
date: 2012-06-07
forum: The Cafe
---

### Post by buzzingrobot on 2012-06-07
Given the current spate of password thefts, I'm wondering, again, if I should use a password manager. 

I'm curious about opinions about them.  Are they really secure? Every one I've looked at relies on a master password. That becomes your most important password, but it is also the only password you can't manage with the password manager. If that's compromised along with any device running your password manager, you are in trouble.

I'm also wondering about consistent use on multiple platforms.  I use a Linux desktop, a Macbook, an iPhone, and an iPad. If I commit to a password manager, I want one that's available for all those devices and one that does not make me responsible for porting data from device to device. In other words, I want to set things up on one machine and have all my passwords available on all the other devices.

Finally, I've tried a couple of password managers in the past.  I quit them because they became a hassle to use. E.g., entering the password in the wrong field.

So, what say you all?  If you use a password manager, which onto and why? I

---

### Post by Porcini M. on 2012-06-07
I have a text file with all my passwords & other sensitive info in it. I have a button on my panel that invokes a script as root (using gksudo), which decrypts the text file & opens it in a text editor. When I'm done reading & potentially editing it, it re-encrypts it.

---

### Post by sffvba[e0rt on 2012-06-07
KeepassX and on Windows Keepass 1.x ... really needed as I have used it to create random passwords as complex as allowed for each and every log in I need to do into any service.

It has a fairly long pass phrase and also needs an additional file to unlock... I feel secure.



404

---

### Post by Erik1984 on 2012-06-07
I use KeePassX. I have too many different accounts and definitely don't want the same weak (relatively short) password anywhere.  As we all know from XKCD, special characters don't matter, passwords just need to be long. The easiest is just to let KeePass or another tool generate a random long string for you. KeePassX is also quite nice to operate, just click on the entry and CTRL+C to copy the password (it will only stay on the clipboard for a short time).

If you use multiple platforms maybe you should look at LastPass to manage your passwords through a web interface (of course usable on all platforms you mention). KeePassX (Linux, and also Mac AFAIK) and KeePass (Windows) are also compatible as long as you use the .kdb database format (KPX can't reed KP's kdb2 format).

---

### Post by madverb on 2012-06-07
Yes, they are. Just make sure the unlock password is nice and long. It means you can have randomly generated long passwords without having to remember them.
Now we just need to make sure all financial institutions and the like allow for long complex passwords and we are set. Some government sites in Australia don't allow for passwords longer than 8 characters. INSANITY.

---

### Post by CharlesA on 2012-06-07
> **madverb said:**
> Yes, they are. Just make sure the unlock password is nice and long. It means you can have randomly generated long passwords without having to remember them.
Now we just need to make sure all financial institutions and the like allow for long complex passwords and we are set. Some government sites in Australia don't allow for passwords longer than 8 characters. INSANITY.

+1. I have a few sites that can only take 8 character passwords with no special characters. It makes me sad. =/

I use KeePass, myself and it has worked well for me - I have it on a USB stick. ;)

---

### Post by scouser73 on 2012-06-07
Why not manage your passwords, create a list of Sites and associated passwords and have it on a flash drive.

I would suggest using a password generator when creating new passwords & making the passwords over twelve characters long

[IMG]http://ompldr.org/vZTYydg[/IMG]

It's your stuff, you're in control of it so it's your job to make it the most secure it can be.

---

### Post by Copper Bezel on 2012-06-08
[QUOTE=CharlesA]+1. I have a few sites that can only take 8 character passwords with no special characters. It makes me sad. =/[/QUOTE]
I ran into this lately with my school login. I was similarly disappointed.

---

### Post by CharlesA on 2012-06-08
> **Copper Bezel said:**
> I ran into this lately with my school login. I was similarly disappointed.
I don't understand what is so hard about adding a special character to a password. I guess it has something to do with the backend database or something.

I don't know for sure, so take that with a kilo of salt. :p

---

### Post by Metallion on 2012-06-08
> **CharlesA said:**
> take that with a kilo of salt. :p

Can you call linkedin and repeat that line? Sorry, couldn't resist.

On topic, I also like password managers. Same as notfound. I have a bunch of really long passwords for different sites and need a password manager to remember them. An encrypted text file would work just as well I guess.

---

### Post by roelforg on 2012-06-08
> **CharlesA said:**
> I don't understand what is so hard about adding a special character to a password. I guess it has something to do with the backend database or something.
 
I don't know for sure, so take that with a kilo of salt. :p
 
My guess?
They don't escape the pass for DB queries... Which inherently means that it's stored in plaintext (or that the hashing is done by the db).
 
I'm switching to using ubuntu SSO (although they should've called it Canonical SSO) wherever possible.
I store my passwords in a text file on an encfs with encryption set to paranoia and the password is the sha2 hash of the "real" password.

---

### Post by buzzingrobot on 2012-06-08
I tried a password manager for a short time a few years ago. I gave up on it due to the lack of a uniform experience across all the devices I used.  Specifically, the passwords the manager generate are impossible to remember.  So, when I needed to log on using a device without the manager, I was at a loss.

Currently, I use two passwords.  One is not especially strong.  I use it on on low- or no-risk sites.  I use a long and rather strong password on financial and other sites. It's derived from a mnemonic phrase that I've memorized (and won't forget), with the addition of odd characters in fixed places.  

I'm considering a scheme to alter that long password on a site by site basis, following some consistent pattern that's keyed to a fixed element at each site, like the site's name or URL. Something simple that I could do in my head to generate a string of characters that I would add to the base password.  That would allow me to use a unique password at each site and avoid using a password manager or needing to record my passwords in any fashion
.

---

### Post by zombifier25 on 2012-06-08
I use Firefox's built-in password manager, encrypt it using a master password (which is really long), and then use Sync to sync it across machines, which requires a password (which is also really long) AND a sync key.

If I have spare hard drive space, I would even encrypt the home folder. Now that's a lot of protection.

---

### Post by buzzingrobot on 2012-06-08
Of course, no security measures we take will help if soneone else permits our password to be stolen.

---

### Post by m_duck on 2012-06-08
> **CharlesA said:**
> I don't understand what is so hard about adding a special character to a password. I guess it has something to do with the backend database or something.

I don't know for sure, so take that with a kilo of salt. :p

My guess is that it is much easier to protect the DB from e.g. SQL injection and whatnot if symbols are just flat out not allowed. Though a similar amount of salt should be considered with that - just a guess.

I use LastPass, it works on everything - would be completely lost without it.

---

### Post by Simian Man on 2012-06-08
I just write them down on my hands.  Then if I see a suspicious looking person I ball my hands into fists so they can't see them.  This method is also convenient if I need to do any punching.

---

### Post by CharlesA on 2012-06-08
> **roelforg said:**
> My guess?
They don't escape the pass for DB queries... Which inherently means that it's stored in plaintext (or that the hashing is done by the db).

That would by me guess too.

Isn't Ubuntu SSO just using OpenID?

> **m_duck said:**
> My guess is that it is much easier to protect the DB from e.g. SQL injection and whatnot if symbols are just flat out not allowed. Though a similar amount of salt should be considered with that - just a guess.

I guess that makes sense too. I would have thought it would be easier to just sanitize your db inputs. 

[http://xkcd.com/327/](http://xkcd.com/327/)

> **Simian Man said:**
> I just write them down on my hands.  Then if I see a suspicious looking person I ball my hands into fists so they can't see them.  This method is also convenient if I need to do any punching.

:lolflag:

---

### Post by Andrewmham on 2012-06-08
I find using the same password I've been using since the AOL days for every single conceivable account I have adds a certain 'thrill' to everyday life...I probably need to fix that.

---

### Post by m_duck on 2012-06-08
> **CharlesA said:**
> I guess that makes sense too. I would have thought it would be easier to just sanitize your db inputs. 

[http://xkcd.com/327/](http://xkcd.com/327/)

Very true, but I just assume that everybody is lazy (myself included).

That's genius, Simian Man.

---

### Post by zombifier25 on 2012-06-09
> **Simian Man said:**
> I just write them down on my hands.  Then if I see a suspicious looking person I ball my hands into fists so they can't see them.  This method is also convenient if I need to do any punching.

Where are my drugs and 5$ wrench?

---

### Post by trinux_bc on 2012-06-09
Sounds like Lastpass would be perfect for the OP. I've used it for a while now and I love it, it works and is accessible pretty much anywhere.

trinux_bc

---

### Post by AlbertJB on 2012-07-08
Well, I need it to use a password manager since I have at least 100 different accounts so.. xD

By the way, I used to work with Keepassx, then I switch to Keepass 2.x, and now I would like to switch back to Keepassx but I don't know how to do that, I think it's impossible :( No export / import combination suitable... :(

---

### Post by BigSilly on 2012-07-08
I absolutely love KeePassX, and also KeePass2 on Windows. I just make sure I keep an up to date database on both applications so I don't get stuck.

---

### Post by Primefalcon on 2012-07-08
I'll tell you what I do, first off I have an encfs volume in my dropbox (which is not needed but an extra layer of security is always nice...

I keep an gpg encrypted text file in this encfs volume, lets call it myPasswords.txt.gpg for arguments sake here....

And I have thi script in my bin folder

==viewPass==
```
#!/bin/bash
#for multiple search critera
if [ "$2" == "" ]; then
gpg --decrypt --no-use-agent $HOME/EncDropbox/myPasswords.txt.gpg | egrep -i "*$1*"; sleep 30s; cat /dev/null | xsel -psb; reset;. ~/.bashrc
else
gpg --decrypt --no-use-agent $HOME/EncDropbox/myPasswords.txt.gpg | egrep -i "*$1*" | egrep -i "*$2*"; sleep 30s; cat /dev/null | xsel -psb; reset;. ~/.bashrc
fi

```

this way no matter what machine I am on, if I need to know m pssword for Ubuntu forums.... I just open a terminal and type in

```
viewPass ubuntu forums
```

and it then prompts me to unlock my gpg key, afterwish it spits out my password and then after 30 seconds clears the terminal and wipes the clipboa...

This way I can have ridiculously long passwords with zero hassle and not having to rely on anyone elses security practices..... or lack thereof for my passwods...

and since it is inside an encfs volume if I want to decrypt the whole document to add passwords.... I can.... safetly

---

### Post by CharlesA on 2012-07-08
> **Gosset Inofensiu said:**
> Well, I need it to use a password manager since I have at least 100 different accounts so.. xD

By the way, I used to work with Keepassx, then I switch to Keepass 2.x, and now I would like to switch back to Keepassx but I don't know how to do that, I think it's impossible :( No export / import combination suitable... :(

The databases are compatible as far as I recall.

---

### Post by BigSilly on 2012-07-08
> **CharlesA said:**
> The databases are compatible as far as I recall.

No, you have to use a Windows machine to import your KeePassX data into KeePass2, then save the file as a new KeePass2 file. Then you can use the KeePass2 program on Linux to use the new database you've made. It won't work directly using Linux. KeePass2 will alert you that you need to use the Windows program to import a KeePassX database for one reason or another. To be honest I mostly use KeePassX at the moment, as I seem to prefer it, but I do keep both databases I have up to date.

---

### Post by CharlesA on 2012-07-08
> **BigSilly said:**
> No, you have to use a Windows machine to import your KeePassX data into KeePass2, then save the file as a new KeePass2 file. Then you can use the KeePass2 program on Linux to use the new database you've made. It won't work directly using Linux. KeePass2 will alert you that you need to use the Windows program to import a KeePassX database for one reason or another. To be honest I mostly use KeePassX at the moment, as I seem to prefer it, but I do keep both databases I have up to date.

D'oh! I've only used KeePass2, so I haven't tried to convert it over. Thanks for the clarification. :)

---

### Post by kellemes on 2012-07-08
I assume [KeePassX 2]("http://www.keepassx.org/news/2012/07/361") will be able to import KeePass 2 db's eventually , but v2 is still alpha at the moment..

---

### Post by AlbertJB on 2012-07-08
Hi, what I meant was I am not able to export a DB from KeePass2 to KeePassX. I've tried to do that both in Ubuntu and in a Windows machine, but from what I remember I was unable to achieve that simple migration. I'm really waiting the KeePassX. 

I also want to say that KeePass2 is compatible at last with Ubuntu OS, but IMHO is way less user friendly than the Windows version. For Ubuntu users, my advice is keep with KeePassX. 

Thanks for the replies, though.

> **BigSilly said:**
> No, you have to use a Windows machine to import your KeePassX data into KeePass2, then save the file as a new KeePass2 file. Then you can use the KeePass2 program on Linux to use the new database you've made. It won't work directly using Linux. KeePass2 will alert you that you need to use the Windows program to import a KeePassX database for one reason or another. To be honest I mostly use KeePassX at the moment, as I seem to prefer it, but I do keep both databases I have up to date.

---

### Post by mastablasta on 2012-07-08
you need to probably save as old type of data basy in keypass 2 that way you should be able to import it into keypassx.
keypass 2 has some additional security (upgraded). i use that one on both win/portable USB and linux  since i don't need any other functions but to encrypt&store passwords. i know that some functions do not work in linux but since i am not sueing them it doesn't matter.

---

### Post by AlbertJB on 2012-07-09
Thanks for the reply @mastablasta.

In my system, keepassx import options are: 

- KeepassX XML files
- Kwallet XML files
- PwManager files 

Keepass2 export options in windows are:

- KDB (1.x)
- KDBX (2.x)
- Keepass XML (2.x)
General options
- Customizable HTML file
- Transform using XSL stylesheet
- Windows favorites (?)

So I think it's pretty clear there's no way I can transform the KDBX 2.x file to KeePassX format.

---

### Post by AlbertJB on 2012-07-09
OK, you were right, I have had to go to Windows, install Keepass 1.X, open the file with Keepass 2.X, export to 1.X format, open Keepass 1.x, import the file, and then on Ubuntu I can open again the file with KeePassX. Thank you all.

---

### Post by mamamia88 on 2013-06-21
Just chose passwords that are easy to remember but hard to crack.  Like a sentence with mixed up capitalazation and using symbols to replace letters occasionally.   And use simple passwords for stuff you don't really care is hacked or nobody will bother hacking ( like this site for example).  I have nothing to lose if somebody hacks this account really.

---

### Post by PJs Ronin on 2013-06-21
I have a little black book.

Actually, I have 2 little black books but one contains ids/passwords.   Done it for years.

---

### Post by montag dp on 2013-06-21
I also use KeepassX.  I keep the database in Dropbox so it stays up to date, but keep a copy of the key file locally on my laptop and desktop at work.  Seems to work pretty well.

---

### Post by dwaite on 2013-06-22
For reasons already stated, I think it's crucial nowadays to use one.

I like LastPass because it basically just works as a browser addon, so it's OS agnostic. It does have OS-dependent executables, but really all they do is install the addon into each browser you have on your machine anyway. Since it's web-based, once you install it to a browser and sign in your up and running without having to sync or anything, although it does have a local password cache that it uses on the odd chance that the LastPass server goes down.

I don't know how it compares to any other managers to be honest, it was the first one I tried and I was happy with it.

---

### Post by zeroseven0183 on 2013-06-23
It depends on how many passwords you are trying to remember. If it's few, you don't need a password manager but if it's over 10 and you can't remember them all, then get one.

I'm using KeepassX for over 3 years and it's reliable.

---

### Post by mikodo on 2013-06-23
> **Simian Man said:**
> I just write them down on my hands.  Then if I see a suspicious looking person I ball my hands into fists so they can't see them.  This method is also convenient if I need to do any punching.
I haven't read anything here, that has made me laugh so much.

:lolflag:

---

### Post by Duhg on 2014-02-16
A number of years ago, I operated a Paid to Click email site. From this experience, I can attest to the value of having a different password for every site that you sign up for. As the administrator, I had access to everything that was required to sign up, including: emails, passwords, user names, addresses, paypal account emails, names, etc. An unscrupulous person could take that info and try different paid to click sites, email accounts, ebay, amazon, paypal,what have you, and attempt to try the usernames/passwords combinations to try accessing accounts if they existed. My only worry is that a virus may copy my copy /paste info when I use a password manager to copy and paste my info to access my sites. The other problem, of course is having a really good Master password to access your password manager. I have seen an article about creating great passwords that are easy to remember.
[http://lifehacker.com/184773/geek-to-live--choose-and-remember-great-passwords](http://lifehacker.com/184773/geek-to-live--choose-and-remember-great-passwords)

I use those ideas for accessing my password manager as opposed to sites.

---

### Post by Don_Stahl on 2014-02-16
I use KeePassX at home, and the Windows version on my work computer. I put miscellaneous info in the file along with passwords -- notes on networks, computer OS details, etc. Put a copy of the kdb file on the cloud. I admire those who have build custom scripts to encrypt their files, but I prefer to let KeePassX do it for me. My memory is not so good, especially in the evenings when I've got adenosine buildup from work, so I really need a password manager. Otherwise I'd sit in front of the boot screen for one of the laptops waiting for some kind of bodhisattva to enlighten me so I can log on.

---

### Post by mbuell on 2014-02-24
I'll add this voice to the crowd: yes, they are worth it. Far more secure with one than without, unless you have a photographic memory. KeePass and K-P-X seem good to me - reliable. But I use another program that is worth mentioning. Treepad Business edition. The business edition permits encryption. Since I used this before KeePass was around, I've stuck with it. I can organize things heirarchically, which helps to find things when you've got a couple hundred logins. It is a Windows paid-for program, but it works on linux (with wine), and I don't mind paying for it every 5 or 6 years.

---

### Post by JeQhdMD on 2014-04-05
Have been using Cherrytree database (in buntu repos).   Cherrytree is a (directory tree) db that serves as a knowledge base.   Text window has many formatting options so it's flexible.  Output to html, pdf using xml or sqlite db.   Compression and Encryption available via 7zip using AES.   This program is the first thing I install to the standard base - a real gem imho.

---

### Post by HermanAB on 2014-04-05
I also use KeepassX as a secure and cross platform alternative to Evernote/Nixnote.  Whenever I need to save something really important, I make a note in KeepassX.  That way, I am quite certain that spooks & crooks will have a really hard time to get it.

---

### Post by sffvba[e0rt on 2014-04-05
> **not found said:**
> KeepassX and on Windows Keepass 1.x ... really needed as I have used it to create random passwords as complex as allowed for each and every log in I need to do into any service.

It has a fairly long pass phrase and also needs an additional file to unlock... I feel secure.



404

See I already posted in this thread many moons ago, so I will only add:

[video=youtube_share;0v2KKTXWd10]http://youtu.be/0v2KKTXWd10[/video]

---

### Post by grumblebum2 on 2014-04-05
...moved to cafe :shock:
...ohhh we're already there. :sad:

---

### Post by Yozuru on 2014-04-06
I say they are if you have multiple accounts with various different passwords associated with them.

---

### Post by HermanAB on 2014-04-08
I have over hundred passwords.  There is no other way to preserve my sanity than with KeepassX and KeepassDroid.

---

### Post by grumblebum2 on 2014-04-08
keepassX a must have for those important logins.
Love the autotype feature and database locking after a set time period.
Save your database to a couple of different locations and you never need worry.
Just choose a master password you'll never forget.

---

### Post by QIII on 2014-04-08
I have a pocket-sized Moleskine soft bound notebook in a heavy steel lock box bolted into a cupboard in the laundry room.

---

### Post by grumblebum2 on 2014-04-08
Yeah but keepassX is mole safe.
No moles were harmed in it's production. 
[-X :-P

---

### Post by mamamia88 on 2014-04-08
I just try and come up with a strong password that is easily rememberable and use it over and over again for important stuff.  The less important stuff ie stuff that doesn't have financial or identity theft potential doesn't need as strong of a password

---

### Post by frostschutz on 2014-04-08
I'm a huge fan of the password hashing idea, as implemented in Password Hasher [http://wijjo.com/passhash/](http://wijjo.com/passhash/)

All you need is a secret passphrase, and the name of the thing the password is for (like domain name, name of your bank, whatever)

secret + ubuntuforums = 6ZohRh/+
secret + google = 5r3q1c*O
secret + derpbank  = 1F2zx,no
etc.

If a site is hacked and the attacker has the clear text password, he doesn't necessarily know it's a hash, since it looks just like any other random password; then he'd have to guess the name used (is it ubuntuforums or ubuntuforums.org), and then start bruteforce in order to get to the secret, since only with the secret he'd be able to guess passwords for other sites.

Unfortunately in this implementation the hashing function isn't terribly expensive, but if it was, such a bruteforce would not be feasible given a good/long/entropy enough secret.

Such a solution is simple and gets by without database, so it can not be lost or not with you when you need it.

---

### Post by HermanAB on 2014-04-09
"a strong password that is easily rememberable and use it over and over again for important stuff"

That leaves you at the mercy of the IT idjits at every important site.  If ONE of them screw up and the password gets exposed, then ALL your important stuff is at risk.  Many sites use your email address as the user name.  Consequently, there are scripts that will try a stolen password and email address at many different institutions automatically.  Sooner or later, they tend to hit paydirt.

With a password manager, it is easy to ensure that all your passwords are unique.  Keepass (Windows), KeepassX (Linux, Mac) and KeepassDroid (Android), with the database stored on Dropbox or similar, means that you can access your passwords everywhere.  It solves the whole head-ache very neatly.

---

