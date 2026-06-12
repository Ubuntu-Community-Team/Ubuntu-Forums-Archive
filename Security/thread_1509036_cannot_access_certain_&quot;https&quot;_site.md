---
title: "cannot access certain &quot;https&quot; site"
date: 2010-06-13
forum: Security
---

### Post by mm0204 on 2010-06-13
This is a random thing that google and I haven't found anywhere else... i'm not sure that the "security discussions" forum is the right place for this, so if not, let me know and i'll repost in the correct forum...

so, i am running 64-bit lucid on an amd 64-bit laptop, i am fully updated, i am using chrome and "a web browser" which appears to be an unbranded/ubuntu branded version of firefox...

upon opening either browser and entering the address of my wife's work email ([https://secure.somecompanyname.org](https://secure.somecompanyname.org)) the page takes FOREVER to load (i timed it once and it took 4.5 minutes); when it finally loads the login page and she enters the credential info, it takes another 4-5 minutes to bring up the next page...

added wierdness: if I access from windows vista on the same laptop (dual boot) it works right away, however, if I try it from XP in VirtualBox under lucid... loooooooong wait times again...

new added wierdness: if i go to proxify.com and then enter the website, it goes right to it... don't know whether or not we can login via that method because i don't have the credentials... we'll test it and report back

so... any thoughts?  let me know if there are any log files or command outputs that would help the diagnoses...

Cheers,
Matt
Lathrop, CA  USA

---

### Post by an0dos on 2010-06-13
> **mm0204 said:**
> This is a random thing that google and I haven't found anywhere else... i'm not sure that the "security discussions" forum is the right place for this, so if not, let me know and i'll repost in the correct forum...

so, i am running 64-bit lucid on an amd 64-bit laptop, i am fully updated, i am using chrome and "a web browser" which appears to be an unbranded/ubuntu branded version of firefox...

upon opening either browser and entering the address of my wife's work email ([https://secure.somecompanyname.org](https://secure.somecompanyname.org)) the page takes FOREVER to load (i timed it once and it took 4.5 minutes); when it finally loads the login page and she enters the credential info, it takes another 4-5 minutes to bring up the next page...

added wierdness: if I access from windows vista on the same laptop (dual boot) it works right away, however, if I try it from XP in VirtualBox under lucid... loooooooong wait times again...

new added wierdness: if i go to proxify.com and then enter the website, it goes right to it... don't know whether or not we can login via that method because i don't have the credentials... we'll test it and report back

so... any thoughts?  let me know if there are any log files or command outputs that would help the diagnoses...

Cheers,
Matt
Lathrop, CA  USA

Go to "System --> Preferences --> Network Connections". 
Select your network interface. In my case it is under the "Wired" tab and "Auto eth0".
Click on the "IPv4 Settings" tab and change the Method to "Automatic (DHCP) addresses only"
Then in DNS Servers type in: "208.67.222.222, 208.67.220.220"
Then click on "apply"
Restart the computer

This configures your DNS to use opendns. Your problem is probably not DNS related, but it is worth trying.

Have you verified that this works with all sites using https, or is it limited to just the one?
You can go to gmail.com to verify. It should load fairly quickly.

If it is specifically related to the site (gmail loads normally). You might also want to try installing the "user agent switcher" addon for firefox. You can use it to make your computer appear to the website as a Windows computer running Internet Explorer to see if that helps.

---

