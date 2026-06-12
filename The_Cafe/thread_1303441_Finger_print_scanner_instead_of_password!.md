---
title: "Finger print scanner instead of password!"
date: 2009-10-28
forum: The Cafe
---

### Post by jeyaganesh on 2009-10-28
We need to type our username and password in most of the websites we visit. I got an idea to using our finger prints instead of passwords. Hope it will be possible and ubiquitous in near future!:D

---

### Post by maflynn on 2009-10-28
Some laptops already have this.

btw, I remember a mythbuster episode where those crazy guys easily circumvented fingerprint scanners.

---

### Post by pwnst*r on 2009-10-28
> **jeyaganesh said:**
> We need to type our username and password in most of the websites we visit. I got an idea to using our finger prints instead of passwords. Hope it will be possible and ubiquitous in near future!:D

lol?  welcome to 2004ish.

---

### Post by 3rdalbum on 2009-10-28
> **maflynn said:**
> Some laptops already have this.

btw, I remember a mythbuster episode where those crazy guys easily circumvented fingerprint scanners.

Not quite - they easily circumvented one of the leading "industrial-strength" fingerprint scanner door locks, but I don't think they outsmarted their laptop's scanner. Or if they did, it was quite difficult.

---

### Post by jeyaganesh on 2009-10-28
I mean not only for login into the laptop. We should use finger print scanner to login to all the websites and for during software installations.

---

### Post by steev182 on 2009-10-28
Two stage authentication is much better than 1 stage.

Something you have and something you know (Fingerprint, iris or smartcard + password) is much more secure.

---

### Post by Pasdar on 2009-10-28
You can not trick a fingerprint scanner, unless the place where the verification happens is accessible to the person trying to trick it. Example of a non-trickable system: fingerprint scans your finger, sends this information to a server at X location, verification happens, signal is sent to a mechanism unaccessible to user (e.g. on the inside) to open the door.

However I doubt any system takes it that far...

---

### Post by coolbrook on 2009-10-28
The very keen invested in biometrics years ago.

As far as using it online goes... No thank you.

---

### Post by Pasdar on 2009-10-28
> **coolbrook said:**
> The very keen invested in biometrics years ago.

As far as using it online goes... No thank you.

I would be very wary of using fingerprint/iris scan for anything on the internet..... evil people could bring identity theft to a whole new level...

---

### Post by [h2o] on 2009-10-28
> **Pasdar said:**
> You can not trick a fingerprint scanner, unless the place where the verification happens is accessible to the person trying to trick it. Example of a non-trickable system: fingerprint scans your finger, sends this information to a server at X location, verification happens, signal is sent to a mechanism unaccessible to user (e.g. on the inside) to open the door.

However I doubt any system takes it that far...
If you fake a physical fingerprint (which is doable) why would "the place where verification happens" make a difference?
To the machine it is the correct finger.

---

### Post by Johnsie on 2009-10-28
How do you know if it's a real finger print scanner sending the finger print data to the server? It could be another device maskerading as a fingerprint scanner and sending false/recordered information ie. someone elses fingerprint data that is held on a hard disk.

Either way, I don't think this would work well with my prosthetic hand.

---

### Post by Pasdar on 2009-10-28
> **'[h2o] said:**
> If you fake a physical fingerprint (which is doable) why would "the place where verification happens" make a difference?
To the machine it is the correct finger.

What if the scanner checks whether its a finger or not to begin with.. e.g. warm and touches the sensor in a way a finger would (like a water drop hitting a flat surface). We don't have any materials that would imitate that. for example we can't make silicon take the shape of the fingerprint and then make a fingershaped/warmed up fake finger touch the scanner. Once that is there, you can combine the scanner with videofeed to add facial recognition, detetect stress/etc...

---

### Post by [h2o] on 2009-10-28
> **Pasdar said:**
> What if the scanner checks whether its a finger or not to begin with.. e.g. warm and touches the sensor in a way a finger would (like a water drop hitting a flat surface). We don't have any materials that would imitate that. for example we can't make silicon take the shape of the fingerprint and then make a fingershaped/warmed up fake finger touch the scanner. Once that is there, you can combine the scanner with videofeed to add facial recognition, detetect stress/etc...
And for the price of that you might as well just hire someone to stand at the door and make a full DNA analysis of everyone who wants to pass...

Are you seriously defending fingerprint scanners by suggesting adding multiple other completely unrelated detection methods? And it still does not explain your hypothesis that if the verification takes place somewhere else it is not foolable.

---

### Post by p_quarles on 2009-10-28
> **jeyaganesh said:**
> I mean not only for login into the laptop. We should use finger print scanner to login to all the websites and for during software installations.
So, instead of having a keyring of different passwords for different sites -- which shields you from disaster should one site you use be compromised -- you use one authentication technique that is based on an immutable (or nearly so) personal characteristic. 

This sounds like a Bad Idea. 

For remote logins that require secure authentication, those key-generating RSA fobs are a much better solution.

---

### Post by gnomeuser on 2009-10-28
Fedora already ships with a fingerprint reader pam module by default (meaning you can login using your fingerprint scanner and thus also unlock the keyring). It would surprise me if they weren't working towards using fingerprinting more when available.

---

### Post by Pasdar on 2009-10-28
> **'[h2o] said:**
> And for the price of that you might as well just hire someone to stand at the door and make a full DNA analysis of everyone who wants to pass...

Are you seriously defending fingerprint scanners by suggesting adding multiple other completely unrelated detection methods? And it still does not explain your hypothesis that if the verification takes place somewhere else it is not foolable.

Lol, the first two options should be coded into the scanner software, so its not seperate... just slightly different coding.

---

### Post by Johnsie on 2009-10-28
Here is the data being sent from my finger print scanner to the website:

01010101010101010


Here is the data being sent from a phishers fake fingerprint scanner to the website:

01010101010101010


Oh dear... someone has stolen my online identity and cloned it ;-)

---

### Post by [h2o] on 2009-10-28
> **Pasdar said:**
> Lol, the first two options should be coded into the scanner software, so its not seperate... just slightly different coding.

I just does not see any reason why those two "features" would be impossible to mimic.
Also, it would not be a software problem since it would require that the fingerprint scanner had sensors that could extract that information. To my knowledge fingerprint scanners today is just a camera.

---

### Post by xuCGC002 on 2009-10-28
Are most fingerprint scanners for logging in at BIOS? If not, that'd be incredibly easy to access someone's data while they think they're secure.

---

