---
title: "Please add transaction integrity for APT."
date: 2024-07-31
forum: Security
---

### Post by vbgf3 on 2024-07-31
Hi, 

Please add Transaction Integrity to APT. So that the Whole Set of package upgrades are checked to ensure that no unauthorized updates are inserted into the upgrade stream. Fedora's DNF already does this. It is about time that we also catch up and have this feature. 

Also APT or it's libraries seems to have a vulnerability. I cannot prove this, but every time I do a 'apt update' I seem to get something installed into my system. (process of elimination) I don't know how to check for it. Please suggest a method for me to check. I am doubling up my monitoring efforts. 

My AIDE logs are too long. And I use tcpdump to capture transmissions that go over 4 kb. I have a sudo log. I use clamAV.  I use logwatch. And I have a few apparmor app profiles (systemd-resolved, timesync,). And I have a hardware firewall standing in between me and the modem; but I have a few favorite forums I always have open so it is easy to spoof traffic thru it. And I resumed use of my VPN. 

I have an infected cable modem. The attackers seems to have multiple exploits for different brands/models. I have changed 3 ISPs, this is still an on-going concern. One time, I was able to find an intruder using nmap. The attackers are near my apartment, they have spoofed and over-powered my SSID so that I connect to them instead and cannot connect online - so I no longer use WiFi. In the past, they have also attacked via WiFi Direct, because Windows accepts WiFi Direct connections bypassing it's firewall. System was noticeably slower after this attack. This I fixed via removing the Windows WiFi Direct driver. If you live in an apartment complex I suggest you do the same via Device Manager. (There is no functionality loss to these 2 drivers' removal) There was another attack on taskhostw, that time they inserted a certificate into Windows registry and was thus able to bypass WDAC because their payload was thus 'properly' signed. This was picked up by my EDR.  

I suspect this new  intrusion onto Ubuntu 24 is an info stealer. The last time the attacker made it thru to Ubuntu, he disabled my AIDE by fiddling with the conf file. (without the conf file, you cannot even do a aide check) and he zero kb my aide db files; and changed my wallpaper. Fun and games.:)


Thanks for reading.

---

### Post by TheFu on 2024-08-01
Nobody here works for Canonical.
If you want someone in Canonical to know these things, open a bug report in Landscape.

If you can think of a good reason WHY an organization might want see all your traffic, then you might not be paranoid.  Location would also matter.  Do you work for a military organization?  Infrastructure (water, power, natural gas) company?  Do you work with nuclear stuff - even if only for medical uses?  Have you upset an authoritarian govt?  Do you live outside the USA and upset the USA or one of the other 5-eyes countries?    Do you live in a location where the govt is known to watch all traffic?  Are you a journalist embarrassing powerful people with your publications/stories?  That is just the normal dictators, BTW. A few democracies do this too, I'm sad to say.  Is your ISP run by a drug cartel?

If the answer to all these things is no, then it is either a mistake or you are screwed.  I'm leaning towards a mistake for 99% of it and you are screwed for 1%.

In short, unless you have a specific enemy, which you should know already, there's very little do be done.  I suppose you could choose to use random internet connections, just not your own, but if your modem is compromised, you should just give up using it.

---

### Post by currentshaft on 2024-08-01
> **vbgf3 said:**
> 
Please add Transaction Integrity to APT. So that the Whole Set of package upgrades are checked to ensure that no unauthorized updates are inserted into the upgrade stream. Fedora's DNF already does this. It is about time that we also catch up and have this feature. 


Ubuntu apt updates are already cryptographically signed.

> **vbgf3 said:**
> 
Also APT or it's libraries seems to have a vulnerability. I cannot prove this


Then it's paranoia, not a vulnerability. 

> **vbgf3 said:**
> 
, but every time I do a 'apt update' I seem to get something installed into my system. (process of elimination) I don't know how to check for it. Please suggest a method for me to check. I am doubling up my monitoring efforts. 


This literally makes zero sense. You run apt to install updates updates and ... something gets installed into your system? Help us make sense of what you're trying to say.

> **vbgf3 said:**
> 
My AIDE logs are too long. And I use tcpdump to capture transmissions that go over 4 kb. I have a sudo log. I use clamAV.  I use logwatch. And I have a few apparmor app profiles (systemd-resolved, timesync,). And I have a hardware firewall standing in between me and the modem; but I have a few favorite forums I always have open so it is easy to spoof traffic thru it. And I resumed use of my VPN. 

Okay? What does this have to do with apt or anything else for what matter?


> **vbgf3 said:**
> 
I have an infected cable modem. The attackers seems to have multiple exploits for different brands/models. I have changed 3 ISPs, this is still an on-going concern. One time, I was able to find an intruder using nmap. The attackers are near my apartment, they have spoofed and over-powered my SSID so that I connect to them instead and cannot connect online - so I no longer use WiFi. In the past, they have also attacked via WiFi Direct, because Windows accepts WiFi Direct connections bypassing it's firewall. System was noticeably slower after this attack. This I fixed via removing the Windows WiFi Direct driver. If you live in an apartment complex I suggest you do the same via Device Manager. (There is no functionality loss to these 2 drivers' removal) There was another attack on taskhostw, that time they inserted a certificate into Windows registry and was thus able to bypass WDAC because their payload was thus 'properly' signed. This was picked up by my EDR.  



Dude, what? I hate to say it, but I think you may need help, and not the kind you're going to find on a technical forum.

You sound extremely paranoid without any rational qualifications. If you think your system is compromised, format it or get a new one. Otherwise, you need to post objective evidence of what you're talking about here for anyone to make sense of your odd post.

---

### Post by vbgf3 on 2024-08-01
@TheFu: 
"[COLOR=#000000]If you can think of a good reason WHY an organization might want see all your traffic, then you might not be paranoid"  

Well now that you asked, I can think of a few people. a) 20+ yrs ago I helped overthrow a set of Directors at my town house complex. They were mis-using funds to re-decorate the complex so they can sell high. b) I am pretty vocal against MS. I had a web site on improving security for Windows aiming to help those who are hacked. And I criticized MS for the lax default security of Windows. Then in the last few years MS took notice and published a few sites that showed up along side my site using various search terms so people can see it. Mine was an "open source" site in that everything was explained and shown how to do it manually. But if the 30+ pages overwhelm you, then you can purchase the script kit ($8). c) I might have upset China because they consider me their countrymen. And I guess they don't look too kindly at folks offering security help openly. 


@currentshaft 
"[/COLOR][COLOR=#000000]Dude, what? I hate to say it, but I think you may need help, and not the kind you're going to find on a technical forum." . 

I tried to offer proof that I was attacked, but I don't document much of the incidents other than fixing them or failing to figure out how, just re-image. But EDR's don't lie and Modems DO get hacked, see here:  [/COLOR]https://www.youtube.com/watch?v=b0fQ-QTx-aY  and here:  [https://samcurry.net/hacking-millions-of-modems](https://samcurry.net/hacking-millions-of-modems)  . I think you are one of those who believe that nowadays every hacker would be a cybercriminal because that's where the money is. But remember there are skill grades to hackers. Only the best would go up against the heavy defenses of big corps to nail the big bucks. As with every market, there is the high end, mid-range and low end. And some hackers still hack for fun, especially those that do not want to turn to crime. Then there are the low end criminals who buy attack kits from the black market, and engage in ransomware attacks that only net $400.


"[COLOR=#000000]Ubuntu apt updates are already cryptographically signed."

Yes, each individual package is signed. But there is nothing saying that an extra package can't be inserted into a update stream.  And that is what Fedora's DNF can do, it offers checks on the entire transaction - the combined set of all upgraded packages, from beginning to the end, to make sure nothing un-wanted has been inserted. The cryptography is there to ensure that all of the packages are unmodified. It does not ensure that something additional and un-wanted is also installed to your PC. 


[/COLOR]

---

### Post by currentshaft on 2024-08-01
> **vbgf3 said:**
> 
I tried to offer proof that I was attacked, but I don't document much of the incidents other than fixing them or failing to figure out how, just re-image. But EDR's don't lie and Modems DO get hacked, see here:  [https://www.youtube.com/watch?v=b0fQ-QTx-aY](https://www.youtube.com/watch?v=b0fQ-QTx-aY)  and here:  [https://samcurry.net/hacking-millions-of-modems](https://samcurry.net/hacking-millions-of-modems)  . I think you are one of those who believe that nowadays every hacker would be a cybercriminal because that's where the money is. But remember there are skill grades to hackers. Only the best would go up against the heavy defenses of big corps to nail the big bucks. As with every market, there is the high end, mid-range and low end. And some hackers still hack for fun, especially those that do not want to turn to crime. Then there are the low end criminals who buy attack kits from the black market, and engage in ransomware attacks that only net $400.

No one is denying those hacks exist. But they are irrelevant to APT, irrelevant to Ubuntu and irrelevant to this discussion.

If you think your cable modem is "infected" - buy a new cable modem and move on. Stop dwelling in paranoia.

> **vbgf3 said:**
> 
Yes, each individual package is signed. But there is nothing saying that an extra package can't be inserted into a update stream.  And that is what Fedora's DNF can do, it offers checks on the entire transaction - the combined set of all upgraded packages, from beginning to the end, to make sure nothing un-wanted has been inserted. The cryptography is there to ensure that all of the packages are unmodified. It does not ensure that something additional and un-wanted is also installed to your PC. 


Demonstrate exactly how an adversary is going to subvert apt to "add an extra package" into your system.

Not this elaborate, ambiguous, contrived situation but the actual steps someone would perform to take advantage of this vulnerability and compromise a Ubuntu system, such as yours.

Then describe the adversary that is interested in doing those things. This is also known as threat modeling.

You will never have real security without a threat model. It will not even be possible to have a productive conversation about security without one.

---

### Post by TheFu on 2024-08-01
> **vbgf3 said:**
> @TheFu: 
"[COLOR=#000000]If you can think of a good reason WHY an organization might want see all your traffic, then you might not be paranoid"  

Well now that you asked, I can think of a few people. a) 20+ yrs ago I helped overthrow a set of Directors at my town house complex. They were mis-using funds to re-decorate the complex so they can sell high. b) I am pretty vocal against MS. I had a web site on improving security for Windows aiming to help those who are hacked. And I criticized MS for the lax default security of Windows. Then in the last few years MS took notice and published a few sites that showed up along side my site using various search terms so people can see it. Mine was an "open source" site in that everything was explained and shown how to do it manually. But if the 30+ pages overwhelm you, then you can purchase the script kit ($8). c) I might have upset China because they consider me their countrymen. And I guess they don't look too kindly at folks offering security help openly.  

Directors in a townhouse aren't going to bother with this. They will use legal means and hassle your SO and pets. They aren't hackers and won't hire hackers.

MSFT doesn't care about you. Sorry. You aren't that important.  I've had MSFT corporate IPs attack some of my servers.  It wasn't a very organized attack and I have no belief that MSFT cared. Their systems were probably just compromised and being used by others.  

I don't think China cares about you providing bad security advice either, unless you embarrass the CCP.  They typical methods they use are all laid out in their Wolf-Warrior documents which have been leaked online.  They use pressure against family who remain in China.  They directly threaten you and them, often after pulling family into a police station there. Depending on where you live, you might find people working for the Overseas Chinese Police watching you and following you as a form of intimidation.  There are examples of all of these in Europe, Australia, Canada, Africa and the USA.  If you never held a mainland China passport, I'd be surprised if they cared.

I've aided exiled Tibetans with their cyber security in Buddhist Monasteries outside China.  In the end, we were unable to keep the CCP out because at least 1 of the monks living in the monastery was working for them.  So, I split the network so that only office workers had access to the office network which was always locked and used only wired ethernet. No wifi.  I maintained their network remotely for a year and didn't see any new incursions, though their wifi network was terrible and full of attacks, constantly.  Almost every visitor who came for live-in training left with a computer full of viruses.  Monks stayed for free. Live-in Trainees paid as a source of income.  We could have done something about that too, but the Monks in charge wanted convenience over security.  While I was living there, they tried to get me to help with computer issues. I explained I knew nothing about commercial OSes and couldn't help. The idea that there are different OSes seems to confuse people.  If you are a "computer person", you are magically supposed to know everything about every OS ever made.

Anyway, the CCP might bother with you, but you'd know it.  Go out of your way to avoid Chinese-made network devices. Keep your systems patched. Lock your doors. Have a wire security system that posts video to the cloud (not Chinese made or to Chinese servers). Don't use bluetooth or wifi, anywhere, and don't install software outside Canonical's repos.  That's my advice.

Perhaps consider moving to a less dense housing situation.  Housing is cheaper here when we live farther outside the cities. Of course, doing that means transportation costs increase.  There are lots of pros/cons to living farther away from neighbors.

---

### Post by vbgf3 on 2024-08-01
@TheFu,

Thanks for your advice. I know I haven't looked hard enough, but I should be able to find non-chinese made equipment. 

I know, I am deluding myself to think the MS cared about my rants. But then, they did seem to have taken some action, maybe I could call it public relations, or maybe it was just a coincidence. 

Fortunately I don't have any relatives in China. And I have read about their intimidation tactics in the news. But my ex-wife and her relatives are adamantly pro Hong Kong independence, go on marches, set up banners and tables in public meetings etc. Sigh. 

Why did you say I was providing "bad security advise"? 


@currentshaft
"Demonstrate exactly how an adversary is going to subvert apt to "add an extra package" into your system." 

That is purely hypothetical, as the attacker with modem access can do mitm. It is not proven. But if Fedora's DNF package manager has the feature to counter that, then it must be for a reasonable attack vector. I just know with reasonable confidence that the attack vector was apt or it's libraries - I altered the way I re-install my system several times. The vulnerability may have nothing to do with insertion of unwanted packages. But it has something to do with apt update & install. The ******* modified my installation scripts, time after time for a whole month. So I was keen to test out where the attack vector was. I started off from network services  and apps and worked my way thru the list. I apparmored timesyncd and resolved, so they weren't it. Process of elimination works. I was merely asking for a feature that dnf has, as it Might close the true attack vector. But there are many ways that the apt and libraries could have been compromised. I'm to blame for not being well versed in offensive security.
 
You asked about threat model. I just start off with the capabilities that a hacked modem allows. It is definitely hacked as I have seen the attacker's machine via nmap. They have changed the settings of the modem at another time. Don;t ask me to recall all the other indications. From that starting point, and after seeing a variety of attacks, I just have to close off all venues as much as possible. They have the means, and the desire, and every couple of months they come up with some new attack. What else am I supposed to do? Things won't get better, so I have to. (somebody's father came up with that line)  Threat modelling tapers off the list of attackable vulnerabilities ending by dealing with the riskiest ones. I start off from a known vulnerable problem and close off the vectors with hardening measures. And I don't stop until I have the bases covered. I am not spending someone else's money and I just have to apply effort and time. EDIT: I just took a quick look at STRIDE. It seems more methodical than what I do, I will adopt it.

I might just for 1 day forget about this hacked modem business. But it gnaws at me that I can't defend my own system. I got my Security+ 12 years ago and never looked back. Some hacker team has me in their sights and I feel compelled to advance along. Looking at the bright side, I consider myself lucky that I have APT type attacks every now and then; you can't get that sort of experience anywhere else.

---

### Post by currentshaft on 2024-08-01
> **vbgf3 said:**
> 
That is purely hypothetical, as the attacker with modem access can do mitm.


No, they can't. TLS defends against MITM.

> **vbgf3 said:**
> 
It is not proven. But if Fedora's DNF package manager has the feature to counter that, then it must be for a reasonable attack vector.

Counter what? You still have not demonstrated a threat.


> **vbgf3 said:**
> 
I just know with reasonable confidence that the attack vector was apt or it's libraries - I altered the way I re-install my system several times. The vulnerability may have nothing to do with insertion of unwanted packages. But it has something to do with apt update & install. The ******* modified my installation scripts, time after time for a whole month. So I was keen to test out where the attack vector was.

Again, what scripts? What packages? What objective facts led to this conclusion?

> **vbgf3 said:**
> I started off from network services  and apps and worked my way thru the list. I apparmored timesyncd and resolved, so they weren't it. Process of elimination works. I was merely asking for a feature that dnf has, as it Might close the true attack vector. But there are many ways that the apt and libraries could have been compromised. I'm to blame for not being well versed in offensive security. 

What you're saying and doing makes absolutely no sense. I mean no offense by this, but it just doesn't.

It is the result of trying to do security without a threat model. No rational individual nor organization does security by "starting off from network services" and "working their way thru the list".

> **vbgf3 said:**
> 
You asked about threat model. I just start off with the capabilities that a hacked modem allows.

Why? That is not threat modeling. It is fantasy, paranoia and doubt. 

Why not just assume everything is hacked? Your phone, your computer, your TV. It makes no sense either way.

> **vbgf3 said:**
> 
It is definitely hacked as I have seen the attacker's machine via nmap.

What exact output did you see, and why did you assume it meant this?


> **vbgf3 said:**
> They have changed the settings of the modem at another time. Don;t ask me to recall all the other indications. 

Again, this is vague, ambiguous and ultimately 100% useless for understanding, discussing and solving security concerns.

What other settings?

What other indications?


> **vbgf3 said:**
> 
From that starting point, and after seeing a variety of attacks, I just have to close off all venues as much as possible. They have the means, and the desire, and every couple of months they come up with some new attack. What else am I supposed to do?

You have yet to describe even a single "attack" or who is interested enough in "attacking" you.

> **vbgf3 said:**
> 
Things won't get better, so I have to. (somebody's father came up with that line)  Threat modelling tapers off the list of attackable vulnerabilities ending by dealing with the riskiest ones. I start off from a known vulnerable problem and close off the vectors with hardening measures. And I don't stop until I have the bases covered. I am not spending someone else's money and I just have to apply effort and time. And I have a better measurement than a monetary budget - as long as I don't fix this my installation scripts are at peril. I have established some administrative counter measures, but I have to 'fix' this. 

I don't know what you think this is, but I can guarantee you it is not threat modeling.

> **vbgf3 said:**
> 
I might just for 1 day forget about this hacked modem business. But it gnaws at me that I can't defend my own system. I got my Security+ 12 years ago and never looked back. Some hacker team has me in their sights and I feel compelled to advance along. Looking at the bright side, I consider myself lucky that I have APT type attacks every now and then; you can't get that sort of experience anywhere else.

Consider talking to someone about these perceived issues and attacks. I mean that sincerely and wholesomely.

---

### Post by TheFu on 2024-08-01
TLS v1.2 is known to be hacked. Prevent your clients from using it or any lower levels of TLS or SSL.  While I haven't seen TLSv1.3 reported with issues, it has been out a long time.
People often misunderstand how TLS is good. [https://www.youtube.com/watch?v=eRWbNno4sN4](https://www.youtube.com/watch?v=eRWbNno4sN4) explains.  Whenever I see people claim that "TLS secures X", I puke just a little.

---

### Post by QIII on 2024-08-02
@vbgf3:

If you cannot provide definitive proof that you have been hacked/compromised/victimized, I will be disposed to close this thread.

You have taken considerable time from knowledgeable users without giving them a clear target to aim at.

Please provide detail.

---

### Post by vbgf3 on 2024-08-02
@currentshaft
"No, they can't. TLS defends against MITM."

TLS encryption only protects the contents of https traffic.(in other words, browser traffic ) So it does protect your https content from eavesdropping by opponents. But TLS does not protect against packet injection. An entire package can be inserted into ubuntu apt's stream, and TLS wouldn't blink. TLS also does not protect the ip address header. 

Now lets say I used a repository that supports https. Then the traffic contents will be protected against eavesdropping. But since APT handles http as well as https repositories, the encrypted transmission is transparent to it. APT checks on the package itself being OK and not tampered with. If the attacker inserts a properly signed package, APT will proceed to install it. His package being OK and valid does not preclude that it is not something I want on my system, like for example open-sshd. ( I don't want/need remote access capability )

 I don't want to point this out in your face, but you overvalue encryption and think it solves all problems. 

So the scripts I mentioned are post installation scripts that I run to configure Ubuntu; copying over conf files, removing unwanted packages and so on. The attacker has modified my scripts so that they fail, by making a syntax error here and there etc. I know the scripts should run pefectly because I wrote and debugged them. And that is tampering in STRIDE.

You are harboring the thought that all my thinking is paranoia and fantasy. But my failed scripts are evidence of tampering. And I have shown the mitm can still be done. If you want to, you can look into the many techniques that can be used to implement mitm. Arp manipulation is my favorite. 

"[COLOR=#000000]Counter what? You still have not demonstrated a threat." 
So now I have demonstrated a threat. And that is mitm. Fedora dnf's transaction checks protect against a package being inserted into an upgrade stream.

And also, since the attacker was modifying my installation scripts, they too are not protected by the existence of TLS 1.3. TLS encryption solves only particular problems. But does not protect me in this instance. Now you can re-read what I am doing and consider it in a different light. 


[/COLOR]

---

### Post by vbgf3 on 2024-08-02
..

---

### Post by vbgf3 on 2024-08-02
[COLOR=#000000]..[/COLOR]

---

### Post by currentshaft on 2024-08-02
> **vbgf3 said:**
> 
TLS encryption only protects the contents of https traffic.(in other words, browser traffic ) So it does protect your https content from eavesdropping by opponents. But TLS does not protect against packet injection. An entire package can be inserted into ubuntu apt's stream, and TLS wouldn't blink. TLS also does not protect the ip address header. 

This is absolute nonsense. It really is.

Inject packets into an end-to-end encrypted TLS stream? How would that even work?

You realize 99.99% of websites support TLS 1.2, right?

If what you're saying is true, then no website on the internet is secure.

Of course it's not true and we can all breathe a sigh of relief.

Also, why does the "IP address header" need "protection"? From this comment alone it is apparent you don't understand the technology being discussed.

> **vbgf3 said:**
> 
Now lets say I used a repository that supports https. Then the traffic contents will be protected against eavesdropping. But since APT handles http as well as https repositories, the encrypted transmission is transparent to it. APT checks on the package itself being OK and not tampered with. If the attacker inserts a properly signed package, APT will proceed to install it. His package being OK and valid does not preclude that it is not something I want on my system, like for example open-sshd. ( I don't want/need remote access capability )


How would an attacker insert a properly signed package ... without the keys? Using magic?

> **vbgf3 said:**
> 
 I don't want to point this out in your face, but you overvalue encryption and think it solves all problems. 


I never made that assertion, nor was it implied.

> **vbgf3 said:**
> 
So the scripts I mentioned are post installation scripts that I run to configure Ubuntu; copying over conf files, removing unwanted packages and so on. The attacker has modified my scripts so that they fail, by making a syntax error here and there etc. I know the scripts should run pefectly because I wrote and debugged them. And that is tampering in STRIDE.

What OBJECTIVE PROOF do you have of this happening? If you have no OBJECTIVE PROOF, it DID NOT HAPPEN. Is that clear yet?


> **vbgf3 said:**
> 
You are harboring the thought that all my thinking is paranoia and fantasy. But my failed scripts are evidence of tampering. And I have shown the mitm can still be done. If you want to, you can look into the many techniques that can be used to implement mitm. Arp manipulation is my favorite. 

What failed scripts? You have posted zero evidence of anything. Just an incoherent rant about apt packages which defies all logic and even common sense.


> **vbgf3 said:**
> 
So now I have demonstrated a threat. And that is mitm. Fedora dnf's transaction checks protect against a package being inserted into an upgrade stream.

No, you did not demonstrate a threat.

You made an unqualified and wrong opinion on how apt package integrity works.

You made a word-salad of some common information security terminology which did not logically compute.

That wrong understanding is compounded by your stubborn attitude and unwillingness to even consider the possibility you might be wrong.

I have tried my best to help you, but without providing artifacts of your situation (logs, command outputs, screenshots, etc), it won't be possible to have a productive discussion.

---

### Post by TheFu on 2024-08-02
[https://www.zdnet.com/article/china-is-now-blocking-all-encrypted-https-traffic-using-tls-1-3-and-esni/](https://www.zdnet.com/article/china-is-now-blocking-all-encrypted-https-traffic-using-tls-1-3-and-esni/) - that's from 2020.  The Chinese "Great Firewall" only allows encryption that they can crack

** Exceptional claims require exceptional proof.**

We're 13 posts in this thread and no real facts have been posted, just claims.

---

### Post by vbgf3 on 2024-08-02
Hi currentshaft: 

Here is a clear explanation :   [https://community.isc2.org/t5/Tech-Talk/link-encryption-vs-end-to-end-encryption/td-p/68194#:~:text=The%20two%20methods%20of%20encryption,application%20of%20the%20IP%20header](https://community.isc2.org/t5/Tech-Talk/link-encryption-vs-end-to-end-encryption/td-p/68194#:~:text=The%20two%20methods%20of%20encryption,application%20of%20the%20IP%20header).

In summary there are 2 ways of doing it. One is End to End ecryption, which does not encrypt the ip address header. It only encrypts the data. With the ip address header in clear text, routers on the internet can route the packet

The other is Link encryption which does encrypt the ip address header. This requires dedicated connection points for both ends.

Here is another explanation:   [https://en.wikipedia.org/wiki/HTTPS#:~:text=Strictly%20speaking%2C%20HTTPS%20is%20not,and%20the%20request%2Fresponse%20data](https://en.wikipedia.org/wiki/HTTPS#:~:text=Strictly%20speaking%2C%20HTTPS%20is%20not,and%20the%20request%2Fresponse%20data).

---

### Post by currentshaft on 2024-08-02
> **vbgf3 said:**
> Hi currentshaft: 

Here is a clear explanation :   [https://community.isc2.org/t5/Tech-Talk/link-encryption-vs-end-to-end-encryption/td-p/68194#:~:text=The%20two%20methods%20of%20encryption,application%20of%20the%20IP%20header](https://community.isc2.org/t5/Tech-Talk/link-encryption-vs-end-to-end-encryption/td-p/68194#:~:text=The%20two%20methods%20of%20encryption,application%20of%20the%20IP%20header)

The amount of nonsense techno-babble in that post is truly impressive. It makes this entire thread look like an O'Reilly book by comparison. I mean, it is truly stupid stuff.

It's time to stop following what some random online strangers are contriving and time to start doing threat modeling, if security is a priority.

And to state the obvious again: Ubuntu apt is not at risk of "unauthorized updates are inserted into the upgrade stream". Such bold claims will require bold evidence.

---

### Post by QIII on 2024-08-03
OK.  That'll do for now.

Closed.

---

