---
title: "Question about old school security solution to safeguard accounts with money"
date: 2019-12-12
forum: Security
---

### Post by patrikmellq on 2019-12-12
Hello I am trading football and using Betfair Exchange Market - now i also been thinking to trading sports with Bitcoin Exchange Market.
Anything from 1000 Euro and more is significant money (for me) that you don't want to lose by a hack, i have read storys about some members at sport betting forum who had there account destroyed where some one have made a withdrawal and taking all the money.

I watch a video about crypto and how to safeguard against hack or reveal sensitive information.

1) Not auto save password on web-browser
2) Get two ordinary papper books and write down the password on them and keep the two papper books in two separate places, in case of fire or similar
3) Secure your computer with antivirus software and make sure you don't have any spyware
4) Make long complex phrases when creating passwords
5) Note the two-identification function by some sites using phone can be hacked where there take order a new phone card and getting access that way (but google two-identification app seems secure,,, my opinion)

A) Now I considering only using Tails-live-cd burned on a rw-cd when trading sports with no saved passwords
B) Have all gambling accounts (sport/gambling sites) password phrases on two separate papper books
C) Use both phone and google two-identification funktion

I assume that a live tails cd only can be hack getting into the computer ram memory and i assume that does not matter as i will have https connection between me and the site when entering password and two-identification password 
My little knowledge about security assume that this is as secure as it get and are more and better then have a window computer with average firewall and antivirus with auto saved passwords in the web-browser

Is this wrong and I am only paranoid or is this the right way to go 

Cheers

---

### Post by TheFu on 2019-12-13
There are many flaws in the plans above.
Never use a phone/tablet for financial accounts.  Once you've installed any 3rd party packages, assume the phone is pwn'd by the bad guys.
Never use a phone for 2FA.  Use a USB key/FOB instead. These are $20-50.  Yubikey is the best known, but any FIDO v1/v2 key should be fine with the U2F standard.
Using passwords alone is a failure and you've already lost the security game.  Use keys whenever possible.  There are keys for PKI, keys for x.509 certs, gpg/pgp keys, etc.
Don't keep your "wallet" on the device where you spend crypto-money.  Have at least 2 backups, on 2 different media devices, of your wallet. Keep those physically secured, not connected to any computing device. Obviously, it will need to be connected during a transaction, but that time should be extremely limited.

Not all logins support key-based authentication. That's too bad.  If you can memorize any password, then you've already failed to make it complex and long enough.  For physical computer logins, I want over 20 random, characters.  For internet logins where keys and a U2F device are not supported, I want 55+, random, characters for the password part. Password managers are good for this.  For example, I don't know my username or passphrase to log into my bank. Both are long and random.  I don't know my google passwords either.  The passphrase is 55+ characters and uses a U2F FOB as the 2nd factor.  Some of my financial institutions support the RSA SecurID FOB. It was free for asking.  Most banks don't and seem relatively clueless with their claimed 2nd factor.  BoA claims a "site image" that I pick added some security.  It doesn't since someone could MiTM that access if they control the DNS being used and capture the image I picked.

For passwords that you must type in and can't use a password manager, go ahead and write down the last 40 characters on 1 paper, but leave off either the first 10-20 or last 10-20 characters, which you should memorize.  Never, ever, write down the entire password anywhere.  Always remember, 
*something you know* 
and
*something you have*
are needed to make up a good passphrase.  The something you have is that paper. The something you know is memorized and should be unique for all physical logins - laptop, desktop, tablet, phone1, phone2.  I think that's about it.  Everything else would be in a password manager and, hopefully, using a u2f device for authentication.  Google saw hacked accounts drop over 90% when u2f was used. It works.

Clearly, never save any passwords inside a browser.  Never use a password manager browser addon to automatically fill in passwords without specific user interaction required.  Though "never" might just be a anything connected to money.  RAM can be scanned for passwords on a hacked system when the password manager is being used.

Use different email addresses for every type of website you can.  If there is money involved, it is worth having a different email address every time. NEVER mix email addresses for social networks with those that are connected/tied to anything financial.  Each broker, bank, retain login that I use has a different email address.

Google, facebook, twitter accounts can be used to authenticate with other services.  I would never do this, since it provides marketing/sales data back to those companies about which other websites I use. I don't want them to have that data and a little inconvenience is worth it to me. OAuth2 seems to be a secure protocol, so this isn't a security issue, just a privacy issue.

I've never used Tails.  Having to get a fresh version every few weeks to get the patches seems like too much hassle to me.  We each have different acceptable risks.  I would never bet online, so use that data if you like to understand my risk levels.  I won't sign up for electronic bills either.  I keep banking/financial stuff off the internet, since anyone in the world can hack anyone elses computer.  Why allow someone in North Korea or Iran to hack my bank account?  Banks are extremely regulated and insured for security.  Are online betting shops similarly regulated and insured for security?  I do use 1 specific credit card for all online purchases and I use different cards for real-life and purchases overseas.  When a card gets stolen, I can usually pinpoint where it was used last.  I've had a card last used in Argentina somehow get used 6 months later in NYC, then later the same day in Miami.  I've never been outside the NYC airports or in Miami, ever.  When the transactions happened, I was happily in Squidbilly-Land.

---

### Post by patrikmellq on 2019-12-16
TheFu thanks for the information and after reading your post i have start to change passwords with password manager with 55+ lenght passwords and i buy/order Yubikey for my email accounts and firwall and antivirus and VPN ...
I think that will do, becasue i want better then average security and thanks to your post i know will get that, so at least i make it more difficult for some one to acces my gambling accounts.

Many Thanks

---

### Post by TheFu on 2019-12-16
Hopefully, someone with more direct online gambling experience will respond with their security techniques.

There's nothing special about "55" characters, except it is very long, computer generated, and we will never actually type those passwords in.  When hackers gain access to encrypted password lists, there isn't much that end-users can do except have a long, complex, password.  Basically, they hack 80% the passwords in a month or 2 using multiple GPUs. Our goal is to be in the last 5% of the passwords in the list, so better than 95% of the other accounts.

Hopefully, you've selected a password manager with a DB file format that works on all your platforms with a slight priority with the primary platform over the read-only platforms.  In my world, I have 1 "system of record" where I make any password updates/deletions and new information.  All the other systems, I consider read-only for the password DB.  Those include laptops, phones, tablets, basically, places where referencing the long, complex, passwords is needed, but that's all.

---

