---
title: "Wine WoW Hacking Issue Please Help!!!"
date: 2010-11-20
forum: Wine
---

### Post by Eldorian on 2010-11-20
Hi all. Here is the issue I was facing. I had WoW running just fine with wine for 5 months. I recently started going through the steps to get DDO installed and working but during that time something happened and my WoW account was hacked. Since then my battle.net account has been compromised over and over until I told blizzard to lock it up tight until I can resolve the issue.

I have downloaded and installed all the major antivirus programs recommended by reputable companies, ie...Avast, AVG, F-prot, ClamAV and BitDefender. I scanned my whole system with each of these and not a single infection or questionable issue was discovered by any of them. Blizzard claims there must be a key logger running on my pc. I can't find one and my account info has not been given out to anyone or any hacking web site. From my perspective at this point it looks like an inside job or there is a key logger on my system that cannot be detected by any of the 5 antivirus programs I have tried. I got fed up with it all and deleted the .wine bottle and am now rethinking the whole situation. I purchased an authenticator from Blizzard and will get it in a few days which should stop my account from being hacked...but the problem remains...what the hell happened to allow someone to hack my account in the first place and how do I protect against it in the future?

So there you have it. Any thoughts, recommendations, critiques are welcome from one and all. Thanks for listening. :)

My system:
Intel Dual-Core E5300 
2GB RAM 
700GB SATA HD
NVidia GeForce 9500 GT with 1GB RAM
Ubuntu 10.04 w/ Gnome Desktop

---

### Post by cwwilson721 on 2010-11-20
After you deleted your .wine folder, any Windows-based stuff is gone.

If you have anything else on your system, it's Linux based, and the P.O.S. anti-virus stuff you mentioned can't do Linux.

Get ClamTk/ClamAV from the Software Center, let it do it's thing.
If there are any rootkits, etc, that can deal with them.

Then Reinstall WoW. Your system will be clean then.

AND USE AN AUTHENTICATOR. AND CHANGE YOUR EMAIL TO A WOW-ONLY ACCOUNT(Change it over the phone, NOT thru the web). AND HAVE A IMPOSSIBLE PASSWORD ONLY FOR WOW. 

DO NOT USE THE EMAIL OR PASSWORD FOR ANYTHING ELSE
Odds are:
[LIST]
[*]You use the same email account for 90% of your online stuff...Forums, etc.
[*]You use the same password for 90% of your online stuff...
[/LIST]
And for a password, use a random password generator that can have a large password, with numbers and symbols.

I've been playing for years, and not one attempt on my account.

---

### Post by hyperAura on 2010-11-20
interesting.. i don't think that this is an inside job though.. as wilson says, probably someone might has seen your password while typing it, if you are using it for most accounts that you have online..

---

### Post by cwwilson721 on 2010-11-20
I forget where the webpage is...(I'll look it up), but a study was done about mail accounts and passwords.

While Blizzard doesn't give out your email address (I KNOW it doesn't, or I'd get spam in my WoW mail), others aren't so nice. And who is to say that out of all the myriads of websites you need a password for, NOT ONE has gotten hacked (or worse, sold their client list and passwords to login to the site), and if you use the same password for WoW as the website....Since the gold sellers make a TON of money from hacked accounts, they just try email addys and passwords...

Thus, if you have an easy-to-crack password (i.e., ANY word in a dictionary, or even worse: qwerty or asdfghjk), all they have to do is random email addresses and a 'dictionary of common passwords. And you get hacked. And they make money.

Which is why you need to change your email address over the phone. If you do it on the web, the Blizzard servers automatically send a confirmation to the old address. And if THAT is already compromised, they now have your new address. Or, decline the change.

---

### Post by Eldorian on 2010-11-20
Thanks for the responses guys. I do not use the same passwords for any account but it appears that my WoW email address was broken into. It seems that once they were in it they could reset the battle.net password and take over my WoW account until I noticed it and reset it again. What I did not know was when they hacked my email address they put in their own backup email which told them when I tried to change my password. I have since cleared all that up and am waiting on the authenticator to come in. Needless to say I am going to use a new email address for WoW which I will tell them over the phone and I have beefed up all my security and passwords. Hopefully that will put an end to the issue and I can learn from it and move onto better things. Thanks again for the help. :)

---

### Post by Tweak42 on 2010-11-20
Just a FYI for US players Blizzard also has a [Dial-in Authenticator](http://us.blizzard.com/support/article.xml?locale=en_US&tag=dialinauth&rhtml=true) that will prompt you dial a toll free number to authorize your login if something different is detected from your normal usage (aka different IP address).

---

### Post by cwwilson721 on 2010-11-20
Actually, I use the Blizzard Mobile Authenticator in a Java app on my computer (NOT in Windows...lol)

Since I bought it for $0.99USD, and if you use it on your phone, if you have to reset the phone, you lose the Authenticator (happened to me 2 days after I installed on my cell phone. 3 hours (2 1/2 spent on hold), and a BIG hassle later, I was back in to my account. I now make a backup of the files that the Java App creates. That way, if anything gets borked, I just replace the folder with the one I have backed up, and I'm back into WoW.

Just my way of keeping things going....

---

### Post by Eldorian on 2010-11-21
Thanks for the info guys. I chose the keyring authenticator cuz if phone service goes down or the wife has it with her I wouldn't be able to play. :D  At least it will be a lot better security than a password alone and that makes me feel safer after all that has happened. I have run every virus scan imaginable as well as rkhunter and still have found nothing on this pc so that also makes me feel a bit safer. Once they had my email account hacked all they did was wait for me to change my battle.net password then go and change it again to something they wanted. I hate hackers but that's no excuse for me being stupid with my email password. :P  Anyway, thanks again. :)

---

### Post by Eldorian on 2010-11-21
Thanks again everyone :)

---

### Post by cwwilson721 on 2010-11-23
You're very welcome.

---

### Post by erusnine on 2011-01-12
I know this post is a few months old, but I felt it important to post and share that I had the exact same experience as the original poster. Something about the way the hacks or Winetricks or whatever that you must perform to install DDO leaves Wine vulnerable to a keyloader spyware. My WoW account was compromised the day after I went through all the mods to Wine to make DDO work. I wiped my machine and started over. It was drastic I know ... but I am one of those people who enjoys reloading my box every so often.

Still I think this is an important thing to note. Installing DDO under Wine leaves your system vulnerable to attack.

Regards,


Jeff Moore

---

### Post by cwwilson721 on 2011-01-12
> **erusnine said:**
> I know this post is a few months old, but I felt it important to post and share that I had the exact same experience as the original poster. Something about the way the hacks or [COLOR="Red"]Winetricks or whatever that you must perform to install DDO [/COLOR]leaves Wine vulnerable to a keyloader spyware. My WoW account was compromised the day after I went through all the mods to Wine to make DDO work. I wiped my machine and started over. It was drastic I know ... but I am one of those people who enjoys reloading my box every so often.

Still I think this is an important thing to note. Installing DDO under Wine leaves your system vulnerable to attack.

Regards,


Jeff Moore

So you installed DDO in the same folder as WoW?

That is fairly silly anyway.

Always try to use a different wine folder for major apps, that way, if you bork it up, or get a keylogger or whatever, [COLOR="Red"]all you have to do is delete the offending wine folder, and NOT YOUR ENTIRE LINUX INSTALL[/COLOR] (This ain't Windows, people. A virus/keylogger, whatever can't get into your main system, so don't reinstall Linux.)

Example: I use a folder called 'wine-wow' for WoW, and a SEPERATE folder for DDO (The standard '.wine' folder that as soon as I am done playing, gets renamed '.wine.ddo'. AND DIFFERENT PASSES AND EMAILS FOR BOTH.

To launch WoW, I use ```
env WINEPREFIX="/home/<USER>/.wine-wow" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```Never had an issue yet.

No keyloggers.
No malware.
No hacks.

So what did YOU do to get them?

---

