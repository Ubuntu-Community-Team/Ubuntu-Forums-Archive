---
title: "Is there other secure solution then Tails - for example running Ubuntu read only?"
date: 2017-04-30
forum: Security
---

### Post by patrikmellq on 2017-04-30
Hello, i have a laptop with Ubuntu Mate.
I would like a simple and secure solution, same as Tails wish i been testing on read only usb stick.

Tails works great with Tor network, but it is slow and there is no way to run your own favorit programs with Tails.

So i was thinking why not install Ubuntu Mate on my usb stick, update the distro using apt-get and install Wine to run my PC programs and install my VPN service.
After that make my Ubuntu Mate read only.

Then i don't have to worry about root kits or any other intrusion.
No need to run Tripwire and make checks on regular basis.

Feel comfort using banking and other things.
Same as Tails but my own secure solution.

Now how would such a set up look like.

1. I download Ubuntu Mate and check that the SHA256 sum is correct (feel secure)
2. Update the Distro with apt-get network (feel secure)
3. Download Wine using apt-get network (feel secure)
4. Download VPN service package with check sum to validate package (feel secure)

During the install process i don't connect to internet with any other applications.
This has to be safe or do you have another suggestion.

Cheers

---

### Post by KenUBF on 2017-06-01
Hi. Are you looking just for a more secure computing environment or privacy, as in hiding your web browsing? If it's just securing your computer I would imagine a regular install would work fine. Then you can install Virtualbox with Tor installed (or your VPN solution) so you have a barrier between your actual computer and your activities. Another solution might be to do what this guide suggests: 
[https://anonguide.cyberguerrilla.org/](https://anonguide.cyberguerrilla.org/)

---

