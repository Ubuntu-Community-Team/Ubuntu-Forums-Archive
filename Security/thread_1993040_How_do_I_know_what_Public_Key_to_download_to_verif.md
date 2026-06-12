---
title: "How do I know what Public Key to download to verify Ubuntu cdimage?"
date: 2012-06-01
forum: Security
---

### Post by nrundy on 2012-06-01
Additionally, how do I verify that the public key I download is in fact the public that that Ubuntu intends for me to verify the signature with?

Is there an HTTPS webpage that tells what the fingerprint of the public key is?

---

### Post by oldos2er on 2012-06-01
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by nrundy on 2012-06-03
the Fingerprint for the ubuntu public key is not listed on that page.

---

### Post by Cavsfan on 2012-06-03
> **nrundy said:**
> the Fingerprint for the ubuntu public key is not listed on that page.
There should not be a key for an image, just an md5sum

Enter this in terminal:
```
md5sum /home/yourhome/Downloads/ubuntu-12.04-desktop-amd64.iso
```Then compare the output to the one on the page **oldos2er** provided.

---

### Post by nrundy on 2012-06-03
look here: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

there is a file 
[SHA256SUMS.gpg]("http://releases.ubuntu.com/precise/SHA256SUMS.gpg")    

in order to verify this file, one needs to download the public key and gpg --verify it. How do I know I"m downloading a legitimate key? It's helpful to know the fingerprint of the key.

---

### Post by Cavsfan on 2012-06-03
> **nrundy said:**
> look here: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

there is a file 
[SHA256SUMS.gpg]("http://releases.ubuntu.com/precise/SHA256SUMS.gpg")    

in order to verify this file, one needs to download the public key and gpg --verify it. How do I know I"m downloading a legitimate key? It's helpful to know the fingerprint of the key.

You can be sure if it comes from [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) that it is legit.
There is also MD5SUMS and a gpg key for that also on that link.

---

### Post by nrundy on 2012-06-03
> **Cavsfan said:**
> You can be sure if it comes from [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) that it is legit.
There is also MD5SUMS and a gpg key for that also on that link.

Where is the gpg key on that link?

---

### Post by Cavsfan on 2012-06-03
> **Cavsfan said:**
> You can be sure if it comes from [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) that it is legit.
There is also MD5SUMS and a gpg key for that also on that link.

> **nrundy said:**
> Where is the gpg key on that link?

If you scroll down a ways, it is the 4th link down not including parent directory.

---

### Post by nrundy on 2012-06-03
cavs, that is not a key. that is a signature file. You need to download the key to verify that signature. This is what I'm asking. Where can I verify the Fingerprint of the key I have to download?

---

### Post by Cavsfan on 2012-06-03
However, you do not need a key or any of that.

Enter this in terminal and it will generate the md5sum:
```
md5sum /home/[COLOR=Red]yourhome[/COLOR]/Downloads/ubuntu-12.04-desktop-amd64.iso
```Just make sure you are in, or point to the same dirctory as the iso.

Change the location to suit your needs.

This is exactly what I did.

---

### Post by Cavsfan on 2012-06-03
[[color=blue]_https://help.ubuntu.com/community/HowToMD5SUM_[/COLOR]](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by nrundy on 2012-06-06
i know how to md5 sum. this is not my question.

Anyone that can address my question?

---

### Post by spynappels on 2012-06-07
You could just go to [http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/) and search for it on there....

There will be a fingerprint on there, and it is the official Ubuntu keyserver, so you can't get more definitive than that.

---

