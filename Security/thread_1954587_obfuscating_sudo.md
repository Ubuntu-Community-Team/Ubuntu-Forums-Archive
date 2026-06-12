---
title: "obfuscating sudo"
date: 2012-04-08
forum: Security
---

### Post by cholericfun on 2012-04-08
Hi

just a thought - i'm not an expert, especially when it comes to security. Would it make sense to mv the sudo binary to some different (nonsense) location with a different name (e.g. a.out) to prevent attackers using it even when they have ssh access to the machine? As a little extra a fake /usr/bin/sudo could just print out "please try again" while mailing the admin about it beeing used.

Similar things could be done with other bins in order to stop an attacker from using "normal" commands to manipulate the system. E.g. the ls command could be "aliased" to pretend to show/ not show files that dont correspond to the actual situation on the disc. 

Are such things done and would they help/make sense?

thanks

PS "obfuscating sudo" doesnt return any google hits...

---

### Post by roelforg on 2012-04-08
no,
it won't matter as sudo doesn't contain sensitive stuff and people willing to do the effort don't even bother with sudo.
It will probably break stuff as well.
Loads of stuff uses direct paths to bins.
And this'll be a lot like the "i organised all my files and now my pc won't boot" call every techie lauchs about and fears

---

### Post by CharlesA on 2012-04-08
> **cholericfun said:**
> Hi

just a thought - i'm not an expert, especially when it comes to security. Would it make sense to mv the sudo binary to some different (nonsense) location with a different name (e.g. a.out) to prevent attackers using it even when they have ssh access to the machine? As a little extra a fake /usr/bin/sudo could just print out "please try again" while mailing the admin about it beeing used.

Similar things could be done with other bins in order to stop an attacker from using "normal" commands to manipulate the system. E.g. the ls command could be "aliased" to pretend to show/ not show files that dont correspond to the actual situation on the disc. 

Are such things done and would they help/make sense?

thanks

PS "obfuscating sudo" doesnt return any google hits...

Easy fix, secure ssh if you have it installed and make sure you use a *strong* password. Moving binaries around is a good way to hose your system.

---

### Post by ridetheteapot on 2012-04-08
Not sure if this applies here - but you don't need every user to be able to su root, so just make yourself the only admin level user.

If someone gets ssh access who isn't supposed to you have other problems :-D In which case you need to (1) use a better password (2) or use keys, because you _can_ brute force a ssh server (if you have a botnet lol) (3) use a nonstandard port for ssh, because unless your a big target, nobody is going to try to randomly bruteforce your port xxxx ssh server (4) set up port knocking for your server.

---

### Post by CharlesA on 2012-04-08
Just a note - using a non-standard port just cuts down on log clutter and doesn't really protect you if someone really wanted to get in.

---

### Post by haqking on 2012-04-08
to the OP

Obfuscation of system files and binaries will quickly lead you to a hosed system and severe headaches.

Most naming conventions are for usability and are often identified by the system in a different manner.

When it comes to users like you mentioned, most hackers/pen testers are concerned with root privelege and all accounts have a UUID which indicates its usage. (Root UUID = Zero)

A admin user will have a group id GID of 4

Similar to in Windows no matter whether you rename the Administrator account or not it doesnt mean anything as the SID will end in :500

Peace

---

### Post by ridetheteapot on 2012-04-08
Using a nonstandard port cuts down on the amount of automated scanning large ip blocks from targeting your service randomly. See "hail mary cloud".


__Edit___
just to clarify, my above post about admin su root, I am talking wheel group - if i caused any confusion. Already assuming ssh login as root is disabled.

---

### Post by haqking on 2012-04-08
> **ridetheteapot said:**
> Using a nonstandard port cuts down on the amount of automated scanning large ip blocks from targeting your service randomly. See "hail mary cloud".

that is true.

but a simple nmap scan with service detection will reveal the service regardless of port.

To the OP, changing default port will aid you and offer a little more security but it is still simple to figure out even if port is changed.

Peace

---

### Post by ridetheteapot on 2012-04-08
haqking have you seen the new ssh bruteforce news spreading around.
Using a password auth system on port 22 is becoming a specific problem.
[http://bsdly.blogspot.com/2012/04/if-we-go-one-attempt-every-ten-seconds.html](http://bsdly.blogspot.com/2012/04/if-we-go-one-attempt-every-ten-seconds.html)

Sure using nmap sV is gonna show up the service (number (4) also recommends port knocking though), but even then by default nmap doesnt scan all ports, you are even better off if you choose a port not on that list, but law of diminishing returns blah blah. Obviously if your a target someone is gonna find your ssh server (well maybe knock knock).

---

### Post by haqking on 2012-04-08
> **ridetheteapot said:**
> haqking have you seen the new ssh bruteforce news spreading around.
Using a password auth system on port 22 is becoming a specific problem.
[http://bsdly.blogspot.com/2012/04/if-we-go-one-attempt-every-ten-seconds.html](http://bsdly.blogspot.com/2012/04/if-we-go-one-attempt-every-ten-seconds.html)

Sure using nmap sV is gonna show up the service (number (4) also recommends port knocking though), but even then by default nmap doesnt scan all ports, you are even better off if you choose a port not on that list, but law of diminishing returns blah blah. Obviously if your a target someone is gonna find your ssh server (well maybe knock knock).

yes im aware of it.

I wasnt saying not to use a non standard port, indeed i recommend it, my point was it is still relatively easy to discover.

and most people using nmap wouldnt do a default scan anyways.

---

### Post by CharlesA on 2012-04-08
Interesting link, thanks.

Doesn't port knocking have it's own advantages/disadvantages?

Sidenote: I'm using keys, but I have a feeling having a strong password (10-20 characters) would stand up to bruteforcing just fine.

---

### Post by ridetheteapot on 2012-04-08
I guess it does, its only an extra layer of obfuscation....
It's like equivalent to an extra plain text password to 'see' the service.
keys are better, probably the decent 10 char password will not get bruteforced, but the chance of a key getting 'bruteforced' is so much lower (possible to bf private keys though).

this was just a best practices list that I use. because in the original op post I wasn't sure where these users who we ware trying to stop from getting root are coming from.
Like if its an user with a legit account your trying to block, then just use the wheel group access, but if not you have to worry about this other stuff. (ie accessed your admin on the wheel account by evil doing)


EDIT___
just to complete the list, and i think ubuntu openssh is preconfigured this way. you want to limit failed login attempts. (why i was referring to distributed bruteforce attacks at all)

---

### Post by CharlesA on 2012-04-08
> **ridetheteapot said:**
> I guess it does, its only an extra layer of obfuscation....
It's like equivalent to an extra plain text password to 'see' the service.
keys are better, probably the decent 10 char password will not get bruteforced, but the chance of a key getting 'bruteforced' is so much lower (possible to bf private keys though).

this was just a best practices list that I use. because in the original op post I wasn't sure where these users who we ware trying to stop from getting root are coming from.
Like if its an user with a legit account your trying to block, then just use the wheel group access, but if not you have to worry about this other stuff. (ie accessed your admin on the wheel account by evil doing)
Pretty good best practices list overall.

Check out the security link in my sig for some nice infos. ;)

---

### Post by ridetheteapot on 2012-04-08
ROFL thanks charles, i checked it out and loved that link on the bottom "didijustgetowned". most righteous.

"I saw this output on a log. Is it bad?"

Anyway brings up the reason I am in no rush to see linux take over the desktop. I mean really is it easier to write a rootkit on *any* oss system or windows? i mean a rk can be as simple as editing the source of cp,ls, and whatever checksum ppl are using at the time to feel safe. It really surprised me to read peoples reactions to the recent apple situation - it's like "that could so easily be us dude." and I bet one day clamav will be crawling launchpad ppas...

---

### Post by CharlesA on 2012-04-08
The weakest link is always the user.

---

