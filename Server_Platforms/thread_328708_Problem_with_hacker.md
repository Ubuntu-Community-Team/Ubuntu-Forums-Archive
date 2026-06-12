---
title: "Problem with hacker"
date: 2006-12-31
forum: Server Platforms
---

### Post by Tasidious on 2006-12-31
I had an issue 2 months ago with a hacker who told me that he hacked my windows system and that he got all of my passwords.I decided to install Ubuntu for better protection but he made his appearance again and he said that he cracked Ubuntu as well.(Our conversation was taking place via PMs in a forum).I dont know what to do anymore.How can i improve security in Ubuntu?Is there anything i can do?I have Firestarter installed and i also have a router with a built in NAT firewall.I changed my root password but i dont know if he is still able to get in.How can i find out?He may still be in my system stealing information and i cant do anything to stop him?Please give me some advice....

PS.I have stopped talking to him since i installed Ubuntu but he edited his signature so as to let me know that he hacked Ubuntu.

---

### Post by Peter76 on 2006-12-31
If you changed your passwords for your Ubuntu installation and did not activate any services ( ssh, ftp, apache ), There's no way he could have gotten in your computer afaik....
Probably someone who wants to piss you off

---

### Post by kvonb on 2006-12-31
When you are online, open the firestarter window, the main window has a list of all current connections, don't run anything and see if there are any connections, if not then he is winding you up.  Can this person give you any REAL proof that he can get into your system?  It's extremely unlikely.  You could invite him to give you proof, keep an eye on the connections window in Firestarter, write down the IP adress that you think is him, then in a console type whois <his IP address>, it will tell you his ISP, send an email to them complaining that this person is illegally accessing your computer and you want it stopped.  He might be getting into your router, you need to change the password for that also.  I would install "nessus": and scan his computer when he says he is doing it, just to scare him, of course you will need his IP.
Regards, Kev :)

---

### Post by Tasidious on 2006-12-31
He sent me a pm in a new forum where i use a new account.How could he possibly know my nick name!He says that he is watching my every move, what im downloading, what online purchases i make!He says that by using linux i made his life easier.He gets in easier!You advised me to have a password in my router.I dont have one.Should i have a password?I dont know what to do really.....:-k :-?

---

### Post by chrisfay on 2006-12-31
> He says that by using linux i made his life easier.He gets in easier

:p .....I needed that

This guy is gett'n  off on your paranoia. I guarantee he won't provide an ounce of proof that he penetrated your system. Why? Because he didn't....simple as that.

---

### Post by FyreBrand on 2006-12-31
> **Tasidious said:**
> He sent me a pm in a new forum where i use a new account.How could he possibly know my nick name!He says that he is watching my every move, what im downloading, what online purchases i make!He says that by using linux i made his life easier.He gets in easier!You advised me to have a password in my router.I dont have one.Should i have a password?I dont know what to do really.....:-k :-?Make sure you always use different passwords for different forums and that they are different from any password on your system.  He might be hacking the forums and getting information that way.  Make sure you report him to the forum admin so they can track him.

Make sure you're at least doing the following with your passwords:
1. Use different passwords for each forum or at least that they are different from other online account passwords (ie: amazon, banking, etc).  Make sure that your forum account passwords are different from your system passwords (your admin or root accounts).

2. Never use real dictionary words in your password; that is any word in the dictionary.  Never use birthdates or other personal numbers.

3. Try and make your password a decent length.  8 characters or more is good and more than 15 characters is great.

4. Use passwords that are acronyms or words that can be spelled using special characters and numbers.  Always included special characters and numbers in a password.  For example lets say you create a password from the word community.  It could be written as:
C@2mUn1%y.  Maybe not the best example, but it illustrates the point.  An acronym example could be: **M**y **B**ig **P**ickup **U**ses **T**oo **M**uch **G**as.  The acronym is MBPUTMG.  We want to mix up the case of the letters and add some numbers and characters.  So it could be M13p@TMG.  Again I'm sure there are better examples that transliterate better, but the example is just to illustrate the point.

About forum accounts.  If the security of the forum is dubious then never use reliable personal information.  Use a fake or nick first name and then a real last name or use a totally fake name period.  Never input your address or location.  Use a proxy email such as gmail or yahoo and never use the email associated with your ISP.  Go to your forum account and make sure that none of your information is visible to others.

This joker likely got the info from poor forum security or by reading your profile.  Delete your user account or if that isn't allowed by the forum; contact the forum admin, explain your problem and ask them to delete them for you.  Then create a new account with this fake information.

Additionally make sure that no one at work, school, or your personal activities or organizations has access to your accounts or information.  It could be that this person is getting your account info from your work or school computer.

Start out-thinking this bonehead.  This person is a jerk that is getting off on scaring people.  Don't give them the satisfaction.

---

### Post by meng on 2006-12-31
1. He's not a hacker at all. If anything, he's claiming to be a CRACKER.
2. I also suspect he's just scaring you. Don't take the bait. Continue ignoring him.
3. Those password tips above are pretty good advice.

---

### Post by Hendrixski on 2006-12-31
Jesus Christ, sometimes linux enthusiasts are their own worst enemy. Is Linux more secure? Yes. What does that mean to someone who wants to steel people's financial data?  It doesn't mean ****.  "where there's a will there's a way"

It's not impossible to hack Linux.  Security is not just a software issue, it's an issue of the way it is used.  You may be doing something that allows someone access to your system.  Perhaps it's someone that you know and may have told your password to, or someone who may have seen it wherever you wrote it down (if you throw it in the trash it's not gone, someone can read it from your garbage can).   Perhaps someone tapped your internet line (the same way that the CiA can now do without a warrant) and reads whatever you're sending through.  

These are all security things that have nothing to do with the Operating System, they're "social engineering".

Here's my advice:  CALL EXPERION, TRANS-UNION, YOUR BANK, ETC.  AND TELL THEM THAT YOU SUSPECT SOMEONE IS SNOOPING YOUR PERSONAL INFO.  THEY WILL THEN PUT YOU ACCOUNT UNDER SURVEILLANCE FOR SUSPICIOUS ACTIVITY, AND WILL CALL YOU WHENEVER THEY SEE SOMETHING EVEN REMOTELY SUSPICIOUS.  This won't effect your FICO score, don't worry, and it's free.  But it will protect you if someone does something.  you can call and have them remove it after a month or two when you feel safe again.

and of course listen to the advice about passwords above, it's 100% correct.

Hope this helps, don't hesitate to alert your bank.  Identity theft is the #1 computer crime today.

---

### Post by jbus on 2006-12-31
He could be a neighbor sniffing your wireless traffic, if you have a wireless network. Meaning he could gain access to any unencrypted communication over your connection regardless of your OS.

What kind of security do you use on your wireless network?

---

### Post by meng on 2006-12-31
I don't want to promote a FALSE sense of security here, but a real cracker wouldn't tell you that your system had been cracked, and someone about to commit identify theft wouldn't advertise the fact either.

---

### Post by BLTicklemonster on 2006-12-31
DON'T use wireless. (wireless is nature's way of saying, "I'm bent over here, come and get me" )

DO get a router with a hardware firewall.

---

### Post by tturrisi on 2006-12-31
> **Tasidious said:**
> You advised me to have a password in my router.I dont have one.Should i have a password?I dont know what to do really.....:-k :-?
If you have a router then there's no way he's cracking your computer UNLESS you were tricked into installing a program that gives a remote user access.  This is very common in windows because many people have backdoor trojans installed that are easily detected remotely by a cracker.

However, you definitely should have a password on your router because the default manufacturer router access username & passwords are well known.

Let's say you have a linksys router and your router has "remote management" enabled..  All someone needs then is your ip address and they can login to your router control panel using the password "admin".  Once there, they could view the linksys logs and see what sites you visit.  They could also see the name of your computer.  Windows users with unpassworded routers also use the default Windows network name, eithe MSHOME or WORKGROUP and also will have File & Print Sharing enabled.  Someone could then connect to your network shares easily and place a trojan there that the user will click to execute.  Once that done, he could gain full control of the computer.

SET A PASSWORD FOR YOUR ROUTER!!!!!!!!!!!!!!!!!!!!!

---

### Post by chrisfay on 2006-12-31
This thread is hilarious.... 

> I don't want to promote a FALSE sense of security here, but a real cracker wouldn't tell you that your system had been cracked, and someone about to commit identify theft wouldn't advertise the fact either.

I couldn't agree more....

---

### Post by squibT on 2006-12-31
If you are using wireless via your router use WPA PSK with minimum TKIP (AES is better). Do not use WEP. Use a 64 character HEX key on your router as a wireless PSK....you can cut and paste it into your clients.

Change the default SSH port if you are using SSH. And use an RSA key and/or Putty to access it.

Turn on HTTPS for admin access also. You can use a different port here also.

Change the default IP address and range  also.

Do use a complicated router password as was mentioned.

squibt

---

### Post by rbhigday on 2006-12-31
this person knows you and is messing with you. like stated before no real cracker or thief would make them self known. This means who ever this is has a grudge against you or something to gain if you go crazy or let his scare tactics effect you life.

Change you passwords, do the identity thief protection if nothing else but for peace of mind and get on with you life.  sooner or later he will bore of his game and move on. Reactions are what he is looking for, thus do not give him any and just ignore him once you protected yourself by the ways mentioned already.

---

### Post by wieman01 on 2007-01-04
Not sure if this thread is still valid or open... however, I suspect that this person has cracked your wireless network. Are you using WEP protection by chance? If so, it is likely your network's security has been compromised and that someone is using "sniffing tools" to eavesdrop on you. I don't want to meet trouble halfway, but this is all within the realm of possibility. 

Use WPA2 encryption/authentication instead to avoid this sort of trouble as SquibT has pointed out.

---

