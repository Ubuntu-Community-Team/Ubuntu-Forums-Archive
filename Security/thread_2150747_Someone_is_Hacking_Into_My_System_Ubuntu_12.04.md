---
title: "Someone is Hacking Into My System Ubuntu 12.04"
date: 2013-06-02
forum: Security
---

### Post by MissNails on 2013-06-02
Hello, 

I just had a security breach..... I received an email that my Yahoo account has been visited by another computer with a different IP address than mine. I haven't been anywhere else but at my home computer, and this REALLY concerns me. I don't know if my security has been compromised because I downloaded OpenVPN without finishing the process... I just got rid of my wine application off my computer. I have a HP Pavilion computer that runs Ubuntu 12.04. Please help! 

Thanks!

(Oh...And if anybody knows how to set up and use the OpenVPN Server.....I would like some tips. :D)

---

### Post by carl4926 on 2013-06-02
Sounds like a [COLOR=#000000]Phishing email
Probably not from Yahoo at all

People access their Yahoo accounts from all over the world. I do.

Don't reply to it

And stop worrying[/COLOR]

---

### Post by mr-woof on 2013-06-02
Log into yahoo (but not via any links in mails), click on account info and you can view your recent sign in activity. Anything look iffy?

If yes, change your passwords.

---

### Post by ajgreeny on 2013-06-02
> **mr-woof said:**
> Log into yahoo (but not via any links in mails), click on account info and you can view your recent sign in activity. Anything look iffy?

If yes, change your passwords.

There have been several yahoo email hacks recently; I have received emails supposedly from friends with yahho mail accounts, but with nothing more than a website link; no covering message or anything else.  On having copied the domain name from these links and googled them, I find they are nearly all likely to be spam advertising messages from companies in the USA.

Change your password even if there is nothing worrying in your logs; it's a good idea to do so occasionally.

---

### Post by ShadowVegan on 2013-06-02
Two possible answers:
1) Someone hacked your Yahoo.
2) The email is fake.

If the email is fake it's just a phishing scam. Delete and ignore it. If someone hacked your Yahoo, of course you have to change your password, but also consider how they hacked it. Are your security questions weak? If so, change them. Is your password weak? If so, make it stronger next time. Are you potentially infected with a keylogger? Scan your system. If you are infected, make sure to change your account information AFTER removing the keylogger.

---

### Post by Hungry Man on 2013-06-02
Yahoo is not particularly secure. I suggest changing the password immediately to something strong; unique and at least 10 characters.

---

### Post by MissNails on 2013-06-02
ummm......The email wasn't fake, so I changed my password. How can I check for a keylogger? I think I need to make my security more strong...

---

### Post by Soul-Sing on 2013-06-02
openvpn is used for what? You just downloaded it for no reason at all? Openvpn is also often used as an ip-changer, or for a vpn service that uses openvpn. If you did use openvpn in combination with a VPN service, then you get these emails because your ip address is changed. (by yourself)

---

### Post by ShadowVegan on 2013-06-02
> **MissNails said:**
> ummm......The email wasn't fake, so I changed my password. How can I check for a keylogger? I think I need to make my security more strong...

Assuming you are using Ubuntu, you can use ClamAV. Keyloggers are primarily an issue with Windows but that doesn't mean it's impossible. I would guess someone just brute forced the password or answered recovery questions (make sure to make the recovery questions secure) but to run a scan, first you have to install clam AV. Open a terminal (ctrl+alt+T) and enter:
```
sudo apt-get install clamav
```
After installation, enter
```
sudo clamscan -r --bell -i /
```

There's also programs to detect rootkits such as chkrootkit and rkhunter.

---

### Post by MissNails on 2013-06-03
Thank you ShadowVegan.... 

@Soul-Sing: I downloaded OpenVPN when I  was in the middle east because I was trying to find ways to not be  blocked from certain websites. But they also blocked the help page and  any other website that told me how to manage the server. They also  blocked IP adresses and other useful information. So, in my ignorance, I  could have changed my IP address? It's possible.

---

