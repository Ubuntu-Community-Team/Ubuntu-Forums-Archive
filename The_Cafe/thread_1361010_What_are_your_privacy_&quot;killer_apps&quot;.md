---
title: "What are your privacy &quot;killer apps&quot;"
date: 2009-12-21
forum: The Cafe
---

### Post by Hallvor on 2009-12-21
Do you use any GNU/Linux applications to protect your privacy? Just like you put your letters in envelopes, what applications do you use/recommend to keep private data a little more private?

---

### Post by Cuddles McKitten on 2009-12-21
Depends how paranoid you are.  I keep all of my tax info and business ideas in a TrueCrypt volume.  You can encrypt your whole hard drive with dm-crypt tools which will make any wandering KGB agents unable to play with your computer though.

---

### Post by pwnst*r on 2009-12-21
OpenVPN, truecrypt, ssh

---

### Post by handy on 2009-12-21
In my house there is only my wife & I, so I have no need for any privacy measures on that front.

We also do not use wireless here, & we are in the country with no houses near us either, so it would be highly unlikely that anyone would ever be around here tapping into our non-existent wireless network anyway. :)

I email very little & again if anyone is interested in reading it they surely must lead a boring life.

I am concerned with the build up of databases built on people's surfing habits, & the potential to use this data-mined info' for whatever reasons; as very sophisticated software manipulation of this data is possible.

So I use a headless box that runs IPCop, the Linux based firewall/router (amongst other services) with the Copfilter add-on, which provides additional services, one being Privoxy, which helps protect my privacy & also kills most all adds & pop-ups on the web. I also use the Firefox add-on called [**_Ghostery_**]("https://addons.mozilla.org/en-US/firefox/addon/9609"), which identifies & blocks web bugs on pages I visit.

Also, I have Firefox set to ask my permission every time a cookie comes my way, my rmb index finger is set to automatically reject the cookie permanently, & have only the cookies I need allowed, so I can visit places like this forum.

I search the web using Scroogle SSL, so as to minimise my additions to Googles database of my surfing history.

I have java enabled.

---

### Post by Pogeymanz on 2009-12-21
> **handy said:**
>  I also use the Firefox add-on called [**_Ghostery_**]("https://addons.mozilla.org/en-US/firefox/addon/9609"), which identifies & blocks web bugs on pages I visit.


What does ghostery do that blocking JS and cookies doesn't do?

---

### Post by CbrPad on 2009-12-21
Truecrypt, Keepassx, JonDo and various Firefox addons (noscript, optimizegoogle, betterprivacy, cslite, foxyproxy).

---

### Post by pwnst*r on 2009-12-21
whoops...forgot about keepass, thanks cbrpad

---

### Post by handy on 2009-12-21
> **Pogeymanz said:**
> What does ghostery do that blocking JS and cookies doesn't do?

Did you have a look at the Ghostery Blog site? 

[http://news.ghostery.com/?src=ff](http://news.ghostery.com/?src=ff)

Ghostery blocks over 230 trackers, it stops things that get past Privoxy & Addblock +.

Try it, if it doesn't block anything for you then delete it.

---

### Post by t0p on 2009-12-21
I have the Flashblock and CustomizeGoogle add-ons on my Firefox browser.I use OpenVPN (actually [AceVPN]("http://www.acevpn.com") at the moment) when I'm using a wifi hotspot.  When I haven't got a VPN account, I've used [Your Freedom]("http://www.your-freedom.net") which is similar.  I use SSH and/or FreeNX when I need to connect to my computer remotely.  I use GnuPG to encrypt some email - I use the Firefox add-on [FireGPG]("http://getfiregpg.org") to do this on my netbook when I'm out and about as it adds GPG controls to Gmail's webpage; when on my desktop at home, I use Evolution which supports GPG encryption.  (Incidentally, users of GPG may be interested to know that, according to Anne Roth in [her talk "Terrorist All-Stars"]("http://chaosradio.ccc.de/media/congress/2008/video/25C3-2991-en-terrorist_all_stars.m4v") at the [25th Chaos Communication Congress]("http://chaosradio.ccc.de/25c3_m4v.html"), the German police are unable to crack GPG encryption.  Moreover, when the police engaged an encryption expert to attempt to crack some GPG-protected files, the professor only felt he had a chance because he had found the suspect's private key on his computer; this would have enabled the professor to attempt a crack *by guessing at the suspect's passphrase*; and the professor told the police that if the passphrase was longer than 8 characters and contained special characters, he probably wouldn't be able to crack it at all.  In the end the expert didn't attempt a crack because the police didn't want to pay his fee of 5000 euros with no guarantee of success.  The files remain encrypted to this day.)

I keep confidential files in a Truecrypt container.  I used to encrypt the files symmetrically with *gpg -c* before putting them in the container; but I've now abandoned this procedure as it's too "belt-and-braces" for my taste.  I'm sure that users more paranoid than myself may like to consider doing that, "just in case".  Paranoid users may also be interested in Truecrypt's *plausible deniability* function.  This involves a container containing 2 sets of contents: "decoy" contents that you pretend is sensitive, and the real contents.  If an evil character finds your Truecrypt container and tortures you for the contents, you give him the decoy passphrase.  This decrypts the decoy contents.  When you want to get to the real sensitive material, you use the real passphrase and this decrypts the real secrets.  It is impossible for an analyst to detect that the container contains 2 sets of contents, as the entire content is encrypted, even the empty space.  As of yet, I haven't heard of anyone successfully cracking Truecrypt.  But of course you must ensure you use a strong passphrase.

---

### Post by pwnst*r on 2009-12-21
how is it you trust acevpn instead of hosting your own openvpn server.

---

### Post by t0p on 2009-12-21
> **pwnst*r said:**
> how is it you trust acevpn instead of hosting your own openvpn server.

1. I don't own suitable infrastructure at the moment and can't afford VPS hosting;
2. I try to keep my paranoia to moderate levels.  I'm not involved in crime or espionage and I'm not especially wealthy, so I don't think it's likely anyone wants to bribe AceVPN staff to get at my traffic.  If my circumstances change to make me more of a potential target, I will revise my security precautions then.

---

### Post by ctrlmd on 2009-12-21
Nothing I keep important things on a standalone Computer that doesn't have internet connection or Networked with others

---

### Post by blueshiftoverwatch on 2009-12-21
I use [Ixquick]("http://ixquick.com/") and occasionally [Scroogle]("http://www.scroogle.org/cgi-bin/scraper.htm") as my search engines to prevent my IP from being logged. [Off-the-Record Messaging]("http://www.cypherpunks.ca/otr/") for over half of all the IM's I send and receive. So far I've gotten about 4 people on my buddy list to start using OTR as well. [Enigmail]("http://enigmail.mozdev.org/home/index.php") in conjunction with Mozilla Thunderbird to encrypt my email. Although most of the people I know don't use OpenPGP, so about 90% of the emails I send aren't encrypted. The [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722"), [RefControl]("https://addons.mozilla.org/en-US/firefox/addon/953"), and [BetterPrivacy]("https://addons.mozilla.org/en-US/firefox/addon/6623") Firefox extensions. I also set Firefox to always operate in private browsing mode so that nothing I do online is saved to my hard drive. I'm thinking about encrypting my hard drive using [LUKS]("http://code.google.com/p/cryptsetup/") in the near future.

I've thought about using anonymizing services like [Tor]("https://www.torproject.org/") and/or [JonDonym]("https://anonymous-proxy-servers.net/en/") to conceal my web activity. But they would take a giant poop over my high speed net connection and be a pain to disable when I wanted to do things like watch Flash videos or download large files. My current security measures provide what I feel to be a greatly increased level of privacy over what the average computer user has while at the same time not being that much of a bother.

---

### Post by t0p on 2009-12-21
> **blueshiftoverwatch said:**
> I use [Ixquick]("http://ixquick.com/") and occasionally [Scroogle]("http://www.scroogle.org/cgi-bin/scraper.htm") as my search engines to prevent my IP from being logged.

I've been trying out Ixquick just lately, and I'm not very satisfied.  Sometimes their results are somewhat lacking in comparison with nosey old Google.  I also used Scroogle for a while, but for some reason it would just "hang" for ages when doing a search - something that doesn't happen with nosey old Google.

I'm far from satisfied with Google either: something about their need for info about their users creeps me out.  At the moment I'm using a combination of search engines: Ixquick, and Google through Firefox with CustomizeGoogle add-on.  If anyone can recommend another good search solution, I'm all ears.

---

### Post by blueshiftoverwatch on 2009-12-21
> **t0p said:**
> I've been trying out Ixquick just lately, and I'm not very satisfied.  Sometimes their results are somewhat lacking in comparison with nosey old Google.  I also used Scroogle for a while, but for some reason it would just "hang" for ages when doing a search - something that doesn't happen with nosey old Google.
I've found Ixquick's search results to be right up there with Google's most of the time. I only occasionally use Scroogle anymore. I tried to set Scroogle as the default search engine on my Dad's iMac. But I had to download an extension to change it and when I reopened Safari the changes I made weren't saved. Apple really doesn't want the users messing with the default settings. Overall I find Safari very lacking compared to Firefox in both usability and customizability. Their interface just seems really clunky for some reason. I've tried to get my parents to switch to Firefox but they insist on Safari for some reason.

What is your avatar from?

---

### Post by Knowle on 2009-12-22
I'm not all that concerned with local privacy at the moment, as in someone having physical access to my laptop but I have considered encrypting my home directory. As far as online privacy goes I just use Firefox with Flashblock, Ghostery, NoScript and Targeted Advertising Cookie Opt-Out (TACO) with a custom HOSTS file.

Yet..I still occasionally use Google Chrome, primary use Gmail for my email needs, and use OpenDNS / Google Public DNS as my primary/secondary DNS servers. So it's some what mixed and not working at all. >:l

---

### Post by handy on 2009-12-22
> **t0p said:**
> I have the Flashblock and CustomizeGoogle add-ons on my Firefox browser.I use OpenVPN (actually [AceVPN]("http://www.acevpn.com") at the moment) when I'm using a wifi hotspot.  When I haven't got a VPN account, I've used [Your Freedom]("http://www.your-freedom.net") which is similar.  I use SSH and/or FreeNX when I need to connect to my computer remotely.  I use GnuPG to encrypt some email - I use the Firefox add-on [FireGPG]("http://getfiregpg.org") to do this on my netbook when I'm out and about as it adds GPG controls to Gmail's webpage; when on my desktop at home, I use Evolution which supports GPG encryption.  (Incidentally, users of GPG may be interested to know that, according to Anne Roth in [her talk "Terrorist All-Stars"]("http://chaosradio.ccc.de/media/congress/2008/video/25C3-2991-en-terrorist_all_stars.m4v") at the [25th Chaos Communication Congress]("http://chaosradio.ccc.de/25c3_m4v.html"), the German police are unable to crack GPG encryption.  Moreover, when the police engaged an encryption expert to attempt to crack some GPG-protected files, the professor only felt he had a chance because he had found the suspect's private key on his computer; this would have enabled the professor to attempt a crack *by guessing at the suspect's passphrase*; and the professor told the police that if the passphrase was longer than 8 characters and contained special characters, he probably wouldn't be able to crack it at all.  In the end the expert didn't attempt a crack because the police didn't want to pay his fee of 5000 euros with no guarantee of success.  The files remain encrypted to this day.)

I keep confidential files in a Truecrypt container.  I used to encrypt the files symmetrically with *gpg -c* before putting them in the container; but I've now abandoned this procedure as it's too "belt-and-braces" for my taste.  I'm sure that users more paranoid than myself may like to consider doing that, "just in case".  Paranoid users may also be interested in Truecrypt's *plausible deniability* function.  This involves a container containing 2 sets of contents: "decoy" contents that you pretend is sensitive, and the real contents.  If an evil character finds your Truecrypt container and tortures you for the contents, you give him the decoy passphrase.  This decrypts the decoy contents.  When you want to get to the real sensitive material, you use the real passphrase and this decrypts the real secrets.  It is impossible for an analyst to detect that the container contains 2 sets of contents, as the entire content is encrypted, even the empty space.  As of yet, I haven't heard of anyone successfully cracking Truecrypt.  But of course you must ensure you use a strong passphrase.

If you paragraphed your post(s) better I would very happily read them, as I'm sure (from what I've read in your short posts) they are quite knowledgeable & stimulating.

But I'm not going to be bothered with a post like the one quoted above which is nought but an overpopulation of letters. :confused:

I look forward to your scathing reply... (though in truth I hope it is a more practical one.)

---

### Post by crimesaucer on 2009-12-22
> **handy said:**
> Did you have a look at the Ghostery Blog site? 

[http://news.ghostery.com/?src=ff](http://news.ghostery.com/?src=ff)

Ghostery blocks over 230 trackers, it stops things that get past Privoxy & Addblock +.

Try it, if it doesn't block anything for you then delete it.


+1


I also use Ghostery with all scripts blocked (but I suggest that anyone trying it out should run it for a few days using the default settings just to see all the scripts used for most web pages).


Besides Ghostery I use iptables with this script: [http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO](http://wiki.archlinux.org/index.php/Simple_stateful_firewall_HOWTO)

---

### Post by lovinglinux on 2009-12-22
Aside from authentication/encryption stuff that is installed by default, I mostly use Firefox extensions and Keepassx. I don't encrypt my partitions, but sensitive data like web site configuration files and passwords are manually encrypted with KGpg.

Among the security/privacy extensions I use are these:

[Better Privacy](https://addons.mozilla.org/en-US/firefox/addon/6623)
[Customize Google](https://addons.mozilla.org/en-US/firefox/addon/743)
[CS Lite](https://addons.mozilla.org/en-US/firefox/addon/5207)
[Ghostery](https://addons.mozilla.org/en-US/firefox/addon/9609)
[AdBlock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865)
[NoScript](https://addons.mozilla.org/en-US/firefox/addon/722)
[Secure Login](https://addons.mozilla.org/en-US/firefox/addon/4429)
[Show IP](https://addons.mozilla.org/en-US/firefox/addon/590)

There is a new extension, that I'm experimenting and so far works really nice, that integrates Firefox with Kwallet: [KDE Wallet  password integration](https://addons.mozilla.org/en-US/firefox/addon/49357). The gnome equivalent is [Gnome-keyring password integration](https://addons.mozilla.org/en-US/firefox/addon/8737).

I also make some Firefox tweaks, for example to [disable the referrer header](http://kb.mozillazine.org/Network.http.sendRefererHeader).

---

### Post by ghindo on 2009-12-22
I *love* the [Targeted Advertising Cookie Opt-Out (TACO) Firefox add-on]("https://addons.mozilla.org/en-US/firefox/addon/11073").  It's a very simple way to secure your privacy while surfing the web.  It's developed by security researcher [Christopher Soghoian]("http://en.wikipedia.org/wiki/Christopher_Soghoian") and you can read more about the add-on [here]("http://taco.dubfire.net/").

---

### Post by lovinglinux on 2009-12-22
> **ghindo said:**
> I *love* the [Targeted Advertising Cookie Opt-Out (TACO) Firefox add-on]("https://addons.mozilla.org/en-US/firefox/addon/11073").  It's a very simple way to secure your privacy while surfing the web.  It's developed by security researcher [Christopher Soghoian]("http://en.wikipedia.org/wiki/Christopher_Soghoian") and you can read more about the add-on [here]("http://taco.dubfire.net/").

Sounds interesting, but see the quote below, extracted from the extension site:

> Most advertising networks will continue to collect detailed information about your web browsing habits, which in some cases is retained indefinitely. Even if you use TACO to opt-out of behavioral advertising, many companies will still attempt to insert other unique, identifiable cookies into your browser in order to track your browsing across multiple sessions.

If you value your privacy, and want to do something to protect yourself from the identifiable cookies which advertising networks will try to insert into your browser, you should configure Firefox to either block all third party cookies and or to delete all cookies at the end of each browsing session.

So it seems to me is still better to block them with Ghostery, NoScript and AdBlock and control the cookies with CS Lite or delete them between sessions. BTW, I just created a new thread to discuss [how to handle cookies](http://ubuntuforums.org/showthread.php?t=1361538).

---

### Post by Paqman on 2009-12-22
> **Hallvor said:**
> Just like you put your letters in envelopes

Bit of a tangent: envelopes actually do nothing to protect your privacy, since it's so easy to take things out and put them into a sealed envelope. And if you licked the stamp/flap, then you're also tagging your letter with a DNA sample.

Back on topic: I use nothing. I'm quite happy with the level of privacy offered by a default Ubuntu & apps.

---

### Post by Hallvor on 2009-12-22
> **Paqman said:**
> Bit of a tangent: envelopes actually do nothing to protect your privacy, since it's so easy to take things out and put them into a sealed envelope. And if you licked the stamp/flap, then you're also tagging your letter with a DNA sample.


Privacy doesn`t equal total anonymity. Privacy is imho a means to control what you reveal about yourself, and is not identical to secrecy and anonymity. It is like the differece between sending a postcard (that everyone can read) and a sealed envelope. 

For normal use a sealed envelope will do just fine for me, since I know that there is minimal chances of anyone opening the letter and reading it. I wouldn`t send my private letters through snailmail encrypted and in titanium boxes. 

However, encrypting email is imho normal privacy, since email is more like sending a postcard than a sealed letter.

Just my 2 cents.

---

### Post by mkvnmtr on 2009-12-22
This is a good thread. It has given me some things to check out. I will say that I have nothing on my computer that would matter if it was public but I just hate the idea of advertising sites keep track of where i go. If I wished to visit questionable sites I would use a live distro so there could be no record. If I wished to use banking sites or spend money on the web I believe I would also use a live distro.

---

### Post by Exodist on 2009-12-22
> **Hallvor said:**
> Do you use any GNU/Linux applications to protect your privacy? Just like you put your letters in envelopes, what applications do you use/recommend to keep private data a little more private?

If someone can get through my double firewall and then decrypt my drive they can have my damn resume!

---

