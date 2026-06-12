---
title: "(Fingerprint reader) Could not download driver"
date: 2009-05-11
forum: System76 Support
---

### Post by Il turisto on 2009-05-11
Hello everybody,

I come from gentoo forum ([http://forums.gentoo.org/viewtopic-p-5718029.html#5718029](http://forums.gentoo.org/viewtopic-p-5718029.html#5718029)).
My problem is really simple in fact. I have a fingerprint reader in my laptop and I want to use it.
For this I have used the wschlich-testing overlay on gentoo who contains libfprint, ... packages.
But for the git version the git server is down and the 0.0.6 version does not work for me.
So I have try this tutorial : [http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation) wich is great but the wget links are also down.

Can you please tell me where I can download newer version of libfprint, pam_fprint, ... ?

---

### Post by thomasaaron on 2009-05-11
All of the packages we use to activate the fingerprint reader drivers are in our System76 Driver. If you crack the driver open, you will find the packages in the src directory.

[http://planet76.com/repositories](http://planet76.com/repositories)

---

### Post by Il turisto on 2009-05-11
Thanks for your quick reply.

I have donwloaded the last version of the .deb in your repository (the 2.3.4 version), extracted all from the .deb.
Inside I have found a folder named fprint with sources so I have followed the tutorial : [http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation)

But when I launch fprint_demo it says : no device found.
Can you tell me what I can verify to make it works?

---

### Post by thomasaaron on 2009-05-11
We do not test with or support Gentoo. And since I don't know my way around Gentoo, I'm not really sure how to help you.

We have a customer who has gotten our fingerprint readers to work in Gentoo. I'm emailing him and asking him to respond to this thread. 

Hopefully he will be able to help.

---

### Post by Il turisto on 2009-05-11
Thanks for emailing him.

Can you tell me the way you test it on ubuntu? Because ubuntu and gentoo work near the same way except on gentoo you compile everything.

---

### Post by thomasaaron on 2009-05-11
We install a program called Fprint Project.

This program allows you to register fingerprints and use them to authenticate administrative tasks.

---

### Post by efone on 2009-05-11
Hi Il turisto,

I replied on the Gentoo forum.

---

### Post by Il turisto on 2009-05-12
Thanks for help all.

I think my fingerprint reader isn't supported. Is it possible?

---

### Post by thomasaaron on 2009-05-12
Yes, that is possible.

Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

---

### Post by Il turisto on 2009-05-12
Thanks for the link. No solution for me in it but it was interesting.

Tomorrow I will boot an ubuntu cd to see if my fingerprint reader is detected.

---

### Post by thomasaaron on 2009-05-12
It won't be detected on a live CD. You have to download and run the System76 driver to install everything for the fingerprint reader. You can try to install and run the driver on a live CD. Not sure if it will work, though.

---

### Post by Il turisto on 2009-05-13
Ok bad news for me. My fingerprint reader doesn't work in ubuntu.

Do you need some information about it to implement the driver in your tools?

The vendor number is really near another product from broadcom wich work as seen in a wiki.

---

### Post by thomasaaron on 2009-05-13
We only support System76 machines. We do not have your particular computer model to test with. Sorry.

---

### Post by Il turisto on 2009-05-13
Ok I understand. I hope my fingerprint reader will be supported on the future.

Thanks for your help. I really appreciate this.

See you :-)

---

