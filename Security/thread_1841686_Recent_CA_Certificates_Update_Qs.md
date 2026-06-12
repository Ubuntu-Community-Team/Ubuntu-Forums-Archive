---
title: "Recent CA Certificates Update Qs?"
date: 2011-09-09
forum: Security
---

### Post by cryptotheslow on 2011-09-09
Hi :)

Posting in Security as it's regards the recent Diginotar blacklisting update....  so vaguely Sec related and this forum gets spammed less ;)

I'm up to speed on the recent Diginotar issues so wasn't surprised to see Firefox updates roll through a couple of days back.

Then I got a "CA Certificates" update today (on v10.04) through the usual Update Manger popup.

Couple of Qs..

1. Can anyone point me to some reading about where else these CA Certs are used other than in a browser scenario please? I was just puzzled to see it come down as a separate apparantly generic Canonical "CA Certificates" update outside of the browser context. I'm not aware that I use them for any other app, but is there an OS store of CA's as well as the browser specific stuff? It makes me think I don't know what I thought I did...  so yeh...  back to school for me!

2. Watching the update apply there was one line that whizzed past...  something like  "CA exists... ignoring...  something.br.sec"  - it went by far too fast to read but as this is a blacklisting of a CA that "ignoring" tweaked me. Is it possible to review those messages in a log file somewhere? 


As a complete aside, on my work WinXP laptop here I just pulled up the CA list shipped with Firefox - :confused::confused::confused:  seriously that has to be a joke - there's a gazillion CAs in there trusted by default....  how so? Is it really down to which CAs grease which palms of which browser pedallers enough to get included in the "green bar" list? Seems like a scheme for distrust rather than trust if that's how it really works.... gotta be a better way surely.

Anyway - ignore that last bit, I was just thinkatypin :) Answers to 1 n 2 on a postcard much appreciated.

Thanks as always :)

---

### Post by Dave_L on 2011-09-10
Regarding the log files, check /var/log/apt/. The file history.log contains the primary actions (packages installed, upgraded, etc.) and the file term.log contains the detailed messages.

The retention policy for those logs is in /etc/logrotate.d/apt.

I'm curious about the certificate changes too. I saw those same warning messages, but don't know whether they're important.

Here are the logs for this update:

history.log
> Start-Date: 2011-09-09  04:36:26
Upgrade: ca-certificates (20090814, 20090814ubuntu0.10.04.1), libnss3-1d (3.12.9+ckbi-1.82-0ubuntu0.10.04.1, 3.12.9+ckbi-1.82-0ubuntu0.10.04.3)
End-Date: 2011-09-09  04:37:18

term.log
> Log started: 2011-09-09  04:36:26
(Reading database ... 191539 files and directories currently installed.)
Preparing to replace ca-certificates 20090814 (using .../ca-certificates_20090814ubuntu0.10.04.1_all.deb) ...
Unpacking replacement ca-certificates ...
Preparing to replace libnss3-1d 3.12.9+ckbi-1.82-0ubuntu0.10.04.1 (using .../libnss3-1d_3.12.9+ckbi-1.82-0ubuntu0.10.04.3_i386.deb) ...
Unpacking replacement libnss3-1d ...
Processing triggers for man-db ...
Setting up ca-certificates (20090814ubuntu0.10.04.1) ...
Updating certificates in /etc/ssl/certs... WARNING: Skipping duplicate certificate Go_Daddy_Class_2_CA.pem
WARNING: Skipping duplicate certificate ca-certificates.crt
0 added, 1 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
  does not exist: /etc/ssl/certs/DigiNotar_Root_CA.pem
done.
done.

Setting up libnss3-1d (3.12.9+ckbi-1.82-0ubuntu0.10.04.3) ...

Log ended: 2011-09-09  04:37:18

---

### Post by FuturePilot on 2011-09-10
> **cryptotheslow said:**
> Hi :)

1. Can anyone point me to some reading about where else these CA Certs are used other than in a browser scenario please? I was just puzzled to see it come down as a separate apparantly generic Canonical "CA Certificates" update outside of the browser context. I'm not aware that I use them for any other app, but is there an OS store of CA's as well as the browser specific stuff? It makes me think I don't know what I thought I did...  so yeh...  back to school for me!

There are other programs that use SSL connections other than browsers. That is where these certificates come in.


> Is it really down to which CAs grease which palms of which browser pedallers enough to get included in the "green bar" list? Seems like a scheme for distrust rather than trust if that's how it really works.... gotta be a better way surely.

That is the issue that has been brought up recently with all the bogus certs. It's too easy for bogus certs to be signed.

---

### Post by uRock on 2011-09-10
> **FuturePilot said:**
> That is the issue that has been brought up recently with all the bogus certs. It's too easy for bogus certs to be signed.

Especially when you have some companies only denying blacklists instead of reading off of white lists. I read a feed explaining how that was being done by one vendor up to this point.(When I find the feed again, I will link it.)

Here is a great read for those who want to see how the CAs work [http://isc.sans.edu/diary.html?storyid=11533&rss](http://isc.sans.edu/diary.html?storyid=11533&rss)

---

### Post by cryptotheslow on 2011-09-10
Thanks to everyone for the input.

@Dave_L: From the little reading up I've had time to do I think I've understood it that the trusted CAs are listed in /etc/ca-certificates.conf and when a change is made the "update-ca-certificates" command is invoked which runs around updating keystores in /etc/ssl/certs and /etc/ssl/certs/java/cacerts - probably other places too. So a "duplicate" message would locigally mean that a CA is listed more than once in /etc/ca-certificates.conf. I've yet to know what is being put in those places - maybe the so called CA root certificates? If it is those, wth they are actually used for.... I don't know. Maybe used to secure the communication verifying the verification of an individual site's cert with the CA?

@uRock: Thanks for the link - interesting reading.

So essentially it is just a paid for web of trust, with some strong-arm tactics employed by the CA and browser producer coalition - i.e. "we'll throw lots of warning boxes at users of our browser visiting sites signed by your certs unless you pay us to be recognised". So for the CA's to get customers they have to pay the browser peeps, in turn to reoup those costs (and make a nice profit) the CA peeps strong-arm site owners wanting to secure communications with the same message.

Given the ridiculous simplicity of setting up a registered business in even "non-dodgy" countries, even the most rigorous CA "EV" checks are pretty meaningless.

What a complete farce.

As an experiment, I removed all the entries from Firefox Certificate Manager "Authorities" and "Servers" tabs. Then added one cert back specifically for a VPS I manage. Going to be interesting when I need to do some banking :D

I guess this just dissolves into a "what is trust anyway" discussion from here. Personally I don't "trust" any business or org based on a little padlock symbol in a browser - but it's nice to know that communication is at least encrypted. But then when the CA goes bad...  great - encrypted traffic to persons unknown who can happily unencrypt it.

Ugh, if I think about this too much more I'll be donning a tinfoil hat and only hand delivering written cheques to companies I wish to deal with. Well, I might if my bank still issued cheque-books :D

---

### Post by BkkBonanza on 2011-09-10
> **cryptotheslow said:**
> 
Ugh, if I think about this too much more I'll be donning a tinfoil hat and only hand delivering written cheques to companies I wish to deal with. Well, I might if my bank still issued cheque-books :D

It's easy to get too paranoid about this. I've installed and used the FF add-on "Certificate Patrol" for quite a while now as it will give you more pop ups about site certificates changing in the background. It's quite astounding actually how often sites change their certs nowadays. Usually they're fine but every now and then I see one I don't quite trust. If I see the CA change for some site then I'm pretty wary of it. Like, if Paypal has always been Verisign and one day CP pops up and says I'm connecting to Paypal using a HongKongPost cert then I'd back out right away.

It's always useful to have an ssh server somewhere you can proxy thru and check a site from another location. To MITM your SSL connection they need both a fake cert and some way to intercept your traffic. eg. For the Iranian govt this isn't too hard, and if you don't trust your ISP to secure their premises then it may not be so hard there either. And it's not hard to do on wifi/web cafe links either, nor any LAN that isn't well secured. 

I created my own CA so that I can issue my own certs for connections I need just for myself. (TinyCA package in Ubuntu repos is worth exploring) This is actually easy to do and safer than relying on third party CAs - though not at all useful for "public" sites, obviously.

---

### Post by cryptotheslow on 2011-09-12
Thanks BkkBonanza - sounds like an useful plugin.

However, I think I am going to run with my no CAs setup. I can count on the digits on my two hands the number of servers I actually need to use SSL for. By removing all CAs I have to manually add exceptions to add a cert to Firefox or Thunderbird for a server - if it changes then Firefox or Thunderbird has an apoplectic fit and throws warnings at me.

I trust myself to be able to verify those changes far more than having a gazillion CAs trusted by default by the applications.

Just tested putty that I use for my VPS stuff by renewing the cert on a VPS and it too spits up a warning... all good :)

One thought - I need to read up on how the Ubuntu repos are secured...  updates may break if I completely dump CAs from the OS entirely  :confused:

Sure it is a little less convenient this way, but puts the control back with me.... I think!

Please do shout at me if I've made a fundamental foobar in my thought process :D

---

### Post by BkkBonanza on 2011-09-12
AFAIK the repos use an SSL cert issued by Canonical. SSL use outside Firefox seems to be controlled by CAs stored in the /etc/ssl/certs directory. When I use curl it seems to pick them up there and I think other programs do as well. There's lots in there too but maybe not as many as FF. Some just point to /usr/share/ca-certiticates/mozilla anyway.

Also I believe the repos use gpg key sigs to verify data as well but I'm not sure of the exact process.

I know the Firefox addons.mozilla.com cert was one of the recently faked certs but even still you would need a net intercept to force using that cert.

---

### Post by FrancisBacon on 2011-09-15
I don't mean to hijack a thread, so if you want me to start a different one, please let me know.

After the ca-certificates updates my /etc/ssl/certs/ was different from machine to machine (they are all running Ubuntu 10.04 64bit).

On some /etc/ssl/certs/219d9499.0 was a link to UbuntuOne-Go_Daddy_Class_2_CA.pem

On some  /etc/ssl/certs/219d9499.0 was a link to Go_Daddy_Class_2_CA.pem which itself is a link to /usr/share/ca-certificates/mozilla/Go_Daddy_Class_2_CA.crt

On some:
/etc/ssl/certs/58a44af1.0 -> cert_igca_rsa.pem
but others:
/etc/ssl/certs/58a44af1.0 -> cert_igca_dsa.pem

There are others, but it's a short list of differences.

Do these differences matter? Can I unify these by copying one directory from one machine to another without ill effects? 

Thanks.

---

### Post by BkkBonanza on 2011-09-15
Make sure that both systems are fully updated with apt-get update and apt-get upgrade. This should make them both have the same files as there were certificate updates a while back. If you still have differences then that's pretty strange but I don;t know if it means something is actually wrong. I think you can probably replace one from the other but which one is correct?

---

