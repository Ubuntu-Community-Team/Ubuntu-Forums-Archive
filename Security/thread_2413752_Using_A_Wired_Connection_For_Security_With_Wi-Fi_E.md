---
title: "Using A Wired Connection For Security With Wi-Fi Enabled"
date: 2019-03-01
forum: Security
---

### Post by John_Patrick_Mason on 2019-03-01
Hi everybody,

It was while reading about security that I learned that people  should use an Ethernet connection whenever possible not only for  performance reasons, but also because it prevents people from snooping  on your traffic without physical access to your computer/router. But is  that still true if you still have devices on your network that are  connected to your router using Wi-Fi, i.e. phones? Can somebody still  snoop on the traffic of your wired connection if you have devices that  use Wi-Fi?

---

### Post by CharlesA on 2019-03-01
Assuming you are using WPA2 with AES (not TKIP), they can capture packets from the air and look at them, but they are encrypted, so it is unlikely they will be able to read the contents.

If you have devices communicating via Wifi, only the wifi traffic is exposed. If an attacker was able to obtain your passphrase and connect, they would have access to your entire network.

I have two main wifi network - a main one that allows access to my NAS and the internet, and a guest one that only allows access to the internet. The main one has a nasty passphrase on it, and the guest one has an easy to remember passphrase.

As long as you have a strong passphrase and are using WPA2 with AES encryption, you should be fine.

---

### Post by John_Patrick_Mason on 2019-03-02
[QUOTE=CharlesA]Assuming you are using WPA2 with AES (not TKIP),  they can capture  packets from the air and look at them, but they are  encrypted, so it is  unlikely they will be able to read the contents.[/QUOTE]

Can't they still know which website you visit, though? I thought  visiting an HTTPS website meant that they couldn't read the contents of  the page you're on, or intercept your search queries, or login  credentials, but they could still find out which website you're on. Is  that also true of ISPs? What about using free Wi-Fi at public places?  Does an attacker have to be connected to your network to capture packets  originating from your computer or can he/she intercept packets without  having access to your Wi-Fi password?

[QUOTE=CharlesA]If you have devices communicating via Wifi, only  the wifi traffic is  exposed. If an attacker was able to obtain your  passphrase and connect,  they would have access to your entire network.
[/QUOTE]

By "passphrase" you mean my router password, not my Wi-Fi password, correct?

---

### Post by CharlesA on 2019-03-02
> **John_Patrick_Mason said:**
> Can't they still know which website you visit, though? I thought  visiting an HTTPS website meant that they couldn't read the contents of  the page you're on, or intercept your search queries, or login  credentials, but they could still find out which website you're on. Is  that also true of ISPs?

An ISP can see all your traffic unless it's encrypted. That is partially why VPNs are popular - they encrypt your traffic, so your local ISP can't read it, but you also have to trust whatever provider and end-point you are using.

However, security and privacy are two different things in this context. You can be secure without using a VPN, but your ISP might collect usage data from you if you use their DNS servers, for example.

> **John_Patrick_Mason said:**
> What about using free Wi-Fi at public places?  Does an attacker have to be connected to your network to capture packets  originating from your computer or can he/she intercept packets without  having access to your Wi-Fi password?

You can capture anything out of the air without having to connect to the network, but you will be unable to read the data unless you know the encryption key used by the network. If you are connecting to an open wifi network, you should use something like a VPN or SSH tunnel to tunnel your traffic so it isn't exposed. If a wifi network has no security enabled, everything is set in the clear and no encryption is used. That is why a VPN or other tunnelling method is a good idea. HTTPS traffic will still be encrypted, but DNS generally is not so you could be in danger of a spoofing attack or other Man in the Middle attack if you connect directly to an open wifi network.

In summary, everything has risks, but you need to decide if the risks are worth taking or if they do not apply to you. Connecting to your own private wifi network with a strong passphrase is less risky than connecting to an open wifi network.

> **John_Patrick_Mason said:**
> By "passphrase" you mean my router password, not my Wi-Fi password, correct?

No, the passphrase is the pre-shared key you use to secure your Wifi. Your router password should be different from that.

---

### Post by John_Patrick_Mason on 2019-03-02
[QUOTE=CharlesA]If you are connecting to an open wifi network, you should use something  like a VPN or SSH tunnel to tunnel your traffic so it isn't exposed.[/QUOTE]

By an open Wi-Fi network I'm assuming you mean Wi-Fi networks that don't require a Wi-Fi password to connect to the network, right?

[QUOTE=CharlesA]If a wifi network has no security enabled, everything is set in the  clear and no encryption is used. That is why a VPN or other tunnelling  method is a good idea. HTTPS traffic will still be encrypted, but DNS  generally is not so you could be in danger of a spoofing attack or other  Man in the Middle attack if you connect directly to an open wifi  network.[/QUOTE]

And, how would a spoofing attack be carried out? Would they need to log in to the network's router and modify the IP address of the DNS server, in order to carry out such an attack?

Also, why isn't the connection between your router and your computer encrypted? When I log in to my router, instead of seeing a green padlock next to the IP address of my default gateway, I get a padlock with a red strikethrough. If there were rogue devices on my network, wouldn't they be able to intercept my login credentials when I decide to log in to my router?

---

### Post by CharlesA on 2019-03-02
> **John_Patrick_Mason said:**
> By an open Wi-Fi network I'm assuming you mean Wi-Fi networks that don't require a Wi-Fi password to connect to the network, right?

That is correct.

> **John_Patrick_Mason said:**
> And, how would a spoofing attack be carried out? Would they need to log in to the network's router and modify the IP address of the DNS server, in order to carry out such an attack?

There are many ways to perform a DNS spoofing attack and that is one of them. You can read about some of them here: [https://doubleoctopus.com/security-wiki/threats-and-tools/dns-spoofing/](https://doubleoctopus.com/security-wiki/threats-and-tools/dns-spoofing/)

> **John_Patrick_Mason said:**
> Also, why isn't the connection between your router and your computer encrypted? When I log in to my router, instead of seeing a green padlock next to the IP address of my default gateway, I get a padlock with a red strikethrough. If there were rogue devices on my network, wouldn't they be able to intercept my login credentials when I decide to log in to my router?

If you are talking about connecting to the router's interface directly, that depends on the router. Some of them give you the ability to load into them via HTTPS, but some don't or they aren't enabled by default. You will still get a security error if you connected to them in this configuration because they use a self-signed certificate, which isn't trusted by your browser. You can add it as an exception, but I think it will still show up as insecure in the address bar.

---

### Post by John_Patrick_Mason on 2019-03-02
Assuming the connection between my computer and my router is encrypted,  albeit with a self-signed certificate that provides enough information  to later identify the certificate, if I decide to log in to my router  again, and I have a rogue device on my network, can an attacker spoof the login page of my router with a certificate containing the same information, thereby potentially tricking me into giving away my router login credentials, or would the certificate contain different information allowing me to check the certificate before I input my information?

---

### Post by CharlesA on 2019-03-03
If you have a rogue device on your network, you have more to worry about than its ability to trick you into logging into a fake login page.

You really should do your own research on this as there are plenty of sources out there that cover this sort of attack.

This is one example: [https://www.veracode.com/security/man-middle-attack](https://www.veracode.com/security/man-middle-attack)

---

### Post by SeijiSensei on 2019-03-03
Maybe I'm naive, but I don't think any of these scenarios are sufficiently plausible to take seriously. 

Some of my machines are hard-wired, some use wifi. I use WPA2 with a long, complex passphrase. I don't worry about my traffic being compromised using either technology.

Yes, your ISP could compile a list of sites you visit. Why would they bother unless they have been served a warrant alleging you're up to no good? 

If you want to protect against aggregation of your DNS queries, run your own DNS server (I do).

HTTPS encrypts the traffic as it leaves your browser, and it is decrypted at the web site. Sniffing those packets would do you little good as Charles says above.

Frankly I'd say the most significant security policy everyone should implement is to stay the hell away from Facebook. So glad I never signed up there.

---

### Post by CharlesA on 2019-03-03
> **SeijiSensei said:**
> Maybe I'm naive, but I don't think any of these scenarios are sufficiently plausible to take seriously. 

I wouldn't call that naive. It is more likely to be used as a targeted attack and not something the majority of people would ever run into.

---

### Post by John_Patrick_Mason on 2019-03-03
[QUOTE=CharlesA]If you have a rogue device on your network, you have more to worry about  than its ability to trick you into logging into a fake login page.

You really should do your own research on this as there are plenty of sources out there that cover this sort of attack.

This is one example: [https://www.veracode.com/security/man-middle-attack](https://www.veracode.com/security/man-middle-attack)[/QUOTE]

OK, I read up on a couple of the links you provided. Let's suppose I have a rogue device on my network, the rogue device can:

1)  Use HTTPS spoofing using [Punycode]("https://arstechnica.com/information-technology/2017/04/chrome-firefox-and-opera-users-beware-this-isnt-the-apple-com-you-want/") to create a domain that looks very  similar to the URL a person is interested in. I'm guessing the way to guard  against this, would be to check the detailed information contained in the certificate.

2)  Redirect the potential victim to a bogus site that infects the victim's  browser in a drive-by download by exploiting a vulnerability within the  browser that allows the attacker to steal a session cookie. To redirect a  victim's computer to a bogus website in 1) and 2), does the attacker need to modify  the IP address of the DNS server or can the attacker redirect a victim's  computer to a bogus website without having access to the router?

3)  Use a [cross-site scripting attack]("https://doubleoctopus.com/security-wiki/threats-and-tools/session-hijacking/") where the attacker tricks a browser  into running code that is treated as trustworthy because it appears to belong to the server, but ends up stealing the victim's session cookie for the attacker.

4) The person decides to log in  to a website,  that might use encryption on the login page, but does not use encryption  for the rest of the site once authenticated, thereby allowing the  attacker to steal the victim's session cookie by sniffing packets and  impersonate him ([side jacking]("https://doubleoctopus.com/security-wiki/threats-and-tools/session-hijacking/")), even if the password itself isn't compromised. Is  this one of those websites said to have "mixed" content? Wouldn't this  website appear with a gray padlock with a yellow warning sign next to the  address bar in FF?

Is that all?

So if a rogue device is connected to a network, it might be able to gain *access* to somebody's online account without necessarily gaining access to a user's password, and possibly even gain access to somebody's password as described in paragraph 4, if the stolen session cookie contains the user's [unencrypted password]("https://www.veracode.com/security/man-middle-attack").

---

