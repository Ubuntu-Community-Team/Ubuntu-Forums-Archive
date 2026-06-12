---
title: "Creating a secure installation for ebanking, online shopping etc"
date: 2011-10-28
forum: Security
---

### Post by PeteAsdf on 2011-10-28
I'm thinking about creating a 'secure' Linux install on an USB stick that I would boot into any time I want to connect to my ebanking accounts/ online shopping websites that store my credit card details or whenever I want to do anything sensitive away from my home PC.

Intended setup:

- Live system with a boot on the USB stick with encrypted home folder and no swap partition

- Encrypt a small partition of the USB stick with Truecrypt to securely store passwords (in keepass), PGP keys etc

- Encrypt the entire system partition with Truecrypt with boot password authentication

- Use Firefox for the web browsing with several extentions (https everywhere, noscript, adblock).

I'm currently using Kubuntu as my main OS and I really like it. The problem I can see with installing Kubuntu on on the USB stick  is that it contains too many packages and apps that I do not need for my needs and consequently I think it doesn't make much sense from the security point of view.

Would you recommend installing some other 'bare bones' distro or going with Ubuntu/ Kubuntu? I was looking at Qubes OS or Tinfoil Hat.

Any other suggestions for securing my system for ebanking, online shopping etc? :confused:

Thanks!

---

### Post by theristus on 2011-10-28
Do you know [https://launchpad.net/nemato](https://launchpad.net/nemato)? It is is developpement and work fine on ubuntu 11.04.

whith this software you can create a customizable live usb.

---

### Post by CharlesA on 2011-10-28
Hmm, I just using an SSH tunnel if I am on a public network and need to access "sensitive" sites - bank, shopping, school, etc.

Of course I use my own machine instead of a random public one.

---

### Post by OpSecShellshock on 2011-10-28
This strikes me as kind of a lateral move from a risk management standpoint. There isn't really such a thing as a secure OS/installation. When dealing with browser-based interactions that deal in sensitive information, behavior is going to be the thing to be most mindful of. It's also going to be a matter of network control. You'll want to be on a network that you are in control of all the way to the ISP premise. You will also only want to engage with sites that use fully encrypted sessions (some of them still only encrypt the authentication and transactions, if you can believe it). Well that applies more to banking than to general commerce I guess. Using a clean browser session for each task is also probably a good idea. I suppose it depends on what you mean to gain from the live USB session.

Granted, this is a technique I have seen recommended in places (Krebs, for example), but it seems to be more of a way to compensate for other, higher risk usage activities than it is to make the banking itself more secure.

---

### Post by Gentoo64 on 2011-10-29
I think you're being over paranoid. If it's just using the browser to do online banking, then imo simply checking https is on should be enough, if you are storing bank details etc then encryption would obviously be a good choice. But if not it's pointless, same for encrypting swap etc.
I think the easiest option would be to carry on using your existing Ubuntu as it's secure as it is. I don't think you've got anything to worry about at all, as long as you have some common sense while browsing.

---

### Post by collisionystm on 2011-10-29
If you are doing online transactions and feeling that paranoid the only thing that I would do is have

1) Clean, add-on free web browser. 
2) Make sure any websites you enter your credit card into prefix with HTTPS at the credit info screen.
3) Check reviews on the website if it is not common to you.

4) Or even better... call the Credit Unions and tell them you want to add a password to your account. It is free. This way no one can do a credit transaction with your name or social without providing a password via the phone.

---

### Post by CharlesA on 2011-10-29
> **collisionystm said:**
> If you are doing online transactions and feeling that paranoid the only thing that I would do is have

1) Clean, add-on free web browser. 
2) Make sure any websites you enter your credit card into prefix with HTTPS at the credit info screen.
3) Check reviews on the website if it is not common to you.


Huge +1. I use my normal browser for online banking, but I haven't gone completely nuts with addons.

Haven't heard about the credit union thing, but I do know some use something like a RSA keyfob.

---

### Post by collisionystm on 2011-10-29
> **CharlesA said:**
> Huge +1. I use my normal browser for online banking, but I haven't gone completely nuts with addons.

Haven't heard about the credit union thing, but I do know some use something like a RSA keyfob.

Yeah I had my Realtor actually tell me about the Credit Union thing lol. Apparently you call these 3

> 

The Three Major Credit Bureaus
Here's how to contact the three major credit bureaus to ask about or obtain your credit report or credit score, alert creditors to a possible fraud using your name, or for any other reason: 

Equifax: 800-685-1111 (general) or 800-525-6285 (fraud); P.O. Box 740241, Atlanta, GA 30374; [www.equifax.com](www.equifax.com)

Experian: 888-397-3742 (general and fraud); PO Box 2002, Allen, TX 75013, [www.experian.com](www.experian.com).

TransUnion: 800-888-4213 (general) or 800-680-7289 (fraud); P.O. Box 2000, Chester, PA 19022; [www.transunion.com](www.transunion.com).




@OP I know this was not mentioned but also be careful using proxies for something like this. #1 you do not know who or what is hosting a proxy. Stay away from them unless it is yours.

---

### Post by CharlesA on 2011-10-29
> **collisionystm said:**
> Yeah I had my Realtor actually tell me about the Credit Union thing lol. Apparently you call these 3

Interesting. I'm guessing that they meant protecting yourself from identity theft since those three companies/agencies monitor your credit report and any new accounts that are opened in your name gets put on your credit report.

> @OP I know this was not mentioned but also be careful using proxies for something like this. #1 you do not know who or what is hosting a proxy. Stay away from them unless it is yours.

Yeah, you never know what they could do with your data. The only "proxy" I use is a SSH tunnel to my server at home when I am on public wifi.

---

### Post by Gentoo64 on 2011-10-29
I was going to add.. don't ever use a proxy (TOR, anything like that). I can't imagine how many people do (thinking it's somehow more secure)

---

### Post by CharlesA on 2011-10-29
> **Gentoo64 said:**
> I was going to add.. don't ever use a proxy (TOR, anything like that). I can't imagine how many people do (thinking it's somehow more secure)

Aye. TOR is more for anonymity then security, but even then you can still be tracked down.

---

### Post by collisionystm on 2011-10-29
> **Gentoo64 said:**
> I was going to add.. don't ever use a proxy (TOR, anything like that). I can't imagine how many people do (thinking it's somehow more secure)


I made my own google proxy a long time ago haha

[http://collisionsystm.appspot.com/](http://collisionsystm.appspot.com/)

Still would not trust it... but it was still fun.

---

### Post by Dangertux on 2011-10-29
> **OpSecShellshock said:**
> This strikes me as kind of a lateral move from a risk management standpoint. There isn't really such a thing as a secure OS/installation. When dealing with browser-based interactions that deal in sensitive information, behavior is going to be the thing to be most mindful of. It's also going to be a matter of network control. You'll want to be on a network that you are in control of all the way to the ISP premise. You will also only want to engage with sites that use fully encrypted sessions (some of them still only encrypt the authentication and transactions, if you can believe it). Well that applies more to banking than to general commerce I guess. Using a clean browser session for each task is also probably a good idea. I suppose it depends on what you mean to gain from the live USB session.

Granted, this is a technique I have seen recommended in places (Krebs, for example), but it seems to be more of a way to compensate for other, higher risk usage activities than it is to make the banking itself more secure.


I agree with this, mostly.

If you think about it, controlling the operating system that the information is sent from while important really isn't going to be the main focus here. You want to insure that you're controlling the data to avoid things like MITM + SSLstrip grabbing your credentials.

Ultimately that goal will be hard if you don't control the network itself. As was stated in the post I quoted.

---

### Post by CharlesA on 2011-10-29
> **Dangertux said:**
> 
If you think about it, controlling the operating system that the information is sent from while important really isn't going to be the main focus here. You want to insure that you're controlling the data to avoid things like MITM + SSLstrip grabbing your credentials.

Yeah, that's the big problem. Not much you can do it someone is doing a MitM attack on you unless you are using a VPN or SSH tunnel to make the traffic unreadable.

---

### Post by HermanAB on 2011-10-29
Well, you are not paranoid if they really are out to get you...

However, to me, my normal laptop computer with Linux is secure enough.

---

### Post by Thewhistlingwind on 2011-10-29
I'd be more worried about the network I'm connecting from than I would my install.

---

### Post by c.cobb on 2011-11-01
All of that said, there are times when a Live USB with Linux is a good and necessary alternative to using a Windows PC for online banking. I use Lucid on my desktop, and have it reasonably secured for this but, where I live, having a Plan B is a necessity.

If my power goes out, if my Internet fails for another reason, or if I'm just on the road, I want the ability to access my bank from an Internet Cafe or hotel lobby. With a custom version of Lucid running from a Live USB, I feel that I have this.

I added several things that help make the Live USB both more secure and easier to use. Password Safe to manage passwords, TrueCrypt with a wrapper script so can mount/unmount TC volumes with a click of a launcher icon and a password, ssh certificates so I can copy stuff to/from my website, and FFox includes security add-ons such as NoScript. If I lose the USB stick, no big deal as everything important is encrypted.

Also added a script that runs during boot that copies some stuff from the USB into the Live file system (such as the ssh certs and other config files), and creates some symlinks in the Live fs back to the USB (such as to a data dir with TC data files). And the USB has the boot files necessary to boot my version from either a PC or a Mac. You can decide during bootup whether to allow write access to the Live USB or have it mounted read-only.

And yes, on top of this it's still important to examine SSL certs when connecting via the browser. However, a Live USB can definitely be made reasonably secure, using Ubuntu, to give a home-made alternative to an Iron Key USB. 

And oh yeah, I package this remix in a ZIP file instead of an ISO, and have a script that installs the Syslinux boot loader. This way, it's simple to setup a Live USB from a Windows box without having to mess with CDs, and this way you won't get the USB "geometry" conflict that you can sometimes have with Grub.
Solo mis dos colones,

---

### Post by PeteAsdf on 2011-11-01
Thanks for the replies.

Just to explain myself: The reason I wanted to create this Live USB
install was mainly because:

1) there are several people who have physical access to my PC

2) from time to time I'm using torrents, who knows what kind of rootkit I might be downloading

Therefore I didn't feel too good about using sensitive data on such an
install.


@c.cobb: thanks for the interesting tips. Out of curiosity- how do you set up that option during boot of your Live USB to be able to choose between read-only and R-W modes?

---

### Post by c.cobb on 2011-11-01
To make the USB writable, make sure that you have the lupin-casper package installed in your remix. Then, if your boot menu entry includes the following option, in addition to the read-only /cdrom mount point, you will get a writable /isodevice mount point.  (edit: Forgot to mention this is only writable by 'root' however, when booted from a Live USB, you are not prompted for a password when using sudo.)

```
iso-scan/filename=/any/existing/file
```The filename can be any existing file on your USB, not just an ISO file. BTW, the lupin-casper package is what allows for booting directly from an ISO file--for example if a USB stick is set up to boot using Grub2, simply add the ISO of your Ubuntu remix, and create a menu entry using Grub's loopback mechanism.  

Here are [examples of the entries]("http://ccobb.net/ubuntu/boot_menu.html") that I use for both Grub2 and Syslinux. These include the option to boot on a computer that has a Spanish keyboard, which needs the language package installed. (correction: it's the 'casper' package (not lupin-casper) that allows keyboard selection--the language package is only necessary to boot in the Spanish language. D'Oh.)

---

