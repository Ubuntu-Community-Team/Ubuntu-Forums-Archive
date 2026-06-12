---
title: "Citrix Receiver on Ubuntu 16.04 LTS"
date: 2018-08-02
forum: Virtualisation
---

### Post by gs7438 on 2018-08-02
I'm wondering if someone could help me get Citrix Receiver working on Ubuntu 16.04 LTS. I've tried a number of things to troubleshoot so far, and none have them have worked. Let me attempt to describe the behavior I've seen so far. 

First, I use the instructions posted [here ]("https://help.ubuntu.com/community/CitrixICAClientHowTo") to download and install Citrix as default. I have also tried re-linking my cacerts with /etc/ssl/certs instead of mozilla's certificates. I'm attempting to run citrix apps from (what I guess is called) a webstore. 

If I attempt to use Citrix Receiver 13.10 or 13.9, I get an error like```
Cannot connect to 0.0.0.2 - Published app name
```I've attempted troubleshooting this by looking [here]("https://discussions.citrix.com/topic/323985-cannot-connect-to-0002-published-app-name-most-distros/") and [here]("https://askubuntu.com/questions/901448/citrix-receiver-error-1000119"). I've tried uninstalling these and reinstalling Citrix 13.8 and 13.4. When using these version, I get an error like```
SSL error: Contact your help desk with the following information: A network error occurred (SSL error 4)
```
I've also attempted rehashing the certificates using Citrix's tool in /opt/Citrix/ICAClient/util/ctx_rehash. This does not solve either problem. I've also attempted to install just the web-receiver only. I've also attempted to install Citrix as a Google Chrome Extension. 

I've attempted updating my ca-certificates using update-ca-certificate on the command line. 

None of this appears to change the behavior of the receivers. Any guidance on what to do moving forward would be appreciated.:D

Thank you.

---

