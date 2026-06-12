---
title: "Opinions on SSH"
date: 2008-07-02
forum: Security
---

### Post by sp0nge on 2008-07-02
So I am exploring remote access as a hobby as I see a need for secure access to a server at my office soon. I figured I'd get a jump on the action so I know what I'm talking about. Thanks in advance for the education. 

I have set up a test server in my home that has been fitting my needs for the moment. In order to understand all variables associated with remote access to a server, a friend of mine has allowed me to put my server on his network. I'm looking for opinions on the most secure way to accomplish this task. Is there something better than SSH?

---

### Post by hyper_ch on 2008-07-02
Have a look at the ssh config and there you can set a few things... like only enable remote ssh access for a specific user...

But generally ssh is the most secure way IF

(a) you use a strong password (or even make keybased login)
(b) use some tool to prevent brute-froce like denyhosts
(c) use a computer that is not compromised itself from which you log into your sshed machine

---

### Post by Aearenda on 2008-07-02
I use SSH for remote support across the internet, no root allowed, on a high port (not 22 - this avoids the annoying script-kiddies) and with mandatory RSA certificates.

---

### Post by hyper_ch on 2008-07-02
different port won't really help...

---

### Post by rickyjones on 2008-07-02
> **hyper_ch said:**
> different port won't really help...

Using a non-standard port will indeed help by hiding the service from the most common attack vector - bots - as an additional layer of security. This, in addition to strong passwords and only allowing specific users, will most likely be a secure set up.

As for general remote access into a network I prefer only opening a VPN port. Once the VPN is connected I can use SSH/RDP/VNC/Etc... to any extent that I wish. Beyond that SSH is a great alternative for getting to the remote console.

Sincerely,
Richard

---

### Post by kevdog on 2008-07-02
SSH is great and real easy to use, clients are available for both windows and linux.  

Just a few thoughts -- not really recommendations:
1. Different Port -- Yes great idea, will cut down on the number of false authentication attempts

2. Limiting repeated authentication attempts -- This can be done a number of different ways -- deny hosts or fail2ban are two methods.  Only problem with these methods are that once the client IP is put on the blacklist, it will always be banned unless you log into the server and delete the IP address from the blacklist file.  This can be a good thing or bad thing.  If you happen to be having a really bad day and type your password wrong like 3 or 5 times in a row (you realize you had the caps key on the whole time or something) you will never be able to log in without editing the file on the server.  

Another way to limit false authentication attempts would be to use iptables to filter the number of connection attempts per minute/hour etc.  This would temporarily ban an IP address but allow for later authentication attempts.  This could be a good or bad thing depending on your needs.

3. Use of keys are better than passwords however are definitely more inconvenient. If using passwords, make sure they are long.  I like the term passphrase instead of password.  For example, if you type with quotes "Mary had 430 little lambs eating in a garden" -- this could be your passphrase or password (as long as you used quotes).  Passphrases are generally longer -- easier to remember -- and are not subject to dictionary based attacks since they are really more than one word.

4. If superparanoid about unauthorized access, you could run ssh along with the iptables firewall along with a port knocker utility such as fwknop.  fwknop requires a client however to issue a port knocking sequence to stealthly temporarily open up a  hole in your firewall to allow you to access your ssh server for a limited period of time (for example 30 seconds).  For most people this is overkill -- however I have written a tutorial on how to do this if you are interested.  Its fun to play with, however for most people (including me) its overkill, but fun none-the-less.

5. SSH vulnerability -- Make sure you are using the most recent version of ssh since version in edgy, fiesty, gutsy, etc contained a compromised version with a faulty OpenSSL library.  This was big news -- there is a sticky about this at the top of the security section.

Other than that ssh is really easy to use --- If you are having problems with your office firewall for example, you could always run ssh with reverse tunneling to allow access from your home to work if your work firewall blocks incoming connections.

---

### Post by ilrudie on 2008-07-02
ssh and turn off root logins.  if you need root login from you user account and su to root.

---

### Post by brian_p on 2008-07-02
> **ilrudie said:**
> ssh and turn off root logins.  if you need root login from you user account and su to root.

I've never really understood this advice. As a general point, why should ssh access with a sixteen character password be any less secure for root than for  another user? In the particular case of Ubuntu there is no root account so it's superfluous.

---

### Post by rickyjones on 2008-07-02
> **brian_p said:**
> I've never really understood this advice. As a general point, why should ssh access with a sixteen character password be any less secure for root than for  another user? In the particular case of Ubuntu there is no root account so it's superfluous.

You can restrict what users can "su" to root I do believe.

Therefore a cracker will need to a) guess the correct user and b) crack their password and c) crack the root password. This is opposed to NOT locking out root in which case a cracker needs to only crack the root password, since root is a common user on most *nix systems.

Sincerely,
Richard

---

### Post by kevdog on 2008-07-02
16 character passwords -- it would depend on the randomness of the password.  I know there are password strength meters out there the grade the level of randomness.  I don't know if their measure is accurate however.

---

### Post by hyper_ch on 2008-07-02
> **rickyjones said:**
> Using a non-standard port will indeed help by hiding the service from the most common attack vector - bots - as an additional layer of security. This, in addition to strong passwords and only allowing specific users, will most likely be a secure set up.

Security through obscurity doesn't work - look at Windows ;)

---

### Post by sp0nge on 2008-07-02
Thanks for the valuable information! I'll be reading up on your suggestions. 

At the moment, this is only for my own personal server to understand what I'm doing, but eventually I'll be implementing what I learn for the business as well. 

I think I'll start experimenting with SSH, deny host or fail2ban, opening a different port, and I'm one for making off the wall and very long pass phrases. 

Are the issues with the faulty OpenSSL library resolved?

---

### Post by rickyjones on 2008-07-02
> **hyper_ch said:**
> Security through obscurity doesn't work - look at Windows ;)

I agree with you that security through obscurity alone is not true security at all. However security through obscurity as a layer is a great way to strengthen the security of your system as a whole.

You have a door in a wall that leads to a secret room. This door is protected with a keypad that requires a valid ID and a valid PIN.

Which scene will increase your security: Hiding the door behind another object; or keeping the door in the open advertising where it is.

In my example hiding the door would be equivalent to changing the SSH port to a non-standard port, like 22222. Keeping the door in the open would be leaving the port at 22.

Security through obscurity alone does not work. However it is a great asset when used in tandem with the other necessary layers of security.

Sincerely,
Richard

---

### Post by kevdog on 2008-07-02
The openssl source has been patched (for the most recent vulnerability) so if you have been doing updates then you have received the new implementation.

My suggestion just to start off with is to get the system up and running.  Install the openssh-server package, keep the port 22 temporarily, and try to connect from client to server using a passphrase or complex password.  You can build complexity to the server with fail2ban, etc once you have things up and running.  Don't get too fancy too quick or you wont know where something went wrong.  In most cases, running ssh on a different port with use of a long passphrase should be sufficient, the next additional layer would be the use of public/private keys.  

Add only filtering mechanisms -- fail2ban, blacklists, iptables -- once the system is running the way you want it.

Remember many employers have restrictive firewalls allowing only outbound but not inbound connections (ie home to work).  In this case you will have to make use of reverse ssh tunneling.  I'm not sure if you will need this, however in many cases people can't successfully connect from home to work if they setup a ssh daemon server at work since the work firewall blocks inbound connections.  Not sure if this is applicable in your case.

Lastly this ssh solution is capable of running on a mix of linux/mac/windows boxes --- most of the implementations should be universal.

---

### Post by brian_p on 2008-07-02
> **rickyjones said:**
> This is opposed to NOT locking out root in which case a cracker needs to only crack the root password, since root is a common user on most *nix systems.

If I added 'random' to 'sixteen character' how feasible would you it was to crack the root password, or any user's password  for that matter? This was really my point about the transmitted wisdom of not allowing a root login with ssh.

---

### Post by brian_p on 2008-07-02
> **kevdog said:**
> 16 character passwords -- it would depend on the randomness of the password.  I know there are password strength meters out there the grade the level of randomness.  I don't know if their measure is accurate however.

Ok then, 16 random characters. Or a key based login. Surely the chance of cracking either makes advising against logging in as root strange to say the least.

---

### Post by kevdog on 2008-07-02
Sounds good to me :)  Thats all a key is anyway -- a random excessively long password.

---

### Post by The Cog on 2008-07-02
Also consider looking at openvpn for your connectivity. It provides full host-host networking of any protocols you want - VNC, file sharing etc. I use it to access our servers from home on occasions.

---

### Post by hyper_ch on 2008-07-03
> **rickyjones said:**
> Which scene will increase your security: Hiding the door behind another object; or keeping the door in the open advertising where it is.

In my example hiding the door would be equivalent to changing the SSH port to a non-standard port, like 22222. Keeping the door in the open would be leaving the port at 22.

Security through obscurity alone does not work. However it is a great asset when used in tandem with the other necessary layers of security

You leave the door open because you can simply nmap ;) Assume an attacker knows your system - and he does because all if opensource.... changing ports will only lead to believe yourself that you feel safer... the only thing it does is reduce number of log entries ;)

---

### Post by Aearenda on 2008-07-03
> changing ports will only lead to believe yourself that you feel safer... the only thing it does is reduce number of log entriesYep, that's why I do it. People rattling the door to see if it's locked annoy me. I rely on the key to keep it secure against those who do find it.

---

### Post by rickyjones on 2008-07-03
> **hyper_ch said:**
> You leave the door open because you can simply nmap ;) Assume an attacker knows your system - and he does because all if opensource.... changing ports will only lead to believe yourself that you feel safer... the only thing it does is reduce number of log entries ;)

Err, the door is still quite closed behind your username and password. Please remember this is a layered approach to security. However the same logic that you just used can be applied to your password.

Assume the attacker knows you and therefore has a good guess on your password. 

Also to keep in mind that a truly determined hacker will easily discover your non-standard port - I've never denied that. However the majority of attacks are done by scripted bots which will: 1. Ping an IP. 2. Probe port 22. 3. If SSH is running on port 22 then begin password crack program. 4. If SSH is not running on port 22 then skip host and do not go back.

This is where layered security comes into play. Why allow the common attack vector when you can change the playing field to your advantage? 

Let me reiterate: Changing ports alone will NOT make you fully secure (the only fully secure solution is to turn off your server...). However, changing ports will add an additional layer of security over your (hopefully) already strong passwords. This will lower the number of attacks which will lower the number of possible penetrations.

Sincerely,
Richard

---

### Post by hyper_ch on 2008-07-03
changing ports will not improve security at all... it will just clear the logs ;)

---

### Post by kevdog on 2008-07-03
> **hyper_ch said:**
> changing ports will not improve security at all... it will just clear the logs ;)


Hey isn't that valuable at all if you are trying to save disk space?

---

### Post by rickyjones on 2008-07-03
> **hyper_ch said:**
> changing ports will not improve security at all... it will just clear the logs ;)

Others in the security field might just disagree with you. For debate sake we may just have to agree to disagree. I obviously have not changed your viewpoint and I refuse to yield to your view that changing ports will do nothing to enhance security. However I feel that it is important to point out others that believe as I do.

[http://www.heise-online.co.uk/networks/Any-port-in-a-storm-moving-for-more-security--/features/110022](http://www.heise-online.co.uk/networks/Any-port-in-a-storm-moving-for-more-security--/features/110022)
[http://www.itworld.com/nls_unixssh0500506](http://www.itworld.com/nls_unixssh0500506)
[http://isc.sans.org/diary.html?storyid=4408](http://isc.sans.org/diary.html?storyid=4408)
[http://people.clarkson.edu/~owensjp/pubs/leet08.pdf](http://people.clarkson.edu/~owensjp/pubs/leet08.pdf)

Didn't we have this debate a few weeks ago? I seem to recall that :P.

Sincerely,
Richard

---

### Post by hyper_ch on 2008-07-03
if you read those, they don't say it makes it more secure but lowers brute-force a bit... but in the end it won't help against brute-force either and hence doesn't make it more secure ;)

---

### Post by rickyjones on 2008-07-03
> **hyper_ch said:**
> if you read those, they don't say it makes it more secure but lowers brute-force a bit... but in the end it won't help against brute-force either and hence doesn't make it more secure ;)

You did read the last link, the security paper, where they ran two SSH installs correct? One was on port 22 and one was on a non-standard port. In the same time period approximately 100,000 brute force attempts were recorded against the SSH server on port 22. Zero were attempted on the other SSH server.

If the attacker is not attempting to attack you because it does not know where to look then how is this no more secure? 

Security is increased when you lower the risk and chance of attack. Why do people disallow root logins from SSH? Does it really make you any safer as long as you use a strong password? I feel it does, and many in the security industry would agree because it mitigates risk by making it more difficult to get to the target.

I appreciate the debate that we have going on here. :)

Sincerely,
Richard

---

### Post by hyper_ch on 2008-07-03
> **rickyjones said:**
> You did read the last link, the security paper, where they ran two SSH installs correct? One was on port 22 and one was on a non-standard port. In the same time period approximately 100,000 brute force attempts were recorded against the SSH server on port 22. Zero were attempted on the other SSH server.
So? Install denyhosts and you take care of those - and possibly real attacks also ;)

> **rickyjones said:**
> If the attacker is not attempting to attack you because it does not know where to look then how is this no more secure?
those you need to worry about are not the script kiddies and for those it doesn't matter what port you're on ;)

> **rickyjones said:**
> Security is increased when you lower the risk and chance of attack.
If you can count an action as attack first-place


> **rickyjones said:**
> Why do people disallow root logins from SSH? Does it really make you any safer as long as you use a strong password?
Yes, it does... if there's no sudo in place with temporary root rights it does make it more difficult... because at frist you have to guess a username and then also the according password... once you get that, you have only limited access to the box... for root the username is known ;)[/QUOTE]

---

### Post by rickyjones on 2008-07-03
> **hyper_ch said:**
> 
Yes, it does... if there's no sudo in place with temporary root rights it does make it more difficult... because at frist you have to guess a username and then also the according password... once you get that, you have only limited access to the box... for root the username is known ;)

You agree that making the attacker guess the correct username and then crack the password makes for better security. However you deny that making the attacker guess the correct port and then guess the username and then crack the password is no more secure?

Sigh, we really seem to have knack for disagreeing with each other regarding this issue. As for using DenyHosts to thwart the issue... I'd prefer to not rely on yet another third party package when the service already has a mechanism built in that I can use to my advantage.

Sincerely,
Richard

---

### Post by brian_p on 2008-07-03
> **rickyjones said:**
> If the attacker is not attempting to attack you because it does not know where to look then how is this no more secure?

The attacker does know where to find you but is either too thick to look or can't be bothered. 

> Security is increased when you lower the risk . . . 

Yes.

>  . . . . and chance of attack.

If the risk is zero (ssh keys, for example) the chance of attack doesn't matter. Also, risk and frequency of attack may not be correlated at all. Trebling the rate of inept login attempts doesn't increase the risk.

> . . . . because it mitigates risk by making it more difficult to get to the target.

If the target is protected by a weak password taking evasive action is about all you can do and your argument has merit. It's when the password is very strong or key based authentication is in place that it begins to fail.

---

### Post by Dr Small on 2008-07-03
Simply put, having SSH listen on a high port will stop alot of automated attacks. These attacks can't be considered crucial since they are only meer dictionary attacks.

But if an attacker deemed to break into your system, they would not stop at a closed port 22. He would port scan, find the open port, and then attack. Changing the port for SSH does not really make you more secure against crucial attacks, as the point hyper_ch is trying to bring across.

---

### Post by hyper_ch on 2008-07-03
> **rickyjones said:**
> You agree that making the attacker guess the correct username and then crack the password makes for better security. However you deny that making the attacker guess the correct port and then guess the username and then crack the password is no more secure?

The attacker does not have to guess the port... he'll just nmap you and knows the port ;)

---

### Post by movieman on 2008-07-03
> **hyper_ch said:**
> The attacker does not have to guess the port... he'll just nmap you and knows the port ;)

Except, as has been pointed out, 99.99% of 'hackers' will just try to connect to port 22 and then move on to the next machine when they find nothing there. A tiny minority will scan other ports, but a decent firewall should auto-block such port-scans anyway.

You're right that a determined hacker won't be delayed long by using a non-standard port, but if you're just running a home server then you're highly unlikely to be attacked by a determined hacker. For Joe Average who just wants to ssh into their home PC from elsewhere, using a non-standard port is vastly more secure than using the default and will probably stop all attempts to break in through ssh; use a non-standard port and large, unpublished, public keys, and, even if he is attacked by a determined hacker, he won't see any intrusions other than through flaws in ssh itself.

There is zero reason to open your system up to attacks from script-kiddies, even if those attacks are likely to fail. If there is a flaw found in ssh (e.g. the recent keygen debacle) you can be sure that any system with ssh on port 22 is far more likely to be attacked and broken into than a system with ssh on port 50491.

---

### Post by hyper_ch on 2008-07-03
but those 99% aren't hackers but script kiddies that you don't have to worry about anyway...

---

### Post by movieman on 2008-07-03
> **hyper_ch said:**
> but those 99% aren't hackers but script kiddies that you don't have to worry about anyway...

Until one of your users uses a weak password, or a flaw is found in ssh itself; then you're toast and I'm still 99.99% safe.

I honestly don't see why you would prefer to have script kiddies attacking your system than not have them attacking it.

---

### Post by hyper_ch on 2008-07-03
script kiddies won't find a flaw in ssh themselves... those who do will nmap... so you're toast anyway... against auto-brute-force you have measures... so script-kiddies don't attack, they just annoy ;)

---

### Post by Dr Small on 2008-07-03
> **movieman said:**
> Except, as has been pointed out, 99.99% of 'hackers' will just try to connect to port 22 and then move on to the next machine when they find nothing there.

No. These are not hackers. These are automated bots, written by scriptkiddies. Why would these script kiddies waste their time attempting to break-in to 1000 servers, when all they have to do is write a script to do it all.

Trust me, it is easy. And hackers don't waste their time with such stuff. So since script kiddies are running bots to bruteforce your machine, having a strong password or ssh key will instantly stop them.

---

### Post by movieman on 2008-07-04
> **Dr Small said:**
> So since script kiddies are running bots to bruteforce your machine, having a strong password or ssh key will instantly stop them.

Running ssh on a port other than 22 will stop them much faster. Again, why would you prefer to have script kiddies attacking your machine than not have them attacking it?

Hardly any home user systems (unless they're living in the White House or working for the CIA) will ever be attacked by a competent hacker, but it only takes one previously unknown ssh flaw to be exploited in a kiddy script for a large number of home systems running ssh on port 22 to be toast. Why would anyone want their system to be exposed in that way? I just don't get it.

Imagine, for example, that the debian SSH key flaw had been discovered by hackers first and the script kiddies had got hold of it a few days before the developers. Any debian-based system running with ssh on port 22 using RSA keys could have been compromised in minutes... while any system with ssh on port 37901 would have been pretty safe.

There is simply no benefit to running ssh on port 22 other than slightly shorter command lines to log in or copy files. Not running it on port 22 could easily make the difference between a compromised system and an uncompromised system, at least for a typical home user.

---

### Post by hyper_ch on 2008-07-04
> **movieman said:**
> Imagine, for example, that the debian SSH key flaw had been discovered by hackers first and the script kiddies had got hold of it a few days before the developers. Any debian-based system running with ssh on port 22 using RSA keys could have been compromised in minutes... while any system with ssh on port 37901 would have been pretty safe.
Unlikely... if hackers will finde a weakness, they will either use it themselves or tell the developpers.... however why should they leak it to script kiddies?
If they are good-hearted they will tell the devs.... if not, then they want to profit from it themselves ;) so that scenario about leaking to script-kiddies is rather... unconvincing...

And besides, a home user will not just install a ssh server... and if they do, they should know what they are doing ;)

---

### Post by Dr Small on 2008-07-04
> **movieman said:**
> Running ssh on a port other than 22 will stop them much faster. Again, why would you prefer to have script kiddies attacking your machine than not have them attacking it?


The point is, and we have sorta went off base here, that just because you move ssh to a higher port, it doesn't make you more secure. Sure, changing ports stops alot of bots hammering port 22, but so what? They are really harmless if your server is secure.

---

### Post by brian_p on 2008-07-04
> **movieman said:**
> Again, why would you prefer to have script kiddies attacking your machine than not have them attacking it?

It passes the time now that Euro 2008 is over (excellent hosting by the way, Austria and Switzerland) and provides some amusement to watch their futile efforts.

> Imagine, for example, that the debian SSH key flaw had been discovered by hackers first and the script kiddies had got hold of it a few days before the developers. Any debian-based system running with ssh on port 22 using RSA keys could have been compromised in minutes... while any system with ssh on port 37901 would have been pretty safe.

Any Debian based system? Minutes? You're joking! First off, it was only key based systems which were at risk. Secondly the key space may have been much reduced but was still large enough to hold up for longer than that - assuming a valid username was guessed. Thirdly, you are endowing script kiddies with intelligence.

---

