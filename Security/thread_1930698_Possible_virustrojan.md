---
title: "Possible virus/trojan?"
date: 2012-02-24
forum: Security
---

### Post by Condor Cluster on 2012-02-24
My father said something strange happened the other day on his laptop. (I set up an old Acer Aspire 5101 laptop with Lucid for him)

He said he was trying to check his emails in Hotmail using Firefox, when he said it came up with 'server errors', and the text 'went really small'.

He then said the light on the top of the laptop came on (the webcam light)

Now, I'm not too concerned about the 'server errors' or 'tiny text', as these could have been problems with Hotmail down their end. But the webcam light concerned me, as this only comes on when the webcamera is active. I have heard of trojans secretly accessing web cams and the like :(

After a reboot, no sign of Hotmail errors, tiny text or webcam lights. Currently running a ClamAV recursive scan, all appears okay.

Any ideas, or am I just being a bit too paranoid?

:confused:

Thanks

---

### Post by 0011235813 on 2012-02-24
> **Condor Cluster said:**
> My father said something strange happened the other day on his laptop. (I set up an old Acer Aspire 5101 laptop with Lucid for him)

He said he was trying to check his emails in Hotmail using Firefox, when he said it came up with 'server errors', and the text 'went really small'.

He then said the light on the top of the laptop came on (the webcam light)

Now, I'm not too concerned about the 'server errors' or 'tiny text', as these could have been problems with Hotmail down their end. But the webcam light concerned me, as this only comes on when the webcamera is active. I have heard of trojans secretly accessing web cams and the like :(

After a reboot, no sign of Hotmail errors, tiny text or webcam lights. Currently running a ClamAV recursive scan, all appears okay.

Any ideas, or am I just being a bit too paranoid?

:confused:

Thanks

Sounds like you've taken paranoia to a whole new level! Seriously, there is **nothing** to suggest infection, a webcam can turn itself on for a lot of reasons. And anyway, if you've taken heart of the firewall wikis out here and only allow specific ports or applications through your firewall, an infection (spyware) couldn't do anything anyway.

PS: With that small text thing, are you sure the zoom wasn't turned too low? Oh and why Lucid? The latest release is Oneiric Ocelot (11.10).

---

### Post by ohadcn on 2012-02-24
did he opened live messenger?

---

### Post by enjoijesus94 on 2012-02-24
Hello 

Iv Never Had Any Problems With My Ubuntu Install.
No Offense But This Aint Windows :guitar:
My Webcam Turns On For Alot Of Reasons.

1. I Was In Yahoo Messenger.
2. Messing With Cheese Or Sometimes Even Config Files.
3. Plus He Would Have To Be Root To Execute A Trojan.

If Your Scared And Want To Install AntiVirus To Be Safe.

Install ClamAV
or rkhunter (But Has Alot Of False Positives.)

"sudo apt-get install clamav" 
"sudo apt-get install rkhunter"

without quotes.

Look Into Other Security To If Your Worried.

---

### Post by claracc on 2012-02-25
Originally posted by: 0011235813
> Oh and why Lucid? The latest release is Oneiric Ocelot (11.10). 

Perhaps because is the last long term support release?. I am too with lucid lynx and will not upgrade till 12.04 (other longer time support).

Lucid lynx is solid rocks, stable and responsive. I don't mind to have the latest version os software but bullet-proof software.

---

### Post by Dangertux on 2012-02-25
As already stated 10.04 is the current LTS and as such will be kept current on security updates and backports until the end of its life in April 2013.

As far as the behavior you witnessed in terms of the webcam turning on you are quite right to be suspicious. That is trojan like behavior, as well hotmail is rather famous for allowing cross site scripting. 

As well, it is not nearly as hard as most people seem to think to create a backdoor, trojan or remote access tool that will run in Linux. In fact it is no harder than Windows.

That being said, I think this is probably a hardware misconfiguratiom or built in functionality of fhe messenger app. Though a little vigilience never hurt anyone

---

### Post by Megaptera on 2012-02-25
> **claracc said:**
> Originally posted by: 0011235813


Perhaps because is the last long term support release?. I am too with lucid lynx and will not upgrade till 12.04 (other longer time support).

Lucid lynx is solid rocks, stable and responsive. I don't mind to have the latest version os software but bullet-proof software.

+1 to that :D

---

### Post by Condor Cluster on 2012-02-29
Why Lucid?

If it ain't broke, don't fix it!

---

### Post by daslinkard on 2012-03-03
My question (being new to Linux) is how easy is it to obtain a virus in Linux?  It is my understanding (or was my understanding) that it was nearly impossible to obtain an infection while utilizing Linux due to a lack of .exe files?

---

### Post by OpSecShellshock on 2012-03-03
> **daslinkard said:**
> My question (being new to Linux) is how easy is it to obtain a virus in Linux?  It is my understanding (or was my understanding) that it was nearly impossible to obtain an infection while utilizing Linux due to a lack of .exe files?

The lack of .exe files contributes to Windows malware not running on Linux, but that's about the extent of that. Cross-platform code (such as browser-based or plugin-based) still has a chance of running, but not many desktop Linux users have reported experience encountering those things in a functional way since most of the malware people are going to come across will be written for Windows systems. That convention sort of goes out the window lately if the distribution is Android, but that's largely not a desktop implementation.

Now, with all of that out of the way, it's important to understand that exploits and malware are both stops along a path, the goal of which is usually either to take control of a system, to obtain information on a system in an unauthorized way, or to compromise the integrity of data and communication on a system. Those things can all be done on a Linux desktop without malware and so it's important to account for and mitigate that risk. That's what we try to help people do in this forum.

---

### Post by Ms. Daisy on 2012-03-03
daslinkard, you may want to read the basic security wiki. It can help you account for & mitigate the risk OpSecShellshock spoke about.

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

