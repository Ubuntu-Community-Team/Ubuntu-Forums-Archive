---
title: "Citrix receiver 13.9.1 on Ubuntu 18.04 64"
date: 2018-05-10
forum: Virtualisation
---

### Post by j4np0l on 2018-05-10
Hi all,

I am trying to get Citrix receiver to work on my Ubuntu laptop, as I'd like to use this as my main laptop, and I need to be able to login to my virtual desktop at work. Sadly, the help desk at my company only supports Windows or OSX, so they can't help me with this :(

I've installed the Citrix receiver (plus usb support and the web receiver as well just in case), however, when I try to open the .ica file that my company provides when I login to my organisation's Citrix Netscaler site, it exits out with an error that states "Cannot connect to 0.0.02 - Connect Desktop No such file or directory. Verify your connection settings and try again". After this, the .ica file gets deleted automatically. 

I've also tried adding the netscaler gateway address manually through configmgr and, after importing the root CA certificate to Citrix (as I was getting an SSL error) I end up getting a "error adding store HTTP 302" error. 

Any ideas on what could be happening here? In OSX or Windows I had no issues at all :(

Thanks!
Juan

---

### Post by j4np0l on 2018-05-10
Solved after a few minutes, I installed the previous version and I started getting a different error. Doing a bit of googling, I found that the solution is to do the following:

cd /opt/Citrix/ICAClient/keystore/
rm -rf cacerts
ln -s /etc/ssl/certs cacerts

---

### Post by alec-n on 2018-05-31
Thank you, that solved it for me for Citrix Receiver 3.9.1 on Ubuntu 18.04 64

---

### Post by sqlchip on 2018-08-13
Thanks so much!
IT Department could not figure this out and this solved my problem!

---

### Post by bittner on 2018-08-28
For explanations and background reading see [AskUbuntu](https://askubuntu.com/questions/1064452/citrix-receiver-13-10-on-ubuntu-18-04-1/1069929#1069929) ("Citrix receiver 13.10 on Ubuntu 18.04.1").

---

### Post by marcodejesus on 2019-01-04
This is really cool! Thanks a lot!

---

### Post by Aditya_Pal on 2019-01-14
Thanks man, your method works !!!

---

### Post by barezb on 2019-02-19
Thanks this worked for me using Citrix Workspace 1901 on Linux Mint 19.1 Cinnamon

---

### Post by russ2001 on 2019-02-19
Thanks worked great on Kubuntu 18.1

---

### Post by rolexim on 2019-03-02
This worked perfect for me too, Kubuntu 18.04 here.

Thanks!

---

