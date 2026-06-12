---
title: "Network manager in 14.04 LTS asks for keyring have no wifi connection"
date: 2014-10-11
forum: Security
---

### Post by mat125 on 2014-10-11
Hi I've been days trying to get Ubuntu to work and be online with wifi. I pressed the upgrade button in Ubuntu 12.04 LTS and only half upgraded and then it became unstable. So I fresh installed 14.04 from a successful image download which for a short while worked online with wifi. Then the network manager started to ask me for keyring access in my admin account and stopped the wifi connection. I entered my admin password and keyring access was denied why ? I tried all the other passwords requested along the way in loading the new op system with no joy. Is this a serious security problem ? Why should the network manager need to access my keyring and not just work for me using my admin password in that account ?

Hope someone can help its taken me three days plus to get here.

 I'm using Ubuntu Only and X86 64 and the latest kernel.

Mat

---

### Post by ian-weisser on 2014-10-11
> **mat125 said:**
> Why should the network manager need to access my keyring and not just work for me using my admin password in that account ?

Usually that happens when your admin password no longer matches the keyring password, or if you have enabled auto-login.

The keyring doesn't take the system's promise that you are who you claim to be. It shouldn't - it's protecting your sensitive data.
Either you use the right password, or you don't get access to the keys. Period.

As a convenience, keyring listens for the correct password when you login. Otherwise, it prompts when you do the first action that requires a stored key - like entering a secured wifi network.

To reset or change your keyring password, see [http://askubuntu.com/questions/65281/how-to-recover-reset-forgotten-gnome-keyring-password](http://askubuntu.com/questions/65281/how-to-recover-reset-forgotten-gnome-keyring-password)

---

### Post by mat125 on 2014-10-11
Hi Thanks for your reply. I have enabled auto login for a named person other than admin. Should I give that account a password then change it back to auto login later ?

I have since changed this user to having a password. Still keyring requests password.

---

### Post by mat125 on 2014-10-11
Which password should I give ? The encryted one ? The admin password ? Unix password ? The new user password ? I've tried all three. I have never been given nor had access to my keyring yet in my brand new install 14.04 LTS. I think the install should have gone smoother and I'm feeling very let down by Ubuntu right now. I'm trying to get wifi going !! I have already tried reinstalling the network manager with no joy and installed synaptic aswell as tried the dist upgrade thing in terminal.

---

### Post by ian-weisser on 2014-10-11
Each user that you create has their own keyring.
Make things simple: Change each user's keyring password so it's identical to that user's login password.

---

### Post by mat125 on 2014-10-11
Hi thanks for your help. Think I may have made the mistake of resetting the GnuPG keys in the software updater to defaults now showing a 2012 entry. I started thinking it may have thrown the security out somehow ! Managed to find 'view by keyring' in passwords and keys. Having a go now fingers crossed.
Mat

Have changed my keyring password to my admin one but still my router shows up with a three quarter signal but it aimlessly searches on and on to no avail. Will have to either change the network manager to something else or think about another distro urgently. Im quickly getting into trouble not having a safe PC working. I keep getting asked for the network password at the moment. Thinking the software is not stable.

---

### Post by bashiergui on 2014-10-12
It sounds like a wireless driver problem to me- the upgrade broke the driver you had. I have no idea how to fix it, though, aside from searching Google and the internet for wireless driver + your NIC + your computer.

---

### Post by mat125 on 2014-10-13
Hi thanks for your replies and thanks to you Ian. The changing the keyring password worked, but there is still a security concern because of the fact both the admin account and the spare user account not only require a wifi password but my _admin_ password ?!! for me to complete a wifi connection, which i recently sorted. Surely that will expose my computer to anyone who is good at hacking !! 
.Secondly it turned out that my direction pci antenna/ariel was broken but i did not realise it soon enough because there was another different long antenna left around the room, which i eventually tried and that to turned out to be broken. Lastly I tried the original three small ariels on the pci card and they worked but with a half a bar strength one quarter inferior to what i had before.

Thanks for your help my wifi connection is now solved. By the way Ubuntu i take back what i said before except for the security thing. Good thing about the 14.04 LTS installation this time was the fact that my cheap canon printer worked first time without the need to find a printer driver, well done i have to say.

Thanks to all once again.

---

### Post by ian-weisser on 2014-10-13
> **mat125 said:**
> The changing the keyring password worked, but there is still a security concern because of the fact both the admin account and the spare user account not only require a wifi password but my _admin_ password ?!! for me to complete a wifi connection, which i recently sorted. Surely that will expose my computer to anyone who is good at hacking !!

Glad to see you have the issue sorted.

I do not see how using your login password to access your keyring that conveniently stores your WEP/WPA key exposes your computer. Neither your login password nor your keyring password is broadcast. If somebody did reconstruct your wireless key, all they could do is join your wireless network. They would not be able to login to your system remotely.

You can change the keyring password to something different from your login/admin password if you wish. Of course, you will still need to enter the (new) keyring password to establish a wireless connection after you login.

---

### Post by mat125 on 2014-10-13
Thanks Ian for your reply which is very much appreciated. I still do not understand why i'm asked for both - the admin password and or additional passwords other than the router password ?. Surely i should only be asked for the router password just that to get access to wifi/wireless ?? The keyring should be protecting and keeping bugs or worms out of the admin account and the keyring password should not have to be asked for during the wifi set up nor accessed. Surely there is an element of immediate exposure here. There must be a simpler way of sorting this out. Basically i was asked for two lots of different passwords on both accounts many times while i was trying to work out the ariel problem !

Many Thanks.

---

### Post by ian-weisser on 2014-10-13
> **mat125 said:**
> I still do not understand why i'm asked for both - the admin password and or additional passwords other than the router password ?. Surely i should only be asked for the router password just that to get access to wifi/wireless ??

Entering the same router password every session gets tedious and annoying.
The purpose of a keyring is to safely automate that authentication.


 > **mat125 said:**
> The keyring should be protecting and keeping bugs or worms out of the admin account

Safeguarding your passwords? Yes.
Protecting from bugs and worms? No. It's a database, not an antivirus.


 > **mat125 said:**
> There must be a simpler way of sorting this out.

There are several, with varying costs and benefits:
1) You can make the keyring password match the login password.
2) You can delete the router password entry from the keyring.
3) Or you can uninstall the keyring entirely.

---

