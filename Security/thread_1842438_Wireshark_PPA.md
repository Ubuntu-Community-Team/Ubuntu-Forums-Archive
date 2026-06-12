---
title: "Wireshark PPA"
date: 2011-09-11
forum: Security
---

### Post by uRock on 2011-09-11
Does anyone here use this PPA for Wireshark? ```
sudo add-apt-repository [COLOR="Indigo"]ppa:n-muench/programs-ppa[/COLOR]
```

Just wondering if it has caused any problems for anyone.

---

### Post by Dangertux on 2011-09-11
Not sure exactly what you mean by problems? Do you mean is it getting backdoored frequently? The answer is no it's not ettercap :-P

Is it a little bit unstable from time to time (yes particularly in monitor mode) I prefer to use the stable release as opposed to the development. 

I hope that answered your question.

---

### Post by uRock on 2011-09-11
> **Dangertux said:**
> Not sure exactly what you mean by problems? Do you mean is it getting backdoored frequently? The answer is no it's not ettercap :-P

Is it a little bit unstable from time to time (yes particularly in monitor mode) I prefer to use the stable release as opposed to the development. 

I hope that answered your question.

I mostly meant with package errors, but security is good to know about as well.

Thanks.

---

### Post by Dangertux on 2011-09-11
> **uRock said:**
> I mostly meant with package errors, but security is good to know about as well.

Thanks.

Oh I haven't had issues with that.

---

### Post by uRock on 2011-09-11
> **Dangertux said:**
> Oh I haven't had issues with that.

Kool, thanx. :p

---

### Post by uRock on 2011-09-11
That was a waste of time. The PPA only offers the same as Canonical's for Lucid. :mad:

---

### Post by haqking on 2011-09-11
> **uRock said:**
> That was a waste of time. The PPA only offers the same as Canonical's for Lucid. :mad:


indeed ;-)

this is the list for each version [http://www.ubuntuupdates.org/pm/wireshark](http://www.ubuntuupdates.org/pm/wireshark)

---

### Post by uRock on 2011-09-11
> **haqking said:**
> indeed ;-)

this is the list for each version [http://www.ubuntuupdates.org/pm/wireshark](http://www.ubuntuupdates.org/pm/wireshark)

They removed the package. [http://www.ubuntuupdates.org/packages/show/256667](http://www.ubuntuupdates.org/packages/show/256667) 

Gonna have to break down and install from source to get 1.6.2.

Edit: Thanks for the link. It did get some of my other packages to a newer version.

---

### Post by haqking on 2011-09-11
> **uRock said:**
> They removed the package. [http://www.ubuntuupdates.org/packages/show/256667](http://www.ubuntuupdates.org/packages/show/256667) 

Gonna have to break down and install from source to get 1.6.2.

Edit: Thanks for the link. It did get some of my other packages to a newer version.

YUCK...lol ;-)

---

### Post by Dangertux on 2011-09-11
You can get 1.6.1 from the ppa which should be newer then 1.4.6 which is in the repos. But yes for 1.6.2 you will need to compile from source (you're not missing out on much anyways if you don't bother)

---

### Post by uRock on 2011-09-11
> **Dangertux said:**
> You can get 1.6.1 from the ppa which should be newer then 1.4.6 which is in the repos. But yes for 1.6.2 you will need to compile from source (you're not missing out on much anyways if you don't bother)

Neither of the PPAs I have tried will update Wireshark.

---

### Post by Dangertux on 2011-09-11
That's odd :-| 

I'm going to test it in a VM later to see if it will go up to 1.6.1 with the ppa. What version are you using, Natty?

---

### Post by haqking on 2011-09-11
> **Dangertux said:**
> That's odd :-| 

I'm going to test it in a VM later to see if it will go up to 1.6.1 with the ppa. What version are you using, Natty?

i am in 10.10 and ppa wont update mine either, i have 1.2.11

but im not that bothered cos i have later version elsewhere and dont use it much on this build.

---

### Post by uRock on 2011-09-11
> **Dangertux said:**
> That's odd :-| 

I'm going to test it in a VM later to see if it will go up to 1.6.1 with the ppa. What version are you using, Natty?

This machine has Lucid. I am debating installing Natty on it tomorrow.

---

### Post by josephmills on 2011-09-13
Hi there I am using oneric and I have 1.6.1 
[IMG]http://img51.imageshack.us/img51/273/wiresharkk.png[/IMG]
which is not 1.6.2 nor 1.6.0-rc2 but

---

### Post by Dangertux on 2011-09-13
It seems that 10.04 and 10.10 will only update to 1.4.2 if you want 1.6+ you will need to install from source or upgrade your distro. I got natty to 1.6.1 using the ppa mentioned.

---

### Post by josephmills on 2011-09-13
well that is good news but I sure hope that open vas gets bumped up to 4.0 but I don't see that happening any time soon  :)

---

### Post by Dangertux on 2011-09-13
I don't use OpenVAS, I prefer Nessus (then again I have access to the corporate feed so this might influence my choice).

But honestly, Nessus is much more modular and can be integrated with a lot more (ex: metasploit, nmap , nikto ,etc). Anyways enough on that topic, it's not related to the original post and is generally frowned upon here.

---

### Post by uRock on 2011-09-13
Installed Natty, then used the PPA to get to 1.6.1.

---

