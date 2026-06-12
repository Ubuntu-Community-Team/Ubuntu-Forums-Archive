---
title: "p4p1 instead of eth0"
date: 2012-10-30
forum: Server Platforms
---

### Post by archieburden9 on 2012-10-30
hey everyone, i have installed a ubuntu server to my laptop (not a virtual machine)

it is for hosting a website just for fun (i know of security risks etc, just give me an answer instead of a load of off topic replies please)

my network card is p4p1 but it needs to be eth0, how do i change it please?

---

### Post by dannyboy79 on 2012-10-30
what does this return when entered within a terminal
```
ifconfig
```

---

### Post by archieburden9 on 2012-10-30
> **dannyboy79 said:**
> what does this return when entered within a terminal
```
ifconfig
```


lo (information)


p4p1 (information)


the information is the same that came up on the youtube tutorial, except eth0 was on the top and lo was on the bottom

---

### Post by archieburden9 on 2012-10-30
can someone help me please? i want to do this...

---

### Post by dannyboy79 on 2012-10-30
> **archieburden9 said:**
> can someone help me please? i want to do this...
im attempting to help you, this is free help and you shouldn't expect immediate answers, if that's what you want you should go check out the ubuntu irc channel. From all my research this appears to be a Fedora issue.

Whcih version of Ubuntu Server did you install?

also, from a terminal, what does this return?
```
sudo aptitude show biosdevname
```

---

### Post by archieburden9 on 2012-10-30
> **dannyboy79 said:**
> im attempting to help you, this is free help and you shouldn't expect immediate answers, if that's what you want you should go check out the ubuntu irc channel. From all my research this appears to be a Fedora issue.

Whcih version of Ubuntu Server did you install?

also, from a terminal, what does this return?
```
sudo aptitude show biosdevname
```

thanks, i thought you had gone :)

i installed 12.10

the command showed
```

package: (the package)
state: installed
automatically installed: no
versionL 0.4.1-0ubuntu3
priority: optional
section: misc
maintainer: colin watson
architecture: amd64
uncompressed size: 100k
depends: libc6 (>=2.14), libpci3 (>= 1:3.1.9-2), udev
description: apply BIOS-given names to network devices
 biosdevname in its simplest form takes a kernal device name as an argument, and returns the BIOS-given name it "should" be

this is necessary on system where the BIOS name for a given device (e.g the label on the chassis is "Gb1") dosent map directly and obviously to the kernel name (e.g eth0)

thiss also works as a straight udev rule, which is provided

home page: http://linux.dell/boisdevname

```

---

### Post by dannyboy79 on 2012-10-30
did you install that package? YOu must of because it says it's NOT installed automatically. Everything I am finding is that you should uninstall that package and also remove this file /lib/udev/rules.d/71-biosdevname.rules


your milage may vary and I am not responsible for anything that goes wrong.

I will be honest and say that I have no experience at all with this issue and am shocked it's happening to you as I have found no other Ubuntu users anywhere within google search results that have this same issue. 

GOod luck

---

### Post by archieburden9 on 2012-10-30
> **dannyboy79 said:**
> did you install that package? YOu must of because it says it's NOT installed automatically. Everything I am finding is that you should uninstall that package and also remove this file /lib/udev/rules.d/71-biosdevname.rules


your milage may vary and I am not responsible for anything that goes wrong.

I will be honest and say that I have no experience at all with this issue and am shocked it's happening to you as I have found no other Ubuntu users anywhere within google search results that have this same issue. 

GOod luck

wait, are you going :(

---

### Post by archieburden9 on 2012-10-30
also, i just realised im not connected to the internet, how do i connect the server to the internet?

---

### Post by dannyboy79 on 2012-10-30
relax, i am subscribed to this thread so when someone replies I am notified. Im not going anywhere BUT if you don't get a response that doesn't mean you bump your own thread after 5 minutes. THere's forum ettiquete which means you wait for a response at least 24 hours before bumping. as i said, if you really want instant support, ubuntu IRC channel which be much better for that.

---

### Post by archieburden9 on 2012-10-30
oh ok, but can you also tell me how to connect me server to the internet? google is failing me

---

### Post by dannyboy79 on 2012-10-30
> **archieburden9 said:**
> also, i just realised im not connected to the internet, how do i connect the server to the internet?

you need to configure your interfaces and then bring the interface up. you're gonna need to look for some guides in setting up iyour internet. SOrry, but I don't have time to walk through getting your server on the internet.

---

