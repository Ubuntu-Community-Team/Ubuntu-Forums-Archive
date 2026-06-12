---
title: "STORE NOT WORKING error 35: gnutls_handshake()"
date: 2011-03-08
forum: Ubuntu Cloud and Juju
---

### Post by vgokulakrishnan on 2011-03-08
Hello.. I'm a newbie in UEC Cloud..
I ve a serious problem with UEC Store.
From the start  it's showin Error, "Error 35: gnutls_handshake() failed: A TLS packet  with unexpected length  was received."
I ve tried everything, please consider this brief  story of my UEC
"I installed UEC Cloud by CDInstall from  help.ubuntu.com/community/uec/cdinstall .. And fixed some issues by  commands including euca-desc-availablty-zones.
I dint do any other settings or changes. All working fine except [B]UEC   Store.
[/B][ CC communicating with NC, all components are Running, Tried Image Store Purging too.. Nothing made store good.. always showin error 35..]

 Tried all changes, but succeeded in nowhere making this STORE workable.
This is ma short story of My UEC.."


Awaiting for ur very valuable replies guys..
Thanx in advance

---

### Post by kim0 on 2011-03-08
Are you trying to download images from the image store ?

If so, I think UEC is trying to connect over https and getting some random gibbersh data back. Do you have some proxy or restricted Internet access somehow? If so that might be blocking UEC from downloading what it needs

---

### Post by vgokulakrishnan on 2011-03-08
hi, my servers too, are under proxy network, and all clients too under
firewall.. can you help me out how to setup a store under proxy..
Isn't there a way for that..
I tried purging Image Store didnt help :(
If we upload a image will it work, showin atleast my image..
Can we use any other software for uploading as an instance, without uploading an os..
Thanx again..

---

### Post by kim0 on 2011-03-09
You might wanna publish an image "manually" without using the web store
Check out these instructions
[https://help.ubuntu.com/community/UEC/BundlingImages](https://help.ubuntu.com/community/UEC/BundlingImages)

Or just ask your IT people to give an exception to you and allow you unrestricted internet access

---

### Post by vgokulakrishnan on 2011-03-09
This manual uploadin/unrestricted internet, should be done in CC server isn't it..
Let me say my organization infra, All machines are under firewall/proxy, and only the Org-Server is out of it..
I asked for Unrestricted internet in my machine..
I'm gona try after gettin it, whether it's workin properly in Org-Server.
:)
Thanks for your help, I may need more..
I ll let you know if its working good.. :)

---

### Post by vgokulakrishnan on 2011-03-10
"uec-publish-tarball" not working..
It replies "Unable to run euca-describe-images. Is euca2ools environment set up?"
But I ve installed euca2ools and i think its working..
What may have gone wrong..
Waiting for your response

---

### Post by kim0 on 2011-03-11
Hi, check step-5 on [https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)
to configure your eucarc file with credentials

---

### Post by vgokulakrishnan on 2011-03-14
my port no for WebUI is 8443
but its set 8773 in eucarc file u said..
U know actually, I did mentioned step5 before itself..

---

### Post by kim0 on 2011-03-15
Just confirming that yes, 8773 is the port used by euca-xxx commands. The "human" web interface is on port 8443 however

---

