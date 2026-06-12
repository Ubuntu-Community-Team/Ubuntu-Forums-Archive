---
title: "Firefox Passwords - Safe?"
date: 2013-08-09
forum: Security
---

### Post by Quarkrad on 2013-08-09
It is obviously convenient to have Firefox save and manage ones passwords for numerous web sites - but it is easy to access these passwords?  They are easily obtained through  Edit/Preferences/Security/Saved Passwords/Show Passwords/Yes - there is no password protection to 'see' these passwords.  So how safe are these valuable passwords when surfing on the net?

---

### Post by SlugSlug on 2013-08-09
You can create a master password to lock them

---

### Post by hakermania on 2013-08-09
> **SlugSlug said:**
> You can create a master password to lock them

This.

Firefox passwords are NOT safe.

From my experience most password multistealers (that are generally designed for windows) ignore firefox passwords if you have set a master password.

This does not mean that the database cannot be bruteforced, so setting one strong master password is highly recommended.

---

### Post by pqwoerituytrueiwoq on 2013-08-09
+1 master password

---

### Post by Quarkrad on 2013-08-10
Thanks very much - all done.  I know this seems silly but if I kept a record of the master password in a spreadsheet that is in my Documents folder is it safe from potential threats on the net?  My understanding is that Ubuntu/Linux is generally safe (I guess compared to Windoze) from outside threats - would a hacker/threat from the net having access via firefox be able to get into my **/home/dad/Documents** folder?

---

### Post by ikt on 2013-08-10
> **Quarkrad said:**
> Thanks very much - all done.  I know this seems silly but if I kept a record of the master password in a spreadsheet that is in my Documents folder is it safe from potential threats on the net?  My understanding is that Ubuntu/Linux is generally safe (I guess compared to Windoze) from outside threats - would a hacker/threat from the net having access via firefox be able to get into my **/home/dad/Documents** folder?

It depends on who is doing the hacking and why... and your paranoia levels.

It's very easy to be paranoid about security, to the point where [you can't trust anything]("http://c2.com/cgi/wiki?TheKenThompsonHack") and eventually reach a point where you've done so much to protect yourself this: [http://xkcd.com/538/](http://xkcd.com/538/) seems more likely.

For general web browsing the likelihood of you getting hacked on linux is somewhere between extremely unlikely to none, straight off the bat, you'd have to be a very unlucky person to have this happen just by browsing the web, I'd almost venture out to say that it'll never happen, but absolute statements are wrong all of the time.

The most likely reality is that someone will download and run a trojan, and even that's extremely unlikely, but if someone was to do that, there's a chance it'll upload your entire home directory and put it up on y00g0thax0red.net. That's the problem with getting owned, if you give a program full access to your computer, you give the program full access to your computer.

I would put the password in the spreadsheet, as it's the master password to your firefox passwords... given the entire scenario above is unlikely to ever happen, you would not only need to have a bot on your system, because there's no way the bot is going to know that the random numbers and digits in your spreadsheet is your firefox master password, you would need to have someone actively going through your computer remotely, desperately seeking to get access to your firefox master password trying anything he can find. Which at this stage is paranoia more than reality.

---

### Post by agillator on 2013-08-10
There are lots of options that will make things more secure if that is your worry. You could, for example, put your spreadsheet on a USB thumb drive and only mount it when you need it. You could use TrueCrypt to encrypt the file and mount/open it only when you need it. You could use GnuPG to encrypt the file and only decrypt it when you need it. Your spreadsheet program itself probably has the ability to password a file. Some things are more 'secure' than others. There has to be a trade off between ease of use and paranoia. Two things to remember: just because you are paranoid doesn't mean they are not out to get you, and any security system developed/invented by a human can be defeated by a human. I fully agree with ikt above, but will add I have not heard of anyone having problems with Firefox's password security even though it is not particularly strong. The options, as with most things in Linux, are yours.

---

### Post by Cyphrex on 2013-08-19
+1 Truecrypt

---

### Post by Buntu Bunny on 2013-08-23
> **agillator said:**
> There are lots of options .... You could, for example, put your spreadsheet on a USB thumb drive and only mount it when you need it.

Now that's a good idea. I'll have to look into TrueCrypt as well. (Not that I have anything of real value to encrypt)

---

### Post by bapoumba on 2013-08-23
Or use an app that will manage your passwords. One recent thread on LastPass/KeepassX : [http://ubuntuforums.org/showthread.php?t=2165372](http://ubuntuforums.org/showthread.php?t=2165372)

---

