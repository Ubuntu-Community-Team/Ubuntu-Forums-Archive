---
title: "Need help securing a Linux box."
date: 2009-01-30
forum: Security
---

### Post by J4m35 M. on 2009-01-30
Hello all~

I'm Going to a Cyber Defense Competition in Feb. and my teacher picked me to be in charge of our Linux box's. They will consist of Ubuntu 6.06, Fedora Core 5, and Free BSD.. (have never even used BSD before) I'm fairly comfortable with Ubuntu, and can move around in command line fairly decent for being a noob. I was just wondering if anyone had any suggestions on; 1.) What would be the best firewall choice, and 2.) any other suggestions to make it nearly impossible to hack/exploit.

    Thank you in advance for your time! (^_^)y
                        Jim~

---

### Post by Masuran on 2009-01-30
Some basic recommendations I give all our clients

**1. Firewall / Packet Filtering:**
 Block everything, only allow what you really need
**2. SSH Configuration:**
 If using SSH, disable root login and password authentication (use Key authentication instead)
**3. Use Ubuntu LTS**
**4. Updates, updates, updates**
 Only update from official repositories, update regularly, subscribe to security mailinglists and update when security updates are available. If repositories are behind important patches then consider updating manually.
**5. Custom software? **
 If using custom software (not from repo's) then follow their updates and security mailinglists daily! And don't forget to apply updates :)

Some other remarks: 
[LIST]
[*]Changing ports is bullsh*t, any decent security expert will port scan you
[*]I**D**S is good but in your case only good if it has I**P**S. **Detection **is good but you will get hacked, so make sure you also got **Prevention**.
[/LIST]

If you want some real good advice tell us more what the boxes should do. If they should just sit there being boxes it will be a breeze. What services will they run, etc?

---

### Post by tubbygweilo on 2009-01-30
J4m35 M.,
Nay I suggest a browse over to [http://daemonforums.org/]("http://daemonforums.org/") for a few ideas as to how you can keep your BSD flavoured box safe and sound.

---

### Post by J4m35 M. on 2009-01-30
Thanks, and as far as I know, the boxes only have to be able to communicate with each other on the LAN, the setup is an Access point, a router, xp, vista, server 03, server 2000, and then my three boxes, Ubuntu 6.06, Fedora core5, and not to sure on the version of FreeBSD, but yea, as far as I know they only have to be able to communicate with the other boxes in the Network, while a team of professional hackers attempts to break in.

---

### Post by Masuran on 2009-01-30
> **J4m35 M. said:**
> Thanks, and as far as I know, the boxes only have to be able to communicate with each other on the LAN, the setup is an Access point, a router, xp, vista, server 03, server 2000, and then my three boxes, Ubuntu 6.06, Fedora core5, and not to sure on the version of FreeBSD, but yea, as far as I know they only have to be able to communicate with the other boxes in the Network, while a team of professional hackers attempts to break in.

What do you mean with communicate? File sharing using SMB/CIFS/NFS, HTTP client server, smtp/pop (email) traffic?

---

### Post by J4m35 M. on 2009-01-30
Sorry, Yea.
If I recall correctly, we must be able to communicate through smtp/pop, and I wana say http client server. I'll figure out more on monday, sorry lol, guess I shoulda came in more prepared!

Kinda got thrown into this at the last minute so sorry for not being prepared.

---

### Post by binbash on 2009-01-30
If you are going to secure an ubuntu box,first secure the temp folder...Then kernel.Then permissions.

---

### Post by Hitman_Forhire on 2009-02-03
I'd be happy to help, I'm not very well known around here but I can certainly help. I have quite a bit of experience with FreeBSD as a server platform and will most likely be of most use in that department if you'd like. 

The greatest thing about FreeBSD is that the base system may be an older version but once you download the latest release of the ports and install them you can simply jump into the directory of an application you want to install/reinstall and 'make install clean' or 'make reinstall' [if the application is already installed] and you'll have the latest and greatest version of that application installed from source WITH some great FreeBSD patches applied, often for security and bugfixes. FreeBSD is very secure and often more-so than it's given credit for. 

Alternately inetd.conf will allow you to enable/disable services at boot. Once you've edited that [which can actually be done during installation] you can simply reboot and thats taken care of. 

For great added security on all of your boxes I would recommend disabling ssh logins and only allow logins by pre-authorized hashes as described [here]("http://www.google.com/url?sa=t&source=web&ct=res&cd=9&url=https%3A%2F%2Fwww.intriniumnetworks.com%2Fresources%2Fwhite-papers%2FImplementing%2520Key-based%2520SSH%2520Authentication.pdf&ei=8xWJSdzCD5K2sAPR6PCUDw&usg=AFQjCNHk8g_GiVEsHOqMvbT_HyDoNbdM2w&sig2=3c6QtAl_B6HlCa8fUwjxqA.").

What I do is just put the hash on a thumbdrive and encrypt it and carry it with me that way there's no way it can be compromised even if I lose it or leave it laying or in a box somewhere. If you do it, I wouldn't recommend using the same has for all three boxes.

If you have any questions or ideas hit me up I'm more than happy to help, and I hope I have given you something to work with.

---

### Post by Sorivenul on 2009-02-04
For FreeBSD, look for information on using the FreeBSD port of "pf" from OpenBSD. Also, check the FreeBSD Handbook section on [Security]("http://www.freebsd.org/doc/en/books/handbook/security.html"). You may also find [this Little White Dog article]("http://www.littlewhitedog.com/content-72.html") interesting. Good luck!

In general, [Bastille]("http://www.bastille-unix.org/") may also give you a jumpstart.

---

