---
title: "NSA cracking encryption"
date: 2013-09-05
forum: The Cafe
---

### Post by Amaroq on 2013-09-05
If this is real, then it's very scary.
[http://www.nytimes.com/2013/09/06/us/nsa-foils-much-internet-encryption.html?pagewanted=all&_r=0](http://www.nytimes.com/2013/09/06/us/nsa-foils-much-internet-encryption.html?pagewanted=all&_r=0)

If this is true, then I think the whole tech world needs to know. Spread it around to techie friends and communities. The sooner people know, the sooner it can be countered.

---

### Post by Welly Wu on 2013-09-05
It doesn't surprise me that my former employer can do these things.

---

### Post by TheFu on 2013-09-05
This is old news.  HTTPS is a deck of cards - it can be blown over through relatively easy methods available to governments and network providers.

If you don't want the NSA viewing the stuff you view .... 
* Do not trust anything based on DNS.  No HTTPS.
* Use Truecrypt with non-trivial, long, long passphrases AND a key file.
* Disable all DMA devices in the BIOS - firewire is the biggy, but that new Apple-centric video connection, thunderbolt, is another.  Laptops with PCMCIA and PCIx or PCIe miniports need to be disabled too or at least NOT hot swappable. The real goal here is to force a reboot to access these devices.
* Do not use standby or hibernation.
* Use VPNs with private keys.
* For email, use GPG encryption and PROTECT YOUR PRIVATE KEY MORE THAN YOU PROTECT YOUR WALLET.
* Use ssh with key-based authentication for remote access, if you use ssh.
* Use OpenVPN (never PPTP) for VPN needs.
* Don't use wifi without a VPN.

That's all I have off the top of my head.

Most of these things can be defeated with social engineering attacks, which are easier to accomplish than direct attacks against the encryption.

It should also be known that using whole disk encryption does not necessarily mean we are safe. There are settings to make those products more convenient, but some of those settings completely open the install to being compromised. Google for Tom Kopchak's talk about this.  It has been accomplished - his experience is NOT from some theory, but a real event.

---

### Post by Amaroq on 2013-09-05
Thank you for the useful information!

---

### Post by RichardET on 2013-09-06
There is more than one side to this story and the NY Times simply did an info dump of information it received indirectly through Snowden's leak (They claim they just want a public debate on this topic.  Really??) The more important discussion here, which is never discussed in polite society, is how did Snowden, who DID NOT have direct access to this classified information, actually get access to it?  Apparently the NSA is not very good at internal security and that's very dangerous, because what Snowden did was outrageous and he has definitely weakened our national security.  Whoever let this clown into the room should be brought before Congress.

---

### Post by Welly Wu on 2013-09-06
1. [https://www.schneier.com/blog/archives/2013/09/the_nsas_crypto_1.html](https://www.schneier.com/blog/archives/2013/09/the_nsas_crypto_1.html)

Read this article.

It's from Mr. Schneier not Mr. Snowden.

---

### Post by grahammechanical on 2013-09-06
Americans never cease to amaze me. They watch all these movies about secret government agencies that even the president does not know about and which are doing stuff that is not just illegal but downright criminal, and then they are surprised to find that some of it is true.

If hackers can hack for criminal purposes then corporations and governments can employ people to hack for their purposes. Do not be surprised that laws have been passed to make it legal.

---

### Post by prodigy_ on 2013-09-06
> The agency has circumvented or cracked much of the encryption
So what was it exactly? Cracking or circumventing? Circumventing a broken implementation (or abusing false assumptions) != cracking an encryption algorithm. For example MITM attacks don't rely on cracking encryption.

The article is 5% useful information and 95% FUD.

---

### Post by Welly Wu on 2013-09-06
[http://investmentwatchblog.com/leaked-german-government-warns-key-entities-not-to-use-windows-8-links-the-nsa/](http://investmentwatchblog.com/leaked-german-government-warns-key-entities-not-to-use-windows-8-links-the-nsa/)

This is an interesting article. TPM 2.0 and Windows 8 make PCs vulnerable to the NSA or the Chinese. Hmm? Could it be possible? [sarcasm]..

---

### Post by santosh83 on 2013-09-06
> **Amaroq said:**
> If this is real, then it's very scary.
[http://www.nytimes.com/2013/09/06/us/nsa-foils-much-internet-encryption.html?pagewanted=all&_r=0](http://www.nytimes.com/2013/09/06/us/nsa-foils-much-internet-encryption.html?pagewanted=all&_r=0)

If this is true, then I think the whole tech world needs to know. Spread it around to techie friends and communities. The sooner people know, the sooner it can be countered.

Seems to be another revelation from Whistleblower Snowden. See the very interesting threads on slashdot & Ars Technica on this issue.

Now here's another opportunity for open source software to beat its drums a little and perhaps gain more traction in the wider computing community. From the leaks it seems the frontline strategies of NSA and GCHQ have been to compromise all popular commercial closed source platforms with backdoors (apart from hardware backdoors which we users can't do much about), as well as using a slew of exploits once a specific target is ID'ed. These besides the long-running work to mathematically break encryption, which according to Snowden himself and Schiener, still eludes them for strong encryption algorithms, and subverting the research and standardisation of these algorithms, as well as compromising trusted CAs.

At least as far as backdoors and exploits are concerned, we in the open source community can get together and pledge to use only trusted FOSS alternatives from now on, which will at least make it harder for these guys to compromise, and inform and urge other people to do so as well.

Even though in my entire computing life I've no data which would interest NSA and the like in the least, still as a matter of principle I've decided to use only open source software. In fact I already do since many years, but was even recently considering installing Windows side by side for games, but this revelation of universal backdoors in large commercial software vendors has finally eroded what little trust I had in the closed source proprietary model. Although it is not inherently flawed, it has proven itself to be too easy to bend for the nefarious purposes of nation states.

---

### Post by santosh83 on 2013-09-06
> **TheFu said:**
> This is old news.  HTTPS is a deck of cards - it can be blown over through relatively easy methods available to governments and network providers.

If you don't want the NSA viewing the stuff you view .... 
* Do not trust anything based on DNS.  No HTTPS.

Isn't HTTP also based on DNS?

> * Use Truecrypt with non-trivial, long, long passphrases AND a key file.
* Disable all DMA devices in the BIOS - firewire is the biggy, but that new Apple-centric video connection, thunderbolt, is another.  Laptops with PCMCIA and PCIx or PCIe miniports need to be disabled too or at least NOT hot swappable. The real goal here is to force a reboot to access these devices.
* Do not use standby or hibernation.
* Use VPNs with private keys.

I read in the articles online that popular VPN providers have been compromised as well.

> * For email, use GPG encryption and PROTECT YOUR PRIVATE KEY MORE THAN YOU PROTECT YOUR WALLET.
* Use ssh with key-based authentication for remote access, if you use ssh.
* Use OpenVPN (never PPTP) for VPN needs.
* Don't use wifi without a VPN.

---

### Post by Welly Wu on 2013-09-06
I'd recommend that you find a VPN service provider that offers SSTP VPN protocol as SSL based OpenVPN is already circumvented by NSA. This is not official, but this is the recommendation by the New York Times and ProPublica articles and from Mr. Schneier himself. SSL is not perfect technology and it's quite easy to circumvent its known weaknesses. SSTP is significantly more modern and harder to compromise, but it's primarily designed for Microsoft Windows Server 2008 and 2012 enterprise customers although there are VPN service providers like Astrill and StrongVPN that offer SSTP VPN protocol to Ubuntu GNU/Linux users. I'd choose Astrill VPN over StrongVPN as StrongVPN monitors, records, and logs your network traffic and they will cut off your access to their VPN gateway servers if you do peer to peer file sharing of copyrighted materials. On the other hand, Astrill VPN does not do this. They don't monitor, log, or record your network traffic and they're friendly toward peer to peer file sharing traffic.

CISCO IPSec, PPTP, MS-CHAP v2, etc. are all considerably weaker than SSL based OpenVPN.

If you can find a VPN service provider that allows you to generate your own encryption key, then that's much safer and more secure.

---

### Post by santosh83 on 2013-09-06
> **RichardET said:**
> There is more than one side to this story and the NY Times simply did an info dump of information it received indirectly through Snowden's leak (They claim they just want a public debate on this topic.  Really??) The more important discussion here, which is never discussed in polite society, is how did Snowden, who DID NOT have direct access to this classified information, actually get access to it?  Apparently the NSA is not very good at internal security and that's very dangerous, because what Snowden did was outrageous and he has definitely weakened our national security.  Whoever let this clown into the room should be brought before Congress.

I wouldn't mind sacrificing a tiny amount of national security for not having a totalitarian surveillance state imposed on me, and were critical systems and software that power the Internet (which is now an INTERNATIONAL network) are weakened and subverted. Installing backdoors, forcing keys from CAs, attacking systems with malware and exploits, deliberately weakening research and standardisation of encryption... all these go a bit beyond mere storing of data and attempting to decrypt it! Snowden at least just leaked info, what if someone inside NSA turns evil and misuses these systems to create global chaos?

IMO all this is going to achieve in the medium term is drive business opportunities away from US companies, and in the long term, an escalating cyber war of attrition that may totally destroy the value of the Internet as we know it now.

---

### Post by TheFu on 2013-09-06
> **santosh83 said:**
> Isn't HTTP also based on DNS?
Yes, but NOBODY should trust it for security or privacy at all.

> **santosh83 said:**
> I read in the articles online that popular VPN providers have been compromised as well.

Sorry, I wasn't clear.  It never crossed my mind to trust any 3rd party when a VPN is involved. I run my own and run other VPNs for my companies/clients on hardware that we control.

Further reading has me thinking that OpenVPN/TLS is NOT as secure as we'd want.  Schneier says to use IPSec or forget it.  Looks like it is time to get no the IPv6 effort (which includes IPSec).

Another thing about VPNs - don&#8217;t run them on your home router. It has likely been cracked and the keys taken.  They aren't out to get anyone individually, but if they can create a little script to grab VPN/ssh/gpg keys, why wouldn't they?

Schneier is also very clear - do not trust Microsoft Windows.
I wouldn't trust any smartphone either.

---

### Post by Welly Wu on 2013-09-06
Mr. Schneier uses Microsoft Windows himself, but he did write that Linux is safer. Google Android is very insecure as 79% of malware targets that mobile operating system. The majority of malware targets Microsoft Windows users as well as the fact that both Microsoft Windows and Google Android are the most popular PC desktop and mobile operating systems in the world so plenty of bad actors are targeting both platforms to compromise user accounts and data.

This is why it's much safer and more secure to use GNU/Linux including Ubuntu and this is why I use Ubuntu 12.04.3 LTS 64 bit myself as a former US DoD NSA employee. I'm looking forward to the new Ubuntu smart phones and tablets in late April 2014 and I do plan to purchase both devices when they do become available on the market as I think Ubuntu for mobile devices as a platform is much safer and more secure than Google Android or Apple iOS combined. I think this is the wise strategy to take if I decide to get mobile Internet facing computing devices in the future.

Ubuntu is safe and it's very secure!

OpenVPN is safe and fairly secure if you use a generic CA certificate and not one that's specific to your VPN account. I use Private Internet Access myself and they are very good. They issue a CA certificate for OpenVPN protocol and they anonymize and share VPN IP addresses for their customers. They also use Blowfish 16 rounds 256 bit public cipher for OpenVPN access. Finally, you can specify your DNS server in Ubuntu or virtually any operating system for added safety and security. I'd recommend OpenDNS with a Home subscription if you require filtering capabilities for work or family usage.

Still, SSTP is the best VPN protocol currently available, but it's not built into Ubuntu and you'll have to go to GitHub to download and install the .DEB files for SSTP protocol and the network manager gnome in Ubuntu Unity or GNOME 2 or 3.

---

### Post by Welly Wu on 2013-09-06
[http://www.pcworld.com/article/2048248/heres-how-to-best-secure-your-data-now-that-the-nsa-can-crack-almost-any-encryption.html#tk.fb_pc](http://www.pcworld.com/article/2048248/heres-how-to-best-secure-your-data-now-that-the-nsa-can-crack-almost-any-encryption.html#tk.fb_pc)

---

### Post by TheFu on 2013-09-06
There is a difference between secure today and secure 5, 10, 20 yrs from now.  The NSA is known for capturing encrypted data to work on for 10-30 yrs later.  My data isn't that important, but if I can slow them down for someone else by encrypting everything possible - sign me up.

I think their current data capture methods are against the US Constitution and 99.9999% illegal. Only if signed warrant has been PREVIOUSLY granted by a court with jurisdiction is their data capture legal. All other data capture is illegal. 

I "trust the math" for now, but expect computing power will be exponentially expanding too. 

A 12 character password can be cracked in 24 hrs with sub-$2000 equipment.  To me, that means I need to use a 20+ character passphrase to be good for 10 yrs or so. This assumes that algorithmic and implementation flaws are not discovered.  For high-value data, I'm going to use 40+ character random passphases with multiple different encryption methods (AES and Blowfish) employed.

<snip>

---

### Post by Welly Wu on 2013-09-06
Actually, it is legal for the US DoD and NSA and other agencies, bureaus, etc. to do this kind of thing. It's part of the US Patriot Act and other laws and the FISA courts have determined that the request for signed warrants and search and seizure orders are legal and secret just like National Security Letters.

How else do you think the US government is able to get away with this kind of activity in the first place? It's legal whether you like it or not.

I hate to say this, but your vote is only a single voice. It's going to take money and influence to be able to convince the majority of US citizens to vote out the current incumbents and to vote in newly elected officials that will promise and lie later on to stop this kind of activity.

How do you do checks and balances when you aren't a part of the system?

How do you make the NSA stop it's spying program when it's a part of their mission?

How do you plan to change the system when you've got no money and power to lobby Congress?

Most Americans are not surprised by this news and they've taken it in stride. Convince them that this should be a national issue and get the lobbyists to water down the current laws to an acceptable level and it'll cost you tens of millions of dollars or more. In the end, you won't be satisfied with the results because they won't go far enough to curtail the NSA or US DoD or any other agency.

This is legal and it's an important tool to fight terrorism and criminals.

I'm not defending the NSA completely, but I say that this mass surveillance is a necessary evil and it's prevented Americans from getting injured or killed for the most part. It's stopped lots of terrorism related behavior in investigations and it's been effective in preventing or disrupting other criminal activities.

If you don't like it, then tough. Move to another country and renounce your US citizenship. You'll have to pay the IRS their share of taxes as a result, but that's on you.

I think that this is an important tool against the war on terror and drugs and child porn and illegal human and arms trafficking and other nefarious behavior.

If this is too political, then close this thread.

---

### Post by Welly Wu on 2013-09-06
What do you have to say to elected officials to stop this mass surveillance program by the US government when they are the ones that receive the classified briefings and documents showing the effectiveness of these secret programs to stop terrorism and criminal activities?

How do you convince an elected official to put a stop to these secret surveillance programs when he or she is thinking in the back of his or her mind that doing so may cause another September 11th, 2001 terrorist attack on the US homeland?

What other alternatives do you have in mind that you're willing to hire lobbyists and spend tens of millions of dollars in public awareness advertisements to convince Americans that something better can replace these secret surveillance programs?

Are you going to take personal responsibility for the consequences of putting and end to these surveillance programs? If there's another terrorist attack that gets Americans injured or killed because these secret surveillance programs were outlawed, then do you take responsibility for contacting the victim's families?

What if Mr. Murphey shows up and unintended consequences happen?

Did you really think this through carefully enough?

---

### Post by QIII on 2013-09-06
This thread has gone from discussion of a political development's effects with regard to information systems and technology into a purely political conversation.

*Thread **Closed.***

---

