---
title: "Ubuntu 8.10 + LTSP = client cannot see USB scanner on server"
date: 2009-01-21
forum: Server Platforms
---

### Post by srangelov on 2009-01-21
Hi, all!

I installed out of the box Ubuntu 8.10 Desktop, then following instructions here:
[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)
I installed LTSP.

It works fine except for the client cannot find the USB scanner on server. Though the scanner works on the server.

I found similar thread but for Ubuntu 8.04 with no solution there:
[http://ubuntuforums.org/showthread.php?t=939589&highlight=ltsp+scanner](http://ubuntuforums.org/showthread.php?t=939589&highlight=ltsp+scanner)

Can any one provide a suggestion?

Thank you in advance

Sotir Rangelov

---

### Post by srangelov on 2009-01-24
I noticed that if I run in terminal (on the client)
```
scanimage -L
```
it founds nothing. But if I run
```
sudo scanimage -L
```
the scanner is found. I also can use it but through 
```
sudo xsane
```

Does anyone have an idea what I need to do to allow user on the client to see the scanner?

Please, note that this same user is administrator and if I log in on the server I can see and use the scanner.

---

### Post by srangelov on 2009-02-07
I made some tests. Here are the results:

1. I installed Ubuntu 8.04 Desktop and ltsp-server-standalone. The scanner is accessible from the server, but not from the client.

2. I installed Ubuntu 7.10 Desktop and ltsp-server-standalone. The scanner is accessible from the server and from the client - as it should be!
Then I upgraded to Ubuntu 8.04 and the scanner is no more accessible.

Any information how to solve this is welcome. Thank you in advance!

---

### Post by mcbride_62 on 2009-02-10
Srangelov,

I had this problem with 8.04.  My fix was to change the permissions of others on the scanner to "rwx".  I saw that you had a similar idea on your cross post.  I've powered down my server and scanner several times and this fix is not temporary.  Not sure of any security implications of allowing all scan though...

Cheers.

---

### Post by srangelov on 2009-02-21
> **mcbride_62 said:**
> I had this problem with 8.04.  My fix was to change the permissions of others on the scanner to "rwx".

mcbride_62,

Can you please write here how exactly you change the permissions, so I can try your way.

What did you mean by "I had this problem with 8.04." Don't you have this problem with 8.10? 

Thank you.

---

### Post by srangelov on 2009-03-02
Here is a permanent solution:

Create a udev rule. My /etc/udev/rules.d/42-local.rules contain the following:

```
# This rule sets scanner's group to "scanner", allowing LTSP users to use the scanner on the server.

SUBSYSTEM=="usb", ATTR{idVendor}=="04a9", ATTR{idProduct}=="2220", SYMLINK+="%k", GROUP="scanner"

```
For more information, visit:
[Ubuntu FAQs > Customizing > LTSP and Thin Clients ]("http://my.oltrans.org/en/ubuntu-faqs/41-customizing/66-ltsp-thin-clients.html")

Sotir

---

