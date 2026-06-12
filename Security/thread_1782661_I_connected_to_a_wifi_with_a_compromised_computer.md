---
title: "I connected to a wifi with a compromised computer"
date: 2011-06-14
forum: Security
---

### Post by Libertydude on 2011-06-14
Some of you may remember me from my last thread, but anyway here is what happened, I connected to the wifi (with a compromised computer also connected) and opened firefox and did not login to my email (but I do have the passwords saved). All I did was open firefox and do a quick google search, is there anyway my passwords could have been compromised? Or do I have to login?

PS thanks for letting me ask a lot of questions here. :)

---

### Post by Libertydude on 2011-06-14
Anybody know?

---

### Post by cariboo on 2011-06-15
If I remember from your last thread, you didn't really prove that the other system had been compromised. The only way to tell if your email account has been compromised is to login. If you have a strong non-dictionary password you shouldn't have a problem. 

If you have a weak dictionary password, your system doesn't need to be compromised for someone to guess it.

---

### Post by Libertydude on 2011-06-15
> **cariboo907 said:**
> If I remember from your last thread, you didn't really prove that the other system had been compromised. The only way to tell if your email account has been compromised is to login. If you have a strong non-dictionary password you shouldn't have a problem. 

If you have a weak dictionary password, your system doesn't need to be compromised for someone to guess it.
Okay, I just scaned the other computer and avast did find some things, but I am very sure it did not get everything.

And my question basically is: I didn't login into my email with her laptop connected, but since I have the passwords saved in my firefox, could her compromised laptop somehow steal my passwords?

I know... I sound like such an idiot who does not know anything.

---

### Post by cariboo on 2011-06-15
The short answer is no, if you don't have samba installed, Windows can't see any shares on a Linux based computer.

---

### Post by Libertydude on 2011-06-15
> **cariboo907 said:**
> The short answer is no, if you don't have samba installed, Windows can't see any shares on a Linux based computer.
But could the compromised computer sniff my data through the router?

---

### Post by Libertydude on 2011-06-15
Does anybody even understand my question?

Sorry if I sound dumb. :(

---

### Post by spynappels on 2011-06-15
Dude, what protocol would the "infected" computer use to sniff the passwords if you did not submit them by logging in?

As Cariboo said unless you shared your file containing your saved passwords using Samba or other protocol, you are fine. 

And as Cariboo pointed out, the fact that the other computer was infected was not established.

If you are really worried about sniffing from the other computer, assuming it is compromised, tunnel all your traffic to and from the internet through a SSL VPN and all a "sniffer" will see is encrypted traffic. Unless you open your system to outside access, anything on there is safe from the "sniffer".

---

### Post by Libertydude on 2011-06-15
> Dude, what protocol would the "infected" computer use to sniff the passwords if you did not submit them by logging in?

This is what I was asking, I was wondering if when I opened firefox it automatically transmitted my passwords to log me in.

> And as Cariboo pointed out, the fact that the other computer was infected was not established.
I did establish this fact, I ran avast and it found 3 trojans, but I am sure it did not get everything.

> If you are really worried about sniffing from the other computer,  assuming it is compromised, tunnel all your traffic to and from the  internet through a SSL VPN and all a "sniffer" will see is encrypted  traffic. Unless you open your system to outside access, anything on  there is safe from the "sniffer".
How do I do this? And can the VPN service see my traffic?

---

### Post by emiller12345 on 2011-06-15
download and burn to CD:
```
http://support.kaspersky.com/viruses/rescuedisk
```
, fix the compromised computer in order to put your mind at ease.

---

### Post by BkkBonanza on 2011-06-15
If you didn't access your account and submit your password to login then it's very unlikely that your passwords would be compromised. The other computer would have to get access to your system to get that password file.

But two points I wanted to make. 

1. Your email login should only occur over an SSL connection. If you are using a email site or program that sends the password in the clear (non SSL) then you would be very advised to change to some other email service that supports secure connections for login.

2. If you are still worried about it then be safe: get a secure connection and change your password. Make sure it's a strong password. 

I don't really trust the FF password safe. It may be fine but I prefer to have all my passwords under my own control with strong encryption. I believe Keepassx to be good for this. I've used it for years and I have hundreds of passwords stored in it. The only downside is that it isn't as automatic as FF - but that's also an upside as I always know when I'm submitting a password. 

And I know which file contains them and I can back that up in several places as it would be a real bummer if somehow my password safe got corrupted/lost or trashed by FF somehow with no backup.

---

### Post by Libertydude on 2011-06-16
> **BkkBonanza said:**
> If you didn't access your account and submit your password to login then it's very unlikely that your passwords would be compromised. The other computer would have to get access to your system to get that password file.

But two points I wanted to make. 

1. Your email login should only occur over an SSL connection. If you are using a email site or program that sends the password in the clear (non SSL) then you would be very advised to change to some other email service that supports secure connections for login.

2. If you are still worried about it then be safe: get a secure connection and change your password. Make sure it's a strong password. 

I don't really trust the FF password safe. It may be fine but I prefer to have all my passwords under my own control with strong encryption. I believe Keepassx to be good for this. I've used it for years and I have hundreds of passwords stored in it. The only downside is that it isn't as automatic as FF - but that's also an upside as I always know when I'm submitting a password. 

And I know which file contains them and I can back that up in several places as it would be a real bummer if somehow my password safe got corrupted/lost or trashed by FF somehow with no backup.
I actually store my passwords in a text file. But I look at it this way, if someone compromises my computer, I am screwed anyway.

---

### Post by BkkBonanza on 2011-06-16
> **Libertydude said:**
> I actually store my passwords in a text file. But I look at it this way, if someone compromises my computer, I am screwed anyway.

I wouldn't look at it like that though. If the file is encrypted then someone can steal your computer and they don't get all your passwords for all your sites... which is a big bonus in my book. 
[URL="http://www.keepassx.org/"]
Keepassx[/URL] is in the repos and easy to install and use. It uses AES/TwoFish encryption (if I recall, could be something else). I have it assigned to a hotkey so on any site I can just Ctrl-WinKey (good use for that useless key) and it pops up.

I also have an encrypted home folder (easy to setup) so if the notebook gets stolen no one (even with root/physical access) can get into it. So my passwords are encrypted by Keepassx and with encryptfs below that. I consider this an easy to setup and easy to use minimal security level.

Another bonus is Keepassx has a pwd generator built in so with one click I can create a 20 char (or whatever) strong random password and link/save it for that site. I actually wish it had a stronger encryption but regardless, if it's also encrypted via encryptfs it should be fine. It's better than nothing.

---

