---
title: "Installing Lubuntu and Ubuntu in VirtualBox Conflict"
date: 2012-05-24
forum: Virtualisation
---

### Post by Bouvet on 2012-05-24
Hello Everyone.
I was looking at trying Lubuntu in VirtualBox but I am having issues installing it.
I currently have Ubuntu 11 already installed in VBox and when I try to add Lubuntu, the system says that I already have something like it. "Could not get the storage format"

Do I have to remove Ubuntu 11 from VBox to install Lubuntu?

---

### Post by Bouvet on 2012-05-24
I realized my mistake and how this question needs to be moved to VirtualBox section. Hope it can be moved.

---

### Post by matt_symes on 2012-05-24
Hi

> **Bouvet said:**
> Hello Everyone.
I was looking at trying Lubuntu in VirtualBox but I am having issues installing it.
I currently have Ubuntu 11 already installed in VBox and when I try to add Lubuntu, the system says that I already have something like it. "Could not get the storage format"

Do I have to remove Ubuntu 11 from VBox to install Lubuntu?

You do not need to remove Ubuntu to install Lubuntu in VBox. The problem is elsewhere i think.

Can you post the exact and entire error message you are getting Bouvet ?

Kind regards

---

### Post by Bouvet on 2012-05-24
Maybe I downloaded the wrong iso file?

I wasn't sure if I was getting the write one.

On my VB, I have Ubuntu 11, Mint 12 and openSUSE.

I don't know how to find the error message.

I feel really dumb that I cannot give you guys more detailed

information.

---

### Post by matt_symes on 2012-05-24
Hi

You downloaded it from here ?

[http://cdimage.ubuntu.com/lubuntu/releases/precise/release/](http://cdimage.ubuntu.com/lubuntu/releases/precise/release/)

I will install lubuntu and see if i get the same problem.

Kind regards

---

### Post by matt_symes on 2012-05-24
Hi

I have just downloaded it and installed it into a virtual machine so that is not a problem.

I suspect the problem is with the iso file you downloaded. 

Do you have a link to the file you downloaded ?

Have you checked its hash to make sure it's not corrupted ?

What settings are you using in VBox ?

Kind regards

---

### Post by Bouvet on 2012-05-24
> **matt_symes said:**
> Hi

I have just downloaded it and installed it into a virtual machine so that is not a problem.

I suspect the problem is with the iso file you downloaded. 

Do you have a link to the file you downloaded ?

Have you checked its hash to make sure it's not corrupted ?

What settings are you using in VBox ?

Kind regards

No Matt I don't recall what/where I find the download on line. 
I am going to try the link you provided. 
When I try to upload Lubuntu, here is the error that pops up from VBox. (See attached)
I only change the settings to allow 3D , 1024 Ram and 128.
That's all.

---

### Post by matt_symes on 2012-05-25
Hi

Re-download the ISO and check its MD5SUM value.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Even better to use a torrent to download it if you can find one.

Kind regards

---

### Post by Bouvet on 2012-05-25
> **matt_symes said:**
> Hi

Re-download the ISO and check its MD5SUM value.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Even better to use a torrent to download it if you can find one.

Kind regards

Thanks for your tops Matt. I think I am over my head on this one.

---

### Post by Bouvet on 2012-05-25
I did it Matt! All thanks to your direction!

I followed the link you provided, selected one of the sites listed

and installed it. It works fine. Now I get to tinker with it.

Huzzah! Huzzah! to Matt!  THANKS MATT =D>\\:D/

---

### Post by matt_symes on 2012-05-25
Hi

Checking the md5sum on the iso is pretty simple.

Open a terminal and type

md5sum <filename>

In my test i downloaded the 64 bit version of lubutu into my ~/Downloads directory

To check the md5sum, i opened a terminal and typed

```
md5sum ~/Downloads/lubuntu-12.04-desktop-amd64.iso
```

This was the output.

```
matthew@matthew-Aspire-7540 ~ % md5sum ~/Downloads/lubuntu-12.04-desktop-amd64.iso
**fca2034b89e8a0acd6536d41ccec061c**  /home/matthew/Downloads/lubuntu-12.04-desktop-amd64.iso
matthew@matthew-Aspire-7540 ~ %
```

I can then compare the number in bold above with the number in the MD5sum file on the server where i downloaded the file.

This is the file 

```
http://cdimage.ubuntu.com/lubuntu/releases/precise/release/MD5SUMS
```

Here is its content

```
729ccd0abea9e2da8fb790c3046e4983 *lubuntu-12.04-alternate-amd64+mac.iso
a277a7d3b8a6fc1dd98e65adb5262493 *lubuntu-12.04-alternate-amd64.iso
a1685837ad50845b6685086fc4743c83 *lubuntu-12.04-alternate-i386.iso
ed95aa4a5f82068d5e11d7dcea218865 *lubuntu-12.04-alternate-powerpc.iso
068fa129f2d95b2fb1fb4e8a2296651b *lubuntu-12.04-desktop-amd64+mac.iso
**fca2034b89e8a0acd6536d41ccec061c *lubuntu-12.04-desktop-amd64.iso**
0fc9564b8fde8ff56100c3d7814fa884 *lubuntu-12.04-desktop-i386.iso
72e66e30983d590ada111728fffdbd3f *lubuntu-12.04-desktop-powerpc.i
```

I can check to see the 2 numbers in bold are the same. They are so i know the download is not corrupted.

Kind regards

---

