---
title: "how do we defend against compromised ISOs?"
date: 2016-11-27
forum: Security
---

### Post by ardouronerous on 2016-11-27
As we all know, Linux Mint's website was hit by a hacker that not only changed ISOs hosted on their site into ISOs modified with a backdoor, but also changed the checksums on the site as well to trick users into thinking that they download a legit Linux Mint ISO.

This is scary, and this could happen to Ubuntu and it's various flavors.

How do we defend against such thing?

---

### Post by alexjpowell on 2016-11-27
Build your own linux if it's that important

---

### Post by HermanAB on 2016-11-27
For starters, make your own mirror server.  (This step is surprisingly easy, the rest not.)

Then gradually increase your level of testing and verification to satisfy your required level of paranoia.

Note that you are not paranoid, if they are really out to get you...

---

### Post by untrustytahr on 2016-11-27
The hash files are all signed by the ubuntu signing key. 

```
gpg --list-key EFE21092
pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>


```

Even if someone hacked the server to change the iso's and hashes, the key (which shouldn't be on the server) would be needed to create new signatures on the hashes.  Otherwise, the signature check will fail on the hashes and you know you couldn't trust them to be correct.

---

### Post by bearlake on 2016-11-27
Easy, read these. [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") and [SHA256SUM]("https://help.ubuntu.com/community/HowToSHA256SUM").

---

### Post by ardouronerous on 2016-11-27
> **alexjpowell said:**
> Build your own linux if it's that important
> **HermanAB said:**
> For starters, make your own mirror server.  (This step is surprisingly easy, the rest not.)

Then gradually increase your level of testing and verification to satisfy your required level of paranoia.

Note that you are not paranoid, if they are really out to get you...

I ain't that tech-savy enough to do that, hell, after 5 years of using Xubuntu, I'm still intimated by the Terminal, but believe me, I wish could build my own Linux OS and server.

> **untrustytahr said:**
> The hash files are all signed by the ubuntu signing key. 

```
gpg --list-key EFE21092
pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>


```

Even if someone hacked the server to change the iso's and hashes, the  key (which shouldn't be on the server) would be needed to create new  signatures on the hashes.  Otherwise, the signature check will fail on  the hashes and you know you couldn't trust them to be correct.

Okay, I wonder why the Linux Mint hacker was able to get away what he did?

> **bearlake said:**
> Easy, read these. [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") and [SHA256SUM]("https://help.ubuntu.com/community/HowToSHA256SUM").

The hacker was able to change the Hash information on Linux Mint's site.

---

### Post by Habitual on 2016-11-27
> **ardouronerous said:**
> As we all know, Linux Mint's website was hit by a hacker that not only changed ISOs hosted on their site into ISOs modified with a backdoor, but also changed the checksums on the site as well to trick users into thinking that they download a legit Linux Mint ISO.

This is scary, and this could happen to Ubuntu and it's various flavors.

How do we defend against such thing?
"As we all know" in February of 2016.
Defense is [verify]("https://linuxmint.com/verify.php")
Not as scary as a torrented pirated version of Windows and folks do/did those things.

Things are better now.
You do verify, right?

---

### Post by ian-weisser on 2016-11-27
There is no magic bullet. Good security is a set of good habits, vigilance, and a community.

The Ubuntu QA Team welcomes more [ISO Testers]("https://wiki.ubuntu.com/Testing/ISO/"). If you wish to add an explicit check of the key to the list of tests, please join the team.

If you wish to create and run a daily explicit check of the download source to test for a hacked site, please contact Canonical IS (or the appropriate mirror admin) before running your bot against their site.

---

### Post by DuckHook on 2016-11-27
In my opinion, your concern is legitimate. The Mint site was hacked in such a fashion that the checksums were also bogus. Since most users don't even bother to checksum their ISO after it is burned, it is not particularly hard to buffalo users who seem determined to be unwary. In this particular case, even the more wary would have been led astray.

But it is also important to understand what actually happened in the Mint case. Mint itself was not compromised. What the cracker did instead was hijack Mint's website and replace it with the cracker's own. Therefore, users were not downloading *hacked* OSes, but rather, *bogus* OSes. This is an important distinction. A hacked OS is truly spooky because it means that the real OS is debased, whereas in the Mint case, the real OS never lost its integrity--users were just redirected to a false one. The saving grace in this scenario is that security measures such as kernel signing and distributed authentication were not compromised. It was only users who downloaded from the bogus site that got bad ISOs.

For two differing opinions on the Mint incident:

[http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/](http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/)
[http://www.ocsmag.com/2016/04/09/linux-mint-security-28-days-later/](http://www.ocsmag.com/2016/04/09/linux-mint-security-28-days-later/)

The second article puts things in a rather more balanced perspective, but both are informative.

From a practical standpoint, the measures recommended in the second article will help. Surprisingly, one better method for downloading ISOs is not mentioned in that article, and that is, to torrent them. Torrents continually checksum as they download and the checksumming from the myriad seeders must always match. The highly and randomly distributed nature of torrents make them extremely difficult for bad guys to subvert.

Lastly, it must be conceded that there is no such thing as absolutely security in computing any more than there are such absolutes in any other aspect of life. We will always have to live with some level of risk and insecurity. There will always be scumbags out there who try to screw good people. We can beef up our security to the point where they go after lower hanging fruit, but the idea of perfect security is a chimera.

For a good start on hardening your system, take a look at the link in my sig: "Security Basics".

---

### Post by bearlake on 2016-11-27
> **ardouronerous said:**
> I ain't that tech-savy enough to do that, hell, after 5 years of using Xubuntu, I'm still intimated by the Terminal, but believe me, I wish could build my own Linux OS and server.



Okay, I wonder why the Linux Mint hacker was able to get away what he did?



The hacker was able to change the Hash information on Linux Mint's site.

People who checked the Hash information noticed it didn't match. Just the ISO files were changed.

---

### Post by cogset on 2016-11-27
> **DuckHook said:**
> In my opinion, your concern is legitimate. The Mint site was hacked in such a fashion that the checksums were also bogus.   I'd agree with that, it is a legitimate question IMHO. I also seem to remember (contrary to what other are saying here) that the hashes indeed matched the altered ISO images, and that allegedly part of the issue was the use of weak md5 hashes on Mint's part instead of more secure sha1 and so on - besides some other flaws in Mint's structure  that they have addressed after the intrusion.     

That > **alexjpowell said:**
> Build your own linux if it's that important
   IMHO isn't an appropriate answer, as I've said above it is after all a legitimate concern in light of what happens. Sure enough building your own version may add more control, but then there always will be the matter of verifying and trusting the sources - aside of the obvious difficulties of building a distro.      

> **HermanAB said:**
> For starters, make your own mirror server.  (This step is surprisingly easy, the rest not.)  Then gradually increase your level of testing and verification to satisfy your required level of paranoia.  Note that you are not paranoid, if they are really out to get you...

     I don't believe that in the case discussed the attacker was out to get someone in particular, more likely it just happened that he spotted some flaws in Mint and went for it, as sometimes these folks do - this is to say again that such concerns sound legitimate to me, yes this line of thinking sometimes borders on the paranoid side but then it's not unreasonable either.        

BTW, this is another interesting article on the Mint issue : [https://micahflee.com/2016/02/backdoored-linux-mint-and-the-perils-of-checksums/](https://micahflee.com/2016/02/backdoored-linux-mint-and-the-perils-of-checksums/) which amongst other things says > Besides the fact that the website isn’t available over HTTPS which doesn't sound good at all... that's probably where all started.

---

### Post by ardouronerous on 2016-11-27
> **Habitual said:**
> "As we all know" in February of 2016.
Defense is [verify]("https://linuxmint.com/verify.php")
Not as scary as a torrented pirated version of Windows and folks do/did those things.

Things are better now.
You do verify, right?
> **bearlake said:**
> People who checked the Hash information noticed  it didn't match. Just the ISO files were changed.

Yes I know things are better now, but I'm just being cautious, and I know I maybe a little paranoid, but my caution has saved my butt many times, and yes, I do verify, every time I download a ISO, be it Xubuntu or ReactOS, I always check the Hashes, but as was stated, the hacker compromised ISOs and changed the Hash information to trick users into thinking they download a legit ISO, bearlake, read the articles sited on this thread.

> **DuckHook said:**
> In my opinion, your concern is legitimate. The  Mint site was hacked in such a fashion that the checksums were also  bogus. Since most users don't even bother to checksum their ISO after it  is burned, it is not particularly hard to buffalo users who seem  determined to be unwary. In this particular case, even the more wary  would have been led astray.

But it is also important to understand what actually happened in the  Mint case. Mint itself was not compromised. What the cracker did instead  was hijack Mint's website and replace it with the cracker's own.  Therefore, users were not downloading *hacked* OSes, but rather, *bogus*  OSes. This is an important distinction. A hacked OS is truly spooky  because it means that the real OS is debased, whereas in the Mint case,  the real OS never lost its integrity--users were just redirected to a  false one. The saving grace in this scenario is that security measures  such as kernel signing and distributed authentication were not  compromised. It was only users who downloaded from the bogus site that  got bad ISOs.

For two differing opinions on the Mint incident:

[http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/](http://www.techrepublic.com/article/why-the-linux-mint-hack-is-an-indicator-of-a-larger-problem/)
[http://www.ocsmag.com/2016/04/09/linux-mint-security-28-days-later/](http://www.ocsmag.com/2016/04/09/linux-mint-security-28-days-later/)

The second article puts things in a rather more balanced perspective, but both are informative.

From a practical standpoint, the measures recommended in the second  article will help. Surprisingly, one better method for downloading ISOs  is not mentioned in that article, and that is, to torrent them. Torrents  continually checksum as they download and the checksumming from the  myriad seeders must always match. The highly and randomly distributed  nature of torrents make them extremely difficult for bad guys to  subvert.

Lastly, it must be conceded that there is no such thing as absolutely  security in computing any more than there are such absolutes in any  other aspect of life. We will always have to live with some level of  risk and insecurity. There will always be scumbags out there who try to  screw good people. We can beef up our security to the point where they  go after lower hanging fruit, but the idea of perfect security is a  chimera.

For a good start on hardening your system, take a look at the link in my sig: "Security Basics".
> **cogset said:**
> I'd agree with that, it is a legitimate question  IMHO. I also seem to remember (contrary to what other are saying here)  that the hashes indeed matched the altered ISO images, and that  allegedly part of the issue was the use of weak md5 hashes on Mint's  part instead of more secure sha1 and so on - besides some other flaws in  Mint's structure  that they have addressed after the intrusion.     

That 
   IMHO isn't an appropriate answer, as I've said above it is after all a  legitimate concern in light of what happens. Sure enough building your  own version may add more control, but then there always will be the  matter of verifying and trusting the sources - aside of the obvious  difficulties of building a distro.      



     I don't believe that in the case discussed the attacker was out to  get someone in particular, more likely it just happened that he spotted  some flaws in Mint and went for it, as sometimes these folks do - this  is to say again that such concerns sound legitimate to me, yes this line  of thinking sometimes borders on the paranoid side but then it's not  unreasonable either.        

BTW, this is another interesting article on the Mint issue : [https://micahflee.com/2016/02/backdoored-linux-mint-and-the-perils-of-checksums/](https://micahflee.com/2016/02/backdoored-linux-mint-and-the-perils-of-checksums/) which amongst other things says  which doesn't sound good at all... that's probably where all started.

The problem with torrents is the source of the torrent, the torrent file itself could be compromised like the ISOs, right? A torrent file is like a set of instructions telling BitTorrent or Transmission to download a certain file, a torrent could easily be turned into a Trojan Horse.

How do I check the public key? When I download a Ubuntu ISO, how do I compare the ISO with the public key?

---

### Post by DuckHook on 2016-11-28
> **ardouronerous said:**
> ...I always check the Hashes, but as was stated, the hacker compromised ISOs and changed the Hash information to trick users into thinking they download a legit ISO...As I recall, you and *bearlake* are both correct. The cracker changed the checksum for the download self-check: the one attached to the ISO itself, that users use to verify download integrity. However, he did not change the checksum published on the Mint site, so a comparison of the two would have shown a discrepancy. There wasn't a lot of info published about the compromise. My understanding was assembled from bits and pieces and could very well be wrong.> The problem with torrents is the source of the torrent, the torrent file itself could be compromised like the ISOs, right? A torrent file is like a set of instructions telling BitTorrent or Transmission to download a certain file, a torrent could easily be turned into a Trojan Horse.Partly correct, but not entirely. Your concern about torrent sourcing is valid. There are a lot of torrents out there that are Trojans or rootkits masquerading as "useful" files. A lot of it is supposedly "pirate" stuff, games, first-run movies, porn, "free" versions of proprietary OSes and apps, etc. The problem with these torrent files is that they *start off* from the underworld, are illegal, trade on people's greed (wanting something for nothing), so have no legitimate origin. Garbage in, garbage out.

However, it is far, far more difficult to compromise a *legitimate* torrent. Consider: first, the website would have to hacked (indetectibly) to point to an illegitimate source. This hack needs to be undetected for a lengthy period because torrents depend on the network effect and require a large enough base of seeders to become self-perpetuating. Moreover, the bad torrent *cannot* incorporate any seeds from the existing good torrents, because checksumming occurs constantly with each packet and bad packets are self-evident. In any event, due to the way torrents work, it is not possible to just "mix in" some bad code because any corruption of the downloaded binary would render the OS unbootable. This is not to say that compromising a torrent is impossible. It is just extremely difficult, the barrier being so high that a scumbag would likely go after lower hanging fruit before trying to compromise a torrent.> How do I check the public key? When I download a Ubuntu ISO, how do I compare the ISO with the public key?Verification instructions: [https://www.ubuntu.com/download/how-to-verify](https://www.ubuntu.com/download/how-to-verify)

---

### Post by ardouronerous on 2016-11-28
> **DuckHook said:**
> As I recall, you and *bearlake* are both correct. The cracker changed the checksum for the download self-check: the one attached to the ISO itself, that users use to verify download integrity. However, he did not change the checksum published on the Mint site, so a comparison of the two would have shown a discrepancy. There wasn't a lot of info published about the compromise. My understanding was assembled from bits and pieces and could very well be wrong.Partly correct, but not entirely. Your concern about torrent sourcing is valid. There are a lot of torrents out there that are Trojans or rootkits masquerading as "useful" files. A lot of it is supposedly "pirate" stuff, games, first-run movies, porn, "free" versions of proprietary OSes and apps, etc. The problem with these torrent files is that they *start off* from the underworld, are illegal, trade on people's greed (wanting something for nothing), so have no legitimate origin. Garbage in, garbage out.

However, it is far, far more difficult to compromise a *legitimate* torrent. Consider: first, the website would have to hacked (indetectibly) to point to an illegitimate source. This hack needs to be undetected for a lengthy period because torrents depend on the network effect and require a large enough base of seeders to become self-perpetuating. Moreover, the bad torrent *cannot* incorporate any seeds from the existing good torrents, because checksumming occurs constantly with each packet and bad packets are self-evident. In any event, due to the way torrents work, it is not possible to just "mix in" some bad code because any corruption of the downloaded binary would render the OS unbootable. This is not to say that compromising a torrent is impossible. It is just extremely difficult, the barrier being so high that a scumbag would likely go after lower hanging fruit before trying to compromise a torrent.Verification instructions: [https://www.ubuntu.com/download/how-to-verify](https://www.ubuntu.com/download/how-to-verify)

Thanks for the information DuckHook, I never knew downloading via torrent was more secure than downloading a ISO directly, I guess I've been doing the right thing all along, I tend to download via torrent for the reason of speed as it's faster than downloading a file directly and waiting 2 to 3 hours.

Thanks for the info on the Public key verification! :)

---

### Post by DuckHook on 2016-11-28
Glad to be of some service. If you feel your question has been answered, please mark thread "solved" using the thread tools at the top of this page.

---

### Post by SeijiSensei on 2016-11-28
Did the attacker hijack the DNS records to redirect connections to the Mint site to his own?  Otherwise wouldn't it be obvious from looking at the browser's address bar that the site wasn't legitimate?

---

### Post by Habitual on 2016-11-28
> **SeijiSensei said:**
> Did the attacker hijack the DNS records to redirect connections to the Mint site to his own?  Otherwise wouldn't it be obvious from looking at the browser's address bar that the site wasn't legitimate?
In short. 
Someone got mad for something and uploaded a reverse shell php script to avatars/uploads/somewhere_unsafe_and_public and then read a very cheesey (IMO) and weak mysql password for a poorly-maintained Wordpress database.
Accessed the database and edited existing posts. They managed to alter the published md5sum values in the posts and it was believed that the next logical step was to point folks at the foreign-hosted mirrored ISOs without anybody noticing.

---

