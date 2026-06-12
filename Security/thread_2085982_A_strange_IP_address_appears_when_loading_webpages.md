---
title: "A strange IP address appears when loading webpages"
date: 2012-11-19
forum: Security
---

### Post by toontu on 2012-11-19
Hi guys,

I need some serious help. This afternoon after a restart for the update, I suddenly discover that at the end of each webpage loading, Chrome always reports "Waiting for 88.190.44.211...". The IP address points to a firm in Amsterdam, which sounds very dodgy. I don't recall changing any network settings recently. What can I do?

Any clue or hint is much appreciated. Is my machine hacked? Are all my online activities watched by some nasty people?

Many thanks,

toon

---

### Post by |{urse on 2012-11-19
Hi,

Maybe theres an unresolved entry in the dns resolver cache.
Close any open instances of chrome, open a terminal and run this command

```
sudo /etc/init.d/dns-clean
```

Then open chrome and see if the issue persists.

---

### Post by toontu on 2012-11-19
Thanks, Kurse. I will try tomorrow morning. Hope that's the solution. :-)

---

### Post by MadsRC on 2012-11-20
That IP isn't dutch, it french.

host: 88-190-44-211.rev.dedibox.fr

```
inetnum:        88.190.44.0 - 88.190.44.255
netname:        FR-DEDIBOX
descr:          Dedibox SAS
descr:          Hosting Customers
descr:          Paris, France
remarks:        trouble: Information: http://www.dedibox.fr/
remarks:        trouble: Spam/Abuse requests: http://www.dedibox.fr/abuse/
remarks:        trouble: Spam/Abuse requests: mailto:abuse@support.dedibox.fr
country:        FR
admin-c:        ACP23-RIPE
tech-c:         TCP8-RIPE
status:         ASSIGNED PA
mnt-by:         PROXAD-MNT
source:         RIPE #Filtered

                                            


role:           Administrative Contact for ProXad
address:        Free SAS / ProXad
address:        8, rue de la Ville L'Eveque
address:        75008 Paris
phone:          +33 1 73 50 20 00
fax-no:         +33 1 73 92 25 69
remarks:        trouble:      Information: http://www.proxad.net/
remarks:        trouble:      Spam/Abuse requests: mailto:abuse@proxad.net
admin-c:        APfP1-RIPE
tech-c:         TPfP1-RIPE
nic-hdl:        ACP23-RIPE
mnt-by:         PROXAD-MNT
source:         RIPE #Filtered
abuse-mailbox:  abuse@proxad.net

                                            


role:           Technical Contact for ProXad
address:        Free SAS / ProXad
address:        8, rue de la Ville L'Eveque
address:        75008 Paris
phone:          +33 1 73 50 20 00
fax-no:         +33 1 73 92 25 69
remarks:        trouble:      Information: http://www.proxad.net/
remarks:        trouble:      Spam/Abuse requests: mailto:abuse@proxad.net
admin-c:        APfP1-RIPE
tech-c:         TPfP1-RIPE
nic-hdl:        TCP8-RIPE
mnt-by:         PROXAD-MNT
source:         RIPE #Filtered
abuse-mailbox:  abuse@proxad.net

                                            


route:          88.160.0.0/11
descr:          ProXad network / Free SAS
descr:          Paris, France
origin:         AS12322
mnt-by:         PROXAD-MNT
source:         RIPE #Filtered
```

---

### Post by vasa1 on 2012-11-20
Do you see it when you run Chrome without any extensions enabled?

---

### Post by toontu on 2012-11-20
> **vasa1 said:**
> Do you see it when you run Chrome without any extensions enabled?

Thanks, vasa1. That solves the problem. I installed ninja fruit from Google Play last week....

---

### Post by toontu on 2012-11-20
> **MadsRC said:**
> That IP isn't dutch, it french.

host: 88-190-44-211.rev.dedibox.fr

```
inetnum:        88.190.44.0 - 88.190.44.255
netname:        FR-DEDIBOX
descr:          Dedibox SAS
descr:          Hosting Customers
descr:          Paris, France
remarks:        trouble: Information: http://www.dedibox.fr/
remarks:        trouble: Spam/Abuse requests: http://www.dedibox.fr/abuse/
remarks:        trouble: Spam/Abuse requests: mailto:abuse@support.dedibox.fr
country:        FR
admin-c:        ACP23-RIPE
tech-c:         TCP8-RIPE
status:         ASSIGNED PA
mnt-by:         PROXAD-MNT
source:         RIPE #Filtered

                                            


role:           Administrative Contact for ProXad
address:        Free SAS / ProXad
address:        8, rue de la Ville L'Eveque
address:        75008 Paris
phone:          +33 1 73 50 20 00
fax-no:         +33 1 73 92 25 69
remarks:        trouble:      Information: http://www.proxad.net/
remarks:        trouble:      Spam/Abuse requests: mailto:abuse@proxad.net
admin-c:        APfP1-RIPE
tech-c:         TPfP1-RIPE
nic-hdl:        ACP23-RIPE
mnt-by:         PROXAD-MNT
source:         RIPE #Filtered
abuse-mailbox:  abuse@proxad.net

                                            


role:           Technical Contact for ProXad
address:        Free SAS / ProXad
address:        8, rue de la Ville L'Eveque
address:        75008 Paris
phone:          +33 1 73 50 20 00
fax-no:         +33 1 73 92 25 69
remarks:        trouble:      Information: http://www.proxad.net/
remarks:        trouble:      Spam/Abuse requests: mailto:abuse@proxad.net
admin-c:        APfP1-RIPE
tech-c:         TPfP1-RIPE
nic-hdl:        TCP8-RIPE
mnt-by:         PROXAD-MNT
source:         RIPE #Filtered
abuse-mailbox:  abuse@proxad.net

                                            


route:          88.160.0.0/11
descr:          ProXad network / Free SAS
descr:          Paris, France
origin:         AS12322
mnt-by:         PROXAD-MNT
source:         RIPE #Filtered
```

I think you were right. :-) At the time of writing my original post, our system admin told me it was in Amsterdam so I didn't check it myself. Well, it doesn't really matter. Cheers.

---

### Post by MadsRC on 2012-11-20
Your welcome.

But, from what I posted you can deduct that IP belongs to either an ISP or Server provider.

Which means
A: The IP belongs to some custommer, private or commercial
B: The IP is used by some software to contact a server at dedibox.fr
C: The software is either legitimate (Browser extension?) or malign (Rootkit, or some browser exploit).

Renting a Virtual Private Server in an anonymous name with untraceable payments isn't extremely difficult, so doing that and attacking from said VPS is a possibility.

---

### Post by toontu on 2012-11-20
> **MadsRC said:**
> Renting a Virtual Private Server in an anonymous name with untraceable payments isn't extremely difficult, so doing that and attacking from said VPS is a possibility.

Agreed. The Chrome extension I installed probably isn't malicious and just tried to update its embedded ads. This problem though could be a crack in Chrome's supposedly solid defence.

---

### Post by Ms. Daisy on 2012-11-20
The best course of action would be to research the app, the developer's website, and the address you noted. 

[virustotal.com ]("https://www.virustotal.com/url/50b682ff0d8b9fac0bc6abfcc0e17c0578641f38293fd01ee7051d51af2eec9b/analysis/1353465833/")found no suspect files on dedibox.fr, nor did [sucuri sitecheck]("http://sitecheck.sucuri.net/results/www.dedibox.fr"). 

I found the [developer's website]("http://www.halfbrick.com/2012/10/fruit-ninja-jetpack-joyride-windows-8/#more-3103"). [Virustotal.com ]("https://www.virustotal.com/url/5a2a185b437548196a7e1c091bdb8ead20f8ba9c2c7ac4d44e0ad27cedf1a410/analysis/1353466151/")didn't find anything suspicious on that website either.
If you want to go further you can upload the file that you got when you installed the app to virustotal & see if it contains anything suspicious.

I would download the file to test it for you but it costs $4.99 and I'm way to cheap for that.  But you can also look at the readme or eula that came with the installation of the app to see what it's doing. I guess it could be adware & constantly calling home with updates on your browser activity. Or it could just be unsuccessfully calling home for updates.

If you have wireshark you could capture the traffic to that IP. If you post the output here I can help you read it.

But I'm leaning towards this being a boring old app that is not malicious.

---

### Post by toontu on 2012-11-21
Thanks, Ms. D. I will dig a bit deeper when having some spare time to kill. :-)

---

