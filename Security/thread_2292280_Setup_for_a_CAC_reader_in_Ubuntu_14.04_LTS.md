---
title: "Setup for a CAC reader in Ubuntu 14.04 LTS"
date: 2015-08-26
forum: Security
---

### Post by Konrad_Stoudenmire on 2015-08-26
Let it be known that I'm a Windows guy that has been tasked with setting up a laptop with Ubuntu 14.04 LTS.  My first task that I'm attempting to accomplish is setting up a CAC reader so the laptop can be used to access CAC enabled DOD websites and eventually CAC login.


I'm attempting to follow the instructions listed here:
[https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

I have no issues until I get to the Firefox setup.  The CAC reader is detected.  The first issue is when I attempt to import the DOD certs.  I get a error that says the cert is invalid and will not be imported.  When I try to import a second time, it says there its already there.  So maybe the error messages are normal.  I move on to the next step to add the cackey module and this is where I get stuck.  When I try to add /usr/lib/libcackey.so I get the error "Unable to add module."  What can I try?  I've tried installing cackey using the command "sudo apt-get install cackey" and I've tried installing cackey by just double clicking the cackey file I download from forge.mil, "cackey_0.7.4-1_386.deb".  I didn't get any helpful results when I Googled "Ubuntu libcackey.so Unable to add module".  

Couple of things:

When I said the CAC reader is detected, the command pcsc_scan shows a reader and can tell when a card is inserted.  BUT, when I click the "Redetect Smart Card Reader" button from within Firefox, no reader is detected.
I also noticed there is a NSS Internal PKCS #11 Module installed already.  I can't unload that module.  I'm assuming this either came with Firefox or was installed when I installed cackey or the DOD Firefox .xpi file from Forge.mil. 

Please help!  I tried following a few other sets of instructions but I didn't make it this far with those.  This has been really frustrating as a Windows user who is used to plugging in a CAC reader and then having to only install the DOD root certs.

Thanks in advance for your patience with a new Ubuntu user!

Konrad

---

### Post by fj401971 on 2015-09-19
It seems that all you need to do is get cackey installed.  

I just did this yesterday.  I used the following source...[http://cackey.rkeene.org/download/0.7.4/]("http://cackey.rkeene.org/download/0.7.4/")  (A more appropriate source would be the source forge.mil site, but you need a cac card reader that already works...and I didn't have access to that a the time.

You need to download the appropriate link for your architecture (64 bit or 32 bit).  Once you download the appropriate version, either cackey....amd64.deb for 64 bit; or cackey...i386.deb for 32 bit.  Simply double-click the downloaded file and click the install package button when prompted.  Or type the following command changing the location or file name as appropriate:

```
sudo dpkg -i ~/Downloads/cackey_0.7.4-1_i386.deb
```

Now, if you're using the 64-bit version as I was, it did not install easily on my computer (a chromebook with ubuntu linux installed).  I had to create the folder "/usr/lib64" first.  This can be done a number of ways, but this is how I did it:

```
sudo mkdir /usr/lib64
```

Once this is done, the 64-bit version can be installed as described above. 

You said you had already installed the firefox extension DoD Confguration extension installed, if not install it: [http://www.forge.mil/Resources-Firefox.html]("http://www.forge.mil/Resources-Firefox.html")

Update your certificates again using the DoD Configuration extension and it will take care of installing the security module for you within Firefox...at least it did it for me. 

If nothing works right away, try restarting firefox.

You didn't mention if you installed the DoD certificates, but you're following the instructions as posted on the Ubuntu CAC page, so I'm assuming you did.

---

### Post by eoliver on 2016-07-27
[COLOR=#000000]Konrad,

So sorry this is a year late. But to all ye who enter know that I've over come the "Unable to add module" problem. I opened a terminal and ran "sudo firefox" then followed the normal steps to load the libcackey.so found in /usr/lib/ and this time it worked. Must be a privilege/permission issue with that .so file. fj401971's comment will get you all the way, but if you stumble at the loading part, try elevating firefox and trying again.

Good luck.[/COLOR]

---

### Post by QIII on 2016-07-27
Thank you for your input.

Rest in peace, dear thread.

Closed.

---

